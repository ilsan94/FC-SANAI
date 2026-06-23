<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>풋살 유니폼 월드컵</title>
    <style>
        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
            background-color: #0f172a;
            color: #ffffff;
            margin: 0;
            padding: 0;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: flex-start;
            min-height: 100vh;
            padding-bottom: 40px;
            box-sizing: border-box;
        }
        h1 {
            font-size: 1.8rem;
            margin: 20px 0 5px 0;
            color: #38bdf8;
            text-align: center;
            font-weight: 800;
        }
        #round-title {
            font-size: 1.1rem;
            font-weight: bold;
            margin-bottom: 15px;
            background: #1e293b;
            padding: 8px 20px;
            border-radius: 20px;
            border: 1px solid #38bdf8;
            box-shadow: 0 4px 6px rgba(0,0,0,0.2);
        }
        .container {
            display: flex;
            flex-direction: column;
            width: 100%;
            max-width: 450px;
            gap: 12px;
            padding: 0 15px;
            box-sizing: border-box;
        }
        .card {
            width: 100%;
            background: #1e293b;
            border-radius: 16px;
            overflow: hidden;
            cursor: pointer;
            transition: transform 0.15s ease, border-color 0.15s ease;
            border: 3px solid transparent;
            box-shadow: 0 6px 12px rgba(0,0,0,0.4);
            display: flex;
            flex-direction: column;
            align-items: center;
            -webkit-tap-highlight-color: transparent;
        }
        .card:active {
            transform: scale(0.97);
            border-color: #38bdf8;
        }
        .vs {
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.2rem;
            font-weight: 900;
            color: #ef4444;
            font-style: italic;
            margin: 2px 0;
            text-shadow: 0 0 8px rgba(239, 68, 68, 0.4);
        }
        .image-wrapper {
            width: 100%;
            height: 260px;
            background: #151f32;
            display: flex;
            align-items: center;
            justify-content: center;
            overflow: hidden;
        }
        .image-wrapper img {
            width: 100%;
            height: 100%;
            object-fit: contain;
        }
        .name {
            padding: 14px 10px;
            font-size: 1.1rem;
            font-weight: bold;
            text-align: center;
            width: 100%;
            box-sizing: border-box;
            background: #0f172a;
            border-top: 1px solid #1e293b;
        }
        #winner-container {
            display: none;
            flex-direction: column;
            align-items: center;
            width: 100%;
            max-width: 450px;
            padding: 0 15px;
            box-sizing: border-box;
        }
        .winner-card {
            width: 100%;
            border: 4px solid #f59e0b;
            box-shadow: 0 0 25px rgba(245, 158, 11, 0.5);
            pointer-events: none;
        }
        .restart-btn {
            margin-top: 25px;
            padding: 15px 40px;
            font-size: 1.2rem;
            font-weight: bold;
            background-color: #38bdf8;
            color: #0f172a;
            border: none;
            border-radius: 12px;
            cursor: pointer;
            width: 100%;
            box-shadow: 0 4px 6px rgba(0,0,0,0.2);
        }
    </style>
</head>
<body>

    <h1>⚽ 풋살 유니폼 월드컵 ⚽</h1>
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
        <h2 style="color: #f59e0b; font-size: 1.6rem; margin-bottom: 15px; text-align: center;">🏆 우리 팀 최종 유니폼 결정! 🏆</h2>
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
            { src: "https://i.postimg.cc/18sbzZ94/image-2.png", name: "발렌시아 오렌지" },
            { src: "https://i.postimg.cc/SnkHKpyY/image-3.png", name: "심플 블랙 카라" },
            { src: "https://i.postimg.cc/3kYzwHKd/image-4.png", name: "블랙 형광" },
            { src: "https://i.postimg.cc/CRS9KVF5/image-5.png", name: "체커보드 패턴" },
            { src: "https://i.postimg.cc/21rg5fzW/image-6.png", name: "블랙 레드 스트라이프" },
            { src: "https://i.postimg.cc/cv0PJNsY/image-7.png", name: "대한민국 국대 느낌" },
            { src: "https://i.postimg.cc/TKfBPXRg/image-8.png", name: "올블랙" },
            { src: "https://i.postimg.cc/21rg5fz4/image-9.png", name: "딥 블루" },
            { src: "https://i.postimg.cc/68tFQN9r/image-10.png", name: "네이비 마블링" },
            { src: "https://i.postimg.cc/9DCsfjWt/image-11.jpg", name: "유벤투스 스타일" },
            { src: "https://i.postimg.cc/gxm10PYy/image-12.jpg", name: "AS로마 스타일" },
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
</html>
