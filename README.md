<!doctype html>
<html lang="th" class="h-full">
 <head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>คณิตศาสตร์การเงิน ป.5</title>
  <script src="/_sdk/element_sdk.js"></script>
  <script src="https://cdn.tailwindcss.com"></script>
  <style>
        body {
            box-sizing: border-box;
        }
        
        @import url('https://fonts.googleapis.com/css2?family=Kanit:wght@400;600;700&display=swap');
        
        * {
            font-family: 'Kanit', sans-serif;
        }
        
        .coin-animation {
            animation: bounce 0.6s ease-in-out;
        }
        
        @keyframes bounce {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-10px); }
        }
        
        .result-appear {
            animation: fadeIn 0.4s ease-in;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .card-hover {
            transition: transform 0.2s ease, box-shadow 0.2s ease;
        }
        
        .card-hover:hover {
            transform: translateY(-4px);
            box-shadow: 0 12px 24px rgba(0, 0, 0, 0.15);
        }
    </style>
  <style>@view-transition { navigation: auto; }</style>
  <script src="/_sdk/data_sdk.js" type="text/javascript"></script>
 </head>
 <body class="h-full overflow-auto">
  <div class="w-full h-full" style="background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);">
   <div class="w-full h-full overflow-auto">
    <div class="max-w-6xl mx-auto px-6 py-8"><!-- Header -->
     <div class="text-center mb-8">
      <div class="bg-white bg-opacity-20 backdrop-blur-sm rounded-2xl p-4 mb-6 inline-block">
       <p class="text-white mb-1" style="font-size: 18px; font-weight: 600;">👧 เด็กหญิง นาขวัญ มิตรมุสิก</p>
       <p class="text-white opacity-90" style="font-size: 16px;">ป.5/5 • สายชั้น MEP</p>
      </div>
      <h1 id="main-title" class="text-white mb-2" style="font-size: 48px; font-weight: 700;">คณิตศาสตร์การเงิน ป.5</h1>
      <p id="subtitle" class="text-white opacity-90" style="font-size: 20px;">เรียนรู้การคิดคำนวณเงินอย่างสนุก 💰</p>
     </div>
     <div class="grid grid-cols-1 lg:grid-cols-2 gap-6 mb-6"><!-- Savings Calculator -->
      <div class="bg-white rounded-2xl p-6 shadow-lg card-hover">
       <h2 id="savings-title" class="mb-4" style="font-size: 28px; font-weight: 600; color: #667eea;">💵 เครื่องคำนวณเงินออม</h2>
       <div class="space-y-4">
        <div><label class="block mb-2" style="font-size: 16px; font-weight: 600; color: #4a5568;">เงินออมต่อวัน (บาท)</label> <input type="number" id="daily-saving" class="w-full px-4 py-3 border-2 rounded-lg" style="border-color: #e2e8f0; font-size: 16px;" placeholder="เช่น 20" min="0">
        </div>
        <div><label class="block mb-2" style="font-size: 16px; font-weight: 600; color: #4a5568;">จำนวนวัน</label> <input type="number" id="days" class="w-full px-4 py-3 border-2 rounded-lg" style="border-color: #e2e8f0; font-size: 16px;" placeholder="เช่น 30" min="0">
        </div><button id="calculate-savings" class="w-full text-white py-3 rounded-lg font-semibold" style="background-color: #667eea; font-size: 18px;">คำนวณเงินออม</button>
        <div id="savings-result" class="hidden p-4 rounded-lg" style="background-color: #f0fdf4; border: 2px solid #86efac;">
         <p class="text-center" style="font-size: 18px; font-weight: 600; color: #15803d;"><span id="savings-amount"></span></p>
        </div>
       </div>
      </div><!-- Money Exchange -->
      <div class="bg-white rounded-2xl p-6 shadow-lg card-hover">
       <h2 id="exchange-title" class="mb-4" style="font-size: 28px; font-weight: 600; color: #764ba2;">💴 แลกเปลี่ยนธนบัตรและเหรียญ</h2>
       <div class="space-y-4">
        <div><label class="block mb-2" style="font-size: 16px; font-weight: 600; color: #4a5568;">จำนวนเงิน (บาท)</label> <input type="number" id="exchange-amount" class="w-full px-4 py-3 border-2 rounded-lg" style="border-color: #e2e8f0; font-size: 16px;" placeholder="เช่น 137" min="0">
        </div><button id="calculate-exchange" class="w-full text-white py-3 rounded-lg font-semibold" style="background-color: #764ba2; font-size: 18px;">คำนวณการแลกเปลี่ยน</button>
        <div id="exchange-result" class="hidden p-4 rounded-lg space-y-2" style="background-color: #fef3c7; border: 2px solid #fbbf24;">
         <div id="exchange-breakdown"></div>
        </div>
       </div>
      </div>
     </div><!-- Quiz Section -->
     <div class="bg-white rounded-2xl p-6 shadow-lg card-hover">
      <h2 id="quiz-title" class="mb-6" style="font-size: 28px; font-weight: 600; color: #10b981;">📝 แบบฝึกหัดคณิตศาสตร์การเงิน</h2>
      <div id="quiz-container" class="space-y-4"><!-- Quiz questions will be inserted here -->
      </div>
      <div class="mt-6 text-center"><button id="check-answers" class="px-8 py-3 text-white rounded-lg font-semibold" style="background-color: #10b981; font-size: 18px;">ตรวจคำตอบ</button> <button id="reset-quiz" class="ml-3 px-8 py-3 text-white rounded-lg font-semibold" style="background-color: #6b7280; font-size: 18px;">ทำใหม่</button>
      </div>
      <div id="quiz-result" class="hidden mt-6 p-4 rounded-lg text-center">
       <p id="score-text" style="font-size: 24px; font-weight: 700;"></p>
      </div>
     </div>
    </div>
   </div>
  </div>
  <script>
        const defaultConfig = {
            primary_color: '#ff6b9d',
            secondary_color: '#ffa500',
            accent_color: '#9b59b6',
            background_color: '#ffffff',
            text_color: '#2c3e50',
            font_family: 'Kanit',
            font_size: 16,
            main_title: 'คณิตศาสตร์การเงิน ป.5',
            subtitle: 'เรียนรู้การคิดคำนวณเงินอย่างสนุก 💰',
            savings_title: '💵 เครื่องคำนวณเงินออม',
            exchange_title: '💴 แลกเปลี่ยนธนบัตรและเหรียญ',
            quiz_title: '📝 แบบฝึกหัดคณิตศาสตร์การเงิน'
        };

        const quizQuestions = [
            {
                question: 'ถ้าออมเงินวันละ 15 บาท เป็นเวลา 20 วัน จะได้เงินออมทั้งหมดกี่บาท?',
                answer: 300
            },
            {
                question: 'มีเงิน 250 บาท ต้องการแลกเป็นธนบัตร 100 บาท ได้กี่ใบ และเหลือเงินอีกกี่บาท?',
                answer: '2 ใบ เหลือ 50 บาท'
            },
            {
                question: 'ซื้อขนมร���คา 35 บาท จ่��ยด้วยธนบัตร 100 บาท จะได้เงินทอนกี่บาท?',
                answer: 65
            },
            {
                question: 'ถ้าออมเงินได้ 450 บาท และใช้ไป 180 บาท จะเหลือเงินกี่บาท?',
                answer: 270
            }
        ];

        function generateQuiz() {
            const container = document.getElementById('quiz-container');
            container.innerHTML = '';
            
            quizQuestions.forEach((q, index) => {
                const questionDiv = document.createElement('div');
                questionDiv.className = 'p-4 rounded-lg';
                questionDiv.style.backgroundColor = '#f9fafb';
                questionDiv.style.border = '2px solid #e5e7eb';
                
                questionDiv.innerHTML = `
                    <p class="mb-3" style="font-size: 18px; font-weight: 600; color: #374151;">
                        ${index + 1}. ${q.question}
                    </p>
                    <input type="text" id="answer-${index}" class="w-full px-4 py-2 border-2 rounded-lg" style="border-color: #e2e8f0; font-size: 16px;" placeholder="พิมพ์��ำตอบ">
                    <div id="feedback-${index}" class="hidden mt-2 p-2 rounded"></div>
                `;
                
                container.appendChild(questionDiv);
            });
        }

        function checkQuizAnswers() {
            let correct = 0;
            
            quizQuestions.forEach((q, index) => {
                const userAnswer = document.getElementById(`answer-${index}`).value.trim();
                const feedback = document.getElementById(`feedback-${index}`);
                const correctAnswer = String(q.answer);
                
                feedback.classList.remove('hidden');
                
                if (userAnswer.toLowerCase() === correctAnswer.toLowerCase() || 
                    (typeof q.answer === 'number' && parseFloat(userAnswer) === q.answer)) {
                    correct++;
                    feedback.style.backgroundColor = '#d1fae5';
                    feedback.style.color = '#065f46';
                    feedback.innerHTML = '✓ ถูกต��อง!';
                } else {
                    feedback.style.backgroundColor = '#fee2e2';
                    feedback.style.color = '#991b1b';
                    feedback.innerHTML = `✗ คำตอบที่ถูกต้อง: ${correctAnswer}`;
                }
            });
            
            const resultDiv = document.getElementById('quiz-result');
            const scoreText = document.getElementById('score-text');
            
            resultDiv.classList.remove('hidden');
            resultDiv.classList.add('result-appear');
            
            const percentage = (correct / quizQuestions.length) * 100;
            
            if (percentage === 100) {
                resultDiv.style.backgroundColor = '#d1fae5';
                resultDiv.style.borderColor = '#34d399';
                resultDiv.style.border = '3px solid';
                scoreText.style.color = '#065f46';
                scoreText.textContent = `🎉 เก่งมาก! ทำ���ูก ${correct}/${quizQuestions.length} ข้อ`;
            } else if (percentage >= 75) {
                resultDiv.style.backgroundColor = '#dbeafe';
                resultDiv.style.borderColor = '#60a5fa';
                resultDiv.style.border = '3px solid';
                scoreText.style.color = '#1e40af';
                scoreText.textContent = `👍 ดีมาก! ทำถูก ${correct}/${quizQuestions.length} ข้อ`;
            } else {
                resultDiv.style.backgroundColor = '#fef3c7';
                resultDiv.style.borderColor = '#fbbf24';
                resultDiv.style.border = '3px solid';
                scoreText.style.color = '#92400e';
                scoreText.textContent = `💪 พยายามต่อไป! ทำถูก ${correct}/${quizQuestions.length} ข้อ`;
            }
        }

        function resetQuiz() {
            quizQuestions.forEach((q, index) => {
                document.getElementById(`answer-${index}`).value = '';
                const feedback = document.getElementById(`feedback-${index}`);
                feedback.classList.add('hidden');
            });
            
            document.getElementById('quiz-result').classList.add('hidden');
        }

        function calculateSavings() {
            const daily = parseFloat(document.getElementById('daily-saving').value);
            const days = parseFloat(document.getElementById('days').value);
            
            if (isNaN(daily) || isNaN(days) || daily < 0 || days < 0) {
                const resultDiv = document.getElementById('savings-result');
                resultDiv.classList.remove('hidden');
                resultDiv.classList.add('result-appear');
                resultDiv.style.backgroundColor = '#fee2e2';
                resultDiv.style.borderColor = '#f87171';
                document.getElementById('savings-amount').style.color = '#991b1b';
                document.getElementById('savings-amount').textContent = 'กรุณากรอกตัวเลขที่ถูกต้อง';
                return;
            }
            
            const total = daily * days;
            
            const resultDiv = document.getElementById('savings-result');
            resultDiv.classList.remove('hidden');
            resultDiv.classList.add('result-appear', 'coin-animation');
            resultDiv.style.backgroundColor = '#f0fdf4';
            resultDiv.style.borderColor = '#86efac';
            document.getElementById('savings-amount').style.color = '#15803d';
            document.getElementById('savings-amount').textContent = 
                `ออมเงิน ${daily} บาท/วัน × ${days} วัน = ${total.toFixed(2)} บาท 🎉`;
            
            setTimeout(() => {
                resultDiv.classList.remove('coin-animation');
            }, 600);
        }

        function calculateExchange() {
            const amount = parseFloat(document.getElementById('exchange-amount').value);
            
            if (isNaN(amount) || amount < 0) {
                const resultDiv = document.getElementById('exchange-result');
                resultDiv.classList.remove('hidden');
                resultDiv.classList.add('result-appear');
                resultDiv.style.backgroundColor = '#fee2e2';
                resultDiv.style.borderColor = '#f87171';
                document.getElementById('exchange-breakdown').innerHTML = 
                    '<p style="color: #991b1b; font-weight: 600;">กรุณากรอกจำนวนเงินที่ถูกต้อง</p>';
                return;
            }
            
            let remaining = amount;
            const bills = [
                { value: 1000, name: '1,000 บาท', emoji: '💶' },
                { value: 500, name: '500 บาท', emoji: '💵' },
                { value: 100, name: '100 บาท', emoji: '💴' },
                { value: 50, name: '50 บาท', emoji: '💵' },
                { value: 20, name: '20 บาท', emoji: '💴' }
            ];
            
            const coins = [
                { value: 10, name: '10 บาท', emoji: '🪙' },
                { value: 5, name: '5 บาท', emoji: '🪙' },
                { value: 2, name: '2 บาท', emoji: '🪙' },
                { value: 1, name: '1 บาท', emoji: '🪙' }
            ];
            
            let breakdown = '<div class="space-y-2">';
            
            bills.forEach(bill => {
                const count = Math.floor(remaining / bill.value);
                if (count > 0) {
                    breakdown += `
                        <div class="flex justify-between items-center">
                            <span style="font-size: 16px; color: #374151;">${bill.emoji} ธนบัตร ${bill.name}</span>
                            <span style="font-size: 18px; font-weight: 600; color: #1f2937;">${count} ใบ</span>
                        </div>
                    `;
                    remaining -= count * bill.value;
                }
            });
            
            coins.forEach(coin => {
                const count = Math.floor(remaining / coin.value);
                if (count > 0) {
                    breakdown += `
                        <div class="flex justify-between items-center">
                            <span style="font-size: 16px; color: #374151;">${coin.emoji} เหรียญ ${coin.name}</span>
                            <span style="font-size: 18px; font-weight: 600; color: #1f2937;">${count} เหรียญ</span>
                        </div>
                    `;
                    remaining -= count * coin.value;
                }
            });
            
            breakdown += '</div>';
            
            const resultDiv = document.getElementById('exchange-result');
            resultDiv.classList.remove('hidden');
            resultDiv.classList.add('result-appear', 'coin-animation');
            resultDiv.style.backgroundColor = '#fef3c7';
            resultDiv.style.borderColor = '#fbbf24';
            document.getElementById('exchange-breakdown').innerHTML = breakdown;
            
            setTimeout(() => {
                resultDiv.classList.remove('coin-animation');
            }, 600);
        }

        async function onConfigChange(config) {
            const baseSize = config.font_size || defaultConfig.font_size;
            const customFont = config.font_family || defaultConfig.font_family;
            const baseFontStack = 'sans-serif';
            
            document.getElementById('main-title').textContent = config.main_title || defaultConfig.main_title;
            document.getElementById('main-title').style.fontSize = `${baseSize * 3}px`;
            document.getElementById('main-title').style.fontFamily = `${customFont}, ${baseFontStack}`;
            
            document.getElementById('subtitle').textContent = config.subtitle || defaultConfig.subtitle;
            document.getElementById('subtitle').style.fontSize = `${baseSize * 1.25}px`;
            document.getElementById('subtitle').style.fontFamily = `${customFont}, ${baseFontStack}`;
            
            document.getElementById('savings-title').textContent = config.savings_title || defaultConfig.savings_title;
            document.getElementById('savings-title').style.fontSize = `${baseSize * 1.75}px`;
            document.getElementById('savings-title').style.fontFamily = `${customFont}, ${baseFontStack}`;
            document.getElementById('savings-title').style.color = config.primary_color || defaultConfig.primary_color;
            
            document.getElementById('exchange-title').textContent = config.exchange_title || defaultConfig.exchange_title;
            document.getElementById('exchange-title').style.fontSize = `${baseSize * 1.75}px`;
            document.getElementById('exchange-title').style.fontFamily = `${customFont}, ${baseFontStack}`;
            document.getElementById('exchange-title').style.color = config.secondary_color || defaultConfig.secondary_color;
            
            document.getElementById('quiz-title').textContent = config.quiz_title || defaultConfig.quiz_title;
            document.getElementById('quiz-title').style.fontSize = `${baseSize * 1.75}px`;
            document.getElementById('quiz-title').style.fontFamily = `${customFont}, ${baseFontStack}`;
            document.getElementById('quiz-title').style.color = config.accent_color || defaultConfig.accent_color;
            
            document.querySelector('body > div').style.background = 
                `linear-gradient(135deg, ${config.primary_color || defaultConfig.primary_color} 0%, ${config.secondary_color || defaultConfig.secondary_color} 100%)`;
            
            const cards = document.querySelectorAll('.bg-white');
            cards.forEach(card => {
                card.style.backgroundColor = config.background_color || defaultConfig.background_color;
            });
            
            document.getElementById('calculate-savings').style.backgroundColor = config.primary_color || defaultConfig.primary_color;
            document.getElementById('calculate-exchange').style.backgroundColor = config.secondary_color || defaultConfig.secondary_color;
            document.getElementById('check-answers').style.backgroundColor = config.accent_color || defaultConfig.accent_color;
            
            const allText = document.querySelectorAll('p, label, input, button, div');
            allText.forEach(el => {
                if (!el.style.color || el.style.color === defaultConfig.text_color) {
                    el.style.color = config.text_color || defaultConfig.text_color;
                }
            });
        }

        if (window.elementSdk) {
            window.elementSdk.init({
                defaultConfig,
                onConfigChange,
                mapToCapabilities: (config) => ({
                    recolorables: [
                        {
                            get: () => config.primary_color || defaultConfig.primary_color,
                            set: (value) => {
                                config.primary_color = value;
                                window.elementSdk.setConfig({ primary_color: value });
                            }
                        },
                        {
                            get: () => config.secondary_color || defaultConfig.secondary_color,
                            set: (value) => {
                                config.secondary_color = value;
                                window.elementSdk.setConfig({ secondary_color: value });
                            }
                        },
                        {
                            get: () => config.accent_color || defaultConfig.accent_color,
                            set: (value) => {
                                config.accent_color = value;
                                window.elementSdk.setConfig({ accent_color: value });
                            }
                        },
                        {
                            get: () => config.background_color || defaultConfig.background_color,
                            set: (value) => {
                                config.background_color = value;
                                window.elementSdk.setConfig({ background_color: value });
                            }
                        },
                        {
                            get: () => config.text_color || defaultConfig.text_color,
                            set: (value) => {
                                config.text_color = value;
                                window.elementSdk.setConfig({ text_color: value });
                            }
                        }
                    ],
                    borderables: [],
                    fontEditable: {
                        get: () => config.font_family || defaultConfig.font_family,
                        set: (value) => {
                            config.font_family = value;
                            window.elementSdk.setConfig({ font_family: value });
                        }
                    },
                    fontSizeable: {
                        get: () => config.font_size || defaultConfig.font_size,
                        set: (value) => {
                            config.font_size = value;
                            window.elementSdk.setConfig({ font_size: value });
                        }
                    }
                }),
                mapToEditPanelValues: (config) => new Map([
                    ['main_title', config.main_title || defaultConfig.main_title],
                    ['subtitle', config.subtitle || defaultConfig.subtitle],
                    ['savings_title', config.savings_title || defaultConfig.savings_title],
                    ['exchange_title', config.exchange_title || defaultConfig.exchange_title],
                    ['quiz_title', config.quiz_title || defaultConfig.quiz_title]
                ])
            });
        }

        document.getElementById('calculate-savings').addEventListener('click', calculateSavings);
        document.getElementById('calculate-exchange').addEventListener('click', calculateExchange);
        document.getElementById('check-answers').addEventListener('click', checkQuizAnswers);
        document.getElementById('reset-quiz').addEventListener('click', resetQuiz);

        generateQuiz();
    </script>
 <script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'9c133ea070c64f5d',t:'MTc2ODk2MTEwNi4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
