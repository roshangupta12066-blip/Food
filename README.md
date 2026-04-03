<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Spice Heaven — Taste the Real Flavor</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,600;0,700;1,400&family=Jost:wght@300;400;500;600;700&display=swap" rel="stylesheet">
<style>
  :root {
    --gold:        #c9a84c;
    --gold-light:  #e8c97a;
    --gold-pale:   rgba(201,168,76,0.12);
    --gold-border: rgba(201,168,76,0.25);
    --gold-glow:   rgba(201,168,76,0.35);
    --black:       #0d0b08;
    --black2:      #141209;
    --black3:      #1c1910;
    --black4:      #252117;
    --black5:      #2e2a1e;
    --white:       #f5efe0;
    --text-mid:    #b0a080;
    --text-dim:    #6e6450;
    --serif:       'Playfair Display', serif;
    --sans:        'Jost', sans-serif;
    --r:           14px;
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
  html { scroll-behavior: smooth; }

  body {
    font-family: var(--sans);
    background: var(--black);
    color: var(--white);
    overflow-x: hidden;
    line-height: 1.6;
  }

  ::-webkit-scrollbar { width: 5px; }
  ::-webkit-scrollbar-track { background: var(--black2); }
  ::-webkit-scrollbar-thumb { background: var(--gold); border-radius: 10px; }

  img { display: block; width: 100%; }

  /* ─── NAV ─── */
  nav {
    position: fixed; top: 0; left: 0; right: 0; z-index: 1000;
    height: 70px;
    display: flex; align-items: center; justify-content: space-between;
    padding: 0 6%;
    background: rgba(13,11,8,0.88);
    backdrop-filter: blur(16px);
    border-bottom: 1px solid var(--gold-border);
    transition: box-shadow 0.3s;
  }
  nav.scrolled { box-shadow: 0 6px 30px rgba(0,0,0,0.5); }

  .logo {
    font-family: var(--serif);
    font-size: 1.5rem;
    color: var(--white);
    text-decoration: none;
    letter-spacing: 1px;
  }
  .logo span { color: var(--gold); }

  .nav-links { display: flex; align-items: center; gap: 2.2rem; list-style: none; }
  .nav-links a {
    color: var(--text-mid);
    text-decoration: none;
    font-size: 0.82rem;
    font-weight: 500;
    letter-spacing: 1.5px;
    text-transform: uppercase;
    transition: color 0.2s;
  }
  .nav-links a:hover { color: var(--gold); }

  .nav-order {
    background: transparent;
    border: 1.5px solid var(--gold);
    color: var(--gold);
    padding: 8px 22px;
    border-radius: 50px;
    font-size: 0.8rem;
    font-weight: 700;
    letter-spacing: 1.5px;
    text-transform: uppercase;
    text-decoration: none;
    transition: all 0.25s;
  }
  .nav-order:hover {
    background: var(--gold);
    color: var(--black);
    box-shadow: 0 0 20px var(--gold-glow);
  }

  .hamburger {
    display: none; flex-direction: column; gap: 5px;
    cursor: pointer; border: none; background: none; padding: 5px;
  }
  .hamburger span { display: block; width: 24px; height: 2px; background: var(--white); border-radius: 4px; transition: all 0.3s; }

  .mobile-menu {
    display: none; position: fixed; top: 70px; left: 0; right: 0;
    background: var(--black2); border-bottom: 1px solid var(--gold-border);
    padding: 1.5rem 6%; flex-direction: column; gap: 1.2rem; z-index: 999;
  }
  .mobile-menu.open { display: flex; }
  .mobile-menu a {
    color: var(--text-mid); text-decoration: none;
    font-size: 0.9rem; font-weight: 500; letter-spacing: 1.5px;
    text-transform: uppercase; padding-bottom: 1rem;
    border-bottom: 1px solid var(--gold-border); transition: color 0.2s;
  }
  .mobile-menu a:hover { color: var(--gold); }

  /* ─── HERO ─── */
  #home {
    min-height: 100vh;
    display: flex; align-items: center;
    padding: 120px 6% 80px;
    position: relative; overflow: hidden;
    background: var(--black2);
  }

  .hero-bg-pattern {
    position: absolute; inset: 0; pointer-events: none;
    background-image:
      radial-gradient(ellipse 80% 60% at 70% 50%, rgba(201,168,76,0.07) 0%, transparent 60%),
      repeating-linear-gradient(-45deg, transparent, transparent 50px, rgba(201,168,76,0.015) 50px, rgba(201,168,76,0.015) 51px);
  }

  .hero-ornament {
    position: absolute; right: 5%; top: 50%; transform: translateY(-50%);
    width: min(480px, 45vw);
    display: flex; align-items: center; justify-content: center;
    pointer-events: none;
  }
  .hero-plate {
    width: 100%; aspect-ratio: 1;
    border-radius: 50%;
    background: radial-gradient(circle at 35% 35%, var(--black3), var(--black5));
    border: 1px solid var(--gold-border);
    box-shadow: 0 0 80px rgba(201,168,76,0.1), inset 0 0 60px rgba(0,0,0,0.5);
    display: flex; align-items: center; justify-content: center;
    position: relative; overflow: hidden;
  }
  .hero-plate::before {
    content: '';
    position: absolute; inset: 12px; border-radius: 50%;
    border: 1px solid var(--gold-border);
  }
  .hero-plate::after {
    content: '';
    position: absolute; inset: 24px; border-radius: 50%;
    border: 1px dashed rgba(201,168,76,0.12);
  }
  .hero-plate-emoji { font-size: clamp(5rem, 10vw, 9rem); filter: drop-shadow(0 8px 24px rgba(0,0,0,0.6)); }

  .hero-content { position: relative; z-index: 1; max-width: 600px; }

  .hero-label {
    display: inline-flex; align-items: center; gap: 10px;
    color: var(--gold); font-size: 0.75rem; font-weight: 700;
    letter-spacing: 4px; text-transform: uppercase; margin-bottom: 1.5rem;
  }
  .hero-label::before, .hero-label::after {
    content: ''; flex: 1; height: 1px; background: var(--gold); min-width: 30px; max-width: 50px;
  }

  .hero-title {
    font-family: var(--serif);
    font-size: clamp(3rem, 7vw, 5.5rem);
    line-height: 1.08;
    margin-bottom: 1.5rem;
    color: var(--white);
  }
  .hero-title .italic { font-style: italic; color: var(--gold); }

  .hero-desc {
    font-size: 1rem; color: var(--text-mid); line-height: 1.8;
    max-width: 460px; margin-bottom: 2.5rem; font-weight: 300;
  }

  .hero-actions { display: flex; gap: 1rem; flex-wrap: wrap; margin-bottom: 3.5rem; }

  .btn-gold {
    background: var(--gold);
    color: var(--black);
    padding: 14px 32px;
    border-radius: 50px;
    font-family: var(--sans);
    font-weight: 700;
    font-size: 0.85rem;
    letter-spacing: 1.5px;
    text-transform: uppercase;
    text-decoration: none;
    border: none; cursor: pointer;
    transition: all 0.25s;
    display: inline-flex; align-items: center; gap: 8px;
  }
  .btn-gold:hover {
    background: var(--gold-light);
    transform: translateY(-2px);
    box-shadow: 0 10px 30px var(--gold-glow);
  }

  .btn-ghost {
    background: transparent;
    color: var(--white);
    padding: 14px 32px;
    border-radius: 50px;
    font-family: var(--sans);
    font-weight: 600;
    font-size: 0.85rem;
    letter-spacing: 1.5px;
    text-transform: uppercase;
    text-decoration: none;
    border: 1.5px solid var(--gold-border);
    transition: all 0.25s;
    display: inline-flex; align-items: center; gap: 8px;
  }
  .btn-ghost:hover { border-color: var(--gold); color: var(--gold); background: var(--gold-pale); }

  .hero-stats { display: flex; gap: 3rem; flex-wrap: wrap; }
  .stat-num {
    font-family: var(--serif); font-size: 2rem; color: var(--gold); line-height: 1;
  }
  .stat-label { font-size: 0.72rem; color: var(--text-dim); letter-spacing: 1.5px; text-transform: uppercase; margin-top: 3px; }

  /* ─── DIVIDER ─── */
  .ornament-divider {
    text-align: center; padding: 0; font-size: 1.3rem;
    color: var(--gold); opacity: 0.5;
    user-select: none; pointer-events: none;
    letter-spacing: 1rem; line-height: 0;
    margin: 0;
  }

  /* ─── SECTION BASE ─── */
  section { padding: 100px 6%; }

  .section-eyebrow {
    display: flex; align-items: center; gap: 12px;
    color: var(--gold); font-size: 0.72rem; font-weight: 700;
    letter-spacing: 4px; text-transform: uppercase; margin-bottom: 1rem;
  }
  .section-eyebrow::before {
    content: ''; display: block;
    width: 30px; height: 1px; background: var(--gold);
  }

  .section-title {
    font-family: var(--serif);
    font-size: clamp(2rem, 5vw, 3.2rem);
    line-height: 1.15; color: var(--white);
    margin-bottom: 0.8rem;
  }
  .section-title .gold { color: var(--gold); }
  .section-title .italic { font-style: italic; }

  .section-sub { font-size: 0.95rem; color: var(--text-mid); line-height: 1.8; font-weight: 300; }

  /* ─── MENU ─── */
  #menu { background: var(--black); }

  .menu-header { text-align: center; margin-bottom: 3.5rem; }
  .menu-header .section-sub { max-width: 480px; margin: 0 auto; }

  .menu-tabs {
    display: flex; justify-content: center; gap: 0;
    margin-bottom: 3rem; border: 1px solid var(--gold-border);
    border-radius: 50px; width: fit-content; margin: 0 auto 3rem;
    overflow: hidden;
  }
  .menu-tab {
    padding: 11px 28px;
    background: transparent;
    border: none; cursor: pointer;
    font-family: var(--sans); font-size: 0.8rem; font-weight: 700;
    letter-spacing: 1.5px; text-transform: uppercase;
    color: var(--text-mid); transition: all 0.25s;
  }
  .menu-tab.active, .menu-tab:hover {
    background: var(--gold); color: var(--black);
  }

  .menu-panel { display: none; }
  .menu-panel.active { display: block; }

  .menu-grid {
    display: grid; grid-template-columns: repeat(2, 1fr); gap: 1.5rem;
    max-width: 900px; margin: 0 auto;
  }

  .menu-item {
    background: var(--black3);
    border: 1px solid var(--black5);
    border-radius: var(--r);
    padding: 1.5rem;
    display: flex; gap: 1rem; align-items: flex-start;
    transition: border-color 0.3s, transform 0.3s;
  }
  .menu-item:hover {
    border-color: var(--gold-border);
    transform: translateY(-3px);
  }

  .menu-item-icon {
    width: 54px; height: 54px; flex-shrink: 0;
    background: var(--gold-pale);
    border: 1px solid var(--gold-border);
    border-radius: 12px;
    display: flex; align-items: center; justify-content: center;
    font-size: 1.5rem;
  }

  .item-name {
    font-family: var(--serif); font-size: 1.05rem; color: var(--white);
    margin-bottom: 4px;
  }
  .item-desc { font-size: 0.78rem; color: var(--text-dim); line-height: 1.6; margin-bottom: 10px; }
  .item-footer { display: flex; align-items: center; justify-content: space-between; }
  .item-price { font-family: var(--serif); font-size: 1.1rem; color: var(--gold); }
  .item-badge {
    font-size: 0.65rem; font-weight: 700; letter-spacing: 1px; text-transform: uppercase;
    padding: 3px 10px; border-radius: 50px;
  }
  .badge-spicy { background: rgba(220,60,40,0.15); color: #e07060; }
  .badge-veg { background: rgba(80,180,80,0.12); color: #70c870; }
  .badge-popular { background: var(--gold-pale); color: var(--gold); border: 1px solid var(--gold-border); }

  /* ─── ABOUT ─── */
  #about { background: var(--black2); }

  .about-inner {
    display: grid; grid-template-columns: 1fr 1fr; gap: 6rem;
    align-items: center; max-width: 1100px; margin: 0 auto;
  }

  .about-visual { position: relative; }

  .about-img-main {
    aspect-ratio: 4/5;
    background: var(--black4);
    border-radius: 20px;
    border: 1px solid var(--gold-border);
    overflow: hidden;
    display: flex; align-items: center; justify-content: center;
    font-size: 7rem;
    position: relative;
  }
  .about-img-main::before {
    content: '';
    position: absolute; inset: 0;
    background: radial-gradient(ellipse at 50% 80%, rgba(201,168,76,0.1) 0%, transparent 60%);
  }

  .about-badge-float {
    position: absolute; bottom: -20px; right: -20px;
    width: 110px; height: 110px; border-radius: 50%;
    background: var(--gold);
    display: flex; flex-direction: column; align-items: center; justify-content: center;
    box-shadow: 0 10px 30px var(--gold-glow);
    font-family: var(--serif); text-align: center; color: var(--black);
  }
  .float-num { font-size: 2rem; line-height: 1; font-weight: 700; }
  .float-text { font-size: 0.55rem; letter-spacing: 1.5px; text-transform: uppercase; font-family: var(--sans); font-weight: 700; }

  .about-text .section-sub { margin-bottom: 1.5rem; }

  .about-highlights { display: grid; grid-template-columns: 1fr 1fr; gap: 1rem; margin: 2rem 0; }
  .highlight {
    background: var(--black4); border: 1px solid var(--black5);
    border-radius: 12px; padding: 1.2rem;
    border-left: 3px solid var(--gold);
    transition: background 0.25s;
  }
  .highlight:hover { background: var(--black5); }
  .highlight-icon { font-size: 1.4rem; margin-bottom: 6px; }
  .highlight-title { font-weight: 700; font-size: 0.88rem; color: var(--white); }
  .highlight-sub { font-size: 0.75rem; color: var(--text-dim); margin-top: 2px; }

  /* ─── GALLERY ─── */
  #gallery { background: var(--black3); }

  .gallery-header { text-align: center; margin-bottom: 3.5rem; }

  .gallery-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-template-rows: auto auto;
    gap: 12px;
    max-width: 1100px; margin: 0 auto;
  }

  .gallery-item {
    border-radius: 14px; overflow: hidden;
    position: relative; cursor: pointer;
    background: var(--black4); border: 1px solid var(--black5);
    transition: transform 0.3s;
  }
  .gallery-item:hover { transform: scale(1.02); }
  .gallery-item.tall { grid-row: span 2; }

  .gallery-inner {
    width: 100%; height: 100%; min-height: 200px;
    display: flex; align-items: center; justify-content: center;
    flex-direction: column; gap: 10px;
    position: relative;
    overflow: hidden;
  }
  .gallery-item.tall .gallery-inner { min-height: 420px; }

  .gallery-bg {
    position: absolute; inset: 0;
    background: radial-gradient(ellipse at 50% 50%, var(--c1, rgba(201,168,76,0.08)) 0%, transparent 70%);
    transition: opacity 0.3s;
  }
  .gallery-item:hover .gallery-bg { opacity: 1.5; }

  .gallery-emoji { font-size: clamp(3rem, 6vw, 5rem); position: relative; z-index: 1; filter: drop-shadow(0 4px 12px rgba(0,0,0,0.5)); }
  .gallery-label {
    font-family: var(--serif); font-size: 0.9rem; color: var(--text-mid);
    position: relative; z-index: 1; letter-spacing: 0.5px;
  }

  .gallery-overlay {
    position: absolute; inset: 0; z-index: 2;
    background: linear-gradient(to top, rgba(201,168,76,0.3) 0%, transparent 50%);
    opacity: 0; transition: opacity 0.3s;
    display: flex; align-items: flex-end; justify-content: center;
    padding-bottom: 1.2rem;
  }
  .gallery-item:hover .gallery-overlay { opacity: 1; }
  .gallery-overlay-text {
    font-size: 0.75rem; font-weight: 700; letter-spacing: 2px;
    text-transform: uppercase; color: var(--black);
    background: var(--gold); padding: 5px 14px; border-radius: 50px;
  }

  /* ─── REVIEWS ─── */
  #reviews { background: var(--black); }

  .reviews-header { text-align: center; margin-bottom: 3.5rem; }

  .reviews-grid {
    display: grid; grid-template-columns: repeat(3, 1fr);
    gap: 1.5rem; max-width: 1100px; margin: 0 auto;
  }

  .review-card {
    background: var(--black3); border: 1px solid var(--black5);
    border-radius: var(--r); padding: 2rem;
    position: relative; overflow: hidden;
    transition: border-color 0.3s, transform 0.3s;
  }
  .review-card:hover { border-color: var(--gold-border); transform: translateY(-5px); }
  .review-card::before {
    content: '';
    position: absolute; top: 0; left: 0; right: 0; height: 2px;
    background: linear-gradient(90deg, transparent, var(--gold), transparent);
    opacity: 0; transition: opacity 0.3s;
  }
  .review-card:hover::before { opacity: 1; }

  .review-quote {
    font-family: var(--serif); font-size: 5rem;
    color: rgba(201,168,76,0.12); line-height: 1;
    margin-bottom: -0.8rem; display: block;
  }

  .review-stars { color: var(--gold); font-size: 0.88rem; letter-spacing: 2px; margin-bottom: 1rem; }

  .review-text {
    font-size: 0.9rem; color: var(--text-mid); line-height: 1.8;
    margin-bottom: 1.8rem; font-style: italic;
  }

  .review-author {
    display: flex; align-items: center; gap: 12px;
    border-top: 1px solid var(--black5); padding-top: 1.2rem;
  }
  .review-avatar {
    width: 44px; height: 44px; border-radius: 50%;
    background: linear-gradient(135deg, var(--black5), var(--gold-pale));
    border: 1.5px solid var(--gold-border);
    display: flex; align-items: center; justify-content: center;
    font-size: 1.1rem; flex-shrink: 0;
  }
  .reviewer-name { font-weight: 700; font-size: 0.9rem; color: var(--white); }
  .reviewer-tag { font-size: 0.72rem; color: var(--text-dim); margin-top: 1px; }

  /* ─── ORDER SECTION ─── */
  #order {
    background: var(--black2);
    text-align: center; padding: 80px 6%;
    position: relative; overflow: hidden;
  }
  #order::before {
    content: '';
    position: absolute; top: -100px; left: 50%; transform: translateX(-50%);
    width: 600px; height: 600px;
    background: radial-gradient(circle, rgba(201,168,76,0.08) 0%, transparent 65%);
    pointer-events: none;
  }

  .order-inner { position: relative; z-index: 1; max-width: 600px; margin: 0 auto; }
  .order-icon { font-size: 3.5rem; margin-bottom: 1.5rem; }
  .order-title { font-family: var(--serif); font-size: clamp(2rem, 5vw, 3rem); margin-bottom: 1rem; }
  .order-desc { color: var(--text-mid); font-size: 0.95rem; line-height: 1.8; margin-bottom: 2.5rem; font-weight: 300; }

  .btn-order-big {
    display: inline-flex; align-items: center; gap: 10px;
    background: var(--gold);
    color: var(--black);
    padding: 16px 40px;
    border-radius: 50px;
    font-family: var(--sans);
    font-weight: 700; font-size: 0.95rem; letter-spacing: 1.5px; text-transform: uppercase;
    text-decoration: none; border: none; cursor: pointer;
    transition: all 0.25s;
    box-shadow: 0 0 30px rgba(201,168,76,0.2);
  }
  .btn-order-big:hover {
    background: var(--gold-light);
    transform: translateY(-3px);
    box-shadow: 0 16px 40px var(--gold-glow);
  }
  .btn-order-big svg { width: 22px; height: 22px; flex-shrink: 0; }

  /* ─── CONTACT ─── */
  #contact { background: var(--black3); }

  .contact-inner {
    display: grid; grid-template-columns: 1fr 1.2fr; gap: 5rem;
    align-items: start; max-width: 1100px; margin: 0 auto;
  }

  .contact-items { display: flex; flex-direction: column; gap: 1.5rem; margin-top: 2rem; }
  .contact-item {
    display: flex; gap: 1rem; align-items: flex-start;
    background: var(--black4); border: 1px solid var(--black5);
    border-radius: 14px; padding: 1.2rem 1.4rem;
    transition: border-color 0.3s;
  }
  .contact-item:hover { border-color: var(--gold-border); }
  .ci-icon {
    width: 44px; height: 44px; flex-shrink: 0;
    background: var(--gold-pale); border: 1px solid var(--gold-border);
    border-radius: 12px; display: flex; align-items: center; justify-content: center;
    font-size: 1.1rem;
  }
  .ci-label { font-size: 0.68rem; font-weight: 700; letter-spacing: 2px; text-transform: uppercase; color: var(--gold); }
  .ci-val { font-size: 0.9rem; color: var(--text-mid); margin-top: 3px; line-height: 1.6; }

  .social-row { display: flex; gap: 12px; margin-top: 2rem; }
  .social-btn {
    width: 42px; height: 42px; border-radius: 50%;
    background: var(--black4); border: 1px solid var(--black5);
    display: flex; align-items: center; justify-content: center;
    font-size: 1.1rem; text-decoration: none;
    transition: all 0.25s;
  }
  .social-btn:hover { background: var(--gold-pale); border-color: var(--gold-border); }

  /* Hours Table */
  .hours-card {
    background: var(--black4); border: 1px solid var(--black5);
    border-radius: 20px; padding: 2.5rem; overflow: hidden; position: relative;
  }
  .hours-card::before {
    content: '';
    position: absolute; top: 0; left: 0; right: 0; height: 3px;
    background: linear-gradient(90deg, var(--gold), var(--gold-light), var(--gold));
  }
  .hours-title {
    font-family: var(--serif); font-size: 1.4rem; color: var(--white);
    margin-bottom: 1.5rem; display: flex; align-items: center; gap: 10px;
  }
  .hours-row {
    display: flex; align-items: center; justify-content: space-between;
    padding: 12px 0; border-bottom: 1px solid var(--black5);
    font-size: 0.88rem;
  }
  .hours-row:last-child { border-bottom: none; }
  .hours-day { color: var(--text-mid); font-weight: 500; }
  .hours-time { color: var(--gold); font-weight: 600; }
  .hours-closed { color: var(--text-dim); }

  .reserve-btn {
    display: flex; align-items: center; justify-content: center; gap: 8px;
    margin-top: 1.8rem;
    background: var(--gold); color: var(--black);
    padding: 13px; border-radius: 50px;
    font-family: var(--sans); font-weight: 700;
    font-size: 0.82rem; letter-spacing: 1.5px; text-transform: uppercase;
    text-decoration: none; transition: all 0.25s;
  }
  .reserve-btn:hover { background: var(--gold-light); box-shadow: 0 8px 24px var(--gold-glow); }

  /* ─── FOOTER ─── */
  footer {
    background: var(--black);
    border-top: 1px solid var(--gold-border);
    padding: 2.5rem 6%;
    display: flex; align-items: center; justify-content: space-between; flex-wrap: wrap; gap: 1rem;
  }
  .footer-logo { font-family: var(--serif); font-size: 1.3rem; color: var(--white); }
  .footer-logo span { color: var(--gold); }
  .footer-links { display: flex; gap: 2rem; }
  .footer-links a { color: var(--text-dim); text-decoration: none; font-size: 0.78rem; letter-spacing: 1.2px; text-transform: uppercase; transition: color 0.2s; }
  .footer-links a:hover { color: var(--gold); }
  .footer-copy { font-size: 0.75rem; color: var(--text-dim); }

  /* ─── ANIMATIONS ─── */
  .reveal { opacity: 0; transform: translateY(28px); transition: opacity 0.7s ease, transform 0.7s ease; }
  .reveal.visible { opacity: 1; transform: none; }
  .reveal-l { opacity: 0; transform: translateX(-28px); transition: opacity 0.7s ease, transform 0.7s ease; }
  .reveal-l.visible { opacity: 1; transform: none; }
  .reveal-r { opacity: 0; transform: translateX(28px); transition: opacity 0.7s ease, transform 0.7s ease; }
  .reveal-r.visible { opacity: 1; transform: none; }

  /* ─── RESPONSIVE ─── */
  @media (max-width: 1024px) {
    .hero-ornament { display: none; }
    .about-inner { grid-template-columns: 1fr; gap: 3rem; }
    .gallery-grid { grid-template-columns: repeat(2, 1fr); }
    .gallery-item.tall { grid-row: span 1; }
    .gallery-item.tall .gallery-inner { min-height: 200px; }
    .reviews-grid { grid-template-columns: 1fr; }
    .contact-inner { grid-template-columns: 1fr; gap: 3rem; }
  }
  @media (max-width: 768px) {
    .nav-links { display: none; }
    .nav-order { display: none; }
    .hamburger { display: flex; }
    section { padding: 80px 6%; }
    .menu-grid { grid-template-columns: 1fr; }
    .gallery-grid { grid-template-columns: 1fr; }
    .about-highlights { grid-template-columns: 1fr 1fr; }
    footer { flex-direction: column; text-align: center; }
    .footer-links { flex-wrap: wrap; justify-content: center; }
  }
  @media (max-width: 480px) {
    .hero-actions { flex-direction: column; }
    .btn-gold, .btn-ghost { text-align: center; width: 100%; justify-content: center; }
    .hero-stats { gap: 1.5rem; }
    .about-highlights { grid-template-columns: 1fr; }
    .menu-tabs { flex-wrap: wrap; border-radius: 14px; }
  }
