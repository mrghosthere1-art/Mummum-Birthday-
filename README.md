# Mummum-Birthday-
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>For My Mummum ❤️</title>

<style>
body {
  margin: 0;
  font-family: 'Poppins', sans-serif;
  background: linear-gradient(135deg, #000, #1a0000, #000);
  color: #fff;
  text-align: center;
  overflow-x: hidden;
}

/* Glow Text */
h1, h2 {
  text-shadow: 0 0 10px red, 0 0 25px pink;
}

/* Letter */
#letter {
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}

button {
  padding: 12px 25px;
  border: none;
  border-radius: 30px;
  background: linear-gradient(45deg, red, pink);
  color: white;
  font-size: 18px;
  cursor: pointer;
  box-shadow: 0 0 15px red;
}

/* Sections */
.section { display: none; padding: 40px; }
.active { display: block; animation: fade 1s; }

@keyframes fade {
  from {opacity: 0;}
  to {opacity: 1;}
}

/* Name */
.name-animation {
  font-size: 30px;
  color: #ff4d6d;
  text-shadow: 0 0 10px pink, 0 0 30px red;
}

/* Love text */
.love-text {
  font-size: 20px;
  margin-top: 10px;
  color: #ffd6e0;
}

/* Gallery */
.gallery img {
  width: 220px;
  margin: 10px;
  border-radius: 15px;
  box-shadow: 0 0 20px red;
}

/* Ending */
#end img {
  width: 280px;
  border-radius: 20px;
  box-shadow: 0 0 30px red;
}

/* Hearts */
.heart {
  position: fixed;
  color: red;
  animation: float 6s linear infinite;
}

@keyframes float {
  from { transform: translateY(100vh); }
  to { transform: translateY(-10vh); opacity: 0; }
}

/* Fireworks */
.firework {
  position: fixed;
  width: 5px;
  height: 5px;
  background: pink;
  border-radius: 50%;
  animation: explode 1s ease-out infinite;
}

@keyframes explode {
  from { transform: scale(1); opacity: 1; }
  to { transform: scale(20); opacity: 0; }
}
</style>
</head>

<body>

<audio id="bgMusic" loop>
  <source src="song.mp3" type="audio/mpeg">
</audio>

<!-- LETTER -->
<div id="letter">
  <h1>💌 For My Mummum</h1>
  <p>Tap to open ❤️</p>
  <button onclick="openLetter()">Open</button>
</div>

<!-- INTRO -->
<div id="intro" class="section">
  <h1>Happy Birthday ❤️</h1>

  <h2 class="name-animation">
    <span id="typedName"></span>
  </h2>

  <p id="loveMessage" class="love-text"></p>

  <button onclick="nextSection('paragraph')">Read This 💌</button>
</div>

<!-- LONG PARAGRAPH -->
<div id="paragraph" class="section">
  <h1>For You 💖</h1>

  <p style="max-width:600px;margin:auto;line-height:1.8;">
    From the moment you came into my life, everything started to feel different… 
    softer, warmer, more meaningful. You are not just someone I love, you are the 
    reason behind my smiles, my peace, and my happiness. Even on my worst days, 
    just thinking about you makes everything feel okay again.

    I don’t know how you do it, but you make my heart feel safe in a way I never 
    knew was possible. Your voice, your presence, your little things… everything 
    about you feels like home to me. And maybe I don’t say it perfectly every time, 
    but I truly, deeply love you more than words can ever explain.

    I don’t just want moments with you, I want a lifetime. More memories, more 
    laughter, more love… just us, together. No matter what happens in life, I promise 
    I’ll always stand beside you, support you, and love you with everything I have.

    Happy Birthday, my Mummum… you are my heart, my happiness, and my forever ❤️
  </p>

  <button onclick="nextSection('memories')">Our Moments 📸</button>
</div>

<!-- MEMORIES -->
<div id="memories" class="section">
  <h1>Our Memories 💕</h1>

  <div class="gallery">
    <img src="IMG_20260430_150104_659.jpg">
    <img src="Snapchat-878636611.jpg">
    <img src="IMG_20260430_171925_372.jpg">
  </div>

  <button onclick="nextSection('end')">Final ❤️</button>
</div>

<!-- END -->
<div id="end" class="section">
  <h1>Forever Yours ❤️</h1>
  <img src="final.jpg">
  <h2>Happy Birthday Mummum 🎂💖</h2>
</div>

<script>
const firstName = "Radhika 💖";
const nickName = "Mummum 😭🤍";
const loveLine = "I love you Mummum ❤️";

let i = 0, j = 0;

function typeFirstName() {
  if (i < firstName.length) {
    typedName.innerHTML += firstName.charAt(i);
    i++;
    setTimeout(typeFirstName, 100);
  } else {
    setTimeout(changeToNickname, 1200);
  }
}

function changeToNickname() {
  typedName.style.opacity = 0;
  setTimeout(() => {
    typedName.innerHTML = nickName;
    typedName.style.opacity = 1;
    setTimeout(typeLoveMessage, 800);
  }, 500);
}

function typeLoveMessage() {
  if (j < loveLine.length) {
    loveMessage.innerHTML += loveLine.charAt(j);
    j++;
    setTimeout(typeLoveMessage, 80);
  }
}

function openLetter() {
  letter.style.display = "none";
  intro.classList.add("active");
  typeFirstName();
  bgMusic.play();
}

function nextSection(id) {
  document.querySelectorAll(".section").forEach(s => s.classList.remove("active"));
  document.getElementById(id).classList.add("active");

  // Fireworks on final
  if (id === "end") {
    setInterval(() => {
      let f = document.createElement("div");
      f.className = "firework";
      f.style.left = Math.random() * 100 + "vw";
      f.style.top = Math.random() * 100 + "vh";
      document.body.appendChild(f);
      setTimeout(() => f.remove(), 1000);
    }, 200);
  }
}

// Floating hearts
setInterval(() => {
  let heart = document.createElement("div");
  heart.className = "heart";
  heart.innerHTML = "❤️";
  heart.style.left = Math.random() * 100 + "vw";
  document.body.appendChild(heart);
  setTimeout(() => heart.remove(), 6000);
}, 500);
</script>

</body>
</html>
