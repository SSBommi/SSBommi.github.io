<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Sai Sanjay Bommisetty</title>
<link href="https://fonts.googleapis.com/css2?family=DM+Mono:ital,wght@0,300;0,400;0,500;1,300&family=Syne:wght@400;500;600;700;800&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #0a0a0a;
    --surface: #111111;
    --border: #1e1e1e;
    --accent: #e8ff47;
    --accent2: #ff6b35;
    --text: #f0f0f0;
    --muted: #666;
    --card: #141414;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  html { scroll-behavior: smooth; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'DM Mono', monospace;
    font-size: 14px;
    line-height: 1.6;
    overflow-x: hidden;
    cursor: none;
  }

  /* Custom cursor */
  .cursor {
    width: 10px;
    height: 10px;
    background: var(--accent);
    border-radius: 50%;
    position: fixed;
    pointer-events: none;
    z-index: 9999;
    transition: transform 0.15s ease;
    mix-blend-mode: difference;
  }

  .cursor-ring {
    width: 36px;
    height: 36px;
    border: 1px solid var(--accent);
    border-radius: 50%;
    position: fixed;
    pointer-events: none;
    z-index: 9998;
    transition: all 0.12s ease;
    mix-blend-mode: difference;
    opacity: 0.5;
  }

  /* Noise texture overlay */
  body::before {
    content: '';
    position: fixed;
    top: 0; left: 0;
    width: 100%; height: 100%;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.04'/%3E%3C/svg%3E");
    pointer-events: none;
    z-index: 1000;
    opacity: 0.4;
  }

  /* Nav */
  nav {
    position: fixed;
    top: 0; left: 0; right: 0;
    z-index: 100;
    padding: 20px 48px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    border-bottom: 1px solid var(--border);
    background: rgba(10,10,10,0.85);
    backdrop-filter: blur(12px);
  }

  .nav-logo {
    font-family: 'Syne', sans-serif;
    font-weight: 800;
    font-size: 16px;
    letter-spacing: -0.5px;
    color: var(--accent);
  }

  .nav-links {
    display: flex;
    gap: 32px;
    list-style: none;
  }

  .nav-links a {
    color: var(--muted);
    text-decoration: none;
    font-size: 12px;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    transition: color 0.2s;
  }

  .nav-links a:hover { color: var(--accent); }

  /* Hero */
  .hero {
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
    padding: 0 48px 80px;
    position: relative;
    overflow: hidden;
  }

  .hero-bg {
    position: absolute;
    top: 0; left: 0; right: 0; bottom: 0;
    background: 
      radial-gradient(ellipse 60% 50% at 70% 30%, rgba(232,255,71,0.06) 0%, transparent 70%),
      radial-gradient(ellipse 40% 40% at 20% 70%, rgba(255,107,53,0.04) 0%, transparent 60%);
  }

  .hero-tag {
    font-size: 11px;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--accent);
    margin-bottom: 24px;
    opacity: 0;
    animation: fadeUp 0.8s ease 0.2s forwards;
  }

  .hero-name {
    font-family: 'Syne', sans-serif;
    font-weight: 800;
    font-size: clamp(56px, 9vw, 130px);
    line-height: 0.9;
    letter-spacing: -4px;
    margin-bottom: 32px;
    opacity: 0;
    animation: fadeUp 0.8s ease 0.4s forwards;
  }

  .hero-name span {
    color: var(--accent);
    display: block;
  }

  .hero-desc {
    max-width: 520px;
    color: var(--muted);
    font-size: 13px;
    line-height: 1.8;
    margin-bottom: 40px;
    opacity: 0;
    animation: fadeUp 0.8s ease 0.6s forwards;
  }

  .hero-meta {
    display: flex;
    gap: 40px;
    opacity: 0;
    animation: fadeUp 0.8s ease 0.8s forwards;
  }

  .hero-meta-item {
    display: flex;
    flex-direction: column;
    gap: 4px;
  }

  .hero-meta-label {
    font-size: 10px;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    color: var(--muted);
  }

  .hero-meta-value {
    font-size: 13px;
    color: var(--text);
  }

  .hero-scroll {
    position: absolute;
    bottom: 40px;
    right: 48px;
    display: flex;
    align-items: center;
    gap: 12px;
    color: var(--muted);
    font-size: 11px;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    opacity: 0;
    animation: fadeUp 0.8s ease 1s forwards;
  }

  .scroll-line {
    width: 40px;
    height: 1px;
    background: var(--muted);
    animation: pulse 2s ease infinite;
  }

  /* Sections */
  section {
    padding: 100px 48px;
    border-top: 1px solid var(--border);
  }

  .section-label {
    font-size: 10px;
    letter-spacing: 0.25em;
    text-transform: uppercase;
    color: var(--accent);
    margin-bottom: 48px;
    display: flex;
    align-items: center;
    gap: 16px;
  }

  .section-label::after {
    content: '';
    flex: 1;
    max-width: 60px;
    height: 1px;
    background: var(--accent);
    opacity: 0.4;
  }

  .section-title {
    font-family: 'Syne', sans-serif;
    font-weight: 700;
    font-size: clamp(32px, 4vw, 56px);
    letter-spacing: -2px;
    line-height: 1;
    margin-bottom: 64px;
  }

  /* Experience */
  .exp-list {
    display: flex;
    flex-direction: column;
    gap: 0;
  }

  .exp-item {
    display: grid;
    grid-template-columns: 200px 1fr;
    gap: 48px;
    padding: 40px 0;
    border-bottom: 1px solid var(--border);
    transition: background 0.3s;
    position: relative;
  }

  .exp-item::before {
    content: '';
    position: absolute;
    left: -48px;
    top: 0;
    bottom: 0;
    width: 2px;
    background: transparent;
    transition: background 0.3s;
  }

  .exp-item:hover::before {
    background: var(--accent);
  }

  .exp-meta {
    display: flex;
    flex-direction: column;
    gap: 6px;
    padding-top: 4px;
  }

  .exp-date {
    font-size: 11px;
    color: var(--muted);
    letter-spacing: 0.05em;
  }

  .exp-type {
    display: inline-block;
    padding: 3px 10px;
    border: 1px solid var(--border);
    font-size: 10px;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    color: var(--muted);
    width: fit-content;
  }

  .exp-content {}

  .exp-company {
    font-family: 'Syne', sans-serif;
    font-weight: 700;
    font-size: 22px;
    letter-spacing: -0.5px;
    margin-bottom: 4px;
  }

  .exp-role {
    color: var(--accent);
    font-size: 12px;
    margin-bottom: 16px;
    letter-spacing: 0.05em;
  }

  .exp-bullets {
    list-style: none;
    display: flex;
    flex-direction: column;
    gap: 8px;
  }

  .exp-bullets li {
    color: var(--muted);
    font-size: 12px;
    line-height: 1.7;
    padding-left: 16px;
    position: relative;
  }

  .exp-bullets li::before {
    content: '—';
    position: absolute;
    left: 0;
    color: var(--accent);
    opacity: 0.6;
  }

  /* Projects */
  .projects-grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 2px;
  }

  .project-card {
    background: var(--card);
    padding: 40px;
    position: relative;
    overflow: hidden;
    transition: all 0.3s;
    border: 1px solid var(--border);
  }

  .project-card:hover {
    border-color: var(--accent);
    background: #161616;
  }

  .project-card:hover .project-arrow {
    transform: translate(4px, -4px);
    color: var(--accent);
  }

  .project-num {
    font-size: 11px;
    color: var(--muted);
    letter-spacing: 0.1em;
    margin-bottom: 24px;
  }

  .project-title {
    font-family: 'Syne', sans-serif;
    font-weight: 700;
    font-size: 20px;
    letter-spacing: -0.5px;
    margin-bottom: 12px;
    line-height: 1.2;
  }

  .project-desc {
    color: var(--muted);
    font-size: 12px;
    line-height: 1.7;
    margin-bottom: 24px;
  }

  .project-tags {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
    margin-bottom: 24px;
  }

  .tag {
    padding: 4px 10px;
    border: 1px solid var(--border);
    font-size: 10px;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    color: var(--muted);
  }

  .project-award {
    font-size: 11px;
    color: var(--accent);
    letter-spacing: 0.05em;
  }

  .project-arrow {
    position: absolute;
    top: 32px;
    right: 32px;
    font-size: 18px;
    transition: all 0.3s;
    color: var(--muted);
  }

  /* Skills */
  .skills-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 2px;
  }

  .skill-block {
    background: var(--card);
    border: 1px solid var(--border);
    padding: 32px;
  }

  .skill-category {
    font-size: 10px;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--accent);
    margin-bottom: 20px;
  }

  .skill-items {
    display: flex;
    flex-direction: column;
    gap: 10px;
  }

  .skill-item {
    display: flex;
    justify-content: space-between;
    align-items: center;
    font-size: 12px;
    color: var(--text);
    padding-bottom: 10px;
    border-bottom: 1px solid var(--border);
  }

  .skill-item:last-child { border-bottom: none; padding-bottom: 0; }

  .skill-bar {
    width: 60px;
    height: 2px;
    background: var(--border);
    position: relative;
    overflow: hidden;
  }

  .skill-fill {
    position: absolute;
    left: 0; top: 0; bottom: 0;
    background: var(--accent);
  }

  /* Stats */
  .stats-row {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 2px;
    margin-bottom: 2px;
  }

  .stat-block {
    background: var(--card);
    border: 1px solid var(--border);
    padding: 40px 32px;
    text-align: center;
  }

  .stat-num {
    font-family: 'Syne', sans-serif;
    font-weight: 800;
    font-size: 48px;
    letter-spacing: -3px;
    color: var(--accent);
    line-height: 1;
    margin-bottom: 8px;
  }

  .stat-label {
    font-size: 11px;
    color: var(--muted);
    letter-spacing: 0.1em;
    text-transform: uppercase;
  }

  /* Contact */
  .contact-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 64px;
    align-items: start;
  }

  .contact-heading {
    font-family: 'Syne', sans-serif;
    font-weight: 800;
    font-size: clamp(40px, 5vw, 72px);
    letter-spacing: -3px;
    line-height: 0.95;
    margin-bottom: 32px;
  }

  .contact-heading span { color: var(--accent); }

  .contact-sub {
    color: var(--muted);
    font-size: 13px;
    line-height: 1.8;
    max-width: 380px;
  }

  .contact-links {
    display: flex;
    flex-direction: column;
    gap: 16px;
    padding-top: 8px;
  }

  .contact-link {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 20px 24px;
    border: 1px solid var(--border);
    text-decoration: none;
    color: var(--text);
    font-size: 13px;
    transition: all 0.2s;
    background: var(--card);
  }

  .contact-link:hover {
    border-color: var(--accent);
    background: #161616;
    color: var(--accent);
  }

  .contact-link-arrow {
    font-size: 16px;
    transition: transform 0.2s;
  }

  .contact-link:hover .contact-link-arrow {
    transform: translate(4px, -4px);
  }

  /* Footer */
  footer {
    padding: 32px 48px;
    border-top: 1px solid var(--border);
    display: flex;
    justify-content: space-between;
    align-items: center;
    color: var(--muted);
    font-size: 11px;
    letter-spacing: 0.05em;
  }

  /* Animations */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(24px); }
    to { opacity: 1; transform: translateY(0); }
  }

  @keyframes pulse {
    0%, 100% { opacity: 0.4; }
    50% { opacity: 1; }
  }

  .reveal {
    opacity: 0;
    transform: translateY(20px);
    transition: opacity 0.7s ease, transform 0.7s ease;
  }

  .reveal.visible {
    opacity: 1;
    transform: translateY(0);
  }

  /* Ticker */
  .ticker-wrap {
    overflow: hidden;
    border-top: 1px solid var(--border);
    border-bottom: 1px solid var(--border);
    padding: 14px 0;
    background: var(--surface);
  }

  .ticker {
    display: flex;
    gap: 48px;
    animation: ticker 20s linear infinite;
    white-space: nowrap;
  }

  .ticker-item {
    font-size: 11px;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--muted);
    flex-shrink: 0;
  }

  .ticker-item span { color: var(--accent); margin-right: 48px; }

  @keyframes ticker {
    from { transform: translateX(0); }
    to { transform: translateX(-50%); }
  }

  @media (max-width: 768px) {
    nav { padding: 16px 24px; }
    .hero { padding: 0 24px 60px; }
    .hero-name { font-size: 48px; letter-spacing: -2px; }
    section { padding: 60px 24px; }
    .exp-item { grid-template-columns: 1fr; gap: 16px; }
    .projects-grid { grid-template-columns: 1fr; }
    .skills-grid { grid-template-columns: 1fr; }
    .stats-row { grid-template-columns: repeat(2, 1fr); }
    .contact-grid { grid-template-columns: 1fr; gap: 40px; }
    footer { flex-direction: column; gap: 8px; text-align: center; }
  }
