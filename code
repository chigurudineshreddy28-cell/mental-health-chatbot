<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>ThriveMind — Mental Health Assessment</title>
<link href="https://fonts.googleapis.com/css2?family=DM+Serif+Display&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
  :root {
    --green-dark: #085041;
    --green-mid: #0F6E56;
    --green: #1D9E75;
    --green-light: #9FE1CB;
    --green-pale: #E1F5EE;
    --amber: #BA7517;
    --amber-pale: #FAEEDA;
    --red: #A32D2D;
    --red-pale: #FCEBEB;
    --text: #1a1a1a;
    --text-muted: #666;
    --text-hint: #999;
    --border: rgba(0,0,0,0.1);
    --bg: #f7f6f2;
    --card: #ffffff;
  }
  body {
    font-family: 'DM Sans', sans-serif;
    background: var(--bg);
    color: var(--text);
    min-height: 100vh;
    padding: 2rem 1rem 4rem;
  }
  .app { max-width: 620px; margin: 0 auto; }
  .header { text-align: center; margin-bottom: 2.5rem; padding-top: 1rem; }
  .header h1 {
    font-family: 'DM Serif Display', serif;
    font-size: 42px;
    color: var(--green-dark);
    letter-spacing: -1px;
    margin-bottom: 8px;
  }
  .header p { font-size: 15px; color: var(--text-muted); line-height: 1.6; }
  .progress-wrap { margin-bottom: 2rem; }
  .progress-bar { height: 3px; background: rgba(0,0,0,0.08); border-radius: 2px; }
  .progress-fill { height: 100%; background: var(--green); border-radius: 2px; transition: width 0.4s ease; }
  .progress-label { font-size: 12px; color: var(--text-hint); margin-top: 6px; text-align: right; }
  .question-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 16px;
    padding: 1.5rem;
    margin-bottom: 1rem;
    transition: border-color 0.2s;
  }
  .question-card:hover { border-color: var(--green-light); }
  .q-meta { display: flex; justify-content: space-between; align-items: center; margin-bottom: 8px; }
  .q-number { font-size: 11px; color: var(--text-hint); letter-spacing: 0.5px; text-transform: uppercase; }
  .q-val-badge { font-size: 13px; font-weight: 500; color: var(--green); background: var(--green-pale); padding: 2px 10px; border-radius: 20px; }
  .q-text { font-family: 'DM Serif Display', serif; font-size: 18px; color: var(--text); margin-bottom: 4px; }
  .q-desc { font-size: 13px; color: var(--text-muted); margin-bottom: 1.25rem; }
  input[type=range] {
    width: 100%; height: 4px; border-radius: 2px; outline: none; border: none;
    background: linear-gradient(to right, var(--green) 0%, var(--green) 40%, rgba(0,0,0,0.1) 40%);
    cursor: pointer; appearance: none; -webkit-appearance: none;
  }
  input[type=range]::-webkit-slider-thumb {
    appearance: none; width: 20px; height: 20px;
    border-radius: 50%; background: var(--green);
    border: 3px solid white; box-shadow: 0 1px 4px rgba(0,0,0,0.2); cursor: pointer;
  }
  .slider-labels { display: flex; justify-content: space-between; margin-top: 6px; }
  .slider-labels span { font-size: 11px; color: var(--text-hint); }
  .submit-btn {
    width: 100%; padding: 16px; background: var(--green-dark); color: white;
    border: none; border-radius: 12px; font-size: 16px; font-weight: 500;
    cursor: pointer; margin-top: 1.5rem; transition: background 0.2s, transform 0.1s;
    font-family: 'DM Sans', sans-serif; letter-spacing: 0.2px;
  }
  .submit-btn:hover { background: var(--green-mid); }
  .submit-btn:active { transform: scale(0.99); }
  .result-wrap { display: none; }
  .score-hero { text-align: center; background: var(--card); border: 1px solid var(--border); border-radius: 16px; padding: 2.5rem 2rem 2rem; margin-bottom: 1rem; }
  .score-ring {
    width: 130px; height: 130px; border-radius: 50%;
    display: flex; flex-direction: column; align-items: center; justify-content: center;
    margin: 0 auto 1.25rem; border: 3px solid;
  }
  .score-num { font-family: 'DM Serif Display', serif; font-size: 44px; line-height: 1; }
  .score-denom { font-size: 13px; color: var(--text-muted); margin-top: 2px; }
  .status-pill { display: inline-block; padding: 8px 22px; border-radius: 30px; font-size: 15px; font-weight: 500; margin-bottom: 1.25rem; }
  .analysis-text { font-size: 15px; color: var(--text-muted); line-height: 1.8; max-width: 480px; margin: 0 auto; }
  .section { background: var(--card); border: 1px solid var(--border); border-radius: 16px; padding: 1.5rem; margin-bottom: 1rem; }
  .section-title { font-family: 'DM Serif Display', serif; font-size: 20px; color: var(--text); margin-bottom: 1.25rem; }
  .bar-row { display: flex; align-items: center; gap: 12px; margin-bottom: 10px; }
  .bar-name { font-size: 12px; color: var(--text-muted); width: 140px; flex-shrink: 0; }
  .bar-track { flex: 1; height: 6px; background: rgba(0,0,0,0.06); border-radius: 3px; }
  .bar-fill { height: 100%; border-radius: 3px; transition: width 0.8s ease; }
  .bar-score { font-size: 12px; color: var(--text-muted); width: 28px; text-align: right; font-weight: 500; }
  .sug-item { border: 1px solid var(--border); border-radius: 12px; padding: 1rem 1.25rem; margin-bottom: 10px; }
  .sug-top { display: flex; justify-content: space-between; align-items: center; margin-bottom: 6px; }
  .sug-name { font-size: 14px; font-weight: 500; color: var(--text); }
  .sug-badge { font-size: 11px; font-weight: 500; padding: 3px 10px; border-radius: 20px; }
  .sug-tip { font-size: 13px; color: var(--text-muted); line-height: 1.65; }
  .retry-btn {
    width: 100%; padding: 14px; background: transparent;
    border: 1px solid rgba(0,0,0,0.15); border-radius: 12px;
    font-size: 14px; cursor: pointer; margin-top: 0.5rem; color: var(--text);
    font-family: 'DM Sans', sans-serif; transition: background 0.2s;
  }
  .retry-btn:hover { background: rgba(0,0,0,0.04); }
  .footer { text-align: center; margin-top: 2rem; font-size: 12px; color: var(--text-hint); }
