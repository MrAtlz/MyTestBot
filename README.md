<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tap Game</title>
    <style>
        body { 
            display: flex; 
            justify-content: center; 
            align-items: center; 
            height: 100vh; 
            background: #222; 
            color: #fff; 
            font-family: Arial, sans-serif; 
            margin: 0;
            flex-direction: column;
        }
        button { 
            padding: 15px 30px; 
            font-size: 20px; 
            border: none; 
            border-radius: 12px; 
            background: gold; 
            color: black; 
            cursor: pointer; 
            transition: transform 0.2s;
        }
        button:active {
            transform: scale(0.95);
        }
        .score {
            font-size: 30px; 
            margin-bottom: 20px;
        }
    </style>
</head>
<body>

    <div class="score">Очки: 0</div>
    <button onclick="addPoint()">🔘 Тап!</button>

    <script src="https://telegram.org/js/telegram-web-app.js"></script>
    <script>
        let score = 0;
        const scoreDiv = document.querySelector('.score');

        function addPoint() {
            score++;
            scoreDiv.textContent = `Очки: ${score}`;

            if (score % 10 === 0) {
                Telegram.WebApp.showPopup({
                    message: `🔥 Бонус! Ты набрал ${score} очков!`,
                    buttons: [{ id: 'ok', type: 'ok', text: 'Круто!' }]
                });
            }
        }

        Telegram.WebApp.ready();
    </script>
</body>
</html>
