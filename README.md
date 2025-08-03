# frontend-sl-app
all html,css,js is available here 
html 
<!DOCTYPE html>
<html lang="en" >
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>SolMate - Your Mind & Body Companion</title>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap" rel="stylesheet" />
  <link rel="stylesheet" href="style.css" />
</head>
<body>
  <div id="app">
    <!-- Dynamic Sky Background + Sun & Moon -->
    <div id="sky">
      <div id="sun"></div>
      <div id="moon"></div>
    </div>

    <!-- Floating Consult Therapist Button -->
    <button class="consult-btn" onclick="openConsult()">💬 Consult Therapist</button>

    <!-- Start Screen -->
    <section class="screen active" id="screen-start">
      <h1>🌿 SolMate</h1>
      <p>Your holistic mental & physical wellness companion</p>
      <button onclick="navigateTo('screen-mood')">Start Your Journey</button>
    </section>

    <!-- Mood Check-In -->
    <section class="screen" id="screen-mood">
      <h2>How are you feeling today?</h2>
      <div class="emoji-row">
        <button aria-label="Happy mood" onclick="setMood('happy')">😊</button>
        <button aria-label="Sad mood" onclick="setMood('sad')">😔</button>
        <button aria-label="Angry mood" onclick="setMood('angry')">😠</button>
        <button aria-label="Anxious mood" onclick="setMood('anxious')">😰</button>
        <button aria-label="Neutral mood" onclick="setMood('neutral')">😐</button>
      </div>
      <button onclick="navigateTo('screen-tools')" class="next-btn">Next →</button>
      <button onclick="navigateTo('screen-start')" class="back-btn">← Back</button>
    </section>

    <!-- Main Tools Dashboard -->
    <section class="screen" id="screen-tools">
      <h2>Choose Your Wellness Tool</h2>
      <div class="tools-grid">
        <button onclick="navigateTo('screen-breathe')" aria-label="Breathe tool">🫁 Breathe</button>
        <button onclick="navigateTo('screen-journal')" aria-label="Journal tool">📓 Journal</button>
        <button onclick="navigateTo('screen-gratitude')" aria-label="Gratitude tool">🙏 Gratitude</button>
        <button onclick="navigateTo('screen-chat')" aria-label="AI Chat">💬 AI Chat</button>
        <button onclick="navigateTo('screen-hydration')" aria-label="Hydration tracker">💧 Hydration</button>
        <button onclick="navigateTo('screen-body-scan')" aria-label="Body scan">🧘 Body Scan</button>
        <button onclick="navigateTo('screen-mini-quest')" aria-label="Mini quest challenges">🎯 Mini Quest</button>
        <button onclick="navigateTo('screen-sleep')" aria-label="Sleep tracker">🛌 Sleep Tracker</button>
        <button onclick="navigateTo('screen-step-counter')" aria-label="Step counter">🚶 Step Counter</button>
        <button onclick="navigateTo('screen-creativity')" aria-label="Creativity corner">🎨 Creativity Corner</button>
      </div>
      <button onclick="navigateTo('screen-mood')" class="back-btn">← Back</button>
    </section>

    <!-- Breathe Tool -->
    <section class="screen" id="screen-breathe">
      <h2>Breathe Deeply</h2>
      <div class="circle" id="breathe-circle" aria-label="Breathing animation"></div>
      <p>Follow the circle to inhale and exhale.</p>
      <button onclick="navigateTo('screen-tools')">Back to Tools</button>
    </section>

    <!-- Journal -->
    <section class="screen" id="screen-journal">
      <h2>Journal Your Thoughts</h2>
      <textarea id="journal-textarea" placeholder="Write your thoughts here..."></textarea>
      <button onclick="saveJournal()">Save & Back</button>
    </section>

    <!-- Gratitude -->
    <section class="screen" id="screen-gratitude">
      <h2>Gratitude Practice</h2>
      <p>List 3 things you're grateful for today:</p>
      <input type="text" placeholder="1." id="gratitude-1" />
      <input type="text" placeholder="2." id="gratitude-2" />
      <input type="text" placeholder="3." id="gratitude-3" />
      <button onclick="saveGratitude()">Save & Back</button>
    </section>

    <!-- AI Chat -->
    <section class="screen" id="screen-chat">
      <h2>Chat with SolMate</h2>
      <div id="chat-log" tabindex="0" role="log" aria-live="polite" aria-label="Chat messages"></div>
      <div class="chat-input-area">
        <input id="chat-input" type="text" placeholder="Say something..." aria-label="Message input" />
        <button onclick="sendMessage()">Send</button>
      </div>
      <button onclick="navigateTo('screen-tools')">Back to Tools</button>
    </section>

    <!-- Hydration Tracker -->
    <section class="screen" id="screen-hydration">
      <h2>Hydration Tracker</h2>
      <p>Tap below each time you drink a glass of water.</p>
      <div id="water-counter">0 / 8 Glasses</div>
      <button onclick="addWater()">Add Glass 💧</button>
      <button onclick="resetWater()">Reset</button>
      <button onclick="navigateTo('screen-tools')">Back to Tools</button>
    </section>

    <!-- Body Scan -->
    <section class="screen" id="screen-body-scan">
      <h2>Body Scan Meditation</h2>
      <p>Close your eyes and slowly scan your body from feet to head.</p>
      <button onclick="startBodyScan()">Start 30s Timer</button>
      <button onclick="navigateTo('screen-tools')">Back to Tools</button>
      <div id="body-scan-timer"></div>
    </section>

    <!-- Mini Quest -->
    <section class="screen" id="screen-mini-quest">
      <h2>Today's Mini Quest</h2>
      <p>Step outside, take 3 slow breaths, and notice how you feel.</p>
      <button onclick="completeQuest()">Mark as Completed</button>
      <button onclick="navigateTo('screen-tools')">Back to Tools</button>
    </section>

    <!-- Sleep Tracker -->
    <section class="screen" id="screen-sleep">
      <h2>Sleep Tracker</h2>
      <p>Log how many hours you slept last night:</p>
      <input type="number" min="0" max="12" id="sleep-hours" placeholder="Hours" />
      <button onclick="saveSleep()">Save</button>
      <button onclick="navigateTo('screen-tools')">Back to Tools</button>
    </section>

    <!-- Step Counter -->
    <section class="screen" id="screen-step-counter">
      <h2>Step Counter</h2>
      <p>Steps walked today:</p>
      <div id="step-count">0</div>
      <button onclick="addSteps(1000)">Add 1000 Steps</button>
      <button onclick="resetSteps()">Reset</button>
      <button onclick="navigateTo('screen-tools')">Back to Tools</button>
    </section>

    <!-- Creativity Corner -->
    <section class="screen" id="screen-creativity">
      <h2>Creativity Corner</h2>
      <p>Draw or write something expressive:</p>
      <textarea id="creativity-textarea" placeholder="Write a poem, doodle ideas, or lyrics..."></textarea>
      <button onclick="saveCreativity()">Save & Back</button>
    </section>
  </div>

  <script src="script.js"></script>
