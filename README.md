# Actividad 2 — Agregar un filtro nuevo

## Filtro agregado

Se añadió un filtro por **edad** (`ageFilter`) que permite al usuario filtrar los animales por su edad.

## Código agregado/modificado

```javascript
// Estado para el nuevo filtro
const [ageFilter, setAgeFilter] = useState("all");

// Control en la UI (dentro de los otros filtros)
<label className="sr-only" htmlFor="age-filter">
  Age
</label>
<select
  id="age-filter"
  value={ageFilter}
  onChange={(e) => setAgeFilter(e.target.value)}
  className="rounded-md border border-gray-300 px-3 py-2 text-sm outline-none focus:ring-2 focus:ring-green-600 dark:border-neutral-700 dark:bg-neutral-800 dark:text-gray-100"
>
  <option value="all">All ages</option>
  <option value="1">1 year</option>
  <option value="2">2 years</option>
  <option value="3">3 years</option>
</select>

// Lógica de filtrado (modificada para incluir ageFilter)
const filteredAnimals = useMemo(() => {
  const q = query.trim().toLowerCase();
  return animals.filter((a) => {
    const byType = typeFilter === "all" || a.type === typeFilter;
    const byStatus = statusFilter === "all" || a.status === statusFilter;
    const byAge = ageFilter === "all" || a.age === parseInt(ageFilter);
    const byQuery =
      q.length === 0 ||
      a.name?.toLowerCase().includes(q) ||
      a.type?.toLowerCase().includes(q) ||
      String(a.weight).includes(q) ||
      String(a.age).includes(q);
    return byType && byStatus && byAge && byQuery;
  });
}, [animals, typeFilter, statusFilter, ageFilter, query]);
