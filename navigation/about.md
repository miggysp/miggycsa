---
layout: default
title: Miheer's Blog
remote_theme: pages-themes/hacker@v0.2.0
---

<style>
    body {
        background-color: #FFFFFF;
    }
    h1#miheers-page {
        color: orange;
        font-size: 45px;
        text-align: center;
    }
    p {
        color: black;
    }
    #name-game {
        text-align: center;
        margin-top: 20px;
    }
    #name-display {
        font-size: 24px;
        letter-spacing: 10px;
        font-weight: bold;
    }
    button, input[type="text"] {
        padding: 10px 20px;
        font-size: 16px;
        margin-top: 10px;
    }
</style>

# Home Page

About Me: My name is Miheer Purandare, and I am a 17-year-old at Del Norte High School. I have a dog named Rocket. 
My parents are both from India. 
I like to do research, watch TV, and hang out with friends in my spare time. 
I want to major in chemical engineering.

<iframe src="https://drive.google.com/file/d/1-wVrNJWQ5Av8EdP_k87PLYBhbdOmydOB/preview" width="640" height="480" allow="autoplay"></iframe>

<iframe src="https://drive.google.com/file/d/1T1lqAw7zh96hbypKbV8AYj4po3tgPj5F/preview" width="640" height="480" allow="autoplay"></iframe>

## Can You Guess My Favorite Food?

<div id="name-game">
    <h2>Can you guess my favorite food?</h2>
    <p id="hint">Hint: It's something cheesy and popular.</p>
    <input type="text" id="name-input" placeholder="Type your guess here...">
    <br>
    <button onclick="checkFood()">Submit</button>
    <p id="response"></p>
</div>

<script>
    const favoriteFood = "pizza";
    let attempts = 0;

    function checkFood() {
        const userGuess = document.getElementById("name-input").value.trim();
        const response = document.getElementById("response");
        const hint = document.getElementById("hint");
        
        if (userGuess.toLowerCase() === favoriteFood.toLowerCase()) {
            response.innerHTML = "Good job! You guessed it right!";
            hint.style.display = "none";
        } else {
            attempts++;
            response.innerHTML = "Not quite, try again!";
            hint.innerHTML = getHint(attempts);
        }
    }

    function getHint(attempts) {
        switch(attempts) {
            case 1:
                return "Hint: It often comes with pepperoni or veggies on top.";
            case 2:
                return "Hint: You can get it from places like Domino's or Pizza Hut.";
            default: 
                return " "
        }
    }
</script>