</body>
</html>

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
                                                                                     CSS
#CSS--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

:root {
  --primary: #705be3;
  --accent: #ffd86b;
  --calm1: #a3e2ff;
  --calm2: #fed6e3;
  --calm3: #f4e2d8;
  --serene-blue: #8fd3f4;
  --serene-pink: #f7bb97;
  --soft-bg: #f9fafd;
  --card-bg: #ffffffb5;
  --input-bg: #f1f4fc;
  --shadow: 0 10px 32px 0 rgba(112,91,227,0.12), 0 2px 4px 0 rgba(0,0,0,0.03);
}

body {
  background: radial-gradient(circle at 70% 30%, var(--calm1), var(--calm2) 70%, var(--soft-bg) 100%);
  min-height: 100vh;
  margin: 0;
  font-family: 'Inter', sans-serif;
  color: #353553;
  display: flex;
  align-items: center;
  justify-content: center;
}

#app {
  width: 380px;
  max-width: 95vw;
  min-height: 680px;
  border-radius: 32px;
  background: var(--card-bg);
  box-shadow: var(--shadow);
  position: relative;
  overflow: hidden;
  padding-bottom: 44px;
}

#sky {
  z-index: 0;
  position: absolute;
  inset: 0;
  transition: background 1s;
  background: linear-gradient(to bottom, var(--serene-blue) 40%, var(--serene-pink) 100%);
}

#sun, #moon {
  width: 56px; height: 56px;
  border-radius: 50%;
  position: absolute;
  left: 24px; top: 32px;
  box-shadow: 0 2px 16px 2px #fff6;
  transition: opacity 0.8s, background 1.2s;
}
#sun {
  background: radial-gradient(circle, #ffe259 65%, #ffa751 100%);
  opacity: 1;
  z-index: 1;
}
#moon {
  background: radial-gradient(circle, #e0e6f7 60%, #868f96 100%);
  opacity: 0;
  z-index: 2;
}

