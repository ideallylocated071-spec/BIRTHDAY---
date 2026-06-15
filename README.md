<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>A Special Surprise For You ❤️</title>
    <script src="https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>
    <link href="https://fonts.googleapis.com/css2?family=Dancing+Script:wght@700&family=Poppins:wght@300;400;600&display=swap" rel="stylesheet">

    <style>
        body {
            font-family: 'Poppins', sans-serif;
            background: linear-gradient(135deg, #0f051d 0%, #290b3a 50%, #05010e 100%);
            overflow-x: hidden;
        }
        .cursive {
            font-family: 'Dancing Script', cursive;
        }
        .glass {
            background: rgba(255, 255, 255, 0.03);
            backdrop-filter: blur(16px);
            -webkit-backdrop-filter: blur(16px);
            border: 1px solid rgba(255, 255, 255, 0.08);
            box-shadow: 0 8px 32px 0 rgba(0, 0, 0, 0.37);
        }
        .step-section {
            display: none;
            animation: fadeIn 0.8s ease-in-out forwards;
        }
        .step-section.active {
            display: flex;
        }
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        /* Floating elements */
        .heart-particle {
            position: absolute;
            pointer-events: none;
            animation: floatUp 6s linear infinite;
        }
        @keyframes floatUp {
            0% { transform: translateY(100vh) rotate(0deg); opacity: 1; }
            100% { transform: translateY(-10vh) rotate(360deg); opacity: 0; }
        }
        /* Typewriter placeholder */
        .cursor::after {
            content: '|';
            animation: blink 0.7s infinite;
        }
        @keyframes blink { 50% { opacity: 0; } }
    </style>
</head>
<body class="relative min-h-screen text-white flex items-center justify-center p-4">

    <div id="particle-container" class="absolute inset-0 overflow-hidden pointer-events-none z-0"></div>

    <main class="w-full max-w-lg glass rounded-3xl p-6 md:p-8 z-10 relative overflow-hidden flex flex-col items-center justify-center min-h-[550px]">
        
        <section id="step-1" class="step-section active flex-col text-center items-center justify-center">
            <div class="w-24 h-24 bg-pink-500/10 rounded-full flex items-center justify-center mb-6 animate-pulse border border-pink-500/30">
                <i class="fa-solid fa-heart text-5xl text-pink-500"></i>
            </div>
            <h1 class="text-4xl font-bold tracking-wide mb-2">Hey Someone Special...</h1>
            <p class="text-pink-300 cursive text-3xl mb-8">A Special Surprise For You ❤️</p>
            <button onclick="nextStep(1)" class="w-full py-4 bg-gradient-to-r from-pink-500 to-purple-600 rounded-2xl font-semibold shadow-lg shadow-pink-500/20 hover:scale-105 transition-all duration-300">
                Begin Journey <i class="fa-solid fa-arrow-right ml-2"></i>
            </button>
        </section>

        <section id="step-2" class="step-section flex-col text-center items-center justify-center w-full">
            <i class="fa-solid fa-compact-disc text-5xl text-purple-400 animate-spin mb-6"></i>
            <h2 id="loading-text" class="text-xl font-medium mb-6 text-gray-300">Gathering stars...</h2>
            <div class="w-full bg-white/5 rounded-full h-3 max-w-xs border border-white/10 overflow-hidden">
                <div id="progress-bar" class="bg-gradient-to-r from-pink-500 to-purple-500 h-full w-0 transition-all duration-100 ease-out"></div>
            </div>
        </section>

        <section id="step-3" class="step-section flex-col text-center items-center justify-center">
            <h2 class="text-2xl font-semibold mb-2">A Package Arrived!</h2>
            <p class="text-sm text-gray-400 mb-8">Tap the box to unlock its contents</p>
            <div onclick="openGift()" class="cursor-pointer group relative my-6">
                <div class="absolute -inset-4 bg-gradient-to-r from-pink-500 to-purple-600 rounded-2xl blur-xl opacity-40 group-hover:opacity-70 transition duration-500"></div>
                <i id="gift-icon" class="fa-solid fa-box-open text-8xl text-pink-400 transition-transform duration-500 group-hover:scale-110"></i>
            </div>
            <p id="gift-hint" class="text-xs text-pink-300/70 mt-4 animate-bounce">Click to open</p>
        </section>

        <section id="step-4" class="step-section flex-col w-full">
            <div class="flex items-center gap-2 mb-4 text-pink-400">
                <i class="fa-solid fa-envelope-open-text text-xl"></i>
                <span class="text-xs tracking-widest uppercase font-semibold">Personal Note</span>
            </div>
            <div class="glass bg-white/5 rounded-2xl p-5 min-h-[180px] text-gray-200 text-sm leading-relaxed mb-6 border border-white/5">
                <p id="typewriter-text" class="cursor"></p>
            </div>
            <button onclick="nextStep(4)" id="letter-btn" class="w-full py-3.5 bg-white/10 rounded-xl font-semibold opacity-50 pointer-events-none transition-all" >
                Continue Reading
            </button>
        </section>

        <section id="step-5" class="step-section flex-col w-full text-center">
            <h2 class="text-xl font-semibold mb-1">Captured Moments 📸</h2>
            <p class="text-xs text-gray-400 mb-6">Our favorite visual snapshots</p>
            <div class="grid grid-cols-2 gap-3 mb-6 w-full">
                <div class="glass p-1.5 rounded-xl border border-white/10"><img src="https://images.unsplash.com/photo-1518199266791-5375a83190b7?w=300" class="rounded-lg object-cover h-28 w-full"></div>
                <div class="glass p-1.5 rounded-xl border border-white/10"><img src="https://images.unsplash.com/photo-1516589178581-6cd7833ae3b2?w=300" class="rounded-lg object-cover h-28 w-full"></div>
                <div class="glass p-1.5 rounded-xl border border-white/10"><img src="https://images.unsplash.com/photo-1494790108377-be9c29b29330?w=300" class="rounded-lg object-cover h-28 w-full"></div>
                <div class="glass p-1.5 rounded-xl border border-white/10"><img src="https://images.unsplash.com/photo-1517841905240-472988babdf9?w=300" class="rounded-lg object-cover h-28 w-full"></div>
            </div>
            <button onclick="nextStep(5)" class="w-full py-3 bg-white/10 rounded-xl font-medium border border-white/10 hover:bg-white/20 transition">View Timeline</button>
        </section>

        <section id="step-6" class="step-section flex-col w-full">
            <h2 class="text-xl font-semibold text-center mb-6">How It Started vs How It's Going</h2>
            <div class="space-y-4 relative before:absolute before:inset-y-0 before:left-4 before:w-[1px] before:bg-white/10 mb-6">
                <div class="relative pl-8 animate-fade-in">
                    <div class="absolute left-2.5 top-1.5 w-3 h-3 bg-pink-500 rounded-full shadow-glow"></div>
                    <span class="text-xs text-pink-400 font-semibold">Day One</span>
                    <h4 class="text-sm font-semibold text-white">The First Conversation</h4>
                    <p class="text-xs text-gray-400 mt-0.5">Where an accidental hello turned into hours of endless talking.</p>
                </div>
                <div class="relative pl-8">
                    <div class="absolute left-2.5 top-1.5 w-3 h-3 bg-purple-500 rounded-full"></div>
                    <span class="text-xs text-purple-400 font-semibold">Month Three</span>
                    <h4 class="text-sm font-semibold text-white">The Inside Jokes</h4>
                    <p class="text-xs text-gray-400 mt-0.5">When we developed a language completely unintelligible to the rest of the world.</p>
                </div>
                <div class="relative pl-8">
                    <div class="absolute left-2.5 top-1.5 w-3 h-3 bg-indigo-500 rounded-full"></div>
                    <span class="text-xs text-indigo-400 font-semibold">Today</span>
                    <h4 class="text-sm font-semibold text-white">Unstoppable Connection</h4>
                    <p class="text-xs text-gray-400 mt-0.5">Growing stronger, closer, and more chaotic every single day.</p>
                </div>
            </div>
            <button onclick="nextStep(6)" class="w-full py-3 bg-white/10 rounded-xl font-medium border border-white/10 hover:bg-white/20 transition">Next Surprise</button>
        </section>

        <section id="step-7" class="step-section flex-col w-full text-center">
            <h2 class="text-xl font-semibold mb-1">Reasons You're Cherished</h2>
            <p class="text-xs text-gray-400 mb-6">Click to reveal a beautiful dynamic truth</p>
            <div class="glass bg-white/5 rounded-2xl p-6 min-h-[140px] flex flex-col items-center justify-center border border-white/10 mb-6">
                <span id="reason-num" class="text-xs font-bold text-pink-400 tracking-widest uppercase mb-2">Reason #1</span>
                <p id="reason-text" class="text-base font-medium italic text-gray-200">Your laugh effortlessly patterns light through my gloomiest afternoons.</p>
            </div>
            <button onclick="nextReason()" id="reason-btn" class="w-full py-3 bg-gradient-to-r from-pink-500/20 to-purple-500/20 rounded-xl font-medium border border-pink-500/30 text-pink-300 hover:bg-pink-500/30 transition">Next Reason (1/13)</button>
        </section>

        <section id="step-8" class="step-section flex-col w-full text-center items-center">
            <h2 class="text-xl font-semibold mb-1">Our Theme Soundtrack 🎵</h2>
            <p class="text-xs text-gray-400 mb-8">Turn your audio up for the ultimate vibe</p>
            <audio id="bg-music" src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3" loop></audio>
            <div class="glass w-28 h-28 rounded-full flex items-center justify-center border border-white/20 mb-6 shadow-xl relative group">
                <div id="music-pulsar" class="absolute inset-0 bg-pink-500/10 rounded-full scale-100 group-hover:animate-ping pointer-events-none"></div>
                <button onclick="toggleMusic()" id="play-btn" class="w-16 h-16 bg-pink-500 rounded-full flex items-center justify-center text-white text-2xl shadow-lg hover:scale-105 transition">
                    <i class="fa-solid fa-play ml-1"></i>
                </button>
            </div>
            <p id="music-status" class="text-sm font-medium text-pink-400 mb-6">Audio is muted</p>
            <button onclick="nextStep(8)" class="w-full py-3 bg-white/10 rounded-xl font-medium border border-white/10 hover:bg-white/20 transition">Keep Audio Playing & Proceed</button>
        </section>

        <section id="step-9" class="step-section flex-col w-full text-center items-center">
            <h2 class="text-xl font-semibold mb-1">The Wheel of Destiny</h2>
            <p class="text-xs text-gray-400 mb-6">Spin to unlock a dynamic promise</p>
            <div class="relative w-40 h-40 flex items-center justify-center mb-6">
                <div id="wheel" class="w-full h-full rounded-full border-4 border-dashed border-purple-400 flex items-center justify-center transition-transform duration-3000 ease-out">
                    <div class="absolute inset-0 flex items-center justify-center rotate-0 font-bold text-xs text-pink-400">🎁</div>
                    <div class="absolute inset-0 flex items-center justify-center rotate-45 font-bold text-xs text-purple-300">💖</div>
                    <div class="absolute inset-0 flex items-center justify-center rotate-90 font-bold text-xs text-blue-300">🔮</div>
                    <div class="absolute inset-0 flex items-center justify-center rotate-135 font-bold text-xs text-indigo-300">⭐</div>
                    <i class="fa-solid fa-circle-dot text-2xl text-white z-10"></i>
                </div>
            </div>
            <button onclick="spinWheel()" id="spin-btn" class="w-full py-3 bg-purple-600 rounded-xl font-semibold shadow-lg hover:bg-purple-700 transition mb-3">Spin the Wheel</button>
            <p id="wheel-result" class="text-sm italic text-pink-300 min-h-[20px] mb-4"></p>
            <button onclick="nextStep(9)" id="wheel-next" class="w-full py-2.5 bg-white/5 rounded-xl text-xs text-gray-400 hidden border border-white/5 hover:bg-white/10">Proceed Further</button>
        </section>

        <section id="step-10" class="step-section flex-col w-full text-center">
            <h2 class="text-xl font-semibold mb-1">A Visual Message</h2>
            <p class="text-xs text-gray-400 mb-4">Crafted explicitly for you</p>
            <div class="glass p-2 rounded-2xl border border-white/10 overflow-hidden bg-black/40 mb-6 aspect-video flex items-center justify-center">
                <iframe class="w-full h-full rounded-xl" src="https://www.youtube.com/embed/dQw4w9WgXcQ" title="Surprise Video" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
            </div>
            <button onclick="nextStep(10)" class="w-full py-3 bg-white/10 rounded-xl font-medium border border-white/10 hover:bg-white/20 transition">Proceed to Countdown</button>
        </section>

        <section id="step-11" class="step-section flex-col w-full text-center">
            <h2 class="text-xl font-semibold mb-1">Our Milestone Countdown</h2>
            <p class="text-xs text-gray-400 mb-6">Counting down the units to our next grand celebration</p>
            <div class="grid grid-cols-3 gap-3 mb-8 w-full max-w-xs mx-auto">
                <div class="glass p-3 rounded-xl border border-white/10"><span id="cd-days" class="text-2xl font-bold text-pink-400">00</span><p class="text-[10px] uppercase text-gray-400 tracking-wider mt-1">Days</p></div>
                <div class="glass p-3 rounded-xl border border-white/10"><span id="cd-hours" class="text-2xl font-bold text-purple-400">00</span><p class="text-[10px] uppercase text-gray-400 tracking-wider mt-1">Hours</p></div>
                <div class="glass p-3 rounded-xl border border-white/10"><span id="cd-mins" class="text-2xl font-bold text-indigo-400">00</span><p class="text-[10px] uppercase text-gray-400 tracking-wider mt-1">Mins</p></div>
            </div>
            <button onclick="nextStep(11)" class="w-full py-3 bg-gradient-to-r from-pink-500/30 to-purple-500/30 rounded-xl font-medium border border-pink-500/30 text-pink-300 hover:scale-102 transition">Initiate Celebration Finale</button>
        </section>

        <section id="step-12" class="step-section flex-col w-full text-center items-center justify-center">
            <div class="w-20 h-20 bg-yellow-500/10 rounded-full flex items-center justify-center mb-4 animate-bounce">
                <i class="fa-solid fa-wand-magic-sparkles text-4xl text-yellow-400"></i>
            </div>
            <h2 class="text-2xl font-bold tracking-wide mb-2">Prepare for Impact!</h2>
            <p class="text-xs text-gray-400 max-w-xs mx-auto mb-6">We are unleashing a digital payload of stars and memories directly to your viewport.</p>
            <button onclick="triggerCelebration()" class="px-8 py-3.5 bg-gradient-to-r from-yellow-500 via-pink-500 to-purple-600 rounded-xl font-semibold shadow-lg shadow-pink-500/20 animate-pulse hover:scale-105 transition">
                Ignite Celebration 🎇
            </button>
        </section>

        <section id="step-13" class="step-section flex-col w-full text-center items-center justify-center">
            <div class="w-20 h-20 bg-pink-500/10 rounded-full flex items-center justify-center mb-4 border border-pink-500/20">
                <i class="fa-solid fa-crown text-4xl text-pink-400"></i>
            </div>
            <h1 class="text-5xl font-extrabold tracking-tight bg-gradient-to-r from-pink-400 via-purple-400 to-indigo-400 bg-clip-text text-transparent mb-2">I LOVE YOU</h1>
            <p class="cursive text-4xl text-pink-300 mb-8">Forever & Always ❤️</p>
            
            <div class="flex gap-2 w-full">
                <button onclick="shareWebsite()" class="flex-1 py-3 bg-white/5 rounded-xl text-xs font-semibold border border-white/10 hover:bg-white/10 transition flex items-center justify-center gap-2">
                    <i class="fa-solid fa-share-nodes text-pink-400"></i> Share Mystery
                </button>
                <button onclick="restartSurprise()" class="flex-1 py-3 bg-white/5 rounded-xl text-xs font-semibold border border-white/10 hover:bg-white/10 transition flex items-center justify-center gap-2">
                    <i class="fa-solid fa-rotate-left text-purple-400"></i> Relive Journey
                </button>
            </div>
        </section>

    </main>

    <script>
        // Active Navigation Logic
        function nextStep(current) {
            document.getElementById(`step-${current}`).classList.remove('active');
            const nextView = document.getElementById(`step-${current + 1}`);
            if (nextView) {
                nextView.classList.add('active');
                handleStepActivation(current + 1);
            }
        }

        function handleStepActivation(stepId) {
            if (stepId === 2) runLoadingSequencer();
            if (stepId === 4) runTypewriterEffect();
            if (stepId === 11) runCountdownTimer();
        }

        // Page 2: Advanced Loading Screen Phrases
        function runLoadingSequencer() {
            const phrases = ["Compiling smiles...", "Archiving warm hugs...", "Assembling late-night memories...", "Syncing heart rates...", "Finalizing surprise package..."];
            let idx = 0;
            const progress = document.getElementById('progress-bar');
            const txt = document.getElementById('loading-text');
            
            const textInterval = setInterval(() => {
                if(idx < phrases.length - 1) {
                    idx++;
                    txt.innerText = phrases[idx];
                }
            }, 900);

            let percent = 0;
            const progressInterval = setInterval(() => {
                percent += 2;
                progress.style.width = percent + '%';
                if(percent >= 100) {
                    clearInterval(progressInterval);
                    clearInterval(textInterval);
                    setTimeout(() => nextStep(2), 400);
                }
            }, 80);
        }

        // Page 3: Gift Opener Logic
        function openGift() {
            const icon = document.getElementById('gift-icon');
            icon.className = "fa-solid fa-box-open text-8xl text-purple-400 scale-125 transition-transform duration-500";
            document.getElementById('gift-hint').innerText = "Unwrapped smoothly!";
            setTimeout(() => nextStep(3), 1000);
        }

        // Page 4: Typewriter Mechanism
        function runTypewriterEffect() {
            const msg = "From the very second our paths crossed, my world quietly shifted. This is a small space dedicated exclusively to you, celebrating the absolute magic you introduce into everyday life simply by being yourself. Thank you for staying true, staying around, and creating beautiful chapters alongside me...";
            let i = 0;
            const target = document.getElementById('typewriter-text');
            target.innerText = "";
            
            function type() {
                if (i < msg.length) {
                    target.innerHTML += msg.charAt(i);
                    i++;
                    setTimeout(type, 35);
                } else {
                    const btn = document.getElementById('letter-btn');
                    btn.classList.remove('opacity-50', 'pointer-events-none');
                    btn.classList.add('bg-gradient-to-r', 'from-pink-500', 'to-purple-500', 'text-white', 'shadow-md');
                }
            }
            setTimeout(type, 500);
        }

        // Page 7: 13 Reasons Sequencer
        const reasonDataset = [
            "Your innate ability to see goodness in absolutely everyone.",
            "The distinct comfort and safety found within your presence.",
            "Your unique cosmic laugh that effortlessly resets bad days.",
            "The profound brilliance behind how your brilliant mind constructs ideas.",
            "Your structural courage during highly challenging personal seasons.",
            "How your eyes playfully brighten when you discuss topics you truly care about.",
            "The elegant grace and patience you routinely practice.",
            "Your unmatched attention to the quietest details of others.",
            "The specific rhythm of safety I feel when walking right by your side.",
            "Your uncompromisingly fierce loyalty to people you love.",
            "Your unconditional empathy toward living things.",
            "How you make ordinary, mundane daily tasks feel uniquely cinematic.",
            "Simply because you exist natively as you, altering my universe for the better."
        ];
        let currentReasonIdx = 0;
        function nextReason() {
            if(currentReasonIdx < reasonDataset.length - 1) {
                currentReasonIdx++;
                document.getElementById('reason-num').innerText = `Reason #${currentReasonIdx + 1}`;
                document.getElementById('reason-text').innerText = reasonDataset[currentReasonIdx];
                document.getElementById('reason-btn').innerText = `Next Reason (${currentReasonIdx + 1}/13)`;
            } else {
                nextStep(7);
            }
        }

        // Page 8: Music Stream Controller
        function toggleMusic() {
            const audio = document.getElementById('bg-music');
            const btnIcon = document.querySelector('#play-btn i');
            const status = document.getElementById('music-status');
            const pulsar = document.getElementById('music-pulsar');

            if (audio.paused) {
                audio.play().catch(e => console.log("Audio play prevented until native gesture interaction."));
                btnIcon.className = "fa-solid fa-pause";
                status.innerText = "Soundtrack is live 🎵";
                pulsar.classList.add('animate-ping');
            } else {
                audio.pause();
                btnIcon.className = "fa-solid fa-play ml-1";
                status.innerText = "Soundtrack is paused";
                pulsar.classList.remove('animate-ping');
            }
        }

        // Page 9: Fortune/Destiny Surprise Wheel
        let wheelSpun = false;
        function spinWheel() {
            if(wheelSpun) return;
            wheelSpun = true;
            const wheel = document.getElementById('wheel');
            const degrees = 1800 + Math.floor(Math.random() * 360);
            wheel.style.transform = `rotate(${degrees}deg)`;
            
            const outcomes = ["Unlimited Hugs Voucher Unlocked! 🎟️", "A Deep Secret Message Pending! 💌", "Late Night Coffee Treat Promised! ☕", "A Lifetime Protection Guarantee Activated! 🛡️"];
            const selectedText = outcomes[Math.floor(Math.random() * outcomes.length)];
            
            setTimeout(() => {
                document.getElementById('wheel-result').innerText = selectedText;
                confetti({ particleCount: 40, spread: 60, origin: { y: 0.6 } });
                document.getElementById('wheel-next').classList.remove('hidden');
                document.getElementById('spin-btn').disabled = true;
                document.getElementById('spin-btn').className = "w-full py-3 bg-white/5 text-gray-500 rounded-xl cursor-not-allowed";
            }, 3050);
        }

        // Page 11: Countdown Module (Targeting a date 100 days away for display consistency)
        function runCountdownTimer() {
            const targetDate = new Date();
            targetDate.setDate(targetDate.getDate() + 14); // Next Milestone hardcoded 14 days out
            
            function updateClock() {
                const now = new Date();
                const diff = targetDate - now;
                if (diff <= 0) return;
                
                const d = Math.floor(diff / (1000 * 60 * 60 * 24));
                const h = Math.floor((diff % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
                const m = Math.floor((diff % (1000 * 60 * 60)) / (1000 * 60));
                
                document.getElementById('cd-days').innerText = d.toString().padStart(2, '0');
                document.getElementById('cd-hours').innerText = h.toString().padStart(2, '0');
                document.getElementById('cd-mins').innerText = m.toString().padStart(2, '0');
            }
            setInterval(updateClock, 1000);
            updateClock();
        }

        // Page 12: High-Graphics Confetti Payload Trigger
        function triggerCelebration() {
            const duration = 4 * 1000;
            const end = Date.now() + duration;

            (function frame() {
                confetti({ particleCount: 4, angle: 60, spread: 55, origin: { x: 0 } });
                confetti({ particleCount: 4, angle: 120, spread: 55, origin: { x: 1 } });
                if (Date.now() < end) {
                    requestAnimationFrame(frame);
                } else {
                    nextStep(12);
                }
            }());
        }

        // Page 13: Finale Core Controls
        function shareWebsite() {
            if(navigator.share) {
                navigator.share({ title: 'Surprise Package', text: 'Open this customized surprise website layout.', url: window.location.href });
            } else {
                navigator.clipboard.writeText(window.location.href);
                alert("URL cloned to your active clipboard! Share it manually anywhere.");
            }
        }
        function restartSurprise() {
            window.location.reload();
        }

        // Global Visual Ambient: Float Floating Hearts Background Architecture
        function createAmbientParticles() {
            const container = document.getElementById('particle-container');
            const shapes = ['fa-heart', 'fa-star', 'fa-sparkles'];
            setInterval(() => {
                const el = document.createElement('i');
                const randomShape = shapes[Math.floor(Math.random() * shapes.length)];
                el.className = `fa-solid ${random
