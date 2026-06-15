<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>XRP · Start Here</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Bricolage+Grotesque:opsz,wght@12..96,500;12..96,700;12..96,800&family=Inter:wght@400;500;600&family=JetBrains+Mono:wght@400;500;700&display=swap" rel="stylesheet">
<style>
  :root{
    --ink:#15203A;
    --paper:#F7F8FB;
    --panel:#FFFFFF;
    --signal:#F4642A;
    --signal-dark:#D44E18;
    --cyan:#137F8E;
    --cyan-soft:#E5F4F6;
    --line:#E2E6EF;
    --muted:#5A6378;
    --done:#2C9A63;
    --code-bg:#161F33;
    --code-ink:#E8ECF6;
    --warn-bg:#FFF3E9;
    --display:'Bricolage Grotesque',-apple-system,system-ui,sans-serif;
    --body:'Inter',-apple-system,system-ui,sans-serif;
    --mono:'JetBrains Mono',ui-monospace,SFMono-Regular,Menlo,monospace;
  }
  *{box-sizing:border-box}
  html{-webkit-text-size-adjust:100%}
  body{
    margin:0;background:var(--paper);color:var(--ink);
    font-family:var(--body);line-height:1.6;
    -webkit-font-smoothing:antialiased;
  }
  .wrap{max-width:900px;margin:0 auto;padding:0 20px 120px}

  /* ---------- top bar ---------- */
  .topbar{
    position:sticky;top:0;z-index:50;
    background:rgba(247,248,251,.86);backdrop-filter:blur(10px);
    border-bottom:1px solid var(--line);
  }
  .topbar .wrap{padding-top:14px;padding-bottom:14px;display:flex;align-items:center;gap:16px;flex-wrap:wrap}
  .brand{display:flex;align-items:center;gap:12px;margin-right:auto}
  .bot{width:42px;height:42px;flex:none}
  .brand h1{font-family:var(--display);font-weight:800;font-size:1.15rem;margin:0;letter-spacing:-.01em}
  .brand p{margin:0;font-size:.72rem;color:var(--muted);letter-spacing:.04em;text-transform:uppercase}
  .progress-mini{display:flex;align-items:center;gap:10px;font-size:.8rem;color:var(--muted)}
  .bar{width:120px;height:8px;border-radius:99px;background:var(--line);overflow:hidden}
  .bar>span{display:block;height:100%;width:0;background:linear-gradient(90deg,var(--cyan),var(--signal));transition:width .4s ease}

  /* ---------- hero ---------- */
  .hero{padding:54px 0 26px}
  .eyebrow{font-family:var(--mono);font-size:.74rem;letter-spacing:.18em;text-transform:uppercase;color:var(--signal-dark);font-weight:700}
  .hero h2{font-family:var(--display);font-weight:800;font-size:clamp(2rem,6vw,3.1rem);line-height:1.04;letter-spacing:-.02em;margin:.4em 0 .35em}
  .hero h2 em{font-style:normal;color:var(--signal)}
  .hero p{font-size:1.05rem;color:var(--muted);max-width:60ch;margin:0}
  .note-path{margin-top:22px;border:1px solid var(--line);background:var(--panel);border-radius:14px;padding:14px 16px;font-size:.9rem;display:flex;gap:12px;align-items:flex-start}
  .note-path b{color:var(--ink)}
  .note-path .dot{width:10px;height:10px;border-radius:99px;background:var(--cyan);margin-top:6px;flex:none}

  /* ---------- board picker ---------- */
  .picker{margin:30px 0 8px;border:1px solid var(--line);background:var(--panel);border-radius:16px;padding:20px}
  .picker h3{font-family:var(--display);font-weight:700;font-size:1rem;margin:0 0 4px}
  .picker .sub{font-size:.85rem;color:var(--muted);margin:0 0 14px}
  .seg{display:inline-flex;background:var(--paper);border:1px solid var(--line);border-radius:12px;padding:4px;gap:4px;flex-wrap:wrap}
  .seg button{
    font-family:var(--body);font-weight:600;font-size:.86rem;border:0;cursor:pointer;
    background:transparent;color:var(--muted);padding:9px 14px;border-radius:9px;transition:.18s;
  }
  .seg button.on{background:var(--ink);color:#fff}
  .picker .hint{margin:13px 0 0;font-size:.83rem;color:var(--muted)}
  .picker .hint a{color:var(--cyan)}
  .chip{display:inline-block;font-family:var(--mono);font-size:.78rem;background:var(--cyan-soft);color:var(--cyan);padding:2px 8px;border-radius:6px;font-weight:500}

  /* ---------- tabs ---------- */
  .tabs{position:sticky;top:71px;z-index:40;display:flex;gap:8px;padding:14px 0;background:var(--paper)}
  .tab{
    flex:1;font-family:var(--display);font-weight:700;font-size:.98rem;cursor:pointer;
    border:1px solid var(--line);background:var(--panel);color:var(--muted);
    border-radius:13px;padding:14px 16px;text-align:left;transition:.18s;line-height:1.2;
  }
  .tab small{display:block;font-family:var(--body);font-weight:500;font-size:.74rem;color:var(--muted);margin-top:3px}
  .tab.on{border-color:var(--ink);color:var(--ink);box-shadow:0 1px 0 var(--ink)}
  .tab.on .num{color:var(--signal)}
  .tab .num{font-family:var(--mono);color:var(--muted)}

  .panel-view{display:none;animation:rise .3s ease}
  .panel-view.on{display:block}
  @keyframes rise{from{opacity:0;transform:translateY(6px)}to{opacity:1;transform:none}}

  /* ---------- steps ---------- */
  .step{border:1px solid var(--line);background:var(--panel);border-radius:16px;margin:14px 0;overflow:hidden}
  .step.done{border-color:#BfE5CF}
  .step-head{display:flex;align-items:flex-start;gap:14px;padding:18px;cursor:pointer;user-select:none}
  .ck{
    width:26px;height:26px;border-radius:8px;border:2px solid var(--line);flex:none;margin-top:1px;
    display:grid;place-items:center;transition:.18s;background:#fff;color:#fff;font-size:14px;
  }
  .step.done .ck{background:var(--done);border-color:var(--done)}
  .step-head h3{font-family:var(--display);font-weight:700;font-size:1.08rem;margin:0;flex:1;letter-spacing:-.01em}
  .idx{font-family:var(--mono);font-size:.8rem;color:var(--signal-dark);font-weight:700;margin-right:2px}
  .caret{color:var(--muted);transition:.2s;flex:none;margin-top:3px}
  .step.open .caret{transform:rotate(180deg)}
  .step-body{display:none;padding:0 18px 20px 58px}
  .step.open .step-body{display:block}
  .step-body p{margin:.2em 0 .8em}
  .step-body ul{margin:.3em 0 .9em;padding-left:1.1em}
  .step-body li{margin:.3em 0}
  .kbd{font-family:var(--mono);font-size:.82rem;background:#EEF0F6;border:1px solid var(--line);border-bottom-width:2px;border-radius:6px;padding:1px 6px}
  a{color:var(--cyan-dark,var(--cyan));text-decoration:none;border-bottom:1px solid currentColor;padding-bottom:1px}
  a:hover{color:var(--signal)}

  /* contextual board text */
  [data-board]{display:none}
  [data-board].show{display:inline}
  .blk[data-board]{display:none}
  .blk[data-board].show{display:block}

  /* callouts */
  .call{border-radius:12px;padding:13px 15px;font-size:.88rem;margin:.6em 0 1em}
  .call b{display:block;font-family:var(--display);font-weight:700;margin-bottom:2px}
  .call.fix{background:var(--warn-bg);border:1px solid #F6C79E}
  .call.fix b{color:var(--signal-dark)}
  .call.tip{background:var(--cyan-soft);border:1px solid #BfE2E8}
  .call.tip b{color:var(--cyan)}

  /* ---------- lessons / code ---------- */
  .lesson{border:1px solid var(--line);background:var(--panel);border-radius:16px;padding:20px;margin:14px 0}
  .lesson .lh{display:flex;align-items:baseline;gap:10px;margin-bottom:6px}
  .lesson .lh .idx{font-size:.85rem}
  .lesson h3{font-family:var(--display);font-weight:700;font-size:1.15rem;margin:0;letter-spacing:-.01em}
  .lesson p{margin:.4em 0 .8em}
  .codewrap{position:relative;margin:.7em 0}
  pre{background:var(--code-bg);color:var(--code-ink);border-radius:12px;padding:16px 16px;margin:0;overflow-x:auto;font-family:var(--mono);font-size:.83rem;line-height:1.65}
  pre .c{color:#7E89A6}
  pre .k{color:#FF9B6A}
  pre .s{color:#8FD0A6}
  pre .f{color:#7FC7D9}
  .copy{
    position:absolute;top:9px;right:9px;font-family:var(--mono);font-size:.72rem;
    background:#26314C;color:#cfd6e8;border:1px solid #38456a;border-radius:7px;
    padding:5px 9px;cursor:pointer;transition:.15s
  }
  .copy:hover{background:#2f3c5c;color:#fff}
  .expect{font-size:.85rem;color:var(--muted);display:flex;gap:8px;align-items:flex-start;margin-top:6px}
  .expect .eye{color:var(--signal)}

  .sectiontitle{font-family:var(--display);font-weight:800;font-size:1.4rem;margin:34px 0 4px;letter-spacing:-.01em}
  .sectionsub{color:var(--muted);font-size:.92rem;margin:0 0 6px}

  footer{margin-top:50px;padding-top:24px;border-top:1px solid var(--line);font-size:.82rem;color:var(--muted)}
  footer a{color:var(--cyan)}
  .links{display:flex;flex-wrap:wrap;gap:8px 18px;margin:10px 0 0;padding:0;list-style:none}

  @media (max-width:560px){
    .tabs{flex-direction:column;top:67px}
    .step-body{padding-left:18px}
    .progress-mini .label{display:none}
  }
  .ideas{display:grid;grid-template-columns:repeat(auto-fill,minmax(220px,1fr));gap:12px;margin:.7em 0 .3em}
  .idea{border:1px solid var(--line);border-radius:12px;padding:14px 15px;background:var(--paper)}
  .idea h4{font-family:var(--display);font-weight:700;font-size:.96rem;margin:5px 0 4px;letter-spacing:-.01em}
  .idea p{margin:0;font-size:.83rem;color:var(--muted)}
  .diff{font-family:var(--mono);font-size:.66rem;letter-spacing:.1em;text-transform:uppercase;font-weight:700}
  .diff.e{color:var(--done)} .diff.m{color:var(--cyan)} .diff.h{color:var(--signal-dark)}
  .makeit{font-size:.85rem;color:var(--ink);background:var(--cyan-soft);border-left:3px solid var(--cyan);border-radius:0 8px 8px 0;padding:9px 13px;margin:.7em 0 0}
  .makeit b{font-family:var(--display)}
  @media (prefers-reduced-motion:reduce){*{animation:none!important;transition:none!important}}
</style>
</head>
<body>

<div class="topbar">
  <div class="wrap">
    <div class="brand">
      <svg class="bot" id="botface" viewBox="0 0 44 44" aria-hidden="true">
        <rect x="6" y="11" width="32" height="24" rx="7" fill="#15203A"/>
        <rect x="11" y="17" width="22" height="9" rx="4" fill="#222F4D"/>
        <circle id="eyeL" cx="17" cy="21.5" r="2.6" fill="#F4642A"/>
        <circle id="eyeR" cx="27" cy="21.5" r="2.6" fill="#F4642A"/>
        <rect x="18" y="6" width="8" height="5" rx="2" fill="#15203A"/>
        <circle id="topled" cx="22" cy="5" r="2.4" fill="#5A6378"/>
        <rect x="3" y="20" width="3" height="8" rx="1.5" fill="#15203A"/>
        <rect x="38" y="20" width="3" height="8" rx="1.5" fill="#15203A"/>
      </svg>
      <div>
        <h1>XRP · Start Here</h1>
        <p id="status">Powered off</p>
      </div>
    </div>
    <div class="progress-mini">
      <span class="label" id="ptext">0 / 6 setup steps</span>
      <div class="bar"><span id="pfill"></span></div>
    </div>
  </div>
</div>

<div class="wrap">

  <section class="hero">
    <div class="eyebrow">First-time guide · no experience needed</div>
    <h2>Get your XRP <em>running</em>,<br>then teach it to <em>move</em>.</h2>
    <p>A start-to-finish path: power it on, connect it to your computer, run your first program — then work up to driving it with a game controller. Every tricky spot has a "stuck? do this" note built right in.</p>

    <div class="note-path">
      <span class="dot"></span>
      <div>This guide uses <b>XRPCode + Python</b> — the friendliest path for first-timers, and it runs in your browser with nothing to install. If you're on an <b>FIRST FRC team coding in Java/C++</b>, you'll want the <a href="https://docs.wpilib.org/en/stable/docs/xrp-robot/index.html" target="_blank" rel="noopener">WPILib path</a> instead.</div>
    </div>
  </section>

  <section class="picker">
    <h3>First: which board do you have?</h3>
    <p class="sub">It changes which cable you need and which firmware is correct — the #1 source of "why won't it connect."</p>
    <div class="seg" role="group" aria-label="Board version">
      <button class="on" data-set="xrp" onclick="setBoard('xrp')">XRP (RP2350) — current</button>
      <button data-set="beta" onclick="setBoard('beta')">XRP Beta (Pico W)</button>
    </div>
    <p class="hint">
      <span class="blk show" data-board="xrp">You have the <b>current XRP</b> if the controller board has no separate green board plugged on top. It uses a <span class="chip">USB-C</span> cable.</span>
      <span class="blk" data-board="beta">You have the <b>Beta</b> if there's a separate green <b>Raspberry Pi Pico W</b> board piggybacked on the controller. It uses a <span class="chip">Micro-USB</span> cable.</span>
      &nbsp;Not sure? <a href="https://docs.wpilib.org/en/stable/docs/xrp-robot/hardware-and-imaging.html" target="_blank" rel="noopener">Compare the two boards here.</a>
    </p>
  </section>

  <div class="tabs">
    <button class="tab on" id="tab-setup" onclick="showTab('setup')"><span class="num">01</span> Set up your XRP<small>From box to first blink</small></button>
    <button class="tab" id="tab-code" onclick="showTab('code')"><span class="num">02</span> Learn to code it<small>Drive, sense, and use a controller</small></button>
    <button class="tab" id="tab-build" onclick="showTab('build')"><span class="num">03</span> Build something<small>Projects to remix into your own</small></button>
    <button class="tab" id="tab-print" onclick="showTab('print')"><span class="num">04</span> Print &amp; customize<small>3D-printed add-ons to dream up</small></button>
  </div>

  <!-- ============ SETUP ============ -->
  <section class="panel-view on" id="view-setup">

    <div class="step open" data-step>
      <div class="step-head" onclick="toggle(this)">
        <div class="ck" onclick="check(event,this)">✓</div>
        <h3><span class="idx">00</span> Gather your gear</h3>
        <svg class="caret" width="18" height="18" viewBox="0 0 24 24" fill="none"><path d="M6 9l6 6 6-6" stroke="currentColor" stroke-width="2.2" stroke-linecap="round"/></svg>
      </div>
      <div class="step-body">
        <ul>
          <li>An <b>assembled XRP</b> with the arm mounted on its servo.</li>
          <li><span class="blk show" data-board="xrp">A <b>USB-C data cable</b>.</span><span class="blk" data-board="beta">A <b>Micro-USB data cable</b>.</span> It must be a <b>data</b> cable, not a charge-only one — this trips people up constantly.</li>
          <li><b>4 AA batteries</b> (rechargeable are ideal — grab a charger too).</li>
          <li>A computer running <b>Google Chrome or Microsoft Edge</b>. XRPCode needs one of these — Safari and Firefox won't connect.</li>
        </ul>
        <div class="call tip"><b>Why batteries AND a cable?</b>The USB cable powers the robot's brain so you can program it, but the <b>motors only run on battery power</b>. No batteries = code runs, robot sits still.</div>
      </div>
    </div>

    <div class="step" data-step>
      <div class="step-head" onclick="toggle(this)">
        <div class="ck" onclick="check(event,this)">✓</div>
        <h3><span class="idx">01</span> Power it on</h3>
        <svg class="caret" width="18" height="18" viewBox="0 0 24 24" fill="none"><path d="M6 9l6 6 6-6" stroke="currentColor" stroke-width="2.2" stroke-linecap="round"/></svg>
      </div>
      <div class="step-body">
        <p>Put 4 AA batteries in the holder, set the robot on a <b>flat surface</b>, and slide the power switch to on. A <b>red power LED</b> lights up.</p>
        <p>For the next few seconds the robot's motion sensor calibrates itself — you'll see a <b>green LED blinking quickly</b>. Leave it still on the flat surface until that settles.</p>
        <div class="call fix"><b>Stuck?</b> If the green LED never settles or the robot acts confused later, press the <span class="kbd">reset</span> button while it sits flat — that re-runs the calibration.</div>
      </div>
    </div>

    <div class="step" data-step>
      <div class="step-head" onclick="toggle(this)">
        <div class="ck" onclick="check(event,this)">✓</div>
        <h3><span class="idx">02</span> Plug it into your computer</h3>
        <svg class="caret" width="18" height="18" viewBox="0 0 24 24" fill="none"><path d="M6 9l6 6 6-6" stroke="currentColor" stroke-width="2.2" stroke-linecap="round"/></svg>
      </div>
      <div class="step-body">
        <p>Connect the XRP to your computer with the <span class="blk show" data-board="xrp">USB-C</span><span class="blk" data-board="beta">Micro-USB</span> cable. Keep the power switch on.</p>
        <div class="call fix"><b>Stuck?</b> If the computer doesn't seem to notice it at all, your cable is almost certainly charge-only. Swap to a different cable (and ideally a different USB port) before anything else.</div>
      </div>
    </div>

    <div class="step" data-step>
      <div class="step-head" onclick="toggle(this)">
        <div class="ck" onclick="check(event,this)">✓</div>
        <h3><span class="idx">03</span> Open XRPCode &amp; connect</h3>
        <svg class="caret" width="18" height="18" viewBox="0 0 24 24" fill="none"><path d="M6 9l6 6 6-6" stroke="currentColor" stroke-width="2.2" stroke-linecap="round"/></svg>
      </div>
      <div class="step-body">
        <p>In Chrome or Edge, go to <a href="https://xrpcode.wpi.edu/" target="_blank" rel="noopener">xrpcode.wpi.edu</a>. Click <b>Connect</b>, and when the browser pops up a list of devices, pick the XRP's serial port and confirm.</p>
        <div class="call fix"><b>Nothing in the device list?</b><ul style="margin:.4em 0 0">
          <li>Make sure you're in <b>Chrome or Edge</b> — other browsers can't do this.</li>
          <li>Close any other tab or program that might be holding the port (a second XRPCode tab will block it).</li>
          <li>Re-seat the cable, then click Connect again.</li>
        </ul></div>
      </div>
    </div>

    <div class="step" data-step>
      <div class="step-head" onclick="toggle(this)">
        <div class="ck" onclick="check(event,this)">✓</div>
        <h3><span class="idx">04</span> Let it update firmware &amp; library</h3>
        <svg class="caret" width="18" height="18" viewBox="0 0 24 24" fill="none"><path d="M6 9l6 6 6-6" stroke="currentColor" stroke-width="2.2" stroke-linecap="round"/></svg>
      </div>
      <div class="step-body">
        <p>On the first connection, XRPCode checks the robot and usually <b>prompts you to update MicroPython and the XRPLib library</b>. Say yes and let each finish — this is XRPCode handling the firmware for you, so you rarely have to flash anything by hand. It automatically picks the right firmware for your <span class="blk show" data-board="xrp">current XRP board.</span><span class="blk" data-board="beta">Beta board.</span></p>
        <div class="call fix"><b>If a manual flash is ever needed</b> (rare): unplug, hold the white <span class="kbd">BOOTSEL</span> button while tapping <span class="kbd">reset</span>, and an <b>RPI-RP2</b> drive appears. Use XRPCode's built-in firmware menu to load the matching MicroPython file — and make sure it's the version for your <span class="blk show" data-board="xrp">non-beta board</span><span class="blk" data-board="beta">beta board</span>, since mismatched firmware is a classic "it connects but acts broken" cause.</div>
      </div>
    </div>

    <div class="step" data-step>
      <div class="step-head" onclick="toggle(this)">
        <div class="ck" onclick="check(event,this)">✓</div>
        <h3><span class="idx">05</span> Run your first program</h3>
        <svg class="caret" width="18" height="18" viewBox="0 0 24 24" fill="none"><path d="M6 9l6 6 6-6" stroke="currentColor" stroke-width="2.2" stroke-linecap="round"/></svg>
      </div>
      <div class="step-body">
        <p>Paste this into a new file in XRPCode and press <b>Run</b>. If the onboard LED blinks, everything works — your XRP is alive and you're ready for the coding track.</p>
        <div class="codewrap">
          <button class="copy" onclick="copyCode(this)">copy</button>
<pre><span class="k">from</span> XRPLib.defaults <span class="k">import</span> *
<span class="k">import</span> time

<span class="k">for</span> i <span class="k">in</span> <span class="f">range</span>(<span class="s">6</span>):
    board.<span class="f">led_on</span>()
    time.<span class="f">sleep</span>(<span class="s">0.3</span>)
    board.<span class="f">led_off</span>()
    time.<span class="f">sleep</span>(<span class="s">0.3</span>)
<span class="f">print</span>(<span class="s">"XRP is ready!"</span>)</pre>
        </div>
        <div class="expect"><span class="eye">▸</span><span>The board LED blinks 6 times and <span class="kbd">XRP is ready!</span> prints in the XRPCode console.</span></div>
        <div class="call tip"><b>Want to cut the cord?</b> The XRP also broadcasts its own Wi-Fi network named <span class="kbd">XRP-XXXX-XXXX</span> (password <span class="kbd">xrp-wpilib</span>). Connect your computer to that and you can program it wirelessly — but USB is the simplest way to start.</div>
      </div>
    </div>

    <div class="call tip" style="margin-top:18px"><b>Setup done? 🎉</b>Switch to <b>02 · Learn to code it</b> above to start making it move.</div>
  </section>

  <!-- ============ CODE ============ -->
  <section class="panel-view" id="view-code">

    <p class="sectionsub" style="margin-top:18px">Each lesson is a complete program. Paste it into XRPCode, press Run, and watch what happens. Start every program with the same import line — it hands you ready-made objects like <span class="kbd">board</span>, <span class="kbd">drivetrain</span>, <span class="kbd">rangefinder</span>, and <span class="kbd">servo_one</span>.</p>
    <div class="call tip"><b>Test safely</b>Until you trust your code, prop the robot up so its wheels spin freely in the air, or give it plenty of floor. A surprise full-speed launch off a desk is a rite of passage you can skip.</div>

    <div class="lesson">
      <div class="lh"><span class="idx">L1</span><h3>Hello, robot</h3></div>
      <p>Blink the light and print a message. This proves your code is reaching the robot.</p>
      <div class="codewrap"><button class="copy" onclick="copyCode(this)">copy</button>
<pre><span class="k">from</span> XRPLib.defaults <span class="k">import</span> *
<span class="k">import</span> time

board.<span class="f">led_on</span>()
time.<span class="f">sleep</span>(<span class="s">1</span>)
board.<span class="f">led_off</span>()
<span class="f">print</span>(<span class="s">"Hello from the XRP"</span>)</pre></div>
      <div class="expect"><span class="eye">▸</span><span>LED on for one second, then off; message in the console.</span></div>
    </div>

    <div class="lesson">
      <div class="lh"><span class="idx">L2</span><h3>Drive straight &amp; turn — the easy way</h3></div>
      <p>XRPLib does the hard math for you. <span class="kbd">straight()</span> takes a distance in centimeters; <span class="kbd">turn()</span> takes degrees. A negative distance drives backward.</p>
      <div class="codewrap"><button class="copy" onclick="copyCode(this)">copy</button>
<pre><span class="k">from</span> XRPLib.defaults <span class="k">import</span> *

drivetrain.<span class="f">straight</span>(<span class="s">20</span>)   <span class="c"># forward 20 cm</span>
drivetrain.<span class="f">turn</span>(<span class="s">90</span>)       <span class="c"># turn 90 degrees</span>
drivetrain.<span class="f">straight</span>(<span class="s">-20</span>)  <span class="c"># back up 20 cm</span></pre></div>
      <div class="expect"><span class="eye">▸</span><span>The robot drives forward, pivots, and reverses. Give it room.</span></div>
      <div class="call fix"><b>Runs but doesn't move?</b> Check that the batteries are in and the power switch is on — USB alone won't drive the motors. You can confirm in code with <span class="kbd">board.are_motors_powered()</span>.</div>
    </div>

    <div class="lesson">
      <div class="lh"><span class="idx">L3</span><h3>Direct motor control</h3></div>
      <p>For full control, set each side's <b>effort</b> from -1.0 (full reverse) to 1.0 (full forward). Equal efforts go straight; different efforts turn. This is the building block for controller driving later.</p>
      <div class="codewrap"><button class="copy" onclick="copyCode(this)">copy</button>
<pre><span class="k">from</span> XRPLib.defaults <span class="k">import</span> *
<span class="k">import</span> time

drivetrain.<span class="f">set_effort</span>(<span class="s">0.6</span>, <span class="s">0.6</span>)  <span class="c"># left, right</span>
time.<span class="f">sleep</span>(<span class="s">1.5</span>)
drivetrain.<span class="f">set_effort</span>(<span class="s">0.6</span>, <span class="s">-0.6</span>) <span class="c"># spin in place</span>
time.<span class="f">sleep</span>(<span class="s">0.7</span>)
drivetrain.<span class="f">stop</span>()</pre></div>
      <div class="expect"><span class="eye">▸</span><span>Forward for 1.5s, a spin, then a clean stop.</span></div>
    </div>

    <div class="lesson">
      <div class="lh"><span class="idx">L4</span><h3>Sense the world — distance sensor</h3></div>
      <p>The front rangefinder reports distance in centimeters. Here the robot drives until something is within 10 cm, then stops.</p>
      <div class="codewrap"><button class="copy" onclick="copyCode(this)">copy</button>
<pre><span class="k">from</span> XRPLib.defaults <span class="k">import</span> *
<span class="k">import</span> time

drivetrain.<span class="f">set_effort</span>(<span class="s">0.5</span>, <span class="s">0.5</span>)
<span class="k">while</span> rangefinder.<span class="f">distance</span>() &gt; <span class="s">10</span>:
    time.<span class="f">sleep</span>(<span class="s">0.05</span>)
drivetrain.<span class="f">stop</span>()</pre></div>
      <div class="expect"><span class="eye">▸</span><span>It rolls forward and halts about a hand's width from a wall or your palm.</span></div>
    </div>

    <div class="lesson">
      <div class="lh"><span class="idx">L5</span><h3>Sense the ground — line sensors</h3></div>
      <p>Two reflectance sensors under the front read how dark the surface is, from 0.0 (light) to 1.0 (dark). This is the heart of line following.</p>
      <div class="codewrap"><button class="copy" onclick="copyCode(this)">copy</button>
<pre><span class="k">from</span> XRPLib.defaults <span class="k">import</span> *
<span class="k">import</span> time

<span class="k">while</span> <span class="k">True</span>:
    left = reflectance.<span class="f">get_left</span>()
    right = reflectance.<span class="f">get_right</span>()
    <span class="f">print</span>(left, right)
    time.<span class="f">sleep</span>(<span class="s">0.2</span>)</pre></div>
      <div class="expect"><span class="eye">▸</span><span>Numbers stream in the console — slide a dark strip of tape under each sensor and watch its value jump.</span></div>
    </div>

    <div class="lesson">
      <div class="lh"><span class="idx">L6</span><h3>Move the arm</h3></div>
      <p>The servo arm takes an angle in degrees.</p>
      <div class="codewrap"><button class="copy" onclick="copyCode(this)">copy</button>
<pre><span class="k">from</span> XRPLib.defaults <span class="k">import</span> *
<span class="k">import</span> time

servo_one.<span class="f">set_angle</span>(<span class="s">0</span>)
time.<span class="f">sleep</span>(<span class="s">1</span>)
servo_one.<span class="f">set_angle</span>(<span class="s">135</span>)</pre></div>
      <div class="expect"><span class="eye">▸</span><span>The arm swings to one position, then up to another.</span></div>
    </div>

    <h2 class="sectiontitle">Driving with a game controller</h2>
    <p class="sectionsub">This is the part the docs barely explain — so here's the whole picture.</p>

    <div class="lesson">
      <div class="lh"><span class="idx">L7</span><h3>How controller driving actually works</h3></div>
      <p><b>The key thing nobody tells you:</b> the controller plugs into your <b>computer</b>, not the robot. Your computer reads the gamepad through XRPCode and relays the commands to the XRP over the same connection you program it on. The robot itself has no USB port for a controller.</p>
      <p><b>What controllers work:</b> standard USB gamepads. <b>Xbox</b> controllers and <b>Logitech</b> gamepads are the officially tested ones; <b>PS4/PS5</b> controllers generally work too. Wired USB is the most reliable. To check yours before you even open XRPCode, plug it in and visit <a href="https://hardwaretester.com/gamepad" target="_blank" rel="noopener">hardwaretester.com/gamepad</a> — if the buttons and sticks respond there, they'll work with the XRP.</p>
      <p><b>The driving idea:</b> a controller's sticks report values from <b>-1.0 to 1.0</b>. You read them in a fast loop and feed them straight into <span class="kbd">drivetrain.set_effort(left, right)</span> from Lesson 3. The simplest scheme is <b>tank drive</b>: left stick runs the left wheels, right stick runs the right wheels.</p>
      <div class="codewrap"><button class="copy" onclick="copyCode(this)">copy</button>
<pre><span class="k">from</span> XRPLib.defaults <span class="k">import</span> *
<span class="k">import</span> time

<span class="c"># XRPCode hands your program the gamepad once a controller</span>
<span class="c"># is plugged into your computer. The two read_* lines below</span>
<span class="c"># are placeholders — copy the exact object/import for your</span>
<span class="c"># XRPCode version from the "Using a Game Pad" page (linked</span>
<span class="c"># under this lesson) and drop it in.</span>

<span class="k">while</span> <span class="k">True</span>:
    left_stick  = read_left_stick_y()    <span class="c"># -1.0 .. 1.0</span>
    right_stick = read_right_stick_y()   <span class="c"># -1.0 .. 1.0</span>

    <span class="c"># Sticks read negative when pushed up, so flip the sign</span>
    <span class="c"># to make "push up" mean "go forward".</span>
    drivetrain.<span class="f">set_effort</span>(-left_stick, -right_stick)
    time.<span class="f">sleep</span>(<span class="s">0.02</span>)</pre></div>
      <div class="call tip"><b>Get the exact gamepad code here</b>The mechanics above (the loop, the sign flip, <span class="kbd">set_effort</span>) are the real teaching. For the precise way to read the gamepad in your XRPCode version, open the official <a href="https://xrpusersguide.readthedocs.io/en/latest/course/introduction.html" target="_blank" rel="noopener">XRP User Guide</a> and find its "Using a Game Pad" lesson, then swap its read calls in for the two placeholders.</div>
      <div class="call fix"><b>Controller not detected?</b><ul style="margin:.4em 0 0">
        <li>Confirm it shows up at <a href="https://hardwaretester.com/gamepad" target="_blank" rel="noopener">hardwaretester.com/gamepad</a> first.</li>
        <li>Use a <b>wired USB</b> connection while learning — it's far less fussy than Bluetooth.</li>
        <li>Plug the controller in <b>before</b> you connect to the robot in XRPCode.</li>
      </ul></div>
    </div>

    <div class="lesson">
      <div class="lh"><span class="idx">L8</span><h3>Going fully wireless (optional, popular)</h3></div>
      <p>Want to drive it from your phone or a controller with no computer tethered at all? The community tool <b>PestoLink</b> lets the XRP run a driving program on its own and connect over Bluetooth to a phone web app or gamepad. It's a great next step once the basics click.</p>
      <p>Find it here: <a href="https://github.com/AlfredoSystems/PestoLink-MicroPython" target="_blank" rel="noopener">PestoLink-MicroPython</a>. Connect over USB first to upload its file, then drive wirelessly afterward.</p>
    </div>

    <div class="lesson">
      <div class="lh"><span class="idx">L9</span><h3>Put it together — a little guard-bot</h3></div>
      <p>Combine driving and sensing: creep forward, and if anything gets too close, back off and turn away. Everything here is from the earlier lessons.</p>
      <div class="codewrap"><button class="copy" onclick="copyCode(this)">copy</button>
<pre><span class="k">from</span> XRPLib.defaults <span class="k">import</span> *
<span class="k">import</span> time

<span class="k">while</span> <span class="k">True</span>:
    <span class="k">if</span> rangefinder.<span class="f">distance</span>() &lt; <span class="s">15</span>:
        board.<span class="f">led_on</span>()
        drivetrain.<span class="f">straight</span>(<span class="s">-10</span>)   <span class="c"># back away</span>
        drivetrain.<span class="f">turn</span>(<span class="s">60</span>)        <span class="c"># turn to a new heading</span>
        board.<span class="f">led_off</span>()
    <span class="k">else</span>:
        drivetrain.<span class="f">set_effort</span>(<span class="s">0.4</span>, <span class="s">0.4</span>)
    time.<span class="f">sleep</span>(<span class="s">0.05</span>)</pre></div>
      <div class="expect"><span class="eye">▸</span><span>It patrols slowly; block its path and it retreats, lights up, and reroutes.</span></div>
    </div>

  </section>

  <!-- ============ BUILD ============ -->
  <section class="panel-view" id="view-build">

    <p class="sectionsub" style="margin-top:18px">Each project below is a complete, working program that teaches <b>one real technique</b>. Run it, watch it, then use the <b>Make it yours</b> note to bend it into something of your own. The point isn't to copy these — it's to see what's possible and get ideas.</p>

    <div class="lesson">
      <div class="lh"><span class="idx">P1</span><h3>Line follower</h3></div>
      <p><b>Teaches:</b> feedback control — the robot reads the ground and steers itself, constantly correcting. Lay down a loop of dark tape on a light floor.</p>
      <p>It compares the two ground sensors: if the left sees more line than the right, it steers left, and vice versa. The gain controls how hard it corrects.</p>
      <div class="codewrap"><button class="copy" onclick="copyCode(this)">copy</button>
<pre><span class="k">from</span> XRPLib.defaults <span class="k">import</span> *
<span class="k">import</span> time

BASE = <span class="s">0.4</span>    <span class="c"># cruising effort</span>
GAIN = <span class="s">0.8</span>    <span class="c"># how sharply it corrects</span>

<span class="k">while</span> <span class="k">True</span>:
    error = reflectance.<span class="f">get_left</span>() - reflectance.<span class="f">get_right</span>()
    drivetrain.<span class="f">set_effort</span>(BASE - GAIN*error, BASE + GAIN*error)
    time.<span class="f">sleep</span>(<span class="s">0.02</span>)</pre></div>
      <div class="expect"><span class="eye">▸</span><span>The robot hugs the edge of the tape line. Too wobbly? Lower the gain. Too lazy on curves? Raise it.</span></div>
      <div class="makeit"><b>Make it yours:</b> stop automatically when both sensors go dark (a finish line), or have a friend tune their own gain and race the same track.</div>
    </div>

    <div class="lesson">
      <div class="lh"><span class="idx">P2</span><h3>Roaming explorer</h3></div>
      <p><b>Teaches:</b> making decisions from sensor data. The robot wanders, and when it meets an obstacle it turns to find open space instead of bonking into it.</p>
      <div class="codewrap"><button class="copy" onclick="copyCode(this)">copy</button>
<pre><span class="k">from</span> XRPLib.defaults <span class="k">import</span> *
<span class="k">import</span> time

<span class="k">while</span> <span class="k">True</span>:
    <span class="k">if</span> rangefinder.<span class="f">distance</span>() &lt; <span class="s">20</span>:
        drivetrain.<span class="f">set_effort</span>(<span class="s">0.4</span>, -<span class="s">0.4</span>)  <span class="c"># turn to scan</span>
        time.<span class="f">sleep</span>(<span class="s">0.3</span>)
    <span class="k">else</span>:
        drivetrain.<span class="f">set_effort</span>(<span class="s">0.5</span>, <span class="s">0.5</span>)  <span class="c"># open road ahead</span>
    time.<span class="f">sleep</span>(<span class="s">0.02</span>)</pre></div>
      <div class="expect"><span class="eye">▸</span><span>It cruises across the floor and spins away whenever something blocks it.</span></div>
      <div class="makeit"><b>Make it yours:</b> when blocked, turn one way and check the distance, turn the other way and check again, then commit to whichever side is more open — a much smarter explorer.</div>
    </div>

    <div class="lesson">
      <div class="lh"><span class="idx">P3</span><h3>Dead-straight driving (using the heading sensor)</h3></div>
      <p><b>Teaches:</b> using the IMU to cancel drift. Even "go straight" is hard — one motor is always slightly stronger. Here the robot watches its heading and nudges itself back on course.</p>
      <div class="codewrap"><button class="copy" onclick="copyCode(this)">copy</button>
<pre><span class="k">from</span> XRPLib.defaults <span class="k">import</span> *
<span class="k">import</span> time

imu.<span class="f">reset_yaw</span>()           <span class="c"># "straight ahead" is now 0</span>
<span class="k">while</span> <span class="k">True</span>:
    error = imu.<span class="f">get_yaw</span>()      <span class="c"># degrees off course</span>
    fix = error * <span class="s">0.02</span>         <span class="c"># tune this number</span>
    drivetrain.<span class="f">set_effort</span>(<span class="s">0.4</span> + fix, <span class="s">0.4</span> - fix)
    time.<span class="f">sleep</span>(<span class="s">0.02</span>)</pre></div>
      <div class="expect"><span class="eye">▸</span><span>A noticeably straighter line than plain equal efforts. Bump it sideways and it steers back.</span></div>
      <div class="makeit"><b>Make it yours:</b> use the same idea to make crisp turns — set a target like 90, and drive until <span class="kbd">get_yaw()</span> reaches it.</div>
    </div>

    <div class="lesson">
      <div class="lh"><span class="idx">P4</span><h3>Fetch-and-carry routine</h3></div>
      <p><b>Teaches:</b> sequencing — chaining actions into a mission. The robot drives up to an object, lowers its arm on it, carries it back, and lets go.</p>
      <div class="codewrap"><button class="copy" onclick="copyCode(this)">copy</button>
<pre><span class="k">from</span> XRPLib.defaults <span class="k">import</span> *
<span class="k">import</span> time

servo_one.<span class="f">set_angle</span>(<span class="s">0</span>)              <span class="c"># arm up</span>
drivetrain.<span class="f">set_effort</span>(<span class="s">0.4</span>, <span class="s">0.4</span>)
<span class="k">while</span> rangefinder.<span class="f">distance</span>() &gt; <span class="s">8</span>:    <span class="c"># roll up to it</span>
    time.<span class="f">sleep</span>(<span class="s">0.05</span>)
drivetrain.<span class="f">stop</span>()
servo_one.<span class="f">set_angle</span>(<span class="s">120</span>)            <span class="c"># lower onto the object</span>
time.<span class="f">sleep</span>(<span class="s">0.5</span>)
drivetrain.<span class="f">straight</span>(-<span class="s">30</span>)            <span class="c"># carry it home</span>
servo_one.<span class="f">set_angle</span>(<span class="s">0</span>)              <span class="c"># release</span></pre></div>
      <div class="expect"><span class="eye">▸</span><span>A full pick-up-and-return performance from a single program.</span></div>
      <div class="makeit"><b>Make it yours:</b> have it follow a line (P1) to the drop-off point instead of just backing up — now it's a delivery robot.</div>
    </div>

    <div class="lesson">
      <div class="lh"><span class="idx">P5</span><h3>Reaction-time game</h3></div>
      <p><b>Teaches:</b> input, timing, and randomness — and it's pure fun, no floor space needed. Wait for the light, smack the button, see your time.</p>
      <div class="codewrap"><button class="copy" onclick="copyCode(this)">copy</button>
<pre><span class="k">from</span> XRPLib.defaults <span class="k">import</span> *
<span class="k">import</span> time, random

<span class="f">print</span>(<span class="s">"Wait for the light..."</span>)
time.<span class="f">sleep</span>(random.<span class="f">uniform</span>(<span class="s">2</span>, <span class="s">5</span>))
board.<span class="f">led_on</span>()
start = time.<span class="f">ticks_ms</span>()
board.<span class="f">wait_for_button</span>()
ms = time.<span class="f">ticks_diff</span>(time.<span class="f">ticks_ms</span>(), start)
board.<span class="f">led_off</span>()
<span class="f">print</span>(<span class="s">"Reaction:"</span>, ms, <span class="s">"ms"</span>)</pre></div>
      <div class="expect"><span class="eye">▸</span><span>After a random pause the LED lights; your reaction time prints when you press the button.</span></div>
      <div class="makeit"><b>Make it yours:</b> make it best-of-five, or (on the current XRP board) flash a random color with <span class="kbd">board.set_rgb_led(r, g, b)</span> and only count presses on "green."</div>
    </div>

    <h2 class="sectiontitle">Idea bank — now invent your own</h2>
    <p class="sectionsub">Every one of these is buildable from the pieces you already have: drive, distance sensor, line sensors, heading sensor, arm, button, and LED. Pick one that excites you and figure out which technique above it leans on.</p>

    <div class="ideas">
      <div class="idea"><span class="diff h">Hard</span><h4>Maze solver</h4><p>Follow walls with the rangefinder using the right-hand rule until you reach the exit.</p></div>
      <div class="idea"><span class="diff m">Medium</span><h4>Sumo bot</h4><p>Charge an opponent, but slam to a stop when the line sensors hit the ring's border.</p></div>
      <div class="idea"><span class="diff m">Medium</span><h4>Parallel parking</h4><p>A timed, tuned routine that backs into a "spot" between two objects.</p></div>
      <div class="idea"><span class="diff e">Easy</span><h4>Morse messenger</h4><p>Blink a secret word in Morse code with the LED. Add the buzzer if you have one.</p></div>
      <div class="idea"><span class="diff m">Medium</span><h4>Security guard</h4><p>Sit still and sound an alert the moment the measured distance suddenly drops.</p></div>
      <div class="idea"><span class="diff m">Medium</span><h4>Drawing bot</h4><p>Tape a marker to it and program it to drive squares, triangles, and spirals.</p></div>
      <div class="idea"><span class="diff h">Hard</span><h4>Robot tag</h4><p>Two XRPs: one keeps a fixed distance behind the other using the rangefinder.</p></div>
      <div class="idea"><span class="diff m">Medium</span><h4>Course speed-run</h4><p>Tape a track, then tune efforts and turns to finish in the fastest time.</p></div>
    </div>

    <div class="call tip" style="margin-top:20px"><b>How to start any of these</b>Don't write the whole thing at once. Get the smallest piece working first (just drive, or just read the sensor), test it, then add one capability at a time. That's how every robot above was built.</div>

  </section>

  <!-- ============ PRINT ============ -->
  <section class="panel-view" id="view-print">

    <p class="sectionsub" style="margin-top:18px">The XRP is designed to be extended. Its chassis and parts are <b>open-source and made for 3D printing</b>, with mounting holes, motor-shaft holes, and Qwiic sensor ports built in so your own pieces snap and screw right on. This track is a starting point — concrete things people print and add — to get you dreaming up your own.</p>

    <div class="lesson">
      <div class="lh"><span class="idx">▸</span><h3>How add-ons attach (and where files live)</h3></div>
      <p>The XRP body itself is a printed part, so accessories are first-class citizens. They mount three ways: clipping into the <b>holes along the chassis</b>, screwing on with <b>M3 hardware</b>, or clipping onto a <b>Qwiic port</b> for sensors. The official CAD is open-source on <b>Onshape</b>, so any part can be remixed.</p>
      <ul>
        <li><b>Official files</b> (chassis, line-sensor mount, distance-sensor mount, wheels, battery cover): on <a href="https://www.printables.com/model/1216372-xrp-robot-kit" target="_blank" rel="noopener">Printables</a> and <a href="https://github.com/Open-STEM" target="_blank" rel="noopener">Open-STEM on GitHub</a>.</li>
        <li><b>Community mods</b> (sensor mounts, tires, steering, and more) keep showing up on Printables — search "XRP."</li>
        <li><b>No printer?</b> Buy the kit with the chassis included, use a library or school makerspace, or send the files to an online print service.</li>
      </ul>
      <div class="call tip"><b>Print-settings starting point</b>Around <b>0.2 mm layer height</b>, <b>~10% grid infill</b>, no brim or supports for most parts (watch for the break-away bits on the chassis). <b>PLA</b> is fine to start; <b>PETG</b> is tougher for bumpers and brackets; <b>TPU</b> is the move for grippy tires. Keep a few <b>M3 screws and nuts</b> on hand.</div>
    </div>

    <p class="eyebrow" style="margin-top:26px">Sensors &amp; electronics</p>
    <div class="ideas">
      <div class="idea"><h4>Universal Qwiic mount</h4><p>A clip that holds almost any SparkFun Qwiic sensor and plugs into an open Qwiic port — add a color sensor, OLED screen, or extra IMU.</p></div>
      <div class="idea"><h4>Camera / phone cradle</h4><p>Hold a phone or small camera for FPV driving or computer-vision experiments.</p></div>
      <div class="idea"><h4>Side-facing sensor bracket</h4><p>Aim a second distance sensor sideways for true wall-following. <span class="diff m">pairs with P2 explorer</span></p></div>
      <div class="idea"><h4>Cable clips</h4><p>Tidy tile of clips so wires stop snagging mid-drive.</p></div>
    </div>

    <p class="eyebrow" style="margin-top:22px">Tools &amp; mechanisms</p>
    <div class="ideas">
      <div class="idea"><h4>Gripper jaws</h4><p>Snap claws onto the servo arm to actually grab and hold objects. <span class="diff m">pairs with P4 fetch</span></p></div>
      <div class="idea"><h4>Plow / bulldozer blade</h4><p>A front blade for pushing objects — cleanup runs or shoving a rival out of the ring. <span class="diff m">pairs with the sumo idea</span></p></div>
      <div class="idea"><h4>Scoop or basket</h4><p>Collect small items and carry a payload around the room.</p></div>
      <div class="idea"><h4>Trailer + hitch</h4><p>Tow a second printed cart — turn it into a little delivery truck.</p></div>
      <div class="idea"><h4>Marker holder</h4><p>Grip a pen at the center so the robot draws whatever path it drives. <span class="diff m">pairs with the drawing-bot idea</span></p></div>
    </div>

    <p class="eyebrow" style="margin-top:22px">Wheels &amp; motion</p>
    <div class="ideas">
      <div class="idea"><h4>Bigger wheels</h4><p>Larger diameter trades torque for speed — feel the difference on the same code.</p></div>
      <div class="idea"><h4>TPU tires &amp; treads</h4><p>Printed grippy tires for traction on carpet, ramps, and slick floors.</p></div>
      <div class="idea"><h4>Steerable front wheel</h4><p>A servo-driven steering assembly for car-style driving instead of tank turns.</p></div>
      <div class="idea"><h4>Bumper ring</h4><p>A protective wrap-around bumper — add a switch behind it to feel collisions.</p></div>
    </div>

    <p class="eyebrow" style="margin-top:22px">Make it yours</p>
    <div class="ideas">
      <div class="idea"><h4>Name plate / team badge</h4><p>A snap-in tag with your name, class, or team number.</p></div>
      <div class="idea"><h4>Costume shell</h4><p>A decorative body — animal, car, mascot — that clips over the frame.</p></div>
      <div class="idea"><h4>Utility "holey" deck</h4><p>An extra plate full of holes as a mounting grid for your own contraptions.</p></div>
      <div class="idea"><h4>Build-system adapter</h4><p>A bracket that bridges the XRP to LEGO Technic or other parts you already own.</p></div>
    </div>

    <div class="lesson" style="margin-top:24px">
      <div class="lh"><span class="idx">★</span><h3>Design your own</h3></div>
      <p>The most satisfying add-on is one nobody's made yet. Open the official model in <a href="https://www.printables.com/model/1216372-xrp-robot-kit" target="_blank" rel="noopener">Onshape</a> to see exact dimensions and hole spacing, or sketch something simple in <b>Tinkercad</b> if you're new to CAD. Measure a mounting hole, model a clip or bracket that fits it, print, test, adjust the tolerance, reprint. Iterating fast on cheap plastic <i>is</i> the engineering.</p>
      <div class="makeit"><b>A good first design:</b> a flat clip that snaps into two chassis holes and holds one small thing you care about — a flag, a googly-eyed face, a tiny ramp. Get the fit right once and you can mount anything.</div>
    </div>

  </section>

  <footer>
    <b>Handy links</b>
    <ul class="links">
      <li><a href="https://xrpcode.wpi.edu/" target="_blank" rel="noopener">XRPCode (the editor)</a></li>
      <li><a href="https://open-stem.github.io/XRP_MicroPython/api.html" target="_blank" rel="noopener">XRPLib full API reference</a></li>
      <li><a href="https://introtoroboticsv2.readthedocs.io" target="_blank" rel="noopener">WPI's free XRP course</a></li>
      <li><a href="https://xrp.discourse.group" target="_blank" rel="noopener">XRP support forum</a></li>
      <li><a href="https://www.printables.com/model/1216372-xrp-robot-kit" target="_blank" rel="noopener">Official 3D-print files</a></li>
    </ul>
    <p style="margin-top:14px">Progress checkmarks are kept for this visit only and reset if you reload.</p>
  </footer>

</div>

<script>
  // ---- board version toggle ----
  function setBoard(b){
    document.querySelectorAll('.seg button').forEach(x=>x.classList.toggle('on', x.dataset.set===b));
    document.querySelectorAll('[data-board]').forEach(el=>{
      el.classList.toggle('show', el.getAttribute('data-board')===b);
    });
  }

  // ---- tabs ----
  function showTab(which){
    ['setup','code','build','print'].forEach(t=>{
      document.getElementById('view-'+t).classList.toggle('on', which===t);
      document.getElementById('tab-'+t).classList.toggle('on', which===t);
    });
    window.scrollTo({top: document.querySelector('.tabs').offsetTop - 80, behavior:'smooth'});
  }

  // ---- accordion ----
  function toggle(head){ head.parentElement.classList.toggle('open'); }

  // ---- checkboxes / progress ----
  const TOTAL = document.querySelectorAll('#view-setup [data-step]').length;
  function check(e, box){
    e.stopPropagation();
    box.closest('[data-step]').classList.toggle('done');
    updateProgress();
  }
  function updateProgress(){
    const done = document.querySelectorAll('#view-setup [data-step].done').length;
    const pct = Math.round(done/TOTAL*100);
    document.getElementById('pfill').style.width = pct+'%';
    document.getElementById('ptext').textContent = done+' / '+TOTAL+' setup steps';
    const status = document.getElementById('status');
    const eyes = [document.getElementById('eyeL'), document.getElementById('eyeR')];
    const topled = document.getElementById('topled');
    if(done===0){ status.textContent='Powered off'; eyes.forEach(x=>x.setAttribute('fill','#5A6378')); topled.setAttribute('fill','#5A6378'); }
    else if(done<TOTAL){ status.textContent='Booting up…'; eyes.forEach(x=>x.setAttribute('fill','#F4642A')); topled.setAttribute('fill','#F4642A'); }
    else { status.textContent='Ready to roll!'; eyes.forEach(x=>x.setAttribute('fill','#2C9A63')); topled.setAttribute('fill','#2C9A63'); }
  }

  // ---- copy buttons ----
  function copyCode(btn){
    const code = btn.parentElement.querySelector('pre').innerText;
    navigator.clipboard.writeText(code).then(()=>{
      const old = btn.textContent; btn.textContent='copied ✓';
      setTimeout(()=>btn.textContent=old, 1300);
    });
  }

  updateProgress();
</script>
</body>
</html>
