
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<style>
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0;}
:root{
  --a:#B4956A;--al:#F5EDE2;--dk:#111110;--mid:#4A4A45;--soft:#8A8A84;
  --bg:#FFFFFF;--bg2:#FAF9F7;--line:rgba(0,0,0,0.08);
}
html{scroll-behavior:smooth;}
body{font-family:'Helvetica Neue',Helvetica,Arial,sans-serif;color:var(--dk);background:var(--bg);-webkit-font-smoothing:antialiased;overflow-x:hidden;}

/* NAV */
.nav{position:fixed;top:0;left:0;right:0;background:rgba(255,255,255,0.95);backdrop-filter:blur(12px);border-bottom:1px solid var(--line);z-index:200;padding:0 24px;display:flex;align-items:center;justify-content:space-between;height:52px;}
.nav-brand{font-size:12px;font-weight:500;letter-spacing:0.1em;color:var(--dk);text-transform:uppercase;}
.nav-links{display:flex;gap:20px;}
.nav-links a{font-size:11px;text-decoration:none;color:var(--soft);letter-spacing:0.06em;text-transform:uppercase;transition:color .2s;cursor:pointer;}
.nav-links a:hover{color:var(--dk);}

/* PROGRESS */
.progress-bar{position:fixed;top:52px;left:0;right:0;height:2px;z-index:199;}
.progress-fill{height:100%;background:var(--a);width:0%;transition:width .1s linear;}

/* REVEAL */
.reveal{opacity:0;transform:translateY(28px);transition:opacity .7s ease,transform .7s ease;}
.reveal.in{opacity:1;transform:translateY(0);}
.reveal-left{opacity:0;transform:translateX(-28px);transition:opacity .7s ease,transform .7s ease;}
.reveal-left.in{opacity:1;transform:translateX(0);}
.reveal-right{opacity:0;transform:translateX(28px);transition:opacity .7s ease,transform .7s ease;}
.reveal-right.in{opacity:1;transform:translateX(0);}
.delay-1{transition-delay:.1s;}.delay-2{transition-delay:.2s;}

/* HERO */
.hero{min-height:100vh;display:flex;flex-direction:column;align-items:center;justify-content:center;text-align:center;padding:100px 24px 80px;position:relative;overflow:hidden;}
.hero-bg-text{position:absolute;font-size:clamp(80px,18vw,220px);font-weight:700;color:rgba(0,0,0,0.025);letter-spacing:-0.05em;white-space:nowrap;pointer-events:none;user-select:none;top:50%;transform:translateY(-50%);animation:bgDrift 20s ease-in-out infinite alternate;}
@keyframes bgDrift{0%{transform:translateY(-50%) translateX(-2%)}100%{transform:translateY(-50%) translateX(2%)}}
.hero-eyebrow{font-size:11px;letter-spacing:0.22em;text-transform:uppercase;color:var(--a);font-weight:500;margin-bottom:24px;animation:fadeUp .8s ease both;}
.hero-name{font-size:clamp(58px,14vw,128px);font-weight:200;line-height:.95;letter-spacing:-0.04em;margin-bottom:16px;animation:fadeUp .9s .1s ease both;}
.hero-name strong{font-weight:600;display:block;}
.hero-name .sub{font-size:clamp(22px,5vw,48px);font-weight:300;letter-spacing:0.08em;text-transform:uppercase;color:var(--a);}
.hero-line{width:48px;height:2px;background:var(--a);margin:0 auto 20px;animation:expandLine .8s .4s ease both;}
@keyframes expandLine{from{width:0}to{width:48px}}
.hero-title{font-size:13px;color:var(--soft);letter-spacing:0.06em;text-transform:uppercase;margin-bottom:32px;animation:fadeUp .8s .3s ease both;}
.hero-tagline{font-size:clamp(15px,2.2vw,20px);color:var(--mid);font-weight:300;line-height:1.65;max-width:520px;margin:0 auto 52px;animation:fadeUp .8s .4s ease both;}
@keyframes fadeUp{from{opacity:0;transform:translateY(20px)}to{opacity:1;transform:translateY(0)}}
.hero-stats{display:flex;flex-direction:row;gap:0;border:1px solid var(--line);border-radius:4px;overflow:hidden;animation:fadeUp .8s .5s ease both;width:100%;max-width:560px;}
.h-stat{padding:20px 16px;border-right:1px solid var(--line);text-align:center;flex:1;}
.h-stat:last-child{border-right:none;}
.h-stat-num{font-size:clamp(20px,4vw,32px);font-weight:200;letter-spacing:-0.03em;line-height:1;}
.h-stat-num em{color:var(--a);font-style:normal;}
.h-stat-label{font-size:10px;color:var(--soft);margin-top:5px;line-height:1.4;}
.scroll-hint{position:absolute;bottom:28px;left:50%;transform:translateX(-50%);display:flex;flex-direction:column;align-items:center;gap:6px;animation:fadeUp .8s .8s ease both;}
.scroll-hint span{font-size:10px;letter-spacing:0.16em;text-transform:uppercase;color:var(--soft);}
.scroll-dot{width:1px;height:40px;background:linear-gradient(to bottom,var(--a),transparent);animation:scrollDot 2s ease-in-out infinite;}
@keyframes scrollDot{0%,100%{opacity:.3;transform:scaleY(.5)}50%{opacity:1;transform:scaleY(1)}}

