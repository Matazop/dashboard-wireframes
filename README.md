<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Puy du Fou — Performance A/B · Direction</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,700;0,900;1,700&family=DM+Sans:wght@300;400;500;600&display=swap" rel="stylesheet">
<style>
  :root {
    --gold: #C9973A;
    --gold-light: #E8C97A;
    --gold-pale: #FAF3E0;
    --dark: #1A1208;
    --ink: #2D2416;
    --charcoal: #4A3F30;
    --muted: #8A7B66;
    --line: #E8DFD0;
    --bg: #F9F5EE;
    --white: #FFFFFF;
    --green: #2D7A4F;
    --green-light: #E8F5EE;
    --red: #B83232;
    --red-light: #FAEAEA;
    --amber: #C96A1A;
    --amber-light: #FDF0E5;
    --blue: #1A4A7A;
    --blue-light: #E8F0FA;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    font-family: 'DM Sans', sans-serif;
    background: var(--bg);
    color: var(--ink);
    min-height: 100vh;
  }

  /* ── HEADER ── */
  header {
    background: var(--dark);
    padding: 0 48px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    height: 64px;
    border-bottom: 2px solid var(--gold);
    position: sticky;
    top: 0;
    z-index: 100;
  }

  .logo-area {
    display: flex;
    align-items: center;
    gap: 14px;
  }

  .logo-flamme {
    width: 28px;
    height: 28px;
    background: linear-gradient(135deg, var(--gold), var(--gold-light));
    clip-path: polygon(50% 0%, 80% 30%, 100% 60%, 70% 100%, 30% 100%, 0% 60%, 20% 30%);
  }

  .logo-text {
    font-family: 'Playfair Display', serif;
    color: var(--white);
    font-size: 15px;
    letter-spacing: 0.04em;
  }

  .logo-text span { color: var(--gold-light); font-weight: 300; }

  .header-right {
    display: flex;
    align-items: center;
    gap: 20px;
  }

  .header-date {
    font-size: 12px;
    color: rgba(255,255,255,.45);
    font-weight: 300;
  }

  .header-date strong { color: var(--gold-light); font-weight: 500; }

  .btn-sm {
    background: none;
    border: 1px solid rgba(201,151,58,.4);
    color: var(--gold-light);
    padding: 6px 14px;
    border-radius: 4px;
    font-family: 'DM Sans', sans-serif;
    font-size: 12px;
    cursor: pointer;
    transition: all .18s;
  }
  .btn-sm:hover { background: var(--gold); color: var(--dark); border-color: var(--gold); }

  /* ── MAIN ── */
  main {
    max-width: 1200px;
    margin: 0 auto;
    padding: 40px 48px 100px;
  }

  .page-title {
    margin-bottom: 32px;
  }

  .page-title h1 {
    font-family: 'Playfair Display', serif;
    font-size: 26px;
    color: var(--dark);
    margin-bottom: 6px;
  }

  .page-title p {
    font-size: 13px;
    color: var(--muted);
    font-weight: 300;
  }

  .page-title p strong { color: var(--charcoal); font-weight: 500; }

  /* ── SECTION LABEL ── */
  .section-label {
    font-size: 10px;
    font-weight: 600;
    text-transform: uppercase;
    letter-spacing: 0.14em;
    color: var(--muted);
    margin-bottom: 14px;
    display: flex;
    align-items: center;
    gap: 10px;
  }

  .section-label::after {
    content: '';
    flex: 1;
    height: 1px;
    background: var(--line);
  }

  /* ── KPI HERO ── */
  .kpi-hero {
    display: grid;
    grid-template-columns: 2fr 1fr 1fr;
    border-radius: 14px;
    overflow: hidden;
    margin-bottom: 28px;
    box-shadow: 0 6px 32px rgba(26,18,8,.08);
    border: 1px solid var(--line);
    gap: 1px;
    background: var(--line);
  }

  .kpi-card {
    background: var(--white);
    padding: 32px 36px;
  }

  .kpi-card.main {
    background: var(--dark);
  }

  .kpi-card-label {
    font-size: 10px;
    font-weight: 600;
    text-transform: uppercase;
    letter-spacing: 0.12em;
    margin-bottom: 14px;
  }

  .kpi-card.main .kpi-card-label { color: var(--gold); }
  .kpi-card:not(.main) .kpi-card-label { color: var(--muted); }

  .kpi-big {
    font-family: 'Playfair Display', serif;
    font-weight: 900;
    line-height: 1;
    margin-bottom: 10px;
  }

  .kpi-card.main .kpi-big {
    font-size: 58px;
    color: var(--gold-light);
  }

  .kpi-card:not(.main) .kpi-big {
    font-size: 44px;
    color: var(--dark);
  }

  .kpi-unit {
    font-family: 'DM Sans', sans-serif;
    font-weight: 300;
    opacity: .6;
  }

  .kpi-card.main .kpi-unit { font-size: 22px; }
  .kpi-card:not(.main) .kpi-unit { font-size: 18px; }

  .kpi-sub {
    font-size: 13px;
    font-weight: 300;
    line-height: 1.5;
  }

  .kpi-card.main .kpi-sub { color: rgba(255,255,255,.5); }
  .kpi-card:not(.main) .kpi-sub { color: var(--muted); }

  /* Pill sous-KPI */
  .kpi-pills {
    display: flex;
    flex-wrap: wrap;
    gap: 6px;
    margin-top: 16px;
  }

  .pill {
    display: inline-flex;
    align-items: center;
    gap: 5px;
    padding: 5px 10px;
    border-radius: 20px;
    font-size: 12px;
    font-weight: 500;
  }

  .pill .dot {
    width: 7px;
    height: 7px;
    border-radius: 50%;
  }

  .pill.green { background: var(--green-light); color: var(--green); }
  .pill.green .dot { background: var(--green); }
  .pill.red { background: var(--red-light); color: var(--red); }
  .pill.red .dot { background: var(--red); }
  .pill.neutral { background: var(--line); color: var(--charcoal); }
  .pill.neutral .dot { background: var(--muted); }

  /* Séparateur horizontal dans la carte */
  .kpi-divider { height: 1px; background: rgba(255,255,255,.08); margin: 20px 0; }

  /* Gain / Pertes détail dans hero */
  .gain-loss-row {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 16px;
    margin-top: 20px;
  }

  .gain-box {
    border-radius: 8px;
    padding: 14px 16px;
  }

  .gain-box.g { background: rgba(45,122,79,.12); }
  .gain-box.l { background: rgba(184,50,50,.12); }

  .gain-box-label {
    font-size: 10px;
    font-weight: 600;
    text-transform: uppercase;
    letter-spacing: .1em;
    margin-bottom: 4px;
  }

  .gain-box.g .gain-box-label { color: #7DC9A0; }
  .gain-box.l .gain-box-label { color: #E08888; }

  .gain-box-value {
    font-family: 'Playfair Display', serif;
    font-size: 22px;
    font-weight: 700;
  }

  .gain-box.g .gain-box-value { color: #A6E0C0; }
  .gain-box.l .gain-box-value { color: #E8A0A0; }

  /* ── KPI CARD SECONDAIRE · taux de succès ── */
  .success-ring {
    display: flex;
    align-items: center;
    gap: 20px;
    margin-top: 12px;
  }

  /* Stat minis pour la 3e carte */
  .mini-stat-list {
    display: flex;
    flex-direction: column;
    gap: 10px;
    margin-top: 14px;
  }

  .mini-stat {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 10px 14px;
    background: var(--bg);
    border-radius: 8px;
    font-size: 12px;
  }

  .mini-stat-label { color: var(--charcoal); font-weight: 400; }
  .mini-stat-value { font-weight: 600; color: var(--dark); }
  .mini-stat-value.g { color: var(--green); }
  .mini-stat-value.r { color: var(--red); }

  /* ── DECISION CARDS ── */
  .decision-row {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    gap: 16px;
    margin-bottom: 32px;
  }

  .dec-card {
    border-radius: 10px;
    padding: 22px 24px;
    position: relative;
    overflow: hidden;
  }

  .dec-card.deploy { background: var(--green); color: white; }
  .dec-card.watch  { background: var(--blue);  color: white; }
  .dec-card.stop   { background: var(--red-light); border: 1px solid var(--red); color: var(--red); }

  .dec-label {
    font-size: 10px;
    font-weight: 700;
    text-transform: uppercase;
    letter-spacing: .1em;
    opacity: .75;
    margin-bottom: 8px;
  }

  .dec-count {
    font-family: 'Playfair Display', serif;
    font-size: 40px;
    font-weight: 900;
    line-height: 1;
    margin-bottom: 4px;
  }

  .dec-sub { font-size: 12px; opacity: .8; }

  .dec-icon {
    position: absolute;
    right: 18px;
    top: 50%;
    transform: translateY(-50%);
    font-size: 40px;
    opacity: .12;
  }

  /* ── TOP TESTS ── */
  .grid-2 {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 20px;
    margin-bottom: 20px;
  }

  .card {
    background: var(--white);
    border-radius: 12px;
    padding: 28px;
    border: 1px solid var(--line);
    box-shadow: 0 2px 10px rgba(26,18,8,.04);
  }

  .card h2 {
    font-family: 'Playfair Display', serif;
    font-size: 16px;
    color: var(--dark);
    margin-bottom: 4px;
  }

  .card-desc {
    font-size: 12px;
    color: var(--muted);
    font-weight: 300;
    margin-bottom: 20px;
  }

  .test-list { list-style: none; }

  .test-row {
    display: grid;
    grid-template-columns: 22px 1fr 72px 68px;
    align-items: center;
    gap: 10px;
    padding: 12px 0;
    border-bottom: 1px solid var(--line);
    cursor: pointer;
    transition: background .15s;
    border-radius: 6px;
  }

  .test-row:last-child { border-bottom: none; }

  .test-row:hover {
    background: var(--gold-pale);
    padding: 12px 10px;
    margin: 0 -10px;
  }

  .test-rank {
    font-size: 11px;
    font-weight: 600;
    color: var(--muted);
    text-align: center;
  }

  .test-rank.gold {
    font-family: 'Playfair Display', serif;
    font-size: 14px;
    color: var(--gold);
  }

  .test-name { font-size: 13px; font-weight: 500; color: var(--ink); }
  .test-name small { display: block; font-size: 11px; color: var(--muted); font-weight: 300; }

  .test-bar-bg {
    height: 4px;
    background: var(--line);
    border-radius: 2px;
    overflow: hidden;
  }

  .test-bar-fill { height: 100%; border-radius: 2px; }
  .test-bar-fill.g { background: var(--green); }
  .test-bar-fill.r { background: var(--red); }

  .test-gain {
    font-size: 13px;
    font-weight: 600;
    text-align: right;
  }

  .test-gain.g { color: var(--green); }
  .test-gain.r { color: var(--red); }

  .btn-see-all {
    width: 100%;
    margin-top: 14px;
    padding: 10px;
    background: none;
    border: 1px solid var(--line);
    border-radius: 6px;
    font-family: 'DM Sans', sans-serif;
    font-size: 12px;
    color: var(--muted);
    cursor: pointer;
    transition: all .15s;
  }

  .btn-see-all:hover { border-color: var(--gold); color: var(--gold); }

  /* ── TIMELINE ── */
  .timeline { padding-left: 18px; position: relative; }
  .timeline::before {
    content: '';
    position: absolute;
    left: 5px;
    top: 8px;
    bottom: 8px;
    width: 1px;
    background: var(--line);
  }

  .tl-item { padding: 0 0 16px 18px; position: relative; }
  .tl-item:last-child { padding-bottom: 0; }

  .tl-dot {
    position: absolute;
    left: -13px;
    top: 4px;
    width: 9px;
    height: 9px;
    border-radius: 50%;
    border: 2px solid var(--white);
  }

  .tl-dot.g { background: var(--green); box-shadow: 0 0 0 2px var(--green-light); }
  .tl-dot.r { background: var(--red); box-shadow: 0 0 0 2px var(--red-light); }
  .tl-dot.a { background: var(--amber); box-shadow: 0 0 0 2px var(--amber-light); }

  .tl-title { font-size: 13px; font-weight: 500; color: var(--ink); margin-bottom: 2px; }
  .tl-meta { font-size: 11px; color: var(--muted); font-weight: 300; }

  /* ── PROJECTION ANNUALISÉE ── */
  .projection-section {
    margin-top: 48px;
    background: var(--dark);
    border-radius: 16px;
    overflow: hidden;
    box-shadow: 0 8px 40px rgba(26,18,8,.12);
  }

  .proj-header {
    padding: 32px 40px 24px;
    border-bottom: 1px solid rgba(255,255,255,.08);
    display: flex;
    align-items: flex-end;
    justify-content: space-between;
    gap: 20px;
  }

  .proj-header-left h2 {
    font-family: 'Playfair Display', serif;
    font-size: 20px;
    color: var(--white);
    margin-bottom: 4px;
  }

  .proj-header-left p {
    font-size: 12px;
    color: rgba(255,255,255,.4);
    font-weight: 300;
  }

  .proj-toggle {
    display: flex;
    background: rgba(255,255,255,.06);
    border-radius: 8px;
    overflow: hidden;
    border: 1px solid rgba(255,255,255,.1);
  }

  .proj-toggle-btn {
    padding: 8px 16px;
    font-family: 'DM Sans', sans-serif;
    font-size: 12px;
    font-weight: 500;
    color: rgba(255,255,255,.45);
    background: none;
    border: none;
    cursor: pointer;
    transition: all .18s;
  }

  .proj-toggle-btn.active {
    background: var(--gold);
    color: var(--dark);
  }

  .proj-body {
    padding: 32px 40px 40px;
  }

  /* Big projection number */
  .proj-hero {
    display: flex;
    align-items: flex-end;
    gap: 24px;
    margin-bottom: 32px;
  }

  .proj-main-val {
    font-family: 'Playfair Display', serif;
    font-size: 72px;
    font-weight: 900;
    color: var(--gold-light);
    line-height: 1;
  }

  .proj-main-unit {
    font-family: 'DM Sans', sans-serif;
    font-size: 24px;
    font-weight: 300;
    color: rgba(201,151,58,.6);
    margin-bottom: 10px;
  }

  .proj-hero-meta {
    margin-bottom: 12px;
  }

  .proj-hero-meta p {
    font-size: 13px;
    color: rgba(255,255,255,.5);
    font-weight: 300;
    margin-bottom: 4px;
  }

  .proj-hero-meta strong {
    color: var(--green);
    font-weight: 600;
  }

  /* Scénarios */
  .proj-scenarios {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    gap: 12px;
    margin-bottom: 28px;
  }

  .scenario {
    border-radius: 10px;
    padding: 18px 20px;
    cursor: pointer;
    transition: all .18s;
    border: 1px solid transparent;
  }

  .scenario.pessimiste { background: rgba(184,50,50,.1); border-color: rgba(184,50,50,.2); }
  .scenario.realiste   { background: rgba(201,151,58,.15); border-color: var(--gold); }
  .scenario.optimiste  { background: rgba(45,122,79,.12); border-color: rgba(45,122,79,.25); }

  .scenario-label {
    font-size: 10px;
    font-weight: 700;
    text-transform: uppercase;
    letter-spacing: .1em;
    margin-bottom: 8px;
  }

  .scenario.pessimiste .scenario-label { color: #E08888; }
  .scenario.realiste   .scenario-label { color: var(--gold-light); }
  .scenario.optimiste  .scenario-label { color: #7DC9A0; }

  .scenario-val {
    font-family: 'Playfair Display', serif;
    font-size: 26px;
    font-weight: 700;
    color: var(--white);
    margin-bottom: 4px;
  }

  .scenario-desc {
    font-size: 11px;
    color: rgba(255,255,255,.4);
    font-weight: 300;
    line-height: 1.4;
  }

  .scenario.realiste .scenario-desc { color: rgba(255,255,255,.6); }

  .scenario-badge {
    display: inline-block;
    margin-top: 8px;
    font-size: 9px;
    font-weight: 700;
    padding: 2px 7px;
    border-radius: 3px;
    text-transform: uppercase;
    letter-spacing: .06em;
    background: var(--gold);
    color: var(--dark);
  }

  /* Bar chart projection */
  .proj-chart {
    display: flex;
    align-items: flex-end;
    gap: 8px;
    height: 100px;
    margin-bottom: 8px;
    padding: 0 2px;
  }

  .proj-bar-wrap {
    flex: 1;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 6px;
    height: 100%;
    justify-content: flex-end;
  }

  .proj-bar {
    width: 100%;
    border-radius: 4px 4px 0 0;
    transition: height .4s ease;
    min-height: 4px;
  }

  .proj-bar.actual { background: var(--gold); }
  .proj-bar.proj   { background: rgba(201,151,58,.3); border: 1px dashed rgba(201,151,58,.5); }

  .proj-bar-label {
    font-size: 9px;
    color: rgba(255,255,255,.35);
    font-weight: 400;
    text-align: center;
  }

  .proj-bar-val {
    font-size: 10px;
    font-weight: 600;
    color: rgba(255,255,255,.6);
    text-align: center;
  }

  .proj-chart-note {
    display: flex;
    gap: 16px;
    align-items: center;
  }

  .chart-legend-item {
    display: flex;
    align-items: center;
    gap: 6px;
    font-size: 11px;
    color: rgba(255,255,255,.4);
  }

  .chart-legend-swatch {
    width: 20px;
    height: 6px;
    border-radius: 2px;
  }

  .chart-legend-swatch.actual { background: var(--gold); }
  .chart-legend-swatch.proj   { background: rgba(201,151,58,.3); border: 1px dashed rgba(201,151,58,.5); }

  /* Hypothèses */
  .proj-hypotheses {
    margin-top: 24px;
    padding-top: 20px;
    border-top: 1px solid rgba(255,255,255,.07);
    display: flex;
    gap: 12px;
    flex-wrap: wrap;
  }

  .hyp-tag {
    display: flex;
    align-items: center;
    gap: 6px;
    padding: 6px 12px;
    background: rgba(255,255,255,.05);
    border: 1px solid rgba(255,255,255,.08);
    border-radius: 20px;
    font-size: 11px;
    color: rgba(255,255,255,.5);
  }

  .hyp-tag span { color: var(--gold-light); font-weight: 500; }

  /* ── FOOTER ── */
  .dash-footer {
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-top: 48px;
    padding-top: 20px;
    border-top: 1px solid var(--line);
  }

  .dash-footer p { font-size: 11px; color: var(--muted); }
  .dash-footer a { color: var(--gold); text-decoration: none; }

  /* Animations */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(14px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  .kpi-hero, .decision-row, .grid-2, .projection-section {
    animation: fadeUp .45s ease both;
  }

  .kpi-hero { animation-delay: .05s; }
  .decision-row { animation-delay: .1s; }
  .grid-2 { animation-delay: .15s; }
  .projection-section { animation-delay: .2s; }
</style>
</head>
<body>

<!-- HEADER -->
<header>
  <div class="logo-area">
    <div class="logo-flamme"></div>
    <div class="logo-text">Puy du Fou <span>· Performance A/B</span></div>
  </div>
  <div class="header-right">
    <div class="header-date">Données au <strong>17 fév. 2026 · 14:34</strong></div>
    <button class="btn-sm">↻ Rafraîchir</button>
  </div>
</header>

<!-- MAIN -->
<main>

  <!-- PAGE TITLE -->
  <div class="page-title">
    <h1>Tableau de bord A/B Tests</h1>
    <p>Indicateur : <strong>Achats finaux</strong> · 44 tests analysés · mise à jour automatique toutes les 30 min</p>
  </div>

  <!-- ── VUE D'ENSEMBLE ── -->
  <div class="section-label">Vue d'ensemble</div>

  <div class="kpi-hero">

    <!-- CARTE PRINCIPALE : Gains de la période -->
    <div class="kpi-card main">
      <div class="kpi-card-label">Gains nets · période en cours</div>
      <div class="kpi-big">+3,3 <span class="kpi-unit">M€</span></div>
      <div class="kpi-sub">Solde net des gains et pertes générés par l'ensemble des tests sur la période</div>
      <div class="gain-loss-row">
        <div class="gain-box g">
          <div class="gain-box-label">Gains</div>
          <div class="gain-box-value">+3,59 M€</div>
        </div>
        <div class="gain-box l">
          <div class="gain-box-label">Pertes</div>
          <div class="gain-box-value">−341 K€</div>
        </div>
      </div>
    </div>

    <!-- CARTE 2 : Taux de succès -->
    <div class="kpi-card">
      <div class="kpi-card-label">Taux de succès</div>
      <div class="kpi-big" style="font-size:44px; color: var(--green);">47 <span class="kpi-unit" style="font-size:18px;">%</span></div>
      <div class="kpi-sub" style="margin-bottom:16px">des tests testés génèrent un gain positif</div>

      <div class="mini-stat-list">
        <div class="mini-stat">
          <span class="mini-stat-label">🟢 Tests gagnants</span>
          <span class="mini-stat-value g">21 / 44</span>
        </div>
        <div class="mini-stat">
          <span class="mini-stat-label">🔴 Tests perdants</span>
          <span class="mini-stat-value r">18 / 44</span>
        </div>
        <div class="mini-stat">
          <span class="mini-stat-label">⚪ Tests neutres</span>
          <span class="mini-stat-value">5 / 44</span>
        </div>
      </div>
    </div>

    <!-- CARTE 3 : Avancement & volume -->
    <div class="kpi-card">
      <div class="kpi-card-label">Activité des tests</div>
      <div class="kpi-big" style="font-size:44px; color: var(--dark);">44</div>
      <div class="kpi-sub" style="margin-bottom:16px">tests actifs ou terminés</div>

      <div class="mini-stat-list">
        <div class="mini-stat">
          <span class="mini-stat-label">▶ En ligne</span>
          <span class="mini-stat-value">29 tests</span>
        </div>
        <div class="mini-stat">
          <span class="mini-stat-label">⏸ Dévié / arrêté</span>
          <span class="mini-stat-value">10 tests</span>
        </div>
        <div class="mini-stat">
          <span class="mini-stat-label">⏱ Durée moyenne</span>
          <span class="mini-stat-value">38 jours</span>
        </div>
      </div>
    </div>

  </div>

  <!-- ── ACTIONS RECOMMANDÉES ── -->
  <div class="section-label">Actions recommandées</div>
  <div class="decision-row">
    <div class="dec-card deploy">
      <div class="dec-label">✅ À déployer maintenant</div>
      <div class="dec-count">3</div>
      <div class="dec-sub">Tests validés, résultats solides</div>
      <div class="dec-icon">🚀</div>
    </div>
    <div class="dec-card watch">
      <div class="dec-label">👁 À surveiller</div>
      <div class="dec-count">7</div>
      <div class="dec-sub">En cours · manque de recul</div>
      <div class="dec-icon">📡</div>
    </div>
    <div class="dec-card stop">
      <div class="dec-label">🛑 À arrêter</div>
      <div class="dec-count">2</div>
      <div class="dec-sub">Impact négatif confirmé</div>
      <div class="dec-icon">⛔</div>
    </div>
  </div>

  <!-- ── TOP TESTS + CHRONOLOGIE ── -->
  <div class="section-label">Détail des tests</div>
  <div class="grid-2">

    <!-- TOP 5 -->
    <div class="card">
      <h2>🏆 Tests les plus rentables</h2>
      <div class="card-desc">Top 5 par gain sur la période · Achats finaux</div>
      <ul class="test-list">
        <li class="test-row">
          <div class="test-rank gold">1</div>
          <div class="test-name">FR-ALL-0023 <small>27 jours · En ligne</small></div>
          <div class="test-bar-bg"><div class="test-bar-fill g" style="width:100%"></div></div>
          <div class="test-gain g">+6,0 M€</div>
        </li>
        <li class="test-row">
          <div class="test-rank gold">2</div>
          <div class="test-name">VEL-ALL-0013 v2 <small>1 jour · En ligne</small></div>
          <div class="test-bar-bg"><div class="test-bar-fill g" style="width:50%"></div></div>
          <div class="test-gain g">+3,0 M€</div>
        </li>
        <li class="test-row">
          <div class="test-rank gold">3</div>
          <div class="test-name">CTA "Compléter votre commande" <small>176 jours · En ligne</small></div>
          <div class="test-bar-bg"><div class="test-bar-fill g" style="width:47%"></div></div>
          <div class="test-gain g">+2,8 M€</div>
        </li>
        <li class="test-row">
          <div class="test-rank">4</div>
          <div class="test-name">FR-ALL-0021 <small>33 jours · Dévié</small></div>
          <div class="test-bar-bg"><div class="test-bar-fill g" style="width:32%"></div></div>
          <div class="test-gain g">+1,9 M€</div>
        </li>
        <li class="test-row">
          <div class="test-rank">5</div>
          <div class="test-name">FR-ALL-0025 <small>19 jours · En ligne</small></div>
          <div class="test-bar-bg"><div class="test-bar-fill g" style="width:4%"></div></div>
          <div class="test-gain g">+223 K€</div>
        </li>
      </ul>
      <button class="btn-see-all">Voir les 44 tests →</button>
    </div>

    <!-- COLONNE DROITE -->
    <div style="display:flex;flex-direction:column;gap:20px;">

      <!-- Tests à stopper -->
      <div class="card">
        <h2>⚠️ Tests à stopper</h2>
        <div class="card-desc">Impact négatif confirmé · action requise</div>
        <ul class="test-list">
          <li class="test-row">
            <div class="test-rank" style="color:var(--red)">▼</div>
            <div class="test-name">VEL-ALL-0011 <small>Impact négatif confirmé</small></div>
            <div class="test-bar-bg"><div class="test-bar-fill r" style="width:100%"></div></div>
            <div class="test-gain r">−151 K€</div>
          </li>
          <li class="test-row">
            <div class="test-rank" style="color:var(--red)">▼</div>
            <div class="test-name">FR-ALL-0008 <small>Impact négatif confirmé</small></div>
            <div class="test-bar-bg"><div class="test-bar-fill r" style="width:36%"></div></div>
            <div class="test-gain r">−55 K€</div>
          </li>
        </ul>
      </div>

      <!-- Chronologie -->
      <div class="card" style="flex:1">
        <h2>Dernières décisions</h2>
        <div class="card-desc">7 derniers jours</div>
        <div class="timeline">
          <div class="tl-item">
            <div class="tl-dot g"></div>
            <div class="tl-title">CTA "Compléter votre commande" — Déployé</div>
            <div class="tl-meta">14 fév. · +2,7 M€ sur la période</div>
          </div>
          <div class="tl-item">
            <div class="tl-dot a"></div>
            <div class="tl-title">FR-ALL-0021 — Résultats insuffisants, dévié</div>
            <div class="tl-meta">12 fév. · Surveillance activée</div>
          </div>
          <div class="tl-item">
            <div class="tl-dot g"></div>
            <div class="tl-title">VEL-ALL-0013 v2 — Test lancé</div>
            <div class="tl-meta">17 fév. · 40 % du trafic engagé</div>
          </div>
          <div class="tl-item">
            <div class="tl-dot r"></div>
            <div class="tl-title">VEL-ALL-0011 — Arrêt recommandé</div>
            <div class="tl-meta">10 fév. · −151 K€ confirmés</div>
          </div>
        </div>
      </div>

    </div>
  </div>

  <!-- ── PROJECTION ANNUALISÉE ── -->
  <div class="projection-section">

    <div class="proj-header">
      <div class="proj-header-left">
        <h2>Projection annualisée</h2>
        <p>Si les tests gagnants actuels sont déployés · basé sur les données de la période en cours</p>
      </div>
      <div class="proj-toggle">
        <button class="proj-toggle-btn">Tests déployés</button>
        <button class="proj-toggle-btn active">Tous les gagnants</button>
        <button class="proj-toggle-btn">Scénarios</button>
      </div>
    </div>

    <div class="proj-body">

      <!-- Chiffre clé + mini chart côte à côte -->
      <div style="display:grid;grid-template-columns:1fr 1fr;gap:40px;align-items:start;margin-bottom:32px;">

        <div>
          <div style="font-size:11px;font-weight:600;text-transform:uppercase;letter-spacing:.12em;color:var(--gold);margin-bottom:12px;">Gain annualisé estimé</div>
          <div style="display:flex;align-items:flex-end;gap:8px;margin-bottom:12px;">
            <div class="proj-main-val">+13,9</div>
            <div class="proj-main-unit">M€ / an</div>
          </div>
          <div style="font-size:13px;color:rgba(255,255,255,.5);font-weight:300;line-height:1.6;margin-bottom:16px;">
            Estimation basée sur <strong style="color:var(--gold-light);font-weight:500;">21 tests gagnants</strong> déployés simultanément, extrapolés sur 12 mois.
          </div>
          <div style="display:flex;gap:10px;flex-wrap:wrap;">
            <div class="pill green" style="background:rgba(45,122,79,.2);color:#7DC9A0;">+3,59 M€ déjà générés</div>
            <div class="pill neutral" style="background:rgba(255,255,255,.07);color:rgba(255,255,255,.5);">× 3,9 extrapolé</div>
          </div>
        </div>

        <!-- Mini bar chart mensuel -->
        <div>
          <div style="font-size:11px;font-weight:600;text-transform:uppercase;letter-spacing:.12em;color:rgba(255,255,255,.35);margin-bottom:16px;">Évolution mensuelle projetée</div>
          <div class="proj-chart">
            <!-- Mois réels -->
            <div class="proj-bar-wrap">
              <div class="proj-bar-val">+1,1M</div>
              <div class="proj-bar actual" style="height:55px"></div>
              <div class="proj-bar-label">Oct</div>
            </div>
            <div class="proj-bar-wrap">
              <div class="proj-bar-val">+0,9M</div>
              <div class="proj-bar actual" style="height:45px"></div>
              <div class="proj-bar-label">Nov</div>
            </div>
            <div class="proj-bar-wrap">
              <div class="proj-bar-val">+0,8M</div>
              <div class="proj-bar actual" style="height:40px"></div>
              <div class="proj-bar-label">Déc</div>
            </div>
            <div class="proj-bar-wrap">
              <div class="proj-bar-val">+0,5M</div>
              <div class="proj-bar actual" style="height:25px"></div>
              <div class="proj-bar-label">Jan</div>
            </div>
            <!-- Mois projetés -->
            <div class="proj-bar-wrap">
              <div class="proj-bar-val" style="color:rgba(201,151,58,.5)">+1,2M</div>
              <div class="proj-bar proj" style="height:60px"></div>
              <div class="proj-bar-label">Mar ▸</div>
            </div>
            <div class="proj-bar-wrap">
              <div class="proj-bar-val" style="color:rgba(201,151,58,.5)">+1,4M</div>
              <div class="proj-bar proj" style="height:70px"></div>
              <div class="proj-bar-label">Avr</div>
            </div>
            <div class="proj-bar-wrap">
              <div class="proj-bar-val" style="color:rgba(201,151,58,.5)">+1,8M</div>
              <div class="proj-bar proj" style="height:90px"></div>
              <div class="proj-bar-label">Mai</div>
            </div>
            <div class="proj-bar-wrap">
              <div class="proj-bar-val" style="color:rgba(201,151,58,.5)">+2,0M</div>
              <div class="proj-bar proj" style="height:100px"></div>
              <div class="proj-bar-label">Jun</div>
            </div>
          </div>
          <div class="proj-chart-note">
            <div class="chart-legend-item">
              <div class="chart-legend-swatch actual"></div>
              Données réelles
            </div>
            <div class="chart-legend-item">
              <div class="chart-legend-swatch proj"></div>
              Projection
            </div>
          </div>
        </div>

      </div>

      <!-- 3 SCÉNARIOS -->
      <div class="proj-scenarios">
        <div class="scenario pessimiste">
          <div class="scenario-label">Scénario prudent</div>
          <div class="scenario-val">+8,5 M€</div>
          <div class="scenario-desc">50 % des tests gagnants déployés, saisonnalité défavorable</div>
        </div>
        <div class="scenario realiste">
          <div class="scenario-label">Scénario retenu</div>
          <div class="scenario-val">+13,9 M€</div>
          <div class="scenario-desc">Tous les tests gagnants déployés · saisonnalité stable</div>
          <span class="scenario-badge">Base de travail</span>
        </div>
        <div class="scenario optimiste">
          <div class="scenario-label">Scénario favorable</div>
          <div class="scenario-val">+18,2 M€</div>
          <div class="scenario-desc">Tests gagnants + 3 nouveaux tests en cours convertis</div>
        </div>
      </div>

      <!-- HYPOTHÈSES -->
      <div class="proj-hypotheses">
        <div style="font-size:10px;font-weight:600;text-transform:uppercase;letter-spacing:.1em;color:rgba(255,255,255,.3);margin-right:4px;line-height:28px;">Hypothèses</div>
        <div class="hyp-tag">Trafic mensuel stable : <span>~375 000 visites</span></div>
        <div class="hyp-tag">Taux de conversion actuel : <span>2,8 %</span></div>
        <div class="hyp-tag">Panier moyen : <span>312 €</span></div>
        <div class="hyp-tag">Déploiement progressif : <span>30 jours</span></div>
        <div class="hyp-tag">Saisonnalité : <span>incluse</span></div>
      </div>

    </div>
  </div>

  <!-- FOOTER -->
  <div class="dash-footer">
    <p>Données Kameleoon · Snapshot 41 · 17 fév. 2026, 14:34</p>
    <p><a href="#">Accès vue technique complète →</a></p>
  </div>

</main>
</body>
</html>
