<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>BxSHEART -- Video Editor</title>

  <!-- Google Fonts -->
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;800&display=swap" rel="stylesheet">

  <style>
    :root{
      --blue:#1e88ff;
      --blue-dark:#0f5ec0;
      --text:#0a0a0a;
      --muted:#6b7280;
      --bg:#ffffff;
    }
    *{box-sizing:border-box}
    html{scroll-behavior:smooth}
    body{
      margin:0;
      font-family:Poppins, system-ui, -apple-system, Segoe UI, Roboto, Arial, sans-serif;
      color:var(--text);
      background:var(--bg);
      line-height:1.6;
    }
    /* Navbar */
    .nav{
      position:fixed; inset:0 0 auto 0;
      display:flex; align-items:center; justify-content:space-between;
      padding:14px 22px; z-index:50;
      background:rgba(255,255,255,.75); backdrop-filter:blur(8px);
      border-bottom:1px solid rgba(0,0,0,.06);
    }
    .brand{font-weight:800; letter-spacing:.2px}
    .brand span{color:var(--blue)}
    .menu{display:flex; gap:18px}
    .menu a{
      text-decoration:none; color:#111; font-weight:600;
      padding:8px 12px; border-radius:12px;
    }
    .menu a:hover{background:rgba(30,136,255,.08)}
    .burger{display:none; border:none; background:transparent; font-size:26px}

    /* Hero */
    .hero{
      min-height:95vh; display:grid; place-items:center; text-align:left;
      padding:110px 22px 40px; position:relative; overflow:hidden;
      color:#fff;
      background:linear-gradient(0deg, rgba(10,23,55,.6), rgba(10,23,55,.6)),
        url('https://images.unsplash.com/photo-1518770660439-4636190af475?q=80&w=1600&auto=format&fit=crop') center/cover no-repeat;
      /* ↑ Replace with your own background if you want */
    }
    .hero-inner{max-width:1100px; width:100%; display:grid; gap:16px}
    .eyebrow{
      display:inline-block; font-size:14px; letter-spacing:2px; text-transform:uppercase;
      background:rgba(255,255,255,.15); padding:6px 12px; border-radius:999px
    }
    .title{
      font-size:clamp(32px, 6vw, 64px);
      line-height:1.1; font-weight:800; margin:8px 0 0
    }
    .title strong{color:#fff; text-shadow:0 6px 26px rgba(0,0,0,.35)}
    .subtitle{font-size:clamp(16px, 2.5vw, 22px); color:#e6eefc}
    .cta{display:flex; gap:12px; flex-wrap:wrap; margin-top:14px}
    .btn{
      border:none; cursor:pointer; font-weight:700; border-radius:14px;
      padding:12px 18px; transition:.2s transform ease, .2s box-shadow ease, .2s background ease;
      text-decoration:none; display:inline-flex; align-items:center; gap:8px
    }
    .btn-primary{background:var(--blue); color:#fff; box-shadow:0 8px 20px rgba(30,136,255,.35)}
    .btn-primary:hover{transform:translateY(-2px); background:var(--blue-dark)}
    .btn-ghost{background:rgba(255,255,255,.15); color:#fff}
    .btn-ghost:hover{background:rgba(255,255,255,.22)}

    /* Sections */
    section{padding:70px 22px}
    .wrap{max-width:1100px; margin:auto}
    h2{font-size:clamp(26px,4.2vw,36px); margin:0 0 12px; letter-spacing:.3px}
    p.lead{color:var(--muted); font-size:18px; margin-top:0}

    /* Services */
    .grid{
      display:grid; gap:16px;
      grid-template-columns:repeat(12, 1fr);
    }
    .card{
      grid-column:span 12; background:#fff; border:1px solid rgba(0,0,0,.06);
      border-radius:20px; padding:20px; box-shadow:0 6px 18px rgba(0,0,0,.06);
    }
    .card h3{margin:4px 0 6px}
    .pill{display:inline-block; font-size:12px; padding:4px 10px; border-radius:999px; background:rgba(30,136,255,.1); color:var(--blue); font-weight:700}

    /* Gallery */
    .gallery{display:grid; grid-template-columns:repeat(12,1fr); gap:12px}
    .thumb{
      grid-column:span 12; border-radius:16px; overflow:hidden; border:1px solid rgba(0,0,0,.08)
    }
    .thumb img{width:100%; height:100%; object-fit:cover; display:block}

    /* Contact */
    .contact{
      background:linear-gradient(180deg, #f7fbff, #ffffff);
      border-top:1px solid rgba(0,0,0,.06)
    }
    .contact .box{
      background:#fff; border:1px solid rgba(0,0,0,.06); border-radius:22px; padding:24px;
      display:grid; gap:8px
    }
    .contact a{color:var(--blue); text-decoration:none; font-weight:700}

    /* Footer */
    footer{padding:26px 22px; text-align:center; color:var(--muted); border-top:1px solid rgba(0,0,0,.06)}

    /* Responsive */
    @media (min-width:700px){
      .card{grid-column:span 4}
      .thumb{grid-column:span 4}
      .menu{gap:8px}
    }
    @media (max-width:820px){
      .menu{display:none}
      .burger{display:block}
      .menu.open{
        display:flex; flex-direction:column; position:absolute; top:56px; right:14px;
        background:#fff; border:1px solid rgba(0,0,0,.06); border-radius:14px; padding:10px; box-shadow:0 10px 30px rgba(0,0,0,.15)
      }
      .menu.open a{padding:10px 12px}
    }
  </style>
</head>
<body>

  <!-- Nav -->
  <nav class="nav">
    <div class="brand">Biswanath <span>Sahu</span></div>
    <div class="menu" id="menu">
      <a href="#about">About</a>
      <a href="#services">Services</a>
      <a href="#work">Work</a>
      <a href="#contact">Contact</a>
      <a href="https://youtube.com/@bxsheart_editz3ulp?si=MbrGZ72TlICJlpGU" target="_blank" rel="noopener">YouTube</a> 
      <button class="burger" aria-label="Menu" onclick="toggleMenu()">☰</button>
      </nav>
  <!-- Hero -->
  <header class="hero" id="home">
    <div class="hero-inner">
      <span class="eyebrow">Based in India • Available Worldwide</span>
      <h1 class="title">Hello, I'm <strong>Biswanath Sahu</strong></h1>
      <p class="subtitle">A passionate <strong>Video Editor</strong> crafting cinematic cuts, snappy shorts, and clean social ads.</p>
      <div class="cta">
        <a class="btn btn-primary" href="#work">View Showreel</a>
        <a class="btn btn-ghost" href=https://youtube.com/@bxsheart_editz3u1p?si=JOihB-rS4U9vRDK7" target="_blank" rel="noopener">Visit YouTube</a>
        <a class="btn btn-ghost" href="#contact">Hire Me</a>
      </div>
    </div>
  </header>

  <!-- About -->
  <section id="about">
    <div class="wrap">
      <h2>About</h2>
      <p class="lead">
        I'm Biswanath Sahu, a video editor focused on fast, story-driven edits.
        I help creators and brands turn raw footage into engaging content for YouTube,
        Instagram Reels, and ads. Clean cuts, smart sound design, and bold titles--that's my style.
      </p>
    </div>
  </section>

  <!-- Services -->
  <section id="services">
    <div class="wrap">
      <h2>Services</h2>
      <div class="grid">
        <div class="card">
          <span class="pill">Short-form</span>
          <h3>Reels & Shorts</h3>
          <p>Hook-first edits, punchy pacing, captions, emojis, and trend-ready formats.</p>
        </div>
        <div class="card">
          <span class="pill">YouTube</span>
          <h3>Long-form Videos</h3>
          <p>Talking-head, vlogs, tutorials, and podcasts with clean storytelling and graphics.</p>
        </div>
        <div class="card">
          <span class="pill">Brands</span>
          <h3>Ads & Promos</h3>
          <p>High-impact edits for product launches, UGC ads, and social campaigns.</p>
        </div>
      </div>
    </div>
  </section>

  <!-- Work Section -->
<section id="work" class="work">
  <h2>My Work</h2>
  <p>A few thumbnails from recent edits. Click to watch the videos:</p>

  <div class="gallery">

    <!-- Work 1 -->
    <a href=https://youtube.com/shorts/9LbmfYTGbbE?si=A_3tzzHOsQDbYDki target="_blank">
      <img src="thumbnail1.jpg" alt="Work 1">
    </a>

    <!-- Work 2 -->
    <a href="https://youtube.com/shorts/juZtyrSS6ic?si=rum7eXPkZlHSNM6Ltarget="_blank">
      <img src="thumbnail2.jpg" alt="Work 2">
    </a>

    <!-- Work 3 -->
    <a href=https://youtube.com/shorts/bhd7cbHxCzA?si=cufgzZNWxfwC06YYtarget="_blank">
      <img src="thumbnail3.jpg" alt="Work 3">
    </a>

  </div>
</section>
