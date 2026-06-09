<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Power Tool Shop — Catálogo</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Bebas+Neue&family=Inter:wght@400;500;600;700&display=swap');

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --bg: #0f0f0f;
    --surface: #1a1a1a;
    --card: #1f1f1f;
    --border: #2e2e2e;
    --red: #d0021b;
    --red-light: #ff1a33;
    --orange: #e85d04;
    --text: #f0f0f0;
    --muted: #888;
    --accent-glow: rgba(208,2,27,0.3);
  }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'Inter', sans-serif;
    min-height: 100vh;
  }

  /* HEADER */
  header {
    background: var(--surface);
    border-bottom: 2px solid var(--red);
    padding: 0 2rem;
    display: flex;
    align-items: center;
    justify-content: space-between;
    height: 72px;
    position: sticky;
    top: 0;
    z-index: 100;
  }

  .logo {
    display: flex;
    align-items: center;
    gap: 0.75rem;
    text-decoration: none;
  }
  .logo img {
    height: 54px;
    width: auto;
    object-fit: contain;
    filter: drop-shadow(0 0 8px rgba(208,2,27,0.5));
  }
  .logo-name {
    font-family: "Bebas Neue", sans-serif;
    font-size: 1.6rem;
    letter-spacing: 0.08em;
    color: var(--text);
    line-height: 1;
  }
  .logo-name em {
    color: var(--red);
    font-style: normal;
    display: block;
    font-size: 1rem;
    letter-spacing: 0.18em;
  }

  nav {
    display: flex;
    gap: 2rem;
  }

  nav a {
    color: var(--muted);
    text-decoration: none;
    font-size: 0.85rem;
    font-weight: 500;
    letter-spacing: 0.05em;
    text-transform: uppercase;
    transition: color 0.2s;
  }

  nav a:hover { color: var(--text); }

  /* HERO */
  .hero {
    padding: 5rem 2rem 3rem;
    max-width: 1200px;
    margin: 0 auto;
  }

  .hero-tag {
    font-size: 0.75rem;
    font-weight: 700;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--red);
    margin-bottom: 1rem;
    display: flex;
    align-items: center;
    gap: 0.5rem;
  }

  .hero-tag::before {
    content: '';
    display: block;
    width: 24px;
    height: 2px;
    background: var(--red);
  }

  h1 {
    font-family: 'Bebas Neue', sans-serif;
    font-size: clamp(3.5rem, 8vw, 7rem);
    line-height: 0.95;
    letter-spacing: 0.02em;
    margin-bottom: 1.5rem;
  }

  h1 span {
    color: var(--red);
  }

  .hero-sub {
    color: var(--muted);
    font-size: 1rem;
    max-width: 440px;
    line-height: 1.6;
  }

  /* FILTER BAR */
  .filter-bar {
    max-width: 1200px;
    margin: 0 auto 2.5rem;
    padding: 0 2rem;
    display: flex;
    gap: 0.75rem;
    flex-wrap: wrap;
    align-items: center;
  }

  .filter-label {
    font-size: 0.75rem;
    font-weight: 600;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    color: var(--muted);
    margin-right: 0.5rem;
  }

  .filter-btn {
    background: transparent;
    border: 1px solid var(--border);
    color: var(--muted);
    padding: 0.45rem 1rem;
    border-radius: 2px;
    font-size: 0.8rem;
    font-weight: 500;
    cursor: pointer;
    transition: all 0.2s;
    font-family: 'Inter', sans-serif;
    text-transform: uppercase;
    letter-spacing: 0.05em;
  }

  .filter-btn:hover, .filter-btn.active {
    border-color: var(--red);
    color: var(--text);
    background: rgba(208,2,27,0.1);
  }

  /* GRID */
  .grid {
    max-width: 1200px;
    margin: 0 auto;
    padding: 0 2rem 5rem;
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
    gap: 1.5px;
    background: var(--border);
  }

  /* CARD */
  .card {
    background: var(--card);
    position: relative;
    overflow: hidden;
    cursor: pointer;
    group: true;
  }

  .card-img-wrap {
    position: relative;
    aspect-ratio: 3/4;
    overflow: hidden;
    background: #111;
  }

  .card-img-wrap img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    transition: transform 0.5s cubic-bezier(0.25, 0.46, 0.45, 0.94);
    display: block;
  }

  .card:hover .card-img-wrap img {
    transform: scale(1.06);
  }

  /* Scanner line effect */
  .card::after {
    content: '';
    position: absolute;
    top: -100%;
    left: 0;
    right: 0;
    height: 2px;
    background: linear-gradient(90deg, transparent, var(--red), transparent);
    transition: top 0.4s ease;
    pointer-events: none;
    z-index: 5;
  }

  .card:hover::after {
    top: 100%;
  }

  .card-badge {
    position: absolute;
    top: 1rem;
    left: 1rem;
    background: var(--red);
    color: white;
    font-size: 0.65rem;
    font-weight: 700;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    padding: 0.3rem 0.6rem;
    z-index: 2;
  }

  .card-badge.orange {
    background: var(--orange);
  }

  .card-body {
    padding: 1.25rem 1.25rem 1.5rem;
    border-top: 1px solid var(--border);
  }

  .card-brand {
    font-size: 0.7rem;
    font-weight: 700;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    color: var(--muted);
    margin-bottom: 0.35rem;
  }

  .card-name {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 1.4rem;
    letter-spacing: 0.04em;
    line-height: 1.1;
    margin-bottom: 0.5rem;
    color: var(--text);
  }

  .card-desc {
    font-size: 0.8rem;
    color: var(--muted);
    line-height: 1.5;
    margin-bottom: 1rem;
  }

  .card-model {
    font-size: 0.7rem;
    color: #555;
    font-weight: 600;
    letter-spacing: 0.08em;
    font-family: 'Courier New', monospace;
  }

  /* FOOTER */
  footer {
    background: var(--surface);
    border-top: 1px solid var(--border);
    padding: 2rem;
    text-align: center;
    color: var(--muted);
    font-size: 0.8rem;
    letter-spacing: 0.05em;
  }

  @media (max-width: 600px) {
    nav { display: none; }
    h1 { font-size: 3.5rem; }
    .grid { grid-template-columns: 1fr 1fr; }
    .card-name { font-size: 1.1rem; }
  }

  .card-price-static {
    margin-top: 0.75rem;
    font-family: 'Bebas Neue', sans-serif;
    font-size: 1.5rem;
    letter-spacing: 0.06em;
    color: #d0021b;
    padding: 0.3rem 0;
  }
