---
id: instalacion
title: Instalación
sidebar_position: 3
---

# Instalar en Proyecto React con Vite, ESLint y TailwindCSS
Se creará un proyecto con React con Vite, ESLint y TailwindCSS, para ello debemos seguir los siguientes pasos

## Iniciar Proyecto React + Vite

# Crear el proyecto con Vite
```
npm create vite@latest
```

Deja esta configuración para inicializar Vite con JavaScript y React, coloca el nombre de proyecto y paquete que quieras
![Inicializar Vite](/img/inicio.jpeg)

# Instalar dependencias
```
npm install
```

## Instalar ESLint
npm install -D eslint eslint-config-google eslint-plugin-react eslint-plugin-jsx-a11y eslint-plugin-import

### Iniciar configuración interactiva
```
npx eslint --init
npx eslint src
```

## Iniciar Tailwind
Es importante instalar Tailwind en el proyecto para una experiencia más completa en pryectos de React debido a las funciones avanzadas

```
npm install -D tailwindcss postcss autoprefixer
```

### Iniciar configuración interactiva
```
npx tailwindcss init -p
```

### Configura Tailwind en el proyecto
Es necesario configurar los archivos tailwind.config.js y postcss.config.js, si no los tienes créalos, pero verifica que se encuentren en tu package.json

Cóloca el código indicado en los archivos

### tailwind.config.js
```
/** @type {import('tailwindcss').Config} */
export default {
  content: [
    "./index.html",
    "./src/**/*.{js,ts,jsx,tsx}",
  ],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

### postcss.config.js
```
export default {
  plugins: {
    '@tailwindcss/postcss': {},
    autoprefixer: {},
  },
}
```

### Colóca esto en index.css
```
@tailwind base;
@tailwind components;
@tailwind utilities;
```