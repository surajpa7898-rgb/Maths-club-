# Maths-club-
<!DOCTYPE html>
<html lang="hi">
<head>
<meta charset="UTF-8">
<title>Maths Learning App</title>

<style>
body {
    font-family: Arial;
    margin: 0;
    background: #f0f8ff;
}
header {
    background: #2196F3;
    color: white;
    padding: 15px;
    text-align: center;
}
nav {
    background: #333;
    padding: 10px;
    text-align: center;
}
nav button {
    margin: 5px;
    padding: 10px;
    border: none;
    background: #555;
    color: white;
    cursor: pointer;
}
nav button:hover {
    background: #2196F3;
}
.section {
    display: none;
    padding: 20px;
}
.active {
    display: block;
}
.box {
    background: white;
    padding: 15px;
    margin: 10px 0;
    border-radius: 8px;
}
</style>
</head>

<body>

<header>
<h1>📘 आसान गणित सीखें</h1>
<p>वैदिक मैथ्स | अबेकस | प्रैक्टिस</p>
</header>

<nav>
<button onclick="show('home')">होम</button>
<button onclick="show('levels')">क्लास</button>
<button onclick="show('vedic')">वैदिक मैथ्स</button>
<button onclick="show('abacus')">अबेकस</button>
</nav>

<!-- HOME -->
<div id="home" class="section active">
<h2>स्वागत है 👋</h2>
<p>यहाँ आप आसान तरीके से गणित सीख सकते हैं</p>
</div>

<!-- LEVELS -->
<div id="levels" class="section">
<h2>क्लास चुनें</h2>

<button onclick="startLevel(5)">कक्षा 5</button>
<button onclick="startLevel(6)">कक्षा 6</button>
<button onclick="startLevel(7)">कक्षा 7</button>
<button onclick="startLevel(8)">कक्षा 8</button>

<div id="quizBox" class="box" style="display:none;">
<h3 id="question"></h3>
<p>⏱️ समय: <span id="time">10</span> सेकंड</p>
<p>🎯 स्कोर: <span id="score">0</span></p>
<button onclick="answer(true)">उत्तर दें</button>
</div>

</div>

<!-- VEDIC -->
<div id="vedic" class="section">
<h2>वैदिक मैथ्स</h2>
<p>उदाहरण: 99 × 98</p>
<p>ट्रिक: (100 - 1)(100 - 2)</p>
<p>उत्तर: 9702</p>
</div>

<!-- ABACUS -->
<div id="abacus" class="section">
<h2>अबेकस मैथ्स</h2>
<p>अबेकस से तेज गणना करना आसान होता है</p>
</div>

<script>
let currentLevel = 5;
let score = 0;
let time = 10;
let timer;

function show(id) {
    document.querySelectorAll('.section').forEach(s => s.classList.remove('active'));
    document.getElementById(id).classList.add('active');
}

function startLevel(level) {
    currentLevel = level;
    score = 0;
    document.getElementById('score').innerText = score;
    document.getElementById('quizBox').style.display = 'block';
    nextQuestion();
}

function nextQuestion() {
    clearInterval(timer);
    time = 10;
    document.getElementById('time').innerText = time;

    let q, ans;

    if (currentLevel == 5) {
        let a = Math.floor(Math.random()*20);
        let b = Math.floor(Math.random()*20);
        q = a + " + " + b;
        ans = a + b;
    }
    else if (currentLevel == 6) {
        let a = Math.floor(Math.random()*50);
        let b = Math.floor(Math.random()*20);
        q = a + " - " + b;
        ans = a - b;
    }
    else if (currentLevel == 7) {
        let a = Math.floor(Math.random()*20);
        let b = Math.floor(Math.random()*10);
        q = a + " × " + b;
        ans = a * b;
    }
    else {
        let a = Math.floor(Math.random()*50);
        let b = Math.floor(Math.random()*10)+1;
        q = a + " ÷ " + b;
        ans = Math.floor(a / b);
    }

    window.correctAns = ans;
    document.getElementById('question').innerText = "सवाल: " + q;

    timer = setInterval(() => {
        time--;
        document.getElementById('time').innerText = time;
        if (time <= 0) {
            alert("⏰ समय समाप्त! सही उत्तर: " + correctAns);
            nextQuestion();
        }
    }, 1000);
}

function answer() {
    let user = prompt("अपना उत्तर लिखें:");
    if (parseInt(user) === correctAns) {
        score++;
        alert("सही 👍");
    } else {
        alert("गलत ❌ सही उत्तर: " + correctAns);
    }
    document.getElementById('score').innerText = score;
    nextQuestion();
}
</script>

</body>
</html>
