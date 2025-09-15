---
id: hooks
title: Hooks
sidebar_position: 7
---

# Hooks

Un hook es como una herramienta especial que te da React para usar estados y otras funciones en tus componentes.
Por ejemplo, que puedan guardar datos, reaccionar a cambios, o conectarse con cosas externas.

## El más famoso: useState

Te permite guardar información (estado) en un componente y actualizar la pantalla cuando cambie.

```
import { useState } from "react";

function Contador() {
  const [contador, setContador] = useState(0);

  return (
    <div>
      <p>Valor: {contador}</p>
      <button onClick={() => setContador(contador + 1)}>Sumar</button>
    </div>
  );
}
```

Qué pasa:

- useState(0) → crea una cajita de datos que empieza en 0.

- contador → el valor actual.

- setContador → función para cambiar el valor.

- Cuando llamas setContador, React vuelve a renderizar el componente con el valor nuevo.

## Otro muy útil: useEffect

Sirve para hacer algo cuando pase un evento en el ciclo de vida del componente
(por ejemplo: al montar el componente, al cambiar un valor o al desmontarse).

```
import { useState, useEffect } from "react";

function Reloj() {
  const [hora, setHora] = useState(new Date());

  useEffect(() => {
    const timer = setInterval(() => {
      setHora(new Date());
    }, 1000);

    return () => clearInterval(timer); // Limpieza al desmontar
  }, []);

  return <p>Hora actual: {hora.toLocaleTimeString()}</p>;
}
```

Qué pasa:

- ```useEffect(() => {...}, [])``` → se ejecuta al montar el componente.

- Creamos un intervalo que actualiza la hora cada segundo.

- React vuelve a renderizar cada vez que hora cambia.

## Otros Hooks Comunes

- useContext → compartir datos entre componentes sin pasarlos manualmente por props.

- useRef → guardar valores que no necesitan volver a renderizar el componente.

- useReducer → manejar estados más complejos (como un mini Redux).

- useMemo / useCallback → optimizar rendimiento.

## Resumen

- Hooks = funciones especiales de React.

- Empiezan siempre con use (useState, useEffect, etc.).

- Te permiten usar estado, efectos secundarios y otras características sin clases.

- Son la base para que tus componentes sean interactivos y dinámicos.