</style>
</head>
<body>
<div class="app">
  <div class="header">
    <h1>ThriveMind</h1>
    <p>A personal mental health check-in — honest, private, and supportive.<br>Rate yourself across 10 key areas of wellbeing.</p>
  </div>

  <div id="quiz">
    <div class="progress-wrap">
      <div class="progress-bar"><div class="progress-fill" id="prog" style="width:0%"></div></div>
      <div class="progress-label" id="prog-label">Move sliders to begin</div>
    </div>
    <div id="questions"></div>
    <button class="submit-btn" onclick="showResult()">Analyze My Mental Health →</button>
  </div>

  <div class="result-wrap" id="result"></div>

  <div class="footer">ThriveMind &nbsp;·&nbsp; Built for AXIORA 2026 &nbsp;·&nbsp; Powered by AI</div>
</div>

<script>
const questions = [
  { label: "Emotional Stability", desc: "How steady is your mood daily?", low: "Wild swings", high: "Calm & steady",
    tips: ["Seek professional support — mood instability can be effectively treated.", "Try journaling your emotions daily to identify triggers and patterns.", "Practice 5-minute mindfulness when you feel a mood shift coming on.", "Notice what affects your mood and gently adjust your environment.", "You are doing brilliantly — keep using your emotional regulation tools."] },
  { label: "Sleep Quality", desc: "How refreshing is your sleep?", low: "Exhausted", high: "Energized",
    tips: ["Consult a doctor — chronic poor sleep needs proper medical attention.", "Set a fixed sleep and wake time every day, including weekends.", "Avoid screens 1 hour before bed and try reading a book instead.", "Keep your room cool, dark and quiet for deeper, more restful sleep.", "Excellent sleep hygiene — protect this routine and it will protect you."] },
  { label: "Social Connection", desc: "How supported do you feel?", low: "Deeply alone", high: "Truly understood",
    tips: ["Consider joining a support group or speaking with a counsellor soon.", "Reach out to one person today — even a simple text message counts.", "Schedule one social activity this week, no matter how small it is.", "Deepen one existing relationship by being more open and vulnerable.", "You feel genuinely connected — nurture these bonds regularly."] },
  { label: "Sense of Purpose", desc: "How meaningful is your direction?", low: "Empty", high: "Driven & aligned",
    tips: ["Talk to a life coach or therapist about finding your direction.", "Write down 3 small things you want to achieve this week.", "Try volunteering or a new hobby — purpose often comes from giving.", "Revisit your goals and break them into smaller, daily actionable steps.", "You have strong purpose — share it with others and inspire them."] },
  { label: "Anxiety Levels", desc: "How much worry consumes you?", low: "Constant anxiety", high: "Calm & clear",
    tips: ["Please speak with a mental health professional about your anxiety.", "Try box breathing: inhale 4s, hold 4s, exhale 4s, hold 4s. Repeat.", "Limit news and social media — they often amplify unnecessary worry.", "Write your worries down on paper and challenge each one with facts.", "Your calm mindset is a real asset — keep practicing this daily."] },
  { label: "Self-Talk", desc: "How kind is your inner voice?", low: "Harsh & critical", high: "Compassionate",
    tips: ["A therapist can genuinely help rewire deeply critical inner dialogue.", "When you catch a harsh thought, consciously replace it with a neutral one.", "Speak to yourself exactly as you would to a good, trusted friend.", "Start a daily self-compassion practice — even just 2 minutes helps greatly.", "Your inner voice is kind and warm — use it to uplift others around you."] },
  { label: "Focus & Clarity", desc: "How sharp is your concentration?", low: "Foggy & scattered", high: "Sustained & alert",
    tips: ["Persistent brain fog may need medical evaluation — please check.", "Try the Pomodoro method: 25 minutes focused work, 5 minutes break.", "Reduce multitasking deliberately — do one single thing at a time.", "Stay well hydrated and limit sugar — both directly impact your focus.", "Your sharp focus is powerful — protect it by guarding your time well."] },
  { label: "Physical Care", desc: "How well do you tend your body?", low: "Neglected", high: "Balanced & at ease",
    tips: ["Your body needs urgent care — start with just one small act today.", "Add a 10-minute daily walk outside — it shifts both body and mood.", "Prepare one genuinely healthy meal today and notice how it feels.", "Build a simple morning routine — stretch, hydrate, and eat breakfast.", "Excellent physical self-care — your body and mind are both thanking you."] },
  { label: "Stress Coping", desc: "How resilient are you to setbacks?", low: "Shutdown", high: "Strong recovery",
    tips: ["You may be burned out — please speak to someone you deeply trust.", "Identify your single top stressor and take one small action against it.", "Build a personal stress toolkit: music, walks, breathing, writing.", "Practice reframing setbacks as temporary, solvable, and educational.", "Your resilience is exceptional — consider teaching others what works for you."] },
  { label: "Future Hope", desc: "How optimistic is your outlook?", low: "Dark & helpless", high: "Bright & proactive",
    tips: ["Persistent hopelessness is serious — please reach out to a professional.", "Write down one small thing you are genuinely looking forward to this week.", "Limit time with pessimistic content or people who drain your energy.", "Celebrate small wins every single day — they build real, lasting optimism.", "Your positive outlook is truly contagious — keep dreaming boldly and big."] }
];

