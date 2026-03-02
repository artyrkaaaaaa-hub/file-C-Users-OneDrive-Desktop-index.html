[index.html](https://github.com/user-attachments/files/25691199/index.html)
<!doctype html>
<html lang="ru" class="h-full">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Цифровой Щит</title>
<script src="https://cdn.tailwindcss.com/3.4.17"></script>
<script src="/_sdk/element_sdk.js"></script>
<link href="https://fonts.googleapis.com/css2?family=Nunito:wght@400;600;700;800&amp;display=swap" rel="stylesheet">
<style>
* { font-family: 'Nunito', sans-serif; }

.neo-card {
background: linear-gradient(145deg, #ffffff, #f0f4f8);
box-shadow: 8px 8px 20px #d1d9e6, -8px -8px 20px #ffffff;
border-radius: 20px;
}

.neo-btn {
background: linear-gradient(145deg, #4a90d9, #3a7bc8);
box-shadow: 4px 4px 12px #d1d9e6, -4px -4px 12px #ffffff;
transition: all 0.3s ease;
}

.neo-btn:hover {
transform: translateY(-2px);
box-shadow: 6px 6px 16px #d1d9e6, -6px -6px 16px #ffffff;
}

.neo-btn:active {
transform: translateY(0);
box-shadow: inset 2px 2px 5px rgba(0,0,0,0.1);
}

.chapter-card {
background: linear-gradient(145deg, #ffffff, #f8fafc);
box-shadow: 5px 5px 15px #e2e8f0, -5px -5px 15px #ffffff;
transition: all 0.3s ease;
}

.chapter-card:hover {
transform: translateY(-3px);
box-shadow: 8px 8px 20px #d1d9e6, -8px -8px 20px #ffffff;
}

.option-btn {
background: linear-gradient(145deg, #f8fafc, #edf2f7);
box-shadow: 3px 3px 8px #e2e8f0, -3px -3px 8px #ffffff;
transition: all 0.2s ease;
}

.option-btn:hover:not(.selected):not(:disabled) {
background: linear-gradient(145deg, #edf2f7, #e2e8f0);
}

.option-btn.selected {
background: linear-gradient(145deg, #4a90d9, #3a7bc8);
color: white;
box-shadow: inset 2px 2px 5px rgba(0,0,0,0.15);
}

.phone-screen {
background: linear-gradient(180deg, #1a1a2e 0%, #16213e 100%);
border-radius: 30px;
box-shadow: 0 25px 50px rgba(0,0,0,0.3);
}

.phone-notch {
background: #0f0f23;
border-radius: 0 0 20px 20px;
}

.call-pulse {
animation: pulse 2s infinite;
}

@keyframes pulse {
0%, 100% { transform: scale(1); opacity: 1; }
50% { transform: scale(1.05); opacity: 0.8; }
}

.message-bubble {
animation: slideIn 0.4s ease-out;
}

@keyframes slideIn {
from { opacity: 0; transform: translateY(10px); }
to { opacity: 1; transform: translateY(0); }
}

.fade-in {
animation: fadeIn 0.5s ease-out;
}

@keyframes fadeIn {
from { opacity: 0; }
to { opacity: 1; }
}

.slide-up {
animation: slideUp 0.5s ease-out;
}

@keyframes slideUp {
from { opacity: 0; transform: translateY(20px); }
to { opacity: 1; transform: translateY(0); }
}

.success-icon {
animation: successBounce 0.6s ease-out;
}

@keyframes successBounce {
0% { transform: scale(0); }
50% { transform: scale(1.2); }
100% { transform: scale(1); }
}

.confetti {
position: absolute;
width: 10px;
height: 10px;
border-radius: 2px;
animation: confettiFall 3s ease-out forwards;
}

@keyframes confettiFall {
0% { transform: translateY(-100px) rotate(0deg); opacity: 1; }
100% { transform: translateY(400px) rotate(720deg); opacity: 0; }
}
</style>
<style>body { box-sizing: border-box; }</style>
<script src="/_sdk/data_sdk.js" type="text/javascript"></script>
</head>
<body class="h-full bg-gradient-to-br from-slate-100 via-blue-50 to-slate-100 overflow-auto">
<div id="app" class="min-h-full w-full"></div>
<script>
const defaultConfig = {
app_title: 'Цифровой Щит',
hero_subtitle: 'Научись распознавать мошенников',
primary_color: '#4a90d9',
secondary_color: '#1e3a5f',
accent_color: '#22c55e',
text_color: '#334155',
bg_color: '#f1f5f9',
font_family: 'Nunito'
};

let config = { ...defaultConfig };

const chapters = [
{
id: 1,
emoji: '📦',
title: 'Золотая доставка',
story: 'Катя заказала новый смартфон на маркетплейсе и с нетерпением ждёт курьера. Телефон должен прийти сегодня, и она постоянно проверяет статус заказа...',
caller: 'СЛУЖБА ДОСТАВКИ',
callerIcon: '🚚',
scammerMsg: 'Екатерина, здравствуйте! Курьер уже выехал, но из-за загруженности мы не успеваем. Чтобы получить заказ сегодня, перейдите по ссылке и оплатите ускоренную доставку (всего 50 рублей).',
katyaMsg: 'Ой, а ссылку прислать можете? Я прямо сейчас оплачу.',
question: 'Что делать, если курьер просит перейти по ссылке для оплаты?',
options: [
{ id: 'A', text: 'Перейти по ссылке и ввести данные карты' },
{ id: 'B', text: 'Положить трубку и проверить статус заказа в официальном приложении' },
{ id: 'C', text: 'Попросить прислать ссылку в СМС, чтобы оплатить позже' },
{ id: 'D', text: 'Отказаться от заказа' }
],
correct: 'B',
explanation: 'Настоящие службы доставки никогда не просят оплату через сторонние ссылки! Всегда проверяйте информацию в официальном приложении магазина. Мошенники создают поддельные страницы оплаты, чтобы украсть данные вашей карты.'
},
{
id: 2,
emoji: '🏦',
title: 'Служба безопасности',
story: 'Кате пришло СМС о подозрительном входе в личный кабинет банка. Сердце ёкнуло — неужели взломали? Сразу после этого звонит телефон...',
caller: 'БАНК РОССИИ',
callerIcon: '🏛️',
scammerMsg: 'Катя, это служба безопасности банка. На ваше имя пытаются оформить кредит на 500 000 рублей. Чтобы отменить заявку, срочно назовите код из СМС.',
katyaMsg: 'Какой код? Мне только что пришло сообщение... Сейчас продиктую.',
question: 'Ваши действия при звонке "из банка" с просьбой назвать код?',
options: [
{ id: 'A', text: 'Назвать код, чтобы спасти свои деньги' },
{ id: 'B', text: 'Сбросить звонок и позвонить в банк по номеру с карты' },
{ id: 'C', text: 'Попросить перезвонить позже' },
{ id: 'D', text: 'Записать код и отправить в ответном СМС' }
],
correct: 'B',
explanation: 'Банк НИКОГДА не запрашивает коды из СМС по телефону! Это главное правило безопасности. Код из СМС — это ключ к вашим деньгам. Если сомневаетесь — положите трубку и сами перезвоните в банк по номеру на обороте карты.'
},
{
id: 3,
emoji: '👮',
title: 'Капитан полиции',
story: 'Обычный вечер. Катя смотрит сериал, когда раздаётся звонок с незнакомого номера. Голос на том конце провода звучит очень серьёзно и официально...',
caller: 'МВД РОССИИ',
callerIcon: '🚔',
scammerMsg: 'Это капитан Сидоров, отдел по борьбе с мошенничеством. Ваши данные скомпрометированы. Для защиты средств необходимо перевести деньги на безопасный счёт. Это секретная операция, никому не сообщайте!',
katyaMsg: 'Ой, капитан, а что мне делать? Я очень волнуюсь за свои сбережения...',
question: 'Что делать, если "полицейский" просит перевести деньги на "безопасный счёт"?',
options: [
{ id: 'A', text: 'Выполнить инструкции, ведь это полиция' },
{ id: 'B', text: 'Прекратить разговор — полиция так не работает' },
{ id: 'C', text: 'Попросить прислать документы на почту' },
{ id: 'D', text: 'Перевести часть денег для проверки' }
],
correct: 'B',
explanation: 'Полиция НИКОГДА не просит переводить деньги на "безопасные счета"! Это классическая схема мошенничества. Настоящие полицейские работают через официальные каналы и повестки, а не по телефону. Любой "секретный" разговор — признак обмана.'
},
{
id: 4,
emoji: '💼',
title: 'Выгодная работа',
story: 'Катя ищет подработку и разместила резюме на сайте вакансий. Приходит сообщение в мессенджер от "крупной компании" с очень заманчивым предложением...',
caller: 'HR МЕНЕДЖЕР',
callerIcon: '👔',
scammerMsg: 'Поздравляем! Вы прошли отбор на удалённую работу с зарплатой 150 000₽/мес. Для оформления нужно оплатить регистрационный взнос 3000₽ и прислать фото паспорта.',
katyaMsg: 'Вау, это супер! А куда переводить деньги? И паспорт прямо сейчас сфотографировать?',
question: 'Вам предлагают высокооплачиваемую работу, но просят оплатить "взнос". Ваши действия?',
options: [
{ id: 'A', text: 'Оплатить взнос — это инвестиция в карьеру' },
{ id: 'B', text: 'Отказаться — честные работодатели не берут деньги с соискателей' },
{ id: 'C', text: 'Отправить паспорт, но не платить' },
{ id: 'D', text: 'Попросить скидку на взнос' }
],
correct: 'B',
explanation: 'Настоящие работодатели НИКОГДА не просят деньги за трудоустройство! Это мошенничество. А фото паспорта мошенники используют для оформления кредитов на ваше имя. Запомните: вам платят за работу, а не вы за возможность работать.'
},
{
id: 5,
emoji: '📞',
title: 'Оператор связи',
story: 'Катя получает СМС: "Ваш номер будет заблокирован через 24 часа". Через минуту звонит "оператор" с предложением решить проблему...',
caller: 'МОБИЛЬНЫЙ ОПЕРАТОР',
callerIcon: '📱',
scammerMsg: 'Ваш договор истекает, номер будет передан другому абоненту. Для продления назовите код из СМС или установите приложение для верификации по ссылке.',
katyaMsg: 'Ой нет, я не хочу потерять номер! Что нужно сделать?',
question: 'Оператор просит код из СМС для "продления номера". Что делать?',
options: [
{ id: 'A', text: 'Назвать код, чтобы сохранить номер' },
{ id: 'B', text: 'Положить трубку и позвонить оператору по официальному номеру' },
{ id: 'C', text: 'Установить приложение по ссылке' },
{ id: 'D', text: 'Попросить прислать код повторно' }
],
correct: 'B',
explanation: 'Операторы связи не блокируют номера внезапно и не просят коды по телефону! Мошенники используют страх потери номера, чтобы получить доступ к вашим аккаунтам. Всегда проверяйте информацию через официальное приложение оператора или салон связи.'
}
];

let currentScreen = 'welcome';
let currentChapter = null;
let currentStep = 'story';
let selectedAnswer = null;
let completedChapters = [];

function render() {
const app = document.getElementById('app');
const fontFamily = config.font_family || defaultConfig.font_family;

app.style.fontFamily = `${fontFamily}, sans-serif`;

switch(currentScreen) {
case 'welcome':
renderWelcome();
break;
case 'chapters':
renderChapters();
break;
case 'game':
renderGame();
break;
}
}

function renderWelcome() {
const app = document.getElementById('app');
app.innerHTML = `
<div class="min-h-full flex items-center justify-center p-4 sm:p-6">
<div class="neo-card p-6 sm:p-10 max-w-md w-full text-center fade-in">
<div class="text-6xl sm:text-7xl mb-4 sm:mb-6">🛡️</div>
<h1 id="main-title" class="text-2xl sm:text-3xl font-extrabold mb-2 sm:mb-3" style="color: ${config.secondary_color}">${config.app_title}</h1>
<p id="main-subtitle" class="text-base sm:text-lg mb-6 sm:mb-8" style="color: ${config.text_color}">${config.hero_subtitle}</p>

<div class="space-y-3 sm:space-y-4 mb-6 sm:mb-8 text-left">
<div class="flex items-center gap-3 p-3 rounded-xl bg-blue-50">
<span class="text-xl sm:text-2xl">📖</span>
<span class="text-sm sm:text-base" style="color: ${config.text_color}">5 реальных историй о мошенниках</span>
</div>
<div class="flex items-center gap-3 p-3 rounded-xl bg-green-50">
<span class="text-xl sm:text-2xl">🎯</span>
<span class="text-sm sm:text-base" style="color: ${config.text_color}">Учись принимать правильные решения</span>
</div>
<div class="flex items-center gap-3 p-3 rounded-xl bg-amber-50">
<span class="text-xl sm:text-2xl">💡</span>
<span class="text-sm sm:text-base" style="color: ${config.text_color}">Узнай, как защитить себя и близких</span>
</div>
</div>

<button onclick="startGame()" class="neo-btn w-full py-3 sm:py-4 px-6 sm:px-8 text-white text-base sm:text-lg font-bold rounded-2xl">
Начать обучение
</button>

<p class="mt-4 sm:mt-6 text-xs sm:text-sm opacity-60" style="color: ${config.text_color}">
Главная героиня — Катя. Помоги ей не попасться на уловки мошенников!
</p>
</div>
</div>
`;
}

function renderChapters() {
const app = document.getElementById('app');
const chaptersHtml = chapters.map(ch => {
const isCompleted = completedChapters.includes(ch.id);
return `
<div class="chapter-card p-4 sm:p-5 rounded-2xl ${isCompleted ? 'border-2 border-green-400' : ''}">
<div class="flex items-start gap-3 sm:gap-4">
<div class="text-3xl sm:text-4xl flex-shrink-0">${ch.emoji}</div>
<div class="flex-1 min-w-0">
<div class="flex items-center gap-2 mb-1">
<h3 class="font-bold text-sm sm:text-base" style="color: ${config.secondary_color}">Глава ${ch.id}</h3>
${isCompleted ? '<span class="text-green-500 text-lg">✓</span>' : ''}
</div>
<p class="text-base sm:text-lg font-semibold mb-2" style="color: ${config.text_color}">${ch.title}</p>
<button onclick="selectChapter(${ch.id})" class="neo-btn py-2 px-4 sm:px-5 text-white text-xs sm:text-sm font-semibold rounded-xl">
${isCompleted ? 'Пройти снова' : 'Начать квест'}
</button>
</div>
</div>
</div>
`;
}).join('');

const completedCount = completedChapters.length;
const progress = (completedCount / chapters.length) * 100;

app.innerHTML = `
<div class="min-h-full p-4 sm:p-6 fade-in">
<div class="max-w-lg mx-auto">
<div class="text-center mb-6 sm:mb-8">
<div class="text-4xl sm:text-5xl mb-2 sm:mb-3">🛡️</div>
<h1 id="chapters-title" class="text-xl sm:text-2xl font-extrabold mb-2" style="color: ${config.secondary_color}">${config.app_title}</h1>
<p class="text-sm sm:text-base" style="color: ${config.text_color}">Выбери главу для прохождения</p>
</div>

<div class="neo-card p-3 sm:p-4 mb-4 sm:mb-6">
<div class="flex justify-between items-center mb-2">
<span class="text-xs sm:text-sm font-semibold" style="color: ${config.text_color}">Прогресс обучения</span>
<span class="text-xs sm:text-sm font-bold" style="color: ${config.primary_color}">${completedCount}/${chapters.length}</span>
</div>
<div class="h-2 sm:h-3 bg-gray-200 rounded-full overflow-hidden">
<div class="h-full rounded-full transition-all duration-500" style="width: ${progress}%; background: linear-gradient(90deg, ${config.primary_color}, ${config.accent_color})"></div>
</div>
</div>

<div class="space-y-3 sm:space-y-4">
${chaptersHtml}
</div>

${completedCount === chapters.length ? `
<div class="mt-6 sm:mt-8 neo-card p-4 sm:p-6 text-center bg-gradient-to-r from-green-50 to-emerald-50">
<div class="text-4xl sm:text-5xl mb-2 sm:mb-3">🏆</div>
<h3 class="text-lg sm:text-xl font-bold text-green-600 mb-1 sm:mb-2">Поздравляем!</h3>
<p class="text-sm sm:text-base text-green-700">Вы прошли все главы и теперь знаете, как защититься от мошенников!</p>
</div>
` : ''}
</div>
</div>
`;
}

function renderGame() {
if (!currentChapter) return;

switch(currentStep) {
case 'story':
renderStory();
break;
case 'call':
renderCall();
break;
case 'question':
renderQuestion();
break;
case 'result':
renderResult();
break;
}
}

function renderStory() {
const ch = currentChapter;
const app = document.getElementById('app');

app.innerHTML = `
<div class="min-h-full p-4 sm:p-6 flex items-center justify-center fade-in">
<div class="max-w-md w-full">
<div class="neo-card p-5 sm:p-8">
<div class="flex items-center gap-2 sm:gap-3 mb-4 sm:mb-6">
<span class="text-3xl sm:text-4xl">${ch.emoji}</span>
<div>
<p class="text-xs sm:text-sm font-semibold" style="color: ${config.primary_color}">Глава ${ch.id}</p>
<h2 class="text-lg sm:text-xl font-bold" style="color: ${config.secondary_color}">${ch.title}</h2>
</div>
</div>

<div class="relative mb-6 sm:mb-8">
<div class="absolute left-0 top-0 bottom-0 w-1 rounded-full" style="background: ${config.primary_color}"></div>
<p class="pl-4 sm:pl-5 text-sm sm:text-base leading-relaxed" style="color: ${config.text_color}">${ch.story}</p>
</div>

<div class="flex items-center justify-center gap-2 mb-4 sm:mb-6 text-sm sm:text-base" style="color: ${config.text_color}">
<span class="animate-pulse">📱</span>
<span class="font-medium">Входящий звонок...</span>
</div>

<button onclick="nextStep()" class="neo-btn w-full py-3 sm:py-4 text-white font-bold rounded-2xl text-sm sm:text-base">
Ответить на звонок
</button>
</div>
</div>
</div>
`;
}

function renderCall() {
const ch = currentChapter;
const app = document.getElementById('app');

app.innerHTML = `
<div class="min-h-full p-4 sm:p-6 flex items-center justify-center fade-in">
<div class="max-w-sm w-full">
<div class="phone-screen p-4 sm:p-6 text-white">
<div class="phone-notch w-24 sm:w-32 h-5 sm:h-6 mx-auto mb-4 sm:mb-6"></div>

<div class="text-center mb-4 sm:mb-6 call-pulse">
<div class="w-16 h-16 sm:w-20 sm:h-20 mx-auto mb-3 sm:mb-4 rounded-full bg-gradient-to-br from-red-500 to-red-600 flex items-center justify-center text-3xl sm:text-4xl shadow-lg">
${ch.callerIcon}
</div>
<p class="text-xs sm:text-sm text-gray-400 mb-1">Входящий звонок</p>
<h3 class="text-base sm:text-lg font-bold">${ch.caller}</h3>
</div>

<div class="space-y-3 sm:space-y-4 mb-6 sm:mb-8">
<div class="message-bubble bg-gray-700 rounded-2xl rounded-tl-sm p-3 sm:p-4 max-w-[85%]">
<p class="text-xs sm:text-sm text-gray-300 mb-1">Мошенник:</p>
<p class="text-xs sm:text-sm">${ch.scammerMsg}</p>
</div>

<div class="message-bubble bg-blue-600 rounded-2xl rounded-tr-sm p-3 sm:p-4 max-w-[85%] ml-auto" style="animation-delay: 0.3s">
<p class="text-xs sm:text-sm text-blue-200 mb-1">Катя:</p>
<p class="text-xs sm:text-sm">${ch.katyaMsg}</p>
</div>
</div>

<button onclick="nextStep()" class="w-full py-3 sm:py-4 bg-gradient-to-r from-green-500 to-emerald-500 rounded-2xl font-bold text-sm sm:text-base shadow-lg">
Далее →
</button>
</div>
</div>
</div>
`;
}

function renderQuestion() {
const ch = currentChapter;
const app = document.getElementById('app');

const optionsHtml = ch.options.map(opt => `
<button onclick="selectAnswer('${opt.id}')" class="option-btn w-full p-3 sm:p-4 rounded-xl text-left transition-all ${selectedAnswer === opt.id ? 'selected' : ''}" ${selectedAnswer && selectedAnswer !== opt.id ? 'style="opacity: 0.6"' : ''}>
<div class="flex items-start gap-2 sm:gap-3">
<span class="w-6 h-6 sm:w-8 sm:h-8 flex-shrink-0 rounded-full flex items-center justify-center font-bold text-xs sm:text-sm ${selectedAnswer === opt.id ? 'bg-white/20 text-white' : 'bg-gray-200'}" style="${selectedAnswer !== opt.id ? 'color: ' + config.secondary_color : ''}">${opt.id}</span>
<span class="text-xs sm:text-sm font-medium pt-0.5 sm:pt-1">${opt.text}</span>
</div>
</button>
`).join('');

app.innerHTML = `
<div class="min-h-full p-4 sm:p-6 flex items-center justify-center fade-in">
<div class="max-w-md w-full">
<div class="neo-card p-5 sm:p-8">
<div class="flex items-center gap-2 mb-4 sm:mb-6">
<span class="text-2xl sm:text-3xl">🤔</span>
<h2 class="text-base sm:text-lg font-bold" style="color: ${config.secondary_color}">Как поступить?</h2>
</div>

<div class="p-3 sm:p-4 rounded-xl mb-4 sm:mb-6" style="background: linear-gradient(135deg, ${config.primary_color}15, ${config.primary_color}05)">
<p class="text-sm sm:text-base font-medium" style="color: ${config.text_color}">${ch.question}</p>
</div>

<div class="space-y-2 sm:space-y-3 mb-6 sm:mb-8">
${optionsHtml}
</div>

<button onclick="checkAnswer()" class="neo-btn w-full py-3 sm:py-4 text-white font-bold rounded-2xl text-sm sm:text-base disabled:opacity-50 disabled:cursor-not-allowed" ${!selectedAnswer ? 'disabled' : ''}>
Проверить ответ
</button>
</div>
</div>
</div>
`;
}

function renderResult() {
const ch = currentChapter;
const isCorrect = selectedAnswer === ch.correct;
const app = document.getElementById('app');

let confettiHtml = '';
if (isCorrect) {
const colors = ['#22c55e', '#3b82f6', '#f59e0b', '#ec4899', '#8b5cf6'];
for (let i = 0; i < 20; i++) {
const left = Math.random() * 100;
const delay = Math.random() * 0.5;
const color = colors[Math.floor(Math.random() * colors.length)];
confettiHtml += `<div class="confetti" style="left: ${left}%; animation-delay: ${delay}s; background: ${color};"></div>`;
}
}

app.innerHTML = `
<div class="min-h-full p-4 sm:p-6 flex items-center justify-center fade-in relative overflow-hidden">
${confettiHtml}
<div class="max-w-md w-full relative z-10">
<div class="neo-card p-5 sm:p-8 ${isCorrect ? 'bg-gradient-to-br from-green-50 to-emerald-50' : 'bg-gradient-to-br from-red-50 to-orange-50'}">
<div class="text-center mb-4 sm:mb-6">
<div class="text-5xl sm:text-6xl mb-3 sm:mb-4 success-icon">${isCorrect ? '🎉' : '😔'}</div>
<h2 class="text-xl sm:text-2xl font-extrabold mb-1 sm:mb-2 ${isCorrect ? 'text-green-600' : 'text-red-600'}">
${isCorrect ? 'Отлично!' : 'Неверно'}
</h2>
<p class="text-sm sm:text-base ${isCorrect ? 'text-green-700' : 'text-red-700'}">
${isCorrect ? 'Вы приняли правильное решение!' : 'К сожалению, это был неверный выбор'}
</p>
</div>

<div class="p-3 sm:p-4 rounded-xl mb-4 sm:mb-6 ${isCorrect ? 'bg-green-100' : 'bg-red-100'}">
<div class="flex items-start gap-2 sm:gap-3">
<span class="text-lg sm:text-xl flex-shrink-0">💡</span>
<p class="text-xs sm:text-sm ${isCorrect ? 'text-green-800' : 'text-red-800'}">${ch.explanation}</p>
</div>
</div>

<div class="p-3 sm:p-4 rounded-xl mb-6 sm:mb-8 bg-white/50">
<p class="text-xs sm:text-sm mb-2" style="color: ${config.text_color}"><strong>Правильный ответ:</strong></p>
<div class="flex items-start gap-2">
<span class="w-6 h-6 sm:w-7 sm:h-7 flex-shrink-0 rounded-full flex items-center justify-center font-bold text-xs sm:text-sm text-white" style="background: ${config.accent_color}">${ch.correct}</span>
<span class="text-xs sm:text-sm pt-0.5" style="color: ${config.text_color}">${ch.options.find(o => o.id === ch.correct).text}</span>
</div>
</div>

<div class="space-y-2 sm:space-y-3">
${ch.id < chapters.length ? `
<button onclick="nextChapter()" class="neo-btn w-full py-3 sm:py-4 text-white font-bold rounded-2xl text-sm sm:text-base">
Следующая глава →
</button>
` : ''}
<button onclick="goToChapters()" class="w-full py-3 sm:py-4 rounded-2xl font-bold text-sm sm:text-base border-2 transition-colors" style="border-color: ${config.primary_color}; color: ${config.primary_color}">
В Цифровой Щит
</button>
</div>
</div>
</div>
</div>
`;
}

function startGame() {
currentScreen = 'chapters';
render();
}

function selectChapter(id) {
currentChapter = chapters.find(ch => ch.id === id);
currentStep = 'story';
selectedAnswer = null;
currentScreen = 'game';
render();
}

function nextStep() {
if (currentStep === 'story') {
currentStep = 'call';
} else if (currentStep === 'call') {
currentStep = 'question';
}
render();
}

function selectAnswer(id) {
selectedAnswer = id;
render();
}

function checkAnswer() {
if (!selectedAnswer) return;

const isCorrect = selectedAnswer === currentChapter.correct;
if (isCorrect && !completedChapters.includes(currentChapter.id)) {
completedChapters.push(currentChapter.id);
}

currentStep = 'result';
render();
}

function nextChapter() {
const nextId = currentChapter.id + 1;
if (nextId <= chapters.length) {
selectChapter(nextId);
} else {
goToChapters();
}
}

function goToChapters() {
currentScreen = 'chapters';
currentChapter = null;
currentStep = 'story';
selectedAnswer = null;
render();
}

async function onConfigChange(newConfig) {
config = { ...config, ...newConfig };

const fontFamily = config.font_family || defaultConfig.font_family;
document.body.style.fontFamily = `${fontFamily}, sans-serif`;

render();
}

function mapToCapabilities(cfg) {
return {
recolorables: [
{
get: () => cfg.bg_color || defaultConfig.bg_color,
set: (v) => { cfg.bg_color = v; window.elementSdk.setConfig({ bg_color: v }); }
},
{
get: () => cfg.text_color || defaultConfig.text_color,
set: (v) => { cfg.text_color = v; window.elementSdk.setConfig({ text_color: v }); }
},
{
get: () => cfg.primary_color || defaultConfig.primary_color,
set: (v) => { cfg.primary_color = v; window.elementSdk.setConfig({ primary_color: v }); }
},
{
get: () => cfg.secondary_color || defaultConfig.secondary_color,
set: (v) => { cfg.secondary_color = v; window.elementSdk.setConfig({ secondary_color: v }); }
},
{
get: () => cfg.accent_color || defaultConfig.accent_color,
set: (v) => { cfg.accent_color = v; window.elementSdk.setConfig({ accent_color: v }); }
}
],
borderables: [],
fontEditable: {
get: () => cfg.font_family || defaultConfig.font_family,
set: (v) => { cfg.font_family = v; window.elementSdk.setConfig({ font_family: v }); }
},
fontSizeable: undefined
};
}

function mapToEditPanelValues(cfg) {
return new Map([
['app_title', cfg.app_title || defaultConfig.app_title],
['hero_subtitle', cfg.hero_subtitle || defaultConfig.hero_subtitle]
]);
}

if (window.elementSdk) {
window.elementSdk.init({
defaultConfig,
onConfigChange,
mapToCapabilities,
mapToEditPanelValues
});
}

render();
</script>
<script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'9d61e5a9e7a8d20a',t:'MTc3MjQ3MDE5MS4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
