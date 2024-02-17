<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Juego 2D en JavaScript</title>
<style>
    canvas {
        border: 1px solid black;
        display: block;
        margin: 0 auto;
    }
</style>
</head>
<body>
<canvas id="gameCanvas" width="800" height="600"></canvas>
<script>
    const canvas = document.getElementById('gameCanvas');
    const ctx = canvas.getContext('2d');

    // Definir variables del jugador
    let playerX = canvas.width / 2;
    let playerY = canvas.height - 30;
    const playerWidth = 50;
    const playerHeight = 50;
    let playerSpeed = 5;

    // Dibujar al jugador
    function drawPlayer() {
        ctx.fillStyle = 'blue';
        ctx.fillRect(playerX, playerY, playerWidth, playerHeight);
    }

    // Controlar la entrada del jugador
    document.addEventListener('keydown', (event) => {
        if (event.key === 'ArrowLeft') {
            playerX -= playerSpeed;
        } else if (event.key === 'ArrowRight') {
            playerX += playerSpeed;
        }

        // Mantener al jugador dentro del canvas
        if (playerX < 0) {
            playerX = 0;
        } else if (playerX + playerWidth > canvas.width) {
            playerX = canvas.width - playerWidth;
        }
    });

    // Función principal de dibujo del juego
    function draw() {
        // Limpiar el canvas
        ctx.clearRect(0, 0, canvas.width, canvas.height);

        // Dibujar al jugador
        drawPlayer();

        requestAnimationFrame(draw);
    }

    // Iniciar el juego
    draw();
</script>
</body>
</html>
