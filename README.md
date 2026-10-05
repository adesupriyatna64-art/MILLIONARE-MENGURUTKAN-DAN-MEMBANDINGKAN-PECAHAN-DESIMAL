<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Who Wants to be a Millionaire - MTK Pecahan Desimal | SDN Kemiri 02</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- FontAwesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Google Font: Montserrat & Poppins -->
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;700;800&family=Roboto+Mono:wght@700&display=swap" rel="stylesheet">
    
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        brand: {
                            dark: '#030712',
                            card: '#0B1528',
                            accent: '#F59E0B',
                            gold: '#FBBF24',
                            glow: '#3B82F6',
                            correct: '#10B981',
                            wrong: '#EF4444',
                        }
                    },
                    fontFamily: {
                        sans: ['Poppins', 'sans-serif'],
                        mono: ['Roboto Mono', 'monospace'],
                    }
                }
            }
        }
    </script>

    <style>
        body {
            background: radial-gradient(circle at center, #1e1b4b 0%, #090d16 100%);
            color: #ffffff;
            font-family: 'Poppins', sans-serif;
            min-height: 100vh;
        }

        /* Millionaire Hexagon Answer Shape Style */
        .option-btn {
            position: relative;
            background: linear-gradient(180deg, #1e293b 0%, #0f172a 100%);
            border: 2px solid #3b82f6;
            transition: all 0.2s ease-in-out;
        }

        .option-btn:hover:not(:disabled) {
            background: linear-gradient(180deg, #1d4ed8 0%, #1e40af 100%);
            border-color: #fbbf24;
            transform: translateY(-2px);
            box-shadow: 0 0 15px rgba(251, 191, 36, 0.4);
        }

        .option-btn.selected {
            background: linear-gradient(180deg, #d97706 0%, #b45309 100%) !important;
            border-color: #fef08a !important;
            color: #ffffff !important;
            animation: pulse-select 0.8s infinite alternate;
        }

        .option-btn.correct {
            background: linear-gradient(180deg, #059669 0%, #047857 100%) !important;
            border-color: #34d399 !important;
            color: #ffffff !important;
            animation: pulse-correct 0.5s 3 alternate;
        }

        .option-btn.wrong {
            background: linear-gradient(180deg, #dc2626 0%, #b91c1c 100%) !important;
            border-color: #fca5a5 !important;
            color: #ffffff !important;
        }

        @keyframes pulse-select {
            from { box-shadow: 0 0 5px #f59e0b; }
            to { box-shadow: 0 0 20px #f59e0b; }
        }

        @keyframes pulse-correct {
            from { box-shadow: 0 0 5px #10b981; }
            to { box-shadow: 0 0 25px #10b981; }
        }

        /* Glassmorphism elements */
        .glass-panel {
            background: rgba(15, 23, 42, 0.75);
            backdrop-filter: blur(12px);
            border: 1px solid rgba(255, 255, 255, 0.1);
        }

        .gold-border {
            border: 2px solid #f59e0b;
            box-shadow: 0 0 10px rgba(245, 158, 11, 0.3);
        }

        /* Custom scrollbar */
        ::-webkit-scrollbar {
            width: 6px;
        }
        ::-webkit-scrollbar-track {
            background: #090d16;
        }
        ::-webkit-scrollbar-thumb {
            background: #3b82f6;
            border-radius: 4px;
        }
    </style>
</head>
<body class="flex flex-col justify-between min-h-screen select-none overflow-x-hidden">

    <!-- Top Navigation Header -->
    <header class="w-full glass-panel border-b border-blue-900/50 p-3 sm:p-4 sticky top-0 z-30">
        <div class="max-w-7xl mx-auto flex flex-wrap justify-between items-center gap-2">
            <div class="flex items-center gap-3">
                <div class="w-10 h-10 rounded-full bg-gradient-to-tr from-amber-500 to-yellow-300 flex items-center justify-center text-slate-900 font-extrabold text-xl shadow-lg">
                    <i class="fa-solid fa-graduation-cap"></i>
                </div>
                <div>
                    <h1 class="font-extrabold text-sm sm:text-lg bg-gradient-to-r from-amber-300 via-yellow-400 to-amber-500 bg-clip-text text-transparent leading-tight">
                        MILLIONAIRE MATEMATIKA
                    </h1>
                    <p class="text-xs text-blue-300">SDN KEMIRI 02 • Ade Supriyatna, S.Pd.,Gr.</p>
                </div>
            </div>

            <!-- Header Controls & Sound -->
            <div class="flex items-center gap-3">
                <button id="soundToggleBtn" onclick="toggleAudio()" class="px-3 py-1.5 rounded-lg bg-slate-800 hover:bg-slate-700 text-amber-400 text-xs sm:text-sm font-semibold border border-slate-600 transition flex items-center gap-2">
                    <i id="soundIcon" class="fa-solid fa-volume-high"></i>
                    <span id="soundLabel" class="hidden sm:inline">Suara: ON</span>
                </button>
            </div>
        </div>
    </header>

    <!-- START SCREEN CONTAINER -->
    <main id="startScreen" class="flex-grow flex items-center justify-center p-4 my-auto">
        <div class="max-w-3xl w-full glass-panel rounded-2xl p-6 sm:p-10 gold-border text-center space-y-6 relative overflow-hidden shadow-2xl">
            <!-- Decorative Glow Background -->
            <div class="absolute -top-24 -left-24 w-48 h-48 bg-amber-500/10 rounded-full blur-3xl pointer-events-none"></div>
            <div class="absolute -bottom-24 -right-24 w-48 h-48 bg-blue-500/10 rounded-full blur-3xl pointer-events-none"></div>

            <div class="inline-block px-4 py-1.5 bg-amber-500/20 text-amber-300 border border-amber-500/40 rounded-full text-xs sm:text-sm font-semibold tracking-wide">
                ✨ Joyful Learning & Pembelajaran Mendalam
            </div>

            <h2 class="text-2xl sm:text-4xl font-extrabold text-white leading-tight">
                Who Wants to be a Millionaire?
            </h2>
            <p class="text-amber-400 text-base sm:text-xl font-medium">
                Materi: Mengurutkan & Membandingkan Pecahan Desimal
            </p>

            <div class="bg-slate-900/80 rounded-xl p-4 sm:p-6 text-left border border-slate-700 space-y-3 text-xs sm:text-sm text-slate-300">
                <h3 class="font-bold text-amber-300 flex items-center gap-2">
                    <i class="fa-solid fa-circle-info"></i> Petunjuk Permainan:
                </h3>
                <ul class="list-disc list-inside space-y-1.5">
                    <li>Jawab <span class="text-amber-300 font-bold">15 pertanyaan</span> secara berurutan untuk memenangkan <span class="text-amber-400 font-bold">Rp 1.000.000.000</span>.</li>
                    <li>Terdapat <span class="text-emerald-400 font-bold">2 Titik Aman (Safe Haven)</span> pada Soal Ke-5 (Rp 1 Juta) dan Soal Ke-10 (Rp 32 Juta).</li>
                    <li>Gunakan 3 Bantuan (Lifelines): <span class="text-blue-300 font-semibold">50:50</span>, <span class="text-blue-300 font-semibold">Tanya Teman</span>, dan <span class="text-blue-300 font-semibold">Tanya Penonton</span>.</li>
                    <li>Setiap soal akan melatih pemahamanmu tentang nilai tempat desimal!</li>
                </ul>
            </div>

            <div class="pt-4 flex flex-col sm:flex-row gap-4 justify-center items-center">
                <button onclick="startGame()" class="w-full sm:w-auto px-8 py-4 bg-gradient-to-r from-amber-500 via-yellow-400 to-amber-600 hover:from-amber-400 hover:to-yellow-500 text-slate-950 font-extrabold text-lg rounded-xl shadow-lg shadow-amber-500/30 transform hover:scale-105 transition active:scale-95 flex items-center justify-center gap-3">
                    <i class="fa-solid fa-play"></i> MULAI PERMAINAN
                </button>
            </div>

            <div class="text-xs text-slate-400 pt-2">
                Kurikulum Merdeka • Kelas VI SD N Kemiri 02
            </div>
        </div>
    </main>

    <!-- GAMEPLAY CONTAINER (Hidden by default) -->
    <main id="gameScreen" class="hidden flex-grow max-w-7xl w-full mx-auto p-3 sm:p-6 grid grid-cols-1 lg:grid-cols-4 gap-4 items-start">
        
        <!-- Main Quiz Section (3 cols on large screens) -->
        <div class="lg:col-span-3 flex flex-col justify-between h-full space-y-4">
            
            <!-- Top Controls & Lifelines Bar -->
            <div class="glass-panel p-3 sm:p-4 rounded-xl flex flex-wrap justify-between items-center gap-3">
                <!-- Level & Prize Badge -->
                <div class="flex items-center gap-2">
                    <span class="px-3 py-1 bg-blue-900/80 text-blue-200 border border-blue-500/30 rounded-lg text-xs sm:text-sm font-semibold">
                        Soal <span id="currentLevelText" class="text-amber-400 text-base font-bold">1</span> dari 15
                    </span>
                    <span id="currentPrizeBadge" class="px-3 py-1 bg-amber-500/20 text-amber-300 border border-amber-500/50 rounded-lg text-xs sm:text-sm font-bold">
                        Rp 50.000
                    </span>
                </div>

                <!-- Lifeline Buttons -->
                <div class="flex items-center gap-2">
                    <span class="text-xs text-slate-400 font-medium hidden sm:inline">Bantuan:</span>
                    <button id="lifeline5050" onclick="useLifeline5050()" class="w-10 h-10 sm:w-12 sm:h-12 rounded-xl bg-slate-800 border-2 border-amber-400/80 hover:bg-amber-500/20 text-amber-300 font-bold text-xs sm:text-sm flex flex-col items-center justify-center transition disabled:opacity-40 disabled:cursor-not-allowed group relative" title="Hilangkan 2 Jawaban Salah">
                        <span>50:50</span>
                    </button>
                    <button id="lifelinePhone" onclick="useLifelinePhone()" class="w-10 h-10 sm:w-12 sm:h-12 rounded-xl bg-slate-800 border-2 border-amber-400/80 hover:bg-amber-500/20 text-amber-300 font-bold text-base sm:text-lg flex flex-col items-center justify-center transition disabled:opacity-40 disabled:cursor-not-allowed group relative" title="Tanya Teman">
                        <i class="fa-solid fa-phone"></i>
                    </button>
                    <button id="lifelineAudience" onclick="useLifelineAudience()" class="w-10 h-10 sm:w-12 sm:h-12 rounded-xl bg-slate-800 border-2 border-amber-400/80 hover:bg-amber-500/20 text-amber-300 font-bold text-base sm:text-lg flex flex-col items-center justify-center transition disabled:opacity-40 disabled:cursor-not-allowed group relative" title="Tanya Penonton">
                        <i class="fa-solid fa-chart-simple"></i>
                    </button>
                </div>
            </div>

            <!-- Question Card -->
            <div class="glass-panel p-6 sm:p-8 rounded-2xl border-2 border-blue-500/40 relative min-h-[160px] sm:min-h-[200px] flex items-center justify-center text-center shadow-xl">
                <div class="absolute -top-3 left-1/2 -translate-x-1/2 px-4 py-0.5 bg-blue-600 text-white rounded-full text-xs font-bold tracking-wider uppercase shadow">
                    Pertanyaan Matematika
                </div>
                <h3 id="questionText" class="text-lg sm:text-2xl font-bold text-slate-100 leading-relaxed max-w-3xl">
                    Memuat pertanyaan...
                </h3>
            </div>

            <!-- Options Grid (2x2) -->
            <div class="grid grid-cols-1 md:grid-cols-2 gap-3 sm:gap-4 pt-2">
                <button id="opt-0" onclick="selectOption(0)" class="option-btn p-4 sm:p-5 rounded-xl text-left font-semibold text-sm sm:text-base flex items-center gap-3">
                    <span class="w-8 h-8 rounded-lg bg-amber-500/20 text-amber-400 flex items-center justify-center font-extrabold text-sm border border-amber-500/40 flex-shrink-0">A</span>
                    <span class="option-text text-slate-100">Pilihan A</span>
                </button>
                <button id="opt-1" onclick="selectOption(1)" class="option-btn p-4 sm:p-5 rounded-xl text-left font-semibold text-sm sm:text-base flex items-center gap-3">
                    <span class="w-8 h-8 rounded-lg bg-amber-500/20 text-amber-400 flex items-center justify-center font-extrabold text-sm border border-amber-500/40 flex-shrink-0">B</span>
                    <span class="option-text text-slate-100">Pilihan B</span>
                </button>
                <button id="opt-2" onclick="selectOption(2)" class="option-btn p-4 sm:p-5 rounded-xl text-left font-semibold text-sm sm:text-base flex items-center gap-3">
                    <span class="w-8 h-8 rounded-lg bg-amber-500/20 text-amber-400 flex items-center justify-center font-extrabold text-sm border border-amber-500/40 flex-shrink-0">C</span>
                    <span class="option-text text-slate-100">Pilihan C</span>
                </button>
                <button id="opt-3" onclick="selectOption(3)" class="option-btn p-4 sm:p-5 rounded-xl text-left font-semibold text-sm sm:text-base flex items-center gap-3">
                    <span class="w-8 h-8 rounded-lg bg-amber-500/20 text-amber-400 flex items-center justify-center font-extrabold text-sm border border-amber-500/40 flex-shrink-0">D</span>
                    <span class="option-text text-slate-100">Pilihan D</span>
                </button>
            </div>

            <!-- Tip/Hint Banner -->
            <div id="learningTipBox" class="p-3 bg-blue-950/60 border border-blue-800/60 rounded-xl text-xs text-blue-200 flex items-start gap-2.5">
                <i class="fa-solid fa-lightbulb text-amber-400 text-sm mt-0.5"></i>
                <div id="learningTipText">
                    Tips: Bandingkan pecahan desimal dari angka di sebelah kiri koma (satuan), lalu persepuluhan (1 angka di belakang koma), dst.
                </div>
            </div>
        </div>

        <!-- Right Sidebar: Prize Ladder -->
        <div class="glass-panel rounded-2xl p-4 border border-blue-900/60 flex flex-col h-full justify-between">
            <div class="text-center pb-2 border-b border-slate-700/60 flex justify-between items-center">
                <span class="text-xs font-bold text-amber-400 uppercase tracking-wider">Tangga Hadiah</span>
                <span class="text-[10px] text-emerald-400 font-semibold">🛡️ Titik Aman: 5 & 10</span>
            </div>

            <div id="prizeLadderContainer" class="flex flex-col-reverse gap-1 my-2 text-xs sm:text-sm font-mono">
                <!-- Dynamically populated via JS -->
            </div>

            <div class="pt-2 border-t border-slate-700/60 text-center">
                <button onclick="quitGame()" class="w-full py-2 bg-red-950/60 hover:bg-red-900/80 text-red-300 border border-red-800/60 rounded-lg text-xs font-semibold transition">
                    <i class="fa-solid fa-door-open mr-1"></i> Bawa Pulang Hadiah Saat Ini
                </button>
            </div>
        </div>
    </main>

    <!-- GAME OVER / RESULT SCREEN -->
    <main id="resultScreen" class="hidden flex-grow flex items-center justify-center p-4 my-auto">
        <div class="max-w-xl w-full glass-panel rounded-2xl p-6 sm:p-10 gold-border text-center space-y-6 relative overflow-hidden shadow-2xl">
            <div id="resultHeaderIcon" class="w-20 h-20 mx-auto rounded-full bg-amber-500/20 text-amber-400 border-2 border-amber-400 flex items-center justify-center text-4xl shadow-inner">
                🏆
            </div>

            <div class="space-y-2">
                <h2 id="resultTitle" class="text-2xl sm:text-3xl font-extrabold text-white">
                    Permainan Selesai!
                </h2>
                <p id="resultSubtitle" class="text-slate-300 text-sm">
                    Terima kasih telah berjuang dengan cerdas!
                </p>
            </div>

            <div class="bg-slate-900/90 rounded-xl p-5 border border-slate-700 space-y-2">
                <div class="text-xs text-slate-400 uppercase tracking-widest font-semibold">Hadiah Akhir Yang Dibawa Pulang:</div>
                <div id="finalPrizeText" class="text-2xl sm:text-4xl font-extrabold text-amber-400 font-mono">
                    Rp 0
                </div>
                <p id="safeHavenNote" class="text-xs text-emerald-400 pt-1 font-medium">
                    (Mencapai Titik Aman)
                </p>
            </div>

            <p id="resultFeedback" class="text-xs sm:text-sm text-slate-300 italic px-2">
                "Pecahan desimal menjadi mudah jika kita memahami nilai tempatnya!"
            </p>

            <div class="pt-2 flex flex-col sm:flex-row gap-3 justify-center">
                <button onclick="startGame()" class="w-full sm:w-auto px-6 py-3 bg-amber-500 hover:bg-amber-400 text-slate-950 font-bold rounded-xl transition shadow-lg flex items-center justify-center gap-2">
                    <i class="fa-solid fa-rotate-right"></i> Main Lagi
                </button>
            </div>
        </div>
    </main>

    <!-- MODAL: PHONE A FRIEND -->
    <div id="phoneModal" class="fixed inset-0 bg-slate-950/80 backdrop-blur-sm z-50 hidden flex items-center justify-center p-4">
        <div class="max-w-md w-full glass-panel rounded-2xl p-6 border-2 border-blue-500 shadow-2xl space-y-4">
            <div class="flex justify-between items-center border-b border-slate-700 pb-3">
                <div class="flex items-center gap-3">
                    <div class="w-10 h-10 rounded-full bg-blue-600 text-white flex items-center justify-center text-lg font-bold">
                        👨‍🏫
                    </div>
                    <div>
                        <h4 class="font-bold text-white text-sm">Telepon Teman / Guru MTK</h4>
                        <p class="text-[11px] text-blue-300">Ade Supriyatna, S.Pd.,Gr.</p>
                    </div>
                </div>
                <button onclick="closeModal('phoneModal')" class="text-slate-400 hover:text-white text-xl">&times;</button>
            </div>

            <div class="bg-slate-900/90 rounded-xl p-4 border border-slate-800 text-slate-200 text-sm space-y-2">
                <p class="italic text-amber-300 font-semibold">"Halo! Mari kita bedah soal ini..."</p>
                <p id="phoneAdviceText" class="text-xs leading-relaxed text-slate-300">
                    Saran analisis akan muncul di sini.
                </p>
            </div>

            <button onclick="closeModal('phoneModal')" class="w-full py-2.5 bg-blue-600 hover:bg-blue-500 text-white font-bold text-xs rounded-xl transition">
                Mengerti, Terima Kasih!
            </button>
        </div>
    </div>

    <!-- MODAL: ASK THE AUDIENCE -->
    <div id="audienceModal" class="fixed inset-0 bg-slate-950/80 backdrop-blur-sm z-50 hidden flex items-center justify-center p-4">
        <div class="max-w-md w-full glass-panel rounded-2xl p-6 border-2 border-amber-500 shadow-2xl space-y-5">
            <div class="flex justify-between items-center border-b border-slate-700 pb-3">
                <div class="flex items-center gap-2">
                    <i class="fa-solid fa-chart-pie text-amber-400 text-xl"></i>
                    <h4 class="font-bold text-white text-sm">Hasil Suara Penonton Kelas</h4>
                </div>
                <button onclick="closeModal('audienceModal')" class="text-slate-400 hover:text-white text-xl">&times;</button>
            </div>

            <div class="space-y-3">
                <div>
                    <div class="flex justify-between text-xs text-slate-300 font-semibold mb-1">
                        <span>A</span> <span id="aud-percent-0">0%</span>
                    </div>
                    <div class="w-full bg-slate-800 rounded-full h-3 overflow-hidden">
                        <div id="aud-bar-0" class="bg-amber-400 h-full rounded-full transition-all duration-1000" style="width: 0%"></div>
                    </div>
                </div>
                <div>
                    <div class="flex justify-between text-xs text-slate-300 font-semibold mb-1">
                        <span>B</span> <span id="aud-percent-1">0%</span>
                    </div>
                    <div class="w-full bg-slate-800 rounded-full h-3 overflow-hidden">
                        <div id="aud-bar-1" class="bg-amber-400 h-full rounded-full transition-all duration-1000" style="width: 0%"></div>
                    </div>
                </div>
                <div>
                    <div class="flex justify-between text-xs text-slate-300 font-semibold mb-1">
                        <span>C</span> <span id="aud-percent-2">0%</span>
                    </div>
                    <div class="w-full bg-slate-800 rounded-full h-3 overflow-hidden">
                        <div id="aud-bar-2" class="bg-amber-400 h-full rounded-full transition-all duration-1000" style="width: 0%"></div>
                    </div>
                </div>
                <div>
                    <div class="flex justify-between text-xs text-slate-300 font-semibold mb-1">
                        <span>D</span> <span id="aud-percent-3">0%</span>
                    </div>
                    <div class="w-full bg-slate-800 rounded-full h-3 overflow-hidden">
                        <div id="aud-bar-3" class="bg-amber-400 h-full rounded-full transition-all duration-1000" style="width: 0%"></div>
                    </div>
                </div>
            </div>

            <button onclick="closeModal('audienceModal')" class="w-full py-2.5 bg-amber-500 hover:bg-amber-400 text-slate-950 font-bold text-xs rounded-xl transition">
                Kembali ke Permainan
            </button>
        </div>
    </div>

    <canvas id="confettiCanvas" class="fixed inset-0 pointer-events-none z-50"></canvas>

    <script>
        // Dynamic Question Generator to ensure fresh numbers on every play
        let questionBank = [];

        function getRandomInt(min, max) {
            return Math.floor(Math.random() * (max - min + 1)) + min;
        }

        function shuffleArray(array) {
            const arr = [...array];
            for (let i = arr.length - 1; i > 0; i--) {
                const j = Math.floor(Math.random() * (i + 1));
                [arr[i], arr[j]] = [arr[j], arr[i]];
            }
            return arr;
        }

        function generateDynamicQuestions() {
            questionBank = [];

            // Level 1: Membandingkan 2 desimal sederhana (Perseratusan)
            const l1Nums = shuffleArray([12, 25, 38, 45, 60, 75, 82]).slice(0, 4);
            const l1Decs = l1Nums.map(n => (n / 100).toFixed(2).replace('.', ','));
            const l1MinIndex = l1Nums.indexOf(Math.min(...l1Nums));
            questionBank.push({
                level: 1,
                prize: "Rp 50.000",
                numericPrize: 50000,
                question: "Di antara pecahan desimal berikut, manakah yang nilainya PALING KECIL?",
                options: l1Decs,
                answer: l1MinIndex,
                hint: "Bandingkan angka persepuluhan (angka ke-1 setelah koma), lalu perseratusannya."
            });

            // Level 2: Simbol Perbandingan (< / >) dengan Digit Berbeda (Jebakan Nol)
            const val2A = getRandomInt(4, 8); // misal 6 -> 0,6
            const val2B = val2A * 10 - getRandomInt(1, 9); // misal 53 -> 0,53
            const dec2A = (val2A / 10).toFixed(1).replace('.', ',');
            const dec2B = (val2B / 100).toFixed(2).replace('.', ',');
            const isALess = (val2A / 10) < (val2B / 100);
            const correctSign2 = isALess ? "<" : ">";
            const opts2 = [">", "<", "=", "+"];
            questionBank.push({
                level: 2,
                prize: "Rp 100.000",
                numericPrize: 100000,
                question: `Tanda perbandingan yang tepat untuk mengisi titik-titik pada: ${dec2A} ... ${dec2B} adalah:`,
                options: opts2,
                answer: opts2.indexOf(correctSign2),
                hint: `Ingat! ${dec2A} sama nilainya dengan ${dec2A}0. Bandingkan ${dec2A}0 dengan ${dec2B}.`
            });

            // Level 3: Pernyataan Benar/Salah (3 Angka di Belakang Koma / Perseribuan)
            const base3 = getRandomInt(100, 300);
            const trueStmt3 = `0,${base3 + 50} > 0,${base3}`;
            const falseStmts3 = [
                `0,${base3} > 0,${base3 + 50}`,
                `0,${base3 + 50} < 0,${base3}`,
                `0,${base3} = 0,${base3 + 50}`
            ];
            const allStmts3 = shuffleArray([trueStmt3, ...falseStmts3]);
            questionBank.push({
                level: 3,
                prize: "Rp 200.000",
                numericPrize: 200000,
                question: "Manakah pernyataan perbandingan pecahan desimal berikut yang BENAR?",
                options: allStmts3,
                answer: allStmts3.indexOf(trueStmt3),
                hint: "Cari perbandingan di mana nilai perseribuan di sebelah kiri lebih besar daripada sebelah kanan."
            });

            // Level 4: Mengurutkan 3 Desimal dengan Panjang Digit Berbeda
            const n4 = getRandomInt(2, 6);
            const dec4_1 = (n4 / 10).toFixed(1).replace('.', ','); // 0,4
            const dec4_2 = (n4 / 100).toFixed(2).replace('.', ','); // 0,04
            const dec4_3 = (n4 / 10 + 0.05).toFixed(2).replace('.', ','); // 0,45
            
            const origStr4 = shuffleArray([dec4_1, dec4_2, dec4_3]).join('; ');
            const opt4Correct = `${dec4_2}; ${dec4_1}; ${dec4_3}`; // 0,04; 0,4; 0,45
            const opt4Wrong1 = `${dec4_1}; ${dec4_2}; ${dec4_3}`;
            const opt4Wrong2 = `${dec4_3}; ${dec4_1}; ${dec4_2}`;
            const opt4Wrong3 = `${dec4_2}; ${dec4_3}; ${dec4_1}`;
            
            const allOpts4 = shuffleArray([opt4Correct, opt4Wrong1, opt4Wrong2, opt4Wrong3]);
            questionBank.push({
                level: 4,
                prize: "Rp 300.000",
                numericPrize: 300000,
                question: `Urutan pecahan desimal ${origStr4} dari yang TERKECIL ke TERBESAR adalah...`,
                options: allOpts4,
                answer: allOpts4.indexOf(opt4Correct),
                hint: `Samakan digit menjadi 2 angka di belakang koma: ${dec4_1}0, ${dec4_2}, dan ${dec4_3}.`
            });

            // Level 5: Safe Haven 1 - Nilai Tempat Perseribuan (0,00X vs 0,0X vs 0,X)
            const x5 = getRandomInt(5, 9);
            const d5_A = (x5 / 1000).toFixed(3).replace('.', ','); // 0,007
            const d5_B = (x5 / 100).toFixed(2).replace('.', ',');  // 0,07
            const stmt5Correct = `${d5_A} < ${d5_B}`;
            const opts5 = shuffleArray([
                `${d5_A} > ${d5_B}`,
                `${d5_A} < ${d5_B}`,
                `${d5_A} = ${d5_B}`,
                `${d5_A} + ${d5_B} = 1,0`
            ]);
            questionBank.push({
                level: 5,
                prize: "Rp 1.000.000",
                numericPrize: 1000000,
                isSafeHaven: true,
                question: `Perhatikan pecahan desimal ${d5_A} (perseribuan) dan ${d5_B} (perseratusan). Pernyataan yang BENAR adalah...`,
                options: opts5,
                answer: opts5.indexOf(stmt5Correct),
                hint: `${d5_A} bernilai ${x5} perseribuan, sedangkan ${d5_B} bernilai ${x5}0 perseribuan.`
            });

            // Level 6: Desimal Senilai Pada Perseribuan
            const val6 = getRandomInt(15, 85);
            const base6 = (val6 / 100).toFixed(2).replace('.', ','); // 0,45
            const correct6 = (val6 / 100).toFixed(3).replace('.', ','); // 0,450
            const wrong6_1 = (val6 / 1000).toFixed(3).replace('.', ','); // 0,045
            const wrong6_2 = (val6 / 10).toFixed(2).replace('.', ','); // 4,50
            const wrong6_3 = (val6 / 10000).toFixed(4).replace('.', ','); // 0,0045
            const opts6 = shuffleArray([correct6, wrong6_1, wrong6_2, wrong6_3]);
            questionBank.push({
                level: 6,
                prize: "Rp 2.000.000",
                numericPrize: 2000000,
                question: `Pecahan desimal mana yang nilainya SAMA dengan ${base6}?`,
                options: opts6,
                answer: opts6.indexOf(correct6),
                hint: "Menambahkan angka 0 di paling belakang setelah koma tidak mengubah nilai desimal!"
            });

            // Level 7: Mencari Paling Besar dengan 3 Digit Desimal
            const base7 = getRandomInt(100, 400);
            const decs7 = [
                ((base7 + 15) / 1000).toFixed(3).replace('.', ','),
                ((base7 + 120) / 1000).toFixed(2).replace('.', ','), // e.g. 0,32
                ((base7 + 5) / 1000).toFixed(3).replace('.', ','),
                ((base7 + 80) / 1000).toFixed(3).replace('.', ',')
            ];
            const maxVal7 = ((base7 + 120) / 1000).toFixed(2).replace('.', ',');
            questionBank.push({
                level: 7,
                prize: "Rp 4.000.000",
                numericPrize: 4000000,
                question: "Di antara pecahan desimal berikut, manakah yang nilainya PALING BESAR?",
                options: decs7,
                answer: decs7.indexOf(maxVal7),
                hint: `Ubah semua opsi ke 3 digit desimal. Misal ${maxVal7} menjadi ${maxVal7}0.`
            });

            // Level 8: Mengurutkan 4 Desimal dari Terbesar ke Terkecil
            const v8 = getRandomInt(1, 4);
            const d8_1 = (0.85 + v8/100).toFixed(2).replace('.', ','); // 0,86
            const d8_2 = (0.8 + v8/100).toFixed(3).replace('.', ',');  // 0,810 -> 0,81
            const d8_3 = (0.085 + v8/1000).toFixed(3).replace('.', ','); // 0,086
            const d8_4 = (0.008 + v8/1000).toFixed(3).replace('.', ','); // 0,009

            const origList8 = shuffleArray([d8_1, d8_2, d8_3, d8_4]).join('; ');
            const correctOrder8 = `${d8_1}; ${d8_2}; ${d8_3}; ${d8_4}`;
            const wrongOrder8_1 = `${d8_4}; ${d8_3}; ${d8_2}; ${d8_1}`;
            const wrongOrder8_2 = `${d8_2}; ${d8_1}; ${d8_3}; ${d8_4}`;
            const wrongOrder8_3 = `${d8_1}; ${d8_3}; ${d8_2}; ${d8_4}`;

            const opts8 = shuffleArray([correctOrder8, wrongOrder8_1, wrongOrder8_2, wrongOrder8_3]);
            questionBank.push({
                level: 8,
                prize: "Rp 8.000.000",
                numericPrize: 8000000,
                question: `Urutkan desimal berikut dari yang TERBESAR ke TERKECIL: ${origList8}`,
                options: opts8,
                answer: opts8.indexOf(correctOrder8),
                hint: "Bandingkan dari angka satuan, persepuluhan, perseratusan, hingga perseribuan."
            });

            // Level 9: Soal Cerita Lari 100m (Presisi Waktu hingga 3 Desimal)
            const baseTime = getRandomInt(11, 13);
            const tA = (baseTime + 0.205).toFixed(3).replace('.', ',');
            const tB = (baseTime + 0.25).toFixed(2).replace('.', ',');
            const opts9 = [
                `Pelari A (${tA} detik)`,
                `Pelari B (${tB} detik)`,
                "Kedua pelari bersamaan",
                "Tidak dapat ditentukan"
            ];
            questionBank.push({
                level: 9,
                prize: "Rp 16.000.000",
                numericPrize: 16000000,
                question: `Dalam lomba lari 100m Kelas VI, Pelari A mencatat waktu ${tA} detik dan Pelari B mencatat waktu ${tB} detik. Siapakah yang berlari LEBIH CEPAT?`,
                options: opts9,
                answer: 0, // Pelari A karena waktunya lebih kecil
                hint: `Ingat, semakin KECIL catatan waktu lari, semakin CEPAT pelarinya! Bandingkan ${tA} detik dengan ${tB}0 detik.`
            });

            // Level 10: Safe Haven 2 - Bilangan Desimal di Antara Dua Nilai Presisi
            const start10 = getRandomInt(10, 40);
            const lowBoundary10 = (start10 / 100).toFixed(2).replace('.', ','); // e.g. 0,25
            const highBoundary10 = ((start10 + 1) / 100).toFixed(2).replace('.', ','); // e.g. 0,26
            
            const betweenVal10 = (start10 / 100 + 0.005).toFixed(3).replace('.', ','); // 0,255
            const belowVal10 = (start10 / 100 - 0.01).toFixed(2).replace('.', ',');
            const aboveVal10 = ((start10 + 2) / 100).toFixed(2).replace('.', ',');
            const farVal10 = (start10 / 10).toFixed(1).replace('.', ',');

            const opts10 = shuffleArray([betweenVal10, belowVal10, aboveVal10, farVal10]);
            questionBank.push({
                level: 10,
                prize: "Rp 32.000.000",
                numericPrize: 32000000,
                isSafeHaven: true,
                question: `Bilangan desimal yang nilainya terletak DI ANTARA ${lowBoundary10} dan ${highBoundary10} adalah...`,
                options: opts10,
                answer: opts10.indexOf(betweenVal10),
                hint: `Ubah ke perseribuan: ${lowBoundary10} menjadi ${lowBoundary10}0 dan ${highBoundary10} menjadi ${highBoundary10}0.`
            });

            // Level 11: Soal Cerita Peringkat Nilai Ujian (4 Siswa)
            const baseScore = getRandomInt(8, 9);
            const scoreAni = `${baseScore},85`;
            const scoreBudi = `${baseScore},805`;
            const scoreCici = `${baseScore},9`;
            const scoreDedi = `${baseScore},089`;

            const opts11 = ["Cici", "Ani", "Budi", "Dedi"];
            questionBank.push({
                level: 11,
                prize: "Rp 64.000.000",
                numericPrize: 64000000,
                question: `Nilai rata-rata Ujian MTK: Ani (${scoreAni}), Budi (${scoreBudi}), Cici (${scoreCici}), Dedi (${scoreDedi}). Siapakah juara ke-2 (nilai tertinggi kedua)?`,
                options: opts11,
                answer: 1, // Ani
                hint: `Samakan digit 3 angka di belakang koma: Cici (${baseScore},900), Ani (${baseScore},850), Budi (${baseScore},805), Dedi (${baseScore},089).`
            });

            // Level 12: Pertidaksamaan SALAH Membandingkan Desimal & Pecahan
            const wrongStmt12 = "0,65 < 3/5"; // 3/5 = 0,60
            const opts12 = shuffleArray([
                "0,75 = 3/4",
                wrongStmt12,
                "0,8 > 4/5 - 0,1",
                "1/2 > 0,45"
            ]);
            questionBank.push({
                level: 12,
                prize: "Rp 125.000.000",
                numericPrize: 125000000,
                question: "Manakah pernyataan perbandingan pecahan dan desimal berikut yang SALAH?",
                options: opts12,
                answer: opts12.indexOf(wrongStmt12),
                hint: "Ubah pecahan biasa ke desimal: 3/5 = 0,60. Bandingkan apakah 0,65 lebih kecil dari 0,60?"
            });

            // Level 13: Membandingkan Persen vs Desimal vs Pecahan
            const val13 = getRandomInt(6, 8); // misal 7 -> 70% vs 0,75 vs 3/4
            const p13 = `${val13 * 10}%`; // 70% = 0,70
            const d13 = `0,${val13 * 10 + 5}`; // 0,75
            const opts13 = [
                `${p13} lebih besar dari ${d13}`,
                `${p13} lebih kecil dari ${d13}`,
                `Kedua nilai sama besar`,
                `Tidak dapat dibandingkan`
            ];
            questionBank.push({
                level: 13,
                prize: "Rp 250.000.000",
                numericPrize: 250000000,
                question: `Pak Ade memberikan tantangan: Manakah hubungan yang BENAR antara ${p13} dengan ${d13}?`,
                options: opts13,
                answer: 1,
                hint: `Ubah ${p13} menjadi desimal: ${p13} = 0,${val13}0. Bandingkan dengan ${d13}.`
            });

            // Level 14: Pengurutan Campuran Pecahan Biasa, Desimal & Persen
            const opt14Correct = "25%; 0,3; 1/2; 0,65";
            const opts14 = shuffleArray([
                opt14Correct,
                "0,3; 25%; 1/2; 0,65",
                "25%; 1/2; 0,3; 0,65",
                "1/2; 0,65; 0,3; 25%"
            ]);
            questionBank.push({
                level: 14,
                prize: "Rp 500.000.000",
                numericPrize: 500000000,
                question: "Urutkan dari yang TERKECIL ke TERBESAR: 0,3;  25%;  1/2;  0,65. Manakah urutan yang tepat?",
                options: opts14,
                answer: opts14.indexOf(opt14Correct),
                hint: "Ubah semua ke desimal: 25% = 0,25; 0,3 = 0,30; 1/2 = 0,50; 0,65."
            });

            // Level 15: Grand Final 1 Miliar - Pengurutan Kompleks Campuran 4 Bentuk
            const opt15Correct = "0,125; 15%; 1/4; 0,4";
            const opts15 = shuffleArray([
                opt15Correct,
                "15%; 0,125; 1/4; 0,4",
                "0,125; 1/4; 15%; 0,4",
                "0,4; 1/4; 15%; 0,125"
            ]);
            questionBank.push({
                level: 15,
                prize: "Rp 1.000.000.000",
                numericPrize: 1000000000,
                isSafeHaven: true,
                question: "SOAL 1 MILIAR: Urutkan dari yang TERKECIL: 1/4;  0,125;  15%;  0,4. Manakah urutan yang BENAR?",
                options: opts15,
                answer: opts15.indexOf(opt15Correct),
                hint: "Ubah ke desimal 3 digit: 0,125; 15% = 0,150; 1/4 = 0,250; 0,4 = 0,400. Urutkan dari terkecil!"
            });
        }

        // Game State Variables
        let currentLevel = 0; // 0-indexed (0 to 14)
        let isAudioOn = true;
        let isAnswering = false;
        let lifelinesUsed = {
            '5050': false,
            'phone': false,
            'audience': false
        };

        // Web Audio API Synthesizer for Zero-Dependency Sound FX
        const AudioCtx = window.AudioContext || window.webkitAudioContext;
        let audioCtx = null;

        function initAudio() {
            if (!audioCtx) {
                audioCtx = new AudioCtx();
            }
            if (audioCtx.state === 'suspended') {
                audioCtx.resume();
            }
        }

        function playSound(type) {
            if (!isAudioOn) return;
            try {
                initAudio();
                const now = audioCtx.currentTime;
                const osc = audioCtx.createOscillator();
                const gain = audioCtx.createGain();
                osc.connect(gain);
                gain.connect(audioCtx.destination);

                if (type === 'click') {
                    osc.type = 'sine';
                    osc.frequency.setValueAtTime(400, now);
                    osc.frequency.exponentialRampToValueAtTime(800, now + 0.08);
                    gain.gain.setValueAtTime(0.15, now);
                    gain.gain.linearRampToValueAtTime(0.01, now + 0.08);
                    osc.start(now);
                    osc.stop(now + 0.08);
                } else if (type === 'lock') {
                    osc.type = 'triangle';
                    osc.frequency.setValueAtTime(300, now);
                    osc.frequency.setValueAtTime(450, now + 0.1);
                    gain.gain.setValueAtTime(0.2, now);
                    gain.gain.linearRampToValueAtTime(0.01, now + 0.3);
                    osc.start(now);
                    osc.stop(now + 0.3);
                } else if (type === 'correct') {
                    // Arpeggio chime
                    const notes = [523.25, 659.25, 783.99, 1046.50]; // C5, E5, G5, C6
                    notes.forEach((freq, idx) => {
                        const noteOsc = audioCtx.createOscillator();
                        const noteGain = audioCtx.createGain();
                        noteOsc.type = 'sine';
                        noteOsc.frequency.setValueAtTime(freq, now + idx * 0.1);
                        noteGain.gain.setValueAtTime(0.2, now + idx * 0.1);
                        noteGain.gain.exponentialRampToValueAtTime(0.001, now + idx * 0.1 + 0.3);
                        noteOsc.connect(noteGain);
                        noteGain.connect(audioCtx.destination);
                        noteOsc.start(now + idx * 0.1);
                        noteOsc.stop(now + idx * 0.1 + 0.3);
                    });
                } else if (type === 'wrong') {
                    osc.type = 'sawtooth';
                    osc.frequency.setValueAtTime(220, now);
                    osc.frequency.linearRampToValueAtTime(110, now + 0.5);
                    gain.gain.setValueAtTime(0.3, now);
                    gain.gain.linearRampToValueAtTime(0.01, now + 0.5);
                    osc.start(now);
                    osc.stop(now + 0.5);
                } else if (type === 'win') {
                    // Victory fanfare chord
                    const freqs = [261.63, 329.63, 392.00, 523.25];
                    freqs.forEach(freq => {
                        const chordOsc = audioCtx.createOscillator();
                        const chordGain = audioCtx.createGain();
                        chordOsc.type = 'triangle';
                        chordOsc.frequency.setValueAtTime(freq, now);
                        chordGain.gain.setValueAtTime(0.15, now);
                        chordGain.gain.exponentialRampToValueAtTime(0.001, now + 1.2);
                        chordOsc.connect(chordGain);
                        chordGain.connect(audioCtx.destination);
                        chordOsc.start(now);
                        chordOsc.stop(now + 1.2);
                    });
                }
            } catch (e) {
                console.log("Audio not supported or blocked");
            }
        }

        function toggleAudio() {
            isAudioOn = !isAudioOn;
            document.getElementById('soundIcon').className = isAudioOn ? 'fa-solid fa-volume-high' : 'fa-solid fa-volume-xmark';
            document.getElementById('soundLabel').innerText = isAudioOn ? 'Suara: ON' : 'Suara: OFF';
            if (isAudioOn) playSound('click');
        }

        function renderPrizeLadder() {
            const container = document.getElementById('prizeLadderContainer');
            container.innerHTML = '';

            questionBank.forEach((q, index) => {
                const item = document.createElement('div');
                const isCurrent = index === currentLevel;
                const isPassed = index < currentLevel;
                const isSafe = q.isSafeHaven;

                let bgClass = "bg-slate-900/60 text-slate-400 border-transparent";
                if (isCurrent) {
                    bgClass = "bg-amber-500/30 text-amber-300 font-bold border-amber-400 shadow-md ring-1 ring-amber-400";
                } else if (isPassed) {
                    bgClass = "bg-emerald-950/40 text-emerald-400 font-semibold";
                } else if (isSafe) {
                    bgClass = "bg-blue-900/40 text-amber-200 font-bold border-blue-500/50";
                }

                item.className = `px-3 py-1.5 rounded-lg flex justify-between items-center border transition-all text-xs ${bgClass}`;
                
                item.innerHTML = `
                    <span class="flex items-center gap-1.5">
                        <span class="w-4 text-right ${isCurrent ? 'text-amber-300' : 'text-slate-500'}">${q.level}.</span>
                        ${isSafe ? '<span class="text-[10px]" title="Titik Aman">🛡️</span>' : ''}
                    </span>
                    <span>${q.prize}</span>
                `;
                container.appendChild(item);
            });
        }

        function startGame() {
            playSound('click');
            generateDynamicQuestions(); // Generate brand new numbers every replay!
            currentLevel = 0;
            isAnswering = false;
            lifelinesUsed = { '5050': false, 'phone': false, 'audience': false };

            // Reset Lifeline UI
            ['lifeline5050', 'lifelinePhone', 'lifelineAudience'].forEach(id => {
                const btn = document.getElementById(id);
                btn.disabled = false;
                btn.classList.remove('opacity-40', 'cursor-not-allowed', 'line-through');
            });

            document.getElementById('startScreen').classList.add('hidden');
            document.getElementById('resultScreen').classList.add('hidden');
            document.getElementById('gameScreen').classList.remove('hidden');

            loadQuestion();
        }

        function loadQuestion() {
            isAnswering = false;
            const q = questionBank[currentLevel];

            document.getElementById('currentLevelText').innerText = q.level;
            document.getElementById('currentPrizeBadge').innerText = q.prize;
            document.getElementById('questionText').innerText = q.question;
            document.getElementById('learningTipText').innerText = `Tips Soal ${q.level}: ` + q.hint;

            // Reset options
            for (let i = 0; i < 4; i++) {
                const btn = document.getElementById(`opt-${i}`);
                btn.disabled = false;
                btn.className = "option-btn p-4 sm:p-5 rounded-xl text-left font-semibold text-sm sm:text-base flex items-center gap-3";
                btn.querySelector('.option-text').innerText = q.options[i];
                btn.style.visibility = 'visible';
            }

            renderPrizeLadder();
        }

        function selectOption(index) {
            if (isAnswering) return;
            isAnswering = true;
            playSound('lock');

            const selectedBtn = document.getElementById(`opt-${index}`);
            selectedBtn.classList.add('selected');

            // Disable all options during validation phase
            for (let i = 0; i < 4; i++) {
                document.getElementById(`opt-${i}`).disabled = true;
            }

            const currentQ = questionBank[currentLevel];
            const isCorrect = (index === currentQ.answer);

            // Dramatic suspense delay (1.5 seconds)
            setTimeout(() => {
                if (isCorrect) {
                    playSound('correct');
                    selectedBtn.classList.remove('selected');
                    selectedBtn.classList.add('correct');

                    setTimeout(() => {
                        if (currentLevel < questionBank.length - 1) {
                            currentLevel++;
                            loadQuestion();
                        } else {
                            // WON THE 1 BILLION PRIZE!
                            triggerWin();
                        }
                    }, 1500);
                } else {
                    playSound('wrong');
                    selectedBtn.classList.remove('selected');
                    selectedBtn.classList.add('wrong');

                    // Highlight the correct answer
                    const correctBtn = document.getElementById(`opt-${currentQ.answer}`);
                    correctBtn.classList.add('correct');

                    setTimeout(() => {
                        gameOver(false);
                    }, 2000);
                }
            }, 1500);
        }

        function calculateSafeHavenPrize() {
            // Safe Haven at Level 5 (index 4) = Rp 1.000.000
            // Safe Haven at Level 10 (index 9) = Rp 32.000.000
            if (currentLevel >= 9) {
                return "Rp 32.000.000";
            } else if (currentLevel >= 4) {
                return "Rp 1.000.000";
            }
            return "Rp 0";
        }

        function quitGame() {
            playSound('click');
            const currentPrize = currentLevel > 0 ? questionBank[currentLevel - 1].prize : "Rp 0";
            showResultScreen(
                "Keputusan Bijak!",
                "Kamu memilih untuk berhenti dan membawa pulang:",
                currentPrize,
                "Luar biasa! Mengetahui kapan harus mengamankan hasil adalah bagian dari strategi cerdas.",
                "🏆"
            );
        }

        function gameOver(isWin = false) {
            if (isWin) {
                showResultScreen(
                    "SELAMAT! KAMU JADI JUTAWAN!",
                    "Kamu berhasil menjawab seluruh 15 Soal Matematika Desimal!",
                    "Rp 1.000.000.000",
                    "Sempurna! Kamu telah menguasai konsep perbandingan dan pengurutan pecahan desimal sepenuhnya!",
                    "🌟"
                );
            } else {
                const safePrize = calculateSafeHavenPrize();
                showResultScreen(
                    "Jawaban Belum Tepat!",
                    "Sayang sekali, namun kamu tetap membawa pulang hadiah Titik Aman:",
                    safePrize,
                    "Jangan menyerah! Pelajari kembali nilai tempat pecahan desimal dan coba lagi!",
                    "💡"
                );
            }
        }

        function triggerWin() {
            playSound('win');
            startConfetti();
            gameOver(true);
        }

        function showResultScreen(title, subtitle, prizeText, feedbackText, icon) {
            document.getElementById('gameScreen').classList.add('hidden');
            document.getElementById('resultScreen').classList.remove('hidden');

            document.getElementById('resultTitle').innerText = title;
            document.getElementById('resultSubtitle').innerText = subtitle;
            document.getElementById('finalPrizeText').innerText = prizeText;
            document.getElementById('resultFeedback').innerText = `"${feedbackText}"`;
            document.getElementById('resultHeaderIcon').innerText = icon;
        }

        function useLifeline5050() {
            if (lifelinesUsed['5050'] || isAnswering) return;
            playSound('click');
            lifelinesUsed['5050'] = true;

            const btn = document.getElementById('lifeline5050');
            btn.disabled = true;
            btn.classList.add('opacity-40', 'cursor-not-allowed', 'line-through');

            const currentQ = questionBank[currentLevel];
            const correctIdx = currentQ.answer;

            let incorrectIndices = [0, 1, 2, 3].filter(i => i !== correctIdx);
            // Shuffle and remove 2 incorrect ones
            incorrectIndices.sort(() => Math.random() - 0.5);
            const toHide = incorrectIndices.slice(0, 2);

            toHide.forEach(idx => {
                document.getElementById(`opt-${idx}`).style.visibility = 'hidden';
            });
        }

        function useLifelinePhone() {
            if (lifelinesUsed['phone'] || isAnswering) return;
            playSound('click');
            lifelinesUsed['phone'] = true;

            const btn = document.getElementById('lifelinePhone');
            btn.disabled = true;
            btn.classList.add('opacity-40', 'cursor-not-allowed', 'line-through');

            const currentQ = questionBank[currentLevel];
            const correctLetter = ['A', 'B', 'C', 'D'][currentQ.answer];

            const adviceText = `Berdasarkan analisis nilai tempat desimal untuk soal ini: "${currentQ.hint}". Saya 85% yakin jawabannya adalah pilihan **${correctLetter}**!`;

            document.getElementById('phoneAdviceText').innerHTML = adviceText;
            document.getElementById('phoneModal').classList.remove('hidden');
        }

        function useLifelineAudience() {
            if (lifelinesUsed['audience'] || isAnswering) return;
            playSound('click');
            lifelinesUsed['audience'] = true;

            const btn = document.getElementById('lifelineAudience');
            btn.disabled = true;
            btn.classList.add('opacity-40', 'cursor-not-allowed', 'line-through');

            const currentQ = questionBank[currentLevel];
            const correctIdx = currentQ.answer;

            // Generate weighted random percentages favouring the correct answer
            let percentages = [0, 0, 0, 0];
            let remaining = 100;

            // Assign high percentage (55% - 80%) to correct option
            const correctShare = Math.floor(Math.random() * 25) + 55;
            percentages[correctIdx] = correctShare;
            remaining -= correctShare;

            // Distribute remaining among other 3 options
            let otherIndices = [0, 1, 2, 3].filter(i => i !== correctIdx);
            otherIndices.forEach((idx, i) => {
                if (i === otherIndices.length - 1) {
                    percentages[idx] = remaining;
                } else {
                    const share = Math.floor(Math.random() * (remaining / 1.5));
                    percentages[idx] = share;
                    remaining -= share;
                }
            });

            // Animate percentages in modal
            document.getElementById('audienceModal').classList.remove('hidden');

            for (let i = 0; i < 4; i++) {
                document.getElementById(`aud-percent-${i}`).innerText = `${percentages[i]}%`;
                document.getElementById(`aud-bar-${i}`).style.width = `0%`;
                setTimeout(() => {
                    document.getElementById(`aud-bar-${i}`).style.width = `${percentages[i]}%`;
                }, 100);
            }
        }

        function closeModal(modalId) {
            playSound('click');
            document.getElementById(modalId).classList.add('hidden');
        }

        function startConfetti() {
            const canvas = document.getElementById('confettiCanvas');
            const ctx = canvas.getContext('2d');
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;

            const pieces = [];
            const numberOfPieces = 150;
            const colors = ['#FBBF24', '#3B82F6', '#10B981', '#EC4899', '#8B5CF6'];

            for (let i = 0; i < numberOfPieces; i++) {
                pieces.push({
                    x: Math.random() * canvas.width,
                    y: Math.random() * canvas.height - canvas.height,
                    size: Math.random() * 8 + 4,
                    color: colors[Math.floor(Math.random() * colors.length)],
                    speed: Math.random() * 5 + 2,
                    angle: Math.random() * 360
                });
            }

            function animateConfetti() {
                ctx.clearRect(0, 0, canvas.width, canvas.height);
                pieces.forEach(p => {
                    ctx.save();
                    ctx.translate(p.x, p.y);
                    ctx.rotate((p.angle * Math.PI) / 180);
                    ctx.fillStyle = p.color;
                    ctx.fillRect(-p.size / 2, -p.size / 2, p.size, p.size);
                    ctx.restore();

                    p.y += p.speed;
                    p.angle += 3;

                    if (p.y > canvas.height) {
                        p.y = -10;
                        p.x = Math.random() * canvas.width;
                    }
                });

                requestAnimationFrame(animateConfetti);
            }

            animateConfetti();
        }

        window.addEventListener('resize', () => {
            const canvas = document.getElementById('confettiCanvas');
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
        });
    </script>
</body>
</html>
