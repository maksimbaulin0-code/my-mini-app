<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>TMA Pro Template</title>
    <script src="https://telegram.org/js/telegram-web-app.js"></script>
    <style>
        /* CSS переменные для автоматической смены темы (светлая/темная) */
        :root {
            --bg-color: var(--tg-theme-bg-color, #ffffff);
            --text-color: var(--tg-theme-text-color, #000000);
            --hint-color: var(--tg-theme-hint-color, #707579);
            --link-color: var(--tg-theme-link-color, #2481cc);
            --button-color: var(--tg-theme-button-color, #2481cc);
            --button-text-color: var(--tg-theme-button-text-color, #ffffff);
            --secondary-bg-color: var(--tg-theme-secondary-bg-color, #f4f4f5);
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
            background-color: var(--bg-color);
            color: var(--text-color);
            margin: 0;
            padding: 0;
            display: flex;
            flex-direction: column;
            align-items: center;
            min-height: 100vh;
            -webkit-font-smoothing: antialiased;
        }

        /* Контейнер приложения */
        .app-container {
            width: 100%;
            max-width: 600px;
            padding: 20px;
            box-sizing: border-box;
            display: flex;
            flex-direction: column;
            gap: 20px;
        }

        /* Блок профиля */
        .profile-card {
            background-color: var(--secondary-bg-color);
            border-radius: 12px;
            padding: 15px;
            display: flex;
            align-items: center;
            gap: 15px;
            box-shadow: 0 2px 4px rgba(0,0,0,0.05);
        }

        .avatar {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            background-color: var(--button-color);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 20px;
            color: white;
            font-weight: bold;
        }

        .user-info h2 { margin: 0; font-size: 18px; }
        .user-info p { margin: 2px 0 0; font-size: 14px; color: var(--hint-color); }

        /* Поле ввода */
        .input-group {
            display: flex;
            flex-direction: column;
            gap: 8px;
        }

        label { font-size: 14px; color: var(--hint-color); padding-left: 5px; }

        input[type="text"] {
            padding: 12px;
            border-radius: 8px;
            border: 1px solid var(--secondary-bg-color);
            background-color: var(--secondary-bg-color);
            color: var(--text-color);
            font-size: 16px;
            outline: none;
            transition: border-color 0.2s;
        }

        input[type="text"]:focus { border-color: var(--button-color); }

        /* Кнопка */
        .main-button {
            background-color: var(--button-color);
            color: var(--button-text-color);
            border: none;
            padding: 15px;
            border-radius: 8px;
            font-size: 16px;
            font-weight: 600;
            cursor: pointer;
            transition: opacity 0.2s;
            box-shadow: 0 4px 6px rgba(0,0,0,0.1);
        }

        .main-button:active { opacity: 0.8; }
        .main-button:disabled { opacity: 0.5; cursor: not-allowed; }

        /* Статус отправки */
        #status {
            font-size: 14px;
            text-align: center;
            margin-top: 10px;
            transition: color 0.2s;
        }

        .status-success { color: #34c759; }
        .status-error { color: #ff3b30; }
        .status-loading { color: var(--hint-color); }

    </style>
</head>
<body>

    <div class="app-container">
        <div class="profile-card">
            <div id="avatar" class="avatar">?</div>
            <div class="user-info">
                <h2 id="username">Пользователь</h2>
                <p id="user-id">ID: ?</p>
            </div>
        </div>

        <div class="input-group">
            <label for="user-message">Напиши что-нибудь для n8n:</label>
            <input type="text" id="user-message" placeholder="Твое сообщение...">
        </div>

        <button id="send-btn" class="main-button" onclick="sendData()">Отправить в n8n</button>
        
        <p id="status"></p>
    </div>

    <script>
        // Инициализация Telegram TMA
        const tg = window.Telegram.WebApp;
        
        // Разворачиваем приложение на весь экран
        tg.expand();
        
        // Сообщаем Telegram, что мы готовы (убирает сплеш-скрин)
        tg.ready();

        // 1. Получаем данные пользователя из Telegram
        const user = tg.initDataUnsafe.user;

        if (user) {
            // Заполняем профиль
            document.getElementById('username').innerText = `${user.first_name} ${user.last_name || ''}`;
            document.getElementById('user-id').innerText = `ID: ${user.id}`;
            
            // Ставим первую букву имени в аватар
            document.getElementById('avatar').innerText = user.first_name[0].toUpperCase();
            
            // Если есть username, добавляем
            if (user.username) {
                document.getElementById('user-id').innerText += ` (@${user.username})`;
            }
        }

        // 2. Настройка Главной Кнопки Telegram (MainButton)
        tg.MainButton.text = "Закрыть приложение";
        tg.MainButton.show();
        tg.MainButton.onClick(() => {
            tg.close(); // Закрываем TMA по нажатию
        });

        // 3. Функция отправки данных в n8n
        async function sendData() {
            // === ВСТАВЬ СЮДА СВОЙ URL ИЗ N8N WEBHOOK ===
            const N8N_WEBHOOK_URL = 'https://scarface.app.n8n.cloud/webhook/my-tma-endpoint'; 

            const messageInput = document.getElementById('user-message');
            const statusText = document.getElementById('status');
            const sendBtn = document.getElementById('send-btn');

            const message = messageInput.value.trim();

            if (!message) {
                tg.showAlert('Пожалуйста, напиши сообщение!');
                return;
            }

            // Блокируем кнопку на время отправки
            sendBtn.disabled = true;
            statusText.innerText = 'Отправка...';
            statusText.className = 'status-loading';

            // Данные для отправки
            const payload = {
                user_id: user ? user.id : 'unknown',
                first_name: user ? user.first_name : 'unknown',
                username: user ? user.username : 'unknown',
                message_text: message,
                timestamp: new Date().toISOString()
            };

            try {
                // Отправляем POST запрос в n8n
                const response = await fetch(N8N_WEBHOOK_URL, {
                    method: 'POST',
                    headers: {
                        'Content-Type': 'application/json',
                    },
                    body: JSON.stringify(payload),
                });

                if (response.ok) {
                    // Успех
                    statusText.innerText = '✅ Данные успешно отправлены!';
                    statusText.className = 'status-success';
                    messageInput.value = ''; // Очищаем поле
                    
                    // Виброотклик (Haptic Feedback) - успех
                    tg.HapticFeedback.notificationOccurred('success');
                    
                    // Через 3 секунды убираем статус
                    setTimeout(() => statusText.innerText = '', 3000);
                } else {
                    // Ошибка сервера
                    throw new Error('Ошибка сервера n8n');
                }
            } catch (error) {
                // Ошибка сети или другая
                statusText.innerText = '❌ Ошибка при отправке. Попробуй позже.';
                statusText.className = 'status-error';
                console.error('Ошибка fetch:', error);
                
                // Виброотклик - ошибка
                tg.HapticFeedback.notificationOccurred('error');
            } finally {
                // Разблокируем кнопку в любом случае
                sendBtn.disabled = false;
            }
        }

    </script>
</body>
</html>