</style>
</head>
<body>

<div class="cursor" id="cursor"></div>
<div class="cursor-ring" id="cursorRing"></div>

<nav>
  <div class="nav-logo">SSB</div>
  <ul class="nav-links">
    <li><a href="#experience">Experience</a></li>
    <li><a href="#projects">Projects</a></li>
    <li><a href="#skills">Skills</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
</nav>

<!-- Hero -->
<section class="hero">
  <div class="hero-bg"></div>
  <div class="hero-tag">Mechanical Engineer / Hardware Builder</div>
  <h1 class="hero-name">
    Sai Sanjay
    <span>Bommisetty</span>
  </h1>
  <p class="hero-desc">
    Sophomore ME at UIUC building real hardware from scratch — biometric sensing systems, pneumatic actuation, precision robotics, and CubeSat thermal analysis. Headed toward humanoid robotics and the intersection of physical systems and human sensing.
  </p>
  <div class="hero-meta">
    <div class="hero-meta-item">
      <span class="hero-meta-label">University</span>
      <span class="hero-meta-value">UIUC — Grainger Engineering</span>
    </div>
    <div class="hero-meta-item">
      <span class="hero-meta-label">GPA</span>
      <span class="hero-meta-value">3.9 / 4.0</span>
    </div>
    <div class="hero-meta-item">
      <span class="hero-meta-label">Location</span>
      <span class="hero-meta-value">Champaign, IL</span>
    </div>
    <div class="hero-meta-item">
      <span class="hero-meta-label">Status</span>
      <span class="hero-meta-value">Open to Opportunities</span>
    </div>
  </div>
  <div class="hero-scroll">
    <div class="scroll-line"></div>
    Scroll
  </div>
