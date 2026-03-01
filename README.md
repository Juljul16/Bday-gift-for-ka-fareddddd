# Bday-gift-for-ka-fareddddd
<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Ucapan Untukmu</title>

<style>
body {
    margin: 0;
    font-family: 'Segoe UI', sans-serif;
    background: linear-gradient(135deg, #ffc0cb, #98fb98);
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    text-align: center;
    overflow: hidden;
}

.card {
    background: white;
    padding: 30px;
    border-radius: 25px;
    box-shadow: 0 10px 30px rgba(0,0,0,0.2);
    max-width: 350px;
    transition: 0.5s;
}

button {
    background: #ff69b4;
    color: white;
    border: none;
    padding: 12px 20px;
    border-radius: 20px;
    cursor: pointer;
    font-size: 14px;
    margin-top: 15px;
    transition: 0.3s;
}

button:hover {
    background: #ff1493;
}

.hidden {
    display: none;
}

/* Cake */
.cake-container {
    position: relative;
    font-size: 80px;
}

.flame {
    position: absolute;
    top: -15px;
    left: 50%;
    transform: translateX(-50%);
    font-size: 25px;
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
    font-size: 20px;
    opacity: 0;
    animation: smokeUp 1s forwards;
}

@keyframes smokeUp {
    0% { opacity: 0.8; transform: translate(-50%, 0); }
    100% { opacity: 0; transform: translate(-50%, -40px); }
}

/* Confetti */
.confetti {
    position: fixed;
    width: 8px;
    height: 8px;
    background-color: red;
    top: -10px;
    animation: fall linear forwards;
}

@keyframes fall {
    to {
        transform: translateY(100vh) rotate(720deg);
    }
}

.message {
    margin-top: 15px;
    font-size: 14px;
    color: #444;
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
    <h3>🎉✨</h3>
    <p class="message">
        Selamat ulang tahun yang ke-25 ya kakak Fariddd 🤍💗<br><br>
        Panjang umurnya, sehat terusss, bahagia teruss.<br>
        Semoga cepat dapat kerja dan nanti segera ketemu jodohnyaa 🌸<br>
        Semoga semua harapan yang belum tercapai segera tercapaiii.<br><br>
        Pokoknya wish u all the best yaw kaka Fariddd 💚✨
    </p>
</div>

<script>
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
    }, 800);
}

function launchConfetti() {
    for (let i = 0; i < 80; i++) {
        const confetti = document.createElement("div");
        confetti.className = "confetti";
        confetti.style.left = Math.random() * 100 + "vw";
        confetti.style.backgroundColor = 
            ["#ff69b4","#98fb98","#ff1493","#32cd32","#ffffff"]
            [Math.floor(Math.random()*5)];
        confetti.style.animationDuration = (Math.random() * 3 + 2) + "s";
        document.body.appendChild(confetti);

        setTimeout(() => confetti.remove(), 5000);
    }
}
</script>

</body>
</html>
