<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Cybrella · HealthGuard AI</title>
<style>
*{margin:0;padding:0;box-sizing:border-box}
html{scroll-behavior:smooth;overflow-x:hidden}
body{background:#030508;color:#dce8f0;font-family:'Segoe UI',system-ui,sans-serif;overflow-x:hidden}
::-webkit-scrollbar{width:4px}
::-webkit-scrollbar-thumb{background:linear-gradient(#2ecc71,#1a7a50);border-radius:2px}

/* NAV */
nav{
  position:fixed;top:0;left:0;width:100%;z-index:999;
  display:flex;align-items:center;justify-content:space-between;
  padding:14px 32px;
  background:rgba(3,5,8,.85);
  backdrop-filter:blur(16px);
  border-bottom:1px solid rgba(46,204,113,.08);
}
.logo{font-weight:900;font-size:17px;background:linear-gradient(135deg,#2ecc71,#2ea0ff);-webkit-background-clip:text;-webkit-text-fill-color:transparent}
.nav-links{display:flex;gap:22px;list-style:none}
.nav-links a{color:#5a7070;font-size:11px;letter-spacing:1.5px;text-transform:uppercase;transition:.3s;cursor:pointer}
.nav-links a:hover{color:#2ecc71}

/* HERO INTRO */
#intro{
  min-height:100vh;display:flex;flex-direction:column;
  align-items:center;justify-content:center;
  padding:100px 20px 40px;position:relative;overflow:hidden;
}
#introBg{position:absolute;inset:0;z-index:0}
.intro-top{
  font-family:'Courier New',monospace;
  font-size:10px;letter-spacing:4px;color:rgba(46,204,113,.5);
  text-transform:uppercase;margin-bottom:16px;
  animation:fadeIn 1s both;z-index:2;
}
@keyframes fadeIn{from{opacity:0;transform:translateY(10px)}to{opacity:1;transform:translateY(0)}}

/* NEW: catchy team + project title */
.hero-title{
  z-index:2;text-align:center;margin-bottom:22px;
}
.team-name{
  font-size:clamp(26px,5vw,44px);
  font-weight:950;letter-spacing:1px;
  background:linear-gradient(135deg,#fff,#2ecc71,#2ea0ff);
  -webkit-background-clip:text;-webkit-text-fill-color:transparent;
}
.project-name{
  margin-top:6px;
  font-family:'Courier New',monospace;
  font-size:11px;letter-spacing:3px;text-transform:uppercase;
  color:rgba(140,190,210,.55);
}
.project-tagline{
  margin-top:10px;
  font-size:13px;line-height:1.6;
  color:#5a7080;max-width:560px;
}

/* THREE PANEL */
.three-panel{
  display:grid;
  grid-template-columns:1fr 260px 1fr;
  gap:20px;
  width:100%;
  max-width:900px;
  z-index:2;
  align-items:center;
}
@media(max-width:700px){
  .three-panel{grid-template-columns:1fr;max-width:320px}
}

/* MEMBER CARD */
.member-wrap{display:flex;flex-direction:column;align-items:center;gap:14px}
.portrait-box{
  width:180px;height:220px;position:relative;
  border-radius:16px;overflow:hidden;
  border:1px solid rgba(46,204,113,.18);
  box-shadow:0 0 40px rgba(46,204,113,.06),inset 0 0 30px rgba(0,0,0,.5);
  cursor:pointer;
}
.portrait-box canvas{width:100%;height:100%;display:block}
.upload-hint{
  position:absolute;inset:0;z-index:12;pointer-events:none;
  display:flex;align-items:flex-end;justify-content:center;
  padding-bottom:10px;
  background:linear-gradient(transparent 60%,rgba(0,0,0,.75));
  opacity:0;transition:opacity .25s;
}
.portrait-box:hover .upload-hint{opacity:1}
.upload-hint span{
  font-family:'Courier New',monospace;
  font-size:9px;letter-spacing:2px;text-transform:uppercase;
  color:rgba(46,204,113,.85);
}
.scan-line{
  position:absolute;left:0;right:0;height:3px;
  background:linear-gradient(90deg,transparent 0%,rgba(46,204,113,.2) 20%,rgba(46,204,113,.9) 50%,rgba(46,204,113,.2) 80%,transparent 100%);
  box-shadow:0 0 12px rgba(46,204,113,.8),0 0 4px rgba(46,204,113,1);
  animation:scanMove 2.8s ease-in-out infinite;
  z-index:10;pointer-events:none;
}
@keyframes scanMove{
  0%{top:8px;opacity:0}
  15%{opacity:1}
  85%{opacity:1}
  100%{top:calc(100% - 11px);opacity:0}
}
.portrait-corner{
  position:absolute;width:14px;height:14px;
  border-color:rgba(46,204,113,.6);border-style:solid;
  z-index:11;pointer-events:none;
}
.portrait-corner.tl{top:6px;left:6px;border-width:2px 0 0 2px}
.portrait-corner.tr{top:6px;right:6px;border-width:2px 2px 0 0}
.portrait-corner.bl{bottom:6px;left:6px;border-width:0 0 2px 2px}
.portrait-corner.br{bottom:6px;right:6px;border-width:0 2px 2px 0}
.member-name{
  font-size:15px;font-weight:700;letter-spacing:1px;text-align:center;
  color:#c8e8dc;
}
.member-role{
  font-size:10px;letter-spacing:2.5px;text-transform:uppercase;
  color:rgba(46,204,113,.6);text-align:center;font-family:'Courier New',monospace;
}

/* STATUS PANEL */
.status-panel{
  background:linear-gradient(160deg,#050a10,#020407);
  border:1px solid rgba(46,154,255,.25);
  border-radius:18px;
  padding:20px 16px;
  display:flex;flex-direction:column;gap:14px;
  position:relative;overflow:hidden;
}
.status-panel::before{
  content:"";position:absolute;
  top:-40px;left:-40px;width:150px;height:150px;
  background:radial-gradient(circle,rgba(46,154,255,.2),transparent 70%);
}
.status-row{font-family:'Courier New',monospace;font-size:10px;text-align:center}
.status-label{color:rgba(52,152,219,.7);letter-spacing:3px;text-transform:uppercase;font-size:9px;margin-bottom:4px}
.status-value{
  color:#2ecc71;font-size:16px;font-weight:700;letter-spacing:2px;
  animation:statusPulse 2s ease-in-out infinite;
}
@keyframes statusPulse{0%,100%{opacity:1}50%{opacity:.6}}
.hex-display{
  background:rgba(2,8,14,.9);border:1px solid rgba(46,204,113,.15);
  border-radius:8px;padding:8px;
  font-family:'Courier New',monospace;font-size:9px;
  color:rgba(46,204,113,.5);text-align:center;
  word-break:break-all;letter-spacing:2px;line-height:1.6;
}
.status-bars{display:flex;flex-direction:column;gap:6px}
.sbar-row{display:flex;align-items:center;gap:8px;font-size:9px;color:#4a6a5a;font-family:'Courier New',monospace}
.sbar-track{flex:1;height:3px;background:rgba(255,255,255,.06);border-radius:2px;overflow:hidden}
.sbar-fill{height:100%;background:linear-gradient(90deg,#1a7a50,#2ecc71);border-radius:2px;transition:width 1s}
.proj-name{
  text-align:center;font-size:18px;font-weight:900;
  background:linear-gradient(135deg,#fff,#2ecc71,#2ea0ff);
  -webkit-background-clip:text;-webkit-text-fill-color:transparent;
  letter-spacing:2px;
}
.sub-name{text-align:center;font-size:9px;color:rgba(46,204,113,.4);letter-spacing:3px;text-transform:uppercase;font-family:'Courier New',monospace}

/* NEW: group icon upload slot */
.icon-slot{
  display:flex;flex-direction:column;align-items:center;gap:8px;
}
.icon-box{
  width:120px;height:120px;border-radius:16px;overflow:hidden;
  border:1px solid rgba(46,204,113,.18);
  background:linear-gradient(145deg,#070d14,#04060b);
  display:flex;align-items:center;justify-content:center;
  position:relative;cursor:pointer;
}
.icon-box canvas{width:100%;height:100%;display:block}
.icon-hint{
  position:absolute;inset:0;pointer-events:none;
  display:flex;align-items:flex-end;justify-content:center;
  padding-bottom:10px;
  background:linear-gradient(transparent 55%,rgba(0,0,0,.75));
  opacity:0;transition:opacity .25s;
}
.icon-box:hover .icon-hint{opacity:1}
.icon-hint span{
  font-family:'Courier New',monospace;
  font-size:9px;letter-spacing:2px;text-transform:uppercase;
  color:rgba(46,204,113,.85);
}
.icon-label{
  font-family:'Courier New',monospace;
  font-size:9px;letter-spacing:3px;text-transform:uppercase;
  color:rgba(46,204,113,.45);
}

/* MARQUEE */
.marquee-strip{
  width:100%;overflow:hidden;z-index:2;margin-top:26px;
  border-top:1px solid rgba(46,204,113,.06);
  border-bottom:1px solid rgba(46,204,113,.06);
  padding:10px 0;
}
.marquee-inner{
  display:flex;gap:0;
  animation:scrollLeft 18s linear infinite;
  width:max-content;
}
@keyframes scrollLeft{from{transform:translateX(0)}to{transform:translateX(-50%)}}
.marquee-item{
  display:flex;align-items:center;gap:10px;
  font-size:10px;letter-spacing:2px;text-transform:uppercase;
  color:rgba(100,160,200,.5);white-space:nowrap;padding:0 40px;
  font-family:'Courier New',monospace;
}
.marquee-dot{width:4px;height:4px;border-radius:50%;background:rgba(46,204,113,.5)}

/* SCROLL SECTIONS (unchanged) */
.scroll-section{padding:80px 20px;max-width:960px;margin:0 auto}
.section-eyebrow{
  display:inline-block;font-size:9px;letter-spacing:4px;text-transform:uppercase;
  color:#2ecc71;font-family:'Courier New',monospace;
  border:1px solid rgba(46,204,113,.2);padding:4px 12px;border-radius:10px;
  margin-bottom:16px;
}
.section-h{font-size:clamp(28px,5vw,42px);font-weight:800;line-height:1.15;margin-bottom:12px}
.section-h .g{color:#2ecc71}
.section-p{font-size:14px;color:#5a7080;max-width:560px;line-height:1.7}

/* PROBLEM CARDS */
.prob-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(220px,1fr));gap:16px;margin-top:28px}
.prob-card{
  background:linear-gradient(145deg,#070d14,#04060b);
  border:1px solid rgba(255,255,255,.04);
  border-radius:14px;padding:22px;
  transition:border-color .3s,transform .3s;
}
.prob-card:hover{border-color:rgba(46,204,113,.2);transform:translateY(-3px)}
.prob-card h4{font-size:14px;font-weight:700;margin-bottom:8px;color:#b0c8d8}
.prob-card p{font-size:12px;color:#4a5a6a;line-height:1.6}
.prob-icon{font-size:22px;margin-bottom:10px;display:block}

/* FLOW */
.flow{display:flex;flex-direction:column;gap:0;margin-top:28px;position:relative;padding-left:30px}
.flow::before{
  content:"";position:absolute;left:10px;top:14px;bottom:14px;
  width:2px;background:linear-gradient(to bottom,#2ecc71,#2ea0ff,transparent);opacity:.2;
}
.flow-step{
  display:flex;gap:16px;align-items:flex-start;padding:16px 0;
  opacity:0;transform:translateX(-20px);transition:all .6s;
}
.flow-step.in{opacity:1;transform:translateX(0)}
.flow-num{
  width:44px;height:44px;min-width:44px;border-radius:50%;
  border:1.5px solid rgba(46,204,113,.3);
  display:flex;align-items:center;justify-content:center;
  font-family:'Courier New',monospace;font-size:12px;color:#2ecc71;
  position:relative;z-index:1;background:#030508;
}
.flow-text h4{font-size:14px;font-weight:700;margin-bottom:4px;color:#b0c8d8}
.flow-text p{font-size:12px;color:#4a5a6a;line-height:1.6}

/* TECH PILLS */
.tech-wrap{display:flex;flex-wrap:wrap;gap:10px;margin-top:24px}
.tech-pill{
  background:rgba(8,14,22,.8);
  border:1px solid rgba(255,255,255,.05);
  border-radius:8px;padding:10px 16px;
  display:flex;align-items:center;gap:8px;
  transition:all .3s;cursor:default;
}
.tech-pill:hover{border-color:rgba(46,204,113,.3);background:rgba(46,204,113,.05)}
.tech-pill span:first-child{font-size:18px}
.tech-pill .pname{font-size:12px;font-weight:700;color:#9ab8c8}
.tech-pill .pcat{font-size:9px;color:#3a5060;letter-spacing:1px;text-transform:uppercase;font-family:'Courier New',monospace}

/* STATS */
.stats-row{display:grid;grid-template-columns:repeat(auto-fit,minmax(180px,1fr));gap:16px;margin-top:28px}
.stat-box{
  background:linear-gradient(145deg,#070d14,#04060b);
  border:1px solid rgba(255,255,255,.04);
  border-radius:14px;padding:22px;text-align:center;
}
.stat-n{font-size:32px;font-weight:900;color:#2ecc71;line-height:1}
.stat-l{font-size:10px;color:#3a5060;letter-spacing:2px;text-transform:uppercase;margin-top:6px;font-family:'Courier New',monospace}

/* ROADMAP */
.roadmap{display:flex;gap:16px;flex-wrap:wrap;margin-top:28px}
.phase{
  flex:1;min-width:240px;
  background:linear-gradient(145deg,#070d14,#04060b);
  border:1px solid rgba(255,255,255,.04);
  border-radius:14px;padding:22px;
}
.phase-tag{
  display:inline-block;font-size:9px;letter-spacing:2px;font-weight:700;
  text-transform:uppercase;padding:3px 10px;border-radius:8px;margin-bottom:12px;
  font-family:'Courier New',monospace;
}
.phase-tag.active{background:rgba(46,204,113,.1);color:#2ecc71;border:1px solid rgba(46,204,113,.2)}
.phase-tag.next{background:rgba(46,100,255,.1);color:#5a80ff;border:1px solid rgba(46,100,255,.2)}
.phase h4{font-size:14px;font-weight:700;color:#b0c8d8;margin-bottom:10px}
.phase ul{list-style:none;display:flex;flex-direction:column;gap:5px}
.phase ul li{font-size:12px;color:#4a5a6a;padding-left:14px;position:relative}
.phase ul li::before{content:"›";position:absolute;left:0;color:#2ecc71}

/* DEMO CHAT */
.chatbox{
  max-width:500px;margin:28px auto;
  background:#040810;
  border:1px solid rgba(255,255,255,.06);
  border-radius:16px;overflow:hidden;
}
.chat-bar{
  padding:11px 16px;
  background:rgba(46,204,113,.06);
  border-bottom:1px solid rgba(255,255,255,.04);
  display:flex;align-items:center;gap:8px;
  font-size:11px;font-weight:600;color:#5a9a6a;
}
.chatdot{width:7px;height:7px;border-radius:50%;background:#2ecc71;animation:pulse 1.5s infinite}
@keyframes pulse{0%,100%{opacity:.5}50%{opacity:1}}
.chat-msgs{padding:14px;display:flex;flex-direction:column;gap:8px;min-height:180px}
.cm{
  max-width:78%;padding:9px 13px;border-radius:12px;
  font-size:12px;line-height:1.5;
  opacity:0;transform:translateY(6px);transition:all .4s;
}
.cm.show{opacity:1;transform:translateY(0)}
.cm.bot{background:rgba(46,204,113,.07);border:1px solid rgba(46,204,113,.15);color:#80d0a0;align-self:flex-start;border-bottom-left-radius:3px}
.cm.user{background:#0e1f35;color:#80b0d0;align-self:flex-end;border-bottom-right-radius:3px}

/* REVEAL */
.reveal{opacity:0;transform:translateY(24px);transition:all .65s cubic-bezier(.25,.46,.45,.94)}
.reveal.in{opacity:1;transform:translateY(0)}

footer{text-align:center;padding:36px 20px;border-top:1px solid rgba(255,255,255,.04);font-size:11px;color:#2a3a48}
</style>
</head>
<body>

<nav>
  <div class="logo">🛡 Cybrella</div>
  <ul class="nav-links">
    <li><a onclick="document.getElementById('problem').scrollIntoView({behavior:'smooth'})">Problem</a></li>
    <li><a onclick="document.getElementById('solution').scrollIntoView({behavior:'smooth'})">Solution</a></li>
    <li><a onclick="document.getElementById('tech').scrollIntoView({behavior:'smooth'})">Stack</a></li>
    <li><a onclick="document.getElementById('team').scrollIntoView({behavior:'smooth'})">Team</a></li>
  </ul>
</nav>

<!-- INTRO -->
<section id="intro">
  <canvas id="introBg"></canvas>
  <div class="intro-top">CYBRELLA · HACKATHON 2025 · QUALIFYING ROUND</div>

  <!-- NEW: Team + Project name -->
  <div class="hero-title">
    <div class="team-name">Team Codex 2.0</div>
    <div class="project-name">Project: HealthGuard AI</div>
    <div class="project-tagline">A smart symptom-to-diagnosis triage assistant designed for faster decisions in rural and remote communities.</div>
  </div>

  <div class="three-panel">

    <!-- DANIEL LEFT (UPLOAD SLOT 1) -->
    <div class="member-wrap">
      <div class="portrait-box" id="pb-left" title="Click to upload Daniel photo">
        <canvas id="cv-left"></canvas>
        <div class="scan-line" style="animation-delay:0s"></div>
        <div class="portrait-corner tl"></div>
        <div class="portrait-corner tr"></div>
        <div class="portrait-corner bl"></div>
        <div class="portrait-corner br"></div>
        <div class="upload-hint"><span>click to upload</span></div>
      </div>
      <div class="member-name" id="nm-left"></div>
      <div class="member-role" id="rl-left">ML</div>
    </div>

    <!-- STATUS CENTER + GROUP ICON UPLOAD SLOT 2 -->
    <div class="status-panel">
      <div class="icon-slot">
        <div class="icon-box" id="pb-icon" title="Click to upload group icon/logo">
          <canvas id="cv-icon"></canvas>
          <div class="icon-hint"><span>click to upload logo</span></div>
        </div>
        <div class="icon-label">Group Icon</div>
      </div>

      <div class="status-row" style="margin-top:6px">
        <div class="status-label">Status</div>
        <div class="status-value" id="statusVal">INITIALIZING</div>
      </div>
      <div class="hex-display" id="hexDisp">FF A3 20 0E</div>
      <div class="status-bars">
        <div class="sbar-row">
          <span>ML</span>
          <div class="sbar-track"><div class="sbar-fill" id="bar1" style="width:0%"></div></div>
          <span id="b1p">0%</span>
        </div>
        <div class="sbar-row">
          <span>UI</span>
          <div class="sbar-track"><div class="sbar-fill" id="bar2" style="width:0%;background:linear-gradient(90deg,#1a4a7a,#2ea0ff)"></div></div>
          <span id="b2p">0%</span>
        </div>
        <div class="sbar-row">
          <span>SYS</span>
          <div class="sbar-track"><div class="sbar-fill" id="bar3" style="width:0%;background:linear-gradient(90deg,#5a1a7a,#9b59b6)"></div></div>
          <span id="b3p">0%</span>
        </div>
      </div>
    </div>

    <!-- RYAN RIGHT (UPLOAD SLOT 3) -->
    <div class="member-wrap">
      <div class="portrait-box" id="pb-right" title="Click to upload Ryan photo">
        <canvas id="cv-right"></canvas>
        <div class="scan-line" style="animation-delay:1.4s"></div>
        <div class="portrait-corner tl"></div>
        <div class="portrait-corner tr"></div>
        <div class="portrait-corner bl"></div>
        <div class="portrait-corner br"></div>
        <div class="upload-hint"><span>click to upload</span></div>
      </div>
      <div class="member-name" id="nm-right"></div>
      <div class="member-role" id="rl-right">Frontend · Backend Integration</div>
    </div>
  </div>

  <!-- hidden inputs for the 3 upload slots -->
  <input id="file-left" type="file" accept="image/*" style="display:none">
  <input id="file-icon" type="file" accept="image/*" style="display:none">
  <input id="file-right" type="file" accept="image/*" style="display:none">

  <!-- MARQUEE -->
  <div class="marquee-strip">
    <div class="marquee-inner" id="mq"></div>
  </div>
</section>

<!-- (rest of your page unchanged) -->
<section class="scroll-section" id="problem">
  <div class="section-eyebrow reveal">01 · Problem</div>
  <h2 class="section-h reveal">The healthcare <span class="g">access gap</span></h2>
  <p class="section-p reveal">Remote communities face dangerous delays in care. Hospitals overflow. Web searches mislead.</p>
  <div class="prob-grid">
    <div class="prob-card reveal"><span class="prob-icon">🌾</span><h4>No Local Doctors</h4><p>Rural patients travel hours for basic consultations.</p></div>
    <div class="prob-card reveal"><span class="prob-icon">⏱️</span><h4>Delayed Decisions</h4><p>Uncertainty about severity leads to dangerous postponement.</p></div>
    <div class="prob-card reveal"><span class="prob-icon">🏥</span><h4>Overwhelmed Clinics</h4><p>Preliminary cases crowd ERs, blocking critical care.</p></div>
    <div class="prob-card reveal"><span class="prob-icon">🔍</span><h4>Bad Information</h4><p>Unverified search results cause panic or self-misdiagnosis.</p></div>
  </div>
</section>

<section class="scroll-section" id="solution" style="background:rgba(46,204,113,.01)">
  <div class="section-eyebrow reveal">02 · Solution</div>
  <h2 class="section-h reveal">Instant <span class="g">ML triage</span> in 3 steps</h2>
  <div class="flow">
    <div class="flow-step">
      <div class="flow-num">01</div>
      <div class="flow-text"><h4>Input Symptoms</h4><p>Chat interface captures natural language, converts to feature vectors.</p></div>
    </div>
    <div class="flow-step">
      <div class="flow-num">02</div>
      <div class="flow-text"><h4>ML Inference</h4><p>Decision Tree + Random Forest + SVM ensemble generate disease prediction with confidence score.</p></div>
    </div>
    <div class="flow-step">
      <div class="flow-num">03</div>
      <div class="flow-text"><h4>Guidance Output</h4><p>Risk level, health advice, and nearest hospital displayed instantly.</p></div>
    </div>
  </div>
</section>

<section class="scroll-section" id="tech">
  <div class="section-eyebrow reveal">03 · Stack</div>
  <h2 class="section-h reveal">Lightweight & <span class="g">offline-ready</span></h2>
  <div class="tech-wrap reveal">
    <div class="tech-pill"><span>🐍</span><div><div class="pname">Python</div><div class="pcat">Backend</div></div></div>
    <div class="tech-pill"><span>🎨</span><div><div class="pname">Streamlit</div><div class="pcat">Frontend</div></div></div>
    <div class="tech-pill"><span>🧠</span><div><div class="pname">Scikit-learn</div><div class="pcat">ML Engine</div></div></div>
    <div class="tech-pill"><span>🐼</span><div><div class="pname">Pandas</div><div class="pcat">Data</div></div></div>
    <div class="tech-pill"><span>🔢</span><div><div class="pname">NumPy</div><div class="pcat">Compute</div></div></div>
    <div class="tech-pill"><span>🌳</span><div><div class="pname">Decision Tree</div><div class="pcat">Classifier</div></div></div>
    <div class="tech-pill"><span>🌲</span><div><div class="pname">Random Forest</div><div class="pcat">Classifier</div></div></div>
    <div class="tech-pill"><span>📐</span><div><div class="pname">SVM</div><div class="pcat">Classifier</div></div></div>
  </div>
</section>

<section class="scroll-section" id="impact" style="background:rgba(46,204,113,.01)">
  <div class="section-eyebrow reveal">04 · Impact</div>
  <h2 class="section-h reveal">Built to <span class="g">scale</span></h2>
  <div class="stats-row">
    <div class="stat-box reveal"><div class="stat-n">87%</div><div class="stat-l">Prediction Accuracy</div></div>
    <div class="stat-box reveal"><div class="stat-n">&lt;500ms</div><div class="stat-l">Inference Speed</div></div>
    <div class="stat-box reveal"><div class="stat-n">2B+</div><div class="stat-l">Rural Reach Potential</div></div>
    <div class="stat-box reveal"><div class="stat-n">100%</div><div class="stat-l">Offline Capable</div></div>
  </div>
</section>

<section class="scroll-section" id="roadmap">
  <div class="section-eyebrow reveal">05 · Roadmap</div>
  <h2 class="section-h reveal">Two-phase <span class="g">delivery</span></h2>
  <div class="roadmap">
    <div class="phase reveal">
      <div class="phase-tag active">✓ Round 1 · Feb 11–17</div>
      <h4>Ideation & Architecture</h4>
      <ul>
        <li>Problem research & dataset collection</li>
        <li>System architecture design</li>
        <li>Initial ML model development</li>
        <li>Project proposal submission</li>
        <li>Concept video creation</li>
      </ul>
    </div>
    <div class="phase reveal">
      <div class="phase-tag next">→ Round 2 · Finals</div>
      <h4>Build & Deploy</h4>
      <ul>
        <li>Full chatbot implementation</li>
        <li>Streamlit UI polish</li>
        <li>Model optimization & testing</li>
        <li>Hospital locator integration</li>
        <li>GitHub repo + demo video</li>
      </ul>
    </div>
  </div>
</section>

<section class="scroll-section" id="demo">
  <div class="section-eyebrow reveal">06 · Demo</div>
  <h2 class="section-h reveal">Live <span class="g">chat preview</span></h2>
  <div class="chatbox reveal">
    <div class="chat-bar"><div class="chatdot"></div>HealthGuard AI · online</div>
    <div class="chat-msgs" id="chatMsgs"></div>
  </div>
</section>

<section class="scroll-section" id="team" style="background:rgba(46,204,113,.01)">
  <div class="section-eyebrow reveal">07 · Team</div>
  <h2 class="section-h reveal">Built by <span class="g">Cybrella</span></h2>
  <div style="display:flex;gap:20px;flex-wrap:wrap;margin-top:28px">
    <div class="prob-card reveal" style="flex:1;min-width:220px">
      <div style="font-size:28px;margin-bottom:12px">👨‍💻</div>
      <h4>Moirangthem Daniel Singh</h4>
      <p style="margin-top:6px">ML · Classifier design, data pipeline, model optimization.</p>
    </div>
    <div class="prob-card reveal" style="flex:1;min-width:220px">
      <div style="font-size:28px;margin-bottom:12px">👨‍🔬</div>
      <h4>Ryan Awungshi</h4>
      <p style="margin-top:6px">Frontend · Backend · Streamlit UI, chatbot integration, hospital locator.</p>
    </div>
  </div>
</section>

<footer>Cybrella · HealthGuard AI · Hackathon 2025 · Qualifying Submission<br>⚕️ Preliminary guidance only — always consult a licensed professional</footer>

<script>
// ── BG CANVAS ──────────────────────────────────────────────────
const bgC=document.getElementById('introBg'),bgX=bgC.getContext('2d');
let bW,bH,bT=0;
function bResize(){
  const s=bgC.parentElement;
  bW=bgC.width=s.offsetWidth;bH=bgC.height=s.offsetHeight;
}
bResize();window.addEventListener('resize',()=>{bResize();drawPortraits();drawIconPlaceholder()});
const bStars=Array.from({length:60},()=>({x:Math.random(),y:Math.random(),s:Math.random()*1.2+.3,b:Math.random()*6}));
function drawBg(){
  bT+=.005;bgX.clearRect(0,0,bW,bH);
  bStars.forEach(s=>{
    let a=.08+.18*(.5+.5*Math.sin(bT+s.b));
    bgX.fillStyle=`rgba(200,230,255,${a})`;bgX.beginPath();bgX.arc(s.x*bW,s.y*bH,s.s,0,Math.PI*2);bgX.fill();
  });
  requestAnimationFrame(drawBg);
}
drawBg();

// ── DEFAULT PLACEHOLDERS ───────────────────────────────────────
function drawPortrait(canvas,facingLeft){
  const box=canvas.parentElement;
  const W=canvas.width=box.offsetWidth*2;
  const H=canvas.height=box.offsetHeight*2;
  const c=canvas.getContext('2d');

  const bg=c.createLinearGradient(0,0,W,H);
  bg.addColorStop(0,'#07090f');bg.addColorStop(1,'#020407');
  c.fillStyle=bg;c.fillRect(0,0,W,H);

  const glow=c.createRadialGradient(W*.5,H*.35,H*.05,W*.5,H*.35,H*.55);
  glow.addColorStop(0,'rgba(255,255,255,.07)');glow.addColorStop(1,'transparent');
  c.fillStyle=glow;c.fillRect(0,0,W,H);

  c.save();
  c.translate(W*.5,H*.5);
  if(!facingLeft) c.scale(-1,1);
  const sc=Math.min(W,H)/280;

  c.fillStyle='#0f1520';
  c.beginPath();
  c.moveTo(25*sc,-95*sc);
  c.bezierCurveTo(55*sc,-100*sc,55*sc,-50*sc,48*sc,-20*sc);
  c.bezierCurveTo(44*sc,5*sc,36*sc,25*sc,28*sc,44*sc);
  c.bezierCurveTo(24*sc,58*sc,30*sc,75*sc,60*sc,90*sc);
  c.lineTo(75*sc,H*.52);c.lineTo(-75*sc,H*.52);
  c.lineTo(-55*sc,85*sc);
  c.bezierCurveTo(-28*sc,70*sc,-20*sc,55*sc,-18*sc,44*sc);
  c.bezierCurveTo(-22*sc,30*sc,-36*sc,15*sc,-44*sc,-2*sc);
  c.bezierCurveTo(-50*sc,-15*sc,-52*sc,-30*sc,-48*sc,-40*sc);
  c.bezierCurveTo(-44*sc,-52*sc,-36*sc,-58*sc,-28*sc,-62*sc);
  c.bezierCurveTo(-20*sc,-72*sc,-5*sc,-95*sc,25*sc,-95*sc);
  c.closePath();c.fill();

  c.strokeStyle='rgba(200,220,240,.09)';c.lineWidth=2.5*sc;
  c.beginPath();
  c.moveTo(48*sc,-20*sc);c.bezierCurveTo(52*sc,5*sc,40*sc,30*sc,28*sc,44*sc);
  c.bezierCurveTo(24*sc,58*sc,30*sc,75*sc,60*sc,90*sc);
  c.stroke();

  c.restore();

  const gt=c.createLinearGradient(0,H*.75,0,H);
  gt.addColorStop(0,'transparent');gt.addColorStop(1,'rgba(46,204,113,.04)');
  c.fillStyle=gt;c.fillRect(0,0,W,H);
}

function drawPortraits(){
  drawPortrait(document.getElementById('cv-left'),true);
  drawPortrait(document.getElementById('cv-right'),false);
}
drawPortraits();

function drawIconPlaceholder(){
  const cv = document.getElementById('cv-icon');
  const box = cv.parentElement;
  const W = cv.width = box.offsetWidth*2;
  const H = cv.height = box.offsetHeight*2;
  const c = cv.getContext('2d');
  c.clearRect(0,0,W,H);
  c.fillStyle="#04060b"; c.fillRect(0,0,W,H);

  const g = c.createRadialGradient(W/2,H/2,10,W/2,H/2,Math.max(W,H)*0.6);
  g.addColorStop(0,"rgba(46,154,255,.12)");
  g.addColorStop(1,"transparent");
  c.fillStyle=g; c.fillRect(0,0,W,H);

  // simple shield + "2.0" placeholder
  c.save();
  c.translate(W/2,H/2);
  const R = Math.min(W,H)*0.32;
  c.strokeStyle="rgba(46,154,255,.45)";
  c.lineWidth=Math.max(3,R*0.08);
  c.shadowColor="rgba(46,154,255,.35)";
  c.shadowBlur=18;
  c.beginPath();
  c.moveTo(0,-R*1.15);
  c.bezierCurveTo(R*1.1,-R*1.0,R*1.2,-R*0.1,R*0.85,R*0.85);
  c.bezierCurveTo(R*0.35,R*1.2,0,R*1.3,0,R*1.3);
  c.bezierCurveTo(0,R*1.3,-R*0.35,R*1.2,-R*0.85,R*0.85);
  c.bezierCurveTo(-R*1.2,-R*0.1,-R*1.1,-R*1.0,0,-R*1.15);
  c.closePath();
  c.stroke();

  c.shadowBlur=0;
  c.fillStyle="rgba(46,204,113,.10)";
  c.font = `900 ${Math.max(18,R*0.6)}px 'Courier New', monospace`;
  c.textAlign="center"; c.textBaseline="middle";
  c.fillText("LOGO",0,0);
  c.restore();
}
drawIconPlaceholder();

// ── UPLOAD SLOTS (3) ───────────────────────────────────────────
function coverDraw(ctx, img, w, h){
  const s = Math.max(w/img.width, h/img.height);
  const dw = img.width*s, dh = img.height*s;
  ctx.drawImage(img, (w-dw)/2, (h-dh)/2, dw, dh);
}
function grayscaleVignette(ctx,w,h){
  const id = ctx.getImageData(0,0,w,h), d = id.data;
  for(let i=0;i<d.length;i+=4){
    const g = d[i]*0.22 + d[i+1]*0.72 + d[i+2]*0.06;
    let v = (g-128)*1.25 + 128;
    v = Math.max(0, Math.min(255, v))*0.92;
    d[i]=d[i+1]=d[i+2]=v;
  }
  ctx.putImageData(id,0,0);
  const vg = ctx.createRadialGradient(w/2,h/2,Math.min(w,h)*0.15,w/2,h/2,Math.max(w,h)*0.75);
  vg.addColorStop(0,"transparent"); vg.addColorStop(1,"rgba(0,0,0,.55)");
  ctx.fillStyle = vg; ctx.fillRect(0,0,w,h);
}
function bindUpload(boxId, fileId, canvasId, mode){
  const box = document.getElementById(boxId);
  const file = document.getElementById(fileId);
  const cv = document.getElementById(canvasId);

  box.addEventListener('click', ()=> file.click());
  file.addEventListener('change', ()=>{
    const f = file.files && file.files[0];
    if(!f) return;
    const reader = new FileReader();
    reader.onload = () => {
      const img = new Image();
      img.onload = () => {
        const W = cv.width = box.offsetWidth*2;
        const H = cv.height = box.offsetHeight*2;
        const ctx = cv.getContext('2d');
        ctx.clearRect(0,0,W,H);
        ctx.fillStyle="#000"; ctx.fillRect(0,0,W,H);
        coverDraw(ctx, img, W, H);
        if(mode === 'portrait') grayscaleVignette(ctx,W,H);
      };
      img.src = reader.result;
    };
    reader.readAsDataURL(f);
  });
}
bindUpload('pb-left','file-left','cv-left','portrait');
bindUpload('pb-right','file-right','cv-right','portrait');
bindUpload('pb-icon','file-icon','cv-icon','icon');

// ── NAME SCRAMBLE ─────────────────────────────────────────────
function scramble(el,target,delay){
  const chars='0123456789ABCDEFGHIJKLMNOPQRSTUVWXYZ#@$%';
  setTimeout(()=>{
    let rev=0,f=0;
    const iv=setInterval(()=>{
      let out='';
      for(let i=0;i<target.length;i++){
        if(target[i]===' '){out+=' ';continue}
        out+=i<rev?target[i]:chars[~~(Math.random()*chars.length)];
      }
      el.textContent=out;f++;
      if(f%5===0&&rev<target.length)rev++;
      if(rev>=target.length){el.textContent=target;clearInterval(iv)}
    },45);
  },delay);
}
setTimeout(()=>{
  const nl=document.getElementById('nm-left');
  const nr=document.getElementById('nm-right');
  nl.textContent='';nr.textContent='';
  scramble(nl,'MOIRANGTHEM DANIEL SINGH',300);
  scramble(nr,'RYAN AWUNGSHI',800);
},250);

// ── STATUS CENTER ─────────────────────────────────────────────
const statusSeq=['INITIALIZING','LOADING MODEL','CALIBRATING','RUNNING TESTS','READY'];
let sIdx=0;
const statusEl=document.getElementById('statusVal');
const hexEl=document.getElementById('hexDisp');

function tickHex(){
  let h='';
  for(let i=0;i<4;i++){
    for(let j=0;j<2;j++) h+='0123456789ABCDEF'[~~(Math.random()*16)];
    if(i<3) h+=' ';
  }
  hexEl.textContent=h;
}
setInterval(tickHex,350);

setInterval(()=>{
  sIdx=(sIdx+1)%statusSeq.length;
  statusEl.textContent=statusSeq[sIdx];
},2200);

setTimeout(()=>{
  function animBar(id,pid,target,delay){
    setTimeout(()=>{
      let v=0;const iv=setInterval(()=>{
        v=Math.min(v+1.2,target);
        document.getElementById(id).style.width=v+'%';
        document.getElementById(pid).textContent=~~v+'%';
        if(v>=target)clearInterval(iv);
      },25);
    },delay);
  }
  animBar('bar1','b1p',78,200);
  animBar('bar2','b2p',65,600);
  animBar('bar3','b3p',50,1000);
},600);

// ── MARQUEE ───────────────────────────────────────────────────
const items=[
  '🔴 Round 1 Live · Feb 11–17 2025',
  '📋 Submit: Problem Statement · Solution · Proposal · Video',
  '⚡ Judging: Feb 18 · Shortlist: Feb 19',
  '🏥 HealthGuard AI · Symptom → ML → Diagnosis',
  '🛡 Team Codex 2.0 · Daniel × Ryan',
  '🌾 Serving Rural Communities Worldwide',
];
const mq=document.getElementById('mq');
for(let pass=0;pass<2;pass++){
  items.forEach(txt=>{
    const el=document.createElement('div');el.className='marquee-item';
    el.innerHTML=`<div class="marquee-dot"></div>${txt}`;
    mq.appendChild(el);
  });
}

// ── SCROLL REVEAL ─────────────────────────────────────────────
const obs=new IntersectionObserver(entries=>{
  entries.forEach(e=>{if(e.isIntersecting) e.target.classList.add('in')});
},{threshold:.1,rootMargin:'0px 0px -40px 0px'});
document.querySelectorAll('.reveal,.flow-step').forEach(el=>obs.observe(el));

// ── CHAT DEMO ─────────────────────────────────────────────────
const script=[
  {r:'bot',t:'👋 Hello! Describe your symptoms.'},
  {r:'user',t:'Headache, nausea, dizziness — since morning.'},
  {r:'bot',t:'⚙️ Analyzing 3 symptoms across 132 vectors...'},
  {r:'bot',t:'🎯 Likely: <b>Heatstroke</b> · Confidence 87% · Risk 🔴 HIGH<br>🌡️ 43°C outside · 🏥 Hospital 4.2km — Hydrate & seek shade now.'},
];
let ci=0,cStarted=false;
const chatEl=document.getElementById('chatMsgs');
const chatObs=new IntersectionObserver(entries=>{
  entries.forEach(e=>{if(e.isIntersecting&&!cStarted){cStarted=true;nextMsg()}});
},{threshold:.4});
chatObs.observe(chatEl);

function nextMsg(){
  if(ci>=script.length)return;
  const m=script[ci];ci++;
  const d=document.createElement('div');
  d.className=`cm ${m.r}`;d.innerHTML=m.t;
  chatEl.appendChild(d);chatEl.scrollTop=chatEl.scrollHeight;
  setTimeout(()=>d.classList.add('show'),50);
  setTimeout(nextMsg,m.r==='bot'?1400:900);
}
</script>
</body>
</html>
