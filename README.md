<!DOCTYPE html>
<html lang="bn">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Test Bazar — Class 12 | Ch 2 | All Sets 1-12</title>
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
.set-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(220px,1fr));gap:1.2rem}
.set-card{background:white;border-radius:14px;padding:1.5rem;border:1.5px solid #c5dccb;transition:all 0.2s;cursor:pointer;color:#1c2e24;box-shadow:0 2px 8px rgba(26,122,74,0.06)}
.set-card:hover{transform:translateY(-3px);border-color:#1a7a4a;box-shadow:0 6px 20px rgba(26,122,74,0.12)}
.set-card .icon{font-size:2.2rem;margin-bottom:0.3rem}
.set-card .set-num{font-weight:700;font-size:1.1rem;color:#1a7a4a}
.set-card .set-title{font-family:'Tiro Bangla',serif;font-size:0.85rem;color:#5a7a66;margin:0.2rem 0 0.5rem}
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
.login-overlay{position:fixed;top:0;left:0;width:100%;height:100%;background:rgba(0,0,0,0.5);display:flex;align-items:center;justify-content:center;z-index:999;display:none}
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

  <!-- ===== LOGIN OVERLAY ===== -->
  <div class="login-overlay" id="loginOverlay">
    <div class="login-modal">
      <h2>🔐 লগইন করুন</h2>
      <p>Test শুরু করতে আপনার ইউজারনেম ও পাসওয়ার্ড দিন</p>
      <div class="set-name-display" id="loginSetName">📚 Set 1</div>
      <div class="limit-info" id="limitInfo">⚠️ <span id="limitMsg"></span></div>
      <label>ইউজারনেম</label>
      <input type="text" id="loginUsername" placeholder="আপনার ইউজারনেম লিখুন">
      <label>পাসওয়ার্ড</label>
      <input type="password" id="loginPassword" placeholder="আপনার পাসওয়ার্ড লিখুন" onkeydown="if(event.key==='Enter') doLoginFromSet()">
      <button class="login-btn" id="loginBtn" onclick="doLoginFromSet()">✅ লগইন করে Test শুরু করো</button>
      <div class="error-msg" id="loginError">❌ ভুল ইউজারনেম বা পাসওয়ার্ড। আবার চেষ্টা করুন।</div>
    </div>
  </div>

  <!-- ===== HUB PAGE ===== -->
  <div id="hubPage">
    <div class="hub-header">
      <h1>📚 Chapter 2 — জাতীয় শিক্ষানীতি—১৯৮৬ ও ২০২০</h1>
      <p>নিচের সেটগুলো থেকে বেছে নিন। Test শুরু করতে সেটে ক্লিক করুন এবং লগইন করুন।</p>
      <div id="hubUserInfo" style="font-family:'Tiro Bangla',serif;font-size:0.85rem;color:#5a7a66;margin-top:0.5rem;"></div>
    </div>
    <div class="set-grid" id="setGrid"></div>
  </div>

  <!-- ===== TEST AREA ===== -->
  <div id="testArea" class="hidden">
    <div class="quiz-info">
      <div class="info-item">🎓 <strong id="testSetName">শিক্ষাবিজ্ঞান</strong> — Class 12 | Ch 2 | <span id="testSetLabel">Set 1</span></div>
      <div class="info-item">📝 <span id="testTopic">বিশ্ববিদ্যালয় শিক্ষা কমিশন</span></div>
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

  <!-- ===== RESULT AREA ===== -->
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
//  ইউজার ডেটাবেস
// ============================================================
const MAX_ATTEMPTS = 10;
const TOTAL_SETS = 12;

const userData = [
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
//  সব সেটের ডেটা (Set 1-12 for Chapter 2)
// ============================================================
const allSets = {
  1: {
    name: 'Set 1',
    icon: '🏛️',
    topic: 'বিশ্ববিদ্যালয় শিক্ষা কমিশন - গঠন ও গ্রামীণ শিক্ষা',
    questions: [
      {q: 'বিশ্ববিদ্যালয় কমিশন গঠিত হয়—', opts: ['1948 খ্রিস্টাব্দের 5 নভেম্বর', '1948 খ্রিস্টাব্দের 7 নভেম্বর', '1949 খ্রিস্টাব্দের 5 নভেম্বর', '1949 খ্রিস্টাব্দের 6 নভেম্বর'], ans: 0, exp: 'স্বাধীনতা লাভের পর দেশের শিক্ষাব্যবস্থার পুনর্গঠন ও উচ্চশিক্ষার পর্যালোচনার জন্য ভারত সরকারের এক বিশেষ আদেশে 1948 সালের 5 নভেম্বর এই কমিশন গঠিত হয়েছিল।'},
      {q: 'বিশ্ববিদ্যালয় কমিশনের সদস্য সংখ্যা—', opts: ['9 জন', '8 জন', '10 জন', '11 জন'], ans: 2, exp: 'এই কমিশনে 7 জন বিশিষ্ট ভারতীয় শিক্ষাবিদ এবং 3 জন বিদেশি চিন্তাবিদ নিয়ে সর্বমোট 10 জন সদস্য ছিলেন।'},
      {q: 'বিশ্ববিদ্যালয় কমিশনের সভাপতি ছিলেন—', opts: ['ড. এ. লক্ষ্মণস্বামী মুদালিয়র', 'ড. সর্বপল্লী রাধাকৃষ্ণণ', 'ড. জাকির হোসেন', 'ড. জেমস এফ. ডাফ'], ans: 1, exp: 'প্রখ্যাত শিক্ষাবিদ ও পরবর্তীকালে ভারতের রাষ্ট্রপতি ড. সর্বপল্লী রাধাকৃষ্ণণ ছিলেন এই কমিশনের সভাপতি।'},
      {q: 'বিশ্ববিদ্যালয় কমিশনের সুপারিশের সংখ্যা—', opts: ['208টি', '207টি', '747টি', '746টি'], ans: 1, exp: '1949 সালের আগস্ট মাসে কমিশন সরকারের কাছে তাদের প্রতিবেদন পেশ করে, যেখানে মোট 207টি সুপারিশ উল্লেখ ছিল।'},
      {q: 'বিশ্ববিদ্যালয় কমিশনের অপর নাম হল—', opts: ['রাধাকৃষ্ণণ কমিশন', 'মুদালিয়র কমিশন', 'কোঠারি কমিশন', 'স্যাডলার কমিশন'], ans: 0, exp: 'ড. সর্বপল্লী রাধাকৃষ্ণণের সভাপতিত্বে গঠিত হয়েছিল বলে এটি রাধাকৃষ্ণণ কমিশন (1948-49) নামে সমধিক পরিচিত।'},
      {q: 'গ্রামীণ শিক্ষার উন্নয়নের গুরুত্বপূর্ণ প্রতিষ্ঠান হল—', opts: ['প্রাথমিক শিক্ষার প্রতিষ্ঠান', 'মাধ্যমিক শিক্ষার প্রতিষ্ঠান', 'গ্রামীণ বিশ্ববিদ্যালয়', 'কোনোটিই নয়'], ans: 2, exp: 'গ্রামনির্ভর ভারতের উন্নতির জন্য এবং গ্রামীণ মেধাবী শিক্ষার্থীদের নিজেদের পরিবেশেই উচ্চশিক্ষার সুযোগ দিতে এই গ্রামীণ বিশ্ববিদ্যালয় (Rural University) স্থাপনের ধারণাটি আনা হয়।'},
      {q: 'বুনিয়াদি শিক্ষার সময়কাল—', opts: ['9 বছর', '6 বছর', '8 বছর', '4 বছর'], ans: 2, exp: 'গ্রামীণ শিক্ষার পরিকল্পনায় প্রথম স্তর বা প্রাথমিক স্তরে বুনিয়াদি শিক্ষার কথা বলা হয়েছে, যার সময়কাল ধরা হয়েছে 6 থেকে 14 বছর বয়স পর্যন্ত (মোট 8 বছর)।'},
      {q: 'রাধাকৃষ্ণণ কমিশনে বিদেশি সদস্য সংখ্যা ছিল—', opts: ['5 জন', '3 জন', '2 জন', '4 জন'], ans: 1, exp: 'এই কমিশনে ইংল্যান্ড ও আমেরিকার মোট 3 জন বিদেশি শিক্ষাবিদ (জেমস এফ. ডাফ, আর্থার ই. মরগ্যান, জন টিগার্ট) ছিলেন।'},
      {q: 'বিশ্ববিদ্যালয় কমিশনের সম্পাদক হলেন—', opts: ['ড. মেঘনাদ সাহা', 'ড. নির্মল কুমার সিদ্ধান্ত', 'ড. জন টিগার্ট', 'ড. জাকির হোসেন'], ans: 1, exp: 'এই ঐতিহাসিক কমিশনের সম্পাদকের গুরুদায়িত্ব অত্যন্ত দক্ষতার সঙ্গে পালন করেছিলেন ড. নির্মল কুমার সিদ্ধান্ত।'},
      {q: 'প্রত্যেকটি মাধ্যমিক শিক্ষাপ্রতিষ্ঠানের এলাকা হবে—', opts: ['20-60 একর', '30-60 একর', '30-50 একর', '30-65 একর'], ans: 1, exp: 'গ্রামীণ শিক্ষা পরিকল্পনায় কমিশন জানায়, প্রতিটি মাধ্যমিক বিদ্যালয় অন্তত 30 থেকে 60 একর জায়গা নিয়ে প্রতিষ্ঠিত হবে যেখানে খামার, বাগান ও কর্মশালা থাকবে।'},
      {q: 'মাধ্যমিক বিদ্যালয়ে তাত্ত্বিক ও ব্যবহারিক বিষয় শেখার জন্য সময়ের শতকরা হার—', opts: ['60 : 40', '50 : 50', '52 : 48', '55 : 45'], ans: 1, exp: 'গ্রামীণ বিদ্যালয়ের পাঠ্যক্রমে তাত্ত্বিক জ্ঞানের পাশাপাশি হাতেকলমে কাজের ওপর সমান গুরুত্ব দিয়ে 50% সময় তাত্ত্বিক এবং 50% সময় ব্যবহারিক কাজের জন্য রাখা হয়।'},
      {q: 'প্রত্যেকটি গ্রামীণ কলেজে শিক্ষার্থীর সংখ্যা হবে—', opts: ['400 জন', '1500 জন', '300 জন', '800 জন'], ans: 2, exp: 'গ্রামীণ কলেজে শিক্ষাদানের গুণগত মান বজায় রাখতে শিক্ষার্থীর সংখ্যা কোনোভাবেই 300 জনের বেশি হবে না বলে কমিশন স্থির করেছিল।'},
      {q: 'প্রত্যেকটি বিশ্ববিদ্যালয়ে শিক্ষার্থীর সংখ্যা হবে—', opts: ['1500 জন', '2500 জন', '2000 জন', '1550 জন'], ans: 1, exp: 'গ্রামীণ বিশ্ববিদ্যালয়ের ক্ষেত্রে প্রতিটি বিশ্ববিদ্যালয়ে সর্বাধিক শিক্ষার্থীর সংখ্যা 2500 জন নির্দিষ্ট করা হয়েছিল।'},
      {q: 'ভারত সরকার কয়টি গ্রামীণ সংস্থা প্রতিষ্ঠা করেন?', opts: ['15টি', '14টি', '9টি', '16টি'], ans: 1, exp: 'বিশেষজ্ঞ কমিটির পরামর্শ মেনে ভারত সরকার প্রথমেই গ্রামীণ বিশ্ববিদ্যালয় না গড়ে পরীক্ষামূলকভাবে 14টি গ্রামীণ সংস্থা বা Rural Institutes প্রতিষ্ঠা করেছিল।'},
      {q: 'গ্রামীণ উচ্চশিক্ষা জাতীয় পর্ষদ (National Council for Rural Higher Education) গঠিত হয়—', opts: ['1956 খ্রিস্টাব্দে', '1957 খ্রিস্টাব্দে', '1958 খ্রিস্টাব্দে', '1955 খ্রিস্টাব্দে'], ans: 0, exp: 'গ্রামীণ শিক্ষা ও সংস্থাগুলির মান উন্নয়ন ও নিয়ন্ত্রণের জন্য 1956 সালে এই জাতীয় পর্ষদ বা NCRHE গঠিত হয়েছিল।'}
    ]
  },
  2: {
    name: 'Set 2',
    icon: '📚',
    topic: 'বিশ্ববিদ্যালয় শিক্ষা কমিশন - ধারণা ও সুপারিশ',
    questions: [
      {q: 'প্রত্যেকটি মাধ্যমিক বিদ্যালয়ের অবস্থান হবে—', opts: ['গ্রামের শেষ প্রান্তে', 'গ্রামের শুরুতে', 'গ্রামের কেন্দ্রস্থলে', 'গ্রামের বাইরে'], ans: 2, exp: 'গ্রামীণ মাধ্যমিক বিদ্যালয়গুলি গ্রামের কেন্দ্রস্থলে অবস্থান করবে যাতে আশেপাশের সকল শিক্ষার্থী সহজেই শিক্ষালাভের জন্য আসতে পারে।'},
      {q: 'গ্রামীণ কলেজ ও বিশ্ববিদ্যালয়গুলি পরিচালনার জন্য থাকবে—', opts: ['পরিচালন সমিতি', 'ম্যানেজিং কমিটি', 'গ্রাম কমিটি', 'পরিচালনা সমিতি'], ans: 0, exp: 'এই প্রতিষ্ঠানগুলিকে স্বাধীনভাবে কাজ করার সুযোগ দিতে এবং সুপরিচালনার জন্য প্রতিটি প্রতিষ্ঠানে পরিচালন সমিতি রাখার কথা বলা হয়।'},
      {q: 'বিশ্ববিদ্যালয় কমিশনের তিনজন বিদেশি সদস্যের নাম—', opts: ['ড. জেমস এফ. ডাফ, ড. আর্থার ই. মরগ্যান, ড. জন টিগার্ট', 'ড. আর্থার ই. মরগ্যান, ড. জেমস এফ. ডাফ, ড. টিগার্ট', 'ড. জন আর্থার ই. মরগ্যান, ড. জন টিগার্ট, ড. জাকির হোসেন', 'ড. জন টিগার্ট, ড. জাকির হোসেন, ড. এ. লক্ষ্মণস্বামী মুদালিয়র'], ans: 0, exp: 'ইংল্যান্ডের ড. জেমস এফ. ডাফ এবং আমেরিকার ড. আর্থার ই. মরগ্যান ও ড. জন টিগার্ট—এই তিনজন বিদেশি চিন্তাবিদ কমিশনের অত্যন্ত গুরুত্বপূর্ণ সদস্য ছিলেন।'},
      {q: 'গ্রামীণ বিশ্ববিদ্যালয়ের উদ্দেশ্য ছিল—', opts: ['গ্রামীণ কৃষি, শিল্প, পশুপালন ইত্যাদির বিজ্ঞানসম্মত উন্নয়ন', 'গ্রামীণ কৃষি ও রাস্তাঘাট প্রভৃতির বিজ্ঞানসম্মত উন্নয়ন', 'গ্রামীণ শিল্প, পশুপালন ও মৎস্যচাষের বিজ্ঞানসম্মত উন্নয়ন', 'গ্রামীণ পানীয় জল ও স্বাস্থ্যের উন্নয়ন'], ans: 0, exp: 'গ্রামগুলিকে বিজ্ঞানসম্মতভাবে পুনর্গঠন করে গ্রামীণ অর্থনীতি, শিল্প ও পশুপালনের সার্বিক উন্নয়নই ছিল গ্রামীণ বিশ্ববিদ্যালয়ের প্রধান লক্ষ্য।'},
      {q: 'শিক্ষার মাধ্যম সম্পর্কে ত্রিভাষা সূত্রটি হল—', opts: ['আঞ্চলিক ভাষা বা মাতৃভাষা, রাষ্ট্রীয় ভাষা (হিন্দি), ইংরেজি ভাষা', 'মাতৃভাষা, বিদেশি যে-কোনো ভাষা, রাষ্ট্রীয় ভাষা', 'রাষ্ট্রীয় ভাষা, ইংরেজি ভাষা, উর্দু ভাষা', 'আঞ্চলিক ভাষা, উর্দু ভাষা, হিন্দি ভাষা'], ans: 0, exp: 'বিশ্ববিদ্যালয় শিক্ষা কমিশন মাধ্যমিক থেকে বিশ্ববিদ্যালয় স্তর পর্যন্ত ভাষার মাধ্যম হিসেবে এই তিনটি ভাষার সুপারিশ প্রথম করেছিল।'},
      {q: 'স্নাতক স্তরে কোন্ ধরনের ধর্মীয় শিক্ষা দেওয়া হয়?', opts: ['মহাপুরুষদের জীবনী পাঠ', 'ধর্মীয় গ্রন্থের সংকলন পাঠ', 'ধর্মীয় দর্শনের মূল সমস্যা নিয়ে আলোচনা', 'সব ক-টি'], ans: 3, exp: 'স্নাতক স্তরে ধর্মীয় শিক্ষার জন্য প্রথম বর্ষে মহাপুরুষদের জীবনী, দ্বিতীয় বর্ষে ধর্মগ্রন্থের সংকলন এবং তৃতীয় বর্ষে ধর্মীয় দর্শনের মূল সমস্যাগুলি নিয়ে আলোচনার কথা বলা হয়েছিল।'},
      {q: 'UGC-এর সম্পূর্ণ নাম—', opts: ['University Grants Commission', 'University Grants Committee', 'Universal Grants Commission', 'University Grade Commission'], ans: 0, exp: 'উচ্চশিক্ষার ব্যয়ভার নির্বাহের দায়িত্ব রাষ্ট্রকে গ্রহণ করতে বলা হয় এবং অবিলম্বে বিশ্ববিদ্যালয় মঞ্জুরি কমিশন বা UGC গঠনের সুপারিশ করা হয়।'},
      {q: 'স্বাধীনতা লাভের পর প্রথম শিক্ষা কমিশন হল—', opts: ['মুদালিয়র কমিশন', 'কোঠারি কমিশন', 'রাধাকৃষ্ণণ কমিশন', 'অশোক মিত্র কমিশন'], ans: 2, exp: '১৯৪৭ সালে দেশ স্বাধীন হওয়ার পর, দেশের উচ্চশিক্ষার সংস্কার ও পুনর্গঠনের জন্য ১৯৪৮ সালে রাধাকৃষ্ণণ কমিশন গঠিত হয়, যা প্রথম শিক্ষা কমিশন।'},
      {q: 'রাধাকৃষ্ণণ কমিশন (1948-49)-এ ভারতীয় সদস্য সংখ্যা হল—', opts: ['আটজন', 'দশজন', 'তিনজন', 'সাতজন'], ans: 3, exp: 'মোট ১০ জন সদস্যের মধ্যে ড. রাধাকৃষ্ণণ, ড. মেঘনাদ সাহা, ড. জাকির হোসেন-সহ ৭ জন ছিলেন ভারতীয় শিক্ষাবিদ।'},
      {q: 'বিশ্ববিদ্যালয় শিক্ষা কমিশন (1948-49)-এ বিদেশি সদস্য সংখ্যা হল—', opts: ['তিনজন', 'পাঁচজন', 'সাতজন', 'আটজন'], ans: 0, exp: 'তিনজন বিদেশি শিক্ষাবিদ এই কমিশনের সদস্য পদ অলংকৃত করেছিলেন।'},
      {q: 'বিশ্ববিদ্যালয় শিক্ষা কমিশন (1948-49)-এর সুপারিশটি ছিল—', opts: ['207 পৃষ্ঠার', '747 পৃষ্ঠার', '509 পৃষ্ঠার', '477 পৃষ্ঠার'], ans: 1, exp: '১৯৪৯ সালের আগস্ট মাসে জমা দেওয়া কমিশনের রিপোর্ট বা প্রতিবেদনটি ছিল সুদীর্ঘ ৭৪৭ পৃষ্ঠার এবং এতে ২০৭টি সুপারিশ ছিল।'},
      {q: 'বিশ্ববিদ্যালয় শিক্ষা কমিশনে উত্তর বুনিয়াদি শিক্ষার জন্য সময়কালের সুপারিশ করা হয়—', opts: ['পাঁচ বছর', 'ছয় বছর', 'তিন বছর', 'তিন-চার বছর'], ans: 3, exp: 'গ্রামীণ শিক্ষার কাঠামো অনুযায়ী প্রাথমিক শিক্ষার পর ১৫ থেকে ১৭ বছর বয়সিদের জন্য উত্তর বুনিয়াদি বা মাধ্যমিক স্তরের শিক্ষাকাল ছিল ৩-৪ বছর।'},
      {q: 'NCRHE-এর সম্পূর্ণ নাম কী?', opts: ['National Central for Rural Higher Education', 'National Council for Rural Heard Education', 'National Council for Rural Higher Education', 'National Council for Realized Higher Education'], ans: 2, exp: '১৯৫৬ সালে গ্রামীণ উচ্চশিক্ষার প্রসারের জন্য এই গ্রামীণ উচ্চশিক্ষা জাতীয় পর্ষদ (NCRHE) গঠন করা হয়েছিল।'},
      {q: 'রাধাকৃষ্ণণ কমিশন, শিক্ষাপ্রতিষ্ঠানগুলিতে দিনের কাজ শুরু করার আগে শিক্ষার্থীদের কয়েক মিনিট কীসের সুপারিশ করা হয়?', opts: ['নীরব প্রার্থনার', 'জাতীয় সংগীত গাওয়ার', 'খবর পড়ার', 'গান গাওয়ার'], ans: 0, exp: 'ধর্ম ও আধ্যাত্মিকতার প্রতি শ্রদ্ধাশীল হতে শিক্ষাপ্রতিষ্ঠানের কাজ শুরুর আগে কয়েক মিনিট নীরব প্রার্থনার সুপারিশ করা হয়েছিল।'},
      {q: 'জাতীয় উন্নয়নের মূল ভিত্তি হল—', opts: ['শিক্ষা', 'আস্থা', 'শিল্প', 'বাণিজ্য'], ans: 0, exp: 'স্বাধীন ভারতের সমাজ ও জাতীয় জীবনের সমস্ত ক্ষেত্রে অগ্রগতি ও অর্থনৈতিক উন্নতি সাধন একমাত্র শিক্ষার মাধ্যমেই সম্ভব।'}
    ]
  },
  3: {
    name: 'Set 3',
    icon: '📜',
    topic: 'রাধাকৃষ্ণণ কমিশনের বিভিন্ন ধারা ও সুপারিশ',
    questions: [
      {q: 'DPI-এর সম্পূর্ণ নাম হল—', opts: ['District of Public Instruction', 'Director of Public Institution', 'Director of Public Instruction', 'Director of Public Instruction'], ans: 2, exp: 'শিক্ষা প্রশাসনের সর্বোচ্চ স্তরে Director of Public Instruction-এর গুরুত্বপূর্ণ ভূমিকা রয়েছে।'},
      {q: 'বহুমুখী বিদ্যালয়ের উদ্দেশ্য হল—', opts: ['শিক্ষার্থীর চাহিদা ও সামর্থ্য অনুযায়ী শিক্ষা', 'শিক্ষার্থীকে গুরুত্ব না দিয়ে শিক্ষা', 'শিক্ষক নির্ভর শিক্ষার ব্যবস্থা', 'কারিগরি শিক্ষা প্রদান'], ans: 0, exp: 'একই ছাদের তলায় শিক্ষার্থীদের নানা রুচি ও সামর্থ্য অনুসারে শিক্ষার সুযোগ দেওয়াই এর লক্ষ্য।'},
      {q: 'রাধাকৃষ্ণণ কমিশনের একজন বিদেশি সদস্য হলেন—', opts: ['ড. জাকির হোসেন', 'জন ডিউই', 'ড. জন টিগার্ট', 'ড. এ. লক্ষ্মণস্বামী মুদালিয়র'], ans: 2, exp: 'আমেরিকার শিক্ষাবিদ ড. জন টিগার্ট ছিলেন এই কমিশনের বিদেশি সদস্য।'},
      {q: 'রাধাকৃষ্ণণ কমিশনের একজন ভারতীয় সদস্য হলেন—', opts: ['ড. জেমস এফ. ডাফ', 'রবীন্দ্রনাথ ঠাকুর', 'ড. এস. কোঠারি', 'ড. কমল নারায়ণ বহল'], ans: 3, exp: 'ড. কমল নারায়ণ বহল ছিলেন রাধাকৃষ্ণণ কমিশনের উল্লেখযোগ্য ভারতীয় সদস্য।'},
      {q: 'বিশ্ববিদ্যালয় কমিশন সুপারিশটি সরকারের কাছে পেশ করেন—', opts: ['1949 খ্রিস্টাব্দের নভেম্বর মাসে', '1948 খ্রিস্টাব্দের আগস্ট মাসে', '1949 খ্রিস্টাব্দের জুন মাসে', '1949 খ্রিস্টাব্দের আগস্ট মাসে'], ans: 3, exp: '১৯৪৮ সালের নভেম্বরে কাজ শুরু করে ১৯৪৯ সালের আগস্টে তারা সুপারিশটি জমা দেন।'},
      {q: 'UGC গঠনের একটি উদ্দেশ্য হল—', opts: ['কলেজগুলিকে আর্থিক সাহায্য দান', 'কলেজ ও বিশ্ববিদ্যালয়গুলিকে আর্থিক সাহায্য দান', 'কলেজ পরিচালন কমিটি গঠন', 'সরকারি বিশ্ববিদ্যালয়গুলিকে আর্থিক সাহায্য দান'], ans: 1, exp: 'উচ্চশিক্ষার ব্যয়ভার বহন করে সমস্ত কলেজ ও বিশ্ববিদ্যালয়গুলিকে আর্থিক অনুদান প্রদান করা।'},
      {q: 'গ্রামীণ কলেজ ও বিশ্ববিদ্যালয়গুলি পরিচালনার জন্য থাকবে—', opts: ['পরিচালন ব্যবস্থা', 'পরিচালন সমিতি', 'পরিচালনার কেন্দ্রীয় সংস্থা', 'রাজ্য সংস্থা'], ans: 1, exp: 'প্রতিষ্ঠানগুলিকে স্বাধীনভাবে কাজ করার সুযোগ দিতে পরিচালন সমিতির কথা বলা হয়।'},
      {q: 'গ্রামীণ বিজ্ঞানের সার্টিফিকেট কোর্সের সময়কাল হল—', opts: ['তিন বছর', 'চার বছর', 'দুই বছর', 'এক বছর'], ans: 2, exp: 'গ্রামীণ বিজ্ঞানের সার্টিফিকেট কোর্সের মেয়াদ দু-বছর রাখা হয়েছিল।'},
      {q: 'NCRHE-এর সুপারিশ অনুযায়ী গ্রামসেবা বিজ্ঞানের ডিপ্লোমা কোর্সের সময়কাল হল—', opts: ['চার বছর', 'তিন বছর', 'দুই বছর', 'এক বছর'], ans: 1, exp: 'গ্রামসেবা পেশা হিসেবে গ্রহণের জন্য ডিপ্লোমা কোর্সটি তিন বছরের জন্য নির্দিষ্ট করা হয়।'},
      {q: 'NCRHE-এর সুপারিশে কৃষিবিজ্ঞানে সার্টিফিকেট কোর্সের সময়কাল হল—', opts: ['দুই বছর', 'তিন বছর', 'চার বছর', 'এক বছর'], ans: 0, exp: 'কৃষির উন্নতির জন্য সার্টিফিকেট কোর্সের সময়কাল দু-বছর ধার্য করা হয়েছিল।'},
      {q: 'গ্রামীণ বিশ্ববিদ্যালয়ের স্নাতকোত্তর স্তরে শিক্ষার সময়কাল হল—', opts: ['দুই বছর', 'তিন বছর', 'পাঁচ বছর', 'এক বছর'], ans: 0, exp: 'গ্রামীণ শিক্ষাকাঠামোতে স্নাতকোত্তর শিক্ষার মেয়াদ ২ বছরের জন্য সুপারিশ করা হয়েছিল।'},
      {q: 'বিশ্ববিদ্যালয় মঞ্জুরি কমিটি প্রতিষ্ঠিত হয়—', opts: ['1953 খ্রিস্টাব্দে', '1945 খ্রিস্টাব্দে', '1947 খ্রিস্টাব্দে', '1948 খ্রিস্টাব্দে'], ans: 1, exp: 'স্বাধীনতা লাভের ঠিক আগে ১৯৪৫ সালে প্রথম একটি কমিটি গঠিত হয়।'},
      {q: 'বিশ্ববিদ্যালয় মঞ্জুরি কমিশন (UGC) প্রতিষ্ঠিত হয়—', opts: ['1945 খ্রিস্টাব্দে', '1948 খ্রিস্টাব্দে', '1953 খ্রিস্টাব্দে', '1956 খ্রিস্টাব্দে'], ans: 2, exp: 'রাধাকৃষ্ণণ কমিশনের সুপারিশের পর ১৯৫৩ সালে এটি প্রতিষ্ঠিত হয়।'},
      {q: 'কোন কমিশনের সুপারিশে বিশ্ববিদ্যালয় মঞ্জুরি কমিশন প্রতিষ্ঠিত হয়?', opts: ['মুদালিয়র কমিশন', 'কোঠারি কমিশন', 'রাধাকৃষ্ণণ কমিশন', 'হান্টার কমিশন'], ans: 2, exp: 'রাধাকৃষ্ণণ কমিশনই প্রথম অনুদান সংস্থা বা UGC গঠনের প্রস্তাব দিয়েছিল।'},
      {q: 'গ্রামীণ উচ্চশিক্ষার বিষয়ে ভারত সরকারকে পরামর্শদানের উদ্দেশ্যে 1956 খ্রিস্টাব্দে প্রতিষ্ঠিত হয়—', opts: ['জাতীয় গ্রামীণ উচ্চশিক্ষা পর্ষদ', 'জাতীয় নগর উচ্চশিক্ষা পর্ষদ', 'রাজ্য গ্রামীণ উচ্চশিক্ষা পর্ষদ', 'গ্রামীণ উচ্চশিক্ষা পর্ষদ'], ans: 0, exp: '১৯৫৬ সালে National Council for Rural Higher Education বা NCRHE গঠিত হয়।'}
    ]
  },
  4: {
    name: 'Set 4',
    icon: '📖',
    topic: 'বিশ্ববিদ্যালয় কমিশনের পাঠ্যক্রম, শিক্ষক ও পরীক্ষাব্যবস্থা',
    questions: [
      {q: 'প্রথম কোন কমিশনে ত্রিভাষা সূত্রের কথা বলা হয়েছিল?', opts: ['কোঠারি কমিশনে', 'মুদালিয়র কমিশনে', 'রাধাকৃষ্ণণ কমিশনে', 'হান্টার কমিশনে'], ans: 2, exp: 'প্রথম রাধাকৃষ্ণণ কমিশনই ত্রিভাষা সূত্রের প্রস্তাব দেয়।'},
      {q: 'বিশ্ববিদ্যালয় শিক্ষা কমিশনের সম্পাদক ছিলেন—', opts: ['ড. এস. রাধাকৃষ্ণণ', 'ড. জাকির হোসেন', 'ড. তারাচাঁদ', 'ড. এন. কে. সিদ্ধান্ত'], ans: 3, exp: 'ড. নির্মল কুমার সিদ্ধান্ত (এন. কে. সিদ্ধান্ত) ছিলেন কমিশনের সম্পাদক।'},
      {q: 'বিশ্ববিদ্যালয় শিক্ষা কমিশনে কলেজের অনার্স কোর্সের জন্য শিক্ষার সময়কালের সুপারিশ করা হয়—', opts: ['দুই বছর', 'তিন বছর', 'পাঁচ বছর', 'আট বছর'], ans: 1, exp: 'অনার্স কোর্সের মেয়াদ তিন বছর করার প্রস্তাব দেওয়া হয়েছিল।'},
      {q: 'বিশ্ববিদ্যালয় শিক্ষার পাঠ্যক্রমে কোনটি পেশাগত শিক্ষার বিষয় নয়?', opts: ['বাণিজ্য', 'আইন', 'মানবিক বিষয়', 'চিকিৎসাবিজ্ঞান'], ans: 2, exp: 'মানবিক বিষয় (সাহিত্য, দর্শন, সমাজবিজ্ঞান) সাধারণ শিক্ষার অন্তর্গত।'},
      {q: 'বিশ্ববিদ্যালয় শিক্ষার পাঠ্যক্রমের পেশাগত শিক্ষার বিষয় কোনটি?', opts: ['কৃষি', 'বাণিজ্য', 'আইন', 'সব ক-টি'], ans: 3, exp: 'কমিশনের পেশাগত শিক্ষার তালিকায় এই তিনটি বিষয়সহ ছয়টি বিষয় ছিল।'},
      {q: 'বিশ্ববিদ্যালয় কমিশনে কৃষি শিক্ষাকে অগ্রাধিকার দেওয়ার কথা বলা হয়েছে কেন?', opts: ['সামাজিক অবস্থার উন্নয়নের জন্য', 'জাতীয় অর্থনৈতিক অবস্থার উন্নয়নের জন্য', 'খাদ্যে স্বনির্ভর হওয়ার জন্য', 'দারিদ্র্য দূরীকরণের জন্য'], ans: 1, exp: 'ভারত কৃষিপ্রধান দেশ, তাই কৃষির মাধ্যমে জাতীয় অর্থনীতির উন্নয়নই লক্ষ্য ছিল।'},
      {q: 'বিশ্ববিদ্যালয় কমিশন কয় ধরনের পেশাগত শিক্ষার সুপারিশ করেছেন?', opts: ['চার ধরনের', 'পাঁচ ধরনের', 'তিন ধরনের', 'ছয় ধরনের'], ans: 3, exp: 'ছয় ধরনের পেশাগত শিক্ষা — কৃষি, বাণিজ্য, শিক্ষাবিজ্ঞান, ইঞ্জিনিয়ারিং, আইন ও চিকিৎসাবিজ্ঞান।'},
      {q: 'বিশ্ববিদ্যালয় কমিশনে শিক্ষকদের কয়টি শ্রেণি থাকার কথা বলেছেন?', opts: ['তিনটি', 'চারটি', 'পাঁচটি', 'দুইটি'], ans: 1, exp: 'অধ্যাপক, রিডার, লেকচারার ও ইনস্ট্রাক্টর — এই চারটি শ্রেণিতে ভাগ করার কথা বলা হয়।'},
      {q: 'বিশ্ববিদ্যালয় কমিশনে শিক্ষকদের অবসর গ্রহণের সাধারণ বয়স কত করার সুপারিশ করা হয়েছে?', opts: ['55 বছর', '60 বছর', '65 বছর', '60 বছর'], ans: 1, exp: 'শিক্ষকদের অবসরের সাধারণ বয়স ৬০ বছর ধার্য করা হয়েছিল।'},
      {q: 'বিশ্ববিদ্যালয় কমিশনের সুপারিশ অনুযায়ী সমগ্র পরীক্ষার মূল্যায়নের কত অংশে অভ্যন্তরীণ পরীক্ষার কথা বলা হয়েছে?', opts: ['দুই-তৃতীয়াংশ', 'এক-তৃতীয়াংশ', 'তিন-চতুর্থাংশ', 'অর্ধাংশ'], ans: 1, exp: 'মোট নম্বরের এক-তৃতীয়াংশ অভ্যন্তরীণ মূল্যায়নের জন্য বরাদ্দ করার কথা বলা হয়।'},
      {q: 'শিক্ষার্থীরা পরীক্ষায় কত শতাংশ নম্বর পেলে প্রথম বিভাগ বলা হবে?', opts: ['60 শতাংশে', '65 শতাংশে', '55 শতাংশে', '70 শতাংশে'], ans: 3, exp: 'প্রথম বিভাগ পাওয়ার জন্য ন্যূনতম ৭০ শতাংশ নম্বর নির্ধারণ করা হয়েছিল।'},
      {q: 'বিশ্ববিদ্যালয় কমিশনে পরীক্ষাব্যবস্থার সংস্কারের ক্ষেত্রে গ্রেড নম্বর দানের সুপারিশটি কী ছিল?', opts: ['গ্রেড প্রথা বর্জন', 'গ্রেড প্রথা গ্রহণ', 'প্রথম বিভাগের ক্ষেত্রে গ্রেড প্রদান', 'কোনোটিই নয়'], ans: 0, exp: 'রাধাকৃষ্ণণ কমিশন গ্রেড প্রথার পরিবর্তে নম্বরের ভিত্তিতে বিভাগ প্রদানের কথা বলেছিল।'},
      {q: 'শিক্ষার্থীরা কত নম্বর পেলে দ্বিতীয় বিভাগে উত্তীর্ণ বলে ঘোষণা করা হবে?', opts: ['40-54 নম্বর', '45-59 নম্বর', '55-69 নম্বর', '35-45 নম্বর'], ans: 2, exp: 'দ্বিতীয় বিভাগের পরিধি ৫৫% থেকে ৬৯% এর মধ্যে নির্দিষ্ট করা হয়েছিল।'},
      {q: 'পরীক্ষক হওয়ার জন্য কত বছরের অভিজ্ঞতা প্রয়োজন?', opts: ['অন্তত চার বছর', 'অন্তত পাঁচ বছর', 'অন্তত তিন বছর', 'অন্তত ছয় বছর'], ans: 1, exp: 'উত্তরপত্র মূল্যায়নে অন্তত পাঁচ বছরের অভিজ্ঞতা সম্পন্ন শিক্ষকদের পরীক্ষক করার কথা বলা হয়েছিল।'},
      {q: 'বিশ্ববিদ্যালয় কমিশন বলেছেন, ধর্মই ভারতের কীসের প্রতীক?', opts: ['আধ্যাত্মিকতার', 'অন্তরাত্মার', 'সামাজিকতার', 'নৈতিকতার'], ans: 1, exp: 'ধর্মকে ভারতীয় সমাজের অন্তরাত্মার প্রতীক বলা হয়েছে।'}
    ]
  },
  5: {
    name: 'Set 5',
    icon: '🎓',
    topic: 'বিশ্ববিদ্যালয় শিক্ষার মান ও মুদালিয়র কমিশনের শুরু',
    questions: [
      {q: 'সাধারণধর্মী শিক্ষার ওপর চাপ কমাতে অধিক সংখ্যায় কোন ধরনের প্রতিষ্ঠান গড়ে তোলার কথা বলা হয়েছে?', opts: ['বৃত্তিমূলক শিক্ষার', 'কারিগরি শিক্ষার', 'সামাজিক শিক্ষার', 'নারীশিক্ষার'], ans: 0, exp: 'বিশ্ববিদ্যালয়ে পঠনপাঠনের মান বজায় রাখতে প্রচুর বৃত্তিশিক্ষা প্রতিষ্ঠান গড়ার ওপর জোর দেওয়া হয়।'},
      {q: 'পরীক্ষাব্যবস্থার কোন বিষয়টি দূর করার জন্য বিশ্ববিদ্যালয় ডিগ্রিকে সরকারি নিয়োগে গুরুত্ব না দিয়ে নিয়োগের জন্য পৃথক পরীক্ষা গ্রহণের সুপারিশ করা হয়েছে?', opts: ['সামগ্রিক উন্নয়ন', 'কুফল দূরীকরণ', 'পরীক্ষার মান উন্নয়ন', 'কোনোটিই নয়'], ans: 1, exp: 'শুধু ডিগ্রির পেছনে ছোটো এবং মুখস্থ বিদ্যার কুফল দূর করতেই ডিগ্রির সঙ্গে চাকরির সম্পর্ক বিচ্ছিন্ন করার কথা বলা হয়।'},
      {q: 'বিশ্ববিদ্যালয় কমিশনে পিএইচডি ডিগ্রির শিক্ষার সময়কাল কত বলা হয়েছে?', opts: ['তিন বছর', 'এক বছর', 'দুই বছর', 'চার বছর'], ans: 2, exp: 'স্নাতকোত্তর ডিগ্রি অর্জনের পর পিএইচডি ডিগ্রির শিক্ষাকাল ন্যূনতম দুই বছর রাখা হয়েছিল।'},
      {q: 'কলেজগুলিতে কার্যদিবস কত দিনের কম হবে না?', opts: ['150 দিন', '140 দিন', '180 দিন', '200 দিন'], ans: 2, exp: 'শিক্ষাদানের মান ঠিক রাখতে বছরে অন্তত ১৮০ দিন কলেজ খোলা রাখার নির্দেশ দেওয়া হয়।'},
      {q: 'কলেজ ও বিশ্ববিদ্যালয়গুলিতে সকল বিভাগ মিলিয়ে শিক্ষার্থীর সংখ্যা কত বেশি হবে না?', opts: ['2000 ও 3000', '2500 ও 3500', '1500 ও 3000', '2000 ও 4000'], ans: 2, exp: 'কলেজে ১৫০০ এবং বিশ্ববিদ্যালয়ে ৩০০০ শিক্ষার্থীর ঊর্ধ্বসীমা বাঁধা হয়।'},
      {q: 'বিশ্ববিদ্যালয়ে শিক্ষার জন্য বিদ্যালয় স্তরে কত বছরের শিক্ষাগ্রহণ করতে হবে?', opts: ['10 বছর', '14 বছর', '40 বছর', '12 বছর'], ans: 3, exp: 'ইন্টারমিডিয়েট কলেজে বা বিদ্যালয় স্তরে অন্তত ১২ বছর পড়ার পরই বিশ্ববিদ্যালয়ে প্রবেশের যোগ্যতা অর্জন হবে।'},
      {q: 'প্রতিটি কলেজে কোন্ ধরনের ক্লাসের ব্যবস্থা করতে হবে?', opts: ['বৃত্তিমুখী শিক্ষার ক্লাস', 'টিউটোরিয়াল ক্লাস', 'পেশাগত শিক্ষার ক্লাস', 'কারিগরি শিক্ষার ক্লাস'], ans: 1, exp: 'শিক্ষার্থীদের ব্যক্তিগত অসুবিধা দূর করতে প্রতিটি কলেজে টিউটোরিয়াল ক্লাসের ব্যবস্থা রাখার কথা বলা হয়।'},
      {q: 'পশ্চিমবঙ্গের গ্রামীণ সংস্থাটির নাম কী?', opts: ['অমরাবতী', 'ওয়ার্ধা', 'গান্ধিগ্রাম', 'শ্রীনিকেতন'], ans: 3, exp: 'বীরভূমের শ্রীনিকেতন গ্রামীণ শিক্ষার জন্য পরীক্ষামূলকভাবে প্রতিষ্ঠিত ১৪টি গ্রামীণ সংস্থার অন্যতম।'},
      {q: 'মাধ্যমিক শিক্ষা কমিশনের সভাপতি ছিলেন—', opts: ['ড. অনাথনাথ বসু', 'ড. এ. লক্ষ্মণস্বামী মুদালিয়র', 'শ্রীমতী হংসরাজ মেহতা', 'শ্রী এম. টি. ব্যাস'], ans: 1, exp: 'তৎকালীন মাদ্রাজ বিশ্ববিদ্যালয়ের উপাচার্য ড. লক্ষ্মণস্বামী মুদালিয়র ছিলেন সভাপতি।'},
      {q: 'মাধ্যমিক শিক্ষা কমিশন গঠিত হয়—', opts: ['23 সেপ্টেম্বর 1952', '23 সেপ্টেম্বর 1962', '23 সেপ্টেম্বর 1952', '29 আগস্ট 1953'], ans: 0, exp: '১৯৫২ সালের ২৩ সেপ্টেম্বর ভারত সরকার মাধ্যমিক শিক্ষা কমিশন গঠন করে।'},
      {q: 'মাধ্যমিক শিক্ষা কমিশনের সম্পাদক ছিলেন—', opts: ['ড. অনাথনাথ বসু', 'ড. এ. লক্ষ্মণস্বামী মুদালিয়র', 'বিদ্যাসাগর', 'বিবেকানন্দ'], ans: 0, exp: 'বিশিষ্ট বাঙালি শিক্ষাবিদ ড. অনাথনাথ বসু মুদালিয়র কমিশনের সম্পাদক ছিলেন।'},
      {q: 'মুদালিয়র কমিশনের সদস্য সংখ্যা ছিল—', opts: ['10 জন', '7 জন', '8 জন', '9 জন'], ans: 3, exp: 'সভাপতি এবং সম্পাদক সহ মোট ৯ জন সদস্য ছিলেন।'},
      {q: 'মাধ্যমিক শিক্ষা কমিশনের বিদেশি সদস্য সংখ্যা ছিল—', opts: ['2 জন', '3 জন', '4 জন', '5 জন'], ans: 0, exp: 'ইংল্যান্ডের জন ক্রিস্টি এবং আমেরিকার কে. আর. উইলিয়াম — এই দুজন বিদেশি সদস্য ছিলেন।'},
      {q: 'মাধ্যমিক শিক্ষা কমিশনের সুপারিশের পৃষ্ঠাসংখ্যা হল—', opts: ['212টি', '331টি', '413টি', '506টি'], ans: 1, exp: '১৯৫৩ সালের আগস্ট মাসে কমিশন ৩৩১ পৃষ্ঠার এই প্রতিবেদন পেশ করে।'},
      {q: 'দশম শ্রেণিযুক্ত বিদ্যালয় থেকে উত্তীর্ণ শিক্ষার্থীদের জন্য কত বছর প্রাক্-বিশ্ববিদ্যালয় শিক্ষার ব্যবস্থা থাকবে?', opts: ['2 বছরের', '1 বছরের', '3 বছরের', '2.5 বছরের'], ans: 1, exp: 'সরাসরি দশম শ্রেণির পর বিশ্ববিদ্যালয়ে যেতে চাইলে ১ বছরের Pre-University Course চালু করা হয়।'}
    ]
  },
  6: {
    name: 'Set 6',
    icon: '📋',
    topic: 'মুদালিয়র কমিশন - সুপারিশসমূহ ও পাঠ্যক্রম',
    questions: [
      {q: 'উচ্চমাধ্যমিক শিক্ষার সময়কাল হল—', opts: ['4 বছর', '1 বছর', '3 বছর', '2 বছর'], ans: 2, exp: 'মুদালিয়র কমিশন ইন্টারমিডিয়েট কোর্স তুলে দিয়ে ৩ বছরের উচ্চমাধ্যমিক স্তরের প্রস্তাব দেয়।'},
      {q: 'বিদ্যালয় শিক্ষার কাঠামোটি হল—', opts: ['5 + 3 + 3 = 11 বছর', '4 + 4 + 3 = 11 বছর', '6 + 2 + 3 = 11 বছর', '4 + 5 + 2 = 11 বছর'], ans: 0, exp: 'প্রাথমিক (৪/৫ বছর), নিম্ন মাধ্যমিক (৪/৩ বছর) এবং উচ্চমাধ্যমিক (৩ বছর) মিলিয়ে ১১ বছর।'},
      {q: 'মাধ্যমিক শিক্ষা কমিশনের (১৯৫২-৫৩) অপর নামটি হল—', opts: ['কোঠারি কমিশন', 'মুদালিয়র কমিশন', 'রাধাকৃষ্ণণ কমিশন', 'হান্টার কমিশন'], ans: 1, exp: 'ড. লক্ষ্মণস্বামী মুদালিয়রের নামানুসারে এটি মুদালিয়র কমিশন নামে পরিচিত।'},
      {q: 'মুদালিয়র কমিশনের সুপারিশ প্রকাশিত হয়—', opts: ['1953 খ্রিস্টাব্দের 28 আগস্ট', '1953 খ্রিস্টাব্দের 29 আগস্ট', '1953 খ্রিস্টাব্দের 23 সেপ্টেম্বর', '1952 খ্রিস্টাব্দের 23 সেপ্টেম্বর'], ans: 1, exp: '১৯৫৩ সালের ২৯ আগস্ট কমিশন তার বিস্তারিত রিপোর্ট প্রকাশ করে।'},
      {q: 'মুদালিয়র কমিশনের মাধ্যমিক বিদ্যালয়ের সুপারিশ হল—', opts: ['একক প্রতিষ্ঠান বিদ্যালয়', 'কমন বিদ্যালয়', 'বহু উদ্দেশ্যসাধক বিদ্যালয়', 'বৃত্তি শিক্ষার বিদ্যালয়'], ans: 2, exp: 'শিক্ষার্থীদের রুচি অনুযায়ী নানা বিষয়ের শিক্ষার সুযোগ দিতে মাল্টিপারপাস স্কুল গড়ার প্রস্তাব দেওয়া হয়।'},
      {q: 'ড. এ. লক্ষ্মণস্বামী মুদালিয়র কে ছিলেন?', opts: ['মাদ্রাজ বিশ্ববিদ্যালয়ের তদানীন্তন উপাচার্য', 'কলকাতা বিশ্ববিদ্যালয়ের তদানীন্তন উপাচার্য', 'দিল্লি বিশ্ববিদ্যালয়ের তদানীন্তন উপাচার্য', 'বিশ্বভারতী বিশ্ববিদ্যালয়ের তদানীন্তন উপাচার্য'], ans: 0, exp: 'তিনি ছিলেন পেশায় চিকিৎসক এবং মাদ্রাজ বিশ্ববিদ্যালয়ের উপাচার্য।'},
      {q: 'CABE-এর সম্পূর্ণ নাম হল—', opts: ['Central Advisory Board of Education', 'Central Advisory Board of Educand', 'Central Advisory Board of Educate', 'Centre Advisory Board of Education'], ans: 0, exp: 'কেন্দ্রীয় শিক্ষা উপদেষ্টা পর্ষদের প্রস্তাবে মুদালিয়র কমিশন গঠিত হয়।'},
      {q: 'মুদালিয়র কমিশনের সুপারিশের মোট অধ্যায়ের সংখ্যা ছিল—', opts: ['9টি', '5টি', '10টি', '16টি'], ans: 3, exp: '৩৩১ পৃষ্ঠার প্রতিবেদনটি ১৬টি অধ্যায়ে বিন্যস্ত ছিল।'},
      {q: '"আমাদের মাধ্যমিক শিক্ষা লক্ষ্যহীনতার শিক্ষা" / "weakest link"—এই মন্তব্যটি করেছেন—', opts: ['রাধাকৃষ্ণণ কমিশন', 'মুদালিয়র কমিশন', 'কোঠারি কমিশন', 'হান্টার কমিশন'], ans: 1, exp: 'মুদালিয়র কমিশন মাধ্যমিক শিক্ষাব্যবস্থাকে দুর্বলতম অংশ হিসেবে চিহ্নিত করেছিল।'},
      {q: 'মুদালিয়র কমিশনের একজন ভারতীয় সদস্য হলেন—', opts: ['জন ক্রিস্টি', 'কে. আর. উইলিয়াম', 'ফ্রয়েবেল', 'শ্রীমতী হংসরাজ মেহতা'], ans: 3, exp: 'শ্রীমতী হংসরাজ মেহতা ছিলেন কমিশনের ৭ জন ভারতীয় সদস্যের একজন।'},
      {q: 'মুদালিয়র কমিশনে একজন বিদেশি সদস্য হলেন—', opts: ['ড. অনাথনাথ বসু', 'শ্রী এন. টি ব্যাস', 'জন ক্রিস্টি', 'শ্রী কে. জি. সাইয়াদ্দিন'], ans: 2, exp: 'ইংল্যান্ডের জন ক্রিস্টি ছিলেন বিদেশি সদস্য।'},
      {q: 'মুদালিয়র কমিশনের মতে, মাধ্যমিক বিদ্যালয়ে সাপ্তাহিক কাজের সময় হবে—', opts: ['25 পিরিয়ড', '40 পিরিয়ড', '42 পিরিয়ড', '45 পিরিয়ড'], ans: 3, exp: 'সপ্তাহে অন্তত ৪৫ পিরিয়ড ক্লাসের কথা বলা হয়েছিল।'},
      {q: 'SABE-এর সম্পূর্ণ নাম হল—', opts: ['State Advisory Board of Educand', 'State Advisory Board of Education', 'State Advanced Board of Education', 'State Educated of Education'], ans: 1, exp: 'প্রতিটি রাজ্যে SABE বা রাজ্য শিক্ষা উপদেষ্টা পর্ষদ গঠনের সুপারিশ করা হয়।'},
      {q: 'ঐচ্ছিক পাঠ্যক্রমের বাণিজ্য বিভাগের একটি বিষয় হল—', opts: ['ইতিহাস', 'বুককিপিং', 'উদ্যান রচনা', 'রসায়নবিদ্যা'], ans: 1, exp: 'বাণিজ্য প্রবাহে বুককিপিং বা হিসাবরক্ষণ অন্তর্ভুক্ত ছিল।'},
      {q: 'ঐচ্ছিক পাঠ্যক্রমের চারুকলা বিভাগের একটি বিষয় হল—', opts: ['সংগীত', 'গার্হস্থ্য অর্থনীতি', 'ভূগোল', 'জীবনবিজ্ঞান'], ans: 0, exp: 'চারুকলার প্রবাহে সংগীত একটি আবশ্যিক বিষয় ছিল।'}
    ]
  },
  7: {
    name: 'Set 7',
    icon: '⭐',
    topic: 'মুদালিয়র কমিশনের সুপারিশ ও মূল্যায়ন',
    questions: [
      {q: 'ঐচ্ছিক পাঠ্যক্রমের মানবিক বিজ্ঞান বিভাগের একটি বিষয় হল—', opts: ['পদার্থবিদ্যা', 'রসায়নবিদ্যা', 'গণিত', 'বুককিপিং'], ans: 2, exp: 'মানবিক বিজ্ঞান প্রবাহে ইতিহাস, ভূগোল, অর্থনীতি, পৌরবিজ্ঞান ও গণিত অন্তর্ভুক্ত ছিল।'},
      {q: '1948 খ্রিস্টাব্দে মাধ্যমিক শিক্ষার পুনর্গঠনের জন্য একটি কমিটি গঠনের সুপারিশ করে—', opts: ['CABE', 'UGC', 'SABE', 'NCERT'], ans: 0, exp: 'CABE বা কেন্দ্রীয় শিক্ষা উপদেষ্টা পর্ষদ সর্বভারতীয় কমিশন গঠনের প্রস্তাব করেন।'},
      {q: 'মাধ্যমিক শিক্ষা কমিশন শিক্ষার্থীদের কাজের মূল্যায়নের জন্য কত Point Scale-এর সুপারিশ করেছিলেন?', opts: ['Four Point Scale', 'Three Point Scale', 'Five Point Scale', 'Seven Point Scale'], ans: 2, exp: 'A, B, C, D, E — এই ৫টি সাংকেতিক চিহ্ন বা Five Point Scale ব্যবহারের কথা বলা হয়।'},
      {q: 'AICTE-এর সম্পূর্ণ নাম হল—', opts: ['All India Council of Teacher Education', 'All India Council for Technical Education', 'All Indian Council for Technical Education', 'All India Central for Technical Education'], ans: 1, exp: 'AICTE হলো ভারতের কারিগরি শিক্ষার সর্বোচ্চ সংস্থা।'},
      {q: 'CRC-এর সম্পূর্ণ নাম হল—', opts: ['Cumulative Record Card', 'Central Record Card', 'Cumulative Reading Card', 'Cumulative Record Curve'], ans: 0, exp: 'শিক্ষার্থীর সর্বাত্মক পরিচয় পত্র বা Cumulative Record Card প্রবর্তনের কথা বলা হয়।'},
      {q: 'মুদালিয়র কমিশন অপর যে নামে পরিচিত তা হল—', opts: ['ভারতীয় শিক্ষা কমিশন', 'মাধ্যমিক শিক্ষা কমিশন', 'বিশ্ববিদ্যালয় শিক্ষা কমিশন', 'প্রথম ভারতীয় শিক্ষা কমিশন'], ans: 1, exp: 'স্বাধীন ভারতের মাধ্যমিক শিক্ষাব্যবস্থা পুনর্গঠনের জন্য এটি মাধ্যমিক শিক্ষা কমিশন নামে পরিচিত।'},
      {q: 'মুদালিয়র কমিশনে ভারতীয় সদস্যসংখ্যা ছিল—', opts: ['5 জন', '2 জন', '7 জন', '9 জন'], ans: 2, exp: 'সভাপতি ও সম্পাদক-সহ ৭ জন ভারতীয় এবং ২ জন বিদেশি শিক্ষাবিদ ছিলেন।'},
      {q: 'মাধ্যমিক শিক্ষা কমিশনে শিক্ষার্থীদের মূল্যায়নের ক্ষেত্রে নম্বর দানের পরিবর্তে কীসের সুপারিশ করা হয়?', opts: ['গ্রেড দান', 'বিভাগ দান', 'পুরস্কার প্রদান', 'কোনোটিই নয়'], ans: 0, exp: 'A, B, C, D, E গ্রেড ব্যবহারের সুপারিশ করা হয়েছিল।'},
      {q: 'কমিশনের মতে মাধ্যমিক বিদ্যালয়ে সাপ্তাহিক কাজের সময়সীমা হবে—', opts: ['35 পিরিয়ড', '40 পিরিয়ড', '45 পিরিয়ড', '50 পিরিয়ড'], ans: 2, exp: 'সপ্তাহে অন্তত ৪৫ পিরিয়ড ক্লাসের কথা বলা হয়েছিল।'},
      {q: 'কমিশনের মতে, মাধ্যমিক বিদ্যালয়ে কাজের সময়সীমা হবে অন্তত পক্ষে—', opts: ['120 দিন', '110 দিন', '235 দিন', '200 দিন'], ans: 3, exp: 'বছরে অন্ততপক্ষে ২০০ দিন কাজের সময়সীমা নির্ধারণ করতে হবে।'},
      {q: 'কমিশনের মতে, শিক্ষার্থীদের বিদ্যালয় জীবনের সমগ্র ঘটনাবলি লিপিবদ্ধ থাকবে—', opts: ['ARC-তে', 'CRC-তে', 'চূড়ান্ত ফলাফলে', 'শংসাপত্রে'], ans: 1, exp: 'CRC বা Cumulative Record Card-এ সকল তথ্য সংরক্ষণ করা হবে।'},
      {q: 'কমিশন কতজন সদস্য নিয়ে মাধ্যমিক শিক্ষা পর্ষদ গঠনের কথা বলেছিলেন?', opts: ['20 জন', '25 জন', '30 জন', '18 জন'], ans: 1, exp: 'প্রতিটি রাজ্যে ২৫ জন সদস্যের একটি মাধ্যমিক শিক্ষা পর্ষদ থাকবে।'},
      {q: 'নীচের কোনটি মাধ্যমিক শিক্ষার লক্ষ্য?', opts: ['ধর্মনিরপেক্ষ মনোভাব গঠন', 'নিরক্ষরতা দূরীকরণ', 'কুসংস্কারমুক্ত সমাজ গঠন', 'সব ক-টি'], ans: 3, exp: 'ধর্মনিরপেক্ষতা, নিরক্ষরতা দূরীকরণ ও কুসংস্কারমুক্ত সমাজ গঠন — সবগুলোই মাধ্যমিক শিক্ষার লক্ষ্য।'},
      {q: 'মাধ্যমিক স্তরের ক্ষেত্রে একটি সাধারণ কী ধরনের পরীক্ষার ব্যবস্থা থাকবে?', opts: ['অভ্যন্তরীণ পরীক্ষা', 'মৌখিক পরীক্ষা', 'কম্পার্টমেন্টাল পরীক্ষা', 'বহিঃপরীক্ষা'], ans: 3, exp: 'মাধ্যমিক স্তরের শিক্ষা সমাপ্তির পর একটি সাধারণ বহিঃপরীক্ষা থাকবে।'},
      {q: 'সরকারি পরীক্ষায় কোন নতুন পরীক্ষার প্রবর্তনের কথা বলা হয়েছে?', opts: ['বহিঃপরীক্ষা', 'অভ্যন্তরীণ পরীক্ষা', 'কম্পার্টমেন্টাল পরীক্ষা', 'ব্যবহারিক পরীক্ষা'], ans: 2, exp: 'অনুত্তীর্ণ শিক্ষার্থীদের পুনরায় সুযোগ দেওয়ার জন্য কম্পার্টমেন্টাল পরীক্ষার প্রবর্তন করা হয়।'}
    ]
  },
  8: {
    name: 'Set 8',
    icon: '🏫',
    topic: 'মুদালিয়র কমিশনের অন্যান্য দিক ও কোঠারি কমিশনের সূচনা',
    questions: [
      {q: 'শিক্ষকদের ছেলেমেয়েরা বিদ্যালয়ে কোন্ সুযোগসুবিধা গ্রহণ করতে পারবে?', opts: ['ভরতির সুযোগ', 'হোস্টেলে থাকার সুযোগ', 'বিনা বেতনে শিক্ষাগ্রহণ', 'কোনোটিই নয়'], ans: 2, exp: 'শিক্ষকদের ছেলেমেয়েরা বিদ্যালয়ে বিনা বেতনে শিক্ষাগ্রহণের সুযোগ পাবে।'},
      {q: 'মাধ্যমিক উত্তীর্ণ শিক্ষকদের প্রশিক্ষণকাল কত হবে?', opts: ['এক বছর', 'দুই বছর', 'তিন বছর', 'চার বছর'], ans: 1, exp: 'মাধ্যমিক উত্তীর্ণ শিক্ষকদের প্রশিক্ষণের সময়কাল ২ বছর।'},
      {q: 'স্নাতক উত্তীর্ণ শিক্ষকদের প্রশিক্ষণকাল কত হবে?', opts: ['এক বছর', 'দুই বছর', 'তিন বছর', 'চার বছর'], ans: 0, exp: 'স্নাতক উত্তীর্ণ শিক্ষকদের প্রশিক্ষণের সময়কাল ১ বছর।'},
      {q: 'কোন্ কমিশনে শিল্পশিক্ষা কর প্রবর্তনের কথা বলা হয়েছে?', opts: ['রাধাকৃষ্ণণ কমিশনে', 'মুদালিয়র কমিশনে', 'কোঠারি কমিশনে', 'অশোক মিত্র কমিশনে'], ans: 1, exp: 'মুদালিয়র কমিশন শিল্পশিক্ষা কর প্রবর্তনের সুপারিশ করেছিলেন।'},
      {q: 'NCC-এর সম্পূর্ণ নাম কী?', opts: ['National Cadet Corps', 'Need Cadet Corps', 'Nation Cadet Corps', 'National Cadet Committee'], ans: 0, exp: 'শিক্ষার্থীদের চরিত্র গঠনে প্রতিটি বিদ্যালয়ে NCC চালু করার ওপর জোর দেওয়া হয়।'},
      {q: 'মুদালিয়র কমিশনের মতে, মাধ্যমিক শিক্ষার লক্ষ্য ও উদ্দেশ্য কোন্ দৃষ্টিভঙ্গিকে কেন্দ্র করে নির্ধারণ করতে হবে?', opts: ['আঞ্চলিক', 'রাজ্য', 'জাতীয়', 'বিদেশি'], ans: 2, exp: 'জাতীয় দৃষ্টিভঙ্গিকে কেন্দ্র করে লক্ষ্য নির্ধারণ করতে হবে।'},
      {q: 'মুদালিয়র কমিশনের মতে, নীচের কোনটি মাধ্যমিক শিক্ষার লক্ষ্য ও উদ্দেশ্য নির্ধারণের জাতীয় দৃষ্টিভঙ্গি?', opts: ['গণতান্ত্রিক', 'দারিদ্র্য দূরীকরণ', 'সাংস্কৃতিক পুনরুজ্জীবন', 'সব ক-টি'], ans: 3, exp: 'গণতান্ত্রিক সমাজব্যবস্থা, দারিদ্র্য দূরীকরণ এবং সাংস্কৃতিক পুনরুজ্জীবন — সবই জাতীয় দৃষ্টিভঙ্গি।'},
      {q: 'জাতীয় দৃষ্টিভঙ্গিকে ভিত্তি করে মাধ্যমিক শিক্ষার লক্ষ্য কোনটি?', opts: ['গণতান্ত্রিক নাগরিক গঠন', 'কর্মদক্ষতা বৃদ্ধি', 'সংস্কৃতির সংরক্ষণ ও বিকাশ সাধন', 'সব ক-টি'], ans: 3, exp: 'যোগ্য নাগরিক গঠন, কর্মদক্ষতা বৃদ্ধি ও সংস্কৃতির বিকাশ সবই লক্ষ্য।'},
      {q: 'মাধ্যমিক শিক্ষাব্যবস্থাকে সুপরিচালনার জন্য প্রতিটি রাজ্যে কী গঠন করার সুপারিশ করেছেন?', opts: ['মাধ্যমিক শিক্ষা পরিষদ গঠন', 'শিক্ষাসংস্থা গঠন', 'মাধ্যমিক বিদ্যালয় স্থাপন', 'কোনোটিই নয়'], ans: 0, exp: 'প্রতিটি রাজ্যে মাধ্যমিক শিক্ষা পর্ষদ বা পরিষদ গঠনের সুপারিশ করা হয়।'},
      {q: 'কোঠারি কমিশনের প্রকাশিত রিপোর্টের শিরোনাম হল—', opts: ['শিক্ষা এবং জাতীয় উন্নয়ন', 'শিক্ষা এবং জাতীয় বিকাশ', 'শিক্ষা এবং আন্তর্জাতিক বিকাশ', 'শিক্ষা এবং রাষ্ট্রের বিকাশ'], ans: 1, exp: 'Education and National Development — শিক্ষা ও জাতীয় অগ্রগতি শিরোনামে প্রকাশিত হয়।'},
      {q: 'কোঠারি কমিশনের মতে শিক্ষা কাঠামোটি হল—', opts: ['10 + 1 + 2 + 3', '10 + 2 + 3 + 2', '10 + 2 + 3 + 2', '4 + 4 + 2 + 2 + 3 + 2'], ans: 1, exp: 'কোঠারি কমিশনের প্রস্তাবিত কাঠামো 10 + 2 + 3 + 2।'},
      {q: 'ভারতীয় শিক্ষা কমিশনের অপর নাম হল—', opts: ['মুদালিয়র কমিশন', 'রাধাকৃষ্ণণ কমিশন', 'কোঠারি কমিশন', 'হান্টার কমিশন'], ans: 2, exp: 'ড. ডি. এস. কোঠারির সভাপতিত্বে গঠিত হওয়ায় এটি কোঠারি কমিশন নামে পরিচিত।'},
      {q: 'কোঠারি কমিশন মোট কতজন সদস্য নিয়ে গঠিত?', opts: ['16 জন', '15 জন', '19 জন', '17 জন'], ans: 3, exp: 'ভারত সরকার ১৭ জন বিশিষ্ট শিক্ষাবিদ নিয়ে কমিশন গঠন করেন।'},
      {q: 'কোঠারি কমিশনের রিপোর্টটি প্রকাশিত হয়—', opts: ['1906 খ্রিস্টাব্দের মে মাসে', '1966 খ্রিস্টাব্দের জুন মাসে', '1964 খ্রিস্টাব্দের জুলাই মাসে', '1967 খ্রিস্টাব্দের মে মাসে'], ans: 1, exp: '১৯৬৬ সালের ২৯ জুন কমিশন তাদের রিপোর্ট জমা দেন।'},
      {q: 'কোঠারি কমিশনে কতজন ভারতীয় সদস্য ছিল?', opts: ['11 জন', '12 জন', '13 জন', '10 জন'], ans: 3, exp: '১৭ জন সদস্যের মধ্যে ১০ জন বিশিষ্ট ভারতীয় শিক্ষাবিদ ছিলেন।'}
    ]
  },
  9: {
    name: 'Set 9',
    icon: '📖',
    topic: 'কোঠারি কমিশনের প্রাথমিক স্তর ও উচ্চশিক্ষা',
    questions: [
      {q: 'কোঠারি কমিশনের সভাপতি হলেন—', opts: ['ড. জে. পি. নায়েক', 'ডি. এস. কোঠারি', 'ড. এ. লক্ষ্মণস্বামী মুদালিয়র', 'লর্ড কার্জন'], ans: 1, exp: 'বিশিষ্ট জ্যোতির্বিদ ড. দৌলত সিং কোঠারি ছিলেন কমিশনের সভাপতি।'},
      {q: 'কোঠারি কমিশনে বিদেশি সদস্য সংখ্যা হল—', opts: ['10 জন', '11 জন', '5 জন', '7 জন'], ans: 3, exp: 'ইউনেস্কো, ইংল্যান্ড, আমেরিকা, জাপান, রাশিয়া ও ফ্রান্সের ৭ জন বিদেশি সদস্য ছিলেন।'},
      {q: 'কোঠারি কমিশনে Working Group-এর সংখ্যা হল—', opts: ['7টি', '8টি', '4টি', '10টি'], ans: 0, exp: '১২টি Task Force এবং ৭টি Working Group নিয়ে কাজ করেছিল।'},
      {q: 'কোঠারি কমিশনের মতে প্রাথমিক শিক্ষার সময়কাল হল—', opts: ['7/8 বছর', '5/6 বছর', '8 বছর', '4/5 বছর'], ans: 0, exp: 'প্রাথমিক শিক্ষার স্তরটি সাত বা আট বছরের হবে।'},
      {q: 'নিম্ন প্রাথমিক শিক্ষা হবে—', opts: ['প্রথম থেকে চতুর্থ বা পঞ্চম শ্রেণি', 'প্রথম থেকে চতুর্থ শ্রেণি', 'প্রথম থেকে ষষ্ঠ শ্রেণি', 'প্রথম থেকে অষ্টম শ্রেণি'], ans: 0, exp: 'চার বা পাঁচ বছরের শিক্ষাকাল নিম্ন প্রাথমিক স্তর।'},
      {q: 'নিম্ন প্রাথমিক শিক্ষার সর্বোচ্চ সময়কাল হল—', opts: ['4/5 বছর', '2 বছর', '3/4 বছর', '2/3 বছর'], ans: 0, exp: 'শিক্ষার্থীদের বয়স ৬ থেকে ১০ বা ১১ বছর এবং শিক্ষাকাল ৪ বা ৫ বছর।'},
      {q: 'উচ্চ প্রাথমিক শিক্ষার সর্বোচ্চ শ্রেণি হল—', opts: ['সপ্তম', 'অষ্টম', 'সপ্তম/অষ্টম', 'কোনোটিই নয়'], ans: 2, exp: 'পঞ্চম বা ষষ্ঠ থেকে সর্বোচ্চ সপ্তম বা অষ্টম শ্রেণি পর্যন্ত।'},
      {q: 'উচ্চশিক্ষার কয়টি স্তর?', opts: ['2টি', '3টি', '4টি', '5টি'], ans: 0, exp: 'উচ্চশিক্ষা প্রধানত দুটি স্তরে (স্নাতক ও স্নাতকোত্তর) ভাগ করা হয়েছে।'},
      {q: 'স্নাতকোত্তর স্তর হল—', opts: ['উচ্চশিক্ষার প্রথম স্তর', 'উচ্চশিক্ষার সর্বশেষ স্তর', 'উচ্চমাধ্যমিক স্তর', 'মাধ্যমিক স্তর'], ans: 1, exp: 'স্নাতকোত্তর স্তর হলো উচ্চশিক্ষার সর্বশেষ পর্যায়।'},
      {q: 'উচ্চশিক্ষার প্রথম স্তরের শিক্ষাকাল হল—', opts: ['5 বছর', '4 বছর', '2 বছর', '3 বছর'], ans: 3, exp: 'স্নাতক স্তরের শিক্ষাকাল তিন বছর।'},
      {q: 'কোঠারি কমিশন কয়টি Task Force গঠন করেছিল?', opts: ['12টি', '17টি', '9টি', '10টি'], ans: 0, exp: 'মোট ১২টি টাস্ক ফোর্স গঠন করেছিল।'},
      {q: 'কর্মের মাধ্যমে শিক্ষা হল—', opts: ['সাধারণ শিক্ষা', 'বৃত্তি ও কারিগরি শিক্ষা', 'কর্ম অভিজ্ঞতা', 'কোনোটিই নয়'], ans: 2, exp: 'কমিশন প্রত্যক্ষ কাজের মাধ্যমে অভিজ্ঞতা অর্জনকে কর্ম অভিজ্ঞতা বলেছেন।'},
      {q: 'বৃত্তিমুখী শিক্ষার একটি বৈশিষ্ট্য হল—', opts: ['স্থিতিশীল প্রক্রিয়া', 'সংগতিবিধানের প্রক্রিয়া', 'নির্বাচনধর্মিতা', 'সৌন্দর্যবোধ বিকাশের প্রক্রিয়া'], ans: 2, exp: 'শিক্ষার্থীরা নিজস্ব দক্ষতা অনুযায়ী বিষয় নির্বাচন করতে পারে।'},
      {q: 'কোঠারি কমিশনের মতে উচ্চশিক্ষার প্রথম স্তরে শিক্ষার মাধ্যম হবে—', opts: ['ইংরেজি ভাষা', 'আঞ্চলিক ভাষা', 'হিন্দি ভাষা', 'সংস্কৃত ভাষা'], ans: 1, exp: 'উচ্চশিক্ষার মাধ্যম হিসেবে আঞ্চলিক ভাষা ব্যবহারের সুপারিশ করা হয়েছে।'},
      {q: 'উচ্চশিক্ষার উচ্চমানের শিক্ষা ও গবেষণার জন্য প্রতিষ্ঠিত করতে হবে—', opts: ['প্রধান বিশ্ববিদ্যালয়', 'বিশ্ববিদ্যালয়', 'ডিপ্লোমা কোর্সের বিশ্ববিদ্যালয়', 'সাধারণ মানের বিশ্ববিদ্যালয়'], ans: 0, exp: 'Major Universities বা প্রধান বিশ্ববিদ্যালয় প্রতিষ্ঠা করতে হবে।'}
    ]
  },
  10: {
    name: 'Set 10',
    icon: '🗣️',
    topic: 'কোঠারি কমিশনের সংগঠন ও ভাষানীতি',
    questions: [
      {q: 'কোঠারি কমিশনের একজন ভারতীয় সদস্য হলেন—', opts: ['অধ্যাপক সুনভোষি', 'ড. বি. পি. পল', 'অধ্যাপক রোজার রেভেলি', 'ড. ডি. এস.'], ans: 1, exp: 'ড. বি. পি. পল ছিলেন ১০ জন ভারতীয় সদস্যের একজন।'},
      {q: 'কোঠারি কমিশনের একটি Task Force হল—', opts: ['বিজ্ঞান শিক্ষা এবং গবেষণা', 'প্রাক্-প্রাথমিক শিক্ষা', 'নারীশিক্ষা', 'মধ্যশিক্ষা পর্ষদ'], ans: 0, exp: 'বিজ্ঞান শিক্ষা এবং গবেষণা ছিল ১২টি টাস্ক ফোর্সের একটি।'},
      {q: 'কোঠারি কমিশনের একজন বিদেশি সদস্য হলেন—', opts: ['ড. টি. সেন', 'ড. পি. এন. কিরাপাল', 'ড. জে. পি. নায়েক', 'মিস্টার এম. জেন থমাস'], ans: 3, exp: 'ফ্রান্সের প্রতিনিধি মিস্টার এম. জেন থমাস ছিলেন বিদেশি সদস্য।'},
      {q: 'কোন কমিশন প্রতিটি রাজ্যে রাজ্য শিক্ষা পরিষদ গঠনের সুপারিশ করেছেন?', opts: ['রাধাকৃষ্ণণ কমিশন', 'মুদালিয়র কমিশন', 'হান্টার কমিশন', 'কোঠারি কমিশন'], ans: 3, exp: 'কোঠারি কমিশন রাজ্য শিক্ষা পরিষদ গঠনের সুপারিশ করেছিল।'},
      {q: 'স্কুল কমপ্লেক্স (বিদ্যালয়গুচ্ছ) গঠনের সুপারিশ করা হয়—', opts: ['মুদালিয়র কমিশনে', 'কোঠারি কমিশনে', 'জনার্দন রেডি কমিশনে', 'রাধাকৃষ্ণণ কমিশনে'], ans: 1, exp: 'কোঠারি কমিশন প্রথম বিদ্যালয়গুচ্ছ গঠনের সুপারিশ করেন।'},
      {q: 'কোঠারি কমিশনের মতে, বিদ্যালয়গুলির কাজের দিনসংখ্যা হবে—', opts: ['210 দিন', '215 দিন', '234 দিন', '307 দিন'], ans: 2, exp: 'কমিশন কাজের দিনসংখ্যা ২৩৪ দিন করার সুপারিশ করেছিলেন।'},
      {q: 'কোঠারি কমিশনের সুপারিশে কমন স্কুলব্যবস্থার দ্বারা কোন বিষয়কে গুরুত্ব দেওয়া হয়েছে?', opts: ['শিক্ষায় সমসুযোগ', 'অপচয় ও অনুন্নয়ন', 'সমাজসেবা', 'জাতীয় উৎপাদন'], ans: 0, exp: 'সকলকে শিক্ষাক্ষেত্রে সমান সুযোগ প্রদান করাই কমন স্কুল ব্যবস্থার লক্ষ্য।'},
      {q: 'কোন শিক্ষার স্তরের ওপর অপচয় ও অনুন্নয়ন সর্বাধিক প্রভাব বিস্তার করে?', opts: ['উচ্চশিক্ষা', 'প্রাক্-প্রাথমিক শিক্ষা', 'প্রাথমিক শিক্ষা', 'মাধ্যমিক শিক্ষা'], ans: 2, exp: 'প্রাথমিক শিক্ষাস্তরে শিক্ষার্থীরা বিদ্যালয় ছেড়ে দেয়ায় অপচয় সর্বাধিক।'},
      {q: 'কোঠারি কমিশনে বহিঃপরীক্ষার উন্নয়নের জন্য সুপারিশ হল—', opts: ['প্রশ্নের সংখ্যা বৃদ্ধি', 'রচনাধর্মী প্রশ্নের ওপর গুরুত্ব', 'প্রশ্নের মানের পরিবর্তন ও বিজ্ঞানভিত্তিক নম্বর দেওয়া', 'পরীক্ষকের সংখ্যা বৃদ্ধি'], ans: 2, exp: 'নম্বর দেওয়ার পদ্ধতিকে বিজ্ঞানভিত্তিক করার সুপারিশ করা হয়।'},
      {q: 'কোঠারি কমিশনের মতে, প্রাক্-প্রাথমিক শিক্ষার প্রধান উদ্দেশ্য হল—', opts: ['নেতৃত্ব দান', 'সু-অভ্যাস গঠন করা', 'বিজ্ঞান শিক্ষা', 'সৃজনশীলতার বিকাশ'], ans: 1, exp: 'শৈশবকালে সু-অভ্যাস গঠন করাই প্রাক্-প্রাথমিক শিক্ষার প্রধান উদ্দেশ্য।'},
      {q: 'কোঠারি কমিশনের মতে, প্রাথমিক শিক্ষাস্তরে ভরতির ন্যূনতম বয়স হবে—', opts: ['4 বছর', '6+ বছর', '7+ বছর', '10+ বছর'], ans: 1, exp: '৬ বছর বয়স থেকে শিশুদের প্রাথমিক শিক্ষাস্তরে ভরতি হওয়ার কথা বলা হয়েছে।'},
      {q: 'কোঠারি কমিশনের ভিত্তিতে কোন্ জাতীয় শিক্ষানীতি রচিত হয়?', opts: ['1968 খ্রিস্টাব্দের জাতীয় শিক্ষানীতি', '1978 খ্রিস্টাব্দের জাতীয় শিক্ষানীতি', '1986 খ্রিস্টাব্দের জাতীয় শিক্ষানীতি', 'কোনোটিই নয়'], ans: 0, exp: 'কোঠারি কমিশনের সুপারিশের ভিত্তিতে ১৯৬৮ সালে প্রথম জাতীয় শিক্ষানীতি রচিত হয়।'},
      {q: 'কোঠারি কমিশনের মূল রিপোর্ট ছিল—', opts: ['692 পৃষ্ঠার', '747 পৃষ্ঠার', '489 পৃষ্ঠার', '542 পৃষ্ঠার'], ans: 2, exp: '৬৯২ পৃষ্ঠার রিপোর্টের মধ্যে মূল রিপোর্টটি ছিল ৪৮৯ পৃষ্ঠার।'},
      {q: 'কোঠারি কমিশন, তাঁদের রিপোর্টটি জমা দেন—', opts: ['Union Education Minister-এর নিকট', 'United Education Minister-এর নিকট', 'Union Educational Minister-এর নিকট', 'Universal Education Minister-এর নিকট'], ans: 0, exp: '১৯৬৬ সালের ২৯ জুন তৎকালীন শিক্ষামন্ত্রীর কাছে রিপোর্ট জমা দেওয়া হয়।'},
      {q: 'কোঠারি কমিশন কত খ্রিস্টাব্দে কাজ শুরু করে?', opts: ['1966 খ্রিস্টাব্দের 29 জুন', '1964 খ্রিস্টাব্দের 2 অক্টোবর', '1965 খ্রিস্টাব্দের 2 অক্টোবর', '1964 খ্রিস্টাব্দের 29 জুন'], ans: 1, exp: '১৯৬৪ সালের ২ অক্টোবর থেকে আনুষ্ঠানিকভাবে কাজ শুরু করে।'}
    ]
  },
  11: {
    name: 'Set 11',
    icon: '🌐',
    topic: 'কোঠারি কমিশনের ভাষা, কারিগরি ও বিদ্যালয়গুচ্ছ',
    questions: [
      {q: 'অধ্যাপক সদতোশি কোন দেশের লোক ছিলেন?', opts: ['ইংল্যান্ড', 'রাশিয়া', 'ফ্রান্স', 'জাপান'], ans: 3, exp: 'অধ্যাপক সদতোশি ইহারা ছিলেন জাপানের শিক্ষাবিদ।'},
      {q: 'কোঠারি কমিশন কোন শ্রেণি থেকে ইংরেজি ভাষাশিক্ষা শুরু করার কথা বলেছেন?', opts: ['প্রথম শ্রেণি', 'দ্বিতীয় শ্রেণি', 'পঞ্চম শ্রেণি', 'চতুর্থ শ্রেণি'], ans: 2, exp: 'পঞ্চম শ্রেণি থেকে ইংরেজি শেখার কথা বলা হয়েছে।'},
      {q: 'কোঠারি কমিশনে বৃত্তিমুখী শিক্ষা কোন্ স্তর থেকে শুরু করার কথা বলা হয়েছে?', opts: ['প্রাক প্রাথমিক', 'প্রাথমিক', 'নিম্ন মাধ্যমিক', 'উচ্চমাধ্যমিক'], ans: 2, exp: 'নিম্ন মাধ্যমিক স্তর (অষ্টম/নবম শ্রেণি) থেকে বৃত্তিমুখী শিক্ষা দেওয়ার সুপারিশ করা হয়েছে।'},
      {q: 'কারিগরি শিক্ষার সঙ্গে কোন্ ধরনের শিক্ষার গভীর সম্পর্ক বিশেষভাবে লক্ষ করা যায়?', opts: ['সাহিত্য', 'গার্হস্থ্য বিজ্ঞান', 'বাণিজ্য', 'বিজ্ঞান শিক্ষা'], ans: 3, exp: 'বিজ্ঞান এবং কারিগরি শিক্ষা একে অপরের পরিপূরক।'},
      {q: 'কারিগরি শিক্ষার সঙ্গে সম্পর্কিত একটি সংস্থা হল—', opts: ['NCERT', 'NCTE', 'UGC', 'AICTE'], ans: 3, exp: 'AICTE হলো ভারতের কারিগরি শিক্ষার সর্বোচ্চ সংস্থা।'},
      {q: 'ভারতীয় শিক্ষা কমিশন গঠিত হয়—', opts: ['1964 খ্রিস্টাব্দে', '1966 খ্রিস্টাব্দে', '1948 খ্রিস্টাব্দে', '1952 খ্রিস্টাব্দে'], ans: 0, exp: '১৯৬৪ সালের ১৪ জুলাই ভারতীয় শিক্ষা কমিশন গঠিত হয়।'},
      {q: 'বিদ্যালয় স্তরে পাঠ্যক্রম রচনা করে—', opts: ['NCERT', 'NCTE', 'CABE', 'UGC'], ans: 0, exp: 'NCERT বিদ্যালয় স্তরের পাঠ্যক্রম রচনা করে।'},
      {q: 'কোঠারি কমিশনের মতে, নিম্ন প্রাথমিক স্তরে কয়টি ভাষা শিক্ষার কথা বলা হয়েছে?', opts: ['একটি ভাষা', 'দুটি ভাষা', 'তিনটি ভাষা', 'সব ক-টি'], ans: 0, exp: 'নিম্ন প্রাথমিক স্তরে শুধু একটি ভাষা (মাতৃভাষা) শেখার কথা বলা হয়েছে।'},
      {q: 'উচ্চ প্রাথমিক স্তরে কয়টি ভাষা শিক্ষার কথা বলা হয়েছে?', opts: ['একটি ভাষা', 'দুটি ভাষা', 'তিনটি ভাষা', 'সব ক-টি'], ans: 1, exp: 'উচ্চ প্রাথমিক স্তরে দুটি ভাষা আবশ্যিক করা হয়েছে।'},
      {q: 'নিম্ন মাধ্যমিক স্তরে কয়টি ভাষা শিক্ষার কথা বলা হয়েছে?', opts: ['একটি ভাষা', 'দুটি ভাষা', 'তিনটি ভাষা', 'সব ক-টি'], ans: 2, exp: 'নিম্ন মাধ্যমিক স্তরে ত্রিভাষা সূত্র প্রয়োগ হয়।'},
      {q: 'উচ্চমাধ্যমিক স্তরে কয়টি ভাষা শিক্ষার কথা বলা হয়েছে?', opts: ['একটি ভাষা', 'দুটি ভাষা', 'তিনটি ভাষা', 'সব ক-টি'], ans: 1, exp: 'উচ্চমাধ্যমিক স্তরে দুটি ভাষা বাধ্যতামূলক।'},
      {q: 'বিদ্যালয় শিক্ষার গুণগত মান উন্নয়নের জন্য কী গড়ে তোলার কথা বলা হয়েছে?', opts: ['বিদ্যালয় সংগঠন', 'বিদ্যালয় সংস্থা', 'বিদ্যালয়গুচ্ছ', 'বিদ্যালয় পাঠ্যক্রম'], ans: 2, exp: 'শিক্ষার মান উন্নয়নে বিদ্যালয়গুচ্ছ বা School Complex গঠনের কথা বলা হয়েছে।'},
      {q: 'প্রথম পর্যায়ে কতগুলি বিদ্যালয় নিয়ে বিদ্যালয়গুচ্ছ গঠনের কথা বলা হয়েছে?', opts: ['8-15টি', '8-10টি', '10-14টি', '15-20টি'], ans: 1, exp: 'প্রথম পর্যায়ে ৮ থেকে ১০টি বিদ্যালয় নিয়ে গুচ্ছ গঠনের কথা বলা হয়েছে।'},
      {q: 'প্রথম পর্যায়ে বিদ্যালয়গুচ্ছের কেন্দ্রে কোন্ বিদ্যালয় থাকবে?', opts: ['নিম্ন প্রাথমিক বিদ্যালয়', 'উচ্চ প্রাথমিক বিদ্যালয়', 'মাধ্যমিক বিদ্যালয়', 'উচ্চমাধ্যমিক বিদ্যালয়'], ans: 1, exp: 'প্রথম পর্যায়ের কেন্দ্রে একটি উচ্চ প্রাথমিক বিদ্যালয় থাকবে।'},
      {q: 'দ্বিতীয় পর্যায়ে বিদ্যালয়গুচ্ছ কতগুলি বিদ্যালয় নিয়ে গঠিত হবে?', opts: ['15-20টি', '10-15টি', '18-25', '10-30টি'], ans: 0, exp: 'দ্বিতীয় পর্যায়ে ১৫ থেকে ২০টি বিদ্যালয় নিয়ে গুচ্ছ গঠিত হবে।'}
    ]
  },
  12: {
    name: 'Set 12',
    icon: '👩‍🏫',
    topic: 'কোঠারি কমিশনের শিক্ষক শিক্ষণ, বয়স্ক শিক্ষা ও নারীশিক্ষা',
    questions: [
      {q: 'দ্বিতীয় পর্যায়ে বিদ্যালয়গুচ্ছের কেন্দ্রে কোন বিদ্যালয় থাকবে?', opts: ['উচ্চমাধ্যমিক বিদ্যালয়', 'নিম্ন প্রাথমিক বিদ্যালয়', 'একটি মাধ্যমিক বিদ্যালয়', 'উচ্চমাধ্যমিক বিদ্যালয়'], ans: 2, exp: 'দ্বিতীয় পর্যায়ের কেন্দ্রে একটি মাধ্যমিক বিদ্যালয় থাকবে।'},
      {q: 'প্রতিবেশী বিদ্যালয় প্রথা গঠনের কথা কোন্ কমিশনে বলা হয়েছে?', opts: ['মুদালিয়র কমিশন', 'রাধাকৃষ্ণণ কমিশন', 'কোঠারি কমিশন', 'অশোক মিত্র কমিশন'], ans: 2, exp: 'কোঠারি কমিশন প্রতিবেশী বিদ্যালয় প্রথা গঠনের কথা বলেছেন।'},
      {q: 'প্রতিবেশী বিদ্যালয় প্রথার উদ্দেশ্য কী?', opts: ['অনুদান প্রদান', 'সকল শিশুকে বিদ্যালয়ে ভরতি', 'সকলের শিক্ষায় অধিকার প্রদান', 'আঞ্চলিক শিক্ষায় গুরুত্ব দান'], ans: 2, exp: 'সকলের শিক্ষায় সমান অধিকার নিশ্চিত করাই এর উদ্দেশ্য।'},
      {q: 'SBTE-এর সম্পূর্ণ নাম কী?', opts: ['State Board of Teacher Education', 'State Board of Teacher Educo', 'State Board of Talent Education', 'কোনোটিই নয়'], ans: 0, exp: 'রাজ্য স্তরে State Board of Teacher Education প্রতিষ্ঠার কথা বলা হয়েছে।'},
      {q: 'শিক্ষক শিক্ষণ ব্যবস্থা তদারকি করার জন্য প্রতিটি রাজ্যে কী গঠন করার কথা বলা হয়েছে?', opts: ['শিক্ষক শিক্ষণ সংস্থা', 'রাজ্য শিক্ষক শিক্ষণ পর্ষদ', 'রাজ্য শিক্ষক শিক্ষণ কমিটি', 'রাজ্য শিক্ষক সংগঠন'], ans: 1, exp: 'রাজ্য শিক্ষক শিক্ষণ পর্ষদ গঠনের প্রস্তাব দেওয়া হয়।'},
      {q: 'কর্মরত শিক্ষকদের জ্ঞানের নবীকরণের জন্য কত বছর অন্তর প্রশিক্ষণের ব্যবস্থা করতে হবে?', opts: ['তিন বছর', 'চার বছর', 'পাঁচ বছর', 'দশ বছর'], ans: 2, exp: 'প্রতি ৫ বছর অন্তর প্রশিক্ষণের ব্যবস্থা করতে হবে।'},
      {q: 'বয়স্ক নারীদের সাক্ষর করে তোলার জন্য কাদের নিয়োগ করতে হবে?', opts: ['গ্রামের শিক্ষক', 'গ্রামের ভগিনী', 'গ্রামের মানুষ', 'কোনোটিই নয়'], ans: 1, exp: 'গ্রামের ভগিনী (Village Sister) নিয়োগের কথা বলা হয়েছে।'},
      {q: 'কোঠারি কমিশন নিরক্ষরতা দূরীকরণের জন্য কোন্ কোন্ পদ্ধতির উল্লেখ করেছেন?', opts: ['নির্বাচনমূলক ও ব্যাপক পদ্ধতি', 'নির্বাচনমূলক ও অনুকরণমূলক পদ্ধতি', 'ব্যাপক ও সংকীর্ণ পদ্ধতি', 'ব্যাপক ও পর্যবেক্ষণ পদ্ধতি'], ans: 0, exp: 'নির্বাচনমূলক ও ব্যাপক পদ্ধতি — এই দুটি পদ্ধতির উল্লেখ করা হয়েছে।'},
      {q: 'বয়স্ক ব্যক্তিদের পাঠে আগ্রহ সৃষ্টি করতে গ্রন্থাগার বিষয়ক উপদেষ্টা কমিটি সারা দেশে কী তৈরির সুপারিশ করেন?', opts: ['Library', 'Home Library', 'Library Net Work', 'কোনোটিই নয়'], ans: 2, exp: 'সারা দেশে Library Network তৈরির সুপারিশ করা হয়।'},
      {q: 'NBAE-এর সম্পূর্ণ নাম কী?', opts: ['National Body of Adult Education', 'National Board of Adult Education', 'National Board of Area Education', 'National Board of Adult of Educo'], ans: 1, exp: 'বয়স্ক শিক্ষার জন্য National Board of Adult Education (NBAE) গঠনের কথা বলা হয়েছে।'},
      {q: 'SAT-এর সম্পূর্ণ নাম কী?', opts: ['State Achievement Test', 'Standardized Achievement Test', 'Standard Achievement Test', 'Standardized Achievement Text'], ans: 1, exp: 'Standardized Achievement Test — আদর্শায়িত পারদর্শিতার অভীক্ষা।'},
      {q: 'প্রাথমিক বিদ্যালয়গুলিতে শিক্ষা শেষে বিভিন্ন জেলায় কীসের মাধ্যমে শিক্ষার্থীদের মূল্যায়নের কথা বলা হয়েছে?', opts: ['আদর্শায়িত পারদর্শিতার অভীক্ষা', 'পারদর্শিতার অভীক্ষা', 'বার্ষিক পরীক্ষা', 'ক্রমিক মূল্যায়ন'], ans: 0, exp: 'SAT বা আদর্শায়িত পারদর্শিতার অভীক্ষার মাধ্যমে মূল্যায়ন করা হবে।'},
      {q: 'মাধ্যমিক ও উচ্চমাধ্যমিক স্তরে কোন্ ধরনের পরীক্ষার ব্যবস্থার কথা কোঠারি কমিশনে বলা হয়?', opts: ['অভ্যন্তরীণ পরীক্ষা', 'বহিঃপরীক্ষা', 'বার্ষিক পরীক্ষা', 'অর্ধবার্ষিক পরীক্ষা'], ans: 1, exp: 'মাধ্যমিক ও উচ্চমাধ্যমিক স্তরে বহিঃপরীক্ষা বা বোর্ড পরীক্ষার ব্যবস্থা করার কথা বলা হয়েছে।'},
      {q: 'কোঠারি কমিশনের সুপারিশ অনুযায়ী কতগুলি বিদ্যালয়ের জন্য একজন পরিদর্শক-পরামর্শদাতা নিয়োগ করতে হবে?', opts: ['5টি', '7টি', '9টি', '10টি'], ans: 3, exp: 'প্রতি ১০টি বিদ্যালয়ের জন্য একজন পরিদর্শক-পরামর্শদাতা নিয়োগের কথা বলা হয়েছে।'},
      {q: 'নারীশিক্ষার প্রসারের জন্য কোঠারি কমিশন কী গঠনের সুপারিশ করেছেন?', opts: ['The National Committee on the Education of Women', 'The National Common on the Education of Women', 'The National Commenly on the Education of Women', 'The National committee on the Educational of Woman'], ans: 0, exp: 'নারীশিক্ষার উন্নয়নে বিশেষ কমিটি গঠনের ওপর গুরুত্ব দেওয়া হয়েছে।'}
    ]
  }
};

// ============================================================
//  গ্লোবাল ভেরিয়েবল
// ============================================================
const LABELS = ['ক', 'খ', 'গ', 'ঘ'];
let currentSetId = 1;
let cur = 0, score = 0, wrong = 0, answered = false, timerInterval, timeLeft = 10 * 60;
let userAnswers = [];
let isLoggedIn = false;
let currentUser = null;
let pendingSetId = null;

// ============================================================
//  হাব পেজ বিল্ড
// ============================================================
function buildHub() {
  const grid = document.getElementById('setGrid');
  grid.innerHTML = '';
  for (let i = 1; i <= TOTAL_SETS; i++) {
    const set = allSets[i];
    const card = document.createElement('div');
    card.className = 'set-card';
    card.innerHTML = `
      <div class="icon">${set.icon}</div>
      <div class="set-num">${set.name}</div>
      <div class="set-title">${set.topic}</div>
      <div class="set-meta"><span>১৫ প্রশ্ন</span><span>১০ মিনিট</span></div>
    `;
    card.onclick = () => selectSet(i);
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
    document.getElementById('hubUserInfo').innerHTML = `👤 ${currentUser.username} — Test দিতে সেট সিলেক্ট করো।`;
  } else {
    document.getElementById('hubUserInfo').innerHTML = '';
  }
}

function goToHub() {
  document.getElementById('testArea').classList.add('hidden');
  document.getElementById('resultWrap').classList.remove('show');
  document.getElementById('hubPage').classList.remove('hidden');
  document.getElementById('timerBox').classList.remove('danger');
  clearInterval(timerInterval);
  isLoggedIn = false;
  currentUser = null;
}

// ============================================================
//  সেট সিলেক্ট - সবসময় লগইন চেক
// ============================================================
function selectSet(id) {
  currentSetId = id;
  const set = allSets[id];
  pendingSetId = id;
  document.getElementById('loginSetName').textContent = `📚 ${set.name} — ${set.topic}`;
  document.getElementById('loginOverlay').classList.add('active');
  document.getElementById('loginUsername').value = '';
  document.getElementById('loginPassword').value = '';
  document.getElementById('loginError').style.display = 'none';
  document.getElementById('limitInfo').style.display = 'none';
  document.getElementById('loginBtn').disabled = false;
  document.getElementById('loginUsername').focus();
}

// ============================================================
//  লগইন ফাংশন
// ============================================================
function doLoginFromSet() {
  const username = document.getElementById('loginUsername').value.trim();
  const password = document.getElementById('loginPassword').value.trim();
  const errorEl = document.getElementById('loginError');
  const limitInfo = document.getElementById('limitInfo');
  const loginBtn = document.getElementById('loginBtn');

  if (!username || !password) {
    errorEl.textContent = '❌ দয়া করে ইউজারনেম ও পাসওয়ার্ড দিন।';
    errorEl.style.display = 'block';
    return;
  }

  const user = userData.find(u => u.username === username && u.password === password);
  if (user) {
    const setAttempts = user.attempts[currentSetId] || 0;
    if (setAttempts >= MAX_ATTEMPTS) {
      limitInfo.style.display = 'block';
      document.getElementById('limitMsg').textContent = `আপনি এই অ্যাকাউন্ট দিয়ে ${allSets[currentSetId].name} এর সর্বোচ্চ ${MAX_ATTEMPTS} বার Test দিয়েছেন। আর Test দেওয়া সম্ভব নয়।`;
      errorEl.style.display = 'none';
      loginBtn.disabled = true;
      return;
    }
    
    isLoggedIn = true;
    currentUser = user;
    errorEl.style.display = 'none';
    limitInfo.style.display = 'none';
    loginBtn.disabled = false;
    document.getElementById('loginOverlay').classList.remove('active');
    
    document.getElementById('hubUserInfo').innerHTML = `👤 ${currentUser.username} — Test দিতে সেট সিলেক্ট করো।`;
    
    startQuiz(currentSetId);
  } else {
    errorEl.textContent = '❌ ভুল ইউজারনেম বা পাসওয়ার্ড। আবার চেষ্টা করুন।';
    errorEl.style.display = 'block';
    limitInfo.style.display = 'none';
  }
}

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
  
  const setAttempts = currentUser.attempts[setId] || 0;
  if (setAttempts >= MAX_ATTEMPTS) {
    alert(`⚠️ আপনি এই সেটের সর্বোচ্চ ${MAX_ATTEMPTS} বার Test দিয়েছেন।`);
    return;
  }
  
  currentUser.attempts[setId] = (currentUser.attempts[setId] || 0) + 1;
  
  cur = 0; score = 0; wrong = 0; answered = false;
  timeLeft = 10 * 60; userAnswers = [];
  document.getElementById('hubPage').classList.add('hidden');
  document.getElementById('resultWrap').classList.remove('show');
  document.getElementById('testArea').classList.remove('hidden');
  document.getElementById('timerBox').classList.remove('danger');
  
  const set = allSets[setId];
  document.getElementById('testSetLabel').textContent = set.name;
  document.getElementById('testSetName').textContent = 'শিক্ষাবিজ্ঞান';
  document.getElementById('testTopic').textContent = set.topic;
  
  clearInterval(timerInterval);
  timerInterval = setInterval(tick, 1000);
  loadQ();
}

function tick() {
  timeLeft--;
  const m = Math.floor(timeLeft / 60);
  const s = timeLeft % 60;
  document.getElementById('timerDisplay').textContent = m + ':' + (s < 10 ? '0' : '') + s;
  if (timeLeft <= 60) document.getElementById('timerBox').classList.add('danger');
  if (timeLeft <= 0) { clearInterval(timerInterval); showResult(); }
}

function loadQ() {
  answered = false;
  const set = allSets[currentSetId];
  const q = set.questions[cur];
  document.getElementById('qNum').textContent = 'প্রশ্ন ' + (cur + 1) + ' / ' + set.questions.length;
  document.getElementById('qText').textContent = q.q;
  document.getElementById('progressFill').style.width = ((cur + 1) / set.questions.length * 100) + '%';
  document.getElementById('nextBtn').disabled = true;
  document.getElementById('nextBtn').textContent = cur === set.questions.length - 1 ? 'ফলাফল দেখো' : 'পরবর্তী →';
  document.getElementById('explanation').classList.remove('show');

  const opts = document.getElementById('qOpts');
  opts.innerHTML = '';
  q.opts.forEach((o, i) => {
    const btn = document.createElement('button');
    btn.className = 'opt';
    btn.innerHTML = '<div class="opt-circle">' + LABELS[i] + '</div><div class="opt-text">' + o + '</div>';
    btn.onclick = () => answer(i);
    opts.appendChild(btn);
  });
}

function answer(i) {
  if (answered) return;
  answered = true;
  const set = allSets[currentSetId];
  const q = set.questions[cur];
  userAnswers[cur] = i;
  const btns = document.querySelectorAll('.opt');
  btns.forEach(b => b.classList.add('disabled'));
  btns[q.ans].classList.add('correct');
  if (i !== q.ans) { btns[i].classList.add('wrong'); wrong++; }
  else score++;
  document.getElementById('scoreShow').textContent = 'সঠিক: ' + score + ' | ভুল: ' + wrong;
  document.getElementById('explanationText').innerHTML = '<strong>ব্যাখ্যা:</strong> ' + q.exp;
  document.getElementById('explanation').classList.add('show');
  document.getElementById('nextBtn').disabled = false;
}

function nextQ() {
  const set = allSets[currentSetId];
  cur++;
  if (cur >= set.questions.length) { clearInterval(timerInterval); showResult(); return; }
  loadQ();
}

function showResult() {
  document.getElementById('testArea').classList.add('hidden');
  const rw = document.getElementById('resultWrap');
  rw.classList.add('show');
  const set = allSets[currentSetId];
  const pct = Math.round(score / set.questions.length * 100);
  document.getElementById('finalScore').textContent = score;
  document.getElementById('rbCorrect').textContent = score;
  document.getElementById('rbWrong').textContent = wrong;
  document.getElementById('rbPct').textContent = pct + '%';
  
  const remaining = MAX_ATTEMPTS - (currentUser.attempts[currentSetId] || 0);
  document.getElementById('attemptInfo').innerHTML = `👤 ${currentUser.username} — ${set.name}: বাকি আছে <strong>${remaining}</strong> বার Test দেওয়ার সুযোগ (সর্বোচ্চ ${MAX_ATTEMPTS} বার)`;
  
  const grades = [
    [90, '🌟', 'অসাধারণ!'],
    [70, '👍', 'খুব ভালো!'],
    [50, '📚', 'ভালো চেষ্টা!'],
    [0, '💪', 'চেষ্টা চালিয়ে যাও!']
  ];
  const g = grades.find(x => pct >= x[0]);
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
  const set = allSets[currentSetId];
  if (cur >= set.questions.length) { 
    document.getElementById('testArea').classList.add('hidden'); 
    document.getElementById('resultWrap').classList.add('show'); 
    return; 
  }
  const q = set.questions[cur];
  document.getElementById('qNum').textContent = 'Review — প্রশ্ন ' + (cur + 1) + ' / ' + set.questions.length;
  document.getElementById('qText').textContent = q.q;
  document.getElementById('progressFill').style.width = ((cur + 1) / set.questions.length * 100) + '%';
  document.getElementById('nextBtn').disabled = false;
  document.getElementById('nextBtn').textContent = cur === set.questions.length - 1 ? 'শেষ করো' : 'পরবর্তী →';
  document.getElementById('nextBtn').onclick = () => { cur++; loadReview(); };

  const opts = document.getElementById('qOpts');
  opts.innerHTML = '';
  q.opts.forEach((o, i) => {
    const btn = document.createElement('button');
    btn.className = 'opt disabled';
    if (i === q.ans) btn.classList.add('correct');
    else if (userAnswers[cur] === i) btn.classList.add('wrong');
    btn.innerHTML = '<div class="opt-circle">' + LABELS[i] + '</div><div class="opt-text">' + o + '</div>';
    opts.appendChild(btn);
  });

  document.getElementById('explanationText').innerHTML = '<strong>ব্যাখ্যা:</strong> ' + q.exp;
  document.getElementById('explanation').classList.add('show');
  document.getElementById('scoreShow').textContent = 'সবুজ = সঠিক উত্তর';
}
</script>

</body>
</html>
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
