<!DOCTYPE html>
<html lang="th">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>MoneyFlow — ไอเดียหาเงินออนไลน์</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@700;900&family=Noto+Sans+Thai:wght@300;400;600;700&display=swap" rel="stylesheet">
<style>
  :root {
    --gold: #C9A84C;
    --gold-light: #F0D080;
    --dark: #0A0A0A;
    --dark2: #111111;
    --dark3: #1A1A1A;
    --dark4: #222222;
    --text: #E8E0D0;
    --text-muted: #888880;
    --accent: #4CAF90;
    --accent2: #E06B3A;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: var(--dark);
    color: var(--text);
    font-family: 'Noto Sans Thai', sans-serif;
    overflow-x: hidden;
  }

  /* NOISE OVERLAY */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.04'/%3E%3C/svg%3E");
    pointer-events: none;
    z-index: 1000;
    opacity: 0.4;
  }

  /* HEADER */
  header {
    position: fixed;
    top: 0; left: 0; right: 0;
    z-index: 100;
    padding: 18px 40px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    background: rgba(10,10,10,0.85);
    backdrop-filter: blur(20px);
    border-bottom: 1px solid rgba(201,168,76,0.15);
  }

  .logo {
    font-family: 'Playfair Display', serif;
    font-size: 1.5rem;
    font-weight: 900;
    color: var(--gold);
    letter-spacing: 2px;
  }
  .logo span { color: var(--text); font-weight: 700; }

  nav a {
    color: var(--text-muted);
    text-decoration: none;
    font-size: 0.85rem;
    letter-spacing: 1.5px;
    text-transform: uppercase;
    margin-left: 30px;
    transition: color 0.3s;
  }
  nav a:hover { color: var(--gold); }

  /* HERO */
  .hero {
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
    padding: 120px 40px 80px;
    position: relative;
    overflow: hidden;
  }

  .hero-bg {
    position: absolute;
    inset: 0;
    background:
      radial-gradient(ellipse 60% 50% at 80% 50%, rgba(201,168,76,0.08) 0%, transparent 70%),
      radial-gradient(ellipse 40% 60% at 10% 80%, rgba(76,175,144,0.05) 0%, transparent 60%);
  }

  .hero-tag {
    display: inline-block;
    font-size: 0.7rem;
    letter-spacing: 4px;
    text-transform: uppercase;
    color: var(--gold);
    border: 1px solid rgba(201,168,76,0.4);
    padding: 6px 16px;
    margin-bottom: 30px;
    width: fit-content;
    animation: fadeUp 0.8s ease forwards;
    opacity: 0;
  }

  .hero h1 {
    font-family: 'Playfair Display', serif;
    font-size: clamp(3rem, 7vw, 6.5rem);
    font-weight: 900;
    line-height: 1.05;
    max-width: 800px;
    animation: fadeUp 0.8s ease 0.15s forwards;
    opacity: 0;
  }

  .hero h1 em {
    font-style: italic;
    color: var(--gold);
    -webkit-text-stroke: 0;
  }

  .hero-sub {
    margin-top: 24px;
    font-size: 1.05rem;
    color: var(--text-muted);
    max-width: 480px;
    line-height: 1.8;
    font-weight: 300;
    animation: fadeUp 0.8s ease 0.3s forwards;
    opacity: 0;
  }

  .hero-cta {
    margin-top: 40px;
    display: flex;
    gap: 16px;
    animation: fadeUp 0.8s ease 0.45s forwards;
    opacity: 0;
  }

  .btn-gold {
    background: var(--gold);
    color: var(--dark);
    padding: 14px 32px;
    font-family: 'Noto Sans Thai', sans-serif;
    font-weight: 700;
    font-size: 0.9rem;
    letter-spacing: 1px;
    cursor: pointer;
    border: none;
    text-decoration: none;
    transition: all 0.3s;
  }
  .btn-gold:hover { background: var(--gold-light); transform: translateY(-2px); }

  .btn-outline {
    background: transparent;
    color: var(--text);
    padding: 14px 32px;
    font-family: 'Noto Sans Thai', sans-serif;
    font-weight: 400;
    font-size: 0.9rem;
    letter-spacing: 1px;
    cursor: pointer;
    border: 1px solid rgba(255,255,255,0.2);
    text-decoration: none;
    transition: all 0.3s;
  }
  .btn-outline:hover { border-color: var(--gold); color: var(--gold); }

  .hero-stats {
    position: absolute;
    right: 60px;
    bottom: 80px;
    display: flex;
    flex-direction: column;
    gap: 24px;
    animation: fadeUp 0.8s ease 0.6s forwards;
    opacity: 0;
  }

  .stat {
    text-align: right;
    border-right: 2px solid var(--gold);
    padding-right: 20px;
  }
  .stat-num {
    font-family: 'Playfair Display', serif;
    font-size: 2.2rem;
    font-weight: 900;
    color: var(--gold);
    line-height: 1;
  }
  .stat-label {
    font-size: 0.72rem;
    color: var(--text-muted);
    letter-spacing: 2px;
    text-transform: uppercase;
    margin-top: 4px;
  }

  /* MARQUEE */
  .marquee-wrapper {
    background: var(--gold);
    overflow: hidden;
    padding: 12px 0;
  }
  .marquee-track {
    display: flex;
    gap: 0;
    animation: marquee 20s linear infinite;
    white-space: nowrap;
  }
  .marquee-item {
    color: var(--dark);
    font-weight: 700;
    font-size: 0.78rem;
    letter-spacing: 3px;
    text-transform: uppercase;
    padding: 0 40px;
  }
  .marquee-dot {
    color: var(--dark);
    opacity: 0.4;
  }

  /* SECTION */
  section {
    padding: 100px 40px;
    max-width: 1200px;
    margin: 0 auto;
  }

  .section-label {
    font-size: 0.7rem;
    letter-spacing: 4px;
    text-transform: uppercase;
    color: var(--gold);
    margin-bottom: 16px;
  }

  .section-title {
    font-family: 'Playfair Display', serif;
    font-size: clamp(2rem, 4vw, 3.2rem);
    font-weight: 900;
    line-height: 1.1;
    margin-bottom: 16px;
  }

  .section-sub {
    color: var(--text-muted);
    font-weight: 300;
    line-height: 1.8;
    max-width: 520px;
    margin-bottom: 60px;
  }

  /* CARD GRID */
  .card-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
    gap: 2px;
  }

  .card {
    background: var(--dark3);
    padding: 36px 32px;
    position: relative;
    overflow: hidden;
    cursor: pointer;
    transition: all 0.4s cubic-bezier(0.23, 1, 0.32, 1);
    border: 1px solid rgba(255,255,255,0.04);
  }

  .card::before {
    content: '';
    position: absolute;
    inset: 0;
    background: linear-gradient(135deg, rgba(201,168,76,0.08), transparent);
    opacity: 0;
    transition: opacity 0.4s;
  }

  .card:hover::before { opacity: 1; }
  .card:hover { transform: translateY(-4px); border-color: rgba(201,168,76,0.2); }

  .card-icon {
    font-size: 2.2rem;
    margin-bottom: 20px;
    display: block;
  }

  .card-category {
    font-size: 0.65rem;
    letter-spacing: 3px;
    text-transform: uppercase;
    color: var(--gold);
    margin-bottom: 10px;
  }

  .card-title {
    font-family: 'Playfair Display', serif;
    font-size: 1.4rem;
    font-weight: 700;
    margin-bottom: 14px;
    line-height: 1.3;
  }

  .card-desc {
    font-size: 0.88rem;
    color: var(--text-muted);
    line-height: 1.75;
    font-weight: 300;
    margin-bottom: 24px;
  }

  .card-footer {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .income-badge {
    font-size: 0.72rem;
    padding: 5px 12px;
    border-radius: 2px;
    font-weight: 600;
    letter-spacing: 1px;
  }
  .income-low { background: rgba(76,175,144,0.15); color: var(--accent); }
  .income-med { background: rgba(201,168,76,0.15); color: var(--gold); }
  .income-high { background: rgba(224,107,58,0.15); color: var(--accent2); }

  .difficulty {
    font-size: 0.7rem;
    color: var(--text-muted);
    letter-spacing: 1px;
  }

  /* FEATURED */
  .featured-grid {
    display: grid;
    grid-template-columns: 1.5fr 1fr;
    gap: 2px;
    margin-top: 0;
  }

  .featured-main {
    background: var(--dark3);
    padding: 60px 50px;
    position: relative;
    overflow: hidden;
    border: 1px solid rgba(255,255,255,0.04);
  }

  .featured-main::after {
    content: '₿';
    position: absolute;
    right: -20px;
    bottom: -30px;
    font-size: 18rem;
    color: rgba(201,168,76,0.04);
    font-family: monospace;
    pointer-events: none;
    line-height: 1;
  }

  .featured-side {
    display: flex;
    flex-direction: column;
    gap: 2px;
  }

  .side-card {
    flex: 1;
    background: var(--dark3);
    padding: 30px;
    border: 1px solid rgba(255,255,255,0.04);
    transition: all 0.3s;
    cursor: pointer;
  }
  .side-card:hover { background: var(--dark4); border-color: rgba(201,168,76,0.15); }

  .side-card-title {
    font-family: 'Playfair Display', serif;
    font-size: 1.1rem;
    margin-bottom: 8px;
  }

  /* STEPS */
  .steps-container {
    background: var(--dark2);
    border: 1px solid rgba(201,168,76,0.1);
    padding: 60px;
    position: relative;
    overflow: hidden;
  }

  .steps-container::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 2px;
    background: linear-gradient(90deg, var(--gold), transparent);
  }

  .steps-grid {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 40px;
    margin-top: 50px;
  }

  .step {
    position: relative;
  }

  .step-num {
    font-family: 'Playfair Display', serif;
    font-size: 4rem;
    font-weight: 900;
    color: rgba(201,168,76,0.12);
    line-height: 1;
    margin-bottom: 12px;
  }

  .step-title {
    font-weight: 700;
    font-size: 1rem;
    margin-bottom: 10px;
    color: var(--text);
  }

  .step-desc {
    font-size: 0.83rem;
    color: var(--text-muted);
    line-height: 1.75;
    font-weight: 300;
  }

  /* TOOLS */
  .tools-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(160px, 1fr));
    gap: 12px;
    margin-top: 40px;
  }

  .tool-item {
    background: var(--dark3);
    padding: 20px;
    text-align: center;
    border: 1px solid rgba(255,255,255,0.04);
    transition: all 0.3s;
    cursor: pointer;
  }
  .tool-item:hover { border-color: rgba(201,168,76,0.3); background: var(--dark4); }

  .tool-icon { font-size: 1.8rem; margin-bottom: 10px; }
  .tool-name { font-size: 0.82rem; font-weight: 600; margin-bottom: 4px; }
  .tool-desc { font-size: 0.72rem; color: var(--text-muted); }

  /* QUOTE */
  .quote-section {
    background: var(--gold);
    padding: 80px 60px;
    text-align: center;
    position: relative;
    overflow: hidden;
  }

  .quote-mark {
    font-family: 'Playfair Display', serif;
    font-size: 8rem;
    color: rgba(0,0,0,0.1);
    position: absolute;
    top: -20px;
    left: 40px;
    line-height: 1;
  }

  .quote-text {
    font-family: 'Playfair Display', serif;
    font-size: clamp(1.5rem, 3vw, 2.4rem);
    font-weight: 700;
    color: var(--dark);
    max-width: 700px;
    margin: 0 auto 20px;
    line-height: 1.4;
    position: relative;
    z-index: 1;
  }

  .quote-author {
    font-size: 0.8rem;
    letter-spacing: 3px;
    text-transform: uppercase;
    color: rgba(0,0,0,0.5);
    font-weight: 600;
  }

  /* NEWSLETTER */
  .newsletter {
    background: var(--dark2);
    padding: 80px 60px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    gap: 60px;
    border-top: 1px solid rgba(201,168,76,0.1);
  }

  .newsletter-text h3 {
    font-family: 'Playfair Display', serif;
    font-size: 2rem;
    margin-bottom: 10px;
  }
  .newsletter-text p {
    color: var(--text-muted);
    font-size: 0.9rem;
    font-weight: 300;
  }

  .newsletter-form {
    display: flex;
    gap: 0;
    min-width: 400px;
  }

  .newsletter-form input {
    flex: 1;
    background: var(--dark3);
    border: 1px solid rgba(255,255,255,0.1);
    border-right: none;
    padding: 14px 20px;
    color: var(--text);
    font-family: 'Noto Sans Thai', sans-serif;
    font-size: 0.9rem;
    outline: none;
    transition: border-color 0.3s;
  }
  .newsletter-form input:focus { border-color: rgba(201,168,76,0.5); }
  .newsletter-form input::placeholder { color: var(--text-muted); }

  .newsletter-form button {
    background: var(--gold);
    color: var(--dark);
    border: none;
    padding: 14px 28px;
    font-family: 'Noto Sans Thai', sans-serif;
    font-weight: 700;
    font-size: 0.85rem;
    cursor: pointer;
    letter-spacing: 1px;
    transition: background 0.3s;
  }
  .newsletter-form button:hover { background: var(--gold-light); }

  /* FOOTER */
  footer {
    background: var(--dark);
    padding: 40px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    border-top: 1px solid rgba(255,255,255,0.05);
  }

  footer .logo { font-size: 1.2rem; }
  .footer-copy { font-size: 0.75rem; color: var(--text-muted); letter-spacing: 1px; }
  .footer-links a { color: var(--text-muted); text-decoration: none; font-size: 0.78rem; margin-left: 20px; transition: color 0.3s; }
  .footer-links a:hover { color: var(--gold); }

  /* ANIMATIONS */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(24px); }
    to { opacity: 1; transform: translateY(0); }
  }

  @keyframes marquee {
    from { transform: translateX(0); }
    to { transform: translateX(-50%); }
  }

  .reveal {
    opacity: 0;
    transform: translateY(30px);
    transition: opacity 0.7s ease, transform 0.7s ease;
  }
  .reveal.visible {
    opacity: 1;
    transform: translateY(0);
  }

  /* SCROLL LINE */
  .scroll-line {
    position: fixed;
    top: 0; left: 0;
    height: 2px;
    background: var(--gold);
    z-index: 200;
    transition: width 0.1s;
  }

  @media (max-width: 768px) {
    header { padding: 16px 20px; }
    nav { display: none; }
    .hero { padding: 100px 20px 60px; }
    .hero-stats { display: none; }
    section { padding: 60px 20px; }
    .featured-grid { grid-template-columns: 1fr; }
    .steps-grid { grid-template-columns: 1fr 1fr; }
    .newsletter { flex-direction: column; gap: 30px; }
    .newsletter-form { min-width: unset; width: 100%; }
    .steps-container { padding: 30px 24px; }
  }
