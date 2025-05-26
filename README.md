<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mahmoud Selmy - GitHub Profile</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background-color: #f4f4f4;
            margin: 0;
            padding: 20px;
        }
        header h1 {
            font-size: 2.5em;
            color: #2c3e50;
            margin-bottom: 10px;
            font-family: 'Noto Naskh Arabic', Arial, sans-serif;
        }
        header p {
            font-size: 1.2em;
            color: #7f8c8d;
        }
        #game {
            margin: 20px auto;
            width: 80%;
            max-width: 600px;
            height: 200px;
            background: #ecf0f1;
            border: 2px solid #bdc3c7;
            position: relative;
            overflow: hidden;
        }
        #gameCanvas {
            width: 100%;
            height: 100%;
        }
        #languages, #social-links {
            margin: 20px 0;
        }
        #languages ul {
            list-style: none;
            padding: 0;
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
        }
        #languages li {
            margin: 10px;
            padding: 10px 20px;
            background: #3498db;
            color: white;
            border-radius: 5px;
            display: flex;
            align-items: center;
        }
        #languages img {
            width: 30px;
            height: 30px;
            margin-right: 10px;
        }
        #social-links a {
            margin: 0 15px;
        }
        #social-links img {
            width: 40px;
            height: 40px;
        }
    </style>
    <link href="https://fonts.googleapis.com/css2?family=Noto+Naskh+Arabic&display=swap" rel="stylesheet">
</head>
<body>
    <header>
        <h1>وَلَقَدْ مَنَنَّا عَلَيْكَ مَرَّةً أُخْرَىٰ (طه - 37)</h1>
        <p>A passionate Mobile Application developer from Egypt</p>
    </header>
    <section id="game">
        <canvas id="gameCanvas"></canvas>
        <p>Press space to jump!</p>
    </section>
    <section id="languages">
        <h2>Programming Languages & Technologies</h2>
        <ul>
            <li><img src="https://img.icons8.com/color/48/000000/dart.png" alt="Dart"> Dart</li>
            <li><img src="https://img.icons8.com/color/48/000000/flutter.png" alt="Flutter"> Flutter</li>
            <li><img src="https://img.icons8.com/color/48/000000/python.png" alt="Python"> Python</li>
            <li><img src="https://img.icons8.com/color/48/000000/linux.png" alt="Linux"> Linux</li>
            <li><img src="https://img.icons8.com/color/48/000000/android-os.png" alt="Android"> Android</li>
            <li><img src="https://img.icons8.com/color/48/000000/c-plus-plus-logo.png" alt="C++"> C++</li>
            <li><img src="https://img.icons8.com/color/48/000000/c-programming.png" alt="C"> C</li>
        </ul>
    </section>
    <section id="social-links">
        <h2>Connect with me</h2>
        <a href="https://www.youtube.com/@Ma7moudSelmy"><img src="https://img.icons8.com/color/48/000000/youtube-play.png" alt="YouTube"></a>
        <a href="https://www.linkedin.com/in/mahmoud-selmy-862162335"><img src="https://img.icons8.com/color/48/000000/linkedin.png" alt="LinkedIn"></a>
        <a href="https://codeforces.com/profile/Ma7moudSelmy1"><img src="https://img.icons8.com/external-tal-revivo-color-tal-revivo/48/000000/external-codeforces-a-russian-website-for-competitive-programming-color-tal-revivo.png" alt="Codeforces"></a>
    </section>
    <script>
        // Dinosaur Game Script
        const canvas = document.getElementById('gameCanvas');
        const ctx = canvas.getContext('2d');
        canvas.width = 600;
        canvas.height = 200;

        let dino = {
            x: 50,
            y: 150,
            width: 40,
            height: 40,
            dy: 0,
            gravity: 0.6,
            jumpPower: -12,
            isJumping: false
        };
        let cactus = {
            x: 600,
            y: 150,
            width: 20,
            height: 40,
            dx: -4
        };
        let gameOver = false;

        document.addEventListener('keydown', function(event) {
            if (event.code === 'Space' && !dino.isJumping && !gameOver) {
                dino.dy = dino.jumpPower;
                dino.isJumping = true;
            }
        });

        function update() {
            if (gameOver) return;

            // Update dino
            dino.dy += dino.gravity;
            dino.y += dino.dy;
            if (dino.y > 150) {
                dino.y = 150;
                dino.dy = 0;
                dino.isJumping = false;
            }

            // Update cactus
            cactus.x += cactus.dx;
            if (cactus.x < -cactus.width) {
                cactus.x = 600;
            }

            // Collision detection
            if (
                dino.x < cactus.x + cactus.width &&
                dino.x + dino.width > cactus.x &&
                dino.y < cactus.y + cactus.height &&
                dino.y + dino.height > cactus.y
            ) {
                gameOver = true;
                alert('Game Over! Refresh to play again.');
            }

            // Draw
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            ctx.fillStyle = '#2c3e50';
            ctx.fillRect(dino.x, dino.y, dino.width, dino.height); // Dino
            ctx.fillStyle = '#27ae60';
            ctx.fillRect(cactus.x, cactus.y, cactus.width, cactus.height); // Cactus
            ctx.fillStyle = '#7f8c8d';
            ctx.fillRect(0, 190, canvas.width, 10); // Ground

            requestAnimationFrame(update);
        }

        update();
    </script>
</body>
</html>
