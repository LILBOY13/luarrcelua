# luarrcelua

<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>LunderCell – Lista de Precios iPhone</title>
  <link href="https://fonts.googleapis.com/css2?family=Syne:wght@700;800;900&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet"/>
  <style>
    :root {
      --bg: #0d0000;
      --surface: #130000;
      --card: #1a0202;
      --border: #3a1010;
      --accent: #dc2626;
      --accent2: #ef4444;
      --accent3: #fca5a5;
      --gold: #f59e0b;
      --green: #22c55e;
      --red: #ef4444;
      --text: #fff5f5;
      --muted: #9e7070;
      --header-h: 84px;
    }

    * { box-sizing: border-box; margin: 0; padding: 0; }

    body {
      background: var(--bg);
      color: var(--text);
      font-family: 'DM Sans', sans-serif;
      min-height: 100vh;
      overflow-x: hidden;
    }

    /* ── HEADER ── */
    header {
      position: sticky; top: 0; z-index: 50;
      height: var(--header-h);
      background: rgba(13,0,0,.95);
      backdrop-filter: blur(20px);
      border-bottom: 1px solid var(--border);
      display: flex; align-items: center; justify-content: space-between;
      padding: 0 36px;
    }

    /* ── LOGO SVG ── */
    .logo { display: flex; align-items: center; gap: 14px; }

    .logo-svg {
      width: 52px; height: 52px; flex-shrink: 0;
    }

    .logo-text {
      font-family: 'Syne', sans-serif;
      font-size: 1.75rem; font-weight: 900; letter-spacing: -1px;
      background: linear-gradient(135deg, #ffffff 0%, #fca5a5 50%, #dc2626 100%);
      -webkit-background-clip: text; -webkit-text-fill-color: transparent;
    }

    .header-contact {
      display: flex; align-items: center; gap: 9px;
      background: rgba(220,38,38,.15); border: 1px solid rgba(220,38,38,.4);
      border-radius: 12px; padding: 9px 18px;
      font-size: .85rem; color: #fca5a5; font-weight: 600;
      text-decoration: none; transition: all .2s;
    }
    .header-contact:hover { background: rgba(220,38,38,.28); }

    /* ── HERO ── */
    .hero {
      background: linear-gradient(160deg, #1a0000 0%, #0d0000 45%, #180808 100%);
      border-bottom: 1px solid var(--border);
      padding: 52px 36px 44px;
      text-align: center;
      position: relative; overflow: hidden;
    }
    .hero::before {
      content: '';
      position: absolute; inset: 0;
      background: radial-gradient(ellipse at 50% -10%, rgba(220,38,38,.25) 0%, transparent 60%);
      pointer-events: none;
    }
    .hero::after {
      content: '';
      position: absolute; bottom: -1px; left: 0; right: 0; height: 1px;
      background: linear-gradient(90deg, transparent, rgba(220,38,38,.6), transparent);
    }
    .hero h1 {
      font-family: 'Syne', sans-serif;
      font-size: clamp(1.7rem, 4.5vw, 3rem);
      font-weight: 900; letter-spacing: -1.5px;
      margin-bottom: 12px; line-height: 1.1;
    }
    .hero h1 em {
      font-style: normal;
      background: linear-gradient(90deg, #dc2626, #fca5a5);
      -webkit-background-clip: text; -webkit-text-fill-color: transparent;
    }
    .hero p { color: var(--muted); font-size: .95rem; max-width: 500px; margin: 0 auto 24px; }
    .hero-badges { display: flex; flex-wrap: wrap; gap: 10px; justify-content: center; }
    .badge {
      background: rgba(255,255,255,.04); border: 1px solid var(--border);
      border-radius: 20px; padding: 5px 15px;
      font-size: .78rem; color: var(--muted);
      display: flex; align-items: center; gap: 7px;
    }
    .badge .dot {
      width: 7px; height: 7px; border-radius: 50%;
      background: var(--green); box-shadow: 0 0 6px var(--green);
      animation: pulse 2s infinite;
    }
    @keyframes pulse { 0%,100%{opacity:1} 50%{opacity:.35} }

    /* ── CONTROLS ── */
    .controls {
      padding: 20px 36px;
      display: flex; flex-wrap: wrap; gap: 12px; align-items: center;
      background: var(--surface); border-bottom: 1px solid var(--border);
    }
    .search-wrap { flex: 1; min-width: 220px; position: relative; }
    .search-wrap input {
      width: 100%; background: var(--card); border: 1px solid var(--border);
      border-radius: 10px; padding: 10px 14px 10px 42px;
      color: var(--text); font-family: 'DM Sans', sans-serif; font-size: .9rem;
      outline: none; transition: border .2s;
    }
    .search-wrap input::placeholder { color: var(--muted); }
    .search-wrap input:focus { border-color: var(--accent); }
    .search-wrap::before {
      content: '🔍'; position: absolute; left: 14px; top: 50%; transform: translateY(-50%);
      font-size: 15px; pointer-events: none;
    }

    /* ── MAIN ── */
    main { padding: 30px 36px 70px; max-width: 1100px; margin: 0 auto; }

    /* ── SECTION ── */
    .section {
      margin-bottom: 0;
      background: var(--card);
      border: 1px solid var(--border);
      border-radius: 18px; overflow: hidden;
    }
    .section-header {
      display: flex; align-items: center; gap: 14px;
      padding: 20px 26px;
      border-bottom: 1px solid var(--border);
    }
    .section-icon {
      width: 46px; height: 46px; border-radius: 14px;
      background: linear-gradient(135deg, #7f0000, #dc2626);
      display: flex; align-items: center; justify-content: center;
      font-size: 22px; flex-shrink: 0;
      box-shadow: 0 0 18px rgba(220,38,38,.35);
    }
    .section-title {
      font-family: 'Syne', sans-serif; font-size: 1.2rem; font-weight: 800;
      flex: 1; color: #fff;
    }
    .section-count {
      background: rgba(220,38,38,.15); border: 1px solid rgba(220,38,38,.3);
      border-radius: 20px; padding: 3px 14px; font-size: .78rem; color: #fca5a5;
    }

    /* TABLE */
    .table-wrap { overflow-x: auto; }
    table { width: 100%; border-collapse: collapse; font-size: .875rem; }
    thead tr { background: rgba(220,38,38,.06); border-bottom: 1px solid var(--border); }
    th {
      padding: 11px 22px; text-align: left;
      font-size: .71rem; text-transform: uppercase; letter-spacing: 1.2px;
      color: var(--muted); font-weight: 600; white-space: nowrap;
    }
    tbody tr { border-bottom: 1px solid rgba(255,255,255,.035); transition: background .12s; }
    tbody tr:last-child { border-bottom: none; }
    tbody tr:hover { background: rgba(220,38,38,.06); }
    tbody tr.row-hidden { display: none; }
    td { padding: 13px 22px; vertical-align: middle; }

    .td-model { font-weight: 500; color: var(--text); }
    .td-gb { color: var(--muted); font-size: .85rem; }

    .cond {
      display: inline-flex; align-items: center;
      border-radius: 6px; padding: 3px 11px;
      font-size: .8rem; font-weight: 700; white-space: nowrap;
    }
    .cond-Sellado,.cond-Nuevo { background: rgba(6,182,212,.1); color: #67e8f9; border: 1px solid rgba(6,182,212,.25); }
    .cond-Aplus  { background: rgba(34,197,94,.1); color: #4ade80; border: 1px solid rgba(34,197,94,.25); }
    .cond-A      { background: rgba(96,165,250,.1); color: #93c5fd; border: 1px solid rgba(96,165,250,.25); }
    .cond-Aminus { background: rgba(251,191,36,.1); color: #fcd34d; border: 1px solid rgba(251,191,36,.25); }
    .cond-B,.cond-C { background: rgba(239,68,68,.1); color: #fca5a5; border: 1px solid rgba(239,68,68,.22); }

    .td-price {
      font-family: 'Syne', sans-serif; font-weight: 800;
      font-size: .95rem; color: #fff; text-align: right; white-space: nowrap;
    }

    /* ── DIVIDER between sub-sections ── */
    .sub-divider td {
      background: rgba(220,38,38,.08);
      padding: 7px 22px;
      font-family: 'Syne', sans-serif; font-size: .72rem;
      text-transform: uppercase; letter-spacing: 1.5px;
      color: rgba(220,38,38,.8); font-weight: 700;
      border-top: 1px solid var(--border);
      border-bottom: 1px solid var(--border);
    }

    /* ── EMPTY STATE ── */
    #empty-state {
      display: none; text-align: center; padding: 70px 20px; color: var(--muted);
    }
    #empty-state .emoji { font-size: 3rem; margin-bottom: 14px; }

    /* ── FOOTER ── */
    footer {
      text-align: center; padding: 36px;
      border-top: 1px solid var(--border);
      color: var(--muted); font-size: .82rem;
    }
    footer a { color: var(--accent2); text-decoration: none; }
    footer strong { color: var(--text); }

    /* ── RESPONSIVE ── */
    @media(max-width:600px) {
      header { padding: 0 16px; }
      .hero, .controls { padding-left: 16px; padding-right: 16px; }
      main { padding: 16px 12px 56px; }
      th, td { padding: 10px 13px; }
      .header-contact .label { display: none; }
      .logo-text { font-size: 1.4rem; }
    }
  </style>
</head>
<body>

<!-- HEADER -->
<header>
  <div class="logo">
    <!-- Logo SVG con la inicial L -->
    <svg class="logo-svg" viewBox="0 0 52 52" xmlns="http://www.w3.org/2000/svg">
      <defs>
        <linearGradient id="lg1" x1="0%" y1="0%" x2="100%" y2="100%">
          <stop offset="0%" style="stop-color:#dc2626"/>
          <stop offset="100%" style="stop-color:#7f1d1d"/>
        </linearGradient>
        <linearGradient id="lg2" x1="0%" y1="0%" x2="100%" y2="100%">
          <stop offset="0%" style="stop-color:#fca5a5"/>
          <stop offset="100%" style="stop-color:#ffffff"/>
        </linearGradient>
        <filter id="glow">
          <feGaussianBlur stdDeviation="1.5" result="blur"/>
          <feMerge><feMergeNode in="blur"/><feMergeNode in="SourceGraphic"/></feMerge>
        </filter>
      </defs>
      <!-- Fondo redondeado -->
      <rect width="52" height="52" rx="14" fill="url(#lg1)"/>
      <!-- Borde sutil -->
      <rect width="52" height="52" rx="14" fill="none" stroke="rgba(255,255,255,0.18)" stroke-width="1"/>
      <!-- Brillo superior -->
      <rect x="8" y="4" width="36" height="16" rx="8" fill="rgba(255,255,255,0.10)"/>
      <!-- Letra L -->
      <text x="13" y="38" font-family="Georgia, serif" font-size="30" font-weight="900"
            fill="url(#lg2)" filter="url(#glow)" letter-spacing="-1">L</text>
      <!-- Punto decorativo -->
      <circle cx="39" cy="36" r="4" fill="#fff" opacity="0.9"/>
      <circle cx="39" cy="36" r="2.2" fill="#dc2626"/>
    </svg>
    <span class="logo-text">LunderCell</span>
  </div>
  <a class="header-contact" href="https://wa.me/18294837223" target="_blank">
    <span>💬</span>
    <span class="label">WhatsApp +1 (829) 483-7223</span>
  </a>
</header>

<!-- HERO -->
<div class="hero">
  <h1>Tu Especialista en<br><em>iPhone</em> en RD</h1>
  <p>Equipos verificados, condición garantizada. Encuentra tu iPhone al mejor precio del mercado.</p>
  <div class="hero-badges">
    <span class="badge"><span class="dot"></span>Lista actualizada</span>
    <span class="badge">📱 Solo iPhone</span>
    <span class="badge">💎 Condición garantizada</span>
    <span class="badge">✅ Precios en DOP</span>
  </div>
</div>

<!-- BÚSQUEDA -->
<div class="controls">
  <div class="search-wrap">
    <input type="text" id="searchInput" placeholder="Buscar modelo, GB, condición..." oninput="filterAll()"/>
  </div>
</div>

<!-- CONTENIDO -->
<main id="main">

  <div class="section" id="sec-iphone">
    <div class="section-header">
      <div class="section-icon">📱</div>
      <span class="section-title">iPhone — Lista de Precios</span>
      <span class="section-count" id="cnt-iphone"></span>
    </div>
    <div class="table-wrap">
      <table>
        <thead>
          <tr>
            <th>Modelo</th>
            <th>GB</th>
            <th>Condición</th>
            <th style="text-align:right">Precio (DOP)</th>
          </tr>
        </thead>
        <tbody id="tb-iphone">

          <!-- ── iPhone 14 Series ── -->
          <tr class="sub-divider"><td colspan="4">iPhone 14 Series</td></tr>
          <tr><td class="td-model">iPhone 14 Pro Max eSIM</td><td class="td-gb">128</td><td><span class="cond cond-Aplus">A+</span></td><td class="td-price">RD$ 33,995</td></tr>
          <tr><td class="td-model">iPhone 14 Pro Max eSIM</td><td class="td-gb">128</td><td><span class="cond cond-A">A</span></td><td class="td-price">RD$ 32,495</td></tr>
          <tr><td class="td-model">iPhone 14 Pro Max eSIM</td><td class="td-gb">128</td><td><span class="cond cond-Aminus">A-</span></td><td class="td-price">RD$ 30,995</td></tr>
          <tr><td class="td-model">iPhone 14 Pro eSIM</td><td class="td-gb">128</td><td><span class="cond cond-Aplus">A+</span></td><td class="td-price">RD$ 26,995</td></tr>
          <tr><td class="td-model">iPhone 14 Pro eSIM</td><td class="td-gb">128</td><td><span class="cond cond-A">A</span></td><td class="td-price">RD$ 25,495</td></tr>
          <tr><td class="td-model">iPhone 14 Plus eSIM</td><td class="td-gb">128</td><td><span class="cond cond-Aplus">A+</span></td><td class="td-price">RD$ 23,995</td></tr>
          <tr><td class="td-model">iPhone 14 Plus eSIM</td><td class="td-gb">128</td><td><span class="cond cond-A">A</span></td><td class="td-price">RD$ 22,995</td></tr>
          <tr><td class="td-model">iPhone 14 Plus eSIM</td><td class="td-gb">128</td><td><span class="cond cond-Aminus">A-</span></td><td class="td-price">RD$ 21,995</td></tr>
          <tr><td class="td-model">iPhone 14 eSIM</td><td class="td-gb">128</td><td><span class="cond cond-Aplus">A+</span></td><td class="td-price">RD$ 21,995</td></tr>
          <tr><td class="td-model">iPhone 14 eSIM</td><td class="td-gb">128</td><td><span class="cond cond-A">A</span></td><td class="td-price">RD$ 20,995</td></tr>
          <tr><td class="td-model">iPhone 14 eSIM</td><td class="td-gb">128</td><td><span class="cond cond-Aminus">A-</span></td><td class="td-price">RD$ 19,995</td></tr>

          <!-- ── iPhone 13 Series ── -->
          <tr class="sub-divider"><td colspan="4">iPhone 13 Series</td></tr>
          <tr><td class="td-model">iPhone 13 Pro Max</td><td class="td-gb">128</td><td><span class="cond cond-Aplus">A+</span></td><td class="td-price">RD$ 28,495</td></tr>
          <tr><td class="td-model">iPhone 13 Pro Max</td><td class="td-gb">128</td><td><span class="cond cond-A">A</span></td><td class="td-price">RD$ 27,495</td></tr>
          <tr><td class="td-model">iPhone 13 Pro Max</td><td class="td-gb">128</td><td><span class="cond cond-Aminus">A-</span></td><td class="td-price">RD$ 26,495</td></tr>
          <tr><td class="td-model">iPhone 13 Pro Max</td><td class="td-gb">256</td><td><span class="cond cond-Aplus">A+</span></td><td class="td-price">RD$ 31,995</td></tr>
          <tr><td class="td-model">iPhone 13 Pro Max</td><td class="td-gb">256</td><td><span class="cond cond-A">A</span></td><td class="td-price">RD$ 30,995</td></tr>
          <tr><td class="td-model">iPhone 13 Pro</td><td class="td-gb">128</td><td><span class="cond cond-Aplus">A+</span></td><td class="td-price">RD$ 23,995</td></tr>
          <tr><td class="td-model">iPhone 13 Pro</td><td class="td-gb">128</td><td><span class="cond cond-A">A</span></td><td class="td-price">RD$ 22,495</td></tr>
          <tr><td class="td-model">iPhone 13</td><td class="td-gb">128</td><td><span class="cond cond-Aplus">A+</span></td><td class="td-price">RD$ 19,995</td></tr>
          <tr><td class="td-model">iPhone 13</td><td class="td-gb">128</td><td><span class="cond cond-A">A</span></td><td class="td-price">RD$ 18,995</td></tr>
          <tr><td class="td-model">iPhone 13</td><td class="td-gb">128</td><td><span class="cond cond-Aminus">A-</span></td><td class="td-price">RD$ 17,995</td></tr>

        </tbody>
      </table>
    </div>
  </div>

  <div id="empty-state">
    <div class="emoji">🔍</div>
    <p>No se encontraron equipos con ese criterio.</p>
  </div>

</main>

<!-- FOOTER -->
<footer>
  <p style="margin-bottom:8px">
    <strong>LunderCell</strong> — Especialistas en iPhone
  </p>
  <p>
    💬 Pedidos y consultas al
    <a href="https://wa.me/18294837223" target="_blank">WhatsApp +1 (829) 483-7223</a>
  </p>
  <p style="margin-top:10px;font-size:.74rem">Precios en Pesos Dominicanos (DOP) · Sujetos a cambio sin previo aviso</p>
</footer>

<script>
  function updateCounts() {
    const tb = document.getElementById('tb-iphone');
    if (!tb) return;
    const visible = [...tb.querySelectorAll('tr:not(.row-hidden):not(.sub-divider)')].length;
    document.getElementById('cnt-iphone').textContent = visible + ' equipo' + (visible !== 1 ? 's' : '');
  }

  function filterAll() {
    const q = document.getElementById('searchInput').value.toLowerCase().trim();
    const rows = document.querySelectorAll('#tb-iphone tr:not(.sub-divider)');
    let anyVisible = 0;
    rows.forEach(row => {
      const match = q === '' || row.textContent.toLowerCase().includes(q);
      row.classList.toggle('row-hidden', !match);
      if (match) anyVisible++;
    });
    document.getElementById('empty-state').style.display = anyVisible === 0 && q !== '' ? 'block' : 'none';
    updateCounts();
  }

  updateCounts();
</script>
</body>
</html>
