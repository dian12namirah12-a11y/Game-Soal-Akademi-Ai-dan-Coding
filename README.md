# Game-Soal-Akademi-Ai-dan-Coding<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Quiz Master 15 Nomor - Kuis Interaktif</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Inter', sans-serif;
        }
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
        .animate-fade-in {
            animation: fadeIn 0.4s ease-out forwards;
        }
    </style>
</head>
<body class="bg-gradient-to-br from-slate-950 via-indigo-950 to-purple-950 min-h-screen text-slate-100 flex flex-col items-center justify-center p-4">

    <div class="w-full max-w-2xl bg-slate-900/90 backdrop-blur-xl rounded-2xl shadow-2xl border border-slate-800 overflow-hidden">
        
        <!-- Header -->
        <header class="bg-slate-900/80 p-5 sm:p-6 border-b border-slate-800 flex justify-between items-center">
            <div class="flex items-center space-x-3">
                <span class="text-3xl">🎯</span>
                <div>
                    <h1 class="text-lg sm:text-xl font-bold tracking-wide text-transparent bg-clip-text bg-gradient-to-r from-indigo-400 to-pink-400">Quiz Master 15 Soal</h1>
                    <p class="text-xs text-slate-400">Tantangan Pengetahuan Lengkap</p>
                </div>
            </div>
            <div id="quiz-header-stats" class="hidden flex items-center space-x-3 text-sm font-medium">
                <div class="bg-slate-800/80 px-3 py-1.5 rounded-lg border border-slate-700 flex items-center space-x-1.5 shadow-sm">
                    <span class="text-indigo-400">⏱️</span>
                    <span id="timer-display" class="font-bold">20s</span>
                </div>
                <div class="bg-slate-800/80 px-3 py-1.5 rounded-lg border border-slate-700 shadow-sm">
                    Skor: <span id="score-display" class="text-emerald-400 font-bold">0</span>
                </div>
            </div>
        </header>

        <!-- Main Content Area -->
        <main class="p-6 sm:p-8">

            <section id="screen-setup" class="space-y-6 animate-fade-in">
                <div>
                    <h2 class="text-2xl font-bold text-slate-100 mb-1">Selamat Datang di Quiz Master!</h2>
                    <p class="text-slate-400 text-sm">Kuis ini berisi 15 pertanyaan pilihan ganda lengkap dengan pembahasan instan dan rekap nilai di akhir.</p>
                </div>

                <div class="bg-indigo-950/40 border border-indigo-500/30 p-4 rounded-xl space-y-2 text-sm text-indigo-200">
                    <div class="font-semibold flex items-center space-x-2">
                        <span>ℹ️</span>
                        <span>Aturan Permainan:</span>
                    </div>
                    <ul class="list-disc list-inside space-y-1 text-slate-300 text-xs sm:text-sm pl-1">
                        <li>Total terdapat 15 pertanyaan berbobot tinggi.</li>
                        <li>Waktu menjawab setiap soal adalah 20 detik.</li>
                        <li>Setiap jawaban benar bernilai +10 poin.</li>
                        <li>Lihat review jawaban lengkap setelah kuis selesai.</li>
                    </ul>
                </div>

                <button onclick="startQuiz()" class="w-full py-4 px-4 bg-gradient-to-r from-indigo-500 via-purple-500 to-pink-500 hover:opacity-95 text-white font-semibold rounded-xl shadow-xl transition transform active:scale-95 flex items-center justify-center space-x-2 text-base">
                    <span>Mulai Kuis 15 Soal Sekarang</span>
                    <span>🚀</span>
                </button>
            </section>

            <section id="screen-quiz" class="hidden space-y-6 animate-fade-in">
                <div class="flex justify-between items-center text-xs font-semibold text-slate-400 uppercase tracking-wider">
                    <span id="question-progress">Pertanyaan 1 dari 15</span>
                    <span class="bg-indigo-500/20 text-indigo-300 px-2.5 py-1 rounded-full border border-indigo-500/30">Campuran Umum</span>
                </div>

                <!-- Progress Bar -->
                <div class="w-full bg-slate-800 h-2.5 rounded-full overflow-hidden shadow-inner">
                    <div id="progress-bar-fill" class="bg-gradient-to-r from-indigo-500 to-pink-500 h-full w-0 transition-all duration-300"></div>
                </div>

                <h3 id="question-text" class="text-lg sm:text-xl font-semibold text-slate-100 leading-relaxed min-h-[60px]">
                    Pertanyaan akan muncul di sini...
                </h3>

                <!-- Pilihan Jawaban -->
                <div id="options-container" class="space-y-3">
                    <!-- Dinamis dimasukkan oleh JS -->
                </div>

                <div id="feedback-container" class="hidden p-4 rounded-xl text-sm font-medium animate-fade-in">
                    <!-- Feedback jawaban benar/salah -->
                </div>

                <div class="flex justify-end pt-2">
                    <button id="next-btn" onclick="nextQuestion()" class="hidden py-3 px-6 bg-indigo-600 hover:bg-indigo-500 text-white font-medium rounded-xl transition shadow-lg active:scale-95 flex items-center space-x-2">
                        <span>Lanjut</span>
                        <span>➡️</span>
                    </button>
                </div>
            </section>

            <section id="screen-result" class="hidden space-y-6 animate-fade-in text-center">
                <div class="inline-flex p-4 bg-indigo-600/20 border border-indigo-500/30 rounded-full text-4xl mb-1 shadow-lg">
                    🏆
                </div>
                <div>
                    <h2 class="text-2xl font-bold text-slate-100">Kuis 15 Soal Selesai!</h2>
                    <p class="text-slate-400 text-sm mt-1">Luar biasa! Kamu telah menyelesaikan seluruh rangkaian pertanyaan.</p>
                </div>

                <div class="bg-slate-900/80 p-6 rounded-2xl border border-slate-800 flex justify-around items-center shadow-inner">
                    <div>
                        <div class="text-3xl font-extrabold text-emerald-400" id="final-score">0</div>
                        <div class="text-xs text-slate-400 mt-1 uppercase tracking-wider font-semibold">Skor Akhir</div>
                    </div>
                    <div class="h-10 w-px bg-slate-800"></div>
                    <div>
                        <div class="text-3xl font-extrabold text-indigo-400" id="final-correct">0/15</div>
                        <div class="text-xs text-slate-400 mt-1 uppercase tracking-wider font-semibold">Benar</div>
                    </div>
                </div>

                <div class="space-y-3 text-left">
                    <h4 class="text-sm font-semibold text-slate-300 uppercase tracking-wider">Review 15 Jawaban:</h4>
                    <div id="review-list" class="space-y-3 max-h-72 overflow-y-auto pr-2 custom-scrollbar">
                        <!-- Dinamis dimasukkan oleh JS -->
                    </div>
                </div>

                <button onclick="restartQuiz()" class="w-full py-3.5 px-4 bg-gradient-to-r from-indigo-500 to-pink-500 hover:opacity-95 text-white font-semibold rounded-xl shadow-xl transition transform active:scale-95">
                    🔄 Mainkan Ulang Kuis
                </button>
            </section>

        </main>
    </div>

    <script>
        // Database 15 Pertanyaan Lengkap
        const quizData15 = [
            {
                q: "Ibu kota negara Indonesia saat ini adalah...",
                options: ["Surabaya", "Bandung", "Jakarta", "Medan"],
                answer: 2
            },
            {
                q: "Planet terdekat dengan matahari di tata surya kita adalah...",
                options: ["Venus", "Merkurius", "Mars", "Bumi"],
                answer: 1
            },
            {
                q: "Hewan mamalia terbesar yang hidup di bumi adalah...",
                options: ["Gajah Afrika", "Paus Biru", "Hiu Putih Besar", "Jerapah"],
                answer: 1
            },
            {
                q: "Tahun berapa proklamasi kemerdekaan Republik Indonesia dikumandangkan?",
                options: ["1942", "1945", "1950", "1948"],
                answer: 1
            },
            {
                q: "Unsur kimia dengan simbol 'O' merujuk pada gas...",
                options: ["Oksigen", "Hidrogen", "Nitrogen", "Karbon Dioksida"],
                answer: 0
            },
            {
                q: "Alat musik tradisional angklung berasal dari provinsi...",
                options: ["Jawa Tengah", "Jawa Barat", "Bali", "Sumatera Barat"],
                answer: 1
            },
            {
                q: "Benua terbesar di permukaan bumi berdasarkan luas wilayahnya adalah...",
                options: ["Afrika", "Amerika", "Asia", "Eropa"],
                answer: 2
            },
            {
                q: "Siapakah penemu bola lampu pijar modern yang komersial?",
                options: ["Nikola Tesla", "Albert Einstein", "Thomas Alva Edison", "Alexander Graham Bell"],
                answer: 2
            },
            {
                q: "Gunung tertinggi di dunia adalah...",
                options: ["Gunung Semeru", "Gunung Kilimanjaro", "Gunung Everest", "Gunung Fuji"],
                answer: 2
            },
            {
                q: "Organ tubuh manusia yang berfungsi untuk memompa darah ke seluruh tubuh adalah...",
                options: ["Paru-paru", "Hati", "Jantung", "Ginjal"],
                answer: 2
            },
            {
                q: "Hari Pahlawan di Indonesia diperingati setiap tahun pada tanggal...",
                options: ["17 Agustus", "1 Juni", "10 November", "28 Oktober"],
                answer: 2
            },
            {
                q: "Mata uang resmi yang digunakan di negara Jepang adalah...",
                options: ["Yuan", "Yen", "Won", "Ringgit"],
                answer: 1
            },
            {
                q: "Air murni pada tekanan atmosfer standar mendidih pada suhu...",
                options: ["50°C", "90°C", "100°C", "120°C"],
                answer: 2
            },
            {
                q: "Samudra terluas di dunia adalah...",
                options: ["Samudra Atlantik", "Samudra Hindia", "Samudra Artik", "Samudra Pasifik"],
                answer: 3
            },
            {
                q: "Kerajaan Hindu-Buddha terbesar di Nusantara pada masa lampau adalah...",
                options: ["Majapahit", "Sriwijaya", "Tarumanegara", "Singhasari"],
                answer: 0
            }
        ];

        // State Variabel Game
        let currentQuestions = [];
        let currentIndex = 0;
        let score = 0;
        let correctCount = 0;
        let timer = null;
        let timeLeft = 20;
        let userAnswersHistory = [];
        let isAnswerLocked = false;

        function startQuiz() {
            currentQuestions = [...quizData15];
            currentIndex = 0;
            score = 0;
            correctCount = 0;
            userAnswersHistory = [];

            document.getElementById('screen-setup').classList.add('hidden');
            document.getElementById('screen-result').classList.add('hidden');
            document.getElementById('screen-quiz').classList.remove('hidden');
            document.getElementById('quiz-header-stats').classList.remove('hidden');
            document.getElementById('score-display').innerText = score;

            loadQuestion();
        }

        function loadQuestion() {
            if (currentIndex >= currentQuestions.length) {
                endQuiz();
                return;
            }

            isAnswerLocked = false;
            clearInterval(timer);
            timeLeft = 20;
            document.getElementById('timer-display').innerText = timeLeft + 's';
            startTimer();

            const qObj = currentQuestions[currentIndex];
            document.getElementById('question-progress').innerText = `Pertanyaan ${currentIndex + 1} dari ${currentQuestions.length}`;
            
            // Update Progress Bar
            const progressPercent = ((currentIndex) / currentQuestions.length) * 100;
            document.getElementById('progress-bar-fill').style.width = progressPercent + '%';

            document.getElementById('question-text').innerText = qObj.q;

            const optionsContainer = document.getElementById('options-container');
            optionsContainer.innerHTML = '';

            qObj.options.forEach((opt, idx) => {
                const btn = document.createElement('button');
                btn.className = "w-full p-4 rounded-xl border border-slate-800 bg-slate-900/80 hover:bg-slate-800/80 text-left font-medium transition flex items-center justify-between group active:scale-[0.99] shadow-sm";
                btn.innerHTML = `
                    <span class="flex items-center space-x-3">
                        <span class="w-7 h-7 rounded-lg bg-slate-800 border border-slate-700 flex items-center justify-center text-xs font-bold text-slate-300 group-hover:bg-indigo-600 group-hover:border-indigo-500 group-hover:text-white transition">${String.fromCharCode(65 + idx)}</span>
                        <span class="text-sm sm:text-base">${opt}</span>
                    </span>
                `;
                btn.onclick = () => selectAnswer(idx);
                optionsContainer.appendChild(btn);
            });

            document.getElementById('feedback-container').classList.add('hidden');
            document.getElementById('next-btn').classList.add('hidden');
        }

        function startTimer() {
            timer = setInterval(() => {
                timeLeft--;
                document.getElementById('timer-display').innerText = timeLeft + 's';
                if (timeLeft <= 0) {
                    clearInterval(timer);
                    handleTimeOut();
                }
            }, 1000);
        }

        function handleTimeOut() {
            if (isAnswerLocked) return;
            isAnswerLocked = true;
            clearInterval(timer);

            const qObj = currentQuestions[currentIndex];
            userAnswersHistory.push({
                question: qObj.q,
                selected: -1,
                correct: qObj.answer,
                options: qObj.options
            });

            const buttons = document.getElementById('options-container').children;
            buttons[qObj.answer].className = "w-full p-4 rounded-xl border border-emerald-500/80 bg-emerald-950/40 text-left font-medium flex items-center justify-between shadow-md";

            showFeedback(false, "Waktu habis! Kamu tidak sempat memilih jawaban.");
        }

        function selectAnswer(selectedIndex) {
            if (isAnswerLocked) return;
            isAnswerLocked = true;
            clearInterval(timer);

            const qObj = currentQuestions[currentIndex];
            const isCorrect = selectedIndex === qObj.answer;
            const buttons = document.getElementById('options-container').children;

            if (isCorrect) {
                score += 10;
                correctCount++;
                document.getElementById('score-display').innerText = score;
                buttons[selectedIndex].className = "w-full p-4 rounded-xl border border-emerald-500/80 bg-emerald-950/50 text-left font-medium flex items-center justify-between transition shadow-md";
                showFeedback(true, "Hebat! Jawaban kamu benar! 🎉");
            } else {
                buttons[selectedIndex].className = "w-full p-4 rounded-xl border border-rose-500/80 bg-rose-950/50 text-left font-medium flex items-center justify-between transition shadow-md";
                buttons[qObj.answer].className = "w-full p-4 rounded-xl border border-emerald-500/80 bg-emerald-950/50 text-left font-medium flex items-center justify-between transition shadow-md";
                showFeedback(false, `Kurang tepat. Jawaban yang benar adalah: ${qObj.options[qObj.answer]}`);
            }

            userAnswersHistory.push({
                question: qObj.q,
                selected: selectedIndex,
                correct: qObj.answer,
                options: qObj.options
            });
        }

        function showFeedback(isCorrect, message) {
            const feedbackEl = document.getElementById('feedback-container');
            feedbackEl.classList.remove('hidden');
            if (isCorrect) {
                feedbackEl.className = "p-4 rounded-xl text-sm font-medium bg-emerald-950/80 border border-emerald-500/40 text-emerald-300 animate-fade-in shadow-inner";
            } else {
                feedbackEl.className = "p-4 rounded-xl text-sm font-medium bg-rose-950/80 border border-rose-500/40 text-rose-300 animate-fade-in shadow-inner";
            }
            feedbackEl.innerText = message;
            document.getElementById('next-btn').classList.remove('hidden');
        }

        function nextQuestion() {
            currentIndex++;
            loadQuestion();
        }

        function endQuiz() {
            clearInterval(timer);
            document.getElementById('screen-quiz').classList.add('hidden');
            document.getElementById('quiz-header-stats').classList.add('hidden');
            document.getElementById('screen-result').classList.remove('hidden');

            document.getElementById('final-score').innerText = score;
            document.getElementById('final-correct').innerText = `${correctCount}/${currentQuestions.length}`;

            const reviewList = document.getElementById('review-list');
            reviewList.innerHTML = '';

            userAnswersHistory.forEach((item, index) => {
                const isCorrect = item.selected === item.correct;
                const card = document.createElement('div');
                card.className = `p-3.5 rounded-xl border text-xs sm:text-sm ${isCorrect ? 'bg-emerald-950/20 border-emerald-500/30' : 'bg-rose-950/20 border-rose-500/30'}`;
                
                let selectedText = item.selected >= 0 ? item.options[item.selected] : "Tidak dijawab";
                let correctText = item.options[item.correct];

                card.innerHTML = `
                    <div class="font-semibold text-slate-200 mb-1">P.${index + 1} - ${item.question}</div>
                    <div class="space-y-0.5 mt-2 text-slate-400">
                        <div>Jawabanmu: <span class="${isCorrect ? 'text-emerald-400 font-medium' : 'text-rose-400 font-medium'}">${selectedText}</span></div>
                        ${!isCorrect ? `<div>Jawaban Benar: <span class="text-emerald-400 font-medium">${correctText}</span></div>` : ''}
                    </div>
                `;
                reviewList.appendChild(card);
            });
        }

        function restartQuiz() {
            document.getElementById('screen-result').classList.add('hidden');
            document.getElementById('screen-setup').classList.remove('hidden');
        }
    </script>
</body>
</html>
