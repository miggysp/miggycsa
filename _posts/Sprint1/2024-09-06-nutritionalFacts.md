---
layout: post
title: Nutritional Facts
courses: {'csa': {'week': 1}}
type: ccc
comments: True
permalink: /nutritionalFacts

---
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Nutritional Facts Finder</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #f4f4f9;
            padding: 40px;
        }
        h1 {
            text-align: center;
            color: #333;
        }
        label {
            font-size: 18px;
            margin-right: 10px;
        }
        select {
            width: 100%;
            padding: 12px;
            font-size: 16px;
            margin-bottom: 20px;
        }
        button {
            background-color: #4CAF50;
            color: white;
            padding: 12px 20px;
            border: none;
            font-size: 18px;
            cursor: pointer;
            width: 100%;
        }
        button:hover {
            background-color: #45a049;
        }
        .nutritional-facts {
            margin-top: 30px;
        }
        .fact {
            background-color: #fff;
            padding: 20px;
            margin: 10px 0;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            border-radius: 8px;
        }
        .fact h2 {
            margin-bottom: 10px;
            color: #333;
        }
        .fact p {
            font-size: 16px;
            color: #555;
        }
    </style>
</head>
<body>

    <h1>Nutritional Facts Finder</h1>
    <label for="foodItem">Select a food item:</label>
    <select id="foodItem">
        <option value="apple">Apple</option>
        <option value="banana">Banana</option>
        <option value="chicken_breast">Chicken Breast</option>
        <option value="salmon">Salmon</option>
        <option value="avocado">Avocado</option>
        <option value="broccoli">Broccoli</option>
        <option value="egg">Egg</option>
    </select>
    <button onclick="displayNutritionalFacts()">Get Nutritional Facts</button>

    <div class="nutritional-facts" id="nutritionalFacts"></div>

    <script>
        const nutritionalData = {
            apple: {
                name: 'Apple',
                calories: 95,
                protein: '0.5g',
                carbs: '25g',
                fat: '0.3g',
                fiber: '4.4g',
                sugar: '19g'
            },
            banana: {
                name: 'Banana',
                calories: 105,
                protein: '1.3g',
                carbs: '27g',
                fat: '0.4g',
                fiber: '3.1g',
                sugar: '14g'
            },
            chicken_breast: {
                name: 'Chicken Breast (100g)',
                calories: 165,
                protein: '31g',
                carbs: '0g',
                fat: '3.6g',
                fiber: '0g',
                sugar: '0g'
            },
            salmon: {
                name: 'Salmon (100g)',
                calories: 208,
                protein: '20g',
                carbs: '0g',
                fat: '13g',
                fiber: '0g',
                sugar: '0g'
            },
            avocado: {
                name: 'Avocado (100g)',
                calories: 160,
                protein: '2g',
                carbs: '9g',
                fat: '15g',
                fiber: '7g',
                sugar: '0.7g'
            },
            broccoli: {
                name: 'Broccoli (100g)',
                calories: 55,
                protein: '3.7g',
                carbs: '11g',
                fat: '0.6g',
                fiber: '3.8g',
                sugar: '2.6g'
            },
            egg: {
                name: 'Egg (1 large)',
                calories: 70,
                protein: '6g',
                carbs: '1g',
                fat: '5g',
                fiber: '0g',
                sugar: '1g'
            }
        };

        function displayNutritionalFacts() {
            const foodItem = document.getElementById('foodItem').value;
            const nutritionalFactsDiv = document.getElementById('nutritionalFacts');
            nutritionalFactsDiv.innerHTML = '';

            const selectedFood = nutritionalData[foodItem];

            const factDiv = document.createElement('div');
            factDiv.classList.add('fact');

            factDiv.innerHTML = `
                <h2>${selectedFood.name}</h2>
                <p>Calories: ${selectedFood.calories}</p>
                <p>Protein: ${selectedFood.protein}</p>
                <p>Carbs: ${selectedFood.carbs}</p>
                <p>Fat: ${selectedFood.fat}</p>
                <p>Fiber: ${selectedFood.fiber}</p>
                <p>Sugar: ${selectedFood.sugar}</p>
            `;

            nutritionalFactsDiv.appendChild(factDiv);
        }
    </script>
</body>
</html>
