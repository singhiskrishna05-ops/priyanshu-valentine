<DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Will You Be My Valentine?</title>

<link href="https://fonts.googleapis.com/css2?family=Pacifico&family=Poppins:wght@400;600;700&display=swap" rel="stylesheet">

<style>
body {
  margin:0;
  padding:0;
  text-align:center;
  font-family:'Poppins', sans-serif;
  background: linear-gradient(135deg, #ff9ec4, #ff4f8b);
  overflow:hidden;
  color:white;
}

h1 {
  font-size:42px;
  margin-top:60px;
  font-weight:700;
}

p {
  font-size:22px;
  padding:0 20px;
}

button {
  padding:14px 30px;
  margin:15px;
  font-size:22px;
  border:none;
  border-radius:30px;
  cursor:pointer;
  transition:0.3s;
}

#yesBtn {
  background:white;
  color:#ff2e75;
  font-weight:600;
}

#noBtn {
  background:#ff2e75;
  color:white;
}

button:hover {
  transform:scale(1.1);
}

#sleepMeterContainer {
  width:70%;
  background:white;
  border-radius:20px;
  margin:25px auto;
  height:20px;
}

#sleepMeter {
  height:100%;
  width:80%;
  background:#ff2e75;
  border-radius:20px;
  animation:sleep 3s infinite alternate;
}

@keyframes sleep {
  from { width:40%; }
  to { width:90%; }
}

.heart {
  position:absolute;
  font-size:22px;
  animation: float 6s linear infinite;
  opacity:0.8;
}

@keyframes float {
  0% { transform:translateY(100vh); }
  100% { transform:translateY(-10vh); }
}

#musicBtn {
  position:fixed;
  bottom:20px;
  right:20px;
  background:white;
  color:#ff2e75;
  font-size:18px;
  padding:10px 20px;
  border-radius:20px;
}

canvas {
  position:fixed;
  top:0;
  left:0;
  pointer-events:none;
}
</style>
</head>

<body>

<h1>Priyanshuuuuu 💘</h1>

<p>
You sleepy little human 🥺😴<br>
We’ve been dating for 11 months now…<br><br>
From our first time at Pirates of Grill<br>
to all those Burger King dates 🍔❤️<br><br>
You saying “hmko neend nahi aa rha h”<br>
and then sleeping mid-convo anyway 🤦🏻‍♀️<br><br>
You never deciding what to eat… ever 😂<br><br>
But still… you are my favourite person.
</p>

<div id="sleepMeterContainer">
  <div id="sleepMeter"></div>
</div>

<p>So Mr. Sleepyhead…</p>

<h1 style="font-family:'Pacifico', cursive;">Will you be my Valentine? 💖</h1>

<button id="yesBtn" onclick="sayYes()">YES 💕</button>
<button id="noBtn" onclick="sayNo()">No 🙄</button>

<button id="musicBtn" onclick="playMusic()">🎵 Play Tum Ho Toh</button>

<audio id="bgMusic" src="https://pagalnew.com/download/128-Tum Ho Toh - Saiyaara 128 Kbps.mp3"></audio>

<canvas id="confetti"></canvas>

<script>
let noClicks = 0;

function sayYes() {
  startConfetti();
  document.body.innerHTML += `
  <h1 style="margin-top:80px; font-size:46px;">YAYYYYYY 💘</h1>
  <p style="font-size:26px;">
  11 months with you…<br><br>
  From Pirates of Grill to Burger King dates 🍔❤️<br>
  From "hmko neend nahi aa rha h"<br>
  to you sleeping in between conversations 😂<br><br>
  I’d choose you every single time.<br><br>
  Happy Valentine’s Day, my sleepy baby 😴💕
  </p>
  `;
}

function sayNo() {
  noClicks++;
  if(noClicks === 1) alert("Are you sure? 🤨");
  else if(noClicks === 2) alert("Think properly, Mr. Can’t-Decide-What-To-Eat 😒");
  else if(noClicks === 3) alert("Don’t act smart 😑");
  else alert("Bas karo ab 😤 Click YES.");
}

function playMusic(){
  document.getElementById("bgMusic").play();
}

function createHeart(){
  const heart = document.createElement("div");
  heart.classList.add("heart");
  heart.innerHTML="💖";
  heart.style.left = Math.random()*100 + "vw";
  heart.style.animationDuration = (3 + Math.random()*3) + "s";
  document.body.appendChild(heart);
  setTimeout(()=>{ heart.remove(); },6000);
}
setInterval(createHeart, 500);

/* CONFETTI */
const canvas = document.getElementById("confetti");
const ctx = canvas.getContext("2d");
canvas.width = window.innerWidth;
canvas.height = window.innerHeight;

let pieces = [];

function startConfetti(){
  for(let i=0;i<150;i++){
    pieces.push({
      x: Math.random()*canvas.width,
      y: Math.random()*canvas.height - canvas.height,
      r: Math.random()*6+4,
      d: Math.random()*150
    });
  }
  animateConfetti();
}

function animateConfetti(){
  ctx.clearRect(0,0,canvas.width,canvas.height);
  ctx.fillStyle="white";
  pieces.forEach(p=>{
    ctx.beginPath();
    ctx.arc(p.x,p.y,p.r,0,Math.PI*2,true);
    ctx.fill();
  });

  updateConfetti();
  requestAnimationFrame(animateConfetti);
}

function updateConfetti(){
  pieces.forEach(p=>{
    p.y += 2;
    if(p.y > canvas.height){
      p.y = -10;
    }
  });
}
</script>

</body>
</html>
