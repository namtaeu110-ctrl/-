# <!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>빼빼로 데이 이벤트</title>
    <style>
        /* 기본 화면 스타일 */
        body {
            font-family: 'Arial', sans-serif;
            background-color: #fff5f5;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            overflow: hidden;
        }
        .container {
            text-align: center;
            background: white;
            padding: 40px;
            border-radius: 20px;
            box-shadow: 0 10px 20px rgba(0,0,0,0.1);
            transition: opacity 0.3s;
        }
        h1 {
            color: #4a2c2a;
            font-size: 24px;
            margin-bottom: 30px;
        }
        .btn-group {
            display: flex;
            justify-content: center;
            gap: 20px;
        }
        button {
            padding: 12px 30px;
            font-size: 18px;
            border: none;
            border-radius: 10px;
            cursor: pointer;
            transition: transform 0.2s;
        }
        .btn-yes { background-color: #e74c3c; color: white; }
        .btn-no { background-color: #7f8c8d; color: white; }
        button:hover { transform: scale(1.05); }

        /* 👻 귀신 점프스퀘어 화면 스타일 (평소에는 숨겨짐) */
        #jumpscare-layer {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100vw;
            height: 100vh;
            background-color: black;
            z-index: 9999;
            justify-content: center;
            align-items: center;
        }
        #jumpscare-layer img {
            width: 100%;
            height: 100%;
            object-fit: contain; /* 이미지 비율 유지하며 꽉 차게 */
        }
    </style>
</head>
<body>

    <!-- 질문 화면 -->
    <div class="container" id="main-content">
        <h1>🍫 나랑 빼빼로 먹을래?</h1>
        <div class="btn-group">
            <button class="btn-yes" onclick="triggerScare()">응!</button>
            <button class="btn-no" onclick="triggerScare()">아니</button>
        </div>
    </div>

    <!-- 👻 숨겨진 귀신 레이어 -->
    <div id="jumpscare-layer">
        <!-- 예시 귀신 이미지 주소 (원하는 이미지 URL로 교체 가능) -->
        <img src="https://unsplash.com" alt="Ghost">
    </div>

    <!-- 🔊 오디오 태그 (원하는 비명소리 MP3 URL로 교체 가능) -->
    <audio id="scream-audio" src="https://google.com" preload="auto"></audio>

    <script>
        function triggerScare() {
            const mainContent = document.getElementById('main-content');
            const scareLayer = document.getElementById('jumpscare-layer');
            const audio = document.getElementById('scream-audio');

            // 1. 기존 메인 화면 숨기기
            mainContent.style.display = 'none';

            // 2. 귀신 화면 띄우기
            scareLayer.style.display = 'flex';

            // 3. 비명 소리 재생 (볼륨 최대)
            audio.volume = 1.0;
            audio.play().catch(function(error) {
                console.log("오디오 재생 실패:", error);
            });
        }
    </script>

</body>
</html>
