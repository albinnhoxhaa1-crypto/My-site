# <!DOCTYPE html>
<html lang="sq">
<head>
    <meta charset="UTF-8">
    <title>Valentine ❤️</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #ffe6eb;
            text-align: center;
            margin-top: 100px;
        }

        h1 {
            font-size: 36px;
        }

        .buttons {
            margin-top: 40px;
        }

        button {
            font-size: 20px;
            padding: 12px 30px;
            border: none;
            border-radius: 8px;
            cursor: pointer;
        }

        #yes {
            background-color: #4CAF50;
            color: white;
        }

        #no {
            background-color: #f44336;
            color: white;
            position: absolute;
        }
    </style>
</head>
<body>

    <h1>💖 Will you be my Valentine Jojo? 💖</h1>

    <div class="buttons">
        <button id="yes" onclick="yesClicked()">Yes</button>
        <button id="no">No</button>
    </div>

    <script>
        const noBtn = document.getElementById("no");

        noBtn.addEventListener("mouseover", () => {
            const x = Math.random() * (window.innerWidth - 100);
            const y = Math.random() * (window.innerHeight - 100);
            noBtn.style.left = x + "px";
            noBtn.style.top = y + "px";
        });

        function yesClicked() {
            document.body.innerHTML = "<h1>🥰 E dija! Të dua ❤️</h1>";
        }
    </script>

</body>
</html>

<!DOCTYPE html>
<html lang="sq">
<head>
    <meta charset="UTF-8">
    <title>Për Ty ❤️</title>
    <style>
        body {
            margin: 0;
            background: black;
            overflow: hidden;
            font-family: Arial, sans-serif;
        }

        .text {
            position: absolute;
            top: 40%;
            width: 100%;
            text-align: center;
            color: white;
            font-size: 28px;
            z-index: 2;
            font-style: italic;
        }

        canvas {
            position: fixed;
            top: 0;
            left: 0;
        }
    </style>
</head>
<body>

<div class="text">
    Edhe pse nuk jemi afër,<br>
    dashuria ime për ty është gjithmonë aty. ❤️
</div>

<canvas id="canvas"></canvas>

<script>
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

canvas.width = window.innerWidth;
canvas.height = window.innerHeight;

let fireworks = [];

function Firework(x, y) {
    this.x = x;
    this.y = y;
    this.radius = Math.random() * 3 + 1;
    this.color = `hsl(${Math.random() * 360}, 100%, 60%)`;
    this.speedX = Math.random() * 6 - 3;
    this.speedY = Math.random() * 6 - 3;
    this.life = 60;
}

function createFirework() {
    const x = Math.random() * canvas.width;
    const y = Math.random() * canvas.height / 2;
    for (let i = 0; i < 50; i++) {
        fireworks.push(new Firework(x, y));
    }
}

function animate() {
    ctx.fillStyle = "rgba(0,0,0,0.2)";
    ctx.fillRect(0, 0, canvas.width, canvas.height);

    fireworks.forEach((f, index) => {
        f.x += f.speedX;
        f.y += f.speedY;
        f.life--;

        ctx.beginPath();
        ctx.arc(f.x, f.y, f.radius, 0, Math.PI * 2);
        ctx.fillStyle = f.color;
        ctx.fill();

        if (f.life <= 0) {
            fireworks.splice(index, 1);
        }
    });

    requestAnimationFrame(animate);
}

setInterval(createFirework, 800);
animate();

window.onresize = () => {
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;
};
</script>

</body>
</html>
