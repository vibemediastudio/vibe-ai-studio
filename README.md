
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="theme-color" content="#090713">

  <title>Vibe AI Studio | AI Animation & Creative Studio</title>
  <meta name="description" content="Vibe AI Studio creates AI animated stories, cinematic visuals, short-form videos and creative content for the digital world.">

  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800;900&display=swap" rel="stylesheet">

  <style>
    :root {
      --bg: #090713;
      --panel: #120d20;
      --purple: #a855f7;
      --pink: #ec4899;
      --text: #f8f5ff;
      --muted: #aaa3bb;
      --border: rgba(255,255,255,.10);
    }

    * { margin: 0; padding: 0; box-sizing: border-box; }
    html { scroll-behavior: smooth; scroll-padding-top: 90px; }
    body {
      font-family: 'Inter', sans-serif;
      background: var(--bg);
      color: var(--text);
      line-height: 1.7;
      overflow-x: hidden;
    }
    a { text-decoration: none; color: inherit; }
    button, a { -webkit-tap-highlight-color: transparent; }
    .container { width: min(1120px, 90%); margin: auto; }
    .gradient {
      background: linear-gradient(100deg, #c084fc, #ec4899);
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
    }

    /* Navigation */
    header {
      position: sticky;
      top: 0;
      z-index: 100;
      background: rgba(9,7,19,.88);
      backdrop-filter: blur(18px);
      border-bottom: 1px solid var(--border);
    }
    nav {
      min-height: 76px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 20px;
    }
    .logo { font-size: 20px; font-weight: 900; letter-spacing: -1px; }
    .logo span { color: #c084fc; }
    .nav-links { display: flex; gap: 28px; align-items: center; }
    .nav-links a { color: var(--muted); font-size: 13px; transition: .2s; }
    .nav-links a:hover { color: white; }
    .nav-cta, .btn {
      display: inline-flex;
      justify-content: center;
      align-items: center;
      gap: 8px;
      padding: 12px 21px;
      border-radius: 9px;
      background: linear-gradient(110deg, #9333ea, #db2777);
      color: white;
      font-size: 13px;
      font-weight: 700;
      border: 0;
      cursor: pointer;
      transition: transform .2s, box-shadow .2s;
    }
    .btn:hover, .nav-cta:hover { transform: translateY(-3px); box-shadow: 0 8px 30px #a855f744; }
    .btn-outline { background: transparent; border: 1px solid #8b5cf6; }
    .menu-toggle { display: none; }

    /* Hero */
    .hero {
      position: relative;
      min-height: 650px;
      display: flex;
      align-items: center;
      padding: 100px 0;
      overflow: hidden;
    }
    .hero::before {
      content: "";
      position: absolute;
      width: 600px;
      height: 600px;
      right: -100px;
      top: 20px;
      background: radial-gradient(circle, #7e22ce30 0%, #7e22ce00 70%);
      pointer-events: none;
    }
    .hero-grid {
      display: grid;
      grid-template-columns: 1.1fr .9fr;
      gap: 55px;
      align-items: center;
    }
    .eyebrow {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      border: 1px solid #a855f744;
      background: #a855f712;
      border-radius: 100px;
      padding: 7px 13px;
      color: #d8b4fe;
      font-size: 11px;
      font-weight: 700;
      letter-spacing: 1px;
      text-transform: uppercase;
    }
    .dot {
      width: 7px; height: 7px; border-radius: 50%;
      background: #c084fc; box-shadow: 0 0 12px #c084fc;
    }
    h1 {
      font-size: clamp(42px, 5.5vw, 70px);
      line-height: 1.08;
      letter-spacing: -3px;
      margin: 25px 0;
    }
    .hero p { max-width: 530px; color: var(--muted); font-size: 16px; }
    .hero-buttons { display: flex; gap: 13px; flex-wrap: wrap; margin-top: 30px; }
    .hero-note { margin-top: 23px; font-size: 11px; color: #817991; }

    .visual {
      min-height: 390px;
      position: relative;
      border: 1px solid #a855f733;
      border-radius: 26px;
      background:
        radial-gradient(ellipse at 50% 40%, #9333ea36, transparent 55%),
        linear-gradient(145deg, #1d1230, #0c0915 70%);
      display: grid;
      place-items: center;
      overflow: hidden;
      isolation: isolate;
    }
    .visual::before, .visual::after {
      content: "";
      position: absolute;
      width: 270px;
      height: 270px;
      border: 1px solid #c084fc44;
      border-radius: 50%;
      transform: rotate(-25deg) scaleY(.45);
    }
    .visual::after { width: 330px; height: 330px; transform: rotate(55deg) scaleY(.45); }
    .ai-core {
      width: 175px; height: 175px; border-radius: 35px;
      display: grid; place-items: center;
      font-size: 70px;
      background: linear-gradient(145deg, #a855f7, #6d28d9 60%, #ec4899);
      box-shadow: 0 0 90px #9333ea66, inset 0 0 25px #ffffff33;
      transform: rotate(-8deg);
      animation: float 5s ease-in-out infinite;
      z-index: 1;
    }
    .ai-core span { transform: rotate(8deg); }
    .floating-label {
      position: absolute; z-index: 2;
      border: 1px solid #ffffff22;
      background: #110b20dd;
      border-radius: 10px;
      padding: 10px 14px;
      font-size: 11px;
      color: #e9d5ff;
    }
    .label-one { top: 50px; left: 24px; }
    .label-two { bottom: 60px; right: 20px; }
    .label-three { bottom: 22px; left: 25px; }
    @keyframes float { 0%,100% { transform: translateY(0) rotate(-8deg); } 50% { transform: translateY(-12px) rotate(-3deg); } }

    /* Shared sections */
    section { padding: 90px 0; }
    .section-head { text-align: center; max-width: 650px; margin: 0 auto 45px; }
    .section-head h2 { font-size: clamp(30px, 4vw, 43px); letter-spacing: -1.5px; line-height: 1.2; margin: 15px 0; }
    .section-head p { color: var(--muted); font-size: 14px; }
    .card-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 18px; }
    .card {
      padding: 28px;
      background: linear-gradient(145deg, #151020, #0e0a17);
      border: 1px solid var(--border);
      border-radius: 16px;
      transition: .25s;
    }
    .card:hover { border-color: #a855f766; transform: translateY(-5px); }
    .card-icon {
      width: 47px; height: 47px; display: grid; place-items: center;
      border-radius: 13px; font-size: 23px;
      background: #a855f71b; margin-bottom: 20px;
    }
    .card h3 { font-size: 17px; margin-bottom: 10px; }
    .card p { color: var(--muted); font-size: 13px; }

    /* Portfolio */
    .portfolio-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 18px; }
    .work {
      border-radius: 16px;
      overflow: hidden;
      background: var(--panel);
      border: 1px solid var(--border);
    }
    .work-art {
      min-height: 235px;
      display: grid;
      place-items: center;
      position: relative;
      font-size: 62px;
      overflow: hidden;
    }
    .work-art::after {
      content: ""; position: absolute; inset: 0;
      background: linear-gradient(transparent 55%, #09071388);
    }
    .art-one { background: radial-gradient(circle at 50% 40%, #7c3aed, #24103e 50%, #100b1a); }
    .art-two { background: radial-gradient(circle at 65% 30%, #ec4899, #4a1749 45%, #120b1d); }
    .art-three { background: radial-gradient(circle at 40% 40%, #2563eb, #15254b 45%, #090e1d); }
    .work-art span { z-index: 1; filter: drop-shadow(0 0 20px #ffffff55); }
    .work-info { padding: 20px; }
    .work-info h3 { font-size: 15px; margin-bottom: 5px; }
    .work-info p { font-size: 12px; color: var(--muted); }
    .tag { display: inline-block; margin-top: 12px; font-size: 10px; color: #d8b4fe; background: #a855f71c; padding: 5px 9px; border-radius: 6px; }

    /* Process */
    .steps { display: grid; grid-template-columns: repeat(4, 1fr); gap: 17px; }
    .step { padding: 22px; border-top: 1px solid #a855f755; }
    .step-num { color: #c084fc; font-size: 12px; font-weight: 800; }
    .step h3 { font-size: 15px; margin: 12px 0 8px; }
    .step p { font-size: 12px; color: var(--muted); }

    /* Contact */
    .contact-box {
      padding: 55px 25px;
      text-align: center;
      border: 1px solid #a855f744;
      border-radius: 24px;
      background: radial-gradient(ellipse at 50% 100%, #7e22ce25, transparent 70%), #110b1b;
    }
    .contact-box h2 { font-size: clamp(30px, 4vw, 44px); line-height: 1.2; margin: 15px 0; letter-spacing: -1.5px; }
    .contact-box p { max-width: 550px; margin: 0 auto 25px; color: var(--muted); font-size: 14px; }
    .contact-links { display: flex; justify-content: center; flex-wrap: wrap; gap: 12px; }

    footer { border-top: 1px solid var(--border); padding: 28px 0; }
    .footer-inner { display: flex; justify-content: space-between; gap: 20px; align-items: center; }
    footer p { color: #8e879c; font-size: 11px; }
    .socials { display: flex; gap: 18px; font-size: 12px; color: #c4b5fd; }

    @media (max-width: 800px) {
      .hero-grid { grid-template-columns: 1fr; gap: 38px; }
      .hero { padding: 75px 0; }
      .visual { min-height: 340px; }
      .card-grid, .portfolio-grid { grid-template-columns: repeat(2, 1fr); }
      .steps { grid-template-columns: repeat(2, 1fr); }
      .nav-links {
        display: none; position: absolute; top: 76px; left: 0; right: 0;
        padding: 25px 5%; background: #0d0917;
        border-bottom: 1px solid var(--border);
        flex-direction: column; align-items: stretch; gap: 18px;
      }
      .nav-links.open { display: flex; }
      .menu-toggle { display: block; background: transparent; border: 0; color: white; font-size: 25px; cursor: pointer; }
      .nav-cta { display: none; }
    }
    @media (max-width: 520px) {
      h1 { letter-spacing: -2px; }
      section { padding: 65px 0; }
      .card-grid, .portfolio-grid, .steps { grid-template-columns: 1fr; }
      .visual { min-height: 300px; }
      .ai-core { width: 140px; height: 140px; font-size: 55px; }
      .footer-inner { flex-direction: column; text-align: center; }
      .contact-box { padding: 40px 18px; }
    }
    @media (prefers-reduced-motion: reduce) {
      html { scroll-behavior: auto; }
      *, *::before, *::after { animation-duration: .01ms !important; transition-duration: .01ms !important; }
    }
  </style>
</head>

<body>
  <header>
    <nav class="container">
      <a class="logo" href="#home">VIBE <span>AI</span> STUDIO</a>

      <button class="menu-toggle" id="menuToggle" aria-label="Open navigation" aria-expanded="false">☰</button>

      <div class="nav-links" id="navLinks">
        <a href="#home">Home</a>
        <a href="#services">Services</a>
        <a href="#portfolio">Portfolio</a>
        <a href="#process">Our Process</a>
        <a href="#contact">Contact</a>
      </div>

      <a class="nav-cta" href="#contact">Let's Create ↗</a>
    </nav>
  </header>

  <main>
    <section class="hero" id="home">
      <div class="container hero-grid">
        <div>
          <div class="eyebrow"><span class="dot"></span> The future is creative</div>
          <h1>Stories Reimagined With <span class="gradient">AI.</span></h1>
          <p>
            Welcome to Vibe AI Studio. We turn creative ideas into AI-powered
            animated stories, cinematic visuals and engaging short-form content.
          </p>
          <div class="hero-buttons">
            <a class="btn" href="#portfolio">Explore Our Work ↗</a>
            <a class="btn btn-outline" href="#services">Discover Services</a>
          </div>
          <div class="hero-note">AI STORYTELLING · ANIMATION · DIGITAL CREATIVITY</div>
        </div>

        <div class="visual" aria-label="Abstract purple AI artwork">
          <div class="floating-label label-one">✦ AI Storytelling</div>
          <div class="ai-core"><span>✳</span></div>
          <div class="floating-label label-two">◈ Creative Intelligence</div>
          <div class="floating-label label-three">▶ Short-form Video</div>
        </div>
      </div>
    </section>

    <section id="services">
      <div class="container">
        <div class="section-head">
          <div class="eyebrow">What we create</div>
          <h2>Creative Services for the <span class="gradient">AI Era</span></h2>
          <p>From your first idea to your final video, create content designed to capture attention.</p>
        </div>

        <div class="card-grid">
          <article class="card">
            <div class="card-icon">🎬</div>
            <h3>AI Story Animation</h3>
            <p>Engaging animated stories, imaginative characters and cinematic storytelling for digital audiences.</p>
          </article>
          <article class="card">
            <div class="card-icon">📱</div>
            <h3>YouTube Shorts</h3>
            <p>Vertical short-form videos designed for YouTube Shorts, Instagram Reels and other social platforms.</p>
          </article>
          <article class="card">
            <div class="card-icon">✨</div>
            <h3>AI Visual Creation</h3>
            <p>Creative concepts, AI-generated visual assets and imaginative worlds for your next project.</p>
          </article>
          <article class="card">
            <div class="card-icon">✂️</div>
            <h3>Video Editing</h3>
            <p>Polished edits with pacing, transitions, sound design, subtitles and a consistent visual identity.</p>
          </article>
          <article class="card">
            <div class="card-icon">📢</div>
            <h3>Social Media Content</h3>
            <p>Content concepts and creative assets to help brands build a recognizable online presence.</p>
          </article>
          <article class="card">
            <div class="card-icon">💡</div>
            <h3>Creative Development</h3>
            <p>Story ideas, scripts, hooks and content planning to turn a simple concept into a video project.</p>
          </article>
        </div>
      </div>
    </section>

    <section id="portfolio">
      <div class="container">
        <div class="section-head">
          <div class="eyebrow">Selected concepts</div>
          <h2>Ideas Into <span class="gradient">Experiences</span></h2>
          <p>Explore our creative direction and the types of projects we aim to bring to life.</p>
        </div>

        <div class="portfolio-grid">
          <article class="work">
            <div class="work-art art-one"><span>🌌</span></div>
            <div class="work-info">
              <h3>Beyond the Stars</h3>
              <p>A science-fiction inspired visual story concept.</p>
              <span class="tag">AI STORY CONCEPT</span>
            </div>
          </article>
          <article class="work">
            <div class="work-art art-two"><span>🦊</span></div>
            <div class="work-info">
              <h3>The Hidden Forest</h3>
              <p>A fantasy character and animated story concept.</p>
              <span class="tag">ANIMATION CONCEPT</span>
            </div>
          </article>
          <article class="work">
            <div class="work-art art-three"><span>🚀</span></div>
            <div class="work-info">
              <h3>Future Unlocked</h3>
              <p>A futuristic short-form creative campaign concept.</p>
              <span class="tag">SHORT-FORM CONCEPT</span>
            </div>
          </article>
        </div>
        <p style="text-align:center;color:#8e879c;font-size:11px;margin-top:22px">
          These are concept previews, not completed client projects.
        </p>
      </div>
    </section>

    <section id="process">
      <div class="container">
        <div class="section-head">
          <div class="eyebrow">How we work</div>
          <h2>From Idea to <span class="gradient">Final Cut</span></h2>
          <p>A simple creative workflow designed to keep every project focused.</p>
        </div>

        <div class="steps">
          <div class="step">
            <div class="step-num">01 / DISCOVER</div>
            <h3>Understand the Idea</h3>
            <p>Define the audience, objective, story and creative direction.</p>
          </div>
          <div class="step">
            <div class="step-num">02 / CREATE</div>
            <h3>Build the Story</h3>
            <p>Develop the script, visuals and assets for the project.</p>
          </div>
          <div class="step">
            <div class="step-num">03 / PRODUCE</div>
            <h3>Bring It to Life</h3>
            <p>Generate, edit and assemble the content with care.</p>
          </div>
          <div class="step">
            <div class="step-num">04 / DELIVER</div>
            <h3>Ready to Publish</h3>
            <p>Prepare the final content for the intended platform.</p>
          </div>
        </div>
      </div>
    </section>

    <section id="contact">
      <div class="container">
        <div class="contact-box">
          <div class="eyebrow">Have an idea?</div>
          <h2>Let's Create Something <span class="gradient">Extraordinary.</span></h2>
          <p>
            Have a story, a brand or a creative project in mind?
            Contact Vibe AI Studio and let's explore the possibilities.
          </p>
          <div class="contact-links">
            <!-- Replace the email below with your business email if different. -->
            <a class="btn" href="mailto:vibemediastudio6@gmail.com?subject=Vibe%20AI%20Studio%20Project">
              Email Us ↗
            </a>
            <!-- Replace the Instagram URL with your AI Studio account when available. -->
            <a class="btn btn-outline" href="https://www.instagram.com/vibemedia_studio/" target="_blank" rel="noopener noreferrer">
              Instagram ↗
            </a>
          </div>
        </div>
      </div>
    </section>
  </main>

  <footer>
    <div class="container footer-inner">
      <a class="logo" href="#home">VIBE <span>AI</span> STUDIO</a>
      <p>© <span id="year"></span> Vibe AI Studio. Built for creative possibilities.</p>
      <div class="socials">
        <a href="#services">Services</a>
        <a href="#portfolio">Portfolio</a>
        <a href="#contact">Contact</a>
      </div>
    </div>
  </footer>

  <script>
    const menuToggle = document.getElementById('menuToggle');
    const navLinks = document.getElementById('navLinks');

    menuToggle.addEventListener('click', () => {
      const isOpen = navLinks.classList.toggle('open');
      menuToggle.setAttribute('aria-expanded', String(isOpen));
      menuToggle.setAttribute('aria-label', isOpen ? 'Close navigation' : 'Open navigation');
      menuToggle.textContent = isOpen ? '✕' : '☰';
    });

    navLinks.querySelectorAll('a').forEach(link => {
      link.addEventListener('click', () => {
        navLinks.classList.remove('open');
        menuToggle.setAttribute('aria-expanded', 'false');
        menuToggle.setAttribute('aria-label', 'Open navigation');
        menuToggle.textContent = '☰';
      });
    });

    document.getElementById('year').textContent = new Date().getFullYear();
  </script>
</body>
</html>
