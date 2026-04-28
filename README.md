<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Academia Taekwondo</title>
  <link href="https://fonts.googleapis.com/css2?family=Black+Han+Sans&family=Noto+Sans+KR:wght@300;400;700&family=Bebas+Neue&display=swap" rel="stylesheet" />
  <style>
    :root {
      --red: #c0392b;
      --dark-red: #922b21;
      --gold: #d4a017;
      --black: #0a0a0a;
      --dark: #111111;
      --mid: #1c1c1c;
      --light: #f5f0e8;
      --white: #ffffff;
      --gray: #888;
    }

    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    html { scroll-behavior: smooth; }

    body {
      background: var(--black);
      color: var(--light);
      font-family: 'Noto Sans KR', sans-serif;
      overflow-x: hidden;
    }

    /* ─── NAVBAR ─── */
    nav {
      position: fixed; top: 0; width: 100%; z-index: 100;
      display: flex; align-items: center; justify-content: space-between;
      padding: 1.2rem 4rem;
      background: rgba(10,10,10,0.85);
      backdrop-filter: blur(12px);
      border-bottom: 1px solid rgba(192,57,43,0.3);
    }
    .logo {
      font-family: 'Bebas Neue', sans-serif;
      font-size: 1.8rem;
      letter-spacing: 0.1em;
      color: var(--white);
    }
    .logo span { color: var(--red); }
    nav ul { list-style: none; display: flex; gap: 2.5rem; }
    nav ul a {
      color: var(--light); text-decoration: none;
      font-size: 0.85rem; letter-spacing: 0.15em; text-transform: uppercase;
      font-weight: 700;
      transition: color 0.2s;
    }
    nav ul a:hover { color: var(--gold); }
    .nav-cta {
      background: var(--red); color: var(--white) !important;
      padding: 0.5rem 1.4rem; border-radius: 2px;
      transition: background 0.2s !important;
    }
    .nav-cta:hover { background: var(--dark-red) !important; color: var(--white) !important; }

    /* ─── HERO ─── */
    #hero {
      min-height: 100vh;
      display: flex; flex-direction: column;
      align-items: center; justify-content: center;
      position: relative; overflow: hidden;
      text-align: center;
      padding: 0 2rem;
    }
    .hero-bg {
      position: absolute; inset: 0;
      background:
        radial-gradient(ellipse 60% 60% at 70% 50%, rgba(192,57,43,0.18) 0%, transparent 70%),
        radial-gradient(ellipse 40% 40% at 20% 80%, rgba(212,160,23,0.08) 0%, transparent 60%),
        var(--black);
    }
    .hero-lines {
      position: absolute; inset: 0; pointer-events: none;
      background-image:
        repeating-linear-gradient(0deg, transparent, transparent 79px, rgba(255,255,255,0.02) 80px),
        repeating-linear-gradient(90deg, transparent, transparent 79px, rgba(255,255,255,0.02) 80px);
    }
    .hero-kicker {
      position: relative;
      font-size: 0.75rem; letter-spacing: 0.4em; text-transform: uppercase;
      color: var(--gold); margin-bottom: 1.5rem;
      font-weight: 700;
      animation: fadeUp 0.8s ease both;
    }
    .hero-kicker::before, .hero-kicker::after {
      content: ''; display: inline-block; width: 40px; height: 1px;
      background: var(--gold); vertical-align: middle; margin: 0 12px;
    }
    .hero-title {
      position: relative;
      font-family: 'Bebas Neue', sans-serif;
      font-size: clamp(4rem, 14vw, 11rem);
      line-height: 0.9;
      color: var(--white);
      letter-spacing: 0.03em;
      animation: fadeUp 0.8s 0.15s ease both;
    }
    .hero-title .red { color: var(--red); }
    .hero-title .outline {
      -webkit-text-stroke: 2px var(--white);
      color: transparent;
    }
    .hero-sub {
      position: relative;
      font-size: 1rem; font-weight: 300; letter-spacing: 0.1em;
      color: var(--gray); margin-top: 1.5rem; margin-bottom: 3rem;
      max-width: 500px;
      animation: fadeUp 0.8s 0.3s ease both;
    }
    .hero-btns {
      position: relative; display: flex; gap: 1rem; flex-wrap: wrap; justify-content: center;
      animation: fadeUp 0.8s 0.45s ease both;
    }
    .btn-primary {
      background: var(--red); color: var(--white);
      padding: 1rem 2.5rem; font-family: 'Bebas Neue', sans-serif;
      font-size: 1.1rem; letter-spacing: 0.15em;
      border: none; cursor: pointer; border-radius: 2px;
      transition: background 0.2s, transform 0.15s;
      text-decoration: none;
    }
    .btn-primary:hover { background: var(--dark-red); transform: translateY(-2px); }
    .btn-outline {
      background: transparent; color: var(--light);
      padding: 1rem 2.5rem; font-family: 'Bebas Neue', sans-serif;
      font-size: 1.1rem; letter-spacing: 0.15em;
      border: 1px solid rgba(255,255,255,0.3); cursor: pointer; border-radius: 2px;
      transition: border-color 0.2s, transform 0.15s;
      text-decoration: none;
    }
    .btn-outline:hover { border-color: var(--gold); color: var(--gold); transform: translateY(-2px); }
    .hero-scroll {
      position: absolute; bottom: 2rem; left: 50%; transform: translateX(-50%);
      display: flex; flex-direction: column; align-items: center; gap: 0.4rem;
      font-size: 0.7rem; letter-spacing: 0.25em; color: var(--gray); text-transform: uppercase;
      animation: bounce 2s infinite;
    }
    .hero-scroll::after {
      content: ''; display: block; width: 1px; height: 40px; background: var(--red);
    }

    /* ─── STATS STRIP ─── */
    .stats-strip {
      background: var(--red);
      display: flex; justify-content: space-around; flex-wrap: wrap;
      padding: 2rem 4rem; gap: 1rem;
    }
    .stat { text-align: center; }
    .stat-num {
      font-family: 'Bebas Neue', sans-serif;
      font-size: 3rem; color: var(--white); line-height: 1;
    }
    .stat-label {
      font-size: 0.7rem; letter-spacing: 0.2em; text-transform: uppercase;
      color: rgba(255,255,255,0.7); margin-top: 0.2rem;
    }

    /* ─── SECTIONS ─── */
    section { padding: 6rem 4rem; }
    .section-label {
      font-size: 0.7rem; letter-spacing: 0.4em; text-transform: uppercase;
      color: var(--red); font-weight: 700; margin-bottom: 1rem;
    }
    .section-title {
      font-family: 'Bebas Neue', sans-serif;
      font-size: clamp(2.5rem, 5vw, 4rem);
      color: var(--white); line-height: 1.05;
      margin-bottom: 1.5rem;
    }
    .section-title em { color: var(--red); font-style: normal; }
    .section-body {
      font-size: 0.95rem; color: var(--gray); line-height: 1.8;
      max-width: 540px;
    }

    /* ─── ABOUT ─── */
    #about { background: var(--dark); }
    .about-grid {
      display: grid; grid-template-columns: 1fr 1fr; gap: 5rem; align-items: center;
      max-width: 1200px; margin: 0 auto;
    }
    .about-visual {
      position: relative; height: 420px;
    }
    .about-card {
      position: absolute;
      background: var(--mid);
      border: 1px solid rgba(255,255,255,0.05);
      border-radius: 4px;
      overflow: hidden;
    }
    .about-card.main {
      width: 75%; height: 100%; left: 0; top: 0;
      display: flex; align-items: center; justify-content: center;
    }
    .about-card.accent {
      width: 45%; height: 55%; right: 0; bottom: 0;
      display: flex; flex-direction: column; align-items: center;
      justify-content: center; gap: 0.5rem;
      border-left: 3px solid var(--red);
    }
    .about-icon {
      font-size: 5rem; line-height: 1;
    }
    .about-card.main .about-icon { font-size: 8rem; }
    .about-card-label {
      font-family: 'Bebas Neue', sans-serif;
      font-size: 1.3rem; letter-spacing: 0.1em; color: var(--white);
    }
    .about-card-sub { font-size: 0.7rem; color: var(--gray); letter-spacing: 0.1em; }
    .values-list { margin-top: 2rem; display: flex; flex-direction: column; gap: 0.8rem; }
    .value-item {
      display: flex; align-items: center; gap: 0.8rem;
      font-size: 0.9rem; color: var(--light);
    }
    .value-dot {
      width: 8px; height: 8px; background: var(--red); border-radius: 50%; flex-shrink: 0;
    }

    /* ─── PROGRAMS ─── */
    #programs { background: var(--black); }
    .programs-header { max-width: 1200px; margin: 0 auto 3.5rem; }
    .programs-grid {
      display: grid; grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
      gap: 1.5rem; max-width: 1200px; margin: 0 auto;
    }
    .program-card {
      background: var(--mid);
      border: 1px solid rgba(255,255,255,0.06);
      border-radius: 4px; overflow: hidden;
      transition: transform 0.25s, border-color 0.25s;
      cursor: default;
    }
    .program-card:hover { transform: translateY(-6px); border-color: var(--red); }
    .program-top {
      padding: 2rem 2rem 1.5rem;
      border-bottom: 1px solid rgba(255,255,255,0.05);
    }
    .program-emoji { font-size: 2.5rem; margin-bottom: 1rem; }
    .program-name {
      font-family: 'Bebas Neue', sans-serif;
      font-size: 1.6rem; color: var(--white); letter-spacing: 0.05em;
    }
    .program-age {
      font-size: 0.7rem; letter-spacing: 0.2em; text-transform: uppercase;
      color: var(--gold); margin-top: 0.2rem;
    }
    .program-bottom { padding: 1.5rem 2rem; }
    .program-desc { font-size: 0.88rem; color: var(--gray); line-height: 1.7; }
    .program-tag {
      display: inline-block; margin-top: 1rem;
      background: rgba(192,57,43,0.15); color: var(--red);
      border: 1px solid rgba(192,57,43,0.4);
      font-size: 0.7rem; letter-spacing: 0.15em; text-transform: uppercase;
      padding: 0.3rem 0.8rem; border-radius: 2px;
    }

    /* ─── INSTRUCTORES ─── */
    #instructors { background: var(--dark); }
    .instructors-inner { max-width: 1200px; margin: 0 auto; }
    .instructors-header { margin-bottom: 3.5rem; }
    .instructors-grid {
      display: grid; grid-template-columns: repeat(auto-fit, minmax(220px, 1fr)); gap: 2rem;
    }
    .instructor-card {
      text-align: center;
      transition: transform 0.2s;
    }
    .instructor-card:hover { transform: translateY(-4px); }
    .instructor-avatar {
      width: 120px; height: 120px; border-radius: 50%;
      background: var(--mid); margin: 0 auto 1.2rem;
      display: flex; align-items: center; justify-content: center;
      font-size: 3rem;
      border: 3px solid var(--red);
    }
    .instructor-name {
      font-family: 'Bebas Neue', sans-serif;
      font-size: 1.4rem; color: var(--white); letter-spacing: 0.05em;
    }
    .instructor-belt {
      font-size: 0.7rem; letter-spacing: 0.2em; text-transform: uppercase;
      color: var(--gold); margin-top: 0.2rem;
    }
    .instructor-bio {
      font-size: 0.82rem; color: var(--gray); margin-top: 0.6rem; line-height: 1.6;
    }

    /* ─── HORARIOS ─── */
    #schedule { background: var(--black); }
    .schedule-inner { max-width: 900px; margin: 0 auto; }
    .schedule-header { margin-bottom: 3rem; }
    .schedule-grid {
      display: grid; grid-template-columns: 1fr;
      gap: 1px; background: rgba(255,255,255,0.05);
      border: 1px solid rgba(255,255,255,0.05); border-radius: 4px; overflow: hidden;
    }
    .schedule-row {
      display: grid; grid-template-columns: 120px 1fr 120px;
      align-items: center; gap: 1rem;
      background: var(--mid); padding: 1.2rem 2rem;
      transition: background 0.2s;
    }
    .schedule-row:hover { background: #222; }
    .schedule-row.head {
      background: var(--red); font-family: 'Bebas Neue', sans-serif;
      letter-spacing: 0.1em; font-size: 1rem;
    }
    .schedule-day {
      font-size: 0.75rem; letter-spacing: 0.15em; text-transform: uppercase;
      color: var(--gold); font-weight: 700;
    }
    .schedule-class { font-size: 0.92rem; color: var(--light); }
    .schedule-time { font-size: 0.82rem; color: var(--gray); text-align: right; }

    /* ─── CTA ─── */
    #cta {
      background: var(--red);
      text-align: center; padding: 6rem 4rem;
    }
    #cta .section-label { color: rgba(255,255,255,0.6); }
    #cta .section-title { color: var(--white); margin: 0 auto 1rem; }
    #cta .section-body { color: rgba(255,255,255,0.75); margin: 0 auto 2.5rem; }
    .cta-form {
      display: flex; gap: 1rem; flex-wrap: wrap; justify-content: center; max-width: 500px; margin: 0 auto;
    }
    .cta-form input {
      flex: 1; min-width: 180px;
      padding: 0.9rem 1.2rem;
      background: rgba(0,0,0,0.25); border: 1px solid rgba(255,255,255,0.3);
      color: var(--white); border-radius: 2px;
      font-family: 'Noto Sans KR', sans-serif; font-size: 0.9rem;
    }
    .cta-form input::placeholder { color: rgba(255,255,255,0.5); }
    .cta-form input:focus { outline: none; border-color: var(--white); }
    .btn-dark {
      background: var(--black); color: var(--white);
      padding: 0.9rem 2rem; font-family: 'Bebas Neue', sans-serif;
      font-size: 1rem; letter-spacing: 0.15em;
      border: none; cursor: pointer; border-radius: 2px;
      transition: background 0.2s;
    }
    .btn-dark:hover { background: #1a1a1a; }

    /* ─── FOOTER ─── */
    footer {
      background: #060606;
      padding: 3rem 4rem;
      display: flex; flex-wrap: wrap; gap: 2rem;
      align-items: center; justify-content: space-between;
      border-top: 1px solid rgba(255,255,255,0.05);
    }
    .footer-logo {
      font-family: 'Bebas Neue', sans-serif;
      font-size: 1.5rem; color: var(--white); letter-spacing: 0.1em;
    }
    .footer-logo span { color: var(--red); }
    .footer-links { display: flex; gap: 2rem; flex-wrap: wrap; }
    .footer-links a {
      color: var(--gray); text-decoration: none;
      font-size: 0.8rem; letter-spacing: 0.1em; text-transform: uppercase;
      transition: color 0.2s;
    }
    .footer-links a:hover { color: var(--white); }
    .footer-copy {
      font-size: 0.75rem; color: var(--gray);
    }

    /* ─── ANIMATIONS ─── */
    @keyframes fadeUp {
      from { opacity: 0; transform: translateY(30px); }
      to   { opacity: 1; transform: translateY(0); }
    }
    @keyframes bounce {
      0%, 100% { transform: translateX(-50%) translateY(0); }
      50%       { transform: translateX(-50%) translateY(8px); }
    }

    /* ─── RESPONSIVE ─── */
    @media (max-width: 768px) {
      nav { padding: 1rem 1.5rem; }
      nav ul { display: none; }
      section { padding: 4rem 1.5rem; }
      .stats-strip { padding: 2rem 1.5rem; }
      .about-grid { grid-template-columns: 1fr; }
      .about-visual { height: 260px; margin-bottom: 2rem; }
      footer { padding: 2rem 1.5rem; flex-direction: column; align-items: flex-start; }
      .schedule-row { grid-template-columns: 1fr; gap: 0.3rem; padding: 1rem 1.5rem; }
      .schedule-time { text-align: left; }
    }
  </style>
</head>
<body>

  <!-- NAVBAR -->
  <nav>
    <div class="logo">TAEKWONDO <span>ACADEMIA</span></div>
    <ul>
      <li><a href="#about">Nosotros</a></li>
      <li><a href="#programs">Programas</a></li>
      <li><a href="#instructors">Instructores</a></li>
      <li><a href="#schedule">Horarios</a></li>
      <li><a href="#cta" class="nav-cta">Inscríbete</a></li>
    </ul>
  </nav>

  <!-- HERO -->
  <section id="hero">
    <div class="hero-bg"></div>
    <div class="hero-lines"></div>
    <p class="hero-kicker">Arte Marcial · Disciplina · Honor</p>
    <h1 class="hero-title">
      <span class="outline">TAE</span><br>
      <span class="red">KWON</span><br>
      DO
    </h1>
    <p class="hero-sub">Forjamos campeones dentro y fuera del tatami. Entrena con los mejores.</p>
    <div class="hero-btns">
      <a href="#cta" class="btn-primary">Clase de Prueba Gratis</a>
      <a href="#programs" class="btn-outline">Ver Programas</a>
    </div>
    <div class="hero-scroll">Scroll</div>
  </section>

  <!-- STATS -->
  <div class="stats-strip">
    <div class="stat">
      <div class="stat-num">15+</div>
      <div class="stat-label">Años de experiencia</div>
    </div>
    <div class="stat">
      <div class="stat-num">500+</div>
      <div class="stat-label">Estudiantes activos</div>
    </div>
    <div class="stat">
      <div class="stat-num">80+</div>
      <div class="stat-label">Medallas nacionales</div>
    </div>
    <div class="stat">
      <div class="stat-num">6</div>
      <div class="stat-label">Instructores certificados</div>
    </div>
  </div>

  <!-- ABOUT -->
  <section id="about">
    <div class="about-grid">
      <div class="about-visual">
        <div class="about-card main">
          <span class="about-icon">🥋</span>
        </div>
        <div class="about-card accent">
          <span class="about-icon">🏅</span>
          <span class="about-card-label">Campeones</span>
          <span class="about-card-sub">nacionales e internacionales</span>
        </div>
      </div>
      <div class="about-text">
        <p class="section-label">Sobre Nosotros</p>
        <h2 class="section-title">Más que un<br>deporte.<br><em>Un estilo de vida.</em></h2>
        <p class="section-body">
          Nuestra academia combina la tradición del Taekwondo con métodos de entrenamiento modernos.
          Desarrollamos atletas completos: físicamente fuertes, mentalmente resilientes y éticamente comprometidos.
        </p>
        <div class="values-list">
          <div class="value-item"><div class="value-dot"></div>Entrenamiento personalizado para cada nivel</div>
          <div class="value-item"><div class="value-dot"></div>Ambiente seguro, respetuoso e inclusivo</div>
          <div class="value-item"><div class="value-dot"></div>Preparación para competencias locales e internacionales</div>
          <div class="value-item"><div class="value-dot"></div>Valores de disciplina, respeto y perseverancia</div>
        </div>
      </div>
    </div>
  </section>

  <!-- PROGRAMS -->
  <section id="programs">
    <div class="programs-header">
      <p class="section-label">Programas</p>
      <h2 class="section-title">Entrenamiento para<br><em>cada etapa</em></h2>
    </div>
    <div class="programs-grid">
      <div class="program-card">
        <div class="program-top">
          <div class="program-emoji">🧒</div>
          <div class="program-name">Infantil</div>
          <div class="program-age">4 – 7 años</div>
        </div>
        <div class="program-bottom">
          <p class="program-desc">Clases lúdicas y seguras para introducir a los más pequeños al arte marcial. Coordinación, equilibrio y valores desde temprana edad.</p>
          <span class="program-tag">Iniciación</span>
        </div>
      </div>
      <div class="program-card">
        <div class="program-top">
          <div class="program-emoji">🧑</div>
          <div class="program-name">Juvenil</div>
          <div class="program-age">8 – 15 años</div>
        </div>
        <div class="program-bottom">
          <p class="program-desc">Técnica, competencia y formación de carácter. Preparamos a jóvenes para cinturones avanzados y torneos nacionales.</p>
          <span class="program-tag">Intermedio · Avanzado</span>
        </div>
      </div>
      <div class="program-card">
        <div class="program-top">
          <div class="program-emoji">🧑‍💼</div>
          <div class="program-name">Adultos</div>
          <div class="program-age">16 años en adelante</div>
        </div>
        <div class="program-bottom">
          <p class="program-desc">Fitness, defensa personal y arte marcial para adultos de todos los niveles. Fuerza, flexibilidad y confianza en cada clase.</p>
          <span class="program-tag">Todos los niveles</span>
        </div>
      </div>
      <div class="program-card">
        <div class="program-top">
          <div class="program-emoji">🏆</div>
          <div class="program-name">Élite</div>
          <div class="program-age">Selección competitiva</div>
        </div>
        <div class="program-bottom">
          <p class="program-desc">Programa de alto rendimiento para atletas con miras a torneos regionales, nacionales e internacionales. Solo por invitación.</p>
          <span class="program-tag">Alto rendimiento</span>
        </div>
      </div>
    </div>
  </section>

  <!-- INSTRUCTORS -->
  <section id="instructors">
    <div class="instructors-inner">
      <div class="instructors-header">
        <p class="section-label">Equipo</p>
        <h2 class="section-title">Nuestros <em>Instructores</em></h2>
        <p class="section-body">Maestros certificados con experiencia nacional e internacional, comprometidos con tu desarrollo.</p>
      </div>
      <div class="instructors-grid">
        <div class="instructor-card">
          <div class="instructor-avatar">🥋</div>
          <div class="instructor-name">Master Kim</div>
          <div class="instructor-belt">Cinturón Negro 7° Dan</div>
          <p class="instructor-bio">Fundador de la academia. 25 años formando campeones en Costa Rica y Corea del Sur.</p>
        </div>
        <div class="instructor-card">
          <div class="instructor-avatar">🥋</div>
          <div class="instructor-name">Profa. Valeria</div>
          <div class="instructor-belt">Cinturón Negro 4° Dan</div>
          <p class="instructor-bio">Especialista en programas infantiles y juveniles. Medalla de plata en Centroamérica 2019.</p>
        </div>
        <div class="instructor-card">
          <div class="instructor-avatar">🥋</div>
          <div class="instructor-name">Prof. Andrés</div>
          <div class="instructor-belt">Cinturón Negro 3° Dan</div>
          <p class="instructor-bio">Entrenador de élite y preparación física. Especialista en Poomsae y combate olímpico.</p>
        </div>
        <div class="instructor-card">
          <div class="instructor-avatar">🥋</div>
          <div class="instructor-name">Profa. Sofía</div>
          <div class="instructor-belt">Cinturón Negro 2° Dan</div>
          <p class="instructor-bio">Instructora de adultos y defensa personal. Certificada por la Federación Mundial de Taekwondo.</p>
        </div>
      </div>
    </div>
  </section>

  <!-- SCHEDULE -->
  <section id="schedule">
    <div class="schedule-inner">
      <div class="schedule-header">
        <p class="section-label">Horarios</p>
        <h2 class="section-title">Encuentra tu <em>clase</em></h2>
      </div>
      <div class="schedule-grid">
        <div class="schedule-row head">
          <span>Día</span><span>Clase</span><span style="text-align:right">Horario</span>
        </div>
        <div class="schedule-row">
          <span class="schedule-day">Lun · Mié · Vie</span>
          <span class="schedule-class">Infantil (4–7 años)</span>
          <span class="schedule-time">3:30 – 4:30 pm</span>
        </div>
        <div class="schedule-row">
          <span class="schedule-day">Lun · Mié · Vie</span>
          <span class="schedule-class">Juvenil (8–15 años)</span>
          <span class="schedule-time">5:00 – 6:30 pm</span>
        </div>
        <div class="schedule-row">
          <span class="schedule-day">Mar · Jue · Sáb</span>
          <span class="schedule-class">Adultos – Todos los niveles</span>
          <span class="schedule-time">6:00 – 7:30 pm</span>
        </div>
        <div class="schedule-row">
          <span class="schedule-day">Sábado</span>
          <span class="schedule-class">Élite – Alto Rendimiento</span>
          <span class="schedule-time">8:00 – 10:00 am</span>
        </div>
        <div class="schedule-row">
          <span class="schedule-day">Sábado</span>
          <span class="schedule-class">Defensa Personal – Adultos</span>
          <span class="schedule-time">10:30 am – 12:00 pm</span>
        </div>
      </div>
    </div>
  </section>

  <!-- CTA -->
  <section id="cta">
    <p class="section-label">¡Únete hoy!</p>
    <h2 class="section-title">Tu primera clase<br>es <em style="color:var(--black)">GRATIS</em></h2>
    <p class="section-body">Déjanos tu nombre y correo y nos ponemos en contacto para agendar tu clase de prueba.</p>
    <div class="cta-form">
      <input type="text" placeholder="Tu nombre" />
      <input type="email" placeholder="Tu correo electrónico" />
      <button class="btn-dark" onclick="handleSubmit()">Inscribirme</button>
    </div>
  </section>

  <!-- FOOTER -->
  <footer>
    <div class="footer-logo">TAEKWONDO <span>ACADEMIA</span></div>
    <div class="footer-links">
      <a href="#about">Nosotros</a>
      <a href="#programs">Programas</a>
      <a href="#schedule">Horarios</a>
      <a href="#cta">Contacto</a>
    </div>
    <div class="footer-copy">© 2026 Academia Taekwondo. Todos los derechos reservados.</div>
  </footer>

  <script>
    // Smooth reveal on scroll
    const observer = new IntersectionObserver((entries) => {
      entries.forEach(e => {
        if (e.isIntersecting) {
          e.target.style.opacity = '1';
          e.target.style.transform = 'translateY(0)';
        }
      });
    }, { threshold: 0.1 });

    document.querySelectorAll('.program-card, .instructor-card, .schedule-row:not(.head)').forEach(el => {
      el.style.opacity = '0';
      el.style.transform = 'translateY(20px)';
      el.style.transition = 'opacity 0.5s ease, transform 0.5s ease';
      observer.observe(el);
    });

    // Form submit
    function handleSubmit() {
      const inputs = document.querySelectorAll('.cta-form input');
      const name = inputs[0].value.trim();
      const email = inputs[1].value.trim();
      if (!name || !email) {
        alert('Por favor completa tu nombre y correo.');
        return;
      }
      alert(`¡Gracias, ${name}! Nos pondremos en contacto contigo pronto a ${email}. 🥋`);
      inputs.forEach(i => i.value = '');
    }
  </script>
</body>
</html>