</style>
</head>
<body>

<header>
  <div class="logo">
    <img src="data:image/jpeg;base64,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" alt="Power Tool Shop">
    <div class="logo-name">Power Tool<em>SHOP</em></div>
  </div>
  <nav>
    <a href="#">Catálogo</a>
    <a href="#">Marcas</a>
    <a href="#">Contacto</a>
  </nav>
</header>

<section class="hero">
  <div class="hero-tag">Colección 2025</div>
  <h1>Herramientas<br>de <span>Trabajo</span><br>Real</h1>
  <p class="hero-sub">Equipo profesional Milwaukee, Truper y Husky — seleccionado para quien trabaja en serio.</p>
</section>

<div class="filter-bar">
  <span class="filter-label">Filtrar:</span>
  <button class="filter-btn active" onclick="filterCards('all', this)">Todo</button>
  <button class="filter-btn" onclick="filterCards('milwaukee', this)">Milwaukee</button>
  <button class="filter-btn" onclick="filterCards('truper', this)">Truper</button>
  <button class="filter-btn" onclick="filterCards('husky', this)">Husky</button>
  <button class="filter-btn" onclick="filterCards('accesorios', this)">Accesorios</button>
  <button class="filter-btn" onclick="filterCards('electricidad', this)">Electricidad</button>
</div>