/* SECTIONS */
section{padding:80px 24px;}
.container{max-width:960px;margin:0 auto;}
.section-label{font-size:10px;letter-spacing:0.22em;text-transform:uppercase;color:var(--a);font-weight:500;margin-bottom:44px;display:flex;align-items:center;gap:14px;}
.section-label::after{content:'';flex:1;height:1px;background:var(--line);}

/* ABOUT */
.about{background:var(--bg2);}
.about-grid{display:grid;grid-template-columns:1fr 1fr;gap:64px;align-items:start;}
.about-headline{font-size:clamp(22px,3.5vw,38px);font-weight:300;line-height:1.2;letter-spacing:-0.02em;margin-bottom:20px;}
.about-body{font-size:14px;color:var(--mid);line-height:1.85;}
.pillars{display:flex;flex-direction:column;}
.pillar{padding:20px 0;border-bottom:1px solid var(--line);}
.pillar:first-child{border-top:1px solid var(--line);}
.pillar-title{font-size:13px;font-weight:500;color:var(--dk);margin-bottom:4px;}
.pillar-body{font-size:12px;color:var(--soft);line-height:1.65;}

/* CASES */
.cases{background:var(--bg);}
.case-card{border:1px solid var(--line);border-radius:6px;overflow:hidden;margin-bottom:40px;transition:box-shadow .3s,transform .3s;}
.case-card:hover{box-shadow:0 10px 40px rgba(0,0,0,0.07);transform:translateY(-2px);}
.case-card:last-child{margin-bottom:0;}
.case-header{padding:32px;background:var(--bg2);display:grid;grid-template-columns:1fr auto;gap:24px;align-items:start;}
.case-meta{font-size:10px;letter-spacing:0.18em;text-transform:uppercase;color:var(--a);font-weight:500;margin-bottom:8px;}
.case-name{font-size:24px;font-weight:400;letter-spacing:-0.02em;margin-bottom:4px;}
.case-sector{font-size:12px;color:var(--soft);}
.case-dual-metrics{display:flex;flex-direction:column;gap:16px;align-items:flex-end;text-align:right;min-width:120px;}
.metric-block{}
.metric-big{font-size:32px;font-weight:200;letter-spacing:-0.04em;line-height:1;}
.metric-big em{color:var(--a);font-style:normal;}
.metric-big.sm{font-size:22px;}
.metric-label{font-size:10px;color:var(--soft);margin-top:3px;line-height:1.4;}
.metric-tag{display:inline-block;font-size:9px;letter-spacing:0.1em;text-transform:uppercase;padding:2px 8px;border-radius:2px;margin-top:4px;font-weight:500;}
.tag-sales{background:#EFF7F0;color:#3B6D11;}
.tag-community{background:var(--al);color:var(--a);}
.case-body{padding:32px;}
.case-body-grid{display:grid;grid-template-columns:1fr 1fr;gap:32px;}
.case-col-title{font-size:10px;letter-spacing:0.14em;text-transform:uppercase;color:var(--soft);margin-bottom:14px;font-weight:500;}
.case-list{list-style:none;display:flex;flex-direction:column;gap:8px;}
.case-list li{font-size:13px;color:var(--mid);padding-left:16px;position:relative;line-height:1.5;}
.case-list li::before{content:'—';position:absolute;left:0;color:var(--a);font-size:10px;top:3px;}
.case-quote{margin-top:28px;padding-top:28px;border-top:1px solid var(--line);font-size:13px;font-style:italic;color:var(--mid);border-left:2px solid var(--a);padding-left:18px;}
.case-results-strip{display:grid;border-top:1px solid var(--line);}
.cols-4{grid-template-columns:repeat(4,1fr);}
.cols-2{grid-template-columns:repeat(2,1fr);}
.result-box{padding:20px 12px;border-right:1px solid var(--line);text-align:center;}
.result-box:last-child{border-right:none;}
.result-num{font-size:22px;font-weight:300;letter-spacing:-0.02em;}
.result-num em{color:var(--a);font-style:normal;}
.result-desc{font-size:10px;color:var(--soft);margin-top:4px;line-height:1.4;}
.result-tag{display:inline-block;font-size:8px;letter-spacing:0.08em;text-transform:uppercase;padding:2px 6px;border-radius:2px;margin-top:4px;font-weight:500;}
.badge-active{display:inline-block;background:var(--al);color:var(--a);font-size:9px;letter-spacing:0.12em;text-transform:uppercase;padding:3px 10px;border-radius:2px;font-weight:500;margin-top:8px;}

/* SERVICES */
.services{background:var(--bg2);}
.services-grid{display:grid;grid-template-columns:1fr 1fr;gap:1px;background:var(--line);border:1px solid var(--line);border-radius:6px;overflow:hidden;}
.svc{background:var(--bg);padding:36px;transition:background .25s;}
.svc:hover{background:#FDFCFA;}
.svc-num{font-size:10px;letter-spacing:0.2em;color:var(--a);font-weight:500;margin-bottom:16px;text-transform:uppercase;}
.svc-name{font-size:18px;font-weight:400;letter-spacing:-0.01em;margin-bottom:5px;}
.svc-sub{font-size:12px;color:var(--a);letter-spacing:0.04em;margin-bottom:14px;}
.svc-desc{font-size:13px;color:var(--mid);line-height:1.75;margin-bottom:16px;}
.svc-list{list-style:none;display:flex;flex-direction:column;gap:6px;}
.svc-list li{font-size:12px;color:var(--soft);display:flex;gap:8px;align-items:flex-start;}
.svc-list li::before{content:'↳';color:var(--a);flex-shrink:0;}
.svc.featured{background:var(--dk);}
.svc.featured .svc-num{color:var(--a);}
.svc.featured .svc-name{color:#fff;}
.svc.featured .svc-sub{color:var(--a);}
.svc.featured .svc-desc{color:rgba(255,255,255,0.55);}
.svc.featured .svc-list li{color:rgba(255,255,255,0.4);}
.svc.featured .svc-list li::before{color:var(--a);}
.svc.featured:hover{background:#1A1A18;}
.not-for{margin-top:40px;padding:28px;background:var(--bg);border:1px solid var(--line);border-radius:4px;}
.not-for-title{font-size:10px;letter-spacing:0.2em;text-transform:uppercase;color:var(--soft);margin-bottom:14px;font-weight:500;}
.not-for-list{display:flex;flex-wrap:wrap;gap:8px;}
.not-tag{font-size:12px;color:var(--soft);border:1px solid var(--line);padding:5px 12px;border-radius:2px;transition:border-color .2s,color .2s;}
.not-tag:hover{border-color:var(--a);color:var(--dk);}

/* CONTACT */
.contact{background:var(--dk);color:#fff;}
.contact .section-label{color:var(--a);}
.contact .section-label::after{background:rgba(255,255,255,0.08);}
.contact-headline{font-size:clamp(28px,5vw,56px);font-weight:300;letter-spacing:-0.03em;line-height:1.1;margin-bottom:56px;}
.contact-headline em{color:var(--a);font-style:normal;}
.contact-grid{display:grid;grid-template-columns:1fr 1fr;gap:56px;}
.promise{padding:18px 0;border-bottom:1px solid rgba(255,255,255,0.07);display:flex;gap:16px;align-items:flex-start;}
.promise:first-child{border-top:1px solid rgba(255,255,255,0.07);}
.promise-dot{width:5px;height:5px;background:var(--a);border-radius:50%;margin-top:9px;flex-shrink:0;}
.promise-text{font-size:14px;color:rgba(255,255,255,0.55);line-height:1.6;}
.channel{padding:18px 0;border-bottom:1px solid rgba(255,255,255,0.07);display:flex;justify-content:space-between;align-items:center;transition:opacity .2s;}
.channel:first-child{border-top:1px solid rgba(255,255,255,0.07);}
.channel:hover{opacity:.7;}
.ch-label{font-size:10px;letter-spacing:0.16em;text-transform:uppercase;color:rgba(255,255,255,0.3);font-weight:500;}
.ch-value{font-size:14px;color:rgba(255,255,255,0.8);}
.footer{background:var(--dk);border-top:1px solid rgba(255,255,255,0.06);padding:20px 24px;display:flex;justify-content:space-between;align-items:center;flex-wrap:wrap;gap:8px;}
.footer-copy{font-size:11px;color:rgba(255,255,255,0.22);}
.footer-brand{font-size:11px;color:rgba(255,255,255,0.35);letter-spacing:0.06em;text-transform:uppercase;}

/* ── TABLET ── */
@media(max-width:768px){
  .nav-links{gap:14px;}
  .nav-links a{font-size:10px;}
  section{padding:64px 20px;}
  .hero{padding:90px 20px 70px;}
  .hero-stats{flex-direction:column;max-width:320px;}
  .h-stat{border-right:none;border-bottom:1px solid var(--line);padding:16px 20px;}
  .h-stat:last-child{border-bottom:none;}
  .about-grid{grid-template-columns:1fr;gap:40px;}
  .case-header{grid-template-columns:1fr;gap:20px;}
  .case-dual-metrics{flex-direction:row;align-items:flex-start;text-align:left;min-width:unset;}
  .metric-block{flex:1;}
  .case-body-grid{grid-template-columns:1fr;gap:24px;}
  .cols-4{grid-template-columns:repeat(2,1fr);}
  .services-grid{grid-template-columns:1fr;}
  .contact-grid{grid-template-columns:1fr;gap:40px;}
  .contact-headline{margin-bottom:40px;}
}

/* ── MOBILE ── */
@media(max-width:480px){
  .nav{padding:0 16px;}
  .nav-links{gap:10px;}
  .nav-links a{font-size:9px;letter-spacing:0.04em;}
  section{padding:52px 16px;}
  .hero{padding:80px 16px 64px;}
  .hero-tagline{font-size:15px;}
  .hero-stats{max-width:100%;}
  .h-stat-num{font-size:26px;}
  .case-header{padding:20px;}
  .case-body{padding:20px;}
  .case-dual-metrics{flex-direction:column;gap:12px;}
  .metric-big{font-size:28px;}
  .metric-big.sm{font-size:20px;}
  .case-name{font-size:20px;}
  .cols-4{grid-template-columns:repeat(2,1fr);}
  .result-box{padding:16px 8px;}
  .result-num{font-size:18px;}
  .svc{padding:24px;}
  .svc-name{font-size:16px;}
  .contact-headline{font-size:26px;}
  .promise-text{font-size:13px;}
  .ch-value{font-size:13px;}
  .footer{flex-direction:column;text-align:center;padding:16px;}
  .not-tag{font-size:11px;}
}
</style>
</head>
<body>

<nav class="nav">
  <span class="nav-brand">@geraldine.digital</span>
  <div class="nav-links">
    <a onclick="goTo('sobre-mi')">Sobre mí</a>
    <a onclick="goTo('casos')">Casos</a>
    <a onclick="goTo('servicios')">Servicios</a>
    <a onclick="goTo('contacto')">Contacto</a>
  </div>
</nav>
<div class="progress-bar"><div class="progress-fill" id="prog"></div></div>

<!-- HERO -->
<section class="hero" id="top">
  <div class="hero-bg-text">MARKETING</div>
  <p class="hero-eyebrow">Media Kit 2026</p>
  <h1 class="hero-name">
    <strong>Geraldine</strong>
    <span class="sub">Digital</span>
  </h1>
  <div class="hero-line"></div>
  <p class="hero-title">Estratega de Marketing &amp; Creadora de Contenido</p>
  <p class="hero-tagline">Ayudo a emprendedores y negocios a dejar de improvisar para empezar a crecer con dirección y propósito.</p>
  <div class="hero-stats">
    <div class="h-stat">
      <div class="h-stat-num"><em>8</em>+ años</div>
      <div class="h-stat-label">Experiencia en marketing digital</div>
    </div>
    <div class="h-stat">
      <div class="h-stat-num"><em>+118%</em></div>
      <div class="h-stat-label">Crecimiento máximo en 90 días</div>
    </div>
    <div class="h-stat">
      <div class="h-stat-num"><em>+20%</em></div>
      <div class="h-stat-label">Impacto máximo en ventas</div>
    </div>
  </div>
  <div class="scroll-hint">
    <span>Scroll</span>
    <div class="scroll-dot"></div>
  </div>
</section>

<!-- ABOUT -->
<section class="about" id="sobre-mi">
  <div class="container">
    <p class="section-label reveal">Quién soy</p>
    <div class="about-grid">
      <div class="reveal-left">
        <h2 class="about-headline">El marketing bien hecho no interrumpe. Conecta.</h2>
        <p class="about-body">Llevo más de 8 años en el mundo del marketing digital. He construido y dirigido un negocio trabajando con marcas grandes, y esa experiencia me dio algo que ningún curso puede dar: saber cómo funciona un negocio desde dentro, con todo lo que eso implica.<br><br>Hoy me enfoco en marcas que conectan de verdad y tienen una historia real detrás. Acompaño a negocios y emprendedores a construir una comunicación con dirección, coherencia y resultados reales. No hay fórmulas genéricas: cada cliente tiene su propio camino.</p>
      </div>
      <div class="pillars reveal-right">
        <div class="pillar"><div class="pillar-title">Experiencia real como empresaria</div><div class="pillar-body">He construido y dirigido un negocio con marcas grandes. No hablo de marketing desde la teoría.</div></div>
        <div class="pillar"><div class="pillar-title">Estrategia antes que ejecución</div><div class="pillar-body">Primero definimos qué comunicar y por qué. El contenido viene después, nunca al revés.</div></div>
        <div class="pillar"><div class="pillar-title">Sin humo ni tendencias vacías</div><div class="pillar-body">Cada decisión se basa en el negocio, la audiencia y los datos. No en lo que está de moda.</div></div>
        <div class="pillar"><div class="pillar-title">Sistema completo</div><div class="pillar-body">Estrategia + contenido + campañas + branding. No piezas sueltas. Un ecosistema coherente.</div></div>
      </div>
    </div>
  </div>
</section>

<!-- CASES -->
<section class="cases" id="casos">
  <div class="container">
    <p class="section-label reveal">Casos de éxito</p>

    <!-- Tu Cachapa -->
    <div class="case-card reveal">
      <div class="case-header">
        <div>
          <div class="case-meta">Caso 01 · Restaurante · Barcelona</div>
          <div class="case-name">Tu Cachapa</div>
          <div class="case-sector">Cocina venezolana · 8 meses de trabajo</div>
        </div>
        <div class="case-dual-metrics">
          <div class="metric-block">
            <div class="metric-big"><em class="count-trigger" data-val="15" data-prefix="+" data-suffix="%">+15%</em></div>
            <div class="metric-label">Aumento en reservas</div>
            <span class="metric-tag tag-sales">Impacto en ventas</span>
          </div>
          <div class="metric-block">
            <div class="metric-big sm">9K<em> → </em>12.4K</div>
            <div class="metric-label">Seguidores totales</div>
            <span class="metric-tag tag-community">Comunidad</span>
          </div>
        </div>
      </div>
      <div class="case-body">
        <div class="case-body-grid">
          <div>
            <div class="case-col-title">El reto</div>
            <ul class="case-list">
              <li>Sin identidad visual ni logo reconocible</li>
              <li>Sin packaging ni bolsa de delivery con marca</li>
              <li>Sin posicionamiento ni historia de negocio</li>
              <li>Sin presencia en eventos ni ferias</li>
            </ul>
          </div>
          <div>
            <div class="case-col-title">La transformación</div>
            <ul class="case-list">
              <li>Branding completo: logo, packaging y bolsa delivery</li>
              <li>Concepto de marca con historia y propósito claros</li>
              <li>Food truck en La Mercè, Sant Jordi, Día del Padre</li>
              <li>Campañas Meta Ads y activaciones por fechas clave</li>
            </ul>
          </div>
        </div>
        <p class="case-quote">Sin identidad no hay negocio. Con identidad, todo lo demás puede crecer.</p>
      </div>
      <div class="case-results-strip cols-4">
        <div class="result-box">
          <div class="result-num"><em class="count-trigger" data-val="15" data-prefix="+" data-suffix="%">+15%</em></div>
          <div class="result-desc">Reservas con Meta Ads</div>
          <span class="result-tag tag-sales">Ventas</span>
        </div>
        <div class="result-box">
          <div class="result-num"><em class="count-trigger" data-val="8" data-prefix="+" data-suffix="%">+8%</em></div>
          <div class="result-desc">Reservas con Karaoke</div>
          <span class="result-tag tag-sales">Ventas</span>
        </div>
        <div class="result-box">
          <div class="result-num"><em class="count-trigger" data-val="37" data-prefix="+" data-suffix="%">+37%</em></div>
          <div class="result-desc">Crecimiento de seguidores</div>
          <span class="result-tag tag-community">Comunidad</span>
        </div>
        <div class="result-box">
          <div class="result-num"><em>+1.000</em></div>
          <div class="result-desc">Seg. nuevos con Meta Ads</div>
          <span class="result-tag tag-community">Comunidad</span>
        </div>
      </div>
    </div>

    <!-- Método Anais -->
    <div class="case-card reveal delay-1">
      <div class="case-header">
        <div>
          <div class="case-meta">Caso 02 · Salud · Fisioterapia</div>
          <div class="case-name">Método Anais Anaya</div>
          <div class="case-sector">Fisioterapia · Suelo Pélvico · Pre y Postparto · 3 meses</div>
        </div>
        <div class="case-dual-metrics">
          <div class="metric-block">
            <div class="metric-big"><em class="count-trigger" data-val="20" data-prefix="+" data-suffix="%">+20%</em></div>
            <div class="metric-label">Reservas en el gym</div>
            <span class="metric-tag tag-sales">Impacto en ventas</span>
          </div>
          <div class="metric-block">
            <div class="metric-big"><em class="count-trigger" data-val="118" data-prefix="+" data-suffix="%">+118%</em></div>
            <div class="metric-label">Crecimiento en 90 días</div>
            <span class="metric-tag tag-community">Comunidad</span>
          </div>
        </div>
      </div>
      <div class="case-body">
        <div class="case-body-grid">
          <div>
            <div class="case-col-title">El reto</div>
            <ul class="case-list">
              <li>Sin guiones ni estructura de contenido definida</li>
              <li>Método difícil de entender para el público general</li>
              <li>Audiencia que no sabía por qué necesitaba el servicio</li>
              <li>Sin presencia offline ni colaboraciones</li>
            </ul>
          </div>
          <div>
            <div class="case-col-title">La transformación</div>
            <ul class="case-list">
              <li>Guiones y pilares: educación, cercanía, entretenimiento</li>
              <li>Serie de reels que educó y generó expectativa</li>
              <li>2 charlas presenciales en guarderías (0–3 años)</li>
              <li>Meta Ads activados tras validar el mensaje orgánico</li>
            </ul>
          </div>
        </div>
        <p class="case-quote">Primero educamos. Luego conectamos. Finalmente amplificamos. El orden importa.</p>
      </div>
      <div class="case-results-strip cols-4">
        <div class="result-box">
          <div class="result-num"><em class="count-trigger" data-val="20" data-prefix="+" data-suffix="%">+20%</em></div>
          <div class="result-desc">Reservas en el gym</div>
          <span class="result-tag tag-sales">Ventas</span>
        </div>
        <div class="result-box">
          <div class="result-num"><em class="count-trigger" data-val="118" data-prefix="+" data-suffix="%">+118%</em></div>
          <div class="result-desc">Crecimiento total comunidad</div>
          <span class="result-tag tag-community">Comunidad</span>
        </div>
        <div class="result-box">
          <div class="result-num"><em>+2.000</em></div>
          <div class="result-desc">Seguidores solo orgánico</div>
          <span class="result-tag tag-community">Comunidad</span>
        </div>
        <div class="result-box">
          <div class="result-num"><em>+6.500</em></div>
          <div class="result-desc">Totales orgánico + ADS</div>
          <span class="result-tag tag-community">Comunidad</span>
        </div>
      </div>
    </div>

    <!-- Beea Reformas -->
    <div class="case-card reveal delay-2">
      <div class="case-header">
        <div>
          <div class="case-meta">Caso 03 · Reformas · Barcelona</div>
          <div class="case-name">Beea Reformas</div>
          <div class="case-sector">Reformas integrales · Proyecto activo</div>
          <div class="badge-active">En curso</div>
        </div>
        <div class="case-dual-metrics">
          <div class="metric-block">
            <div class="metric-big"><em class="count-trigger" data-val="4" data-prefix="" data-suffix="">4</em></div>
            <div class="metric-label">Clientes cerrados: local, piso, baño y habitación</div>
            <span class="metric-tag tag-sales">Impacto en ventas</span>
          </div>
          <div class="metric-block">
            <div class="metric-big"><em>66</em></div>
            <div class="metric-label">Seguidores al cerrar esos clientes</div>
            <span class="metric-tag tag-community">Comunidad</span>
          </div>
        </div>
      </div>
      <div class="case-body">
        <div class="case-body-grid">
          <div>
            <div class="case-col-title">El reto</div>
            <ul class="case-list">
              <li>Sin nombre visual ni identidad de marca</li>
              <li>Sin landing page ni sistema de captación de leads</li>
              <li>Clientes únicamente por boca a boca</li>
              <li>Sin diferenciador frente a la competencia</li>
            </ul>
          </div>
          <div>
            <div class="case-col-title">La construcción</div>
            <ul class="case-list">
              <li>Identidad de marca + diferenciador: "Presupuesto gratis en 24h"</li>
              <li>Landing page con propuesta de valor clara (Systeme.io)</li>
              <li>Formulario de cualificación automática (Tally.so)</li>
              <li>Campaña de captación constante en Meta Ads</li>
            </ul>
          </div>
        </div>
        <p class="case-quote">4 clientes reformados con 66 seguidores. Los seguidores no hacen el negocio. El sistema sí.</p>
      </div>
    </div>

  </div>
</section>

<!-- SERVICES -->
<section class="services" id="servicios">
  <div class="container">
    <p class="section-label reveal">Servicios</p>
    <div class="services-grid reveal">
      <div class="svc">
        <div class="svc-num">01</div>
        <div class="svc-name">Asesoría / Consultoría 1:1</div>
        <div class="svc-sub">Sesión puntual · 60 minutos</div>
        <p class="svc-desc">Una sesión enfocada en resolver un problema concreto. Sin rodeos: saldrás con claridad y pasos de acción definidos.</p>
        <ul class="svc-list">
          <li>Diagnóstico de tu situación actual</li>
          <li>Identificación del bloqueo principal</li>
          <li>Plan de acción con próximos pasos</li>
          <li>Respuestas directas a tus preguntas</li>
        </ul>
      </div>
      <div class="svc">
        <div class="svc-num">02</div>
        <div class="svc-name">Plan Ruta</div>
        <div class="svc-sub">Tú ejecutas · Yo estratego</div>
        <p class="svc-desc">Hago todo el trabajo estratégico: la hoja de ruta, el calendario editorial y los guiones. Tu equipo lo lleva a la práctica.</p>
        <ul class="svc-list">
          <li>Estrategia de contenido completa</li>
          <li>Calendario editorial con objetivos</li>
          <li>Guiones para cada pieza de contenido</li>
          <li>Manual de directrices para ejecución</li>
        </ul>
      </div>
      <div class="svc featured">
        <div class="svc-num">03</div>
        <div class="svc-name">Plan Ruta + Acompañamiento</div>
        <div class="svc-sub">Yo estratego y ejecuto</div>
        <p class="svc-desc">Hago la estrategia y la ejecuto contigo: community management, creación de contenido y edición de video básica.</p>
        <ul class="svc-list">
          <li>Todo lo del Plan Ruta incluido</li>
          <li>Gestión de redes sociales</li>
          <li>Textos, creatividades y piezas</li>
          <li>Edición de video básica</li>
        </ul>
      </div>
      <div class="svc">
        <div class="svc-num">04</div>
        <div class="svc-name">Plan Premium</div>
        <div class="svc-sub">Producción completa</div>
        <p class="svc-desc">Todo lo anterior más producción audiovisual profesional con filmmaker incluido y edición avanzada.</p>
        <ul class="svc-list">
          <li>Todo el Plan Ruta + Acompañamiento</li>
          <li>Filmmaker profesional</li>
          <li>Edición de video avanzada</li>
          <li>Máxima calidad para todas las plataformas</li>
        </ul>
      </div>
    </div>
    <div class="not-for reveal">
      <div class="not-for-title">No trabajo con…</div>
      <div class="not-for-list">
        <span class="not-tag">Quienes buscan resultados inmediatos sin proceso</span>
        <span class="not-tag">Quienes ven el marketing como gasto, no inversión</span>
        <span class="not-tag">Quienes no pueden comprometerse con el proyecto</span>
        <span class="not-tag">Quienes quieren regatear el valor del trabajo</span>
      </div>
    </div>
  </div>
</section>

<!-- CONTACT -->
<section class="contact" id="contacto">
  <div class="container">
    <p class="section-label reveal">¿Hablamos?</p>
    <h2 class="contact-headline reveal">Si algo resonó,<br>el siguiente paso es<br>una <em>conversación.</em></h2>
    <div class="contact-grid">
      <div class="reveal-left">
        <div class="promise"><div class="promise-dot"></div><div class="promise-text">Claridad sobre tu situación actual</div></div>
        <div class="promise"><div class="promise-dot"></div><div class="promise-text">Honestidad sobre lo que necesitas realmente</div></div>
        <div class="promise"><div class="promise-dot"></div><div class="promise-text">Sin venta de humo ni presión</div></div>
        <div class="promise"><div class="promise-dot"></div><div class="promise-text">Una sola conversación para ver si tiene sentido trabajar juntos</div></div>
      </div>
      <div class="reveal-right">
        <div class="channel"><span class="ch-label">Instagram</span><span class="ch-value">@geraldine.digital</span></div>
        <div class="channel"><span class="ch-label">Email</span><span class="ch-value">hola@geraldine.digital</span></div>
        <div class="channel"><span class="ch-label">LinkedIn</span><span class="ch-value">Geraldine Berroterán</span></div>
        <div class="channel"><span class="ch-label">Web</span><span class="ch-value">geraldine.digital</span></div>
      </div>
    </div>
  </div>
</section>

<div class="footer">
  <span class="footer-copy">© 2026 Geraldine Digital</span>
  <span class="footer-brand">@geraldine.digital · Estrategia · Contenido · Resultados</span>
</div>

<script>
function goTo(id){document.getElementById(id).scrollIntoView({behavior:'smooth'});}

window.addEventListener('scroll',()=>{
  const h=document.documentElement;
  const pct=(h.scrollTop/(h.scrollHeight-h.clientHeight))*100;
  document.getElementById('prog').style.width=pct+'%';
});

const obs=new IntersectionObserver(entries=>{
  entries.forEach(e=>{if(e.isIntersecting)e.target.classList.add('in');});
},{threshold:0.1});
document.querySelectorAll('.reveal,.reveal-left,.reveal-right').forEach(el=>obs.observe(el));

function animateCount(el){
  const val=parseInt(el.dataset.val);
  const prefix=el.dataset.prefix||'';
  const suffix=el.dataset.suffix||'';
  const dur=1400;const start=performance.now();
  function frame(now){
    const p=Math.min((now-start)/dur,1);
    const ease=1-Math.pow(1-p,3);
    const cur=Math.round(ease*val);
    let disp=cur>=1000?cur.toLocaleString('es-ES'):cur;
    el.textContent=prefix+disp+suffix;
    if(p<1)requestAnimationFrame(frame);
  }
  requestAnimationFrame(frame);
}
const cObs=new IntersectionObserver(entries=>{
  entries.forEach(e=>{
    if(e.isIntersecting&&!e.target.dataset.done){
      e.target.dataset.done='1';animateCount(e.target);
    }
  });
},{threshold:0.5});
document.querySelectorAll('.count-trigger').forEach(el=>cObs.observe(el));
</script>
</body>
</html>
