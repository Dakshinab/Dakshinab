<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Dakshina Dissanayake</title>
<link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@300;400;500;600;700&family=Inter:wght@300;400;500&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --bg: #0D0D0D;
    --surface: #161616;
    --surface2: #1E1E1E;
    --border: #2A2A2A;
    --text: #F0EDE8;
    --muted: #888580;
    --accent: #FF5C1A;
    --accent-dim: rgba(255, 92, 26, 0.12);
  }

  html { scroll-behavior: smooth; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'Inter', sans-serif;
    font-size: 16px;
    line-height: 1.7;
    overflow-x: hidden;
  }

  /* ── NOISE OVERLAY ── */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.03'/%3E%3C/svg%3E");
    pointer-events: none;
    z-index: 0;
    opacity: 0.4;
  }

  /* ── LAYOUT ── */
  .container {
    max-width: 780px;
    margin: 0 auto;
    padding: 0 2rem;
    position: relative;
    z-index: 1;
  }

  section { padding: 5rem 0; }

  /* ── SCROLL REVEAL ── */
  .reveal {
    opacity: 0;
    transform: translateY(28px);
    transition: opacity 0.65s cubic-bezier(0.22, 1, 0.36, 1),
                transform 0.65s cubic-bezier(0.22, 1, 0.36, 1);
  }
  .reveal.visible { opacity: 1; transform: none; }

  /* ── NAV ── */
  nav {
    position: fixed;
    top: 0; left: 0; right: 0;
    z-index: 100;
    padding: 1.25rem 2rem;
    display: flex;
    align-items: center;
    justify-content: space-between;
    background: rgba(13, 13, 13, 0.85);
    backdrop-filter: blur(12px);
    border-bottom: 1px solid transparent;
    transition: border-color 0.3s;
  }
  nav.scrolled { border-bottom-color: var(--border); }

  .nav-logo {
    font-family: 'Space Grotesk', sans-serif;
    font-size: 1.05rem;
    font-weight: 600;
    letter-spacing: -0.02em;
    color: var(--text);
    text-decoration: none;
  }
  .nav-logo span { color: var(--accent); }

  .nav-links {
    display: flex;
    gap: 2rem;
    list-style: none;
  }
  .nav-links a {
    font-size: 0.85rem;
    font-weight: 500;
    color: var(--muted);
    text-decoration: none;
    letter-spacing: 0.04em;
    text-transform: uppercase;
    transition: color 0.2s;
  }
  .nav-links a:hover { color: var(--text); }

  /* ── HERO ── */
  #hero {
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
    padding-top: 5rem;
  }

  .hero-eyebrow {
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.8rem;
    color: var(--accent);
    letter-spacing: 0.1em;
    margin-bottom: 1.5rem;
    display: flex;
    align-items: center;
    gap: 0.5rem;
  }
  .hero-eyebrow::before {
    content: '';
    display: inline-block;
    width: 24px;
    height: 1px;
    background: var(--accent);
  }

  .hero-name {
    font-family: 'Space Grotesk', sans-serif;
    font-size: clamp(2.8rem, 8vw, 5.5rem);
    font-weight: 700;
    letter-spacing: -0.04em;
    line-height: 1.05;
    color: var(--text);
    margin-bottom: 0.4rem;
  }

  .hero-name .last {
    color: var(--accent);
  }

  .hero-terminal {
    font-family: 'JetBrains Mono', monospace;
    font-size: clamp(1rem, 2.5vw, 1.35rem);
    color: var(--muted);
    margin-top: 1.25rem;
    margin-bottom: 2.5rem;
    min-height: 2em;
  }
  .hero-terminal .cursor {
    display: inline-block;
    width: 2px;
    height: 1.1em;
    background: var(--accent);
    vertical-align: text-bottom;
    margin-left: 2px;
    animation: blink 1s step-end infinite;
  }
  @keyframes blink { 0%,100%{opacity:1} 50%{opacity:0} }

  .hero-desc {
    max-width: 520px;
    color: var(--muted);
    font-size: 1rem;
    line-height: 1.8;
    margin-bottom: 3rem;
  }

  .hero-cta {
    display: flex;
    gap: 1rem;
    flex-wrap: wrap;
  }

  .btn {
    font-family: 'Space Grotesk', sans-serif;
    font-size: 0.875rem;
    font-weight: 600;
    letter-spacing: 0.02em;
    padding: 0.75rem 1.75rem;
    border-radius: 6px;
    text-decoration: none;
    transition: all 0.2s;
    cursor: pointer;
  }
  .btn-primary {
    background: var(--accent);
    color: #0D0D0D;
    border: 1px solid var(--accent);
  }
  .btn-primary:hover {
    background: #ff7040;
    border-color: #ff7040;
    transform: translateY(-2px);
  }
  .btn-ghost {
    background: transparent;
    color: var(--text);
    border: 1px solid var(--border);
  }
  .btn-ghost:hover {
    border-color: var(--muted);
    transform: translateY(-2px);
  }

  .hero-scroll {
    margin-top: 5rem;
    display: flex;
    align-items: center;
    gap: 0.75rem;
    color: var(--muted);
    font-size: 0.75rem;
    letter-spacing: 0.08em;
    text-transform: uppercase;
  }
  .scroll-line {
    width: 40px;
    height: 1px;
    background: var(--border);
    position: relative;
    overflow: hidden;
  }
  .scroll-line::after {
    content: '';
    position: absolute;
    top: 0; left: -100%;
    width: 100%;
    height: 100%;
    background: var(--accent);
    animation: slide-line 2.5s ease-in-out infinite;
  }
  @keyframes slide-line { 0%{left:-100%} 100%{left:100%} }

  /* ── SECTION HEADER ── */
  .section-label {
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.75rem;
    color: var(--accent);
    letter-spacing: 0.12em;
    text-transform: uppercase;
    margin-bottom: 0.75rem;
    display: flex;
    align-items: center;
    gap: 0.5rem;
  }
  .section-label::before {
    content: '';
    width: 16px;
    height: 1px;
    background: var(--accent);
  }

  .section-title {
    font-family: 'Space Grotesk', sans-serif;
    font-size: clamp(1.6rem, 4vw, 2.4rem);
    font-weight: 700;
    letter-spacing: -0.03em;
    color: var(--text);
    margin-bottom: 1rem;
  }

  .section-sub {
    color: var(--muted);
    max-width: 480px;
    margin-bottom: 3rem;
    font-size: 0.95rem;
  }

  /* ── DIVIDER ── */
  .divider {
    width: 100%;
    height: 1px;
    background: var(--border);
    margin: 0;
  }

  /* ── ABOUT ── */
  .about-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 3rem;
    align-items: start;
  }
  .about-text { color: var(--muted); line-height: 1.9; font-size: 0.97rem; }
  .about-text p + p { margin-top: 1rem; }

  .about-stats {
    display: flex;
    flex-direction: column;
    gap: 1.5rem;
  }
  .stat-item { border-left: 2px solid var(--accent); padding-left: 1.25rem; }
  .stat-number {
    font-family: 'Space Grotesk', sans-serif;
    font-size: 2rem;
    font-weight: 700;
    color: var(--text);
    letter-spacing: -0.04em;
    line-height: 1;
  }
  .stat-label { font-size: 0.8rem; color: var(--muted); margin-top: 0.25rem; letter-spacing: 0.04em; }

  /* ── SKILLS ── */
  .skills-block { margin-bottom: 2.5rem; }
  .skills-block-label {
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.72rem;
    color: var(--muted);
    letter-spacing: 0.1em;
    text-transform: uppercase;
    margin-bottom: 1rem;
  }
  .skill-tags {
    display: flex;
    flex-wrap: wrap;
    gap: 0.6rem;
  }
  .tag {
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.8rem;
    padding: 0.35rem 0.85rem;
    border: 1px solid var(--border);
    border-radius: 4px;
    color: var(--muted);
    background: var(--surface);
    transition: all 0.2s;
    cursor: default;
  }
  .tag:hover {
    border-color: var(--accent);
    color: var(--accent);
    background: var(--accent-dim);
    transform: translateY(-2px);
  }

  /* ── PROJECTS ── */
  .projects-list { display: flex; flex-direction: column; gap: 1px; }

  .project-item {
    padding: 2rem 0;
    border-bottom: 1px solid var(--border);
    display: grid;
    grid-template-columns: 1fr auto;
    gap: 1.5rem;
    align-items: start;
    transition: background 0.2s;
    position: relative;
  }
  .project-item::before {
    content: '';
    position: absolute;
    left: -2rem;
    top: 0; bottom: 0;
    width: 2px;
    background: var(--accent);
    transform: scaleY(0);
    transform-origin: bottom;
    transition: transform 0.35s cubic-bezier(0.22, 1, 0.36, 1);
  }
  .project-item:hover::before { transform: scaleY(1); }

  .project-name {
    font-family: 'Space Grotesk', sans-serif;
    font-size: 1.05rem;
    font-weight: 600;
    color: var(--text);
    margin-bottom: 0.5rem;
    letter-spacing: -0.01em;
  }
  .project-desc { color: var(--muted); font-size: 0.9rem; line-height: 1.7; margin-bottom: 1rem; }
  .project-tech {
    display: flex;
    flex-wrap: wrap;
    gap: 0.4rem;
  }
  .tech-badge {
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.72rem;
    padding: 0.2rem 0.6rem;
    border-radius: 3px;
    background: var(--accent-dim);
    color: var(--accent);
    border: 1px solid rgba(255,92,26,0.2);
  }
  .project-link {
    font-family: 'Space Grotesk', sans-serif;
    font-size: 0.8rem;
    font-weight: 600;
    color: var(--muted);
    text-decoration: none;
    letter-spacing: 0.04em;
    text-transform: uppercase;
    white-space: nowrap;
    transition: color 0.2s;
    padding-top: 0.25rem;
  }
  .project-link:hover { color: var(--accent); }
  .project-link::after { content: ' →'; }

  /* ── EDUCATION ── */
  .edu-card {
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 2rem;
    background: var(--surface);
    position: relative;
    overflow: hidden;
  }
  .edu-card::after {
    content: '';
    position: absolute;
    top: 0; left: 0;
    width: 3px;
    height: 100%;
    background: var(--accent);
  }
  .edu-degree {
    font-family: 'Space Grotesk', sans-serif;
    font-size: 1.1rem;
    font-weight: 700;
    color: var(--text);
    margin-bottom: 0.25rem;
    letter-spacing: -0.02em;
  }
  .edu-school { color: var(--accent); font-size: 0.875rem; font-weight: 500; margin-bottom: 1rem; }
  .edu-meta { display: flex; gap: 2rem; flex-wrap: wrap; }
  .edu-meta span {
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.78rem;
    color: var(--muted);
    letter-spacing: 0.04em;
  }
  .edu-gpa { color: var(--accent) !important; }

  /* ── CONNECT ── */
  .connect-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 1rem;
  }
  .connect-item {
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 1.25rem 1.5rem;
    text-decoration: none;
    background: var(--surface);
    transition: all 0.25s;
    display: block;
  }
  .connect-item:hover {
    border-color: var(--accent);
    background: var(--accent-dim);
    transform: translateY(-3px);
  }
  .connect-type {
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.7rem;
    color: var(--muted);
    letter-spacing: 0.1em;
    text-transform: uppercase;
    margin-bottom: 0.5rem;
  }
  .connect-value {
    font-family: 'Space Grotesk', sans-serif;
    font-size: 0.9rem;
    font-weight: 500;
    color: var(--text);
  }

  /* ── FOOTER ── */
  footer {
    padding: 3rem 0;
    border-top: 1px solid var(--border);
  }
  .footer-inner {
    display: flex;
    align-items: center;
    justify-content: space-between;
    flex-wrap: wrap;
    gap: 1rem;
  }
  .footer-copy {
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.75rem;
    color: var(--muted);
  }
  .footer-quote {
    font-size: 0.8rem;
    color: var(--muted);
    font-style: italic;
    max-width: 320px;
    text-align: right;
  }

  /* ── RESPONSIVE ── */
  @media (max-width: 640px) {
    nav { padding: 1rem 1.25rem; }
    .container { padding: 0 1.25rem; }
    .nav-links { display: none; }
    .about-grid { grid-template-columns: 1fr; gap: 2rem; }
    .footer-inner { flex-direction: column; }
    .footer-quote { text-align: left; }
    .project-item { grid-template-columns: 1fr; }
  }

  @media (prefers-reduced-motion: reduce) {
    .reveal { opacity: 1; transform: none; transition: none; }
    * { animation-duration: 0.01ms !important; transition-duration: 0.01ms !important; }
  }
