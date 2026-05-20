[index.html](https://github.com/user-attachments/files/28052961/index.html)
<!DOCTYPE html>
<html lang="ko">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>4권역 마음 열기 — 우리 지역 자랑</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Noto+Sans+KR:wght@400;500;700&display=swap');
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
  :root {
    --bg: #ffffff; --bg2: #f5f5f3; --bg3: #eeede8;
    --tx: #1a1a18; --tx2: #5f5e5a; --tx3: #9a9990;
    --border: rgba(0,0,0,0.12); --border2: rgba(0,0,0,0.22);
    --radius: 8px; --radius-lg: 12px;
    --blue: #378ADD; --blue-bg: #E6F1FB; --blue-tx: #185FA5;
    --green: #1D9E75; --green-bg: #E1F5EE; --green-tx: #0F6E56;
    --amber: #EF9F27; --amber-bg: #FAEEDA; --amber-tx: #854F0B;
    --pink: #D4537E; --pink-bg: #FBEAF0; --pink-tx: #993556;
    --purple: #7F77DD; --purple-bg: #EEEDFE; --purple-tx: #534AB7;
  }
  @media (prefers-color-scheme: dark) {
    :root {
      --bg: #1c1c1a; --bg2: #252522; --bg3: #2e2e2b;
      --tx: #f0efe9; --tx2: #a8a79f; --tx3: #6a6960;
      --border: rgba(255,255,255,0.12); --border2: rgba(255,255,255,0.22);
      --blue-bg: #0c2d50; --blue-tx: #85B7EB;
      --green-bg: #062a1c; --green-tx: #5DCAA5;
      --amber-bg: #2e1d04; --amber-tx: #FAC775;
      --pink-bg: #2a0e1d; --pink-tx: #ED93B1;
      --purple-bg: #1a1640; --purple-tx: #AFA9EC;
    }
  }
  body { font-family: 'Noto Sans KR', sans-serif; background: var(--bg3); min-height: 100vh; display: flex; align-items: flex-start; justify-content: center; padding: 24px 16px 48px; }
  .app { background: var(--bg); border-radius: var(--radius-lg); border: 0.5px solid var(--border); width: 100%; max-width: 620px; padding: 24px 20px 28px; }
  .top-bar { display: flex; align-items: center; justify-content: space-between; margin-bottom: 1.25rem; }
  .app-title { font-size: 17px; font-weight: 700; color: var(--tx); }
  .timer-box { display: flex; align-items: center; gap: 6px; background: var(--bg2); border: 0.5px solid var(--border); border-radius: var(--radius); padding: 5px 10px; }
  .timer-label { font-size: 11px; color: var(--tx2); }
  .timer-num { font-size: 14px; font-weight: 500; color: var(--tx); min-width: 38px; }
  .timer-btn { font-size: 11px; padding: 2px 8px; border-radius: var(--radius); border: 0.5px solid var(--border2); background: var(--bg); color: var(--tx); cursor: pointer; }
  .phase-bar { display: flex; gap: 5px; margin-bottom: 1.25rem; }
  .phase-step { flex: 1; height: 4px; border-radius: 2px; background: var(--bg3); transition: background 0.3s; }
  .phase-step.done { background: var(--green); }
  .phase-step.active { background: var(--blue); }
  .screen { display: none; }
  .screen.visible { display: block; }
  .prompt-card { background: var(--bg2); border-radius: var(--radius-lg); padding: 14px 16px; margin-bottom: 1.25rem; }
  .prompt-num { font-size: 11px; font-weight: 500; color: var(--tx2); letter-spacing: 0.5px; margin-bottom: 5px; }
  .prompt-q { font-size: 15px; font-weight: 700; color: var(--tx); line-height: 1.4; margin-bottom: 10px; }
  .prompt-hint { font-size: 12px; color: var(--tx2); line-height: 1.55; background: var(--bg); border-radius: var(--radius); padding: 8px 11px; }
  .section-label { font-size: 12px; color: var(--tx2); margin-bottom: 7px; }
  .regions { display: grid; grid-template-columns: repeat(5, 1fr); gap: 6px; margin-bottom: 1rem; }
  .region-btn { border: 0.5px solid var(--border2); border-radius: var(--radius); padding: 9px 6px; text-align: center; cursor: pointer; background: var(--bg); transition: border-color 0.15s, background 0.15s; }
  .region-btn:hover { border-color: var(--blue); }
  .region-btn.selected { border: 2px solid var(--blue); }
  .region-dot { width: 28px; height: 28px; border-radius: 50%; margin: 0 auto 5px; display: flex; align-items: center; justify-content: center; font-size: 12px; font-weight: 700; }
  .region-name { font-size: 11px; font-weight: 500; color: var(--tx); }
  .answer-wrap { margin-bottom: 1rem; }
  .answer-wrap textarea { width: 100%; font-family: 'Noto Sans KR', sans-serif; font-size: 13px; color: var(--tx); background: var(--bg); border: 0.5px solid var(--border2); border-radius: var(--radius); padding: 9px 11px; resize: none; height: 76px; line-height: 1.6; }
  .answer-wrap textarea:focus { outline: none; border-color: var(--blue); box-shadow: 0 0 0 2px rgba(55,138,221,0.15); }
  .char-count { font-size: 11px; color: var(--tx3); text-align: right; margin-top: 3px; }
  .btn-row { display: flex; gap: 8px; justify-content: flex-end; }
  .btn-primary { background: var(--blue); color: #fff; border: none; border-radius: var(--radius); padding: 8px 20px; font-size: 13px; font-weight: 700; cursor: pointer; font-family: 'Noto Sans KR', sans-serif; }
  .btn-primary:disabled { opacity: 0.4; cursor: not-allowed; }
  .btn-secondary { background: transparent; color: var(--tx2); border: 0.5px solid var(--border2); border-radius: var(--radius); padding: 8px 14px; font-size: 13px; cursor: pointer; font-family: 'Noto Sans KR', sans-serif; }
  .board-header { display: flex; align-items: center; justify-content: space-between; margin-bottom: .75rem; }
  .board-title { font-size: 14px; font-weight: 700; color: var(--tx); }
  .board-count { font-size: 11px; color: var(--tx2); background: var(--bg2); padding: 3px 9px; border-radius: 20px; }
  .posts-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 8px; margin-bottom: 1rem; }
  .post-card { background: var(--bg); border: 0.5px solid var(--border); border-radius: var(--radius-lg); padding: 11px 13px; }
  .post-region-row { display: flex; align-items: center; gap: 6px; margin-bottom: 6px; }
  .post-dot { width: 7px; height: 7px; border-radius: 50%; flex-shrink: 0; }
  .post-region-name { font-size: 11px; font-weight: 700; }
  .post-question { font-size: 10px; color: var(--tx3); margin-bottom: 4px; }
  .post-text { font-size: 12px; color: var(--tx); line-height: 1.55; }
  .post-footer { display: flex; justify-content: flex-end; margin-top: 7px; }
  .like-btn { display: flex; align-items: center; gap: 4px; border: 0.5px solid var(--border); border-radius: 20px; padding: 3px 9px; font-size: 11px; color: var(--tx2); cursor: pointer; background: transparent; font-family: 'Noto Sans KR', sans-serif; }
  .like-btn.liked { border-color: var(--pink); color: var(--pink-tx); background: var(--pink-bg); }
  .summary-grid { display: grid; grid-template-columns: repeat(5, 1fr); gap: 6px; margin-bottom: 1rem; }
  .summary-card { background: var(--bg2); border-radius: var(--radius); padding: 9px 7px; text-align: center; }
  .summary-region { font-size: 11px; font-weight: 700; margin-bottom: 3px; }
  .summary-count { font-size: 20px; font-weight: 700; color: var(--tx); }
  .summary-label { font-size: 10px; color: var(--tx2); }
  .keyword-row { display: flex; flex-wrap: wrap; gap: 5px; margin-bottom: 1rem; }
  .keyword-chip { font-size: 11px; padding: 3px 10px; border-radius: 20px; font-weight: 500; }
  .facilitator-box { background: var(--bg2); border-radius: var(--radius); padding: 11px 13px; margin-bottom: 1rem; }
  .facilitator-label { font-size: 11px; color: var(--tx2); margin-bottom: 4px; }
  .facilitator-text { font-size: 12px; color: var(--tx); line-height: 1.6; }
  .empty-state { text-align: center; padding: 2rem; font-size: 13px; color: var(--tx2); grid-column: 1 / -1; }
</style>
</head>
<body>
<div class="app">

  <div class="top-bar">
    <div class="app-title">우리 지역 자랑 한마디</div>
    <div class="timer-box">
      <span class="timer-label">남은 시간</span>
      <span class="timer-num" id="timer-display">07:00</span>
      <button class="timer-btn" id="timer-btn" onclick="toggleTimer()">시작</button>
    </div>
  </div>

  <div class="phase-bar">
    <div class="phase-step active" id="ph0"></div>
    <div class="phase-step" id="ph1"></div>
    <div class="phase-step" id="ph2"></div>
  </div>

  <div class="screen visible" id="screen-input">
    <div class="prompt-card">
      <div class="prompt-num">질문 <span id="q-num">1</span> / 2</div>
      <div class="prompt-q" id="q-text">우리 지역 하면 떠오르는 것 딱 하나만!</div>
      <div class="prompt-hint" id="q-hint">음식, 장소, 소문난 것 뭐든 OK — 단어 하나도 좋아요</div>
    </div>
    <div class="section-label">내 지역 선택</div>
    <div class="regions">
      <div class="region-btn" data-region="용인" onclick="selectRegion(this)">
        <div class="region-dot" style="background:var(--blue-bg);color:var(--blue-tx);">용</div>
        <div class="region-name">용인</div>
      </div>
      <div class="region-btn" data-region="여주" onclick="selectRegion(this)">
        <div class="region-dot" style="background:var(--green-bg);color:var(--green-tx);">여</div>
        <div class="region-name">여주</div>
      </div>
      <div class="region-btn" data-region="안성" onclick="selectRegion(this)">
        <div class="region-dot" style="background:var(--amber-bg);color:var(--amber-tx);">안</div>
        <div class="region-name">안성</div>
      </div>
      <div class="region-btn" data-region="이천" onclick="selectRegion(this)">
        <div class="region-dot" style="background:var(--pink-bg);color:var(--pink-tx);">이</div>
        <div class="region-name">이천</div>
      </div>
      <div class="region-btn" data-region="양평" onclick="selectRegion(this)">
        <div class="region-dot" style="background:var(--purple-bg);color:var(--purple-tx);">양</div>
        <div class="region-name">양평</div>
      </div>
    </div>
    <div class="answer-wrap">
      <textarea id="answer-input" placeholder="여기에 입력하세요..." maxlength="60" oninput="updateChar()"></textarea>
      <div class="char-count"><span id="char-num">0</span> / 60자</div>
    </div>
    <div class="btn-row">
      <button class="btn-secondary" onclick="skipQ()">건너뛰기</button>
      <button class="btn-primary" id="next-btn" onclick="submitAnswer()" disabled>다음 →</button>
    </div>
  </div>

  <div class="screen" id="screen-board">
    <div class="board-header">
      <div class="board-title">4권역 자랑 모음</div>
      <div class="board-count" id="board-count">0개</div>
    </div>
    <div class="posts-grid" id="posts-grid">
      <div class="empty-state">아직 답변이 없어요. 첫 번째로 작성해보세요!</div>
    </div>
    <div class="btn-row">
      <button class="btn-secondary" onclick="goInput()">내 답변 추가</button>
      <button class="btn-primary" onclick="goSummary()">결과 보기 →</button>
    </div>
  </div>

  <div class="screen" id="screen-summary">
    <div class="board-header">
      <div class="board-title">지역별 참여 현황</div>
    </div>
    <div class="summary-grid" id="summary-grid"></div>
    <div class="section-label">많이 등장한 키워드</div>
    <div class="keyword-row" id="keyword-row"></div>
    <div class="facilitator-box">
      <div class="facilitator-label">진행자 메모</div>
      <div class="facilitator-text" id="facilitator-note">지역별 공통점과 차이점을 이야기해 보세요. 어떤 지역이 비슷해 보이나요?</div>
    </div>
    <div class="btn-row">
      <button class="btn-secondary" onclick="goBoard()">← 전체 보기</button>
    </div>
  </div>

</div>

<script>
const QUESTIONS = [
  { q: "우리 지역 하면 떠오르는 것 딱 하나만!", hint: "음식, 장소, 소문난 것 뭐든 OK — 단어 하나도 좋아요" },
  { q: "우리 지역에서 청소년이 바꾸고 싶은 것은?", hint: "교통, 문화공간, 환경, 학교생활 … 솔직하게!" }
];
const REG = {
  "용인": { dot: "#378ADD", bg: "#E6F1FB", tx: "#185FA5" },
  "여주": { dot: "#1D9E75", bg: "#E1F5EE", tx: "#0F6E56" },
  "안성": { dot: "#EF9F27", bg: "#FAEEDA", tx: "#854F0B" },
  "이천": { dot: "#D4537E", bg: "#FBEAF0", tx: "#993556" },
  "양평": { dot: "#7F77DD", bg: "#EEEDFE", tx: "#534AB7" }
};
const KW_PALETTES = [
  ["#E6F1FB","#185FA5"],["#E1F5EE","#0F6E56"],["#FAEEDA","#854F0B"],
  ["#FBEAF0","#993556"],["#EEEDFE","#534AB7"],["#F1EFE8","#5F5E5A"]
];
let state = { region: null, qIdx: 0, posts: [] };
let timerSec = 420, timerOn = false, timerIv = null;
function $(id) { return document.getElementById(id); }
function toggleTimer() {
  if (timerOn) { clearInterval(timerIv); timerOn = false; $('timer-btn').textContent = '재개'; }
  else {
    timerOn = true; $('timer-btn').textContent = '정지';
    timerIv = setInterval(() => {
      if (timerSec <= 0) { clearInterval(timerIv); $('timer-display').textContent = '00:00'; return; }
      timerSec--;
      const m = Math.floor(timerSec / 60), s = timerSec % 60;
      $('timer-display').textContent = String(m).padStart(2,'0') + ':' + String(s).padStart(2,'0');
    }, 1000);
  }
}
function selectRegion(el) {
  document.querySelectorAll('.region-btn').forEach(b => b.classList.remove('selected'));
  el.classList.add('selected'); state.region = el.dataset.region; checkNext();
}
function updateChar() { $('char-num').textContent = $('answer-input').value.length; checkNext(); }
function checkNext() { $('next-btn').disabled = !(state.region && $('answer-input').value.trim().length > 0); }
function submitAnswer() {
  const text = $('answer-input').value.trim();
  if (!text || !state.region) return;
  state.posts.push({ region: state.region, q: QUESTIONS[state.qIdx].q, text, likes: 0, liked: false, id: Date.now() });
  $('answer-input').value = ''; $('char-num').textContent = '0';
  if (state.qIdx < QUESTIONS.length - 1) {
    state.qIdx++; $('q-num').textContent = state.qIdx + 1;
    $('q-text').textContent = QUESTIONS[state.qIdx].q;
    $('q-hint').textContent = QUESTIONS[state.qIdx].hint;
    updatePhase(1);
  } else { renderBoard(); showScreen('board'); updatePhase(2); }
  checkNext();
}
function skipQ() {
  if (state.qIdx < QUESTIONS.length - 1) {
    state.qIdx++; $('q-num').textContent = state.qIdx + 1;
    $('q-text').textContent = QUESTIONS[state.qIdx].q;
    $('q-hint').textContent = QUESTIONS[state.qIdx].hint;
    $('answer-input').value = ''; $('char-num').textContent = '0'; checkNext();
  } else { renderBoard(); showScreen('board'); updatePhase(2); }
}
function renderBoard() {
  const grid = $('posts-grid');
  $('board-count').textContent = state.posts.length + '개';
  if (!state.posts.length) { grid.innerHTML = '<div class="empty-state">아직 답변이 없어요. 첫 번째로 작성해보세요!</div>'; return; }
  grid.innerHTML = state.posts.map(p => {
    const r = REG[p.region] || { dot:'#888', bg:'#eee', tx:'#444' };
    return `<div class="post-card">
      <div class="post-region-row"><div class="post-dot" style="background:${r.dot};"></div>
      <span class="post-region-name" style="color:${r.tx};">${p.region}</span></div>
      <div class="post-question">${p.q}</div>
      <div class="post-text">${p.text}</div>
      <div class="post-footer"><button class="like-btn ${p.liked?'liked':''}" onclick="toggleLike(${p.id})">♥ ${p.likes}</button></div>
    </div>`;
  }).join('');
}
function toggleLike(id) {
  const p = state.posts.find(x => x.id === id);
  if (!p) return; p.liked = !p.liked; p.likes += p.liked ? 1 : -1; renderBoard();
}
function goSummary() {
  const counts = {}, words = [];
  state.posts.forEach(p => {
    counts[p.region] = (counts[p.region] || 0) + 1;
    p.text.split(/[\s,。、!?~]+/).forEach(w => { if (w.length > 1) words.push(w); });
  });
  $('summary-grid').innerHTML = Object.keys(REG).map(r => {
    const c = REG[r];
    return `<div class="summary-card"><div class="summary-region" style="color:${c.tx};">${r}</div><div class="summary-count">${counts[r]||0}</div><div class="summary-label">답변</div></div>`;
  }).join('');
  const freq = {};
  words.forEach(w => { freq[w] = (freq[w]||0)+1; });
  const top = Object.entries(freq).sort((a,b)=>b[1]-a[1]).slice(0,8);
  $('keyword-row').innerHTML = top.map(([w,n],i) => {
    const [bg,tx] = KW_PALETTES[i%KW_PALETTES.length];
    return `<span class="keyword-chip" style="background:${bg};color:${tx};">${w}${n>1?' ('+n+')':''}</span>`;
  }).join('');
  const dominated = Object.entries(counts).sort((a,b)=>b[1]-a[1]);
  if (dominated.length > 0) $('facilitator-note').textContent = `"${dominated[0][0]}"에서 가장 많이 참여했어요. 지역별 공통 키워드와 차이점을 함께 읽어보고, 오늘 워크숍 주제와 연결해 보세요.`;
  showScreen('summary'); updatePhase(2);
}
function goBoard() { renderBoard(); showScreen('board'); }
function goInput() { showScreen('input'); updatePhase(state.qIdx > 0 ? 1 : 0); }
function showScreen(name) {
  document.querySelectorAll('.screen').forEach(s => s.classList.remove('visible'));
  $('screen-' + name).classList.add('visible');
}
function updatePhase(step) {
  ['ph0','ph1','ph2'].forEach((id,i) => {
    const el=$(id); el.classList.remove('done','active');
    if(i<step) el.classList.add('done'); else if(i===step) el.classList.add('active');
  });
}
</script>
</body>
</html>
