<!DOCTYPE html>
<html lang="ja">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>ストームの銀の盾カウントダウン</title>
  <style>
    body {
      margin: 0;
      font-family: "Noto Sans JP", sans-serif;
      background: #6ec7ff;
      color: white;
      text-align: center;
      image-rendering: pixelated;
      background-image: url("background_pixel_grass.png");
      background-size: cover;
    }
    h1 {
      font-size: 2rem;
      margin-top: 1em;
    }
    h2 {
      font-size: 1.5rem;
    }
    #shield {
      margin: 2em auto;
      width: 128px;
      height: 128px;
      background-size: contain;
      background-repeat: no-repeat;
      background-position: center;
    }
    .progress-bar {
      width: 80%;
      background: #333;
      margin: 1em auto;
      height: 20px;
      border: 2px solid #222;
      border-radius: 4px;
      overflow: hidden;
    }
    .progress {
      background: linear-gradient(to right, gold, orange);
      height: 100%;
      width: 0%;
      transition: width 0.5s;
    }
    .percent {
      font-size: 1.2rem;
      margin-top: 0.5em;
    }
  </style>
</head>
<body>
  <h1>ストームの<br />銀の盾完成カウントダウン</h1>
  <h2>現在の登録者数</h2>
  <div id="subscriberCount">--</div>
  <div id="shield"></div>
  <div class="progress-bar">
    <div class="progress" id="progressBar"></div>
  </div>
  <div class="percent" id="percentText">--%</div>

  <script>
    const maxSubs = 100000;
    const shieldElement = document.getElementById("shield");
    const progressBar = document.getElementById("progressBar");
    const percentText = document.getElementById("percentText");
    const countText = document.getElementById("subscriberCount");

    // 仮の登録者数（APIの代用）
    let currentSubs = 17890;

    function updateUI() {
      // 登録者数表示
      countText.innerText = currentSubs.toLocaleString();

      // 進行率
      const percent = Math.min(100, (currentSubs / maxSubs) * 100);
      progressBar.style.width = percent + "%";
      percentText.innerText = percent.toFixed(2) + "%";

      // 盾画像段階切り替え（1万ごと）
      const stage = Math.floor(currentSubs / 10000) + 1;
      const totalStages = 10;
      const clampedStage = Math.min(stage, totalStages);
      shieldElement.style.backgroundImage = `url('shield_stage${clampedStage}.png')`;
    }

    updateUI();
  </script>
</body>
</html>