</style>
</head>
<body>

<!-- NAV -->
<nav id="nav">
  <a href="#hero" class="nav-logo">dakshina<span>.</span></a>
  <ul class="nav-links">
    <li><a href="#about">About</a></li>
    <li><a href="#skills">Skills</a></li>
    <li><a href="#projects">Projects</a></li>
    <li><a href="#connect">Connect</a></li>
  </ul>
</nav>

<!-- HERO -->
<section id="hero">
  <div class="container">
    <p class="hero-eyebrow">available for opportunities</p>
    <h1 class="hero-name">
      Dakshina<br><span class="last">Dissanayake</span>
    </h1>
    <p class="hero-terminal">
      <span id="typewriter"></span><span class="cursor"></span>
    </p>
    <p class="hero-desc">
      IT undergraduate building full-stack products and cloud infrastructure.
      Interested in developer tooling, DevOps automation, and shipping things that actually work.
    </p>
    <div class="hero-cta">
      <a href="#projects" class="btn btn-primary">View Projects</a>
      <a href="#connect" class="btn btn-ghost">Get in Touch</a>
    </div>
    <div class="hero-scroll">
      <span class="scroll-line"></span>
      scroll
    </div>
  </div>
</section>

<div class="divider"></div>

<!-- ABOUT -->
<section id="about">
  <div class="container">
    <div class="reveal">
      <p class="section-label">about</p>
      <h2 class="section-title">Building with purpose.</h2>
    </div>
    <div class="about-grid reveal">
      <div class="about-text">
        <p>I'm a final-year IT undergraduate at Horizon Campus, Sri Lanka, with hands-on experience across the full development lifecycle — from writing APIs to deploying infrastructure on AWS.</p>
        <p>I care about code that's clean, systems that don't break at 3am, and interfaces people actually enjoy using. Currently targeting Full Stack and DevOps roles where both matter.</p>
        <p>When I'm not in the terminal, I'm exploring machine learning fundamentals or pushing a personal project forward.</p>
      </div>
      <div class="about-stats">
        <div class="stat-item">
          <div class="stat-number">3.4</div>
          <div class="stat-label">GPA — BSc (Hons) IT</div>
        </div>
        <div class="stat-item">
          <div class="stat-number">2026</div>
          <div class="stat-label">Graduating</div>
        </div>
        <div class="stat-item">
          <div class="stat-number">Full Stack<br>+ DevOps</div>
          <div class="stat-label" style="margin-top:0.5rem">Target roles</div>
        </div>
      </div>
    </div>
  </div>