<main class="grid" id="catalog">

  <div class="card" data-tags="milwaukee accesorios">
    <div class="card-img-wrap">
      <img src="IMG_8921.JPEG" alt="Milwaukee Compact Utility Pouch" loading="lazy">
      <div class="card-badge">Milwaukee</div>
    </div>
    <div class="card-body">
      <div class="card-brand">Milwaukee</div>
      <div class="card-name">Compact Utility Pouch</div>
      <div class="card-desc">Porta herramientas compacto con material balístico 1680D. Costuras remachadas 4× más resistentes y clip de cinturón de acceso rápido.</div>
      <div class="card-model">SKU: 48-22-8118</div>
      <div class="card-price-static">$550</div>
    </div>
  </div>

  <div class="card" data-tags="milwaukee accesorios">
    <div class="card-img-wrap">
      <img src="IMG_8920.JPEG" alt="Milwaukee Shockwave PH2 Bits" loading="lazy">
      <div class="card-badge">Milwaukee</div>
    </div>
    <div class="card-body">
      <div class="card-brand">Milwaukee · Shockwave</div>
      <div class="card-name">Impact Bits PH2 1"</div>
      <div class="card-desc">Puntas de impacto Ultimate Fit con zona de absorción de torque pico. Pack de 5 puntas Phillips #2 de 1 pulgada.</div>
      <div class="card-model">SKU: 48-32-4601</div>
      <div class="card-price-static">$110</div>
    </div>
  </div>

  <div class="card" data-tags="husky accesorios">
    <div class="card-img-wrap">
      <img src="IMG_8919.JPEG" alt="Husky Zipper Pouches" loading="lazy">
      <div class="card-badge orange">Husky</div>
    </div>
    <div class="card-body">
      <div class="card-brand">Husky</div>
      <div class="card-name">Zipper Pouches Set</div>
      <div class="card-desc">Set de bolsas organizadoras con cierre de alto desempeño. Tela resistente y múltiples compartimentos para accesorios y consumibles.</div>
      <div class="card-model">Husky Tools</div>
      <div class="card-price-static">$200</div>
    </div>
  </div>

  <div class="card" data-tags="milwaukee accesorios">
    <div class="card-img-wrap">
      <img src="IMG_8917.JPEG" alt="Milwaukee Inkzall Markers" loading="lazy">
      <div class="card-badge">Milwaukee</div>
    </div>
    <div class="card-body">
      <div class="card-brand">Milwaukee · Inkzall</div>
      <div class="card-name">Marcadores de Obra</div>
      <div class="card-desc">Marcadores con punta fina resistentes a la obstrucción. Escriben sobre polvo, superficies mojadas y grasosas. Pack 4 colores + pack 2 negros.</div>
      <div class="card-model">SKU: 48-22-3105</div>
      <div class="card-price-static">$115 y $200</div>
    </div>
  </div>

  <div class="card" data-tags="truper electricidad">
    <div class="card-img-wrap">
      <img src="IMG_8916.JPEG" alt="Truper Automatic Wire Stripper" loading="lazy">
      <div class="card-badge orange">Truper</div>
    </div>
    <div class="card-body">
      <div class="card-brand">Truper</div>
      <div class="card-name">Pela Cables Automático</div>
      <div class="card-desc">Pinza pelacables automática para calibres 22–10 AWG. Pela, corta y crimpa. Tope ajustable de longitud y 3 mordazas de crimpar.</div>
      <div class="card-model">SKU: 17360 · PEC-AUT</div>
      <div class="card-price-static">$320</div>
    </div>
  </div>

  <div class="card" data-tags="milwaukee accesorios">
    <div class="card-img-wrap">
      <img src="IMG_8915.JPEG" alt="Milwaukee Fastback Hawkbill Knife" loading="lazy">
      <div class="card-badge">Milwaukee</div>
    </div>
    <div class="card-body">
      <div class="card-brand">Milwaukee · Fastback</div>
      <div class="card-name">Navaja Hawkbill Punta Roma</div>
      <div class="card-desc">Navaja plegable con filo curvo tipo halcón y punta redondeada. Apertura press-and-flip de un solo dedo. Hoja de acero inoxidable con seguro liner lock.</div>
      <div class="card-model">SKU: 48-22-1526</div>
      <div class="card-price-static">$500</div>
    </div>
  </div>

  <div class="card" data-tags="milwaukee accesorios">
    <div class="card-img-wrap">
      <img src="IMG_8912.JPEG" alt="Milwaukee Hammer Drill Bits Concrete" loading="lazy">
      <div class="card-badge">Milwaukee</div>
    </div>
    <div class="card-body">
      <div class="card-brand">Milwaukee · Shockwave</div>
      <div class="card-name">Brocas Percutoras Concreto</div>
      <div class="card-desc">Set de 5 brocas para concreto con vida útil hasta 9× mayor. Medidas: 5/32", 3/16", 1/4", 5/16" y 3/8". Compatible con Impact Duty.</div>
      <div class="card-model">SKU: 48-20-9051</div>
      <div class="card-price-static">$700</div>
    </div>
  </div>

  <div class="card" data-tags="milwaukee electricidad">
    <div class="card-img-wrap">
      <img src="IMG_8910.JPEG" alt="Milwaukee Compact Wire Stripper" loading="lazy">
      <div class="card-badge">Milwaukee</div>
    </div>
    <div class="card-body">
      <div class="card-brand">Milwaukee</div>
      <div class="card-name">Pela Cables Compacto</div>
      <div class="card-desc">Pelacables compacto de precisión calibres 10–24 AWG. Pelado limpio y exacto con resorte de ajuste automático integrado.</div>
      <div class="card-model">SKU: 48-22-3044</div>
      <div class="card-price-static">$460</div>
    </div>
  </div>

  <div class="card" data-tags="milwaukee accesorios">
    <div class="card-img-wrap">
      <img src="IMG_8909.JPEG" alt="Milwaukee 43pc Impact Bit Set" loading="lazy">
      <div class="card-badge">Milwaukee</div>
    </div>
    <div class="card-body">
      <div class="card-brand">Milwaukee · Shockwave</div>
      <div class="card-name">Set 43 Puntas de Impacto</div>
      <div class="card-desc">Set completo Ultimate Fit de 43 piezas: Phillips, Torx, cuadradas y planas. Estuche compatible con organizadores Packout.</div>
      <div class="card-model">SKU: 48-32-4033</div>
      <div class="card-price-static">$655</div>
     
    </div>
  </div>

  <div class="card" data-tags="milwaukee accesorios">
    <div class="card-img-wrap">
      <img src="IMG_8907.JPEG" alt="Milwaukee 43pc Impact Bit Set Open" loading="lazy">
      <div class="card-badge">Milwaukee</div>
    </div>
    <div class="card-body">
      <div class="card-brand">Milwaukee · Shockwave</div>
      <div class="card-name">Set 43 Puntas — Vista Interior</div>
      <div class="card-desc">Vista del organizador interior: hileras de puntas PH2, SQ3, T25 y más. Estuche apilable diseñado para el sistema PACKOUT.</div>
      <div class="card-model">SKU: 48-32-4033</div>
      <div class="card-price-static">$530</div>
    </div>
  </div>