</style>
</head>
<body>

<div class="scroll-line" id="scrollLine"></div>

<!-- HEADER -->
<header>
  <div class="logo">Money<span>Flow</span></div>
  <nav>
    <a href="#">ไอเดีย</a>
    <a href="#">แนวทาง</a>
    <a href="#">เครื่องมือ</a>
    <a href="#">เริ่มต้น</a>
  </nav>
</header>

<!-- HERO -->
<div class="hero">
  <div class="hero-bg"></div>
  <div class="hero-tag">💰 รวมไอเดียหาเงินออนไลน์ 2025</div>
  <h1>หาเงินได้จริง<br><em>ไม่ต้องออกจากบ้าน</em></h1>
  <p class="hero-sub">รวมวิธีหาเงินออนไลน์ที่ได้ผลจริง พร้อมแนวทางเริ่มต้นแบบ step-by-step สำหรับทุกระดับ</p>
  <div class="hero-cta">
    <a href="#ideas" class="btn-gold">ดูไอเดียทั้งหมด</a>
    <a href="#guide" class="btn-outline">เริ่มต้นอย่างไร?</a>
  </div>
  <div class="hero-stats">
    <div class="stat">
      <div class="stat-num">50+</div>
      <div class="stat-label">ไอเดียหาเงิน</div>
    </div>
    <div class="stat">
      <div class="stat-num">฿0</div>
      <div class="stat-label">ค่าใช้จ่ายเริ่มต้น</div>
    </div>
    <div class="stat">
      <div class="stat-num">24h</div>
      <div class="stat-label">เริ่มได้ทันที</div>
    </div>
  </div>
