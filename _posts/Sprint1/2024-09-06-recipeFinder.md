---
layout: post
title: Recipe Finder
courses: {'csa': {'week': 1}}
type: ccc
comments: True
permalink: /recipeFinder

---

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Recipe Finder</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f9f9f9;
            margin: 50px;
        }
        input {
            padding: 10px;
            font-size: 16px;
            width: 300px;
            margin-right: 10px;
            border: 1px solid #ccc;
        }
        button {
            padding: 10px 20px;
            font-size: 16px;
            background-color: #28a745;
            color: white;
            border: none;
            cursor: pointer;
        }
        button:hover {
            background-color: #218838;
        }
        .recipe {
            margin-top: 20px;
        }
        .recipe h2 {
            color: #333;
        }
        .recipe p {
            color: #555;
        }
    </style>
</head>
<body>
    <h1>Recipe Finder</h1>
    <input type="text" id="ingredientInput" placeholder="Enter an ingredient">
    <button onclick="findRecipes()">Find Recipes</button>

    <div id="results"></div>

    <script>
        const recipes = [
            { name: 'Pasta Carbonara', ingredients: ['pasta', 'eggs', 'parmesan', 'bacon'] },
            { name: 'Guacamole', ingredients: ['avocado', 'lime', 'salt', 'onion'] },
            { name: 'Tomato Soup', ingredients: ['tomato', 'onion', 'garlic', 'basil'] },
            { name: 'Chocolate Cake', ingredients: ['flour', 'sugar', 'cocoa', 'butter'] }
        ];

        function findRecipes() {
            const ingredient = document.getElementById('ingredientInput').value.toLowerCase();
            const resultsDiv = document.getElementById('results');
            resultsDiv.innerHTML = '';

            const matchingRecipes = recipes.filter(recipe => 
                recipe.ingredients.some(ing => ing.toLowerCase().includes(ingredient))
            );

            if (matchingRecipes.length > 0) {
                matchingRecipes.forEach(recipe => {
                    const recipeDiv = document.createElement('div');
                    recipeDiv.classList.add('recipe');
                    recipeDiv.innerHTML = `<h2>${recipe.name}</h2><p>Ingredients: ${recipe.ingredients.join(', ')}</p>`;
                    resultsDiv.appendChild(recipeDiv);
                });
            } else {
                resultsDiv.innerHTML = '<p>No recipes found.</p>';
            }
        }
    </script>
</body>
</html>
