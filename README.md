# SSBommi.github.io
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
  }

  section {
    padding: 100px 48px;
  }

  .hero-meta {
    display: flex;
    gap: 40px;
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

  .exp-company {
    font-family: 'Syne', sans-serif;
    font-weight: 700;
    font-size: 22px;
  }
</style>
</head>

<body>

<div class="cursor"></div>
<div class="cursor-ring"></div>

<nav>
  <div class="nav-logo">SSB</div>
  <ul class="nav-links">
    <li><a href="#experience">Experience</a></li>
  </ul>
</nav>

<section class="hero">
  <div class="hero-meta">
    <div class="hero-meta-item">
      <span class="hero-meta-label">Status</span>
      <span class="hero-meta-value"></span>
    </div>
  </div>
</section>

<section id="experience">
  <div class="exp-item">
    <div class="exp-content">
      <div class="exp-company">Northrop Grumman Innovation Lab</div>
    </div>
  </div>
</section>

</body>
</html>