</style>
</head>
<body>

<!-- NAV -->
<nav id="mainNav">
  <a href="#home" class="logo">Spice<span>Heaven</span></a>
  <ul class="nav-links">
    <li><a href="#menu">Menu</a></li>
    <li><a href="#about">About</a></li>
    <li><a href="#gallery">Gallery</a></li>
    <li><a href="#reviews">Reviews</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
  <a href="https://wa.me/919876543210?text=Hello!%20I%20would%20like%20to%20place%20an%20order%20at%20Spice%20Heaven%20🍛" target="_blank" class="nav-order">🛒 Order Now</a>
  <button class="hamburger" id="hamburger">
    <span></span><span></span><span></span>
  </button>
</nav>

<div class="mobile-menu" id="mobileMenu">
  <a href="#menu" onclick="cm()">Menu</a>
  <a href="#about" onclick="cm()">About</a>
  <a href="#gallery" onclick="cm()">Gallery</a>
  <a href="#reviews" onclick="cm()">Reviews</a>
  <a href="#contact" onclick="cm()">Contact</a>
  <a href="https://wa.me/919876543210?text=Hello!%20I%20would%20like%20to%20place%20an%20order%20at%20Spice%20Heaven%20🍛" target="_blank" style="color:var(--gold)">🛒 Order on WhatsApp</a>
