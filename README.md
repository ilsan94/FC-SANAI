HTML
<div align="center">
    <h1>:soccer: FC사나이 유니폼 월드컵 :soccer:</h1>
    <div id="round-title" style="font-size: 1.1rem; font-weight: bold; margin-bottom: 25px; color: #38bdf8; letter-spacing: 0.05em;">16강 - 1 / 8</div>
</div>

<div id="game-container" style="display: flex; flex-direction: column; align-items: center; width: 100%; max-width: 420px; margin: 0 auto; gap: 15px;">
    <div id="card-left" style="width: 100%; background: #1e293b; border-radius: 24px; overflow: hidden; cursor: pointer; border: 1px solid rgba(255, 255, 255, 0.05); box-shadow: 0 8px 25px rgba(0, 0, 0, 0.3); display: flex; flex-direction: column; align-items: center;" onclick="selectCandidate(0)">
        <div style="width: 100%; height: 270px; background: #0f172a; display: flex; align-items: center; justify-content: center; overflow: hidden;">
            <img id="img-left" src="" style="width: 90%; height: 90%; object-fit: contain;">
        </div>
        <div id="name-left" style="padding: 16px 15px; font-size: 1.05rem; font-weight: 700; text-align: center; width: 100%; box-sizing: border-box; background: #1e293b; color: #e2e8f0; border-top: 1px solid rgba(255, 255, 255, 0.03);">유니폼 A</div>
    </div>
    
    <div style="display: flex; align-items: center; justify-content: center; width: 100%; margin: 10px 0; font-size: 1.4rem; font-weight: 900; color: #ef4444; font-style: italic; letter-spacing: 0.05em;">
        ─── VS ───
    </div>
    
    <div id="card-right" style="width: 100%; background: #1e293b; border-radius: 24px; overflow: hidden; cursor: pointer; border: 1px solid rgba(255, 255, 255, 0.05); box-shadow: 0 8px 25px rgba(0, 0, 0, 0.3); display: flex; flex-direction: column; align-items: center;" onclick="selectCandidate(1)">
        <div style="width: 100%; height: 270px; background: #0f172a; display: flex; align-items: center; justify-content: center; overflow: hidden;">
            <img id="img-right" src="" style="width: 90%; height: 90%; object-fit: contain;">
        </div>
        <div id="name-right" style="padding: 16px 15px; font-size: 1.05rem; font-weight: 700; text-align: center; width: 100%; box-sizing: border-box; background: #1e293b; color: #e2e8f0; border-top: 1px solid rgba(255, 255, 255, 0.03);">유니폼 B</div>
    </div>
</div>

<div id="winner-container" style="display: none; flex-direction: column; align-items: center; width: 100%; max-width: 420px; margin: 0 auto;">
    <h2 style="color: #f59e0b; font-size: 1.5rem; margin-bottom: 20px; text-align: center; font-weight: 800;">🏆 MY PICK 🏆</h2>
    <div style="width: 100%; background: #1e293b; border-radius: 24px; overflow: hidden; border: 2px solid #f59e0b; box-shadow: 0 0 35px rgba(245, 158, 11, 0.3); display: flex; flex-direction: column; align-items: center;">
        <div style="width: 100%; height: 270px; background: #0f172a; display: flex; align-items: center; justify-content: center; overflow: hidden;">
            <img id="img-winner" src="" style="width: 90%; height: 90%; object-fit: contain;">
        </div>
        <div id="name-winner" style="padding: 16px 15px; font-size: 1.05rem; font-weight: 700; text-align: center; width: 100%; box-sizing: border-box; background: #1e293b; color: #e2e8f0; border-top: 1px solid rgba(255, 255, 255, 0.03);">우승 유니폼</div>
    </div>
    <button onclick="restartGame()" style="margin-top: 30px; padding: 16px; font-size: 1.1rem; font-weight: 700; background: linear-gradient(135deg, #38bdf8 0%, #0284c7 100%); color: #ffffff; border: none; border-radius: 16px; cursor: pointer; width: 100%; box-shadow: 0 4px 15px rgba(2, 132, 199, 0.25);">다시 하기</button>
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

    // 깃허브 마크다운 환경 고려 스크립트 실행
    setTimeout(initGame, 100);
</script>