.screen {
  position: absolute;
  inset: 0;
  z-index: 2;
  background: none;
  display: none;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  animation: fadeIn 0.6s;
  padding: 32px 16px;
  overflow-y: auto;
}
.screen.active { display: flex; }

@keyframes fadeIn {
  from { opacity:0; transform: translateY(12px);}
  to { opacity:1; transform: translateY(0);}
}

h1 {
  font-size: 2.4rem;
  color: var(--primary);
  font-weight: 700;
  margin: 0 0 8px 0;
  letter-spacing: 1.5px;
}

h2 {
  font-size: 1.45rem;
  color: #3c326d;
  margin: 0 0 14px 0;
  font-weight: 600;
  line-height: 1.2;
}

p {
  color: #5f5f78;
  margin: 0 0 22px 0;
}

.emoji-row {
  display: flex;
  gap: 18px;
  justify-content: center;
  margin: 18px 0 10px 0;
}

.emoji-row button {
  font-size: 2.1em;
  background: none;
  border: none;
  cursor: pointer;
  transition: transform 0.25s ease;
}
.emoji-row button:hover, .emoji-row button:focus {
  transform: scale(1.25) rotate(-5deg);
  background: rgba(255,255,255,0.13);
  border-radius: 50%;
}

.tools-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 15px;
  width: 100%;
  margin-bottom: 10px;
}
.tools-grid button {
  background: var(--input-bg);
  color: var(--primary);
  font-weight: 500;
  font-size: 1.12em;
  border: none;
  padding: 18px 0;
  border-radius: 17px;
  box-shadow: 0 4px 18px 0 rgba(185,186,222,0.06);
  transition: background 0.3s, color 0.24s;
}
.tools-grid button:hover, .tools-grid button:focus {
  background: var(--primary);
  color: white;
}

button {
  font-family: inherit;
  font-size: 1em;
  border: none;
  border-radius: 13px;
  background: var(--primary);
  color: #fff;
  padding: 12px 28px;
  box-shadow: 0 3px 12px 0 rgba(112,91,227,0.10);
  transition: background 0.3s opacity 0.3s;
  letter-spacing: 0.7px;
  cursor: pointer;
  font-weight: 600;
  outline: none;
  margin: 8px 0;
}
.next-btn, .back-btn {
  padding: 9px 17px;
  font-size: 1em;
  background: #ede9fe;
  color: var(--primary);
  border-radius: 9px;
  margin-left: 7px;
  margin-right: 7px;
  box-shadow: none;
}
.next-btn:hover, .back-btn:hover {
  background: var(--primary);
  color: #fff;
}

.consult-btn {
  position: absolute;
  bottom: 18px;
  right: 16px;
  z-index: 50;
  background: var(--accent);
  color: #835012;
  border-radius: 18px;
  padding: 11px 22px;
  font-weight: 700;
  font-size: 1em;
  box-shadow: 0 2px 18px #ffc8013f;
  opacity: 0.96;
  border: 2px solid #faf1cb66;
  transition: background 0.23s, color 0.23s;
}
.consult-btn:hover {
  background: #fff3c6;
  color: #ffac01;
}

