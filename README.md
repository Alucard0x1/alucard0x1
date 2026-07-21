<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Mythical Profile</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Cinzel+Decorative:wght@400;700;900&family=Cormorant+Garamond:ital,wght@0,300;0,400;0,600;1,300;1,400&family=MedievalSharp&display=swap" rel="stylesheet">
<style>
  :root {
    --bg-deep: #0a0a12;
    --bg-card: #12121f;
    --gold: #d4af37;
    --gold-bright: #f5d67b;
    --gold-dim: #8a7028;
    --mystic: #7b4bb3;
    --mystic-bright: #a97cf5;
    --celestial: #4a90e2;
    --text-primary: #e8e4d9;
    --text-dim: #8a8678;
    --border-glow: rgba(212, 175, 55, 0.3);
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: var(--bg-deep);
    background-image:
      radial-gradient(ellipse at top, rgba(123, 75, 179, 0.15) 0%, transparent 50%),
      radial-gradient(ellipse at bottom, rgba(74, 144, 226, 0.1) 0%, transparent 50%);
    color: var(--text-primary);
    font-family: 'Cormorant Garamond', serif;
    min-height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 40px 20px;
    position: relative;
    overflow-x: hidden;
  }

  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image:
      repeating-linear-gradient(0deg, transparent, transparent 2px, rgba(212, 175, 55, 0.03) 2px, rgba(212, 175, 55, 0.03) 4px),
      repeating-linear-gradient(90deg, transparent, transparent 2px, rgba(212, 175, 55, 0.03) 2px, rgba(212, 175, 55, 0.03) 4px);
    pointer-events: none;
    z-index: 0;
  }

  .stars {
    position: fixed;
    inset: 0;
    pointer-events: none;
    z-index: 0;
  }

  .star {
    position: absolute;
    width: 2px;
    height: 2px;
    background: var(--gold-bright);
    border-radius: 50%;
    animation: twinkle var(--duration, 3s) ease-in-out infinite;
    opacity: 0;
  }

  @keyframes twinkle {
    0%, 100% { opacity: 0; transform: scale(0.5); }
    50% { opacity: 0.8; transform: scale(1.2); }
  }

  .profile-frame {
    position: relative;
    max-width: 900px;
    width: 100%;
    z-index: 1;
    padding: 60px 40px;
    background: linear-gradient(145deg, rgba(18, 18, 31, 0.9), rgba(10, 10, 18, 0.95));
    border: 1px solid var(--border-glow);
    box-shadow:
      0 0 60px rgba(212, 175, 55, 0.15),
      inset 0 0 60px rgba(123, 75, 179, 0.05);
  }

  .profile-frame::before {
    content: '';
    position: absolute;
    inset: 8px;
    border: 1px solid rgba(212, 175, 55, 0.15);
    pointer-events: none;
  }

  .corner {
    position: absolute;
    width: 40px;
    height: 40px;
    border: 2px solid var(--gold);
    opacity: 0.6;
  }

  .corner-tl { top: 15px; left: 15px; border-right: none; border-bottom: none; }
  .corner-tr { top: 15px; right: 15px; border-left: none; border-bottom: none; }
  .corner-bl { bottom: 15px; left: 15px; border-right: none; border-top: none; }
  .corner-br { bottom: 15px; right: 15px; border-left: none; border-top: none; }

  .header {
    text-align: center;
    margin-bottom: 50px;
    position: relative;
  }

  .title {
    font-family: 'Cinzel Decorative', serif;
    font-size: clamp(2rem, 5vw, 3.5rem);
    font-weight: 900;
    background: linear-gradient(135deg, var(--gold-bright), var(--gold), var(--gold-bright));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    margin-bottom: 12px;
    animation: shimmer 4s ease-in-out infinite;
    filter: drop-shadow(0 0 20px rgba(212, 175, 55, 0.4));
  }

  @keyframes shimmer {
    0%, 100% { filter: drop-shadow(0 0 20px rgba(212, 175, 55, 0.4)); }
    50% { filter: drop-shadow(0 0 30px rgba(245, 214, 123, 0.6)); }
  }

  .subtitle {
    font-family: 'Cormorant Garamond', serif;
    font-style: italic;
    font-size: 1.1rem;
    color: var(--text-dim);
    letter-spacing: 0.3em;
    text-transform: lowercase;
    font-weight: 300;
  }

  .divider {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 15px;
    margin: 40px 0;
  }

  .divider-line {
    flex: 1;
    height: 1px;
    background: linear-gradient(90deg, transparent, var(--gold-dim), transparent);
    max-width: 200px;
  }

  .divider-symbol {
    color: var(--gold);
    font-size: 1.2rem;
    opacity: 0.7;
  }

  .section {
    margin: 40px 0;
  }

  .section-title {
    font-family: 'Cinzel Decorative', serif;
    font-size: 1.1rem;
    color: var(--gold);
    text-align: center;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    margin-bottom: 30px;
    position: relative;
  }

  .section-title::before,
  .section-title::after {
    content: '✦';
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    opacity: 0.5;
    font-size: 0.8rem;
  }

  .section-title::before { left: calc(50% - 80px); }
  .section-title::after { right: calc(50% - 80px); }

  .skills-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(140px, 1fr));
    gap: 20px;
    padding: 20px;
  }

  .skill-card {
    background: rgba(212, 175, 55, 0.03);
    border: 1px solid rgba(212, 175, 55, 0.15);
    padding: 20px 15px;
    text-align: center;
    transition: all 0.4s ease;
    position: relative;
    overflow: hidden;
  }

  .skill-card::before {
    content: '';
    position: absolute;
    top: 0;
    left: -100%;
    width: 100%;
    height: 100%;
    background: linear-gradient(90deg, transparent, rgba(212, 175, 55, 0.1), transparent);
    transition: left 0.6s ease;
  }

  .skill-card:hover::before {
    left: 100%;
  }

  .skill-card:hover {
    border-color: var(--gold);
    transform: translateY(-4px);
    box-shadow: 0 10px 30px rgba(212, 175, 55, 0.2);
  }

  .skill-icon {
    width: 48px;
    height: 48px;
    margin: 0 auto 12px;
    filter: drop-shadow(0 0 8px rgba(212, 175, 55, 0.3));
    transition: filter 0.4s ease;
  }

  .skill-card:hover .skill-icon {
    filter: drop-shadow(0 0 15px rgba(245, 214, 123, 0.6));
  }

  .skill-name {
    font-family: 'MedievalSharp', cursive;
    font-size: 0.9rem;
    color: var(--text-primary);
    letter-spacing: 0.05em;
  }

  .contribution-section {
    text-align: center;
    padding: 30px;
    background: rgba(123, 75, 179, 0.05);
    border: 1px solid rgba(123, 75, 179, 0.2);
    position: relative;
  }

  .contribution-section::before {
    content: '';
    position: absolute;
    inset: 0;
    background: radial-gradient(circle at center, rgba(123, 75, 179, 0.1), transparent 70%);
    pointer-events: none;
  }

  .contribution-graph {
    position: relative;
    z-index: 1;
    max-width: 100%;
    overflow-x: auto;
  }

  .contribution-graph img {
    max-width: 100%;
    height: auto;
    filter: drop-shadow(0 0 20px rgba(123, 75, 179, 0.3));
  }

  .stats-row {
    display: flex;
    justify-content: center;
    gap: 40px;
    flex-wrap: wrap;
    margin-top: 30px;
  }

  .stat {
    text-align: center;
    padding: 15px 25px;
    border: 1px solid rgba(212, 175, 55, 0.2);
    background: rgba(212, 175, 55, 0.03);
    min-width: 120px;
  }

  .stat-value {
    font-family: 'Cinzel Decorative', serif;
    font-size: 1.8rem;
    color: var(--gold-bright);
    font-weight: 700;
  }

  .stat-label {
    font-family: 'Cormorant Garamond', serif;
    font-size: 0.85rem;
    color: var(--text-dim);
    letter-spacing: 0.2em;
    text-transform: uppercase;
    margin-top: 5px;
  }

  .footer {
    text-align: center;
    margin-top: 50px;
    padding-top: 30px;
    border-top: 1px solid rgba(212, 175, 55, 0.15);
  }

  .footer-text {
    font-family: 'Cormorant Garamond', serif;
    font-style: italic;
    color: var(--text-dim);
    font-size: 0.95rem;
    letter-spacing: 0.1em;
  }

  @media (max-width: 600px) {
    .profile-frame { padding: 40px 20px; }
    .skills-grid { grid-template-columns: repeat(2, 1fr); gap: 12px; }
    .stats-row { gap: 20px; }
    .stat { min-width: 100px; padding: 12px 18px; }
  }
