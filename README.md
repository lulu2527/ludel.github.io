
<html lang="fr">
<head>
<meta charset="UTF-8">
<title>Valentine 💖</title>

<style>
    body {
        margin: 0;
        height: 100vh;
        background: linear-gradient(135deg, #ff9a9e, #fad0c4);
        display: flex;
        justify-content: center;
        align-items: center;
        font-family: Arial, sans-serif;
        overflow: hidden;
    }

    .container {
        text-align: center;
        background: white;
        padding: 40px 50px;
        border-radius: 20px;
        box-shadow: 0 10px 30px rgba(0,0,0,0.2);
        position: relative;
        z-index: 2;
    }

    h1 {
        color: #e63946;
        margin-bottom: 30px;
    }

    .buttons {
        display: flex;
        gap: 30px;
        justify-content: center;
    }

    button {
        font-size: 20px;
        padding: 15px 35px;
        border-radius: 30px;
        border: none;
        cursor: pointer;
    }

    #yes {
        background: #e63946;
        color: white;
    }

    #no {
        background: #adb5bd;
        color: white;
        position: relative;
    }

    .heart {
        position: fixed;
        font-size: 24px;
        animation: float 3s linear forwards;
        z-index: 1;
    }

    @keyframes float {
        0% { transform: translateY(0); opacity: 1; }
        100% { transform: translateY(-300px); opacity: 0; }
    }
</style>
</head>

<body>

<div class="container" id="box">
    <h1>Veux-tu être ma Valentine ? 💘</h1>

    <div class="buttons">
        <button id="yes">Oui 💖</button>
        <button id="no">Non 💔</button>
    </div>
</div>

<script>
    const noBtn = document.getElementById("no");
    const yesBtn = document.getElementById("yes");
    const box = document.getElementById("box");

    let escaped = false;

    noBtn.addEventListener("mouseenter", () => {
        if (!escaped) {
            escaped = true;
            noBtn.style.position = "fixed";
        }

        const btnWidth = noBtn.offsetWidth;
        const btnHeight = noBtn.offsetHeight;

        const maxX = window.innerWidth - btnWidth - 10;
        const maxY = window.innerHeight - btnHeight - 10;

        const x = Math.random() * maxX;
        const y = Math.random() * maxY;

        noBtn.style.left = x + "px";
        noBtn.style.top = y + "px";
    });

    const messages = [
        "Je savais que tu dirais oui 😌💖",
        "Meilleure décision de ta journée 💘",
        "Et voilà… officiellement ma Valentine 🥰",
        "Mon cœur avait déjà signé le contrat ❤️",
        "Choix validé par le destin ✨",
        "J’avais parié sur toi 😉💖"
    ];

    yesBtn.addEventListener("click", () => {
        const message = messages[Math.floor(Math.random() * messages.length)];

        box.innerHTML = `
            <h1>${message}</h1>
            <img src="https://media.giphy.com/media/MDJ9IbxxvDUQM/giphy.gif" width="250">
        `;
        hearts();
    });

    function hearts() {
        for (let i = 0; i < 30; i++) {
            setTimeout(() => {
                const heart = document.createElement("div");
                heart.className = "heart";
                heart.textContent = "💖";
                heart.style.left = Math.random() * window.innerWidth + "px";
                heart.style.top = window.innerHeight + "px";
                document.body.appendChild(heart);

                setTimeout(() => heart.remove(), 3000);
            }, i * 100);
        }
    }
</script>

</body>
</html>
