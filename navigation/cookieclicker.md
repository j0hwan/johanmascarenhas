---
layout: page
title: cookieclicker
permalink: /cookieclicker/
---

# Cookie Clicker App 🍪


   

   <div style="text-align: center;">
    <h2>Score: <span id="score">0</span></h2>
    <h3>Upgrade Level: <span id="level">0</span></h3>
    <canvas id="gameCanvas" width="300" height="300" style="border: 2px solid black;"></canvas>
    <br>
    <div id="clickFeedback" style="position: relative; height: 100px; overflow: hidden;"></div>
    <button id="upgradeButton" style="font-size: 20px; padding: 10px 20px; background-color: #3498db; color: white; border: none; border-radius: 10px; cursor: pointer;">Buy Upgrade (Cost: 100 Points)</button>
    <h3>Tools</h3>
    <button id="tool1" style="font-size: 16px; padding: 10px 15px; margin: 5px;" onclick="buyTool(1)">Buy Wooden Spoon (100 points)</button>
    <button id="tool2" style="font-size: 16px; padding: 10px 15px; margin: 5px;" onclick="buyTool(2)">Buy Plastic Spatula (499 points)</button>
    <button id="tool3" style="font-size: 16px; padding: 10px 15px; margin: 5px;" onclick="buyTool(3)">Buy Iron Mixer (1500 points)</button>
    <button id="tool4" style="font-size: 16px; padding: 10px 15px; margin: 5px;" onclick="buyTool(4)">Buy Golden Whisk (14,000 points)</button>
    <button id="tool5" style="font-size: 16px; padding: 10px 15px; margin: 5px;" onclick="buyTool(5)">Buy Diamond Oven (30,000 points)</button>
    <p id="tool">No tool equipped</p>
</div>

<script>
    const canvas = document.getElementById('gameCanvas');
    const ctx = canvas.getContext('2d');
    const cookie = new Image();
    cookie.src = 'https://www.inkatrinaskitchen.com/wp-content/uploads/2011/04/Cookie-Monster-Cookies.jpg'; // Replace with actual cookie image URL
    let score = 0;
    let upgradeLevel = 0;
    let tools = ['Wooden Spoon', 'Plastic Spatula', 'Iron Mixer', 'Golden Whisk', 'Diamond Oven'];
    let toolIndex = 0;
    let pointsPerClick = 1;
    let toolCosts = [100, 499, 1500, 14000, 30000];

    document.getElementById('upgradeButton').addEventListener('click', buyUpgrade);
    canvas.addEventListener('mousedown', cookieClicked);
    canvas.addEventListener('mouseup', resetCookieSize);
    document.addEventListener('keydown', cheatCode);

    function cookieClicked() {
        if (score >= 100000) {
            alert("Game Over! You've reached 100,000 points!");
            return;
        }
        score += pointsPerClick;
        document.getElementById('score').innerText = score;
        drawCookie(250);  // Make the cookie small when clicked
        showClickFeedback(`+${pointsPerClick}`);
    }

    function resetCookieSize() {
        drawCookie(300);  // Reset the cookie to full size
    }

    function drawCookie(size) {
        ctx.clearRect(0, 0, canvas.width, canvas.height);
        ctx.drawImage(cookie, (canvas.width - size) / 2, (canvas.height - size) / 2, size, size);
    }

    function showClickFeedback(text) {
        const feedbackDiv = document.createElement('div');
        feedbackDiv.innerText = text;
        feedbackDiv.style.position = 'absolute';
        feedbackDiv.style.right = '0';
        feedbackDiv.style.color = '#3498db';
        feedbackDiv.style.fontSize = '18px';
        feedbackDiv.style.opacity = '1';
        feedbackDiv.style.transition = 'opacity 3s ease';
        
        document.getElementById('clickFeedback').appendChild(feedbackDiv);
        
        setTimeout(() => {
            feedbackDiv.style.opacity = '0';
            setTimeout(() => feedbackDiv.remove(), 3000);  // Remove after fading out
        }, 3000);  // Visible for 3 seconds
    }

    function buyUpgrade() {
        if (score >= 100 * (upgradeLevel + 1)) {
            score -= 100 * (upgradeLevel + 1);
            upgradeLevel++;
            document.getElementById('score').innerText = score;
            document.getElementById('level').innerText = upgradeLevel;
            pointsPerClick += 2;  // Increase base points per click with each upgrade

            if (upgradeLevel === 15) {
                document.getElementById('upgradeButton').disabled = true;
                alert("Max upgrade reached! Keep clicking to reach 100,000 points!");
            }
        }
    }

    function buyTool(tool) {
        if (score >= toolCosts[tool - 1]) {
            score -= toolCosts[tool - 1];
            document.getElementById('score').innerText = score;
            pointsPerClick += tool * 5;  // Make tools more powerful
            toolIndex = tool - 1;
            document.getElementById('tool').innerText = `Tool: ${tools[toolIndex]}`;
            document.getElementById(`tool${tool}`).disabled = true;  // Disable button after purchase
        } else {
            alert("Not enough points to buy this tool!");
        }
    }

    function cheatCode(event) {
        if (event.key === 'A' && event.getModifierState('Alt')) {
            score += 20000;
            document.getElementById('score').innerText = score;
        }
    }

    drawCookie(300);  // Initial cookie size
</script>

<style>
    canvas {
        display: block;
        margin: 20px auto;
        background-color: #f3f3f3;
    }

    button {
        margin-top: 10px;
    }

    #clickFeedback {
        display: flex;
        flex-direction: column;
        align-items: flex-end;
    }
</style>