---
id: componentes
title: Crear y anidar componentes
sidebar_position: 4
---

# Componentes

En React, un componente es normalmente una función que devuelve algo de HTML (bueno, JSX, que es como HTML dentro de JS).

## Crear un componente

Ejemplo de un componente muy básico:

```
function Saludo() {
  return <h1>¡Hola, mundo!</h1>;
}
```

- function Saludo() es el nombre del componente.

- return < h1 > ... < /h1 > dice qué debe mostrar en pantalla.

Para usarlo, lo escribes como si fuera una etiqueta HTML:

```
<Saludo />
```
Esto mostrará en la página:
¡Hola, mundo!

## Anidar componentes

Ahora imagina que tienes varios componentes y quieres ponerlos juntos.
Por ejemplo:

```
function Saludo() {
  return <h1>¡Hola!</h1>;
}

function Despedida() {
  return <p>Adiós, que te vaya bien</p>;
}

function App() {
  return (
    <div>
      <Saludo />
      <Despedida />
    </div>
  );
}
```

- App es como el componente principal.

- Dentro de App, pusimos otros dos componentes (Saludo y Despedida).

- React los junta y muestra:


```
¡Hola!
Adiós, que te vaya bien

```