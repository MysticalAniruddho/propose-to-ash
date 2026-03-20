# propose-to-ash
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Senior, do you like me?</title>

  <!-- Google Fonts: Inter (UI) and Playfair Display (heading) -->
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;700&family=Playfair+Display:wght@400;700&display=swap" rel="stylesheet">

  <!-- Theme color for mobile browsers -->
  <meta name="theme-color" content="#0a0a0a">

  <style>
    /* Base and variables */
    :root{
      --bg-deep: #0a0a0a; /* primary background */
      --card-bg: rgba(255,255,255,0.04);
      --glass-border: rgba(255,255,255,0.06);
      --accent: #e33b3b; /* rose red */
      --accent-deep: #bf2a2a;
      --muted: rgba(255,255,255,0.65);
      --glass-blur: 10px;
      --radius: 16px;
      --shadow: 0 6px 30px rgba(0,0,0,0.6);
      --transition: 280ms cubic-bezier(.2,.9,.3,1);
    }

    /* Page reset */
    *{box-sizing:border-box}
    html,body{height:100%}
    body{
      margin:0;
      font-family: "Inter", system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial;
      background: linear-gradient(180deg, rgba(255,10,20,0.02) 0%, rgba(255,8,8,0.02) 100%), var(--bg-deep);
      color: #fff;
      -webkit-font-smoothing:antialiased;
      -moz-osx-font-smoothing:grayscale;
      display:grid;
      place-items:center;
      padding:28px;
      /* decorative rose SVG background (subtle, repeating, low-opacity) */
      background-image:
        radial-gradient(circle at 20% 10%, rgba(227,59,59,0.06), transparent 12%),
        radial-gradient(circle at 85% 80%, rgba(227,59,59,0.04), transparent 12%),
        url('data:image/svg+xml;utf8,\
          <svg xmlns="http://www.w3.org/2000/svg" width="800" height="800" viewBox="0 0 800 800">\
            <defs>\
              <linearGradient id="g" x1="0" x2="1">\
                <stop offset="0" stop-color="%23ff4d4d" stop-opacity="0.12" />\
                <stop offset="1" stop-color="%23a80000" stop-opacity="0.06" />\
              </linearGradient>\
            </defs>\
            <g opacity="0.12" transform="translate(100,100) scale(0.9)">\
              <path fill="url(%23g)" d="M200 20c30 10 50 45 38 74-12 28-33 37-45 56-12 19-6 38 2 59 8 21 11 50-10 62-21 12-64-6-95-18-31-12-64-20-82-46-18-26-17-62 2-89 19-27 49-45 79-63 30-18 68-40 113-35z"/>\
            </g>\
          </svg>');
      background-repeat: no-repeat;
      background-position: center;
      background-size: cover;
      min-height:100vh;
    }

    /* Centered card */
    .card {
      width: min(720px, 96vw);
      max-width:720px;
      background: linear-gradient(180deg, rgba(255,255,255,0.03), rgba(255,255,255,0.015));
      border-radius: var(--radius);
      padding: clamp(20px, 4vw, 36px);
      box-shadow: var(--shadow);
      border: 1px solid var(--glass-border);
      backdrop-filter: blur(var(--glass-blur));
      display:flex;
      gap:18px;
      align-items:center;
      flex-direction:column;
      text-align:center;
      transition: transform var(--transition), box-shadow var(--transition);
    }

    /* small decorative top accent line */
    .rose-badge {
      display:flex;
      align-items:center;
      gap:10px;
      margin-top:-8px;
    }
    .rose-emoji {
      font-size:36px;
      filter: drop-shadow(0 4px 10px rgba(227,59,59,0.15));
      transform: translateY(0);
      transition: transform 360ms ease;
    }
    .card:hover .rose-emoji{ transform: translateY(-4px) }

    h1 {
      font-family: "Playfair Display", serif;
      font-weight:700;
      letter-spacing:-0.6px;
      color: #fff;
      margin:6px 0 0 0;
      font-size: clamp(20px, 4.5vw, 38px);
      text-shadow: 0 6px 24px rgba(163,18,18,0.15);
    }

    p.instruction {
      margin:10px 0 20px 0;
      color: var(--muted);
      font-size:14px;
      max-width:640px;
    }

    /* button row */
    .actions {
      display:flex;
      gap:12px;
      width:100%;
      justify-content:center;
      flex-wrap:wrap;
    }

    button.btn {
      -webkit-appearance:none;
      border: none;
      padding: 12px 20px;
      border-radius: 12px;
      font-weight:600;
      cursor:pointer;
      font-size:15px;
      transition: transform var(--transition), box-shadow var(--transition), opacity var(--transition);
      display:inline-flex;
      align-items:center;
      gap:10px;
      min-width:140px;
      justify-content:center;
    }

    /* Primary (Yes) */
    .btn-primary {
      background: linear-gradient(180deg, var(--accent) 0%, var(--accent-deep) 100%);
      color: white;
      box-shadow: 0 8px 24px rgba(195,34,34,0.28), inset 0 -2px 6px rgba(0,0,0,0.12);
    }
    .btn-primary:active{ transform: translateY(2px) scale(0.998) }

    /* Secondary (No) */
    .btn-ghost {
      background: rgba(255,255,255,0.03);
      color: var(--muted);
      border: 1px solid rgba(255,255,255,0.04);
      box-shadow: 0 6px 18px rgba(0,0,0,0.4);
    }
    .btn-ghost:hover{ transform: translateY(-3px) }

    button[disabled]{
      opacity:0.5;
      cursor:not-    .response {
      margin-top:12px;
      min-height:56px;
      display:flex;
      align-items:center;
      justify-content:center;
      color:var(--muted);
      font-size:16px;
      padding:10px 14px;
      border-radius:10px;
      width:100%;
      max-width:620px;
    }
    .response .text {
      transition: opacity var(--transition), transform var(--transition);
      display:inline-block;
    }

    /* sweet message styles */
    .sweet {
      color: #ffeef0;
      background: linear-gradient(90deg, rgba(227,59,59,0.12), rgba(255,135,135,0.03));
      border: 1px solid rgba0.08);
      box-shadow: 0 8px 30px rgba(227,59,59,0.06);
    }

    .gentle {
      color: #fff9f9;
      background: linear-gradient(90deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));
      border: 1px solid rgba(255,255,255,0.03);
    }

    /* subtle "No" animation */
    .gentle .text {
      animation: soft-breath 2200ms ease forwards;
    }
    @keyframes soft-breath {
      0% { transform: scale(0.995); opacity:0 }
      60% { transform: scale(1.01); opacity:1 }
      100% { transform: scale(1); opacity:1 }
    }

    /* Reset link */
    .reset {
      margin-top:10px;
      font-size:13px;
      color: var(--muted);
      text-decoration:underline;
      cursor:pointer;
    }
    .reset:hover{ color: #fff }

    /* footer small note */
    .note {
      font-size:12px;
      color: rgba(255,255,255,0.45);
      margin-top:8px;
    }

    /* responsiveness */
    @media (max-width:520px){
      .card{ padding:20px; border-radius:14px }
      .rose-emoji{ font-size:30px }
      button.btn{ min-width:120px; padding:10px 14px }
    }
  </style>
</head>
<body>
  <main class="card" role="main" aria-labelledby="title">
    <!-- Rose badge with emoji -->
    <div class="rose-badge" aria-hidden="true">
      <div class="rose-emoji" title="rose">🌹</div>
    </div>

    <!-- Main heading -->
    <h1 id="title">Senior, do you like me?</h1>

    <!-- instruction: the answer will be sent to the creator -->
    <p class="instruction">Please choose your answer below. Your response will be sent to the creator (Formspree placeholder endpoint). You can reset the UI after submitting to answer again locally.</p>

    <!-- Action buttons -->
    <div class="actions" role="group" aria-label="answer choices">
      <button id="yesBtn" class="btn btn-primary" aria-describedby="note" type="button">
        Yes, I do
      </button>

      <button id="noBtn" class="btn btn-ghost" aria-describedby="note" type="button">
        Not yet...
      </button>
    </div>

    <!-- Response / feedback area -->
    <div id="response" class="response" aria-live="polite" aria-atomic="true">
      <span class="text" id="responseText" style="opacity:0">Waiting for your answer 💌</span>
    </div>

    <!-- small reset link -->
    <div class="reset" id="resetLink" role="button" tabindex="0" aria-hidden="false">Ask again</div>

    <div class="note" id="note">Your answer will be submitted to: formspree (placeholder)</div>
  </main>

  <!-- canvas-confetti CDN (browser build) -->
  <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>

  <script>
    // GitHub Copilot Chat Assistant: single-file romantic responder
    // Formspree endpoint (placeholder). The user provided this endpoint:
    // https://formspree.io/f/mkoqenak
    // If you want to use your own, replace the URL below with your form endpoint.
    const FORMSPREE_ENDPOINT = 'https://formspree.io/f/mkoqenak';

    // UI elements
    const yesBtn = document.getElementById('yesBtn');
    const noBtn = document.getElementById('noBtn');
    const response = document.getElementById('response');
    const responseText = document.getElementById('responseText');
    const resetLink = document.getElementById('resetLink');

    // Helper: disables/enables buttons
    function setButtonsDisabled(disabled = true) {
      yesBtn.disabled = disabled;
      noBtn.disabled = disabled;
    }

    // Helper: update response area with optional style class
    function showResponse(message, styleClass = '', live = true) {
      response.classList.remove('sweet', 'gentle');
      if (styleClass) response.classList.add(styleClass);

      // small animation
      responseText.style.opacity = 0;
      responseText.style.transform = 'translateY(6px)';
      setTimeout(() => {
        responseText.textContent = message;
        responseText.style.opacity = 1;
        responseText.style.transform = 'translateY(0)';
      }, 80);
    }

    // Send result to Formspree
    async function sendAnswer(answer) {
      // Prepare payload. Formspree accepts application/json for the form endpoint.
      const payload = {
        // Example fields: sender could be added if desired
        answer: answer,
        page: location.href,
        timestamp: new Date().toISOString()
      };

      try {
        const res = await fetch(FORMSPREE_ENDPOINT, {
          method: 'POST',
          headers: {
            'Content-Type': 'application/json',
            'Accept': 'application/json'
          },
          body: JSON.stringify(payload)
        });

        if (!res.ok) {
          // Non-200 from the endpoint
          const text = await res.text().catch(()=>null);
          throw new Error('Non-OK response: ' + (text || res.status));
        }

        // Success: return parsed JSON (if any)
        const json = await res.json().catch(()=>null);
        return { ok: true, data: json };
      } catch (err) {
        // Network or parsing error
        return { ok: false, error: err };
      }
    }

    // Confetti effect for Yes
    function triggerConfetti() {
      // Use canvas-confetti to make a romantic burst
      // Basic burst
      confetti({
        particleCount: 40,
        startVelocity: 26,
        spread: 80,
        origin: { x: 0.5, y: 0.35 },
        colors: ['#ff6b6b','#ff4757','#ff9aa2','#ffd6d6']
      });

      // small shaped extra bursts
      setTimeout(() => confetti({
        particleCount: 24,
        startVelocity: 20,
        spread: 60,
        origin: { x: 0.35, y: 0.25 },
        colors: ['#ff6b6b','#ff4757']
      }), 160);

      setTimeout(() => confetti({
        particleCount: 24,
        startVelocity: 20,
        spread: 60,
        origin: { x: 0.65, y: 0.25 },
        colors: ['#ff9aa2','#ffd6d6']
      }), 220);
    }

    // Handler for "Yes" click
    yesBtn.addEventListener('click', async () => {
      // disable to prevent multiple submissions
      setButtonsDisabled(true);

      // Immediate sweet UI feedback
      showResponse('Aww, that makes me so happy! 💕 Thank you — your warmth means a lot.', 'sweet');

      // trigger confetti animation
      try { triggerConfetti(); } catch(e) {/* fail silently if confetti fails */}

      // send to Formspree
      const result = await sendAnswer('Yes');

      if (!result.ok) {
        // fallback messaging if network error / non-OK
        showResponse('Saved locally: your "Yes" was recorded visually. (Submission failed — try again later.)', 'sweet');
        console.error('Formspree submit error:', result.error);
      } else {
        // success message update (keep sweet)
        showResponse('Your "Yes" has been sent to the creator. Thank you for being kind! 💌', 'sweet');
      }
    });

    // Handler for "No" click (gentle)
    noBtn.addEventListener('click', async () => {
      setButtonsDisabled(true);

      // gentle, kind reply with a soft animation
      showResponse('That’s okay — thank you for your honesty. Wishing you all the best. 🌱', 'gentle');

      // subtle gentle pulse on the card to indicate acknowledgement
      const card = document.querySelector('.card');
      card.style.transition = 'transform 320ms ease';
      card.style.transform = 'scale(1.01)';
      setTimeout(()=> card.style.transform = 'scale(1)', 320);

      // send to Formspree
      const result = await sendAnswer('No');

      if (!result.ok) {
        // fallback message
        showResponse('Response acknowledged locally. (Submission failed — try again later.)', 'gentle');
        console.error('Formspree submit error:', result.error);
      } else {
        showResponse('Your response has been sent gently to the creator. Thank you. 🌷', 'gentle');
      }
    });

    // Reset link: restores UI for another local try (note: submission already sent)
    function resetUI() {
      setButtonsDisabled(false);
      response.classList.remove('sweet','gentle');
      responseText.textContent = 'Waiting for your answer 💌';
      responseText.style.opacity = 1;
    }

    resetLink.addEventListener('click', resetUI);
    resetLink.addEventListener('keypress', (e) => {
      if (e.key === 'Enter' || e.key === ' ') {
        e.preventDefault();
        resetUI();
      }
    });

    // Initialize visible state
    (function init(){
      responseText.style.opacity = 1;
      responseText.textContent = 'Waiting for your answer 💌';
    })();
  </script>
</body>
</html>