</div>

<!-- HERO -->
<section id="home">
  <div class="hero-bg-pattern"></div>
  <div class="hero-ornament">
    <div class="hero-plate">
      <div class="hero-plate-emoji">🍛</div>
    </div>
  </div>
  <div class="hero-content">
    <div class="hero-label">Est. 2012 · Lucknow</div>
    <h1 class="hero-title">
      Taste the<br>
      <span class="italic">Real Flavor</span>
    </h1>
    <p class="hero-desc">Where every dish tells a story of authentic spices, slow-cooked passion, and memories that linger long after the last bite.</p>
    <div class="hero-actions">
      <a href="https://wa.me/919876543210?text=Hello!%20I%20want%20to%20order%20from%20Spice%20Heaven%20🍛%20Please%20share%20your%20menu." target="_blank" class="btn-gold">🛒 Order Now</a>
      <a href="#menu" class="btn-ghost">View Menu →</a>
    </div>
    <div class="hero-stats">
      <div class="stat-item">
        <div class="stat-num">12+</div>
        <div class="stat-label">Years of Taste</div>
      </div>
      <div class="stat-item">
        <div class="stat-num">80+</div>
        <div class="stat-label">Dishes</div>
      </div>
      <div class="stat-item">
        <div class="stat-num">15K+</div>
        <div class="stat-label">Happy Guests</div>
      </div>
    </div>
  </div>
