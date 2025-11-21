### Actividad 1 — Modificación de estado
 
Estado modificado: `typeFilter`  
Valor inicial cambiado de `"all"` a `"cow"`.

const [typeFilter, setTypeFilter] = useState("cow"); // Cambio de 'all' a 'cow'
const [statusFilter, setStatusFilter] = useState("all");
const [query, setQuery] = useState("");

**Qué cambió visualmente:**  
Al cargar la aplicación, en lugar de mostrar todos los animales, solo se mostró el animal cuyo tipo es `"cow"`.  
Esto se debe a que el filtro ahora aplica automáticamente desde el inicio.


**Relación con renderizado:**  
React vuelve a renderizar la interfaz según el valor del estado `typeFilter`.  
Como `typeFilter` ahora tiene el valor `"cow"` desde el inicio, la lista de animales se filtra automáticamente y solo se muestran los animales que coinciden con ese tipo.
