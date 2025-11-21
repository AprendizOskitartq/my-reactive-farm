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
# Respuestas del Cuestionario de React

A continuación se responden las 10 preguntas solicitadas basadas en el análisis del proyecto **My Reactive Farm**.

---

## 1. ¿Cuál es la diferencia entre un componente presentacional y un componente de página en React?  
Los **componentes presentacionales** muestran información y reciben datos por props. No manejan lógica compleja.  
Ejemplo del proyecto: **AnimalCard.jsx**, que solo muestra la información de un animal.

Los **componentes de página** contienen lógica, estados, efectos y llamadas a la API.  
Ejemplo: **AnimalsPage.jsx**, que carga los animales, maneja filtros y muestra mensajes de carga o error.

---

## 2. ¿Para qué se utiliza useState en el proyecto? Menciona dos estados distintos y su función.  
- **animals**: almacena la lista completa de animales obtenidos desde MockAPI.  
- **loading**: indica si la aplicación está esperando la respuesta de la API y permite mostrar un mensaje de "Cargando...".

---

## 3. ¿Cómo se usa useEffect para cargar datos desde MockAPI al inicio? Explica el flujo.  
1. La página se monta (se renderiza por primera vez).  
2. useEffect se ejecuta automáticamente.  
3. Llama a la función `getAnimals()` desde `animalsApi.js`.  
4. Cuando llega la respuesta, actualiza el estado `animals`.  
5. React vuelve a renderizar la interfaz con los datos reales.

---

## 4. ¿Cómo maneja el proyecto los estados de loading, error y lista vacía?  
- **loading = true** → Se muestra un texto como *"Cargando animales..."*.  
- **error = true** → Se muestra un mensaje indicando que ocurrió un problema al cargar la información.  
- **animals.length = 0** → Se muestra *"No hay animales disponibles"*.

Esto ayuda a que el usuario siempre entienda lo que está pasando.

---

## 5. ¿Qué significa que un formulario sea controlado en React? Relaciónalo con el proyecto.  
Un **formulario controlado** es aquel en el que el valor de cada input viene del estado.  
En el proyecto, los campos del formulario de creación de animales usan `useState` para guardar:  
- nombre  
- tipo  
- edad  

Cada cambio en un input actualiza el estado y React vuelve a renderizar el formulario.

---

## 6. ¿Por qué es buena práctica separar la lógica de datos en archivos como animalsApi.js en vez de hacer peticiones dentro de los componentes?  
Porque:  
- Organiza el código.  
- Reduce duplicación.  
- Los componentes quedan más limpios.  
- Permite reutilizar las funciones en varias páginas.

Además, si cambia la URL de la API, solo se modifica un archivo.

---

## 7. ¿Qué hace que AnimalCard sea un componente reutilizable?  
Porque:  
- Recibe datos por props.  
- No está limitado a un tipo específico de información.  
- Solo muestra la UI, no maneja lógica interna.

Una tarjeta similar podría usarse para:  
- Usuarios  
- Productos  
- Mascotas en adopción  
- Vehículos

---

## 8. ¿Qué elementos del proyecto contribuyen a la accesibilidad?  
1. **Etiquetas semánticas (`button`, `form`, `label`)** → Permiten que lectores de pantalla entiendan la interfaz.  
2. **Texto alternativo o labels claros** → Los usuarios saben qué deben escribir en cada campo.  
3. **Botones grandes y colores con contraste (Tailwind)** → Hace más fácil la interacción para personas con baja visión o dispositivos pequeños.

---

## 9. Antes de agregar una funcionalidad nueva, ¿qué pasos debes pensar según la filosofía de React?  
1. ¿Qué datos voy a manejar?  
2. ¿Qué estado necesito crear?  
3. ¿En qué componente debe vivir ese estado?  
4. ¿Quién debe recibir ese estado por props?  
5. ¿Qué cambios van a disparar un re-render?

---

## 10. ¿Qué conceptos de React aprendidos en este proyecto podrías reutilizar en otras aplicaciones?  
- Manejo de estados con **useState**  
- Llamadas a API con **Axios**  
- Efectos iniciales con **useEffect**  
- Formularios controlados  
- Componentes reutilizables  
- Filtrado y renderizado condicional  
- Manejo de loading y error

hecho por oskitar torres quintero ficha:3293689