</section>

<!-- Ticker -->
<div class="ticker-wrap">
  <div class="ticker">
    <span class="ticker-item"><span>★</span> Biometric Sensing</span>
    <span class="ticker-item"><span>★</span> Electromechanical Systems</span>
    <span class="ticker-item"><span>★</span> FEA / Thermal Analysis</span>
    <span class="ticker-item"><span>★</span> PCB Design</span>
    <span class="ticker-item"><span>★</span> Pneumatic Actuation</span>
    <span class="ticker-item"><span>★</span> Humanoid Robotics</span>
    <span class="ticker-item"><span>★</span> Sensor Integration</span>
    <span class="ticker-item"><span>★</span> Biometric Sensing</span>
    <span class="ticker-item"><span>★</span> Electromechanical Systems</span>
    <span class="ticker-item"><span>★</span> FEA / Thermal Analysis</span>
    <span class="ticker-item"><span>★</span> PCB Design</span>
    <span class="ticker-item"><span>★</span> Pneumatic Actuation</span>
    <span class="ticker-item"><span>★</span> Humanoid Robotics</span>
    <span class="ticker-item"><span>★</span> Sensor Integration</span>
  </div>
</div>

<!-- Stats -->
<section style="padding: 60px 48px;">
  <div class="stats-row reveal">
    <div class="stat-block">
      <div class="stat-num">3.9</div>
      <div class="stat-label">GPA at UIUC</div>
    </div>
    <div class="stat-block">
      <div class="stat-num">3×</div>
      <div class="stat-label">Award Winner</div>
    </div>
    <div class="stat-block">
      <div class="stat-num">15</div>
      <div class="stat-label">Person Team Led</div>
    </div>
    <div class="stat-block">
      <div class="stat-num">2.5M</div>
      <div class="stat-label">Patients Impacted</div>
    </div>
  </div>
