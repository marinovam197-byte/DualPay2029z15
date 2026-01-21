<!DOCTYPE html>
<html lang="bg">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>DualPay Party 🎉🌈💰</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Luckiest+Guy&family=Permanent+Marker&family=Orbitron:wght@900&display=swap" rel="stylesheet">
    <style>
        :root {
            --party-pink: #ff1493; /* Deep Pink */
            --party-blue: #00ffff; /* Aqua */
            --party-yellow: #ffff00; /* Yellow */
            --party-green: #39ff14; /* Neon Green */
            --party-orange: #ff4500; /* Orange Red */
            --rainbow-gradient: linear-gradient(45deg, var(--party-pink), var(--party-orange), var(--party-yellow), var(--party-green), var(--party-blue), var(--party-purple));
        }

        body {
            font-family: 'Permanent Marker', cursive;
            background: linear-gradient(-45deg, #FF6F61, #FFD180, #D1C4E9, #8C9EFF);
            background-size: 400% 400%;
            animation: gradient-bg 15s ease infinite;
            height: 100vh;
            overflow: hidden;
            display: flex;
            align-items: center;
            justify-content: center;
            color: #333; /* Default text for readability */
            position: relative;
        }

        @keyframes gradient-bg {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        /* Confetti Overlay */
        .confetti-overlay {
            position: fixed;
            top: 0; left: 0; width: 100%; height: 100%;
            pointer-events: none;
            overflow: hidden;
            z-index: 0;
        }
        .confetti {
            position: absolute;
            width: 10px; height: 10px;
            background-color: var(--party-pink); /* Default color */
            border-radius: 50%;
            animation: fall 5s linear infinite;
        }
        @keyframes fall {
            0% { transform: translateY(-10vh) rotate(0deg); opacity: 1; }
            100% { transform: translateY(100vh) rotate(720deg); opacity: 0.5; }
        }

        /* Main Card - Super Glitchy & Shiny */
        .party-card {
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(15px) saturate(150%);
            border-radius: 4rem;
            border: 5px dashed var(--party-yellow);
            box-shadow: 0 0 50px var(--party-pink), 0 0 80px var(--party-blue);
            padding: 2.5rem;
            position: relative;
            z-index: 10;
            animation: pulse-border 2s infinite alternate;
        }
        @keyframes pulse-border {
            0% { border-color: var(--party-yellow); box-shadow: 0 0 50px var(--party-pink), 0 0 80px var(--party-blue); }
            100% { border-color: var(--party-green); box-shadow: 0 0 60px var(--party-orange), 0 0 90px var(--party-purple); }
        }

        /* Rainbow Text Effect */
        .rainbow-text {
            background: var(--rainbow-gradient);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            font-family: 'Luckiest Guy', cursive;
            animation: rainbow-shift 3s ease infinite;
            display: inline-block; /* Essential for proper rendering */
        }
        @keyframes rainbow-shift {
            0% { filter: hue-rotate(0deg); }
            100% { filter: hue-rotate(360deg); }
        }

        /* Blinking Text */
        .blinking-text {
            animation: blink-animation 1s steps(5, start) infinite;
        }
        @keyframes blink-animation {
            to { visibility: hidden; }
        }

        /* Input Styles */
        input {
            border: 3px solid var(--party-blue) !important;
            border-radius: 1.5rem !important;
            padding: 1.25rem !important;
            background-color: rgba(255, 255, 255, 0.7) !important;
            color: #333 !important;
            font-family: 'Orbitron', sans-serif !important;
            font-size: 1.5rem !important;
            text-align: center;
        }
        input:focus {
            outline: none !important;
            border-color: var(--party-pink) !important;
            box-shadow: 0 0 20px var(--party-yellow);
        }

        select {
            border: 3px solid var(--party-yellow) !important;
            background-color: rgba(255, 255, 255, 0.8) !important;
            font-family: 'Orbitron', sans-serif !important;
            color: #333 !important;
        }

        /* Button Styles */
        .fun-button {
            font-family: 'Luckiest Guy', cursive;
            background: var(--rainbow-gradient);
            background-size: 200% auto;
            color: white;
            padding: 1rem 1.5rem;
            border-radius: 2rem;
            border: none;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
            transition: all 0.3s ease;
            animation: move-bg 2s linear infinite;
        }
        .fun-button:hover {
            transform: translateY(-3px) scale(1.05);
            box-shadow: 0 8px 20px rgba(0, 0, 0, 0.4);
        }
        .fun-button:active {
            transform: translateY(1px) scale(0.98);
        }
        @keyframes move-bg {
            to { background-position: 200% center; }
        }

        /* Result Display */
        .result-display {
            background: var(--rainbow-gradient);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            font-family: 'Orbitron', sans-serif;
            font-weight: 900;
            font-size: 4rem; /* Huge size */
            text-shadow: 5px 5px 10px rgba(0,0,0,0.3);
            animation: glitch 1.5s linear infinite;
        }

        @keyframes glitch {
            0% { transform: translateX(0); text-shadow: 5px 5px 10px rgba(0,0,0,0.3); }
            20% { transform: translateX(-2px) translateY(2px); text-shadow: -5px -5px 10px rgba(255,0,0,0.5); }
            40% { transform: translateX(2px) translateY(-2px); text-shadow: 5px -5px 10px rgba(0,255,0,0.5); }
            60% { transform: translateX(-3px) translateY(3px); text-shadow: -5px 5px 10px rgba(0,0,255,0.5); }
            80% { transform: translateX(3px) translateY(-3px); text-shadow: 5px 5px 10px rgba(255,255,0,0.5); }
            100% { transform: translateX(0); text-shadow: 5px 5px 10px rgba(0,0,0,0.3); }
        }

        .secondary-result {
            font-family: 'Permanent Marker', cursive;
            font-size: 1.2rem;
            color: #6a0dad; /* Deep Purple */
            animation: pulse-color 3s infinite alternate;
        }
        @keyframes pulse-color {
            0% { color: #6a0dad; }
            50% { color: var(--party-pink); }
            100% { color: #6a0dad; }
        }
    </style>
</head>
<body>

    <div id="confetti-container" class="confetti-overlay"></div>

    <main class="w-full max-w-md p-4">
        <div class="party-card mx-auto space-y-8">
            
            <div class="text-center">
                <h1 class="text-5xl font-black mb-4 leading-none">
                    <span class="rainbow-text">DualPay</span>
                    <span class="rainbow-text">Party!</span> 🎉
                </h1>
                <p class="text-xl text-gray-700 blinking-text">✨ Ресто калкулатор за теб! ✨</p>
            </div>

            <div class="space-y-6">
                <div>
                    <label class="block text-center text-xl font-bold mb-2">Сума за плащане 🤑</label>
                    <input type="number" id="billAmount" placeholder="0.00" 
                           class="w-full">
                    <div class="flex justify-center mt-3 gap-3">
                        <button onclick="setBillCurr('BGN')" id="btnBGN" class="fun-button text-lg">BGN 🇧🇬</button>
                        <button onclick="setBillCurr('EUR')" id="btnEUR" class="fun-button text-lg">EUR 🇪🇺</button>
                    </div>
                </div>

                <div class="grid grid-cols-2 gap-4">
                    <div>
                        <label class="block text-center text-sm font-bold text-gray-600 mb-1">Платено в лв 💰</label>
                        <input type="number" id="paidBGN" placeholder="0.00" class="w-full">
                    </div>
                    <div>
                        <label class="block text-center text-sm font-bold text-gray-600 mb-1">Платено в € 💸</label>
                        <input type="number" id="paidEUR" placeholder="0.00" class="w-full">
                    </div>
                </div>
            </div>

            <div class="text-center p-6 bg-yellow-100/50 rounded-3xl border-4 border-dashed border-purple-500">
                <p class="text-xl font-bold text-gray-800 mb-2 blinking-text">Твоето ресто е: 👇</p>
                <div id="changePrimary" class="result-display">0.00</div>
                <div id="changeSecondary" class="secondary-result mt-2">≈ 0.00</div>
                
                <div class="flex justify-center mt-6 gap-3">
                    <button onclick="setResCurr('BGN')" id="resBGN" class="fun-button text-xl px-6 py-3">В ЛЕВОВЕ! 🥳</button>
                    <button onclick="setResCurr('EUR')" id="resEUR" class="fun-button text-xl px-6 py-3">В ЕВРО! 🤑</button>
                </div>
            </div>

            <footer class="text-center pt-4">
                <p class="text-sm font-bold text-purple-700">💫 Курс: 1 EUR = 1.95583 BGN 💫</p>
                <p class="text-xs text-gray-500 mt-2">© ТВОЕТО ИМЕ - Изработено с любов и блясък! ✨💖</p>
            </footer>
        </div>
    </main>

    <script>
        const RATE = 1.95583;
        let billCurr = 'BGN';
        let resCurr = 'BGN';

        // Confetti generation
        const confettiContainer = document.getElementById('confetti-container');
        const colors = ['var(--party-pink)', 'var(--party-blue)', 'var(--party-yellow)', 'var(--party-green)', 'var(--party-orange)'];
        for (let i = 0; i < 50; i++) { // Generate 50 confetti pieces
            const confetti = document.createElement('div');
            confetti.className = 'confetti';
            confetti.style.left = Math.random() * 100 + 'vw';
            confetti.style.backgroundColor = colors[Math.floor(Math.random() * colors.length)];
            confetti.style.animationDelay = (Math.random() * -5) + 's'; // Stagger animations
            confettiContainer.appendChild(confetti);
        }


        const inputs = ['billAmount', 'paidBGN', 'paidEUR'];
        inputs.forEach(id => document.getElementById(id).addEventListener('input', calculate));

        function setBillCurr(c) {
            billCurr = c;
            const btnBGN = document.getElementById('btnBGN');
            const btnEUR = document.getElementById('btnEUR');

            btnBGN.style.background = c === 'BGN' ? 'var(--rainbow-gradient)' : 'linear-gradient(90deg, #ccc, #eee)';
            btnBGN.style.color = c === 'BGN' ? 'white' : '#333';
            btnBGN.style.borderColor = c === 'BGN' ? 'var(--party-blue)' : '#ccc';

            btnEUR.style.background = c === 'EUR' ? 'var(--rainbow-gradient)' : 'linear-gradient(90deg, #ccc, #eee)';
            btnEUR.style.color = c === 'EUR' ? 'white' : '#333';
            btnEUR.style.borderColor = c === 'EUR' ? 'var(--party-blue)' : '#ccc';

            calculate();
        }

        function setResCurr(c) {
            resCurr = c;
            const resBGN = document.getElementById('resBGN');
            const resEUR = document.getElementById('resEUR');

            resBGN.style.background = c === 'BGN' ? 'var(--rainbow-gradient)' : 'linear-gradient(90deg, #ccc, #eee)';
            resBGN.style.color = c === 'BGN' ? 'white' : '#333';
            resBGN.style.borderColor = c === 'BGN' ? 'var(--party-blue)' : '#ccc';


            resEUR.style.background = c === 'EUR' ? 'var(--rainbow-gradient)' : 'linear-gradient(90deg, #ccc, #eee)';
            resEUR.style.color = c === 'EUR' ? 'white' : '#333';
            resEUR.style.borderColor = c === 'EUR' ? 'var(--party-blue)' : '#ccc';


            calculate();
        }

        function calculate() {
            const bill = parseFloat(document.getElementById('billAmount').value) || 0;
            const pBGN = parseFloat(document.getElementById('paidBGN').value) || 0;
            const pEUR = parseFloat(document.getElementById('paidEUR').value) || 0;

            const billInBGN = billCurr === 'EUR' ? bill * RATE : bill;
            const totalPaidInBGN = pBGN + (pEUR * RATE);
            const changeInBGN = totalPaidInBGN - billInBGN;

            const primDisp = document.getElementById('changePrimary');
            const secDisp = document.getElementById('changeSecondary');

            if (changeInBGN < 0) {
                primDisp.innerHTML = "НЕ СТИГА! 😭";
                primDisp.style.color = 'var(--party-pink)'; // Make error text extra pink
                secDisp.innerHTML = "Дай още парички! 💸";
                secDisp.style.color = 'var(--party-orange)';
                primDisp.classList.remove('result-display'); // Remove glitch on error
                primDisp.style.fontSize = '3rem'; // Adjust font size for error message
            } else {
                primDisp.classList.add('result-display'); // Add glitch back
                primDisp.style.fontSize = '4rem'; // Restore font size
                if (resCurr === 'BGN') {
                    primDisp.innerHTML = changeInBGN.toFixed(2) + " лв 🇧🇬";
                    secDisp.innerHTML = "≈ " + (changeInBGN / RATE).toFixed(2) + " € 🇪🇺";
                } else {
                    primDisp.innerHTML = (changeInBGN / RATE).toFixed(2) + " € 🇪🇺";
                    secDisp.innerHTML = "≈ " + changeInBGN.toFixed(2) + " лв 🇧🇬";
                }
            }
        }

        // PWA (Inline Service Worker)
        if ('serviceWorker' in navigator) {
            const sw = `
                self.addEventListener('install', (event) => {
                    event.waitUntil(
                        caches.open('dualpay-party-v1').then((cache) => {
                            return cache.addAll(['./', 'index.html']); // Cache essential assets
                        })
                    );
                });
                self.addEventListener('fetch', (event) => {
                    event.respondWith(
                        caches.match(event.request).then((response) => {
                            return response || fetch(event.request);
                        })
                    );
                });
            `;
            const blob = new Blob([sw], {type: 'text/javascript'});
            navigator.serviceWorker.register(URL.createObjectURL(blob));
        }

        // Initial setup for buttons
        setBillCurr('BGN');
        setResCurr('BGN');
    </script>
</body>
</html>
