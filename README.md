<html lang="th" class="h-full">
 <head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>คณิตศาสตร์การเงิน ���.5</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <script src="/_sdk/element_sdk.js"></script>
  <link href="https://fonts.googleapis.com/css2?family=Kanit:wght@300;400;500;600;700&amp;display=swap" rel="stylesheet">
  <style>
    body {
      box-sizing: border-box;
    }
    * {
      font-family: 'Kanit', sans-serif;
    }
    .coin-bounce {
      animation: bounce 0.5s ease;
    }
    @keyframes bounce {
      0%, 100% { transform: scale(1); }
      50% { transform: scale(1.2); }
    }
    .correct-animation {
      animation: correctPulse 0.6s ease;
    }
    @keyframes correctPulse {
      0% { transform: scale(1); }
      50% { transform: scale(1.05); background-color: #10b981; }
      100% { transform: scale(1); }
    }
    .wrong-animation {
      animation: shake 0.5s ease;
    }
    @keyframes shake {
      0%, 100% { transform: translateX(0); }
      25% { transform: translateX(-10px); }
      75% { transform: translateX(10px); }
    }
    .money-icon {
      filter: drop-shadow(2px 2px 4px rgba(0,0,0,0.2));
    }
  </style>
  <style>@view-transition { navigation: auto; }</style>
  <script src="/_sdk/data_sdk.js" type="text/javascript"></script>
 </head>
 <body class="h-full">
  <div id="app" class="h-full w-full overflow-auto" style="background: linear-gradient(135deg, #1e3a5f 0%, #2d5a87 50%, #3d7ab5 100%);"><!-- Header -->
   <header class="text-center py-6 px-4">
    <h1 id="main-title" class="text-3xl md:text-4xl font-bold text-white drop-shadow-lg">💰 คณิตศาสตร์การเงิน ป.5</h1>
    <p class="text-amber-200 mt-2 text-lg">เรียนรู้เรื่องเงินอย่างสนุกสนาน!</p>
   </header><!-- Score Board -->
   <div class="flex justify-center gap-4 px-4 mb-6">
    <div class="bg-white/20 backdrop-blur-sm rounded-2xl px-6 py-3 text-center">
     <div class="text-amber-300 text-sm">
      คะแนน
     </div>
     <div id="score" class="text-white text-2xl font-bold">
      0
     </div>
    </div>
    <div class="bg-white/20 backdrop-blur-sm rounded-2xl px-6 py-3 text-center">
     <div class="text-amber-300 text-sm">
      ข้อที่
     </div>
     <div id="question-num" class="text-white text-2xl font-bold">
      1/10
     </div>
    </div>
    <div class="bg-white/20 backdrop-blur-sm rounded-2xl px-6 py-3 text-center">
     <div class="text-amber-300 text-sm">
      ถูกต้อง
     </div>
     <div id="correct-count" class="text-green-400 text-2xl font-bold">
      0
     </div>
    </div>
   </div><!-- Main Game Area -->
   <main class="max-w-2xl mx-auto px-4 pb-8"><!-- Game Type Selection -->
    <div id="menu-screen" class="bg-white rounded-3xl shadow-2xl p-6 mb-6">
     <h2 class="text-xl font-bold text-gray-800 text-center mb-6">🎯 เลือกบทเรียน</h2>
     <div class="grid grid-cols-1 md:grid-cols-2 gap-4"><button onclick="startGame('counting')" class="game-btn bg-gradient-to-r from-emerald-400 to-teal-500 hover:from-emerald-500 hover:to-teal-600 text-white p-5 rounded-2xl transition-all transform hover:scale-105 shadow-lg">
       <div class="text-3xl mb-2">
        🪙
       </div>
       <div class="font-bold text-lg">
        นับเงิน
       </div>
       <div class="text-sm opacity-90">
        นับเหรียญและธนบัตร
       </div></button> <button onclick="startGame('change')" class="game-btn bg-gradient-to-r from-blue-400 to-indigo-500 hover:from-blue-500 hover:to-indigo-600 text-white p-5 rounded-2xl transition-all transform hover:scale-105 shadow-lg">
       <div class="text-3xl mb-2">
        💵
       </div>
       <div class="font-bold text-lg">
        ทอนเงิน
       </div>
       <div class="text-sm opacity-90">
        คำนวณเงินทอน
       </div></button> <button onclick="startGame('shopping')" class="game-btn bg-gradient-to-r from-pink-400 to-rose-500 hover:from-pink-500 hover:to-rose-600 text-white p-5 rounded-2xl transition-all transform hover:scale-105 shadow-lg">
       <div class="text-3xl mb-2">
        🛒
       </div>
       <div class="font-bold text-lg">
        ซื้อของ
       </div>
       <div class="text-sm opacity-90">
        คำนวณราคารวม
       </div></button> <button onclick="startGame('compare')" class="game-btn bg-gradient-to-r from-amber-400 to-orange-500 hover:from-amber-500 hover:to-orange-600 text-white p-5 rounded-2xl transition-all transform hover:scale-105 shadow-lg">
       <div class="text-3xl mb-2">
        ⚖️
       </div>
       <div class="font-bold text-lg">
        เปรียบเทียบ
       </div>
       <div class="text-sm opacity-90">
        เปรียบเทียบจำนวนเงิน
       </div></button>
     </div>
    </div><!-- Question Area -->
    <div id="question-screen" class="hidden">
     <div id="question-card" class="bg-white rounded-3xl shadow-2xl p-6 mb-6">
      <div id="question-type-badge" class="inline-block px-4 py-1 rounded-full text-sm font-medium mb-4 bg-emerald-100 text-emerald-700">
       นับเงิ��
      </div>
      <div id="question-content" class="text-center"><!-- Question will be inserted here -->
      </div>
     </div><!-- Answer Options -->
     <div id="answer-options" class="grid grid-cols-2 gap-4 mb-6"><!-- Options will be inserted here -->
     </div><!-- Feedback -->
     <div id="feedback" class="hidden text-center bg-white rounded-2xl p-4 mb-4">
      <div id="feedback-icon" class="text-4xl mb-2"></div>
      <div id="feedback-text" class="font-bold text-lg"></div>
      <div id="feedback-explanation" class="text-gray-600 mt-2"></div>
     </div><!-- Next Button --> <button id="next-btn" onclick="nextQuestion()" class="hidden w-full bg-gradient-to-r from-amber-400 to-orange-500 hover:from-amber-500 hover:to-orange-600 text-white font-bold py-4 rounded-2xl text-lg transition-all transform hover:scale-105 shadow-lg"> ข้อถัดไป ➡️ </button>
    </div><!-- Result Screen -->
    <div id="result-screen" class="hidden bg-white rounded-3xl shadow-2xl p-8 text-center">
     <div class="text-6xl mb-4">
      🎉
     </div>
     <h2 class="text-2xl font-bold text-gray-800 mb-4">เล่นจบแล้ว!</h2>
     <div class="bg-gradient-to-r from-amber-100 to-orange-100 rounded-2xl p-6 mb-6">
      <div class="text-4xl font-bold text-amber-600" id="final-score">
       0
      </div>
      <div class="text-gray-600">
       คะแนนรวม
      </div>
     </div>
     <div class="flex justify-center gap-4 mb-6">
      <div class="text-center">
       <div id="final-correct" class="text-3xl font-bold text-green-500">
        0
       </div>
       <div class="text-sm text-gray-500">
        ถูก
       </div>
      </div>
      <div class="text-center">
       <div id="final-wrong" class="text-3xl font-bold text-red-500">
        0
       </div>
       <div class="text-sm text-gray-500">
        ผิด
       </div>
      </div>
     </div>
     <div id="result-message" class="text-lg text-gray-700 mb-6"></div><button onclick="backToMenu()" class="w-full bg-gradient-to-r from-blue-400 to-indigo-500 hover:from-blue-500 hover:to-indigo-600 text-white font-bold py-4 rounded-2xl text-lg transition-all"> 🏠 กลับหน้าหลัก </button>
    </div>
   </main><!-- Footer - Creator Info -->
   <footer class="text-center py-6 px-4">
    <div class="max-w-md mx-auto bg-white/10 backdrop-blur-sm rounded-2xl p-4">
     <div class="text-amber-200 text-sm mb-2">
      👨‍💻 ผู้สร้างเกม
     </div>
     <div class="text-white font-bold text-lg">
      เด็กชายธีทัต เพ็ชรหิน
     </div>
     <div class="text-amber-100 text-sm">
      ชั้นประถมศึกษาปีที่ 5/5 สาย MEP
     </div>
    </div>
   </footer>
  </div>
  <script>
    // Default config
    const defaultConfig = {
      app_title: 'คณิตศาสตร์การเงิน ป.5',
      primary_color: '#1e3a5f',
      text_color: '#ffffff',
      accent_color: '#f59e0b',
      button_color: '#10b981',
      card_color: '#ffffff'
    };

    let config = { ...defaultConfig };

    // Game State
    let gameState = {
      currentType: '',
      currentQuestion: 0,
      totalQuestions: 10,
      score: 0,
      correctCount: 0,
      questions: [],
      answered: false
    };

    // Thai currency data
    const coins = [
      { value: 0.25, name: 'สตางค์ 25', emoji: '🪙' },
      { value: 0.50, name: 'สตางค์ 50', emoji: '🪙' },
      { value: 1, name: '1 บาท', emoji: '🪙' },
      { value: 2, name: '2 บาท', emoji: '🪙' },
      { value: 5, name: '5 บาท', emoji: '🪙' },
      { value: 10, name: '10 บาท', emoji: '🪙' }
    ];

    const bills = [
      { value: 20, name: '20 บาท', emoji: '💵', color: '#16a34a' },
      { value: 50, name: '50 บาท', emoji: '💵', color: '#2563eb' },
      { value: 100, name: '100 บาท', emoji: '💵', color: '#dc2626' },
      { value: 500, name: '500 บาท', emoji: '💵', color: '#7c3aed' },
      { value: 1000, name: '1,000 บาท', emoji: '💵', color: '#854d0e' }
    ];

    const items = [
      { name: 'ดินสอ', price: 5, emoji: '✏️' },
      { name: 'ยา���ลบ', price: 8, emoji: '🧽' },
      { name: 'ไม้บรรทัด', price: 15, emoji: '📏' },
      { name: 'สมุด', price: 20, emoji: '📓' },
      { name: 'กระเป๋าดินสอ', price: 45, emoji: '🎒' },
      { name: 'น้ำดื่ม', price: 10, emoji: '💧' },
      { name: 'ขนมปัง', price: 25, emoji: '🍞' },
      { name: 'นม', price: 15, emoji: '🥛' },
      { name: 'แอปเปิ้ล', price: 30, emoji: '🍎' },
      { name: 'กล้วย', price: 12, emoji: '🍌' },
      { name: 'ไอศกรีม', price: 20, emoji: '🍦' },
      { name: 'ลูกอม', price: 5, emoji: '🍬' }
    ];

    // Initialize SDK
    if (window.elementSdk) {
      window.elementSdk.init({
        defaultConfig,
        onConfigChange: async (newConfig) => {
          config = { ...defaultConfig, ...newConfig };
          updateUI();
        },
        mapToCapabilities: (config) => ({
          recolorables: [
            {
              get: () => config.primary_color || defaultConfig.primary_color,
              set: (value) => window.elementSdk.setConfig({ primary_color: value })
            },
            {
              get: () => config.accent_color || defaultConfig.accent_color,
              set: (value) => window.elementSdk.setConfig({ accent_color: value })
            },
            {
              get: () => config.button_color || defaultConfig.button_color,
              set: (value) => window.elementSdk.setConfig({ button_color: value })
            }
          ],
          borderables: [],
          fontEditable: undefined,
          fontSizeable: undefined
        }),
        mapToEditPanelValues: (config) => new Map([
          ['app_title', config.app_title || defaultConfig.app_title]
        ])
      });
    }

    function updateUI() {
      const title = config.app_title || defaultConfig.app_title;
      document.getElementById('main-title').textContent = '💰 ' + title;
      
      const app = document.getElementById('app');
      const primaryColor = config.primary_color || defaultConfig.primary_color;
      app.style.background = `linear-gradient(135deg, ${primaryColor} 0%, ${adjustColor(primaryColor, 40)} 50%, ${adjustColor(primaryColor, 80)} 100%)`;
    }

    function adjustColor(hex, amount) {
      const num = parseInt(hex.replace('#', ''), 16);
      const r = Math.min(255, ((num >> 16) & 0xff) + amount);
      const g = Math.min(255, ((num >> 8) & 0xff) + amount);
      const b = Math.min(255, (num & 0xff) + amount);
      return `#${((r << 16) | (g << 8) | b).toString(16).padStart(6, '0')}`;
    }

    function startGame(type) {
      gameState = {
        currentType: type,
        currentQuestion: 0,
        totalQuestions: 10,
        score: 0,
        correctCount: 0,
        questions: generateQuestions(type, 10),
        answered: false
      };

      document.getElementById('menu-screen').classList.add('hidden');
      document.getElementById('question-screen').classList.remove('hidden');
      document.getElementById('result-screen').classList.add('hidden');
      
      updateScoreboard();
      showQuestion();
    }

    function generateQuestions(type, count) {
      const questions = [];
      for (let i = 0; i < count; i++) {
        questions.push(generateQuestion(type));
      }
      return questions;
    }

    function generateQuestion(type) {
      switch(type) {
        case 'counting': return generateCountingQuestion();
        case 'change': return generateChangeQuestion();
        case 'shopping': return generateShoppingQuestion();
        case 'compare': return generateCompareQuestion();
        default: return generateCountingQuestion();
      }
    }

    function generateCountingQuestion() {
      const moneyItems = [];
      const useBills = Math.random() > 0.3;
      
      if (useBills) {
        const numBills = Math.floor(Math.random() * 3) + 1;
        for (let i = 0; i < numBills; i++) {
          const bill = bills[Math.floor(Math.random() * 3)]; // 20, 50, 100
          moneyItems.push(bill);
        }
      }
      
      const numCoins = Math.floor(Math.random() * 4) + 1;
      for (let i = 0; i < numCoins; i++) {
        const coin = coins[Math.floor(Math.random() * 4) + 2]; // 1, 2, 5, 10 บาท
        moneyItems.push(coin);
      }

      const total = moneyItems.reduce((sum, item) => sum + item.value, 0);
      
      return {
        type: 'counting',
        typeName: 'น����เงิน',
        typeColor: 'bg-emerald-100 text-emerald-700',
        moneyItems,
        correctAnswer: total,
        question: 'เงินทั้งหมดเท่ากับเท่าไร?'
      };
    }

    function generateChangeQuestion() {
      const payAmounts = [20, 50, 100, 200, 500];
      const price = Math.floor(Math.random() * 80) + 10; // 10-89 บาท
      const validPays = payAmounts.filter(p => p > price);
      const pay = validPays[Math.floor(Math.random() * validPays.length)];
      const change = pay - price;

      return {
        type: 'change',
        typeName: 'ทอนเงิน',
        typeColor: 'bg-blue-100 text-blue-700',
        price,
        pay,
        correctAnswer: change,
        question: `ซื้อของราคา ${price} บาท จ่าย ${pay} บาท ต้องได้เงินทอนเท่าไร?`
      };
    }

    function generateShoppingQuestion() {
      const numItems = Math.floor(Math.random() * 3) + 2; // 2-4 items
      const selectedItems = [];
      const usedIndexes = new Set();
      
      while (selectedItems.length < numItems) {
        const idx = Math.floor(Math.random() * items.length);
        if (!usedIndexes.has(idx)) {
          usedIndexes.add(idx);
          const item = items[idx];
          const qty = Math.floor(Math.random() * 3) + 1;
          selectedItems.push({ ...item, quantity: qty });
        }
      }

      const total = selectedItems.reduce((sum, item) => sum + (item.price * item.quantity), 0);

      return {
        type: 'shopping',
        typeName: 'ซื้อของ',
        typeColor: 'bg-pink-100 text-pink-700',
        items: selectedItems,
        correctAnswer: total,
        question: 'ต้องจ่ายเงินทั้งหมดเท่าไร?'
      };
    }

    function generateCompareQuestion() {
      const amount1 = Math.floor(Math.random() * 500) + 50;
      let amount2 = Math.floor(Math.random() * 500) + 50;
      while (amount2 === amount1) {
        amount2 = Math.floor(Math.random() * 500) + 50;
      }

      const questionTypes = [
        { text: 'มากกว่า', answer: amount1 > amount2 ? amount1 : amount2 },
        { text: '��้��ยกว่า', answer: amount1 < amount2 ? amount1 : amount2 }
      ];
      
      const qType = questionTypes[Math.floor(Math.random() * 2)];

      return {
        type: 'compare',
        typeName: 'เปรียบเทียบ',
        typeColor: 'bg-amber-100 text-amber-700',
        amount1,
        amount2,
        compareType: qType.text,
        correctAnswer: qType.answer,
        question: `จำนวนใด${qType.text}?`
      };
    }

    function showQuestion() {
      const q = gameState.questions[gameState.currentQuestion];
      gameState.answered = false;
      
      document.getElementById('question-type-badge').className = `inline-block px-4 py-1 rounded-full text-sm font-medium mb-4 ${q.typeColor}`;
      document.getElementById('question-type-badge').textContent = q.typeName;
      
      let contentHTML = '';
      
      switch(q.type) {
        case 'counting':
          contentHTML = renderCountingQuestion(q);
          break;
        case 'change':
          contentHTML = renderChangeQuestion(q);
          break;
        case 'shopping':
          contentHTML = renderShoppingQuestion(q);
          break;
        case 'compare':
          contentHTML = renderCompareQuestion(q);
          break;
      }
      
      document.getElementById('question-content').innerHTML = contentHTML;
      renderAnswerOptions(q);
      
      document.getElementById('feedback').classList.add('hidden');
      document.getElementById('next-btn').classList.add('hidden');
    }

    function renderCountingQuestion(q) {
      let moneyHTML = '<div class="flex flex-wrap justify-center gap-3 mb-4">';
      q.moneyItems.forEach(item => {
        if (item.value >= 20) {
          moneyHTML += `
            <div class="bg-gradient-to-br from-green-100 to-green-200 rounded-xl p-3 text-center shadow-md money-icon">
              <div class="text-2xl">💵</div>
              <div class="font-bold text-green-700">${item.value} บาท</div>
            </div>`;
        } else {
          moneyHTML += `
            <div class="bg-gradient-to-br from-amber-100 to-yellow-200 rounded-full w-16 h-16 flex flex-col items-center justify-center shadow-md money-icon">
              <div class="text-lg">🪙</div>
              <div class="font-bold text-amber-700 text-sm">${item.value}</div>
            </div>`;
        }
      });
      moneyHTML += '</div>';
      return moneyHTML + `<p class="text-xl font-medium text-gray-700">${q.question}</p>`;
    }

    function renderChangeQuestion(q) {
      return `
        <div class="space-y-4 mb-4">
          <div class="flex items-center justify-center gap-4">
            <div class="bg-pink-100 rounded-xl p-4 text-center">
              <div class="text-3xl">🛍️</div>
              <div class="font-bold text-pink-700">${q.price} บาท</div>
              <div class="text-sm text-gray-500">ราคาสินค้า</div>
            </div>
            <div class="text-3xl">➡️</div>
            <div class="bg-green-100 rounded-xl p-4 text-center">
              <div class="text-3xl">💵</div>
              <div class="font-bold text-green-700">${q.pay} บาท</div>
              <div class="text-sm text-gray-500">จ่ายเงิน</div>
            </div>
          </div>
        </div>
        <p class="text-xl font-medium text-gray-700">${q.question}</p>`;
    }

    function renderShoppingQuestion(q) {
      let itemsHTML = '<div class="grid grid-cols-2 gap-3 mb-4">';
      q.items.forEach(item => {
        itemsHTML += `
          <div class="bg-gray-50 rounded-xl p-3 text-center">
            <div class="text-3xl">${item.emoji}</div>
            <div class="font-medium text-gray-700">${item.name}</div>
            <div class="text-sm text-gray-500">${item.price} บาท × ${item.quantity}</div>
            <div class="font-bold text-blue-600">${item.price * item.quantity} บาท</div>
          </div>`;
      });
      itemsHTML += '</div>';
      return itemsHTML + `<p class="text-xl font-medium text-gray-700">${q.question}</p>`;
    }

    function renderCompareQuestion(q) {
      return `
        <div class="flex items-center justify-center gap-6 mb-4">
          <div class="bg-blue-100 rounded-2xl p-6 text-center">
            <div class="text-4xl font-bold text-blue-700">${q.amount1}</div>
            <div class="text-sm text-gray-500">บาท</div>
          </div>
          <div class="text-4xl">🆚</div>
          <div class="bg-purple-100 rounded-2xl p-6 text-center">
            <div class="text-4xl font-bold text-purple-700">${q.amount2}</div>
            <div class="text-sm text-gray-500">บาท</div>
          </div>
        </div>
        <p class="text-xl font-medium text-gray-700">${q.question}</p>`;
    }

    function renderAnswerOptions(q) {
      const options = generateOptions(q);
      let optionsHTML = '';
      
      options.forEach((opt, idx) => {
        optionsHTML += `
          <button onclick="checkAnswer(${opt}, ${q.correctAnswer})" 
                  class="answer-btn bg-white hover:bg-gray-50 border-3 border-gray-200 hover:border-blue-400 rounded-2xl p-4 text-center transition-all transform hover:scale-105 shadow-md"
                  data-value="${opt}">
            <div class="text-3xl font-bold text-gray-700">${opt}</div>
            <div class="text-gray-500">บาท</div>
          </button>`;
      });
      
      document.getElementById('answer-options').innerHTML = optionsHTML;
    }

    function generateOptions(q) {
      const correct = q.correctAnswer;
      const options = new Set([correct]);
      
      while (options.size < 4) {
        let wrong;
        const variance = Math.max(10, Math.floor(correct * 0.3));
        wrong = correct + (Math.floor(Math.random() * variance * 2) - variance);
        if (wrong > 0 && wrong !== correct) {
          options.add(wrong);
        }
      }
      
      return Array.from(options).sort(() => Math.random() - 0.5);
    }

    function checkAnswer(selected, correct) {
      if (gameState.answered) return;
      gameState.answered = true;
      
      const isCorrect = selected === correct;
      const buttons = document.querySelectorAll('.answer-btn');
      
      buttons.forEach(btn => {
        const val = parseInt(btn.dataset.value);
        if (val === correct) {
          btn.classList.remove('border-gray-200');
          btn.classList.add('border-green-500', 'bg-green-50');
          if (isCorrect) btn.classList.add('correct-animation');
        } else if (val === selected && !isCorrect) {
          btn.classList.remove('border-gray-200');
          btn.classList.add('border-red-500', 'bg-red-50', 'wrong-animation');
        }
        btn.disabled = true;
      });
      
      const feedback = document.getElementById('feedback');
      const feedbackIcon = document.getElementById('feedback-icon');
      const feedbackText = document.getElementById('feedback-text');
      const feedbackExplanation = document.getElementById('feedback-explanation');
      
      if (isCorrect) {
        gameState.score += 10;
        gameState.correctCount++;
        feedbackIcon.textContent = '🎉';
        feedbackText.textContent = 'ถูกต้อง!';
        feedbackText.className = 'font-bold text-lg text-green-600';
        feedbackExplanation.textContent = 'เก่งมาก! ได้ 10 คะแนน';
      } else {
        feedbackIcon.textContent = '😢';
        feedbackText.textContent = 'ไม่ถูกต้อง';
        feedbackText.className = 'font-bold text-lg text-red-600';
        feedbackExplanation.textContent = `คำตอบที่ถูกต้องคือ ${correct} บาท`;
      }
      
      feedback.classList.remove('hidden');
      document.getElementById('next-btn').classList.remove('hidden');
      
      updateScoreboard();
    }

    function nextQuestion() {
      gameState.currentQuestion++;
      
      if (gameState.currentQuestion >= gameState.totalQuestions) {
        showResults();
      } else {
        showQuestion();
        updateScoreboard();
      }
    }

    function updateScoreboard() {
      document.getElementById('score').textContent = gameState.score;
      document.getElementById('question-num').textContent = `${gameState.currentQuestion + 1}/${gameState.totalQuestions}`;
      document.getElementById('correct-count').textContent = gameState.correctCount;
    }

    function showResults() {
      document.getElementById('question-screen').classList.add('hidden');
      document.getElementById('result-screen').classList.remove('hidden');
      
      const wrong = gameState.totalQuestions - gameState.correctCount;
      
      document.getElementById('final-score').textContent = gameState.score;
      document.getElementById('final-correct').textContent = gameState.correctCount;
      document.getElementById('final-wrong').textContent = wrong;
      
      let message = '';
      const percent = (gameState.correctCount / gameState.totalQuestions) * 100;
      
      if (percent === 100) {
        message = '🌟 สุดยอดมาก! คะแนนเต็ม! 🌟';
      } else if (percent >= 80) {
        message = '⭐ เก่งมาก! ทำได้ดีเยี่ยม! ⭐';
      } else if (percent >= 60) {
        message = '👍 ดีมาก! พยาย���มต่อไปนะ!';
      } else if (percent >= 40) {
        message = '💪 ไม่เป็นไร ลองอีกครั้งนะ!';
      } else {
        message = '📚 ฝึกฝนเพิ่มเติม แล้วลองใหม่อีกครั้ง!';
      }
      
      document.getElementById('result-message').textContent = message;
    }

    function backToMenu() {
      document.getElementById('menu-screen').classList.remove('hidden');
      document.getElementById('question-screen').classList.add('hidden');
      document.getElementById('result-screen').classList.add('hidden');
      
      gameState = {
        currentType: '',
        currentQuestion: 0,
        totalQuestions: 10,
        score: 0,
        correctCount: 0,
        questions: [],
        answered: false
      };
      
      document.getElementById('score').textContent = '0';
      document.getElementById('question-num').textContent = '1/10';
      document.getElementById('correct-count').textContent = '0';
    }

    // Initialize
    updateUI();
  </script>
 <script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'9c0b9303c4847336',t:'MTc2ODg4MDY3Ny4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>**
