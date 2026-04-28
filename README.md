<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>NeuralPath — Aprende Machine Learning desde cero</title>
  <link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;700;800&family=DM+Mono:wght@300;400;500&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet" />
  <style>
    :root {
      --bg:       #f4f1eb;
      --ink:      #0f0f0f;
      --mid:      #2a2a2a;
      --soft:     #7a7a6e;
      --accent:   #1a6b3c;
      --accent2:  #e8f5ee;
      --yellow:   #f5c842;
      --yellow-d: #d4a800;
      --card:     #ffffff;
      --border:   #ddd9d0;
      --code:     #1e1e2e;
    }

    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
    html { scroll-behavior: smooth; }

    body {
      background: var(--bg);
      color: var(--ink);
      font-family: 'DM Sans', sans-serif;
      overflow-x: hidden;
    }

    /* ── GRAIN OVERLAY ── */
    body::before {
      content: '';
      position: fixed; inset: 0; z-index: 0; pointer-events: none;
      background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.04'/%3E%3C/svg%3E");
      background-size: 256px;
      opacity: 0.5;
    }

    /* ── NAV ── */
    nav {
      position: fixed; top: 0; width: 100%; z-index: 100;
      display: flex; align-items: center; justify-content: space-between;
      padding: 1.1rem 4rem;
      background: rgba(244,241,235,0.88);
      backdrop-filter: blur(16px);
      border-bottom: 1px solid var(--border);
    }
    .logo {
      font-family: 'Syne', sans-serif;
      font-weight: 800; font-size: 1.3rem;
      color: var(--ink); text-decoration: none;
      display: flex; align-items: center; gap: 0.5rem;
    }
    .logo-dot { width: 10px; height: 10px; background: var(--accent); border-radius: 50%; display: inline-block; }
    nav ul { list-style: none; display: flex; gap: 2rem; align-items: center; }
    nav ul a {
      color: var(--mid); text-decoration: none;
      font-size: 0.85rem; font-weight: 500;
      transition: color 0.2s;
    }
    nav ul a:hover { color: var(--accent); }
    .nav-cta {
      background: var(--ink) !important; color: var(--bg) !important;
      padding: 0.55rem 1.4rem; border-radius: 100px;
      font-size: 0.82rem !important; font-weight: 500 !important;
      transition: background 0.2s !important;
    }
    .nav-cta:hover { background: var(--accent) !important; }

    /* ── HERO ── */
    #hero {
      min-height: 100vh;
      display: grid; grid-template-columns: 1fr 1fr;
      align-items: center; gap: 4rem;
      padding: 8rem 4rem 5rem;
      position: relative; overflow: hidden;
    }
    .hero-bg-circle {
      position: absolute; right: -10%; top: 10%;
      width: 55vw; height: 55vw;
      border-radius: 50%;
      background: radial-gradient(circle, rgba(26,107,60,0.12) 0%, transparent 70%);
      pointer-events: none;
    }
    .hero-badge {
      display: inline-flex; align-items: center; gap: 0.5rem;
      background: var(--accent2); border: 1px solid rgba(26,107,60,0.25);
      color: var(--accent); border-radius: 100px;
      font-size: 0.72rem; font-weight: 500; letter-spacing: 0.05em;
      padding: 0.4rem 1rem; margin-bottom: 1.8rem;
      animation: fadeUp 0.7s ease both;
    }
    .badge-dot { width: 6px; height: 6px; background: var(--accent); border-radius: 50%; }
    .hero-title {
      font-family: 'Syne', sans-serif;
      font-weight: 800;
      font-size: clamp(2.8rem, 5.5vw, 5rem);
      line-height: 1.02;
      color: var(--ink);
      animation: fadeUp 0.7s 0.1s ease both;
    }
    .hero-title .underline-green {
      position: relative; display: inline-block;
    }
    .hero-title .underline-green::after {
      content: '';
      position: absolute; bottom: 2px; left: 0; width: 100%; height: 6px;
      background: var(--yellow); z-index: -1; border-radius: 2px;
    }
    .hero-desc {
      font-size: 1.05rem; color: var(--soft); line-height: 1.75;
      margin: 1.5rem 0 2.5rem; max-width: 440px;
      animation: fadeUp 0.7s 0.2s ease both;
    }
    .hero-btns {
      display: flex; gap: 1rem; flex-wrap: wrap;
      animation: fadeUp 0.7s 0.3s ease both;
    }
    .btn-primary {
      background: var(--ink); color: var(--bg);
      padding: 0.9rem 2rem; border-radius: 100px;
      font-size: 0.9rem; font-weight: 500;
      border: none; cursor: pointer; text-decoration: none;
      display: inline-flex; align-items: center; gap: 0.5rem;
      transition: background 0.2s, transform 0.15s;
    }
    .btn-primary:hover { background: var(--accent); transform: translateY(-2px); }
    .btn-ghost {
      background: transparent; color: var(--ink);
      padding: 0.9rem 2rem; border-radius: 100px;
      font-size: 0.9rem; font-weight: 500;
      border: 1.5px solid var(--border); cursor: pointer; text-decoration: none;
      display: inline-flex; align-items: center; gap: 0.5rem;
      transition: border-color 0.2s, transform 0.15s;
    }
    .btn-ghost:hover { border-color: var(--ink); transform: translateY(-2px); }
    .hero-trust {
      margin-top: 2.5rem; font-size: 0.78rem; color: var(--soft);
      display: flex; align-items: center; gap: 0.6rem;
      animation: fadeUp 0.7s 0.4s ease both;
    }
    .trust-avatars { display: flex; }
    .trust-avatars span {
      width: 28px; height: 28px; border-radius: 50%;
      border: 2px solid var(--bg);
      display: flex; align-items: center; justify-content: center;
      font-size: 0.8rem; margin-left: -6px;
    }
    .trust-avatars span:first-child { margin-left: 0; }

    /* ── HERO VISUAL (right side) ── */
    .hero-visual {
      position: relative;
      animation: fadeUp 0.7s 0.2s ease both;
    }
    .code-window {
      background: var(--code);
      border-radius: 16px; overflow: hidden;
      box-shadow: 0 40px 80px rgba(0,0,0,0.18);
      font-family: 'DM Mono', monospace;
    }
    .code-bar {
      padding: 0.9rem 1.2rem;
      background: #16162a;
      display: flex; align-items: center; gap: 0.5rem;
    }
    .dot { width: 12px; height: 12px; border-radius: 50%; }
    .dot.r { background: #ff5f57; }
    .dot.y { background: #febc2e; }
    .dot.g { background: #28c840; }
    .code-filename {
      font-size: 0.72rem; color: #666; margin-left: auto;
      font-family: 'DM Mono', monospace;
    }
    .code-body { padding: 1.5rem 1.8rem; font-size: 0.82rem; line-height: 1.8; }
    .c-comment { color: #6a737d; }
    .c-keyword { color: #ff79c6; }
    .c-string  { color: #f1fa8c; }
    .c-func    { color: #50fa7b; }
    .c-var     { color: #8be9fd; }
    .c-num     { color: #bd93f9; }
    .c-white   { color: #f8f8f2; }
    .code-output {
      background: #0d1117; padding: 1rem 1.8rem;
      border-top: 1px solid #2a2a3e;
      font-size: 0.78rem; color: #50fa7b; font-family: 'DM Mono', monospace;
    }
    .floating-card {
      position: absolute;
      background: var(--card);
      border: 1px solid var(--border);
      border-radius: 12px;
      padding: 0.9rem 1.2rem;
      box-shadow: 0 8px 30px rgba(0,0,0,0.1);
      font-size: 0.8rem;
    }
    .fc-top {
      top: -1.5rem; left: -2rem;
      display: flex; align-items: center; gap: 0.6rem;
    }
    .fc-icon { font-size: 1.5rem; }
    .fc-label { font-weight: 600; color: var(--ink); font-size: 0.85rem; }
    .fc-sub   { color: var(--soft); font-size: 0.72rem; }
    .fc-bottom {
      bottom: -1.5rem; right: -1.5rem;
      display: flex; align-items: center; gap: 0.8rem;
    }
    .fc-progress { width: 90px; }
    .fc-prog-label { font-size: 0.7rem; color: var(--soft); margin-bottom: 0.3rem; }
    .fc-prog-bar { height: 5px; background: #eee; border-radius: 10px; overflow: hidden; }
    .fc-prog-fill { height: 100%; background: var(--accent); border-radius: 10px; width: 68%; }
    .fc-pct { font-family: 'Syne', sans-serif; font-weight: 700; font-size: 1.1rem; color: var(--accent); }

    /* ── LOGOS STRIP ── */
    .logos-strip {
      border-top: 1px solid var(--border);
      border-bottom: 1px solid var(--border);
      padding: 1.5rem 4rem;
      display: flex; align-items: center; justify-content: center;
      gap: 3rem; flex-wrap: wrap;
      background: var(--card);
    }
    .logos-label { font-size: 0.72rem; color: var(--soft); letter-spacing: 0.1em; text-transform: uppercase; }
    .tech-pill {
      display: flex; align-items: center; gap: 0.5rem;
      font-family: 'DM Mono', monospace; font-size: 0.82rem;
      color: var(--mid); font-weight: 500;
    }
    .tech-pill span { font-size: 1.2rem; }

    /* ── SECTIONS ── */
    section { padding: 6rem 4rem; position: relative; }
    .section-chip {
      display: inline-block;
      background: var(--accent2); color: var(--accent);
      border: 1px solid rgba(26,107,60,0.2);
      font-size: 0.72rem; font-weight: 600; letter-spacing: 0.1em; text-transform: uppercase;
      padding: 0.3rem 0.9rem; border-radius: 100px; margin-bottom: 1rem;
    }
    .section-title {
      font-family: 'Syne', sans-serif; font-weight: 800;
      font-size: clamp(2rem, 4vw, 3.2rem);
      color: var(--ink); line-height: 1.1; margin-bottom: 1rem;
    }
    .section-title em { color: var(--accent); font-style: normal; }
    .section-body {
      font-size: 1rem; color: var(--soft); line-height: 1.8; max-width: 520px;
    }

    /* ── HOW IT WORKS ── */
    #how { background: var(--ink); color: var(--bg); }
    #how .section-chip { background: rgba(26,107,60,0.25); color: #6fcf97; border-color: rgba(111,207,151,0.2); }
    #how .section-title { color: var(--bg); }
    #how .section-body { color: #888; }
    .steps-grid {
      display: grid; grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
      gap: 2rem; margin-top: 3.5rem; max-width: 1100px;
    }
    .step-card {
      padding: 2rem;
      border: 1px solid rgba(255,255,255,0.07);
      border-radius: 12px;
      background: #1a1a1a;
      transition: border-color 0.2s, transform 0.2s;
    }
    .step-card:hover { border-color: var(--accent); transform: translateY(-4px); }
    .step-num {
      font-family: 'Syne', sans-serif; font-weight: 800;
      font-size: 3rem; color: rgba(255,255,255,0.07);
      line-height: 1; margin-bottom: 1rem;
    }
    .step-icon { font-size: 2rem; margin-bottom: 0.8rem; }
    .step-title {
      font-family: 'Syne', sans-serif; font-weight: 700;
      font-size: 1.1rem; color: var(--bg); margin-bottom: 0.5rem;
    }
    .step-desc { font-size: 0.88rem; color: #777; line-height: 1.7; }

    /* ── CURRÍCULO ── */
    #curriculum { background: var(--bg); }
    .curriculum-grid {
      display: grid; grid-template-columns: 1fr 1fr; gap: 1.5rem;
      margin-top: 3rem; max-width: 900px;
    }
    .module-card {
      background: var(--card);
      border: 1px solid var(--border);
      border-radius: 12px; padding: 1.5rem;
      display: flex; gap: 1.2rem; align-items: flex-start;
      transition: box-shadow 0.2s, transform 0.2s;
      cursor: default;
    }
    .module-card:hover {
      box-shadow: 0 12px 40px rgba(0,0,0,0.08);
      transform: translateY(-3px);
    }
    .module-num {
      width: 36px; height: 36px; border-radius: 8px;
      background: var(--accent2); color: var(--accent);
      font-family: 'DM Mono', monospace; font-weight: 500; font-size: 0.8rem;
      display: flex; align-items: center; justify-content: center; flex-shrink: 0;
    }
    .module-num.done { background: var(--accent); color: #fff; }
    .module-info {}
    .module-title {
      font-family: 'Syne', sans-serif; font-weight: 700;
      font-size: 0.95rem; color: var(--ink); margin-bottom: 0.3rem;
    }
    .module-meta { font-size: 0.75rem; color: var(--soft); display: flex; gap: 1rem; }
    .module-tag {
      display: inline-block; margin-top: 0.6rem;
      background: var(--accent2); color: var(--accent);
      font-size: 0.65rem; font-weight: 600; letter-spacing: 0.08em; text-transform: uppercase;
      padding: 0.2rem 0.6rem; border-radius: 4px;
    }
    .module-tag.free { background: #fff9e0; color: var(--yellow-d); }

    /* ── TESTIMONIOS ── */
    #testimonials { background: var(--accent2); }
    .testi-grid {
      display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
      gap: 1.5rem; margin-top: 3rem;
    }
    .testi-card {
      background: var(--card); border: 1px solid var(--border);
      border-radius: 12px; padding: 1.8rem;
      transition: transform 0.2s;
    }
    .testi-card:hover { transform: translateY(-4px); }
    .testi-stars { color: var(--yellow-d); font-size: 1rem; margin-bottom: 1rem; }
    .testi-quote {
      font-size: 0.92rem; color: var(--mid); line-height: 1.75; margin-bottom: 1.2rem;
    }
    .testi-author { display: flex; align-items: center; gap: 0.8rem; }
    .testi-avatar {
      width: 38px; height: 38px; border-radius: 50%;
      background: var(--accent2); display: flex; align-items: center;
      justify-content: center; font-size: 1.2rem;
    }
    .testi-name { font-weight: 600; font-size: 0.85rem; color: var(--ink); }
    .testi-role { font-size: 0.72rem; color: var(--soft); }

    /* ── PRICING ── */
    #pricing { background: var(--bg); }
    .pricing-grid {
      display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
      gap: 1.5rem; margin-top: 3rem; max-width: 900px;
    }
    .price-card {
      background: var(--card); border: 1px solid var(--border);
      border-radius: 16px; padding: 2.2rem; position: relative;
      transition: transform 0.2s;
    }
    .price-card:hover { transform: translateY(-4px); }
    .price-card.featured {
      background: var(--ink); border-color: var(--ink);
      color: var(--bg);
    }
    .price-badge {
      position: absolute; top: -12px; left: 50%; transform: translateX(-50%);
      background: var(--yellow); color: var(--ink);
      font-size: 0.7rem; font-weight: 700; letter-spacing: 0.08em; text-transform: uppercase;
      padding: 0.3rem 1rem; border-radius: 100px;
    }
    .price-plan { font-size: 0.75rem; letter-spacing: 0.15em; text-transform: uppercase; color: var(--soft); font-weight: 600; margin-bottom: 0.5rem; }
    .price-card.featured .price-plan { color: #888; }
    .price-amount {
      font-family: 'Syne', sans-serif; font-weight: 800;
      font-size: 3rem; color: var(--ink); line-height: 1;
      margin-bottom: 0.3rem;
    }
    .price-card.featured .price-amount { color: var(--bg); }
    .price-period { font-size: 0.8rem; color: var(--soft); margin-bottom: 1.5rem; }
    .price-card.featured .price-period { color: #777; }
    .price-features { list-style: none; display: flex; flex-direction: column; gap: 0.7rem; margin-bottom: 2rem; }
    .price-features li {
      font-size: 0.88rem; color: var(--mid); display: flex; align-items: center; gap: 0.6rem;
    }
    .price-card.featured .price-features li { color: #ccc; }
    .price-check { color: var(--accent); font-weight: 700; }
    .price-card.featured .price-check { color: #6fcf97; }
    .btn-price-primary {
      display: block; width: 100%; text-align: center;
      background: var(--bg); color: var(--ink);
      padding: 0.9rem; border-radius: 100px;
      font-size: 0.88rem; font-weight: 600;
      border: none; cursor: pointer; text-decoration: none;
      transition: background 0.2s;
    }
    .btn-price-primary:hover { background: var(--accent2); }
    .btn-price-dark {
      display: block; width: 100%; text-align: center;
      background: var(--ink); color: var(--bg);
      padding: 0.9rem; border-radius: 100px;
      font-size: 0.88rem; font-weight: 600;
      border: none; cursor: pointer; text-decoration: none;
      transition: background 0.2s;
    }
    .btn-price-dark:hover { background: var(--accent); }

    /* ── CTA FINAL ── */
    #cta-final {
      background: var(--accent);
      padding: 6rem 4rem; text-align: center;
    }
    #cta-final .section-title { color: #fff; max-width: 700px; margin: 0 auto 1rem; }
    #cta-final .section-body { color: rgba(255,255,255,0.75); margin: 0 auto 2.5rem; }
    .cta-input-row {
      display: flex; gap: 0.8rem; flex-wrap: wrap;
      justify-content: center; max-width: 480px; margin: 0 auto;
    }
    .cta-input-row input {
      flex: 1; min-width: 200px;
      padding: 0.9rem 1.3rem;
      background: rgba(255,255,255,0.15); border: 1px solid rgba(255,255,255,0.3);
      color: #fff; border-radius: 100px;
      font-family: 'DM Sans', sans-serif; font-size: 0.9rem;
    }
    .cta-input-row input::placeholder { color: rgba(255,255,255,0.6); }
    .cta-input-row input:focus { outline: none; background: rgba(255,255,255,0.2); }
    .btn-white {
      background: #fff; color: var(--accent);
      padding: 0.9rem 2rem; border-radius: 100px;
      font-size: 0.9rem; font-weight: 600;
      border: none; cursor: pointer;
      transition: transform 0.15s;
    }
    .btn-white:hover { transform: scale(1.03); }

    /* ── FOOTER ── */
    footer {
      background: #0a0a0a; color: #555;
      padding: 3rem 4rem;
      display: flex; align-items: center; justify-content: space-between; flex-wrap: wrap; gap: 1.5rem;
    }
    .footer-logo {
      font-family: 'Syne', sans-serif; font-weight: 800;
      font-size: 1.2rem; color: #fff;
      display: flex; align-items: center; gap: 0.4rem;
    }
    .footer-links { display: flex; gap: 2rem; flex-wrap: wrap; }
    .footer-links a { color: #555; text-decoration: none; font-size: 0.82rem; transition: color 0.2s; }
    .footer-links a:hover { color: #fff; }
    footer p { font-size: 0.78rem; }

    /* ── ANIMATIONS ── */
    @keyframes fadeUp {
      from { opacity: 0; transform: translateY(24px); }
      to   { opacity: 1; transform: translateY(0); }
    }

    /* ── RESPONSIVE ── */
    @media (max-width: 900px) {
      #hero { grid-template-columns: 1fr; padding: 7rem 1.5rem 4rem; }
      .hero-visual { display: none; }
      nav { padding: 1rem 1.5rem; }
      nav ul { display: none; }
      section { padding: 4rem 1.5rem; }
      .logos-strip { padding: 1.5rem; gap: 1.5rem; }
      .curriculum-grid { grid-template-columns: 1fr; }
      footer { flex-direction: column; padding: 2rem 1.5rem; }
      .steps-grid { gap: 1rem; }
      #how { padding: 4rem 1.5rem; }
    }
  </style>
</head>
<body>

<!-- NAV -->
<nav>
  <a href="#" class="logo"><span class="logo-dot"></span> NeuralPath</a>
  <ul>
    <li><a href="#how">Cómo funciona</a></li>
    <li><a href="#curriculum">Currículo</a></li>
    <li><a href="#testimonials">Testimonios</a></li>
    <li><a href="#pricing">Precios</a></li>
    <li><a href="#cta-final" class="nav-cta">Empezar gratis →</a></li>
  </ul>
</nav>

<!-- HERO -->
<section id="hero">
  <div>
    <div class="hero-badge"><span class="badge-dot"></span> Para principiantes absolutos · Sin experiencia previa</div>
    <h1 class="hero-title">
      Aprende<br>
      <span class="underline-green">Machine Learning</span><br>
      desde cero.
    </h1>
    <p class="hero-desc">
      NeuralPath te lleva de "¿qué es una variable?" hasta construir tus propios modelos de inteligencia artificial — en español, a tu ritmo y sin prerrequisitos.
    </p>
    <div class="hero-btns">
      <a href="#cta-final" class="btn-primary">Comenzar gratis →</a>
      <a href="#curriculum" class="btn-ghost">Ver el programa</a>
    </div>
    <div class="hero-trust">
      <div class="trust-avatars">
        <span>👩</span><span>👨</span><span>🧑</span><span>👩‍💻</span>
      </div>
      +2,400 estudiantes ya están aprendiendo
    </div>
  </div>
  <div class="hero-visual">
    <div class="hero-bg-circle"></div>
    <div class="floating-card fc-top">
      <span class="fc-icon">🧠</span>
      <div>
        <div class="fc-label">Modelo entrenado</div>
        <div class="fc-sub">Precisión: 94.3%</div>
      </div>
    </div>
    <div class="code-window">
      <div class="code-bar">
        <div class="dot r"></div><div class="dot y"></div><div class="dot g"></div>
        <span class="code-filename">mi_primer_modelo.py</span>
      </div>
      <div class="code-body">
        <div><span class="c-comment"># Importar las herramientas</span></div>
        <div><span class="c-keyword">from</span> <span class="c-var">sklearn</span> <span class="c-keyword">import</span> <span class="c-func">tree</span></div>
        <div>&nbsp;</div>
        <div><span class="c-comment"># Datos de entrenamiento</span></div>
        <div><span class="c-var">datos</span> <span class="c-white">= [[</span><span class="c-num">1</span><span class="c-white">, </span><span class="c-num">0</span><span class="c-white">], [</span><span class="c-num">0</span><span class="c-white">, </span><span class="c-num">1</span><span class="c-white">]]</span></div>
        <div><span class="c-var">etiquetas</span> <span class="c-white">= [</span><span class="c-string">"perro"</span><span class="c-white">, </span><span class="c-string">"gato"</span><span class="c-white">]</span></div>
        <div>&nbsp;</div>
        <div><span class="c-comment"># Crear y entrenar el modelo</span></div>
        <div><span class="c-var">modelo</span> <span class="c-white">=</span> <span class="c-func">tree.DecisionTreeClassifier</span><span class="c-white">()</span></div>
        <div><span class="c-var">modelo</span><span class="c-white">.</span><span class="c-func">fit</span><span class="c-white">(</span><span class="c-var">datos</span><span class="c-white">, </span><span class="c-var">etiquetas</span><span class="c-white">)</span></div>
        <div>&nbsp;</div>
        <div><span class="c-comment"># ¡Hacer una predicción!</span></div>
        <div><span class="c-func">print</span><span class="c-white">(</span><span class="c-var">modelo</span><span class="c-white">.</span><span class="c-func">predict</span><span class="c-white">([[</span><span class="c-num">1</span><span class="c-white">, </span><span class="c-num">0</span><span class="c-white">]]))</span></div>
      </div>
      <div class="code-output">▶ ['perro'] — ¡Tu primer modelo funcionó! 🎉</div>
    </div>
    <div class="floating-card fc-bottom">
      <div class="fc-progress">
        <div class="fc-prog-label">Módulo 3 de 8</div>
        <div class="fc-prog-bar"><div class="fc-prog-fill"></div></div>
      </div>
      <div class="fc-pct">68%</div>
    </div>
  </div>
</section>

<!-- LOGOS -->
<div class="logos-strip">
  <span class="logos-label">Aprenderás a usar</span>
  <div class="tech-pill"><span>🐍</span> Python</div>
  <div class="tech-pill"><span>🔢</span> NumPy</div>
  <div class="tech-pill"><span>🐼</span> Pandas</div>
  <div class="tech-pill"><span>⚙️</span> Scikit-learn</div>
  <div class="tech-pill"><span>📊</span> Matplotlib</div>
  <div class="tech-pill"><span>🔥</span> TensorFlow</div>
</div>

<!-- HOW IT WORKS -->
<section id="how">
  <div class="section-chip">¿Cómo funciona?</div>
  <h2 class="section-title">Tu camino al ML,<br><em>paso a paso</em></h2>
  <p class="section-body">Sin confusión, sin saltos gigantes. Cada lección construye sobre la anterior hasta que dominas los conceptos con confianza.</p>
  <div class="steps-grid">
    <div class="step-card">
      <div class="step-num">01</div>
      <div class="step-icon">📖</div>
      <div class="step-title">Conceptos en español</div>
      <div class="step-desc">Explicamos cada idea con analogías del mundo real — sin jerga innecesaria ni suposiciones de conocimiento previo.</div>
    </div>
    <div class="step-card">
      <div class="step-num">02</div>
      <div class="step-icon">💻</div>
      <div class="step-title">Practica en el navegador</div>
      <div class="step-desc">Escribe y ejecuta código Python directamente en tu navegador. Sin instalar nada, sin configurar nada.</div>
    </div>
    <div class="step-card">
      <div class="step-num">03</div>
      <div class="step-icon">🧪</div>
      <div class="step-title">Mini proyectos reales</div>
      <div class="step-desc">Cada módulo termina con un pequeño proyecto real: predecir precios, clasificar imágenes, analizar texto.</div>
    </div>
    <div class="step-card">
      <div class="step-num">04</div>
      <div class="step-icon">🏆</div>
      <div class="step-title">Certificado final</div>
      <div class="step-desc">Al completar el programa recibes un certificado verificable que puedes compartir en LinkedIn y tu portafolio.</div>
    </div>
  </div>
</section>

<!-- CURRICULUM -->
<section id="curriculum">
  <div class="section-chip">Currículo</div>
  <h2 class="section-title">8 módulos que te llevan<br>de <em>cero a modelo</em></h2>
  <p class="section-body">Diseñado para personas sin experiencia técnica. Avanza a tu propio ritmo, con acceso de por vida.</p>
  <div class="curriculum-grid">
    <div class="module-card">
      <div class="module-num done">01</div>
      <div class="module-info">
        <div class="module-title">Fundamentos de Python</div>
        <div class="module-meta"><span>📚 8 lecciones</span><span>⏱ ~3 horas</span></div>
        <span class="module-tag free">Gratis</span>
      </div>
    </div>
    <div class="module-card">
      <div class="module-num done">02</div>
      <div class="module-info">
        <div class="module-title">Datos con Pandas & NumPy</div>
        <div class="module-meta"><span>📚 10 lecciones</span><span>⏱ ~4 horas</span></div>
        <span class="module-tag free">Gratis</span>
      </div>
    </div>
    <div class="module-card">
      <div class="module-num">03</div>
      <div class="module-info">
        <div class="module-title">Visualización de Datos</div>
        <div class="module-meta"><span>📚 6 lecciones</span><span>⏱ ~2 horas</span></div>
        <span class="module-tag">Incluido</span>
      </div>
    </div>
    <div class="module-card">
      <div class="module-num">04</div>
      <div class="module-info">
        <div class="module-title">Aprendizaje Supervisado</div>
        <div class="module-meta"><span>📚 12 lecciones</span><span>⏱ ~5 horas</span></div>
        <span class="module-tag">Incluido</span>
      </div>
    </div>
    <div class="module-card">
      <div class="module-num">05</div>
      <div class="module-info">
        <div class="module-title">Aprendizaje No Supervisado</div>
        <div class="module-meta"><span>📚 9 lecciones</span><span>⏱ ~3.5 horas</span></div>
        <span class="module-tag">Incluido</span>
      </div>
    </div>
    <div class="module-card">
      <div class="module-num">06</div>
      <div class="module-info">
        <div class="module-title">Redes Neuronales Básicas</div>
        <div class="module-meta"><span>📚 11 lecciones</span><span>⏱ ~5 horas</span></div>
        <span class="module-tag">Incluido</span>
      </div>
    </div>
    <div class="module-card">
      <div class="module-num">07</div>
      <div class="module-info">
        <div class="module-title">Procesamiento de Lenguaje</div>
        <div class="module-meta"><span>📚 8 lecciones</span><span>⏱ ~4 horas</span></div>
        <span class="module-tag">Incluido</span>
      </div>
    </div>
    <div class="module-card">
      <div class="module-num">08</div>
      <div class="module-info">
        <div class="module-title">Proyecto Final + Portafolio</div>
        <div class="module-meta"><span>📚 5 lecciones</span><span>⏱ ~6 horas</span></div>
        <span class="module-tag">Incluido</span>
      </div>
    </div>
  </div>
</section>

<!-- TESTIMONIALS -->
<section id="testimonials">
  <div class="section-chip">Testimonios</div>
  <h2 class="section-title">Lo que dicen<br>nuestros <em>estudiantes</em></h2>
  <div class="testi-grid">
    <div class="testi-card">
      <div class="testi-stars">★★★★★</div>
      <p class="testi-quote">Venía de las humanidades, nunca había programado. En 3 meses entendí regresión lineal y entrené mi primer modelo. La didáctica es increíble.</p>
      <div class="testi-author">
        <div class="testi-avatar">👩</div>
        <div>
          <div class="testi-name">Mariana López</div>
          <div class="testi-role">Estudiante de Psicología · Costa Rica</div>
        </div>
      </div>
    </div>
    <div class="testi-card">
      <div class="testi-stars">★★★★★</div>
      <p class="testi-quote">Había intentado con otros cursos en inglés y siempre me perdía. NeuralPath explica todo tan claro que lo entiendes en el primer intento.</p>
      <div class="testi-author">
        <div class="testi-avatar">👨</div>
        <div>
          <div class="testi-name">Carlos Ramírez</div>
          <div class="testi-role">Contador · México</div>
        </div>
      </div>
    </div>
    <div class="testi-card">
      <div class="testi-stars">★★★★★</div>
      <p class="testi-quote">Conseguí mi primer trabajo como analista de datos a los 3 meses de terminar el curso. El proyecto final del portafolio marcó la diferencia.</p>
      <div class="testi-author">
        <div class="testi-avatar">🧑</div>
        <div>
          <div class="testi-name">Sebastián Torres</div>
          <div class="testi-role">Analista de Datos · Colombia</div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- PRICING -->
<section id="pricing">
  <div class="section-chip">Precios</div>
  <h2 class="section-title">Invierte en tu futuro<br>con el plan <em>correcto</em></h2>
  <p class="section-body">Empieza gratis. Actualiza cuando quieras. Sin contratos ni sorpresas.</p>
  <div class="pricing-grid">
    <div class="price-card">
      <div class="price-plan">Gratuito</div>
      <div class="price-amount">$0</div>
      <div class="price-period">Para siempre</div>
      <ul class="price-features">
        <li><span class="price-check">✓</span> Módulos 1 y 2 completos</li>
        <li><span class="price-check">✓</span> Entorno de código en navegador</li>
        <li><span class="price-check">✓</span> Comunidad de Discord</li>
        <li><span style="color:#ccc">✗</span> Módulos 3–8</li>
        <li><span style="color:#ccc">✗</span> Certificado verificable</li>
        <li><span style="color:#ccc">✗</span> Mentoría con instructores</li>
      </ul>
      <a href="#cta-final" class="btn-price-dark">Empezar gratis</a>
    </div>
    <div class="price-card featured">
      <div class="price-badge">Más popular</div>
      <div class="price-plan">Completo</div>
      <div class="price-amount">$49</div>
      <div class="price-period">pago único · acceso de por vida</div>
      <ul class="price-features">
        <li><span class="price-check">✓</span> Los 8 módulos completos</li>
        <li><span class="price-check">✓</span> Entorno de código en navegador</li>
        <li><span class="price-check">✓</span> Comunidad de Discord</li>
        <li><span class="price-check">✓</span> Certificado verificable</li>
        <li><span class="price-check">✓</span> Proyectos guiados de portafolio</li>
        <li><span class="price-check">✓</span> Actualizaciones de por vida</li>
      </ul>
      <a href="#cta-final" class="btn-price-primary">Obtener acceso completo</a>
    </div>
  </div>
</section>

<!-- CTA FINAL -->
<section id="cta-final">
  <div class="section-chip" style="background:rgba(255,255,255,0.15);color:#fff;border-color:rgba(255,255,255,0.2)">¡Empieza hoy!</div>
  <h2 class="section-title">Tu camino al Machine Learning<br>comienza aquí</h2>
  <p class="section-body">Únete gratis hoy. Sin tarjeta de crédito. Sin instalaciones. Solo tú y tu primera línea de código.</p>
  <div class="cta-input-row">
    <input type="email" placeholder="tu@correo.com" id="emailInput" />
    <button class="btn-white" onclick="handleSignup()">Comenzar gratis →</button>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-logo"><span style="color:var(--accent)">●</span> NeuralPath</div>
  <div class="footer-links">
    <a href="#how">Cómo funciona</a>
    <a href="#curriculum">Currículo</a>
    <a href="#pricing">Precios</a>
    <a href="#testimonials">Testimonios</a>
    <a href="#cta-final">Contacto</a>
  </div>
  <p>© 2026 NeuralPath. Hecho con 🧠 en Latinoamérica.</p>
</footer>

<script>
  // Scroll reveal
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(e => {
      if (e.isIntersecting) {
        e.target.style.opacity = '1';
        e.target.style.transform = 'translateY(0)';
      }
    });
  }, { threshold: 0.08 });

  document.querySelectorAll(
    '.step-card, .module-card, .testi-card, .price-card'
  ).forEach((el, i) => {
    el.style.opacity = '0';
    el.style.transform = 'translateY(22px)';
    el.style.transition = `opacity 0.5s ${i * 0.06}s ease, transform 0.5s ${i * 0.06}s ease`;
    observer.observe(el);
  });

  // Signup
  function handleSignup() {
    const email = document.getElementById('emailInput').value.trim();
    if (!email || !email.includes('@')) {
      alert('Por favor ingresa un correo válido.');
      return;
    }
    alert(`¡Bienvenido/a a NeuralPath! 🧠\nTe enviamos un correo a ${email} para activar tu cuenta gratuita.`);
    document.getElementById('emailInput').value = '';
  }
</script>
</body>
</html>