</section>

<div class="divider"></div>

<!-- SKILLS -->
<section id="skills">
  <div class="container">
    <div class="reveal">
      <p class="section-label">skills</p>
      <h2 class="section-title">What I work with.</h2>
      <p class="section-sub">A practical toolkit built through real projects, not just coursework.</p>
    </div>

    <div class="skills-block reveal">
      <p class="skills-block-label">Languages</p>
      <div class="skill-tags">
        <span class="tag">JavaScript</span>
        <span class="tag">TypeScript</span>
        <span class="tag">Python</span>
        <span class="tag">Java</span>
        <span class="tag">PHP</span>
        <span class="tag">SQL</span>
        <span class="tag">C++</span>
        <span class="tag">HTML / CSS</span>
      </div>
    </div>

    <div class="skills-block reveal">
      <p class="skills-block-label">Frameworks & Libraries</p>
      <div class="skill-tags">
        <span class="tag">Next.js</span>
        <span class="tag">React</span>
        <span class="tag">Expo React Native</span>
        <span class="tag">Node.js</span>
        <span class="tag">Express.js</span>
        <span class="tag">Prisma</span>
        <span class="tag">NativeWind</span>
        <span class="tag">Tailwind CSS</span>
        <span class="tag">Streamlit</span>
        <span class="tag">Scikit-Learn</span>
      </div>
    </div>

    <div class="skills-block reveal">
      <p class="skills-block-label">Cloud & DevOps</p>
      <div class="skill-tags">
        <span class="tag">AWS</span>
        <span class="tag">Terraform</span>
        <span class="tag">GitHub Actions</span>
        <span class="tag">Docker</span>
        <span class="tag">Supabase</span>
        <span class="tag">Vercel</span>
        <span class="tag">Netlify</span>
        <span class="tag">CI/CD</span>
      </div>
    </div>

    <div class="skills-block reveal">
      <p class="skills-block-label">Databases & Tools</p>
      <div class="skill-tags">
        <span class="tag">PostgreSQL</span>
        <span class="tag">MongoDB</span>
        <span class="tag">MySQL</span>
        <span class="tag">Firebase</span>
        <span class="tag">Git</span>
        <span class="tag">VS Code</span>
        <span class="tag">Android Studio</span>
      </div>
    </div>
  </div>
