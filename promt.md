Este codigo es de un juego de la serpiente que crece cada vez que se come el bloque que hay en el canvas, el codigo funciona con un array y no te tiene errores. Lo que quiero que hagas es que cambies ese array por un arreglo de datos tipo cola y que adaptes el codigo a la cola para que funciones igual a cuando funcionaba con el array.


Código con el "Array"

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Simple Snake Game</title>
    <style>
        canvas {
            border: 1px solid black;
            background-color: #f0f0f0;
        }
    </style>
</head>
<body>
    <canvas id="snakeCanvas" width="400" height="400"></canvas>
    <script>
        const canvas = document.getElementById('snakeCanvas');
        const ctx = canvas.getContext('2d');
        const box = 20;
        let snake = [{ x: 9 * box, y: 9 * box }];
        let direction = 'RIGHT';
        let food = {
            x: Math.floor(Math.random() * 20) * box,
            y: Math.floor(Math.random() * 20) * box
        };

        document.addEventListener('keydown', directionControl);

        function directionControl(event) {
            if (event.keyCode === 37 && direction !== 'RIGHT') direction = 'LEFT';
            if (event.keyCode === 38 && direction !== 'DOWN') direction = 'UP';
            if (event.keyCode === 39 && direction !== 'LEFT') direction = 'RIGHT';
            if (event.keyCode === 40 && direction !== 'UP') direction = 'DOWN';
        }

        function draw() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            for (let i = 0; i < snake.length; i++) {
                ctx.fillStyle = (i === 0) ? 'green' : 'lightgreen';
                ctx.fillRect(snake[i].x, snake[i].y, box, box);
                ctx.strokeStyle = 'darkgreen';
                ctx.strokeRect(snake[i].x, snake[i].y, box, box);
            }
            ctx.fillStyle = 'red';
            ctx.fillRect(food.x, food.y, box, box);

            let snakeX = snake[0].x;
            let snakeY = snake[0].y;

            if (direction === 'LEFT') snakeX -= box;
            if (direction === 'UP') snakeY -= box;
            if (direction === 'RIGHT') snakeX += box;
            if (direction === 'DOWN') snakeY += box;

            if (snakeX === food.x && snakeY === food.y) {
                food = {
                    x: Math.floor(Math.random() * 20) * box,
                    y: Math.floor(Math.random() * 20) * box
                };
            } else {
                snake.pop();
            }

            const newHead = { x: snakeX, y: snakeY };

            if (snakeX < 0 || snakeY < 0 || snakeX >= canvas.width || snakeY >= canvas.height || collision(newHead, snake)) {
                clearInterval(game);
                alert('Game Over!');
            }

            snake.unshift(newHead);
            ctx.fillStyle = 'black';
            ctx.font = '20px Arial';
            ctx.fillText('Score: ' + (snake.length - 1), 10, 20);
        }

        function collision(head, array) {
            for (let i = 0; i < array.length; i++) {
                if (head.x === array[i].x && head.y === array[i].y) {
                    return true;
                }
            }
            return false;
        }

        let game = setInterval(draw, 100);
    </script>
</body>
</html>

