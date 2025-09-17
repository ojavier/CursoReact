---
title: Lab 2
sidebar_position: 2
---

# Laboratorio: Agregando Interactividad al Recetario con React

En este segundo laboratorio aprenderás a darle vida a los componentes de tu recetario. Hasta ahora, tus recetas se muestran de manera estática; en esta práctica, incorporarás interactividad usando eventos y estados (hooks).

Con ello, podrás reaccionar a las acciones del usuario (como dar clic en un botón) y actualizar la pantalla automáticamente.

A continucación se presentarán ideas de componentes y estructuras, pero tengan la libertad de hacer la aplicación a su gusto.

## RecipeCard con Likes

Cada tarjeta de receta tiene su propio contador de “likes”. Cada vez que das clic, el estado cambia y React actualiza el número automáticamente.

```
import { useState } from "react";

function RecipeCard({ title, description }) {
  // Estado para los likes
  const [likes, setLikes] = useState(0);

  // Función que aumenta likes
  const handleLike = () => {
    setLikes(likes + 1);
  };

  return (
    <div className="border p-4 rounded-lg shadow-md mb-4">
      <h2 className="text-xl font-bold">{title}</h2>
      <p>{description}</p>
      
      <button 
        onClick={handleLike}
        className="bg-blue-500 text-white px-3 py-1 rounded mt-2"
      >
        👍 Me gusta ({likes})
      </button>
    </div>
  );
}

export default RecipeCard;
```

## RecipeList con Formulario para Agregar Nuevas Recetas

Esto debería:

- Llenar el formulario con una nueva receta.

- Al enviar, la receta se agrega a la lista sin recargar la página.

- React vuelve a renderizar y muestra la nueva receta.

```
import { useState } from "react";
import RecipeCard from "./RecipeCard";

function RecipeList() {
  // Estado con las recetas iniciales
  const [recipes, setRecipes] = useState([
    { title: "Spaghetti Bolognese", description: "Pasta con salsa de tomate y carne." },
    { title: "Tacos al Pastor", description: "Tortilla con carne marinada, piña y salsa." }
  ]);

  // Estado para los inputs del formulario
  const [newTitle, setNewTitle] = useState("");
  const [newDescription, setNewDescription] = useState("");

  // Función que agrega nueva receta
  const handleAddRecipe = (e) => {
    e.preventDefault(); // Evita recargar la página

    // Crear objeto receta
    const newRecipe = { title: newTitle, description: newDescription };

    // Agregar receta al arreglo
    setRecipes([...recipes, newRecipe]);

    // Limpiar inputs
    setNewTitle("");
    setNewDescription("");
  };

  return (
    <div className="p-4">
      <h1 className="text-2xl font-bold mb-4">📖 Recetario</h1>

      {/* Formulario para nueva receta */}
      <form onSubmit={handleAddRecipe} className="mb-6">
        <input
          type="text"
          placeholder="Nombre de la receta"
          value={newTitle}
          onChange={(e) => setNewTitle(e.target.value)}
          className="border p-2 mr-2 rounded"
          required
        />
        <input
          type="text"
          placeholder="Descripción"
          value={newDescription}
          onChange={(e) => setNewDescription(e.target.value)}
          className="border p-2 mr-2 rounded"
          required
        />
        <button 
          type="submit"
          className="bg-green-500 text-white px-3 py-1 rounded"
        >
          ➕ Agregar
        </button>
      </form>

      {/* Lista de recetas */}
      {recipes.map((recipe, index) => (
        <RecipeCard 
          key={index}
          title={recipe.title}
          description={recipe.description}
        />
      ))}
    </div>
  );
}

export default RecipeList;
```