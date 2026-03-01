# Ucapan Buat Kaka Fariddd
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Ada Ucapan Untukmu</title>

<style>
body {
    margin: 0;
    font-family: 'Segoe UI', sans-serif;
    overflow: hidden;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
    background: linear-gradient(-45deg, #ffc0cb, #ffb6c1, #98fb98, #90ee90);
    background-size: 400% 400%;
    animation: gradientBG 10s ease infinite;
}

@keyframes gradientBG {
    0% {background-position: 0% 50%;}
    50% {background-position: 100% 50%;}
    100% {background-position: 0% 50%;}
}

.card {
    background: rgba(255,255,255,0.95);
    padding: 35px;
    border-radius: 30px;
    box-shadow: 0 15px 40px rgba(0,0,0,0.2);
    max-width: 360px;
    animation: popUp 0.6s ease;
}

@keyframes popUp {
    from {transform: scale(0.8); opacity: 0;}
    to {transform: scale(1); opacity: 1;}
}

button {
    background: #ff69b4;
    color: white;
    border: none;
    padding: 12px 22px;
    border-radius: 25px;
    cursor: pointer;
    font-size: 14px;
    margin-top: 15px;
    transition: 0.3s;
}

button:hover {
    background: #ff1493;
    transform: scale(1.05);
}

.hidden { display: none; }

.cake-container {
    position: relative;
    font-size: 90px;
}

.flame {
    position: absolute;
    top: -18px;
    left: 50%;
    transform: translateX(-50%);
    font-size: 28px;
    animation: flicker 0.2s infinite alternate;
}

@keyframes flicker {
    from { transform: translateX(-50%) scale(1); }
    to { transform: translateX(-50%) scale(1.2); }
}

.smoke {
    position: absolute;
    top: -25px;
    left: 50%;
    transform: translateX(-50%);
    font-size: 22px;
    animation: smokeUp 1s forwards;
}

@keyframes smokeUp {
    0% { opacity: 1; transform: translate(-50%,0); }
    100% { opacity: 0; transform: translate(-50%,-40px); }
}

.confetti {
    position: fixed;
    width: 8px;
    height: 8px;
    top: -10px;
    animation: fall linear forwards;
}

@keyframes fall {
    to { transform: translateY(100vh) rotate(720deg); }
}

.floating {
    position: fixed;
    font-size: 20px;
    animation: floatUp linear infinite;
    opacity: 0.7;
}

@keyframes floatUp {
    from { transform: translateY(100vh); }
    to { transform: translateY(-10vh); }
}

.message {
    margin-top: 15px;
    font-size: 14px;
    color: #444;
    line-height: 1.6;
}
</style>
</head>

<body>

<div class="card" id="startCard">
    <h2>Ada ucapan untukmu 💌</h2>
    <button onclick="openCard()">Klik di sini untuk membuka kartu ucapan</button>
</div>

<div class="card hidden" id="cakeCard">
    <div class="cake-container">
        🎂
        <div class="flame" id="flame">🔥</div>
    </div>
    <p>Lilin angka <strong>25</strong> lagi menyala ✨</p>
    <button onclick="blowCandle()">Klik di sini untuk tiup lilin</button>
</div>

<div class="card hidden" id="messageCard">
    <h3>🎉✨ Happy 25th Birthday ✨🎉</h3>
    <p class="message" id="typingText"></p>
</div>

<script>
const text = `Selamat ulang tahun yang ke-25 ya kakak Fariddd 🤍💗

Panjang umurnya, sehat terusss, bahagia teruss.
Semoga cepat dapat kerja dan nanti segera ketemu jodohnyaa 🌸
Semoga semua harapan yang belum tercapai segera tercapaiii.

Pokoknya wish u all the best yaw kaka Fariddd 💚✨`;

function openCard() {
    document.getElementById("startCard").classList.add("hidden");
    document.getElementById("cakeCard").classList.remove("hidden");
}

function blowCandle() {
    const flame = document.getElementById("flame");
    flame.remove();

    const smoke = document.createElement("div");
    smoke.className = "smoke";
    smoke.innerHTML = "💨";
    document.querySelector(".cake-container").appendChild(smoke);

    setTimeout(() => {
        document.getElementById("cakeCard").classList.add("hidden");
        document.getElementById("messageCard").classList.remove("hidden");
        launchConfetti();
        typeText();
    }, 800);
}

function launchConfetti() {
    for (let i = 0; i < 120; i++) {
        const confetti = document.createElement("div");
        confetti.className = "confetti";
        confetti.style.left = Math.random() * 100 + "vw";
        confetti.style.backgroundColor =
            ["#ff69b4","#98fb98","#ff1493","#32cd32","#ffffff"]
            [Math.floor(Math.random()*5)];
        confetti.style.animationDuration = (Math.random()*3+2)+"s";
        document.body.appendChild(confetti);
        setTimeout(() => confetti.remove(), 5000);
    }
}

function typeText() {
    let i = 0;
    function typing() {
        if (i < text.length) {
            document.getElementById("typingText").innerHTML += text.charAt(i);
            i++;
            setTimeout(typing, 30);
        }
    }
    typing();
}

function createFloating() {
    const symbols = ["💗","🌸","💚"];
    for (let i = 0; i < 20; i++) {
        const float = document.createElement("div");
        float.className = "floating";
        float.innerHTML = symbols[Math.floor(Math.random()*3)];
        float.style.left = Math.random()*100+"vw";
        float.style.animationDuration = (Math.random()*5+5)+"s";
        document.body.appendChild(float);
    }
}

createFloating();
</script>

</body>
</html>
