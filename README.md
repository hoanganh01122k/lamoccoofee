[lamo-coffee.html](https://github.com/user-attachments/files/26904050/lamo-coffee.html)
<!DOCTYPE html>
<html lang="vi">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Là Mơ Coffee — Hương Vị Trong Giấc Mơ</title>
  <meta name="description" content="Là Mơ Coffee — Nơi mỗi tách cà phê là một giấc mơ nhỏ. Thực đơn phong phú, không gian ấm áp, giao hàng tận nơi." />

  <!-- Bootstrap 5.3 -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/bootstrap/5.3.8/css/bootstrap.min.css" />
  <!-- Bootstrap Icons -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/bootstrap-icons/1.11.3/font/bootstrap-icons.min.css" />
  <!-- AOS -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/aos/2.3.4/aos.css" />
  <!-- Google Fonts -->
  <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,700;0,900;1,400;1,700&family=Cormorant+Garamond:ital,wght@0,300;0,400;0,600;1,300;1,400&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet" />

  <style>
    /* ===== VARIABLES ===== */
    :root {
      --cream:       #F5EFE0;
      --ivory:       #FBF7EE;
      --espresso:    #2C1A0E;
      --dark-roast:  #3D2314;
      --medium-roast:#7B4A2A;
      --caramel:     #B5651D;
      --gold:        #D4A847;
      --latte:       #C8A882;
      --mist:        #EDE0CC;
      --blush:       #F0E6D8;
      --white:       #FFFFFF;
      --font-display:'Playfair Display', Georgia, serif;
      --font-body:   'DM Sans', sans-serif;
      --font-accent: 'Cormorant Garamond', Georgia, serif;
      --nav-h:       80px;
      --tr:          cubic-bezier(0.4, 0, 0.2, 1);
    }

    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
    html { scroll-behavior: smooth; overflow-x: hidden; }
    body {
      background: var(--ivory);
      color: var(--espresso);
      font-family: var(--font-body);
      font-size: 16px;
      line-height: 1.7;
      overflow-x: hidden;
    }

    /* ===== NOISE TEXTURE ===== */
    body::before {
      content: '';
      position: fixed; inset: 0;
      background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.035'/%3E%3C/svg%3E");
      pointer-events: none;
      z-index: 9990;
      opacity: 0.6;
    }

    /* ===== CUSTOM CURSOR ===== */
    .cursor-dot {
      width: 8px; height: 8px;
      background: var(--caramel); border-radius: 50%;
      position: fixed; pointer-events: none; z-index: 9999;
      transform: translate(-50%, -50%);
    }
    .cursor-ring {
      width: 36px; height: 36px;
      border: 1.5px solid var(--caramel); border-radius: 50%;
      position: fixed; pointer-events: none; z-index: 9998;
      transform: translate(-50%, -50%);
      transition: width .25s var(--tr), height .25s var(--tr), background .25s, transform .12s;
      opacity: .7;
    }
    .cursor-ring.hovered { width: 56px; height: 56px; background: rgba(181,101,29,.12); opacity: 1; }
    body:not(.desktop) .cursor-dot, body:not(.desktop) .cursor-ring { display: none; }

    /* ===== PAGE LOADER ===== */
    #page-loader {
      position: fixed; inset: 0;
      background: var(--espresso);
      z-index: 99999;
      display: flex; align-items: center; justify-content: center; flex-direction: column;
      transition: opacity .6s, visibility .6s;
    }
    #page-loader.done { opacity: 0; visibility: hidden; }
    .loader-brand {
      font-family: var(--font-display);
      font-size: 2.4rem; font-weight: 900;
      color: var(--cream); margin-bottom: 8px; letter-spacing: -1px;
    }
    .loader-brand span { color: var(--gold); font-style: italic; }
    .loader-tagline {
      font-family: var(--font-accent); font-style: italic;
      font-size: 1rem; color: var(--latte); margin-bottom: 28px;
    }
    .loader-bar-wrap { width: 200px; height: 2px; background: rgba(245,239,224,.15); }
    .loader-bar { height: 100%; width: 0; background: var(--caramel); animation: loadBar 1.5s ease forwards; }
    @keyframes loadBar { from{width:0} to{width:100%} }

    /* ===== NAVBAR ===== */
    .navbar-custom {
      height: var(--nav-h);
      background: transparent;
      transition: background .5s, box-shadow .5s, height .4s;
      z-index: 1000;
    }
    .navbar-custom.scrolled {
      background: rgba(44,26,14,.96);
      backdrop-filter: blur(14px);
      box-shadow: 0 2px 30px rgba(0,0,0,.22);
      height: 68px;
    }
    .navbar-brand-text {
      font-family: var(--font-display);
      font-size: 1.45rem; font-weight: 700;
      color: var(--cream) !important; letter-spacing: .5px;
    }
    .navbar-brand-text em { color: var(--gold); font-style: italic; }
    .nav-link-custom {
      font-family: var(--font-body); font-size: .8rem; font-weight: 500;
      color: rgba(245,239,224,.85) !important; text-transform: uppercase;
      letter-spacing: 1.5px; padding: 6px 0 !important; margin: 0 14px;
      position: relative; transition: color .3s;
    }
    .nav-link-custom::after {
      content: ''; position: absolute; bottom: 0; left: 0;
      width: 0; height: 1.5px; background: var(--gold);
      transition: width .35s var(--tr);
    }
    .nav-link-custom:hover { color: var(--gold) !important; }
    .nav-link-custom:hover::after { width: 100%; }
    .navbar-toggler { border: none !important; }
    .navbar-toggler:focus { box-shadow: none !important; }

    /* ===== HERO ===== */
    #hero {
      height: 100vh; min-height: 640px;
      position: relative; display: flex; align-items: center; justify-content: center;
      overflow: hidden;
    }
    .hero-bg {
      position: absolute; inset: 0;
      background:
        linear-gradient(160deg, rgba(44,26,14,.75) 0%, rgba(61,35,20,.52) 50%, rgba(44,26,14,.85) 100%),
        url('https://images.unsplash.com/photo-1495474472287-4d71bcdd2085?w=1800&q=80') center/cover no-repeat;
      transform: scale(1.08); will-change: transform;
    }
    .hero-content { position: relative; z-index: 2; text-align: center; padding: 0 16px; }
    .hero-eyebrow {
      font-family: var(--font-accent); font-size: 1rem; font-style: italic;
      color: var(--gold); letter-spacing: 4px; display: block; margin-bottom: 1rem;
      opacity: 0; transform: translateY(20px); animation: fadeUp .9s .4s forwards;
    }
    .hero-title {
      font-family: var(--font-display);
      font-size: clamp(3rem, 8vw, 6rem); font-weight: 900;
      color: var(--cream); line-height: 1.08; margin-bottom: 1.4rem;
      opacity: 0; transform: translateY(30px); animation: fadeUp 1s .65s forwards;
    }
    .hero-title em { color: var(--gold); font-style: italic; }
    .hero-subtitle {
      font-family: var(--font-accent); font-size: clamp(1rem,2vw,1.3rem);
      color: rgba(245,239,224,.78); max-width: 500px; margin: 0 auto 2.4rem;
      opacity: 0; transform: translateY(20px); animation: fadeUp .9s .9s forwards;
    }
    .hero-cta { opacity: 0; transform: translateY(16px); animation: fadeUp .8s 1.1s forwards; }

    /* ===== BUTTONS ===== */
    .btn-coffee {
      background: var(--caramel); color: var(--cream); border: none;
      font-family: var(--font-body); font-size: .82rem; font-weight: 500;
      text-transform: uppercase; letter-spacing: 2px; padding: 14px 36px;
      border-radius: 0; position: relative; overflow: hidden;
      transition: color .35s, transform .2s;
    }
    .btn-coffee::before {
      content: ''; position: absolute; inset: 0;
      background: var(--espresso); transform: translateX(-101%);
      transition: transform .38s var(--tr); z-index: 0;
    }
    .btn-coffee:hover { color: var(--cream); transform: translateY(-2px); }
    .btn-coffee:hover::before { transform: translateX(0); }
    .btn-coffee span { position: relative; z-index: 1; }
    .btn-outline-coffee {
      background: transparent; color: var(--cream);
      border: 1.5px solid rgba(245,239,224,.5);
      font-family: var(--font-body); font-size: .82rem; font-weight: 500;
      text-transform: uppercase; letter-spacing: 2px; padding: 13px 36px;
      border-radius: 0; transition: all .35s;
    }
    .btn-outline-coffee:hover { background: rgba(245,239,224,.1); border-color: var(--cream); color: var(--cream); }

    /* ===== SCROLL INDICATOR ===== */
    .scroll-indicator {
      position: absolute; bottom: 2.5rem; left: 50%; transform: translateX(-50%);
      display: flex; flex-direction: column; align-items: center; gap: 6px;
      cursor: pointer; z-index: 2;
      opacity: 0; animation: fadeUp .8s 1.5s forwards;
    }
    .scroll-indicator span { font-size: .7rem; letter-spacing: 3px; text-transform: uppercase; color: rgba(245,239,224,.55); }
    .scroll-line { width: 1px; height: 50px; background: linear-gradient(to bottom, rgba(245,239,224,.5), transparent); animation: scrollPulse 2s infinite; }
    @keyframes scrollPulse { 0%,100%{opacity:.4; transform:scaleY(1)} 50%{opacity:1; transform:scaleY(1.15)} }

    /* ===== TICKER ===== */
    .ticker-strip { background: var(--espresso); padding: 12px 0; overflow: hidden; white-space: nowrap; }
    .ticker-inner { display: inline-flex; animation: ticker 30s linear infinite; }
    .ticker-inner:hover { animation-play-state: paused; }
    .ticker-item { font-family: var(--font-accent); font-size: .9rem; font-style: italic; color: var(--latte); padding: 0 3rem; display: flex; align-items: center; gap: 1.5rem; }
    .ticker-dot { color: var(--gold); font-size: .5rem; }
    @keyframes ticker { from{transform:translateX(0)} to{transform:translateX(-50%)} }

    /* ===== SECTION COMMONS ===== */
    section { position: relative; }
    .section-eyebrow { font-family: var(--font-accent); font-style: italic; font-size: .92rem; color: var(--caramel); letter-spacing: 3px; text-transform: uppercase; display: block; margin-bottom: .6rem; }
    .section-title { font-family: var(--font-display); font-size: clamp(2rem,4.5vw,3.2rem); font-weight: 900; line-height: 1.15; color: var(--espresso); }
    .section-title.light { color: var(--cream); }
    .divider-gold { width: 48px; height: 2px; background: var(--gold); margin: 1.2rem auto 0; display: block; }
    .divider-gold.left { margin-left: 0; }

    /* ===== ABOUT ===== */
    #about { padding: 120px 0; background: var(--ivory); }
    .about-img-wrap { position: relative; border-radius: 2px; overflow: hidden; box-shadow: 24px 24px 0 var(--mist); }
    .about-img-wrap img { width: 100%; height: 480px; object-fit: cover; display: block; transition: transform .7s var(--tr); }
    .about-img-wrap:hover img { transform: scale(1.04); }
    .about-badge {
      position: absolute; bottom: -20px; right: -20px;
      width: 110px; height: 110px; background: var(--caramel); border-radius: 50%;
      display: flex; flex-direction: column; align-items: center; justify-content: center;
      color: var(--cream); box-shadow: 0 8px 24px rgba(181,101,29,.35);
      animation: rotateBadge 18s linear infinite;
    }
    .about-badge-inner { font-family: var(--font-display); font-size: 1.6rem; font-weight: 900; line-height: 1; }
    .about-badge-label { font-size: .6rem; text-transform: uppercase; letter-spacing: 1.5px; opacity: .85; }
    @keyframes rotateBadge { from{transform:rotate(0deg)} to{transform:rotate(360deg)} }
    .about-text { padding-left: clamp(0px,4vw,48px); }
    .about-text p { font-family: var(--font-accent); font-size: 1.1rem; color: var(--dark-roast); margin-bottom: 1.4rem; }
    .stat-card { padding: 24px 20px; border-left: 2px solid var(--caramel); background: var(--cream); transition: transform .3s, box-shadow .3s; }
    .stat-card:hover { transform: translateY(-4px); box-shadow: 0 12px 28px rgba(44,26,14,.1); }
    .stat-num { font-family: var(--font-display); font-size: 2.4rem; font-weight: 900; color: var(--caramel); line-height: 1; }
    .stat-label { font-size: .78rem; text-transform: uppercase; letter-spacing: 2px; color: var(--medium-roast); margin-top: 4px; }

    /* ===== PROMO BANNER ===== */
    #promo {
      padding: 80px 0;
      background: linear-gradient(135deg, var(--caramel) 0%, #8B4513 100%);
      position: relative; overflow: hidden;
    }
    #promo::before {
      content: '';
      position: absolute; inset: 0;
      background: repeating-linear-gradient(-45deg, transparent 0, transparent 12px, rgba(255,255,255,.04) 12px, rgba(255,255,255,.04) 13px);
    }
    .promo-card {
      background: rgba(255,255,255,.1);
      border: 1px solid rgba(255,255,255,.18);
      border-radius: 4px; padding: 32px 28px;
      text-align: center; color: var(--cream);
      transition: transform .35s, background .35s;
    }
    .promo-card:hover { transform: translateY(-6px); background: rgba(255,255,255,.18); }
    .promo-icon { font-size: 2.5rem; margin-bottom: 16px; display: block; }
    .promo-title { font-family: var(--font-display); font-size: 1.5rem; font-weight: 700; margin-bottom: 8px; }
    .promo-desc { font-family: var(--font-accent); font-style: italic; font-size: .95rem; opacity: .82; }
    .promo-badge {
      display: inline-block; background: var(--espresso); color: var(--gold);
      font-size: .72rem; font-weight: 700; letter-spacing: 2px; text-transform: uppercase;
      padding: 5px 14px; margin-top: 12px; border-radius: 2px;
    }

    /* ===== MENU ===== */
    #menu { padding: 120px 0; background: var(--espresso); position: relative; }
    #menu::before {
      content: ''; position: absolute; inset: 0;
      background: radial-gradient(ellipse 80% 60% at 20% 50%, rgba(181,101,29,.12) 0%, transparent 70%),
                  radial-gradient(ellipse 60% 80% at 80% 30%, rgba(212,168,71,.08) 0%, transparent 70%);
    }
    .menu-tabs {
      display: flex; justify-content: center; flex-wrap: wrap;
      margin-bottom: 3rem; border-bottom: 1px solid rgba(245,239,224,.12);
    }
    .menu-tab-btn {
      background: none; border: none; font-family: var(--font-body);
      font-size: .78rem; font-weight: 500; text-transform: uppercase; letter-spacing: 2px;
      color: rgba(245,239,224,.45); padding: 12px 28px; cursor: pointer; position: relative; transition: color .3s;
    }
    .menu-tab-btn::after { content: ''; position: absolute; bottom: -1px; left: 0; width: 0; height: 2px; background: var(--gold); transition: width .35s var(--tr); }
    .menu-tab-btn.active, .menu-tab-btn:hover { color: var(--cream); }
    .menu-tab-btn.active::after, .menu-tab-btn:hover::after { width: 100%; }
    .menu-panel { display: none; }
    .menu-panel.active { display: block; }
    .menu-card {
      background: rgba(245,239,224,.04); border: 1px solid rgba(245,239,224,.08);
      border-radius: 2px; overflow: hidden;
      transition: transform .4s var(--tr), box-shadow .4s, border-color .3s; cursor: pointer;
    }
    .menu-card:hover { transform: translateY(-8px); box-shadow: 0 20px 48px rgba(0,0,0,.35); border-color: rgba(212,168,71,.3); }
    .menu-card-img-wrap { overflow: hidden; position: relative; height: 220px; }
    .menu-card-img-wrap img { width: 100%; height: 100%; object-fit: cover; transition: transform .6s var(--tr); }
    .menu-card:hover .menu-card-img-wrap img { transform: scale(1.08); }
    .menu-card-badge { position: absolute; top: 12px; left: 12px; background: var(--caramel); color: var(--cream); font-size: .65rem; font-weight: 500; letter-spacing: 1.5px; text-transform: uppercase; padding: 4px 10px; }
    .menu-card-body { padding: 20px 22px 24px; }
    .menu-card-name { font-family: var(--font-display); font-size: 1.15rem; font-weight: 700; color: var(--cream); margin-bottom: 6px; }
    .menu-card-desc { font-family: var(--font-accent); font-style: italic; font-size: .88rem; color: rgba(245,239,224,.55); line-height: 1.5; margin-bottom: 16px; }
    .menu-card-footer { display: flex; align-items: center; justify-content: space-between; }
    .menu-card-price { font-family: var(--font-display); font-size: 1.1rem; font-weight: 700; color: var(--gold); }
    .btn-add {
      width: 36px; height: 36px; border-radius: 50%; border: 1.5px solid var(--caramel);
      background: none; color: var(--caramel); font-size: 1.1rem;
      display: flex; align-items: center; justify-content: center;
      cursor: pointer; transition: background .3s, color .3s, transform .3s;
    }
    .btn-add:hover { background: var(--caramel); color: var(--cream); transform: rotate(90deg); }

    /* ===== COLLECTION SECTION (from 1234.html) ===== */
    #collection { padding: 100px 0; background: var(--blush); }
    .collection-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(260px, 1fr)); gap: 24px; }
    .coll-card {
      background: var(--white); border-radius: 4px; overflow: hidden;
      box-shadow: 0 4px 20px rgba(44,26,14,.07);
      transition: transform .35s var(--tr), box-shadow .35s;
    }
    .coll-card:hover { transform: translateY(-8px); box-shadow: 0 20px 40px rgba(44,26,14,.14); }
    .coll-card-img { position: relative; overflow: hidden; height: 260px; }
    .coll-card-img img { width: 100%; height: 100%; object-fit: cover; transition: transform .6s var(--tr); }
    .coll-card:hover .coll-card-img img { transform: scale(1.07); }
    .coll-badge {
      position: absolute; top: 12px; right: 12px;
      background: var(--caramel); color: var(--cream);
      font-size: .65rem; font-weight: 600; letter-spacing: 1.5px;
      text-transform: uppercase; padding: 4px 12px; border-radius: 2px;
    }
    .coll-body { padding: 18px 20px 22px; }
    .coll-name { font-family: var(--font-display); font-size: 1.05rem; font-weight: 700; color: var(--espresso); margin-bottom: 4px; }
    .coll-price { font-family: var(--font-display); font-size: 1rem; font-weight: 700; color: var(--caramel); }
    .coll-price-old { font-size: .82rem; color: #aaa; text-decoration: line-through; margin-left: 6px; }
    .btn-order {
      display: block; width: 100%; margin-top: 14px;
      background: var(--espresso); color: var(--cream); border: none;
      font-family: var(--font-body); font-size: .78rem; font-weight: 500;
      text-transform: uppercase; letter-spacing: 2px; padding: 12px 0;
      border-radius: 0; cursor: pointer;
      transition: background .3s, transform .2s;
    }
    .btn-order:hover { background: var(--caramel); transform: translateY(-2px); }

    /* ===== STORY SPLIT ===== */
    #story {
      display: grid; grid-template-columns: 1fr 1fr;
      min-height: 520px;
    }
    .story-visual { position: relative; overflow: hidden; }
    .story-visual img { width: 100%; height: 100%; object-fit: cover; display: block; transition: transform .7s var(--tr); }
    .story-visual:hover img { transform: scale(1.04); }
    .story-visual-overlay { position: absolute; inset: 0; background: linear-gradient(to right, rgba(44,26,14,.2), transparent); }
    .story-text-panel {
      background: var(--espresso); padding: 80px 64px;
      display: flex; flex-direction: column; justify-content: center;
    }
    blockquote {
      font-family: var(--font-display); font-style: italic;
      font-size: clamp(1.3rem,2.5vw,1.9rem); font-weight: 700;
      color: var(--cream); line-height: 1.45;
      border-left: 3px solid var(--gold); padding-left: 24px; margin-bottom: 1.6rem;
    }
    .story-author { font-family: var(--font-accent); font-style: italic; color: var(--latte); font-size: .92rem; }

    /* ===== PROCESS ===== */
    #process { padding: 100px 0; background: var(--ivory); }
    .process-steps { display: flex; gap: 0; align-items: flex-start; position: relative; }
    .process-line {
      position: absolute; top: 32px; left: calc(16.67% + 24px); right: calc(16.67% + 24px);
      height: 1px; background: linear-gradient(to right, var(--caramel), var(--gold), var(--caramel));
      z-index: 0;
    }
    .process-step { flex: 1; text-align: center; padding: 0 12px; position: relative; z-index: 1; }
    .process-icon {
      width: 64px; height: 64px; border-radius: 50%; background: var(--cream);
      border: 2px solid var(--caramel);
      display: flex; align-items: center; justify-content: center;
      font-size: 1.5rem; margin: 0 auto 16px;
      transition: background .3s, transform .3s;
    }
    .process-step:hover .process-icon { background: var(--caramel); transform: scale(1.08); }
    .process-step-title { font-family: var(--font-display); font-size: .95rem; font-weight: 700; color: var(--espresso); margin-bottom: 6px; }
    .process-step-desc { font-size: .82rem; color: var(--medium-roast); }

    /* ===== TESTIMONIALS ===== */
    #testimonials { padding: 100px 0; background: var(--cream); }
    .testimonial-card {
      background: var(--ivory); border-radius: 2px;
      padding: 32px 28px; height: 100%;
      border-bottom: 3px solid var(--caramel);
      transition: transform .3s, box-shadow .3s;
    }
    .testimonial-card:hover { transform: translateY(-4px); box-shadow: 0 16px 36px rgba(44,26,14,.1); }
    .testimonial-stars { color: var(--gold); font-size: 1rem; letter-spacing: 2px; margin-bottom: 14px; }
    .testimonial-text { font-family: var(--font-accent); font-style: italic; font-size: 1rem; color: var(--dark-roast); line-height: 1.65; margin-bottom: 20px; }
    .testimonial-author { display: flex; align-items: center; gap: 12px; }
    .testimonial-avatar { width: 44px; height: 44px; border-radius: 50%; object-fit: cover; border: 2px solid var(--mist); }
    .testimonial-name { font-weight: 600; font-size: .9rem; display: block; }
    .testimonial-role { font-size: .78rem; color: var(--medium-roast); }

    /* ===== LOCATIONS ===== */
    #locations { padding: 100px 0; background: var(--ivory); }
    .location-card { position: relative; overflow: hidden; border-radius: 2px; cursor: pointer; height: 360px; }
    .location-card img { width: 100%; height: 100%; object-fit: cover; transition: transform .7s var(--tr); }
    .location-card:hover img { transform: scale(1.06); }
    .location-card-overlay { position: absolute; inset: 0; background: linear-gradient(to top, rgba(44,26,14,.88) 0%, rgba(44,26,14,.1) 55%); transition: background .4s; }
    .location-card:hover .location-card-overlay { background: linear-gradient(to top, rgba(44,26,14,.94) 0%, rgba(44,26,14,.22) 55%); }
    .location-card-body { position: absolute; bottom: 0; left: 0; right: 0; padding: 28px 24px; }
    .location-city { font-family: var(--font-display); font-size: 1.4rem; font-weight: 700; color: var(--cream); display: block; margin-bottom: 4px; }
    .location-address { font-size: .8rem; color: rgba(245,239,224,.6); }
    .location-btn { margin-top: 14px; font-size: .72rem; text-transform: uppercase; letter-spacing: 2px; color: var(--gold); display: flex; align-items: center; gap: 6px; opacity: 0; transform: translateY(8px); transition: opacity .3s, transform .3s; }
    .location-card:hover .location-btn { opacity: 1; transform: translateY(0); }

    /* ===== APP SECTION ===== */
    #app-section {
      padding: 100px 0;
      background: linear-gradient(135deg, var(--espresso) 0%, var(--dark-roast) 100%);
      position: relative; overflow: hidden;
    }
    #app-section::before { content: ''; position: absolute; width: 500px; height: 500px; border-radius: 50%; background: radial-gradient(circle, rgba(181,101,29,.18) 0%, transparent 70%); top: -150px; right: -100px; }
    .app-phone { position: relative; text-align: center; }
    .app-phone-img { max-height: 420px; filter: drop-shadow(0 30px 60px rgba(0,0,0,.5)); animation: floatPhone 5s ease-in-out infinite; }
    @keyframes floatPhone { 0%,100%{transform:translateY(0) rotate(-2deg)} 50%{transform:translateY(-16px) rotate(2deg)} }
    .app-badge {
      display: inline-flex; align-items: center; gap: 10px;
      background: rgba(245,239,224,.08); border: 1px solid rgba(245,239,224,.15);
      padding: 12px 20px; border-radius: 8px; color: var(--cream); text-decoration: none;
      transition: background .3s, transform .2s; margin: 6px;
    }
    .app-badge:hover { background: rgba(245,239,224,.14); color: var(--cream); transform: translateY(-2px); }
    .app-badge i { font-size: 1.5rem; }
    .app-badge-label { font-size: .65rem; text-transform: uppercase; letter-spacing: 1.5px; opacity: .7; }
    .app-badge-store { font-size: .9rem; font-weight: 500; }

    /* ===== NEWSLETTER ===== */
    #newsletter { padding: 80px 0; background: var(--caramel); position: relative; overflow: hidden; }
    #newsletter::before { content: ''; position: absolute; inset: 0; background: repeating-linear-gradient(-45deg, transparent 0, transparent 12px, rgba(44,26,14,.04) 12px, rgba(44,26,14,.04) 13px); }
    .newsletter-title { font-family: var(--font-display); font-size: clamp(1.5rem,3vw,2.4rem); font-weight: 900; color: var(--cream); }
    .newsletter-sub { font-family: var(--font-accent); font-style: italic; font-size: 1rem; color: rgba(245,239,224,.8); }
    .newsletter-input-wrap { display: flex; max-width: 460px; }
    .newsletter-input { flex: 1; border: none; outline: none; background: rgba(245,239,224,.15); color: var(--cream); font-family: var(--font-body); font-size: .9rem; padding: 14px 20px; }
    .newsletter-input::placeholder { color: rgba(245,239,224,.55); }
    .newsletter-btn { background: var(--espresso); border: none; color: var(--cream); font-family: var(--font-body); font-size: .78rem; text-transform: uppercase; letter-spacing: 2px; padding: 14px 24px; cursor: pointer; transition: background .3s; }
    .newsletter-btn:hover { background: var(--dark-roast); }

    /* ===== FOOTER ===== */
    footer { background: var(--espresso); padding: 80px 0 32px; color: rgba(245,239,224,.55); }
    .footer-brand { font-family: var(--font-display); font-size: 1.8rem; font-weight: 900; color: var(--cream); margin-bottom: .8rem; }
    .footer-brand em { color: var(--gold); font-style: italic; }
    .footer-tagline { font-family: var(--font-accent); font-style: italic; font-size: .95rem; color: rgba(245,239,224,.45); margin-bottom: 1.4rem; }
    .footer-social a {
      width: 38px; height: 38px; border: 1px solid rgba(245,239,224,.18); border-radius: 50%;
      display: inline-flex; align-items: center; justify-content: center;
      color: rgba(245,239,224,.6); font-size: .9rem; text-decoration: none; margin-right: 8px;
      transition: all .3s;
    }
    .footer-social a:hover { background: var(--caramel); border-color: var(--caramel); color: var(--cream); }
    .footer-heading { font-family: var(--font-body); font-size: .75rem; text-transform: uppercase; letter-spacing: 2.5px; color: var(--latte); margin-bottom: 1.2rem; }
    .footer-links { list-style: none; padding: 0; }
    .footer-links li { margin-bottom: .65rem; }
    .footer-links a { color: rgba(245,239,224,.5); text-decoration: none; font-size: .9rem; transition: color .3s, padding-left .3s; }
    .footer-links a:hover { color: var(--gold); padding-left: 8px; }
    .footer-divider { border-color: rgba(245,239,224,.08); margin: 48px 0 24px; }
    .footer-bottom { font-size: .78rem; color: rgba(245,239,224,.3); }

    /* ===== ANIMATIONS ===== */
    @keyframes fadeUp { from{opacity:0; transform:translateY(28px)} to{opacity:1; transform:translateY(0)} }

    /* ===== CART TOAST ===== */
    .cart-toast {
      position: fixed; bottom: 24px; right: 80px;
      background: var(--espresso); color: var(--cream);
      padding: 14px 22px 14px 18px; border-left: 3px solid var(--gold);
      font-size: .88rem; z-index: 8888;
      transform: translateX(200%); transition: transform .4s var(--tr); pointer-events: none;
    }
    .cart-toast.show { transform: translateX(0); }

    /* ===== BACK TO TOP ===== */
    .back-top {
      position: fixed; bottom: 28px; right: 28px;
      width: 44px; height: 44px; background: var(--caramel); color: var(--cream); border: none;
      display: flex; align-items: center; justify-content: center; font-size: 1rem;
      cursor: pointer; z-index: 900;
      opacity: 0; pointer-events: none; transition: opacity .3s, transform .3s, background .3s;
    }
    .back-top.visible { opacity: 1; pointer-events: auto; }
    .back-top:hover { background: var(--dark-roast); transform: translateY(-3px); }

    /* ===== RESPONSIVE ===== */
    @media (max-width: 991.98px) {
      #story { grid-template-columns: 1fr; }
      .story-text-panel { padding: 48px 32px; }
      .process-line { display: none; }
      .about-text { padding-left: 0; margin-top: 2rem; }
    }
    @media (max-width: 767.98px) {
      #hero { height: 100svh; }
      .hero-title { font-size: 2.6rem; }
      .about-img-wrap img { height: 320px; }
      .about-badge { width: 88px; height: 88px; }
      .process-steps { flex-wrap: wrap; }
      .process-step { flex: 0 0 50%; margin-bottom: 32px; }
    }
  </style>
