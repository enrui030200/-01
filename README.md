<!DOCTYPE html>
<html lang="ko">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>관계가 상처가 되기 전에</title>
<link href="https://fonts.googleapis.com/css2?family=Noto+Serif+KR:wght@300;400;500&family=Noto+Sans+KR:wght@300;400;500&display=swap" rel="stylesheet">
<style>
* { margin: 0; padding: 0; box-sizing: border-box; }
html { scroll-behavior: smooth; }
body { font-family: 'Noto Sans KR', sans-serif; background: #f0f7e8; color: #2d4a24; }

/* NAV */
nav {
  position: sticky; top: 0; z-index: 200;
  display: flex; justify-content: center; gap: 0;
  background: rgba(255,255,255,0.88);
  backdrop-filter: blur(12px);
  border-bottom: 1px solid rgba(100,140,70,0.18);
}
.nav-btn {
  padding: 15px 20px; font-size: 13px; font-weight: 500;
  color: #5a7a4a; background: none; border: none;
  border-bottom: 2px solid transparent;
  cursor: pointer; transition: all 0.22s;
  font-family: 'Noto Sans KR', sans-serif;
  letter-spacing: 0.03em;
}
.nav-btn:hover { color: #2d4a24; background: rgba(120,170,70,0.07); }
.nav-btn.active { color: #2d4a24; border-bottom-color: #7aaa50; }

/* PAGES */
.page { display: none; }
.page.active { display: block; }

/* HERO */
.hero {
  position: relative; min-height: calc(100vh - 50px);
  display: flex; align-items: center; justify-content: center;
  overflow: hidden;
}
.hero-photo {
  position: absolute; inset: 0;
  background-image: url('https://images.unsplash.com/photo-1448375240586-882707db888b?w=1600&q=80');
  background-size: cover; background-position: center;
  filter: brightness(0.9) saturate(0.85);
}
.hero-overlay {
  position: absolute; inset: 0;
  background: linear-gradient(160deg,
    rgba(220,240,200,0.62) 0%,
    rgba(180,220,150,0.5) 40%,
    rgba(140,190,110,0.45) 100%);
}
.hero-content {
  position: relative; z-index: 2;
  text-align: center; padding: 4rem 2rem;
  max-width: 560px;
}
.hero-label {
  font-size: 11px; letter-spacing: 0.25em; color: #3a5a2a;
  font-weight: 500; margin-bottom: 1.4rem;
  text-transform: uppercase;
}
.hero-title {
  font-family: 'Noto Serif KR', serif;
  font-size: 32px; font-weight: 400; line-height: 1.65;
  color: #1e3616; margin-bottom: 0.6rem;
  text-shadow: 0 1px 20px rgba(200,230,160,0.6);
}
.hero-book-title {
  font-size: 14px; color: #4a6a38;
  font-style: italic; margin-bottom: 2.5rem;
  letter-spacing: 0.05em;
}
.hero-cta {
  display: inline-block; padding: 13px 32px;
  background: rgba(50,90,30,0.78);
  color: #e8f5d8; border-radius: 30px;
  font-size: 14px; font-weight: 500; cursor: pointer;
  border: 1px solid rgba(100,150,60,0.4);
  text-decoration: none; transition: all 0.22s;
  backdrop-filter: blur(4px);
  font-family: 'Noto Sans KR', sans-serif;
}
.hero-cta:hover {
  background: rgba(35,70,20,0.88);
  transform: translateY(-2px);
}

/* SECTION CONTAINER */
.section { max-width: 720px; margin: 0 auto; padding: 3rem 2rem; }
.section-header { margin-bottom: 2rem; }
.section-title {
  font-family: 'Noto Serif KR', serif;
  font-size: 22px; font-weight: 400; color: #1e3616;
  margin-bottom: 6px;
}
.section-sub { font-size: 13px; color: #7a9a6a; }
.divider { height: 1px; background: linear-gradient(90deg, #b8d4a0, transparent); margin: 1rem 0 2rem; }

/* TYPES */
.types-grid {
  display: grid; grid-template-columns: repeat(3, 1fr); gap: 12px;
  margin-bottom: 1.5rem;
}
.type-card {
  background: rgba(255,255,255,0.75);
  border: 1px solid #c8ddb0; border-radius: 14px;
  padding: 1.1rem; cursor: pointer;
  transition: all 0.22s; text-align: center;
  backdrop-filter: blur(4px);
}
.type-card:hover {
  background: rgba(234,243,222,0.95);
  border-color: #9dc870; transform: translateY(-3px);
  box-shadow: 0 6px 20px rgba(100,160,60,0.13);
}
.type-card.selected {
  background: rgba(221,239,200,0.97);
  border-color: #7aaa50;
  box-shadow: 0 6px 20px rgba(100,160,60,0.18);
}
.type-icon { font-size: 26px; margin-bottom: 8px; }
.type-name { font-size: 15px; font-weight: 500; color: #2d4a24; margin-bottom: 5px; }
.type-tag {
  font-size: 11px; color: #5a7a4a;
  background: rgba(120,170,80,0.15);
  padding: 3px 10px; border-radius: 10px; display: inline-block;
}
.type-detail {
  background: rgba(255,255,255,0.88);
  border: 1px solid #b8d4a0; border-radius: 14px;
  padding: 1.75rem; display: none;
  backdrop-filter: blur(8px);
}
.type-detail.show { display: block; }
.type-detail h3 {
  font-family: 'Noto Serif KR', serif;
  font-size: 18px; font-weight: 400; color: #1e3616; margin-bottom: 1rem;
}
.type-detail p { font-size: 14px; color: #3a5a2a; line-height: 2; }

/* BOOK PAGE */
.book-badge {
  display: inline-block; background: #ddefc8; color: #2d4a24;
  font-size: 12px; padding: 5px 14px; border-radius: 12px;
  margin-bottom: 1.25rem; font-weight: 500;
}
.book-card {
  background: rgba(255,255,255,0.82);
  border: 1px solid #c8ddb0; border-radius: 16px;
  padding: 2rem; backdrop-filter: blur(8px);
}
.book-headline {
  font-family: 'Noto Serif KR', serif;
  font-size: 17px; font-weight: 400; color: #1e3616;
  margin-bottom: 0.5rem; line-height: 1.6;
}
.book-quote {
  font-style: italic; color: #4a7a30; font-size: 14px;
  border-left: 3px solid #9dc870; padding-left: 1rem;
  margin: 1rem 0; line-height: 1.8;
}
.book-body { font-size: 14px; color: #3a5a2a; line-height: 2; }
.buy-btn {
  display: inline-block; margin-top: 2rem;
  padding: 13px 32px; background: #4a7a30;
  color: #f0f8e8; border-radius: 30px;
  font-size: 14px; font-weight: 500;
  text-decoration: none; transition: all 0.22s;
  font-family: 'Noto Sans KR', sans-serif;
}
.buy-btn:hover { background: #3a6020; transform: translateY(-1px); }

/* TRAILER */
.trailer-wrap { text-align: center; }
.trailer-thumb-link {
  display: inline-block; border-radius: 16px; overflow: hidden;
  border: 2px solid #c8ddb0; margin-bottom: 1.5rem;
  transition: all 0.22s; text-decoration: none;
  position: relative;
}
.trailer-thumb-link:hover { border-color: #7aaa50; transform: translateY(-2px); box-shadow: 0 8px 28px rgba(80,140,40,0.18); }
.trailer-img {
  width: 100%; max-width: 540px; height: 304px;
  object-fit: cover; display: block;
  filter: brightness(0.88) saturate(0.8);
}
.play-overlay {
  position: absolute; top: 50%; left: 50%;
  transform: translate(-50%, -50%);
  width: 64px; height: 64px; border-radius: 50%;
  background: rgba(255,255,255,0.88);
  display: flex; align-items: center; justify-content: center;
  transition: all 0.2s;
}
.trailer-thumb-link:hover .play-overlay { background: rgba(255,255,255,0.97); transform: translate(-50%, -50%) scale(1.08); }
.play-triangle {
  width: 0; height: 0;
  border-top: 12px solid transparent;
  border-bottom: 12px solid transparent;
  border-left: 20px solid #3a6020;
  margin-left: 4px;
}
.trailer-title { font-family: 'Noto Serif KR', serif; font-size: 17px; font-weight: 400; color: #1e3616; margin-bottom: 6px; }
.trailer-sub { font-size: 13px; color: #7a9a6a; margin-bottom: 1.25rem; }
.yt-btn {
  display: inline-block; padding: 12px 28px;
  background: rgba(50,90,30,0.85); color: #e8f5d8;
  border-radius: 28px; font-size: 13px; font-weight: 500;
  text-decoration: none; transition: all 0.2s;
  font-family: 'Noto Sans KR', sans-serif;
}
.yt-btn:hover { background: rgba(35,70,20,0.92); transform: translateY(-1px); }

/* AUTHOR */
.author-wrap {
  background: rgba(255,255,255,0.82);
  border: 1px solid #c8ddb0; border-radius: 16px;
  padding: 2rem; backdrop-filter: blur(8px);
}
.author-top { display: flex; align-items: center; gap: 18px; margin-bottom: 1.5rem; }
.author-avatar {
  width: 76px; height: 76px; border-radius: 50%;
  background: linear-gradient(135deg, #9dc870, #5a8a3a);
  display: flex; align-items: center; justify-content: center;
  font-family: 'Noto Serif KR', serif;
  font-size: 26px; color: #fff; flex-shrink: 0;
}
.author-name { font-family: 'Noto Serif KR', serif; font-size: 20px; font-weight: 400; color: #1e3616; }
.author-cn { font-size: 13px; color: #7a9a6a; margin-top: 3px; }
.author-bio { font-size: 14px; color: #3a5a2a; line-height: 2; }

/* PAGE BG */
#types, #book, #author, #trailer {
  min-height: calc(100vh - 50px);
  background: linear-gradient(170deg, #eaf3de 0%, #f5f9f0 60%, #e8f2dc 100%);
}
</style>
</head>
<body>

<nav>
  <button class="nav-btn active" onclick="showPage('home')">홈</button>
  <button class="nav-btn" onclick="showPage('types')">불안 유형</button>
  <button class="nav-btn" onclick="showPage('book')">책 소개</button>
  <button class="nav-btn" onclick="showPage('trailer')">북 트레일러</button>
  <button class="nav-btn" onclick="showPage('author')">작가 소개</button>
</nav>

<!-- HOME -->
<div id="home" class="page active">
  <div class="hero">
    <div class="hero-photo"></div>
    <div class="hero-overlay"></div>
    <div class="hero-content">
      <div class="hero-label">Healing Psychology</div>
      <div class="hero-title">당신의 불안 유형은<br>무엇입니까?</div>
      <div class="hero-book-title">《관계가 상처가 되기 전에》</div>
      <a href="#" class="hero-cta" onclick="showPage('types'); return false;">유형 검사 시작하기 →</a>
    </div>
  </div>
</div>

<!-- TYPES -->
<div id="types" class="page">
  <div class="section">
    <div class="section-header">
      <div class="section-title">6가지 불안 유형</div>
      <div class="section-sub">어린 시절의 상처가 만들어낸 관계 패턴을 확인해보세요</div>
    </div>
    <div class="divider"></div>
    <div class="types-grid" id="typesGrid"></div>
    <div class="type-detail" id="typeDetail">
      <h3 id="detailTitle"></h3>
      <p id="detailText"></p>
    </div>
  </div>
</div>

<!-- BOOK -->
<div id="book" class="page">
  <div class="section">
    <div class="section-header">
      <div class="section-title">책 소개</div>
    </div>
    <div class="divider"></div>
    <div class="book-card">
      <span class="book-badge">📚 교보문고 심리학 분야 베스트셀러</span>
      <div class="book-headline">100만 조회 수를 부른 화제의 콘텐츠!<br>어린 시절의 상처가 관계의 독이 된 이들에게<br>심리학자가 건네는 가장 따뜻한 마음 처방</div>
      <div class="book-quote">"어제의 상처에 얽매여 오늘의 관계를 망치지는 마세요"<br>— 후회, 집착, 불안을 멈추는 관계 회복 심리학</div>
      <div class="book-body">
        학창시절 한 친구와 가까워지기 위해 갖은 애를 썼지만 오히려 사이가 더 멀어진 경험이 있지 않은가? 또는 연인과 끝없는 싸움에 지쳐 이별을 건네고 뒤돌아서 바로 후회했거나, 같이 사는 가족이 무거운 짐처럼 느껴진 적이 있을 것이다.<br><br>
        더 행복하기 위해 열심히 노력한 것뿐인데 왜 이런 결말에 이르는 걸까? 심리학자이자 전문 심리 상담사로서 오랫동안 성인들의 정신 건강과 대인관계 문제를 다룬 장자치 박사는 대부분의 사람이 이처럼 친밀한 관계에서 헤어 나오기 어려운 고통을 겪고 있다는 사실에 놀랐다. 더 심각한 것은 이들의 고통이 어느 한 관계에서 끝나는 것이 아니라 역병처럼 퍼져서 그들 주위의 모든 관계에서 말썽을 일으킨다는 사실이었다.<br><br>
        장자치 박사는 사람들이 더 이상 인간관계에서 불행하지 않고 보다 더 행복한 삶을 누릴 수 있도록 갈등의 원인을 찾는 데 집중했고, 어린 시절에 치유 받지 못한 상처에서 그 답을 찾았다. 이를 정리해 칼럼으로 알렸고, 이 글이 사람들에게 입소문이 나기 시작해 100만 독자에게 '미처 몰랐던 감정을 비추는 거울'로 불리기 시작했다.<br><br>
        이 책에서는 불건강한 관계의 모습을 총 여섯 가지 유형으로 나누었다. 모든 사람에게 '을'이 되기를 자처하는 희생형 유형부터 기댈 사람이 없으면 스스로 살아가지 못하는 기생형 유형까지 과거에 느낀 상처와 감정이 왜 오늘날의 문제가 되고 앞으로 어떻게 해결할 수 있는지 구체적으로 알려 준다.<br><br>
        아직도 주변 사람과의 문제로 골머리를 앓고 매일 밤마다 무거운 한숨을 내쉬고 있다면 이 책과 함께 그동안 외면했던 상처를 들여다보자. 당신의 어린 시절은 어른이 된 지금의 당신이 자신을 구해주길 기다리고 있다. 조금만 용기를 낸다면 오래된 상처에서 벗어나 더 이상 아픔 없이 사람들과 웃고 있는 자신의 미래를 발견할 것이다.
      </div>
      <a href="https://www.yes24.com/Product/Goods/123702688?pid=123487&cosemkid=go17011508330437912&utm_source=google_pc&utm_medium=cpc&utm_campaign=book_pc&utm_content=ys_240530_google_pc_cc_book_pc_12311%EB%8F%84%EC%84%9C&utm_term=%EA%B4%80%EA%B3%84%EA%B0%80%EC%83%81%EC%B2%98%EA%B0%80%EB%90%98%EA%B8%B0%EC%A0%84%EC%97%90" class="buy-btn" target="_blank">책 구매하기 →</a>
    </div>
  </div>
</div>

<!-- TRAILER -->
<div id="trailer" class="page">
  <div class="section">
    <div class="section-header">
      <div class="section-title">북 트레일러</div>
    </div>
    <div class="divider"></div>
    <div class="trailer-wrap">
      <a href="https://www.youtube.com/watch?v=DorWhyChrK4" target="_blank" class="trailer-thumb-link">
        <img
          class="trailer-img"
          src="https://img.youtube.com/vi/DorWhyChrK4/maxresdefault.jpg"
          alt="관계가 상처가 되기 전에 북 트레일러 썸네일"
          onerror="this.src='https://img.youtube.com/vi/DorWhyChrK4/hqdefault.jpg'"
        >
        <div class="play-overlay">
          <div class="play-triangle"></div>
        </div>
      </a>
      <div class="trailer-title">관계가 상처가 되기 전에 — 북 트레일러</div>
      <div class="trailer-sub">영상을 클릭하면 유튜브에서 감상하실 수 있습니다</div>
      <a href="https://www.youtube.com/watch?v=DorWhyChrK4" target="_blank" class="yt-btn">유튜브에서 보기 →</a>
    </div>
  </div>
</div>

<!-- AUTHOR -->
<div id="author" class="page">
  <div class="section">
    <div class="section-header">
      <div class="section-title">작가 소개</div>
    </div>
    <div class="divider"></div>
    <div class="author-wrap">
      <div class="author-top">
        <div class="author-avatar">장</div>
        <div>
          <div class="author-name">장자치</div>
          <div class="author-cn">張家齊 · Zhang Jiaqi</div>
        </div>
      </div>
      <div class="author-bio">
        대만 출신의 임상 심리학자이자 중국 시안교통리버풀대학교(XJTLU) 심리학 교수다. 사람들의 상처받은 마음을 치유해 모두가 행복한 인생을 살 수 있도록 돕고자 성인 정신건강학과 관계 심리학 분야에 발을 들였다.<br><br>
        연구와 상담 과정에서 얻은 심리 이론을 칼럼으로 정리해 알렸고, 이 글이 입소문이 나면서 <strong>120만 회가 넘는 누적 조회 수</strong>를 기록했다. 저자의 명쾌한 심리 처방은 '미처 몰랐던 감정을 비추는 거울'로 알려졌고, 위로와 조언이 필요한 이들에게 따뜻한 공감과 해결책을 주었다.<br><br>
        현재는 칼럼뿐만 아니라 강연도 활발하게 진행하고 있다.
      </div>
    </div>
  </div>
</div>

<script>
const types = [
  { name: '희생형', tag: '자존감 문제', icon: '🤲', desc: '희생형은 자존감 문제에서 비롯됩니다. 모든 사람에게 "을"이 되기를 자처하며, 타인의 필요와 요구를 자신보다 항상 우선시합니다. 어린 시절 자신의 존재 가치를 인정받지 못한 경험이 반복되면서, 스스로를 희생해야만 사랑받을 수 있다는 믿음이 형성됩니다. 관계 속에서 자꾸 손해를 보면서도 그것을 멈추지 못하는 이유가 바로 이 뿌리 깊은 자존감 결핍에 있습니다.' },
  { name: '통제형', tag: '죄책감', icon: '🎯', desc: '통제형은 죄책감에 기반한 불안 유형입니다. 관계에서 무언가 잘못될 것 같은 두려움 때문에, 상대방이나 상황을 과도하게 통제하려는 경향을 보입니다. 어린 시절 감당하기 어려운 책임감을 떠안거나, 주변 사람의 감정을 책임져야 했던 경험이 이런 패턴을 만들어냅니다. 통제는 결국 친밀감을 무너뜨리는 방어기제입니다.' },
  { name: '증오형', tag: '압박감', icon: '🌋', desc: '증오형은 압박감에서 비롯된 불안 유형입니다. 관계에서 느끼는 과도한 압박과 스트레스가 분노와 증오의 감정으로 표출됩니다. 어린 시절 억압되고 자유롭지 못했던 환경에서 자랐거나, 감정을 건강하게 표현하는 법을 배우지 못한 경우 이 유형이 나타납니다. 겉으로는 차갑거나 적대적으로 보이지만, 깊은 내면에는 이해받고 싶은 강한 욕구가 있습니다.' },
  { name: '다중연애형', tag: '권력욕', icon: '💫', desc: '다중연애형은 권력욕에 기반한 불안 유형입니다. 여러 사람과 동시에 관계를 맺으며 자신이 원하는 것을 상대방에게서 얻으려 합니다. 어린 시절 원하는 것을 충분히 얻지 못했거나, 관계 속에서 힘과 우위를 통해 안정감을 느끼는 법을 배운 경우 나타납니다. 진정한 친밀감보다 우위와 선택권을 유지하는 것에 집중하게 됩니다.' },
  { name: '무신뢰형', tag: '불안감', icon: '🔒', desc: '무신뢰형은 불안감에서 비롯된 유형입니다. 타인을 쉽게 믿지 못하고, 관계 속에서 항상 배신당할 것을 두려워합니다. 어린 시절 믿었던 사람에게 반복적으로 상처받거나 실망한 경험이 누적되면서, 방어막을 치고 타인과의 깊은 연결을 스스로 차단합니다. 혼자가 더 안전하다고 느끼지만, 내면 깊은 곳에서는 진정한 연결을 갈망합니다.' },
  { name: '기생형', tag: '존재감 문제', icon: '🌿', desc: '기생형은 존재감 문제에서 비롯된 불안 유형입니다. 혼자서는 살아갈 수 없다는 두려움이 커서, 기댈 사람이 없으면 극심한 불안을 느낍니다. 어린 시절 혼자 감당해야 했던 경험이나, 반대로 지나친 과보호로 인해 스스로의 능력을 키우지 못한 경우 나타납니다. 상대방에 대한 과도한 의존은 결국 관계를 질식시키는 결과를 낳습니다.' },
];

let selected = -1;

function renderTypes() {
  document.getElementById('typesGrid').innerHTML = types.map((t, i) => `
    <div class="type-card ${selected===i?'selected':''}" onclick="selectType(${i})">
      <div class="type-icon">${t.icon}</div>
      <div class="type-name">${t.name}</div>
      <div class="type-tag">${t.tag}</div>
    </div>
  `).join('');
}

function selectType(i) {
  selected = selected === i ? -1 : i;
  renderTypes();
  const detail = document.getElementById('typeDetail');
  if (selected >= 0) {
    document.getElementById('detailTitle').textContent = types[i].icon + ' ' + types[i].name + ' — ' + types[i].tag;
    document.getElementById('detailText').textContent = types[i].desc;
    detail.classList.add('show');
    detail.scrollIntoView({ behavior: 'smooth', block: 'nearest' });
  } else {
    detail.classList.remove('show');
  }
}

function showPage(id) {
  document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
  document.querySelectorAll('.nav-btn').forEach(b => b.classList.remove('active'));
  document.getElementById(id).classList.add('active');
  const idx = ['home','types','book','trailer','author'].indexOf(id);
  document.querySelectorAll('.nav-btn')[idx].classList.add('active');
  window.scrollTo(0, 0);
}

renderTypes();
</script>
</body>
</html>