</div>

<!-- MARQUEE -->
<div class="marquee-wrapper">
  <div class="marquee-track">
    <span class="marquee-item">Freelance</span><span class="marquee-dot">◆</span>
    <span class="marquee-item">Content Creator</span><span class="marquee-dot">◆</span>
    <span class="marquee-item">Dropshipping</span><span class="marquee-dot">◆</span>
    <span class="marquee-item">Affiliate</span><span class="marquee-dot">◆</span>
    <span class="marquee-item">ขายของออนไลน์</span><span class="marquee-dot">◆</span>
    <span class="marquee-item">Stock Photo</span><span class="marquee-dot">◆</span>
    <span class="marquee-item">Online Course</span><span class="marquee-dot">◆</span>
    <span class="marquee-item">Trading</span><span class="marquee-dot">◆</span>
    <span class="marquee-item">Virtual Assistant</span><span class="marquee-dot">◆</span>
    <span class="marquee-item">Print on Demand</span><span class="marquee-dot">◆</span>
    <!-- repeat -->
    <span class="marquee-item">Freelance</span><span class="marquee-dot">◆</span>
    <span class="marquee-item">Content Creator</span><span class="marquee-dot">◆</span>
    <span class="marquee-item">Dropshipping</span><span class="marquee-dot">◆</span>
    <span class="marquee-item">Affiliate</span><span class="marquee-dot">◆</span>
    <span class="marquee-item">ขายของออนไลน์</span><span class="marquee-dot">◆</span>
    <span class="marquee-item">Stock Photo</span><span class="marquee-dot">◆</span>
    <span class="marquee-item">Online Course</span><span class="marquee-dot">◆</span>
    <span class="marquee-item">Trading</span><span class="marquee-dot">◆</span>
    <span class="marquee-item">Virtual Assistant</span><span class="marquee-dot">◆</span>
    <span class="marquee-item">Print on Demand</span><span class="marquee-dot">◆</span>
  </div>
