<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>FC사나이 유니폼 월드컵</title>
    <style>
        /* 기본 스타일 및 세련된 미드나잇 그라데이션 배경 */
        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
            background: radial-gradient(circle at top, #1e293b 0%, #0f172a 100%);
            color: #f8fafc;
            margin: 0;
            padding: 0;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: flex-start;
            min-height: 100vh;
            padding-bottom: 50px;
            box-sizing: border-box;
        }

        /* 타이틀 디자인: 깨지는 이모지 제거 후 flex 정렬 적용 */
        h1 {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
            font-size: 1.5rem;
            margin: 25px 0 10px 0;
            font-weight: 900;
            background: linear-gradient(135deg, #38bdf8 0%, #0284c7 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            text-shadow: 0 4px 10px rgba(56, 189, 248, 0.15);
            letter-spacing: -0.06em;
            text-align: center;
            white-space: nowrap;
        }

        /* 라운드 패널: 반투명 유리(Blur) 효과 */
        #round-title {
            font-size: 0.95rem;
            font-weight: bold;
            margin-bottom: 25px;
            background: rgba(30, 41, 59, 0.7);
            backdrop-filter: blur(8px);
            -webkit-backdrop-filter: blur(8px);
            padding: 6px 20px;
            border-radius: 30px;
            border: 1px solid rgba(56, 189, 248, 0.3);
            color: #38bdf8;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.25);
            letter-spacing: 0.05em;
        }

        /* 메인 정렬 컨테이너 */
        .container {
            display: flex;
            flex-direction: column;
            width: 100%;
            max-width: 420px;
            gap: 10px;
            padding: 0 20px;
            box-sizing: border-box;
        }

        /* 플랫 네온 스타일 카드 */
        .card {
            width: 100%;
            background: #1e293b;
            border-radius: 24px;
            overflow: hidden;
            cursor: pointer;
            transition: all 0.2s cubic-bezier(0.4, 0, 0.2, 1);
            border: 1px solid rgba(255, 255, 255, 0.05);
            box-shadow: 0 8px 25px rgba(0, 0, 0, 0.3);
            display: flex;
            flex-direction: column;
            align-items: center;
            -webkit-tap-highlight-color: transparent;
        }

        /* PC 마우스 반응 */
        @media (min-width: 768px) {
            .card:hover {
                transform: translateY(-4px);
                border-color: rgba(56, 189, 248, 0.4);
                box-shadow: 0 12px 30px rgba(56, 189, 248, 0.15);
            }
            h1 {
                font-size: 1.8rem;
            }
        }

        /* 모바일 터치 피드백 (손맛 강조) */
        .card:active {
            transform: scale(0.96);
            border-color: #38bdf8;
            box-shadow: 0 0 20px rgba(56, 189, 248, 0.35);
        }

        /* VS 구역 레이아웃 */
        .vs-wrapper {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 15px;
            margin: 15px 0;
            width: 100%;
        }
        
        .vs-line {
            flex: 1;
            height: 2px;
            background: linear-gradient(90deg, transparent, rgba(239, 68, 68, 0.6), transparent);
        }

        .vs {
            font-size: 1.4rem;
            font-weight: 900;
            color: #ef4444;
            font-style: italic;
            text-shadow: 0 0 12px rgba(239, 68, 68, 0.8);
            letter-spacing: 0.05em;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        /* 절대 깨지지 않는 SVG 축구공 아이콘 공통 스타일 */
        .soccer-icon {
            width: 24px;
            height: 24px;
            vertical-align: middle;
        }

        /* 이미지 부모 영역: 왜곡 없이 깔끔하게 배치 */
        .image-wrapper {
            width: 100%;
            height: 270px;
            background: #0f172a;
            display: flex;
            align-items: center;
            justify-content: center;
            overflow: hidden;
        }

        .image-wrapper img {
            width: 90%;
            height: 90%;
            object-fit: contain;
        }

        /* 텍스트 영역 */
        .name {
            padding: 16px 15px;
            font-size: 1.05rem;
            font-weight: 700;
            text-align: center;
            width: 100%;
            box-sizing: border-box;
            background: #1e293b;
            color: #e2e8f0;
            border-top: 1px solid rgba(255, 255, 255, 0.03);
        }

        /* 최종 화면 구성 */
        #winner-container {
            display: none;
            flex-direction: column;
            align-items: center;
            width: 100%;
            max-width: 420px;
            padding: 0 20px;
            box-sizing: border-box;
        }

        /* 우승 골드 카드 효과 */
        .winner-card {
            width: 100%;
            border: 2px solid #f59e0b;
            box-shadow: 0 0 35px rgba(245, 158, 11, 0.3);
            pointer-events: none;
        }

        /* 다시하기 버튼 모던화 */
        .restart-btn {
            margin-top: 30px;
            padding: 16px;
            font-size: 1.1rem;
            font-weight: 700;
            background: linear-gradient(135deg, #38bdf8 0%, #0284c7 100%);
            color: #ffffff;
            border: none;
            border-radius: 16px;
            cursor: pointer;
            width: 100%;
            box-shadow: 0 4px 15px rgba(2, 132, 199, 0.25);
            transition: all 0.2s ease;
        }

        .restart-btn:active {
            transform: scale(0.97);
        }
    </style>
</head>
<body>

    <!-- 고화질 축구공 SVG가 적용된 타이틀 -->
    <h1>
        <svg class="soccer-icon" viewBox="0 0 512 512" fill="#ffffff"><path d="M256 0a256 256 0 1 0 0 512 A256 256 0 1 0 256 0zM128 171.5l56.6-18.4 41.4 38.3L200 244l-72-5.4V171.5zm6.5 106.8l56.5 4.3 12.3 54.3-46.7 34.6-22.1-93.2zm110 162.2l-33.1-43.2 34.6-25.6 44 19.3-5.5 49.5-40 0zm43.9-98.3l-34.4-15.1-4.8-51.7 49-36.2 41.7 33.1-51.5 69.9zm49.1-127.3l-41.2-32.7 13.9-53.9 57.5 13.3-30.2 73.3zm5.7-142.1l-40.4-9.3L287.4 96l46.2-46.7 10.1 23.5-9.7 41.1zm-174.4 7l24 49-41.6 13.5L138.3 88.6 168.8 81.8zm-76.4 75.3l57.7 12.9V219L92.4 213.6v-56.5zM64.6 256l46.1 3.5 17.6 74.3L91.4 361.3 64.6 256zm71.7 127l37.2-27.6 44.9 58.6-47.5 25.1-34.6-56.1zm174.1 52.8l-15.9-45.7 39.8-17.4 38.1 40-62 23.1zm107.1-54.8l-44.4-46.6 41.1-55.8 40.5 43.1-37.2 59.3zm29.9-101.4l-42-44.7 24.1-58.5 41.3 43.3-23.4 59.9z"/></svg>
        <span>FC사나이 유니폼 월드컵</span>
        <svg class="soccer-icon" viewBox="0 0 512 512" fill="#ffffff"><path d="M256 0a256 256 0 1 0 0 512 A256 256 0 1 0 256 0zM128 171.5l56.6-18.4 41.4 38.3L200 244l-72-5.4V171.5zm6.5 106.8l56.5 4.3 12.3 54.3-46.7 34.6-22.1-93.2zm110 162.2l-33.1-43.2 34.6-25.6 44 19.3-5.5 49.5-40 0zm43.9-98.3l-34.4-15.1-4.8-51.7 49-36.2 41.7 33.1-51.5 69.9zm49.1-127.3l-41.2-32.7 13.9-53.9 57.5 13.3-30.2 73.3zm5.7-142.1l-40.4-9.3L287.4 96l46.2-46.7 10.1 23.5-9.7 41.1zm-174.4 7l24 49-41.6 13.5L138.3 88.6 168.8 81.8zm-76.4 75.3l57.7 12.9V219L92.4 213.6v-56.5zM64.6 256l46.1 3.5 17.6 74.3L91.4 361.3 64.6 256zm71.7 127l37.2-27.6 44.9 58.6-47.5 25.1-34.6-56.1zm174.1 52.8l-15.9-45.7 39.8-17.4 38.1 40-62 23.1zm107.1-54.8l-44.4-46.6 41.1-55.8 40.5 43.1-37.2 59.3zm29.9-101.4l-42-44.7 24.1-58.5 41.3 43.3-23.4 59.9z"/></svg>
    </h1>
    <div id="round-title">16강 - 1 / 8</div>

    <div class="container" id="game-container">
        <div class="card" onclick="selectCandidate(0)">
            <div class="image-wrapper">
                <img id="img-left" src="" alt="유니폼 위쪽">
            </div>
            <div class="name" id="name-left">유니폼 A</div>
        </div>
        
        <!-- 깨지지 않는 그래픽 기반의 모던 VS 존 -->
        <div class="vs-wrapper">
            <div class="vs-line"></div>
            <div class="vs">
                <svg class="soccer-icon" viewBox="0 0 512 512" fill="#ef4444" style="filter: drop-shadow(0 0 6px rgba(239, 68, 68, 0.6));"><path d="M256 0a256 256 0 1 0 0 512 A256 256 0 1 0 256 0zM128 171.5l56.6-18.4 41.4 38.3L200 244l-72-5.4V171.5zm6.5 106.8l56.5 4.3 12.3 54.3-46.7 34.6-22.1-93.2zm110 162.2l-33.1-43.2 34.6-25.6 44 19.3-5.5 49.5-40 0zm43.9-98.3l-34.4-15.1-4.8-51.7 49-36.2 41.7 33.1-51.5 69.9zm49.1-127.3l-41.2-32.7 13.9-53.9 57.5 13.3-30.2 73.3zm5.7-142.1l-40.4-9.3L287.4 96l46.2-46.7 10.1 23.5-9.7 41.1zm-174.4 7l24 49-41.6 13.5L138.3 88.6 168.8 81.8zm-76.4 75.3l57.7 12.9V219L92.4 213.6v-56.5zM64.6 256l46.1 3.5 17.6 74.3L91.4 361.3 64.6 256zm71.7 127l37.2-27.6 44.9 58.6-47.5 25.1-34.6-56.1zm174.1 52.8l-15.9-45.7 39.8-17.4 38.1 40-62 23.1zm107.1-54.8l-44.4-46.6 41.1-55.8 40.5 43.1-37.2 59.3zm29.9-101.4l-42-44.7 24.1-58.5 41.3 43.3-23.4 59.9z"/></svg>
                VS
                <svg class="soccer-icon" viewBox="0 0 512 512" fill="#ef4444" style="filter: drop-shadow(0 0 6px rgba(239, 68, 68, 0.6));"><path d="M256 0a256 256 0 1 0 0 512 A256 256 0 1 0 256 0zM128 171.5l56.6-18.4 41.4 38.3L200 244l-72-5.4V171.5zm6.5 106.8l56.5 4.3 12.3 54.3-46.7 34.6-22.1-93.2zm110 162.2l-33.1-43.2 34.6-25.6 44 19.3-5.5 49.5-40 0zm43.9-98.3l-34.4-15.1-4.8-51.7 49-36.2 41.7 33.1-51.5 69.9zm49.1-127.3l-41.2-32.7 13.9-53.9 57.5 13.3-30.2 73.3zm5.7-142.1l-40.4-9.3L287.4 96l46.2-46.7 10.1 23.5-9.7 41.1zm-174.4 7l24 49-41.6 13.5L138.3 88.6 168.8 81.8zm-76.4 75.3l57.7 12.9V219L92.4 213.6v-56.5zM64.6 256l46.1 3.5 17.6 74.3L91.4 361.3 64.6 256zm71.7 127l37.2-27.6 44.9 58.6-47.5 25.1-34.6-56.1zm174.1 52.8l-15.9-45.7 39.8-17.4 38.1 40-62 23.1zm107.1-54.8l-44.4-46.6 41.1-55.8 40.5 43.1-37.2 59.3zm29.9-101.4l-42-44.7 24.1-58.5 41.3 43.3-23.4 59.9z"/></svg>
            </div>
            <div class="vs-line"></div>
        </div>
        
        <div class="card" onclick="selectCandidate(1)">
            <div class="image-wrapper">
                <img id="img-right" src="" alt="유니폼 아래쪽">
            </div>
            <div class="name" id="name-right">유니폼 B</div>
        </div>
    </div>

    <div id="winner-container">
        <h2 style="color: #f59e0b; font-size: 1.5rem; margin-bottom: 20px; text-align: center; font-weight: 800;">🏆 MY PICK 🏆</h2>
        <div class="card winner-card">
            <div class="image-wrapper">
                <img id="img-winner" src="" alt="우승 유니폼">
            </div>
            <div class="name" id="name-winner">우승 유니폼</div>
        </div>
        <button class="restart-btn" onclick="restartGame()">다시 하기</button>
    </div>

    <script>
        const initialImages = [
            { src: "https://i.postimg.cc/PCy9pFxZ/image.png", name: "민트그린" },
            { src: "https://i.postimg.cc/68tFQN93/image-1.png", name: "핑크" },
            { src: "https://i.postimg.cc/18sbzZ94/image-2.png", name: "발렌시아 느낌" },
            { src: "https://i.postimg.cc/SnkHKpyY/image-3.png", name: "블랙 카라 화이트라인" },
            { src: "https://i.postimg.cc/3kYzwHKd/image-4.png", name: "블랙 & 형광" },
            { src: "https://i.postimg.cc/CRS9KVF5/image-5.png", name: "체커보드" },
            { src: "https://i.postimg.cc/21rg5fzW/image-6.png", name: "블랙 레드 스트라이프" },
            { src: "https://i.postimg.cc/cv0PJNsY/image-7.png", name: "대한민국 국대 느낌" },
            { src: "https://i.postimg.cc/TKfBPXRg/image-8.png", name: "블랙 화이트 카라" },
            { src: "https://i.postimg.cc/21rg5fz4/image-9.png", name: "딥 블루" },
            { src: "https://i.postimg.cc/68tFQN9r/image-10.png", name: "마블링(김홍중's PICK)" },
            { src: "https://i.postimg.cc/9DCsfjWt/image-11.jpg", name: "유벤투스 느낌" },
            { src: "https://i.postimg.cc/gxm10PYy/image-12.jpg", name: "AS로마 느낌" },
            { src: "https://i.postimg.cc/TK0FLHwy/image-13.jpg", name: "블랙 & 핫핑크" },
            { src: "https://i.postimg.cc/68cg2134/image-14.jpg", name: "딥그린 & 옐로우" },
            { src: "https://i.postimg.cc/hXs6z3j7/image-16.jpg", name: "화이트 & 블랙 래글런" }
        ];

        let candidates = [];
        let winners = [];
        let currentRound = 16;
        let matchIndex = 0;

        function shuffle(array) {
            return array.sort(() => Math.random() - 0.5);
        }

        function initGame() {
            candidates = shuffle([...initialImages]);
            winners = [];
            currentRound = 16;
            matchIndex = 0;
            document.getElementById('game-container').style.display = 'flex';
            document.getElementById('winner-container').style.display = 'none';
            document.getElementById('round-title').style.display = 'block';
            updateMatch();
        }

        function updateMatch() {
            let roundText = "";
            if (currentRound === 2) {
                roundText = "💥 결승전 💥";
            } else if (currentRound === 4) {
                roundText = `4강 - ${matchIndex + 1} / 2`;
            } else {
                roundText = `${currentRound}강 - ${matchIndex + 1} / ${currentRound / 2}`;
            }
            document.getElementById('round-title').innerText = roundText;

            const left = candidates[matchIndex * 2];
            const right = candidates[matchIndex * 2 + 1];

            document.getElementById('img-left').src = left.src;
            document.getElementById('name-left').innerText = left.name;

            document.getElementById('img-right').src = right.src;
            document.getElementById('name-right').innerText = right.name;
            
            window.scrollTo({ top: 0, behavior: 'smooth' });
        }

        function selectCandidate(selectedIndex) {
            const winner = candidates[matchIndex * 2 + selectedIndex];
            winners.push(winner);

            matchIndex++;

            if (matchIndex >= currentRound / 2) {
                if (currentRound === 2) {
                    showWinner(winners[0]);
                    return;
                }
                candidates = [...winners];
                winners = [];
                currentRound = currentRound / 2;
                matchIndex = 0;
            }

            updateMatch();
        }

        function showWinner(finalWinner) {
            document.getElementById('game-container').style.display = 'none';
            document.getElementById('round-title').style.display = 'none';
            
            const winnerContainer = document.getElementById('winner-container');
            winnerContainer.style.display = 'flex';
            
            document.getElementById('img-winner').src = finalWinner.src;
            document.getElementById('name-winner').innerText = finalWinner.name;
        }

        function restartGame() {
            initGame();
        }

        window.onload = initGame;
