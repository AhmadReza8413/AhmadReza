<!DOCTYPE html>
<html lang="fa">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>آزمون‌ساز A.R (نسخه نهایی و کامل)</title>
    <link href="https://cdn.jsdelivr.net/gh/rastikerdar/dana-font@v3.0.0/dist/font-face.css" rel="stylesheet" type="text/css" />
    <style>
        :root {
            --font-family: 'Dana', 'Vazirmatn', sans-serif;
            --bg-color: #0c0a18;
            --container-bg: rgba(20, 14, 38, 0.6);
            --blur-bg: blur(16px);
            --container-border: rgba(255, 255, 255, 0.1);
            --text-color: #e8e0ff;
            --text-muted: #a49cc5;
            --title-color: #fff;
            --tab-indicator-bg: linear-gradient(90deg, #8A2BE2, #C71585);
            --tab-active-shadow: 0 0 20px rgba(199, 21, 133, 0.7);
            --option-border-hover: #8A2BE2;
            --option-selected-shadow: 0 0 15px rgba(138, 43, 226, 0.6);
            --correct-bg: linear-gradient(45deg, #0bab64, #3bb78f);
            --incorrect-bg: linear-gradient(45deg, #b20a2c, #d42a4b);
            --scrollbar-bg: rgba(0,0,0,0.2);
            --scrollbar-thumb: #8A2BE2;
            --input-bg: rgba(0, 0, 0, 0.2);
            --input-border-focus: #C71585;
            --btn-bg: rgba(255, 255, 255, 0.08);
            --btn-border: rgba(255, 255, 255, 0.2);
            --btn-hover-bg: rgba(255, 255, 255, 0.12);
            --option-bg: rgba(255, 255, 255, 0.05);
            --section-bg: rgba(255, 255, 255, 0.03);
        }

        * { margin: 0; padding: 0; box-sizing: border-box; }

        body {
            font-family: var(--font-family); font-weight: 400; direction: rtl;
            background-color: var(--bg-color); color: var(--text-color);
            min-height: 100vh; display: flex; justify-content: center; align-items: center;
            padding: 80px 20px 80px; overflow: hidden; position: relative;
        }
        
        #plexus-background { position: fixed; top: 0; left: 0; width: 100%; height: 100%; z-index: 0; }

        .container {
            width: 900px; max-width: 100%; background: var(--container-bg);
            backdrop-filter: var(--blur-bg); -webkit-backdrop-filter: var(--blur-bg);
            border-radius: 24px; padding: 30px;
            box-shadow: 0 0 0 1px var(--container-border), 0 8px 40px rgba(0,0,0,0.5);
            position: relative; z-index: 2; max-height: 85vh; overflow-y: auto; padding-left: 40px;
        }
        .container::-webkit-scrollbar { width: 10px; }
        .container::-webkit-scrollbar-track { background: var(--scrollbar-bg); border-radius: 10px; }
        .container::-webkit-scrollbar-thumb { background: var(--scrollbar-thumb); border-radius: 10px; }
        
        header { 
            display: grid;
            grid-template-columns: 1fr auto 1fr;
            align-items: center;
            gap: 20px;
            margin-bottom: 20px; 
            border-bottom: 1px solid var(--container-border); 
            padding-bottom: 20px;
        }
        header .title {
            grid-column: 2 / 3;
            text-align: center;
            font-size: 2.2em; 
            font-weight: 700; 
            color: var(--title-color);
        }
        .logo-container {
            display: flex;
        }
        .logo-container.left {
            justify-content: flex-start;
        }
        .logo-container.right {
            justify-content: flex-end;
        }
        
        .logo-ar {
            width: 70px;
            height: 70px;
            border-radius: 50%;
            display: grid;
            place-items: center;
            position: relative;
            background: radial-gradient(circle, rgba(138,43,226,0.1) 0%, rgba(138,43,226,0) 70%);
            transition: transform 0.4s ease;
            transform-style: preserve-3d;
            cursor: pointer;
        }

        .logo-ar::before, .logo-ar::after {
            content: '';
            position: absolute;
            border-radius: 50%;
            animation: spin 8s linear infinite;
        }

        .logo-ar::before {
            inset: -3px;
            border: 2px solid transparent;
            border-top-color: #8e2de2;
            border-left-color: #8e2de2;
            filter: drop-shadow(0 0 5px #8e2de2);
        }
        
        .logo-ar::after {
            inset: 3px;
            border: 2px solid transparent;
            border-bottom-color: #ff0079;
            border-right-color: #ff0079;
            animation-direction: reverse;
            animation-duration: 6s;
            filter: drop-shadow(0 0 5px #ff0079);
        }

        @keyframes spin {
            from { transform: rotateZ(0deg) rotateX(0deg); }
            to { transform: rotateZ(360deg) rotateX(360deg); }
        }
        
        .logo-ar span {
            font-family: 'Orbitron', var(--font-family);
            font-weight: 500;
            color: #fff;
            position: relative;
            z-index: 2;
            background: rgba(12, 10, 24, 0.5);
            width: calc(100% - 10px);
            height: calc(100% - 10px);
            border-radius: 50%;
            display: grid;
            place-items: center;
            text-shadow: 0 0 4px #fff, 0 0 10px #ff0079, 0 0 18px #ff0079;
            animation: pulse-text 4s infinite alternate;
            transition: text-shadow 0.3s ease, letter-spacing 0.3s ease;
        }
        
        .logo-ar:hover span {
             text-shadow: 0 0 6px #fff, 0 0 15px #ff0079, 0 0 25px #ff0079;
             letter-spacing: 1px;
        }

        @keyframes pulse-text {
            from { text-shadow: 0 0 4px #fff, 0 0 10px #ff0079, 0 0 18px #ff0079; }
            to { text-shadow: 0 0 6px #fff, 0 0 16px #c71585, 0 0 28px #c71585; }
        }
        
        .logo-ar.logo-name span {
            font-size: 0.8em;
            letter-spacing: 1px;
        }

        #info-overlay {
            position: fixed; top: 0; left: 0; width: 100%; display: flex;
            justify-content: center; align-items: center; padding: 10px 20px;
            background: rgba(13, 4, 26, 0.5); backdrop-filter: var(--blur-bg);
            z-index: 10; font-size: 1em; color: var(--text-muted); gap: 25px;
        }
        .info-widget { text-align: center; cursor: pointer; }
        .info-widget .value { font-weight: 600; color: var(--text-color); font-size: 1.2em; }
        #clock-container { perspective: 500px; width: 150px; height: 32px; position: relative; }
        .clock-face { position: absolute; width: 100%; height: 100%; backface-visibility: hidden; transition: transform 0.6s; display: grid; place-items: center; }
        #digital-clock .value { animation: pulse-glow 2s infinite alternate; }
        @keyframes pulse-glow { from { text-shadow: 0 0 4px #ff0079; } to { text-shadow: 0 0 12px #ff0079, 0 0 20px #ff0079; } }
        #analog-clock { width: 52px; height: 52px; background: rgba(0,0,0,0.3); border: 2px solid var(--container-border); border-radius: 50%; transform: rotateY(180deg); position: absolute; top: -12px; left: 49px; }
        .hand { position: absolute; bottom: 50%; left: 50%; transform-origin: bottom; background: var(--text-color); border-radius: 2px; }
        #hour-hand { width: 3px; height: 13px; background: #fff; }
        #minute-hand { width: 2px; height: 18px; }
        #second-hand { width: 1px; height: 20px; background: #ff0079; }
        #analog-clock .tick { position: absolute; top: 2px; left: 50%; width: 1px; height: 5px; background: var(--text-muted); transform-origin: 0 24px; }
        #clock-container.show-analog #digital-clock { transform: rotateY(-180deg); }
        #clock-container.show-analog #analog-clock { transform: rotateY(0deg); }
        
        #calendar-popup { position: absolute; top: 60px; z-index: 11; width: 320px; padding: 20px; background: var(--container-bg); backdrop-filter: var(--blur-bg); border-radius: 15px; border: 1px solid var(--container-border); box-shadow: 0 8px 30px rgba(0,0,0,0.3); opacity: 0; transform: translateY(-20px) scale(0.95); transition: transform 0.3s ease, opacity 0.3s ease; pointer-events: none; }
        #calendar-popup.visible { opacity: 1; transform: translateY(0) scale(1); pointer-events: auto; }
        .calendar-header { display: flex; justify-content: space-between; align-items: center; margin-bottom: 15px; }
        .calendar-header button { background: var(--option-bg); border: none; color: var(--text-color); cursor: pointer; font-size: 1.5em; width: 35px; height: 35px; border-radius: 50%; display: grid; place-items: center; transition: background 0.2s; }
        .calendar-header button:hover { background: var(--btn-hover-bg); }
        .calendar-header span { font-weight: 600; font-size: 1.1em; }
        .calendar-weekdays, .calendar-days { display: grid; grid-template-columns: repeat(7, 1fr); text-align: center; }
        .calendar-weekdays div { font-size: 0.9em; color: var(--text-muted); padding-bottom: 10px; }
        .calendar-days div { padding: 8px 0; cursor: pointer; border-radius: 50%; transition: background 0.2s, color 0.2s; }
        .calendar-days div:not(.empty):hover { background: var(--option-bg); }
        .calendar-days .current-day { background: var(--tab-indicator-bg); color: #fff; font-weight: 700; box-shadow: var(--tab-active-shadow); }

        #battery-widget {
            position: fixed;
            bottom: 15px;
            left: 15px;
            display: flex;
            align-items: center;
            gap: 8px;
            transition: all .5s ease;
            z-index: 10;
            padding: 5px 10px;
            background: rgba(0,0,0,0.2);
            backdrop-filter: blur(5px);
            border-radius: 10px;
            border: 1px solid var(--container-border);
        }
        .battery-icon {
            width: 35px;
            height: 18px;
            border: 2px solid var(--container-border);
            border-radius: 5px;
            display: flex;
            align-items: center;
            padding: 2px;
            position:relative;
        }
        .battery-icon::after{
            content:'';
            position:absolute;
            right:-6px;
            top:50%;
            transform:translateY(-50%);
            width:3px;
            height:8px;
            background:var(--container-border);
            border-radius:0 2px 2px 0;
        }
        #battery-level{
            width:100%;
            height:100%;
            border-radius:2px;
            transition:width .5s ease,background-color .5s ease
        }
        #battery-percentage {
            font-size: 0.9em;
            font-weight: 600;
            color: var(--text-color);
        }
        #battery-widget.charging .battery-icon {
            animation:charging-glow 1.5s infinite alternate
        }
        @keyframes charging-glow{
            from{box-shadow:0 0 5px var(--container-border)}
            to{box-shadow:0 0 15px #38ef7d}
        }
        .lightning-icon {
            display: none;
            position: absolute;
            left: 50%;
            top: 50%;
            transform: translate(-50%, -50%);
            width: 14px;
            height: 14px;
            fill: #fff;
            animation: spark 0.8s infinite;
        }
        #battery-widget.charging .lightning-icon {
            display: block;
        }
        @keyframes spark {
            0%, 100% { opacity: 1; transform: translate(-50%, -50%) scale(1); }
            50% { opacity: 0.5; transform: translate(-50%, -50%) scale(0.8); }
        }


        .bottom-panel {
            position: fixed; bottom: 0; left: 0; width: 100%;
            background: rgba(13, 4, 26, 0.6); backdrop-filter: var(--blur-bg);
            border-top: 1px solid var(--container-border); padding: 12px 20px;
            z-index: 5; display: flex; justify-content: space-around;
            align-items: center; font-size: 1rem; font-weight: 600;
            transform: translateY(100%); transition: transform 0.5s cubic-bezier(0.23, 1, 0.32, 1);
        }
        .bottom-panel.visible { transform: translateY(0); }
        .live-stat { text-align: center; flex: 1; }
        .live-stat .label { font-size: 0.8em; color: var(--text-muted); display: block; }
        .live-stat .value { font-size: 1.2em; color: var(--title-color); }
        
        .tabs { position: relative; display: flex; justify-content: center; flex-wrap: wrap; gap: 10px; margin-bottom: 20px; filter: url('#gooey'); }
        #active-tab-indicator { position: absolute; bottom: -5px; height: 45px; background: var(--tab-indicator-bg); border-radius: 25px; z-index: 0; box-shadow: var(--tab-active-shadow); transition: all 0.5s cubic-bezier(0.68, -0.55, 0.27, 1.55); }
        .tab { padding: 10px 20px; background: transparent; border: none; border-radius: 25px; color: var(--text-muted); font-weight: 600; cursor: pointer; font-family: inherit; font-size: 1rem; display: inline-flex; align-items: center; gap: 8px; position: relative; z-index: 1; transition: color 0.3s ease; }
        .tab.active { color: #fff; }
        
        .btn { background: var(--btn-bg); border: 1px solid var(--btn-border); padding: 12px 30px; border-radius: 50px; color: #fff; cursor: pointer; transition: all 0.3s ease; font-family: inherit; font-size: 1rem; font-weight: 600; position: relative; overflow: hidden; z-index: 1; transform-style: preserve-3d; }
        .btn:hover { background: var(--btn-hover-bg); transform: scale(1.05); }
        .btn:active { transform: scale(0.98); }
        .btn span.spotlight { position: absolute; width: 100%; height: 100%; top: 0; left: 0; background: radial-gradient(circle at var(--x) var(--y), rgba(255,255,255,0.25), transparent 40%); opacity: 0; transition: opacity 0.3s; }
        .btn:hover span.spotlight { opacity: 1; }
        
        .delete-tab-btn { background: transparent; border: none; display: flex; align-items: center; justify-content: center; padding: 5px; margin-right: -10px; border-radius: 50%; cursor: pointer; transition: background 0.3s; }
        .delete-tab-btn:hover { background: rgba(220, 53, 69, 0.7); }
        .delete-tab-btn svg { width: 16px; height: 16px; fill: #fff; }

        .section { display: none; background: var(--section-bg); padding: 25px; border-radius: 15px; }
        .section.active { display: block; }
        .section-reveal.active { animation: revealFromCenter 0.7s cubic-bezier(0.23, 1, 0.32, 1); }
        .section-glitch.active { animation: glitchIn 0.5s steps(3, end); }
        .section-modular.active > * { animation: slideInUp 0.5s 0.1s both; }
        .section-flip.active { animation: flipIn 0.6s ease-out; }

        @keyframes revealFromCenter { from { clip-path: circle(0% at 50% 50%); } to { clip-path: circle(150% at 50% 50%); } }
        @keyframes glitchIn { 0% { transform: skewX(20deg) scale(0.95); opacity: 0; } 50% { transform: skewX(-10deg); opacity: 0.8; } 100% { transform: skewX(0) scale(1); opacity: 1; } }
        @keyframes slideInUp { from { transform: translateY(40px); opacity: 0; } to { transform: translateY(0); opacity: 1; } }
        @keyframes flipIn { from { transform: perspective(1000px) rotateX(-90deg); opacity: 0; } to { transform: perspective(1000px) rotateX(0deg); opacity: 1; } }

        .question-box { font-size: 1.3em; font-weight: 600; margin-bottom: 25px; padding: 20px; background: var(--input-bg); border-radius: 10px; text-align: center; line-height: 1.7; min-height: 80px; }
        .options { display: grid; grid-template-columns: 1fr 1fr; gap: 15px; }
        .option { background: var(--option-bg); border-radius: 12px; cursor: pointer; padding: 15px; position: relative; transition: transform 0.2s ease, box-shadow 0.2s ease, border-color 0.2s ease; border: 2px solid transparent; }
        .option:hover { transform: translateY(-3px); border-color: var(--option-border-hover); }
        .option.selected { transform: scale(1.03); border-color: var(--option-border-hover); box-shadow: var(--option-selected-shadow); }
        .option.correct, .option.incorrect { color: #fff; font-weight: 600; }
        .option.correct { background: var(--correct-bg); animation: pulse-correct 0.5s; border-color: transparent !important; }
        .option.incorrect { background: var(--incorrect-bg); animation: shake 0.5s; border-color: transparent !important;}
        @keyframes pulse-correct { from { transform: scale(1); } to { transform: scale(1.03); } }
        @keyframes shake { 0%, 100% {transform: translateX(0);} 25% {transform: translateX(-8px);} 75% {transform: translateX(8px);} }
        
        .quiz-form, .online-quiz-form { display: grid; gap: 20px; }
        .quiz-form label, .online-quiz-form label { font-weight: 600; color: var(--text-muted); }
        .quiz-form fieldset { border: 1px solid var(--container-border); padding: 20px; border-radius: 15px; display: grid; gap: 15px; transition: opacity 0.3s ease; }
        .quiz-form fieldset:disabled { opacity: 0.5; pointer-events: none; }
        .quiz-form legend { font-weight: 700; padding: 0 10px; color: var(--title-color); }
        .quiz-form input, .quiz-form textarea, .quiz-form select, .online-quiz-form input, .online-quiz-form textarea, .online-quiz-form select { 
            padding: 12px 15px; 
            border: 1px solid var(--container-border); 
            border-radius: 10px; 
            background: var(--input-bg); 
            color: var(--text-color); 
            font-family: inherit; 
            font-size: 1rem; 
            transition: all 0.3s ease; 
        }
        .quiz-form input:focus, .quiz-form textarea:focus, .quiz-form select:focus, .online-quiz-form input:focus, .online-quiz-form textarea:focus, .online-quiz-form select:focus { 
            outline: none; 
            border-color: var(--input-border-focus); 
            box-shadow: 0 0 15px rgba(199, 21, 133, 0.5); 
        }
        .inline-inputs { display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 15px; align-items: end; }
        .topic-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(150px, 1fr)); gap: 15px; padding: 20px 0; }
        .topic-card { background: var(--option-bg); border: 1px solid var(--container-border); border-radius: 15px; padding: 20px; text-align: center; cursor: pointer; transition: all 0.3s ease; color: var(--text-muted); }
        .topic-card:hover { transform: translateY(-5px); background: var(--btn-hover-bg); color: var(--text-color); box-shadow: 0 0 20px var(--option-border-hover); }
        .topic-card svg { width: 40px; height: 40px; margin-bottom: 10px; fill: currentColor; }
        .topic-card span { font-weight: 600; display: block; pointer-events: none; }

        h2 { text-align: center; margin-bottom: 20px; font-weight: 700; color: var(--title-color); }
        .result { margin-top: 20px; font-size: 1.2em; text-align: center; font-weight: bold; min-height: 30px; }
        .final-score-container { text-align: center; }
        .final-score-container .score-title { font-size: 1.5rem; opacity: 0.8; }
        .final-score-container .score-value { font-size: 4em; color: #fff; font-weight: 700; text-shadow: 0 0 20px var(--tab-indicator-bg);}
        .final-score-container .score-base { font-size: 1.2em; opacity: 0.7; }
        .progress-container { width: 100%; background-color: var(--input-bg); border-radius: 25px; margin-top: 25px; height: 15px; position: relative; overflow: hidden; border: 1px solid var(--container-border); }
        .progress-bar { height: 100%; background: var(--tab-indicator-bg); width: 0%; border-radius: 25px; transition: width 0.4s ease-in-out; }
    
        .online-maker-tabs { display: flex; border-bottom: 1px solid var(--container-border); margin-bottom: 20px; }
        .online-maker-tab { padding: 10px 20px; cursor: pointer; color: var(--text-muted); font-weight: 600; position: relative; }
        .online-maker-tab.active { color: var(--title-color); }
        .online-maker-tab.active::after { content: ''; position: absolute; bottom: -1px; left: 0; right: 0; height: 2px; background: var(--tab-indicator-bg); }
        .online-maker-content { display: none; }
        .online-maker-content.active { display: block; }
    </style>
</head>
<body>
    
    <canvas id="plexus-background"></canvas>
    
    <div id="info-overlay">
        <div id="date-widget" class="info-widget">
            <span id="date-display" class="value"></span>
        </div>
        <div id="clock-container">
            <div id="digital-clock" class="clock-face info-widget">
                 <span id="time-display" class="value"></span>
            </div>
            <div id="analog-clock" class="clock-face">
                <div id="hour-hand" class="hand"></div>
                <div id="minute-hand" class="hand"></div>
                <div id="second-hand" class="hand"></div>
            </div>
        </div>
    </div>
    
    <div id="calendar-popup">
        <div class="calendar-header">
            <button id="prev-month">&lt;</button>
            <span id="month-year-display"></span>
            <button id="next-month">&gt;</button>
        </div>
        <div class="calendar-weekdays">
            <div>ش</div><div>ی</div><div>د</div><div>س</div><div>چ</div><div>پ</div><div>ج</div>
        </div>
        <div class="calendar-days"></div>
    </div>

    <div id="battery-widget">
        <span id="battery-percentage">--%</span>
        <div class="battery-icon">
             <div id="battery-level"></div>
             <svg class="lightning-icon" viewBox="0 0 24 24"><path d="M7 2v11h3v9l7-12h-4l4-8z"></path></svg>
        </div>
    </div>

    <div class="container">
        <header>
            <div class="logo-container left">
                <div class="logo-ar"><span>A.R</span></div>
            </div>
            <h1 class="title">آزمون ساز</h1>
            <div class="logo-container right">
                <div class="logo-ar logo-name"><span>AhmadReza</span></div>
            </div>
        </header>
        <div class="tabs">
            <div id="active-tab-indicator"></div>
            <button class="tab active" data-target="lifestyleQuiz">آزمون آیین زندگی<span class="spotlight"></span></button>
            <button class="tab" data-target="onlineQuizMaker">آزمون ساز آنلاین<span class="spotlight"></span></button>
            <button class="tab" data-target="generalQuiz">کوییز عمومی<span class="spotlight"></span></button>
            <button class="tab" data-target="quizMaker">آزمون‌ساز دستی<span class="spotlight"></span></button>
            <button class="tab" data-target="customQuiz" id="customQuizTab" style="display:none;">
                <span id="customQuizTabTitle">آزمون شما</span>
                <span class="delete-tab-btn" id="deleteCustomQuizTab">
                     <svg viewBox="0 0 24 24" fill="currentColor"><path d="M6 19c0 1.1.9 2 2 2h8c1.1 0 2-.9 2-2V7H6v12zM19 4h-3.5l-1-1h-5l-1 1H5v2h14V4z"></path></svg>
                </span>
                <span class="spotlight"></span>
            </button>
        </div>

        <div id="lifestyleQuiz" class="section active section-reveal">
            <div class="quiz-header"><h2>کوییز آیین زندگی</h2></div>
            <div class="quiz-content">
                <div class="question-box">برای شروع آزمون، دکمه زیر را بزنید.</div>
                <div class="options"></div>
                <div class="buttons">
                   <button class="btn" id="startLifestyleQuiz">شروع<span class="spotlight"></span></button>
                </div>
                <div class="result"></div>
                <div class="progress-container" style="display:none;"><div class="progress-bar"></div></div>
            </div>
        </div>
        
        <div id="onlineQuizMaker" class="section">
            <h2>آزمون ساز آنلاین (با هوش مصنوعی)</h2>
            <div class="online-maker-tabs">
                <div class="online-maker-tab active" data-content="text-input">ارائه متن</div>
                <div class="online-maker-tab" data-content="topic-input">انتخاب موضوع</div>
            </div>
            <form id="onlineQuizForm" class="online-quiz-form">
                <div id="text-input" class="online-maker-content active">
                    <label for="onlineMakerText">متن خود را اینجا وارد کنید:</label>
                    <textarea id="onlineMakerText" rows="6" placeholder="برای مثال، یک پاراگراف از کتاب درسی خود را کپی کنید..."></textarea>
                </div>
                <div id="topic-input" class="online-maker-content">
                    <label for="onlineMakerTopic">موضوع مورد نظر خود را بنویسید:</label>
                    <input type="text" id="onlineMakerTopic" placeholder="مثلا: تاریخ ایران باستان یا ریاضی نهم فصل اول">
                </div>
                <div class="inline-inputs">
                     <div>
                        <label for="onlineMakerType">نوع سوالات:</label>
                        <select id="onlineMakerType">
                            <option value="multiple_choice">تستی (چهار گزینه‌ای)</option>
                            <option value="descriptive">تشریحی</option>
                        </select>
                    </div>
                    <button type="submit" class="btn" id="onlineMakerBtn">طراحی سوالات<span class="spotlight"></span></button>
                </div>
            </form>
             <div id="online-maker-result" class="result"></div>
        </div>

        <div id="generalQuiz" class="section">
            <div class="quiz-header"><h2>کوییز عمومی</h2></div>
            <div id="general-quiz-setup">
                <p style="text-align: center; margin-bottom: 20px;">یک موضوع را برای شروع انتخاب کنید</p>
                <div class="topic-grid"></div>
            </div>
            <div class="quiz-content" style="display:none;">
                <div class="question-box"></div><div class="options"></div>
                <div class="buttons"></div><div class="result"></div>
                <div class="progress-container" style="display:none;"><div class="progress-bar"></div></div>
            </div>
        </div>
        <div id="quizMaker" class="section">
            <h2>ساخت آزمون سفارشی (دستی)</h2>
            <form id="quizForm" class="quiz-form">
                <fieldset>
                    <legend>۱. مشخصات آزمون</legend>
                    <div class="inline-inputs">
                        <div><label for="customQuizName">نام آزمون:</label><input type="text" id="customQuizName" placeholder="مثلا: آزمون فیزیک" required></div>
                        <div><label for="questionCount">تعداد سوالات:</label><input type="number" id="questionCount" min="1" placeholder="مثلا: ۱۰" required></div>
                        <div><label for="customQuizScore">نمره کل آزمون:</label><input type="number" id="customQuizScore" min="1" max="100" value="20" placeholder="مثلا: ۲۰" required></div>
                    </div>
                    <button type="button" class="btn" id="confirmDetailsBtn">تایید و ادامه<span class="spotlight"></span></button>
                </fieldset>
                <fieldset id="addQuestionFields" disabled>
                    <legend>۲. افزودن سوالات</legend>
                    <label for="questionText">متن سوال:</label><textarea id="questionText" rows="3" required></textarea>
                    <label>گزینه‌ها:</label>
                    <input type="text" id="option1" placeholder="گزینه ۱" required><input type="text" id="option2" placeholder="گزینه ۲" required>
                    <input type="text" id="option3" placeholder="گزینه ۳" required><input type="text" id="option4" placeholder="گزینه ۴" required>
                    <label for="correctOption">شماره گزینه صحیح:</label>
                    <select id="correctOption"><option value="0">گزینه ۱</option><option value="1">گزینه ۲</option><option value="2">گزینه ۳</option><option value="3">گزینه ۴</option></select>
                    <div id="questionCounter">سوالات اضافه شده: ۰ / ۰</div>
                    <button type="submit" class="btn" id="addQuestionBtn">اضافه کردن سوال<span class="spotlight"></span></button>
                </fieldset>
            </form>
            <div id="makerResult" class="result"></div>
            <div class="buttons" id="makerActions">
                <button id="startCustomQuiz" class="btn" style="display:none;">شروع آزمون<span class="spotlight"></span></button>
                <button id="printCustomQuiz" class="btn" style="display:none;">چاپ/ذخیره PDF<span class="spotlight"></span></button>
            </div>
        </div>
        <div id="customQuiz" class="section">
            <div class="quiz-header"><h2 id="customQuizTitle">آزمون شما</h2></div>
            <div class="quiz-content">
                <div class="question-box"></div><div class="options"></div>
                <div class="buttons"></div><div class="result"></div>
                <div class="progress-container" style="display:none;"><div class="progress-bar"></div></div>
           </div>
       </div>
    </div>
    
    <div id="live-results-panel" class="bottom-panel">
        <div class="live-stat"><span class="label">سوال</span><span class="value" id="live-question-count">- / -</span></div>
        <div class="live-stat"><span class="label">پاسخ صحیح</span><span class="value" id="live-score">۰</span></div>
        <div class="live-stat"><span class="label">درصد موفقیت</span><span class="value" id="live-percentage">۰٪</span></div>
        <div class="live-stat"><span class="label" id="live-scaled-score-label">امتیاز</span><span class="value" id="live-scaled-score">۰.۰</span></div>
    </div>

    <div id="maker-helper-panel" class="bottom-panel">
         <div class="live-stat"><span class="label">نام آزمون</span><span class="value" id="helper-quiz-name">وارد نشده</span></div>
         <div class="live-stat"><span class="label">مبنای نمره</span><span class="value" id="helper-quiz-score">۲۰</span></div>
         <div class="live-stat"><span class="label">سوالات باقی‌مانده</span><span class="value" id="helper-questions-remaining">-</span></div>
    </div>

    <svg style="position:absolute; width:0; height:0;"><defs><filter id="gooey"><feGaussianBlur in="SourceGraphic" stdDeviation="10" result="blur" /><feColorMatrix in="blur" mode="matrix" values="1 0 0 0 0  0 1 0 0 0  0 0 1 0 0  0 0 0 18 -7" result="goo" /><feBlend in="SourceGraphic" in2="goo" /></filter></defs></svg>

    <script>
        const plexusBackground = {
            canvas: null, ctx: null, points: [], mouse: { x: null, y: null, maxDistance: 20000 },
            init() {
                this.canvas = document.getElementById('plexus-background');
                this.ctx = this.canvas.getContext('2d');
                this.canvas.width = window.innerWidth; this.canvas.height = window.innerHeight;
                
                window.addEventListener('resize', () => {
                    this.canvas.width = window.innerWidth; this.canvas.height = window.innerHeight;
                    this.mouse.maxDistance = this.canvas.width/7 * this.canvas.height/7;
                });
                
                window.addEventListener('mousemove', (event) => {
                    this.mouse.x = event.x; this.mouse.y = event.y;
                });
                window.addEventListener('mouseout', () => {
                    this.mouse.x = null; this.mouse.y = null;
                });
                
                this.points = [];
                const pointCount = Math.floor(this.canvas.width * this.canvas.height / 9000);
                for (let i = 0; i < pointCount; i++) {
                    this.points.push({
                        x: Math.random() * this.canvas.width, y: Math.random() * this.canvas.height,
                        vx: Math.random() * 0.4 - 0.2, vy: Math.random() * 0.4 - 0.2,
                    });
                }
                this.animate();
            },
            animate() {
                this.ctx.clearRect(0, 0, this.canvas.width, this.canvas.height);
                for(let i = 0; i < this.points.length; i++) {
                    const p1 = this.points[i];
                    p1.x += p1.vx; p1.y += p1.vy;
                    if (p1.x > this.canvas.width + 5) p1.x = -5;
                    else if (p1.x < -5) p1.x = this.canvas.width + 5;
                    if (p1.y > this.canvas.height + 5) p1.y = -5;
                    else if (p1.y < -5) p1.y = this.canvas.height + 5;
                    
                    let distanceToMouse = Math.pow(p1.x - this.mouse.x, 2) + Math.pow(p1.y - this.mouse.y, 2);
                    if(distanceToMouse < this.mouse.maxDistance) {
                        this.ctx.strokeStyle = `rgba(199, 21, 133, ${1 - distanceToMouse/this.mouse.maxDistance})`;
                        this.ctx.lineWidth = 1;
                        this.ctx.beginPath();
                        this.ctx.moveTo(p1.x, p1.y);
                        this.ctx.lineTo(this.mouse.x, this.mouse.y);
                        this.ctx.stroke();
                    }

                    for(let j = i + 1; j < this.points.length; j++) {
                        const p2 = this.points[j];
                        const distance = Math.pow(p1.x - p2.x, 2) + Math.pow(p1.y - p2.y, 2);
                        if(distance < 140*140) {
                            this.ctx.strokeStyle = `rgba(138, 43, 226, ${1 - distance/(140*140)})`;
                            this.ctx.lineWidth = 0.5;
                            this.ctx.beginPath();
                            this.ctx.moveTo(p1.x, p1.y);
                            this.ctx.lineTo(p2.x, p2.y);
                            this.ctx.stroke();
                        }
                    }
                }
                requestAnimationFrame(this.animate.bind(this));
            }
        };

        const jalaliTools = {
            gregorianToJalali(gy, gm, gd) { const g_d_m = [0, 31, 59, 90, 120, 151, 181, 212, 243, 273, 304, 334]; let jy = (gy <= 1600) ? 0 : 979; gy -= (gy <= 1600) ? 621 : 1600; let gy2 = (gm > 2) ? (gy + 1) : gy; let days = (365 * gy) + (parseInt((gy2 + 3) / 4)) - (parseInt((gy2 + 99) / 100)) + (parseInt((gy2 + 399) / 400)) - 80 + gd + g_d_m[gm - 1]; jy += 33 * (parseInt(days / 12053)); days %= 12053; jy += 4 * (parseInt(days / 1461)); days %= 1461; jy += parseInt((days - 1) / 365); if (days > 365) days = (days - 1) % 365; let jm = (days < 186) ? 1 + parseInt(days / 31) : 7 + parseInt((days - 186) / 30); let jd = 1 + ((days < 186) ? (days % 31) : ((days - 186) % 30)); return [jy, jm, jd]; }, isLeapJalali(jy) { const r = (jy + 2346) % 2820; return r < 21 || (r > 25 && r < 2820 && (r+23) % 128 < 30) }, daysInJalaliMonth(jy, jm) { if (jm <= 6) return 31; if (jm <= 11) return 30; return this.isLeapJalali(jy) ? 30 : 29; }, jalaliToGregorian(jy, jm, jd) { let gy = (jy <= 979) ? 621 : 1600; jy -= (jy <= 979) ? 0 : 979; let days = (365 * jy) + (parseInt(jy / 33) * 8) + (parseInt(((jy % 33) + 3) / 4)) + 78 + jd + ((jm < 7) ? (jm - 1) * 31 : ((jm - 7) * 30) + 186); gy += 400 * (parseInt(days / 146097)); days %= 146097; if (days > 36524) { days--; gy += 100 * (parseInt(days / 36524)); days %= 36524; if (days >= 365) days++; } gy += 4 * (parseInt(days / 1461)); days %= 1461; gy += parseInt((days - 1) / 365); if (days > 365) days = (days - 1) % 365; let gd = days + 1; const sal_a = [0, 31, ((gy % 4 === 0 && gy % 100 !== 0) || (gy % 400 === 0)) ? 29 : 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31]; let gm = 0; while (gm < 13 && gd > sal_a[gm]) { gd -= sal_a[gm]; gm++; } return [gy, gm, gd]; }, jalaliMonthNames: ["فروردین", "اردیبهشت", "خرداد", "تیر", "مرداد", "شهریور", "مهر", "آبان", "آذر", "دی", "بهمن", "اسفند"]
        };
        
        const uiManager = {
            dom: {}, jalaliDateState: { year: null, month: null },
            init() {
                this.dom = { timeDisplay: document.getElementById('time-display'), dateDisplay: document.getElementById('date-display'), batteryWidget: document.getElementById('battery-widget'), batteryLevel: document.getElementById('battery-level'), batteryPercentage: document.getElementById('battery-percentage'), clockContainer: document.getElementById('clock-container'), analogClock: document.getElementById('analog-clock'), hourHand: document.getElementById('hour-hand'), minuteHand: document.getElementById('minute-hand'), secondHand: document.getElementById('second-hand'), dateWidget: document.getElementById('date-widget'), calendarPopup: document.getElementById('calendar-popup'), prevMonthBtn: document.getElementById('prev-month'), nextMonthBtn: document.getElementById('next-month'), monthYearDisplay: document.getElementById('month-year-display'), calendarDays: document.querySelector('.calendar-days') };
                this.createClockTicks(); this.updateTime(); setInterval(this.updateTime.bind(this), 1000); this.initBattery(); this.bindEvents();
                const today = new Date(); const [jy, jm] = jalaliTools.gregorianToJalali(today.getFullYear(), today.getMonth() + 1, today.getDate()); this.jalaliDateState = { year: jy, month: jm };
            },
            bindEvents() {
                if (this.dom.clockContainer) this.dom.clockContainer.addEventListener('click', () => this.dom.clockContainer.classList.toggle('show-analog'));
                if (this.dom.dateWidget) this.dom.dateWidget.addEventListener('click', (e) => { e.stopPropagation(); this.dom.calendarPopup.classList.toggle('visible'); if(this.dom.calendarPopup.classList.contains('visible')) this.renderCalendar(); });
                if (this.dom.prevMonthBtn) this.dom.prevMonthBtn.addEventListener('click', (e) => { e.stopPropagation(); this.changeMonth(-1); });
                if (this.dom.nextMonthBtn) this.dom.nextMonthBtn.addEventListener('click', (e) => { e.stopPropagation(); this.changeMonth(1); });
                document.addEventListener('click', (e) => { if (this.dom.calendarPopup && !this.dom.calendarPopup.contains(e.target) && !this.dom.dateWidget.contains(e.target)) this.dom.calendarPopup.classList.remove('visible'); });
            },
            createClockTicks() { const clock = this.dom.analogClock; if (!clock) return; for (let i = 0; i < 12; i++) { const tick = document.createElement('div'); tick.className = 'tick'; tick.style.transform = `rotate(${i * 30}deg)`; clock.appendChild(tick); } },
            updateTime() {
                const now = new Date(); const [jy, jm, jd] = jalaliTools.gregorianToJalali(now.getFullYear(), now.getMonth() + 1, now.getDate()); const weekday = now.toLocaleDateString('fa-IR', { weekday: 'long' });
                if(this.dom.dateDisplay) this.dom.dateDisplay.textContent = `${weekday}، ${new Intl.NumberFormat('fa-IR').format(jd)} ${jalaliTools.jalaliMonthNames[jm - 1]} ${new Intl.NumberFormat('fa-IR').format(jy)}`;
                if(this.dom.timeDisplay) this.dom.timeDisplay.textContent = now.toLocaleTimeString('fa-IR', { hour: '2-digit', minute: '2-digit', second: '2-digit' });
                const seconds = now.getSeconds(); const minutes = now.getMinutes(); const hours = now.getHours();
                const secondsDeg = (seconds / 60) * 360; const minutesDeg = (minutes / 60) * 360 + (seconds / 60) * 6; const hoursDeg = (hours % 12 / 12) * 360 + (minutes / 60) * 30;
                if (this.dom.secondHand) this.dom.secondHand.style.transform = `rotate(${secondsDeg}deg)`; if (this.dom.minuteHand) this.dom.minuteHand.style.transform = `rotate(${minutesDeg}deg)`; if (this.dom.hourHand) this.dom.hourHand.style.transform = `rotate(${hoursDeg}deg)`;
            },
            async initBattery() { if ('getBattery' in navigator) { try { const battery = await navigator.getBattery(); this.updateBatteryUI(battery); battery.addEventListener('chargingchange', () => this.updateBatteryUI(battery)); battery.addEventListener('levelchange', () => this.updateBatteryUI(battery)); } catch (err) { if(this.dom.batteryWidget) this.dom.batteryWidget.style.display = 'none'; } } else { if(this.dom.batteryWidget) this.dom.batteryWidget.style.display = 'none'; } },
            updateBatteryUI(battery) {
                const level = Math.floor(battery.level * 100);
                this.dom.batteryLevel.style.width = `${level}%`;
                this.dom.batteryPercentage.textContent = `${level}%`;
                if (level <= 20) this.dom.batteryLevel.style.backgroundColor = 'var(--incorrect-bg)';
                else if (level <= 50) this.dom.batteryLevel.style.backgroundColor = '#f1c40f';
                else this.dom.batteryLevel.style.backgroundColor = '#11998e';
                this.dom.batteryWidget.classList.toggle('charging', battery.charging);
            },
            changeMonth(direction) { this.jalaliDateState.month += direction; if (this.jalaliDateState.month > 12) { this.jalaliDateState.month = 1; this.jalaliDateState.year++; } else if (this.jalaliDateState.month < 1) { this.jalaliDateState.month = 12; this.jalaliDateState.year--; } this.renderCalendar(); },
            renderCalendar() {
                const { year, month } = this.jalaliDateState; this.dom.monthYearDisplay.textContent = `${jalaliTools.jalaliMonthNames[month - 1]} ${new Intl.NumberFormat('fa-IR').format(year)}`; this.dom.calendarDays.innerHTML = '';
                const today = new Date(); const [currentJy, currentJm, currentJd] = jalaliTools.gregorianToJalali(today.getFullYear(), today.getMonth() + 1, today.getDate());
                const [gy, gm, gd] = jalaliTools.jalaliToGregorian(year, month, 1); const firstDayOfMonth = new Date(gy, gm - 1, gd).getDay(); const faFirstDay = (firstDayOfMonth + 1) % 7;
                for (let i = 0; i < faFirstDay; i++) { this.dom.calendarDays.appendChild(document.createElement('div')).classList.add('empty'); }
                const daysInMonth = jalaliTools.daysInJalaliMonth(year, month);
                for (let i = 1; i <= daysInMonth; i++) { const dayEl = document.createElement('div'); dayEl.textContent = new Intl.NumberFormat('fa-IR').format(i); if (i === currentJd && month === currentJm && year === currentJy) dayEl.classList.add('current-day'); this.dom.calendarDays.appendChild(dayEl); }
            }
        };

        const quizApp = {
            dom: {}, 
            state: { 
                userQuestions: [],
                targetQuestionCount: 0,
                customQuizName: '',
                customQuizBaseScore: 20,
                activeQuizData: [],
                currentQuestionIndex: 0,
                selectedOptionIndex: null,
                activeSectionId: 'lifestyleQuiz',
                score: 0,
                userAnswers: {},
                lastGeneralQuizTopic: null
            },
            generalQuizBank: {
                '9': [ { question: "پایتخت کشور استرالیا کدام شهر است؟", options: ["کانبرا", "سیدنی", "ملبورن", "پرت"], correct: 0 }, { question: "کدام دانشمند قانون جاذبه عمومی را کشف کرد؟", options: ["اسحاق نیوتن", "آلبرت انیشتین", "گالیلئو گالیله", "نیکولا تسلا"], correct: 0 }, { question: "بلندترین قله جهان چه نام دارد؟", options: ["اورست", "کی۲", "کانگچنجونگا", "لوتسه"], correct: 0 }, { question: "کدام سیاره به «سیاره سرخ» معروف است؟", options: ["مریخ", "زهره", "مشتری", "زحل"], correct: 0 }, { question: "واحد پول کشور ژاپن چیست؟", options: ["ین", "یوان", "وون", "دلار"], correct: 0 }, { question: "اثر معروف «دن کیشوت» نوشته کیست؟", options: ["میگل د سروانتس", "ویلیام شکسپیر", "لئو تولستوی", "هومر"], correct: 0 }, { question: "کدام گاز برای تنفس انسان ضروری است؟", options: ["اکسیژن", "نیتروژن", "دی‌اکسید کربن", "هیدروژن"], correct: 0 }, { question: "بزرگترین حیوان روی کره زمین چیست؟", options: ["نهنگ آبی", "فیل آفریقایی", "زرافه", "کوسه سفید"], correct: 0 }, { question: "شعار معروف «آمدم، دیدم، فتح کردم» از کیست؟", options: ["ژولیوس سزار", "اسکندر مقدونی", "ناپلئون بناپارت", "چنگیز خان"], correct: 0 }, { question: "چند قاره در جهان وجود دارد؟", options: ["هفت", "پنج", "شش", "هشت"], correct: 0 } ], '23': [ { question: "جنگ جهانی دوم در چه سالی پایان یافت؟", options: ["۱۹۴۵", "۱۹۳۹", "۱۹۱۸", "۱۹۵۰"], correct: 0 }, { question: "کدام تمدن باستانی در منطقه بین‌النهرین شکوفا شد؟", options: ["سومر", "مصر", "یونان", "روم"], correct: 0 }, { question: "دیوار بزرگ چین به دستور کدام امپراتور ساخته شد؟", options: ["کین شی هوانگ", "هان وودی", "کوبلای خان", "وو زتیان"], correct: 0 }, { question: "رنسانس در کدام کشور اروپایی آغاز شد؟", options: ["ایتالیا", "فرانسه", "اسپانیا", "انگلیس"], correct: 0 }, { question: "کدام رویداد باعث آغاز جنگ جهانی اول شد؟", options: ["ترور آرشیدوک فرانتس فردیناند", "حمله به پرل هاربر", "انقلاب روسیه", "بحران موشکی کوبا"], correct: 0 }, { question: "چه کسی امپراتوری مغول را تاسیس کرد؟", options: ["چنگیز خان", "آتیلا", "تیمور لنگ", "کوبلای خان"], correct: 0 }, { question: "انقلاب صنعتی از کدام کشور آغاز شد؟", options: ["بریتانیا", "آلمان", "ایالات متحده", "فرانسه"], correct: 0 }, { question: "کدام جنگ طولانی‌ترین جنگ در تاریخ آمریکا بود؟", options: ["جنگ افغانستان", "جنگ ویتنام", "جنگ عراق", "جنگ کره"], correct: 0 } ], '18': [ { question: "CPU مخفف چیست؟", options: ["Central Processing Unit", "Computer Personal Unit", "Central Power Unit", "Core Processing Unit"], correct: 0 }, { question: "کدام یک از این‌ها یک زبان برنامه‌نویسی نیست؟", options: ["HTML", "Python", "Java", "C++"], correct: 0 }, { question: "اولین نسخه سیستم عامل ویندوز در چه سالی منتشر شد؟", options: ["۱۹۸۵", "۱۹۹۵", "۲۰۰۱", "۱۹۸۳"], correct: 0 }, { question: "WWW مخفف چیست؟", options: ["World Wide Web", "Wide World Web", "Web World Wide", "World Web Wide"], correct: 0 }, { question: "چه کسی به عنوان پدر علم کامپیوتر شناخته می‌شود؟", options: ["آلن تورینگ", "بیل گیتس", "استیو جابز", "چارلز بابیج"], correct: 0 }, { question: "کدام شرکت پردازنده های سری Core i را تولید می کند؟", options: ["اینتل", "AMD", "انویدیا", "کوالکام"], correct: 0 }, { question: "RAM در کامپیوتر مخفف چیست؟", options: ["Random Access Memory", "Read Only Memory", "Realtime Application Memory", "Rapid Action Memory"], correct: 0 } ], '17': [ { question: "فرآیندی که گیاهان از نور خورشید انرژی تولید می‌کنند چه نام دارد؟", options: ["فتوسنتز", "تنفس سلولی", "تعرق", "گرده افشانی"], correct: 0 }, { question: "بزرگترین اقیانوس جهان کدام است؟", options: ["آرام", "اطلس", "هند", "منجمد جنوبی"], correct: 0 }, { question: "H2O فرمول شیمیایی کدام ماده است؟", options: ["آب", "نمک", "شکر", "اکسیژن"], correct: 0 }, { question: "کدام لایه جو از ما در برابر اشعه‌های مضر فرابنفش محافظت می‌کند؟", options: ["لایه ازون", "تروپوسفر", "مزوسفر", "یونوسفر"], correct: 0 }, { question: "کدام فلز در دمای اتاق مایع است؟", options: ["جیوه", "سرب", "آهن", "آلومینیوم"], correct: 0 } ], '21': [ { question: "بازی‌های المپیک هر چند سال یکبار برگزار می‌شود؟", options: ["چهار سال", "دو سال", "پنج سال", "هر سال"], correct: 0 }, { question: "کدام کشور بیشترین قهرمانی در جام جهانی فوتبال مردان را دارد؟", options: ["برزیل", "آلمان", "ایتالیا", "آرژانتین"], correct: 0 }, { question: "ورزش بسکتبال توسط چه کسی اختراع شد؟", options: ["جیمز نای‌اسمیت", "مایکل جردن", "لبرون جیمز", "کریم عبدالجبار"], correct: 0 }, { question: "در یک مسابقه ماراتن، دوندگان چه مسافتی را می‌دوند؟", options: ["۴۲.۱۹۵ کیلومتر", "۲۰ کیلومتر", "۳۰ کیلومتر", "۵۰ کیلومتر"], correct: 0 }, { question: "ورزش ملی کشور کانادا چیست؟", options: ["هاکی روی یخ", "لاکراس", "بیسبال", "فوتبال کانادایی"], correct: 1 } ]
            },
            lifestyleQuestions: [
                { question: "«اخلاق» به چه دانشی گفته میشود؟", options: ["دانشی که خصال خوب و بد تحسین‌برانگیز را بررسی میکند", "دانشی که تنها به زیبایی‌های ظاهری می‌پردازد", "دانشی که به بررسی رفتارهای غیرارادی انسان می‌پردازد", "دانشی که فقط روی جنبه‌های مالی و اقتصادی تمرکز دارد"], correct: 0 }, { question: "موضوع اخلاق شامل چه مواردی است؟", options: ["رفتار اختیاری و منش و صفات اکتسابی انسان", "فقط رفتارهای عینی و بیرونی", "فقط صفات درونی و اکتسابی", "تنها پدیده‌های طبیعی و غیرارادی"], correct: 0 }, { question: "سازه‌های اصلی یک قضیه اخلاقی کدامند؟", options: ["موضوع، محمول و اسناد", "فاعل، فعل و مفعول", "علت، معلول و نتیجه", "قصد، عمل و پیامد"], correct: 0 }, { question: "بر اساس نظریه نتیجه‌گرایی در فلسفه اخلاق، معیار تعیین درستی یا نادرستی اعمال چیست؟", options: ["نتایج و پیامدهای عمل", "نیت فاعل عمل", "فرمان الهی", "فضیلت‌های اخلاقی"], correct: 0 }, { question: "نظریه وظیفه‌گرایی بر چه معیارهایی برای سنجش ارزش اخلاقی فعل تأکید دارد؟", options: ["ویژگی‌های در خود عمل، فارغ از پیامدها", "تنها نتایج و پیامدهای عمل", "منش و خصلت‌های فاعل", "سود و زیان مادی"], correct: 0 }, { question: "نظریه فضیلت‌گرایی بر چه چیزی تمرکز دارد؟", options: ["منش‌ها و خصلت‌های فاعل عمل", "تک‌رفتارهای فردی", "پیامدهای مستقیم اعمال", "تعیین اعمال صواب و خطا"], correct: 0 }, { question: "تعریف اخلاق کاربردی چیست؟", options: ["کاربرد نظریه‌ها و اصول عام اخلاقی در عرصه‌های خاص زندگی و مسائل و چالش‌های اخلاقی", "شناسایی قواعد اخلاقی عام", "بررسی انواع امور خوب و بد", "تحلیل رفتارهای انسان در کلی‌ترین حالت‌ها"], correct: 0 }, { question: "کدام یک از موارد زیر جزو فواید جنبه فلسفی اخلاق کاربردی محسوب میشود؟", options: ["ایجاد جذابیت در گفت‌وگوهای فلسفه اخلاقی", "افزایش دغدغه‌های اخلاقی افراد جامعه", "کمک به تصمیم‌گیری اخلاقی افراد", "حذف اضطراب در روابط برون حرفه‌ای"], correct: 2 }, { question: "کدام یک از موارد زیر از فواید جنبه حرفه‌ای و عمومی اخلاق کاربردی است؟", options: ["نهادینه شدن اندیشه و رفتار اخلاقی در حرفه و سازمان", "کارایی‌بخشی به مباحث فلسفی اخلاقی", "گشودن پای فیلسوفان به حل معضلات اجتماعی", "خارج کردن مباحث فلسفی از حالت انتزاعی"], correct: 0 }, { question: "کدام دیدگاه درباره رابطه اخلاق کاربردی و اخلاق حرفه‌ای صحیح است؟", options: ["اخلاق حرفه‌ای بخشی از اخلاق کاربردی است", "اخلاق حرفه‌ای و اخلاق کاربردی هیچ نسبتی با هم ندارند", "اخلاق کاربردی زیرمجموعه اخلاق حرفه‌ای است", "اخلاق حرفه‌ای تنها کار فیلسوفان است"], correct: 0 }, { question: "بر اساس فرمایش امام صادق (ع)، حقیقت بندگی در چند چیز دانسته شده است؟", options: ["سه چیز", "دو چیز", "چهار چیز", "یک چیز"], correct: 0 }, { question: "اگر خداوند سه خصلت بندگی را به بنده‌ای عطا کند، چه آثاری در پی دارد؟", options: ["دنیا و شیطان و مردم در نظرش خوار میشوند", "تنها به ثروت و مقام دنیوی دست مییابد", "فقط از مردم عزت و مقام میطلبد", "هیچ تغییری در دیدگاه او نسبت به دنیا ایجاد نمیشود"], correct: 0 }, { question: "مراتب بندگی خدا از نظر امام علی (ع) کدامند؟", options: ["بندگی بازرگانان، بندگی بردگان، بندگی آزادگان", "بندگی از سر عادت، بندگی از سر ترس، بندگی از سر عشق", "بندگی از سر امید، بندگی از سر نیاز، بندگی از سر شکر", "بندگی ظاهری، بندگی باطنی، بندگی خالص"], correct: 0 }, { question: "بزرگترین مانع بندگی خداوند چیست؟", options: ["گناه", "جهل", "فقر", "بیماری"], correct: 0 }, { question: "کدام یک از موارد زیر از شتابدهنده‌های بندگی خدا محسوب میشود؟", options: ["الگوگیری از اسوه‌ها", "تنها مطالعه کتاب‌های دینی", "دوری از اجتماع", "تمرکز بر مشکلات"], correct: 0 }, { question: "چرا دوران جوانی برای اصلاح نفس سزاوارتر است؟", options: ["اراده قوی‌تر است و پاکی درون بیشتر است", "مشکلات زندگی کمتر است", "فرصت‌های اجتماعی بیشتر است", "بار گناهان زیاد شده است"], correct: 0 }, { question: "خلوت‌گزینی درست در سلوک معنوی به چه معناست؟", options: ["رهایی دل از هرگونه تعلق به خلق که مانع یاد خداست", "رها کردن زندگی اجتماعی روزمره", "گوشه‌نشینی و دوری از مردم", "دوری از هرگونه سخن گفتن"], correct: 0 }, { question: "کم‌گویی درست در سلوک معنوی به چه معناست؟", options: ["پرهیز از سخن بیهوده و بی‌نتیجه", "پرهیز از هرگونه سخن گفتن، حتی در جای درست", "سکوت مطلق", "کم‌خوری"], correct: 0 }, { question: "کم‌خوری درست در سلوک معنوی به چه معناست؟", options: ["کاستن غذا به اندازه‌ای که به مزاج انسان آسیب نرسد و توانایی‌ها حفظ شود", "نخوردن غذا تا سرحد بیماری", "پرهیز کامل از غذا", "صرفاً کاهش وزن"], correct: 0 }, { question: "کم‌خوابی درست در سلوک معنوی به چه معناست؟", options: ["داشتن خواب متعادل (حدود ۶ تا ۸ ساعت) و پرهیز از خواب زیاد", "کم‌خوابی مفرط تا جایی که به سلامتی آسیب برسد", "نخوابیدن به طور کلی", "هرگز نخوابیدن در طول شب"], correct: 0 }, { question: "اصل اخلاص در بندگی خداوند به چه معناست؟", options: ["انجام اعمال عبادی تنها با انگیزه الهی و بدون انگیزه‌های دیگر", "انجام عبادت برای کسب شهرت و مقام", "انجام عبادت به دلیل ترس از مجازات الهی", "انجام عبادت برای رسیدن به منافع مادی"], correct: 0 }, { question: "اصل احترام در بندگی خداوند به چه معناست؟", options: ["ارزش نهادن به خالق هستی و بروز آن در رفتار عبادی", "انجام عبادت از روی عادت", "توجه فقط به ظاهر عبادات", "بی‌تفاوتی نسبت به یتیمان و فقرا"], correct: 0 }, { question: "معنای درست «توکل» به خدا چیست؟", options: ["واگذاری امور به خدا و انتخاب او به عنوان وکیل، همراه با استفاده از اسباب مادی", "رها کردن هرگونه تلاش و انتظار از خدا برای حل مشکلات", "صرفاً دعا کردن بدون هیچ اقدام عملی", "تنها اعتماد به اسباب و علل مادی"], correct: 0 }, { question: "جایگاه نماز در منطق بندگی دینداری چیست؟", options: ["مظهر نیاز، خضوع و اطاعت مخلوق از خالق", "صرفاً یک تکلیف شرعی بدون معنا", "راهی برای حل مشکلات مادی", "فعالیتی که فقط برای مسلمانان واجب است"], correct: 0 }, { question: "نخستین گام برای توجه قلبی در نماز چیست؟", options: ["وضوی باطنی و طهارت قلبی", "پوشیدن لباس تمیز", "انتخاب مکان خلوت", "بلند خواندن اذکار نماز"], correct: 0 }, { question: "منظور از «استقبال دل» در آداب مقدمات نماز چیست؟", options: ["روی گردانی دل از تعلقات غیرالهی و روی آوردن کامل به خداوند", "رو به قبله ایستادن", "انتظار کشیدن برای اذان", "صحبت با دیگران قبل از نماز"], correct: 0 }, { question: "منظور از «گفت‌وگوی قریبانه با خدای سبحان» در نماز چیست؟", options: ["مناجات همراه با خشوع و ذکر خداوند", "صرفاً تلاوت قرآن", "انجام حرکات فیزیکی نماز", "صحبت کردن با خود"], correct: 0 }, { question: "ادب قرائت در نماز شامل چه چیزی است؟", options: ["توجه عمیق به معانی اذکار و عظمت مخاطب (خداوند)", "صرفاً درست تلفظ کردن کلمات", "سریع خواندن سوره‌ها", "نادیده گرفتن معانی"], correct: 0 }, { question: "رکوع در نماز نماد چیست؟", options: ["سر تعظیم فروآوردن در برابر پروردگار بزرگ", "اظهار وجود", "درخواست حاجت", "آمادگی برای ایستادن"], correct: 0 }, { question: "سجده در نماز نشانه چیست؟", options: ["عبودیت، تذلل و خاکساری در برابر خداوند", "برابری با دیگران", "قدرت و بزرگی انسان", "فراموشی دنیا"], correct: 0 }, { question: "در زندگی امروزی، مدیریت خویشتن چه جایگاهی دارد؟", options: ["عامل اصلی در انتخابگری و شرط موفقیت", "عاملی بی‌تأثیر در موفقیت", "تنها مربوط به جنبه‌های مالی", "تنها مربوط به زندگی سنتی"], correct: 0 }, { question: "نگرش عمیق به زندگی از منظر ادیان ابراهیمی به چه معناست؟", options: ["باور به هدفمند بودن زندگی و انتخاب‌های انسانی", "تمرکز بر خوشی‌های آنی", "بی‌توجهی به پیامدهای اعمال", "نگاه ابزاری به دیگران"], correct: 0 }, { question: "برای افزایش خودآگاهی چه باید کرد؟", options: ["اجتناب از نادیده‌گرفتن آگاهی درباره خویشتن", "صرفاً به نظر دیگران توجه کردن", "تمرکز بر نقاط ضعف دیگران", "نادیده گرفتن احساسات درونی"], correct: 0 }, { question: "فردی که خود را بیان میکند، چگونه عمل میکند؟", options: ["افکار و احساسات درونی خود را در زمان مناسب و مسئولانه با دیگران در میان میگذارد", "احساسات خود را بدون توجیه و عذرخواهی بیان میکند", "در ابراز افکار و احساسات دچار افراط و تفریط میشود", "از فاش کردن احساسات خود خجالت میکشد"], correct: 0 }, { question: "پذیرش خود به چه معناست؟", options: ["احترام به نفس بر اساس آگاهی از نقاط قوت و ضعف خود", "خودشیفتگی و غرور", "نادیده گرفتن اشتباهات خود", "مقایسه دائمی خود با دیگران"], correct: 0 }, { question: "تعریف «عزت نفس» چیست؟", options: ["ارزیابی صادقانه خود و برداشتی واقع‌بینانه و تحسین‌آمیز از خویش", "خودشیفتگی و غرور بیجا", "شرم و خجالت بی‌مورد", "مقایسه دائمی خود با دیگران"], correct: 0 }, { question: "عوامل سه‌گانه تقویت‌کننده عزت نفس کدامند؟", options: ["ارزش انسانی بی‌قید و شرط، محبت و عشق، رشد", "ثروت، قدرت، شهرت", "زیبایی، هوش، مهارت", "هوش، استعداد، تلاش"], correct: 0 }, { question: "مفهوم «ارزش انسانی بی‌قید و شرط» به چه معناست؟", options: ["هر انسانی دارای ارزشی ذاتی، ثابت و مستقل از عوامل بیرونی است", "ارزش انسان تنها با پول و قیافه تعیین میشود", "ارزش انسان با عملکرد و پیشرفت‌ها افزایش مییابد", "ارزش انسان بر اساس مقایسه با دیگران تعیین میشود"], correct: 0 }, { question: "منظور از «اتقان در فعالیت» در اخلاق فردی چیست؟", options: ["انجام دادن کارها با استحکام و دقت", "انجام دادن کارها به سرعت", "نیمه‌تمام گذاشتن کارها", "انجام ندادن کارها"], correct: 0 }, { question: "جایگاه «ناامیدی» در ادبیات دینی چیست؟", options: ["از گناهان کبیره به شمار میآید", "صفتی ممدوح است", "موجب پیشرفت انسان میشود", "عاملی برای افزایش تلاش"], correct: 0 }, { question: "«خود نظم‌جویی» به چه معناست؟", options: ["توانایی مهار ارادی بر زندگی و رفتار خود", "رها کردن خود در برابر خواسته‌های نفسانی", "پیروی از الگوهای رفتاری دیگران", "ناتوانی در تصمیم‌گیری"], correct: 0 }, { question: "خود نظم‌جویی بر چه ایده‌ای استوار است و به چه توانایی‌هایی اشاره دارد؟", options: ["خود تأملی و توانایی تغییر رفتار به سمت اهداف پسندیده", "صرفاً مهار هیجانات", "تنها خود نظارتگری", "بی‌توجهی به اهداف"], correct: 0 }, { question: "در اخلاق عفت، «کنترل مجاری دریافتی به ویژه نگاه» به چه منظوری است؟", options: ["جلوگیری از آغاز شدن مشکلات اخلاقی جنسی", "صرفاً رعایت آداب اجتماعی", "دوری از ارتباط با دیگران", "عدم استفاده از فضای مجازی"], correct: 0 }, { question: "کنترل «خیال و تصویرسازی ذهنی» در اخلاق عفت چه نقشی دارد؟", options: ["جلوگیری از غلیان هیجانات و سوق یافتن به رفتارهای نامناسب جنسی", "افزایش خلاقیت", "تقویت حافظه", "افزایش تمرکز"], correct: 0 }, { question: "«سالم‌سازی محیط» در اخلاق عفت به چه معناست؟", options: ["مدیریت هوشمندانه ابزارهای ارتباطی و ایجاد محیطی سالم برای رشد", "فقط پاکسازی فیزیکی محیط", "دوری کامل از تکنولوژی", "انزوای اجتماعی"], correct: 0 }, { question: "کدام یک از موارد زیر جزو کارکردهای اصلی خانواده محسوب میشود؟", options: ["تولیدمثل و جامعه‌پذیری", "صرفاً تأمین نیازهای اقتصادی", "تنها تفریح و سرگرمی", "ایجاد رقابت"], correct: 0 }, { question: "نقش «محبت» در اخلاق خانواده چیست؟", options: ["نیروی عظیمی برای ایجاد کشش و میل بین اعضای خانواده", "صرفاً یک حس عاطفی بدون عمل", "ایجاد رقابت بین اعضا", "دوری از مسئولیت‌پذیری"], correct: 0 }, { question: "«احترام» در اخلاق خانواده به چه معناست؟", options: ["ارزش نهادن به ارزش ذاتی اعضای خانواده و توجه به آنان", "پیروی بی‌چون‌وچرا از خواسته‌های دیگران", "نادیده‌گرفتن اشتباهات", "بی‌تفاوتی نسبت به احساسات"], correct: 0 }, { question: "«مسئولیت‌پذیری» در اخلاق خانواده به چه معناست؟", options: ["انجام وظایف متناسب با نقش خود برای رفاه و موفقیت خانواده", "انجام دادن کارهای دیگران", "نادیده گرفتن وظایف خود", "تنها تمرکز بر حقوق خود"], correct: 0 }, { question: "«سخت‌کوشی و همت بلند و هدف عالی» در دانشوری به چه معناست؟", options: ["جدیت در علم‌آموزی و تلاش برای یافتن راه‌های جدید در دانش", "صرفاً مطالعه بدون تلاش", "تقلید از دیگران", "بی‌توجهی به هدف"], correct: 0 }, { question: "«تواضع و احترام و ادب» در دانشوری به چه معناست؟", options: ["تواضع در برابر دیگران و دوری از غرور علمی", "نادیده گرفتن توانایی‌های خود", "تملق در برابر استادان", "تنها تمرکز بر موفقیت‌های شخصی"], correct: 0 }, { question: "وظیفه اخلاقی دانشجو در برابر استادان چیست؟", options: ["حفظ احترام استاد در گفتار و نوشتار و رفتار", "انتقاد تند و بی‌ادبانه", "بی‌توجهی به راهنمایی‌ها", "تلاش برای فریب دادن استاد"], correct: 0 }, { question: "کدام یک از موارد زیر از وظایف اخلاقی دانشجو در برابر همکلاسی‌ها است؟", options: ["شمردن همکلاسی‌ها به مثابه یارانی در جهت موفقیت جمعی", "رقابت ناسالم", "غیبت و حسادت", "بی‌توجهی به حقوق دیگران"], correct: 0 }, { question: "کدام یک از موارد زیر از مصادیق «سرقت علمی» محسوب میشود؟", options: ["استفاده از زبان، فکر یا نوشته دیگران به نام خود", "ارجاع مناسب به منابع", "همکاری در پژوهش", "انتشار مجدد کار خود"], correct: 0 }, { question: "مدیریت معیشت دربرگیرنده چه مواردی است؟", options: ["انضباط مالی، مسئولیت‌پذیری، قاطعیت", "تنها جمع‌آوری ثروت", "اسراف در مصرف", "بی‌برنامه‌ریزی در هزینه‌ها"], correct: 0 }, { question: "«انضباط مالی» در کسب درآمد به چه معناست؟", options: ["برنامه‌ریزی دقیق برای درآمد و هزینه", "کسب درآمد به هر روشی", "عدم مسئولیت‌پذیری مالی", "نادیده گرفتن تعهدات"], correct: 0 }, { question: "کدام یک از موارد زیر جزو قواعد اخلاقی در مصرف است؟", options: ["اعتدال و اولویت‌بندی در مصرف", "مصرف‌گرایی بی‌حد و حصر", "احتکار", "عدم بخشش"], correct: 0 }, { question: "«پس‌انداز هدفمند» به چه معناست؟", options: ["پس‌انداز با هدف مشخص و برنامه‌ریزی شده", "پس‌انداز بدون هیچ هدف", "مصرف تمام درآمد", "قرض گرفتن مداوم"], correct: 0 }, { question: "«اصل هدفداری» در اخلاق اوقات فراغت به چه معناست؟", options: ["استفاده از اوقات فراغت با هدف رفع نواقص، برآوردن نیازهای آینده و انسان‌سازی", "صرفاً گذراندن وقت به هر شکلی", "بی‌توجهی به برنامه‌ریزی", "فقط تفریح و سرگرمی"], correct: 0 }
            ],
            
            init() { this.cacheDom(); this.bindEvents(); this.resetQuizMakerForm(); this.loadPersistedCustomQuiz(); this.populateTopicCards(); setTimeout(() => this.positionTabIndicator(), 100); },
            cacheDom() { this.dom = { tabs: document.querySelectorAll('.tab'), sections: document.querySelectorAll('.section'), logos: document.querySelectorAll('.logo-ar'), tabsContainer: document.querySelector('.tabs'), tabIndicator: document.getElementById('active-tab-indicator'), liveResultsPanel: document.getElementById('live-results-panel'), liveQuestionCount: document.getElementById('live-question-count'), liveScore: document.getElementById('live-score'), livePercentage: document.getElementById('live-percentage'), liveScaledScore: document.getElementById('live-scaled-score'), liveScaledScoreLabel: document.getElementById('live-scaled-score-label'), makerHelperPanel: document.getElementById('maker-helper-panel'), helperQuizName: document.getElementById('helper-quiz-name'), helperQuizScore: document.getElementById('helper-quiz-score'), helperQuestionsRemaining: document.getElementById('helper-questions-remaining'), startLifestyleQuizBtn: document.getElementById('startLifestyleQuiz'), topicGrid: document.querySelector('#generalQuiz .topic-grid'), generalQuizSetup: document.getElementById('general-quiz-setup'), quizForm: document.getElementById('quizForm'), customQuizNameInput: document.getElementById('customQuizName'), questionCountInput: document.getElementById('questionCount'), customQuizScore: document.getElementById('customQuizScore'), confirmDetailsBtn: document.getElementById('confirmDetailsBtn'), addQuestionFields: document.getElementById('addQuestionFields'), questionCounterEl: document.getElementById('questionCounter'), makerActions: document.getElementById('makerActions'), startCustomQuizBtn: document.getElementById('startCustomQuiz'), printCustomQuizBtn: document.getElementById('printCustomQuiz'), customQuizTab: document.getElementById('customQuizTab'), customQuizTabTitle: document.getElementById('customQuizTabTitle'), deleteCustomQuizTabBtn: document.getElementById('deleteCustomQuizTab'), onlineQuizForm: document.getElementById('onlineQuizForm'), onlineMakerResult: document.getElementById('online-maker-result'), onlineMakerTabs: document.querySelectorAll('.online-maker-tab') }; },
            bindEvents() {
                this.dom.tabs.forEach(tab => tab.addEventListener('click', (e) => this.handleTabClick(e)));
                this.dom.logos.forEach(logo => {
                    logo.addEventListener('mousemove', this.handleLogoTilt.bind(this));
                    logo.addEventListener('mouseleave', (e) => {
                        e.currentTarget.style.transform = 'rotateX(0deg) rotateY(0deg) scale(1)';
                    });
                });
                this.dom.startLifestyleQuizBtn.addEventListener('click', () => this.loadQuiz(this.shuffle(this.lifestyleQuestions), 'lifestyleQuiz', 'کوییز آیین زندگی'));
                this.dom.topicGrid.addEventListener('click', (e) => { const card = e.target.closest('.topic-card'); if (card) { this.startGeneralQuiz(card.dataset.categoryId, card.dataset.categoryName); } });
                this.dom.confirmDetailsBtn.addEventListener('click', this.setupQuizMaker.bind(this));
                this.dom.quizForm.addEventListener('submit', this.addCustomQuestion.bind(this));
                this.dom.makerActions.addEventListener('click', (e) => { const target = e.target.closest('button'); if(!target) return; if (target.id === 'startCustomQuiz') this.startCustomQuiz(); if (target.id === 'printCustomQuiz') this.handlePrintQuiz(); });
                if(this.dom.deleteCustomQuizTabBtn) { this.dom.deleteCustomQuizTabBtn.addEventListener('click', this.deleteCustomQuiz.bind(this)); }
                [this.dom.customQuizNameInput, this.dom.questionCountInput, this.dom.customQuizScore].forEach(el => { el.addEventListener('keyup', this.updateMakerHelper.bind(this)); el.addEventListener('change', this.updateMakerHelper.bind(this)); });
                
                // New event listeners for Online Quiz Maker
                this.dom.onlineQuizForm.addEventListener('submit', this.handleOnlineQuizGeneration.bind(this));
                this.dom.onlineMakerTabs.forEach(tab => {
                    tab.addEventListener('click', (e) => this.handleOnlineMakerTabClick(e));
                });
                
                window.addEventListener('resize', this.positionTabIndicator.bind(this));
                this.rebindSpotlightListeners();
            },
            rebindSpotlightListeners() { 
                document.querySelectorAll('.btn').forEach(btn => { 
                    const spotlight = btn.querySelector('.spotlight')
                    if(spotlight) {
                        btn.removeEventListener('mousemove', this.handleButtonSpotlight); 
                        btn.addEventListener('mousemove', this.handleButtonSpotlight.bind(this)); 
                    }
                }); 
            },
            handleLogoTilt(e) { 
                const logo = e.currentTarget; 
                const { clientX, clientY } = e; 
                const { left, top, width, height } = logo.getBoundingClientRect(); 
                const x = (clientX - (left + width / 2)) / (width/2); 
                const y = (clientY - (top + height / 2)) / (height/2); 
                logo.style.transform = `perspective(1000px) rotateY(${x * 15}deg) rotateX(${-y * 15}deg) scale(1.1)`;
            },
            handleButtonSpotlight(e) { const btn = e.currentTarget; const spotlight = btn.querySelector('.spotlight'); if(!spotlight) return; const { left, top } = btn.getBoundingClientRect(); spotlight.style.setProperty('--x', `${e.clientX - left}px`); spotlight.style.setProperty('--y', `${e.clientY - top}px`); },
            positionTabIndicator() { const activeTab = this.dom.tabsContainer.querySelector('.tab.active'); if(activeTab){ this.dom.tabIndicator.style.width = `${activeTab.offsetWidth}px`; this.dom.tabIndicator.style.left = `${activeTab.offsetLeft}px`; } },
            handleTabClick(e) {
                const tab = e.target.closest('.tab'); if (!tab || tab.classList.contains('active')) return; if (e.target.closest('.delete-tab-btn')) { this.deleteCustomQuiz(e); return; } if (tab.style.display === 'none') return;
                const targetId = tab.dataset.target;
                this.dom.sections.forEach(s => s.classList.remove('active', 'section-reveal', 'section-glitch', 'section-modular', 'section-flip'));
                const targetSection = document.getElementById(targetId);
                switch(targetId) { case 'lifestyleQuiz': case 'onlineQuizMaker': targetSection.classList.add('section-reveal'); break; case 'generalQuiz': targetSection.classList.add('section-glitch'); break; case 'quizMaker': targetSection.classList.add('section-modular'); break; case 'customQuiz': targetSection.classList.add('section-flip'); break; }
                this.dom.tabs.forEach(t => t.classList.remove('active'));
                tab.classList.add('active'); targetSection.classList.add('active');
                this.state.activeSectionId = targetId; this.positionTabIndicator();
                this.dom.liveResultsPanel.classList.remove('visible');
                if (targetId === 'quizMaker') { this.dom.makerHelperPanel.classList.add('visible'); this.updateMakerHelper(); }
                else { this.dom.makerHelperPanel.classList.remove('visible'); }
                if(targetId === 'generalQuiz') { const quizContent = document.querySelector('#generalQuiz .quiz-content'); if (quizContent) quizContent.style.display = 'none'; if (this.dom.generalQuizSetup) this.dom.generalQuizSetup.style.display = 'block'; }
            },
            handleOnlineMakerTabClick(e) {
                const clickedTab = e.currentTarget;
                this.dom.onlineMakerTabs.forEach(tab => tab.classList.remove('active'));
                clickedTab.classList.add('active');
                
                const contentId = clickedTab.dataset.content;
                document.querySelectorAll('.online-maker-content').forEach(content => content.classList.remove('active'));
                document.getElementById(contentId).classList.add('active');
            },
            handleOnlineQuizGeneration(e) {
                e.preventDefault();
                this.dom.onlineMakerResult.innerHTML = `
                    <p style="color: var(--text-muted);">
                        این قابلیت نیازمند اتصال به اینترنت و سرویس‌های هوش مصنوعی است. 
                        <br>
                        پس از اتصال برنامه به اینترنت، این بخش به طور خودکار فعال خواهد شد.
                    </p>
                `;
            },
            populateTopicCards() {
                const grid = this.dom.topicGrid; if (!grid) return; grid.innerHTML = '';
                const topics = { '9': {name: 'اطلاعات عمومی', icon: '<path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm-1 17.93c-3.95-.49-7-3.85-7-7.93 0-.62.08-1.21.21-1.79L9 15v1c0 1.1.9 2 2 2v-2.07zM18.93 10.21c-.13.58-.21 1.17-.21 1.79 0 4.08-3.05 7.44-7 7.93V18c0-1.1-.9-2-2-2v-1l6.79-6.79c.58.13 1.17.21 1.79.21.62 0 1.21-.08 1.79-.21z"/>'}, '23': {name: 'تاریخ', icon: '<path d="M19 4h-1V2h-2v2H8V2H6v2H5c-1.11 0-1.99.9-1.99 2L3 20c0 1.1.89 2 2 2h14c1.1 0 2-.9 2-2V6c0-1.1-.9-2-2-2zm0 16H5V10h14v10z"/>'}, '18': {name: 'تکنولوژی', icon: '<path d="M20 18c1.1 0 1.99-.9 1.99-2L22 6c0-1.1-.9-2-2-2H4c-1.1 0-2 .9-2 2v10c0 1.1.9 2 2 2H0v2h24v-2h-4zM4 6h16v10H4V6z"/>'}, '17': {name: 'علم و طبیعت', icon: '<path d="M17.66 7.93 12 2.27 6.34 7.93a8.008 8.008 0 0 0 11.32 0zM12 17.73c-3.14 0-6-1.95-6-5.08 0-2.05 1.23-3.83 3-4.68.77-.36 1.6-.55 2.48-.55l.52.01c.88.06 1.71.25 2.48.55 1.77.85 3 2.63 3 4.68 0 3.13-2.86 5.08-6 5.08z"/>'}, '21': {name: 'ورزش', icon: '<path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm3.62 14.35c-1.16 1.34-2.82 2.15-4.62 2.15s-3.46-.81-4.62-2.15C5.23 15.02 5.06 13.57 5.5 12.1c.43-1.48 1.68-2.6 3.2-3.02.5-.13 1.02-.2 1.55-.2.55 0 1.05.07 1.55.2 1.52.42 2.77 1.54 3.2 3.02.44 1.47.27 2.92-.88 4.25z"/>'} };
                for (const id in topics) { const card = document.createElement('div'); card.className = 'topic-card'; card.dataset.categoryId = id; card.dataset.categoryName = topics[id].name; card.innerHTML = `<svg viewBox="0 0 24 24">${topics[id].icon}</svg><span>${topics[id].name}</span>`; grid.appendChild(card); }
            },
            
            shuffleOptions(question) {
                const newQuestion = JSON.parse(JSON.stringify(question)); // Deep copy
                const correctAnswerText = newQuestion.options[newQuestion.correct];
                this.shuffle(newQuestion.options);
                const newCorrectIndex = newQuestion.options.indexOf(correctAnswerText);
                newQuestion.correct = newCorrectIndex;
                return newQuestion;
            },

            startGeneralQuiz(category, name) { 
                this.state.lastGeneralQuizTopic = { category, name };
                const bank = this.generalQuizBank[category] || [];
                if (bank.length === 0) { alert('متاسفانه سوالی برای این موضوع یافت نشد.'); return; }
                const shuffled = this.shuffle(bank);
                const questions = shuffled.slice(0, 10);
                this.loadQuiz(questions, 'generalQuiz', name);
            },

            loadQuiz(questions, sectionId, quizTitle) {
                if (sectionId === 'lifestyleQuiz' || sectionId === 'generalQuiz') {
                    this.state.activeQuizData = questions.map(q => this.shuffleOptions(q));
                } else {
                    this.state.activeQuizData = questions;
                }
                
                this.state.activeSectionId = sectionId;
                this.state.currentQuestionIndex = 0;
                this.state.score = 0;
                this.state.selectedOptionIndex = null;
                this.state.userAnswers = {};
                
                const section = document.getElementById(sectionId);
                const h2 = section.querySelector('h2');
                if (h2) h2.textContent = quizTitle;
                
                const quizContent = section.querySelector('.quiz-content');
                if(quizContent) {
                    const progressContainer = quizContent.querySelector('.progress-container');
                    if (progressContainer) progressContainer.style.display = 'block';
                    quizContent.style.display = 'block';
                }
                
                if (section.querySelector('#general-quiz-setup')) {
                    section.querySelector('#general-quiz-setup').style.display = 'none';
                }
                
                this.dom.makerHelperPanel.classList.remove('visible');
                if (sectionId !== 'quizMaker' && sectionId !== 'onlineQuizMaker') {
                    this.dom.liveResultsPanel.classList.add('visible');
                }
                
                this.displayQuestion();
            },

            displayQuestion() {
                try {
                    const questionData = this.state.activeQuizData[this.state.currentQuestionIndex];
                    if (!questionData || !Array.isArray(questionData.options)) {
                        console.error("Invalid question data at index " + this.state.currentQuestionIndex, questionData);
                        alert("خطا در بارگذاری سوال.");
                        return;
                    }

                    const quizContent = document.querySelector(`#${this.state.activeSectionId} .quiz-content`);
                    quizContent.querySelector('.question-box').innerHTML = `${this.state.currentQuestionIndex + 1}. ${questionData.question}`;
                    const optionsContainer = quizContent.querySelector('.options');
                    optionsContainer.innerHTML = '';
                    
                    questionData.options.forEach((option, index) => {
                        const optionEl = document.createElement('div');
                        optionEl.className = 'option';
                        optionEl.textContent = option;
                        optionEl.addEventListener('click', () => this.selectOption(optionEl, index));
                        optionsContainer.appendChild(optionEl);
                    });
                    
                    const buttonsContainer = quizContent.querySelector('.buttons');
                    buttonsContainer.innerHTML = `<button class="btn">بررسی پاسخ<span class="spotlight"></span></button>`;
                    buttonsContainer.querySelector('.btn').addEventListener('click', this.checkAnswer.bind(this));
                    this.rebindSpotlightListeners();
                    quizContent.querySelector('.result').innerHTML = '';
                    this.updateProgress();
                } catch(error) {
                    console.error("Error in displayQuestion: ", error);
                    alert("خطایی در نمایش سوال رخ داد.");
                }
            },

            selectOption(selectedEl, index) { 
                if (document.querySelector(`#${this.state.activeSectionId} .buttons .nav-btn`)) return;
                const options = document.querySelectorAll(`#${this.state.activeSectionId} .option`);
                options.forEach(opt => opt.classList.remove('selected'));
                selectedEl.classList.add('selected');
                this.state.selectedOptionIndex = index;
            },

            checkAnswer() {
                if (this.state.selectedOptionIndex === null) { alert('لطفاً یک گزینه را انتخاب کنید.'); return; }
                const questionData = this.state.activeQuizData[this.state.currentQuestionIndex];
                const correctIndex = questionData.correct;
                const options = document.querySelectorAll(`#${this.state.activeSectionId} .option`);
                const resultEl = document.querySelector(`#${this.state.activeSectionId} .result`);
                options.forEach(opt => { opt.style.pointerEvents = 'none'; });
                options[this.state.selectedOptionIndex].classList.remove('selected');
                this.state.userAnswers[this.state.currentQuestionIndex] = this.state.selectedOptionIndex;
                if (this.state.selectedOptionIndex === correctIndex) {
                    this.state.score++;
                    options[this.state.selectedOptionIndex].classList.add('correct');
                    resultEl.textContent = 'آفرین، صحیح بود!';
                } else {
                    options[this.state.selectedOptionIndex].classList.add('incorrect');
                    options[correctIndex].classList.add('correct');
                    resultEl.textContent = 'اشتباه بود!';
                }
                this.updateProgress();
                const buttonsContainer = document.querySelector(`#${this.state.activeSectionId} .buttons`);
                let nextButtonText = (this.state.currentQuestionIndex === this.state.activeQuizData.length - 1) ? 'مشاهده نتایج' : 'سوال بعدی';
                buttonsContainer.innerHTML = `<button class="btn nav-btn">${nextButtonText}<span class="spotlight"></span></button>`;
                buttonsContainer.querySelector('.btn').addEventListener('click', this.navigateNext.bind(this));
                this.rebindSpotlightListeners();
            },

            navigateNext() { this.state.currentQuestionIndex++; this.state.selectedOptionIndex = null; if (this.state.currentQuestionIndex < this.state.activeQuizData.length) { this.displayQuestion(); } else { this.showFinalResults(); } },
            
            showFinalResults() {
                this.dom.liveResultsPanel.classList.remove('visible');
                const quizContent = document.querySelector(`#${this.state.activeSectionId} .quiz-content`); if(!quizContent) return;
                if(quizContent.querySelector('.progress-container')) { quizContent.querySelector('.progress-container').style.display = 'none'; }
                let baseScore = 20, scoreFromText = `از ${baseScore}`; if(this.state.activeSectionId === 'customQuiz') { baseScore = this.state.customQuizBaseScore; scoreFromText = `از ${baseScore}`; } else if (this.state.activeSectionId === 'generalQuiz') { baseScore = 100; scoreFromText = `از ${baseScore}`; }
                const scaledScore = (this.state.activeQuizData.length > 0) ? (this.state.score / this.state.activeQuizData.length) * baseScore : 0;
                
                quizContent.querySelector('.question-box').innerHTML = `<div class="final-score-container"><p class="score-title">نمره نهایی شما</p><div class="score-value" id="finalScoreDisplay">0.0</div><p class="score-base">${scoreFromText}</p></div>`;
                quizContent.querySelector('.options').innerHTML = '';
                quizContent.querySelector('.result').textContent = `شما به ${this.state.score} از ${this.state.activeQuizData.length} سوال پاسخ صحیح دادید.`;
                
                quizContent.querySelector('.buttons').innerHTML = `<button class="btn" id="restart-quiz">آزمون مجدد<span class="spotlight"></span></button>`; 
                this.animateScore(scaledScore);

                quizContent.querySelector('#restart-quiz').addEventListener('click', () => {
                    if (this.state.activeSectionId === 'generalQuiz') {
                        if (this.state.lastGeneralQuizTopic) {
                           this.startGeneralQuiz(this.state.lastGeneralQuizTopic.category, this.state.lastGeneralQuizTopic.name);
                        } else {
                           quizContent.style.display = 'none';
                           this.dom.generalQuizSetup.style.display = 'block';
                        }
                    } else if (this.state.activeSectionId === 'lifestyleQuiz') {
                        this.loadQuiz(this.shuffle(this.lifestyleQuestions), 'lifestyleQuiz', 'کوییز آیین زندگی');
                    } else if (this.state.activeSectionId === 'customQuiz') {
                        this.loadQuiz(JSON.parse(localStorage.getItem('userQuestions')) || [], 'customQuiz', localStorage.getItem('customQuizName') || "آزمون شما");
                    }
                });
                this.rebindSpotlightListeners();
            },

            animateScore(finalScore) {
                const scoreDisplay = document.getElementById('finalScoreDisplay');
                if (!scoreDisplay) return;
                const end = parseFloat(finalScore);
                const duration = 1500;
                
                if (end === 0) {
                    scoreDisplay.textContent = '0.0';
                    return;
                }

                let startTime = null;

                const step = (currentTime) => {
                    if (!startTime) startTime = currentTime;
                    const elapsedTime = currentTime - startTime;
                    const progress = Math.min(elapsedTime / duration, 1);
                    const currentScore = progress * end;
                    scoreDisplay.textContent = currentScore.toFixed(1);

                    if (progress < 1) {
                        requestAnimationFrame(step);
                    } else {
                        scoreDisplay.textContent = end.toFixed(1);
                    }
                };
                requestAnimationFrame(step);
            },
            
            updateProgress() {
                const quizContent = document.querySelector(`#${this.state.activeSectionId} .quiz-content`); if(!quizContent) return; const progressBar = quizContent.querySelector('.progress-bar'); if(!progressBar || !this.state.activeQuizData || this.state.activeQuizData.length === 0) return;
                const progressPercent = ((this.state.currentQuestionIndex) / this.state.activeQuizData.length) * 100; progressBar.style.width = `${progressPercent}%`;
                if (this.dom.liveResultsPanel.classList.contains('visible')) {
                    const totalQuestions = this.state.activeQuizData.length; const answeredCount = Object.keys(this.state.userAnswers).length; const percentage = answeredCount > 0 ? Math.round((this.state.score / answeredCount) * 100) : 0;
                    let baseScore = 20, labelText = `امتیاز از ${baseScore}`; if (this.state.activeSectionId === 'generalQuiz') { baseScore = 100; labelText = `امتیاز از ${baseScore}`; } else if (this.state.activeSectionId === 'customQuiz') { baseScore = this.state.customQuizBaseScore; labelText = `امتیاز از ${baseScore}`; }
                    const scaledScore = (totalQuestions > 0) ? (this.state.score / totalQuestions) * baseScore : 0;
                    this.dom.liveQuestionCount.textContent = `${this.state.currentQuestionIndex + 1} / ${totalQuestions}`; this.dom.liveScore.textContent = this.state.score; this.dom.livePercentage.textContent = `${percentage}٪`; this.dom.liveScaledScoreLabel.textContent = labelText; this.dom.liveScaledScore.textContent = scaledScore.toFixed(1);
                }
            },
            updateMakerHelper() { this.dom.helperQuizName.textContent = this.dom.customQuizNameInput.value || 'وارد نشده'; this.dom.helperQuizScore.textContent = this.dom.customQuizScore.value || '-'; const remaining = (this.dom.questionCountInput.value || 0) - this.state.userQuestions.length; this.dom.helperQuestionsRemaining.textContent = Math.max(0, remaining); },
            setupQuizMaker() { this.state.customQuizName = this.dom.customQuizNameInput.value.trim(); this.state.targetQuestionCount = parseInt(this.dom.questionCountInput.value); this.state.customQuizBaseScore = parseInt(this.dom.customQuizScore.value); if (this.state.customQuizName && this.state.targetQuestionCount > 0) { this.state.userQuestions = []; this.dom.addQuestionFields.disabled = false; this.dom.confirmDetailsBtn.parentElement.disabled = true; this.updateMakerHelper(); this.updateQuestionCounter(); } else { alert('لطفا نام آزمون و تعداد کل سوالات را به درستی وارد کنید.'); } },
            addCustomQuestion(e) { e.preventDefault(); if (this.state.userQuestions.length >= this.state.targetQuestionCount) return; const newQuestion = { question: document.getElementById('questionText').value, options: [document.getElementById('option1').value, document.getElementById('option2').value, document.getElementById('option3').value, document.getElementById('option4').value], correct: parseInt(document.getElementById('correctOption').value) }; if (Object.values(newQuestion.options).some(v => v === '') || !newQuestion.question) { alert('لطفا متن سوال و تمام گزینه‌ها را پر کنید.'); return; } this.state.userQuestions.push(newQuestion); this.updateQuestionCounter(); this.updateMakerHelper(); this.dom.addQuestionFields.querySelector('textarea').value = ''; this.dom.addQuestionFields.querySelectorAll('input[type="text"]').forEach(i => i.value = ''); this.dom.addQuestionFields.querySelector('textarea').focus(); if (this.state.userQuestions.length === this.state.targetQuestionCount) { this.dom.startCustomQuizBtn.style.display = 'inline-block'; this.dom.printCustomQuizBtn.style.display = 'inline-block'; this.dom.addQuestionFields.disabled = true; } },
            updateQuestionCounter(){ this.dom.questionCounterEl.textContent = `سوالات اضافه شده: ${this.state.userQuestions.length} / ${this.state.targetQuestionCount}`; },
            startCustomQuiz() { localStorage.setItem('userQuestions', JSON.stringify(this.state.userQuestions)); localStorage.setItem('customQuizName', this.state.customQuizName); localStorage.setItem('customQuizBaseScore', this.state.customQuizBaseScore); this.dom.customQuizTabTitle.textContent = this.state.customQuizName; this.dom.customQuizTab.style.display = 'inline-flex'; document.querySelector('#customQuiz h2').textContent = this.state.customQuizName; this.loadQuiz(this.state.userQuestions, 'customQuiz', this.state.customQuizName); setTimeout(() => this.dom.customQuizTab.click(), 100); },
            loadPersistedCustomQuiz() { const persistedName = localStorage.getItem('customQuizName'); const persistedQuestions = localStorage.getItem('userQuestions'); const persistedScore = localStorage.getItem('customQuizBaseScore'); if(persistedName && persistedQuestions) { this.dom.customQuizTabTitle.textContent = persistedName; this.dom.customQuizTab.style.display = 'inline-flex'; this.state.customQuizBaseScore = parseInt(persistedScore) || 20; } },
            deleteCustomQuiz(e) { e.stopPropagation(); if (confirm("آیا از حذف این آزمون سفارشی و تمام سوالات آن مطمئن هستید؟")) { localStorage.removeItem('userQuestions'); localStorage.removeItem('customQuizName'); localStorage.removeItem('customQuizBaseScore'); this.state.userQuestions = []; this.dom.customQuizTab.style.display = 'none'; document.querySelector('.tab[data-target="lifestyleQuiz"]').click(); this.resetQuizMakerForm(); } },
            resetQuizMakerForm() { this.dom.quizForm.reset(); this.state.userQuestions = []; this.state.targetQuestionCount = 0; this.updateQuestionCounter(); this.updateMakerHelper(); this.dom.startCustomQuizBtn.style.display = 'none'; this.dom.printCustomQuizBtn.style.display = 'none'; this.dom.addQuestionFields.disabled = true; this.dom.confirmDetailsBtn.parentElement.disabled = false; },
            shuffle(array) { const newArr = [...array]; for (let i = newArr.length - 1; i > 0; i--) { const j = Math.floor(Math.random() * (i + 1)); [newArr[i], newArr[j]] = [newArr[j], newArr[i]]; } return newArr; },
            handlePrintQuiz() {
                const quizName = this.state.customQuizName || 'آزمون سفارشی'; const questions = this.state.userQuestions; if(questions.length === 0) { alert('ابتدا باید سوالی طراحی کنید!'); return; }
                const printHTML = this.generatePrintHTML(quizName, questions); const printWindow = window.open('', '_blank');
                printWindow.document.write(printHTML); printWindow.document.close(); printWindow.focus(); setTimeout(() => { printWindow.print(); }, 500);
            },
            generatePrintHTML(title, questions) { let questionsHTML = ''; questions.forEach((q, index) => { let optionsHTML = ''; q.options.forEach(opt => { optionsHTML += `<li>${opt}</li>`; }); questionsHTML += `<div class="question-item"><h4>${index + 1}. ${q.question}</h4><ol class="option-list">${optionsHTML}</ol></div>`; }); return `<!DOCTYPE html><html lang="fa" dir="rtl"><head><meta charset="UTF-8"><title>چاپ آزمون: ${title}</title><link href="https://cdn.jsdelivr.net/gh/rastikerdar/dana-font@v3.0.0/dist/font-face.css" rel="stylesheet" type="text/css" /><style>body{font-family:'Dana',Arial,sans-serif;background:#fff;color:#000;padding:20px;line-height:1.6;}.print-header{text-align:center;border-bottom:2px solid #0d041a;padding-bottom:15px;margin-bottom:20px;}.print-header h1{margin:0;font-size:24px;color:#0d041a;}.print-header .logo{font-size:18px;color:#8A2BE2;}.info-fields{display:flex;justify-content:space-between;margin-bottom:30px;font-size:16px;border-bottom:1px dotted #ccc;padding-bottom:15px;}.question-item{margin-bottom:25px;page-break-inside:avoid;}.question-item h4{margin-bottom:10px;font-weight:600;}.option-list{list-style:none;padding-right:0;}.option-list li{padding:4px 0;font-size:15px;}.option-list li::before{content:'☐ ';margin-left:8px;}@media print{body{-webkit-print-color-adjust:exact;}}</style></head><body><div class="print-header"><span class="logo">آزمون ساز A.R</span><h1>آزمون: ${title}</h1></div><div class="info-fields"><span>نام و نام خانوادگی: .................................................</span><span>تاریخ: ..... / ..... / ...........</span><span>نمره: ...............</span></div>${questionsHTML}</body></html>`; }
        };
        
        document.addEventListener('DOMContentLoaded', () => {
            try {
                plexusBackground.init();
                uiManager.init();
                quizApp.init();
            } catch (error) {
                console.error("Initialization failed:", error);
                document.body.innerHTML = '<div style="color: white; text-align: center; padding: 50px; font-family: sans-serif;"><h1>An error occurred</h1><p>The application could not be started. Please check the console for details.</p></div>';
            }
        });
    </script>
</body>
</html>