</section>

<!-- Experience -->
<section id="experience">
  <div class="section-label">Experience</div>
  <h2 class="section-title reveal">Where I've<br>built things.</h2>

  <div class="exp-list">

    <div class="exp-item reveal">
      <div class="exp-meta">
        <span class="exp-date">May 2026 — Aug 2026</span>
        <span class="exp-type">Internship</span>
      </div>
      <div class="exp-content">
        <div class="exp-company">International Motors</div>
        <div class="exp-role">Human Factors & Biometrics Intern — Lisle, IL</div>
        <ul class="exp-bullets">
          <li>Building biometric sensing pipelines to capture physiological data during human driving studies</li>
          <li>Integrating sensors including eye trackers, GSR, heart rate monitors, and SpO2 devices into a unified instrumentation system</li>
          <li>Developing data collection and synchronization workflows for the Experience Design R&D team</li>
        </ul>
      </div>
    </div>

    <div class="exp-item reveal">
      <div class="exp-meta">
        <span class="exp-date">May 2025 — Oct 2025</span>
        <span class="exp-type">Internship</span>
      </div>
      <div class="exp-content">
        <div class="exp-company">Northrop Grumman Innovation Lab</div>
        <div class="exp-role">R&D Intern — Baltimore, MD</div>
        <ul class="exp-bullets">
          <li>Designed and prototyped hardware housings integrating Raspberry Pi, sensors, and bone-conduction transducers — validated electromechanical integration across iterative build cycles</li>
          <li>Led a 4-person team to develop a wearable hardware system integrating AR optics, PCB electronics, and sensor fusion — owned end-to-end mechanical design, prototyping, and physical validation</li>
        </ul>
      </div>
    </div>

    <div class="exp-item reveal">
      <div class="exp-meta">
        <span class="exp-date">Sep 2025 — Present</span>
        <span class="exp-type">Research</span>
      </div>
      <div class="exp-content">
        <div class="exp-company">LASSI — UIUC</div>
        <div class="exp-role">Undergraduate Structures/Thermal Researcher — Champaign, IL</div>
        <ul class="exp-bullets">
          <li>Running FEA studies on the deployer interface of the MonARCH 12U CubeSat in Siemens NX, simulating structural loads and validating interface compliance with CubeSat standards</li>
          <li>Converting CAD geometry into Thermal Desktop models to analyze heat flux and temperature gradients across satellite subsystems during orbital cycles</li>
          <li>Supporting systems engineering and trade studies under SWaP and radiation constraints</li>
        </ul>
      </div>
    </div>

  </div>
