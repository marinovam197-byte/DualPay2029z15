<!DOCTYPE html>
<html lang="bg">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>DualPay Ultra Color</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Comfortaa:wght@700&family=Montserrat:wght@400;900&display=swap" rel="stylesheet">
    <style>
        :root {
            --neon-pink: #ff00ff;
            --neon-blue: #00f2ff;
            --neon-purple: #7000ff;
        }

        body {
            font-family: 'Montserrat', sans-serif;
            background: #0f172a;
            height: 100vh;
            overflow: hidden;
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 0;
        }

        /* Анимиран течен фон */
        .blob-bg {
            position: fixed;
            top: 0; left: 0; width: 100%; height: 100%;
            background: linear-gradient(45deg, #0f172a, #1e1b4b);
            z-index: -1;
        }

        .blob {
            position: absolute;
            width: 300px; height: 300px;
            background: linear-gradient(to right, var(--neon-pink), var(--neon-purple));
            filter: blur(80px);
            border-radius: 50%;
            opacity: 0.4;
            animation: move 20s infinite alternate;
        }

        @keyframes move {
            from { transform: translate(-10%, -10%) rotate(0deg); }
            to { transform: translate(110%, 110%) rotate(360deg); }
        }

        /* Динамична мрежа */
        .grid-overlay {
            position: fixed;
            inset: 0;
            background-image: linear-gradient(to right, rgba(0,242,255,0.05) 1px, transparent 1px),
                              linear-gradient(to bottom, rgba(0,242,255,0.05) 1px, transparent 1px);
            background-size: 40px 40px;
            z-index: -1;
        }

        /* Стъклена карта с дъга */
        .glass-card {
            background: rgba(255, 255, 255, 0.05);
            backdrop-filter: blur(25px);
            border: 2px solid rgba(255, 255, 255, 0.1);
            border-radius: 3rem;
            box-shadow: 0 0 40px rgba(0,0,0,0.5), inset 0 0 20px rgba(255,255,255,0.05);
            position: relative;
            overflow: hidden;
        }

        .glass-card::before {
            content: '';
            position: absolute;
            top: -50%; left: -50%; width: 200%; height: 200%;
            background: conic-gradient(transparent, var(--neon-blue), var(--neon-pink), transparent);
            animation: rotate-border 6s linear infinite;
            z-index: -1;
            opacity: 0.3;
        }

        @keyframes rotate-border {
            100% { transform: rotate(360deg); }
        }

        /* Цветни текстове */
        .text-neon {
            color: var(--neon-blue);
            text-shadow: 0 0 10px rgba(0,242,255,0.5);
        }

        .gradient-btn {
            background: linear-gradient(90deg, var(--neon-blue), var(--neon-purple));
            transition: all 0.3s ease;
        }

        .gradient-btn:active { transform: scale(0.95); filter: hue-rotate(45deg); }

        input {
            background: rgba(255,255,255,0.05) !important;
            border: 1px solid rgba(255,255,255,0.1) !important;
            color: white !important;
            text-align: center;
        }

        .comfortaa { font-family: 'Comfortaa', cursive; }
    </style>
</head>
<body>

    <div class="blob-bg">
        <div class="blob" style="top: 10%; left: 10%;"></div>
        <div class="blob" style="bottom: 10%; right: 10%; animation-delay: -5s; background: var(--neon-blue);"></div>
    </div>
    <div class="grid-overlay"></div>

    <main class="w-full max-w-sm p-4">
        <div class="glass-card p-8 space-y-6">
            
            <div class="text-center">
                <div class="inline-block p-4 rounded-3xl bg-white/10 mb-4">
                    <span class="comfortaa text-3xl font-bold text-white tracking-tighter">€ <span class="text-neon">⇄</span> лв</span>
                </div>
                <h1 class="comfortaa text-2xl font-black text-white uppercase tracking-widest">DualPay <span class="text-neon">Ultra</span></h1>
            </div>

            <div class="space-y-4">
                <div>
                    <input type="number" id="billAmount" placeholder="СУМА ЗА ПЛАЩАНЕ" 
                           class="w-full p-5 rounded-2xl text-xl font-bold placeholder:text-gray-500 focus:ring-2 ring-cyan-400 outline-none transition-all">
                    <div class="flex justify-center mt-2 gap-2">
                        <button onclick="setBillCurr('BGN')" id="btnBGN" class="px-4 py-1 rounded-full text-xs font-bold bg-cyan-500 text-black">BGN</button>
                        <button onclick="setBillCurr('EUR')" id="btnEUR" class="px-4 py-1 rounded-full text-xs font-bold bg-white/10 text-white">EUR</button>
                    </div>
                </div>

                <div class="grid grid-cols-2 gap-3">
                    <input type="number" id="paidBGN" placeholder="В лв" class="p-4 rounded-2xl font-bold">
                    <input type="number" id="paidEUR" placeholder="В €" class="p-4 rounded-2xl font-bold">
                </div>
            </div>

            <div class="bg-black/20 rounded-[2rem] p-6 text-center border border-white/5">
                <div id="resLabel" class="text-[10px] font-black text-gray-400 uppercase tracking-[0.3em] mb-2">Ресто за връщане</div>
                <div id="changePrimary" class="text-5xl font-black text-white mb-1">0.00</div>
                <div id="changeSecondary" class="text-sm font-bold text-neon opacity-70">≈ 0.00</div>
                
                <div class="flex mt-4 p-1 bg-white/5 rounded-xl">
                    <button onclick="setResCurr('BGN')" id="resBGN" class="flex-1 py-2 rounded-lg text-[10px] font-bold bg-white text-black transition-all">В ЛЕВОВЕ</button>
                    <button onclick="setResCurr('EUR')" id="resEUR" class="flex-1 py-2 rounded-lg text-[10px] font-bold text-white transition-all">В ЕВРО</button>
                </div>
            </div>

            <footer class="text-center pt-2">
                <p class="text-[9px] text-cyan-400 font-bold tracking-widest uppercase opacity-50">Курс: 1.95583</p>
                <p class="text-[10px] text-white/30 mt-2">© ТВОЕТО ИМЕ</p>
            </footer>
        </div>
    </main>

    <script>
        const RATE = 1.95583;
        let billCurr = 'BGN';
        let resCurr = 'BGN';

        const inputs = ['billAmount', 'paidBGN', 'paidEUR'];
        inputs.forEach(id => document.getElementById(id).addEventListener('input', calculate));

        function setBillCurr(c) {
            billCurr = c;
            document.getElementById('btnBGN').className = c === 'BGN' ? 'px-4 py-1 rounded-full text-xs font-bold bg-cyan-400 text-black' : 'px-4 py-1 rounded-full text-xs font-bold bg-white/10 text-white';
            document.getElementById('btnEUR').className = c === 'EUR' ? 'px-4 py-1 rounded-full text-xs font-bold bg-cyan-400 text-black' : 'px-4 py-1 rounded-full text-xs font-bold bg-white/10 text-white';
            calculate();
        }

        function setResCurr(c) {
            resCurr = c;
            document.getElementById('resBGN').className = c === 'BGN' ? 'flex-1 py-2 rounded-lg text-[10px] font-bold bg-white text-black' : 'flex-1 py-2 rounded-lg text-[10px] font-bold text-white';
            document.getElementById('resEUR').className = c === 'EUR' ? 'flex-1 py-2 rounded-lg text-[10px] font-bold bg-white text-black' : 'flex-1 py-2 rounded-lg text-[10px] font-bold text-white';
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
                primDisp.innerText = "---";
                primDisp.style.color = "#ff4444";
                secDisp.innerText = "Недостатъчна сума";
            } else {
                primDisp.style.color = "white";
                if (resCurr === 'BGN') {
                    primDisp.innerText = changeInBGN.toFixed(2) + " лв";
                    secDisp.innerText = "≈ " + (changeInBGN / RATE).toFixed(2) + " €";
                } else {
                    primDisp.innerText = (changeInBGN / RATE).toFixed(2) + " €";
                    secDisp.innerText = "≈ " + changeInBGN.toFixed(2) + " лв";
                }
            }
        }

        // PWA
        if ('serviceWorker' in navigator) {
            const sw = `self.addEventListener('fetch', e => e.respondWith(caches.match(e.request).then(r => r || fetch(e.request))));`;
            const blob = new Blob([sw], {type: 'text/javascript'});
            navigator.serviceWorker.register(URL.createObjectURL(blob));
        }
    </script>
</body>
</html>
