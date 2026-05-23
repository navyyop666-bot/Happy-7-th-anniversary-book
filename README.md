# Happy 7 months anniversary my love 🫠🫠
<!DECOTYPE html>
<html lang="hi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>7 Months Love Book - Teena & Navu</title>
    <!-- Premium Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Cinzel:wght@500;700&family=Playfair+Display:ital,wght@0,400;0,700;1,400&family=Poppins:wght@300;400;600&display=swap" rel="stylesheet">
    
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Poppins', sans-serif;
            background: linear-gradient(135deg, #f5efe3 0%, #f3e9dc 100%);
            color: #2c2c2c;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            overflow: hidden;
            padding: 20px;
            perspective: 1500px; /* 3D effect ke liye zaroori hai */
        }

        /* Fireworks Canvas Container */
        #fireworksCanvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none; /* Taaki buttons click ho sakein */
            z-index: 999;
        }

        /* 3D Book Container */
        .book-container {
            position: relative;
            width: 450px;
            height: 600px;
            transition: transform 0.5s;
            transform-style: preserve-3d;
        }

        /* Individual Page Setup */
        .page {
            position: absolute;
            width: 100%;
            height: 100%;
            top: 0;
            left: 0;
            background-color: #fffdfa;
            box-shadow: 0 10px 30px rgba(0,0,0,0.08);
            transform-origin: left center;
            transition: transform 1.2s cubic-bezier(0.4, 0, 0.2, 1);
            transform-style: preserve-3d;
            z-index: 1;
            padding: 45px;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            border-left: 1px solid rgba(0,0,0,0.1);
            border-radius: 4px 12px 12px 4px;
            backface-visibility: hidden; /* Page palatne par peeche ka hussa chhupane ke liye */
        }

        /* Aesthetic Inner Border */
        .page::after {
            content: '';
            position: absolute;
            top: 15px;
            bottom: 15px;
            left: 15px;
            right: 15px;
            border: 1px solid #dfc3c3;
            pointer-events: none;
            border-radius: 4px;
        }

        /* Book Spine Effect */
        .page-spine {
            position: absolute;
            left: 0;
            top: 0;
            bottom: 0;
            width: 20px;
            background: linear-gradient(to right, rgba(0,0,0,0.15), transparent);
            z-index: 10;
            pointer-events: none;
        }

        /* Flipped State (Panna Palatna) */
        .page.flipped {
            transform: rotateY(-180deg);
            z-index: 0;
        }

        /* Z-Index Management for Layers */
        .page:nth-child(1) { z-index: 6; }
        .page:nth-child(2) { z-index: 5; }
        .page:nth-child(3) { z-index: 4; }
        .page:nth-child(4) { z-index: 3; }
        .page:nth-child(5) { z-index: 2; }
        .page:nth-child(6) { z-index: 1; }

        /* Typography */
        .magazine-header {
            font-family: 'Cinzel', serif;
            font-size: 0.8rem;
            letter-spacing: 4px;
            color: #8a7373;
            text-transform: uppercase;
            text-align: center;
        }

        .page-title {
            font-family: 'Playfair Display', serif;
            font-size: 2.2rem;
            color: #bc4749;
            font-style: italic;
            margin-bottom: 20px;
            text-align: center;
        }

        .page-content {
            font-size: 1.05rem;
            line-height: 1.8rem;
            color: #444;
            text-align: center;
            flex-grow: 1;
            display: flex;
            flex-direction: column;
            justify-content: center;
        }

        .page-footer {
            display: flex;
            justify-content: space-between;
            align-items: center;
            font-family: 'Cinzel', serif;
            font-size: 0.8rem;
            color: #a38181;
            z-index: 5;
        }

        /* --- PAGE 1: COVER --- */
        .cover-bg {
            background: linear-gradient(rgba(255, 255, 255, 0.88), rgba(255, 255, 255, 0.88)), url('https://picsum.photos/450/600?romantic') no-repeat center center/cover;
            border: 6px double #dfc3c3;
        }
        .cover-title {
            font-family: 'Playfair Display', serif;
            font-size: 3.2rem;
            font-style: italic;
            color: #bc4749;
            font-weight: 700;
            line-height: 3.8rem;
        }
        .issue-info {
            font-family: 'Cinzel', serif;
            border-top: 1px solid #2c2c2c;
            border-bottom: 1px solid #2c2c2c;
            padding: 8px 0;
            font-size: 0.8rem;
            letter-spacing: 3px;
            margin: 20px 0;
        }

        /* --- SHAYARI BOX --- */
        .shayari-box {
            background: #fff9f9;
            padding: 20px;
            border-left: 3px solid #bc4749;
            font-family: 'Playfair Display', serif;
            font-size: 1.15rem;
            font-style: italic;
            line-height: 2.2rem;
            color: #333;
            border-radius: 4px;
        }

        /* --- BUTTONS & CONTROLS --- */
        .action-btn {
            background-color: #2c2c2c;
            color: white;
            border: none;
            padding: 10px 25px;
            font-family: 'Cinzel', serif;
            font-size: 0.8rem;
            letter-spacing: 2px;
            cursor: pointer;
            transition: all 0.3s;
            margin-top: 15px;
        }
        .action-btn:hover { background-color: #bc4749; }
        
        .meter-bar {
            width: 100%;
            height: 6px;
            background: #eee;
            margin-top: 20px;
            border-radius: 3px;
            overflow: hidden;
            display: none;
        }
        .meter-fill {
            height: 100%;
            width: 0%;
            background: #bc4749;
            transition: width 2s ease-in-out;
        }

        .nav-btn {
            background: none;
            border: none;
            color: #bc4749;
            font-family: 'Cinzel', serif;
            font-size: 0.8rem;
            letter-spacing: 1px;
            cursor: pointer;
            font-weight: bold;
        }

        .book-controls {
            margin-top: 35px;
            display: flex;
            gap: 20px;
            z-index: 1000;
        }
        .control-arrow {
            background-color: white;
            border: 1px solid #dfc3c3;
            padding: 10px 25px;
            border-radius: 20px;
            font-family: 'Cinzel', serif;
            font-size: 0.8rem;
            cursor: pointer;
            box-shadow: 0 4px 10px rgba(0,0,0,0.05);
            transition: all 0.3s;
        }
        .control-arrow:hover {
            background-color: #bc4749;
            color: white;
        }

        /* --- BACK COVER --- */
        .supreme-court-badge {
            font-family: 'Cinzel', serif;
            font-size: 1.2rem;
            color: #bc4749;
            letter-spacing: 3px;
            font-weight: 700;
            border-top: 1px solid #dfc3c3;
            border-bottom: 1px solid #dfc3c3;
            padding: 10px 0;
            margin: 20px 0;
        }
    </style>
</head>
<body>

    <!-- Fireworks Canvas Background -->
    <canvas id="fireworksCanvas"></canvas>

    <!-- THE 3D BOOK CONTAINER -->
    <div class="book-container">
        
        <!-- PAGE 1: COVER -->
        <div class="page cover-bg" id="p1">
            <div class="page-spine"></div>
            <div class="magazine-header">Special Anniversary Edition</div>
            <div class="page-content">
                <h1 class="cover-title">The 7 Months<br>Love Book</h1>
                <div class="issue-info">ISSUE NO. 07 • TEENA SONI</div>
                <p style="font-size: 0.95rem; color: #666; font-style: italic;">Aapke liye Navu ki ek choti si digital bhent.</p>
            </div>
            <div class="page-footer">
                <span>VOL I</span>
                <button class="nav-btn" onclick="turnPage(1)">Open Book →</button>
            </div>
        </div>

        <!-- PAGE 2: CHAPTER 1 -->
        <div class="page" id="p2">
            <div class="page-spine"></div>
            <div class="magazine-header">Chapter 1: Initial Days</div>
            <h2 class="page-title">Haseen Shuruat</h2>
            <div class="page-content">
                <p>Aapke sath bitaye in 7 mahino ka ek-ek pal mere dil mein mehfooz hai. Jab aap pehli baar meri zindagi mein aayi thi, tab mujhe nahi pata tha ki aap meri poori duniya ban jayengi.</p>
                <p style="margin-top: 15px;">Aapki baatein, aapki khubsoorat muskurahat aur aapka har pal meri fikr karna... mere liye sabse badi khushi hai.</p>
            </div>
            <div class="page-footer">
                <button class="nav-btn" onclick="backPage(1)">← Back</button>
                <span>PAGE 02</span>
                <button class="nav-btn" onclick="turnPage(2)">Next →</button>
            </div>
        </div>

        <!-- PAGE 3: SHAYARI -->
        <div class="page" id="p3">
            <div class="page-spine"></div>
            <div class="magazine-header">Chapter 2: Pure Romance</div>
            <h2 class="page-title">Sirf Aapke Liye</h2>
            <div class="page-content">
                <div class="shayari-box">
                    "Aapki muskurahat se shuru hoti hai meri har subah,<br>
                    Aap sath ho toh har manzil lagti hai aasan.<br><br>
                    7 mahine ka yeh safar toh bas ek shuruat hai,<br>
                    Aap hi toh ho meri duniya, meri jaan."
                </div>
            </div>
            <div class="page-footer">
                <button class="nav-btn" onclick="backPage(2)">← Back</button>
                <span>PAGE 03</span>
                <button class="nav-btn" onclick="turnPage(3)">Next →</button>
            </div>
        </div>

        <!-- PAGE 4: INTERACTIVE INDEX -->
        <div class="page" id="p4">
            <div class="page-spine"></div>
            <div class="magazine-header">Chapter 3: Interactive Index</div>
            <h2 class="page-title">Compatibility Test</h2>
            <div class="page-content">
                <p style="font-size: 0.95rem; color: #555;">Chaliye is magazine ke zariye hamare rishte ki sachaai aur gehraai ka digital analysis karte hain.</p>
                <div>
                    <button class="action-btn" onclick="startMeter()">Analyze Bond</button>
                    <div class="meter-bar" id="mBar">
                        <div class="meter-fill" id="mFill"></div>
                    </div>
                    <p id="mResult" style="font-family: 'Playfair Display', serif; font-size: 1.15rem; margin-top: 15px; color: #bc4749; font-style: italic;"></p>
                </div>
            </div>
            <div class="page-footer">
                <button class="nav-btn" onclick="backPage(3)">← Back</button>
                <span>PAGE 04</span>
                <button class="nav-btn" onclick="turnPage(4)">Next →</button>
            </div>
        </div>

        <!-- PAGE 5: THE VOW -->
        <div class="page" id="p5">
            <div class="page-spine"></div>
            <div class="magazine-header">Chapter 4: The Vow</div>
            <h2 class="page-title">Mera Waada</h2>
            <div class="page-content">
                <p>Navu ka aap se waada hai... halat chahe jaise bhi ho, main hamesha aapka sath nibhaunga. Aapki har khushi meri khushi hogi aur aapka har gham mera gham.</p>
                <p style="margin-top: 15px; font-weight: 600; color: #bc4749;">7 mahine toh bas ek pyara sa trailer hain, humari poori zindagi ki khubsoorat film abhi baaki hai!</p>
            </div>
            <div class="page-footer">
                <button class="nav-btn" onclick="backPage(4)">← Back</button>
                <span>PAGE 05</span>
                <button class="nav-btn" onclick="turnPage(5)">Final Page →</button>
            </div>
        </div>

        <!-- PAGE 6: BACK COVER (FIREWORKS TRIGGER) -->
        <div class="page" id="p6">
            <div class="page-spine"></div>
            <div class="magazine-header">The Back Cover</div>
            <div class="page-content">
                <h1 style="font-family: 'Playfair Display', serif; font-size: 2.5rem; color: #2c2c2c; margin-bottom: 10px;">I Love You Teena</h1>
                <p style="font-size: 1rem; color: #555;">Aap kal bhi meri thi, aaj bhi meri ho aur hamesha meri rahogi.</p>
                
                <div class="supreme-court-badge">✨ MY SUPREME COURT ✨</div>
                
                <p style="font-family: 'Playfair Display', serif; font-style: italic; color: #777;">
                    Hamesha ke liye sirf aapka,<br>
                    <strong style="color: #bc4749; font-size: 1.3rem; font-family: 'Cinzel', serif;">Navu</strong>
                </p>
            </div>
            <div class="page-footer">
                <button class="nav-btn" onclick="backPage(5)">← Back</button>
                <span>THE END</span>
                <span></span>
            </div>
        </div>

    </div>

    <!-- Outer Controls -->
    <div class="book-controls">
        <button class="control-arrow" id="prevBtn" onclick="triggerPrev()" style="display: none;">← Previous Page</button>
        <button class="control-arrow" id="nextBtn" onclick="triggerNext()">Next Page →</button>
    </div>

    <script>
        let currentOpenPage = 1;
        const maxPages = 6;
        let fireworksActive = false;

        // Panna Palatne ki 3D Logic
        function turnPage(pageIndex) {
            document.getElementById(`p${pageIndex}`).classList.add('flipped');
            currentOpenPage = pageIndex + 1;
            checkFireworksTrigger();
            toggleOuterButtons();
        }

        function backPage(pageIndex) {
            document.getElementById(`p${pageIndex}`).classList.remove('flipped');
            currentOpenPage = pageIndex;
            checkFireworksTrigger();
            toggleOuterButtons();
        }

        // External Arrow Controls Connection
        function triggerNext() {
            if(currentOpenPage < maxPages) {
                turnPage(currentOpenPage);
            }
        }

        function triggerPrev() {
            if(currentOpenPage > 1) {
                backPage(currentOpenPage - 1);
            }
        }

        function toggleOuterButtons() {
            document.getElementById('prevBtn').style.display = currentOpenPage > 1 ? 'block' : 'none';
            document.getElementById('nextBtn').style.display = currentOpenPage < maxPages ? 'block' : 'none';
        }

        function checkFireworksTrigger() {
            if (currentOpenPage === 6) {
                fireworksActive = true;
                // Click setting instructions alert text removal for pure integration
            } else {
                fireworksActive = false;
            }
        }

        // Love Index Game
        function startMeter() {
            const bar = document.getElementById('mBar');
            const fill = document.getElementById('mFill');
            const result = document.getElementById('mResult');
            bar.style.display = 'block';
            fill.style.width = '0%';
            result.innerHTML = "Analyzing relationship bonds... ✨";
            setTimeout(() => fill.style.width = '100%', 100);
            setTimeout(() => {
                result.innerHTML = "💝 Result: 100% Infinite Love! Humara Rishta Sabse Bemisaal Hai! 💝";
            }, 2100);
        }

        // --- ULTRA HIGH PERFORMANCE FIREWORKS ENGINE ---
        const canvas = document.getElementById('fireworksCanvas');
        const ctx = canvas.getContext('2d');

        function resizeCanvas() {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
        }
        window.addEventListener('resize', resizeCanvas);
        resizeCanvas();

        class Particle {
            constructor(x, y, color) {
                this.x = x;
                this.y = y;
                this.color = color;
                this.radius = Math.random() * 3 + 1;
                this.velocity = {
                    x: (Math.random() - 0.5) * 8,
                    y: (Math.random() - 0.5) * 8
                };
                this.alpha = 1;
                this.gravity = 0.05;
            }
            draw() {
                ctx.save();
                ctx.globalAlpha = this.alpha;
                ctx.beginPath();
                ctx.arc(this.x, this.y, this.radius, 0, Math.PI * 2, false);
                ctx.fillStyle = this.color;
                ctx.fill();
                ctx.restore();
            }
            update() {
                this.velocity.y += this.gravity;
                this.x += this.velocity.x;
                this.y += this.velocity.y;
                this.alpha -= 0.015;
            }
        }

        let particles = [];
        const colors = ['#ff7675', '#fd79a8', '#e84393', '#00b894', '#0984e3', '#f1c40f', '#e67e22'];

        function spawnFirework(x, y) {
            const particleCount = 60;
            const randomColor = colors[Math.floor(Math.random() * colors.length)];
            for (let i = 0; i < particleCount; i++) {
                particles.push(new Particle(x, y, randomColor));
            }
        }

        // Automatically launch random fireworks if active
        setInterval(() => {
            if (fireworksActive) {
                const randomX = Math.random() * canvas.width;
                const randomY = Math.random() * (canvas.height * 0.6);
                spawnFirework(randomX, randomY);
            }
        }, 600);

        // Screen intersection click trigger for manual fireworks
        window.addEventListener('click', (e) => {
            if (fireworksActive) {
                spawnFirework(e.clientX, e.clientY);
            }
        });

        function animate() {
            requestAnimationFrame(animate);
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            
            particles.forEach((particle, index) => {
                if (particle.alpha > 0) {
                    particle.update();
                    particle.draw();
                } else {
                    particles.splice(index, 1);
                }
            });
        }
        animate();
    </script>
</body>
</html>
