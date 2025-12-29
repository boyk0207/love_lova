<!DOCTYPE html>
<html lang="mn">
<head>
<meta charset="UTF-8">
<title>2026 New Year Love 💖</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<style>
    body {
        margin: 0;
        height: 100vh;
        background: linear-gradient(180deg,
            #fbc2eb,
            #a6c1ee,
            #fde2e4);
        display: flex;
        justify-content: center;
        align-items: center;
        overflow: hidden;
        font-family: 'Segoe UI', sans-serif;
        color: #ffffff;
        touch-action: manipulation;
    }

    .container {
        text-align: center;
        z-index: 2;
    }

    h1 {
        font-size: 2.6rem;
        text-shadow: 0 0 20px rgba(255,255,255,0.6);
        margin-bottom: 10px;
    }

    #countdown {
        font-size: 1.8rem;
        margin-bottom: 20px;
        text-shadow: 0 0 10px rgba(255,255,255,0.8);
    }

    /* Big heart */
    .heart {
        width: 120px;
        height: 120px;
        background: #ffffff;
        position: relative;
        margin: 40px auto;
        transform: rotate(45deg);
        animation: beat 1s infinite;
        box-shadow: 0 0 40px #ffffff;
    }

    .heart::before,
    .heart::after {
        content: "";
        width: 120px;
        height: 120px;
        background: #ffffff;
        border-radius: 50%;
        position: absolute;
    }

    .heart::before {
        top: -60px;
        left: 0;
    }

    .heart::after {
        left: -60px;
        top: 0;
    }

    @keyframes beat {
        0%, 100% { transform: rotate(45deg) scale(1); }
        50% { transform: rotate(45deg) scale(1.2); }
    }

    /* Explosion hearts */
    .mini-heart {
        position: absolute;
        width: 14px;
        height: 14px;
        background: #ffd6e8;
        transform: rotate(45deg);
    }

    .mini-heart::before,
    .mini-heart::after {
        content: "";
        width: 14px;
        height: 14px;
        background: #ffd6e8;
        border-radius: 50%;
        position: absolute;
    }

    .mini-heart::before { top: -7px; }
    .mini-heart::after { left: -7px; }

    /* Firework spark */
    .spark {
        position: absolute;
        width: 5px;
        height: 5px;
        background: rgba(255,255,255,0.9);
        border-radius: 50%;
        animation: spark 1.5s ease-out forwards;
    }

    @keyframes spark {
        to { transform: scale(6); opacity: 0; }
    }

    .final-text {
        font-size: 2.2rem;
        margin-top: 15px;
        opacity: 0;
        animation: fadeIn 2s forwards;
        text-shadow: 0 0 15px rgba(255,255,255,0.9);
    }

    @keyframes fadeIn {
        to { opacity: 1; }
    }
</style>
</head>
<body>

<div class="container">
    <h1>Happy New Year ❤️</h1>
    <div id="countdown"></div>
    <div class="heart" id="bigHeart"></div>
    <div class="final-text" id="finalText"></div>
</div>

<script>
    /* Countdown */
    const target = new Date("Jan 1, 2026 00:00:00").getTime();
    const cd = document.getElementById("countdown");
    const finalText = document.getElementById("finalText");

    const timer = setInterval(() => {
        const now = new Date().getTime();
        const d = target - now;

        if (d <= 0) {
            clearInterval(timer);
            cd.innerHTML = "";
            finalText.innerHTML = "2025 онд надтай хамт байсанд баярлалаа! 💖\nхамтдаа олон зүйл үзэж туулла ясан ч их айсан жил байвдаа хамт одоо хүртэл ингээд байж байна\n уурлуулж гомдоосонд уудларай бодлоггүй үйлдэл их хийсэн гэвч чамдаа маш их хайртай шүү\nмуа муа муа";
            fireworks();
            return;
        }

        const days = Math.floor(d / (1000 * 60 * 60 * 24));
        const hours = Math.floor((d / (1000 * 60 * 60)) % 24);
        const mins = Math.floor((d / (1000 * 60)) % 60);
        const secs = Math.floor((d / 1000) % 60);

        cd.innerHTML = `${days}д ${hours}ц ${mins}м ${secs}с`;
    }, 1000);

    /* Fireworks */
    function fireworks() {
        setInterval(() => {
            const s = document.createElement("div");
            s.className = "spark";
            s.style.left = Math.random() * 100 + "vw";
            s.style.top = Math.random() * 100 + "vh";
            document.body.appendChild(s);
            setTimeout(() => s.remove(), 1500);
        }, 200);
    }

    /* Heart explosion on click */
    const bigHeart = document.getElementById("bigHeart");

    bigHeart.addEventListener("click", (e) => {
        const rect = bigHeart.getBoundingClientRect();
        const x = rect.left + rect.width / 2;
        const y = rect.top + rect.height / 2;

        for (let i = 0; i < 24; i++) {
            const h = document.createElement("div");
            h.className = "mini-heart";
            h.style.left = x + "px";
            h.style.top = y + "px";
            document.body.appendChild(h);

            const angle = Math.random() * Math.PI * 2;
            const distance = Math.random() * 140;

            h.animate([
                { transform: "translate(0,0) rotate(45deg)", opacity: 1 },
                { transform: `translate(${Math.cos(angle)*distance}px, ${Math.sin(angle)*distance}px) rotate(45deg)`, opacity: 0 }
            ], { duration: 1000, easing: "ease-out" });

            setTimeout(() => h.remove(), 1000);
        }
    });
</script>

</body>
</html>