</section>

<div class="divider"></div>

<!-- PROJECTS -->
<section id="projects">
  <div class="container">
    <div class="reveal">
      <p class="section-label">projects</p>
      <h2 class="section-title">Things I've built.</h2>
      <p class="section-sub">Personal and academic projects that went further than the brief.</p>
    </div>

    <div class="projects-list">

      <div class="project-item reveal">
        <div>
          <p class="project-name">JobTracker</p>
          <p class="project-desc">Cross-platform mobile app for tracking job applications, featuring AI-powered job description analysis via Groq (llama-3.3-70b), Supabase auth, and a polished dark/light UI.</p>
          <div class="project-tech">
            <span class="tech-badge">Expo React Native</span>
            <span class="tech-badge">TypeScript</span>
            <span class="tech-badge">Supabase</span>
            <span class="tech-badge">Groq API</span>
            <span class="tech-badge">Zustand</span>
            <span class="tech-badge">NativeWind</span>
          </div>
        </div>
        <a href="https://github.com/Dakshinab" class="project-link">GitHub</a>
      </div>

      <div class="project-item reveal">
        <div>
          <p class="project-name">Serene Stay — DevOps Pipeline</p>
          <p class="project-desc">Hotel booking app with a full cloud infrastructure: AWS Amplify, RDS (PostgreSQL), S3, IAM, SSM Parameter Store, GitHub Actions CI/CD, and Terraform IaC.</p>
          <div class="project-tech">
            <span class="tech-badge">Next.js</span>
            <span class="tech-badge">AWS</span>
            <span class="tech-badge">Terraform</span>
            <span class="tech-badge">GitHub Actions</span>
            <span class="tech-badge">Prisma</span>
            <span class="tech-badge">RDS</span>
          </div>
        </div>
        <a href="https://github.com/Dakshinab" class="project-link">GitHub</a>
      </div>

      <div class="project-item reveal">
        <div>
          <p class="project-name">Personal Portfolio</p>
          <p class="project-desc">Developer portfolio built with Next.js 15 and React 19, featuring dark/light theme support, responsive layout, and Tailwind CSS. Live at dakshina-bytes.online.</p>
          <div class="project-tech">
            <span class="tech-badge">Next.js 15</span>
            <span class="tech-badge">React 19</span>
            <span class="tech-badge">Tailwind CSS</span>
            <span class="tech-badge">TypeScript</span>
          </div>
        </div>
        <a href="https://dakshina-bytes.online" class="project-link">Live</a>
      </div>

      <div class="project-item reveal">
        <div>
          <p class="project-name">Panda's Kitchen</p>
          <p class="project-desc">A MERN-stack burger shop web experience — full-stack product with a custom frontend and REST API backend. Work in progress.</p>
          <div class="project-tech">
            <span class="tech-badge">MongoDB</span>
            <span class="tech-badge">Express.js</span>
            <span class="tech-badge">React</span>
            <span class="tech-badge">Node.js</span>
          </div>
        </div>
        <a href="https://github.com/Dakshinab" class="project-link">GitHub</a>
      </div>

    </div>
  </div>
