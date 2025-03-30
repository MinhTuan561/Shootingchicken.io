# Shootingchicken.io<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Trò Chơi Bắn Gà</title>
    <style>
        /* Các định dạng CSS tương tự như trước */
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
        // Các hàm và logic trò chơi tương tự như trước
        // Thêm các sự kiện cảm ứng và xử lý tương ứng

        // Xử lý sự kiện touchstart
        canvas.addEventListener('touchstart', (event) => {
            event.preventDefault(); // Ngăn chặn hành vi mặc định của trình duyệt
            handleTouchStart(event.touches[0].clientX, event.touches[0].clientY);
        });

        // Xử lý sự kiện touchmove
        canvas.addEventListener('touchmove', (event) => {
            event.preventDefault(); // Ngăn chặn hành vi mặc định của trình duyệt
            handleTouchMove(event.touches[0].clientX, event.touches[0].clientY);
        });

        // Xử lý sự kiện touchend
        canvas.addEventListener('touchend', (event) => {
            event.preventDefault(); // Ngăn chặn hành vi mặc định của trình duyệt
            handleTouchEnd();
        });

        // Hàm xử lý sự kiện touchstart
        function handleTouchStart(x, y) {
            // Xử lý sự kiện chạm vào màn hình để bắn
            if (x > gunX && x < gunX + 50 && y > 550) {
                shoot();
            }
        }

        // Hàm xử lý sự kiện touchmove
        function handleTouchMove(x, y) {
            // Xử lý sự kiện vuốt để di chuyển súng
            gunX = Math.max(0, Math.min(canvas.width - 50, x - 25));
        }

        // Hàm xử lý sự kiện touchend
        function handleTouchEnd() {
            // Không cần xử lý gì thêm
        }

        // Gọi hàm gameLoop() để bắt đầu trò chơi
        gameLoop();
    </script>
</body>
</html>
