<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Special Romantic Surprise</title>
<style>
  body {
    background-color: #111;
    color: #fff;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    text-align: center;
    padding: 40px 20px;
  }
  .hearts {
    position: fixed;
    top: 0; left: 0;
    width: 100vw; height: 100vh;
    pointer-events: none;
    overflow: hidden;
    z-index: -1;
  }
  .heart {
    position: absolute;
    font-size: 20px;
    color: #ff4d6d;
    animation: floatUp linear infinite;
    user-select: none;
  }
  @keyframes floatUp {
    0% { transform: translateY(100vh) scale(1); opacity: 1; }
    100% { transform: translateY(-10vh) scale(0.5); opacity: 0; }
  }
  button {
    background-color: #ff4d6d;
    border: none;
    color: white;
    padding: 10px 18px;
    margin: 8px;
    font-size: 16px;
    border-radius: 6px;
    cursor: pointer;
    transition: background-color 0.3s ease;
  }
  button:hover {
    background-color: #e03e5b;
  }
  #imageContainer {
    margin-top: 20px;
  }
  #imageContainer img {
    width: 200px;
    border-radius: 12px;
    box-shadow: 0 0 15px #ff4d6d;
  }
  #countdown {
    font-size: 20px;
    margin-top: 10px;
  }
  .hidden { display: none; }
  #finalEffect {
    white-space: pre-line;
    font-size: 24px;
    margin-top: 30px;
    color: #ff9aad;
    animation: glow 2s ease-in-out infinite alternate;
  }
  @keyframes glow {
    0% { text-shadow: 0 0 5px #ff4d6d, 0 0 10px #ff4d6d; }
    100% { text-shadow: 0 0 15px #ff4d6d, 0 0 30px #ff4d6d; }
  }
</style>
</head>
<body>

<div class="hearts" id="hearts"></div>

<div id="step1">
  <h2>What is your name?</h2>
  <input type="text" id="nameInput" placeholder="Type your name here" />
  <br />
  <button onclick="checkName()">Submit</button>
</div>

<div id="step2" class="hidden">
  <h3>I have something for you. Show it or leave it?</h3>
  <button onclick="chooseShow(true)">Show it</button>
  <button onclick="chooseShow(false)">Leave it</button>
</div>

<div id="step3" class="hidden">
  <h3>From today, I am yours, Shona.</h3>
  <div id="imageContainer">
    <!-- Online image of romantic couple -->
    <img src="https://i.ibb.co/4V5kCcn/romantic-couple.png" alt="Romantic Couple" />
  </div>
  <div id="countdown"></div>
</div>

<div id="step4" class="hidden">
  <h3>Do you want to know more?</h3>
  <button onclick="knowMore(true)">Yes</button>
  <button onclick="knowMore(false)">No</button>
</div>

<div id="step5" class="hidden">
  <h3>How much do you love me, Bishmu?</h3>
  <button onclick="loveAmount('Countable')">Countable</button>
  <button onclick="loveAmount('Uncountable')">Uncountable</button>
</div>

<div id="step6" class="hidden">
  <h2 id="finalEffect">If the whole world goes against you,<br />I will be with you, my Shona.</h2>
</div>

<script>
// Hearts animation function
function launchHearts() {
  const heartsContainer = document.getElementById('hearts');
  for(let i=0; i<50; i++){
    const heart = document.createElement('div');
    heart.className = 'heart';
    heart.textContent = '♥';
    heart.style.left = Math.random() * 100 + 'vw';
    heart.style.animationDuration = (Math.random() * 3 + 3) + 's';
    heart.style.fontSize = (Math.random() * 20 + 10) + 'px';
    heartsContainer.appendChild(heart);
  }
}

// Name check and start flow
function checkName() {
  const name = document.getElementById('nameInput').value.trim().toLowerCase();
  if(name === 'bisma'){
    document.getElementById('step1').classList.add('hidden');
    document.getElementById('step2').classList.remove('hidden');
    launchHearts();
  } else {
    alert('Only for Bisma!');
  }
}

function chooseShow(show) {
  document.getElementById('step2').classList.add('hidden');
  if(show){
    document.getElementById('step3').classList.remove('hidden');
    startCountdown();
  } else {
    document.getElementById('step4').classList.remove('hidden');
  }
}

function startCountdown() {
  let seconds = 5;
  const countdownEl = document.getElementById('countdown');
  const interval = setInterval(() => {
    countdownEl.textContent = `Wait for it... ${seconds}s`;
    seconds--;
    if(seconds < 0){
      clearInterval(interval);
      countdownEl.textContent = '';
    }
  }, 1000);
}

function knowMore(answer) {
  document.getElementById('step4').classList.add('hidden');
  if(answer){
    document.getElementById('step5').classList.remove('hidden');
  } else {
    alert('Okay, maybe next time!');
  }
}

function loveAmount(type) {
  document.getElementById('step5').classList.add('hidden');
  const finalText = document.getElementById('finalEffect');
  finalText.textContent = `If the whole world goes against you,\nI will be with you, my Shona.\n\nYour love is ${type}.`;
  document.getElementById('step6').classList.remove('hidden');
  launchHearts();
}
</script>

</body>
</html>