</style>
</head>
<body>

<div class="stars" id="stars"></div>

<div class="profile-frame">
  <div class="corner corner-tl"></div>
  <div class="corner corner-tr"></div>
  <div class="corner corner-bl"></div>
  <div class="corner corner-br"></div>

  <div class="header">
    <h1 class="title">Alucard</h1>
    <p class="subtitle">"Born from code, forged in the arcane"</p>
  </div>

  <div class="divider">
    <div class="divider-line"></div>
    <div class="divider-symbol">⚜</div>
    <div class="divider-line"></div>
  </div>

  <div class="section">
    <div class="section-title">Arcane Arsenal</div>
    <div class="skills-grid">
      <div class="skill-card">
        <img class="skill-icon" src="https://skillicons.dev/icons?i=ts" alt="TypeScript">
        <div class="skill-name">TypeScript</div>
      </div>
      <div class="skill-card">
        <img class="skill-icon" src="https://skillicons.dev/icons?i=nextjs" alt="Next.js">
        <div class="skill-name">Next.js</div>
      </div>
      <div class="skill-card">
        <img class="skill-icon" src="https://skillicons.dev/icons?i=tailwind" alt="Tailwind">
        <div class="skill-name">Tailwind</div>
      </div>
      <div class="skill-card">
        <img class="skill-icon" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/storybook/storybook-original.svg" alt="Storybook">
        <div class="skill-name">Storybook</div>
      </div>
      <div class="skill-card">
        <img class="skill-icon" src="https://skillicons.dev/icons?i=graphql" alt="GraphQL">
        <div class="skill-name">GraphQL</div>
      </div>
      <div class="skill-card">
        <img class="skill-icon" src="https://skillicons.dev/icons?i=go" alt="Go">
        <div class="skill-name">Go</div>
      </div>
      <div class="skill-card">
        <img class="skill-icon" src="https://skillicons.dev/icons?i=rust" alt="Rust">
        <div class="skill-name">Rust</div>
      </div>
      <div class="skill-card">
        <img class="skill-icon" src="https://skillicons.dev/icons?i=nestjs" alt="NestJS">
        <div class="skill-name">NestJS</div>
      </div>
      <div class="skill-card">
        <img class="skill-icon" src="https://skillicons.dev/icons?i=py" alt="Python">
        <div class="skill-name">Python</div>
      </div>
      <div class="skill-card">
        <img class="skill-icon" src="https://skillicons.dev/icons?i=aws" alt="AWS">
        <div class="skill-name">AWS</div>
      </div>
    </div>
  </div>

  <div class="divider">
    <div class="divider-line"></div>
    <div class="divider-symbol">☽</div>
    <div class="divider-line"></div>
  </div>

  <div class="section">
    <div class="section-title">Chronicles of Contribution</div>
    <div class="contribution-section">
      <div class="contribution-graph">
        <picture>
          <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/alucard0x1/alucard0x1/output/pacman-contribution-graph-dark.svg">
          <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/alucard0x1/alucard0x1/output/pacman-contribution-graph.svg">
          <img alt="pacman contribution graph" src="https://raw.githubusercontent.com/alucard0x1/alucard0x1/output/pacman-contribution-graph.svg">
        </picture>
      </div>
      <div class="stats-row">
        <div class="stat">
          <div class="stat-value">∞</div>
          <div class="stat-label">Quests</div>
        </div>
        <div class="stat">
          <div class="stat-value">☠</div>
          <div class="stat-label">Bugs Slain</div>
        </div>
        <div class="stat">
          <div class="stat-value">⚡</div>
          <div class="stat-label">Deployments</div>
        </div>
      </div>
    </div>
  </div>

  <div class="footer">
    <p class="footer-text">✦ Crafted with arcane energies · No frameworks were harmed ✦</p>
  </div>
</div>

<script>
  (function() {
    const container = document.getElementById('stars');
    const count = 80;
    for (let i = 0; i < count; i++) {
      const star = document.createElement('div');
      star.className = 'star';
      star.style.left = Math.random() * 100 + '%';
      star.style.top = Math.random() * 100 + '%';
      star.style.setProperty('--duration', (2 + Math.random() * 4) + 's');
      star.style.animationDelay = Math.random() * 5 + 's';
      container.appendChild(star);
    }
  })();
</script>

</body>
</html>