.circle, #breathe-circle {
  width: 105px;
  height: 105px;
  background: radial-gradient(circle,#c7fff7 60%, var(--primary) 100%);
  border-radius: 50%;
  animation: breathGlow 3.3s infinite ease-in-out;
  margin-bottom: 22px;
  box-shadow: 0 0 32px 0 #00bcd47a;
}
@keyframes breathGlow {
  0%,100% { transform: scale(1); box-shadow: 0 0 32px #c8fbfa86;}
  50% { transform: scale(1.33); box-shadow: 0 0 46px #6c63ff96;}
}

textarea, input:not([type="number"]) {
  border: none;
  background: var(--input-bg);
  border-radius: 12px;
  width: 97%;
  min-height: 48px;
  padding: 10px 14px;
  margin: 7px 0 12px 0;
  font-size: 1em;
  resize: none;
  outline: none;
  box-shadow: none;
}

input[type="number"] {
  width: 90px;
  border-radius: 10px;
  border: 1.1px solid #d7dbec;
  margin: 10px 0 16px 0;
  padding: 9px 13px;
  font-size: 1em;
  background: var(--soft-bg);
}

input:focus, textarea:focus { background: #f3ecff; }

#water-counter, #step-count {
  font-size: 1.3em;
  margin-bottom: 12px;
  color: var(--primary);
  font-weight: 600;
  background: #f9f7ff;
  border-radius: 7px;
  padding: 8px 15px;
  display: inline-block;
  letter-spacing: 1px;
  box-shadow: 0 1px 10px 0 #dcecff3b;
}

.chat-input-area {
  display: flex;
  width: 100%;
  gap: 7px;
  align-items: center;
  margin-top: 8px;
}
.chat-input-area input {
  flex: 1 1 0;
}
#chat-log {
  background: #f2f2fa;
  width: 100%;
  min-height: 150px; max-height: 210px;
  overflow-y: auto;
  border-radius: 13px;
  box-shadow: 0 2px 10px #cfcff73a;
  margin: 10px 0 0 0;
  padding: 11px;
  font-size: 1em;
  display: flex;
  flex-direction: column;
  gap: 7px;
}

#chat-log div.user { align-self: flex-end; background: #e3e1fb; color: #624EDD; border-radius: 13px 13px 2px 13px; padding: 8px 13px; max-width: 92%; }
#chat-log div.bot { align-self: flex-start; background: #e7f4ff; color: #1c3554; border-radius: 13px 13px 13px 2px; padding: 8px 13px; max-width: 92%; }

@media (max-width: 477px) {
  #app { min-height: 99vh; width: 100vw; border-radius: 0; }
  .screen { padding: 20px 6vw; }
}

::-webkit-scrollbar { width: 7px; background: #f9f9fd;}
::-webkit-scrollbar-thumb { background: #e3e1fb; border-radius: 12px; }

::-webkit-input-placeholder { color: #888caa; opacity: 1; }
::-moz-placeholder { color: #888caa; opacity: 1; }
:-ms-input-placeholder { color: #888caa; opacity: 1; }
::placeholder { color: #888caa; opacity: 1; }
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
                                                                   SCRIP.JS
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  
// --- State ---
let waterCount = 0;
let stepCount = 0;
let bodyScanInterval = null;

// --- Navigation, Modal, and Sky Dynamics ---
function navigateTo(id) {
  // Hide all screens and show one
  document.querySelectorAll('.screen').forEach(sc => sc.classList.remove('active'));
  document.getElementById(id).classList.add('active');
}

function openConsult() {
  alert('A licensed therapist will join you soon via secure chat or video. Stay tuned!');
}

// --- Mood-Driven Suncycle and Gradients ---
function setMood(mood) {
  const sky = document.getElementById('sky');
  const sun = document.getElementById('sun');
  const moon = document.getElementById('moon');
  // Animate backgrounds for different moods
  switch (mood) {
    case 'happy':
      sky.style.background = 'linear-gradient(120deg, #fff6b7 0%, #f6416c 100%)';
      sun.style.opacity = '1';
      moon.style.opacity = '0';
      break;
    case 'sad':
      sky.style.background = 'linear-gradient(120deg, #89f7fe 0%, #66a6ff 100%)';
      sun.style.opacity = '0';
      moon.style.opacity = '1';
      break;
    case 'angry':
      sky.style.background = 'linear-gradient(120deg, #e96443 0%, #904e95 100%)';
      sun.style.opacity = '0';
      moon.style.opacity = '1';
      break;
    case 'anxious':
      sky.style.background = 'linear-gradient(120deg, #c9ffbf 0%, #ffafbd 100%)';
      sun.style.opacity = '0.7';
      moon.style.opacity = '1';
      break;
    case 'neutral':
    default:
      sky.style.background = 'linear-gradient(120deg, #a3e2ff 0%, #fed6e3 100%)';
      sun.style.opacity = '1';
      moon.style.opacity = '0';
      break;
  }
  navigateTo('screen-tools');
}

// --- Wellness Tool Logic ---

// -- Hydration Tracker --
function addWater() {
  waterCount = Math.min(waterCount + 1, 8);
  updateWater();
}
function resetWater() {
  waterCount = 0;
  updateWater();
}
function updateWater() {
  document.getElementById('water-counter').innerText = `${waterCount} / 8 Glasses`;
}

// -- Step Counter --
function addSteps(n) {
  stepCount = Math.min(stepCount + n, 20000);
  updateSteps();
}
function resetSteps() {
  stepCount = 0;
  updateSteps();
}
function updateSteps() {
  document.getElementById('step-count').innerText = stepCount;
}

// -- Sleep Tracker --
function saveSleep() {
  const h = document.getElementById('sleep-hours').value;
  if (h.length > 0 && Number(h) >= 0) {
    alert(`Great! Slept ${h} hours last night.\nYour log is saved.`);
    document.getElementById('sleep-hours').value = '';
    navigateTo('screen-tools');
  } else {
    alert('Please enter a valid number of hours.');
  }
}

// -- Journal, Gratitude, Creativity save (mock persistence) --
function saveJournal() {
  const text = document.getElementById('journal-textarea').value;
  alert('Your journal has been saved.');
  document.getElementById('journal-textarea').value = '';
  navigateTo('screen-tools');
}

function saveGratitude() {
  const g1 = document.getElementById('gratitude-1').value;
  const g2 = document.getElementById('gratitude-2').value;
  const g3 = document.getElementById('gratitude-3').value;
  alert("Gratitude noted:\n" + [g1, g2, g3].filter(x=>x).join('\n'));
  document.getElementById('gratitude-1').value = '';
  document.getElementById('gratitude-2').value = '';
  document.getElementById('gratitude-3').value = '';
  navigateTo('screen-tools');
}

function saveCreativity() {
  alert('Your creativity is logged. Keep expressing yourself!');
  document.getElementById('creativity-textarea').value = '';
  navigateTo('screen-tools');
}

// -- Body Scan Timer --
function startBodyScan() {
  let timer = 30;
  const display = document.getElementById('body-scan-timer');
  display.innerText = "30s";
  if (bodyScanInterval) clearInterval(bodyScanInterval);
  bodyScanInterval = setInterval(() => {
    timer -= 1;
    if (timer > 0) {
      display.innerText = timer + "s";
    } else {
      clearInterval(bodyScanInterval);
      display.innerText = "Done!";
      setTimeout(() => {
        display.innerText = "";
        alert("How do you feel? Your 30s scan is complete!");
      }, 1000);
    }
  }, 1000);
}

// -- Mini Quest
function completeQuest() {
  alert('Great job! Small wins = big progress. Quest completed for today.');
  navigateTo('screen-tools');
}

// --- AI Chat ---
function sendMessage() {
  const log = document.getElementById('chat-log');
  const input = document.getElementById('chat-input');
  const msg = input.value.trim();
  if (!msg) return;

  // Add user bubble
  const userDiv = document.createElement('div');
  userDiv.className = 'user';
  userDiv.innerText = msg;
  log.appendChild(userDiv);

  input.value = '';

  // Bot thinking bubble
  const botDiv = document.createElement('div');
  botDiv.className = 'bot';
  botDiv.innerText = '...';
  log.appendChild(botDiv);
  log.scrollTop = log.scrollHeight;

  setTimeout(() => {
    botDiv.innerText = getBotReply(msg);
    log.scrollTop = log.scrollHeight;
  }, 700);
}

// --- AI reply logic (placeholder, customize for your purpose!) ---
function getBotReply(text) {
  const generic = [
    "Thank you for sharing. Want to try a breathing exercise?",
    "I'm here for you. How would you describe your feelings today?",
    "Would you like to record this in your journal or practice gratitude?",
    "Remember, small steps matter. Ready for a mini quest?",
    "Staying hydrated and rested really helps. Want to track those?"
  ];
  if (/sad|blue|down|unhappy|tired|cry/i.test(text)) return "I'm sorry you're feeling that way. Shall we try some breathing or gratitude?";
  if (/angry|mad|upset|frustrated/i.test(text)) return "Would you like to calm down with a body scan or chat more?";
  if (/happy|good|great|fine|awesome/i.test(text)) return "That's wonderful! Celebrate every win. Maybe capture a gratitude or a creative thought?";
  return generic[Math.floor(Math.random()*generic.length)];
}

// --- Initialization and Accessibility ---
window.addEventListener('DOMContentLoaded', () => {
  // For better keyboard navigation:
  document.querySelectorAll('button, input, textarea').forEach(el => {
    el.addEventListener('keyup', function(e) { if(e.key==='Enter' && typeof el.onclick==='function') el.onclick(); });
  });
  updateWater();
  updateSteps();
});