</main>

<section style="background:#111; border-top:2px solid #d0021b; padding:4rem 2rem; text-align:center;">
  <div style="max-width:700px; margin:0 auto;">
    <div style="font-family:Bebas Neue,sans-serif; font-size:0.8rem; letter-spacing:0.25em; text-transform:uppercase; color:#d0021b; margin-bottom:1rem;">&#128295; Herramientas Profesionales</div>
    <h2 style="font-family:Bebas Neue,sans-serif; font-size:clamp(2.5rem,6vw,4.5rem); color:#f0f0f0; line-height:1; margin-bottom:1.2rem; letter-spacing:0.03em;">Power Tool Shop<br><span style="color:#d0021b;">Queda a tu disposici&#243;n</span></h2>
    <p style="color:#f0f0f0; font-size:1.1rem; font-weight:600; letter-spacing:0.04em; margin-bottom:2rem; background:rgba(208,2,27,0.12); display:inline-block; padding:0.7rem 1.5rem; border-left:3px solid #d0021b;">&#128296; Podemos conseguirte todo tipo de herramienta</p>
    <div style="display:flex; gap:1.5rem; justify-content:center; flex-wrap:wrap; margin-top:1rem;">
      <a href="tel:4623337763" style="display:flex; align-items:center; gap:0.6rem; background:#d0021b; color:#fff; font-family:Bebas Neue,sans-serif; font-size:1.1rem; letter-spacing:0.1em; padding:0.9rem 2rem; text-decoration:none;">
        &#128222; 462 333 7763</a>
      <a href="https://www.instagram.com/powertool_shop?igsh=MXRrNGd0eXBicGE0Zg%3D%3D&amp;utm_source=qr" target="_blank" rel="noopener" style="display:flex; align-items:center; gap:0.6rem; border:1px solid #833ab4; color:#c13584; font-family:Bebas Neue,sans-serif; font-size:1.1rem; letter-spacing:0.1em; padding:0.9rem 2rem; text-decoration:none; background:rgba(193,53,132,0.08);">
        &#128247; @powertool_shop</a>
    </div>
  </div>
</section>

<footer>
  Power Tool Shop &nbsp;·&nbsp; Catálogo de Herramientas Profesionales &nbsp;·&nbsp; 2025
</footer>

<script>
function filterCards(tag, btn) {
  document.querySelectorAll('.filter-btn').forEach(b => b.classList.remove('active'));
  btn.classList.add('active');

  document.querySelectorAll('.card').forEach(card => {
    const tags = card.dataset.tags || '';
    if (tag === 'all' || tags.includes(tag)) {
      card.style.display = '';
    } else {
      card.style.display = 'none';
    }
  });
}
</script>

</body>
</html>