</section>

<div class="divider"></div>

<!-- EDUCATION -->
<section id="education">
  <div class="container">
    <div class="reveal">
      <p class="section-label">education</p>
      <h2 class="section-title">Background.</h2>
    </div>
    <div class="edu-card reveal">
      <p class="edu-degree">BSc (Hons) in Information Technology</p>
      <p class="edu-school">Horizon Campus, Sri Lanka</p>
      <div class="edu-meta">
        <span class="edu-gpa">GPA 3.4</span>
        <span>Graduating 2026</span>
        <span>Software Development · Databases · Web Technologies · System Design</span>
      </div>
    </div>
  </div>
</section>

<div class="divider"></div>

<!-- CONNECT -->
<section id="connect">
  <div class="container">
    <div class="reveal">
      <p class="section-label">connect</p>
      <h2 class="section-title">Let's talk.</h2>
      <p class="section-sub">Open to full-time roles, internships, and interesting collaborations.</p>
    </div>
    <div class="connect-grid reveal">
      <a href="mailto:dakshinabanu@gmail.com" class="connect-item">
        <p class="connect-type">Email</p>
        <p class="connect-value">dakshinabanu@gmail.com</p>
      </a>
      <a href="https://www.linkedin.com/in/dakshinab-dissanayake-301162227/" target="_blank" class="connect-item">
        <p class="connect-type">LinkedIn</p>
        <p class="connect-value">dakshinab-dissanayake</p>
      </a>
      <a href="https://github.com/Dakshinab" target="_blank" class="connect-item">
        <p class="connect-type">GitHub</p>
        <p class="connect-value">Dakshinab</p>
      </a>
      <a href="https://dakshina-bytes.online" target="_blank" class="connect-item">
        <p class="connect-type">Portfolio</p>
        <p class="connect-value">dakshina-bytes.online</p>
      </a>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="container">
    <div class="footer-inner">
      <p class="footer-copy">© 2026 Dakshina Dissanayake · Colombo, Sri Lanka</p>
      <p class="footer-quote">"Continuous learning and consistent execution build strong engineers."</p>
    </div>
  </div>