let scores = new Array(10).fill(5);

function updateSlider(i, v) {
  scores[i] = parseInt(v);
  document.getElementById('badge-' + i).textContent = v + '/10';
  const pct = ((v - 1) / 9 * 100).toFixed(1);
  document.getElementById('range-' + i).style.background =
    `linear-gradient(to right, #1D9E75 0%, #1D9E75 ${pct}%, rgba(0,0,0,0.1) ${pct}%)`;
  updateProgress();
}

function updateProgress() {
  const total = scores.reduce((a,b) => a+b, 0);
  const pct = Math.round((total - 10) / 90 * 100);
  document.getElementById('prog').style.width = pct + '%';
  document.getElementById('prog-label').textContent = pct + '% complete';
}

function getTip(score) {
  if (score <= 2) return 0;
  if (score <= 4) return 1;
  if (score <= 6) return 2;
  if (score <= 8) return 3;
  return 4;
}

function getBadgeLabel(score) {
  if (score <= 2) return ['Critical', '#791F1F', '#FCEBEB'];
  if (score <= 4) return ['Low', '#633806', '#FAEEDA'];
  if (score <= 6) return ['Moderate', '#3B6D11', '#EAF3DE'];
  if (score <= 8) return ['Good', '#0F6E56', '#E1F5EE'];
  return ['Excellent', '#085041', '#9FE1CB'];
}

function buildQuiz() {
  let html = '';
  questions.forEach((q, i) => {
    html += `<div class="question-card">
      <div class="q-meta">
        <span class="q-number">Question ${i+1} of ${questions.length}</span>
        <span class="q-val-badge" id="badge-${i}">5/10</span>
      </div>
      <div class="q-text">${q.label}</div>
      <div class="q-desc">${q.desc}</div>
      <input type="range" id="range-${i}" min="1" max="10" step="1" value="5"
        oninput="updateSlider(${i}, this.value)"
        style="background: linear-gradient(to right, #1D9E75 0%, #1D9E75 44.4%, rgba(0,0,0,0.1) 44.4%)">
      <div class="slider-labels"><span>${q.low}</span><span>${q.high}</span></div>
    </div>`;
  });
  document.getElementById('questions').innerHTML = html;
}

