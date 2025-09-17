---
title: Lab 1
sidebar_position: 1
---

# Laboratorio: Construyendo un Recetario con React

## Componentes reutilizables

En este laboratorio aprenderás a construir una pequeña aplicación web utilizando React, enfocándote en el uso de componentes, props y renderizado de listas.

El objetivo principal es comprender cómo dividir una aplicación en piezas reutilizables y cómo estas piezas pueden comunicarse entre sí para formar una interfaz completa.

A continucación se presentarán ideas de componentes y estructuras, pero tengan la libertad de hacer la aplicación a su gusto.


## Crear la estructura base (App)

En App.js (o App.jsx) colocamos los componentes principales.

Algo así:

```
function App() {
  return (
    <div>
      <Header />
      <RecipeList />
      <Footer />
    </div>
  );
}
```

## Crea el componente Header

```
function Header() {
  return <h1>Mi Recetario</h1>;
}
```

## Crea el componente RecipeCard

```
function RecipeCard({ title, description, image }) {
  return (
    <div style={{ border: "1px solid #ccc", padding: "1rem", margin: "1rem" }}>
      <h2>{title}</h2>
      <img src={image} alt={title} width="200" />
      <p>{description}</p>
    </div>
  );
}
```