</section>

<!-- Projects -->
<section id="projects">
  <div class="section-label">Projects</div>
  <h2 class="section-title reveal">Hardware I've<br>shipped.</h2>

  <div class="projects-grid">

    <div class="project-card reveal">
      <div class="project-arrow">↗</div>
      <div class="project-num">01</div>
      <div class="project-title">Smart Mattress Topper — Pressure Ulcer Prevention</div>
      <p class="project-desc">Led a 15-person ASME team building an embedded pressure sensor array with pneumatic actuation to monitor patient pressure points and prevent ulcers. Designed the full hardware stack from PCB to pneumatic repositioning system.</p>
      <div class="project-tags">
        <span class="tag">Arduino</span>
        <span class="tag">PCB Design</span>
        <span class="tag">Pneumatic Actuation</span>
        <span class="tag">Sensor Arrays</span>
      </div>
      <div class="project-award">🏆 1st & 2nd Place — Engineering Industry Impact Award (100+ projects) &nbsp;·&nbsp; Semifinalist — International Tapie Medical Competition</div>
    </div>

    <div class="project-card reveal">
      <div class="project-arrow">↗</div>
      <div class="project-num">02</div>
      <div class="project-title">Cartesian Gantry & Microbot System</div>
      <p class="project-desc">Designed a high-precision X/Y/Z gantry system for a custom robotic end-effector achieving 0.5mm positional accuracy. Integrated Arduino/ESP32 microcontrollers to synchronize multi-axis movement across the full electromechanical system.</p>
      <div class="project-tags">
        <span class="tag">ESP32</span>
        <span class="tag">Mechatronics</span>
        <span class="tag">Lead Screw Drives</span>
        <span class="tag">CAD</span>
      </div>
      <div class="project-award">🏆 1st Place — Distinguished Tech Award (UIUC EOH)</div>
    </div>

    <div class="project-card reveal">
      <div class="project-arrow">↗</div>
      <div class="project-num">03</div>
      <div class="project-title">MonARCH 12U CubeSat — Thermal & Structural Analysis</div>
      <p class="project-desc">Running FEA and thermal modeling for a 12U CubeSat at LASSI. Simulating structural loads at the deployer interface in Siemens NX and building Thermal Desktop models to evaluate heat flux across satellite subsystems in orbital cycles.</p>
      <div class="project-tags">
        <span class="tag">Siemens NX</span>
        <span class="tag">Thermal Desktop</span>
        <span class="tag">FEA</span>
        <span class="tag">Space Systems</span>
      </div>
    </div>

    <div class="project-card reveal">
      <div class="project-arrow">↗</div>
      <div class="project-num">04</div>
      <div class="project-title">AR Wearable Hardware System — Northrop Grumman</div>
      <p class="project-desc">Designed and prototyped a wearable hardware platform at the Northrop Grumman Innovation Lab integrating Raspberry Pi compute, bone-conduction transducers, custom sensors, and PCB electronics. Led 4-person team through end-to-end design, build, and validation.</p>
      <div class="project-tags">
        <span class="tag">Raspberry Pi</span>
        <span class="tag">PCB Electronics</span>
        <span class="tag">Sensor Fusion</span>
        <span class="tag">Wearables</span>
      </div>
    </div>

  </div>
