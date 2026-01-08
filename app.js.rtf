{\rtf1\ansi\ansicpg936\cocoartf2867
\cocoatextscaling0\cocoaplatform0{\fonttbl\f0\fswiss\fcharset0 Helvetica;}
{\colortbl;\red255\green255\blue255;}
{\*\expandedcolortbl;;}
\paperw11900\paperh16840\margl1440\margr1440\vieww11520\viewh8400\viewkind0
\pard\tx566\tx1133\tx1700\tx2267\tx2834\tx3401\tx3968\tx4535\tx5102\tx5669\tx6236\tx6803\pardirnatural\partightenfactor0

\f0\fs24 \cf0 const $ = (id) => document.getElementById(id);\
\
const stateKey = "AVA_APP_STATE_V1";\
\
function loadState()\{\
  const raw = localStorage.getItem(stateKey);\
  if(!raw)\{\
    return \{\
      cnOn: true,\
      done: \{ words:false, math:false, phonics:false \},\
      streak: 0,\
      lastDoneDate: null,\
      vocabStatus: \{\}, // wordId -> "know"|"review"|"not_sure"\
    \};\
  \}\
  try \{ return JSON.parse(raw); \} catch \{ return null; \}\
\}\
\
function saveState(s)\{ localStorage.setItem(stateKey, JSON.stringify(s)); \}\
\
let S = loadState() || \{\
  cnOn:true, done:\{words:false, math:false, phonics:false\},\
  streak:0, lastDoneDate:null, vocabStatus:\{\}\
\};\
\
function setCN(on)\{\
  S.cnOn = on;\
  saveState(S);\
  document.querySelectorAll(".cn").forEach(el => \{\
    el.style.display = on ? "" : "none";\
  \});\
  $("btnCN").textContent = on ? "\uc0\u25552 \u31034  ON" : "\u25552 \u31034  OFF";\
  $("btnCN").setAttribute("aria-pressed", String(on));\
\}\
\
function showPage(name)\{\
  const pages = ["today","vocab","math","phonics"];\
  pages.forEach(p => $("page-"+p).classList.add("hidden"));\
  $("page-"+name).classList.remove("hidden");\
\
  const titles = \{today:"Today", vocab:"Words", math:"Math", phonics:"Phonics"\};\
  $("pageTitle").textContent = titles[name] || "Today";\
\}\
\
function updateTodayUI()\{\
  $("badgeWords").textContent = S.done.words ? "\uc0\u9989 " : "\u9633 ";\
  $("badgeMath").textContent = S.done.math ? "\uc0\u9989 " : "\u9633 ";\
  $("badgePhonics").textContent = S.done.phonics ? "\uc0\u9989 " : "\u9633 ";\
  $("streakText").textContent = `Streak: $\{S.streak\} days`;\
  $("streakCN").textContent = String(S.streak);\
\}\
\
function todayISO()\{\
  const d = new Date();\
  const y = d.getFullYear();\
  const m = String(d.getMonth()+1).padStart(2,"0");\
  const day = String(d.getDate()).padStart(2,"0");\
  return `$\{y\}-$\{m\}-$\{day\}`;\
\}\
\
function updateStreakIfFinishToday()\{\
  const today = todayISO();\
  if(S.lastDoneDate === today) return;\
\
  // Simple streak logic: if yesterday then +1 else reset to 1\
  const last = S.lastDoneDate ? new Date(S.lastDoneDate) : null;\
  const t = new Date(today);\
  if(last)\{\
    const diff = Math.round((t - last) / (1000*60*60*24));\
    if(diff === 1) S.streak += 1;\
    else S.streak = 1;\
  \} else \{\
    S.streak = 1;\
  \}\
  S.lastDoneDate = today;\
  saveState(S);\
\}\
\
function speak(text)\{\
  if(!("speechSynthesis" in window)) return;\
  const u = new SpeechSynthesisUtterance(text);\
  u.lang = "en-US";\
  window.speechSynthesis.cancel();\
  window.speechSynthesis.speak(u);\
\}\
\
/* ---------- Vocab page ---------- */\
let vocabIndex = 0;\
\
function renderVocab()\{\
  const v = CONTENT.vocab[vocabIndex];\
  $("wordEN").textContent = v.en;\
  $("wordDefEN").textContent = v.defEn;\
  $("wordDefCN").textContent = v.cn;\
  $("wordExEN").textContent = v.exEn;\
  $("wordExCN").textContent = v.exCn;\
\
  // dots\
  $("wordDots").innerHTML = "";\
  CONTENT.vocab.forEach((_, i) => \{\
    const dot = document.createElement("div");\
    dot.className = "dot" + (i === vocabIndex ? " on" : "");\
    $("wordDots").appendChild(dot);\
  \});\
\
  $("btnPrevWord").disabled = vocabIndex === 0;\
  $("btnNextWord").disabled = true; // until status clicked\
\}\
\
function setVocabStatus(status)\{\
  const v = CONTENT.vocab[vocabIndex];\
  S.vocabStatus[v.id] = status;\
  saveState(S);\
  $("btnNextWord").disabled = false;\
\}\
\
function vocabAllDone()\{\
  return CONTENT.vocab.every(w => !!S.vocabStatus[w.id]);\
\}\
\
/* ---------- Math page ---------- */\
function renderMath()\{\
  $("mathProblemText").textContent = CONTENT.math.problem;\
  $("keywordChips").innerHTML = "";\
  $("keywordHintCN").textContent = "";\
\
  CONTENT.math.keywords.forEach(k => \{\
    const chip = document.createElement("button");\
    chip.className = "chip";\
    chip.textContent = k.key;\
    chip.onclick = () => \{\
      // show CN hint line (and can be hidden by CN toggle)\
      $("keywordHintCN").textContent = S.cnOn ? k.hintCn : k.hintEn;\
    \};\
    $("keywordChips").appendChild(chip);\
  \});\
\
  $("inKnow").value = "";\
  $("inNeed").value = "";\
  $("inEq").value = "";\
  $("inAns").value = "";\
  $("mathFeedback").textContent = "";\
  $("btnDoneMath").classList.add("hidden");\
\}\
\
function parseNumberFromAnswer(text)\{\
  // extract first number\
  const m = text.match(/-?\\d+/);\
  return m ? parseInt(m[0],10) : null;\
\}\
\
/* ---------- Phonics page ---------- */\
function renderPhonics()\{\
  $("phonicsSkillEN").textContent = CONTENT.phonics.skillEn;\
  $("phonicsSkillDescEN").textContent = CONTENT.phonics.descEn;\
  $("phonicsSkillDescCN").textContent = CONTENT.phonics.descCn;\
\
  $("phonicsWords").innerHTML = "";\
  CONTENT.phonics.practiceWords.forEach(w => \{\
    const tile = document.createElement("div");\
    tile.className = "word-tile";\
    tile.innerHTML = `<span>$\{w\}</span><button class="icon-btn" aria-label="Hear">\uc0\u55357 \u56586 </button>`;\
    tile.querySelector("button").onclick = () => speak(w);\
    $("phonicsWords").appendChild(tile);\
  \});\
\
  $("phonicsChoices").innerHTML = "";\
  CONTENT.phonics.choices.forEach(opt => \{\
    const b = document.createElement("button");\
    b.className = "btn";\
    b.textContent = opt;\
    b.onclick = () => \{\
      if(opt === CONTENT.phonics.listenTarget)\{\
        $("phonicsFeedback").textContent = "\uc0\u9989  Great!";\
      \} else \{\
        $("phonicsFeedback").textContent = S.cnOn ? "\uc0\u55357 \u56577  \u20877 \u35797 \u19968 \u27425 " : "\u55357 \u56577  Try again";\
      \}\
    \};\
    $("phonicsChoices").appendChild(b);\
  \});\
\
  $("phonicsFeedback").textContent = "";\
\}\
\
/* ---------- Navigation logic ---------- */\
function startFlow()\{\
  if(!S.done.words) showPage("vocab");\
  else if(!S.done.math) showPage("math");\
  else if(!S.done.phonics) showPage("phonics");\
  else showPage("today");\
\}\
\
function finishTodayIfAllDone()\{\
  if(S.done.words && S.done.math && S.done.phonics)\{\
    updateStreakIfFinishToday();\
    updateTodayUI();\
    alert(S.cnOn ? "\uc0\u55356 \u57225  \u22826 \u26834 \u20102 \u65281 \u23436 \u25104 \u20170 \u22825 \u65281 " : "\u55356 \u57225  Great job! You finished today!");\
  \}\
\}\
\
/* ---------- Event bindings ---------- */\
window.addEventListener("DOMContentLoaded", () => \{\
  setCN(S.cnOn);\
  updateTodayUI();\
  showPage("today");\
\
  $("btnHome").onclick = () => \{ updateTodayUI(); showPage("today"); \};\
  $("btnCN").onclick = () => setCN(!S.cnOn);\
\
  $("btnStart").onclick = startFlow;\
  $("tileWords").onclick = () => showPage("vocab");\
  $("tileMath").onclick = () => showPage("math");\
  $("tilePhonics").onclick = () => showPage("phonics");\
\
  // Vocab\
  vocabIndex = 0;\
  renderVocab();\
  $("btnSpeakWord").onclick = () => speak(CONTENT.vocab[vocabIndex].en);\
\
  document.querySelectorAll("#wordCard .btn-row .btn").forEach(btn => \{\
    btn.onclick = () => setVocabStatus(btn.dataset.status);\
  \});\
\
  $("btnPrevWord").onclick = () => \{ vocabIndex = Math.max(0, vocabIndex-1); renderVocab(); \};\
  $("btnNextWord").onclick = () => \{\
    vocabIndex = Math.min(CONTENT.vocab.length-1, vocabIndex+1);\
    renderVocab();\
  \};\
\
  $("btnDoneWords").onclick = () => \{\
    if(!vocabAllDone())\{\
      alert(S.cnOn ? "\uc0\u35831 \u20808 \u32473 \u27599 \u20010 \u35789 \u36873 \u25321 \u19968 \u20010 \u29366 \u24577  \u9989 \u55357 \u56577 \u10067 " : "Please mark each word \u9989 \u55357 \u56577 \u10067  first.");\
      return;\
    \}\
    S.done.words = true; saveState(S);\
    updateTodayUI();\
    showPage("math");\
    renderMath();\
  \};\
\
  // Math\
  renderMath();\
  $("btnCheckMath").onclick = () => \{\
    const num = parseNumberFromAnswer($("inAns").value);\
    if(num === CONTENT.math.answerNumber)\{\
      $("mathFeedback").textContent = S.cnOn ? "\uc0\u9989  \u23545 \u20102 \u65281 " : "\u9989  Correct!";\
      S.done.math = true; saveState(S);\
      updateTodayUI();\
      $("btnDoneMath").classList.remove("hidden");\
    \} else \{\
      $("mathFeedback").textContent = (S.cnOn ? "\uc0\u55357 \u56577  \u20877 \u35797 \u19968 \u27425 \u65306  " : "\u55357 \u56577  Try again: ")\
        + (S.cnOn ? CONTENT.math.answerHintCn : CONTENT.math.answerHintEn);\
    \}\
  \};\
\
  $("btnDoneMath").onclick = () => \{ showPage("phonics"); renderPhonics(); \};\
\
  // Phonics\
  renderPhonics();\
  $("btnPlaySound").onclick = () => speak(CONTENT.phonics.listenTarget);\
\
  $("btnFinishToday").onclick = () => \{\
    S.done.phonics = true; saveState(S);\
    updateTodayUI();\
    showPage("today");\
    finishTodayIfAllDone();\
  \};\
\});\
}