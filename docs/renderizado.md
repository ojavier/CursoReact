---
id: renderizado
title: Renderizado
sidebar_position: 5
---

# Renderizado

## Renderizado condicional

El renderizado condicional es mostrar algo u otra cosa dependiendo de una condición (como un “si pasa esto, muestra esto”).

Ejemplo simple:

```
function Mensaje({ estaLogueado }) {
  return (
    <div>
      {estaLogueado ? <h1>Bienvenido </h1> : <h1>Por favor inicia sesión </h1>}
    </div>
  );
}
```

- estaLogueado es true o false.

- Si es true → muestra “Bienvenido”.

- Si es false → muestra “Por favor inicia sesión”.

Uso:
```
<Mensaje estaLogueado={true} />   // Muestra "Bienvenido"
<Mensaje estaLogueado={false} />  // Muestra "Por favor inicia sesión"

```

## Renderizado de listas

Si tienes varios elementos (por ejemplo, una lista de nombres), no quieres escribir un < p > para cada uno.
React te deja recorrer la lista y crear un elemento para cada item.

Ejemplo:

```
function ListaDeNombres() {
  const nombres = ["Ana", "Luis", "María"];

  return (
    <ul>
      {nombres.map((nombre, index) => (
        <li key={index}>{nombre}</li>
      ))}
    </ul>
  );
}
```

- nombres.map(...) recorre la lista.

- Por cada nombre, crea un < li >.

- ```key =  { "index" }``` es importante para que React sepa cuál elemento es cuál (ayuda a que la página se actualice eficientemente).

Esto mostraría en pantalla:

```
• Ana
• Luis
• María
```

## Uso de ambos

Puedes combinar condicionales + listas para hacer algo más útil.

Por ejemplo, mostrar una lista solo si hay elementos:

```
function ListaDeTareas({ tareas }) {
  return (
    <div>
      {tareas.length > 0 ? (
        <ul>
          {tareas.map((tarea, index) => (
            <li key={index}>{tarea}</li>
          ))}
        </ul>
      ) : (
        <p>No hay tareas pendientes 🎉</p>
      )}
    </div>
  );
}
```

Uso:

```
<ListaDeTareas tareas={["Estudiar React", "Hacer la cena"]} />
<ListaDeTareas tareas={[]} />
```