function showResult() {
  const total = scores.reduce((a,b) => a+b, 0);
  const score = Math.round((total / 100) * 100);

  const indexed = scores.map((s,i) => ({ s, label: questions[i].label }));
  const sorted = [...indexed].sort((a,b) => a.s - b.s);
  const weakAreas = sorted.slice(0,2).map(x => x.label);
  const strongAreas = sorted.slice(-2).reverse().map(x => x.label);

  let status, sColor, sBg, ringColor;
  if (score >= 80) { status = "Thriving"; sColor = "#085041"; sBg = "#E1F5EE"; ringColor = "#1D9E75"; }
  else if (score >= 60) { status = "Good"; sColor = "#0F6E56"; sBg = "#E1F5EE"; ringColor = "#1D9E75"; }
  else if (score >= 40) { status = "Needs Attention"; sColor = "#633806"; sBg = "#FAEEDA"; ringColor = "#BA7517"; }
  else if (score >= 20) { status = "Seek Support"; sColor = "#A32D2D"; sBg = "#FCEBEB"; ringColor = "#E24B4A"; }
  else { status = "Crisis Support Needed"; sColor = "#791F1F"; sBg = "#FCEBEB"; ringColor = "#E24B4A"; }

  let analysis = '';
  if (score >= 80) analysis = `Your overall wellbeing is strong, especially your <strong>${strongAreas[0]}</strong> and <strong>${strongAreas[1]}</strong>. To reach your full potential, give some focused attention to your <strong>${weakAreas[0]}</strong> and <strong>${weakAreas[1]}</strong> — even small improvements there will be meaningful.`;
  else if (score >= 60) analysis = `You are doing well. Your <strong>${strongAreas[0]}</strong> and <strong>${strongAreas[1]}</strong> are solid foundations. Giving consistent care to your <strong>${weakAreas[0]}</strong> and <strong>${weakAreas[1]}</strong> will noticeably improve how you feel day to day.`;
  else if (score >= 40) analysis = `You are managing, but your <strong>${weakAreas[0]}</strong> and <strong>${weakAreas[1]}</strong> are pulling your wellbeing down. Small daily actions in these areas will create real change. Lean on your stronger areas — <strong>${strongAreas[0]}</strong> and <strong>${strongAreas[1]}</strong> — for support.`;
  else if (score >= 20) analysis = `Your <strong>${weakAreas[0]}</strong> and <strong>${weakAreas[1]}</strong> are significantly affecting your quality of life. Please lean on your <strong>${strongAreas[0]}</strong> as an anchor while you seek proper support. You deserve care.`;
  else analysis = `You are going through something very difficult right now. Your <strong>${weakAreas[0]}</strong> and <strong>${weakAreas[1]}</strong> need urgent attention. Please reach out to a mental health professional or someone you trust today — you do not have to carry this alone.`;

  const barsHtml = questions.map((q,i) => {
    const pct = scores[i] * 10;
    const c = scores[i] >= 7 ? '#1D9E75' : scores[i] >= 4 ? '#BA7517' : '#E24B4A';
    return `<div class="bar-row">
      <div class="bar-name">${q.label}</div>
      <div class="bar-track"><div class="bar-fill" style="width:${pct}%;background:${c}"></div></div>
      <div class="bar-score">${scores[i]}/10</div>
    </div>`;
  }).join('');

  const sugsHtml = questions.map((q,i) => {
    const [label, color, bg] = getBadgeLabel(scores[i]);
    const tip = q.tips[getTip(scores[i])];
    return `<div class="sug-item">
      <div class="sug-top">
        <span class="sug-name">${q.label}</span>
        <span class="sug-badge" style="background:${bg};color:${color}">${scores[i]}/10 — ${label}</span>
      </div>
      <div class="sug-tip">${tip}</div>
    </div>`;
  }).join('');

  document.getElementById('quiz').style.display = 'none';
  const res = document.getElementById('result');
  res.style.display = 'block';
  res.innerHTML = `
    <div class="score-hero">
      <div class="score-ring" style="border-color:${ringColor};background:${sBg}">
        <span class="score-num" style="color:${sColor}">${score}</span>
        <span class="score-denom">out of 100</span>
      </div>
      <span class="status-pill" style="background:${sBg};color:${sColor}">${status}</span>
      <p class="analysis-text">${analysis}</p>
    </div>
    <div class="section">
      <div class="section-title">Your breakdown</div>
      ${barsHtml}
    </div>
    <div class="section">
      <div class="section-title">Personalized suggestions</div>
      ${sugsHtml}
    </div>
    <button class="retry-btn" onclick="retake()">↩ Retake assessment</button>`;
}

function retake() {
  scores = new Array(10).fill(5);
  document.getElementById('result').style.display = 'none';
  document.getElementById('quiz').style.display = 'block';
  buildQuiz();
  updateProgress();
}

buildQuiz();
</script>
</body>
</html>
