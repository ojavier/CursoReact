---
id: vdom
title: Virtual DOM
sidebar_position: 3
---

## ¿Qué es el DOM?

- El DOM (Document Object Model) es una representación en forma de árbol de tu página web.

- Cada elemento HTML (un ```<div>, <button>, <p>, etc.```) es un “nodo” en ese árbol.

- El navegador usa este árbol para saber qué mostrar en pantalla.

Modificar el DOM real es lento. Cada vez que cambias algo (ej. el texto de un botón), el navegador tiene que recalcular estilos, reestructurar el árbol y redibujar la pantalla.

## ¿Qué hace React con el Virtual DOM?

- React crea una copia virtual del DOM → el Virtual DOM.

- Este Virtual DOM es una representación ligera del DOM real, que React guarda en memoria.

- Cuando algo cambia en tu app (ej. se incrementa un contador con useState):

    1. React actualiza el Virtual DOM primero.

    2.  Compara el Virtual DOM anterior con el nuevo (esto se llama diffing).

    3. Encuentra las diferencias mínimas (ej. “solo cambió el número en este ```<span>```”).

    4. Actualiza solo esa parte en el DOM real.

## Ejemplo

```
function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <h1>Contador: {count}</h1>
      <button onClick={() => setCount(count + 1)}>+1</button>
    </div>
  );
}
```

Cada vez que das clic en el botón:

- React NO vuelve a dibujar toda la página.

- Solo cambia el texto ```{count}``` dentro del ```<h1>```.

- Esto es gracias al Virtual DOM que detecta qué cambió exactamente.

## Ventajas del Virtual DOM

- Rendimiento: evita modificaciones innecesarias en el DOM real.

- Optimización automática: React decide qué actualizar, tú no te preocupas por eso.

- Experiencia fluida: la app responde rápido, incluso con muchos cambios.


El Virtual DOM es como un borrador en memoria que React usa para planear los cambios en la interfaz. Luego solo aplica los cambios estrictamente necesarios en el navegador.