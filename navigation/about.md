---
layout: default
title: Miheer's Blog
remote_theme: pages-themes/hacker@v0.2.0
---
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
    #name-game, #hobby-game, #tv-show-game {
        text-align: center;
        margin-top: 20px;
    }
    .game-display {
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

## Can You Guess My Favorite Hobby?

<div id="hobby-game">
    <h2>Can you guess my favorite hobby?</h2>
    <p id="hobby-hint">Hint: It's something that can involve a lot of information and critical thinking.</p>
    <input type="text" id="hobby-input" placeholder="Type your guess here...">
    <br>
    <button onclick="checkHobby()">Submit</button>
    <p id="hobby-response"></p>
</div>

## Can You Guess My Favorite TV Show?

<div id="tv-show-game">
    <h2>Can you guess my favorite TV show?</h2>
    <p id="tv-hint">Hint: It's a popular Netflix show with a lot of action and mystery.</p>
    <input type="text" id="tv-input" placeholder="Type your guess here...">
    <br>
    <button onclick="checkTVShow()">Submit</button>
    <p id="tv-response"></p>
</div>

<script>
    const favoriteFood = "pizza";
    const favoriteHobby = "research";
    const favoriteTVShow = "stranger things";
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
            hint.innerHTML = getFoodHint(attempts);
        }
    }

    function getFoodHint(attempts) {
        switch(attempts) {
            case 1:
                return "Hint: It often comes with pepperoni or veggies on top.";
            case 2:
                return "Hint: You can get it from places like Domino's or Pizza Hut.";
            case 3: 
                return "Hint: There are 2 z's in the word.";
            case 4: 
                return "Hint: It is shaped like a triangle."; 
            default: 
                return "No more hints for you.";
        }
    }

    function checkHobby() {
        const userGuess = document.getElementById("hobby-input").value.trim();
        const response = document.getElementById("hobby-response");
        const hint = document.getElementById("hobby-hint");

        if (userGuess.toLowerCase() === favoriteHobby.toLowerCase()) {
            response.innerHTML = "Well done! You guessed my favorite hobby!";
            hint.style.display = "none";
        } else {
            attempts++;
            response.innerHTML = "Not quite, try again!";
            hint.innerHTML = getHobbyHint(attempts);
        }
    }

    function getHobbyHint(attempts) {
        switch(attempts) {
            case 1:
                return "Hint: It is usually done in a library or lab setting.";
            case 2:
                return "Hint: It involves a lot of reading and exploring new ideas.";
            case 3: 
                return "Hint: This hobby is essential for students and scientists.";
            default: 
                return "No more hints for you.";
        }
    }

    function checkTVShow() {
        const userGuess = document.getElementById("tv-input").value.trim();
        const response = document.getElementById("tv-response");
        const hint = document.getElementById("tv-hint");

        if (userGuess.toLowerCase() === favoriteTVShow.toLowerCase()) {
            response.innerHTML = "Awesome! You guessed it!";
            hint.style.display = "none";
        } else {
            attempts++;
            response.innerHTML = "Nope, try again!";
            hint.innerHTML = getTVShowHint(attempts);
        }
    }

    function getTVShowHint(attempts) {
        switch(attempts) {
            case 1:
                return "Hint: It features a group of kids facing off against strange creatures.";
            case 2:
                return "Hint: One of the main characters has psychokinetic abilities.";
            case 3: 
                return "Hint: The story is set in the 1980s.";
            default: 
                return "No more hints for you.";
        }
    }
</script>
