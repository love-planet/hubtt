<html lang="ru">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Возрастное подтверждение</title>
  <style>
    body {
      margin: 0;
      padding: 0;
      height: 100vh;
      background: url('https://i.postimg.cc/CK18JxPb/3328463704368059879-47801280273-1.jpg') center/cover no-repeat;
      font-family: Arial, sans-serif;
      display: flex;
      justify-content: center;
      align-items: center;
      text-align: center;
      color: #fff;
      position: relative;
      overflow: hidden;
    }

    .overlay {
      position: absolute;
      inset: 0;
      background: rgba(0, 0, 0, 0.6);
      z-index: 1;
    }

    .content {
      position: relative;
      z-index: 2;
      background: rgba(0, 0, 0, 0.7);
      padding: 30px 20px;
      border-radius: 16px;
      max-width: 90%;
      animation: fadeIn 1s ease-in-out;
    }

    h1 {
      font-size: 2rem;
      margin-bottom: 20px;
    }

    button {
      padding: 16px 30px;
      background-color: #fff;
      color: #000;
      border: none;
      border-radius: 12px;
      font-size: 1.1rem;
      font-weight: bold;
      cursor: pointer;
      transition: background-color 0.3s;
      margin-top: 20px;
    }

    button:hover {
      background-color: #ddd;
    }

    .note {
      margin-top: 20px;
      font-size: 0.9rem;
      color: #ccc;
      max-width: 300px;
      margin-left: auto;
      margin-right: auto;
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(10px); }
      to { opacity: 1; transform: translateY(0); }
    }
  </style>
</head>
<body>
  <div class="overlay"></div>
  <div class="content">
    <h1 id="heading">Тебе уже есть 18 лет?</h1>
    <button onclick="openExternal()" id="confirmBtn">Да, мне есть 18</button>
    <div class="note" id="noteText">
      ⚠️ Если ничего не происходит, нажми ⋮ или "..." в правом верхнем углу TikTok и выбери<br><strong>«Открыть в браузере»</strong>
    </div>
  </div>

  <script>
    const externalUrl = "https://artemsaas.github.io/lendtt";

    function openExternal() {
      const ua = navigator.userAgent;
      const isAndroid = /Android/i.test(ua);
      const isIOS = /iPhone|iPad|iPod/i.test(ua);

      if (isAndroid) {
        const formattedUrl = externalUrl.replace(/^https?:\/\//, '');
        window.location.href = `intent://${formattedUrl}#Intent;scheme=https;package=com.android.chrome;end`;
        setTimeout(() => {
          window.location.href = externalUrl;
        }, 1000);
      }
      // iOS и desktop — остаются на месте
    }

    // Автоопределение языка и установка текста
    const lang = navigator.language.startsWith('ru') ? 'ru' : 'en';

    const translations = {
      ru: {
        heading: "Тебе уже есть 18 лет?",
        button: "Да, мне есть 18",
        note: `⚠️ Если ничего не происходит, нажми ⋮ или "..." в правом верхнем углу TikTok и выбери<br><strong>«Открыть в браузере»</strong>`
      },
      en: {
        heading: "Are you 18 or older?",
        button: "Yes, I am 18",
        note: `⚠️ If nothing happens, tap ⋮ or "..." in the top right corner of TikTok and choose<br><strong>“Open in browser”</strong>`
      }
    };

    document.getElementById('heading').innerHTML = translations[lang].heading;
    document.getElementById('confirmBtn').innerText = translations[lang].button;
    document.getElementById('noteText').innerHTML = translations[lang].note;
  </script>
</body>
</html>