</footer>

<script>
  /* ── TYPEWRITER ── */
  const roles = [
    "Full Stack Developer",
    "DevOps Engineer",
    "Cloud Enthusiast",
    "IT Undergraduate"
  ];
  let ri = 0, ci = 0, deleting = false;
  const el = document.getElementById('typewriter');

  function type() {
    const current = roles[ri];
    if (!deleting) {
      el.textContent = current.slice(0, ++ci);
      if (ci === current.length) { deleting = true; setTimeout(type, 1800); return; }
    } else {
      el.textContent = current.slice(0, --ci);
      if (ci === 0) { deleting = false; ri = (ri + 1) % roles.length; }
    }
    setTimeout(type, deleting ? 45 : 90);
  }
  setTimeout(type, 600);

  /* ── NAV SCROLL ── */
  const nav = document.getElementById('nav');
  window.addEventListener('scroll', () => {
    nav.classList.toggle('scrolled', window.scrollY > 40);
  });

  /* ── SCROLL REVEAL ── */
  const observer = new IntersectionObserver((entries) => {
    entries.forEach((e, i) => {
      if (e.isIntersecting) {
        const siblings = [...e.target.parentElement.querySelectorAll('.reveal')];
        const delay = siblings.indexOf(e.target) * 80;
        setTimeout(() => e.target.classList.add('visible'), delay);
        observer.unobserve(e.target);
      }
    });
  }, { threshold: 0.12 });

  document.querySelectorAll('.reveal').forEach(el => observer.observe(el));
</script>
</body>
</html>
