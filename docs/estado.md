---
id: estado
title: Eventos y estados
sidebar_position: 6
---

# Eventos y estados

## Responder a eventos

Un evento es algo que hace el usuario: un clic, escribir en un input, pasar el mouse, etc.
En React, puedes poner funciones que reaccionan a esos eventos.

Ejemplo simple:

```
function Boton() {
  function manejarClick() {
    alert("¡Hiciste clic!");
  }

  return <button onClick={manejarClick}>Haz clic aquí</button>;
}
```

- onClick = {"manejarClick"} → cuando el usuario haga clic, ejecuta la función manejarClick.

- React nombra los eventos con camelCase → onClick, onChange, onSubmit.


## Actualizar la pantalla (estado)

Para que React actualice la pantalla, usamos algo llamado estado.
El estado es como una cajita de datos que React vigila.
Cuando cambias el estado → React redibuja el componente con la información nueva.

Ejemplo con contador:

```
import { useState } from "react";

function Contador() {
  const [contador, setContador] = useState(0);

  function sumar() {
    setContador(contador + 1);
  }

  return (
    <div>
      <p>Has hecho clic {contador} veces</p>
      <button onClick={sumar}>Haz clic</button>
    </div>
  );
}
```
Qué pasa:

- useState(0) → crea el estado inicial en 0.

- contador → el valor actual.

- setContador() → función para cambiar el valor.

- Cada vez que llamas setContador(...), React vuelve a renderizar el componente y muestra el nuevo número.

## Combinando eventos + actualización de pantalla

Podemos combinar eventos y estado para hacer interfaces dinámicas.
Ejemplo: mostrar/ocultar un texto con un botón.

```
import { useState } from "react";

function MostrarOcultar() {
  const [visible, setVisible] = useState(true);

  function toggle() {
    setVisible(!visible); // Cambia true → false y viceversa
  }

  return (
    <div>
      <button onClick={toggle}>
        {visible ? "Ocultar" : "Mostrar"}
      </button>
      {visible && <p> ¡Me puedes ver!</p>}
    </div>
  );
}
```

Qué pasa:

- Cuando haces clic, cambias el estado (visible).

- React vuelve a renderizar y decide si debe mostrar el < p > o no (renderizado condicional).

## Resumen

- Eventos: permiten que el usuario interactúe (clic, escribir, etc.).

- Estado (useState): almacena datos que pueden cambiar.

- React actualiza la pantalla automáticamente cuando el estado cambia → no tienes que actualizar el HTML manualmente.