# Actividad 3 — Mejorar el formulario

## Mejoras implementadas

Se realizaron dos mejoras en el formulario de creación de animales para mejorar la experiencia del usuario:

1. **Validación en tiempo real**:  
   - Se agregaron mensajes de error que se muestran inmediatamente cuando un campo obligatorio está vacío o el valor ingresado es incorrecto (por ejemplo, edad o peso no numérico).  
   - Esto evita que el usuario envíe un formulario con datos inválidos y proporciona retroalimentación instantánea.

2. **Autofocus en el primer campo**:  
   - Al abrir el formulario, el cursor se coloca automáticamente en el primer campo de entrada (nombre del animal).  
   - Esto mejora la fluidez al llenar el formulario, evitando que el usuario tenga que hacer clic antes de escribir.

## Qué cambió visualmente

- Aparecen mensajes de error en rojo debajo de los campos cuando los datos no son válidos.  
- Al abrir el formulario, el cursor ya está en el campo "Nombre", listo para escribir.

## Relación con la experiencia de usuario

- La validación en tiempo real reduce errores y frustración, asegurando que los datos sean correctos antes de enviarlos.  
- El autofocus acelera la interacción y hace que el formulario sea más intuitivo y cómodo de usar.

## Líneas de código modificadas (ejemplos)

```javascript
// Validación en tiempo real dentro del formulario
{errors.name && <p className="text-red-500 text-sm">{errors.name}</p>}

// Autofocus en el primer input
<input
  type="text"
  name="name"
  value={form.name}
  onChange={handleChange}
  autoFocus
  className="..."
/>
```

Estas modificaciones hacen que el formulario sea más amigable, eficiente y accesible para los usuarios.