</section>

<!-- MENU -->
<section id="menu">
  <div class="menu-header reveal">
    <div class="section-eyebrow">Our Menu</div>
    <h2 class="section-title">Crafted with <span class="gold italic">Passion</span></h2>
    <p class="section-sub">From fiery starters to soul-warming mains and divine desserts — every plate is a masterpiece.</p>
  </div>

  <div class="reveal">
    <div class="menu-tabs">
      <button class="menu-tab active" onclick="switchTab('starters', this)">🥗 Starters</button>
      <button class="menu-tab" onclick="switchTab('mains', this)">🍛 Main Course</button>
      <button class="menu-tab" onclick="switchTab('desserts', this)">🍮 Desserts</button>
    </div>
  </div>

  <!-- STARTERS -->
  <div class="menu-panel active reveal" id="tab-starters">
    <div class="menu-grid">
      <div class="menu-item">
        <div class="menu-item-icon">🥟</div>
        <div>
          <div class="item-name">Seekh Kebab</div>
          <div class="item-desc">Minced lamb skewers marinated in aromatic spices, grilled in tandoor to smoky perfection.</div>
          <div class="item-footer">
            <div class="item-price">₹320</div>
            <span class="item-badge badge-spicy">🌶 Spicy</span>
          </div>
        </div>
      </div>
      <div class="menu-item">
        <div class="menu-item-icon">🧅</div>
        <div>
          <div class="item-name">Crispy Onion Bhaji</div>
          <div class="item-desc">Golden-fried onion fritters with chickpea batter, served with mint-coriander chutney.</div>
          <div class="item-footer">
            <div class="item-price">₹180</div>
            <span class="item-badge badge-veg">🌿 Veg</span>
          </div>
        </div>
      </div>
      <div class="menu-item">
        <div class="menu-item-icon">🍗</div>
        <div>
          <div class="item-name">Chicken Tikka</div>
          <div class="item-desc">Boneless chicken marinated in yogurt and spice blend, charred in a clay oven.</div>
          <div class="item-footer">
            <div class="item-price">₹380</div>
            <span class="item-badge badge-popular">⭐ Popular</span>
          </div>
        </div>
      </div>
      <div class="menu-item">
        <div class="menu-item-icon">🥗</div>
        <div>
          <div class="item-name">Paneer Tikka</div>
          <div class="item-desc">Chunky cottage cheese cubes marinated in spiced yogurt, grilled with peppers & onions.</div>
          <div class="item-footer">
            <div class="item-price">₹280</div>
            <span class="item-badge badge-veg">🌿 Veg</span>
          </div>
        </div>
      </div>
    </div>
  </div>

  <!-- MAINS -->
  <div class="menu-panel" id="tab-mains">
    <div class="menu-grid">
      <div class="menu-item">
        <div class="menu-item-icon">🍛</div>
        <div>
          <div class="item-name">Dum Biryani</div>
          <div class="item-desc">Slow-cooked basmati rice with tender mutton, saffron & fried onions — the crown jewel.</div>
          <div class="item-footer">
            <div class="item-price">₹520</div>
            <span class="item-badge badge-popular">⭐ Popular</span>
          </div>
        </div>
      </div>
      <div class="menu-item">
        <div class="menu-item-icon">🥘</div>
        <div>
          <div class="item-name">Butter Chicken</div>
          <div class="item-desc">Tender chicken in silky tomato-cream sauce, slow-simmered with butter and fenugreek.</div>
          <div class="item-footer">
            <div class="item-price">₹440</div>
            <span class="item-badge badge-popular">⭐ Popular</span>
          </div>
        </div>
      </div>
      <div class="menu-item">
        <div class="menu-item-icon">🫕</div>
        <div>
          <div class="item-name">Dal Makhani</div>
          <div class="item-desc">Black lentils slow-cooked overnight with butter, cream and tomatoes. Served with naan.</div>
          <div class="item-footer">
            <div class="item-price">₹280</div>
            <span class="item-badge badge-veg">🌿 Veg</span>
          </div>
        </div>
      </div>
      <div class="menu-item">
        <div class="menu-item-icon">🍖</div>
        <div>
          <div class="item-name">Rogan Josh</div>
          <div class="item-desc">Kashmiri-style braised lamb in deep red gravy of Kashmiri chillies and whole spices.</div>
          <div class="item-footer">
            <div class="item-price">₹580</div>
            <span class="item-badge badge-spicy">🌶 Spicy</span>
          </div>
        </div>
      </div>
    </div>
  </div>

  <!-- DESSERTS -->
  <div class="menu-panel" id="tab-desserts">
    <div class="menu-grid">
      <div class="menu-item">
        <div class="menu-item-icon">🍮</div>
        <div>
          <div class="item-name">Gulab Jamun</div>
          <div class="item-desc">Soft milk-solid dumplings soaked in rose-cardamom syrup, served warm with ice cream.</div>
          <div class="item-footer">
            <div class="item-price">₹160</div>
            <span class="item-badge badge-popular">⭐ Popular</span>
          </div>
        </div>
      </div>
      <div class="menu-item">
        <div class="menu-item-icon">🍨</div>
        <div>
          <div class="item-name">Kulfi Falooda</div>
          <div class="item-desc">Dense pistachio-cardamom kulfi over rose falooda, basil seeds and vermicelli. Divine.</div>
          <div class="item-footer">
            <div class="item-price">₹220</div>
            <span class="item-badge badge-veg">🌿 Veg</span>
          </div>
        </div>
      </div>
      <div class="menu-item">
        <div class="menu-item-icon">🥮</div>
        <div>
          <div class="item-name">Shahi Tukda</div>
          <div class="item-desc">Fried bread soaked in sugar syrup, topped with thickened saffron milk and dry fruits.</div>
          <div class="item-footer">
            <div class="item-price">₹200</div>
            <span class="item-badge badge-popular">⭐ Popular</span>
          </div>
        </div>
      </div>
      <div class="menu-item">
        <div class="menu-item-icon">🍦</div>
        <div>
          <div class="item-name">Phirni</div>
          <div class="item-desc">Creamy ground rice pudding with saffron, cardamom and crushed pistachios, chilled to set.</div>
          <div class="item-footer">
            <div class="item-price">₹180</div>
            <span class="item-badge badge-veg">🌿 Veg</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- ABOUT -->
