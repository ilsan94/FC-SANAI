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

        /* 타이틀 디자인: 모바일 한 줄 표기를 위해 폰트 크기 하향 및 자간 축소 */
        h1 {
            font-size: 1.5rem; /* 1.8rem -> 1.5rem으로 변경 */
            margin: 25px 0 10px 0;
            font-weight: 900;
            background: linear-gradient(135deg, #38bdf8 0%, #0284c7 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            text-shadow: 0 4px 10px rgba(56, 189, 248, 0.15);
            letter-spacing: -0.06em; /* 글자 간격을 조금 더 촘촘하게 변경 */
            text-align: center;
            white-space: nowrap; /* 무조건 한 줄로 나오도록 강제 */
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
                font-size: 1.8rem; /* PC 화면에서는 웅장하게 키워줌 */
            }
        }

        /* 모바일 터치 피드백 (손맛 강조) */
        .card:active {
            transform: scale(0.96);
            border-color: #38bdf8;
            box-shadow: 0 0 20px rgba(56, 189, 248, 0.35);
        }

        /* VS 뱃지 디자인 크기 및 폰트 세련화 */
        .vs {
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 0.85rem;
            font-weight: 900;
            color: #ffffff;
            background: linear-gradient(135deg, #ef4444, #dc2626);
            width: 36px;
            height: 36px;
            border-radius: 50%;
            margin: -5px auto;
            z-index: 10;
            box-shadow: 0 0 15px rgba(239, 68, 68, 0.5);
            font-style: normal;
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

    <h1>⚽ FC사나이 유니폼 월드컵 ⚽</h1>
    <div id="round-title">16강 - 1 / 8</div>

    <div class="container" id="game-container">
        <div class="card" onclick="selectCandidate(0)">
            <div class="image-wrapper">
                <img id="img-left" src="" alt="유니폼 위쪽">
            </div>
            <div class="name" id="name-left">유니폼 A</div>
        </div>
        
        <div class="vs">VS</div>
        
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
    </script>
</body>
</html>initGame;
    </script>
</body>
</html>
