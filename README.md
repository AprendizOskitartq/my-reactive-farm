# Actividad 2 — Agregar un filtro nuevo

## Filtro agregado

Se añadió un filtro por **edad** (`ageFilter`) que permite al usuario filtrar los animales por su edad.

## Líneas de código agregadas/modificadas

- Estado para el filtro:
  ```javascript
  const [ageFilter, setAgeFilter] = useState("all");
  ```
- Dropdown en la interfaz de filtros:
  ```javascript
  <label className="sr-only" htmlFor="age-filter">Age</label>
  <select
    id="age-filter"
    value={ageFilter}
    onChange={(e) => setAgeFilter(e.target.value)}
  >
    <option value="all">All ages</option>
    <option value="1">1 year</option>
    <option value="2">2 years</option>
    <option value="3">3 years</option>
  </select>
  ```
- Modificación en la lógica de filtrado:
  ```javascript
  const byAge = ageFilter === "all" || a.age === parseInt(ageFilter);
  return byType && byStatus && byAge && byQuery;
  ```

## Qué cambió visualmente

Se agregó un nuevo dropdown en los filtros que permite seleccionar la edad de los animales. Al elegir una edad específica, la lista de animales se actualiza automáticamente mostrando solo los animales que cumplen con ese criterio. Si se selecciona "All ages", se muestran todos los animales.

## Relación con el renderizado en React

- React vuelve a renderizar la lista de animales cada vez que cambia el estado `ageFilter`.
- Esto permite que la interfaz se actualice dinámicamente sin recargar la página, mostrando únicamente los animales que coinciden con el filtro seleccionado.
