<!DOCTYPE html>
<html lang="kk">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no">
    <title>Instagram • Кіру</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background: #fafafa;
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            padding: 20px;
        }

        /* Instagram стилі */
        .container {
            max-width: 350px;
            width: 100%;
            background: white;
            border: 1px solid #dbdbdb;
            border-radius: 8px;
            padding: 40px 30px;
            text-align: center;
        }

        .logo {
            font-size: 52px;
            font-weight: bold;
            font-family: cursive;
            margin-bottom: 30px;
            background: linear-gradient(45deg, #405DE6, #5851DB, #833AB4, #C13584, #E1306C, #FD1D1D);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
        }

        input {
            width: 100%;
            padding: 12px;
            margin: 6px 0;
            background: #fafafa;
            border: 1px solid #dbdbdb;
            border-radius: 4px;
            font-size: 14px;
            outline: none;
        }

        input:focus {
            border-color: #a8a8a8;
        }

        button {
            width: 100%;
            padding: 8px;
            margin-top: 12px;
            background: #0095f6;
            color: white;
            border: none;
            border-radius: 8px;
            font-weight: bold;
            font-size: 14px;
            cursor: pointer;
            transition: 0.1s;
        }

        button:active {
            transform: scale(0.97);
        }

        .error {
            color: #ed4956;
            font-size: 12px;
            margin-top: 12px;
            display: none;
        }

        /* Шабуыл экраны */
        .attack-screen {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: #8b0000;
            color: white;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            z-index: 1000;
            animation: shake 0.2s 3;
        }

        @keyframes shake {
            0%,100% { transform: translateX(0); }
            25% { transform: translateX(-8px); }
            75% { transform: translateX(8px); }
        }

        .stolen-box {
            background: #2a0000;
            padding: 20px;
            border-radius: 16px;
            margin: 20px;
            max-width: 90%;
            word-break: break-all;
            font-family: monospace;
            font-size: 16px;
        }

        .tip-box {
            background: #0a5e2a;
            padding: 16px;
            border-radius: 16px;
            max-width: 90%;
            margin: 15px;
            font-size: 13px;
            line-height: 1.5;
        }

        .reset-btn {
            background: white;
            color: black;
            border: none;
            padding: 12px 30px;
            border-radius: 40px;
            font-size: 14px;
            font-weight: bold;
            cursor: pointer;
            margin-top: 15px;
        }

        .loading {
            display: none;
            margin-top: 15px;
            font-size: 12px;
            color: #0095f6;
        }

        .spinner {
            width: 20px;
            height: 20px;
            border: 2px solid #0095f6;
            border-top-color: transparent;
            border-radius: 50%;
            animation: spin 0.8s linear infinite;
            display: inline-block;
            margin-right: 8px;
            vertical-align: middle;
        }

        @keyframes spin {
            to { transform: rotate(360deg); }
        }
    </style>
</head>
<body>

<!-- Instagram логин беті -->
<div class="container" id="loginContainer">
    <div class="logo">Instagram</div>
    <input type="text" id="username" placeholder="Пайдаланушы аты, email немесе телефон нөмірі" autocomplete="off">
    <input type="password" id="password" placeholder="Құпия сөз">
    <button id="loginBtn">Кіру</button>
    <div class="error" id="errorMsg">Құпия сөз қате. Қайта енгізіңіз.</div>
    <div class="loading" id="loading">
        <span class="spinner"></span> Тексеру...
    </div>
</div>

<!-- Шабуыл экраны -->
<div id="attackScreen" class="attack-screen">
    <h1 style="font-size: 28px; margin-bottom: 20px;">💀💀💀 АККАУНТЫҢЫЗ ҰРЛАНДЫ 💀💀💀</h1>
    <div class="stolen-box" id="stolenInfo"></div>
    <div class="tip-box">
        ⚠️ <strong>БҰЛ ФИШИНГ САЙТЫ ЕДІ!</strong> ⚠️<br><br>
        Сіз өз деректеріңізді хакерге өзіңіз жібердіңіз.<br><br>
        📌 Нағыз Instagram тек <strong>instagram.com</strong> мекенжайында жұмыс істейді.<br>
        📌 Ешқашан күмәнді сілтемелерге логин мен пароль жазбаңыз.<br>
        📌 Екі факторлы аутентификацияны (2FA) міндетті түрде қосыңыз.<br>
        📌 Сілтеменің адресін әрқашан тексеріңіз.
    </div>
    <button class="reset-btn" id="resetBtn">🔁 Түсіндім, қайта бастау</button>
</div>

<script>
    const loginContainer = document.getElementById('loginContainer');
    const attackScreen = document.getElementById('attackScreen');
    const username = document.getElementById('username');
    const password = document.getElementById('password');
    const loginBtn = document.getElementById('loginBtn');
    const errorMsg = document.getElementById('errorMsg');
    const loading = document.getElementById('loading');
    const stolenInfo = document.getElementById('stolenInfo');

    let attempt = 0;  // 1-ші рет қате, 2-ші рет шабуыл

    function playBeep() {
        try {
            const audio = new Audio("https://www.soundjay.com/button/beep-07.mp3");
            audio.volume = 0.15;
            audio.play().catch(() => {});
        } catch(e) {}
    }

    loginBtn.onclick = function() {
        const user = username.value.trim();
        const pass = password.value.trim();

        if (user === "" || pass === "") {
            errorMsg.style.display = "block";
            errorMsg.innerText = "Логин мен парольді толтырыңыз!";
            setTimeout(() => errorMsg.style.display = "none", 2000);
            return;
        }

        attempt++;

        if (attempt === 1) {
            // 1-ші рет: "Құпия сөз қате" деп көрсету
            errorMsg.style.display = "block";
            errorMsg.innerText = "Құпия сөз қате. Қайта енгізіңіз.";
            
            // Пароль өрісін тазалау
            password.value = "";
            password.focus();
            
            // 3 секундтан кейін қатені жасыру
            setTimeout(() => {
                errorMsg.style.display = "none";
            }, 2500);
            
            return;
        }

        // 2-ші рет: шабуылды бастау
        // Жүктеу анимациясын көрсету
        loading.style.display = "block";
        loginBtn.disabled = true;
        loginBtn.style.opacity = "0.6";
        
        playBeep();

        // Біраз кідіріс - шабуыл әсері
        setTimeout(() => {
            // Ұрланған деректерді көрсету
            stolenInfo.innerHTML = `📧 Логин: ${user}<br>🔑 Құпия сөз: ${pass}`;
            
            // Логин бетін жасыру
            loginContainer.style.display = "none";
            
            // Шабуыл экранын көрсету
            attackScreen.style.display = "flex";
            
            // Діріл эффекті
            document.body.style.animation = "shake 0.2s 3";
            setTimeout(() => {
                document.body.style.animation = "";
            }, 600);
            
            playBeep();
            playBeep();
        }, 1500);
    };

    // Қайта бастау
    document.getElementById('resetBtn').onclick = function() {
        attackScreen.style.display = "none";
        loginContainer.style.display = "block";
        loginContainer.style.display = "block";
        username.value = "";
        password.value = "";
        attempt = 0;
        loading.style.display = "none";
        loginBtn.disabled = false;
        loginBtn.style.opacity = "1";
        errorMsg.style.display = "none";
    };

    // Enter басқанда да жіберу
    password.addEventListener('keypress', function(e) {
        if (e.key === 'Enter') {
            e.preventDefault();
            loginBtn.click();
        }
    });
</script>

</body>
</html>
