<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>MamaOnTrack — Health Tracking Built by a Nurse Mom, for Every Mom</title>
<meta name="description" content="MamaOnTrack is the only app that tracks your baby AND your postpartum health in one place. Built by a nurse mom of three. Free forever. Zero ads.">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;1,300;1,400;1,600&family=DM+Sans:ital,wght@0,300;0,400;0,500;1,300&display=swap">
<style>
  :root {
    --terra:  #b5836a;
    --dark:   #1a1a1a;
    --linen:  #faf8f5;
    --white:  #ffffff;
    --border: #e8e2db;
    --muted:  #8a8480;
    --green:  #7a9e87;
    --purple: #8f8aa0;
    --blue:   #7a96a8;
    --yellow: #c9a96e;
    --sand:   #f0ebe3;
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  html { scroll-behavior: smooth; }

  body {
    font-family: 'DM Sans', sans-serif;
    background: var(--linen);
    color: var(--dark);
    overflow-x: hidden;
  }

  /* ── NAV ── */
  nav {
    position: fixed;
    top: 0; left: 0; right: 0;
    z-index: 200;
    background: rgba(26,26,26,0.96);
    backdrop-filter: blur(12px);
    border-bottom: 1px solid #2a2a2a;
    padding: 0 48px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    height: 64px;
  }

  .nav-logo {
    font-family: 'Cormorant Garamond', serif;
    font-style: italic;
    font-weight: 400;
    font-size: 26px;
    color: #f0ece4;
    text-decoration: none;
    letter-spacing: 0.01em;
  }

  .nav-links {
    display: flex;
    gap: 32px;
    align-items: center;
  }

  .nav-links a {
    font-size: 11px;
    font-weight: 400;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    color: rgba(240,236,228,0.55);
    text-decoration: none;
    transition: color 0.2s;
  }

  .nav-links a:hover { color: var(--terra); }

  .nav-cta {
    padding: 8px 22px;
    background: var(--terra);
    color: var(--white) !important;
    border-radius: 4px;
    font-size: 11px !important;
    font-weight: 500 !important;
    letter-spacing: 0.08em !important;
    text-transform: uppercase !important;
    transition: opacity 0.2s !important;
  }

  .nav-cta:hover { opacity: 0.85; }

  /* ── HERO ── */
  .hero {
    min-height: 100vh;
    background: var(--dark);
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    text-align: center;
    padding: 120px 40px 80px;
    position: relative;
    overflow: hidden;
  }

  .hero::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0; bottom: 0;
    background: radial-gradient(ellipse at 50% 60%, rgba(181,131,106,0.08) 0%, transparent 70%);
    pointer-events: none;
  }

  .hero::after {
    content: '';
    position: absolute;
    bottom: 0; left: 0; right: 0;
    height: 1px;
    background: linear-gradient(90deg, transparent, var(--terra), transparent);
    opacity: 0.4;
  }

  .hero-eyebrow {
    font-size: 10px;
    font-weight: 400;
    letter-spacing: 0.3em;
    text-transform: uppercase;
    color: var(--terra);
    margin-bottom: 28px;
    opacity: 0;
    animation: fadeUp 0.8s ease 0.2s forwards;
  }

  .hero-botanical {
    margin-bottom: 16px;
    opacity: 0;
    animation: fadeUp 0.8s ease 0.3s forwards;
  }

  .hero-title {
    font-family: 'Cormorant Garamond', serif;
    font-style: italic;
    font-weight: 400;
    font-size: clamp(52px, 9vw, 96px);
    color: #f0ece4;
    line-height: 1;
    letter-spacing: 0.01em;
    margin-bottom: 24px;
    opacity: 0;
    animation: fadeUp 0.8s ease 0.4s forwards;
  }

  .hero-divider {
    width: 40px;
    height: 0.5px;
    background: var(--terra);
    opacity: 0.5;
    margin: 0 auto 28px;
    opacity: 0;
    animation: fadeUp 0.8s ease 0.5s forwards;
  }

  .hero-sub {
    font-size: clamp(15px, 2.5vw, 18px);
    font-weight: 300;
    color: rgba(240,236,228,0.55);
    line-height: 1.8;
    max-width: 560px;
    margin: 0 auto 48px;
    opacity: 0;
    animation: fadeUp 0.8s ease 0.6s forwards;
  }

  .hero-sub em {
    color: rgba(240,236,228,0.8);
    font-style: normal;
  }

  .hero-actions {
    display: flex;
    gap: 14px;
    justify-content: center;
    flex-wrap: wrap;
    opacity: 0;
    animation: fadeUp 0.8s ease 0.7s forwards;
  }

  .btn-primary {
    padding: 14px 36px;
    background: var(--terra);
    color: var(--white);
    border: none;
    border-radius: 4px;
    font-size: 12px;
    font-weight: 500;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    cursor: pointer;
    text-decoration: none;
    transition: opacity 0.2s, transform 0.2s;
    display: inline-block;
  }

  .btn-primary:hover { opacity: 0.88; transform: translateY(-1px); }

  .btn-ghost {
    padding: 14px 36px;
    background: transparent;
    color: rgba(240,236,228,0.7);
    border: 1px solid rgba(240,236,228,0.2);
    border-radius: 4px;
    font-size: 12px;
    font-weight: 400;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    cursor: pointer;
    text-decoration: none;
    transition: all 0.2s;
    display: inline-block;
  }

  .btn-ghost:hover {
    border-color: var(--terra);
    color: var(--terra);
  }

  .hero-note {
    margin-top: 24px;
    font-size: 11px;
    color: rgba(240,236,228,0.25);
    letter-spacing: 0.1em;
    opacity: 0;
    animation: fadeUp 0.8s ease 0.9s forwards;
  }

  /* ── PROMISE STRIP ── */
  .promise-strip {
    background: var(--terra);
    padding: 18px 40px;
    display: flex;
    justify-content: center;
    gap: 48px;
    flex-wrap: wrap;
  }

  .promise-item {
    font-size: 11px;
    font-weight: 400;
    letter-spacing: 0.14em;
    text-transform: uppercase;
    color: rgba(255,255,255,0.9);
    display: flex;
    align-items: center;
    gap: 8px;
  }

  .promise-dot {
    width: 4px;
    height: 4px;
    border-radius: 50%;
    background: rgba(255,255,255,0.6);
  }

  /* ── SECTIONS ── */
  section { padding: 100px 40px; }

  .section-eyebrow {
    font-size: 10px;
    font-weight: 400;
    letter-spacing: 0.28em;
    text-transform: uppercase;
    color: var(--terra);
    margin-bottom: 16px;
    text-align: center;
  }

  .section-title {
    font-family: 'Cormorant Garamond', serif;
    font-style: italic;
    font-weight: 400;
    font-size: clamp(36px, 5vw, 56px);
    color: var(--dark);
    text-align: center;
    line-height: 1.15;
    margin-bottom: 20px;
  }

  .section-title-light {
    color: #f0ece4;
  }

  .section-sub {
    font-size: 15px;
    font-weight: 300;
    color: var(--muted);
    text-align: center;
    line-height: 1.85;
    max-width: 520px;
    margin: 0 auto 64px;
  }

  .section-sub-light {
    color: rgba(240,236,228,0.5);
  }

  .section-divider {
    width: 32px;
    height: 0.5px;
    background: var(--terra);
    opacity: 0.4;
    margin: 16px auto 20px;
  }

  /* ── FOR SECTION ── */
  .for-section {
    background: var(--linen);
  }

  .for-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 2px;
    max-width: 1100px;
    margin: 0 auto;
  }

  .for-card {
    background: var(--white);
    padding: 52px 48px;
    position: relative;
    overflow: hidden;
  }

  .for-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0;
    width: 3px;
    height: 100%;
  }

  .for-card.baby::before { background: var(--terra); }
  .for-card.mama::before { background: var(--green); }
  .for-card.family::before { background: var(--purple); }
  .for-card.ai::before { background: var(--blue); }

  .for-card-label {
    font-size: 10px;
    font-weight: 500;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    margin-bottom: 16px;
  }

  .for-card.baby .for-card-label { color: var(--terra); }
  .for-card.mama .for-card-label { color: var(--green); }
  .for-card.family .for-card-label { color: var(--purple); }
  .for-card.ai .for-card-label { color: var(--blue); }

  .for-card-title {
    font-family: 'Cormorant Garamond', serif;
    font-style: italic;
    font-weight: 400;
    font-size: 32px;
    color: var(--dark);
    margin-bottom: 24px;
    line-height: 1.2;
  }

  .for-list {
    list-style: none;
    display: flex;
    flex-direction: column;
    gap: 10px;
  }

  .for-list li {
    font-size: 13px;
    font-weight: 300;
    color: var(--muted);
    padding-left: 16px;
    position: relative;
    line-height: 1.6;
  }

  .for-list li::before {
    content: '';
    position: absolute;
    left: 0;
    top: 8px;
    width: 5px;
    height: 5px;
    border-radius: 50%;
  }

  .for-card.baby .for-list li::before { background: var(--terra); }
  .for-card.mama .for-list li::before { background: var(--green); }
  .for-card.family .for-list li::before { background: var(--purple); }
  .for-card.ai .for-list li::before { background: var(--blue); }

  /* ── FEATURES ── */
  .features-section {
    background: var(--dark);
  }

  .features-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1px;
    max-width: 1100px;
    margin: 0 auto;
    background: #2a2a2a;
  }

  .feature-card {
    background: #1a1a1a;
    padding: 40px 36px;
    transition: background 0.2s;
  }

  .feature-card:hover { background: #202020; }

  .feature-num {
    font-family: 'Cormorant Garamond', serif;
    font-style: italic;
    font-size: 40px;
    color: var(--terra);
    opacity: 0.3;
    line-height: 1;
    margin-bottom: 16px;
  }

  .feature-title {
    font-size: 13px;
    font-weight: 500;
    color: #f0ece4;
    letter-spacing: 0.04em;
    margin-bottom: 10px;
  }

  .feature-desc {
    font-size: 12px;
    font-weight: 300;
    color: rgba(240,236,228,0.4);
    line-height: 1.7;
  }

  /* ── PRICING ── */
  .pricing-section {
    background: var(--sand);
  }

  .pricing-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 16px;
    max-width: 900px;
    margin: 0 auto;
  }

  .pricing-card {
    background: var(--white);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 40px 32px;
    position: relative;
    text-align: center;
    transition: transform 0.2s, box-shadow 0.2s;
  }

  .pricing-card:hover {
    transform: translateY(-4px);
    box-shadow: 0 16px 40px rgba(0,0,0,0.08);
  }

  .pricing-card.featured {
    background: var(--dark);
    border-color: var(--terra);
    border-width: 1.5px;
  }

  .pricing-card.featured::before {
    content: 'Most Popular';
    position: absolute;
    top: -12px;
    left: 50%;
    transform: translateX(-50%);
    background: var(--terra);
    color: var(--white);
    font-size: 9px;
    font-weight: 500;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    padding: 4px 16px;
    border-radius: 20px;
    white-space: nowrap;
  }

  .pricing-plan {
    font-size: 10px;
    font-weight: 500;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--terra);
    margin-bottom: 16px;
  }

  .pricing-price {
    font-family: 'Cormorant Garamond', serif;
    font-weight: 300;
    font-size: 52px;
    color: var(--dark);
    line-height: 1;
    margin-bottom: 6px;
  }

  .pricing-card.featured .pricing-price { color: #f0ece4; }

  .pricing-period {
    font-size: 11px;
    color: var(--muted);
    margin-bottom: 28px;
  }

  .pricing-card.featured .pricing-period { color: rgba(240,236,228,0.4); }

  .pricing-divider {
    width: 24px;
    height: 0.5px;
    background: var(--border);
    margin: 0 auto 24px;
  }

  .pricing-features {
    list-style: none;
    text-align: left;
    margin-bottom: 32px;
  }

  .pricing-features li {
    font-size: 12px;
    font-weight: 300;
    color: var(--muted);
    padding: 6px 0;
    border-bottom: 1px solid var(--border);
    display: flex;
    align-items: center;
    gap: 8px;
    line-height: 1.5;
  }

  .pricing-card.featured .pricing-features li {
    color: rgba(240,236,228,0.55);
    border-bottom-color: #2a2a2a;
  }

  .pricing-features li::before {
    content: '';
    width: 5px;
    height: 5px;
    border-radius: 50%;
    background: var(--terra);
    flex-shrink: 0;
  }

  .pricing-btn {
    display: block;
    width: 100%;
    padding: 12px;
    border-radius: 4px;
    font-size: 11px;
    font-weight: 500;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    cursor: pointer;
    border: none;
    transition: opacity 0.2s;
    text-decoration: none;
    text-align: center;
  }

  .pricing-btn:hover { opacity: 0.85; }

  .pricing-btn-light {
    background: var(--linen);
    color: var(--terra);
    border: 1px solid var(--border);
  }

  .pricing-btn-dark {
    background: var(--terra);
    color: var(--white);
  }

  .pricing-no-ads {
    text-align: center;
    margin-top: 28px;
    font-size: 12px;
    color: var(--muted);
    letter-spacing: 0.06em;
  }

  /* ── STORY ── */
  .story-section {
    background: var(--dark);
    position: relative;
    overflow: hidden;
  }

  .story-section::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0; bottom: 0;
    background: radial-gradient(ellipse at 30% 50%, rgba(181,131,106,0.06) 0%, transparent 65%);
    pointer-events: none;
  }

  .story-inner {
    max-width: 680px;
    margin: 0 auto;
    text-align: center;
    position: relative;
  }

  .story-quote {
    font-family: 'Cormorant Garamond', serif;
    font-style: italic;
    font-weight: 300;
    font-size: clamp(24px, 3.5vw, 36px);
    color: #f0ece4;
    line-height: 1.6;
    margin-bottom: 36px;
  }

  .story-quote em {
    color: var(--terra);
    font-style: italic;
  }

  .story-attr {
    font-size: 11px;
    color: rgba(240,236,228,0.35);
    letter-spacing: 0.16em;
    text-transform: uppercase;
  }

  /* ── PROMISE ── */
  .promise-section {
    background: var(--linen);
  }

  .promise-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 16px;
    max-width: 1000px;
    margin: 0 auto;
  }

  .promise-card {
    background: var(--white);
    border: 1px solid var(--border);
    border-radius: 6px;
    padding: 32px 28px;
    position: relative;
  }

  .promise-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 2px;
    border-radius: 6px 6px 0 0;
  }

  .promise-card:nth-child(1)::before { background: var(--terra); }
  .promise-card:nth-child(2)::before { background: var(--green); }
  .promise-card:nth-child(3)::before { background: var(--purple); }
  .promise-card:nth-child(4)::before { background: var(--blue); }
  .promise-card:nth-child(5)::before { background: var(--yellow); }
  .promise-card:nth-child(6)::before { background: var(--terra); }

  .promise-icon {
    width: 32px;
    height: 32px;
    border-radius: 6px;
    margin-bottom: 16px;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .promise-card-title {
    font-size: 13px;
    font-weight: 500;
    color: var(--dark);
    margin-bottom: 8px;
    letter-spacing: 0.02em;
  }

  .promise-card-desc {
    font-size: 12px;
    font-weight: 300;
    color: var(--muted);
    line-height: 1.7;
  }

  /* ── DOWNLOAD ── */
  .download-section {
    background: var(--dark);
    text-align: center;
    padding: 120px 40px;
    position: relative;
    overflow: hidden;
  }

  .download-section::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 1px;
    background: linear-gradient(90deg, transparent, var(--terra), transparent);
    opacity: 0.3;
  }

  .store-buttons {
    display: flex;
    gap: 16px;
    justify-content: center;
    flex-wrap: wrap;
    margin-top: 48px;
  }

  .store-btn {
    display: flex;
    align-items: center;
    gap: 12px;
    padding: 14px 28px;
    background: rgba(240,236,228,0.06);
    border: 1px solid rgba(240,236,228,0.12);
    border-radius: 8px;
    text-decoration: none;
    transition: all 0.2s;
  }

  .store-btn:hover {
    background: rgba(240,236,228,0.1);
    border-color: var(--terra);
    transform: translateY(-2px);
  }

  .store-btn-text { text-align: left; }

  .store-btn-sub {
    font-size: 9px;
    color: rgba(240,236,228,0.4);
    letter-spacing: 0.1em;
    text-transform: uppercase;
    display: block;
  }

  .store-btn-name {
    font-size: 16px;
    font-weight: 400;
    color: #f0ece4;
    display: block;
    margin-top: 2px;
    letter-spacing: 0.02em;
  }

  .store-icon {
    font-size: 28px;
    line-height: 1;
  }

  /* ── FOOTER ── */
  footer {
    background: #111111;
    padding: 60px 48px 40px;
    border-top: 1px solid #1e1e1e;
  }

  .footer-top {
    display: flex;
    justify-content: space-between;
    align-items: flex-start;
    flex-wrap: wrap;
    gap: 40px;
    margin-bottom: 48px;
    padding-bottom: 48px;
    border-bottom: 1px solid #1e1e1e;
  }

  .footer-brand .footer-logo {
    font-family: 'Cormorant Garamond', serif;
    font-style: italic;
    font-weight: 400;
    font-size: 32px;
    color: #f0ece4;
    display: block;
    margin-bottom: 8px;
    text-decoration: none;
  }

  .footer-brand p {
    font-size: 11px;
    color: rgba(240,236,228,0.3);
    letter-spacing: 0.1em;
    text-transform: uppercase;
    max-width: 220px;
    line-height: 1.7;
  }

  .footer-col h4 {
    font-size: 10px;
    font-weight: 500;
    letter-spacing: 0.18em;
    text-transform: uppercase;
    color: var(--terra);
    margin-bottom: 16px;
  }

  .footer-col a {
    display: block;
    font-size: 12px;
    font-weight: 300;
    color: rgba(240,236,228,0.4);
    text-decoration: none;
    margin-bottom: 10px;
    transition: color 0.2s;
    letter-spacing: 0.02em;
  }

  .footer-col a:hover { color: var(--terra); }

  .footer-bottom {
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-wrap: wrap;
    gap: 16px;
  }

  .footer-copy {
    font-size: 11px;
    color: rgba(240,236,228,0.2);
    letter-spacing: 0.06em;
  }

  .footer-social {
    display: flex;
    gap: 20px;
  }

  .footer-social a {
    font-size: 11px;
    color: rgba(240,236,228,0.3);
    text-decoration: none;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    transition: color 0.2s;
  }

  .footer-social a:hover { color: var(--terra); }

  /* ── ANIMATIONS ── */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(20px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  .fade-up {
    opacity: 0;
    transform: translateY(24px);
    transition: opacity 0.7s ease, transform 0.7s ease;
  }

  .fade-up.visible {
    opacity: 1;
    transform: translateY(0);
  }

  /* ── MOBILE ── */
  @media (max-width: 768px) {
    nav { padding: 0 20px; }
    .nav-links { display: none; }
    section { padding: 72px 24px; }
    .for-grid { grid-template-columns: 1fr; }
    .features-grid { grid-template-columns: 1fr; }
    .pricing-grid { grid-template-columns: 1fr; max-width: 380px; }
    .promise-grid { grid-template-columns: 1fr 1fr; }
    footer { padding: 48px 24px 32px; }
    .footer-top { flex-direction: column; }
    .footer-bottom { flex-direction: column; align-items: flex-start; }
    .hero { padding: 100px 24px 72px; }
    .store-buttons { flex-direction: column; align-items: center; }
  }

  @media (max-width: 480px) {
    .promise-grid { grid-template-columns: 1fr; }
  }
</style>
</head>
<body>

<!-- ── NAV ── -->
<nav>
  <a href="#" class="nav-logo">MamaOnTrack</a>
  <div class="nav-links">
    <a href="#features">Features</a>
    <a href="#pricing">Pricing</a>
    <a href="#promise">Privacy</a>
    <a href="#download">Download</a>
    <a href="#download" class="nav-cta">Get the App</a>
  </div>
</nav>

<!-- ── HERO ── -->
<section class="hero" id="home">
  <div class="hero-eyebrow">Now Available — Free Forever</div>
  <div class="hero-botanical">
    <svg width="36" height="38" viewBox="0 0 36 38" fill="none">
      <line x1="18" y1="36" x2="18" y2="9" stroke="#b5836a" stroke-width="0.8" opacity="0.6"/>
      <path d="M18 28 C8 21 4 10 11 3 C14 12 17 22 18 28" fill="#7a9e87" opacity="0.5"/>
      <path d="M18 28 C28 21 32 10 25 3 C22 12 19 22 18 28" fill="#7a9e87" opacity="0.35"/>
      <circle cx="18" cy="8" r="2.4" fill="#b5836a" opacity="0.6"/>
    </svg>
  </div>
  <h1 class="hero-title">MamaOnTrack</h1>
  <div class="hero-divider"></div>
  <p class="hero-sub">
    The only app that tracks <em>your children's health</em> and <em>your own</em> — all in one place.
    Built by a nurse mom of three. Free forever. Zero ads.
  </p>
  <div class="hero-actions">
    <a href="#download" class="btn-primary">Download Free</a>
    <a href="#features" class="btn-ghost">See Features</a>
  </div>
  <p class="hero-note">Free forever &nbsp;&middot;&nbsp; No credit card required &nbsp;&middot;&nbsp; Zero ads on any plan</p>
</section>

<!-- ── PROMISE STRIP ── -->
<div class="promise-strip">
  <div class="promise-item"><div class="promise-dot"></div> Free Forever</div>
  <div class="promise-item"><div class="promise-dot"></div> Zero Ads — Ever</div>
  <div class="promise-item"><div class="promise-dot"></div> Built by a Nurse Mom</div>
  <div class="promise-item"><div class="promise-dot"></div> All Ages — Newborn to Teen</div>
  <div class="promise-item"><div class="promise-dot"></div> Your Data Is Never Sold</div>
</div>

<!-- ── FOR SECTION ── -->
<section class="for-section" id="features">
  <div class="section-eyebrow fade-up">Everything in one app</div>
  <div class="section-divider fade-up"></div>
  <h2 class="section-title fade-up">One app. Your whole family.</h2>
  <p class="section-sub fade-up">Whether your child is 3 weeks old or 13 years old — you need one place to track it all. MamaOnTrack covers every stage, every age, and every member of your family.</p>

  <div class="for-grid">
    <div class="for-card baby fade-up">
      <div class="for-card-label">For Your Kids</div>
      <div class="for-card-title">Every age.<br>Every stage.</div>
      <ul class="for-list">
        <li>Symptom log with severity tracking</li>
        <li>Full AAP 2026 vaccination schedule</li>
        <li>CDC developmental milestone tracker</li>
        <li>Growth tracking — height, weight, head circumference</li>
        <li>Doctor visit log with AI document scanner</li>
        <li>Allergy tracker with EpiPen action plans</li>
        <li>Infant feeding and diaper log</li>
        <li>Medications and active prescription tracking</li>
        <li>Vitals and lab results log</li>
        <li>Firsts journal — first smile, first steps, first word</li>
      </ul>
    </div>

    <div class="for-card mama fade-up">
      <div class="for-card-label">For Mama</div>
      <div class="for-card-title">Your health<br>matters too.</div>
      <ul class="for-list">
        <li>Breastfeeding timer with side tracking</li>
        <li>Pumping tracker with smart milk inventory</li>
        <li>Hydration tracker — 13 cup daily goal</li>
        <li>Postpartum mood, sleep, and pain log</li>
        <li>PPD and PPA guide with resources</li>
        <li>Cycle tracker — postpartum cycles are unpredictable</li>
        <li>My Visits — OB, midwife, therapist appointments</li>
        <li>Vitals, labs, and medication tracking</li>
        <li>Nutrition log and wellness trends</li>
        <li>Mom community resources — find your village</li>
      </ul>
    </div>

    <div class="for-card family fade-up">
      <div class="for-card-label">For Your Family</div>
      <div class="for-card-title">Everyone<br>on the same page.</div>
      <ul class="for-list">
        <li>Shared family calendar — color coded by person</li>
        <li>Role-based caregiver access</li>
        <li>Admin, Co-Parent, Caregiver, and View Only roles</li>
        <li>Real-time sync across all devices</li>
        <li>Share with partner, grandparents, nanny</li>
        <li>Per-person schedules on each dashboard</li>
        <li>Coming Up Next — everyone's appointments at a glance</li>
        <li>Daily motivational note — changes every day</li>
      </ul>
    </div>

    <div class="for-card ai fade-up">
      <div class="for-card-label">AI Features — Premium</div>
      <div class="for-card-title">Smarter tracking<br>for tired moms.</div>
      <ul class="for-list">
        <li>AI Sleep Planner — personalized schedules based on AAP guidelines and your logged data</li>
        <li>AI Visit Scanner — photograph your after-visit summary and it fills in automatically</li>
        <li>Trends and Insights — spot patterns in symptoms, sleep, mood, and hydration</li>
        <li>Health Reports — PDF exports for any doctor visit</li>
        <li>Smart Reminders — medications, vaccines, appointments, and more</li>
        <li>Four evidence-based sleep training methods</li>
      </ul>
    </div>
  </div>
</section>

<!-- ── FEATURES GRID ── -->
<section class="features-section">
  <div class="section-eyebrow" style="color:var(--terra);" class="fade-up">Why MamaOnTrack</div>
  <div class="section-divider fade-up"></div>
  <h2 class="section-title section-title-light fade-up">Built different.<br>On purpose.</h2>
  <p class="section-sub section-sub-light fade-up">Most baby apps forget the mother exists. Most maternal health apps forget you have children. We built the one that remembers both.</p>

  <div class="features-grid">
    <div class="feature-card fade-up">
      <div class="feature-num">01</div>
      <div class="feature-title">All Ages — Newborn to Teen</div>
      <div class="feature-desc">Not just for new moms. Track vaccine records for your 9-year-old, symptoms for your toddler, and milestones for your baby — all in the same app.</div>
    </div>
    <div class="feature-card fade-up">
      <div class="feature-num">02</div>
      <div class="feature-title">Free Forever. No Exceptions.</div>
      <div class="feature-desc">The free plan is free forever — not a trial. One child, core tracking, and zero ads. No credit card required, no automatic conversion.</div>
    </div>
    <div class="feature-card fade-up">
      <div class="feature-num">03</div>
      <div class="feature-title">Zero Ads on Every Plan</div>
      <div class="feature-desc">Your baby's health data is not an advertising opportunity. MamaOnTrack is 100% ad-free on free, monthly, and lifetime plans. Always.</div>
    </div>
    <div class="feature-card fade-up">
      <div class="feature-num">04</div>
      <div class="feature-title">Built by a Nurse Mom</div>
      <div class="feature-desc">Not a tech startup guessing what moms need. Every feature was designed around a real clinical and parenting moment by someone who has lived it.</div>
    </div>
    <div class="feature-card fade-up">
      <div class="feature-num">05</div>
      <div class="feature-title">Replace Four Apps with One</div>
      <div class="feature-desc">Baby tracker, family calendar, postpartum health, and breastfeeding app — all replaced by MamaOnTrack. One login, one place, everything connected.</div>
    </div>
    <div class="feature-card fade-up">
      <div class="feature-num">06</div>
      <div class="feature-title">Your Data Stays Yours</div>
      <div class="feature-desc">Never sold, never shared with insurers or employers, never used to train AI. Encrypted in transit and at rest. Delete everything anytime.</div>
    </div>
  </div>
</section>

<!-- ── PRICING ── -->
<section class="pricing-section" id="pricing">
  <div class="section-eyebrow fade-up">Simple, honest pricing</div>
  <div class="section-divider fade-up"></div>
  <h2 class="section-title fade-up">Free forever.<br>Upgrade when you're ready.</h2>
  <p class="section-sub fade-up">No pressure, no tricks, no ads on any plan. The free plan is genuinely free — forever.</p>

  <div class="pricing-grid">
    <div class="pricing-card fade-up">
      <div class="pricing-plan">Free</div>
      <div class="pricing-price">$0</div>
      <div class="pricing-period">Forever — no credit card needed</div>
      <div class="pricing-divider"></div>
      <ul class="pricing-features">
        <li>1 child profile</li>
        <li>Core health tracking</li>
        <li>Family calendar</li>
        <li>Mama health tabs</li>
        <li>Nurse tips and daily note</li>
        <li>Zero ads — always</li>
      </ul>
      <a href="#download" class="pricing-btn pricing-btn-light">Get Started Free</a>
    </div>

    <div class="pricing-card featured fade-up">
      <div class="pricing-plan">Premium</div>
      <div class="pricing-price" style="color:#f0ece4;">$6.99</div>
      <div class="pricing-period">per month — cancel anytime</div>
      <div class="pricing-divider" style="background:#2a2a2a;"></div>
      <ul class="pricing-features">
        <li>Unlimited children</li>
        <li>AI Sleep Planner</li>
        <li>AI Visit Scanner</li>
        <li>Family sharing — up to 5 caregivers</li>
        <li>Health reports and PDF export</li>
        <li>Smart reminders and notifications</li>
        <li>Trends and insights</li>
        <li>Unlimited health history</li>
      </ul>
      <a href="#download" class="pricing-btn pricing-btn-dark">Start Premium</a>
    </div>

    <div class="pricing-card fade-up">
      <div class="pricing-plan">Lifetime</div>
      <div class="pricing-price">$49.99</div>
      <div class="pricing-period">one time — all future updates included</div>
      <div class="pricing-divider"></div>
      <ul class="pricing-features">
        <li>Everything in Premium</li>
        <li>Pay once, use forever</li>
        <li>All future updates included</li>
        <li>Unlimited caregiver sharing</li>
        <li>Priority support</li>
        <li>Best value for growing families</li>
      </ul>
      <a href="#download" class="pricing-btn pricing-btn-light">Get Lifetime Access</a>
    </div>
  </div>

  <p class="pricing-no-ads">Zero ads on every plan &nbsp;&middot;&nbsp; Your data is never sold &nbsp;&middot;&nbsp; Cancel anytime</p>
</section>

<!-- ── STORY ── -->
<section class="story-section">
  <div class="story-inner fade-up">
    <div class="section-eyebrow" style="color:var(--terra); margin-bottom:32px;">Our Story</div>
    <div class="story-quote">
      "I looked for an app that tracked my baby's health, my postpartum recovery, our family calendar, and my own wellbeing — <em>all in one place.</em> It didn't exist. So I built it."
    </div>
    <div class="story-attr">Alexis &nbsp;&middot;&nbsp; Nurse &amp; Mom of Three &nbsp;&middot;&nbsp; Founder, MamaOnTrack</div>
  </div>
</section>

<!-- ── PROMISE ── -->
<section class="promise-section" id="promise">
  <div class="section-eyebrow fade-up">Our Commitment</div>
  <div class="section-divider fade-up"></div>
  <h2 class="section-title fade-up">Privacy you can<br>actually trust.</h2>
  <p class="section-sub fade-up">Your family's health data is among the most personal information that exists. We treat it that way.</p>

  <div class="promise-grid">
    <div class="promise-card fade-up">
      <div class="promise-icon" style="background:#b5836a14;">
        <svg width="16" height="16" viewBox="0 0 16 16" fill="none">
          <path d="M8 1L2 4v4c0 3.5 2.5 6.5 6 7.5C12 14.5 14 11.5 14 8V4L8 1z" stroke="#b5836a" stroke-width="1" fill="none"/>
          <path d="M5 8l2 2 4-4" stroke="#b5836a" stroke-width="1" stroke-linecap="round"/>
        </svg>
      </div>
      <div class="promise-card-title">Your data is never sold</div>
      <div class="promise-card-desc">Your health data, your children's records, and your personal information will never be sold to any third party — not advertisers, not data brokers, not anyone.</div>
    </div>
    <div class="promise-card fade-up">
      <div class="promise-icon" style="background:#7a9e8714;">
        <svg width="16" height="16" viewBox="0 0 16 16" fill="none">
          <circle cx="8" cy="8" r="6" stroke="#7a9e87" stroke-width="1" fill="none"/>
          <path d="M5 8l2 2 4-4" stroke="#7a9e87" stroke-width="1" stroke-linecap="round"/>
        </svg>
      </div>
      <div class="promise-card-title">Zero ads on every plan</div>
      <div class="promise-card-desc">MamaOnTrack is 100% ad-free on every plan. We do not use ad networks, ad SDKs, or behavioral targeting of any kind. Revenue comes from subscriptions only.</div>
    </div>
    <div class="promise-card fade-up">
      <div class="promise-icon" style="background:#8f8aa014;">
        <svg width="16" height="16" viewBox="0 0 16 16" fill="none">
          <rect x="3" y="6" width="10" height="8" rx="1.5" stroke="#8f8aa0" stroke-width="1" fill="none"/>
          <path d="M5 6V4.5a3 3 0 016 0V6" stroke="#8f8aa0" stroke-width="1" fill="none"/>
        </svg>
      </div>
      <div class="promise-card-title">Encrypted and secure</div>
      <div class="promise-card-desc">All data is encrypted in transit using TLS and at rest using AES-256. Your health records are protected using the same standards as banking.</div>
    </div>
    <div class="promise-card fade-up">
      <div class="promise-icon" style="background:#7a96a814;">
        <svg width="16" height="16" viewBox="0 0 16 16" fill="none">
          <circle cx="8" cy="6" r="3" stroke="#7a96a8" stroke-width="1" fill="none"/>
          <path d="M2 14c0-3.3 2.7-6 6-6s6 2.7 6 6" stroke="#7a96a8" stroke-width="1" fill="none" stroke-linecap="round"/>
        </svg>
      </div>
      <div class="promise-card-title">You own your data</div>
      <div class="promise-card-desc">Export your complete health records at any time. Delete your account and all data permanently, instantly, and irreversibly — whenever you choose.</div>
    </div>
    <div class="promise-card fade-up">
      <div class="promise-icon" style="background:#c9a96e14;">
        <svg width="16" height="16" viewBox="0 0 16 16" fill="none">
          <path d="M8 2L3 5v4c0 3 2 5 5 6 3-1 5-3 5-6V5L8 2z" stroke="#c9a96e" stroke-width="1" fill="none"/>
        </svg>
      </div>
      <div class="promise-card-title">No AI training on your data</div>
      <div class="promise-card-desc">Your personal entries and health records are never used to train artificial intelligence models — ours or anyone else's.</div>
    </div>
    <div class="promise-card fade-up">
      <div class="promise-icon" style="background:#b5836a14;">
        <svg width="16" height="16" viewBox="0 0 16 16" fill="none">
          <path d="M4 8h8M8 4l4 4-4 4" stroke="#b5836a" stroke-width="1" stroke-linecap="round" stroke-linejoin="round"/>
        </svg>
      </div>
      <div class="promise-card-title">Full transparency</div>
      <div class="promise-card-desc">Our complete Privacy Policy, Terms of Service, and HIPAA Notice are publicly available. No hidden practices, no buried terms.</div>
    </div>
  </div>
</section>

<!-- ── DOWNLOAD ── -->
<section class="download-section" id="download">
  <div class="section-eyebrow fade-up" style="color:var(--terra);">Available Now</div>
  <div class="section-divider fade-up"></div>
  <h2 class="section-title section-title-light fade-up">Start tracking today.<br>It's free.</h2>
  <p class="section-sub section-sub-light fade-up">Download MamaOnTrack and finally have one place for everything that matters — your kids, your health, your family.</p>

  <div class="store-buttons fade-up">
    <a href="#" class="store-btn">
      <div class="store-icon">&#xF8FF;</div>
      <div class="store-btn-text">
        <span class="store-btn-sub">Download on the</span>
        <span class="store-btn-name">App Store</span>
      </div>
    </a>
    <a href="#" class="store-btn">
      <div class="store-icon">&#9654;</div>
      <div class="store-btn-text">
        <span class="store-btn-sub">Get it on</span>
        <span class="store-btn-name">Google Play</span>
      </div>
    </a>
  </div>

  <p style="font-size:11px;color:rgba(240,236,228,0.2);margin-top:28px;letter-spacing:0.1em;">Free forever &nbsp;&middot;&nbsp; No credit card &nbsp;&middot;&nbsp; Zero ads</p>
</section>

<!-- ── FOOTER ── -->
<footer>
  <div class="footer-top">
    <div class="footer-brand">
      <a href="#" class="footer-logo">MamaOnTrack</a>
      <p>Built by a nurse mom,<br>for every mom.</p>
    </div>
    <div class="footer-col">
      <h4>Product</h4>
      <a href="#features">Features</a>
      <a href="#pricing">Pricing</a>
      <a href="#download">Download</a>
      <a href="#promise">Privacy</a>
    </div>
    <div class="footer-col">
      <h4>Legal</h4>
      <a href="https://ablink1017-cyber.github.io/mamaontrack-legal" target="_blank">Privacy Policy</a>
      <a href="https://ablink1017-cyber.github.io/mamaontrack-legal" target="_blank">Terms of Service</a>
      <a href="https://ablink1017-cyber.github.io/mamaontrack-legal" target="_blank">HIPAA Notice</a>
      <a href="https://ablink1017-cyber.github.io/mamaontrack-legal" target="_blank">Cookie Policy</a>
    </div>
    <div class="footer-col">
      <h4>Contact</h4>
      <a href="mailto:support@mamaontrack.com">support@mamaontrack.com</a>
      <a href="mailto:privacy@mamaontrack.com">privacy@mamaontrack.com</a>
      <a href="mailto:press@mamaontrack.com">press@mamaontrack.com</a>
      <a href="mailto:hello@mamaontrack.com">hello@mamaontrack.com</a>
    </div>
  </div>
  <div class="footer-bottom">
    <div class="footer-copy">&copy; 2026 MamaOnTrack. All rights reserved. &nbsp;&middot;&nbsp; Always ad-free.</div>
    <div class="footer-social">
      <a href="https://instagram.com/MAMA_ON_TRACK" target="_blank">Instagram</a>
      <a href="https://facebook.com/MamaOnTrackApp" target="_blank">Facebook</a>
    </div>
  </div>
</footer>

<script>
  // Intersection Observer for fade-up animations
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(el => {
      if (el.isIntersecting) {
        el.target.classList.add('visible');
      }
    });
  }, { threshold: 0.1, rootMargin: '0px 0px -40px 0px' });

  document.querySelectorAll('.fade-up').forEach(el => observer.observe(el));

  // Smooth nav highlight
  const sections = document.querySelectorAll('section[id]');
  const navLinks = document.querySelectorAll('.nav-links a');

  window.addEventListener('scroll', () => {
    let current = '';
    sections.forEach(s => {
      if (window.scrollY >= s.offsetTop - 100) current = s.id;
    });
    navLinks.forEach(a => {
      a.style.color = a.getAttribute('href') === '#' + current
        ? 'var(--terra)'
        : 'rgba(240,236,228,0.55)';
    });
  });
</script>

</body>
</html>
