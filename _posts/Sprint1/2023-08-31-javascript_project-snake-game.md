---
layout: post
title: Snake Game
permalink: /snake
courses: {'csa': {'week': 2}}
type: ccc
comments: false
---
I added event.preventDefault() to the keydown event listener to prevent the page from scrolling when using the arrow keys (ArrowLeft, ArrowRight, ArrowUp, and ArrowDown) to control the snake.

Also added extra life & double points power up to make the game more interesting. 

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Snake Game with Power-Ups</title>
    <style>
        body {
            background-color: #2E2E2E;
            font-family: 'Arial', sans-serif;
            color: #FFFFFF;
            text-align: center;
        }

        canvas {
            background-color: #333;
            display: block;
            margin: 0 auto;
            border: 5px solid #FFF;
        }

        #score {
            font-size: 20px;
            margin-bottom: 10px;
        }

        #gameOver {
            display: none;
            font-size: 24px;
            color: #FF4500;
            margin-top: 20px;
        }
    </style>
</head>
<body>

    <div id="score">Score: 0 | Extra Lives: 0 | Double Points: No</div>
    <canvas id="gameCanvas" width="400" height="400"></canvas>
    <div id="gameOver">Game Over! Press Space to Restart</div>

    <script>
        const canvas = document.getElementById('gameCanvas');
        const ctx = canvas.getContext('2d');
        const scoreDisplay = document.getElementById('score');
        const gameOverDisplay = document.getElementById('gameOver');
        const blockSize = 20;
        const widthInBlocks = canvas.width / blockSize;
        const heightInBlocks = canvas.height / blockSize;
        let snake;
        let food;
        let powerUp;
        let direction;
        let newDirection;
        let score;
        let extraLives;
        let doublePoints;
        let doublePointsActive;
        let doublePointsTimer;
        let gameLoop;

        const initGame = () => {
            snake = [{ x: 10, y: 10 }];
            direction = 'right';
            newDirection = 'right';
            score = 0;
            extraLives = 0;
            doublePoints = false;
            doublePointsActive = false;
            doublePointsTimer = 0;
            placeFood();
            placePowerUp();
            gameOverDisplay.style.display = 'none';
            updateScoreDisplay();
            gameLoop = setInterval(gameStep, 100);
        };

        const placeFood = () => {
            food = {
                x: Math.floor(Math.random() * widthInBlocks),
                y: Math.floor(Math.random() * heightInBlocks)
            };
        };

        const placePowerUp = () => {  //This controls the placement of the power ups
            const randomChance = Math.random();
            if (randomChance < 0.3) {
                powerUp = {
                    x: Math.floor(Math.random() * widthInBlocks),
                    y: Math.floor(Math.random() * heightInBlocks),
                    type: 'extraLife'
                };
            } else if (randomChance < 0.6) {
                powerUp = {
                    x: Math.floor(Math.random() * widthInBlocks),
                    y: Math.floor(Math.random() * heightInBlocks),
                    type: 'doublePoints'
                };
            } else {
                powerUp = null;
            }
        };

        const drawBlock = (x, y, color) => {
            ctx.fillStyle = color;
            ctx.fillRect(x * blockSize, y * blockSize, blockSize, blockSize);
        };

        const drawSnake = () => {
            snake.forEach(segment => drawBlock(segment.x, segment.y, '#0F0'));
        };

        const drawFood = () => {
            drawBlock(food.x, food.y, '#F00');
        };

        const drawPowerUp = () => {
            if (powerUp) {
                if (powerUp.type === 'extraLife') {
                    drawBlock(powerUp.x, powerUp.y, '#00F');
                } else if (powerUp.type === 'doublePoints') {
                    drawBlock(powerUp.x, powerUp.y, '#FF0'); // Yellow for double points
                }
            }
        };

        const resetSnakeToCenter = () => { //function I made b/c the snake wasn't reseting to the middle it was just staying there
            snake = [{ x: Math.floor(widthInBlocks / 2), y: Math.floor(heightInBlocks / 2) }];
            direction = 'right';
            newDirection = 'right';
        };

        const gameStep = () => {
            const head = { ...snake[0] };

            switch (newDirection) {
                case 'left':
                    head.x -= 1;
                    break;
                case 'right':
                    head.x += 1;
                    break;
                case 'up':
                    head.y -= 1;
                    break;
                case 'down':
                    head.y += 1;
                    break;
            }

            direction = newDirection;

            if (head.x < 0 || head.x >= widthInBlocks || head.y < 0 || head.y >= heightInBlocks || snake.some(segment => segment.x === head.x && segment.y === head.y)) {
                if (extraLives > 0) { //EXTRA LIVES
                    extraLives--;
                    resetSnakeToCenter();
                    updateScoreDisplay();
                } else {
                    gameOver();
                    return;
                }
            } else {
                snake.unshift(head);

                if (head.x === food.x && head.y === food.y) { //Manages double points
                    score += doublePointsActive ? 2 : 1;
                    updateScoreDisplay();
                    placeFood();
                    placePowerUp();
                } else {
                    snake.pop();
                }

                if (powerUp && head.x === powerUp.x && head.y === powerUp.y) {
                    if (powerUp.type === 'extraLife') {
                        extraLives += 1;
                    } else if (powerUp.type === 'doublePoints') {
                        doublePointsActive = true;
                        doublePointsTimer = 100; // 100 game steps of double points //time for double points so it doesnt last forever
                    }
                    powerUp = null;
                    updateScoreDisplay();
                }
            }

            ctx.clearRect(0, 0, canvas.width, canvas.height);
            drawSnake();
            drawFood();
            drawPowerUp();

            if (doublePointsActive) {
                doublePointsTimer--;
                if (doublePointsTimer <= 0) {
                    doublePointsActive = false;
                }
                updateScoreDisplay();
            }
        };

        const updateScoreDisplay = () => {
            scoreDisplay.innerHTML = `Score: ${score} | Extra Lives: ${extraLives} | Double Points: ${doublePointsActive ? 'Yes' : 'No'}`;
        };

        const gameOver = () => {
            clearInterval(gameLoop);
            gameOverDisplay.style.display = 'block';
        };

        document.addEventListener('keydown', (event) => {
            if (['ArrowLeft', 'ArrowRight', 'ArrowUp', 'ArrowDown'].includes(event.code)) {
                event.preventDefault();
            }

            switch (event.code) {
                case 'ArrowLeft':
                    if (direction !== 'right') newDirection = 'left';
                    break;
                case 'ArrowRight':
                    if (direction !== 'left') newDirection = 'right';
                    break;
                case 'ArrowUp':
                    if (direction !== 'down') newDirection = 'up';
                    break;
                case 'ArrowDown':
                    if (direction !== 'up') newDirection = 'down';
                    break;
                case 'Space':
                    if (gameOverDisplay.style.display === 'block') initGame();
                    break;
            }
        });

        initGame();
    </script>

</body>
</html>
