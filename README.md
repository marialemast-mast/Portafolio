<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <title>María Alejandra Sánchez Tristancho — Portafolio</title>

  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>

  <link
    href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,600;0,700;1,400&family=Inter:wght@300;400;500;600&display=swap"
    rel="stylesheet"
  >

  <style>
    /* =========================
       RESET & BASE
    ========================= */

    *,
    *::before,
    *::after {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    html {
      scroll-behavior: smooth;
      font-size: 16px;
    }

    body {
      font-family: 'Inter', sans-serif;
      background: #FDF6F8;
      color: #3A3A3A;
      line-height: 1.7;
      overflow-x: hidden;
    }

    /* =========================
       COLOR TOKENS
    ========================= */

    :root {
      --pink-light: #F9E4EC;
      --pink-soft: #F2C4D7;
      --pink-accent: #E8A0BF;

      --teal-light: #D5ECE8;
      --teal-soft: #A8D5D0;
      --teal-accent: #6DBFB8;
      --teal-dark: #4A9B93;

      --bg: #FDF6F8;
      --bg-alt: #F5F0F2;

      --text: #3A3A3A;
      --text-light: #6B6B6B;

      --white: #FFFFFF;

      --shadow-soft: 0 4px 24px rgba(0, 0, 0, 0.06);
      --shadow-hover: 0 8px 40px rgba(0, 0, 0, 0.10);
    }

    /* =========================
       SCROLLBAR
    ========================= */

    ::-webkit-scrollbar {
      width: 8px;
    }

    ::-webkit-scrollbar-track {
      background: var(--bg);
    }

    ::-webkit-scrollbar-thumb {
      background: var(--pink-soft);
      border-radius: 4px;
    }

    /* =========================
       NAVIGATION
    ========================= */

    nav {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      z-index: 100;

      padding: 1rem 2rem;

      display: flex;
      justify-content: space-between;
      align-items: center;

      transition: all 0.4s ease;
    }

    nav.scrolled {
      background: rgba(253, 246, 248, 0.92);
      backdrop-filter: blur(16px);
      -webkit-backdrop-filter: blur(16px);

      box-shadow: 0 2px 20px rgba(0, 0, 0, 0.05);
    }

    nav .logo {
      font-family: 'Playfair Display', serif;
      font-weight: 600;
      font-size: 1.15rem;
      color: var(--teal-dark);
      letter-spacing: 0.02em;
    }

    nav .nav-links {
      display: flex;
      gap: 2rem;
      list-style: none;
    }

    nav .nav-links a {
      text-decoration: none;
      color: var(--text-light);
      font-size: 0.85rem;
      font-weight: 500;
      letter-spacing: 0.06em;
      text-transform: uppercase;

      position: relative;
      transition: color 0.3s;
    }

    nav .nav-links a::after {
      content: '';

      position: absolute;
      bottom: -4px;
      left: 0;

      width: 0;
      height: 2px;

      background: var(--pink-accent);
      border-radius: 2px;

      transition: width 0.3s ease;
    }

    nav .nav-links a:hover {
      color: var(--teal-dark);
    }

    nav .nav-links a:hover::after {
      width: 100%;
    }

    /* =========================
       HAMBURGER
    ========================= */

    .hamburger {
      display: none;
      flex-direction: column;
      gap: 5px;

      cursor: pointer;
      z-index: 200;
    }

    .hamburger span {
      width: 24px;
      height: 2px;

      background: var(--teal-dark);
      border-radius: 2px;

      transition: all 0.3s;
    }

    /* =========================
       HERO
    ========================= */

    .hero {
      min-height: 100vh;

      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;

      text-align: center;

      padding: 2rem;

      position: relative;
      overflow: hidden;
    }

    .hero::before {
      content: '';

      position: absolute;
      top: -120px;
      right: -120px;

      width: 480px;
      height: 480px;

      background:
        radial-gradient(
          circle,
          var(--pink-light) 0%,
          transparent 70%
        );

      border-radius: 50%;
      opacity: 0.7;
    }

    .hero::after {
      content: '';

      position: absolute;
      bottom: -100px;
      left: -100px;

      width: 400px;
      height: 400px;

      background:
        radial-gradient(
          circle,
          var(--teal-light) 0%,
          transparent 70%
        );

      border-radius: 50%;
      opacity: 0.6;
    }

    .hero h1 {
      font-family: 'Playfair Display', serif;
      font-size: clamp(2.4rem, 5vw, 4.2rem);
      font-weight: 700;

      color: var(--teal-dark);

      margin-bottom: 1.2rem;

      position: relative;
      z-index: 1;

      animation: fadeUp 1s ease forwards;
    }

    .hero .subtitle {
      font-size: clamp(0.95rem, 1.8vw, 1.15rem);

      color: var(--text-light);
      font-weight: 300;

      letter-spacing: 0.04em;

      max-width: 680px;

      position: relative;
      z-index: 1;

      animation: fadeUp 1s 0.3s ease forwards;

      opacity: 0;
    }

    .hero .subtitle span {
      display: inline-block;
      margin: 0 0.25em;

      color: var(--pink-accent);
      font-weight: 400;
    }

    .hero .scroll-indicator {
      position: absolute;

      bottom: 2.5rem;
      left: 50%;

      transform: translateX(-50%);

      display: flex;
      flex-direction: column;
      align-items: center;

      gap: 0.5rem;

      animation: float 2.5s ease-in-out infinite;

      z-index: 1;
    }

    .hero .scroll-indicator span {
      font-size: 0.7rem;

      text-transform: uppercase;
      letter-spacing: 0.15em;

      color: var(--text-light);
    }

    .hero .scroll-indicator .arrow {
      width: 20px;
      height: 20px;

      border-right: 2px solid var(--pink-accent);
      border-bottom: 2px solid var(--pink-accent);

      transform: rotate(45deg);
    }

    /* =========================
       SECTIONS
    ========================= */

    section {
      padding: 6rem 2rem;
    }

    .section-inner {
      max-width: 960px;
      margin: 0 auto;
    }

    .section-label {
      font-size: 0.75rem;

      font-weight: 600;

      letter-spacing: 0.18em;
      text-transform: uppercase;

      color: var(--pink-accent);

      margin-bottom: 0.75rem;
    }

    .section-title {
      font-family: 'Playfair Display', serif;

      font-size: clamp(1.8rem, 3.5vw, 2.6rem);

      font-weight: 600;

      color: var(--teal-dark);

      margin-bottom: 2rem;
    }

    .divider {
      width: 60px;
      height: 3px;

      background:
        linear-gradient(
          90deg,
          var(--pink-accent),
          var(--teal-soft)
        );

      border-radius: 3px;

      margin-bottom: 2.5rem;
    }

    /* =========================
       ABOUT
    ========================= */

    .about {
      background: var(--white);
    }

    .about p {
      font-size: 1.02rem;

      line-height: 1.85;

      color: var(--text);

      margin-bottom: 1.5rem;

      max-width: 720px;
    }

    .about .languages {
      display: flex;

      gap: 1rem;

      flex-wrap: wrap;

      margin-top: 1rem;
    }

    .about .lang-tag {
      display: inline-flex;
      align-items: center;

      gap: 0.5rem;

      padding: 0.55rem 1.3rem;

      background: var(--pink-light);

      border-radius: 50px;

      font-size: 0.85rem;

      font-weight: 500;

      color: var(--text);

      transition:
        transform 0.2s,
        box-shadow 0.2s;
    }

    .about .lang-tag:hover {
      transform: translateY(-2px);

      box-shadow:
        0 4px 12px
        rgba(232, 160, 191, 0.25);
    }

    .about .lang-tag .level {
      font-size: 0.75rem;

      color: var(--teal-dark);

      font-weight: 600;
    }

    /* =========================
       PERIODISMO
    ========================= */

    .periodismo {
      background: var(--bg);
    }

    .periodismo .focus-grid {
      display: grid;

      grid-template-columns:
        repeat(auto-fit, minmax(240px, 1fr));

      gap: 2rem;

      margin-top: 1rem;
    }

    .periodismo .focus-card {
      background: var(--white);

      padding: 2rem;

      border-radius: 20px;

      border:
        1px solid
        rgba(168, 213, 208, 0.3);

      transition:
        transform 0.3s,
        box-shadow 0.3s;
    }

    .periodismo .focus-card:hover {
      transform: translateY(-6px);

      box-shadow: var(--shadow-hover);
    }

    .periodismo .focus-card .icon {
      width: 52px;
      height: 52px;

      border-radius: 16px;

      display: flex;
      align-items: center;
      justify-content: center;

      font-size: 1.5rem;

      margin-bottom: 1.2rem;
    }

    .periodismo .focus-card .icon.geo {
      background: var(--teal-light);
    }

    .periodismo .focus-card .icon.media {
      background: var(--pink-light);
    }

    .periodismo .focus-card .icon.impact {
      background:
        linear-gradient(
          135deg,
          var(--pink-light),
          var(--teal-light)
        );
    }

    .periodismo .focus-card h3 {
      font-family: 'Playfair Display', serif;

      font-size: 1.15rem;

      color: var(--teal-dark);

      margin-bottom: 0.6rem;
    }

    .periodismo .focus-card p {
      font-size: 0.92rem;

      color: var(--text-light);

      line-height: 1.65;
    }

    /* =========================
       INCLUSION
    ========================= */

    .inclusion {
      background: var(--white);
    }

    .inclusion .project-highlight {
      background:
        linear-gradient(
          135deg,
          var(--teal-light) 0%,
          var(--pink-light) 100%
        );

      border-radius: 24px;

      padding: 3rem;

      margin-top: 1.5rem;

      position: relative;

      overflow: hidden;
    }

    .inclusion .project-highlight::after {
      content: '';

      position: absolute;

      top: -40px;
      right: -40px;

      width: 200px;
      height: 200px;

      background:
        rgba(255, 255, 255, 0.15);

      border-radius: 50%;
    }

    .inclusion .project-highlight h3 {
      font-family: 'Playfair Display', serif;

      font-size: 1.6rem;

      color: var(--teal-dark);

      margin-bottom: 1rem;
    }

    .inclusion .project-highlight p {
      font-size: 1rem;

      color: var(--text);

      line-height: 1.8;

      max-width: 600px;
    }

    .inclusion .project-highlight .badge {
      display: inline-block;

      margin-top: 1.5rem;

      padding: 0.5rem 1.5rem;

      background: var(--white);

      border-radius: 50px;

      font-size: 0.82rem;

      font-weight: 600;

      color: var(--teal-dark);

      letter-spacing: 0.04em;
    }

    /* =========================
       PROJECTS
    ========================= */

    .projects {
      background: var(--bg);
    }

    .projects-grid {
      display: grid;

      grid-template-columns:
        repeat(auto-fit, minmax(260px, 1fr));

      gap: 1.5rem;

      margin-top: 0.5rem;
    }

    .project-card {
      background: var(--white);

      border-radius: 20px;

      overflow: hidden;

      border:
        1px solid
        rgba(168, 213, 208, 0.2);

      transition:
        transform 0.35s,
        box-shadow 0.35s;

      cursor: default;
    }

    .project-card:hover {
      transform: translateY(-8px);

      box-shadow: var(--shadow-hover);
    }

    .project-card .card-header {
      height: 140px;

      display: flex;
      align-items: center;
      justify-content: center;

      position: relative;
    }

    .project-card .card-header .emoji {
      font-size: 3rem;

      position: relative;
      z-index: 1;
    }

    .project-card:nth-child(1) .card-header {
      background:
        linear-gradient(
          135deg,
          #A8D5D0,
          #D5ECE8
        );
    }

    .project-card:nth-child(2) .card-header {
      background:
        linear-gradient(
          135deg,
          #F2C4D7,
          #F9E4EC
        );
    }

    .project-card:nth-child(3) .card-header {
      background:
        linear-gradient(
          135deg,
          #E8A0BF,
          #F9E4EC
        );
    }

    .project-card:nth-child(4) .card-header {
      background:
        linear-gradient(
          135deg,
          #6DBFB8,
          #A8D5D0
        );
    }

    .project-card .card-body {
      padding: 1.5rem;
    }

    .project-card .card-body h3 {
      font-family: 'Playfair Display', serif;

      font-size: 1.2rem;

      color: var(--teal-dark);

      margin-bottom: 0.6rem;
    }

    .project-card .card-body p {
      font-size: 0.9rem;

      color: var(--text-light);

      line-height: 1.65;

      margin-bottom: 1rem;
    }

    .project-card .card-body .tags {
      display: flex;

      gap: 0.5rem;

      flex-wrap: wrap;
    }

    .project-card .card-body .tag {
      font-size: 0.72rem;

      padding: 0.3rem 0.8rem;

      border-radius: 50px;

      background: var(--pink-light);

      color: var(--text);

      font-weight: 500;
    }

    /* =========================
       CONTACT
    ========================= */

    .contact {
      background: var(--white);

      text-align: center;
    }

    .contact .contact-card {
      display: inline-flex;

      flex-direction: column;

      gap: 1.5rem;

      background:
        linear-gradient(
          160deg,
          var(--pink-light) 0%,
          var(--teal-light) 100%
        );

      padding: 3rem 4rem;

      border-radius: 28px;

      margin-top: 1rem;
    }

    .contact .contact-item {
      display: flex;

      align-items: center;

      gap: 1rem;

      justify-content: flex-start;
    }

    .contact .contact-item .icon-circle {
      width: 44px;
      height: 44px;

      border-radius: 50%;

      background: var(--white);

      display: flex;
      align-items: center;
      justify-content: center;

      font-size: 1.1rem;

      flex-shrink: 0;
    }

    .contact .contact-item .info {
      text-align: left;
    }

    .contact .contact-item .info .label {
      font-size: 0.72rem;

      text-transform: uppercase;

      letter-spacing: 0.1em;

      color: var(--text-light);

      font-weight: 600;
    }

    .contact .contact-item .info .value {
      font-size: 0.95rem;

      color: var(--text);

      font-weight: 500;
    }

    .contact .contact-item .info a {
      color: var(--teal-dark);

      text-decoration: none;

      transition: color 0.2s;
    }

    .contact .contact-item .info a:hover {
      color: var(--pink-accent);
    }

    /* =========================
       FOOTER
    ========================= */

    footer {
      background: var(--teal-dark);

      color: rgba(255, 255, 255, 0.8);

      text-align: center;

      padding: 2rem;

      font-size: 0.85rem;

      letter-spacing: 0.04em;
    }

    footer a {
      color: var(--pink-soft);

      text-decoration: none;
    }

    /* =========================
       ANIMATIONS
    ========================= */

    @keyframes fadeUp {
      from {
        opacity: 0;
        transform: translateY(30px);
      }

      to {
        opacity: 1;
        transform: translateY(0);
      }
    }

    @keyframes float {
      0%,
      100% {
        transform:
          translateX(-50%)
          translateY(0);
      }

      50% {
        transform:
          translateX(-50%)
          translateY(-10px);
      }
    }

    .reveal {
      opacity: 0;

      transform: translateY(40px);

      transition:
        opacity 0.7s ease,
        transform 0.7s ease;
    }

    .reveal.visible {
      opacity: 1;

      transform: translateY(0);
    }

    /* =========================
       RESPONSIVE
    ========================= */

    @media (max-width: 768px) {

      nav .nav-links {
        display: none;
      }

      .hamburger {
        display: flex;
      }

      nav .nav-links.open {
        display: flex;

        flex-direction: column;

        position: fixed;

        top: 0;
        right: 0;

        width: 260px;
        height: 100vh;

        background:
          rgba(253, 246, 248, 0.97);

        backdrop-filter: blur(20px);

        padding: 5rem 2rem 2rem;

        gap: 1.5rem;

        z-index: 150;

        box-shadow:
          -4px 0 30px
          rgba(0, 0, 0, 0.08);
      }

      section {
        padding: 4rem 1.5rem;
      }

      .contact .contact-card {
        padding: 2rem 2.5rem;
      }

      .inclusion .project-highlight {
        padding: 2rem;
      }
    }
  </style>
</head>

<body>

  <!-- =========================
       NAVIGATION
  ========================= -->

  <nav id="navbar">

    <div class="logo">
      MAS
    </div>

    <ul class="nav-links" id="navLinks">

      <li>
        <a href="#inicio">Inicio</a>
      </li>

      <li>
        <a href="#sobre-mi">Sobre mí</a>
      </li>

      <li>
        <a href="#periodismo">Periodismo</a>
      </li>

      <li>
        <a href="#inclusion">Inclusión</a>
      </li>

      <li>
        <a href="#proyectos">Proyectos</a>
      </li>

      <li>
        <a href="#contacto">Contacto</a>
      </li>

    </ul>

    <div
      class="hamburger"
      id="hamburger"
      onclick="toggleMenu()"
      aria-label="Abrir menú"
      role="button"
      tabindex="0"
    >
      <span></span>
      <span></span>
      <span></span>
    </div>

  </nav>

  <!-- =========================
       HERO
  ========================= -->

  <section
    class="hero"
    id="inicio"
  >

    <h1>
      María Alejandra<br>
      Sánchez Tristancho
    </h1>

    <p class="subtitle">
      Estudiante de Comunicación Social y Periodismo
      <span>·</span>
      Investigación sociopolítica
      <span>·</span>
      Dirección editorial
      <span>·</span>
      Narrativa transmedia
    </p>

    <div class="scroll-indicator">

      <span>
        Explorar
      </span>

      <div class="arrow"></div>

    </div>

  </section>

  <!-- =========================
       ABOUT
  ========================= -->

  <section
    class="about"
    id="sobre-mi"
  >

    <div class="section-inner reveal">

      <p class="section-label">
        Conóceme
      </p>

      <h2 class="section-title">
        Sobre mí
      </h2>

      <div class="divider"></div>

      <p>
        Soy estudiante de Comunicación Social y Periodismo en la Universidad de La Sabana, con un profundo interés en la investigación sociopolítica, la dirección editorial y la narrativa transmedia. Mi formación académica me ha permitido explorar las intersecciones entre comunicación, poder y sociedad, desarrollando una mirada crítica sobre el rol de los medios en la construcción de realidades.
      </p>

      <p>
        Como directora editorial de <em>Hilo Abierto</em>, he liderado la curaduría y gestión de contenidos que buscan abrir diálogos significativos sobre temas contemporáneos. Paralelamente, creé <em>Las Reinas del Silencio</em>, una saga narrativa que explora las voces silenciadas y las historias que necesitan ser contadas, y produje el podcast <em>Verse and Voice</em>, donde convergen la literatura y la reflexión social desde una perspectiva bilingüe.
      </p>

      <p>
        En el ámbito investigativo, participo activamente en el Semillero Observatorio de Medios, donde realizo monitoreo y análisis de medios, fortaleciendo mi compromiso con la comunicación rigurosa y de impacto social. Creo firmemente que el periodismo y la narrativa son herramientas poderosas para la transformación y la inclusión.
      </p>

      <div class="languages">

        <div class="lang-tag">
          Español
          <span class="level">
            Nativo
          </span>
        </div>

        <div class="lang-tag">
          Inglés
          <span class="level">
            B2
          </span>
        </div>

        <div class="lang-tag">
          Francés
          <span class="level">
            A2
          </span>
        </div>

      </div>

    </div>

  </section>

  <!-- =========================
       PERIODISMO
  ========================= -->

  <section
    class="periodismo"
    id="periodismo"
  >

    <div class="section-inner reveal">

      <p class="section-label">
        Enfoque
      </p>

      <h2 class="section-title">
        Periodismo
      </h2>

      <div class="divider"></div>

      <div class="focus-grid">

        <div class="focus-card">

          <div class="icon geo">
            🌍
          </div>

          <h3>
            Análisis geopolítico
          </h3>

          <p>
            Abordo hechos globales con perspectiva analítica, conectando coyunturas internacionales con realidades locales para comprender el mundo desde múltiples dimensiones.
          </p>

        </div>

        <div class="focus-card">

          <div class="icon media">
            📡
          </div>

          <h3>
            Monitoreo de medios
          </h3>

          <p>
            Realizo seguimiento crítico a la cobertura mediática, identificando sesgos, agendas y patrones narrativos que moldean la opinión pública.
          </p>

        </div>

        <div class="focus-card">

          <div class="icon impact">
            ✊
          </div>

          <h3>
            Comunicación con impacto social
          </h3>

          <p>
            Apuesto por un periodismo que no solo informe, sino que genere conversación, visibilice desigualdades y contribuya a la construcción de sociedades más justas.
          </p>

        </div>

      </div>

    </div>

  </section>

  <!-- =========================
       INCLUSIÓN Y DIVERSIDAD
  ========================= -->

  <section
    class="inclusion"
    id="inclusion"
  >

    <div class="section-inner reveal">

      <p class="section-label">
        Compromiso
      </p>

      <h2 class="section-title">
        Inclusión y Diversidad
      </h2>

      <div class="divider"></div>

      <div class="project-highlight">

        <h3>
          Aulas Sin Barreras
        </h3>

        <p>
          Proyecto dedicado a la eliminación de barreras educativas que limitan el acceso y la permanencia de estudiantes en contextos vulnerables. A través de la investigación, la sensibilización y la articulación con actores institucionales, <em>Aulas Sin Barreras</em> busca transformar el sistema educativo en un espacio verdaderamente inclusivo donde la diversidad sea reconocida como fortaleza.
        </p>

        <div class="badge">
          Educación inclusiva · Equidad · Acceso
        </div>

      </div>

    </div>

  </section>

  <!-- =========================
       PROJECTS
  ========================= -->

  <section
    class="projects"
    id="proyectos"
  >

    <div class="section-inner reveal">

      <p class="section-label">
        Trayectoria
      </p>

      <h2 class="section-title">
        Proyectos
      </h2>

      <div class="divider"></div>

      <div class="projects-grid">

        <!-- Hilo Abierto -->

        <div class="project-card">

          <div class="card-header">
            <span class="emoji">
              🧵
            </span>
          </div>

          <div class="card-body">

            <h3>
              Hilo Abierto
            </h3>

            <p>
              Medio editorial independiente dirigido a la comunidad universitaria. Curaduría de contenidos, gestión de equipo editorial y producción de piezas que abren diálogos sobre cultura, política y sociedad.
            </p>

            <div class="tags">

              <span class="tag">
                Dirección editorial
              </span>

              <span class="tag">
                Curaduría
              </span>

              <span class="tag">
                Gestión de equipo
              </span>

            </div>

          </div>

        </div>

        <!-- Las Reinas del Silencio -->

        <div class="project-card">

          <div class="card-header">
            <span class="emoji">
              👑
            </span>
          </div>

          <div class="card-body">

            <h3>
              Las Reinas del Silencio
            </h3>

            <p>
              Saga narrativa que rescata voces silenciadas y historias olvidadas. Una exploración literaria sobre la memoria, la resistencia y la fuerza de quienes habitan los márgenes del relato oficial.
            </p>

            <div class="tags">

              <span class="tag">
                Narrativa
              </span>

              <span class="tag">
                Creación literaria
              </span>

              <span class="tag">
                Transmedia
              </span>

            </div>

          </div>

        </div>

        <!-- Verso y Voz -->

        <div class="project-card">

          <div class="card-header">
            <span class="emoji">
              🎙️
            </span>
          </div>

          <div class="card-body">

            <h3>
              Verso y Voz
            </h3>

            <p>
              Podcast bilingüe donde convergen la literatura, la reflexión social y la experimentación sonora. Un espacio para escuchar, pensar y sentir en dos idiomas.
            </p>

            <div class="tags">

              <span class="tag">
                Podcast
              </span>

              <span class="tag">
                Bilingüe
              </span>

              <span class="tag">
                Producción audiovisual
              </span>

            </div>

          </div>

        </div>

        <!-- Aulas Sin Barreras -->

        <div class="project-card">

          <div class="card-header">
            <span class="emoji">
              🏫
            </span>
          </div>

          <div class="card-body">

            <h3>
              Aulas Sin Barreras
            </h3>

            <p>
              Iniciativa de inclusión educativa orientada a eliminar obstáculos que impiden el acceso y la permanencia de estudiantes en condiciones de vulnerabilidad.
            </p>

            <div class="tags">

              <span class="tag">
                Inclusión
              </span>

              <span class="tag">
                Investigación
              </span>

              <span class="tag">
                Equidad
              </span>

            </div>

          </div>

        </div>

      </div>

    </div>

  </section>

  <!-- =========================
       CONTACT
  ========================= -->

  <section
    class="contact"
    id="contacto"
  >

    <div class="section-inner reveal">

      <p class="section-label">
        Hablemos
      </p>

      <h2 class="section-title">
        Contacto
      </h2>

      <div
        class="divider"
        style="margin-left:auto;margin-right:auto;"
      ></div>

      <div class="contact-card">

        <!-- Email -->

        <div class="contact-item">

          <div class="icon-circle">
            ✉️
          </div>

          <div class="info">

            <div class="label">
              Correo
            </div>

            <div class="value">

              <a href="mailto:masancheztrancho@gmail.com">
                masancheztrancho@gmail.com
              </a>

            </div>

          </div>

        </div>

        <!-- LinkedIn -->

        <div class="contact-item">

          <div class="icon-circle">
            💼
          </div>

          <div class="info">

            <div class="label">
              LinkedIn
            </div>

            <div class="value">

              <a
                href="https://linkedin.com/in/maría-alejandra-sánchez-tristancho"
                target="_blank"
                rel="noopener noreferrer"
              >
                María Alejandra Sánchez Tristancho
              </a>

            </div>

          </div>

        </div>

        <!-- Teléfono -->

        <div class="contact-item">

          <div class="icon-circle">
            📱
          </div>

          <div class="info">

            <div class="label">
              Teléfono
            </div>

            <div class="value">

              <a href="tel:+573212343384">
                +57 321 234 3384
              </a>

            </div>

          </div>

        </div>

      </div>

    </div>

  </section>

  <!-- =========================
       FOOTER
  ========================= -->

  <footer>

    <p>
      © 2026 María Alejandra Sánchez Tristancho
      · Todos los derechos reservados
    </p>

  </footer>

  <!-- =========================
       JAVASCRIPT
  ========================= -->

  <script>

    /* Navbar scroll effect */

    const navbar =
      document.getElementById('navbar');

    window.addEventListener('scroll', () => {

      navbar.classList.toggle(
        'scrolled',
        window.scrollY > 60
      );

    });


    /* Reveal on scroll */

    const reveals =
      document.querySelectorAll('.reveal');

    const observer =
      new IntersectionObserver(
        (entries) => {

          entries.forEach((entry) => {

            if (entry.isIntersecting) {

              entry.target.classList.add(
                'visible'
              );

              observer.unobserve(
                entry.target
              );

            }

          });

        },
        {
          threshold: 0.12
        }
      );

    reveals.forEach((element) => {
      observer.observe(element);
    });


    /* Mobile menu */

    function toggleMenu() {

      const navLinks =
        document.getElementById('navLinks');

      navLinks.classList.toggle('open');

    }


    /* Close mobile menu when clicking a link */

    document
      .querySelectorAll('#navLinks a')
      .forEach((link) => {

        link.addEventListener('click', () => {

          document
            .getElementById('navLinks')
            .classList.remove('open');

        });

      });


    /* Keyboard accessibility for hamburger */

    document
      .getElementById('hamburger')
      .addEventListener('keydown', (event) => {

        if (
          event.key === 'Enter' ||
          event.key === ' '
        ) {

          event.preventDefault();

          toggleMenu();

        }

      });

  </script>

</body>
</html>
