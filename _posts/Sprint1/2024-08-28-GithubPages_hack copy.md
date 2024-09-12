---
layout: post
title: Github Pages Hack
courses: {'csa': {'week': 1}}
type: ccc
comments: True
---

<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cooking Submenu</title>
    <style>
        /* Styling for the submenu */
        .submenu {
            display: flex;
            justify-content: center;
            background-color: #f8f9fa;
            padding: 10px;
        }
        .submenu a {
            margin: 0 15px;
            text-decoration: none;
            color: #007bff;
            font-weight: bold;
        }
        .submenu a:hover {
            color: #0056b3;
            text-decoration: underline;
        }
    </style>
</head>

<body>

    <!-- Submenu navigation -->
    <div class="submenu">
        <a href="/miggycsa/recipeFinder">Recipe Finder</a>
        <a href="/miggycsa/mealPlanner">Meal Planner</a>
        <a href="/miggycsa/nutritionalFacts">Nutritional Facts</a>
        <a href="/miggycsa/cookingTips">Cooking Tips</a>
    </div>

    <!-- Example content for the main page -->
    <h1>Welcome to the Cooking Submenu!</h1>
    <p>Select an option above to start exploring delicious recipes and more.</p>

    <!-- Utteranc.es comment section -->
    <script src="https://utteranc.es/client.js"
        repo="miggysp/miggycsa"
        issue-term="pathname"
        theme="github-light"
        crossorigin="anonymous"
        async>
    </script>

</body>

</html>