</div>

<!-- IDEAS SECTION -->
<section id="ideas">
  <div class="reveal">
    <div class="section-label">// ไอเดียหลัก</div>
    <h2 class="section-title">เลือกแนวทาง<br>ที่ใช่สำหรับคุณ</h2>
    <p class="section-sub">ไอเดียหาเงินออนไลน์ที่ได้รับการพิสูจน์แล้ว จัดเรียงตามความยากและรายได้ที่คาดหวัง</p>
  </div>

  <div class="card-grid reveal">
    <div class="card">
      <span class="card-icon">✍️</span>
      <div class="card-category">Content</div>
      <div class="card-title">Freelance เขียนคอนเทนต์</div>
      <div class="card-desc">รับเขียนบทความ คอนเทนต์โซเชียล สคริปต์วิดีโอ SEO ให้บริษัทและแบรนด์ต่างๆ ผ่านแพลตฟอร์มอย่าง Fastwork หรือ Upwork</div>
      <div class="card-footer">
        <span class="income-badge income-low">฿5,000–30,000/เดือน</span>
        <span class="difficulty">เริ่มง่าย ⭐⭐</span>
      </div>
    </div>

    <div class="card">
      <span class="card-icon">🎬</span>
      <div class="card-category">Creator</div>
      <div class="card-title">YouTube / TikTok</div>
      <div class="card-desc">สร้างช่องและผลิตคอนเทนต์สม่ำเสมอ รายได้จาก Ad Revenue, Brand Deal, และสินค้าของตัวเอง ต้องใช้เวลาแต่ยั่งยืน</div>
      <div class="card-footer">
        <span class="income-badge income-high">฿10,000–ไม่จำกัด</span>
        <span class="difficulty">ใช้เวลา ⭐⭐⭐⭐</span>
      </div>
    </div>

    <div class="card">
      <span class="card-icon">🛍️</span>
      <div class="card-category">E-Commerce</div>
      <div class="card-title">ขายของ Shopee / Lazada</div>
      <div class="card-desc">เริ่มจากสินค้าใกล้มือ หรือ Dropship จากซัพพลายเออร์ ไม่ต้องสต็อกของก็ได้ เน้นการตลาดและรีวิว</div>
      <div class="card-footer">
        <span class="income-badge income-med">฿5,000–50,000/เดือน</span>
        <span class="difficulty">ปานกลาง ⭐⭐⭐</span>
      </div>
    </div>

    <div class="card">
      <span class="card-icon">📸</span>
      <div class="card-category">Digital Asset</div>
      <div class="card-title">ขาย Stock Photo / Video</div>
      <div class="card-desc">ถ่ายภาพหรือวิดีโอคุณภาพดี อัปโหลดขายบน Shutterstock, Adobe Stock, Pond5 รายได้ passive income แท้จริง</div>
      <div class="card-footer">
        <span class="income-badge income-low">฿2,000–20,000/เดือน</span>
        <span class="difficulty">เริ่มง่าย ⭐⭐</span>
      </div>
    </div>

    <div class="card">
      <span class="card-icon">🎓</span>
      <div class="card-category">Education</div>
      <div class="card-title">สอนออนไลน์ / คอร์ส</div>
      <div class="card-desc">แพ็กความรู้เป็นคอร์สบน Skillane, Udemy หรือ SkillLane สร้างครั้งเดียว ขายได้ตลอด ถ้ามีความเชี่ยวชาญในด้านใดด้านหนึ่ง</div>
      <div class="card-footer">
        <span class="income-badge income-high">฿20,000–200,000+</span>
        <span class="difficulty">ลงทุนสูง ⭐⭐⭐⭐</span>
      </div>
    </div>

    <div class="card">
      <span class="card-icon">🤝</span>
      <div class="card-category">Marketing</div>
      <div class="ca
