<!DOCTYPE html>
<html lang="bn">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Test Bazar — Chapter 2 | NEP 1986 & 2020</title>
<link href="https://fonts.googleapis.com/css2?family=Tiro+Bangla&family=Syne:wght@400;600;700;800&display=swap" rel="stylesheet">
<style>
*{margin:0;padding:0;box-sizing:border-box}
body{font-family:'Syne',sans-serif;background:#f0faf4;min-height:100vh;color:#1c2e24}
.top-bar{background:#1a7a4a;padding:0.8rem 1.5rem;display:flex;justify-content:space-between;align-items:center;position:sticky;top:0;z-index:100}
.top-logo{font-size:1.1rem;font-weight:800;color:white}.top-logo span{color:#f9a825}
.timer-box{background:rgba(255,255,255,0.15);border-radius:8px;padding:0.4rem 1rem;display:flex;align-items:center;gap:6px;font-size:1rem;font-weight:700;color:white}
.timer-box.danger{background:#dc3545}
.main{max-width:820px;margin:0 auto;padding:1.5rem 1rem}
.hub-header{text-align:center;margin-bottom:2rem}
.hub-header h1{font-family:'Tiro Bangla',serif;font-size:2rem;color:#1c2e24}
.hub-header p{font-family:'Tiro Bangla',serif;font-size:0.95rem;color:#5a7a66;margin-top:0.3rem}
.set-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(220px,1fr));gap:1.2rem;margin-top:1.5rem}
.set-card{background:white;border-radius:14px;padding:1.5rem;border:1.5px solid #c5dccb;transition:all 0.2s;cursor:pointer;color:#1c2e24;box-shadow:0 2px 8px rgba(26,122,74,0.06)}
.set-card:hover{transform:translateY(-3px);border-color:#1a7a4a;box-shadow:0 6px 20px rgba(26,122,74,0.12)}
.set-card .icon{font-size:2rem;margin-bottom:0.3rem}
.set-card .set-num{font-weight:700;font-size:1rem;color:#1a7a4a}
.set-card .set-title{font-family:'Tiro Bangla',serif;font-size:0.8rem;color:#5a7a66;margin:0.2rem 0 0.5rem}
.set-card .set-meta{display:flex;gap:1rem;font-size:0.7rem;color:#5a7a66}
.set-card .set-meta span{background:#f0faf4;padding:0.15rem 0.6rem;border-radius:4px}
.quiz-info{background:white;border-radius:12px;padding:1rem 1.2rem;margin-bottom:1.2rem;border:1px solid #c5dccb;display:flex;gap:1rem;flex-wrap:wrap}
.info-item{font-family:'Tiro Bangla',serif;font-size:0.85rem;color:#5a7a66}
.info-item strong{color:#1a7a4a}
.progress-wrap{background:#c5dccb;border-radius:4px;height:6px;margin-bottom:1.2rem;overflow:hidden}
.progress-fill{height:100%;background:#1a7a4a;border-radius:4px;transition:width 0.3s}
.q-card{background:white;border-radius:14px;padding:1.4rem;margin-bottom:1rem;border:1px solid #c5dccb;box-shadow:0 2px 10px rgba(26,122,74,0.06)}
.q-num{font-size:0.75rem;font-weight:700;color:#e8730a;letter-spacing:1px;text-transform:uppercase;margin-bottom:0.6rem}
.q-text{font-family:'Tiro Bangla',serif;font-size:1rem;color:#1c2e24;line-height:1.7;margin-bottom:1.1rem}
.opts{display:flex;flex-direction:column;gap:0.6rem}
.opt{display:flex;align-items:flex-start;gap:10px;padding:0.7rem 1rem;border:1.5px solid #c5dccb;border-radius:10px;cursor:pointer;transition:all 0.15s;background:white;text-align:left;width:100%;font-family:inherit}
.opt:hover:not(.disabled){border-color:#1a7a4a;background:#f0faf4}
.opt-circle{min-width:28px;height:28px;border-radius:50%;border:1.5px solid #c5dccb;display:flex;align-items:center;justify-content:center;font-size:12px;font-weight:700;color:#5a7a66;flex-shrink:0;transition:all 0.15s}
.opt-text{font-family:'Tiro Bangla',serif;font-size:0.92rem;color:#1c2e24;line-height:1.6;padding-top:2px}
.opt.correct{border-color:#1a7a4a;background:#e8f7ef}
.opt.correct .opt-circle{background:#1a7a4a;border-color:#1a7a4a;color:white}
.opt.wrong{border-color:#dc3545;background:#fdf0f0}
.opt.wrong .opt-circle{background:#dc3545;border-color:#dc3545;color:white}
.opt.disabled{cursor:default}
.explanation{background:#f0faf4;border-left:3px solid #1a7a4a;border-radius:0 8px 8px 0;padding:0.8rem 1rem;margin-top:0.8rem;display:none}
.explanation.show{display:block}
.explanation p{font-family:'Tiro Bangla',serif;font-size:0.88rem;color:#2c4035;line-height:1.7}
.explanation strong{color:#1a7a4a}
.nav-row{display:flex;justify-content:space-between;align-items:center;margin-top:0.8rem}
.score-show{font-family:'Tiro Bangla',serif;font-size:0.85rem;color:#5a7a66}
.next-btn{background:#1a7a4a;color:white;border:none;padding:0.6rem 1.4rem;border-radius:8px;font-family:'Tiro Bangla',serif;font-size:0.9rem;cursor:pointer;transition:all 0.15s}
.next-btn:hover{background:#2aad68}
.next-btn:disabled{background:#c5dccb;cursor:default}
.result-wrap{background:white;border-radius:14px;padding:2rem;text-align:center;border:1px solid #c5dccb;display:none}
.result-wrap.show{display:block}
.result-icon{font-size:3rem;margin-bottom:0.5rem}
.result-score{font-size:3.5rem;font-weight:800;color:#1a7a4a}
.result-total{font-size:1rem;color:#5a7a66;margin-bottom:0.5rem;font-family:'Tiro Bangla',serif}
.result-grade{font-size:1.2rem;font-weight:600;color:#1c2e24;margin-bottom:1.5rem;font-family:'Tiro Bangla',serif}
.result-bars{display:grid;grid-template-columns:1fr 1fr 1fr;gap:0.8rem;margin-bottom:1.5rem}
.result-bar{background:#f0faf4;border-radius:10px;padding:0.8rem;text-align:center}
.rb-num{font-size:1.4rem;font-weight:800}
.rb-label{font-family:'Tiro Bangla',serif;font-size:0.8rem;color:#5a7a66;margin-top:0.2rem}
.retry-btn{background:#1a7a4a;color:white;border:none;padding:0.75rem 2rem;border-radius:8px;font-family:'Tiro Bangla',serif;font-size:1rem;cursor:pointer;margin-right:0.5rem}
.review-btn{background:white;color:#1a7a4a;border:1.5px solid #1a7a4a;padding:0.75rem 2rem;border-radius:8px;font-family:'Tiro Bangla',serif;font-size:1rem;cursor:pointer}
.back-btn{background:white;color:#5a7a66;border:1.5px solid #c5dccb;padding:0.75rem 2rem;border-radius:8px;font-family:'Tiro Bangla',serif;font-size:1rem;cursor:pointer;margin-top:0.6rem}
.login-overlay{position:fixed;top:0;left:0;width:100%;height:100%;background:rgba(0,0,0,0.5);display:none;align-items:center;justify-content:center;z-index:999}
.login-overlay.active{display:flex}
.login-modal{background:white;border-radius:16px;padding:2.5rem;max-width:420px;width:90%;box-shadow:0 20px 60px rgba(0,0,0,0.3)}
.login-modal h2{font-family:'Tiro Bangla',serif;font-size:1.3rem;color:#1c2e24;text-align:center;margin-bottom:0.3rem}
.login-modal p{font-family:'Tiro Bangla',serif;font-size:0.85rem;color:#5a7a66;text-align:center;margin-bottom:1.5rem}
.login-modal label{font-size:0.8rem;font-weight:600;color:#1c2e24;display:block;margin-bottom:0.3rem}
.login-modal input{width:100%;padding:0.7rem 1rem;border:1.5px solid #c5dccb;border-radius:8px;font-size:0.95rem;margin-bottom:1rem;font-family:'Tiro Bangla',serif}
.login-modal input:focus{outline:none;border-color:#1a7a4a}
.login-modal .login-btn{width:100%;background:#1a7a4a;color:white;border:none;padding:0.75rem;border-radius:8px;font-size:1rem;font-weight:700;cursor:pointer;font-family:'Tiro Bangla',serif}
.login-modal .login-btn:hover{background:#2aad68}
.login-modal .login-btn:disabled{background:#c5dccb;cursor:not-allowed}
.login-modal .error-msg{color:#dc3545;font-size:0.8rem;text-align:center;margin-top:0.5rem;font-family:'Tiro Bangla',serif;display:none}
.login-modal .limit-info{background:#fff3cd;border:1px solid #ffc107;border-radius:8px;padding:0.6rem 1rem;margin-bottom:1rem;font-family:'Tiro Bangla',serif;font-size:0.8rem;color:#856404;display:none}
.login-modal .set-name-display{background:#f0faf4;border-radius:8px;padding:0.5rem;text-align:center;margin-bottom:1rem;font-family:'Tiro Bangla',serif;font-size:0.9rem;color:#1a7a4a;font-weight:600}
.hidden{display:none !important}
</style>
</head>
<body>

<div class="top-bar">
  <div class="top-logo">Test <span>Bazar</span></div>
  <div class="timer-box" id="timerBox">⏱ <span id="timerDisplay">10:00</span></div>
</div>

<div class="main">

  <!-- LOGIN OVERLAY -->
  <div class="login-overlay" id="loginOverlay">
    <div class="login-modal">
      <h2>🔐 লগইন করুন</h2>
      <p>Test শুরু করতে আপনার ইউজারনেম ও পাসওয়ার্ড দিন</p>
      <div class="set-name-display" id="loginSetName">📚 সেট ১</div>
      <div class="limit-info" id="limitInfo">⚠️ <span id="limitMsg"></span></div>
      <label>ইউজারনেম</label>
      <input type="text" id="loginUsername" placeholder="আপনার ইউজারনেম লিখুন">
      <label>পাসওয়ার্ড</label>
      <input type="password" id="loginPassword" placeholder="আপনার পাসওয়ার্ড লিখুন" onkeydown="if(event.key==='Enter') doLoginFromSet()">
      <button class="login-btn" id="loginBtn" onclick="doLoginFromSet()">✅ লগইন করে Test শুরু করো</button>
      <div class="error-msg" id="loginError">❌ ভুল ইউজারনেম বা পাসওয়ার্ড। আবার চেষ্টা করুন।</div>
    </div>
  </div>

  <!-- HUB PAGE -->
  <div id="hubPage">
    <div class="hub-header">
      <h1>📚 অধ্যায় ২: জাতীয় শিক্ষানীতি — ১৯৮৬ ও ২০২০</h1>
      <p>নিচের সেটগুলো থেকে বেছে নিন। Test শুরু করতে সেটে ক্লিক করুন এবং লগইন করুন।</p>
      <div id="hubUserInfo" style="font-family:'Tiro Bangla',serif;font-size:0.85rem;color:#5a7a66;margin-top:0.5rem;"></div>
    </div>
    <div class="set-grid" id="setGrid"></div>
  </div>

  <!-- TEST AREA -->
  <div id="testArea" class="hidden">
    <div class="quiz-info">
      <div class="info-item">🎓 <strong>জাতীয় শিক্ষানীতি</strong> — <span id="testSetLabel">সেট ১</span></div>
      <div class="info-item">📝 <span id="testTopic">প্রাথমিক ধারণা ও গঠন</span></div>
    </div>
    <div class="progress-wrap"><div class="progress-fill" id="progressFill" style="width:0%"></div></div>
    <div class="q-card" id="qCard">
      <div class="q-num" id="qNum">প্রশ্ন ১ / ১৫</div>
      <div class="q-text" id="qText"></div>
      <div class="opts" id="qOpts"></div>
      <div class="explanation" id="explanation"><p id="explanationText"></p></div>
      <div class="nav-row">
        <div class="score-show" id="scoreShow">সঠিক: ০ | ভুল: ০</div>
        <button class="next-btn" id="nextBtn" onclick="nextQ()" disabled>পরবর্তী →</button>
      </div>
    </div>
  </div>

  <!-- RESULT AREA -->
  <div class="result-wrap" id="resultWrap">
    <div class="result-icon" id="resultIcon"></div>
    <div class="result-score" id="finalScore"></div>
    <div class="result-total">/ ১৫</div>
    <div class="result-grade" id="resultGrade"></div>
    <div class="result-bars">
      <div class="result-bar"><div class="rb-num" id="rbCorrect" style="color:#1a7a4a"></div><div class="rb-label">সঠিক</div></div>
      <div class="result-bar"><div class="rb-num" id="rbWrong" style="color:#dc3545"></div><div class="rb-label">ভুল</div></div>
      <div class="result-bar"><div class="rb-num" id="rbPct" style="color:#e8730a"></div><div class="rb-label">স্কোর</div></div>
    </div>
    <div id="attemptInfo" style="font-family:'Tiro Bangla',serif;font-size:0.85rem;color:#5a7a66;margin-bottom:1rem;"></div>
    <button class="retry-btn" onclick="startQuiz(currentSetId)">আবার চেষ্টা করো</button>
    <button class="review-btn" onclick="showReview()">উত্তর দেখো</button>
    <br>
    <button class="back-btn" onclick="goToHub()">← Hub এ ফিরে যাও</button>
  </div>

</div>

<script>
// ============================================================
//  ডেটা
// ============================================================
var MAX_ATTEMPTS = 10;
var currentSetId = 1;
var cur = 0, score = 0, wrong = 0, answered = false, timerInterval, timeLeft = 10 * 60;
var userAnswers = [];
var isLoggedIn = false;
var currentUser = null;
var pendingSetId = null;
var LABELS = ['ক', 'খ', 'গ', 'ঘ'];

// ============================================================
//  ইউজার ডেটাবেস
// ============================================================
var userData = [
  {username:"alfa_romeo", password:"ARx7P29m", attempts:{}},
  {username:"santos", password:"St8Qv41L", attempts:{}},
  {username:"falcon", password:"Fc3MZ92k", attempts:{}},
  {username:"titan", password:"Ti6Rp84W", attempts:{}},
  {username:"matrix", password:"Mx5Kd73N", attempts:{}},
  {username:"phoenix", password:"Ph9Js28V", attempts:{}},
  {username:"cobra", password:"Cb4Ln65X", attempts:{}},
  {username:"shadow", password:"Sh7Wp19Q", attempts:{}},
  {username:"rocket", password:"Rc2Ty86M", attempts:{}},
  {username:"warrior", password:"Wr8Az34K", attempts:{}},
  {username:"eagle", password:"Eg5Xq72P", attempts:{}},
  {username:"thunder", password:"Th1Vk93R", attempts:{}},
  {username:"dragon", password:"Dr6Hm48N", attempts:{}},
  {username:"panther", password:"Pa9Nc25J", attempts:{}},
  {username:"viking", password:"Vi4Qs87L", attempts:{}},
  {username:"hunter", password:"Hu7Bp31X", attempts:{}},
  {username:"legend", password:"Le2Mz64T", attempts:{}},
  {username:"ranger", password:"Ra8Kd95W", attempts:{}},
  {username:"knight", password:"Kn3Xp57Q", attempts:{}},
  {username:"turbo", password:"Tu6Lv21N", attempts:{}},
  {username:"alpha", password:"Ap9Rm83K", attempts:{}},
  {username:"bravo", password:"Br5Yt42M", attempts:{}},
  {username:"charlie", password:"Ch7Wq16P", attempts:{}},
  {username:"delta", password:"De4Nk78X", attempts:{}},
  {username:"echo", password:"Ec8Jp35V", attempts:{}},
  {username:"foxtrot", password:"Fx2Lm94Q", attempts:{}},
  {username:"gamma", password:"Ga6Xs27T", attempts:{}},
  {username:"helix", password:"He1Vp85N", attempts:{}},
  {username:"inferno", password:"In9Qk43L", attempts:{}},
  {username:"jaguar", password:"Ja5Mz72W", attempts:{}},
  {username:"karma", password:"Ka8Rp14X", attempts:{}},
  {username:"laser", password:"La3Tn67Q", attempts:{}},
  {username:"meteor", password:"Me7Wx29P", attempts:{}},
  {username:"nova", password:"No4Kz86M", attempts:{}},
  {username:"omega", password:"Om2Lp53V", attempts:{}},
  {username:"pegasus", password:"Pe9Xq71N", attempts:{}},
  {username:"quantum", password:"Qu5Vr38K", attempts:{}},
  {username:"rebel", password:"Re8Mz24T", attempts:{}},
  {username:"storm", password:"St1Kp97W", attempts:{}},
  {username:"tornado", password:"To6Nx45Q", attempts:{}},
  {username:"ultra", password:"Ul3Wp82M", attempts:{}},
  {username:"vector", password:"Ve7Lq19X", attempts:{}},
  {username:"wolf", password:"Wo4Rm63P", attempts:{}},
  {username:"xenon", password:"Xe9Tk25N", attempts:{}},
  {username:"yodha", password:"Yo2Vz78K", attempts:{}},
  {username:"zeus", password:"Ze8Mp41Q", attempts:{}},
  {username:"atlas", password:"At5Lx93W", attempts:{}},
  {username:"blaze", password:"Bl1Qn67M", attempts:{}},
  {username:"cyclone", password:"Cy7Rp34T", attempts:{}},
  {username:"dynamo", password:"Dy4Wk82X", attempts:{}},
  {username:"apollo", password:"Ap7Kx94Lm", attempts:{}},
  {username:"archer", password:"Ar3Vp62Qn", attempts:{}},
  {username:"asteroid", password:"As8Tm15Rw", attempts:{}},
  {username:"bandit", password:"Ba5Qz71Kp", attempts:{}},
  {username:"bison", password:"Bi9Ln34Xt", attempts:{}},
  {username:"bullet", password:"Bu2Wr86Mv", attempts:{}},
  {username:"canyon", password:"Ca6Xp29Qk", attempts:{}},
  {username:"captain", password:"Cp1Mz75Ln", attempts:{}},
  {username:"comet", password:"Co8Tk43Wp", attempts:{}},
  {username:"cyclonex", password:"Cy4Vr92Km", attempts:{}},
  {username:"diesel", password:"Di7Lp18Qx", attempts:{}},
  {username:"domino", password:"Do3Wn67Rt", attempts:{}},
  {username:"duke", password:"Du9Kx25Mv", attempts:{}},
  {username:"empire", password:"Em5Qp84Ln", attempts:{}},
  {username:"explorer", password:"Ex2Vz39Kt", attempts:{}},
  {username:"fighter", password:"Fi8Lm71Qw", attempts:{}},
  {username:"galaxy", password:"Ga4Tk26Xp", attempts:{}},
  {username:"gladiator", password:"Gl7Wp95Mn", attempts:{}},
  {username:"gravity", password:"Gr1Nx53Lq", attempts:{}},
  {username:"hawk", password:"Ha9Kz42Rt", attempts:{}},
  {username:"horizon", password:"Ho5Vm87Xp", attempts:{}},
  {username:"icefire", password:"Ic3Lp16Qn", attempts:{}},
  {username:"impact", password:"Im8Wr74Kt", attempts:{}},
  {username:"ironman", password:"Ir2Xq95Mv", attempts:{}},
  {username:"jetstar", password:"Je6Nk38Lp", attempts:{}},
  {username:"kingston", password:"Ki1Vp72Qw", attempts:{}},
  {username:"lightning", password:"Li9Tm45Rx", attempts:{}},
  {username:"majestic", password:"Ma4Kp83Ln", attempts:{}},
  {username:"monster", password:"Mo7Wz21Qt", attempts:{}},
  {username:"neptune", password:"Ne3Lx96Mv", attempts:{}},
  {username:"ninja", password:"Ni8Qr54Kp", attempts:{}},
  {username:"orbit", password:"Or2Vp73Ln", attempts:{}},
  {username:"patriot", password:"Pa6Tk18Qw", attempts:{}},
  {username:"pioneer", password:"Pi1Xm85Rt", attempts:{}},
  {username:"predator", password:"Pr9Lq47Kv", attempts:{}},
  {username:"proton", password:"Pt4Wn62Mx", attempts:{}},
  {username:"rapid", password:"Ra7Kx93Lp", attempts:{}},
  {username:"samurai", password:"Sa3Vp25Qn", attempts:{}},
  {username:"sniper", password:"Sn8Tm71Rw", attempts:{}},
  {username:"solaris", password:"So2Qk84Mv", attempts:{}},
  {username:"spartan", password:"Sp6Ln39Xt", attempts:{}},
  {username:"striker", password:"St1Wr57Kp", attempts:{}},
  {username:"summit", password:"Su9Xp26Lm", attempts:{}},
  {username:"taurus", password:"Ta5Vz91Qw", attempts:{}},
  {username:"tempest", password:"Te3Kp48Rt", attempts:{}},
  {username:"trident", password:"Tr8Wm72Ln", attempts:{}},
  {username:"valiant", password:"Va2Nx35Qk", attempts:{}},
  {username:"voyager", password:"Vo6Lp97Mx", attempts:{}},
  {username:"wildfire", password:"Wi1Tk64Rv", attempts:{}},
  {username:"zenith", password:"Ze9Qx28Lp", attempts:{}}
];

// ============================================================
//  প্রশ্ন ডেটা
// ============================================================
var allSets = {
  1: {
    name: 'সেট ১', icon: '📘', topic: 'জাতীয় শিক্ষানীতি ১৯৮৬ (প্রাথমিক ধারণা ও গঠন)',
    questions: [
      {q: '1986 খ্রিস্টাব্দের জাতীয় শিক্ষানীতিতে কয়টি অংশ আছে?', opts: ['১০টি', '১২টি', '১১টি', '১৩টি'], ans: 1, exp: '১৯৮৬ সালের শিক্ষানীতি সর্বমোট বারোটি অংশে বিভক্ত।'},
      {q: '১৯৮৬-এর শিক্ষানীতির কোন্ অংশে "সাম্যের জন্য শিক্ষা" বলা আছে?', opts: ['প্রথম', 'দ্বিতীয়', 'চতুর্থ', 'দ্বাদশ'], ans: 2, exp: 'চতুর্থ অংশে সাম্যের জন্য শিক্ষার কথা বলা হয়েছে।'},
      {q: 'শিক্ষানীতির কোন্ অংশে শিক্ষার বিষয়বস্তু ও প্রক্রিয়ার পুনবিন্যাস বলা হয়েছে?', opts: ['অষ্টম', 'দ্বিতীয়', 'একাদশ', 'দশম'], ans: 0, exp: 'অষ্টম অংশে এই বিষয়ে আলোচনা করা হয়েছে।'},
      {q: 'জাতীয় শিক্ষানীতির প্রতিবেদনে কয়টি Paragraph আছে?', opts: ['১৫৮টি', '১৪৯টি', '১০২টি', '১৫৭টি'], ans: 3, exp: 'বারোটি অংশে মোট ১৫৭টি স্তবক রয়েছে।'},
      {q: 'ECCE-এর পূর্ণরূপ কী?', opts: ['Early Childhood Care and Education', 'Elementary Childhood Care and Education', 'Early Child Care and Educare', 'Early Childhood Care and Educatum'], ans: 0, exp: 'শিশুর সামগ্রিক বিকাশের জন্য ECCE-র কথা বলা হয়েছে।'},
      {q: 'POA কথাটির অর্থ কী?', opts: ['Programme of Action', 'Programme of Act', 'Progress of Action', 'Progress of Act'], ans: 0, exp: '১৯৯২ সালে সংশোধিত POA বা Programme of Action।'},
      {q: '১৯৮৬-এর শিক্ষানীতির কোন্ অধ্যায়ে ভবিষ্যতের কথা বলা হয়েছে?', opts: ['প্রথম', 'দ্বিতীয়', 'দ্বাদশ', 'দশম'], ans: 2, exp: 'দ্বাদশ অংশে ভবিষ্যৎ নিয়ে আলোচনা করা হয়েছে।'},
      {q: 'পঞ্চম অধ্যায়ে কোন্ বিষয়ে আলোচনা করা হয়?', opts: ['ভূমিকা', 'শিক্ষক', 'শিক্ষাব্যবস্থাকে সক্রিয়করণ', 'বিভিন্ন স্তরের শিক্ষার পুনর্গঠন'], ans: 3, exp: 'পঞ্চম অংশে শিক্ষার বিভিন্ন স্তরের পুনর্গঠন নিয়ে আলোচনা।'},
      {q: 'কারিগরি ও পরিচালনার শিক্ষা কোন্ অধ্যায়ে?', opts: ['ষষ্ঠ', 'পঞ্চম', 'প্রথম', 'দ্বিতীয়'], ans: 0, exp: 'ষষ্ঠ অংশে কারিগরি ও পরিচালনার শিক্ষার কথা বলা হয়েছে।'},
      {q: '১৯৮৬-এর সাধারণ শিক্ষা কাঠামো কী?', opts: ['১০+২+৩', '১১+১+৩', '১০+১+১+৩', '৪+৪+২+২+৩'], ans: 0, exp: '১০+২+৩ কাঠামো (১০ বছর স্কুল, ২ বছর উচ্চমাধ্যমিক, ৩ বছর স্নাতক)।'},
      {q: '১৯৮৬-এর শিক্ষানীতি যে নামে প্রকাশিত হয়:', opts: ['Challenge of Education, A Policy Perspective', 'Challenge of Education, A Plan Perspective', 'Challenge on Education, A Policy Perspective', 'Change of Education, A Policy Perspective'], ans: 0, exp: '১৯৮৫ সালে Challenge of Education-A Policy Perspective প্রকাশিত হয়।'},
      {q: 'অপারেশন ব্ল্যাকবোর্ডের উদ্দেশ্য কী?', opts: ['প্রাথমিক শিক্ষার মান উন্নয়ন', 'শুধু পরিমাণগত উন্নয়ন', 'শুধু সুযোগ বৃদ্ধি', 'শুধু ব্ল্যাকবোর্ডের ব্যবস্থা'], ans: 0, exp: 'প্রাথমিক শিক্ষার পরিমাণগত ও গুণগতমান উন্নয়নই এর উদ্দেশ্য।'},
      {q: 'নবোদয় বিদ্যালয়ের উদ্দেশ্য কী?', opts: ['দরিদ্র শিশুদের জন্য', 'নারীদের জন্য', 'অনুন্নত শ্রেণির জন্য', 'মেধাসম্পন্ন শিশুদের জন্য'], ans: 3, exp: 'অত্যন্ত মেধাসম্পন্ন শিশুদের উন্নত শিক্ষার জন্য নবোদয় বিদ্যালয়।'},
      {q: 'সম্পদ ও পুনঃপরীক্ষায় কত বছর অন্তর মূল্যায়নের কথা বলা হয়েছে?', opts: ['৬ বছর', '৫ বছর', '৩ বছর', '২ বছর'], ans: 1, exp: 'প্রতি ৫ বছর অন্তর মূল্যায়ন করার কথা বলা হয়েছে।'},
      {q: 'CABE-এর ভূমিকা কী?', opts: ['সমন্বয় বিধান', 'সমন্বয় বিচ্ছিন্ন', 'জাতীয় বিদ্যালয়ে সমন্বয়', 'SABE গঠন'], ans: 0, exp: 'CABE মানবসম্পদ উন্নয়নের বিভিন্ন ক্ষেত্রের মধ্যে সমন্বয় বিধান করে।'}
    ]
  },
  2: {
    name: 'সেট ২', icon: '📗', topic: 'জাতীয় শিক্ষানীতি ১৯৮৬ (শিক্ষা ব্যবস্থাপনা ও অন্যান্য)',
    questions: [
      {q: 'শিক্ষা ব্যবস্থাপনার গুরুত্বপূর্ণ সুপারিশটি কী?', opts: ['বিকেন্দ্রীকরণ ও স্বায়ত্তশাসন', 'বিকেন্দ্রীকরণ ও আমলাতন্ত্র', 'কেন্দ্রীকরণ ও স্বায়ত্তশাসন', 'বিকেন্দ্রীকরণ ও সরকারিকরণ'], ans: 0, exp: 'শিক্ষাকে বিকেন্দ্রীকরণ ও প্রতিষ্ঠানে স্বায়ত্তশাসনের কথা বলা হয়েছে।'},
      {q: 'DIET-এর পূর্ণরূপ কী?', opts: ['Direct Institute for Education and Training', 'District Institute of Evaluation and Training', 'District Institute of Education and Training', 'District Inspector of Education and Training'], ans: 2, exp: 'District Institute of Education and Training — জেলা শিক্ষা ও প্রশিক্ষণ সংস্থা।'},
      {q: 'NCTE-এর পূর্ণরূপ কী?', opts: ['National Council for Teacher Education', 'National Counter of Teacher Education', 'National Centre of Teacher Education', 'National Control of Teacher Education'], ans: 0, exp: 'জাতীয় শিক্ষক শিক্ষণ সংস্থা বা NCTE।'},
      {q: 'SCERT-এর পূর্ণরূপ কী?', opts: ['State Council of Educational Record and Training', 'State Control of Educational Research and Training', 'State Council of Educational Research and Training', 'State Council of Educand Research and Training'], ans: 2, exp: 'রাজ্য শিক্ষা গবেষণা ও প্রশিক্ষণ সংস্থা।'},
      {q: 'ভারতের জাতীয় শিক্ষার সংস্থাটি কোনটি?', opts: ['AICTE', 'WHO', 'IMF', 'UNESCO'], ans: 0, exp: 'AICTE — All India Council of Technical Education।'},
      {q: '১৯৮৬-এর শিক্ষানীতির ২য় অংশে কী বলা হয়েছে?', opts: ['ভূমিকা', 'শিক্ষার উপাদান ও ভূমিকা', 'জাতীয় ব্যবস্থায় শিক্ষা', 'সাম্যের জন্য শিক্ষা'], ans: 1, exp: '২য় অংশে শিক্ষার উপাদান ও ভূমিকা নিয়ে আলোচনা।'},
      {q: '১৯৮৬-এর শিক্ষানীতির ৩য় অংশে কী বলা হয়েছে?', opts: ['ভূমিকা', 'শিক্ষার উপাদান ও ভূমিকা', 'জাতীয় ব্যবস্থায় শিক্ষা', 'সাম্যের জন্য শিক্ষা'], ans: 2, exp: '৩য় অংশে জাতীয় ব্যবস্থায় শিক্ষা নিয়ে আলোচনা।'},
      {q: 'সপ্তম অংশে কোন্ বিষয়ের উল্লেখ আছে?', opts: ['কারিগরি শিক্ষা', 'শিক্ষক', 'শিক্ষা ব্যবস্থাপনা', 'শিক্ষা ব্যবস্থাকে সক্রিয়করণ'], ans: 3, exp: '৭ম অংশে শিক্ষাব্যবস্থাকে সক্রিয়করণ নিয়ে আলোচনা।'},
      {q: 'দশম অংশে কোন্ বিষয়ের উল্লেখ আছে?', opts: ['সম্পদ ও পুনঃপরীক্ষা', 'শিক্ষা ব্যবস্থাপনা', 'ভবিষ্যৎ', 'শিক্ষক'], ans: 1, exp: '১০ম অংশে শিক্ষা ব্যবস্থাপনা নিয়ে আলোচনা।'},
      {q: '"শিক্ষকদের ওপরে আর কেউ হতে পারে না" — এই উক্তিটি কোন্ নীতিতে?', opts: ['১৯৬৮', '১৯৭৯', '১৯৮৬', 'কোঠারি কমিশন'], ans: 2, exp: '১৯৮৬ সালের শিক্ষানীতির ৯ম অংশে এই কথা বলা হয়েছে।'},
      {q: 'নবোদয় বিদ্যালয়ের অপর নাম কী?', opts: ['Pace Setting School', 'Pre Primary School', 'Lower Primary School', 'Higher Primary School'], ans: 0, exp: 'পেস সেটিং স্কুল বা আদর্শ বিদ্যালয়।'},
      {q: 'IGNOU প্রতিষ্ঠিত হয় কবে?', opts: ['১৯৮৬', '১৯৮৭', '১৯৮৫', '১৯৯৭'], ans: 2, exp: '১৯৮৫ সালে ইন্দিরা গান্ধী মুক্ত বিশ্ববিদ্যালয় প্রতিষ্ঠিত হয়।'},
      {q: 'চাকরি ও ডিগ্রির সম্পর্ক বিচ্ছেদের কথা কোন্ নীতিতে বলা হয়েছে?', opts: ['১৯৬৮', '১৯৮৬', '১৯৯২', 'কোনোটিই নয়'], ans: 1, exp: '১৯৮৬ সালের শিক্ষানীতিতে এই কথা বলা হয়েছে।'},
      {q: 'নবোদয় বিদ্যালয়ে মেয়েদের জন্য কত আসন সংরক্ষিত?', opts: ['এক-তৃতীয়াংশ', 'দুই-তৃতীয়াংশ', 'অর্ধেক', 'সম্পূর্ণ'], ans: 0, exp: 'মোট আসনের এক-তৃতীয়াংশ মেয়েদের জন্য সংরক্ষিত।'},
      {q: 'নবোদয় বিদ্যালয় কোন্ শ্রেণি থেকে শুরু?', opts: ['অষ্টম', 'পঞ্চম', 'ষষ্ঠ', 'সপ্তম'], ans: 2, exp: 'নবোদয় বিদ্যালয় ষষ্ঠ শ্রেণি থেকে শুরু হয়।'}
    ]
   },
  3: {
    name: 'সেট ৩', icon: '📕', topic: 'জাতীয় শিক্ষানীতি ১৯৮৬ (সংস্থা ও নীতিসমূহ)',
    questions: [
      {q: 'নবোদয় বিদ্যালয়ে নবম শ্রেণি থেকে শিক্ষার মাধ্যম কী?', opts: ['আঞ্চলিক ভাষা', 'হিন্দি অথবা ইংরেজি', 'অলচিকি ভাষা', 'উর্দু'], ans: 1, exp: 'নবম শ্রেণি থেকে হিন্দি অথবা ইংরেজি মাধ্যম ব্যবহৃত হয়।'},
      {q: 'নবোদয় বিদ্যালয়গুলি কে পরিচালনা করে?', opts: ['রাজ্য বোর্ড', 'আঞ্চলিক বোর্ড', 'কেন্দ্রীয় সরকার', 'CBSE'], ans: 3, exp: 'কেন্দ্রীয় মাধ্যমিক শিক্ষাবোর্ড বা CBSE পরিচালনা করে।'},
      {q: 'অপারেশন ব্ল্যাকবোর্ডের দায়িত্ব কার?', opts: ['রাজ্য সরকার', 'কেন্দ্রীয় সরকার', 'স্বেচ্ছাসেবী', 'কেন্দ্র+রাজ্য+স্বেচ্ছাসেবী'], ans: 3, exp: 'তিনটি স্তরের যৌথ দায়িত্ব এতে রয়েছে।'},
      {q: '১৯৮৬-এর শিক্ষানীতির অগ্রগতি কত বছর অন্তর মূল্যায়ন করতে হবে?', opts: ['২ বছর', '৫ বছর', '৭ বছর', '৯ বছর'], ans: 1, exp: 'প্রতি ৫ বছর অন্তর মূল্যায়ন করার কথা বলা হয়েছে।'},
      {q: 'কোন্ শিক্ষানীতিতে NCTE স্বশাসিত সংস্থা হিসেবে স্বীকৃত?', opts: ['১৯৬৮', '১৯৮৬', '১৯৭৯', 'কোনোটিই নয়'], ans: 1, exp: '১৯৮৬ সালের শিক্ষানীতিতে NCTE গঠনের কথা বলা হয়েছে।'},
      {q: 'সুসংহত শিশু বিকাশ কর্মসূচি কোন্ স্তরের জন্য?', opts: ['প্রারম্ভিক বাল্য', 'মধ্য বাল্য', 'প্রাক্-শৈশব', 'শৈশব'], ans: 2, exp: 'প্রাক্-শৈশব স্তরের শিশুদের জন্য এই কর্মসূচি।'},
      {q: 'NIEPA-এর পূর্ণরূপ কী?', opts: ['National Institute of Educational Planning and Administration', 'National Institute of Educant Planning and Administration', 'National Institute of Educational Plane and Administration', 'National Institution of Educational Planning and Administration'], ans: 0, exp: 'শিক্ষা পরিকল্পনার জাতীয় সংস্থা।'},
      {q: 'ন্যূনতম শিক্ষার মান কী?', opts: ['শ্রেণিভিত্তিক মান', 'ব্যক্তিভিত্তিক মান', 'সমাজভিত্তিক মান', 'কোনোটিই নয়'], ans: 0, exp: 'শ্রেণিভিত্তিক একটি নির্দিষ্ট মান।'},
      {q: 'NCC-এর পূর্ণরূপ কী?', opts: ['National Cadet Corps', 'Nation Core Curriculum', 'National Control Camp', 'National Central Council'], ans: 0, exp: 'ন্যাশনাল ক্যাডেট কর্পস।'},
      {q: 'AICTE-এর পূর্ণরূপ কী?', opts: ['All India Council of Technical Education', 'All Indian Council of Technical Education', 'All India Control of Technical Education', 'All India Council of Technology Education'], ans: 0, exp: 'অল ইন্ডিয়া কাউন্সিল অফ টেকনিক্যাল এডুকেশন।'},
      {q: 'অপারেশন ব্ল্যাকবোর্ড কোন্ শিক্ষানীতিতে বলা হয়েছে?', opts: ['১৯৬৮', '১৯৮৬', '১৯৬৯', 'কোনোটিই নয়'], ans: 1, exp: '১৯৮৬ সালের শিক্ষানীতিতে এই কর্মসূচি নেওয়া হয়।'},
      {q: 'স্বশাসিত মহাবিদ্যালয়ের কথা কোন্ কমিশনে বলা হয়েছে?', opts: ['১৯৮৬', '১৯৬৮', 'কোঠারি', 'বিশ্ববিদ্যালয়'], ans: 0, exp: '১৯৮৬ সালের শিক্ষানীতিতে স্বশাসিত কলেজের কথা বলা হয়।'},
      {q: 'NEP-2020 কোন্ শিক্ষাবর্ষে বাস্তবায়িত হয়?', opts: ['২০২০-২১', '২০২১-২২', '২০২২-২৩', '২০২৩-২৪'], ans: 3, exp: '২০২৩-২৪ শিক্ষাবর্ষে এটি বাস্তবায়িত হয়।'},
      {q: 'MHRD-এর নাম পরিবর্তন করে কী করা হয়েছে?', opts: ['মানবসম্পদ বিনিয়োগ', 'শিক্ষামন্ত্রক', 'মানবসম্পদ মন্ত্রক', 'কোনোটিই নয়'], ans: 1, exp: 'MHRD-এর নাম পরিবর্তন করে শিক্ষামন্ত্রক করা হয়েছে।'},
      {q: 'MCQ-এর পূর্ণরূপ কী?', opts: ['Multiple Choice Question', 'Multiple Chance Question', 'More Choice Question', 'Multiple Change Question'], ans: 0, exp: 'Multiple Choice Question — নৈর্ব্যক্তিক প্রশ্ন।'}
    ]
   },
  4: {
    name: 'সেট ৪', icon: '📙', topic: 'জাতীয় শিক্ষানীতি ২০২০ (প্রাথমিক ধারণা ও কাঠামো)',
    questions: [
      {q: 'প্রাক্-শৈশব যত্নের পাঠ্যক্রম তৈরিতে কোন্ মন্ত্রক যুক্ত?', opts: ['শিক্ষা মন্ত্রক', 'মহিলা ও শিশু মন্ত্রক', 'স্বাস্থ্য মন্ত্রক', 'সব ক-টি'], ans: 3, exp: 'তিনটি মন্ত্রক একত্রে কাজ করবে।'},
      {q: 'জীবনব্যাপী শিক্ষার শর্ত কী?', opts: ['সাক্ষরতা', 'গাণিতিক ধারণা', 'সাক্ষরতা ও গাণিতিক ধারণা', 'কোনোটিই নয়'], ans: 2, exp: 'সাক্ষরতা ও গাণিতিক ধারণা — উভয়ই প্রয়োজন।'},
      {q: 'সুযোগসুবিধা কম অঞ্চলে ছাত্র-শিক্ষক অনুপাত কত?', opts: ['৩০:১', '২৫:১', '৪৫:১', '২১:১'], ans: 1, exp: '২৫:১ এর কম হওয়া উচিত।'},
      {q: 'DIKSHA-এর পূর্ণরূপ কী?', opts: ['Distance Infrastructure for Knowledge Sharing', 'Digital Infrastructure for Knowledge Sharing', 'Digital India for Knowledge Sharing', 'Digital India for Knowledge Share'], ans: 1, exp: 'ডিজিটাল ইনফ্রাস্ট্রাকচার ফর নলেজ শেয়ারিং।'},
      {q: 'SOS-এর পূর্ণরূপ কী?', opts: ['State of School', 'State Open Schooling', 'State Open School', 'State Open Scheme'], ans: 2, exp: 'State Open School — মুক্ত বিদ্যালয়।'},
      {q: 'SIOS-এর পূর্ণরূপ কী?', opts: ['State Institutes of Open School', 'State Institutes of Open Schooling', 'State Institutes of Over Scheme', 'State Institution of Open Schooling'], ans: 1, exp: 'রাজ্য মুক্ত বিদ্যালয় সংস্থা।'},
      {q: 'শিক্ষার মানোন্নয়নে এলাকার জনগণকে কী কাজে নিযুক্ত করা হবে?', opts: ['এক-এক করে শিক্ষাদান', 'সাক্ষরতা পাঠদান', 'ক্যারিয়ার নির্দেশনা', 'সব ক-টি'], ans: 3, exp: 'তিনটি কাজেই নিযুক্ত করা হবে।'},
      {q: 'প্রস্তুতিমূলক স্তর কোন্ শ্রেণি নিয়ে গঠিত?', opts: ['১ম-২য়', '৩য়-৫ম', '৬ষ্ঠ-৮ম', '৯ম-১২শ'], ans: 1, exp: '৩য় থেকে ৫ম শ্রেণি (৩ বছর)।'},
      {q: 'মধ্যবর্তী স্তর কোন্ শ্রেণি নিয়ে গঠিত?', opts: ['১ম-২য়', '৩য়-৫ম', '৬ষ্ঠ-৮ম', '৯ম-১২শ'], ans: 2, exp: '৬ষ্ঠ থেকে ৮ম শ্রেণি (৩ বছর)।'},
      {q: 'অঙ্গনওয়াড়ির শিক্ষাকাল কত বছর?', opts: ['২', '৩', '৪', '১'], ans: 1, exp: 'প্রথম ৩ বছর অঙ্গনওয়াড়িতে।'},
      {q: 'পরীক্ষায় প্রশ্নের ধরন কী?', opts: ['শুধু MCQ', 'শুধু বর্ণনাত্মক', 'MCQ ও বর্ণনাত্মক', 'রচনাধর্মী ও মৌখিক'], ans: 2, exp: 'MCQ ও বর্ণনাত্মক — উভয় ধরনের প্রশ্ন থাকবে।'},
      {q: 'শিক্ষক নিয়োগের জন্য কী সম্প্রসারিত করতে হবে?', opts: ['MAT', 'TET', 'NET', 'DIET'], ans: 1, exp: 'TET বা শিক্ষক যোগ্যতা পরীক্ষা সম্প্রসারিত করতে হবে।'},
      {q: 'সামাজিক ন্যায়ের জন্য শিক্ষার লক্ষ্য কী?', opts: ['অন্তর্ভুক্তিকরণ', 'ন্যায়সংগত শিক্ষা', 'অন্তর্ভুক্তি ও ন্যায়সংগত শিক্ষা', 'কারিগরি শিক্ষা'], ans: 2, exp: 'অন্তর্ভুক্তি ও ন্যায়সংগত শিক্ষা — উভয়ই।'},
      {q: 'SSSA-এর পূর্ণরূপ কী?', opts: ['State School Standard Authority', 'State Scheme Standard Authority', 'State Schooling Standard Authority', 'State School Stand Authority'], ans: 0, exp: 'রাজ্য বিদ্যালয় মান কর্তৃপক্ষ।'},
      {q: 'উচ্চশিক্ষার নতুন দৃষ্টিভঙ্গি কী?', opts: ['সহজ কিন্তু আঁটোসাঁটো', 'হালকা কিন্তু আঁটোসাঁটো', 'হালকা কিন্তু যুক্তিনির্ভর', 'অল্প কিন্তু দীর্ঘস্থায়ী'], ans: 1, exp: 'হালকা কিন্তু আঁটোসাঁটো নিয়মকানুন।'}
    ]
   },
  5: {
    name: 'সেট ৫', icon: '📒', topic: 'জাতীয় শিক্ষানীতি ২০২০ (উচ্চশিক্ষা ও সংস্থা)',
    questions: [
      {q: 'ODL-এর পূর্ণরূপ কী?', opts: ['Open and Distance Learning', 'Open and Distance Learner', 'Over and Distance Learning', 'Open and Distributed Lane'], ans: 0, exp: 'Open and Distance Learning — মুক্ত ও দূরশিক্ষা।'},
      {q: 'HEIs-এর পূর্ণরূপ কী?', opts: ['Higher Education Institutions', 'Higher Education Institution', 'Higher Educational Institutions', 'Higher Education Institute'], ans: 0, exp: 'Higher Education Institutions — উচ্চশিক্ষা প্রতিষ্ঠান।'},
      {q: 'GER বাড়ালে কোন্ শিখনের সুযোগ বাড়বে?', opts: ['বৃত্তিমুখী', 'পেশাগত', 'সামাজিক', 'জীবনব্যাপী'], ans: 3, exp: 'জীবনব্যাপী শিখনের সুযোগ বাড়বে।'},
      {q: '৪ বছরের স্নাতক শেষে মাস্টার করতে কত বছর?', opts: ['২', '৩', '১', '১.৫'], ans: 2, exp: 'গবেষণাসহ স্নাতক করলে মাস্টার ১ বছর।'},
      {q: 'MERUS-এর পূর্ণরূপ কী?', opts: ['Multidisciplinary Education and Research University', 'Multi Educational and Rest University', 'Multidistance Education and Research University', 'Multiple Education and Research University'], ans: 0, exp: 'বহুবিভাগীয় শিক্ষা ও গবেষণা বিশ্ববিদ্যালয়।'},
      {q: 'CBCS-এর পূর্ণরূপ কী?', opts: ['Choice Based Cost System', 'Choice Base Credit System', 'Choice Based Credit System', 'Choice Based Credited System'], ans: 2, exp: 'Choice Based Credit System — ক্রেডিট ব্যবস্থা।'},
      {q: 'NHERA-এর পূর্ণরূপ কী?', opts: ['National Higher Education Regulatory Authority', 'Nation Higher Education Regulatory Authority', 'National Higher Educational Regulatory Authority', 'National Higher Regular Authority'], ans: 0, exp: 'জাতীয় উচ্চশিক্ষা নিয়ন্ত্রক কর্তৃপক্ষ।'},
      {q: 'NRF-এর পূর্ণরূপ কী?', opts: ['National Research Foundation', 'Nations Research Foundation', 'National Rear Foundation', 'National Research Fund'], ans: 0, exp: 'জাতীয় গবেষণা ফাউন্ডেশন।'},
      {q: 'HECI-এর পূর্ণরূপ কী?', opts: ['Higher Education Commission of India', 'Higher Education Commission of Institutions', 'High Education Commission of Instituion', 'Higher Educational Commission of India'], ans: 0, exp: 'ভারতের উচ্চশিক্ষা কমিশন।'},
      {q: 'HEGC-এর পূর্ণরূপ কী?', opts: ['Higher Education Grants Council', 'Higher Education Grants Commission', 'Higher Education Grants Committee', 'Higher Educational Grants Council'], ans: 0, exp: 'উচ্চশিক্ষা অনুদান পরিষদ।'},
      {q: 'NHEQF-এর পূর্ণরূপ কী?', opts: ['National Higher Education Qualification Framework', 'National Higher Education Quality Framework', 'National Higher Educational Qualification Foundation', 'National Higher Education Quality Form'], ans: 0, exp: 'জাতীয় উচ্চশিক্ষা যোগ্যতা কাঠামো।'},
      {q: 'NSQF-এর পূর্ণরূপ কী?', opts: ['National Skill Qualification Framework', 'National Skill Qualification Frame', 'National Skill Quality Framework', 'National Skilled Qualification Framework'], ans: 0, exp: 'জাতীয় দক্ষতা যোগ্যতা কাঠামো।'},
      {q: 'GEC-এর পূর্ণরূপ কী?', opts: ['General Education Council', 'General Educational Council', 'General Education Committee', 'General Educational Commission'], ans: 0, exp: 'সাধারণ শিক্ষা পরিষদ।'},
      {q: 'HEGC-এর মূল কাজ কী?', opts: ['ব্যয় নির্বাহ', 'নিয়ম তৈরি', 'অর্থব্যবস্থা পরিচালনা', 'বিনিয়োগ'], ans: 2, exp: 'উচ্চশিক্ষার অর্থব্যবস্থা পরিচালনা করা।'},
      {q: 'IITI-এর পূর্ণরূপ কী?', opts: ['Indian Institute of Translation and Interpretation', 'Indian Institutes of Translation and Interpretation', 'Indian Institutes of Translation and Interaction', 'Indian Institutes of Trade and Interaction'], ans: 0, exp: 'ভারতীয় অনুবাদ ও ব্যাখ্যা প্রতিষ্ঠান।'}
    ]
   },
  6: {
    name: 'সেট ৬', icon: '📘', topic: 'জাতীয় শিক্ষানীতি (প্রযুক্তি, ভাষা ও সাধারণ)',
    questions: [
      {q: 'ভারতীয় ভাষা, কলা ও সংস্কৃতির প্রসারে কী গুরুত্ব দেওয়া হয়েছে?', opts: ['লুপ্তপ্রায় ভাষা', 'স্থানীয় কলা ও সংস্কৃতি', 'অনুবাদ', 'সব ক-টি'], ans: 3, exp: 'তিনটি বিষয়েই গুরুত্ব দেওয়া হয়েছে।'},
      {q: 'AI-এর পূর্ণরূপ কী?', opts: ['Artificial Intelligence', 'Artificial Intellect', 'Art and Intellect', 'Artical and Intelligence'], ans: 0, exp: 'Artificial Intelligence — কৃত্রিম বুদ্ধি।'},
      {q: 'AI প্রযুক্তিতে NRF কটি কৌশল নেবে?', opts: ['১টি', '২টি', '৩টি', '৪টি'], ans: 2, exp: 'NRF তিনটি কৌশল অবলম্বন করবে।'},
      {q: 'NRF-এর তিনটি কৌশল কী?', opts: ['গবেষণা, প্রয়োগ, গুণমান', 'মূল গবেষণা, প্রয়োগ, আন্তর্জাতিক মান', 'পরিমাণগত, গুণগত, আন্তর্জাতিক', 'কোনোটিই নয়'], ans: 1, exp: 'মূল গবেষণা, প্রয়োগমূলক গবেষণা ও আন্তর্জাতিক মানের গবেষণা।'},
      {q: 'NETF-এর পূর্ণরূপ কী?', opts: ['National Educational Technology Forum', 'National Education Technology Forum', 'National Educational Techno Farm', 'National Educational Technology Foundation'], ans: 0, exp: 'জাতীয় শিক্ষক প্রযুক্তি ফোরাম।'},
      {q: 'ভারতকে জ্ঞানভিত্তিক অর্থনীতিতে রূপান্তর করতে কী সহায়তা করেছে?', opts: ['ডিজিটাল রাষ্ট্র', 'ডিজিটাল ভারত', 'ডিজিটাল প্রচার', 'ডিজিটাল রাজ্য'], ans: 1, exp: 'ডিজিটাল ভারত প্রচারাভিযান।'},
      {q: 'শিক্ষার ধারাবাহিক বিকাশে কোন্ সংস্থাকে শক্তিশালী করতে হবে?', opts: ['UGC', 'NCERT', 'CABE', 'DIET'], ans: 2, exp: 'CABE-কে শক্তিশালী করতে হবে।'},
      {q: 'শিক্ষকতা পেশায় উৎসাহ দিতে কী করতে হবে?', opts: ['শ্রদ্ধা', 'মর্যাদা', 'শ্রদ্ধা ও মর্যাদা পুনরুদ্ধার', 'বেতন বৃদ্ধি'], ans: 2, exp: 'শিক্ষকদের প্রতি শ্রদ্ধা ও পেশাগত মর্যাদা পুনরুদ্ধার করতে হবে।'},
      {q: 'অপারেশন ব্ল্যাকবোর্ড কোন্ স্তরের শিক্ষার জন্য?', opts: ['প্রাক্-প্রাথমিক', 'প্রাথমিক', 'মাধ্যমিক', 'উচ্চমাধ্যমিক'], ans: 1, exp: 'প্রাথমিক শিক্ষার উন্নয়নের জন্য।'},
      {q: 'নবোদয় বিদ্যালয় কোন্ স্তরের শিক্ষার জন্য?', opts: ['প্রাক্-প্রাথমিক', 'প্রাথমিক', 'মাধ্যমিক', 'উচ্চমাধ্যমিক'], ans: 2, exp: 'মাধ্যমিক শিক্ষার উন্নয়নের জন্য।'},
      {q: 'অপারেশন ব্ল্যাকবোর্ডে "ব্ল্যাকবোর্ড" কীসের প্রতীক?', opts: ['প্রতীক', 'নির্দেশনা', 'উপাদান', 'কোনোটিই নয়'], ans: 0, exp: 'শিক্ষা সহায়ক উপাদানের প্রতীক হিসেবে ধরা হয়েছে।'},
      {q: 'নবোদয় বিদ্যালয়ে কী ধরনের মূল্যায়ন থাকে?', opts: ['সামগ্রিক', 'ধারাবাহিক', 'আংশিক', 'অভ্যন্তরীণ'], ans: 1, exp: 'ধারাবাহিক মূল্যায়ন বা Continuous Evaluation।'},
      {q: '১৯৮৬-এর শিক্ষানীতির ৪র্থ অংশটি কী?', opts: ['ভূমিকা', 'শিক্ষার পুনর্গঠন', 'সাম্যের জন্য শিক্ষা', 'শিক্ষক'], ans: 2, exp: '"সাম্যের জন্য শিক্ষা" — ৪র্থ অংশ।'},
      {q: 'জীবনব্যাপী শিক্ষার মূল ভিত্তি কী?', opts: ['প্রত্যক্ষ শিক্ষা', 'সর্বজনীন সাক্ষরতা', 'শিক্ষার সংস্থা', 'প্রথাযুক্ত শিক্ষা'], ans: 1, exp: 'সর্বজনীন সাক্ষরতা।'},
      {q: 'প্রাথমিক শিক্ষার উন্নয়নের কর্মপ্রকল্প কোনটি?', opts: ['নবোদয়', 'ECCE', 'বয়স্কশিক্ষা', 'অপারেশন ব্ল্যাকবোর্ড'], ans: 3, exp: 'অপারেশন ব্ল্যাকবোর্ড।'}
    ]
   },
  7: {
    name: 'সেট ৭', icon: '📗', topic: 'শূন্যস্থান পূরণ ও মিশ্র প্রশ্নাবলি',
    questions: [
      {q: 'নবোদয় বিদ্যালয় ________ শিশুদের জন্য।', opts: ['মেধাসম্পন্ন', 'মাঝারি মেধাসম্পন্ন', 'গরিব', 'প্রতিবন্ধী'], ans: 0, exp: 'অত্যন্ত মেধাসম্পন্ন শিশুদের জন্য।'},
      {q: 'IGNOU প্রতিষ্ঠিত হয় ________ সালে।', opts: ['১৯৯৭', '১৯৯২', '১৯৯৩', '১৯৮৫'], ans: 3, exp: '১৯৮৫ সালে IGNOU প্রতিষ্ঠিত হয়।'},
      {q: 'উচ্চমাধ্যমিক পর্যন্ত শিক্ষা পরিচালনার জন্য ________ গঠিত হবে।', opts: ['SABE', 'ব্লক বোর্ড', 'জেলা শিক্ষাবোর্ড', 'জাতীয় বোর্ড'], ans: 2, exp: 'জেলা শিক্ষাবোর্ড গঠনের কথা বলা হয়েছে।'},
      {q: 'শিক্ষার জন্য অর্থ বরাদ্দ ________ শতাংশের বেশি করতে হবে।', opts: ['৪', '৫', '৬', '১০'], ans: 2, exp: '৬ শতাংশের বেশি করতে বলা হয়েছে।'},
      {q: 'NEP-2020-তে MHRD-এর নাম পরিবর্তন করে ________ করা হয়।', opts: ['শিক্ষা ও স্বাস্থ্য', 'শিক্ষামন্ত্রক', 'জাতীয় শিক্ষা', 'কোনোটিই নয়'], ans: 1, exp: 'শিক্ষামন্ত্রক করা হয়।'},
      {q: '৫ বছর বয়সের আগে শিশু ________-তে যাবে।', opts: ['প্রাক্-প্রাথমিক', 'প্রাথমিক', 'বুনিয়াদি', 'বালভাটিকা'], ans: 3, exp: 'বাল-বাটিকা বা অঙ্গনওয়াড়িতে যাবে।'},
      {q: 'PTR ________-এর কম হওয়া উচিত।', opts: ['৪০:১', '৩৫:১', '৩০:১', '২৫:১'], ans: 2, exp: '৩০:১ এর কম হওয়া উচিত।'},
      {q: 'NEP-2020-এর লক্ষ্য ________ স্তর পর্যন্ত সর্বজনীন প্রবেশাধিকার।', opts: ['প্রাথমিক', 'উচ্চমাধ্যমিক', 'উচ্চশিক্ষা', 'মাধ্যমিক'], ans: 3, exp: 'মাধ্যমিক স্তর পর্যন্ত ১০০% GER।'},
      {q: 'NEP-2020-এর বিদ্যালয় কাঠামো ________।', opts: ['৪+৪+২+২', '৫+৩+৩+৪', '৫+৩+৩', '৫+৩+২+২'], ans: 1, exp: '৫+৩+৩+৪ কাঠামো।'},
      {q: 'মাধ্যমিক স্তর ________ শ্রেণি নিয়ে গঠিত।', opts: ['৯ম-১০ম', '১১শ-১২শ', '৯ম-১২শ', '৮ম-১১শ'], ans: 2, exp: '৯ম থেকে ১২শ শ্রেণি (৪ বছর)।'},
      {q: 'পরীক্ষায় MCQ ও ________ প্রশ্ন থাকবে।', opts: ['মৌখিক', 'সৃজনধর্মী', 'বর্ণনাত্মক', 'অভীক্ষানির্ভর'], ans: 2, exp: 'MCQ ও বর্ণনাত্মক প্রশ্ন।'},
      {q: 'উচ্চশিক্ষায় ________ ফিরিয়ে আনতে হবে।', opts: ['উদার শিল্পকলা', 'মানবতা', 'নতুন পরীক্ষা', 'ক্রেডিট ব্যবস্থা'], ans: 0, exp: 'উদার শিল্পকলা বা Liberal Arts ফিরিয়ে আনতে হবে।'},
      {q: 'বিদ্যালয় ________ হিসেবে কাজ করবে।', opts: ['সামাজিক সংস্থা', 'সামাজিক চেতনা কেন্দ্র', 'স্থানীয় সংস্থা', 'শিক্ষার হাতিয়ার'], ans: 1, exp: 'সামাজিক চেতনা কেন্দ্র হিসেবে কাজ করবে।'},
      {q: 'স্তম্ভ মেলাও: (i) ২য় অংশ → (a) শিক্ষার উপাদান, (ii) ৪র্থ অংশ → (b) সাম্যের জন্য শিক্ষা, (iii) ৬ষ্ঠ অংশ → (c) কারিগরি শিক্ষা, (iv) ১০ম অংশ → (d) শিক্ষা ব্যবস্থাপনা', opts: ['i-a, ii-b, iii-c, iv-d', 'i-a, ii-c, iii-b, iv-d', 'i-b, ii-a, iii-c, iv-d', 'i-c, ii-b, iii-a, iv-d'], ans: 0, exp: 'সঠিক মিল: ২য়-শিক্ষার উপাদান, ৪র্থ-সাম্যের জন্য শিক্ষা, ৬ষ্ঠ-কারিগরি, ১০ম-শিক্ষা ব্যবস্থাপনা।'},
      {q: 'স্তম্ভ মেলাও: (i) প্রাথমিক শিক্ষা → (a) অপারেশন ব্ল্যাকবোর্ড, (ii) মাধ্যমিক শিক্ষা → (b) নবোদয়, (iii) প্রাক্-শৈশব → (c) বাল-ভাটিকা, (iv) ড্রপ আউট → (d) SOS', opts: ['i-a, ii-b, iii-c, iv-d', 'i-b, ii-a, iii-c, iv-d', 'i-a, ii-c, iii-d, iv-b', 'i-d, ii-c, iii-b, iv-a'], ans: 0, exp: 'প্রাথমিক-অপারেশন ব্ল্যাকবোর্ড, মাধ্যমিক-নবোদয়, প্রাক্-শৈশব-বালভাটিকা, ড্রপ আউট-SOS।'}
    ]
   },
  8: {
    name: 'সেট ৮', icon: '📙', topic: 'স্তম্ভ মেলানো ও সত্য/মিথ্যা',
    questions: [
      {q: 'বিবৃতি: (A) ১৯৬৮ সালে প্রথম শিক্ষানীতি হয়, (B) ১৯৮৬-এর শিক্ষানীতি ১০টি অংশে, (C) শিক্ষা একটি বিনিয়োগ। কোনটি সঠিক?', opts: ['A মিথ্যা, B সত্য, C মিথ্যা', 'A সত্য, B মিথ্যা, C সত্য', 'A সত্য, B সত্য, C মিথ্যা', 'A সত্য, B সত্য, C সত্য'], ans: 1, exp: '১৯৬৮ সত্য, ১৯৮৬ ১২টি অংশে (১০টি নয়), শিক্ষা বিনিয়োগ সত্য।'},
      {q: 'বিবৃতি: (A) অপারেশন ব্ল্যাকবোর্ড ১৪ বছর পর্যন্ত শিশুদের বিদ্যালয়মুখী করে, (B) নবোদয় ক্ষীণ মেধা সম্পন্নদের জন্য।', opts: ['A সত্য, B মিথ্যা', 'A ও B সত্য', 'A ও B মিথ্যা', 'A মিথ্যা, B সত্য'], ans: 0, exp: 'A সত্য, B মিথ্যা (নবোদয় মেধাবীদের জন্য)।'},
      {q: 'বিবৃতি: (A) NEP-2020 ভারতকে নলেজ সুপার পাওয়ার বানাবে, (B) প্রাক্-বিদ্যালয় থেকে মাধ্যমিক পর্যন্ত প্রবেশাধিকার, (C) উচ্চশিক্ষার বাণিজ্যিকীকরণ।', opts: ['A সত্য, B মিথ্যা, C সত্য', 'A মিথ্যা, B সত্য, C সত্য', 'A সত্য, B সত্য, C মিথ্যা', 'A মিথ্যা, B সত্য, C মিথ্যা'], ans: 2, exp: 'A ও B সত্য, C মিথ্যা (বাণিজ্যিকীকরণ প্রতিহত করতে চায়)।'},
      {q: 'বিবৃতি: (A) AI-তে NRF ৩টি কৌশল, (B) অনলাইন শিক্ষায় গুরুত্ব, (C) উদার শিল্পকলা ফিরিয়ে আনা, (D) ৪ বছরের স্নাতকে মাস্টার ১ বছর।', opts: ['A সত্য, B মিথ্যা, C সত্য, D মিথ্যা', 'A মিথ্যা, B মিথ্যা, C সত্য, D সত্য', 'A সত্য, B সত্য, C মিথ্যা, D মিথ্যা', 'A সত্য, B সত্য, C সত্য, D সত্য'], ans: 3, exp: 'চারটি বিবৃতিই সত্য।'},
      {q: '১৯৮৬-এর অংশগুলির সঠিক ক্রম কোনটি?', opts: ['শিক্ষার উপাদান, জাতীয় ব্যবস্থা, শিক্ষাব্যবস্থাপনা, শিক্ষক', 'শিক্ষার উপাদান, শিক্ষক, শিক্ষাব্যবস্থাপনা, জাতীয়', 'শিক্ষার উপাদান, জাতীয় ব্যবস্থা, শিক্ষক, শিক্ষাব্যবস্থাপনা', 'জাতীয়, শিক্ষক, ব্যবস্থাপনা, উপাদান'], ans: 2, exp: 'ক্রম: ২য় (উপাদান) → ৩য় (জাতীয়) → ৯ম (শিক্ষক) → ১০ম (শিক্ষাব্যবস্থাপনা)।'},
      {q: 'NEP-2020-এর শিক্ষাস্তরের সঠিক ক্রম কোনটি?', opts: ['প্রস্তুতিমূলক, বাল-বাটিকা, প্রাক্-বিদ্যালয়, মধ্যবর্তী', 'বাল-বাটিকা, প্রাক্-বিদ্যালয়, প্রস্তুতিমূলক, মধ্যবর্তী', 'প্রাক্-বিদ্যালয়, প্রস্তুতিমূলক, মধ্যবর্তী, বালভাটিকা', 'বাল-বাটিকা, প্রস্তুতিমূলক, মধ্যবর্তী, প্রাক্-বিদ্যালয়'], ans: 1, exp: '৫+৩+৩+৪ কাঠামোর সঠিক ক্রম।'},
      {q: 'শিক্ষা কমিশনগুলির সঠিক ক্রম কোনটি?', opts: ['মুদালিয়র, কোঠারি, জাতীয়, রাধাকৃষ্ণন', 'জাতীয়, কোঠারি, মুদালিয়র, রাধাকৃষ্ণন', 'রাধাকৃষ্ণন, মুদালিয়র, কোঠারি, জাতীয়', 'কোঠারি, রাধাকৃষ্ণন, মুদালিয়র, জাতীয়'], ans: 2, exp: 'কালানুক্রমিক সঠিক ক্রম।'},
      {q: '১৯৮৬-এর বিদ্যালয় কাঠামোর সঠিক স্তর কোনটি?', opts: ['প্রাথমিক → উচ্চ প্রাথমিক → উচ্চবিদ্যালয় → উচ্চমাধ্যমিক', 'প্রাক্-প্রাথমিক → প্রাথমিক → স্নাতক → স্নাতকোত্তর', 'অঙ্গনওয়াড়ি → বাল-বাটিকা → প্রস্তুতিমূলক → মাধ্যমিক', 'প্রাক্-প্রাথমিক → প্রস্তুতিমূলক → মধ্যবর্তী → মাধ্যমিক'], ans: 0, exp: '১৯৮৬ সালের ১০ বছরের স্কুল কাঠামো।'},
      {q: 'অপারেশন ব্ল্যাকবোর্ডের উদ্দেশ্য কোনটি সঠিক?', opts: ['মান উন্নয়ন, শিক্ষোপকরণ, পরিবেশ, শিক্ষক নিয়োগ কমানো', 'মান উন্নয়ন, শিক্ষোপকরণ, পরিবেশ, বিদ্যালয়মুখী', 'প্রাক্-প্রাথমিক মান উন্নয়ন', 'প্রতিবন্ধীদের শিক্ষা'], ans: 1, exp: 'চারটি প্রধান উদ্দেশ্য।'},
      {q: 'বিবৃতি (A): গ্রামের পরিকাঠামো উন্নয়ন, (B): গ্রাম-শহর ব্যবধান হ্রাস। সম্পর্ক?', opts: ['স্বাধীন', 'B, A-এর উদ্দেশ্য', 'A মিথ্যা, B সত্য', 'A সত্য, B মিথ্যা'], ans: 1, exp: 'গ্রাম-শহর ব্যবধান হ্রাসই উদ্দেশ্য।'},
      {q: 'বিবৃতি (A): প্রাথমিক শিক্ষার ফেজড ড্রাইভ, (B): অপারেশন ব্ল্যাকবোর্ড। সম্পর্ক?', opts: ['A সত্য, B মিথ্যা', 'A, B-এর কারণ', 'স্বাধীন', 'A-এর ফল B'], ans: 3, exp: 'ফেজড ড্রাইভের ফল হল অপারেশন ব্ল্যাকবোর্ড।'},
      {q: 'বিবৃতি (A): উদার শিল্পকলা ফিরিয়ে আনা, (B): STEM-এর সঙ্গে কলা যুক্ত। সম্পর্ক?', opts: ['স্বাধীন', 'A মিথ্যা, B সত্য', 'B, A-এর কারণ', 'A সত্য, B মিথ্যা'], ans: 2, exp: 'উদার শিল্পকলা ফিরিয়ে আনতেই STEM-এর সঙ্গে কলা যুক্ত করা।'},
      {q: 'বিবৃতি (A): MHRD রাজ্যগুলির সাথে কাজ করে, (B): CABE-এর ক্ষমতা হ্রাস।', opts: ['A সত্য, B মিথ্যা', 'A মিথ্যা, B সত্য', 'স্বাধীন', 'উভয় মিথ্যা'], ans: 0, exp: 'A সত্য, কিন্তু CABE-কে শক্তিশালী করার কথা (হ্রাস নয়)।'},
      {q: 'বিবৃতি-কারণ: (A) শিক্ষা ও গবেষণা সংগঠিত করলে জাতীয় উন্নয়ন, (R) মানবসম্পদ বিকাশ।', opts: ['A ও R সঠিক, A, R-এর ব্যাখ্যা', 'A ও R সঠিক কিন্তু ব্যাখ্যা নয়', 'A সঠিক, R ভুল', 'উভয় ভুল'], ans: 0, exp: 'শিক্ষা ও গবেষণার মাধ্যমে মানবসম্পদ বিকাশ হয় এবং জাতীয় উন্নয়ন হয়।'},
      {q: 'বিবৃতি-কারণ: (A) NEP-1986-তে শিশুর সামগ্রিক বিকাশের স্বীকৃতি, (R) ECCE অগ্রাধিকার।', opts: ['A সঠিক, R ভুল', 'A ভুল, R সঠিক', 'A ও R সঠিক, A, R-এর ব্যাখ্যা', 'A ও R সঠিক কিন্তু ব্যাখ্যা নয়'], ans: 2, exp: 'শিশুর সার্বিক বিকাশের জন্যই ECCE অগ্রাধিকার পেয়েছে।'}
    ]
   },
  9: {
    name: 'সেট ৯', icon: '📕', topic: 'সম্পর্ক, বিবৃতি-কারণ ও কেস স্টাডি',
    questions: [
      {q: 'বিবৃতি-কারণ: (A) ডিগ্রি ছাড়া চাকরিতে ডিগ্রির সম্পর্ক বিচ্ছেদ, (R) দক্ষ কর্মী নিয়োগ।', opts: ['A ও R সঠিক কিন্তু ব্যাখ্যা নয়', 'A ও R সঠিক ও ব্যাখ্যা', 'A সঠিক, R ভুল', 'A ভুল, R সঠিক'], ans: 1, exp: 'ডিগ্রির পরিবর্তে দক্ষ কর্মী নিয়োগের জন্যই এই বিচ্ছেদ।'},
      {q: 'বিবৃতি-কারণ: (A) অঙ্গনওয়াড়িতে উন্নত পরিকাঠামো, (R) গাণিতিক ধারণার বিকাশ।', opts: ['A সঠিক, R ভুল', 'A ভুল, R সঠিক', 'A ও R সঠিক ও ব্যাখ্যা', 'A ও R সঠিক কিন্তু ব্যাখ্যা নয়'], ans: 3, exp: 'উভয় সঠিক, কিন্তু পরিকাঠামো শুধু গাণিতিক ধারণার জন্য নয় — বৃহত্তর লক্ষ্যের অংশ।'},
      {q: 'কেস: "কর্মনিযুক্তির সুযোগ বৃদ্ধি, দক্ষ জনশক্তির চাহিদা পূরণ" — এর সাথে সম্পর্কিত:', opts: ['অপারেশন ব্ল্যাকবোর্ড', 'মুক্তশিক্ষা', 'প্রবহমান শিক্ষা', 'বৃত্তিমুখীকরণ'], ans: 3, exp: 'বৃত্তিমুখীকরণের মাধ্যমে কর্মসংস্থান বৃদ্ধি।'},
      {q: 'কেস: "সুসংগঠিত পরিবেশ, উদ্দেশ্যের আন্তরিকতা, নব উদ্ভাবন, শৃঙ্খলা" — সম্পর্কিত:', opts: ['কারিগরি শিক্ষা', 'শিক্ষাব্যবস্থাকে সক্রিয়করণ', 'শিক্ষক প্রশিক্ষণ', 'কোনোটিই নয়'], ans: 1, exp: 'শিক্ষানীতির ৭ম অংশ "শিক্ষাব্যবস্থাকে সক্রিয়করণ"।'},
      {q: 'কেস: "প্রতি ৫ বছর অন্তর মূল্যায়ন, গুণাগুণ বিচার" — সম্পর্কিত:', opts: ['শিক্ষা ব্যবস্থাপনা', 'সম্পদ ও পুনঃপরীক্ষা', 'পর্যালোচনা', 'ভবিষ্যৎ'], ans: 2, exp: 'একাদশ অংশে "পর্যালোচনা" বা Review।'},
      {q: 'কেস: "বিদ্যালয়ের মান বজায় রাখতে রাজ্যব্যাপী সংস্থা" — সম্পর্কিত:', opts: ['মান নির্ধারণ', 'মান নির্ধারণ ও স্বীকৃতি', 'ন্যায়সংগত শিক্ষা', 'সামাজিক চেতনা'], ans: 1, exp: 'SSSA-এর মাধ্যমে মান নির্ধারণ ও স্বীকৃতি।'},
      {q: 'কেস: "প্রযুক্তি ব্যবহারের ওপর মুক্ত ধারণার বিনিময়ের প্ল্যাটফর্ম" — সম্পর্কিত:', opts: ['শিক্ষার্থী ফোরাম', 'অভিভাবক ফোরাম', 'শিক্ষক প্রযুক্তি ফোরাম', 'শিক্ষক-শিক্ষার্থী ফোরাম'], ans: 2, exp: 'NETF বা জাতীয় শিক্ষক প্রযুক্তি ফোরাম।'},
      {q: 'স্তম্ভ মেলাও: (i) HECI-এর অধীনে → (a) NHERC, (ii) NEP-2020 → (b) বাণিজ্যিকীকরণ রোধ, (iii) NEP-1986 → (c) রাজনীতি মুক্ত, (iv) NRF → (d) গবেষণা ত্বরান্বিত', opts: ['i-a, ii-b, iii-c, iv-d', 'i-d, ii-c, iii-b, iv-a', 'i-b, ii-c, iii-d, iv-a', 'i-c, ii-d, iii-a, iv-b'], ans: 0, exp: 'HECI-এর অধীনে NHERC, NEP-2020 বাণিজ্যিকীকরণ রোধ, NEP-1986 রাজনীতি মুক্ত, NRF গবেষণা ত্বরান্বিত।'},
      {q: '"হালকা কিন্তু আঁটোসাঁটো" — কোন্ নীতির অংশ?', opts: ['NEP 1986', 'NEP 2020', 'কোঠারি', 'মুদালিয়র'], ans: 1, exp: 'NEP-2020-এর উচ্চশিক্ষার দৃষ্টিভঙ্গি।'},
      {q: 'বিবৃতি: (A) ১৯৮৬-তে ১০+২+৩, (B) ২০২০-তে ৫+৩+৩+৪।', opts: ['A সত্য, B মিথ্যা', 'A মিথ্যা, B সত্য', 'A ও B সত্য', 'A ও B মিথ্যা'], ans: 2, exp: 'উভয় কাঠামোই সঠিক।'},
      {q: 'বিবৃতি: (A) অপারেশন ব্ল্যাকবোর্ড প্রাথমিকের জন্য, (B) নবোদয় মাধ্যমিকের জন্য।', opts: ['A সত্য, B মিথ্যা', 'A মিথ্যা, B সত্য', 'A ও B সত্য', 'A ও B মিথ্যা'], ans: 2, exp: 'উভয় বিবৃতিই সত্য।'},
      {q: 'কেস: "গ্রামীণ প্রাথমিক বিদ্যালয়ে শিক্ষক ও শিক্ষোপকরণের অভাব দূরীকরণ" — সম্পর্কিত:', opts: ['নবোদয়', 'অপারেশন ব্ল্যাকবোর্ড', 'ECCE', 'DIET'], ans: 1, exp: 'অপারেশন ব্ল্যাকবোর্ডের প্রধান উদ্দেশ্য।'},
      {q: 'কেস: "মেধাবীদের গ্রামীণ এলাকায় আবাসিক শিক্ষা" — সম্পর্কিত:', opts: ['নবোদয়', 'অপারেশন ব্ল্যাকবোর্ড', 'ECCE', 'IGNOU'], ans: 0, exp: 'নবোদয় বিদ্যালয়ের মূল উদ্দেশ্য।'},
      {q: 'বিবৃতি-কারণ: (A) শিক্ষার বাণিজ্যিকীকরণ রোধ, (R) শিক্ষা পাবলিক গুড।', opts: ['A ও R সঠিক ও ব্যাখ্যা', 'A ও R সঠিক কিন্তু ব্যাখ্যা নয়', 'A সঠিক, R ভুল', 'A ভুল, R সঠিক'], ans: 0, exp: 'শিক্ষা পাবলিক গুড, তাই বাণিজ্যিকীকরণ রোধ প্রয়োজন।'},
      {q: 'কোন্ শিক্ষানীতিতে প্রথম "অপারেশন ব্ল্যাকবোর্ড" ও "নবোদয়" বলা হয়?', opts: ['১৯৬৮', '১৯৮৬', '২০২০', '১৯৯২'], ans: 1, exp: '১৯৮৬ সালের শিক্ষানীতিতে প্রথম এই দুটি কর্মসূচির কথা বলা হয়।'}
    ]
   }
};

// ============================================================
//  হাব পেজ তৈরি
// ============================================================
function buildHub() {
  var grid = document.getElementById('setGrid');
  grid.innerHTML = '';
  for (var i = 1; i <= 9; i++) {
    var set = allSets[i];
    var card = document.createElement('div');
    card.className = 'set-card';
    card.innerHTML = '<div class="icon">' + set.icon + '</div><div class="set-num">' + set.name + '</div><div class="set-title">' + set.topic + '</div><div class="set-meta"><span>১৫ প্রশ্ন</span><span>১০ মিনিট</span></div>';
    card.onclick = (function(id) { return function() { selectSet(id); }; })(i);
    grid.appendChild(card);
  }
}

function showHub() {
  document.getElementById('hubPage').classList.remove('hidden');
  document.getElementById('testArea').classList.add('hidden');
  document.getElementById('resultWrap').classList.remove('show');
  document.getElementById('timerBox').classList.remove('danger');
  clearInterval(timerInterval);
  if (currentUser) {
    document.getElementById('hubUserInfo').innerHTML = '👤 ' + currentUser.username + ' — সেট সিলেক্ট করো।';
  }
}

function goToHub() {
  document.getElementById('testArea').classList.add('hidden');
  document.getElementById('resultWrap').classList.remove('show');
  document.getElementById('hubPage').classList.remove('hidden');
  document.getElementById('timerBox').classList.remove('danger');
  clearInterval(timerInterval);
}

// ============================================================
//  সেট সিলেক্ট
// ============================================================
function selectSet(id) {
  currentSetId = id;
  var set = allSets[id];
  if (isLoggedIn && currentUser) {
    var attempts = currentUser.attempts[id] || 0;
    if (attempts >= MAX_ATTEMPTS) {
      alert('⚠️ আপনি ' + set.name + ' এর সর্বোচ্চ ' + MAX_ATTEMPTS + ' বার Test দিয়েছেন।');
      return;
    }
    startQuiz(id);
    return;
  }
  pendingSetId = id;
  document.getElementById('loginSetName').textContent = '📚 ' + set.name + ' — ' + set.topic;
  document.getElementById('loginOverlay').classList.add('active');
  document.getElementById('loginUsername').value = '';
  document.getElementById('loginPassword').value = '';
  document.getElementById('loginError').style.display = 'none';
  document.getElementById('limitInfo').style.display = 'none';
  document.getElementById('loginBtn').disabled = false;
  document.getElementById('loginUsername').focus();
}

// ============================================================
//  লগইন
// ============================================================
function doLoginFromSet() {
  var username = document.getElementById('loginUsername').value.trim();
  var password = document.getElementById('loginPassword').value.trim();
  var errorEl = document.getElementById('loginError');
  var limitInfo = document.getElementById('limitInfo');

  if (!username || !password) {
    errorEl.textContent = '❌ দয়া করে ইউজারনেম ও পাসওয়ার্ড দিন।';
    errorEl.style.display = 'block';
    return;
  }

  var user = null;
  for (var i = 0; i < userData.length; i++) {
    if (userData[i].username === username && userData[i].password === password) {
      user = userData[i];
      break;
    }
  }

  if (user) {
    var attempts = user.attempts[currentSetId] || 0;
    if (attempts >= MAX_ATTEMPTS) {
      limitInfo.style.display = 'block';
      document.getElementById('limitMsg').textContent = 'আপনি ' + allSets[currentSetId].name + ' এর সর্বোচ্চ ' + MAX_ATTEMPTS + ' বার দিয়েছেন।';
      errorEl.style.display = 'none';
      return;
    }
    isLoggedIn = true;
    currentUser = user;
    errorEl.style.display = 'none';
    limitInfo.style.display = 'none';
    document.getElementById('loginOverlay').classList.remove('active');
    document.getElementById('hubUserInfo').innerHTML = '👤 ' + currentUser.username + ' — সেট সিলেক্ট করো।';
    startQuiz(currentSetId);
  } else {
    errorEl.textContent = '❌ ভুল ইউজারনেম বা পাসওয়ার্ড।';
    errorEl.style.display = 'block';
    limitInfo.style.display = 'none';
  }
}

// Enter key support
document.addEventListener('DOMContentLoaded', function() {
  document.getElementById('loginPassword').addEventListener('keydown', function(e) {
    if (e.key === 'Enter') doLoginFromSet();
  });
  document.getElementById('loginUsername').addEventListener('keydown', function(e) {
    if (e.key === 'Enter') doLoginFromSet();
  });
  buildHub();
  document.getElementById('hubPage').classList.remove('hidden');
  document.getElementById('testArea').classList.add('hidden');
  document.getElementById('resultWrap').classList.remove('show');
});

// ============================================================
//  কুইজ ফাংশন
// ============================================================
function startQuiz(setId) {
  if (!isLoggedIn || !currentUser) return;
  var attempts = currentUser.attempts[setId] || 0;
  if (attempts >= MAX_ATTEMPTS) {
    alert('⚠️ আপনি এই সেটের সর্বোচ্চ ' + MAX_ATTEMPTS + ' বার দিয়েছেন।');
    return;
  }
  currentUser.attempts[setId] = (currentUser.attempts[setId] || 0) + 1;
  cur = 0; score = 0; wrong = 0; answered = false;
  timeLeft = 10 * 60; userAnswers = [];
  document.getElementById('hubPage').classList.add('hidden');
  document.getElementById('resultWrap').classList.remove('show');
  document.getElementById('testArea').classList.remove('hidden');
  document.getElementById('timerBox').classList.remove('danger');
  var set = allSets[setId];
  document.getElementById('testSetLabel').textContent = set.name;
  document.getElementById('testTopic').textContent = set.topic;
  clearInterval(timerInterval);
  timerInterval = setInterval(tick, 1000);
  loadQ();
}

function tick() {
  timeLeft--;
  var m = Math.floor(timeLeft / 60);
  var s = timeLeft % 60;
  document.getElementById('timerDisplay').textContent = m + ':' + (s < 10 ? '0' : '') + s;
  if (timeLeft <= 60) document.getElementById('timerBox').classList.add('danger');
  if (timeLeft <= 0) { clearInterval(timerInterval); showResult(); }
}

function loadQ() {
  answered = false;
  var set = allSets[currentSetId];
  var q = set.questions[cur];
  document.getElementById('qNum').textContent = 'প্রশ্ন ' + (cur + 1) + ' / ' + set.questions.length;
  document.getElementById('qText').textContent = q.q;
  document.getElementById('progressFill').style.width = ((cur + 1) / set.questions.length * 100) + '%';
  document.getElementById('nextBtn').disabled = true;
  document.getElementById('nextBtn').textContent = cur === set.questions.length - 1 ? 'ফলাফল দেখো' : 'পরবর্তী →';
  document.getElementById('explanation').classList.remove('show');
  var opts = document.getElementById('qOpts');
  opts.innerHTML = '';
  for (var i = 0; i < q.opts.length; i++) {
    var btn = document.createElement('button');
    btn.className = 'opt';
    btn.innerHTML = '<div class="opt-circle">' + LABELS[i] + '</div><div class="opt-text">' + q.opts[i] + '</div>';
    btn.onclick = (function(idx) { return function() { answer(idx); }; })(i);
    opts.appendChild(btn);
  }
}

function answer(i) {
  if (answered) return;
  answered = true;
  var set = allSets[currentSetId];
  var q = set.questions[cur];
  userAnswers[cur] = i;
  var btns = document.querySelectorAll('.opt');
  for (var j = 0; j < btns.length; j++) { btns[j].classList.add('disabled'); }
  btns[q.ans].classList.add('correct');
  if (i !== q.ans) { btns[i].classList.add('wrong'); wrong++; }
  else score++;
  document.getElementById('scoreShow').textContent = 'সঠিক: ' + score + ' | ভুল: ' + wrong;
  document.getElementById('explanationText').innerHTML = '<strong>ব্যাখ্যা:</strong> ' + q.exp;
  document.getElementById('explanation').classList.add('show');
  document.getElementById('nextBtn').disabled = false;
}

function nextQ() {
  var set = allSets[currentSetId];
  cur++;
  if (cur >= set.questions.length) { clearInterval(timerInterval); showResult(); return; }
  loadQ();
}

function showResult() {
  document.getElementById('testArea').classList.add('hidden');
  var rw = document.getElementById('resultWrap');
  rw.classList.add('show');
  var set = allSets[currentSetId];
  var pct = Math.round(score / set.questions.length * 100);
  document.getElementById('finalScore').textContent = score;
  document.getElementById('rbCorrect').textContent = score;
  document.getElementById('rbWrong').textContent = wrong;
  document.getElementById('rbPct').textContent = pct + '%';
  var remaining = MAX_ATTEMPTS - (currentUser.attempts[currentSetId] || 0);
  document.getElementById('attemptInfo').innerHTML = '👤 ' + currentUser.username + ' — ' + set.name + ': বাকি <strong>' + remaining + '</strong> বার (সর্বোচ্চ ' + MAX_ATTEMPTS + ')';
  var grades = [[90,'🌟','অসাধারণ!'],[70,'👍','খুব ভালো!'],[50,'📚','ভালো চেষ্টা!'],[0,'💪','চেষ্টা চালিয়ে যাও!']];
  var g = grades[0];
  for (var i = 0; i < grades.length; i++) {
    if (pct >= grades[i][0]) { g = grades[i]; break; }
  }
  document.getElementById('resultIcon').textContent = g[1];
  document.getElementById('resultGrade').textContent = g[2] + ' (' + set.topic + ')';
}

function showReview() {
  document.getElementById('resultWrap').classList.remove('show');
  document.getElementById('testArea').classList.remove('hidden');
  cur = 0;
  loadReview();
}

function loadReview() {
  var set = allSets[currentSetId];
  if (cur >= set.questions.length) {
    document.getElementById('testArea').classList.add('hidden');
    document.getElementById('resultWrap').classList.add('show');
    return;
  }
  var q = set.questions[cur];
  document.getElementById('qNum').textContent = 'Review — প্রশ্ন ' + (cur + 1) + ' / ' + set.questions.length;
  document.getElementById('qText').textContent = q.q;
  document.getElementById('progressFill').style.width = ((cur + 1) / set.questions.length * 100) + '%';
  document.getElementById('nextBtn').disabled = false;
  document.getElementById('nextBtn').textContent = cur === set.questions.length - 1 ? 'শেষ করো' : 'পরবর্তী →';
  document.getElementById('nextBtn').onclick = function() { cur++; loadReview(); };
  var opts = document.getElementById('qOpts');
  opts.innerHTML = '';
  for (var i = 0; i < q.opts.length; i++) {
    var btn = document.createElement('button');
    btn.className = 'opt disabled';
    if (i === q.ans) btn.classList.add('correct');
    else if (userAnswers[cur] === i) btn.classList.add('wrong');
    btn.innerHTML = '<div class="opt-circle">' + LABELS[i] + '</div><div class="opt-text">' + q.opts[i] + '</div>';
    opts.appendChild(btn);
  }
  document.getElementById('explanationText').innerHTML = '<strong>ব্যাখ্যা:</strong> ' + q.exp;
  document.getElementById('explanation').classList.add('show');
  document.getElementById('scoreShow').textContent = 'সবুজ = সঠিক উত্তর';
}
</script>

</body>
</html>
