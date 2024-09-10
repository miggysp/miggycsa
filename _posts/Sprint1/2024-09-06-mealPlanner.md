---
layout: post
title: Meal Planner
courses: {'csa': {'week': 1}}
type: ccc
comments: True
permalink: /mealPlanner

---
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Advanced Meal Planner</title>
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
        input[type="range"] {
            width: 100%;
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
        .meal-planner {
            margin-top: 30px;
        }
        .meal {
            background-color: #fff;
            padding: 20px;
            margin: 10px 0;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            border-radius: 8px;
        }
        .meal h2 {
            margin-bottom: 10px;
            color: #333;
        }
        .nutrition {
            margin-top: 10px;
            color: #555;
        }
        .nutrition span {
            display: block;
            font-size: 16px;
        }
    </style>
</head>
<body>

    <h1>Advanced Meal Planner</h1>
    <label for="hungerLevel">How hungry are you?</label>
    <input type="range" id="hungerLevel" min="1" max="5" value="3" step="1" oninput="displayHungerLevel()">
    <p id="hungerDisplay">Moderately Hungry</p>
    <button onclick="generateMealPlan()">Generate Meal Plan</button>

    <div class="meal-planner" id="mealPlanner"></div>

    <script>
        const meals = {
            1: [
                { name: 'Fruit Salad', protein: 2, carbs: 20, fat: 0.5 },
                { name: 'Greek Yogurt with Honey', protein: 10, carbs: 15, fat: 3 },
                { name: 'Vegetable Soup', protein: 3, carbs: 8, fat: 1 }
            ],
            2: [
                { name: 'Egg Whites & Spinach', protein: 15, carbs: 5, fat: 2 },
                { name: 'Grilled Veggie Wrap', protein: 10, carbs: 20, fat: 5 },
                { name: 'Chicken Caesar Salad', protein: 30, carbs: 8, fat: 10 }
            ],
            3: [
                { name: 'Grilled Chicken Salad', protein: 40, carbs: 10, fat: 15 },
                { name: 'Turkey Sandwich on Whole Grain', protein: 25, carbs: 40, fat: 7 },
                { name: 'Quinoa & Black Bean Bowl', protein: 18, carbs: 45, fat: 8 }
            ],
            4: [
                { name: 'Steak with Sweet Potato', protein: 50, carbs: 30, fat: 20 },
                { name: 'Salmon with Brown Rice', protein: 45, carbs: 35, fat: 25 },
                { name: 'Chicken Alfredo', protein: 35, carbs: 50, fat: 30 }
            ],
            5: [
                { name: 'Burger & Fries', protein: 30, carbs: 55, fat: 35 },
                { name: 'BBQ Ribs & Mashed Potatoes', protein: 60, carbs: 40, fat: 50 },
                { name: 'Fettuccine Carbonara', protein: 40, carbs: 65, fat: 45 }
            ]
        };

        function displayHungerLevel() {
            const hungerLevel = document.getElementById('hungerLevel').value;
            const hungerDisplay = document.getElementById('hungerDisplay');
            const hungerStates = ['Not Hungry', 'Slightly Hungry', 'Moderately Hungry', 'Very Hungry', 'Starving'];
            hungerDisplay.textContent = hungerStates[hungerLevel - 1];
        }

        function generateMealPlan() {
            const hungerLevel = document.getElementById('hungerLevel').value;
            const mealPlannerDiv = document.getElementById('mealPlanner');
            mealPlannerDiv.innerHTML = '';

            const selectedMeals = meals[hungerLevel]; // Selecting meals based on hunger level.

            selectedMeals.forEach(meal => {
                const mealDiv = document.createElement('div');
                mealDiv.classList.add('meal');

                mealDiv.innerHTML = `
                    <h2>${meal.name}</h2>
                    <div class="nutrition">
                        <span>Protein: ${meal.protein}g</span>
                        <span>Carbs: ${meal.carbs}g</span>
                        <span>Fats: ${meal.fat}g</span>
                    </div>
                `;

                mealPlannerDiv.appendChild(mealDiv);
            });
        }
    </script>
</body>
</html>