</section>

<!-- Skills -->
<section id="skills">
  <div class="section-label">Skills</div>
  <h2 class="section-title reveal">Tools &<br>capabilities.</h2>

  <div class="skills-grid reveal">
    <div class="skill-block">
      <div class="skill-category">CAD & Simulation</div>
      <div class="skill-items">
        <div class="skill-item">Siemens NX <div class="skill-bar"><div class="skill-fill" style="width:90%"></div></div></div>
        <div class="skill-item">Fusion 360 <div class="skill-bar"><div class="skill-fill" style="width:85%"></div></div></div>
        <div class="skill-item">Thermal Desktop <div class="skill-bar"><div class="skill-fill" style="width:80%"></div></div></div>
        <div class="skill-item">AutoCAD <div class="skill-bar"><div class="skill-fill" style="width:75%"></div></div></div>
        <div class="skill-item">FEA <div class="skill-bar"><div class="skill-fill" style="width:85%"></div></div></div>
      </div>
    </div>

    <div class="skill-block">
      <div class="skill-category">Electronics & Embedded</div>
      <div class="skill-items">
        <div class="skill-item">Arduino IDE <div class="skill-bar"><div class="skill-fill" style="width:90%"></div></div></div>
        <div class="skill-item">PCB Design <div class="skill-bar"><div class="skill-fill" style="width:80%"></div></div></div>
        <div class="skill-item">Circuit Design <div class="skill-bar"><div class="skill-fill" style="width:80%"></div></div></div>
        <div class="skill-item">ESP32 / Raspberry Pi <div class="skill-bar"><div class="skill-fill" style="width:85%"></div></div></div>
        <div class="skill-item">Sensor Integration <div class="skill-bar"><div class="skill-fill" style="width:88%"></div></div></div>
      </div>
    </div>

    <div class="skill-block">
      <div class="skill-category">Programming</div>
      <div class="skill-items">
        <div class="skill-item">Python <div class="skill-bar"><div class="skill-fill" style="width:75%"></div></div></div>
        <div class="skill-item">Data Pipeline Dev <div class="skill-bar"><div class="skill-fill" style="width:70%"></div></div></div>
        <div class="skill-item">Hardware Scripting <div class="skill-bar"><div class="skill-fill" style="width:72%"></div></div></div>
      </div>
    </div>
  </div>