<section id="about">
  <div class="about-inner">
    <div class="about-visual reveal-l">
      <div class="about-img-main">🧑‍🍳</div>
      <div class="about-badge-float">
        <span class="float-num">12</span>
        <span class="float-text">Years of<br>Flavor</span>
      </div>
    </div>
    <div class="about-text reveal-r">
      <div class="section-eyebrow">Our Story</div>
      <h2 class="section-title">Where Spice Meets <span class="gold italic">Soul</span></h2>
      <p class="section-sub">Spice Heaven was born in 2012 from a grandmother's kitchen and a chef's dream. Head Chef Arjun Khanna spent years mastering the ancient art of Mughlai and Awadhi cooking before opening these doors in Lucknow's heart.</p>
      <p class="section-sub" style="margin-top:1rem;">Every recipe here carries a story — passed down through generations, refined over decades, and served with love. We don't just cook food; we craft experiences that transport you to the royal kitchens of old India.</p>
      <div class="about-highlights">
        <div class="highlight">
          <div class="highlight-icon">🌶</div>
          <div class="highlight-title">Fresh Spices Daily</div>
          <div class="highlight-sub">Whole spices ground every morning</div>
        </div>
        <div class="highlight">
          <div class="highlight-icon">🔥</div>
          <div class="highlight-title">Slow Dum Cooking</div>
          <div class="highlight-sub">Traditional clay oven & dum technique</div>
        </div>
        <div class="highlight">
          <div class="highlight-icon">🌿</div>
          <div class="highlight-title">Farm-Fresh Ingredients</div>
          <div class="highlight-sub">Sourced locally every morning</div>
        </div>
        <div class="highlight">
          <div class="highlight-icon">👨‍🍳</div>
          <div class="highlight-title">Master Chefs</div>
          <div class="highlight-sub">15+ years average experience</div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- GALLERY -->
