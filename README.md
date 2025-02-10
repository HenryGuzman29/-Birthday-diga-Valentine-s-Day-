<!DOCTYPE html>
<html>
    <head>
        <title>Page Title</title>
    <style>
    @import url('https://fonts.googleapis.com/css2?family=Zen+Kurenaido&display=swap');
    * {
      margin: 20px 10px 10px 10px;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: Zen Kurenaido;
      background-color: #f3f3f3;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      flex-direction: column;
    }

    #cube-container {
      perspective: 1500px;
      margin-bottom: 20px;
    }

    #cube {
      width: 200px;
      height: 200px;
      position: relative;
      transform-style: preserve-3d;
      animation: rotateCube 12s infinite;
    }

    .face {
      position: absolute;
      width: 200px;
      height: 200px;
      background-color: rgba(255, 255, 255, 0.9);
      display: flex;
      justify-content: center;
      align-items: center;
      font-size: 24px;
      font-weight: bold;
      color: #333;
      border: 2px solid #ccc;
    }

    .front { transform: rotateY(  0deg) translateZ(100px); }
    .back { transform: rotateY(180deg) translateZ(100px); }
    .left { transform: rotateY(-90deg) translateZ(100px); }
    .right { transform: rotateY( 90deg) translateZ(100px); }
    .top { transform: rotateX( 90deg) translateZ(100px); }
    .bottom { transform: rotateX(-90deg) translateZ(100px); }

    @keyframes rotateCube {
      0% { 
          transform: rotateY(0deg); 
      }
      16% { 
          transform: rotateX(90deg);
      }
      33% { 
          transform: rotateY(180deg); 
      }
      50% {
          transform: rotateZ(180deg) rotateY(90deg); 
      }
      66% {
          transform: rotateY(450deg);
      }
    }

    .typing {
      display: inline-block;
      overflow: hidden;
      white-space: nowrap;
      border-right: 2px solid black;
      animation: typing 4s steps(30) 1s forwards, blink 0.75s step-end infinite;
      font-size: 24px;
      margin-top: 160px;
      position: absolute;
      font-family: Zen Kurenaido;
      top: 60px;
      left: 10px;
      white-space: pre-wrap;
      overflow-wrap: break-word;
      max-width: 90vw;
    }

    @keyframes typing {
      from { width: 0; }
      to { width: 100%; }
    }

    @keyframes blink {
      50% { border-color: transparent; }
    }

    .typing::after {
      content: ''; 
      border-right: 2px solid;
      animation: blink-caret 0.75s step-end infinite;
      display: inline-block;
      width: 1px;
      height: 1em; 
      vertical-align: bottom;
    }

    @keyframes blink-caret {
      from, to { 
          border-color: transparent; 
      }
      50% { 
          border-color: black; 
      }
    }

    </style>
    </head>
<body>
  <div id="cube-container">
    <div id="cube">
      <div class="face front">"Valentine's Day":<br>🎉🎊✨🧨❤</div>
      <div class="face back">Kirrianna<br>💘❤💞💕💌💟</div>
      <div class="face left"><img src="kirianna.png" height="150" width="150"></div>
      <div class="face right"></div>
      <div class="face top"></div>
      <div class="face bottom">"Valentine's Day":<br>Baby😍</div>
    </div>
  </div>
  <div id="wishes"></div>
  <div id="typing-text"></div>
  <img id="mars-img" src="path-to-image.jpg" style="display:none;" />
  
  <script>
    const cube = document.getElementById('cube');
    const wishesContainer = document.getElementById('wishes');
    const typingText = document.getElementById('typing-text');

    
    

    function startCubeAnimation() {
      setTimeout(() => {
        cube.style.animation = 'rotateCube 12s infinite';
      }, 500);
    }





    const messages = [
      "Que tengas un día maravilloso. Que sea un tiempo lleno de sonrisas y risas. Y que siempre seas feliz. 💖"
    ];

    let messageIndex = 0;
    let charIndex = 0;
    let isDeleting = false;
    const typingSpeed = 150;
    const deletingSpeed = 100; 
    const delayBetweenMessages = 1500; 

    function type() {
      const currentMessage = messages[messageIndex];

      if (isDeleting) {
        typingText.innerHTML = currentMessage.substring(0, charIndex--);
        if (charIndex < 0) {
          isDeleting = false;
          messageIndex = (messageIndex + 1) % messages.length;
          setTimeout(type, delayBetweenMessages);
        } else {
          setTimeout(type, deletingSpeed);
        }
      } else {
        typingText.innerHTML = currentMessage.substring(0, charIndex++);
        if (charIndex > currentMessage.length) {
          isDeleting = true;
          setTimeout(type, delayBetweenMessages);
        } else {
          setTimeout(type, typingSpeed);
        }
      }
    }
    
    

    setTimeout(type, 2000);
    startCubeAnimation();
  </script>
</body>
</html>