</section>

<!-- Contact -->
<section id="contact">
  <div class="section-label">Contact</div>
  <div class="contact-grid reveal">
    <div>
      <h2 class="contact-heading">Let's<br>build<br><span>something.</span></h2>
      <p class="contact-sub">Open to internship opportunities in humanoid robotics, biometric hardware, defense tech, and aerospace. Reach out directly — I respond fast.</p>
    </div>
    <div class="contact-links">
      <a class="contact-link" href="mailto:ssb13@illinois.edu">
        ssb13@illinois.edu
        <span class="contact-link-arrow">↗</span>
      </a>
      <a class="contact-link" href="https://linkedin.com/in/ssbommisetty" target="_blank">
        linkedin.com/in/ssbommisetty
        <span class="contact-link-arrow">↗</span>
      </a>
      <a class="contact-link" href="tel:3313855335">
        (331) 385-5335
        <span class="contact-link-arrow">↗</span>
      </a>
    </div>
  </div>
</section>

<footer>
  <span>Sai Sanjay Bommisetty © 2026</span>
  <span>UIUC Mechanical Engineering — Hoeft T&M Minor</span>
</footer>

<script>
  // Custom cursor
  const cursor = document.getElementById('cursor');
  const ring = document.getElementById('cursorRing');
  let mouseX = 0, mouseY = 0;
  let ringX = 0, ringY = 0;

  document.addEventListener('mousemove', e => {
    mouseX = e.clientX;
    mouseY = e.clientY;
    cursor.style.left = mouseX - 5 + 'px';
    cursor.style.top = mouseY - 5 + 'px';
  });

  function animateRing() {
    ringX += (mouseX - ringX - 18) * 0.12;
    ringY += (mouseY - ringY - 18) * 0.12;
    ring.style.left = ringX + 'px';
    ring.style.top = ringY + 'px';
    requestAnimationFrame(animateRing);
  }
  animateRing();

  document.querySelectorAll('a, button').forEach(el => {
    el.addEventListener('mouseenter', () => {
      cursor.style.transform = 'scale(2.5)';
      ring.style.transform = 'scale(1.5)';
    });
    el.addEventListener('mouseleave', () => {
      cursor.style.transform = 'scale(1)';
      ring.style.transform = 'scale(1)';
    });
  });

  // Scroll reveal
  const reveals = document.querySelectorAll('.reveal');
  const observer = new IntersectionObserver((entries) => {
    entries.forEach((entry, i) => {
      if (entry.isIntersecting) {
        setTimeout(() => {
          entry.target.classList.add('visible');
        }, i * 80);
      }
    });
  }, { threshold: 0.1 });

  reveals.forEach(el => observer.observe(el));
</script>

</body>
</html>
