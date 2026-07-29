# zk
18岁生日快乐！
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no" />
    <title>🎂 ZK · 18岁生日快乐</title>

    <style>
        /* ===== 全局 ===== */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            user-select: none;
        }

        body {
            font-family: 'PingFang SC', 'Microsoft YaHei', sans-serif;
            background: linear-gradient(145deg, #0b1a2e, #1a3355, #0f2847);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 16px;
            position: relative;
            overflow-x: hidden;
        }

        body::before {
            content: '';
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background-image:
                radial-gradient(2px 2px at 20px 30px, rgba(255, 255, 255, 0.6), transparent),
                radial-gradient(2px 2px at 40px 70px, rgba(255, 255, 255, 0.6), transparent),
                radial-gradient(2px 2px at 50px 160px, rgba(255, 255, 255, 0.6), transparent),
                radial-gradient(2px 2px at 90px 40px, rgba(255, 255, 255, 0.6), transparent),
                radial-gradient(3px 3px at 130px 80px, rgba(255, 255, 255, 0.6), transparent),
                radial-gradient(2px 2px at 160px 30px, rgba(255, 255, 255, 0.6), transparent),
                radial-gradient(2px 2px at 200px 120px, rgba(255, 255, 255, 0.6), transparent);
            background-size: 200px 200px;
            opacity: 0.5;
            pointer-events: none;
            z-index: 0;
        }

        .app-wrapper {
            position: relative;
            z-index: 1;
            width: 100%;
            max-width: 480px;
            background: linear-gradient(180deg, #d4e9ff 0%, #a8c8f0 100%);
            border-radius: 40px 40px 32px 32px;
            padding: 20px 16px 18px;
            box-shadow: 0 30px 60px rgba(0, 0, 0, 0.7), 0 0 0 2px #6a9ecf inset;
            min-height: 580px;
        }

        /* ===== 密码锁 ===== */
        #lockPage {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            min-height: 500px;
            padding: 20px;
            text-align: center;
        }
        #lockPage .lock-icon {
            font-size: 72px;
            margin-bottom: 12px;
            animation: lockPulse 2s ease-in-out infinite;
        }
        @keyframes lockPulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.1); }
        }
        #lockPage h2 { font-size: 26px; color: #0a2a44; margin-bottom: 6px; }
        #lockPage p { color: #1d4a7a; font-size: 14px; margin-bottom: 18px; opacity: 0.8; }
        .lock-input-group {
            display: flex;
            gap: 10px;
            flex-wrap: wrap;
            justify-content: center;
        }
        .lock-input-group input {
            padding: 14px 20px;
            border: none;
            border-radius: 30px;
            font-size: 18px;
            font-weight: 700;
            text-align: center;
            background: rgba(255, 255, 255, 0.8);
            backdrop-filter: blur(4px);
            width: 160px;
            outline: 2px solid rgba(31, 90, 158, 0.3);
            transition: all 0.3s;
            letter-spacing: 6px;
            color: #0a2a44;
        }
        .lock-input-group input:focus {
            outline-color: #1f5a9e;
            background: #fff;
            box-shadow: 0 0 30px rgba(31, 90, 158, 0.2);
        }
        .lock-input-group .btn {
            padding: 14px 32px;
            border: none;
            border-radius: 30px;
            font-weight: 700;
            font-size: 16px;
            color: #fff;
            background: linear-gradient(135deg, #2d7bcb, #1a4f8a);
            box-shadow: 0 5px 0 #0d2f55, 0 6px 20px rgba(26, 79, 138, 0.3);
            cursor: pointer;
            transition: all 0.08s linear;
        }
        .lock-input-group .btn:active {
            transform: translateY(4px);
            box-shadow: 0 1px 0 #0d2f55;
        }
        .lock-error {
            color: #e74c3c;
            font-size: 14px;
            margin-top: 12px;
            min-height: 24px;
            font-weight: 600;
        }

        /* ===== 主内容 ===== */
        #mainContent {
            display: none;
            animation: fadeInUp 1s ease-out;
        }
        #mainContent.visible { display: block; }
        @keyframes fadeInUp {
            0% { opacity: 0; transform: translateY(40px); }
            100% { opacity: 1; transform: translateY(0); }
        }

        .header {
            text-align: center;
            margin-bottom: 10px;
        }
        .header h1 {
            font-size: 28px;
            font-weight: 900;
            color: #0a2a44;
            text-shadow: 0 2px 12px rgba(100, 180, 255, 0.5);
            letter-spacing: 2px;
        }
        .header h1 span { color: #ffb84d; text-shadow: 0 0 20px #ffb84d88; }
        .header .sub {
            font-size: 14px;
            color: #1d4a7a;
            font-weight: 600;
            background: rgba(255, 255, 255, 0.4);
            display: inline-block;
            padding: 2px 18px;
            border-radius: 40px;
            backdrop-filter: blur(4px);
            margin-top: 2px;
        }

        /* ===== 解锁进度条 ===== */
        .progress-bar {
            display: flex;
            gap: 10px;
            margin: 10px 0 14px;
            justify-content: center;
            align-items: center;
            background: rgba(255, 255, 255, 0.3);
            border-radius: 40px;
            padding: 8px 16px;
            backdrop-filter: blur(4px);
        }
        .progress-step {
            display: flex;
            align-items: center;
            gap: 4px;
            font-size: 12px;
            font-weight: 700;
            color: #1d4a7a;
            opacity: 0.5;
            transition: all 0.3s;
        }
        .progress-step.done {
            opacity: 1;
            color: #00b894;
        }
        .progress-step.active {
            opacity: 1;
            color: #1f5a9e;
            animation: stepPulse 1s ease-in-out infinite;
        }
        .progress-step .step-icon { font-size: 18px; }
        .progress-step .step-num { font-size: 11px; }
        .progress-line {
            width: 20px;
            height: 2px;
            background: rgba(255, 255, 255, 0.3);
            border-radius: 2px;
            transition: all 0.5s;
        }
        .progress-line.done { background: #00b894; }
        @keyframes stepPulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.05); }
        }

        /* ===== 解密序列 ===== */
        #unlockSequence {
            background: rgba(255, 255, 255, 0.2);
            backdrop-filter: blur(8px);
            border-radius: 24px;
            padding: 18px 16px;
            margin: 10px 0 14px;
            border: 1px solid rgba(255, 255, 255, 0.25);
            min-height: 100px;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            text-align: center;
        }
        #unlockSequence .seq-emoji { font-size: 48px; margin-bottom: 4px; }
        #unlockSequence .seq-text { font-size: 18px; font-weight: 700; color: #0a2a44; }
        #unlockSequence .seq-sub { font-size: 13px; color: #1d4a7a; opacity: 0.7; margin-top: 2px; }
        .seq-progress {
            display: flex;
            gap: 10px;
            margin-top: 12px;
            justify-content: center;
        }
        .seq-dot {
            width: 14px;
            height: 14px;
            border-radius: 50%;
            background: rgba(255, 255, 255, 0.3);
            border: 2px solid rgba(255, 255, 255, 0.2);
            transition: all 0.5s ease;
        }
        .seq-dot.done {
            background: #ffb84d;
            border-color: #ffb84d;
            box-shadow: 0 0 20px rgba(255, 184, 77, 0.5);
            transform: scale(1.2);
        }
        .seq-dot.active {
            background: #1f5a9e;
            border-color: #1f5a9e;
            animation: dotPulse 1s ease-in-out infinite;
        }
        @keyframes dotPulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.4); }
        }

        /* ===== 游戏标签 ===== */
        .tab-bar {
            display: flex;
            gap: 8px;
            margin: 12px 0 10px;
            flex-wrap: wrap;
            justify-content: center;
        }
        .tab-btn {
            flex: 1;
            min-width: 55px;
            padding: 8px 4px;
            border: none;
            border-radius: 40px;
            font-weight: 700;
            font-size: 10px;
            background: rgba(255, 255, 255, 0.25);
            color: #1d4a7a;
            cursor: pointer;
            transition: all 0.3s;
            box-shadow: 0 2px 6px rgba(0, 0, 0, 0.06);
            backdrop-filter: blur(4px);
            border: 1px solid rgba(255, 255, 255, 0.15);
            opacity: 0.5;
            pointer-events: none;
        }
        .tab-btn.active {
            background: #1f5a9e;
            color: #fff;
            box-shadow: 0 4px 14px rgba(31, 90, 158, 0.4);
            border-color: #1f5a9e;
            opacity: 1;
            pointer-events: auto;
        }
        .tab-btn.unlocked {
            opacity: 1;
            pointer-events: auto;
            background: rgba(255, 255, 255, 0.35);
            color: #0a2a44;
        }
        .tab-btn.unlocked:hover { background: rgba(255, 255, 255, 0.55); }
        .tab-btn .lock-icon-small { font-size: 10px; margin-left: 2px; }
        .tab-btn .check-icon { color: #00b894; font-size: 12px; margin-left: 2px; }

        /* ===== 游戏面板 ===== */
        .game-panel {
            display: none;
            background: rgba(255, 255, 255, 0.25);
            backdrop-filter: blur(6px);
            border-radius: 28px;
            padding: 16px 14px 18px;
            border: 1px solid rgba(255, 255, 255, 0.3);
            min-height: 380px;
        }
        .game-panel.active { display: block; }

        .game-info {
            display: flex;
            justify-content: space-between;
            align-items: center;
            background: rgba(255, 255, 255, 0.5);
            border-radius: 60px;
            padding: 6px 16px;
            margin-bottom: 12px;
            font-weight: 700;
            font-size: 15px;
            color: #0a2a44;
            border: 1px solid rgba(255, 255, 255, 0.4);
        }
        .game-info .score span {
            color: #1a5a9e;
            font-size: 22px;
            min-width: 36px;
            display: inline-block;
            text-align: center;
        }
        .game-info .timer span {
            color: #c0392b;
            font-size: 22px;
            min-width: 36px;
            display: inline-block;
            text-align: center;
            background: rgba(255, 255, 255, 0.3);
            border-radius: 30px;
            padding: 0 8px;
        }

        /* ===== 画布 ===== */
        .canvas-container {
            position: relative;
            width: 100%;
            aspect-ratio: 1 / 1;
            background: radial-gradient(ellipse at 50% 80%, #e3f0ff, #b8d6f5);
            border-radius: 24px;
            overflow: hidden;
            box-shadow: 0 6px 0 #4a7da0, 0 10px 30px rgba(0, 0, 0, 0.15);
            cursor: default;
            touch-action: none;
            display: flex;
            flex-wrap: wrap;
            align-items: center;
            justify-content: center;
            padding: 10px;
            gap: 8px;
        }

        .game-object {
            position: absolute;
            font-size: 40px;
            cursor: pointer;
            touch-action: none;
            z-index: 10;
            will-change: top, left;
            line-height: 1;
            filter: drop-shadow(0 4px 8px rgba(0, 0, 0, 0.15));
            animation: floatObj 2.2s ease-in-out infinite alternate;
            transition: transform 0.05s;
        }
        .game-object:active { transform: scale(0.8); }
        .game-object[data-type="good"] {
            z-index: 20;
            filter: drop-shadow(0 6px 16px rgba(50, 150, 255, 0.35));
        }
        .game-object[data-type="bad"] {
            opacity: 0.8;
            filter: drop-shadow(0 2px 6px rgba(0, 0, 0, 0.1));
        }
        @keyframes floatObj {
            0% { transform: translateY(-4px) rotate(-2deg); }
            100% { transform: translateY(4px) rotate(2deg); }
        }

        .popup-text {
            position: absolute;
            font-weight: 800;
            font-size: 20px;
            pointer-events: none;
            z-index: 50;
            animation: popUp 0.9s ease-out forwards;
            white-space: nowrap;
            text-shadow: 0 0 16px rgba(255, 255, 255, 0.6);
        }
        .popup-text.good { color: #1a7a3a; }
        .popup-text.bad { color: #c0392b; }
        @keyframes popUp {
            0% { opacity: 1; transform: translateY(0) scale(0.5); }
            100% { opacity: 0; transform: translateY(-80px) scale(1.3); }
        }

        /* ===== 按钮 ===== */
        .btn-group {
            display: flex;
            gap: 10px;
            margin-top: 14px;
            flex-wrap: wrap;
            justify-content: center;
        }
        .btn {
            padding: 10px 24px;
            border: none;
            border-radius: 60px;
            font-weight: 700;
            font-size: 15px;
            color: #fff;
            background: linear-gradient(135deg, #2d7bcb, #1a4f8a);
            box-shadow: 0 5px 0 #0d2f55, 0 6px 20px rgba(26, 79, 138, 0.3);
            cursor: pointer;
            transition: all 0.08s linear;
            flex: 1;
            min-width: 80px;
        }
        .btn:active {
            transform: translateY(4px);
            box-shadow: 0 1px 0 #0d2f55;
        }
        .btn:disabled {
            opacity: 0.4;
            transform: translateY(4px);
            box-shadow: 0 1px 0 #0d2f55;
            pointer-events: none;
        }
        .btn-pink {
            background: linear-gradient(135deg, #f093fb, #f5576c);
            box-shadow: 0 5px 0 #a53a4a;
        }
        .btn-gold {
            background: linear-gradient(135deg, #f6d365, #fda085);
            box-shadow: 0 5px 0 #b87a4a;
            color: #2d2d2d;
        }
        .btn-green {
            background: linear-gradient(135deg, #00b894, #00a381);
            box-shadow: 0 5px 0 #006b57;
        }
        .btn-cheat {
            background: linear-gradient(135deg, #e17055, #d63031);
            box-shadow: 0 5px 0 #8a1a1a;
            font-size: 12px;
            padding: 8px 12px;
            min-width: 50px;
            flex: 0.5;
        }
        .btn-cheat:disabled {
            opacity: 0.3;
            transform: translateY(4px);
            box-shadow: 0 1px 0 #8a1a1a;
            pointer-events: none;
        }

        /* ===== 剧本杀 ===== */
        .story-container {
            width: 100%;
            height: 100%;
            display: flex;
            flex-direction: column;
            padding: 6px;
            overflow-y: auto;
            gap: 6px;
        }
        .story-title {
            font-size: 16px;
            font-weight: 800;
            color: #0a2a44;
            text-align: center;
            background: rgba(255, 255, 255, 0.5);
            padding: 6px 12px;
            border-radius: 16px;
            border-left: 4px solid #ffb84d;
        }
        .story-narrative {
            font-size: 13px;
            color: #1d4a7a;
            background: rgba(255, 255, 255, 0.6);
            padding: 8px 12px;
            border-radius: 14px;
            line-height: 1.6;
            flex-shrink: 0;
        }
        .story-narrative .highlight { color: #e84393; font-weight: 700; }
        .suspect-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 8px;
            flex: 1;
            min-height: 0;
        }
        .suspect-card {
            background: rgba(255, 255, 255, 0.7);
            border-radius: 14px;
            padding: 8px 6px;
            text-align: center;
            cursor: pointer;
            transition: all 0.2s;
            border: 2px solid rgba(255, 255, 255, 0.3);
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            gap: 2px;
        }
        .suspect-card:active { transform: scale(0.95); }
        .suspect-card .avatar { font-size: 32px; }
        .suspect-card .name { font-weight: 700; color: #0a2a44; font-size: 13px; }
        .suspect-card .status { font-size: 11px; color: #1d4a7a; opacity: 0.7; }
        .suspect-card.interviewed {
            border-color: #4a9eff;
            background: rgba(74, 158, 255, 0.15);
        }
        .suspect-card .clue-box {
            font-size: 11px;
            color: #1d4a7a;
            background: rgba(255, 255, 255, 0.5);
            padding: 3px 8px;
            border-radius: 8px;
            margin-top: 3px;
            width: 100%;
            max-height: 36px;
            overflow: hidden;
            text-overflow: ellipsis;
            white-space: nowrap;
        }
        .clue-log {
            background: rgba(255, 255, 255, 0.5);
            border-radius: 12px;
            padding: 6px 10px;
            max-height: 50px;
            overflow-y: auto;
            font-size: 12px;
            color: #0a2a44;
            flex-shrink: 0;
            border: 1px solid rgba(255, 255, 255, 0.3);
        }
        .clue-log .clue-item { padding: 2px 0; border-bottom: 1px solid rgba(255, 255, 255, 0.2); }
        .clue-log .clue-item:last-child { border-bottom: none; }
        .clue-log .clue-suspect { font-weight: 700; color: #1f5a9e; }
        .judge-area {
            display: flex;
            gap: 6px;
            flex-shrink: 0;
            flex-wrap: wrap;
            justify-content: center;
        }
        .judge-area select {
            padding: 6px 10px;
            border: none;
            border-radius: 30px;
            font-size: 13px;
            background: rgba(255, 255, 255, 0.8);
            color: #0a2a44;
            flex: 2;
            min-width: 80px;
            outline: 2px solid rgba(31, 90, 158, 0.2);
        }
        .judge-area select:focus { outline-color: #1f5a9e; }
        .judge-area .btn {
            flex: 1;
            min-width: 50px;
            padding: 6px 12px;
            font-size: 12px;
        }
        .result-banner {
            text-align: center;
            padding: 6px;
            border-radius: 12px;
            font-weight: 700;
            font-size: 14px;
            flex-shrink: 0;
        }
        .result-banner.success {
            background: rgba(0, 184, 148, 0.25);
            color: #00a381;
            border: 2px solid #00b894;
        }
        .result-banner.fail {
            background: rgba(225, 112, 85, 0.2);
            color: #c0392b;
            border: 2px solid #e17055;
        }
        .result-banner.waiting {
            background: rgba(255, 184, 77, 0.2);
            color: #b87a4a;
            border: 2px solid #f6d365;
        }

        /* ===== 弹窗 ===== */
        .modal-overlay {
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: rgba(0, 0, 0, 0.6);
            backdrop-filter: blur(8px);
            display: none;
            justify-content: center;
            align-items: center;
            z-index: 999;
            padding: 20px;
        }
        .modal-overlay.active { display: flex; }
        .modal {
            background: linear-gradient(180deg, #e8f4ff, #c0ddf5);
            border-radius: 48px;
            max-width: 380px;
            width: 100%;
            padding: 32px 24px 28px;
            text-align: center;
            box-shadow: 0 40px 80px rgba(0, 0, 0, 0.5);
            animation: fadeIn 0.4s ease-out;
        }
        @keyframes fadeIn {
            from { opacity: 0; transform: scale(0.9); }
            to { opacity: 1; transform: scale(1); }
        }
        .modal .big-emoji { font-size: 64px; display: block; }
        .modal h2 { font-size: 26px; color: #0a2a44; margin: 6px 0; }
        .modal .result-score {
            font-size: 42px;
            font-weight: 900;
            color: #1a5a9e;
            background: rgba(255, 255, 255, 0.5);
            display: inline-block;
            padding: 2px 28px;
            border-radius: 60px;
            margin: 6px 0 10px;
        }
        .modal .result-desc { font-size: 16px; color: #1d4a7a; line-height: 1.6; margin: 6px 0 16px; }
        .modal .btn-group { flex-direction: column; }
        .modal .btn-group .btn { width: 100%; flex: none; }

        .footer-credit {
            text-align: center;
            margin-top: 18px;
            padding-top: 12px;
            border-top: 1px solid rgba(255, 255, 255, 0.3);
            font-size: 14px;
            color: #1d4a7a;
            font-weight: 500;
            letter-spacing: 1px;
        }
        .footer-credit span { color: #ff6b6b; font-weight: 700; }
        .footer-credit .heart {
            color: #ff4757;
            animation: heartBeat 1.2s ease-in-out infinite;
            display: inline-block;
        }
        @keyframes heartBeat {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.25); }
        }

        .confetti-container {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 1000;
            overflow: hidden;
        }
        .confetti {
            position: absolute;
            width: 10px;
            height: 10px;
            opacity: 0.9;
            animation: confettiFall linear forwards;
        }
        @keyframes confettiFall {
            0% { transform: translateY(-20px) rotate(0deg); opacity: 1; }
            100% { transform: translateY(110vh) rotate(720deg); opacity: 0; }
        }

        /* ===== 自定义音乐播放器 ===== */
        .music-player {
            position: fixed;
            bottom: 20px;
            left: 50%;
            transform: translateX(-50%);
            z-index: 100;
            background: rgba(255, 255, 255, 0.12);
            backdrop-filter: blur(16px);
            border-radius: 60px;
            padding: 8px 16px 8px 12px;
            display: flex;
            align-items: center;
            gap: 12px;
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.3);
            border: 1px solid rgba(255, 255, 255, 0.15);
            width: 340px;
            max-width: 92vw;
        }
        .music-player .cover {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            background: linear-gradient(135deg, #f093fb, #f5576c);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 18px;
            flex-shrink: 0;
            box-shadow: 0 0 20px rgba(245, 87, 108, 0.2);
            animation: spin 8s linear infinite;
            animation-play-state: paused;
        }
        .music-player .cover.playing {
            animation-play-state: running;
        }
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
        .music-player .info {
            flex: 1;
            min-width: 0;
        }
        .music-player .info .title {
            font-size: 13px;
            font-weight: 700;
            color: #fff;
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
        }
        .music-player .info .artist {
            font-size: 11px;
            color: rgba(255, 255, 255, 0.6);
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
        }
        .music-player .controls {
            display: flex;
            align-items: center;
            gap: 6px;
            flex-shrink: 0;
        }
        .music-player .controls button {
            background: none;
            border: none;
            color: #fff;
            font-size: 20px;
            cursor: pointer;
            padding: 4px 6px;
            border-radius: 50%;
            transition: all 0.2s;
            opacity: 0.8;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        .music-player .controls button:hover {
            opacity: 1;
            transform: scale(1.1);
        }
        .music-player .controls button:active {
            transform: scale(0.85);
        }
        .music-player .controls .play-btn {
            font-size: 28px;
            opacity: 1;
        }
        .music-player .controls .play-btn:hover {
            transform: scale(1.1);
        }
        .music-player .volume-bar {
            width: 4px;
            height: 24px;
            background: rgba(255, 255, 255, 0.2);
            border-radius: 4px;
            position: relative;
            cursor: pointer;
            flex-shrink: 0;
        }
        .music-player .volume-bar .volume-fill {
            position: absolute;
            bottom: 0;
            left: 0;
            width: 100%;
            height: 60%;
            background: linear-gradient(0deg, #f093fb, #f5576c);
            border-radius: 4px;
            transition: height 0.1s;
        }

        /* ===== 证书 ===== */
        .certificate-modal .modal { max-width: 420px; padding: 20px 20px 28px; }
        .certificate-modal .cert-image {
            width: 100%;
            max-width: 280px;
            border-radius: 20px;
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.15);
            margin: 6px auto 12px;
            display: block;
            border: 3px solid #ffd700;
        }
        .certificate-modal .cert-title { font-size: 22px; font-weight: 900; color: #0a2a44; margin: 4px 0 2px; }
        .certificate-modal .cert-name { font-size: 28px; font-weight: 900; color: #e84393; margin: 2px 0; }
        .certificate-modal .cert-desc { font-size: 14px; color: #1d4a7a; line-height: 1.6; margin: 6px 0 12px; }
        .certificate-modal .cert-footer {
            font-size: 13px;
            color: #1d4a7a;
            border-top: 2px dashed #6a9ecf;
            padding-top: 10px;
            margin-top: 4px;
        }

        /* ===== 作弊确认弹窗 ===== */
        .cheat-modal .modal { max-width: 360px; }
        .cheat-modal .cheat-cost {
            font-size: 20px;
            font-weight: 900;
            color: #e17055;
            background: rgba(225, 112, 85, 0.1);
            padding: 8px 16px;
            border-radius: 12px;
            display: inline-block;
            margin: 6px 0;
        }
        .cheat-modal .cheat-warning {
            font-size: 14px;
            color: #c0392b;
            background: rgba(192, 57, 43, 0.08);
            padding: 8px 12px;
            border-radius: 10px;
            margin: 8px 0;
        }

        /* ===== 响应式 ===== */
        @media (max-width: 440px) {
            .app-wrapper { padding: 14px 10px 14px; }
            .header h1 { font-size: 22px; }
            .tab-btn { font-size: 9px; padding: 6px 3px; min-width: 40px; }
            .game-info { font-size: 13px; padding: 4px 12px; }
            .game-info .score span, .game-info .timer span { font-size: 18px; min-width: 28px; }
            .btn { font-size: 13px; padding: 8px 16px; min-width: 60px; }
            .btn-cheat { font-size: 10px; padding: 6px 8px; min-width: 40px; }
            .modal { padding: 24px 16px 20px; }
            .modal .result-score { font-size: 32px; }
            .footer-credit { font-size: 12px; }
            .music-player { width: 290px; padding: 6px 12px 6px 10px; bottom: 12px; }
            .music-player .cover { width: 32px; height: 32px; font-size: 14px; }
            .music-player .info .title { font-size: 11px; }
            .music-player .info .artist { font-size: 9px; }
            .music-player .controls button { font-size: 16px; }
            .music-player .controls .play-btn { font-size: 22px; }
            #lockPage .lock-icon { font-size: 52px; }
            #lockPage h2 { font-size: 20px; }
            .lock-input-group input { width: 130px; font-size: 16px; padding: 12px 16px; }
            .lock-input-group .btn { padding: 12px 24px; font-size: 14px; }
            .progress-step { font-size: 10px; }
            .progress-line { width: 12px; }
            .story-title { font-size: 14px; }
            .story-narrative { font-size: 12px; padding: 6px 10px; }
            .suspect-card .avatar { font-size: 26px; }
            .suspect-card .name { font-size: 11px; }
            .suspect-card .clue-box { font-size: 10px; max-height: 28px; }
            .clue-log { font-size: 11px; max-height: 40px; padding: 4px 8px; }
            .judge-area select { font-size: 11px; padding: 4px 8px; }
            .judge-area .btn { font-size: 11px; padding: 4px 10px; }
            .result-banner { font-size: 12px; padding: 4px; }
            .certificate-modal .cert-image { max-width: 200px; }
            .certificate-modal .cert-title { font-size: 18px; }
            .certificate-modal .cert-name { font-size: 22px; }
        }
        @media (max-width: 360px) {
            .music-player { width: 240px; padding: 4px 8px 4px 8px; }
            .music-player .cover { width: 26px; height: 26px; font-size: 12px; }
            .music-player .info .title { font-size: 10px; }
            .music-player .info .artist { font-size: 8px; }
            .music-player .controls button { font-size: 14px; }
            .music-player .controls .play-btn { font-size: 18px; }
            .suspect-grid { gap: 4px; }
            .suspect-card { padding: 4px 3px; }
            .suspect-card .avatar { font-size: 20px; }
            .suspect-card .name { font-size: 10px; }
            .suspect-card .clue-box { font-size: 9px; max-height: 22px; padding: 1px 4px; }
            .progress-step { font-size: 8px; }
            .progress-line { width: 8px; }
            .tab-btn { font-size: 8px; padding: 4px 2px; min-width: 32px; }
        }
    </style>
</head>
<body>

    <div class="app-wrapper">

        <!-- ===== 密码锁 ===== -->
        <div id="lockPage">
            <div class="lock-icon">🔐</div>
            <h2>🎂 ZK · 18</h2>
            <p>请输入访问密码，解锁生日惊喜 ✨</p>
            <div class="lock-input-group">
                <input type="password" id="passwordInput" maxlength="6" placeholder="· · · ·" inputmode="numeric" />
                <button class="btn" id="unlockBtn">🔓 解锁</button>
            </div>
            <div class="lock-error" id="lockError"></div>
            <div style="margin-top:16px;font-size:12px;color:#1d4a7a;opacity:0.5;">提示：四个数字 · 她的生日</div>
        </div>

        <!-- ===== 主内容 ===== -->
        <div id="mainContent">

            <div class="header">
                <h1>🎂 ZK <span>· 18</span></h1>
                <div class="sub">✨ 陈奕恒 · 专属应援站 ✨</div>
            </div>

            <!-- ===== 解锁进度条 ===== -->
            <div class="progress-bar" id="progressBar">
                <div class="progress-step active" data-step="0">
                    <span class="step-icon">🔓</span>
                    <span class="step-num">游戏1</span>
                </div>
                <div class="progress-line" data-line="0"></div>
                <div class="progress-step" data-step="1">
                    <span class="step-icon">🔒</span>
                    <span class="step-num">游戏2</span>
                </div>
                <div class="progress-line" data-line="1"></div>
                <div class="progress-step" data-step="2">
                    <span class="step-icon">🔒</span>
                    <span class="step-num">游戏3</span>
                </div>
            </div>

            <!-- ===== 解密序列 ===== -->
            <div id="unlockSequence">
                <div class="seq-emoji" id="seqEmoji">🌟</div>
                <div class="seq-text" id="seqText">欢迎来到 ZK 的18岁世界</div>
                <div class="seq-sub" id="seqSub">完成游戏，解锁更多惊喜！</div>
                <div class="seq-progress" id="seqProgress">
                    <span class="seq-dot" data-step="0"></span>
                    <span class="seq-dot" data-step="1"></span>
                    <span class="seq-dot" data-step="2"></span>
                    <span class="seq-dot" data-step="3"></span>
                    <span class="seq-dot" data-step="4"></span>
                </div>
            </div>

            <!-- ===== 游戏标签 ===== -->
            <div class="tab-bar" id="tabBar">
                <button class="tab-btn active" data-game="game1" data-index="0">🎂 保卫蛋糕</button>
                <button class="tab-btn locked" data-game="game2" data-index="1">🖼️ 记忆翻牌 🔒</button>
                <button class="tab-btn locked" data-game="game3" data-index="2">🎭 剧本杀 🔒</button>
            </div>

            <!-- ===== 游戏1：保卫蛋糕 ===== -->
            <div class="game-panel active" id="game1">
                <div class="game-info">
                    <div class="score">🎯 <span id="score1">0</span></div>
                    <div class="timer">⏱️ <span id="timer1">30</span>s</div>
                </div>
                <div class="canvas-container" id="canvas1"></div>
                <div class="btn-group">
                    <button class="btn" id="start1">🚀 开始</button>
                    <button class="btn btn-pink" id="reset1">🔄 重置</button>
                    <button class="btn btn-cheat" id="cheat1" disabled>💀 作弊</button>
                </div>
                <div style="text-align:center;font-size:12px;color:#1d4a7a;opacity:0.6;margin-top:6px;">
                    💡 目标：≥60分 通关 | 当前可用分数：<span id="totalScore1">0</span> 分
                </div>
            </div>

            <!-- ===== 游戏2：记忆翻牌 ===== -->
            <div class="game-panel" id="game2">
                <div class="game-info">
                    <div class="score">🧩 配对 <span id="score2">0</span>/8</div>
                    <div class="timer">⏱️ <span id="timer2">60</span>s</div>
                </div>
                <div class="canvas-container" id="canvas2" style="display:grid;grid-template-columns:repeat(4,1fr);gap:6px;padding:10px;background:radial-gradient(ellipse at 50% 80%,#d4e9ff,#8bb4dd);align-content:center;">
                </div>
                <div class="btn-group">
                    <button class="btn" id="start2">🚀 开始</button>
                    <button class="btn btn-pink" id="reset2">🔄 重置</button>
                    <button class="btn btn-cheat" id="cheat2" disabled>💀 作弊</button>
                </div>
                <div style="text-align:center;font-size:12px;color:#1d4a7a;opacity:0.6;margin-top:6px;">
                    💡 目标：配对所有8对 | 当前可用分数：<span id="totalScore2">0</span> 分
                </div>
            </div>

            <!-- ===== 游戏3：剧本杀 ===== -->
            <div class="game-panel" id="game3">
                <div class="game-info">
                    <div class="score">🔍 <span id="score3">0</span>/4 询问</div>
                    <div class="timer">⏱️ <span id="timer3">--</span></div>
                </div>
                <div class="canvas-container" id="canvas3" style="display:block;aspect-ratio:auto;min-height:380px;height:auto;padding:8px;background:radial-gradient(ellipse at 50% 80%,#e8f0ff,#c5d9f0);">
                    <div class="story-container" id="storyContainer"></div>
                </div>
                <div class="btn-group">
                    <button class="btn btn-green" id="reset3">🔄 重新开始</button>
                </div>
                <div style="text-align:center;font-size:12px;color:#1d4a7a;opacity:0.6;margin-top:6px;">
                    💡 找出真凶即可通关！
                </div>
            </div>

            <div class="footer-credit">
                <span class="heart">❤️</span>
                你永远的好朋友 <span>wcy</span> 制作
                <span class="heart">❤️</span>
            </div>

        </div>
    </div>

    <!-- ===== 结算弹窗 ===== -->
    <div class="modal-overlay" id="resultModal">
        <div class="modal">
            <span class="big-emoji" id="rEmoji">🎉</span>
            <h2 id="rTitle">太棒啦！</h2>
            <div class="result-score" id="rScore">0</div>
            <div class="result-desc" id="rDesc">你就是天选之女！</div>
            <div class="btn-group">
                <button class="btn" id="modalRestart">🔄 再来一次</button>
                <button class="btn btn-gold" id="modalClaim">🎁 领取证书</button>
            </div>
        </div>
    </div>

    <!-- ===== 作弊确认弹窗 ===== -->
    <div class="modal-overlay cheat-modal" id="cheatModal">
        <div class="modal">
            <span class="big-emoji">💀</span>
            <h2 style="color:#c0392b;">作弊确认</h2>
            <p style="color:#1d4a7a;font-size:14px;margin:6px 0;">
                你将消耗 <span class="cheat-cost" id="cheatCost">50</span> 分
                来直接通关当前游戏
            </p>
            <div class="cheat-warning">
                ⚠️ 作弊会扣除分数，且无法获得通关奖励
            </div>
            <div style="font-size:13px;color:#1d4a7a;margin:6px 0;">
                当前可用分数：<strong id="cheatBalance">0</strong> 分
            </div>
            <div class="btn-group">
                <button class="btn btn-pink" id="cheatConfirm">💀 确认作弊</button>
                <button class="btn" id="cheatCancel">取消</button>
            </div>
        </div>
    </div>

    <!-- ===== 证书弹窗 ===== -->
    <div class="modal-overlay certificate-modal" id="certModal">
        <div class="modal">
            <img class="cert-image" id="certImage" src="data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='400' height='300' viewBox='0 0 400 300'%3E%3Crect width='400' height='300' rx='20' fill='%23fdf6e3'/%3E%3Crect x='10' y='10' width='380' height='280' rx='15' fill='none' stroke='%23ffd700' stroke-width='4' stroke-dasharray='10 6'/%3E%3Ctext x='200' y='55' text-anchor='middle' font-size='22' font-weight='bold' fill='%230a2a44'%3E🎓 成 人 证 书 🎓%3C/text%3E%3Ctext x='200' y='100' text-anchor='middle' font-size='16' fill='%231d4a7a'%3E兹 证 明%3C/text%3E%3Ctext x='200' y='150' text-anchor='middle' font-size='36' font-weight='900' fill='%23e84393'%3EZK%3C/text%3E%3Ctext x='200' y='190' text-anchor='middle' font-size='16' fill='%231d4a7a'%3E于 2026 年 正 式 成 为 大 人%3C/text%3E%3Ctext x='200' y='225' text-anchor='middle' font-size='14' fill='%231d4a7a'%3E🌟 陈奕恒头号粉丝 · 闺蜜永久VIP 🌟%3C/text%3E%3Ctext x='200' y='265' text-anchor='middle' font-size='12' fill='%236a9ecf'%3E💌 发证机关：你永远的好朋友 wcy  💌%3C/text%3E%3C/svg%3E" alt="成人证书" />
            <div class="cert-title">🎓 成人证书</div>
            <div class="cert-name">ZK · 18岁</div>
            <div class="cert-desc">
                🌟 陈奕恒头号粉丝认证<br />
                💖 闺蜜永久VIP特权<br />
                🎂 终身享受投喂、陪聊、帮忙骂渣男
            </div>
            <div class="cert-footer">
                💌 发证机关：你永远的好朋友 wcy<br />
                📅 有效期：一辈子
            </div>
            <div class="btn-group" style="margin-top:12px;">
                <button class="btn btn-gold" id="certCloseBtn">💖 收到啦！</button>
            </div>
        </div>
    </div>

    <!-- ===== 撒花容器 ===== -->
    <div class="confetti-container" id="confettiContainer"></div>

    <!-- ===== 自定义音乐播放器 ===== -->
    <div class="music-player" id="musicPlayer">
        <div class="cover" id="playerCover">🎤</div>
        <div class="info">
            <div class="title" id="playerTitle">Be Yourself</div>
            <div class="artist" id="playerArtist">陈奕恒 · TF家族</div>
        </div>
        <div class="controls">
            <button id="playerToggle" class="play-btn" title="播放/暂停">▶</button>
            <div class="volume-bar" id="volumeBar">
                <div class="volume-fill" id="volumeFill"></div>
            </div>
        </div>
    </div>

    <script>
        // ================================================================
        //  🔐  密 码 锁
        // ================================================================
        const PASSWORD = '0802';
        const lockPage = document.getElementById('lockPage');
        const mainContent = document.getElementById('mainContent');
        const passwordInput = document.getElementById('passwordInput');
        const unlockBtn = document.getElementById('unlockBtn');
        const lockError = document.getElementById('lockError');

        function tryUnlock() {
            const input = passwordInput.value.trim();
            if (input === PASSWORD) {
                lockPage.style.display = 'none';
                mainContent.classList.add('visible');
                lockError.textContent = '';
                passwordInput.value = '';
                startUnlockSequence();
                initGameSystem();
                initMusicPlayer();
            } else {
                lockError.textContent = '❌ 密码错误，再想想～';
                passwordInput.value = '';
                passwordInput.focus();
                setTimeout(() => { lockError.textContent = ''; }, 2000);
            }
        }
        unlockBtn.addEventListener('click', tryUnlock);
        passwordInput.addEventListener('keydown', (e) => { if (e.key === 'Enter') tryUnlock(); });
        passwordInput.addEventListener('input', () => { if (passwordInput.value.length === 4) tryUnlock(); });

        // ================================================================
        //  🎬  解 密 序 列
        // ================================================================
        const SEQUENCE = [
            { emoji: '🌟', text: '✨ 第一道封印 · 星光觉醒', sub: 'wcy 在远方为你点亮' },
            { emoji: '🔮', text: '🔮 第二道封印 · 记忆之泉', sub: '属于你的18年故事即将展开' },
            { emoji: '🎂', text: '🎂 第三道封印 · 蛋糕之力', sub: '许个愿吧，它一定会实现' },
            { emoji: '💙', text: '💙 第四道封印 · 应援之心', sub: '陈奕恒为你加油！' },
            { emoji: '🎉', text: '🎉 全部解开 · 18岁快乐！', sub: '欢迎来到 ZK 的成人世界 💖' },
        ];

        let seqStep = -1;
        let seqInterval = null;

        function startUnlockSequence() {
            const emojiEl = document.getElementById('seqEmoji');
            const textEl = document.getElementById('seqText');
            const subEl = document.getElementById('seqSub');
            const dots = document.querySelectorAll('.seq-dot');
            seqStep = -1;
            dots.forEach(d => d.className = 'seq-dot');
            if (seqInterval) clearInterval(seqInterval);

            seqInterval = setInterval(() => {
                seqStep++;
                if (seqStep >= SEQUENCE.length) {
                    clearInterval(seqInterval);
                    seqInterval = null;
                    emojiEl.textContent = '🎊';
                    textEl.textContent = '🎉 解锁成功！开始游戏吧！';
                    subEl.textContent = 'wcy 永远挺你 ❤️';
                    launchConfetti();
                    return;
                }
                const step = SEQUENCE[seqStep];
                emojiEl.textContent = step.emoji;
                textEl.textContent = step.text;
                subEl.textContent = step.sub;
                dots.forEach((dot, idx) => {
                    dot.className = 'seq-dot';
                    if (idx < seqStep) dot.classList.add('done');
                    else if (idx === seqStep) dot.classList.add('active');
                });
                if (seqStep >= 1) launchMiniConfetti();
            }, 1200);

            document.addEventListener('keydown', function skipSeq(e) {
                if (e.key === 'Enter' && seqInterval) {
                    clearInterval(seqInterval);
                    seqInterval = null;
                    seqStep = SEQUENCE.length - 1;
                    document.getElementById('seqEmoji').textContent = '🎊';
                    document.getElementById('seqText').textContent = '🎉 解锁成功！开始游戏吧！';
                    document.getElementById('seqSub').textContent = 'wcy 永远挺你 ❤️';
                    document.querySelectorAll('.seq-dot').forEach(d => d.className = 'seq-dot done');
                    launchConfetti();
                    document.removeEventListener('keydown', skipSeq);
                }
            });
        }

        function launchMiniConfetti() {
            const container = document.getElementById('confettiContainer');
            const colors = ['#ffd700', '#4a9eff', '#ff9ff3', '#feca57', '#ff6b6b'];
            for (let i = 0; i < 20; i++) {
                const el = document.createElement('div');
                el.className = 'confetti';
                el.style.left = rand(0, 100) + '%';
                el.style.top = '-10px';
                el.style.background = colors[randInt(0, colors.length - 1)];
                el.style.width = (4 + rand(0, 6)) + 'px';
                el.style.height = (4 + rand(0, 6)) + 'px';
                el.style.borderRadius = Math.random() > 0.5 ? '50%' : '2px';
                el.style.animationDuration = (2 + rand(0, 2)) + 's';
                el.style.animationDelay = rand(0, 1) + 's';
                container.appendChild(el);
            }
            setTimeout(() => { container.innerHTML = ''; }, 3000);
        }

        // ================================================================
        //  🎵  自 定 义 音 乐 播 放 器
        // ================================================================
        let audioPlayer = null;
        let isPlaying = false;

        function initMusicPlayer() {
            const cover = document.getElementById('playerCover');
            const toggleBtn = document.getElementById('playerToggle');

            // 使用网易云音乐的真实音频源
            // 通过网易云歌曲ID获取播放地址
            const songId = 3379580642;
            const audioUrl = `https://music.163.com/song/media/outer/url?id=${songId}.mp3`;

            audioPlayer = new Audio(audioUrl);
            audioPlayer.loop = true;
            audioPlayer.volume = 0.6;

            // 更新封面旋转状态
            audioPlayer.addEventListener('play', () => {
                cover.classList.add('playing');
                toggleBtn.textContent = '⏸';
                isPlaying = true;
            });

            audioPlayer.addEventListener('pause', () => {
                cover.classList.remove('playing');
                toggleBtn.textContent = '▶';
                isPlaying = false;
            });

            // 加载完成后自动播放
            audioPlayer.addEventListener('canplaythrough', () => {
                audioPlayer.play().catch(() => {});
            });

            // 播放/暂停切换
            toggleBtn.addEventListener('click', () => {
                if (isPlaying) {
                    audioPlayer.pause();
                } else {
                    audioPlayer.play().catch(() => {
                        // 如果播放失败，重新加载
                        audioPlayer.load();
                        setTimeout(() => audioPlayer.play().catch(() => {}), 500);
                    });
                }
            });

            // 音量控制
            const volumeBar = document.getElementById('volumeBar');
            const volumeFill = document.getElementById('volumeFill');

            function setVolume(e) {
                const rect = volumeBar.getBoundingClientRect();
                const y = (e.clientY || e.touches?.[0]?.clientY || rect.bottom) - rect.top;
                const percent = Math.max(0, Math.min(1, 1 - y / rect.height));
                audioPlayer.volume = percent;
                volumeFill.style.height = (percent * 100) + '%';
            }

            volumeBar.addEventListener('click', setVolume);
            volumeBar.addEventListener('touchstart', (e) => {
                e.preventDefault();
                setVolume(e);
            });

            // 默认音量 60%
            volumeFill.style.height = '60%';

            // 尝试自动播放（需要用户交互）
            document.addEventListener('click', () => {
                if (audioPlayer.paused && audioPlayer.src) {
                    audioPlayer.play().catch(() => {});
                }
            }, { once: true });

            console.log('🎵 自定义播放器已加载，歌曲ID:', songId);
        }

        // ================================================================
        //  🎮  工 具 函 数
        // ================================================================
        function rand(min, max) { return Math.random() * (max - min) + min; }

        function randInt(min, max) { return Math.floor(rand(min, max + 1)); }

        function shuffle(arr) {
            for (let i = arr.length - 1; i > 0; i--) {
                const j = randInt(0, i);
                [arr[i], arr[j]] = [arr[j], arr[i]];
            }
            return arr;
        }

        let totalScore = 0;
        let game1Completed = false;
        let game2Completed = false;
        let game3Completed = false;
        let currentGame = 0;
        let cheatTarget = null;

        function showModal(emoji, title, scoreText, desc, onRestart, onClaim) {
            document.getElementById('rEmoji').textContent = emoji;
            document.getElementById('rTitle').textContent = title;
            document.getElementById('rScore').textContent = scoreText;
            document.getElementById('rDesc').textContent = desc;
            document.getElementById('resultModal').classList.add('active');
            document.getElementById('modalRestart').onclick = () => {
                document.getElementById('resultModal').classList.remove('active');
                if (onRestart) onRestart();
            };
            document.getElementById('modalClaim').onclick = () => {
                document.getElementById('resultModal').classList.remove('active');
                if (onClaim) onClaim();
            };
        }

        function closeModal() { document.getElementById('resultModal').classList.remove('active'); }

        function launchConfetti() {
            const container = document.getElementById('confettiContainer');
            container.innerHTML = '';
            const colors = ['#4a9eff', '#feca57', '#48dbfb', '#ff9ff3', '#54a0ff', '#ff9f43', '#00d2d3', '#ee5a24'];
            for (let i = 0; i < 80; i++) {
                const el = document.createElement('div');
                el.className = 'confetti';
                el.style.left = rand(0, 100) + '%';
                el.style.top = '-10px';
                el.style.background = colors[randInt(0, colors.length - 1)];
                el.style.width = (6 + rand(0, 8)) + 'px';
                el.style.height = (6 + rand(0, 8)) + 'px';
                el.style.borderRadius = Math.random() > 0.5 ? '50%' : '2px';
                el.style.animationDuration = (2 + rand(0, 2.5)) + 's';
                el.style.animationDelay = rand(0, 1.5) + 's';
                el.style.transform = `rotate(${rand(0,360)}deg)`;
                container.appendChild(el);
            }
            setTimeout(() => { container.innerHTML = ''; }, 5000);
        }

        function showCertificate() {
            document.getElementById('certModal').classList.add('active');
        }
        document.getElementById('certCloseBtn').addEventListener('click', () => {
            document.getElementById('certModal').classList.remove('active');
        });
        document.getElementById('certModal').addEventListener('click', (e) => {
            if (e.target === e.currentTarget) {
                document.getElementById('certModal').classList.remove('active');
            }
        });

        // ================================================================
        //  🔓  游 戏 解 锁 系 统
        // ================================================================
        function initGameSystem() {
            updateProgressAndTabs();
            updateTotalScoreDisplay();
        }

        function updateTotalScoreDisplay() {
            document.getElementById('totalScore1').textContent = totalScore;
            document.getElementById('totalScore2').textContent = totalScore;
        }

        function updateProgressAndTabs() {
            const steps = document.querySelectorAll('.progress-step');
            const lines = document.querySelectorAll('.progress-line');
            const tabs = document.querySelectorAll('.tab-btn');

            steps.forEach((step, i) => {
                step.className = 'progress-step';
                if (i < currentGame) {
                    step.classList.add('done');
                    step.querySelector('.step-icon').textContent = '✅';
                } else if (i === currentGame) {
                    step.classList.add('active');
                    step.querySelector('.step-icon').textContent = '▶️';
                } else {
                    step.querySelector('.step-icon').textContent = '🔒';
                }
            });

            lines.forEach((line, i) => {
                line.className = 'progress-line';
                if (i < currentGame) line.classList.add('done');
            });

            tabs.forEach((tab, i) => {
                tab.className = 'tab-btn';
                if (i < currentGame) {
                    tab.classList.add('done');
                    tab.innerHTML = tab.dataset.game === 'game1' ? '🎂 保卫蛋糕 ✅' :
                        tab.dataset.game === 'game2' ? '🖼️ 记忆翻牌 ✅' :
                        '🎭 剧本杀 ✅';
                    tab.classList.add('unlocked');
                } else if (i === currentGame) {
                    tab.classList.add('active');
                    tab.classList.add('unlocked');
                    const names = ['🎂 保卫蛋糕', '🖼️ 记忆翻牌', '🎭 剧本杀'];
                    tab.innerHTML = names[i];
                } else {
                    tab.classList.add('locked');
                    const names = ['🎂 保卫蛋糕 🔒', '🖼️ 记忆翻牌 🔒', '🎭 剧本杀 🔒'];
                    tab.innerHTML = names[i];
                }
            });

            document.querySelectorAll('.game-panel').forEach((panel, i) => {
                panel.classList.toggle('active', i === currentGame);
            });

            updateTotalScoreDisplay();
        }

        function unlockNextGame() {
            if (currentGame < 2) {
                currentGame++;
                updateProgressAndTabs();
                if (currentGame === 1) G2.init();
                if (currentGame === 2) G3.init();
                launchMiniConfetti();
            } else {
                showModal('🎊', '🎉 全部通关！', '你太强了！', 'ZK，你完成了所有游戏！陈奕恒为你骄傲！wcy永远爱你！💖',
                    () => {},
                    showCertificate
                );
                launchConfetti();
            }
        }

        // ================================================================
        //  💀  作 弊 系 统
        // ================================================================
        function showCheatModal(gameId, cost) {
            if (totalScore < cost) {
                alert(`💀 分数不足！需要 ${cost} 分，当前只有 ${totalScore} 分。再去赚点分数吧！`);
                return;
            }
            cheatTarget = gameId;
            document.getElementById('cheatCost').textContent = cost;
            document.getElementById('cheatBalance').textContent = totalScore;
            document.getElementById('cheatModal').classList.add('active');
        }

        document.getElementById('cheatConfirm').addEventListener('click', () => {
            const cost = cheatTarget === 'game1' ? 50 : 60;
            if (totalScore >= cost) {
                totalScore -= cost;
                if (cheatTarget === 'game1') {
                    game1Completed = true;
                    if (currentGame === 0) unlockNextGame();
                    document.getElementById('cheat1').disabled = true;
                    showModal('💀', '作弊成功！', '消耗 ' + cost + ' 分', '你通过作弊通关了保卫蛋糕！虽然有点取巧，但wcy还是爱你的 💕',
                        () => {},
                        showCertificate
                    );
                } else if (cheatTarget === 'game2') {
                    game2Completed = true;
                    if (currentGame === 1) unlockNextGame();
                    document.getElementById('cheat2').disabled = true;
                    showModal('💀', '作弊成功！', '消耗 ' + cost + ' 分', '你通过作弊通关了记忆翻牌！下次还是凭实力吧 😜',
                        () => {},
                        showCertificate
                    );
                }
                updateTotalScoreDisplay();
                updateProgressAndTabs();
                document.getElementById('cheatModal').classList.remove('active');
            } else {
                alert('分数不足！');
                document.getElementById('cheatModal').classList.remove('active');
            }
        });

        document.getElementById('cheatCancel').addEventListener('click', () => {
            document.getElementById('cheatModal').classList.remove('active');
        });

        // ================================================================
        //  🎮  游 戏 1：保 卫 蛋 糕
        // ================================================================
        const G1 = {
            score: 0,
            time: 30,
            running: false,
            ended: false,
            objects: new Map(),
            timerInterval: null,
            spawnInterval: null,
            idCounter: 0,
            passed: false,

            canvas: document.getElementById('canvas1'),
            scoreEl: document.getElementById('score1'),
            timerEl: document.getElementById('timer1'),
            startBtn: document.getElementById('start1'),
            resetBtn: document.getElementById('reset1'),
            cheatBtn: document.getElementById('cheat1'),

            init() {
                if (game1Completed) {
                    this.startBtn.disabled = true;
                    this.startBtn.textContent = '✅ 已通关';
                    this.cheatBtn.disabled = true;
                    return;
                }
                this.canvas.innerHTML = '';
                this.objects.clear();
                this.score = 0;
                this.time = 30;
                this.running = false;
                this.ended = false;
                this.passed = false;
                this.updateUI();
                this.startBtn.disabled = false;
                this.startBtn.textContent = '🚀 开始';
                this.cheatBtn.disabled = false;
                clearInterval(this.timerInterval);
                clearInterval(this.spawnInterval);
                this.cheatBtn.textContent = '💀 作弊(50分)';
            },

            updateUI() {
                this.scoreEl.textContent = this.score;
                this.timerEl.textContent = this.time;
            },

            start() {
                if (this.running || game1Completed) return;
                this.init();
                this.running = true;
                this.ended = false;
                this.startBtn.disabled = true;
                this.startBtn.textContent = '⏳ 进行中...';
                this.cheatBtn.disabled = true;
                closeModal();

                this.timerInterval = setInterval(() => {
                    this.time--;
                    this.timerEl.textContent = this.time;
                    if (this.time <= 0) this.end();
                }, 1000);

                this.spawnInterval = setInterval(() => this.spawn(), 400);
                for (let i = 0; i < 4; i++) setTimeout(() => this.spawn(), i * 200);
                this.msgInterval = setInterval(() => this.showFriendMsg(), 3800);
            },

            spawn() {
                if (!this.running || this.ended) return;
                const isGood = Math.random() < 0.45;
                const emojis = isGood ? ['🎂', '🧁', '🍰'] : ['📚', '⏰', '💔', '💰', '😤', '📱'];
                const emoji = emojis[randInt(0, emojis.length - 1)];
                const el = document.createElement('div');
                el.className = 'game-object';
                el.dataset.type = isGood ? 'good' : 'bad';
                el.textContent = emoji;
                el.dataset.points = isGood ? 10 : -5;

                const rect = this.canvas.getBoundingClientRect();
                const size = Math.min(rect.width, rect.height) * 0.12;
                const maxX = this.canvas.clientWidth - size;
                const maxY = this.canvas.clientHeight - size;
                el.style.left = (8 + rand(0, maxX - 16)) + 'px';
                el.style.top = (8 + rand(0, maxY - 16)) + 'px';
                el.style.fontSize = (28 + rand(0, 28)) + 'px';

                const id = this.idCounter++;
                el.dataset.id = id;
                el.addEventListener('click', (e) => { e.stopPropagation();
                    this.handleClick(el, e); });
                el.addEventListener('touchstart', (e) => { e.preventDefault();
                    this.handleClick(el, e); }, { passive: false });

                this.canvas.appendChild(el);
                this.objects.set(id, el);
                setTimeout(() => {
                    if (this.objects.has(id)) {
                        this.objects.get(id).remove();
                        this.objects.delete(id);
                    }
                }, 6000);
            },

            handleClick(el, e) {
                if (!this.running || this.ended) return;
                const points = parseInt(el.dataset.points);
                const good = el.dataset.type === 'good';
                const rect = this.canvas.getBoundingClientRect();
                let x, y;
                if (e.touches) {
                    x = e.touches[0].clientX - rect.left;
                    y = e.touches[0].clientY - rect.top;
                } else {
                    x = e.clientX - rect.left;
                    y = e.clientY - rect.top;
                }
                this.score = Math.max(0, this.score + points);
                this.updateUI();
                const msgs = good ? ['🍰 甜！', '✨ 完美！', '💖 守护！', '🎂 啊呜~', '🌟 好棒！'] : ['📚 走开！', '⏰ 赖床！', '💔 退散！', '💰 暴富！', '😤 不要！'];
                this.showPopup(msgs[randInt(0, msgs.length - 1)], x, y, good);
                el.remove();
                this.objects.delete(parseInt(el.dataset.id));
                if (good) this.miniStars(x, y);
            },

            showPopup(text, x, y, good) {
                const pop = document.createElement('div');
                pop.className = 'popup-text' + (good ? ' good' : ' bad');
                pop.textContent = text;
                pop.style.left = (x - 30) + 'px';
                pop.style.top = (y - 20) + 'px';
                this.canvas.appendChild(pop);
                setTimeout(() => pop.remove(), 1000);
            },

            miniStars(cx, cy) {
                const colors = ['#ffd700', '#4a9eff', '#ff9ff3', '#54a0ff', '#feca57'];
                for (let i = 0; i < 6; i++) {
                    const s = document.createElement('div');
                    s.textContent = ['✦', '✧', '•', '☆'][randInt(0, 3)];
                    s.style.cssText = `
                                position:absolute; left:${cx+rand(-30,30)}px; top:${cy+rand(-30,30)}px;
                                font-size:${12+rand(0,16)}px; color:${colors[randInt(0,colors.length-1)]};
                                pointer-events:none; z-index:40; opacity:1;
                                transition: all 0.6s ease-out;
                            `;
                    this.canvas.appendChild(s);
                    setTimeout(() => {
                        s.style.opacity = '0';
                        s.style.transform = `translate(${rand(-40,40)}px, ${-40-rand(0,40)}px) scale(0.2)`;
                    }, 20);
                    setTimeout(() => s.remove(), 700);
                }
            },

            showFriendMsg() {
                if (!this.running || this.ended) return;
                const msgs = [
                    '👭 ZK！手速！', '⚡ 快点！蛋糕要没了！',
                    '🥤 加油！赢了请你奶茶！', '😏 就这？再来！',
                    '💪 18岁支棱起来！', '✨ 陈奕恒给你力量！',
                    '❤️ wcy 在为你打call！'
                ];
                const el = document.createElement('div');
                el.textContent = msgs[randInt(0, msgs.length - 1)];
                el.style.cssText = `
                            position:absolute; top:${10+rand(0,70)}%; right:-200px;
                            font-size:${14+rand(0,6)}px; font-weight:700;
                            color:#0a2a44; background:rgba(255,255,255,0.8);
                            padding:4px 16px; border-radius:40px; white-space:nowrap;
                            z-index:30; box-shadow:0 4px 12px rgba(0,0,0,0.08);
                            pointer-events:none; border:1px solid rgba(255,255,255,0.4);
                        `;
                this.canvas.appendChild(el);
                let pos = -200;
                const speed = 1.8;
                const anim = () => {
                    if (!this.running || this.ended || !el.parentNode) { el.remove(); return; }
                    pos += speed;
                    el.style.right = pos + 'px';
                    if (pos < this.canvas.clientWidth + 100) requestAnimationFrame(anim);
                    else el.remove();
                };
                requestAnimationFrame(anim);
            },

            end() {
                if (this.ended) return;
                this.running = false;
                this.ended = true;
                clearInterval(this.timerInterval);
                clearInterval(this.spawnInterval);
                clearInterval(this.msgInterval);
                this.startBtn.disabled = false;
                this.startBtn.textContent = '🚀 开始';
                this.cheatBtn.disabled = false;
                this.objects.forEach(el => el.remove());
                this.objects.clear();

                if (this.score >= 60 && !game1Completed) {
                    this.passed = true;
                    game1Completed = true;
                    totalScore += this.score;
                    this.cheatBtn.disabled = true;
                    this.startBtn.textContent = '✅ 已通关';
                    launchConfetti();
                    showModal('👑', '🎉 通关成功！', this.score + '分', '你守护了蛋糕！18岁的第一关通过！接下来解锁记忆翻牌！',
                        () => { unlockNextGame(); },
                        showCertificate
                    );
                    unlockNextGame();
                } else if (!game1Completed) {
                    let msg = this.score >= 40 ? '差一点就通关了！再试一次吧！' : '多练习一下，目标60分！加油！';
                    showModal('😅', '未通关', this.score + '分', msg + ' (需要≥60分)',
                        () => { this.init(); },
                        showCertificate
                    );
                }
                updateTotalScoreDisplay();
                updateProgressAndTabs();
            },

            reset() {
                if (game1Completed) return;
                this.init();
                closeModal();
                this.objects.forEach(el => el.remove());
                this.objects.clear();
                this.cheatBtn.disabled = false;
            }
        };

        // ================================================================
        //  🎮  游 戏 2：记 忆 翻 牌
        // ================================================================
        const G2 = {
            cards: [],
            flipped: [],
            matched: 0,
            score: 0,
            time: 60,
            running: false,
            ended: false,
            lock: false,
            timerInterval: null,
            passed: false,

            canvas: document.getElementById('canvas2'),
            scoreEl: document.getElementById('score2'),
            timerEl: document.getElementById('timer2'),
            startBtn: document.getElementById('start2'),
            resetBtn: document.getElementById('reset2'),
            cheatBtn: document.getElementById('cheat2'),

            PAIRS: [
                { emoji: '⭐', name: '星星' },
                { emoji: '🎤', name: '麦克风' },
                { emoji: '💙', name: '应援色' },
                { emoji: '✨', name: '光芒' },
                { emoji: '🎶', name: '音符' },
                { emoji: '🏆', name: '奖杯' },
                { emoji: '🌙', name: '月亮' },
                { emoji: '🌸', name: '花' },
            ],

            init() {
                if (game2Completed) {
                    this.startBtn.disabled = true;
                    this.startBtn.textContent = '✅ 已通关';
                    this.cheatBtn.disabled = true;
                    return;
                }
                if (!game1Completed && currentGame !== 1) {
                    this.startBtn.disabled = true;
                    this.startBtn.textContent = '🔒 未解锁';
                    this.cheatBtn.disabled = true;
                    return;
                }
                this.canvas.innerHTML = '';
                this.flipped = [];
                this.matched = 0;
                this.score = 0;
                this.time = 60;
                this.running = false;
                this.ended = false;
                this.lock = false;
                this.passed = false;
                this.updateUI();
                this.startBtn.disabled = false;
                this.startBtn.textContent = '🚀 开始';
                this.cheatBtn.disabled = false;
                this.cheatBtn.textContent = '💀 作弊(60分)';
                clearInterval(this.timerInterval);
                this.renderCards(false);
            },

            renderCards(faceUp) {
                this.canvas.innerHTML = '';
                let arr = [];
                this.PAIRS.forEach((p, idx) => {
                    arr.push({ idx, emoji: p.emoji, name: p.name, matched: false });
                    arr.push({ idx, emoji: p.emoji, name: p.name, matched: false });
                });
                shuffle(arr);
                this.cards = arr.map((item, i) => ({ ...item, id: i, flipped: false }));
                this.cards.forEach(c => c.flipped = faceUp);
                this.render();
            },

            render() {
                this.canvas.style.display = 'grid';
                this.canvas.style.gridTemplateColumns = 'repeat(4,1fr)';
                this.canvas.innerHTML = '';
                this.cards.forEach((card, index) => {
                    const div = document.createElement('div');
                    div.style.cssText = `
                                background: ${card.flipped || card.matched ? '#fff' : '#1f5a9e'};
                                border-radius: 14px;
                                display: flex;
                                align-items: center;
                                justify-content: center;
                                font-size: 32px;
                                font-weight: 700;
                                color: #0a2a44;
                                cursor: ${this.running && !this.ended ? 'pointer' : 'default'};
                                box-shadow: 0 4px 8px rgba(0,0,0,0.12);
                                transition: all 0.2s;
                                aspect-ratio: 1;
                                border: 2px solid ${card.matched ? '#4a9eff' : 'rgba(255,255,255,0.3)'};
                                background: ${card.flipped || card.matched ? 'rgba(255,255,255,0.9)' : 'linear-gradient(145deg,#2d7bcb,#1a4f8a)'};
                            `;
                    div.textContent = (card.flipped || card.matched) ? card.emoji : '?';
                    div.dataset.index = index;
                    if (this.running && !this.ended) {
                        div.addEventListener('click', () => this.flipCard(index));
                        div.addEventListener('touchstart', (e) => { e.preventDefault();
                            this.flipCard(index); }, { passive: false });
                    }
                    this.canvas.appendChild(div);
                });
            },

            flipCard(index) {
                if (this.lock || !this.running || this.ended) return;
                const card = this.cards[index];
                if (card.flipped || card.matched) return;
                if (this.flipped.length >= 2) return;

                card.flipped = true;
                this.flipped.push(index);
                this.render();

                if (this.flipped.length === 2) {
                    this.lock = true;
                    const i1 = this.flipped[0],
                        i2 = this.flipped[1];
                    const c1 = this.cards[i1],
                        c2 = this.cards[i2];
                    if (c1.idx === c2.idx) {
                        c1.matched = true;
                        c2.matched = true;
                        this.matched++;
                        this.score += 10;
                        this.updateUI();
                        this.flipped = [];
                        this.lock = false;
                        this.render();
                        if (this.matched === this.PAIRS.length) {
                            setTimeout(() => this.end(true), 300);
                        }
                    } else {
                        setTimeout(() => {
                            c1.flipped = false;
                            c2.flipped = false;
                            this.flipped = [];
                            this.lock = false;
                            this.render();
                        }, 800);
                    }
                }
            },

            updateUI() {
                this.scoreEl.textContent = this.matched;
                this.timerEl.textContent = this.time;
            },

            start() {
                if (this.running || game2Completed || !game1Completed) return;
                this.init();
                this.running = true;
                this.ended = false;
                this.startBtn.disabled = true;
                this.startBtn.textContent = '⏳ 进行中...';
                this.cheatBtn.disabled = true;
                closeModal();
                this.cards.forEach(c => c.flipped = false);
                this.matched = 0;
                this.score = 0;
                this.flipped = [];
                this.lock = false;
                this.render();

                this.timerInterval = setInterval(() => {
                    this.time--;
                    this.timerEl.textContent = this.time;
                    if (this.time <= 0) this.end(false);
                }, 1000);
            },

            end(win) {
                if (this.ended) return;
                this.running = false;
                this.ended = true;
                clearInterval(this.timerInterval);
                this.startBtn.disabled = false;
                this.startBtn.textContent = '🚀 开始';
                this.cheatBtn.disabled = false;
                this.cards.forEach(c => c.flipped = true);
                this.render();

                if (win && this.matched === this.PAIRS.length && !game2Completed) {
                    this.passed = true;
                    game2Completed = true;
                    totalScore += this.score + 20;
                    this.cheatBtn.disabled = true;
                    this.startBtn.textContent = '✅ 已通关';
                    launchConfetti();
                    showModal('🧠', '🎉 通关成功！', this.matched + '/' + this.PAIRS.length + ' 对', '记忆大师！你太强了！剧本杀即将解锁！',
                        () => { unlockNextGame(); },
                        showCertificate
                    );
                    unlockNextGame();
                } else if (!game2Completed) {
                    let msg = this.matched >= 4 ? '再努力一下！全部配对吧！' : '多练习记忆力！目标配对所有8对！';
                    showModal('😅', '未通关', this.matched + '/' + this.PAIRS.length + ' 对', msg,
                        () => { this.init(); },
                        showCertificate
                    );
                }
                updateTotalScoreDisplay();
                updateProgressAndTabs();
            },

            reset() {
                if (game2Completed) return;
                this.init();
                closeModal();
                this.cards.forEach(c => c.flipped = false);
                this.matched = 0;
                this.score = 0;
                this.flipped = [];
                this.lock = false;
                this.render();
                clearInterval(this.timerInterval);
                this.running = false;
                this.ended = false;
                this.startBtn.disabled = false;
                this.startBtn.textContent = '🚀 开始';
                this.time = 60;
                this.updateUI();
                if (!game1Completed) {
                    this.startBtn.disabled = true;
                    this.startBtn.textContent = '🔒 未解锁';
                    this.cheatBtn.disabled = true;
                }
            }
        };

        // ================================================================
        //  🎮  游 戏 3：剧 本 杀
        // ================================================================
        const G3 = {
            suspects: [],
            interviewed: [],
            clues: [],
            gameOver: false,
            solved: false,
            passed: false,

            canvas: document.getElementById('canvas3'),
            scoreEl: document.getElementById('score3'),
            timerEl: document.getElementById('timer3'),
            resetBtn: document.getElementById('reset3'),

            storyData: {
                title: '🎭 排练室谜案',
                narrative: '陈奕恒在排练室发现了一张神秘纸条，上面写着：<span class="highlight">"今晚10点，天台见。——？"</span><br>你作为侦探 ZK，需要找出是谁留下的纸条！',
                suspects: [
                    { id: 'zhang', name: '张桂源', emoji: '🧑', clues: ['下午在排练室练舞', '看到陈奕恒在写东西'] },
                    { id: 'zuo', name: '左奇函', emoji: '🧑', clues: ['晚上8点看到有人去天台', '那人穿着蓝色外套'] },
                    { id: 'yang', name: '杨博文', emoji: '🧑', clues: ['知道有人想给惊喜', '但不知道具体是谁'] },
                    { id: 'chen', name: '陈浚铭', emoji: '🧑', clues: ['纸条字迹有点眼熟', '像是张桂源的字'] },
                ],
                answer: {
                    suspectId: 'zhang',
                    reason: '张桂源下午在排练室看到陈奕恒写东西，晚上又有人去天台，字迹也像他的'
                }
            },

            init() {
                if (game3Completed) {
                    this.renderCompleted();
                    return;
                }
                if (!game2Completed) {
                    this.renderLocked();
                    return;
                }
                this.interviewed = [];
                this.clues = [];
                this.gameOver = false;
                this.solved = false;
                this.passed = false;
                this.suspects = this.storyData.suspects.map(s => ({ ...s }));
                this.updateUI();
                this.render();
            },

            renderLocked() {
                const container = document.getElementById('storyContainer');
                container.innerHTML = `
                            <div style="display:flex;flex-direction:column;align-items:center;justify-content:center;height:100%;gap:12px;text-align:center;padding:20px;color:#1d4a7a;">
                                <div style="font-size:64px;">🔒</div>
                                <div style="font-size:18px;font-weight:700;">剧本杀未解锁</div>
                                <div style="font-size:14px;opacity:0.7;">完成记忆翻牌后即可解锁！</div>
                            </div>
                        `;
            },

            renderCompleted() {
                const container = document.getElementById('storyContainer');
                container.innerHTML = `
                            <div style="display:flex;flex-direction:column;align-items:center;justify-content:center;height:100%;gap:12px;text-align:center;padding:20px;color:#00a381;">
                                <div style="font-size:64px;">🎉</div>
                                <div style="font-size:18px;font-weight:700;">全部通关！</div>
                                <div style="font-size:14px;">你太棒了 ZK！🎂</div>
                            </div>
                        `;
            },

            render() {
                if (game3Completed) { this.renderCompleted(); return; }
                if (!game2Completed) { this.renderLocked(); return; }

                const container = document.getElementById('storyContainer');
                const data = this.storyData;

                let html = `
                            <div class="story-title">${data.title}</div>
                            <div class="story-narrative">${data.narrative}</div>
                            <div class="suspect-grid">
                        `;

                this.suspects.forEach((s, idx) => {
                    const interviewed = this.interviewed.includes(s.id);
                    const clueText = interviewed ? s.clues.join('；') : '❓ 点击询问';
                    html += `
                                <div class="suspect-card ${interviewed ? 'interviewed' : ''}" data-id="${s.id}" data-index="${idx}">
                                    <div class="avatar">${s.emoji}</div>
                                    <div class="name">${s.name}</div>
                                    <div class="status">${interviewed ? '✅ 已询问' : '🔍 未询问'}</div>
                                    <div class="clue-box">${clueText}</div>
                                </div>
                            `;
                });

                html += `
                            </div>
                            <div class="clue-log" id="clueLog">
                                ${this.clues.length === 0 ? '💡 点击嫌疑人获取线索' : this.clues.map(c => `<div class="clue-item"><span class="clue-suspect">${c.name}：</span>${c.clue}</div>`).join('')}
                            </div>
                            <div class="judge-area">
                                <select id="judgeSelect">
                                    <option value="">👤 指认谁写的？</option>
                                    ${this.suspects.map(s => `<option value="${s.id}">${s.emoji} ${s.name}</option>`).join('')}
                                </select>
                                <button class="btn btn-green" id="judgeBtn">🔍 破案！</button>
                            </div>
                            <div class="result-banner waiting" id="resultBanner">${this.gameOver ? (this.solved ? '🎉 破案成功！' : '😅 再想想...') : '🕵️ 收集线索，找出真凶！'}</div>
                        `;

                container.innerHTML = html;

                container.querySelectorAll('.suspect-card').forEach(el => {
                    el.addEventListener('click', () => {
                        const id = el.dataset.id;
                        this.interviewSuspect(id);
                    });
                });

                const judgeBtn = document.getElementById('judgeBtn');
                const judgeSelect = document.getElementById('judgeSelect');
                if (judgeBtn) {
                    judgeBtn.addEventListener('click', () => {
                        const selected = judgeSelect.value;
                        if (!selected) {
                            alert('请先选择你要指认的嫌疑人！');
                            return;
                        }
                        this.judge(selected);
                    });
                }
                this.updateUI();
            },

            interviewSuspect(id) {
                if (this.gameOver || game3Completed) return;
                if (this.interviewed.includes(id)) {
                    alert('这个人你已经问过啦！去问问其他人吧～');
                    return;
                }

                const suspect = this.suspects.find(s => s.id === id);
                if (!suspect) return;

                this.interviewed.push(id);
                const clueIndex = this.interviewed.length % suspect.clues.length;
                const clue = suspect.clues[clueIndex % suspect.clues.length];
                this.clues.push({ name: suspect.name, clue: clue });
                this.render();

                if (this.interviewed.length === this.suspects.length) {
                    setTimeout(() => {
                        document.getElementById('resultBanner').textContent = '🔍 所有嫌疑人都问过了！现在指认真凶吧！';
                        document.getElementById('resultBanner').className = 'result-banner waiting';
                    }, 300);
                }
                this.updateUI();
            },

            judge(selectedId) {
                if (this.gameOver || game3Completed) return;
                if (this.interviewed.length < 2) {
                    alert('🕵️ 线索太少了！至少先问2个嫌疑人再破案吧！');
                    return;
                }

                const correctId = this.storyData.answer.suspectId;
                if (selectedId === correctId) {
                    this.gameOver = true;
                    this.solved = true;
                    this.passed = true;
                    game3Completed = true;
                    totalScore += 50;
                    launchConfetti();
                    document.getElementById('resultBanner').textContent = '🎉 破案成功！你真是太厉害了！陈奕恒的谜案被你解开啦！';
                    document.getElementById('resultBanner').className = 'result-banner success';
                    this.scoreEl.textContent = this.interviewed.length;
                    showModal('🕵️', '🎉 破案成功！', '真相只有一个！', '你成功找出了真凶——张桂源！陈奕恒一定会感谢你的！wcy为你骄傲！\n🎊 所有游戏通关！',
                        () => {},
                        showCertificate
                    );
                    launchConfetti();
                    updateTotalScoreDisplay();
                    updateProgressAndTabs();
                    this.renderCompleted();
                } else {
                    document.getElementById('resultBanner').textContent = '😅 指认错了...再想想谁最可疑？注意看每个人的线索！';
                    document.getElementById('resultBanner').className = 'result-banner fail';
                    setTimeout(() => {
                        document.getElementById('resultBanner').className = 'result-banner waiting';
                        document.getElementById('resultBanner').textContent = '🕵️ 继续收集线索吧！';
                    }, 2500);
                }
                this.updateUI();
            },

            updateUI() {
                this.scoreEl.textContent = this.interviewed.length;
                this.timerEl.textContent = this.gameOver ? (this.solved ? '✅' : '❌') : '--';
            },

            reset() {
                if (game3Completed) return;
                closeModal();
                this.init();
                this.render();
                this.updateUI();
            }
        };

        // ================================================================
        //  🔗  切 换 游 戏
        // ================================================================
        document.querySelectorAll('.tab-btn').forEach(btn => {
            btn.addEventListener('click', function() {
                if (this.classList.contains('locked')) return;
                const gameId = this.dataset.game;
                const index = parseInt(this.dataset.index);
                if (index > currentGame) return;

                document.querySelectorAll('.tab-btn').forEach(b => b.classList.remove('active'));
                this.classList.add('active');
                document.querySelectorAll('.game-panel').forEach(p => p.classList.remove('active'));
                document.getElementById(gameId).classList.add('active');

                if (gameId === 'game1') G1.init();
                else if (gameId === 'game2') G2.init();
                else if (gameId === 'game3') G3.init();
                closeModal();
            });
        });

        // ================================================================
        //  💀  作 弊 按 钮 绑 定
        // ================================================================
        document.getElementById('cheat1').addEventListener('click', () => {
            if (game1Completed) return;
            showCheatModal('game1', 50);
        });

        document.getElementById('cheat2').addEventListener('click', () => {
            if (game2Completed) return;
            showCheatModal('game2', 60);
        });

        // ================================================================
        //  🚀  初 始 化
        // ================================================================
        G1.init();
        G2.init();
        G3.init();

        G1.startBtn.addEventListener('click', () => G1.start());
        G1.resetBtn.addEventListener('click', () => G1.reset());

        G2.startBtn.addEventListener('click', () => G2.start());
        G2.resetBtn.addEventListener('click', () => G2.reset());

        G3.resetBtn.addEventListener('click', () => G3.reset());

        console.log('🎂 ZK 18岁生日快乐！❤️ 你永远的好朋友 wcy 制作');
        console.log('🔐 密码: 0802');
        console.log('🎵 歌曲: 陈奕恒 - Be Yourself (自定义播放器)');
        console.log('🎮 游戏顺序：保卫蛋糕 → 记忆翻牌 → 剧本杀');
        console.log('💀 作弊条件：消耗分数直接通关');
    </script>
</body>
</html>
