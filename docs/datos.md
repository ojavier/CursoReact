---
id: datos
title: Compartir datos entre componentes
sidebar_position: 8
---

## ¿Qué pasa si varios componentes comparten datos?

Por ejemplo:

- Un componente que guarda el nombre del usuario.

- Otro componente que lo muestra en pantalla.

## Pasar datos con Props

```
function Saludo({ nombre }) {
  return <h1>Hola, {nombre} </h1>;
}

function App() {
  return <Saludo nombre="Oscar" />;
}
```

Qué pasa:

- App pasa nombre="Oscar" a Saludo.

- Saludo recibe nombre y lo muestra en pantalla.

- Esto es como pasarle un mensaje de un componente padre a su hijo.

## Compartir datos entre hermanos (levantar el estado)

¿Qué pasa si dos componentes necesitan el mismo dato?

Ejemplo: un input que guarda el nombre y un saludo que lo muestra.

```
import { useState } from "react";

function EntradaNombre({ onChangeNombre }) {
  return (
    <input
      type="text"
      placeholder="Escribe tu nombre"
      onChange={(e) => onChangeNombre(e.target.value)}
    />
  );
}

function Saludo({ nombre }) {
  return <h1>Hola, {nombre || "desconocido"} </h1>;
}

function App() {
  const [nombre, setNombre] = useState("");

  return (
    <div>
      <EntradaNombre onChangeNombre={setNombre} />
      <Saludo nombre={nombre} />
    </div>
  );
}
```

Qué pasa:

- App guarda el nombre en su estado.

- EntradaNombre actualiza el estado.

- Saludo recibe el valor y lo muestra.

- Así, ambos usan el mismo dato, porque está en el componente padre.

Esto se llama levantar el estado (porque subes el estado a un componente que está por encima de ambos).

## Compartir datos con Context (cuando hay muchos componentes)

Si tienes que pasar los mismos datos a muchos niveles (por ejemplo, usuario → header, sidebar, footer), usar props puede ser muy incómodo.

Para eso existe el **Context API**.

Ejemplo simple:

```
import { createContext, useContext, useState } from "react";

const UsuarioContext = createContext();

function Saludo() {
  const nombre = useContext(UsuarioContext);
  return <h1>Hola, {nombre} </h1>;
}

function App() {
  const [nombre, setNombre] = useState("Oscar");

  return (
    <UsuarioContext.Provider value={nombre}>
      <Saludo />
    </UsuarioContext.Provider>
  );
}
```

Qué pasa:

- UsuarioContext.Provider → es como una caja que envuelve los componentes y les pasa el valor.

- useContext(UsuarioContext) → saca el valor de esa caja.

- No necesitas pasar props manualmente por cada nivel. React lo hace automáticamente.

## Resumen

- **Props**: Cuando pasas datos de padre → hijo (caso simple).

- **Levantar estado**: Cuando pasas datos de padre → hijo (caso simple).

- **Context**: Cuando los datos se usan en muchos niveles y pasar props sería tedioso.