</head>
<body class="desktop">

  <!-- ===== PAGE LOADER ===== -->
  <div id="page-loader">
    <div class="loader-brand">Là <em>Mơ</em> Coffee</div>
    <div class="loader-tagline">Hương vị trong giấc mơ</div>
    <div class="loader-bar-wrap"><div class="loader-bar"></div></div>
  </div>

  <!-- CUSTOM CURSOR -->
  <div class="cursor-dot" id="cursorDot"></div>
  <div class="cursor-ring" id="cursorRing"></div>

  <!-- BACK TO TOP -->
  <button class="back-top" id="backTop" aria-label="Về đầu trang">
    <i class="bi bi-arrow-up"></i>
  </button>

  <!-- CART TOAST -->
  <div class="cart-toast" id="cartToast">
    <i class="bi bi-check-circle me-2 text-warning"></i> Đã thêm vào giỏ hàng!
  </div>

  <!-- ===== NAVBAR ===== -->
  <nav class="navbar navbar-expand-lg navbar-custom fixed-top" id="mainNav">
    <div class="container">
      <a class="navbar-brand navbar-brand-text" href="#">Là <em>Mơ</em> Coffee</a>
      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navMenu">
        <span style="display:block;width:24px;height:2px;background:var(--cream);margin:5px 0"></span>
        <span style="display:block;width:18px;height:2px;background:var(--cream);margin:5px 0"></span>
        <span style="display:block;width:24px;height:2px;background:var(--cream);margin:5px 0"></span>
      </button>
      <div class="collapse navbar-collapse" id="navMenu">
        <ul class="navbar-nav ms-auto align-items-lg-center">
          <li class="nav-item"><a class="nav-link nav-link-custom" href="#about">Về Chúng Tôi</a></li>
          <li class="nav-item"><a class="nav-link nav-link-custom" href="#menu">Thực Đơn</a></li>
          <li class="nav-item"><a class="nav-link nav-link-custom" href="#collection">Bộ Sưu Tập</a></li>
          <li class="nav-item"><a class="nav-link nav-link-custom" href="#locations">Chi Nhánh</a></li>
          <li class="nav-item"><a class="nav-link nav-link-custom" href="#newsletter">Ưu Đãi</a></li>
          <li class="nav-item ms-lg-3">
            <a href="#menu" class="btn btn-coffee btn-sm text-decoration-none">
              <span>Đặt Ngay</span>
            </a>
          </li>
        </ul>
      </div>
    </div>
  </nav>

  <!-- ===== HERO ===== -->
  <section id="hero">
    <div class="hero-bg" id="heroBg"></div>
    <div class="hero-content">
      <em class="hero-eyebrow">Chào Mừng Đến Với Là Mơ Coffee</em>
      <h1 class="hero-title">
        Hương Vị<br>
        <em>Trong Giấc Mơ</em>
      </h1>
      <p class="hero-subtitle">
        Mỗi tách cà phê là một khoảnh khắc riêng — nơi bạn được là chính mình, thư giãn và mơ mộng.
      </p>
      <div class="hero-cta d-flex gap-3 justify-content-center flex-wrap">
        <a href="#menu" class="btn btn-coffee"><span>Khám Phá Thực Đơn</span></a>
        <a href="#about" class="btn btn-outline-coffee">Câu Chuyện Của Chúng Tôi</a>
      </div>
    </div>
    <div class="scroll-indicator" onclick="document.getElementById('ticker').scrollIntoView({behavior:'smooth'})">
      <span>Cuộn</span>
      <div class="scroll-line"></div>
    </div>
  </section>

  <!-- ===== TICKER ===== -->
  <div class="ticker-strip" id="ticker">
    <div class="ticker-inner" id="tickerInner"></div>
  </div>

  <!-- ===== ABOUT ===== -->
  <section id="about">
    <div class="container">
      <div class="row align-items-center g-5">
        <div class="col-lg-5" data-aos="fade-right" data-aos-duration="900">
          <div class="about-img-wrap">
            <img src="https://images.unsplash.com/photo-1447933601403-0c6688de566e?w=800&q=80" alt="Cà phê Là Mơ" />
            <div class="about-badge">
              <div class="about-badge-inner">8+</div>
              <div class="about-badge-label">Năm</div>
            </div>
          </div>
        </div>
        <div class="col-lg-7" data-aos="fade-left" data-aos-duration="900" data-aos-delay="150">
          <div class="about-text">
            <em class="section-eyebrow">Câu Chuyện Của Chúng Tôi</em>
            <h2 class="section-title mb-3">Nơi Những<br>Giấc Mơ Bắt Đầu</h2>
            <div class="divider-gold left mb-4"></div>
            <p>Là Mơ Coffee ra đời từ một góc nhỏ yên bình năm 2017 — một nơi mà người sáng lập muốn tạo ra để bất kỳ ai cũng có thể tìm lại chính mình giữa nhịp sống hối hả.</p>
            <p>Chúng tôi tin rằng một tách cà phê tốt không chỉ là hương vị — đó còn là không gian, là cảm xúc, là khoảnh khắc bạn được ngồi xuống và cho phép mình mơ.</p>
            <div class="row g-3 mt-3">
              <div class="col-6 col-sm-3" data-aos="zoom-in" data-aos-delay="100">
                <div class="stat-card">
                  <div class="stat-num" data-count="45">0</div>
                  <div class="stat-label">Chi Nhánh</div>
                </div>
              </div>
              <div class="col-6 col-sm-3" data-aos="zoom-in" data-aos-delay="200">
                <div class="stat-card">
                  <div class="stat-num" data-count="8">0</div>
                  <div class="stat-label">Tỉnh Thành</div>
                </div>
              </div>
              <div class="col-6 col-sm-3" data-aos="zoom-in" data-aos-delay="300">
                <div class="stat-card">
                  <div class="stat-num" data-count="3">0</div>
                  <div class="stat-label">Giải Thưởng</div>
                </div>
              </div>
              <div class="col-6 col-sm-3" data-aos="zoom-in" data-aos-delay="400">
                <div class="stat-card">
                  <div class="stat-num">100<span style="font-size:1.4rem">%</span></div>
                  <div class="stat-label">Việt Nam</div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- ===== PROMO BANNER ===== -->
  <section id="promo">
    <div class="container position-relative" style="z-index:1">
      <div class="text-center mb-5" data-aos="fade-up">
        <em class="section-eyebrow" style="color:rgba(245,239,224,.7)">Ưu Đãi Đặc Biệt</em>
        <h2 class="section-title light" style="color:var(--cream)">Dành Riêng Cho Bạn</h2>
        <div class="divider-gold mx-auto mt-3" style="background:rgba(245,239,224,.5)"></div>
      </div>
      <div class="row g-4">
        <div class="col-md-4" data-aos="fade-up" data-aos-delay="0">
          <div class="promo-card">
            <span class="promo-icon">🎉</span>
            <div class="promo-title">Mua 2 Tặng 1</div>
            <div class="promo-desc">Mua 2 ly bất kỳ — nhận thêm 1 ly cùng loại miễn phí. Áp dụng mỗi ngày từ 14:00 – 16:00.</div>
            <div class="promo-badge">Hôm Nay</div>
          </div>
        </div>
        <div class="col-md-4" data-aos="fade-up" data-aos-delay="120">
          <div class="promo-card">
            <span class="promo-icon">📱</span>
            <div class="promo-title">Đặt App Giảm 20%</div>
            <div class="promo-desc">Tải ứng dụng Là Mơ Coffee và đặt hàng lần đầu — giảm ngay 20% không giới hạn đơn tối thiểu.</div>
            <div class="promo-badge">Mã: LAMO20</div>
          </div>
        </div>
        <div class="col-md-4" data-aos="fade-up" data-aos-delay="240">
          <div class="promo-card">
            <span class="promo-icon">🎂</span>
            <div class="promo-title">Quà Sinh Nhật</div>
            <div class="promo-desc">Thành viên Là Mơ nhận 1 ly miễn phí trong tuần sinh nhật cùng voucher đặc biệt từ chúng tôi.</div>
            <div class="promo-badge">Thành Viên</div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- ===== MENU ===== -->
  <section id="menu">
    <div class="container position-relative" style="z-index:1">
      <div class="text-center mb-5" data-aos="fade-up">
        <em class="section-eyebrow" style="color:var(--latte)">Thực Đơn</em>
        <h2 class="section-title light">Chọn Theo Cảm Xúc</h2>
        <div class="divider-gold mx-auto mt-3"></div>
      </div>

      <!-- Tabs -->
      <div class="menu-tabs" data-aos="fade-up" data-aos-delay="100">
        <button class="menu-tab-btn active" data-tab="coffee">☕ Cà Phê</button>
        <button class="menu-tab-btn" data-tab="drinks">🥤 Thức Uống</button>
        <button class="menu-tab-btn" data-tab="food">🥐 Bánh & Snack</button>
        <button class="menu-tab-btn" data-tab="special">✨ Đặc Biệt</button>
      </div>

      <!-- Coffee -->
      <div class="menu-panel active" id="tab-coffee">
        <div class="row g-4">
          <div class="col-sm-6 col-lg-3" data-aos="fade-up" data-aos-delay="0">
            <div class="menu-card" onclick="addToCart(this)">
              <div class="menu-card-img-wrap">
                <img src="https://images.unsplash.com/photo-1514432324607-a09d9b4aefdd?w=600&q=75" alt="Espresso" loading="lazy" />
                <span class="menu-card-badge">Bán Chạy</span>
              </div>
              <div class="menu-card-body">
                <div class="menu-card-name">Espresso Là Mơ</div>
                <div class="menu-card-desc">Đậm đà, mạnh mẽ, với hậu vị ngọt dai của Robusta cao nguyên</div>
                <div class="menu-card-footer">
                  <span class="menu-card-price">29.000 ₫</span>
                  <button class="btn-add"><i class="bi bi-plus"></i></button>
                </div>
              </div>
            </div>
          </div>
          <div class="col-sm-6 col-lg-3" data-aos="fade-up" data-aos-delay="80">
            <div class="menu-card" onclick="addToCart(this)">
              <div class="menu-card-img-wrap">
                <img src="https://images.unsplash.com/photo-1541167760496-1628856ab772?w=600&q=75" alt="Latte" loading="lazy" />
              </div>
              <div class="menu-card-body">
                <div class="menu-card-name">Latte Mật Ong</div>
                <div class="menu-card-desc">Espresso, sữa tươi phủ bọt, kết thúc bằng giọt mật ong nguyên chất</div>
                <div class="menu-card-footer">
                  <span class="menu-card-price">45.000 ₫</span>
                  <button class="btn-add"><i class="bi bi-plus"></i></button>
                </div>
              </div>
            </div>
          </div>
          <div class="col-sm-6 col-lg-3" data-aos="fade-up" data-aos-delay="160">
            <div class="menu-card" onclick="addToCart(this)">
              <div class="menu-card-img-wrap">
                <img src="https://images.unsplash.com/photo-1461023058943-07fcbe16d735?w=600&q=75" alt="Cold Brew" loading="lazy" />
                <span class="menu-card-badge">Mới</span>
              </div>
              <div class="menu-card-body">
                <div class="menu-card-name">Cold Brew 24h</div>
                <div class="menu-card-desc">Ủ lạnh 24 giờ, vị ngọt tự nhiên, thanh mát từng ngụm</div>
                <div class="menu-card-footer">
                  <span class="menu-card-price">55.000 ₫</span>
                  <button class="btn-add"><i class="bi bi-plus"></i></button>
                </div>
              </div>
            </div>
          </div>
          <div class="col-sm-6 col-lg-3" data-aos="fade-up" data-aos-delay="240">
            <div class="menu-card" onclick="addToCart(this)">
              <div class="menu-card-img-wrap">
                <img src="https://images.unsplash.com/photo-1509042239860-f550ce710b93?w=600&q=75" alt="Phin" loading="lazy" />
              </div>
              <div class="menu-card-body">
                <div class="menu-card-name">Phin Truyền Thống</div>
                <div class="menu-card-desc">Phin nhỏ giọt chậm rãi — thưởng thức cả hành trình pha chế</div>
                <div class="menu-card-footer">
                  <span class="menu-card-price">35.000 ₫</span>
                  <button class="btn-add"><i class="bi bi-plus"></i></button>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>

      <!-- Drinks -->
      <div class="menu-panel" id="tab-drinks">
        <div class="row g-4">
          <div class="col-sm-6 col-lg-3" data-aos="fade-up">
            <div class="menu-card" onclick="addToCart(this)">
              <div class="menu-card-img-wrap">
                <img src="https://images.unsplash.com/photo-1544145945-f90425340c7e?w=600&q=75" alt="Trà Đào" loading="lazy" />
                <span class="menu-card-badge">Yêu Thích</span>
              </div>
              <div class="menu-card-body">
                <div class="menu-card-name">Trà Đào Cam Sả</div>
                <div class="menu-card-desc">Trà xanh, đào tươi, cam vắt và tinh dầu sả thơm nhẹ</div>
                <div class="menu-card-footer">
                  <span class="menu-card-price">49.000 ₫</span>
                  <button class="btn-add"><i class="bi bi-plus"></i></button>
                </div>
              </div>
            </div>
          </div>
          <div class="col-sm-6 col-lg-3" data-aos="fade-up" data-aos-delay="80">
            <div class="menu-card" onclick="addToCart(this)">
              <div class="menu-card-img-wrap">
                <img src="https://images.unsplash.com/photo-1630559788000-9af46ea2f7e0?w=600&q=75" alt="Matcha" loading="lazy" />
              </div>
              <div class="menu-card-body">
                <div class="menu-card-name">Matcha Latte</div>
                <div class="menu-card-desc">Matcha Nhật Bản cao cấp, sữa yến mạch, vị đắng ngọt hài hòa</div>
                <div class="menu-card-footer">
                  <span class="menu-card-price">59.000 ₫</span>
                  <button class="btn-add"><i class="bi bi-plus"></i></button>
                </div>
              </div>
            </div>
          </div>
          <div class="col-sm-6 col-lg-3" data-aos="fade-up" data-aos-delay="160">
            <div class="menu-card" onclick="addToCart(this)">
              <div class="menu-card-img-wrap">
                <img src="https://images.unsplash.com/photo-1587734195503-904fca47e0e9?w=600&q=75" alt="Nước ép" loading="lazy" />
              </div>
              <div class="menu-card-body">
                <div class="menu-card-name">Cam Ép Tươi</div>
                <div class="menu-card-desc">100% cam tươi ép thủ công, không đường, không chất bảo quản</div>
                <div class="menu-card-footer">
                  <span class="menu-card-price">45.000 ₫</span>
                  <button class="btn-add"><i class="bi bi-plus"></i></button>
                </div>
              </div>
            </div>
          </div>
          <div class="col-sm-6 col-lg-3" data-aos="fade-up" data-aos-delay="240">
            <div class="menu-card" onclick="addToCart(this)">
              <div class="menu-card-img-wrap">
                <img src="https://images.unsplash.com/photo-1571167366136-b57e23b08306?w=600&q=75" alt="Soda" loading="lazy" />
                <span class="menu-card-badge">Mới</span>
              </div>
              <div class="menu-card-body">
                <div class="menu-card-name">Chanh Sả Soda</div>
                <div class="menu-card-desc">Chanh ta, sả tươi, soda lạnh — thanh mát, cực kỳ sảng khoái</div>
                <div class="menu-card-footer">
                  <span class="menu-card-price">39.000 ₫</span>
                  <button class="btn-add"><i class="bi bi-plus"></i></button>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>

      <!-- Food -->
      <div class="menu-panel" id="tab-food">
        <div class="row g-4">
          <div class="col-sm-6 col-lg-3" data-aos="fade-up">
            <div class="menu-card" onclick="addToCart(this)">
              <div class="menu-card-img-wrap">
                <img src="https://images.unsplash.com/photo-1555507036-ab1f4038808a?w=600&q=75" alt="Croissant" loading="lazy" />
                <span class="menu-card-badge">Sáng</span>
              </div>
              <div class="menu-card-body">
                <div class="menu-card-name">Croissant Bơ</div>
                <div class="menu-card-desc">Nướng tươi mỗi sáng, giòn lớp ngoài, mềm bơ ngậy bên trong</div>
                <div class="menu-card-footer">
                  <span class="menu-card-price">35.000 ₫</span>
                  <button class="btn-add"><i class="bi bi-plus"></i></button>
                </div>
              </div>
            </div>
          </div>
          <div class="col-sm-6 col-lg-3" data-aos="fade-up" data-aos-delay="80">
            <div class="menu-card" onclick="addToCart(this)">
              <div class="menu-card-img-wrap">
                <img src="https://images.unsplash.com/photo-1559620192-032c4bc4674e?w=600&q=75" alt="Bánh mì" loading="lazy" />
              </div>
              <div class="menu-card-body">
                <div class="menu-card-name">Bánh Mì Sandwich</div>
                <div class="menu-card-desc">Bánh mì nướng, trứng, rau sạch và sốt đặc biệt của nhà</div>
                <div class="menu-card-footer">
                  <span class="menu-card-price">55.000 ₫</span>
                  <button class="btn-add"><i class="bi bi-plus"></i></button>
                </div>
              </div>
            </div>
          </div>
          <div class="col-sm-6 col-lg-3" data-aos="fade-up" data-aos-delay="160">
            <div class="menu-card" onclick="addToCart(this)">
              <div class="menu-card-img-wrap">
                <img src="https://images.unsplash.com/photo-1565958011703-44f9829ba187?w=600&q=75" alt="Cake" loading="lazy" />
                <span class="menu-card-badge">Mới</span>
              </div>
              <div class="menu-card-body">
                <div class="menu-card-name">Bánh Bông Lan Cà Phê</div>
                <div class="menu-card-desc">Bánh tự làm với espresso, hạnh nhân và kem tươi vanilla</div>
                <div class="menu-card-footer">
                  <span class="menu-card-price">65.000 ₫</span>
                  <button class="btn-add"><i class="bi bi-plus"></i></button>
                </div>
              </div>
            </div>
          </div>
          <div class="col-sm-6 col-lg-3" data-aos="fade-up" data-aos-delay="240">
            <div class="menu-card" onclick="addToCart(this)">
              <div class="menu-card-img-wrap">
                <img src="https://images.unsplash.com/photo-1550317138-10000687a72b?w=600&q=75" alt="Waffles" loading="lazy" />
              </div>
              <div class="menu-card-body">
                <div class="menu-card-name">Waffles Caramel</div>
                <div class="menu-card-desc">Waffle giòn rụm phủ sốt caramel muối và kem tươi đánh bông</div>
                <div class="menu-card-footer">
                  <span class="menu-card-price">79.000 ₫</span>
                  <button class="btn-add"><i class="bi bi-plus"></i></button>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>

      <!-- Special -->
      <div class="menu-panel" id="tab-special">
        <div class="row g-4">
          <div class="col-sm-6 col-lg-4" data-aos="fade-up">
            <div class="menu-card" onclick="addToCart(this)">
              <div class="menu-card-img-wrap" style="height:280px">
                <img src="https://images.unsplash.com/photo-1572286258217-40e8cf1b7c54?w=600&q=75" alt="Signature" loading="lazy" />
                <span class="menu-card-badge">Đặc Biệt</span>
              </div>
              <div class="menu-card-body">
                <div class="menu-card-name">Cà Phê Trứng Là Mơ</div>
                <div class="menu-card-desc">Espresso đậm đà phủ kem trứng đánh bông với đường phèn và gừng — signature độc quyền</div>
                <div class="menu-card-footer">
                  <span class="menu-card-price">65.000 ₫</span>
                  <button class="btn-add"><i class="bi bi-plus"></i></button>
                </div>
              </div>
            </div>
          </div>
          <div class="col-sm-6 col-lg-4" data-aos="fade-up" data-aos-delay="120">
            <div class="menu-card" onclick="addToCart(this)">
              <div class="menu-card-img-wrap" style="height:280px">
                <img src="https://images.unsplash.com/photo-1498804103079-a6351b050096?w=600&q=75" alt="Pour over" loading="lazy" />
              </div>
              <div class="menu-card-body">
                <div class="menu-card-name">Pour Over Arabica</div>
                <div class="menu-card-desc">Arabica Cầu Đất, chiết xuất pour over tỉ mỉ — vị trái cây, hoa và caramel nhẹ</div>
                <div class="menu-card-footer">
                  <span class="menu-card-price">85.000 ₫</span>
                  <button class="btn-add"><i class="bi bi-plus"></i></button>
                </div>
              </div>
            </div>
          </div>
          <div class="col-sm-6 col-lg-4" data-aos="fade-up" data-aos-delay="240">
            <div class="menu-card" onclick="addToCart(this)">
              <div class="menu-card-img-wrap" style="height:280px">
                <img src="https://images.unsplash.com/photo-1495474472287-4d71bcdd2085?w=600&q=75" alt="Nitro" loading="lazy" />
                <span class="menu-card-badge">Mới</span>
              </div>
              <div class="menu-card-body">
                <div class="menu-card-name">Nitro Cold Brew</div>
                <div class="menu-card-desc">Cold brew sục khí nitơ — bọt mịn như bia, vị ngọt hoàn toàn tự nhiên</div>
                <div class="menu-card-footer">
                  <span class="menu-card-price">75.000 ₫</span>
                  <button class="btn-add"><i class="bi bi-plus"></i></button>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- ===== STORY SPLIT ===== -->
  <section id="story">
    <div class="story-visual" data-aos="fade-right" data-aos-duration="1000">
      <img src="https://images.unsplash.com/photo-1522992319-0365e5f11656?w=900&q=80" alt="Barista Là Mơ" loading="lazy" />
      <div class="story-visual-overlay"></div>
    </div>
    <div class="story-text-panel" data-aos="fade-left" data-aos-duration="1000" data-aos-delay="150">
      <em class="section-eyebrow mb-3 d-block" style="color:var(--latte)">Triết Lý</em>
      <blockquote>
        Là Mơ không chỉ bán cà phê — chúng tôi trao tặng những khoảnh khắc bạn được là chính mình.
      </blockquote>
      <p style="color:rgba(245,239,224,.6); font-family:var(--font-accent); font-size:.95rem; margin-bottom: 2rem;">
        Chúng tôi chọn mỗi hạt cà phê như chọn từng khoảnh khắc sống — có chủ đích, có tâm huyết, không vội vã. Vì cuộc sống đã đủ nhanh rồi.
      </p>
      <cite class="story-author">— Người sáng lập Là Mơ Coffee</cite>
    </div>
  </section>

  <!-- ===== PROCESS ===== -->
  <section id="process">
    <div class="container">
      <div class="text-center mb-5" data-aos="fade-up">
        <em class="section-eyebrow">Từ Hạt Đến Ly</em>
        <h2 class="section-title">Quy Trình Của Chúng Tôi</h2>
        <div class="divider-gold mx-auto mt-3"></div>
      </div>
      <div class="process-steps" data-aos="fade-up" data-aos-delay="100">
        <div class="process-line"></div>
        <div class="process-step">
          <div class="process-icon">🌿</div>
          <div class="process-step-title">Chọn Hạt</div>
          <div class="process-step-desc">Trực tiếp từ các nông trại đối tác uy tín vùng cao nguyên</div>
        </div>
        <div class="process-step">
          <div class="process-icon">🔥</div>
          <div class="process-step-title">Rang Tươi</div>
          <div class="process-step-desc">Rang theo mẻ nhỏ mỗi ngày để giữ trọn hương vị tươi mới</div>
        </div>
        <div class="process-step">
          <div class="process-icon">⚗️</div>
          <div class="process-step-title">Kiểm Định</div>
          <div class="process-step-desc">Mỗi mẻ rang đều qua cupping chuẩn quốc tế trước khi phục vụ</div>
        </div>
        <div class="process-step">
          <div class="process-icon">☕</div>
          <div class="process-step-title">Pha Chế</div>
          <div class="process-step-desc">Barista được đào tạo chuyên nghiệp, từng ly là một tác phẩm</div>
        </div>
        <div class="process-step">
          <div class="process-icon">🤍</div>
          <div class="process-step-title">Trao Tặng</div>
          <div class="process-step-desc">Mỗi tách được phục vụ với sự trân trọng dành cho bạn</div>
        </div>
      </div>
    </div>
  </section>

  <!-- ===== COLLECTION (from 1234.html) ===== -->
  <section id="collection">
    <div class="container">
      <div class="text-center mb-5" data-aos="fade-up">
        <em class="section-eyebrow">Bộ Sưu Tập</em>
        <h2 class="section-title">Là Mơ Collection</h2>
        <div class="divider-gold mx-auto mt-3"></div>
        <p class="mt-3" style="font-family:var(--font-accent); font-style:italic; color:var(--medium-roast); max-width:500px; margin-left:auto; margin-right:auto;">Những sản phẩm mang hương vị Là Mơ về tận nhà bạn</p>
      </div>
      <div class="collection-grid" data-aos="fade-up" data-aos-delay="100">
        <div class="coll-card">
          <div class="coll-card-img">
            <img src="https://images.unsplash.com/photo-1559056199-641a0ac8b55e?w=600&q=75" alt="Cà phê rang xay" loading="lazy" />
            <span class="coll-badge">Bán Chạy</span>
          </div>
          <div class="coll-body">
            <div class="coll-name">Cà Phê Rang Xay Là Mơ #1</div>
            <div>
              <span class="coll-price">185.000 ₫</span>
              <span class="coll-price-old">220.000 ₫</span>
            </div>
            <button class="btn-order">Mua Ngay</button>
          </div>
        </div>
        <div class="coll-card">
          <div class="coll-card-img">
            <img src="https://images.unsplash.com/photo-1572442388796-11668a67e53d?w=600&q=75" alt="Cold Brew Bottle" loading="lazy" />
            <span class="coll-badge">Mới</span>
          </div>
          <div class="coll-body">
            <div class="coll-name">Cold Brew Chai 500ml</div>
            <div>
              <span class="coll-price">95.000 ₫</span>
            </div>
            <button class="btn-order">Mua Ngay</button>
          </div>
        </div>
        <div class="coll-card">
          <div class="coll-card-img">
            <img src="https://images.unsplash.com/photo-1600093463592-8e36ae95ef56?w=600&q=75" alt="Gift set" loading="lazy" />
            <span class="coll-badge">Quà Tặng</span>
          </div>
          <div class="coll-body">
            <div class="coll-name">Gift Set Là Mơ Premium</div>
            <div>
              <span class="coll-price">350.000 ₫</span>
            </div>
            <button class="btn-order">Mua Ngay</button>
          </div>
        </div>
        <div class="coll-card">
          <div class="coll-card-img">
            <img src="https://images.unsplash.com/photo-1495474472287-4d71bcdd2085?w=600&q=75" alt="Drip bag" loading="lazy" />
          </div>
          <div class="coll-body">
            <div class="coll-name">Drip Bag Hộp 10 Gói</div>
            <div>
              <span class="coll-price">120.000 ₫</span>
              <span class="coll-price-old">140.000 ₫</span>
            </div>
            <button class="btn-order">Mua Ngay</button>
          </div>
        </div>
        <div class="coll-card">
          <div class="coll-card-img">
            <img src="https://images.unsplash.com/photo-1514432324607-a09d9b4aefdd?w=600&q=75" alt="Phin bộ" loading="lazy" />
          </div>
          <div class="coll-body">
            <div class="coll-name">Bộ Phin Là Mơ Inox</div>
            <div>
              <span class="coll-price">89.000 ₫</span>
            </div>
            <button class="btn-order">Mua Ngay</button>
          </div>
        </div>
        <div class="coll-card">
          <div class="coll-card-img">
            <img src="https://images.unsplash.com/photo-1611162617474-5b21e879e113?w=600&q=75" alt="Áo thương hiệu" loading="lazy" />
            <span class="coll-badge">Limited</span>
          </div>
          <div class="coll-body">
            <div class="coll-name">Áo Là Mơ Coffee Limited</div>
            <div>
              <span class="coll-price">250.000 ₫</span>
            </div>
            <button class="btn-order">Mua Ngay</button>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- ===== TESTIMONIALS ===== -->
  <section id="testimonials">
    <div class="container">
      <div class="text-center mb-5" data-aos="fade-up">
        <em class="section-eyebrow">Khách Hàng Nói Gì</em>
        <h2 class="section-title">Những Giấc Mơ Nhỏ</h2>
        <div class="divider-gold mx-auto mt-3"></div>
      </div>
      <div class="row g-4">
        <div class="col-md-4" data-aos="fade-up" data-aos-delay="0">
          <div class="testimonial-card">
            <div class="testimonial-stars">★★★★★</div>
            <div class="testimonial-text">Lần đầu uống Espresso Là Mơ, tôi đứng im mấy giây. Vị đậm mà không gắt, hậu ngọt cứ kéo dài mãi. Từ đó tôi không thể uống cà phê chỗ khác nữa.</div>
            <div class="testimonial-author">
              <img src="https://i.pravatar.cc/100?img=47" alt="" class="testimonial-avatar" />
              <div>
                <span class="testimonial-name">Phạm Thị Lan Anh</span>
                <span class="testimonial-role">Kế toán, TP.HCM</span>
              </div>
            </div>
          </div>
        </div>
        <div class="col-md-4" data-aos="fade-up" data-aos-delay="100">
          <div class="testimonial-card">
            <div class="testimonial-stars">★★★★★</div>
            <div class="testimonial-text">Không gian quán ấm áp, nhạc nhẹ, cà phê ngon. Tôi đã làm việc ở đây cả ngày mà không muốn về — cảm giác thật sự được là chính mình ở đây.</div>
            <div class="testimonial-author">
              <img src="https://i.pravatar.cc/100?img=33" alt="" class="testimonial-avatar" />
              <div>
                <span class="testimonial-name">Trần Đức Minh</span>
                <span class="testimonial-role">Lập trình viên, Đà Nẵng</span>
              </div>
            </div>
          </div>
        </div>
        <div class="col-md-4" data-aos="fade-up" data-aos-delay="200">
          <div class="testimonial-card">
            <div class="testimonial-stars">★★★★★</div>
            <div class="testimonial-text">Cà Phê Trứng Là Mơ là thứ tôi không bao giờ nghĩ mình sẽ nghiện. Thế mà giờ mỗi sáng tôi ghé đây trước khi vào văn phòng — không có nó ngày không bắt đầu được.</div>
            <div class="testimonial-author">
              <img src="https://i.pravatar.cc/100?img=5" alt="" class="testimonial-avatar" />
              <div>
                <span class="testimonial-name">Nguyễn Hoàng Yến</span>
                <span class="testimonial-role">Marketing Manager, Hà Nội</span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- ===== LOCATIONS ===== -->
  <section id="locations" style="padding:100px 0; background:var(--blush);">
    <div class="container">
      <div class="text-center mb-5" data-aos="fade-up">
        <em class="section-eyebrow">Tìm Chúng Tôi</em>
        <h2 class="section-title">Chi Nhánh Gần Bạn</h2>
        <div class="divider-gold mx-auto mt-3"></div>
      </div>
      <div class="row g-4">
        <div class="col-md-4" data-aos="fade-up" data-aos-delay="0">
          <div class="location-card">
            <img src="https://images.unsplash.com/photo-1554118811-1e0d58224f24?w=700&q=75" alt="TP.HCM" loading="lazy" />
            <div class="location-card-overlay"></div>
            <div class="location-card-body">
              <span class="location-city">TP. Hồ Chí Minh</span>
              <span class="location-address">18 chi nhánh · Quận 1, 3, 7, Bình Thạnh...</span>
              <div class="location-btn">Xem bản đồ <i class="bi bi-arrow-right"></i></div>
            </div>
          </div>
        </div>
        <div class="col-md-4" data-aos="fade-up" data-aos-delay="100">
          <div class="location-card">
            <img src="https://images.unsplash.com/photo-1501339847302-ac426a4a7cbb?w=700&q=75" alt="Hà Nội" loading="lazy" />
            <div class="location-card-overlay"></div>
            <div class="location-card-body">
              <span class="location-city">Hà Nội</span>
              <span class="location-address">14 chi nhánh · Hoàn Kiếm, Đống Đa, Cầu Giấy...</span>
              <div class="location-btn">Xem bản đồ <i class="bi bi-arrow-right"></i></div>
            </div>
          </div>
        </div>
        <div class="col-md-4" data-aos="fade-up" data-aos-delay="200">
          <div class="location-card">
            <img src="https://images.unsplash.com/photo-1537996194471-e657df975ab4?w=700&q=75" alt="Đà Nẵng" loading="lazy" />
            <div class="location-card-overlay"></div>
            <div class="location-card-body">
              <span class="location-city">Đà Nẵng</span>
              <span class="location-address">8 chi nhánh · Hải Châu, Sơn Trà, Ngũ Hành Sơn...</span>
              <div class="location-btn">Xem bản đồ <i class="bi bi-arrow-right"></i></div>
            </div>
          </div>
        </div>
      </div>
      <div class="text-center mt-5" data-aos="fade-up">
        <a href="#" class="btn btn-coffee"><span>Xem Tất Cả Chi Nhánh</span></a>
      </div>
    </div>
  </section>

  <!-- ===== APP SECTION ===== -->
  <section id="app-section">
    <div class="container position-relative" style="z-index:1">
      <div class="row align-items-center g-5">
        <div class="col-lg-6" data-aos="fade-right" data-aos-duration="900">
          <em class="section-eyebrow" style="color:var(--latte)">Ứng Dụng</em>
          <h2 class="section-title light mb-3">Đặt Trước,<br>Không Chờ Đợi</h2>
          <p style="color:rgba(245,239,224,.65); font-family:var(--font-accent); font-size:1.05rem; margin-bottom:2rem;">
            Tải ứng dụng Là Mơ Coffee — đặt trước 10 phút, tích điểm thành viên, nhận ưu đãi sinh nhật và hàng ngàn ưu đãi độc quyền chỉ dành riêng cho thành viên Là Mơ.
          </p>
          <div class="d-flex flex-wrap">
            <a href="#" class="app-badge">
              <i class="bi bi-apple" style="font-size:1.8rem"></i>
              <div>
                <div class="app-badge-label">Tải từ</div>
                <div class="app-badge-store">App Store</div>
              </div>
            </a>
            <a href="#" class="app-badge">
              <i class="bi bi-google-play" style="font-size:1.6rem"></i>
              <div>
                <div class="app-badge-label">Tải từ</div>
                <div class="app-badge-store">Google Play</div>
              </div>
            </a>
          </div>
        </div>
        <div class="col-lg-6" data-aos="zoom-in" data-aos-duration="900" data-aos-delay="200">
          <div class="app-phone">
            <img src="https://images.unsplash.com/photo-1512941937669-90a1b58e7e9c?w=400&q=80"
                 alt="App Là Mơ Coffee" class="app-phone-img rounded-4"
                 style="max-width:320px; width:100%;" />
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- ===== NEWSLETTER ===== -->
  <section id="newsletter">
    <div class="container position-relative" style="z-index:1">
      <div class="row align-items-center g-4">
        <div class="col-lg-5" data-aos="fade-right">
          <h2 class="newsletter-title">Nhận Ưu Đãi Mỗi Tuần</h2>
          <p class="newsletter-sub mt-2">Đăng ký và nhận ngay voucher 20% cho lần đầu tiên từ Là Mơ</p>
        </div>
        <div class="col-lg-7" data-aos="fade-left">
          <div class="newsletter-input-wrap ms-lg-auto">
            <input type="email" class="newsletter-input" placeholder="Địa chỉ email của bạn..." id="newsletterEmail" />
            <button class="newsletter-btn" onclick="subscribeNewsletter()">Đăng Ký</button>
          </div>
          <p style="font-size:.72rem; color:rgba(245,239,224,.55); margin-top:8px;">Chúng tôi không spam. Hủy đăng ký bất cứ lúc nào.</p>
        </div>
      </div>
    </div>
  </section>

  <!-- ===== FOOTER ===== -->
  <footer>
    <div class="container">
      <div class="row g-5">
        <div class="col-lg-4">
          <div class="footer-brand">Là <em>Mơ</em> Coffee</div>
          <div class="footer-tagline">Hương vị trong giấc mơ — mỗi ngày</div>
          <p style="font-size:.88rem; max-width:280px; line-height:1.7;">
            Mỗi tách cà phê chúng tôi phục vụ là sự kết tinh của đất trời Tây Nguyên và tâm huyết của những con người yêu nghề.
          </p>
          <div class="footer-social mt-3">
            <a href="#"><i class="bi bi-facebook"></i></a>
            <a href="#"><i class="bi bi-instagram"></i></a>
            <a href="#"><i class="bi bi-tiktok"></i></a>
            <a href="#"><i class="bi bi-youtube"></i></a>
          </div>
        </div>
        <div class="col-6 col-lg-2">
          <div class="footer-heading">Khám Phá</div>
          <ul class="footer-links">
            <li><a href="#about">Về Chúng Tôi</a></li>
            <li><a href="#menu">Thực Đơn</a></li>
            <li><a href="#collection">Bộ Sưu Tập</a></li>
            <li><a href="#story">Câu Chuyện</a></li>
            <li><a href="#process">Quy Trình</a></li>
          </ul>
        </div>
        <div class="col-6 col-lg-2">
          <div class="footer-heading">Hỗ Trợ</div>
          <ul class="footer-links">
            <li><a href="#">Liên Hệ</a></li>
            <li><a href="#">Nhượng Quyền</a></li>
            <li><a href="#">Tuyển Dụng</a></li>
            <li><a href="#">Điều Khoản</a></li>
            <li><a href="#">Chính Sách Bảo Mật</a></li>
          </ul>
        </div>
        <div class="col-lg-4">
          <div class="footer-heading">Liên Hệ</div>
          <ul class="footer-links">
            <li><a href="tel:19001234"><i class="bi bi-telephone me-2"></i>1800 6868</a></li>
            <li><a href="mailto:hello@lamocoffee.vn"><i class="bi bi-envelope me-2"></i>hello@lamocoffee.vn</a></li>
            <li><a href="#"><i class="bi bi-geo-alt me-2"></i>45 chi nhánh toàn quốc</a></li>
          </ul>
          <div class="mt-4" style="font-size:.78rem; color:rgba(245,239,224,.35);">
            <i class="bi bi-clock me-1"></i> Mở cửa 6:30 – 22:30 hằng ngày
          </div>
        </div>
      </div>
      <hr class="footer-divider" />
      <div class="d-flex flex-wrap justify-content-between align-items-center footer-bottom gap-2">
        <span>© 2025 Là Mơ Coffee. Mọi quyền bảo lưu.</span>
        <div class="d-flex gap-3">
          <a href="#" style="color:inherit;text-decoration:none;transition:color .3s" onmouseover="this.style.color='var(--gold)'" onmouseout="this.style.color='inherit'">Chính Sách Bảo Mật</a>
          <a href="#" style="color:inherit;text-decoration:none;transition:color .3s" onmouseover="this.style.color='var(--gold)'" onmouseout="this.style.color='inherit'">Điều Khoản Sử Dụng</a>
        </div>
      </div>
    </div>
  </footer>

  <!-- ===== SCRIPTS ===== -->
  <script src="https://cdnjs.cloudflare.com/ajax/libs/bootstrap/5.3.8/js/bootstrap.bundle.min.js"></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/aos/2.3.4/aos.js"></script>

  <script>
    /* PAGE LOADER */
    window.addEventListener('load', () => {
      setTimeout(() => document.getElementById('page-loader').classList.add('done'), 1600);
    });

    /* AOS */
    AOS.init({ once: true, offset: 80, easing: 'ease-out-cubic' });

    /* NAVBAR SCROLL */
    const nav = document.getElementById('mainNav');
    const backTop = document.getElementById('backTop');
    window.addEventListener('scroll', () => {
      const y = window.scrollY;
      nav.classList.toggle('scrolled', y > 60);
      backTop.classList.toggle('visible', y > 500);
    }, { passive: true });

    /* PARALLAX HERO */
    const heroBg = document.getElementById('heroBg');
    window.addEventListener('scroll', () => {
      const y = window.scrollY;
      if (y < window.innerHeight)
        heroBg.style.transform = `scale(1.08) translateY(${y * 0.28}px)`;
    }, { passive: true });

    /* CUSTOM CURSOR */
    const dot = document.getElementById('cursorDot');
    const ring = document.getElementById('cursorRing');
    let mx = 0, my = 0, rx = 0, ry = 0;
    const isMobile = /Mobi|Android/i.test(navigator.userAgent);
    if (!isMobile) {
      document.addEventListener('mousemove', e => { mx = e.clientX; my = e.clientY; });
      const lerp = (a, b, t) => a + (b - a) * t;
      (function animateCursor() {
        dot.style.left = mx + 'px'; dot.style.top = my + 'px';
        rx = lerp(rx, mx, 0.14); ry = lerp(ry, my, 0.14);
        ring.style.left = rx + 'px'; ring.style.top = ry + 'px';
        requestAnimationFrame(animateCursor);
      })();
      document.querySelectorAll('a,button,.menu-card,.coll-card,.location-card,.stat-card').forEach(el => {
        el.addEventListener('mouseenter', () => ring.classList.add('hovered'));
        el.addEventListener('mouseleave', () => ring.classList.remove('hovered'));
      });
    } else { document.body.classList.remove('desktop'); }

    /* TICKER */
    const tickerItems = [
      'Là Mơ Coffee — Hương Vị Trong Giấc Mơ', 'Cà Phê Rang Xay Mới Mỗi Ngày',
      'Thưởng Thức Tại Chỗ hoặc Mang Về', 'Giao Hàng Trong Vòng 30 Phút',
      'Thành Viên Nhận Ưu Đãi Mỗi Tuần', 'Hạt Cà Phê Từ Cao Nguyên Đắk Lắk',
      'Không Gian Làm Việc Thoải Mái', 'Miễn Phí Wifi Tốc Độ Cao',
    ];
    const inner = document.getElementById('tickerInner');
    [...tickerItems, ...tickerItems].forEach(t => {
      inner.innerHTML += `<span class="ticker-item">${t}<span class="ticker-dot">◆</span></span>`;
    });

    /* MENU TABS */
    document.querySelectorAll('.menu-tab-btn').forEach(btn => {
      btn.addEventListener('click', () => {
        document.querySelectorAll('.menu-tab-btn').forEach(b => b.classList.remove('active'));
        document.querySelectorAll('.menu-panel').forEach(p => p.classList.remove('active'));
        btn.classList.add('active');
        document.getElementById('tab-' + btn.dataset.tab).classList.add('active');
        AOS.refreshHard();
      });
    });

    /* ADD TO CART */
    const toast = document.getElementById('cartToast');
    let toastTimer;
    function addToCart(card) {
      clearTimeout(toastTimer);
      toast.classList.add('show');
      toastTimer = setTimeout(() => toast.classList.remove('show'), 2400);
      const btn = card.querySelector('.btn-add');
      if (btn) { btn.style.transform = 'rotate(180deg) scale(1.2)'; setTimeout(() => btn.style.transform = '', 400); }
    }

    /* COLLECTION BUTTONS */
    document.querySelectorAll('.btn-order').forEach(btn => {
      btn.addEventListener('click', function() {
        this.textContent = '✓ Đã Thêm';
        this.style.background = 'var(--caramel)';
        setTimeout(() => { this.textContent = 'Mua Ngay'; this.style.background = ''; }, 2000);
      });
    });

    /* COUNTER ANIMATION */
    const counters = document.querySelectorAll('[data-count]');
    new IntersectionObserver(entries => {
      entries.forEach(entry => {
        if (!entry.isIntersecting) return;
        const el = entry.target, target = +el.dataset.count;
        let start = 0;
        const step = ts => {
          if (!start) start = ts;
          const p = Math.min((ts - start) / 1800, 1);
          el.textContent = Math.floor((1 - Math.pow(1-p,3)) * target);
          if (p < 1) requestAnimationFrame(step); else el.textContent = target;
        };
        requestAnimationFrame(step);
      });
    }, { threshold: 0.5 }).observe.length;
    counters.forEach(c => {
      new IntersectionObserver(entries => {
        entries.forEach(e => {
          if (!e.isIntersecting) return;
          const el = e.target, target = +el.dataset.count;
          let start = 0;
          const step = ts => {
            if (!start) start = ts;
            const p = Math.min((ts-start)/1800,1);
            el.textContent = Math.floor((1-Math.pow(1-p,3))*target);
            if (p<1) requestAnimationFrame(step); else el.textContent = target;
          };
          requestAnimationFrame(step);
          e.target.observer.unobserve(e.target);
        });
      }, { threshold: 0.5 }).observe(c);
    });

    /* NEWSLETTER */
    function subscribeNewsletter() {
      const input = document.getElementById('newsletterEmail');
      if (!input.value || !input.value.includes('@')) {
        input.style.borderBottom = '2px solid #e74c3c';
        setTimeout(() => input.style.borderBottom = '', 1500);
        return;
      }
      input.value = '';
      input.placeholder = '✓ Đăng ký thành công! Cảm ơn bạn.';
      input.style.color = 'var(--cream)';
      setTimeout(() => { input.placeholder = 'Địa chỉ email của bạn...'; input.style.color = ''; }, 3000);
    }

    /* BACK TO TOP */
    backTop.addEventListener('click', () => window.scrollTo({ top: 0, behavior: 'smooth' }));

    /* ACTIVE NAV */
    const sections = document.querySelectorAll('section[id]');
    const navLinks = document.querySelectorAll('.nav-link-custom');
    new IntersectionObserver(entries => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          navLinks.forEach(a => {
            a.style.color = '';
            if (a.getAttribute('href') === '#' + entry.target.id) a.style.color = 'var(--gold)';
          });
        }
      });
    }, { rootMargin: '-40% 0px -40% 0px' }).observe.length;
    sections.forEach(s => {
      new IntersectionObserver(entries => {
        entries.forEach(entry => {
          if (entry.isIntersecting) {
            navLinks.forEach(a => {
              a.style.color = '';
              if (a.getAttribute('href') === '#' + entry.target.id) a.style.color = 'var(--gold)';
            });
          }
        });
      }, { rootMargin: '-40% 0px -40% 0px' }).observe(s);
    });
  </script>
</body>
</html>
