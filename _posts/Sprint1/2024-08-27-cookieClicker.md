---
layout: post
title: Cookie Clicker
courses: {'csa': {'week': 2}}
type: ccc
comments: True
---
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Fancy Cookie Clicker</title>
    <style>
        body {
            text-align: center;
            font-family: 'Segoe UI', Arial, sans-serif;
            background-color: #f5f5f5;
            background-image: url('https://i.imgur.com/u3TPBOP.jpg');
            background-size: cover;
            color: #333;
        }
        img {
            cursor: pointer;
            width: 300px;
            transition: transform 0.1s;
        }
        img:hover {
            transform: scale(1.1);
        }
        .score {
            font-size: 24px;
            margin: 20px;
            background-color: rgba(255, 255, 255, 0.7);
            padding: 10px;
            border-radius: 10px;
            display: inline-block;
        }
        .shop {
            background-color: rgba(255, 255, 255, 0.9);
            padding: 20px;
            border-radius: 15px;
            width: 300px;
            margin: 20px auto;
        }
        .shop h2 {
            margin-bottom: 15px;
            font-size: 22px;
        }
        .shop-item {
            display: flex;
            justify-content: space-between;
            margin: 10px 0;
            font-size: 18px;
        }
        button {
            background-color: #4CAF50;
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 5px;
            cursor: pointer;
            transition: background-color 0.2s;
        }
        button:hover {
            background-color: #45a049;
        }
        .achievements {
            margin-top: 30px;
            background-color: rgba(255, 255, 255, 0.9);
            padding: 15px;
            border-radius: 15px;
            width: 300px;
            margin: 20px auto;
        }
        .achievement {
            margin-bottom: 10px;
            font-size: 16px;
        }
    </style>
</head>
<body>
    <h1>Fancy Cookie Clicker</h1>
    <p class="score">Cookies: <span id="score">0</span></p>
    <img id="cookie" src="/miggycsa/images/cookieclicker.png" alt="cookie"> 
    <audio id="clickSound" src="/miggycsa/click1.mp3"></audio>

    <!-- Shop Section -->
    <div class="shop">
        <h2>Shop</h2>
        <div class="shop-item">
            <span>Worker: 100 cookies</span>
            <button id="buyWorker">Buy Worker</button>
        </div>
        <div class="shop-item">
            <span>Oven: 500 cookies</span>
            <button id="buyOven">Buy Oven</button>
        </div>
        <div class="shop-item">
            <span>Cookie Factory: 1000 cookies</span>
            <button id="buyFactory">Buy Factory</button>
        </div>
        <p>Each worker adds 1 cookie per click</p>
        <p>Ovens add 5 cookies per second</p>
        <p>Factories add 20 cookies per second</p>
    </div>

    <!-- Achievements Section -->
    <div class="achievements">
        <h2>Achievements</h2>
        <div class="achievement" id="achievement1" style="display:none;">🎉 100 Cookies - Nice Start!</div>
        <div class="achievement" id="achievement2" style="display:none;">🎉 500 Cookies - Getting there!</div>
        <div class="achievement" id="achievement3" style="display:none;">🎉 1000 Cookies - Cookie Master!</div>
    </div>

    <script>
        let score = 0;
        let cookiesPerClick = 1;
        let workers = 0;
        let ovens = 0;
        let factories = 0;
        let cookiesPerSecond = 0;

        document.getElementById('cookie').addEventListener('click', () => {
            score += cookiesPerClick;
            document.getElementById('score').innerText = score;
            document.getElementById('clickSound').play();
            checkAchievements();
        });

        document.getElementById('buyWorker').addEventListener('click', () => {
            if (score >= 100) {
                score -= 100;
                workers++;
                cookiesPerClick = 1 + workers;
                document.getElementById('score').innerText = score;
            }
        });

        document.getElementById('buyOven').addEventListener('click', () => {
            if (score >= 500) {
                score -= 500;
                ovens++;
                cookiesPerSecond += 5;
                document.getElementById('score').innerText = score;
            }
        });

        document.getElementById('buyFactory').addEventListener('click', () => {
            if (score >= 1000) {
                score -= 1000;
                factories++;
                cookiesPerSecond += 20;
                document.getElementById('score').innerText = score;
            }
        });

        setInterval(function() {
            score += cookiesPerSecond;
            document.getElementById('score').innerText = score;
            checkAchievements();
        }, 1000);

        function checkAchievements() {
            if (score >= 100) {
                document.getElementById('achievement1').style.display = 'block';
            }
            if (score >= 500) {
                document.getElementById('achievement2').style.display = 'block';
            }
            if (score >= 1000) {
                document.getElementById('achievement3').style.display = 'block';
            }
        }
    </script>
</body>
</html>