<section id="gallery">
  <div class="gallery-header reveal">
    <div class="section-eyebrow">Food Gallery</div>
    <h2 class="section-title">A Feast for the <span class="gold italic">Eyes</span></h2>
    <p class="section-sub" style="max-width:420px;margin:0 auto;">Every dish is plated like art. Here's a glimpse of what awaits you.</p>
  </div>
  <div class="gallery-grid reveal">
    <div class="gallery-item tall">
      <div class="gallery-inner" style="background:linear-gradient(160deg,#1c1508,#2a1a06)">
        <div class="gallery-bg" style="--c1:rgba(201,168,76,0.1)"></div>
        <div class="gallery-emoji">🍛</div>
        <div class="gallery-label">Signature Biryani</div>
        <div class="gallery-overlay"><span class="gallery-overlay-text">Fan Favourite</span></div>
      </div>
    </div>
    <div class="gallery-item">
      <div class="gallery-inner" style="background:linear-gradient(160deg,#1a0c0c,#2a1008)">
        <div class="gallery-bg" style="--c1:rgba(200,80,50,0.1)"></div>
        <div class="gallery-emoji">🍗</div>
        <div class="gallery-label">Tandoori Delights</div>
        <div class="gallery-overlay"><span class="gallery-overlay-text">Must Try</span></div>
      </div>
    </div>
    <div class="gallery-item">
      <div class="gallery-inner" style="background:linear-gradient(160deg,#0c1a0c,#0e2010)">
        <div class="gallery-bg" style="--c1:rgba(80,180,80,0.08)"></div>
        <div class="gallery-emoji">🥗</div>
        <div class="gallery-label">Fresh Starters</div>
        <div class="gallery-overlay"><span class="gallery-overlay-text">Light & Fresh</span></div>
      </div>
    </div>
    <div class="gallery-item">
      <div class="gallery-inner" style="background:linear-gradient(160deg,#1a1008,#251806)">
        <div class="gallery-bg" style="--c1:rgba(201,168,76,0.08)"></div>
        <div class="gallery-emoji">🍮</div>
        <div class="gallery-label">Royal Desserts</div>
        <div class="gallery-overlay"><span class="gallery-overlay-text">Save Room!</span></div>
      </div>
    </div>
    <div class="gallery-item">
      <div class="gallery-inner" style="background:linear-gradient(160deg,#180c18,#200e20)">
        <div class="gallery-bg" style="--c1:rgba(180,80,200,0.08)"></div>
        <div class="gallery-emoji">🧆</div>
        <div class="gallery-label">Kebab Platter</div>
        <div class="gallery-overlay"><span class="gallery-overlay-text">Chef's Special</span></div>
      </div>
    </div>
    <div class="gallery-item tall">
      <div class="gallery-inner" style="background:linear-gradient(160deg,#0d1520,#0a1828)">
        <div class="gallery-bg" style="--c1:rgba(80,160,220,0.08)"></div>
        <div class="gallery-emoji">🍽️</div>
        <div class="gallery-label">Full Thali Experience</div>
        <div class="gallery-overlay"><span class="gallery-overlay-text">The Royal Spread</span></div>
      </div>
    </div>
  </div>
