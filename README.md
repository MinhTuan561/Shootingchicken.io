<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Trò Chơi Bắn Gà</title>
    <style>
        body { margin: 0; display: flex; justify-content: center; align-items: center; height: 100vh; background-color: #87CEEB; }
        canvas { border: 2px solid #000; }
        #controls { display: none; } /* Ẩn các nút điều khiển */
        #restartButton { /* Giữ nguyên định dạng nút chơi lại */ }
    </style>
</head>
<body>
    <canvas id="gameCanvas" width="800" height="600"></canvas>
    <button id="restartButton">Chơi lại</button>
    <script>
        const canvas = document.getElementById('gameCanvas');
        const ctx = canvas.getContext('2d');

        let blocks = [];
        let bullets = [];
        let enemyBullets = [];
        let score = 0;
        let gunX = 400; // Vị trí ban đầu của súng
        let startTime = Date.now();
        const timeLimit = 60;
        let gameOver = false;
        let round = 1;
        let blockDirection = 1;

        let lastBulletTime = 0;
        const bulletInterval = 1000;

        function resetGame() {
            // Các đoạn code khác như trước
            createBlocks();
            gameLoop();
        }

        function createBlocks() {
            // Tạo lại các block như trước
            blocks = [];
            const blockCount = round === 1 ? 10 : 5;
            const rows = 1;
            const blockWidth = 50;
            const blockHeight = 50;
            const gapX = (canvas.width - (blockWidth * blockCount)) / (blockCount + 1);

            for (let i = 0; i < blockCount; i++) {
                const x = gapX + i * (blockWidth + gapX);
                const y = 100;
                blocks.push({ x: x, y: y, width: blockWidth, height: blockHeight });
            }
        }

        function drawGun() {
            ctx.fillStyle = 'black';
            ctx.fillRect(gunX, 550, 50, 10); // Vẽ súng
        }

        function drawBlocks() {
            blocks.forEach(block => {
                drawChicken(block.x, block.y); // Vẽ hình con gà
            });
        }

        function drawChicken(x, y) {
            // Vẽ lại hình con gà như trước
            // ...
        }

        function drawBullets() {
            ctx.fillStyle = 'red';
            bullets.forEach(bullet => {
                ctx.fillRect(bullet.x, bullet.y, bullet.width, bullet.height);
            });
        }

        function drawEnemyBullets() {
            ctx.fillStyle = 'blue';
            enemyBullets.forEach(bullet => {
                ctx.fillRect(bullet.x, bullet.y, bullet.width, bullet.height);
            });
        }

        // Các hàm update và check collision tương tự như trước

        // Xử lý sự kiện touchstart
        canvas.addEventListener('touchstart', (event) => {
            event.preventDefault();
            handleTouchStart(event.touches[0].clientX, event.touches[0].clientY);
        });

        // Xử lý sự kiện touchmove
        canvas.addEventListener('touchmove', (event) => {
            event.preventDefault();
            handleTouchMove(event.touches[0].clientX, event.touches[0].clientY);
        });

        // Xử lý sự kiện touchend
        canvas.addEventListener('touchend', (event) => {
            event.preventDefault();
            handleTouchEnd();
        });

        function handleTouchStart(x, y) {
            if (x > gunX && x < gunX + 50 && y > 550) {
                shoot();
            }
        }

        function handleTouchMove(x, y) {
            gunX = Math.max(0, Math.min(canvas.width - 50, x - 25));
        }

        function handleTouchEnd() {
            // Không cần xử lý gì thêm
        }

        function gameLoop() {
            // Các đoạn code khác như trước
            drawGun();
            drawBlocks();
            drawBullets();
            drawEnemyBullets();
            // ...
        }

        resetGame();
    </script>
</body>
</html>
