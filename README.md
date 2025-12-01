<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>Ryoma Komiyama — Data Journalist</title>
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <style>
    :root {
      --bg: #f5f5f7;
      --card-bg: #ffffff;
      --accent: #2563eb;
      --accent-soft: rgba(37, 99, 235, 0.08);
      --text-main: #111827;
      --text-muted: #4b5563;
      --border-subtle: #e5e7eb;
      --shadow-soft: 0 18px 45px rgba(15, 23, 42, 0.15);
      --radius-lg: 18px;
      --radius-pill: 999px;
      --font-sans: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
    }

    * {
      box-sizing: border-box;
    }

    body {
      margin: 0;
      padding: 32px 16px 48px;
      font-family: var(--font-sans);
      background: radial-gradient(circle at top left, #e0ecff 0, #f5f5f7 40%, #f9fafb 100%);
      color: var(--text-main);
    }

    .page {
      max-width: 980px;
      margin: 0 auto;
    }

    .hero {
      background: linear-gradient(135deg, #0f172a, #111827);
      border-radius: 28px;
      padding: 28px 26px 26px;
      color: #f9fafb;
      box-shadow: var(--shadow-soft);
      position: relative;
      overflow: hidden;
    }

    .hero::after {
      content: "";
      position: absolute;
      inset: 0;
      background:
        radial-gradient(circle at top right, rgba(59, 130, 246, 0.25), transparent 55%),
        radial-gradient(circle at bottom left, rgba(34, 197, 94, 0.18), transparent 55%);
      opacity: 0.9;
      pointer-events: none;
    }

    .hero-inner {
      position: relative;
      z-index: 1;
    }

    .hero-title {
      font-size: 1.9rem;
      font-weight: 700;
      margin: 0 0 0.35rem;
      letter-spacing: 0.04em;
    }

    .hero-subtitle {
      font-size: 0.98rem;
      color: #d1d5db;
      margin-bottom: 0.9rem;
    }

    .hero-body {
      font-size: 0.95rem;
      line-height: 1.6;
      color: #e5e7eb;
      max-width: 40rem;
    }

    .hero-tags {
      display: flex;
      flex-wrap: wrap;
      gap: 0.4rem;
      margin-top: 0.9rem;
    }

    .hero-tag {
      font-size: 0.75rem;
      padding: 0.25rem 0.7rem;
      border-radius: var(--radius-pill);
      border: 1px solid rgba(148, 163, 184, 0.45);
      backdrop-filter: blur(10px);
      background: rgba(15, 23, 42, 0.5);
      color: #e5e7eb;
      white-space: nowrap;
    }

    .section {
      margin-top: 32px;
    }

    .section-header {
      display: flex;
      justify-content: space-between;
      align-items: baseline;
      gap: 1rem;
      margin-bottom: 16px;
    }

    .section-title {
      font-size: 1.1rem;
      font-weight: 650;
      display: inline-flex;
      align-items: center;
      gap: 0.5rem;
    }

    .section-title span.emoji {
      font-size: 1.2rem;
    }

    .section-kicker {
      font-size: 0.85rem;
      color: var(--text-muted);
    }

    .card-grid {
      display: grid;
      grid-template-columns: minmax(0, 1fr);
      gap: 16px;
    }

    @media (min-width: 720px) {
      .card-grid {
        grid-template-columns: repeat(2, minmax(0, 1fr));
      }
    }

    .card {
      background: var(--card-bg);
      border-radius: var(--radius-lg);
      padding: 16px 16px 18px;
      border: 1px solid var(--border-subtle);
      box-shadow: 0 10px 25px rgba(15, 23, 42, 0.08);
      display: flex;
      flex-direction: column;
      gap: 8px;
      transition: transform 0.18s ease, box-shadow 0.18s ease, border-color 0.18s ease;
      position: relative;
      overflow: hidden;
    }

    .card::before {
      content: "";
      position: absolute;
      inset: 0;
      background: linear-gradient(135deg, rgba(37, 99, 235, 0.12), transparent 55%);
      opacity: 0;
      transition: opacity 0.2s ease;
      pointer-events: none;
    }

    .card:hover {
      transform: translateY(-2px);
      box-shadow: 0 18px 40px rgba(15, 23, 42, 0.18);
      border-color: rgba(37, 99, 235, 0.45);
    }

    .card:hover::before {
      opacity: 1;
    }

    .card-eyebrow {
      font-size: 0.74rem;
      text-transform: uppercase;
      letter-spacing: 0.12em;
      color: var(--text-muted);
    }

    .card-title {
      font-size: 0.97rem;
      font-weight: 650;
      line-height: 1.35;
      margin: 0;
    }

    .card-title span.main {
      background: linear-gradient(135deg, #111827, #1d4ed8);
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
    }

    .card-body {
      font-size: 0.86rem;
      color: var(--text-muted);
      line-height: 1.6;
    }

    .card-skills {
      display: flex;
      flex-wrap: wrap;
      gap: 0.3rem;
      margin-top: 0.25rem;
    }

    .pill {
      font-size: 0.75rem;
      padding: 0.18rem 0.55rem;
      border-radius: var(--radius-pill);
      background: var(--accent-soft);
      color: #1d4ed8;
      border: 1px solid rgba(37, 99, 235, 0.2);
      white-space: nowrap;
    }

    .card-footer {
      margin-top: 6px;
      font-size: 0.8rem;
      display: flex;
      justify-content: space-between;
      align-items: center;
      gap: 0.75rem;
    }

    .card-link {
      font-size: 0.8rem;
      font-weight: 600;
      text-decoration: none;
      color: var(--accent);
      display: inline-flex;
      align-items: center;
      gap: 0.28rem;
    }

    .card-link span.arrow {
      font-size: 0.9em;
      transform: translateY(1px);
    }

    .card-meta {
      font-size: 0.75rem;
      color: var(--text-muted);
    }

    .stack-list {
      display: flex;
      flex-wrap: wrap;
      gap: 0.35rem;
    }

    .stack-pill {
      font-size: 0.78rem;
      padding: 0.2rem 0.65rem;
      border-radius: var(--radius-pill);
      border: 1px dashed rgba(148, 163, 184, 0.9);
      background: rgba(249, 250, 251, 0.9);
      color: var(--text-muted);
      white-space: nowrap;
    }

    .contact {
      background: #0f172a;
      color: #e5e7eb;
      border-radius: 22px;
      padding: 16px 18px;
      margin-top: 18px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      gap: 1rem;
      box-shadow: 0 16px 35px rgba(15, 23, 42, 0.5);
    }

    .contact-main {
      font-size: 0.86rem;
    }

    .contact-label {
      font-size: 0.78rem;
      text-transform: uppercase;
      letter-spacing: 0.18em;
      color: #9ca3af;
      margin-bottom: 3px;
    }

    .contact-mail {
      font-weight: 600;
    }

    .contact-note {
      font-size: 0.76rem;
      color: #9ca3af;
      margin-top: 2px;
    }

    .contact-chip {
      font-size: 0.78rem;
      padding: 0.3rem 0.8rem;
      border-radius: var(--radius-pill);
      border: 1px solid rgba(148, 163, 184, 0.6);
      background: rgba(15, 23, 42, 0.8);
      white-space: nowrap;
    }

    @media (max-width: 640px) {
      .hero {
        padding: 22px 18px 18px;
      }
      .hero-title {
        font-size: 1.5rem;
      }
      .hero-subtitle {
        font-size: 0.9rem;
      }
      .contact {
        flex-direction: column;
        align-items: flex-start;
      }
    }
  </style>
</head>
<body>
  <main class="page">
    <!-- HERO -->
    <header class="hero">
      <div class="hero-inner">
        <h1 class="hero-title">Ryoma Komiyama — Data Journalist</h1>
        <p class="hero-subtitle">Data-driven investigations on elections, public health, and climate risk</p>
        <p class="hero-body">
          I am a data journalist at <strong>The Asahi Shimbun</strong>, specializing in large-scale,
          data-driven investigations on <strong>elections, public health, and climate risk</strong>.
          My work combines data cleaning, causal inference, geospatial analysis, and interactive
          visualization — always built on fully reproducible R workflows. I collaborate closely with
          academic researchers and specialist reporters to keep analyses rigorous and grounded in real-world context.
        </p>
        <div class="hero-tags">
          <span class="hero-tag">Elections &amp; democracy</span>
          <span class="hero-tag">Public health &amp; excess mortality</span>
          <span class="hero-tag">Climate &amp; heat risk</span>
          <span class="hero-tag">Reproducible R workflows</span>
        </div>
      </div>
    </header>

    <!-- FEATURED INVESTIGATIONS -->
    <section class="section">
      <div class="section-header">
        <h2 class="section-title">
          <span class="emoji">📌</span>
          <span>Featured investigations</span>
        </h2>
        <p class="section-kicker">Selected projects combining reporting, statistics, and interactive visuals</p>
      </div>

      <div class="card-grid">
        <!-- Card 1 -->
        <article class="card">
          <div class="card-eyebrow">Election dynamics</div>
          <h3 class="card-title">
            <span class="main">How Japan’s First Major Populist Party Found Its Voters</span>
          </h3>
          <p class="card-body">
            A 10-wave political-attitude survey (5,200 people; 19,000 responses) revealed how a centrist
            party’s supporters migrated to a new right-leaning populist party — a shift large enough to
            reshape Japan’s party system.
          </p>
          <div class="card-skills">
            <span class="pill">Quasi-panel survey analysis</span>
            <span class="pill">Sankey visualization</span>
            <span class="pill">R</span>
            <span class="pill">Flourish</span>
          </div>
          <div class="card-footer">
            <a class="card-link" href="https://ryomakom-en.github.io/portfolio/online_sentiment" target="_blank" rel="noopener noreferrer">
              View project page <span class="arrow">↗</span>
            </a>
            <span class="card-meta">10-wave voter-flow tracking</span>
          </div>
        </article>

        <!-- Card 2 -->
        <article class="card">
          <div class="card-eyebrow">Excess mortality</div>
          <h3 class="card-title">
            <span class="main">Japan’s True COVID Toll: 135,000 Excess Deaths in Three Years</span>
          </h3>
          <p class="card-body">
            Geospatial analysis showed that rural prefectures — not major urban areas — experienced the
            highest per-capita mortality during the pandemic, quantifying the gap between official COVID
            deaths and all-cause mortality.
          </p>
          <div class="card-skills">
            <span class="pill">Excess mortality modeling</span>
            <span class="pill">Geospatial analysis (sf)</span>
            <span class="pill">R</span>
          </div>
          <div class="card-footer">
            <a class="card-link" href="https://ryomakom-en.github.io/portfolio/excess_mortality" target="_blank" rel="noopener noreferrer">
              View project page <span class="arrow">↗</span>
            </a>
            <span class="card-meta">135k excess deaths, 2020–22</span>
          </div>
        </article>

        <!-- Card 3 -->
        <article class="card">
          <div class="card-eyebrow">Climate &amp; health</div>
          <h3 class="card-title">
            <span class="main">Why Japan’s Coolest Regions Face Double the Heatstroke Risk</span>
          </h3>
          <p class="card-body">
            Analysis of <strong>790,000 emergency heatstroke transports (2008–2022)</strong> showed that
            residents in Japan’s coolest northern prefectures face nearly <strong>2× the risk</strong> of
            residents in warmer areas at the same temperature.
          </p>
          <div class="card-skills">
            <span class="pill">Climate–health modeling</span>
            <span class="pill">Nonlinear regression (GAMs)</span>
            <span class="pill">Interactive graphics</span>
          </div>
          <div class="card-footer">
            <a class="card-link" href="https://ryomakom-en.github.io/portfolio/heat_stroke" target="_blank" rel="noopener noreferrer">
              View project page <span class="arrow">↗</span>
            </a>
            <span class="card-meta">790k emergency records</span>
          </div>
        </article>

        <!-- Card 4 -->
        <article class="card">
          <div class="card-eyebrow">Causal inference</div>
          <h3 class="card-title">
            <span class="main">How a Religious Organization Delivered Decisive Votes</span>
          </h3>
          <p class="card-body">
            A quasi-experimental design comparing matched municipalities showed that support from a
            controversial religious organization delivered ~17,000 votes — enough to flip a national-level
            proportional race.
          </p>
          <div class="card-skills">
            <span class="pill">Matching &amp; causal inference</span>
            <span class="pill">Election data</span>
            <span class="pill">Uncertainty estimation</span>
          </div>
          <div class="card-footer">
            <a class="card-link" href="https://ryomakom-en.github.io/portfolio/uc_inoue" target="_blank" rel="noopener noreferrer">
              View project page <span class="arrow">↗</span>
            </a>
            <span class="card-meta">Municipal-level quasi-experiment</span>
          </div>
        </article>
      </div>
    </section>

    <!-- METHODS & TOOLS -->
    <section class="section">
      <div class="section-header">
        <h2 class="section-title">
          <span class="emoji">🛠</span>
          <span>Methods &amp; tools</span>
        </h2>
        <p class="section-kicker">What I use to move from raw data to publishable stories</p>
      </div>
      <div class="stack-list">
        <span class="stack-pill">R (tidyverse, sf, mgcv, plotly, rvest, targets)</span>
        <span class="stack-pill">Causal inference (matching, quasi-experimental designs)</span>
        <span class="stack-pill">Geospatial workflows (GIS integration, spatial clustering)</span>
        <span class="stack-pill">Interactive storytelling (Flourish, plotly, HTML/JS embeds)</span>
        <span class="stack-pill">Reproducible pipelines (GitHub Pages, GitHub Actions, markdown-first)</span>
      </div>
    </section>

    <!-- CONTACT -->
    <section class="section">
      <div class="contact">
        <div class="contact-main">
          <div class="contact-label">Contact</div>
          <div class="contact-mail">ryomakom [at] gmail.com</div>
          <div class="contact-note">
            For collaborations, newsroom projects, or speaking invitations on data journalism and reproducible workflows.
          </div>
        </div>
        <div class="contact-chip">
          This site is a public-facing data-journalism portfolio. No private CV is posted.
        </div>
      </div>
    </section>
  </main>
</body>
</html>
