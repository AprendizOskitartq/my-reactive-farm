
  # Proyecto React --- Análisis Técnico

##  Propósito General del Proyecto

Este proyecto es una aplicación construida en **React** que permite
gestionar información mediante formularios, consumir datos desde una API
(MockAPI) y mostrar resultados en pantalla. Usa **Axios** para las
peticiones HTTP y **Tailwind CSS** para el diseño responsivo y moderno.

------------------------------------------------------------------------

##  Estructura del Proyecto

    /src
     ├── components/
     │    ├── Form.jsx
     │    ├── ItemList.jsx
     │    └── Navbar.jsx
     ├── pages/
     │    ├── Home.jsx
     │    └── Dashboard.jsx
     ├── services/
     │    └── api.js
     ├── App.jsx
     ├── main.jsx
     └── index.css

### Descripción:

-   **components/** --- Componentes reutilizables como formularios y
    listas.
-   **pages/** --- Vistas principales del proyecto.
-   **services/api.js** --- Configuración de Axios para conectarse a
    MockAPI.
-   **App.jsx** --- Enrutamiento y estructura base.
-   **index.css** --- Configuración global de Tailwind.

------------------------------------------------------------------------

##  Manejo del Estado --- useState

`useState` se utiliza para manejar valores internos del componente
como: - Inputs del formulario. - Datos obtenidos de la API. - Estados de
carga y error.

Ejemplo:

``` javascript
const [nombre, setNombre] = useState("");
const [items, setItems] = useState([]);
```

------------------------------------------------------------------------

##  Efectos --- useEffect

Se emplea para ejecutar acciones cuando un componente se monta, como:

-   Cargar datos desde la API al iniciar.
-   Sincronizar información cuando cambia un estado.

Ejemplo:

``` javascript
useEffect(() => {
  obtenerItems();
}, []);
```

------------------------------------------------------------------------

##  Consumo de API --- Axios + MockAPI

### Configuración base (`services/api.js`):

``` javascript
import axios from "axios";

export const api = axios.create({
  baseURL: "https://<tu-endpoint>.mockapi.io",
});
```

### Ejemplo de GET:

``` javascript
const obtenerItems = async () => {
  const respuesta = await api.get("/items");
  setItems(respuesta.data);
};
```

### Ejemplo de POST:

``` javascript
const crearItem = async () => {
  await api.post("/items", { nombre, edad });
};
```

------------------------------------------------------------------------

##  Manejo de Formularios y Validaciones

El formulario controla los inputs con `useState`:

``` javascript
<input
  value={nombre}
  onChange={e => setNombre(e.target.value)}
/>
```

Validaciones típicas: - Verificar campos vacíos. - Validar formato de
correo/números. - Mostrar mensajes de error.

Ejemplo:

``` javascript
if (!nombre.trim()) {
  setError("El nombre es obligatorio");
  return;
}
```

------------------------------------------------------------------------

##  Uso de Tailwind CSS

El proyecto utiliza clases utilitarias como:

``` html
<div class="p-4 bg-gray-100 rounded-lg shadow">
  <h1 class="text-2xl font-bold">Formulario</h1>
</div>
```

Ventajas: - Código más limpio. - Diseño rápido. - Totalmente responsivo.

------------------------------------------------------------------------

##  Resumen Final

Este proyecto implementa: ✔ Gestión de estado con **useState**\
✔ Acciones automáticas con **useEffect**\
✔ Consumo de API usando **Axios** y **MockAPI**\
✔ Formularios controlados con validaciones\
✔ Diseño responsivo con **Tailwind CSS**\
✔ Estructura modular y escalable

------------------------------------------------------------------------

##  Autor

Oscar Torres Quintero Ficha 3293689
