<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Flappy Bird Interactive Arcade</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Google Font - Press Start 2P for Arcade Feel -->
    <link href="https://fonts.googleapis.com/css2?family=Press+Start+2P&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Press Start 2P', cursive;
            touch-action: manipulation;
            user-select: none;
            -webkit-user-select: none;
        }
        .arcade-shadow {
            box-shadow: 0 10px 25px -5px rgba(0, 0, 0, 0.5), 0 8px 10px -6px rgba(0, 0, 0, 0.3);
        }
        .pixel-border {
            border-style: solid;
            border-width: 4px;
            border-color: #000;
        }
    </style>
</head>
<body class="bg-slate-900 text-white min-h-screen flex flex-col items-center justify-center p-2 sm:p-4 overflow-hidden">

    <!-- Game Container -->
    <div class="relative w-full max-w-md flex flex-col items-center">
        <!-- Header -->
        <div class="w-full flex justify-between items-center mb-3 px-2">
            <h1 class="text-xl sm:text-2xl text-yellow-400 font-bold tracking-wider drop-shadow-md">FLAPPY BIRD</h1>
            <button id="soundToggle" class="bg-slate-800 hover:bg-slate-700 text-yellow-400 p-2 rounded-lg border-2 border-yellow-400 text-xs transition duration-200 focus:outline-none">
                🔊 SFX: ON
            </button>
        </div>

        <!-- Canvas Container -->
        <div class="relative w-full aspect-[2/3] max-h-[75vh] bg-sky-300 rounded-xl overflow-hidden pixel-border arcade-shadow">
            <canvas id="gameCanvas" class="w-full h-full block cursor-pointer"></canvas>

            <!-- Start / Ready Overlay -->
            <div id="startOverlay" class="absolute inset-0 bg-black/40 flex flex-col items-center justify-center p-4 text-center z-10 transition-opacity duration-300">
                <div class="bg-slate-900/90 p-6 rounded-2xl border-4 border-yellow-400 max-w-[85%] flex flex-col items-center gap-4 shadow-2xl">
                    <div class="text-yellow-400 text-sm sm:text-base leading-relaxed animate-pulse">
                        PETUNJUK MAIN
                    </div>
                    <div class="text-[10px] sm:text-xs text-slate-200 space-y-2 text-left">
                        <p>🔹 <span class="text-yellow-300">Spasi / Klik / Tap</span> : Terbang Ke Atas</p>
                        <p>🔹 Hindari Pipa Hijau & Tanah</p>
                        <p>🔹 Lewati Pipa Untuk Dapat Skor</p>
                    </div>
                    <button id="startButton" class="mt-2 bg-emerald-500 hover:bg-emerald-400 text-slate-950 font-bold py-3 px-6 rounded-xl border-b-4 border-emerald-700 active:border-b-0 active:translate-y-1 text-xs tracking-wider transition-all">
                        MULAIMAIN!
                    </button>
                </div>
            </div>

            <!-- Game Over Overlay -->
            <div id="gameOverOverlay" class="hidden absolute inset-0 bg-black/60 flex flex-col items-center justify-center p-4 text-center z-20">
                <div class="bg-slate-900/95 p-6 rounded-2xl border-4 border-red-500 max-w-[85%] w-full flex flex-col items-center gap-4 shadow-2xl">
                    <h2 class="text-red-500 text-xl font-bold tracking-widest animate-bounce">GAME OVER</h2>
                    
                    <div class="w-full bg-slate-800/80 p-4 rounded-xl border-2 border-slate-700 space-y-3 text-xs">
                        <div class="flex justify-between items-center">
                            <span class="text-slate-400">SKOR:</span>
                            <span id="finalScore" class="text-yellow-400 text-base font-bold">0</span>
                        </div>
                        <div class="flex justify-between items-center">
                            <span class="text-slate-400">SKOR TERTINGGI:</span>
                            <span id="highScoreDisplay" class="text-emerald-400 text-base font-bold">0</span>
                        </div>
                    </div>

                    <button id="restartButton" class="w-full bg-yellow-400 hover:bg-yellow-300 text-slate-950 font-bold py-3 px-6 rounded-xl border-b-4 border-yellow-600 active:border-b-0 active:translate-y-1 text-xs tracking-wider transition-all">
                        MAIN LAGI 🔄
                    </button>
                </div>
            </div>
        </div>

        <!-- Controls Footer Hint -->
        <div class="mt-3 text-[10px] text-slate-400 text-center">
            Tekan <kbd class="px-1.5 py-0.5 bg-slate-800 border border-slate-700 rounded text-slate-300">Spasi</kbd> atau Tap Layar Untuk Melompat
        </div>
    </div>

    <script>
        // --- Game Setup & Variables ---
        const canvas = document.getElementById('gameCanvas');
        const ctx = canvas.getContext('2d');

        // Overlays & UI
        const startOverlay = document.getElementById('startOverlay');
        const gameOverOverlay = document.getElementById('gameOverOverlay');
        const startButton = document.getElementById('startButton');
        const restartButton = document.getElementById('restartButton');
        const finalScoreEl = document.getElementById('finalScore');
        const highScoreDisplayEl = document.getElementById('highScoreDisplay');
        const soundToggleBtn = document.getElementById('soundToggle');

        // Internal Canvas Resolution
        const CANVAS_WIDTH = 360;
        const CANVAS_HEIGHT = 540;
        canvas.width = CANVAS_WIDTH;
        canvas.height = CANVAS_HEIGHT;

        // Audio System (Synthesized via Web Audio API)
        let audioCtx = null;
        let soundEnabled = true;

        function initAudio() {
            if (!audioCtx) {
                const AudioContext = window.AudioContext || window.webkitAudioContext;
                audioCtx = new AudioContext();
            }
        }

        function playSound(type) {
            if (!soundEnabled) return;
            initAudio();
            if (audioCtx.state === 'suspended') {
                audioCtx.resume();
            }

            const osc = audioCtx.createOscillator();
            const gain = audioCtx.createGain();
            osc.connect(gain);
            gain.connect(audioCtx.destination);

            const now = audioCtx.currentTime;

            if (type === 'flap') {
                osc.type = 'sine';
                osc.frequency.setValueAtTime(400, now);
                osc.frequency.exponentialRampToValueAtTime(800, now + 0.1);
                gain.gain.setValueAtTime(0.3, now);
                gain.gain.exponentialRampToValueAtTime(0.01, now + 0.1);
                osc.start(now);
                osc.stop(now + 0.1);
            } else if (type === 'score') {
                osc.type = 'triangle';
                osc.frequency.setValueAtTime(523.25, now); // C5
                osc.frequency.setValueAtTime(659.25, now + 0.08); // E5
                gain.gain.setValueAtTime(0.2, now);
                gain.gain.exponentialRampToValueAtTime(0.01, now + 0.25);
                osc.start(now);
                osc.stop(now + 0.25);
            } else if (type === 'hit') {
                osc.type = 'sawtooth';
                osc.frequency.setValueAtTime(150, now);
                osc.frequency.exponentialRampToValueAtTime(40, now + 0.2);
                gain.gain.setValueAtTime(0.4, now);
                gain.gain.exponentialRampToValueAtTime(0.01, now + 0.2);
                osc.start(now);
                osc.stop(now + 0.2);
            }
        }

        // --- Game State Variables ---
        let gameState = 'START'; // 'START', 'PLAYING', 'GAMEOVER'
        let score = 0;
        let highScore = localStorage.getItem('flappy_high_score') || 0;
        let frames = 0;

        // Bird Settings
        const bird = {
            x: 60,
            y: 200,
            radius: 14,
            gravity: 0.35,
            jump: -6.8,
            velocity: 0,
            rotation: 0,
            wingAngle: 0,
            wingSpeed: 0.2,

            draw() {
                ctx.save();
                ctx.translate(this.x, this.y);
                
                // Calculate Rotation based on velocity
                this.rotation = Math.min(Math.PI / 4, Math.max(-Math.PI / 4, (this.velocity * 4) * Math.PI / 180));
                ctx.rotate(this.rotation);

                // Body (Yellow)
                ctx.fillStyle = '#facc15';
                ctx.beginPath();
                ctx.arc(0, 0, this.radius, 0, Math.PI * 2);
                ctx.fill();
                ctx.lineWidth = 2;
                ctx.strokeStyle = '#000';
                ctx.stroke();

                // Eye (White & Pupil)
                ctx.fillStyle = '#ffffff';
                ctx.beginPath();
                ctx.arc(6, -4, 5, 0, Math.PI * 2);
                ctx.fill();
                ctx.stroke();

                ctx.fillStyle = '#000000';
                ctx.beginPath();
                ctx.arc(8, -4, 2, 0, Math.PI * 2);
                ctx.fill();

                // Beak (Orange)
                ctx.fillStyle = '#f97316';
                ctx.beginPath();
                ctx.moveTo(8, 2);
                ctx.lineTo(18, 5);
                ctx.lineTo(8, 10);
                ctx.closePath();
                ctx.fill();
                ctx.stroke();

                // Wing (White/Light Yellow Animation)
                ctx.fillStyle = '#fef08a';
                ctx.beginPath();
                const wingY = Math.sin(this.wingAngle) * 4;
                ctx.ellipse(-4, wingY, 7, 4, 0, 0, Math.PI * 2);
                ctx.fill();
                ctx.stroke();

                ctx.restore();
            },

            update() {
                if (gameState === 'PLAYING') {
                    this.velocity += this.gravity;
                    this.y += this.velocity;
                    this.wingAngle += this.wingSpeed;

                    // Ground collision
                    if (this.y + this.radius >= CANVAS_HEIGHT - 60) {
                        this.y = CANVAS_HEIGHT - 60 - this.radius;
                        triggerGameOver();
                    }

                    // Ceiling collision limit
                    if (this.y - this.radius <= 0) {
                        this.y = this.radius;
                        this.velocity = 0;
                    }
                } else if (gameState === 'START') {
                    // Hovering effect before game starts
                    this.y = 200 + Math.sin(frames * 0.08) * 6;
                    this.wingAngle += 0.1;
                }
            },

            flap() {
                this.velocity = this.jump;
                playSound('flap');
            },

            reset() {
                this.y = 200;
                this.velocity = 0;
                this.rotation = 0;
            }
        };

        // Pipes System
        const pipes = {
            list: [],
            width: 52,
            gap: 130,
            spawnRate: 100,

            draw() {
                this.list.forEach(pipe => {
                    // Top Pipe
                    ctx.fillStyle = '#22c55e'; // Green 500
                    ctx.fillRect(pipe.x, 0, this.width, pipe.topHeight);
                    ctx.strokeStyle = '#000';
                    ctx.lineWidth = 2;
                    ctx.strokeRect(pipe.x, 0, this.width, pipe.topHeight);

                    // Top Pipe Cap
                    ctx.fillStyle = '#16a34a'; // Darker rim
                    ctx.fillRect(pipe.x - 3, pipe.topHeight - 20, this.width + 6, 20);
                    ctx.strokeRect(pipe.x - 3, pipe.topHeight - 20, this.width + 6, 20);

                    // Bottom Pipe
                    const bottomPipeY = pipe.topHeight + this.gap;
                    const bottomPipeHeight = CANVAS_HEIGHT - 60 - bottomPipeY;
                    ctx.fillStyle = '#22c55e';
                    ctx.fillRect(pipe.x, bottomPipeY, this.width, bottomPipeHeight);
                    ctx.strokeRect(pipe.x, bottomPipeY, this.width, bottomPipeHeight);

                    // Bottom Pipe Cap
                    ctx.fillStyle = '#16a34a';
                    ctx.fillRect(pipe.x - 3, bottomPipeY, this.width + 6, 20);
                    ctx.strokeRect(pipe.x - 3, bottomPipeY, this.width + 6, 20);
                });
            },

            update() {
                if (gameState !== 'PLAYING') return;

                // Spawn Pipes
                if (frames % this.spawnRate === 0) {
                    const minHeight = 40;
                    const maxHeight = CANVAS_HEIGHT - 60 - this.gap - minHeight;
                    const topHeight = Math.floor(Math.random() * (maxHeight - minHeight + 1)) + minHeight;
                    
                    this.list.push({
                        x: CANVAS_WIDTH,
                        topHeight: topHeight,
                        passed: false
                    });
                }

                // Move Pipes
                this.list.forEach((pipe, index) => {
                    pipe.x -= 2;

                    // Check for score pass
                    if (!pipe.passed && pipe.x + this.width < bird.x) {
                        pipe.passed = true;
                        score++;
                        playSound('score');
                    }

                    // Collision Detection
                    const birdBox = {
                        left: bird.x - bird.radius + 3,
                        right: bird.x + bird.radius - 3,
                        top: bird.y - bird.radius + 3,
                        bottom: bird.y + bird.radius - 3
                    };

                    const topPipeBox = { left: pipe.x, right: pipe.x + this.width, top: 0, bottom: pipe.topHeight };
                    const bottomPipeBox = { left: pipe.x, right: pipe.x + this.width, top: pipe.topHeight + this.gap, bottom: CANVAS_HEIGHT - 60 };

                    if (
                        (birdBox.right > topPipeBox.left && birdBox.left < topPipeBox.right && birdBox.top < topPipeBox.bottom) ||
                        (birdBox.right > bottomPipeBox.left && birdBox.left < bottomPipeBox.right && birdBox.bottom > bottomPipeBox.top)
                    ) {
                        playSound('hit');
                        triggerGameOver();
                    }
                });

                // Remove offscreen pipes
                if (this.list.length > 0 && this.list[0].x < -this.width - 10) {
                    this.list.shift();
                }
            },

            reset() {
                this.list = [];
            }
        };

        // Background & Ground Scenery
        let groundOffset = 0;
        function drawBackground() {
            // Sky Gradient
            const skyGradient = ctx.createLinearGradient(0, 0, 0, CANVAS_HEIGHT - 60);
            skyGradient.addColorStop(0, '#38bdf8'); // Sky 400
            skyGradient.addColorStop(1, '#bae6fd'); // Sky 200
            ctx.fillStyle = skyGradient;
            ctx.fillRect(0, 0, CANVAS_WIDTH, CANVAS_HEIGHT - 60);

            // Distant Clouds
            ctx.fillStyle = 'rgba(255, 255, 255, 0.7)';
            ctx.beginPath();
            ctx.arc(80, 100, 25, 0, Math.PI * 2);
            ctx.arc(110, 95, 30, 0, Math.PI * 2);
            ctx.arc(140, 100, 25, 0, Math.PI * 2);
            ctx.fill();

            ctx.beginPath();
            ctx.arc(260, 150, 20, 0, Math.PI * 2);
            ctx.arc(285, 145, 25, 0, Math.PI * 2);
            ctx.arc(310, 150, 20, 0, Math.PI * 2);
            ctx.fill();

            // Ground
            ctx.fillStyle = '#eab308'; // Ground base
            ctx.fillRect(0, CANVAS_HEIGHT - 60, CANVAS_WIDTH, 60);

            // Grass stripe on top of ground
            ctx.fillStyle = '#22c55e';
            ctx.fillRect(0, CANVAS_HEIGHT - 60, CANVAS_WIDTH, 14);

            // Black divider line
            ctx.strokeStyle = '#000';
            ctx.lineWidth = 2;
            ctx.beginPath();
            ctx.moveTo(0, CANVAS_HEIGHT - 60);
            ctx.lineTo(CANVAS_WIDTH, CANVAS_HEIGHT - 60);
            ctx.stroke();

            // Scrolling ground pattern
            if (gameState === 'PLAYING' || gameState === 'START') {
                groundOffset = (groundOffset + 2) % 20;
            }

            ctx.fillStyle = '#ca8a04';
            for (let x = -groundOffset; x < CANVAS_WIDTH; x += 20) {
                ctx.beginPath();
                ctx.moveTo(x, CANVAS_HEIGHT - 46);
                ctx.lineTo(x + 10, CANVAS_HEIGHT);
                ctx.lineTo(x + 5, CANVAS_HEIGHT);
                ctx.lineTo(x - 5, CANVAS_HEIGHT - 46);
                ctx.fill();
            }
        }

        // Draw In-Game Score Display
        function drawScore() {
            if (gameState === 'PLAYING') {
                ctx.fillStyle = '#ffffff';
                ctx.strokeStyle = '#000000';
                ctx.lineWidth = 4;
                ctx.font = '24px "Press Start 2P", cursive';
                ctx.textAlign = 'center';
                ctx.strokeText(score, CANVAS_WIDTH / 2, 60);
                ctx.fillText(score, CANVAS_WIDTH / 2, 60);
            }
        }

        // --- Core Loop ---
        function loop() {
            ctx.clearRect(0, 0, CANVAS_WIDTH, CANVAS_HEIGHT);

            drawBackground();
            pipes.update();
            pipes.draw();
            bird.update();
            bird.draw();
            drawScore();

            frames++;
            requestAnimationFrame(loop);
        }

        // Game State Controls
        function startGame() {
            initAudio();
            gameState = 'PLAYING';
            score = 0;
            bird.reset();
            pipes.reset();
            startOverlay.classList.add('hidden');
            gameOverOverlay.classList.add('hidden');
        }

        function triggerGameOver() {
            gameState = 'GAMEOVER';
            
            if (score > highScore) {
                highScore = score;
                localStorage.setItem('flappy_high_score', highScore);
            }

            finalScoreEl.innerText = score;
            highScoreDisplayEl.innerText = highScore;
            gameOverOverlay.classList.remove('hidden');
        }

        // Action Handlers
        function handleAction() {
            if (gameState === 'START') {
                startGame();
            } else if (gameState === 'PLAYING') {
                bird.flap();
            }
        }

        // Input Listeners
        window.addEventListener('keydown', (e) => {
            if (e.code === 'Space') {
                e.preventDefault();
                handleAction();
            }
        });

        canvas.addEventListener('click', (e) => {
            e.preventDefault();
            handleAction();
        });

        canvas.addEventListener('touchstart', (e) => {
            e.preventDefault();
            handleAction();
        }, { passive: false });

        startButton.addEventListener('click', () => {
            startGame();
        });

        restartButton.addEventListener('click', () => {
            startGame();
        });

        // Audio Toggle
        soundToggleBtn.addEventListener('click', (e) => {
            e.stopPropagation();
            soundEnabled = !soundEnabled;
            soundToggleBtn.innerText = soundEnabled ? '🔊 SFX: ON' : '🔇 SFX: OFF';
            soundToggleBtn.classList.toggle('text-yellow-400', soundEnabled);
            soundToggleBtn.classList.toggle('text-slate-500', !soundEnabled);
        });

        // Initialize Loop
        requestAnimationFrame(loop);
    </script>
</body>
</html>
