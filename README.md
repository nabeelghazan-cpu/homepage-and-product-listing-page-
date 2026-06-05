#<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>LUXE — Premium eCommerce</title>
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,600;1,300;1,400&family=DM+Sans:wght@300;400;500;600&display=swap" rel="stylesheet" />

  <style>
    /* ─── CSS Variables ─── */
    :root {
      --cream:    #faf7f2;
      --sand:     #ede8df;
      --tan:      #c9bba8;
      --espresso: #2b1f14;
      --ink:      #1a1410;
      --copper:   #b87a4b;
      --copper-light: #d4956a;
      --white:    #ffffff;
      --gray-mid: #7a6e65;

      --font-display: 'Cormorant Garamond', Georgia, serif;
      --font-body:    'DM Sans', sans-serif;

      --nav-height: 72px;
      --top-bar-height: 36px;
      --transition: 0.28s cubic-bezier(0.4, 0, 0.2, 1);
    }

    /* ─── Reset ─── */
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
    html { scroll-behavior: smooth; }
    body {
      font-family: var(--font-body);
      background: var(--cream);
      color: var(--ink);
      min-height: 100vh;
      display: flex;
      flex-direction: column;
    }
    a { text-decoration: none; color: inherit; }
    ul { list-style: none; }
    button { cursor: pointer; border: none; background: none; font-family: inherit; }
    img { display: block; max-width: 100%; }

    /* ═══════════════════════════════════════
       TOP ANNOUNCEMENT BAR
    ═══════════════════════════════════════ */
    .top-bar {
      background: var(--espresso);
      color: var(--tan);
      height: var(--top-bar-height);
      display: flex;
      align-items: center;
      justify-content: center;
      font-family: var(--font-body);
      font-size: 11.5px;
      font-weight: 500;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      position: relative;
      overflow: hidden;
    }
    .top-bar span { color: var(--copper-light); }
    .top-bar-close {
      position: absolute;
      right: 20px;
      top: 50%;
      transform: translateY(-50%);
      color: var(--tan);
      font-size: 16px;
      opacity: 0.6;
      transition: opacity var(--transition);
      cursor: pointer;
    }
    .top-bar-close:hover { opacity: 1; }

    /* ═══════════════════════════════════════
       MAIN HEADER
    ═══════════════════════════════════════ */
    .header {
      background: var(--cream);
      border-bottom: 1px solid var(--sand);
      position: sticky;
      top: 0;
      z-index: 100;
      transition: box-shadow var(--transition);
    }
    .header.scrolled {
      box-shadow: 0 2px 24px rgba(43, 31, 20, 0.08);
    }

    /* ── Inner wrapper ── */
    .header-inner {
      max-width: 1360px;
      margin: 0 auto;
      padding: 0 40px;
      height: var(--nav-height);
      display: grid;
      grid-template-columns: 1fr auto 1fr;
      align-items: center;
      gap: 24px;
    }

    /* ── Logo ── */
    .logo {
      display: flex;
      align-items: center;
      gap: 10px;
      text-decoration: none;
    }
    .logo-mark {
      width: 34px;
      height: 34px;
      background: var(--espresso);
      display: flex;
      align-items: center;
      justify-content: center;
      position: relative;
    }
    .logo-mark::after {
      content: '';
      position: absolute;
      inset: 4px;
      border: 1px solid var(--copper);
    }
    .logo-mark svg { width: 16px; height: 16px; fill: var(--cream); }
    .logo-text {
      font-family: var(--font-display);
      font-size: 26px;
      font-weight: 600;
      letter-spacing: 0.08em;
      color: var(--espresso);
      line-height: 1;
    }
    .logo-tagline {
      font-size: 8px;
      letter-spacing: 0.2em;
      text-transform: uppercase;
      color: var(--copper);
      font-weight: 500;
      margin-top: 2px;
    }

    /* ── Nav ── */
    .nav {
      display: flex;
      align-items: center;
      gap: 2px;
    }
    .nav-item {
      position: relative;
    }
    .nav-link {
      display: flex;
      align-items: center;
      gap: 4px;
      padding: 8px 16px;
      font-size: 12px;
      font-weight: 500;
      letter-spacing: 0.1em;
      text-transform: uppercase;
      color: var(--espresso);
      transition: color var(--transition);
    }
    .nav-link:hover { color: var(--copper); }
    .nav-link svg { width: 10px; height: 10px; transition: transform var(--transition); }
    .nav-item:hover .nav-link svg { transform: rotate(180deg); }

    /* Dropdown */
    .dropdown {
      position: absolute;
      top: calc(100% + 12px);
      left: 50%;
      transform: translateX(-50%);
      background: var(--white);
      border: 1px solid var(--sand);
      min-width: 200px;
      padding: 8px 0;
      opacity: 0;
      visibility: hidden;
      transform: translateX(-50%) translateY(-8px);
      transition: opacity var(--transition), transform var(--transition), visibility var(--transition);
      box-shadow: 0 8px 40px rgba(43,31,20,0.12);
    }
    .nav-item:hover .dropdown {
      opacity: 1;
      visibility: visible;
      transform: translateX(-50%) translateY(0);
    }
    .dropdown a {
      display: block;
      padding: 10px 20px;
      font-size: 12.5px;
      color: var(--espresso);
      letter-spacing: 0.04em;
      transition: background var(--transition), color var(--transition);
    }
    .dropdown a:hover {
      background: var(--sand);
      color: var(--copper);
    }
    .dropdown-divider {
      height: 1px;
      background: var(--sand);
      margin: 6px 0;
    }

    /* ── Header Actions ── */
    .header-actions {
      display: flex;
      align-items: center;
      justify-content: flex-end;
      gap: 4px;
    }

    .search-bar {
      display: flex;
      align-items: center;
      background: var(--sand);
      border: 1px solid transparent;
      border-radius: 2px;
      padding: 0 12px;
      height: 36px;
      gap: 8px;
      transition: border-color var(--transition), background var(--transition);
      width: 200px;
    }
    .search-bar:focus-within {
      background: var(--white);
      border-color: var(--copper);
    }
    .search-bar svg { width: 15px; height: 15px; color: var(--gray-mid); flex-shrink: 0; }
    .search-bar input {
      border: none;
      background: none;
      outline: none;
      font-family: var(--font-body);
      font-size: 12.5px;
      color: var(--ink);
      width: 100%;
    }
    .search-bar input::placeholder { color: var(--tan); }

    .icon-btn {
      width: 40px;
      height: 40px;
      display: flex;
      align-items: center;
      justify-content: center;
      border-radius: 2px;
      color: var(--espresso);
      transition: background var(--transition), color var(--transition);
      position: relative;
    }
    .icon-btn:hover {
      background: var(--sand);
      color: var(--copper);
    }
    .icon-btn svg { width: 19px; height: 19px; }

    .cart-badge {
      position: absolute;
      top: 6px;
      right: 6px;
      background: var(--copper);
      color: var(--white);
      font-size: 9px;
      font-weight: 600;
      width: 15px;
      height: 15px;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
    }

    /* ═══════════════════════════════════════
       HERO (demo content)
    ═══════════════════════════════════════ */
    .hero {
      flex: 1;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      padding: 100px 40px;
      text-align: center;
      background:
        radial-gradient(ellipse 70% 60% at 50% 40%, rgba(201,187,168,0.25) 0%, transparent 70%),
        var(--cream);
      position: relative;
      overflow: hidden;
    }
    .hero::before {
      content: 'LUXE';
      position: absolute;
      font-family: var(--font-display);
      font-size: 28vw;
      font-weight: 300;
      color: rgba(43,31,20,0.04);
      letter-spacing: -0.04em;
      pointer-events: none;
      line-height: 1;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      white-space: nowrap;
    }
    .hero-label {
      font-size: 11px;
      letter-spacing: 0.22em;
      text-transform: uppercase;
      color: var(--copper);
      font-weight: 500;
      margin-bottom: 20px;
      display: flex;
      align-items: center;
      gap: 12px;
    }
    .hero-label::before,
    .hero-label::after {
      content: '';
      width: 40px;
      height: 1px;
      background: var(--copper);
      opacity: 0.6;
    }
    .hero h1 {
      font-family: var(--font-display);
      font-size: clamp(48px, 6vw, 88px);
      font-weight: 300;
      color: var(--espresso);
      line-height: 1.05;
      letter-spacing: -0.01em;
      margin-bottom: 24px;
    }
    .hero h1 em {
      font-style: italic;
      color: var(--copper);
    }
    .hero p {
      font-size: 15px;
      color: var(--gray-mid);
      max-width: 480px;
      line-height: 1.7;
      margin-bottom: 40px;
    }
    .hero-cta {
      display: flex;
      gap: 16px;
      justify-content: center;
      flex-wrap: wrap;
    }
    .btn-primary {
      background: var(--espresso);
      color: var(--cream);
      padding: 14px 36px;
      font-size: 11.5px;
      font-weight: 500;
      letter-spacing: 0.14em;
      text-transform: uppercase;
      transition: background var(--transition), transform var(--transition);
      display: inline-flex;
      align-items: center;
      gap: 10px;
    }
    .btn-primary:hover {
      background: var(--copper);
      transform: translateY(-1px);
    }
    .btn-outline {
      border: 1.5px solid var(--espresso);
      color: var(--espresso);
      padding: 13px 36px;
      font-size: 11.5px;
      font-weight: 500;
      letter-spacing: 0.14em;
      text-transform: uppercase;
      transition: background var(--transition), color var(--transition);
      display: inline-flex;
      align-items: center;
      gap: 10px;
    }
    .btn-outline:hover {
      background: var(--espresso);
      color: var(--cream);
    }

    /* ═══════════════════════════════════════
       FOOTER
    ═══════════════════════════════════════ */
    .footer {
      background: var(--espresso);
      color: var(--tan);
    }

    /* ── Newsletter strip ── */
    .footer-newsletter {
      background: var(--copper);
      padding: 40px 40px;
    }
    .footer-newsletter-inner {
      max-width: 1360px;
      margin: 0 auto;
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 40px;
      flex-wrap: wrap;
    }
    .newsletter-copy h3 {
      font-family: var(--font-display);
      font-size: 26px;
      font-weight: 400;
      color: var(--white);
      letter-spacing: 0.02em;
    }
    .newsletter-copy p {
      font-size: 13px;
      color: rgba(255,255,255,0.75);
      margin-top: 4px;
    }
    .newsletter-form {
      display: flex;
      gap: 0;
      flex: 0 1 440px;
    }
    .newsletter-form input {
      flex: 1;
      border: none;
      background: rgba(255,255,255,0.18);
      color: var(--white);
      padding: 0 20px;
      height: 48px;
      font-family: var(--font-body);
      font-size: 13px;
      outline: none;
      transition: background var(--transition);
    }
    .newsletter-form input::placeholder { color: rgba(255,255,255,0.55); }
    .newsletter-form input:focus { background: rgba(255,255,255,0.28); }
    .newsletter-form button {
      background: var(--espresso);
      color: var(--cream);
      padding: 0 28px;
      height: 48px;
      font-family: var(--font-body);
      font-size: 11px;
      font-weight: 600;
      letter-spacing: 0.14em;
      text-transform: uppercase;
      transition: background var(--transition);
    }
    .newsletter-form button:hover { background: var(--ink); }

    /* ── Main footer grid ── */
    .footer-main {
      max-width: 1360px;
      margin: 0 auto;
      padding: 64px 40px 48px;
      display: grid;
      grid-template-columns: 2fr 1fr 1fr 1fr 1.2fr;
      gap: 48px;
    }

    /* Brand column */
    .footer-brand .logo-text { color: var(--cream); }
    .footer-brand .logo-mark { background: var(--cream); }
    .footer-brand .logo-mark svg { fill: var(--espresso); }
    .footer-brand .logo-mark::after { border-color: var(--tan); }
    .footer-brand p {
      font-size: 13px;
      line-height: 1.75;
      color: rgba(201,187,168,0.7);
      margin-top: 20px;
      max-width: 280px;
    }

    .social-links {
      display: flex;
      gap: 8px;
      margin-top: 28px;
    }
    .social-link {
      width: 36px;
      height: 36px;
      border: 1px solid rgba(201,187,168,0.25);
      display: flex;
      align-items: center;
      justify-content: center;
      color: var(--tan);
      transition: background var(--transition), border-color var(--transition), color var(--transition);
    }
    .social-link:hover {
      background: var(--copper);
      border-color: var(--copper);
      color: var(--white);
    }
    .social-link svg { width: 15px; height: 15px; }

    /* Link columns */
    .footer-col h4 {
      font-family: var(--font-body);
      font-size: 10px;
      font-weight: 600;
      letter-spacing: 0.2em;
      text-transform: uppercase;
      color: var(--cream);
      margin-bottom: 20px;
    }
    .footer-col ul li { margin-bottom: 10px; }
    .footer-col ul li a {
      font-size: 13px;
      color: rgba(201,187,168,0.65);
      transition: color var(--transition);
    }
    .footer-col ul li a:hover { color: var(--copper-light); }

    /* Contact column */
    .footer-contact-item {
      display: flex;
      gap: 12px;
      margin-bottom: 16px;
      align-items: flex-start;
    }
    .footer-contact-item svg {
      width: 15px;
      height: 15px;
      color: var(--copper);
      flex-shrink: 0;
      margin-top: 1px;
    }
    .footer-contact-item span {
      font-size: 13px;
      color: rgba(201,187,168,0.65);
      line-height: 1.6;
    }

    /* ── Footer bottom bar ── */
    .footer-bottom {
      border-top: 1px solid rgba(201,187,168,0.12);
    }
    .footer-bottom-inner {
      max-width: 1360px;
      margin: 0 auto;
      padding: 20px 40px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 20px;
      flex-wrap: wrap;
    }
    .footer-bottom-left {
      font-size: 12px;
      color: rgba(201,187,168,0.4);
      letter-spacing: 0.04em;
    }
    .footer-bottom-left span { color: var(--copper); }

    .footer-links-row {
      display: flex;
      gap: 24px;
    }
    .footer-links-row a {
      font-size: 11.5px;
      color: rgba(201,187,168,0.4);
      letter-spacing: 0.06em;
      transition: color var(--transition);
    }
    .footer-links-row a:hover { color: var(--tan); }

    .payment-icons {
      display: flex;
      gap: 8px;
      align-items: center;
    }
    .pay-chip {
      background: rgba(255,255,255,0.08);
      border: 1px solid rgba(255,255,255,0.1);
      border-radius: 3px;
      padding: 4px 8px;
      font-size: 10px;
      font-weight: 600;
      letter-spacing: 0.06em;
      color: rgba(255,255,255,0.5);
    }

    /* ═══════════════════════════════════════
       SCROLL ANIMATION
    ═══════════════════════════════════════ */
    @keyframes fadeUp {
      from { opacity: 0; transform: translateY(20px); }
      to   { opacity: 1; transform: translateY(0); }
    }
    .header { animation: fadeUp 0.5s ease both; }
    .hero-label { animation: fadeUp 0.5s 0.15s ease both; }
    .hero h1 { animation: fadeUp 0.5s 0.25s ease both; }
    .hero p { animation: fadeUp 0.5s 0.35s ease both; }
    .hero-cta { animation: fadeUp 0.5s 0.45s ease both; }
  </style>