</section>

<!-- REVIEWS -->
<section id="reviews">
  <div class="reviews-header reveal">
    <div class="section-eyebrow">Guest Stories</div>
    <h2 class="section-title">What Our <span class="gold italic">Guests</span> Say</h2>
    <p class="section-sub" style="max-width:450px;margin:0 auto;">Real diners, real experiences. The flavor speaks for itself.</p>
  </div>
  <div class="reviews-grid reveal">
    <div class="review-card">
      <span class="review-quote">"</span>
      <div class="review-stars">★★★★★</div>
      <p class="review-text">The Dum Biryani here is not just food — it's an emotion. I've traveled across India trying biryanis, and Spice Heaven's version genuinely ranks in the top three. The aroma alone is worth the visit.</p>
      <div class="review-author">
        <div class="review-avatar">👨</div>
        <div>
          <div class="reviewer-name">Vikram Chaudhary</div>
          <div class="reviewer-tag">Food Blogger · Visited 20+ times</div>
        </div>
      </div>
    </div>
    <div class="review-card">
      <span class="review-quote">"</span>
      <div class="review-stars">★★★★★</div>
      <p class="review-text">Took my entire family here for Eid dinner. The Rogan Josh, Seekh Kebab and Shahi Tukda — everything was absolutely divine. The ambience is royal and the staff so warm. Will keep coming back.</p>
      <div class="review-author">
        <div class="review-avatar">👩</div>
        <div>
          <div class="reviewer-name">Nadia Siddiqui</div>
          <div class="reviewer-tag">Lucknow · Family diner</div>
        </div>
      </div>
    </div>
    <div class="review-card">
      <span class="review-quote">"</span>
      <div class="review-stars">★★★★★</div>
      <p class="review-text">As a chef myself I'm very critical about spice balance. Spice Heaven absolutely nails it. Their Butter Chicken has depth, the dal is slow-cooked exactly right. This kitchen knows its craft. Highly recommend.</p>
      <div class="review-author">
        <div class="review-avatar">👨‍🍳</div>
        <div>
          <div class="reviewer-name">Rohit Bajaj</div>
          <div class="reviewer-tag">Professional Chef · Zomato Reviewer</div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- ORDER CTA -->
