<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Inteligencia Artificial y Robots</title>
  <meta name="description" content="Página web básica sobre Inteligencia Artificial y Robots creada con HTML, CSS y JavaScript." />
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;800&display=swap" rel="stylesheet">
  <style>
    :root {
      --bg: #0b0d10;
      --bg-soft: #11151b;
      --card: #151a21;
      --text: #e8eef7;
      --muted: #a8b3c5;
      --accent: #7c5cff;
      --accent-2: #21c1b3;
      --ring: rgba(124, 92, 255, 0.45);
      --shadow: 0 10px 30px rgba(0,0,0,.35);
    }

    * { box-sizing: border-box; }
    html { scroll-behavior: smooth; }
    body {
      margin: 0;
      font-family: Inter, system-ui, -apple-system, Segoe UI, Roboto, Ubuntu, Cantarell, Noto Sans, "Helvetica Neue", Arial, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol", "Noto Color Emoji", sans-serif;
      color: var(--text);
      background: radial-gradient(1200px 600px at 80% -10%, rgba(124,92,255,.15), transparent 60%),
                  radial-gradient(1000px 600px at 0% 10%, rgba(33,193,179,.12), transparent 60%),
                  var(--bg);
    }

    /* ====== NAV ====== */
    .nav {
      position: sticky;
      top: 0;
      z-index: 50;
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: .9rem 1rem;
      background: rgba(11,13,16,.65);
      backdrop-filter: blur(10px);
      border-bottom: 1px solid rgba(255,255,255,.06);
    }
    .brand {
      display: flex; align-items: center; gap: .65rem; font-weight: 800; letter-spacing: .3px;
    }
    .brand .logo {
      display: grid; place-items: center; width: 36px; height: 36px; border-radius: 10px; background: linear-gradient(135deg, var(--accent), var(--accent-2)); box-shadow: var(--shadow);
      font-size: 20px;
    }
    .nav a { color: var(--text); text-decoration: none; opacity: .85; }
    .nav a:hover { opacity: 1; }
    .links { display: none; gap: 1rem; align-items: center; }
    .btn { border: 1px solid rgba(255,255,255,.12); background: transparent; color: var(--text); padding: .6rem .9rem; border-radius: 12px; cursor: pointer; font-weight: 600; }
    .btn:hover { border-color: rgba(255,255,255,.3); }
    .btn-primary { background: linear-gradient(135deg, var(--accent), var(--accent-2)); border: none; color: #0a0c0f; box-shadow: var(--shadow); }

    .menu { display: inline-flex; gap: .5rem; }
    .menu-btn { background: transparent; border: 1px solid rgba(255,255,255,.12); color: var(--text); border-radius: 10px; padding: .4rem .6rem; display: none; }

    /* ====== LAYOUT ====== */
    .container { width: min(1100px, 92%); margin-inline: auto; }
    .grid { display: grid; gap: 1.2rem; }

    /* ====== HERO ====== */
    .hero { padding: 4.5rem 0 3rem; }
    .hero-inner { display: grid; grid-template-columns: 1.2fr 1fr; gap: 2rem; align-items: center; }
    .title { font-size: clamp(2rem, 4vw, 3rem); margin: 0; line-height: 1.1; }
    .lead { color: var(--muted); font-size: clamp(1rem, 2vw, 1.15rem); }
    .kpis { display: grid; grid-template-columns: repeat(3, 1fr); gap: .9rem; margin-top: 1.2rem; }
    .kpi { background: var(--card); border: 1px solid rgba(255,255,255,.06); border-radius: 16px; padding: .9rem; text-align: center; box-shadow: var(--shadow); }
    .kpi b { font-size: 1.3rem; }
    .hero-visual { position: relative; background: radial-gradient(400px 200px at 60% 30%, rgba(124, 92, 255, 0.4), transparent 60%), var(--bg-soft); border: 1px solid rgba(255,255,255,.08); border-radius: 18px; min-height: 320px; display:grid; place-items:center; overflow: hidden; }
    .chip { position: absolute; background: rgba(255,255,255,.06); border: 1px solid rgba(255,255,255,.12); padding: .5rem .7rem; border-radius: 999px; font-size: .9rem; }
    .chip:nth-child(1){ top: 18px; right: 18px; }
    .chip:nth-child(2){ bottom: 18px; left: 18px; }
    .bot { width: 180px; aspect-ratio: 1; border-radius: 24px; background: linear-gradient(160deg, #1a2230, #0f141b); border: 1px solid rgba(255,255,255,.08); display:grid; place-items:center; box-shadow: 0 30px 60px rgba(124,92,255,.22); }
    .bot svg { width: 120px; height: 120px; }

    /* ====== SECTIONS ====== */
    section { padding: 2.5rem 0; }
    .section-title { font-size: 1.6rem; margin-bottom: .6rem; }
    .muted { color: var(--muted); }

    .cards { display:grid; grid-template-columns: repeat(3, 1fr); gap: 1rem; }
    .card { background: var(--card); border: 1px solid rgba(255,255,255,.08); border-radius: 18px; padding: 1rem; box-shadow: var(--shadow); }
    .card h3 { margin-top: 0; }

    .gallery { display:grid; grid-template-columns: repeat(4, 1fr); gap: .8rem; }
    .gallery div { height: 110px; border-radius: 14px; background: linear-gradient(135deg, rgba(124,92,255,.25), rgba(33,193,179,.25)); border: 1px solid rgba(255,255,255,.08); }

    /* ====== TIMELINE ====== */
    .timeline { border-left: 2px dashed rgba(255,255,255,.14); padding-left: 1rem; }
    .tl-item { margin-bottom: 1rem; position: relative; }
    .tl-item::before { content: ""; position: absolute; left: -10px; top: .3rem; width: 10px; height: 10px; background: linear-gradient(135deg, var(--accent), var(--accent-2)); border-radius: 999px; }

    /* ====== FAQ ====== */
    .faq { display: grid; gap: .7rem; }
    .faq details { background: var(--card); border: 1px solid rgba(255,255,255,.08); border-radius: 16px; padding: .8rem 1rem; }
    .faq summary { cursor: pointer; font-weight: 600; }

    /* ====== FOOTER ====== */
    footer { padding: 2rem 0 4rem; color: var(--muted); text-align: center; }

    /* ====== UTIL ====== */
    .row { display:flex; gap: .6rem; flex-wrap: wrap; align-items: center; }
    .pill { padding: .3rem .6rem; border-radius: 999px; border: 1px solid rgba(255,255,255,.16); font-size: .85rem; }
    .note { font-size: .95rem; }
    .sr { position:absolute; width:1px; height:1px; padding:0; margin:-1px; overflow:hidden; clip:rect(0,0,0,0); border:0; }

    /* ====== RESPONSIVE ====== */
    @media (max-width: 960px){
      .hero-inner { grid-template-columns: 1fr; }
      .cards { grid-template-columns: 1fr 1fr; }
      .gallery { grid-template-columns: repeat(3, 1fr); }
      .links { display: none; }
      .menu-btn { display: inline-flex; }
    }
    @media (max-width: 640px){
      .cards { grid-template-columns: 1fr; }
      .gallery { grid-template-columns: repeat(2, 1fr); }
      .kpis { grid-template-columns: repeat(2, 1fr); }
    }

    /* ====== MOBILE SHEET ====== */
    .sheet { position: fixed; inset: auto 0 0 0; transform: translateY(105%); background: var(--bg-soft); border-top: 1px solid rgba(255,255,255,.08); padding: 1rem; transition: transform .25s ease; box-shadow: 0 -10px 30px rgba(0,0,0,.4); }
    .sheet.open { transform: translateY(0); }
    .sheet a { display:block; padding: .9rem 1rem; border-radius: 12px; border: 1px solid rgba(255,255,255,.08); margin-bottom: .6rem; background: rgba(255,255,255,.02); }
  </style>
</head>
<body>
  <header class="nav">
    <div class="brand">
      <div class="logo" aria-hidden="true">🤖</div>
      <a href="#home" aria-label="Ir al inicio">IA & Robots</a>
    </div>
    <nav class="links" aria-label="Navegación principal">
      <a href="#que-es">¿Qué es la IA?</a>
      <a href="#robots">Robots</a>
      <a href="#aplicaciones">Aplicaciones</a>
      <a href="#linea-tiempo">Historia</a>
      <a href="#faq">FAQ</a>
    </nav>
    <div class="menu">
      <button class="btn" id="themeBtn" aria-label="Cambiar tema">Tema</button>
      <button class="menu-btn" id="menuBtn" aria-expanded="false" aria-controls="mobileSheet">Menú</button>
    </div>
  </header>

  <div id="mobileSheet" class="sheet" role="dialog" aria-modal="true" aria-label="Menú móvil">
    <a href="#que-es">¿Qué es la IA?</a>
    <a href="#robots">Robots</a>
    <a href="#aplicaciones">Aplicaciones</a>
    <a href="#linea-tiempo">Historia</a>
    <a href="#faq">FAQ</a>
  </div>

  <main id="home" class="container">
    <section class="hero">
      <div class="hero-inner">
        <div>
          <p class="pill">Guía básica • HTML + CSS + JS</p>
          <h1 class="title">Inteligencia Artificial y Robots</h1>
          <p class="lead">Una introducción sencilla para comprender qué es la IA, cómo funcionan los robots y en qué tareas ya están presentes hoy.</p>
          <div class="row" style="margin-top:1rem;">
            <a class="btn btn-primary" href="#que-es">Comenzar</a>
            <a class="btn" href="#aplicaciones">Ver aplicaciones</a>
          </div>
          <div class="kpis">
            <div class="kpi"><b>1950 → hoy</b><div class="muted">Evolución de la IA</div></div>
            <div class="kpi"><b>4 tipos</b><div class="muted">Robots comunes</div></div>
            <div class="kpi"><b>∞</b><div class="muted">Casos de uso</div></div>
          </div>
        </div>
        <div class="hero-visual">
          <span class="chip">⚡ Aprendizaje automático</span>
          <span class="chip">🦾 Robótica colaborativa</span>
          <div class="bot" aria-hidden="true">
            <!-- Simple robot SVG -->
            <svg viewBox="0 0 200 200" fill="none" xmlns="http://www.w3.org/2000/svg" aria-hidden="true">
              <rect x="40" y="60" width="120" height="90" rx="16" fill="#202a36" stroke="rgba(255,255,255,.12)"/>
              <circle cx="80" cy="100" r="12" fill="#7c5cff"/>
              <circle cx="120" cy="100" r="12" fill="#21c1b3"/>
              <rect x="85" y="30" width="30" height="20" rx="6" fill="#202a36" stroke="rgba(255,255,255,.12)"/>
              <rect x="90" y="20" width="20" height="10" rx="5" fill="#7c5cff"/>
              <rect x="25" y="85" width="15" height="30" rx="6" fill="#202a36"/>
              <rect x="160" y="85" width="15" height="30" rx="6" fill="#202a36"/>
              <rect x="70" y="150" width="60" height="15" rx="8" fill="#202a36"/>
            </svg>
          </div>
        </div>
      </div>
    </section>

    <section id="que-es">
      <h2 class="section-title">¿Qué es la Inteligencia Artificial?</h2>
      <p class="muted note">La <strong>IA</strong> es un campo de la informática que diseña sistemas capaces de realizar tareas que normalmente requieren inteligencia humana: aprender, razonar, percibir y tomar decisiones.</p>
      <div class="cards">
        <article class="card" aria-labelledby="ia-ml">
          <h3 id="ia-ml">Aprendizaje Automático (ML)</h3>
          <p>Los algoritmos aprenden patrones a partir de datos para hacer predicciones o clasificar información sin programar cada regla.</p>
        </article>
        <article class="card" aria-labelledby="ia-dl">
          <h3 id="ia-dl">Aprendizaje Profundo (DL)</h3>
          <p>Redes neuronales con muchas capas que resuelven tareas complejas como visión por computadora o reconocimiento de voz.</p>
        </article>
        <article class="card" aria-labelledby="ia-nlp">
          <h3 id="ia-nlp">Procesamiento de Lenguaje (NLP)</h3>
          <p>Modelos que entienden y generan texto para traducción, chat, resumen y más.</p>
        </article>
      </div>
    </section>

    <section id="robots">
      <h2 class="section-title">¿Qué es un robot?</h2>
      <p class="muted note">Un <strong>robot</strong> es una máquina programable capaz de percibir su entorno, procesar información y actuar de forma autónoma o asistida.</p>
      <div class="cards">
        <article class="card"><h3>Industriales</h3><p>Brazos robóticos en fábricas: soldadura, pintura, ensamblaje con alta precisión.</p></article>
        <article class="card"><h3>Colaborativos (cobots)</h3><p>Trabajan junto a personas de forma segura en tareas repetitivas o de apoyo.</p></article>
        <article class="card"><h3>De servicio</h3><p>Aspiradoras, robots de limpieza, reparto y atención en hoteles o hospitales.</p></article>
        <article class="card"><h3>Móviles autónomos</h3><p>Drones y vehículos autónomos que navegan utilizando sensores y mapas.</p></article>
        <article class="card"><h3>Humanoides</h3><p>Plataformas con forma humana orientadas a investigación, asistencia y demostraciones.</p></article>
        <article class="card"><h3>Educativos</h3><p>Kits para aprender programación, electrónica y control de motores y sensores.</p></article>
      </div>
      <div class="gallery" style="margin-top:1rem;">
        <div title="Visión por computadora"></div>
        <div title="Brazos robóticos"></div>
        <div title="Drones"></div>
        <div title="Sensores y datos"></div>
      </div>
    </section>

    <section id="aplicaciones">
      <h2 class="section-title">Aplicaciones de IA + Robótica</h2>
      <div class="cards">
        <article class="card">
          <h3>Salud</h3>
          <p>Asistencia en diagnósticos por imágenes, planificación quirúrgica y robots de rehabilitación.</p>
          <ul>
            <li>Detección temprana con IA</li>
            <li>Cirugía asistida por robot</li>
            <li>Telemedicina</li>
          </ul>
        </article>
        <article class="card">
          <h3>Educación</h3>
          <p>Tutores inteligentes, evaluación automática y laboratorios remotos con robots didácticos.</p>
          <ul>
            <li>Aprendizaje personalizado</li>
            <li>Simuladores</li>
            <li>Clases interactivas</li>
          </ul>
        </article>
        <article class="card">
          <h3>Industria</h3>
          <p>Automatización, control de calidad con visión y mantenimiento predictivo con sensores.</p>
          <ul>
            <li>Inspección en línea</li>
            <li>Logística autónoma</li>
            <li>Gestión de energía</li>
          </ul>
        </article>
      </div>
    </section>

    <section id="linea-tiempo">
      <h2 class="section-title">Línea de tiempo breve</h2>
      <div class="timeline">
        <div class="tl-item">
          <strong>1950</strong> · Test de Turing propone evaluar la inteligencia de una máquina.
        </div>
        <div class="tl-item">
          <strong>1956</strong> · Se acuña el término «Inteligencia Artificial» en Dartmouth.
        </div>
        <div class="tl-item">
          <strong>1997</strong> · Deep Blue vence al campeón mundial de ajedrez Garry Kasparov.
        </div>
        <div class="tl-item">
          <strong>2012</strong> · Revolución del deep learning con redes convolucionales (ImageNet).
        </div>
        <div class="tl-item">
          <strong>2020s</strong> · Modelos generativos y robots más autónomos y colaborativos.
        </div>
      </div>
    </section>

    <section id="recursos">
      <h2 class="section-title">Recursos para aprender</h2>
      <div class="cards">
        <article class="card">
          <h3>Conceptos clave</h3>
          <p>Algoritmos supervisados y no supervisados, redes neuronales, sobreajuste, conjuntos de datos.</p>
          <div class="row"><span class="pill">Python</span><span class="pill">Datasets</span><span class="pill">Práctica</span></div>
        </article>
        <article class="card">
          <h3>Herramientas</h3>
          <p>Plataformas de notebooks, simuladores de robots, bibliotecas de IA y control.</p>
          <div class="row"><span class="pill">Jupyter</span><span class="pill">ROS</span><span class="pill">TensorFlow</span></div>
        </article>
        <article class="card">
          <h3>Proyectos</h3>
          <p>Clasificador de imágenes, chatbot básico, seguidor de línea con robot móvil.</p>
          <div class="row"><span class="pill">Principiante</span><span class="pill">Intermedio</span><span class="pill">Avanzado</span></div>
        </article>
      </div>
    </section>

    <section id="faq">
      <h2 class="section-title">Preguntas frecuentes</h2>
      <div class="faq">
        <details>
          <summary>¿La IA reemplazará todos los trabajos?</summary>
          <p>No. La IA automatiza tareas específicas; la mayoría de trabajos cambian combinando habilidades humanas con herramientas inteligentes.</p>
        </details>
        <details>
          <summary>¿Qué lenguaje de programación debo aprender primero?</summary>
          <p><strong>Python</strong> es una opción popular por su ecosistema de bibliotecas para ciencia de datos, IA y robótica.</p>
        </details>
        <details>
          <summary>¿Necesito matemáticas avanzadas?</summary>
          <p>Al inicio no. Con conceptos básicos de estadística y álgebra lineal puedes comenzar y profundizar conforme avances.</p>
        </details>
      </div>
    </section>

    <section>
      <div class="card">
        <h3>Descarga esta página</h3>
        <p class="muted">Guarda este archivo como <code>index.html</code> y ábrelo en tu navegador. Puedes editar el contenido para tareas o proyectos.</p>
        <div class="row">
          <a class="btn" href="#" onclick="downloadHTML(); return false;">Descargar HTML</a>
          <a class="btn" href="#home">Volver arriba ↑</a>
        </div>
      </div>
    </section>
  </main>

  <footer>
    <p>Hecho con ❤️ usando HTML, CSS y JavaScript. | © <span id="year"></span></p>
  </footer>

  <script>
    // ====== THEME TOGGLE (persistente) ======
    const themeBtn = document.getElementById('themeBtn');
    const MENU_KEY = 'ia-robots-theme';
    function applyTheme(theme){
      if(theme === 'light'){
        document.documentElement.style.setProperty('--bg', '#f7f8fb');
        document.documentElement.style.setProperty('--bg-soft', '#ffffff');
        document.documentElement.style.setProperty('--card', '#ffffff');
        document.documentElement.style.setProperty('--text', '#0b0d10');
        document.documentElement.style.setProperty('--muted', '#4b5563');
        document.body.style.background = 'radial-gradient(1200px 600px at 80% -10%, rgba(124,92,255,.15), transparent 60%), radial-gradient(1000px 600px at 0% 10%, rgba(33,193,179,.12), transparent 60%), #f7f8fb';
        themeBtn.textContent = 'Modo oscuro';
      } else {
        document.documentElement.style.setProperty('--bg', '#0b0d10');
        document.documentElement.style.setProperty('--bg-soft', '#11151b');
        document.documentElement.style.setProperty('--card', '#151a21');
        document.documentElement.style.setProperty('--text', '#e8eef7');
        document.documentElement.style.setProperty('--muted', '#a8b3c5');
        document.body.style.background = 'radial-gradient(1200px 600px at 80% -10%, rgba(124,92,255,.15), transparent 60%), radial-gradient(1000px 600px at 0% 10%, rgba(33,193,179,.12), transparent 60%), #0b0d10';
        themeBtn.textContent = 'Tema';
      }
    }
    function getTheme(){ return localStorage.getItem(MENU_KEY) || 'dark'; }
    function setTheme(theme){ localStorage.setItem(MENU_KEY, theme); applyTheme(theme); }
    themeBtn.addEventListener('click', () => setTheme(getTheme() === 'dark' ? 'light' : 'dark'));
    applyTheme(getTheme());

    // ====== MOBILE MENU SHEET ======
    const menuBtn = document.getElementById('menuBtn');
    const mobileSheet = document.getElementById('mobileSheet');
    menuBtn.addEventListener('click', () => {
      const isOpen = mobileSheet.classList.toggle('open');
      menuBtn.setAttribute('aria-expanded', isOpen);
    });
    mobileSheet.querySelectorAll('a').forEach(a => a.addEventListener('click', () => mobileSheet.classList.remove('open')));

    // ====== FOOTER YEAR ======
    document.getElementById('year').textContent = new Date().getFullYear();

    // ====== SIMPLE SCROLL REVEAL ======
    const revealEls = document.querySelectorAll('.card, .kpi, .tl-item, .gallery div');
    const obs = new IntersectionObserver((entries) => {
      entries.forEach(e => {
        if (e.isIntersecting) {
          e.target.animate([
            { transform: 'translateY(8px)', opacity: .001 },
            { transform: 'translateY(0)', opacity: 1 }
          ], { duration: 420, easing: 'cubic-bezier(.2,.6,.2,1)', fill: 'forwards' });
          obs.unobserve(e.target);
        }
      });
    }, { threshold: 0.12 });
    revealEls.forEach(el => obs.observe(el));

    // ====== DOWNLOAD THIS PAGE ======
    function downloadHTML(){
      const blob = new Blob([document.documentElement.outerHTML], { type: 'text/html;charset=utf-8' });
      const url = URL.createObjectURL(blob);
      const a = document.createElement('a');
      a.href = url; a.download = 'ia-robots.html'; a.click();
      URL.revokeObjectURL(url);
    }
  </script>
</body>
</html>
