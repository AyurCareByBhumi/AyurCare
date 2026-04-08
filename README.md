<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>AyurCare — Pure Ayurveda, Pure Care | Dr. Bhumika Kirote</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Cinzel:wght@400;600;700;900&family=Cormorant+Garamond:ital,wght@0,300;0,400;0,500;0,600;1,300;1,400&family=Lato:wght@300;400;700&display=swap" rel="stylesheet">
<style>
  :root {
    --gold: #c9a84c;
    --gold-light: #e8c96b;
    --gold-dark: #9b7a2e;
    --forest: #1a3a28;
    --forest-mid: #254d37;
    --forest-light: #3a6b4f;
    --cream: #f9f3e8;
    --cream-dark: #ede4d0;
    --parchment: #f5edd8;
    --brown: #5c3d1e;
    --text-dark: #1e1a14;
    --text-mid: #4a3f30;
    --white: #fff;
    --shadow: 0 8px 40px rgba(26,58,40,0.13);
    --shadow-gold: 0 4px 24px rgba(201,168,76,0.18);
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  html { scroll-behavior: smooth; font-size: 16px; }

  body {
    font-family: 'Lato', sans-serif;
    background: var(--cream);
    color: var(--text-dark);
    overflow-x: hidden;
  }

  /* ── ANNOUNCEMENT BAR ── */
  .announce-bar {
    background: var(--forest);
    color: var(--gold-light);
    font-family: 'Cormorant Garamond', serif;
    font-size: 0.92rem;
    letter-spacing: 0.08em;
    padding: 7px 0;
    overflow: hidden;
    white-space: nowrap;
  }
  .announce-inner {
    display: inline-block;
    animation: marquee 28s linear infinite;
  }
  .announce-inner span { margin: 0 3rem; }
  @keyframes marquee {
    0% { transform: translateX(100vw); }
    100% { transform: translateX(-100%); }
  }

  /* ── NAVBAR ── */
  .navbar {
    position: fixed;
    top: 0; left: 0; right: 0;
    z-index: 1000;
    padding: 14px 24px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    transition: background 0.35s, box-shadow 0.35s, padding 0.35s;
  }
  .navbar.scrolled {
    background: rgba(26,58,40,0.97);
    box-shadow: 0 2px 24px rgba(0,0,0,0.25);
    padding: 10px 24px;
    backdrop-filter: blur(10px);
  }
  .nav-logo {
    display: flex; align-items: center; gap: 10px;
    text-decoration: none;
  }
  .nav-logo-icon {
    width: 42px; height: 42px;
    background: linear-gradient(135deg, var(--gold), var(--gold-dark));
    border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    font-size: 1.3rem;
    box-shadow: 0 2px 12px rgba(201,168,76,0.35);
    flex-shrink: 0;
  }
  .nav-logo-text { line-height: 1.1; }
  .nav-logo-text .brand { font-family: 'Cinzel', serif; font-size: 1.15rem; color: var(--gold-light); font-weight: 700; letter-spacing: 0.06em; }
  .nav-logo-text .tagline { font-family: 'Cormorant Garamond', serif; font-size: 0.75rem; color: rgba(232,201,107,0.7); letter-spacing: 0.12em; font-style: italic; }

  .nav-right { display: flex; align-items: center; gap: 14px; }
  .nav-cta {
    background: linear-gradient(135deg, var(--gold), var(--gold-dark));
    color: var(--forest);
    font-family: 'Cinzel', serif;
    font-size: 0.75rem;
    font-weight: 700;
    letter-spacing: 0.08em;
    padding: 8px 18px;
    border-radius: 100px;
    text-decoration: none;
    white-space: nowrap;
    box-shadow: var(--shadow-gold);
    transition: transform 0.2s, box-shadow 0.2s;
    display: none;
  }
  @media(min-width:600px){ .nav-cta { display: inline-block; } }
  .nav-cta:hover { transform: translateY(-1px); box-shadow: 0 6px 24px rgba(201,168,76,0.4); }

  .hamburger {
    background: none; border: none; cursor: pointer;
    width: 36px; height: 36px;
    display: flex; flex-direction: column;
    justify-content: center; gap: 5px;
    padding: 4px;
  }
  .hamburger span {
    display: block; height: 2px; border-radius: 2px;
    background: var(--gold-light);
    transition: all 0.3s;
  }
  .hamburger.open span:nth-child(1) { transform: translateY(7px) rotate(45deg); }
  .hamburger.open span:nth-child(2) { opacity: 0; }
  .hamburger.open span:nth-child(3) { transform: translateY(-7px) rotate(-45deg); }

  /* ── SIDE DRAWER ── */
  .drawer-overlay {
    position: fixed; inset: 0; z-index: 1100;
    background: rgba(10,24,17,0.65);
    backdrop-filter: blur(3px);
    opacity: 0; pointer-events: none;
    transition: opacity 0.35s;
  }
  .drawer-overlay.open { opacity: 1; pointer-events: all; }

  .drawer {
    position: fixed;
    top: 0; right: 0;
    width: min(320px, 88vw); height: 100vh;
    background: var(--forest);
    z-index: 1200;
    transform: translateX(105%);
    transition: transform 0.38s cubic-bezier(.4,0,.2,1);
    display: flex; flex-direction: column;
    overflow-y: auto;
    border-left: 1px solid rgba(201,168,76,0.2);
  }
  .drawer.open { transform: translateX(0); }

  .drawer-header {
    padding: 22px 22px 16px;
    border-bottom: 1px solid rgba(201,168,76,0.15);
    display: flex; align-items: center; justify-content: space-between;
    background: linear-gradient(180deg, rgba(201,168,76,0.08) 0%, transparent 100%);
  }
  .drawer-title { font-family: 'Cinzel', serif; color: var(--gold-light); font-size: 1.05rem; letter-spacing: 0.1em; }
  .drawer-close {
    background: none; border: none; cursor: pointer;
    color: var(--gold-light); font-size: 1.5rem; line-height: 1;
    width: 32px; height: 32px; display: flex; align-items: center; justify-content: center;
    border-radius: 50%;
    transition: background 0.2s;
  }
  .drawer-close:hover { background: rgba(201,168,76,0.12); }

  .drawer-nav { padding: 10px 0; flex: 1; }
  .drawer-link {
    display: flex; align-items: center; gap: 12px;
    padding: 13px 22px;
    color: rgba(249,243,232,0.85);
    font-family: 'Cormorant Garamond', serif;
    font-size: 1.08rem;
    letter-spacing: 0.04em;
    text-decoration: none;
    border-left: 3px solid transparent;
    transition: all 0.22s;
  }
  .drawer-link:hover, .drawer-link.active {
    background: rgba(201,168,76,0.08);
    border-left-color: var(--gold);
    color: var(--gold-light);
  }
  .drawer-link .icon { font-size: 1.1rem; width: 22px; text-align: center; }

  .drawer-products-toggle {
    display: flex; align-items: center; justify-content: space-between;
    padding: 13px 22px;
    color: rgba(249,243,232,0.85);
    font-family: 'Cormorant Garamond', serif;
    font-size: 1.08rem;
    letter-spacing: 0.04em;
    cursor: pointer;
    border-left: 3px solid transparent;
    transition: all 0.22s;
    user-select: none;
  }
  .drawer-products-toggle:hover { background: rgba(201,168,76,0.08); border-left-color: var(--gold); color: var(--gold-light); }
  .drawer-products-toggle .left { display: flex; align-items: center; gap: 12px; }
  .drawer-chevron { transition: transform 0.3s; font-size: 0.85rem; color: var(--gold); }
  .drawer-chevron.open { transform: rotate(180deg); }

  .drawer-sub {
    max-height: 0; overflow: hidden;
    transition: max-height 0.38s cubic-bezier(.4,0,.2,1);
    background: rgba(0,0,0,0.15);
  }
  .drawer-sub.open { max-height: 400px; }
  .drawer-sub-link {
    display: flex; align-items: center; gap: 10px;
    padding: 10px 22px 10px 50px;
    color: rgba(232,201,107,0.75);
    font-family: 'Cormorant Garamond', serif;
    font-size: 0.97rem;
    text-decoration: none;
    transition: color 0.2s;
  }
  .drawer-sub-link:hover { color: var(--gold-light); }
  .drawer-sub-link::before { content: '✦'; font-size: 0.5rem; }

  .drawer-footer {
    padding: 18px 22px;
    border-top: 1px solid rgba(201,168,76,0.15);
    display: flex; gap: 12px;
  }
  .drawer-social {
    flex: 1; padding: 10px; border-radius: 10px;
    display: flex; align-items: center; justify-content: center; gap: 8px;
    font-family: 'Cinzel', serif; font-size: 0.72rem; font-weight: 700;
    letter-spacing: 0.06em; text-decoration: none;
    transition: transform 0.2s, opacity 0.2s;
  }
  .drawer-social:hover { transform: translateY(-2px); opacity: 0.9; }
  .drawer-social.wa { background: #25D366; color: #fff; }
  .drawer-social.ig { background: linear-gradient(135deg,#f09433,#e6683c,#dc2743,#cc2366,#bc1888); color: #fff; }

  /* ── HERO ── */
  .hero {
    min-height: 100vh;
    background: linear-gradient(160deg, var(--forest) 0%, #0e2318 55%, #162d20 100%);
    display: flex; flex-direction: column;
    align-items: center; justify-content: center;
    text-align: center;
    padding: 120px 24px 80px;
    position: relative;
    overflow: hidden;
  }
  .hero-bg-pattern {
    position: absolute; inset: 0;
    background-image:
      radial-gradient(circle at 20% 30%, rgba(201,168,76,0.07) 0%, transparent 50%),
      radial-gradient(circle at 80% 70%, rgba(201,168,76,0.06) 0%, transparent 50%);
    pointer-events: none;
  }
  .hero-ornament {
    position: absolute;
    border-radius: 50%;
    border: 1px solid rgba(201,168,76,0.12);
    animation: pulse-ring 4s ease-in-out infinite;
  }
  .hero-ornament:nth-child(1) { width: 320px; height: 320px; animation-delay: 0s; }
  .hero-ornament:nth-child(2) { width: 520px; height: 520px; animation-delay: 1s; }
  .hero-ornament:nth-child(3) { width: 720px; height: 720px; animation-delay: 2s; }
  @keyframes pulse-ring {
    0%,100% { opacity: 0.4; transform: scale(1); }
    50% { opacity: 0.12; transform: scale(1.04); }
  }

  .hero-badge {
    display: inline-flex; align-items: center; gap: 8px;
    background: rgba(201,168,76,0.12);
    border: 1px solid rgba(201,168,76,0.3);
    border-radius: 100px;
    padding: 6px 18px;
    font-family: 'Cormorant Garamond', serif;
    font-size: 0.88rem;
    color: var(--gold-light);
    letter-spacing: 0.14em;
    margin-bottom: 22px;
    animation: fadeUp 0.8s ease both;
  }
  .hero-badge::before, .hero-badge::after { content: '✦'; font-size: 0.55rem; }

  .hero-eyebrow {
    font-family: 'Cormorant Garamond', serif;
    font-size: clamp(0.9rem, 2.5vw, 1.1rem);
    color: var(--gold);
    letter-spacing: 0.22em;
    text-transform: uppercase;
    margin-bottom: 12px;
    animation: fadeUp 0.9s 0.1s ease both;
  }

  .hero-title {
    font-family: 'Cinzel', serif;
    font-size: clamp(2.4rem, 8vw, 5rem);
    font-weight: 900;
    color: var(--cream);
    line-height: 1.08;
    letter-spacing: -0.01em;
    margin-bottom: 14px;
    animation: fadeUp 1s 0.2s ease both;
  }
  .hero-title .gold { color: var(--gold-light); }

  .hero-subtitle {
    font-family: 'Cormorant Garamond', serif;
    font-size: clamp(1.1rem, 3vw, 1.5rem);
    color: rgba(249,243,232,0.7);
    font-style: italic;
    margin-bottom: 36px;
    animation: fadeUp 1s 0.3s ease both;
    max-width: 500px;
    line-height: 1.6;
  }

  .hero-btns {
    display: flex; flex-wrap: wrap; gap: 14px; justify-content: center;
    animation: fadeUp 1s 0.45s ease both;
  }
  .btn-primary {
    background: linear-gradient(135deg, var(--gold-light), var(--gold-dark));
    color: var(--forest);
    font-family: 'Cinzel', serif; font-weight: 700;
    font-size: 0.82rem; letter-spacing: 0.1em;
    padding: 14px 32px; border-radius: 100px;
    text-decoration: none; border: none; cursor: pointer;
    box-shadow: 0 6px 28px rgba(201,168,76,0.35);
    transition: transform 0.22s, box-shadow 0.22s;
    white-space: nowrap;
  }
  .btn-primary:hover { transform: translateY(-2px); box-shadow: 0 10px 36px rgba(201,168,76,0.45); }

  .btn-outline {
    background: transparent;
    color: var(--gold-light);
    font-family: 'Cinzel', serif; font-weight: 600;
    font-size: 0.82rem; letter-spacing: 0.1em;
    padding: 13px 28px; border-radius: 100px;
    text-decoration: none; cursor: pointer;
    border: 1.5px solid rgba(201,168,76,0.5);
    transition: all 0.22s;
    white-space: nowrap;
  }
  .btn-outline:hover { background: rgba(201,168,76,0.1); border-color: var(--gold); }

  .hero-scroll {
    position: absolute; bottom: 30px; left: 50%; transform: translateX(-50%);
    display: flex; flex-direction: column; align-items: center; gap: 6px;
    animation: fadeUp 1s 0.7s ease both;
  }
  .hero-scroll span { font-size: 0.7rem; color: rgba(232,201,107,0.5); letter-spacing: 0.18em; font-family: 'Cinzel', serif; }
  .scroll-dot {
    width: 1px; height: 40px;
    background: linear-gradient(to bottom, var(--gold), transparent);
    animation: scroll-bounce 2s ease-in-out infinite;
  }
  @keyframes scroll-bounce {
    0%,100% { transform: scaleY(1); opacity: 0.6; }
    50% { transform: scaleY(1.3); opacity: 1; }
  }

  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(28px); }
    to { opacity: 1; transform: translateY(0); }
  }

  /* ── STATS STRIP ── */
  .stats-strip {
    background: linear-gradient(90deg, var(--forest-mid), var(--forest), var(--forest-mid));
    padding: 22px 24px;
    display: flex; flex-wrap: wrap;
    align-items: center; justify-content: center;
    gap: 0;
    border-top: 1px solid rgba(201,168,76,0.2);
    border-bottom: 1px solid rgba(201,168,76,0.2);
  }
  .stat-item {
    display: flex; align-items: center; gap: 10px;
    padding: 10px 28px;
    border-right: 1px solid rgba(201,168,76,0.18);
  }
  .stat-item:last-child { border-right: none; }
  .stat-icon { font-size: 1.5rem; }
  .stat-num { font-family: 'Cinzel', serif; font-size: 1.35rem; font-weight: 700; color: var(--gold-light); line-height: 1; }
  .stat-label { font-family: 'Cormorant Garamond', serif; font-size: 0.85rem; color: rgba(249,243,232,0.65); letter-spacing: 0.08em; }

  /* ── SECTION BASE ── */
  section { padding: 80px 20px; }
  .section-eyebrow {
    font-family: 'Cormorant Garamond', serif;
    font-size: 0.82rem; letter-spacing: 0.22em; text-transform: uppercase;
    color: var(--gold-dark); margin-bottom: 8px; text-align: center;
  }
  .section-title {
    font-family: 'Cinzel', serif;
    font-size: clamp(1.6rem, 4vw, 2.5rem);
    font-weight: 700; color: var(--forest);
    text-align: center; margin-bottom: 14px;
    letter-spacing: 0.03em;
  }
  .section-divider {
    display: flex; align-items: center; justify-content: center; gap: 10px;
    margin-bottom: 50px;
  }
  .divider-line { height: 1px; width: 60px; background: linear-gradient(to right, transparent, var(--gold)); }
  .divider-line.r { background: linear-gradient(to left, transparent, var(--gold)); }
  .divider-gem { color: var(--gold); font-size: 0.7rem; }

  /* ── ABOUT ── */
  #about { background: var(--parchment); }
  .about-grid {
    max-width: 1100px; margin: 0 auto;
    display: grid; grid-template-columns: 1fr;
    gap: 40px; align-items: start;
  }
  @media(min-width:768px){ .about-grid { grid-template-columns: 1fr 1.4fr; gap: 60px; align-items: center; } }

  .about-card {
    background: var(--forest);
    border-radius: 22px;
    padding: 36px 28px;
    text-align: center;
    position: relative;
    overflow: hidden;
    box-shadow: var(--shadow);
  }
  .about-card::before {
    content: '';
    position: absolute; top: 0; left: 0; right: 0;
    height: 4px;
    background: linear-gradient(90deg, transparent, var(--gold), transparent);
  }
  .about-avatar {
    width: 110px; height: 110px; border-radius: 50%;
    background: linear-gradient(135deg, var(--gold-dark), var(--gold));
    display: flex; align-items: center; justify-content: center;
    font-size: 3.2rem; margin: 0 auto 18px;
    box-shadow: 0 6px 28px rgba(201,168,76,0.3);
    border: 3px solid rgba(201,168,76,0.4);
  }
  .about-name { font-family: 'Cinzel', serif; font-size: 1.25rem; color: var(--gold-light); font-weight: 700; margin-bottom: 4px; }
  .about-degree { font-family: 'Cormorant Garamond', serif; font-size: 1rem; color: var(--gold); font-style: italic; margin-bottom: 12px; }
  .about-desc { font-size: 0.87rem; color: rgba(249,243,232,0.72); line-height: 1.7; }
  .about-tag {
    display: inline-block;
    background: rgba(201,168,76,0.12);
    border: 1px solid rgba(201,168,76,0.25);
    border-radius: 100px;
    padding: 4px 14px;
    font-size: 0.75rem;
    color: var(--gold-light);
    letter-spacing: 0.08em;
    margin: 4px 3px;
    font-family: 'Cormorant Garamond', serif;
  }
  .about-tags { margin-top: 14px; }

  .about-content .section-title { text-align: left; }
  .about-content .section-eyebrow { text-align: left; }
  .about-content .section-divider { justify-content: flex-start; margin-bottom: 22px; }
  .about-text { color: var(--text-mid); line-height: 1.8; margin-bottom: 24px; font-size: 1.02rem; font-family: 'Cormorant Garamond', serif; font-size: 1.1rem; }

  .philosophy-cards { display: grid; grid-template-columns: 1fr 1fr; gap: 14px; margin-top: 22px; }
  .phil-card {
    background: white;
    border-radius: 14px;
    padding: 18px 16px;
    border: 1px solid rgba(201,168,76,0.2);
    box-shadow: 0 2px 14px rgba(26,58,40,0.06);
    transition: transform 0.22s, box-shadow 0.22s;
  }
  .phil-card:hover { transform: translateY(-3px); box-shadow: 0 8px 28px rgba(26,58,40,0.1); }
  .phil-icon { font-size: 1.6rem; margin-bottom: 8px; }
  .phil-title { font-family: 'Cinzel', serif; font-size: 0.8rem; color: var(--forest); font-weight: 700; letter-spacing: 0.06em; margin-bottom: 4px; }
  .phil-text { font-size: 0.8rem; color: var(--text-mid); line-height: 1.5; }

  /* ── PRODUCTS ── */
  #products { background: var(--cream); }
  .filter-bar {
    display: flex; gap: 10px; justify-content: center; flex-wrap: wrap;
    margin-bottom: 40px;
  }
  .filter-btn {
    background: none;
    border: 1.5px solid rgba(201,168,76,0.35);
    color: var(--forest);
    font-family: 'Cinzel', serif;
    font-size: 0.75rem; letter-spacing: 0.1em;
    padding: 9px 22px; border-radius: 100px;
    cursor: pointer;
    transition: all 0.22s;
  }
  .filter-btn.active, .filter-btn:hover {
    background: var(--forest);
    border-color: var(--forest);
    color: var(--gold-light);
  }

  .products-grid {
    max-width: 1150px; margin: 0 auto;
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
    gap: 26px;
  }

  .product-card {
    background: white;
    border-radius: 20px;
    overflow: hidden;
    box-shadow: 0 4px 22px rgba(26,58,40,0.08);
    border: 1px solid rgba(201,168,76,0.15);
    transition: transform 0.28s, box-shadow 0.28s;
    position: relative;
  }
  .product-card:hover { transform: translateY(-6px); box-shadow: 0 16px 48px rgba(26,58,40,0.14); }

  .product-card.hidden { display: none; }

  .product-img-wrap {
    position: relative;
    background: linear-gradient(135deg, var(--parchment), var(--cream-dark));
    padding: 28px 28px 18px;
    display: flex; align-items: center; justify-content: center;
    min-height: 140px;
  }
  .product-emoji { font-size: 4rem; }
  .product-badge-price {
    position: absolute; top: 14px; right: 14px;
    background: linear-gradient(135deg, #8B1A1A, #c0392b);
    color: #fff;
    font-family: 'Cinzel', serif;
    font-weight: 700; font-size: 0.8rem;
    padding: 7px 14px; border-radius: 100px;
    box-shadow: 0 3px 12px rgba(139,26,26,0.35);
    letter-spacing: 0.05em;
  }
  .product-cat-tag {
    position: absolute; top: 14px; left: 14px;
    background: var(--forest);
    color: var(--gold-light);
    font-family: 'Cinzel', serif;
    font-size: 0.62rem; letter-spacing: 0.1em;
    padding: 5px 12px; border-radius: 100px;
  }

  .product-body { padding: 22px 22px 24px; }
  .product-name {
    font-family: 'Cinzel', serif;
    font-size: 1.1rem; font-weight: 700;
    color: var(--forest); margin-bottom: 4px;
    letter-spacing: 0.03em; line-height: 1.25;
  }
  .product-tagline {
    font-family: 'Cormorant Garamond', serif;
    font-style: italic; font-size: 0.92rem;
    color: var(--gold-dark); margin-bottom: 14px;
  }
  .product-benefits { list-style: none; margin-bottom: 18px; }
  .product-benefits li {
    display: flex; align-items: flex-start; gap: 8px;
    font-size: 0.84rem; color: var(--text-mid);
    padding: 4px 0; line-height: 1.4;
  }
  .product-benefits li::before {
    content: '✓';
    color: var(--forest-light);
    font-weight: 700; font-size: 0.75rem;
    margin-top: 1px; flex-shrink: 0;
  }
  .product-footer {
    display: flex; gap: 10px; align-items: center;
    padding-top: 14px;
    border-top: 1px solid rgba(201,168,76,0.12);
  }
  .btn-order {
    flex: 1; background: var(--forest);
    color: var(--gold-light);
    font-family: 'Cinzel', serif; font-size: 0.75rem;
    font-weight: 700; letter-spacing: 0.08em;
    padding: 11px 16px; border-radius: 100px;
    text-decoration: none; text-align: center;
    transition: all 0.22s; border: none; cursor: pointer;
    display: block;
  }
  .btn-order:hover { background: var(--forest-light); transform: translateY(-1px); }
  .btn-wa-small {
    width: 42px; height: 42px; border-radius: 50%;
    background: #25D366;
    display: flex; align-items: center; justify-content: center;
    font-size: 1.1rem; text-decoration: none; flex-shrink: 0;
    transition: transform 0.2s;
  }
  .btn-wa-small:hover { transform: scale(1.1); }

  /* ── FEATURED BANNER ── */
  .featured-banner {
    background: linear-gradient(135deg, var(--forest) 0%, #0e2318 60%, var(--forest-mid) 100%);
    padding: 60px 24px;
    text-align: center;
    position: relative; overflow: hidden;
  }
  .featured-banner::before {
    content: '';
    position: absolute; inset: 0;
    background: radial-gradient(ellipse at center, rgba(201,168,76,0.1) 0%, transparent 70%);
  }
  .featured-banner h2 { font-family: 'Cinzel', serif; font-size: clamp(1.5rem,4vw,2.6rem); color: var(--gold-light); margin-bottom: 12px; position: relative; }
  .featured-banner p { font-family: 'Cormorant Garamond', serif; font-style: italic; font-size: 1.2rem; color: rgba(249,243,232,0.75); max-width: 600px; margin: 0 auto 28px; position: relative; line-height: 1.6; }
  .featured-banner .btn-primary { position: relative; }

  /* ── HOW TO ORDER ── */
  #order { background: var(--parchment); }
  .steps-grid {
    max-width: 900px; margin: 0 auto;
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(190px, 1fr));
    gap: 22px;
  }
  .step-card {
    background: white;
    border-radius: 18px;
    padding: 30px 22px 26px;
    text-align: center;
    border: 1px solid rgba(201,168,76,0.15);
    box-shadow: 0 3px 18px rgba(26,58,40,0.07);
    position: relative;
    transition: transform 0.22s;
  }
  .step-card:hover { transform: translateY(-4px); }
  .step-num {
    width: 48px; height: 48px; border-radius: 50%;
    background: linear-gradient(135deg, var(--gold), var(--gold-dark));
    color: white;
    font-family: 'Cinzel', serif; font-size: 1.1rem; font-weight: 700;
    display: flex; align-items: center; justify-content: center;
    margin: 0 auto 14px;
    box-shadow: 0 4px 14px rgba(201,168,76,0.3);
  }
  .step-icon { font-size: 1.8rem; margin-bottom: 10px; }
  .step-title { font-family: 'Cinzel', serif; font-size: 0.88rem; color: var(--forest); font-weight: 700; letter-spacing: 0.06em; margin-bottom: 7px; }
  .step-text { font-size: 0.83rem; color: var(--text-mid); line-height: 1.6; }

  /* ── REVIEWS ── */
  #reviews { background: var(--cream); }
  .reviews-grid {
    max-width: 1100px; margin: 0 auto;
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 22px;
  }
  .review-card {
    background: white;
    border-radius: 18px;
    padding: 26px 22px;
    border: 1px solid rgba(201,168,76,0.15);
    box-shadow: 0 3px 16px rgba(26,58,40,0.06);
    transition: transform 0.22s, box-shadow 0.22s;
    position: relative;
  }
  .review-card:hover { transform: translateY(-3px); box-shadow: 0 10px 32px rgba(26,58,40,0.1); }
  .review-card::before {
    content: '"';
    position: absolute; top: 14px; left: 20px;
    font-family: 'Cinzel', serif; font-size: 3.5rem;
    color: rgba(201,168,76,0.15); line-height: 1;
    font-weight: 900;
  }
  .stars { color: var(--gold); font-size: 1rem; margin-bottom: 10px; letter-spacing: 2px; }
  .review-text { font-family: 'Cormorant Garamond', serif; font-size: 1.05rem; color: var(--text-mid); line-height: 1.65; margin-bottom: 16px; font-style: italic; }
  .reviewer { display: flex; align-items: center; gap: 10px; }
  .reviewer-avatar {
    width: 38px; height: 38px; border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    font-size: 1.1rem;
    flex-shrink: 0;
  }
  .reviewer-name { font-family: 'Cinzel', serif; font-size: 0.8rem; color: var(--forest); font-weight: 700; }
  .reviewer-location { font-size: 0.75rem; color: var(--gold-dark); font-family: 'Cormorant Garamond', serif; }
  .reviewer-product { font-size: 0.72rem; color: rgba(74,63,48,0.55); margin-top: 2px; font-style: italic; }

  /* ── WHY AYURCARE ── */
  #why { background: var(--parchment); }
  .why-grid {
    max-width: 1000px; margin: 0 auto;
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
    gap: 20px;
  }
  .why-card {
    background: white;
    border-radius: 16px;
    padding: 26px 20px;
    text-align: center;
    border: 1px solid rgba(201,168,76,0.12);
    box-shadow: 0 2px 14px rgba(26,58,40,0.05);
    transition: transform 0.22s, border-color 0.22s;
  }
  .why-card:hover { transform: translateY(-4px); border-color: rgba(201,168,76,0.4); }
  .why-icon { font-size: 2.2rem; margin-bottom: 12px; }
  .why-title { font-family: 'Cinzel', serif; font-size: 0.85rem; color: var(--forest); font-weight: 700; letter-spacing: 0.06em; margin-bottom: 8px; }
  .why-text { font-size: 0.82rem; color: var(--text-mid); line-height: 1.55; }

  /* ── CONTACT ── */
  #contact { background: var(--forest); }
  #contact .section-title { color: var(--gold-light); }
  #contact .section-eyebrow { color: var(--gold); }
  #contact .divider-line { background: linear-gradient(to right, transparent, var(--gold)); }
  #contact .divider-line.r { background: linear-gradient(to left, transparent, var(--gold)); }

  .contact-grid {
    max-width: 900px; margin: 0 auto;
    display: grid; grid-template-columns: 1fr;
    gap: 24px;
  }
  @media(min-width:600px){ .contact-grid { grid-template-columns: 1fr 1fr; } }

  .contact-card {
    background: rgba(249,243,232,0.06);
    border: 1px solid rgba(201,168,76,0.2);
    border-radius: 18px;
    padding: 30px 26px;
    text-align: center;
    transition: background 0.22s, transform 0.22s;
  }
  .contact-card:hover { background: rgba(201,168,76,0.08); transform: translateY(-3px); }
  .contact-icon { font-size: 2.4rem; margin-bottom: 12px; }
  .contact-title { font-family: 'Cinzel', serif; font-size: 1rem; color: var(--gold-light); font-weight: 700; margin-bottom: 6px; }
  .contact-sub { font-family: 'Cormorant Garamond', serif; font-size: 1rem; color: rgba(249,243,232,0.65); font-style: italic; margin-bottom: 16px; }
  .contact-btn {
    display: inline-flex; align-items: center; gap: 8px;
    padding: 12px 26px; border-radius: 100px;
    font-family: 'Cinzel', serif; font-size: 0.78rem; font-weight: 700;
    letter-spacing: 0.08em; text-decoration: none;
    transition: transform 0.2s, opacity 0.2s;
  }
  .contact-btn:hover { transform: translateY(-2px); opacity: 0.9; }
  .contact-btn.wa { background: #25D366; color: #fff; }
  .contact-btn.ig { background: linear-gradient(135deg,#f09433,#e6683c,#dc2743,#cc2366,#bc1888); color: #fff; }
  .contact-phone { font-family: 'Cinzel', serif; font-size: 1.25rem; color: var(--gold); font-weight: 700; letter-spacing: 0.08em; }
  .contact-handle { font-size: 0.9rem; color: rgba(249,243,232,0.6); font-family: 'Cormorant Garamond', serif; font-style: italic; }

  /* ── FOOTER ── */
  footer {
    background: #0b1e13;
    padding: 40px 24px 24px;
    text-align: center;
    border-top: 1px solid rgba(201,168,76,0.15);
  }
  .footer-logo { font-family: 'Cinzel', serif; font-size: 1.5rem; color: var(--gold-light); font-weight: 700; letter-spacing: 0.08em; margin-bottom: 8px; }
  .footer-tagline { font-family: 'Cormorant Garamond', serif; font-style: italic; color: rgba(232,201,107,0.55); font-size: 1rem; margin-bottom: 20px; }
  .footer-links { display: flex; flex-wrap: wrap; gap: 8px 24px; justify-content: center; margin-bottom: 20px; }
  .footer-links a { color: rgba(249,243,232,0.5); font-size: 0.82rem; text-decoration: none; font-family: 'Cormorant Garamond', serif; letter-spacing: 0.06em; transition: color 0.2s; }
  .footer-links a:hover { color: var(--gold-light); }
  .footer-social { display: flex; gap: 12px; justify-content: center; margin-bottom: 24px; }
  .footer-social a {
    width: 38px; height: 38px; border-radius: 50%;
    border: 1px solid rgba(201,168,76,0.25);
    display: flex; align-items: center; justify-content: center;
    font-size: 1rem; text-decoration: none; color: var(--gold-light);
    transition: all 0.22s;
  }
  .footer-social a:hover { background: rgba(201,168,76,0.12); border-color: var(--gold); }
  .footer-copy { font-size: 0.75rem; color: rgba(249,243,232,0.28); font-family: 'Lato', sans-serif; }

  /* ── FLOATING BUTTONS ── */
  .float-buttons {
    position: fixed; bottom: 24px; right: 20px;
    display: flex; flex-direction: column; gap: 12px;
    z-index: 900;
  }
  .float-btn {
    width: 52px; height: 52px; border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    font-size: 1.35rem; text-decoration: none;
    box-shadow: 0 6px 22px rgba(0,0,0,0.22);
    transition: transform 0.22s, box-shadow 0.22s;
    border: none; cursor: pointer;
  }
  .float-btn:hover { transform: scale(1.12); box-shadow: 0 10px 30px rgba(0,0,0,0.28); }
  .float-wa { background: #25D366; }
  .float-ig { background: linear-gradient(135deg,#f09433,#e6683c,#dc2743,#cc2366,#bc1888); }
  .float-top { background: var(--forest); color: var(--gold-light); opacity: 0; pointer-events: none; transition: opacity 0.3s; }
  .float-top.visible { opacity: 1; pointer-events: all; }

  /* ── SCROLL ANIMATIONS ── */
  .reveal {
    opacity: 0; transform: translateY(32px);
    transition: opacity 0.65s ease, transform 0.65s ease;
  }
  .reveal.visible { opacity: 1; transform: translateY(0); }
  .reveal-delay-1 { transition-delay: 0.1s; }
  .reveal-delay-2 { transition-delay: 0.2s; }
  .reveal-delay-3 { transition-delay: 0.3s; }
  .reveal-delay-4 { transition-delay: 0.4s; }
  .reveal-delay-5 { transition-delay: 0.5s; }

  /* responsive tweaks */
  @media(max-width:480px){
    .stat-item { padding: 8px 14px; border-right: none; border-bottom: 1px solid rgba(201,168,76,0.12); }
    .stat-item:last-child { border-bottom: none; }
    .philosophy-cards { grid-template-columns: 1fr; }
  }
</style>
</head>
<body>

<!-- ANNOUNCEMENT BAR -->
<div class="announce-bar" id="announcebar">
  <div class="announce-inner">
    <span>🌿 100% Natural Ayurvedic Products</span>
    <span>✦ No Harmful Chemicals</span>
    <span>🌸 Handcrafted by Dr. Bhumika Kirote (BAMS)</span>
    <span>✦ Free Consultation on Order</span>
    <span>📞 7741988734</span>
    <span>✦ DM on Instagram @bhumi.creations_19</span>
    <span>🌿 100% Natural Ayurvedic Products</span>
    <span>✦ No Harmful Chemicals</span>
    <span>🌸 Handcrafted by Dr. Bhumika Kirote (BAMS)</span>
  </div>
</div>

<!-- NAVBAR -->
<nav class="navbar" id="navbar" style="margin-top:38px;">
  <a href="#hero" class="nav-logo">
    <div class="nav-logo-icon">🌿</div>
    <div class="nav-logo-text">
      <div class="brand">AyurCareByBhumi</div>
      <div class="tagline">Pure Ayurveda, Pure Care</div>
    </div>
  </a>
  <div class="nav-right">
    <a href="https://wa.me/917741988734?text=Hello%20Dr.%20Bhumika!%20I%27d%20like%20to%20order%20an%20AyurCare%20product." target="_blank" class="nav-cta">Order Now</a>
    <button class="hamburger" id="hamburger" aria-label="Menu">
      <span></span><span></span><span></span>
    </button>
  </div>
</nav>

<!-- DRAWER OVERLAY -->
<div class="drawer-overlay" id="drawerOverlay" onclick="closeDrawer()"></div>

<!-- SIDE DRAWER -->
<aside class="drawer" id="drawer">
  <div class="drawer-header">
    <span class="drawer-title">✦ Navigation</span>
    <button class="drawer-close" onclick="closeDrawer()" aria-label="Close">✕</button>
  </div>
  <nav class="drawer-nav">
    <a href="#hero" class="drawer-link" onclick="closeDrawer()"><span class="icon">🏠</span> Home</a>
    <a href="#about" class="drawer-link" onclick="closeDrawer()"><span class="icon">👩‍⚕️</span> About Dr. Bhumika</a>

    <div class="drawer-products-toggle" onclick="toggleProductMenu()" id="prodToggle">
      <div class="left"><span class="icon">🛍️</span> Our Products</div>
      <span class="drawer-chevron" id="prodChevron">▼</span>
    </div>
    <div class="drawer-sub" id="productSub">
      <a href="#products" class="drawer-sub-link" onclick="filterAndGo('all')">All Products</a>
      <a href="#products" class="drawer-sub-link" onclick="filterAndGo('skin')">Skin Care</a>
      <a href="#products" class="drawer-sub-link" onclick="filterAndGo('hair')">Hair Care</a>
      <a href="#products" class="drawer-sub-link" onclick="filterAndGo('ghrita')">Ghrita (Butter)</a>
    </div>

    <a href="#order" class="drawer-link" onclick="closeDrawer()"><span class="icon">📦</span> How to Order</a>
    <a href="#reviews" class="drawer-link" onclick="closeDrawer()"><span class="icon">⭐</span> Reviews</a>
    <a href="#why" class="drawer-link" onclick="closeDrawer()"><span class="icon">🌱</span> Why AyurCare</a>
    <a href="#contact" class="drawer-link" onclick="closeDrawer()"><span class="icon">📞</span> Contact</a>
  </nav>
  <div class="drawer-footer">
    <a href="https://wa.me/917741988734?text=Hello%20Dr.%20Bhumika!" target="_blank" class="drawer-social wa">
      💬 WhatsApp
    </a>
    <a href="https://instagram.com/bhumi.creations_19" target="_blank" class="drawer-social ig">
      📷 Instagram
    </a>
  </div>
</aside>

<!-- HERO -->
<section class="hero" id="hero">
  <div class="hero-bg-pattern"></div>
  <div class="hero-ornament"></div>
  <div class="hero-ornament"></div>
  <div class="hero-ornament"></div>

  <div class="hero-badge">Pure Ayurveda, Pure Care</div>
  <p class="hero-eyebrow">Handcrafted with Ancient Wisdom</p>
  <h1 class="hero-title">
    Heal Naturally<br>with <span class="gold">AyurCare</span>
  </h1>
  <p class="hero-subtitle">
    Authentic Ayurvedic formulations by Dr. Bhumika Kirote (BAMS) — crafted without chemicals, rooted in tradition.
  </p>
  <div class="hero-btns">
    <a href="#products" class="btn-primary">Explore Products</a>
    <a href="https://wa.me/917741988734?text=Hello!%20I%27d%20like%20to%20know%20more%20about%20AyurCare%20products." target="_blank" class="btn-outline">💬 WhatsApp Us</a>
  </div>

  <div class="hero-scroll">
    <span>SCROLL</span>
    <div class="scroll-dot"></div>
  </div>
</section>

<!-- STATS STRIP -->
<div class="stats-strip">
  <div class="stat-item">
    <span class="stat-icon">🌿</span>
    <div>
      <div class="stat-num">100%</div>
      <div class="stat-label">Natural</div>
    </div>
  </div>
  <div class="stat-item">
    <span class="stat-icon">🚫</span>
    <div>
      <div class="stat-num">Zero</div>
      <div class="stat-label">Chemicals</div>
    </div>
  </div>
  <div class="stat-item">
    <span class="stat-icon">👥</span>
    <div>
      <div class="stat-num">500+</div>
      <div class="stat-label">Happy Customers</div>
    </div>
  </div>
  <div class="stat-item">
    <span class="stat-icon">🏆</span>
    <div>
      <div class="stat-num">BAMS</div>
      <div class="stat-label">Certified Doctor</div>
    </div>
  </div>
</div>

<!-- ABOUT -->
<section id="about">
  <p class="section-eyebrow reveal">The Healer Behind AyurCare</p>
  <h2 class="section-title reveal">Meet Dr. Bhumika Kirote</h2>
  <div class="section-divider reveal">
    <div class="divider-line"></div>
    <span class="divider-gem">✦</span>
    <div class="divider-line r"></div>
  </div>

  <div class="about-grid">
    <div class="about-card reveal">
      <div class="about-avatar">👩‍⚕️</div>
      <div class="about-name">Dr. Bhumika Samadhan Kirote</div>
      <div class="about-degree">BAMS — Bachelor of Ayurvedic Medicine & Surgery</div>
      <p class="about-desc">
        A passionate Ayurvedic physician dedicated to bringing the healing power of ancient herbs to modern lives — naturally, safely, and effectively.
      </p>
      <div class="about-tags">
        <span class="about-tag">Ayurvedic Medicine</span>
        <span class="about-tag">Herbal Formulations</span>
        <span class="about-tag">Skin & Hair Care</span>
        <span class="about-tag">Natural Healing</span>
      </div>
    </div>

    <div class="about-content">
      <p class="section-eyebrow">Philosophy & Vision</p>
      <h3 class="section-title" style="font-size:1.6rem;">Rooted in Tradition,<br>Made for Today</h3>
      <div class="section-divider">
        <div class="divider-line"></div>
        <span class="divider-gem">✦</span>
        <div class="divider-line r"></div>
      </div>
      <p class="about-text reveal">
        AyurCare was born from a simple belief — that nature holds the remedy for every ailment. As a practicing BAMS doctor, Dr. Bhumika carefully formulates each product using time-tested Ayurvedic herbs, handcrafted in small batches to ensure maximum potency and purity.
      </p>
      <p class="about-text reveal">
        Every product is prepared following shastriya (classical) methods, without any synthetic additives, preservatives, or harsh chemicals. Pure ingredients, pure results.
      </p>

      <div class="philosophy-cards">
        <div class="phil-card reveal reveal-delay-1">
          <div class="phil-icon">🌱</div>
          <div class="phil-title">Pure Ingredients</div>
          <p class="phil-text">Only the finest Ayurvedic herbs, sourced and blended with care.</p>
        </div>
        <div class="phil-card reveal reveal-delay-2">
          <div class="phil-icon">🧪</div>
          <div class="phil-title">No Chemicals</div>
          <p class="phil-text">Zero synthetic additives — safe for all skin types including sensitive skin.</p>
        </div>
        <div class="phil-card reveal reveal-delay-3">
          <div class="phil-icon">📜</div>
          <div class="phil-title">Shastriya Method</div>
          <p class="phil-text">Formulated following classical Ayurvedic texts and time-tested processes.</p>
        </div>
        <div class="phil-card reveal reveal-delay-4">
          <div class="phil-icon">💛</div>
          <div class="phil-title">Doctor Crafted</div>
          <p class="phil-text">Each product personally formulated and verified by a qualified BAMS doctor.</p>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- PRODUCTS -->
<section id="products">
  <p class="section-eyebrow reveal">Crafted with Ancient Herbs</p>
  <h2 class="section-title reveal">Our Ayurvedic Collection</h2>
  <div class="section-divider reveal">
    <div class="divider-line"></div>
    <span class="divider-gem">✦</span>
    <div class="divider-line r"></div>
  </div>

  <div class="filter-bar reveal">
    <button class="filter-btn active" onclick="filterProducts('all', this)">All Products</button>
    <button class="filter-btn" onclick="filterProducts('skin', this)">Skin Care</button>
    <button class="filter-btn" onclick="filterProducts('hair', this)">Hair Care</button>
    <button class="filter-btn" onclick="filterProducts('ghrita', this)">Ghrita</button>
  </div>

  <div class="products-grid">

    <!-- Product 1: Shatdhaut Ghrita -->
    <div class="product-card reveal" data-category="ghrita skin">
      <div class="product-img-wrap">
        <div class="product-emoji">🫙</div>
        <span class="product-badge-price">₹ Ask</span>
        <span class="product-cat-tag">GHRITA</span>
      </div>
      <div class="product-body">
        <div class="product-name">Shatdhaut Ghrita</div>
        <div class="product-tagline">100 Times Washed Clarified Butter</div>
        <ul class="product-benefits">
          <li>Deeply moisturizes & nourishes skin</li>
          <li>100% Natural — no additives</li>
          <li>Protects against sun damage</li>
          <li>For glowing, radiant skin</li>
          <li>Heals cracked heels</li>
          <li>Best for lip care</li>
        </ul>
        <div class="product-footer">
          <a href="https://wa.me/917741988734?text=Hello%20Dr.%20Bhumika!%20I%20want%20to%20order%20Shatdhaut%20Ghrita.%20Please%20share%20details." target="_blank" class="btn-order">Order Now</a>
          <a href="https://wa.me/917741988734?text=Hello%20Dr.%20Bhumika!%20I%20want%20to%20order%20Shatdhaut%20Ghrita." target="_blank" class="btn-wa-small">💬</a>
        </div>
      </div>
    </div>

    <!-- Product 2: Keshvardhini Hair Pack – Hair Fall -->
    <div class="product-card reveal reveal-delay-1" data-category="hair">
      <div class="product-img-wrap" style="background:linear-gradient(135deg,#f5edd8,#e8d5b0);">
        <div class="product-emoji">🌿</div>
        <span class="product-badge-price">₹50 / Pack</span>
        <span class="product-cat-tag">HAIR CARE</span>
      </div>
      <div class="product-body">
        <div class="product-name">Keshvardhini Hair Pack</div>
        <div class="product-tagline">For Hair Fall — केस गळती साठी</div>
        <ul class="product-benefits">
          <li>Reduces hair fall significantly</li>
          <li>Strengthens roots and strands</li>
          <li>Nourishes hair from the roots</li>
          <li>Promotes natural hair growth</li>
          <li>Homemade — no chemicals</li>
        </ul>
        <div class="product-footer">
          <a href="https://wa.me/917741988734?text=Hello!%20I%20want%20to%20order%20Keshvardhini%20Hair%20Pack%20for%20Hair%20Fall.%20Price%20Rs.50%20per%20pack." target="_blank" class="btn-order">Order — ₹50</a>
          <a href="https://wa.me/917741988734?text=Hello!%20Order%20Keshvardhini%20Hair%20Pack%20(Hair%20Fall)" target="_blank" class="btn-wa-small">💬</a>
        </div>
      </div>
    </div>

    <!-- Product 3: Keshvardhini Hair Pack – Dandruff -->
    <div class="product-card reveal reveal-delay-2" data-category="hair">
      <div class="product-img-wrap" style="background:linear-gradient(135deg,#edf5e8,#d5e8c8);">
        <div class="product-emoji">🌾</div>
        <span class="product-badge-price">₹50 / Pack</span>
        <span class="product-cat-tag">HAIR CARE</span>
      </div>
      <div class="product-body">
        <div class="product-name">Keshvardhini Hair Pack</div>
        <div class="product-tagline">For Dandruff — दारूणका साठी</div>
        <ul class="product-benefits">
          <li>Removes dandruff effectively</li>
          <li>Keeps scalp clean and fresh</li>
          <li>Reduces itching & irritation</li>
          <li>Controls excess oil on scalp</li>
          <li>Reduces hair fall from roots</li>
        </ul>
        <div class="product-footer">
          <a href="https://wa.me/917741988734?text=Hello!%20I%20want%20to%20order%20Keshvardhini%20Hair%20Pack%20for%20Dandruff.%20Rs.50%20per%20pack." target="_blank" class="btn-order">Order — ₹50</a>
          <a href="https://wa.me/917741988734?text=Hello!%20Order%20Keshvardhini%20Hair%20Pack%20(Dandruff)" target="_blank" class="btn-wa-small">💬</a>
        </div>
      </div>
    </div>

    <!-- Product 4: Saundarya Face Pack – Skin Glow -->
    <div class="product-card reveal reveal-delay-1" data-category="skin">
      <div class="product-img-wrap" style="background:linear-gradient(135deg,#fdf0e8,#f5d9c0);">
        <div class="product-emoji">✨</div>
        <span class="product-badge-price">₹60 / Pack</span>
        <span class="product-cat-tag">SKIN CARE</span>
      </div>
      <div class="product-body">
        <div class="product-name">Saundarya Face Pack</div>
        <div class="product-tagline">For Glowing, Radiant Skin</div>
        <ul class="product-benefits">
          <li>Makes your skin glow naturally</li>
          <li>Reduces pigmentation & dark spots</li>
          <li>Intense hydration for skin</li>
          <li>Brightens dull & tired skin</li>
          <li>Made from Ayurvedic herbs</li>
        </ul>
        <div class="product-footer">
          <a href="https://wa.me/917741988734?text=Hello!%20I%20want%20to%20order%20Saundarya%20Face%20Pack%20for%20Skin%20Glow.%20Rs.60%20per%20pack." target="_blank" class="btn-order">Order — ₹60</a>
          <a href="https://wa.me/917741988734?text=Hello!%20Order%20Saundarya%20Face%20Pack%20(Skin%20Glow)" target="_blank" class="btn-wa-small">💬</a>
        </div>
      </div>
    </div>

    <!-- Product 5: Saundarya Face Pack – Pimples -->
    <div class="product-card reveal reveal-delay-2" data-category="skin">
      <div class="product-img-wrap" style="background:linear-gradient(135deg,#f5e8f0,#e8c8d8);">
        <div class="product-emoji">🌸</div>
        <span class="product-badge-price">₹50 / Pack</span>
        <span class="product-cat-tag">SKIN CARE</span>
      </div>
      <div class="product-body">
        <div class="product-name">Saundarya Face Pack</div>
        <div class="product-tagline">Specially for Pimples & Acne</div>
        <ul class="product-benefits">
          <li>Reduces acne & pimples</li>
          <li>Controls excess oil production</li>
          <li>Soothes irritated skin</li>
          <li>Reduces redness & pimple marks</li>
          <li>Clears and unclogs pores</li>
        </ul>
        <div class="product-footer">
          <a href="https://wa.me/917741988734?text=Hello!%20I%20want%20to%20order%20Saundarya%20Face%20Pack%20for%20Pimples.%20Rs.50%20per%20pack." target="_blank" class="btn-order">Order — ₹50</a>
          <a href="https://wa.me/917741988734?text=Hello!%20Order%20Saundarya%20Face%20Pack%20(Pimples)" target="_blank" class="btn-wa-small">💬</a>
        </div>
      </div>
    </div>

  </div>
</section>

<!-- FEATURED BANNER -->
<div class="featured-banner">
  <h2 class="reveal">✦ Start Your Natural Healing Journey ✦</h2>
  <p class="reveal">
    "Every skin, every hair, every person deserves the gentle touch of nature. No shortcuts, no chemicals — just pure Ayurveda."
    <br><em style="font-size:0.9rem;opacity:0.6;">— Dr. Bhumika Kirote, BAMS</em>
  </p>
  <a href="https://wa.me/917741988734?text=Hello%20Dr.%20Bhumika!%20I%20want%20to%20consult%20about%20the%20best%20product%20for%20me." target="_blank" class="btn-primary reveal">Get a Free Consultation 🌿</a>
</div>

<!-- HOW TO ORDER -->
<section id="order">
  <p class="section-eyebrow reveal">Simple & Easy</p>
  <h2 class="section-title reveal">How to Order</h2>
  <div class="section-divider reveal">
    <div class="divider-line"></div>
    <span class="divider-gem">✦</span>
    <div class="divider-line r"></div>
  </div>

  <div class="steps-grid">
    <div class="step-card reveal">
      <div class="step-icon">💬</div>
      <div class="step-num">1</div>
      <div class="step-title">DM or WhatsApp</div>
      <p class="step-text">Contact Dr. Bhumika on WhatsApp (7741988734) or Instagram DM @bhumi.creations_19</p>
    </div>
    <div class="step-card reveal reveal-delay-1">
      <div class="step-icon">🛍️</div>
      <div class="step-num">2</div>
      <div class="step-title">Choose Product</div>
      <p class="step-text">Select your desired product — Hair Pack, Face Pack, Ghrita, or ask for a personalized recommendation.</p>
    </div>
    <div class="step-card reveal reveal-delay-2">
      <div class="step-icon">💳</div>
      <div class="step-num">3</div>
      <div class="step-title">Confirm & Pay</div>
      <p class="step-text">Confirm your order, share your address, and complete payment via UPI or Cash on Delivery (local).</p>
    </div>
    <div class="step-card reveal reveal-delay-3">
      <div class="step-icon">📦</div>
      <div class="step-num">4</div>
      <div class="step-title">Receive & Glow</div>
      <p class="step-text">Receive your fresh, handcrafted Ayurvedic product and begin your natural healing journey!</p>
    </div>
  </div>
</section>

<!-- REVIEWS -->
<section id="reviews">
  <p class="section-eyebrow reveal">What Customers Say</p>
  <h2 class="section-title reveal">Real Results, Real Smiles</h2>
  <div class="section-divider reveal">
    <div class="divider-line"></div>
    <span class="divider-gem">✦</span>
    <div class="divider-line r"></div>
  </div>

  <div class="reviews-grid">
    <div class="review-card reveal">
      <div class="stars">★★★★★</div>
      <p class="review-text">My hair fall reduced so much after just 3 weeks! The Keshvardhini pack is truly magical. My scalp feels so clean and refreshed every time I use it.</p>
      <div class="reviewer">
        <div class="reviewer-avatar" style="background:#e8f5e8;">🌸</div>
        <div>
          <div class="reviewer-name">Priya Deshmukh</div>
          <div class="reviewer-location">Pune, Maharashtra</div>
          <div class="reviewer-product">Keshvardhini Hair Pack</div>
        </div>
      </div>
    </div>
    <div class="review-card reveal reveal-delay-1">
      <div class="stars">★★★★★</div>
      <p class="review-text">I was struggling with stubborn acne for years. The Saundarya face pack cleared my skin in just 2 weeks. No chemicals, no side effects — only results!</p>
      <div class="reviewer">
        <div class="reviewer-avatar" style="background:#f5e8f0;">✨</div>
        <div>
          <div class="reviewer-name">Sneha Patil</div>
          <div class="reviewer-location">Nashik, Maharashtra</div>
          <div class="reviewer-product">Saundarya Face Pack (Pimples)</div>
        </div>
      </div>
    </div>
    <div class="review-card reveal reveal-delay-2">
      <div class="stars">★★★★★</div>
      <p class="review-text">The Shatdhaut Ghrita is unlike anything I've tried before. My cracked heels healed completely and my lips are so soft now. Highly recommend to everyone!</p>
      <div class="reviewer">
        <div class="reviewer-avatar" style="background:#f5f0e8;">🫙</div>
        <div>
          <div class="reviewer-name">Kavita Jadhav</div>
          <div class="reviewer-location">Aurangabad, Maharashtra</div>
          <div class="reviewer-product">Shatdhaut Ghrita</div>
        </div>
      </div>
    </div>
    <div class="review-card reveal reveal-delay-3">
      <div class="stars">★★★★★</div>
      <p class="review-text">The dandruff variant of the hair pack removed my dandruff in just 7 days. My scalp itching is completely gone. Dr. Bhumika is so knowledgeable and helpful!</p>
      <div class="reviewer">
        <div class="reviewer-avatar" style="background:#e8eef5;">🌿</div>
        <div>
          <div class="reviewer-name">Rohan Sharma</div>
          <div class="reviewer-location">Mumbai, Maharashtra</div>
          <div class="reviewer-product">Keshvardhini (Dandruff)</div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- WHY AYURCARE -->
<section id="why">
  <p class="section-eyebrow reveal">Our Promise to You</p>
  <h2 class="section-title reveal">Why Choose AyurCare?</h2>
  <div class="section-divider reveal">
    <div class="divider-line"></div>
    <span class="divider-gem">✦</span>
    <div class="divider-line r"></div>
  </div>

  <div class="why-grid">
    <div class="why-card reveal">
      <div class="why-icon">🌿</div>
      <div class="why-title">100% Natural</div>
      <p class="why-text">Every ingredient is sourced from nature — herbs, roots, and botanicals with no synthetic fillers.</p>
    </div>
    <div class="why-card reveal reveal-delay-1">
      <div class="why-icon">🏥</div>
      <div class="why-title">Doctor Formulated</div>
      <p class="why-text">Each product is personally crafted by Dr. Bhumika Kirote, a qualified BAMS Ayurvedic physician.</p>
    </div>
    <div class="why-card reveal reveal-delay-2">
      <div class="why-icon">🚫</div>
      <div class="why-title">Chemical Free</div>
      <p class="why-text">Zero parabens, sulfates, synthetic fragrances or harmful preservatives. Safe for sensitive skin.</p>
    </div>
    <div class="why-card reveal reveal-delay-3">
      <div class="why-icon">💰</div>
      <div class="why-title">Affordable Prices</div>
      <p class="why-text">Premium Ayurvedic care starting at just ₹50 — because good health should be accessible to all.</p>
    </div>
    <div class="why-card reveal reveal-delay-4">
      <div class="why-icon">📜</div>
      <div class="why-title">Proven Formulas</div>
      <p class="why-text">Based on classical Ayurvedic texts (shastriya paddhati) tested over thousands of years.</p>
    </div>
    <div class="why-card reveal reveal-delay-5">
      <div class="why-icon">💛</div>
      <div class="why-title">Personalized Care</div>
      <p class="why-text">Get free guidance from Dr. Bhumika to find the right product for your unique needs.</p>
    </div>
  </div>
</section>

<!-- CONTACT -->
<section id="contact">
  <p class="section-eyebrow reveal">Get in Touch</p>
  <h2 class="section-title reveal">Order or Consult Today</h2>
  <div class="section-divider reveal">
    <div class="divider-line"></div>
    <span class="divider-gem">✦</span>
    <div class="divider-line r"></div>
  </div>

  <div class="contact-grid">
    <div class="contact-card reveal">
      <div class="contact-icon">💬</div>
      <div class="contact-title">WhatsApp</div>
      <p class="contact-sub">Fastest way to order or get a free consultation</p>
      <div class="contact-phone">7741988734</div>
      <br>
      <a href="https://wa.me/917741988734?text=Hello%20Dr.%20Bhumika!%20I%20want%20to%20order%20an%20AyurCare%20product." target="_blank" class="contact-btn wa">
        💬 Chat on WhatsApp
      </a>
    </div>
    <div class="contact-card reveal reveal-delay-1">
      <div class="contact-icon">📷</div>
      <div class="contact-title">Instagram</div>
      <p class="contact-sub">DM us for orders, product info & skin/hair tips</p>
      <div class="contact-handle">@bhumi.creations_19</div>
      <br>
      <a href="https://instagram.com/bhumi.creations_19" target="_blank" class="contact-btn ig">
        📷 Follow & DM
      </a>
    </div>
  </div>

  <div style="text-align:center; margin-top:40px;">
    <p style="font-family:'Cormorant Garamond',serif; font-style:italic; color:rgba(249,243,232,0.5); font-size:1rem; margin-bottom:10px;">By Dr. Bhumika Samadhan Kirote</p>
    <p style="font-family:'Cinzel',serif; color:var(--gold); font-size:1.1rem; font-weight:700; letter-spacing:0.1em;">AyurCare — Pure Ayurveda, Pure Care</p>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-logo">AyurCare</div>
  <div class="footer-tagline">Pure Ayurveda, Pure Care — by Dr. Bhumika Kirote</div>
  <div class="footer-links">
    <a href="#hero">Home</a>
    <a href="#about">About</a>
    <a href="#products">Products</a>
    <a href="#order">How to Order</a>
    <a href="#reviews">Reviews</a>
    <a href="#contact">Contact</a>
  </div>
  <div class="footer-social">
    <a href="https://wa.me/917741988734" target="_blank" title="WhatsApp">💬</a>
    <a href="https://instagram.com/bhumi.creations_19" target="_blank" title="Instagram">📷</a>
    <a href="tel:+917741988734" title="Call">📞</a>
  </div>
  <div class="footer-copy">© 2024 AyurCare by Dr. Bhumika Samadhan Kirote · All rights reserved · Made with 🌿 love</div>
</footer>

<!-- FLOATING BUTTONS -->
<div class="float-buttons">
  <a href="https://wa.me/917741988734?text=Hello%20Dr.%20Bhumika!%20I%20want%20to%20order." target="_blank" class="float-btn float-wa" title="WhatsApp">💬</a>
  <a href="https://instagram.com/bhumi.creations_19" target="_blank" class="float-btn float-ig" title="Instagram">📷</a>
  <button class="float-btn float-top" id="scrollTopBtn" onclick="scrollToTop()" title="Back to top">↑</button>
</div>

<script>
  // Navbar scroll
  const navbar = document.getElementById('navbar');
  const announceBar = document.getElementById('announcebar');
  function handleScroll() {
    const scrolled = window.scrollY > 60;
    navbar.classList.toggle('scrolled', scrolled);
    if(scrolled) {
      navbar.style.marginTop = '0';
      announceBar.style.display = 'none';
    } else {
      navbar.style.marginTop = '38px';
      announceBar.style.display = '';
    }
    document.getElementById('scrollTopBtn').classList.toggle('visible', window.scrollY > 400);
  }
  window.addEventListener('scroll', handleScroll, { passive: true });

  // Hamburger
  const hamburger = document.getElementById('hamburger');
  hamburger.addEventListener('click', () => {
    const isOpen = document.getElementById('drawer').classList.contains('open');
    isOpen ? closeDrawer() : openDrawer();
  });
  function openDrawer() {
    document.getElementById('drawer').classList.add('open');
    document.getElementById('drawerOverlay').classList.add('open');
    hamburger.classList.add('open');
    document.body.style.overflow = 'hidden';
  }
  function closeDrawer() {
    document.getElementById('drawer').classList.remove('open');
    document.getElementById('drawerOverlay').classList.remove('open');
    hamburger.classList.remove('open');
    document.body.style.overflow = '';
  }

  // Product sub-menu
  function toggleProductMenu() {
    const sub = document.getElementById('productSub');
    const chevron = document.getElementById('prodChevron');
    sub.classList.toggle('open');
    chevron.classList.toggle('open');
  }
  function filterAndGo(cat) {
    closeDrawer();
    filterProducts(cat, null);
    setTimeout(() => document.getElementById('products').scrollIntoView({behavior:'smooth'}), 300);
  }

  // Product filter
  function filterProducts(category, btn) {
    const cards = document.querySelectorAll('.product-card');
    cards.forEach(card => {
      const cats = card.dataset.category || '';
      if (category === 'all' || cats.includes(category)) {
        card.classList.remove('hidden');
      } else {
        card.classList.add('hidden');
      }
    });
    document.querySelectorAll('.filter-btn').forEach(b => b.classList.remove('active'));
    if (btn) btn.classList.add('active');
    else {
      document.querySelectorAll('.filter-btn').forEach(b => {
        if(b.textContent.toLowerCase().includes(category) || (category==='all' && b.textContent.toLowerCase().includes('all')))
          b.classList.add('active');
      });
    }
  }

  // Scroll to top
  function scrollToTop() { window.scrollTo({top:0,behavior:'smooth'}); }

  // Reveal on scroll
  const revealEls = document.querySelectorAll('.reveal');
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(e => {
      if(e.isIntersecting) { e.target.classList.add('visible'); observer.unobserve(e.target); }
    });
  }, { threshold: 0.12 });
  revealEls.forEach(el => observer.observe(el));
</script>
</body>
</html>
