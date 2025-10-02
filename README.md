<!DOCTYPE html>
<html lang="ne">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Dashain Celebration App</title>
<style>
  body {
    margin: 0;
    font-family: "Segoe UI", sans-serif;
    background: #fdf5e6;
    color: #333;
    text-align: center;
    overflow-x: hidden;
  }
  header {
    background: #d84315;
    color: #fff;
    padding: 16px;
    font-size: 1.6em;
    font-weight: bold;
    text-shadow: 0 2px 4px rgba(0,0,0,0.3);
  }
  nav {
    position: fixed;
    bottom: 0;
    left: 0;
    right: 0;
    background: #4e342e;
    display: flex;
    justify-content: space-around;
    z-index: 200;
  }
  nav button {
    flex: 1;
    padding: 14px;
    border: none;
    background: #4e342e;
    color: #fff;
    font-size: 1em;
    transition: background 0.3s;
  }
  nav button:hover {
    background: #5d4037;
  }
  section {
    display: none;
    padding: 24px 16px;
    min-height: 80vh;
    box-sizing: border-box;
  }
  section.active {
    display: block;
    animation: fadeIn 0.4s ease-in-out;
  }
  @keyframes fadeIn {
    from { opacity: 0; }
    to { opacity: 1; }
  }
  .card {
    background: #fff;
    margin: 16px auto;
    max-width: 500px;
    padding: 20px;
    border-radius: 12px;
    box-shadow: 0 4px 12px rgba(0,0,0,0.15);
    text-align: left;
  }
  .card h3 {
    margin-top: 0;
    color: #bf360c;
  }
  .chatbox {
    margin: 20px auto;
    width: 90%;
    max-width: 400px;
    background: #fff;
    border-radius: 12px;
    box-shadow: 0 4px 10px rgba(0,0,0,0.2);
    padding: 16px;
  }
  #chat {
    height: 200px;
    overflow-y: auto;
    border: 1px solid #ccc;
    margin-bottom: 12px;
    padding: 8px;
    text-align: left;
    background: #fafafa;
  }
  .msg-user { color: #1565c0; margin: 6px 0; }
  .msg-ai { color: #2e7d32; margin: 6px 0; }
  .btn {
    background: linear-gradient(135deg, #ffb74d, #d84315);
    color: #111;
    padding: 10px 16px;
    border: none;
    border-radius: 20px;
    font-weight: bold;
    cursor: pointer;
    transition: background 0.3s;
  }
  .btn:hover {
    background: linear-gradient(135deg, #ffcc80, #e64a19);
  }
  label {
    display: block;
    margin: 10px 0;
    font-size: 1em;
  }
  input[type="text"], input[type="number"], input[type="search"] {
    width: 80%;
    padding: 8px;
    font-size: 1em;
    border: 1px solid #bbb;
    border-radius: 6px;
    margin-top: 4px;
  }
  .greeting {
    margin: 20px;
    font-size: 1.2em;
    color: #4e342e;
  }
</style>
</head>
<body>

<header id="headerTitle">🎉 Dashain Celebration 🎉</header>

<!-- Gate section -->
<section id="gate" class="active">
  <h2>Welcome to the Dashain App</h2>
  <p>Enter your name and age to continue.</p>
  <form onsubmit="return enterGate()">
    <label>Name: <input type="text" id="gateName" required></label>
    <label>Age: <input type="number" id="gateAge" required></label>
    <button class="btn" type="submit">Enter App</button>
  </form>
  <p id="gateMessage" style="color:red; font-weight:bold;"></p>
</section>

<!-- Home / Info -->
<section id="home">
  <div class="greeting">Namaste <span id="userDisplay"></span>! Welcome to your Dashain guide.</div>

  <div class="card">
    <h3>What is Dashain?</h3>
    <p>Dashain (दशैं) is Nepal’s most celebrated festival. It spans 15 days and honors Goddess Durga’s victory over the demon Mahishasura. It’s a time for family reunions, blessings, rituals, and joy.</p>
  </div>

  <div class="card">
    <h3>Traditions & Rituals</h3>
    <ul>
      <li><b>Tika & Jamara:</b> Elders put red tika & jamara on younger family members as blessings.</li>
      <li><b>Ghatasthapana:</b> The day when barley seeds (jamara) are planted.</li>
      <li><b>Phulpati:</b> Floral procession, sacred leaves brought into temples.</li>
      <li><b>Animal sacrifice:</b> In some communities, offerings to goddess Durga.</li>
      <li><b>Swings & Kites:</b> Traditional swings (ping) and kite flying are common during Dashain.</li>
    </ul>
  </div>

  <div class="card">
    <h3>Fun Facts</h3>
    <ul>
      <li>Malashree Dhun is traditionally played to announce arrival of Dashain. 2</li>
      <li>“Dashain Aayo” is a popular Nepali song about the festival. 3</li>
    </ul>
  </div>

  <div class="card">
    <h3>Important Dates (2082)</h3>
    <ul>
      <li>Ghatasthapana – Sept 29</li>
      <li>Phulpati – Oct 5</li>
      <li>Maha Ashtami – Oct 6</li>
      <li>Maha Navami – Oct 7</li>
      <li>Bijaya Dashami – Oct 8</li>
    </ul>
  </div>
</section>

<!-- Dashain AI Chatbot -->
<section id="ai">
  <h2>🤖 Dashain Expert</h2>
  <div class="chatbox">
    <div id="chat"></div>
    <input type="search" id="question" placeholder="Ask anything about Dashain...">
    <button class="btn" onclick="askAI()">Ask</button>
  </div>
</section>

<!-- Dashain Tune / Music -->
<section id="tune">
  <h2>🎶 Dashain Music</h2>
  <p>Enjoy an instrumental Dhun inspired by Malashree Dhun:</p>
  <audio id="music" controls loop>
    <!-- placeholder mp3, replace with real dashain/malashree mp3 you have rights to -->
    <source src="https://cdn.jsdelivr.net/gh/anars/blank-audio@master/10-seconds-of-silence.mp3" type="audio/mpeg">
    Your browser does not support audio
  </audio>
  <p style="margin-top:12px; font-size:0.95em;">(Replace with a proper Dashain instrument track)</p>
</section>

<!-- Profile Page -->
<section id="profile">
  <h2>👤 Profile</h2>
  <div class="card">
    <p><b>Name:</b> <span id="profName"></span></p>
    <p><b>Age:</b> <span id="profAge"></span></p>
    <p style="color:green;">You are allowed to access this app.</p>
  </div>
</section>

<!-- Bottom navigation -->
<nav id="navbar" style="display:none;">
  <button onclick="showPage('home')">Home</button>
  <button onclick="showPage('ai')">AI</button>
  <button onclick="showPage('tune')">Tune</button>
  <button onclick="showPage('profile')">Profile</button>
</nav>

<script>
let userName = "";
let userAge = 0;

function enterGate() {
  userName = document.getElementById("gateName").value.trim();
  userAge = parseInt(document.getElementById("gateAge").value);
  const msg = document.getElementById("gateMessage");

  if (!userName) {
    msg.innerText = "Please enter your name.";
    return false;
  }
  if (isNaN(userAge)) {
    msg.innerText = "Please enter a valid age.";
    return false;
  }

  if (userAge < 12) {
    msg.innerText = `Sorry ${userName}, you are under 12 and cannot access this site.`;
    return false;
  }

  // passed gate
  document.getElementById("gate").style.display = "none";
  document.getElementById("navbar").style.display = "flex";
  document.getElementById("userDisplay").innerText = userName;
  document.getElementById("profName").innerText = userName;
  document.getElementById("profAge").innerText = userAge;
  showPage("home");
  return false;
}

function showPage(id) {
  document.querySelectorAll("section").forEach(sec => sec.classList.remove("active"));
  const sec = document.getElementById(id);
  if (sec) sec.classList.add("active");
  document.getElementById("headerTitle").innerText = "🎉 Dashain — " + id.charAt(0).toUpperCase() + id.slice(1);
}

// Intelligent Dashain AI
function askAI() {
  const qraw = document.getElementById("question").value;
  const chat = document.getElementById("chat");
  if (!qraw) return;
  const q = qraw.toLowerCase();

  let answer = "माफ गर्नुहोस्, म त्यो प्रश्नको उत्तर थाहा छैन। कृपया टिका, जमरा, मितिहरू, परम्परा, देवी दुर्गा… विषयहरूमा सोध्नुहोस्।";

  // greetings
  if (q.includes("namaste") || q.includes("hello") || q.includes("hi")) {
    answer = `नमस्ते ${userName}! शुभ दशैं!`;
  } else if (q.includes("what is dashain") || q.includes("dashain के हो")) {
    answer = "दशैं नेपालकै ठूलो चाड हो, जहाँ शक्ति, पारिवारिक एकता र धर्म मनाइन्छ।";
  } else if (q.includes("when is dashain") || q.includes("dashain कहिले")) {
    answer = "सन् 2082 को दशैं 29 सेप्टेम्बरबाट 8 अक्टोबरसम्म हुनेछ।";
  } else if (q.includes("tika") || q.includes("टिका")) {
    answer = "टिका रातो रंग र चावलले बनाइन्छ र बुढाहरूले आशिर्वाद स्वरूप उमेरका कान्छाहरूको शिरमा लगाइन्छ।";
  } else if (q.includes("jamara") || q.includes("जमरा")) {
    answer = "जमरा धानका बीउबाट बालिन्छ र पवित्रता र समृद्धिको प्रतीक हो।";
  } else if (q.includes("swing") || q.includes("झुला")) {
    answer = "झुला पारम्परिक रूपमा बाँस र रस्सीबाट बनाईन्छ र विशेष गरी दशैंका दिन रमाइन्छ।";
  } else if (q.includes("kite") || q.includes("पिचकारी") || q.includes("पतंग")) {
    answer = "पिचकारी / पतंग उडाइसक्नु रमाइलो हुन्छ, छुट्टै उत्सवको आनन्द।";
  } else if (q.includes("durga") || q.includes("देवी") || q.includes("दुर्गा")) {
    answer = "दशैंमा देवी दुर्गालाई पूजा गरिन्छ, उनीले दुष्ट शक्तिसँग युद्ध गरी विजय प्राप्त गरिन्।";
  }

  chat.innerHTML += `<p class="msg-user"><b>You:</b> ${qraw}</p><p class="msg-ai"><b>AI:</b> ${answer}</p>`;
  document.getElementById("question").value = "";
  chat.scrollTop = chat.scrollHeight;
}
</script>

</body>
</html>