<section id="order">
  <div class="order-inner reveal">
    <div class="order-icon">🛒</div>
    <h2 class="order-title">Hungry? <span style="color:var(--gold);font-style:italic;">Order Now</span></h2>
    <p class="order-desc">Fresh, hot food delivered to your doorstep or reserved at your table — just one WhatsApp message away.</p>
    <a href="https://wa.me/919876543210?text=Hello%20Spice%20Heaven!%20🍛%0AI%20would%20like%20to%20place%20an%20order.%0APlease%20share%20today%27s%20specials!" target="_blank" class="btn-order-big">
      <svg viewBox="0 0 24 24" fill="currentColor">
        <path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347z"/>
        <path d="M12 0C5.373 0 0 5.373 0 12c0 2.123.554 4.115 1.523 5.845L0 24l6.32-1.496A11.94 11.94 0 0012 24c6.627 0 12-5.373 12-12S18.627 0 12 0zm0 21.818a9.794 9.794 0 01-5.003-1.374l-.359-.213-3.72.88.927-3.618-.234-.372A9.772 9.772 0 012.182 12C2.182 6.574 6.574 2.182 12 2.182S21.818 6.574 21.818 12 17.426 21.818 12 21.818z"/>
      </svg>
      Order on WhatsApp
    </a>
  </div>
</section>

<!-- CONTACT -->
<section id="contact">
  <div class="contact-inner">
    <div class="reveal-l">
      <div class="section-eyebrow">Find Us</div>
      <h2 class="section-title">Visit <span class="gold italic">Spice Heaven</span></h2>
      <p class="section-sub">Come hungry, leave happy. We're always ready to welcome you.</p>
      <div class="contact-items">
        <div class="contact-item">
          <div class="ci-icon">📍</div>
          <div>
            <div class="ci-label">Address</div>
            <div class="ci-val">45, Aminabad Market, Near Clock Tower<br>Lucknow, Uttar Pradesh – 226018</div>
          </div>
        </div>
        <div class="contact-item">
          <div class="ci-icon">📞</div>
          <div>
            <div class="ci-label">Phone / WhatsApp</div>
            <div class="ci-val">+91 98765 43210<br>+91 05224 78901</div>
          </div>
        </div>
        <div class="contact-item">
          <div class="ci-icon">✉️</div>
          <div>
            <div class="ci-label">Email</div>
            <div class="ci-val">hello@spiceheavenlko.in</div>
          </div>
        </div>
      </div>
      <div class="social-row">
        <a href="#" class="social-btn" title="Instagram">📸</a>
        <a href="#" class="social-btn" title="Facebook">👤</a>
        <a href="https://wa.me/919876543210" target="_blank" class="social-btn" title="WhatsApp">💬</a>
        <a href="#" class="social-btn" title="Zomato">🍽️</a>
      </div>
    </div>
    <div class="reveal-r">
      <div class="hours-card">
        <div class="hours-title">⏰ Opening Hours</div>
        <div class="hours-row">
          <span class="hours-day">Monday – Friday</span>
          <span class="hours-time">11:00 AM – 11:00 PM</span>
        </div>
        <div class="hours-row">
          <span class="hours-day">Saturday</span>
          <span class="hours-time">10:00 AM – 11:30 PM</span>
        </div>
        <div class="hours-row">
          <span class="hours-day">Sunday</span>
          <span class="hours-time">10:00 AM – 12:00 AM</span>
        </div>
        <div class="hours-row">
          <span class="hours-day">Public Holidays</span>
          <span class="hours-time">11:00 AM – 10:00 PM</span>
        </div>
        <a href="https://wa.me/919876543210?text=Hello!%20I%20would%20like%20to%20reserve%20a%20table%20at%20Spice%20Heaven%20🍛" target="_blank" class="reserve-btn">
          🪑 Reserve a Table on WhatsApp
        </a>
      </div>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-logo">Spice<span>Heaven</span></div>
  <div class="footer-links">
    <a href="#menu">Menu</a>
    <a href="#about">About</a>
    <a href="#gallery">Gallery</a>
    <a href="#contact">Contact</a>
  </div>
  <div class="footer-copy">© 2024 Spice Heaven, Lucknow. Made with ❤️ & 🌶</div>
</footer>

<script>
  // ── NAV SCROLL
  const nav = document.getElementById('mainNav');
  window.addEventListener('scroll', () => nav.classList.toggle('scrolled', window.scrollY > 30));

  // ── HAMBURGER
  const hbg = document.getElementById('hamburger');
  const mm = document.getElementById('mobileMenu');
  hbg.addEventListener('click', () => {
    mm.classList.toggle('open');
    const s = hbg.querySelectorAll('span');
    if (mm.classList.contains('open')) {
      s[0].style.transform = 'rotate(45deg) translate(5px,5px)';
      s[1].style.opacity = '0';
      s[2].style.transform = 'rotate(-45deg) translate(5px,-5px)';
    } else {
      s.forEach(x => { x.style.transform = ''; x.style.opacity = ''; });
    }
  });
  function cm() {
    mm.classList.remove('open');
    hbg.querySelectorAll('span').forEach(x => { x.style.transform = ''; x.style.opacity = ''; });
  }

  // ── MENU TABS
  function switchTab(tab, btn) {
    document.querySelectorAll('.menu-panel').forEach(p => p.classList.remove('active'));
    document.querySelectorAll('.menu-tab').forEach(b => b.classList.remove('active'));
    document.getElementById('tab-' + tab).classList.add('active');
    btn.classList.add('active');
  }

  // ── SCROLL REVEAL
  const allReveal = document.querySelectorAll('.reveal, .reveal-l, .reveal-r');
  const obs = new IntersectionObserver(entries => {
    entries.forEach(e => {
      if (e.isIntersecting) { e.target.classList.add('visible'); obs.unobserve(e.target); }
    });
  }, { threshold: 0.08 });
  allReveal.forEach(el => obs.observe(el));
</script>
</body>
</html>
