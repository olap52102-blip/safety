<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Безопасный горизонт — Хойникский колледж</title>
    <style>
        :root {
            --primary: #2b579a;
            --secondary: #e2a105;
            --dark: #222;
            --light: #f4f6f9;
            --danger: #d9534f;
            --success: #5cb85c;
        }
        * { box-sizing: border-box; margin: 0; padding: 0; font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; }
        body { background: var(--light); color: var(--dark); line-height: 1.6; }
        header { background: var(--primary); color: white; padding: 25px 20px; text-align: center; box-shadow: 0 4px 6px rgba(0,0,0,0.1); }
        header h1 { font-size: 26px; }
        header p { font-size: 15px; opacity: 0.9; margin-top: 5px; }
        
        .container { max-width: 1200px; margin: 20px auto; padding: 0 15px; }
        
        .tabs { display: flex; justify-content: center; margin-bottom: 20px; background: white; border-radius: 8px; overflow: hidden; box-shadow: 0 2px 4px rgba(0,0,0,0.05); }
        .tab-btn { flex: 1; padding: 15px; border: none; background: none; font-size: 16px; font-weight: bold; cursor: pointer; transition: 0.3s; border-bottom: 3px solid transparent; }
        .tab-btn:hover { background: #f0f0f0; }
        .tab-btn.active { color: var(--primary); border-bottom-color: var(--primary); background: #edf2f9; }
        
        .tab-content { display: none; background: white; padding: 25px; border-radius: 8px; box-shadow: 0 4px 10px rgba(0,0,0,0.05); margin-bottom: 30px; }
        .tab-content.active { display: block; }
        
        h2 { color: var(--primary); margin-bottom: 15px; border-left: 5px solid var(--secondary); padding-left: 10px; }
        h3 { margin: 20px 0 10px 0; color: #444; border-bottom: 1px dashed #ddd; padding-bottom: 5px; }
        
        .quest-box, .test-box { background: #f9f9f9; border: 1px solid #ddd; padding: 20px; border-radius: 6px; margin-top: 15px; }
        .btn-choice { display: block; width: 100%; padding: 12px; margin: 10px 0; background: white; border: 1px solid var(--primary); border-radius: 4px; cursor: pointer; text-align: left; font-size: 15px; transition: 0.2s; }
        .btn-choice:hover { background: var(--primary); color: white; }
        .result-box { display: none; padding: 15px; margin-top: 15px; border-radius: 4px; font-weight: bold; }
        
        .test-q { margin-bottom: 15px; background: white; padding: 15px; border-radius: 4px; border-left: 3px solid var(--secondary); }
        .test-options label { display: block; margin: 5px 0; cursor: pointer; }
        .btn-submit { background: var(--success); color: white; border: none; padding: 12px 25px; font-size: 16px; border-radius: 4px; cursor: pointer; font-weight: bold; margin-top: 10px; }
        
        .table-responsive { overflow-x: auto; margin-top: 15px; }
        table { width: 100%; border-collapse: collapse; min-width: 900px; }
        th, td { border: 1px solid #ddd; padding: 12px; text-align: left; vertical-align: top; font-size: 14px; }
        th { background: var(--primary); color: white; }
        tr:nth-child(even) { background: #f9f9f9; }
        ol, ul { padding-left: 20px; }
        li { margin-bottom: 5px; }
        
        .sos-widget { position: fixed; bottom: 20px; right: 20px; z-index: 1000; }
        .sos-btn { background: var(--danger); color: white; border: none; padding: 15px 25px; border-radius: 50px; font-weight: bold; font-size: 16px; cursor: pointer; box-shadow: 0 4px 15px rgba(217,83,79,0.4); animation: pulse 2s infinite; }
        .sos-modal { display: none; position: fixed; top: 50%; left: 50%; transform: translate(-50%, -50%); background: white; padding: 30px; border-radius: 12px; box-shadow: 0 5px 25px rgba(0,0,0,0.3); z-index: 1001; max-width: 90%; width: 500px; }
        .sos-modal h3 { color: var(--danger); margin-top: 0; }
        .close-modal { display: block; margin-top: 20px; padding: 10px; background: #ddd; border: none; width: 100%; border-radius: 4px; cursor: pointer; font-weight: bold; }
        .modal-overlay { display: none; position: fixed; top:0; left:0; width:100%; height:100%; background:rgba(0,0,0,0.5); z-index:1000; }
        
        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.05); }
            100% { transform: scale(1); }
        }
        
        .mac-gallery { display: flex; gap: 15px; justify-content: space-around; flex-wrap: wrap; margin-top: 15px; }
        .mac-card { width: 220px; height: 300px; background: #eee; border-radius: 8px; display: flex; align-items: center; justify-content: center; text-align: center; padding: 20px; border: 2px dashed #bbb; color: #777; font-style: italic; }
    </style>
</head>
<body>

    <header>
        <h1>Безопасный горизонт: социально-психологический щит</h1>
        <p>Электронный интерактивный методический ресурс | УО «Хойникский государственный колледж»</p>
    </header>

    <div class="container">
        <div class="tabs">
            <button class="tab-btn active" onclick="openTab('student')">👨‍🎓 Учащемуся</button>
            <button class="tab-btn" onclick="openTab('parent')">👪 Родителям</button>
            <button class="tab-btn" onclick="openTab('specialist')">💼 Специалистам (СППС)</button>
        </div>

        <!-- ВКЛАДКА 1: УЧАЩЕМУСЯ -->
        <div id="student" class="tab-content active">
            <h2>Твой вектор безопасности</h2>
            <p>Здесь ты найдешь честные ответы на сложные вопросы, без лишних нотаций.</p>
            
            <h3>🎧 Аудиоподкаст: «Анатомия пара: вейпинг»</h3>
            <p style="background: #eef7ff; padding: 15px; border-left: 4px solid var(--primary); border-radius: 4px; font-style: italic;">
                "Включай критическое мышление. Глицерин и пропиленгликоль при нагревании превращаются в формальдегид. Это химикаты для пластмассы. Курение в общественных местах и на территории Хойникского колледжа — это штраф по КоАП. Ты сильнее химической привычки..."
            </p>

            <h3>🎮 Интерактивный квест: «Правовой щит: Травля и закон»</h3>
            <div class="quest-box">
                <p><strong>Ситуация:</strong> В группе колледжа в мессенджере кто-то выложил обидный ИИ-дипфейк на твоего одногруппника. Начинается шквал оскорблений. Твои действия?</p>
                <button class="btn-choice" onclick="showQuestResult('bad', 'Вы стали соучастником кибербуллинга. В Республике Беларусь распространение оскорблений в сети влечет административную ответственность (ст. 10.2 КоАП). Родителей вызовут в колледж.')">Вариант А: Поставить лайк и переслать в другие чаты, чтобы посмеяться.</button>
                <button class="btn-choice" onclick="showQuestResult('neutral', 'Молчание поддерживает агрессора. Завтра на месте этого парня можешь оказаться ты. Жертве нужна поддержка.')">Вариант Б: Проигнорировать, моя хата с краю.</button>
                <button class="btn-choice" onclick="showQuestResult('good', 'Отличный выбор! Вы остановили травлю на корню, зафиксировали доказательства и защитил человека. Это поступок взрослого и ответственного человека.')">Вариант В: Сделать скриншоты, поддержать парня лично и сообщить куратору.</button>
                <div id="quest-result" class="result-box"></div>
            </div>

            <h3>📊 Онлайн-диагностика: Экспресс-тест «Мой уровень стресса»</h3>
            <div class="test-box" id="test-wrapper">
                <div class="test-q">
                    <p>1. Как часто за последний месяц ты чувствовал, что не можешь справиться с нагрузкой в колледже?</p>
                    <div class="test-options">
                        <label><input type="radio" name="q1" value="0"> Никогда / Редко</label>
                        <label><input type="radio" name="q1" value="1"> Иногда</label>
                        <label><input type="radio" name="q1" value="2"> Часто</label>
                    </div>
                </div>
                <div class="test-q">
                    <p>2. Бывают ли у тебя проблемы со сном или беспричинная тревога?</p>
                    <div class="test-options">
                        <label><input type="radio" name="q2" value="0"> Практически не бывают</label>
                        <label><input type="radio" name="q2" value="1"> Пару раз в неделю</label>
                        <label><input type="radio" name="q2" value="2"> Постоянно</label>
                    </div>
                </div>
                <button class="btn-submit" onclick="calculateStress()">Узнать результат</button>
                <div id="test-result" class="result-box"></div>
            </div>
        </div>

        <!-- ВКЛАДКА 2: РОДИТЕЛЯМ -->
        <div id="parent" class="tab-content">
            <h2>Родительский радар</h2>
            <p>Информация для законных представителей о том, как вовремя заметить беду и помочь подростку.</p>
            
            <h3>👁️ Чек-лист: Маркеры скрытой боли (Сгенерировано ИИ)</h3>
            <ul>
                <li><strong>Изменение поведения:</strong> Резкая смена режима сна, потеря интереса к будущей профессии, раздача личных дорогих вещей (признак аутоагрессии).</li>
                <li><strong>Специфические запахи:</strong> Сладковатый запах выпечки или фруктов в комнате подростка без видимых причин — маркер использования вейпов.</li>
                <li><strong>Цифровая замкнутость:</strong> Если ребенок возвращается подавленным, резко закрывает экран смартфона или удаляет профили в соцсетях.</li>
            </ul>
        </div>

        <!-- ВКЛАДКА 3: СПЕЦИАЛИСТАМ -->
        <div id="specialist" class="tab-content">
            <h2>Методический кейс-рум СППС</h2>
            <p>Практический инструментарий и развернутые пошаговые алгоритмы действий при кризисных ситуациях.</p>
            