</head>
<body>

  <!-- ╔════════════════════════════╗
       ║     ANNOUNCEMENT BAR      ║
       ╚════════════════════════════╝ -->
  <div class="top-bar" id="topBar">
    Free worldwide shipping on orders over <span>&nbsp;$150&nbsp;</span> — Use code&nbsp;<span>LUXESHIP</span>
    <span class="top-bar-close" onclick="document.getElementById('topBar').style.display='none'">✕</span>
  </div>

  <!-- ╔════════════════════════════╗
       ║         HEADER             ║
       ╚════════════════════════════╝ -->
  <header class="header" id="mainHeader">
    <div class="header-inner">

      <!-- Logo -->
      <a href="#" class="logo">
        <div class="logo-mark">
          <svg viewBox="0 0 16 16"><path d="M8 2L10 7H15L11 10L13 15L8 12L3 15L5 10L1 7H6Z"/></svg>
        </div>
        <div>
          <div class="logo-text">LUXE</div>
          <div class="logo-tagline">Curated Living</div>
        </div>
      </a>

      <!-- Navigation -->
      <nav class="nav">

        <div class="nav-item">
          <a href="#" class="nav-link">
            New In
            <svg viewBox="0 0 10 10"><path d="M2 3L5 6L8 3" stroke="currentColor" stroke-width="1.5" fill="none" stroke-linecap="round"/></svg>
          </a>
          <div class="dropdown">
            <a href="#">New Arrivals</a>
            <a href="#">Best Sellers</a>
            <a href="#">Editor's Picks</a>
            <div class="dropdown-divider"></div>
            <a href="#">Sale</a>
          </div>
        </div>

        <div class="nav-item">
          <a href="#" class="nav-link">
            Women
            <svg viewBox="0 0 10 10"><path d="M2 3L5 6L8 3" stroke="currentColor" stroke-width="1.5" fill="none" stroke-linecap="round"/></svg>
          </a>
          <div class="dropdown">
            <a href="#">Clothing</a>
            <a href="#">Accessories</a>
            <a href="#">Footwear</a>
            <a href="#">Handbags</a>
            <div class="dropdown-divider"></div>
            <a href="#">Lingerie & Lounge</a>
          </div>
        </div>

        <div class="nav-item">
          <a href="#" class="nav-link">
            Men
            <svg viewBox="0 0 10 10"><path d="M2 3L5 6L8 3" stroke="currentColor" stroke-width="1.5" fill="none" stroke-linecap="round"/></svg>
          </a>
          <div class="dropdown">
            <a href="#">Clothing</a>
            <a href="#">Accessories</a>
            <a href="#">Footwear</a>
            <div class="dropdown-divider"></div>
            <a href="#">Grooming</a>
          </div>
        </div>

        <div class="nav-item">
          <a href="#" class="nav-link">
            Home
            <svg viewBox="0 0 10 10"><path d="M2 3L5 6L8 3" stroke="currentColor" stroke-width="1.5" fill="none" stroke-linecap="round"/></svg>
          </a>
          <div class="dropdown">
            <a href="#">Décor</a>
            <a href="#">Bedding & Bath</a>
            <a href="#">Kitchen</a>
            <a href="#">Candles & Fragrance</a>
          </div>
        </div>

        <div class="nav-item">
          <a href="#" class="nav-link">Brands</a>
        </div>

        <div class="nav-item">
          <a href="#" class="nav-link" style="color:var(--copper);">Sale</a>
        </div>

      </nav>

      <!-- Actions -->
      <div class="header-actions">

        <div class="search-bar">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
            <circle cx="11" cy="11" r="7"/><path d="M21 21l-4.35-4.35"/>
          </svg>
          <input type="text" placeholder="Search products…" />
        </div>

        <button class="icon-btn" title="Account">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8">
            <circle cx="12" cy="7" r="4"/><path d="M4 21c0-4 3.6-7 8-7s8 3 8 7"/>
          </svg>
        </button>

        <button class="icon-btn" title="Wishlist">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8">
            <path d="M20.84 4.61a5.5 5.5 0 0 0-7.78 0L12 5.67l-1.06-1.06a5.5 5.5 0 0 0-7.78 7.78l1.06 1.06L12 21.23l7.78-7.78 1.06-1.06a5.5 5.5 0 0 0 0-7.78z"/>
          </svg>
        </button>

        <button class="icon-btn" title="Cart">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8">
            <path d="M6 2L3 6v14a2 2 0 0 0 2 2h14a2 2 0 0 0 2-2V6l-3-4z"/><line x1="3" y1="6" x2="21" y2="6"/><path d="M16 10a4 4 0 0 1-8 0"/>
          </svg>
          <span class="cart-badge">3</span>
        </button>

      </div>
    </div>
  </header>

  <!-- ╔════════════════════════════╗
       ║   HERO (placeholder body)  ║
       ╚════════════════════════════╝ -->
  <main class="hero">
    <p class="hero-label">New Collection · SS 2026</p>
    <h1>Dress in <em>quiet</em><br>luxury.</h1>
    <p>Carefully sourced, mindfully made. Discover pieces that speak softly but stay with you forever.</p>
    <div class="hero-cta">
      <a href="#" class="btn-primary">
        Shop Collection
        <svg width="14" height="14" viewBox="0 0 14 14" fill="none"><path d="M2 7H12M8 3l4 4-4 4" stroke="currentColor" stroke-width="1.6" stroke-linecap="round" stroke-linejoin="round"/></svg>
      </a>
      <a href="#" class="btn-outline">Explore Brands</a>
    </div>
  </main>

  <!-- ╔════════════════════════════╗
       ║          FOOTER            ║
       ╚════════════════════════════╝ -->
  <footer class="footer">

    <!-- Newsletter strip -->
    <div class="footer-newsletter">
      <div class="footer-newsletter-inner">
        <div class="newsletter-copy">
          <h3>Join the inner circle.</h3>
          <p>Early access, exclusive offers, and style notes — delivered to your inbox.</p>
        </div>
        <div class="newsletter-form">
          <input type="email" placeholder="Your email address" />
          <button type="button">Subscribe</button>
        </div>
      </div>
    </div>

    <!-- Main grid -->
    <div class="footer-main">

      <!-- Brand -->
      <div class="footer-brand">
        <a href="#" class="logo">
          <div class="logo-mark">
            <svg viewBox="0 0 16 16"><path d="M8 2L10 7H15L11 10L13 15L8 12L3 15L5 10L1 7H6Z"/></svg>
          </div>
          <div>
            <div class="logo-text">LUXE</div>
            <div class="logo-tagline" style="color:var(--tan)">Curated Living</div>
          </div>
        </a>
        <p>We believe beauty is in the details — hand-selected pieces from independent designers and heritage houses around the world.</p>
        <div class="social-links">
          <!-- Instagram -->
          <a href="#" class="social-link" title="Instagram">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8"><rect x="2" y="2" width="20" height="20" rx="5"/><circle cx="12" cy="12" r="5"/><circle cx="17.5" cy="6.5" r="1.2" fill="currentColor" stroke="none"/></svg>
          </a>
          <!-- Pinterest -->
          <a href="#" class="social-link" title="Pinterest">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8"><path d="M12 2C6.48 2 2 6.48 2 12c0 4.24 2.65 7.86 6.39 9.29-.09-.78-.17-1.98.03-2.83.19-.77 1.26-5.33 1.26-5.33s-.32-.64-.32-1.59c0-1.49.86-2.6 1.93-2.6.91 0 1.35.68 1.35 1.5 0 .91-.58 2.28-.88 3.55-.25 1.06.53 1.92 1.57 1.92 1.88 0 3.14-2.42 3.14-5.28 0-2.18-1.46-3.82-4.1-3.82-3 0-4.86 2.24-4.86 4.74 0 .86.25 1.47.64 1.94.18.21.21.29.14.54-.05.17-.16.59-.2.76-.06.25-.25.34-.46.24-1.32-.54-1.93-1.99-1.93-3.61 0-2.67 2.25-5.88 6.72-5.88 3.61 0 5.97 2.62 5.97 5.44 0 3.73-2.07 6.53-5.11 6.53-1.02 0-1.99-.55-2.32-1.18l-.63 2.43c-.23.87-.84 1.95-1.24 2.61.94.29 1.93.44 2.96.44 5.52 0 10-4.48 10-10S17.52 2 12 2z"/></svg>
          </a>
          <!-- Twitter/X -->
          <a href="#" class="social-link" title="X / Twitter">
            <svg viewBox="0 0 24 24" fill="currentColor"><path d="M18.244 2.25h3.308l-7.227 8.26 8.502 11.24H16.17l-4.714-6.231-5.401 6.231H2.744l7.73-8.835L2.396 2.25h6.978l4.265 5.64zm-1.161 17.52h1.833L7.084 4.126H5.117z"/></svg>
          </a>
          <!-- Facebook -->
          <a href="#" class="social-link" title="Facebook">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8"><path d="M18 2h-3a4 4 0 0 0-4 4v3H8v4h3v8h4v-8h3l1-4h-4V6a1 1 0 0 1 1-1h3z"/></svg>
          </a>
          <!-- YouTube -->
          <a href="#" class="social-link" title="YouTube">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8"><rect x="2" y="6" width="20" height="13" rx="2"/><polygon fill="currentColor" stroke="none" points="10,9.5 16,12.5 10,15.5"/></svg>
          </a>
        </div>
      </div>

      <!-- Shop -->
      <div class="footer-col">
        <h4>Shop</h4>
        <ul>
          <li><a href="#">New Arrivals</a></li>
          <li><a href="#">Women</a></li>
          <li><a href="#">Men</a></li>
          <li><a href="#">Home & Living</a></li>
          <li><a href="#">Gift Cards</a></li>
          <li><a href="#">Sale</a></li>
        </ul>
      </div>

      <!-- Help -->
      <div class="footer-col">
        <h4>Help</h4>
        <ul>
          <li><a href="#">FAQs</a></li>
          <li><a href="#">Shipping & Returns</a></li>
          <li><a href="#">Size Guide</a></li>
          <li><a href="#">Order Tracking</a></li>
          <li><a href="#">Payment Options</a></li>
          <li><a href="#">Contact Us</a></li>
        </ul>
      </div>

      <!-- Company -->
      <div class="footer-col">
        <h4>Company</h4>
        <ul>
          <li><a href="#">About Us</a></li>
          <li><a href="#">Sustainability</a></li>
          <li><a href="#">Careers</a></li>
          <li><a href="#">Press</a></li>
          <li><a href="#">Affiliates</a></li>
          <li><a href="#">Brand Partners</a></li>
        </ul>
      </div>

      <!-- Contact -->
      <div class="footer-col">
        <h4>Contact</h4>
        <div class="footer-contact-item">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8"><path d="M21 10c0 7-9 13-9 13S3 17 3 10a9 9 0 0 1 18 0z"/><circle cx="12" cy="10" r="3"/></svg>
          <span>14 Rue du Faubourg<br>Saint-Honoré, Paris 75008</span>
        </div>
        <div class="footer-contact-item">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8"><path d="M22 16.92v3a2 2 0 0 1-2.18 2A19.79 19.79 0 0 1 11.41 18a19.5 19.5 0 0 1-6-6 19.79 19.79 0 0 1-3.9-8.37A2 2 0 0 1 3.47 2h3a2 2 0 0 1 2 1.72c.127.96.361 1.903.7 2.81a2 2 0 0 1-.45 2.11L7.91 9.91a16 16 0 0 0 6 6l.92-.83a2 2 0 0 1 2.11-.45c.907.339 1.85.573 2.81.7A2 2 0 0 1 21.73 17z"/></svg>
          <span>+1 (800) 589-2210</span>
        </div>
        <div class="footer-contact-item">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8"><path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/><polyline points="22,6 12,13 2,6"/></svg>
          <span>hello@luxe-store.com</span>
        </div>
        <div class="footer-contact-item">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8"><circle cx="12" cy="12" r="10"/><polyline points="12 6 12 12 16 14"/></svg>
          <span>Mon – Fri: 9am – 6pm CET<br>Sat: 10am – 4pm CET</span>
        </div>
      </div>

    </div><!-- /footer-main -->

    <!-- Bottom bar -->
    <div class="footer-bottom">
      <div class="footer-bottom-inner">
        <p class="footer-bottom-left">© 2026 <span>LUXE</span>. All rights reserved.</p>
        <div class="footer-links-row">
          <a href="#">Privacy Policy</a>
          <a href="#">Terms of Service</a>
          <a href="#">Cookie Settings</a>
          <a href="#">Accessibility</a>
        </div>
        <div class="payment-icons">
          <span class="pay-chip">VISA</span>
          <span class="pay-chip">MC</span>
          <span class="pay-chip">AMEX</span>
          <span class="pay-chip">PAYPAL</span>
          <span class="pay-chip">APPLE PAY</span>
        </div>
      </div>
    </div>

  </footer>

  <script>
    // Sticky header shadow on scroll
    const header = document.getElementById('mainHeader');
    window.addEventListener('scroll', () => {
      header.classList.toggle('scrolled', window.scrollY > 10);
    });
  </script>

</body>
</html>
 homepage-and-product-listing-page-