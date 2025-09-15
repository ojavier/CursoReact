---
id: componentes
title: Crear y anidar componentes
sidebar_position: 3
---

# Crear un componente

En React, un componente es normalmente una función que devuelve algo de HTML (bueno, JSX, que es como HTML dentro de JS).

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