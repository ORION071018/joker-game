<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>抖音尬笑 · 朱梓健你个乐乐</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      background: #0b0b0e;
      min-height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
      font-family: system-ui, -apple-system, 'Segoe UI', Roboto, 'Helvetica Neue', sans-serif;
      padding: 16px;
    }

    .card {
      max-width: 620px;
      width: 100%;
      background: #1c1c22;
      border-radius: 42px;
      padding: 36px 32px 42px 32px;
      box-shadow: 0 20px 35px rgba(0, 0, 0, 0.7), 0 0 0 1px rgba(255, 255, 255, 0.03) inset;
      display: flex;
      flex-direction: column;
      align-items: center;
      transition: transform 0.2s ease;
    }

    .emoji-stage {
      position: relative;
      width: 180px;
      height: 180px;
      margin-bottom: 28px;
      display: flex;
      align-items: center;
      justify-content: center;
      animation: stageWobble 2.2s infinite ease-in-out;
    }

    .giant-emoji {
      font-size: 148px;
      line-height: 1;
      text-shadow: 0 0 18px rgba(250, 200, 80, 0.45), 0 8px 20px rgba(0, 0, 0, 0.6);
      filter: drop-shadow(0 0 8px #f7d44a55);
      transform: scale(1.1);
      animation: breath 1.9s infinite alternate;
      user-select: none;
    }

    .emoji-stage::after {
      content: '';
      position: absolute;
      inset: -8px;
      border-radius: 50%;
      background: radial-gradient(circle at 30% 30%, rgba(247, 212, 74, 0.2) 0%, transparent 70%);
      z-index: 0;
      animation: pulse 2.4s infinite alternate;
      pointer-events: none;
    }

    .emoji-stage::before {
      content: '抖音 · 尬笑';
      position: absolute;
      bottom: -20px;
      left: 50%;
      transform: translateX(-50%);
      font-size: 14px;
      font-weight: 600;
      letter-spacing: 2px;
      color: #ffffff70;
      background: #00000050;
      padding: 4px 14px;
      border-radius: 30px;
      backdrop-filter: blur(2px);
      white-space: nowrap;
      z-index: 5;
      border: 1px solid #ffffff12;
    }

    .message-box {
      background: #26262e;
      border-radius: 32px;
      padding: 28px 30px;
      width: 100%;
      box-shadow: 0 8px 0 #0e0e12, 0 14px 25px -8px black;
      border: 1px solid #3d3d4a;
      transition: all 0.15s;
    }

    .message-text {
      font-size: 1.4rem;
      line-height: 1.5;
      font-weight: 500;
      color: #f2f2f7;
      word-break: break-word;
      text-align: center;
      letter-spacing: 0.2px;
      text-shadow: 0 2px 5px black;
      max-height: 300px;
      overflow-y: auto;
      padding-right: 6px;
      scrollbar-width: thin;
      scrollbar-color: #f7d44a #2e2e3a;
    }

    .message-text::-webkit-scrollbar {
      width: 6px;
    }

    .message-text::-webkit-scrollbar-track {
      background: #2e2e3a;
      border-radius: 12px;
    }

    .message-text::-webkit-scrollbar-thumb {
      background: #f7d44a;
      border-radius: 12px;
    }

    @media (max-width: 480px) {
      .card {
        padding: 26px 20px 32px;
        border-radius: 32px;
      }
      .giant-emoji {
        font-size: 118px;
      }
      .emoji-stage {
        width: 150px;
        height: 150px;
      }
      .message-text {
        font-size: 1.2rem;
        padding: 0 4px;
      }
      .message-box {
        padding: 22px 18px;
      }
    }

    @keyframes breath {
      0% {
        transform: scale(1.06) rotate(-1deg);
      }
      100% {
        transform: scale(1.16) rotate(1deg);
      }
    }

    @keyframes stageWobble {
      0%,
      100% {
        transform: rotate(0deg) translateY(0);
      }
      25% {
        transform: rotate(1.2deg) translateY(-3px);
      }
      75% {
        transform: rotate(-1.2deg) translateY(3px);
      }
    }

    @keyframes pulse {
      0% {
        opacity: 0.3;
        transform: scale(0.95);
      }
      100% {
        opacity: 0.7;
        transform: scale(1.25);
      }
    }
  </style>
</head>
<body>
  <div class="card">
    <div class="emoji-stage">
      <div class="giant-emoji" aria-label="抖音尬笑表情">😅</div>
    </div>

    <div class="message-box">
      <div class="message-text" id="dynamicText">
        朱梓健你个乐乐，你还真点进来啊
      </div>
    </div>
  </div>

  <script>
    (function() {
      const textElement = document.getElementById('dynamicText');

      // 你发给我的文字
      const incomingText = '朱梓健你个乐乐，你还真点进来啊';

      // 写入文字
      if (textElement) {
        textElement.innerText = incomingText;
      }

      // 点击文字可复制
      textElement.addEventListener('click', function() {
        navigator.clipboard?.writeText(incomingText).then(() => {
          const originalText = textElement.innerText;
          textElement.innerText = '😅 文案已复制！';
          setTimeout(() => {
            textElement.innerText = originalText;
          }, 800);
        }).catch(() => {});
      });

      // 方便从控制台修改文字
      window.setGagText = function(newText) {
        if (typeof newText === 'string') {
          textElement.innerText = newText;
        }
      };
    })();
  </script>
</body>
</html>
