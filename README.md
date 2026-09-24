<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Bekmurod Akhmadov — Backend Developer</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Fraunces:opsz,wght@9..144,400;9..144,500;9..144,600&family=Inter:wght@400;500;600&family=IBM+Plex+Mono:wght@400;500&display=swap" rel="stylesheet">
<style>
  :root{
    --bg:#12140F; --bg-alt:#181a13; --line:#33362A;
    --text:#EAE6D9; --muted:#9C9884;
    --gold:#C9A227; --teal:#4E8B82;
    box-sizing:border-box;
  }
  *{box-sizing:border-box;}
  html{scroll-behavior:smooth; scroll-padding-top:env(safe-area-inset-top,0px);}
  body{
    margin:0; background:var(--bg); color:var(--text); overflow-x:hidden;
    font-family:'Inter',sans-serif; line-height:1.6; font-size:16px;
    padding-top:env(safe-area-inset-top,0px); padding-bottom:env(safe-area-inset-bottom,0px);
    -webkit-font-smoothing:antialiased;
  }
  h1,h2,h3{font-family:'Fraunces',serif; font-weight:500; margin:0; letter-spacing:-0.01em;}
  .mono{font-family:'IBM Plex Mono',monospace;}
  a{color:inherit;} img,svg{max-width:100%;}
  .wrap{max-width:880px; margin:0 auto; padding:0 24px; position:relative;}
  ::selection{background:var(--gold); color:#12140F;}
  a:focus-visible, button:focus-visible{outline:2px solid var(--teal); outline-offset:3px;}

  /* reveal-on-scroll */
  .reveal{opacity:0; transform:translateY(16px); transition:opacity .6s ease, transform .6s ease;}
  .reveal.in{opacity:1; transform:translateY(0);}
  @media (prefers-reduced-motion:reduce){ .reveal{opacity:1; transform:none; transition:none;} }

  header{
    position:sticky; top:0; top:env(safe-area-inset-top,0px); z-index:20;
    background:rgba(18,20,15,0.86); backdrop-filter:blur(6px); border-bottom:1px solid var(--line);
  }
  .nav{display:flex; align-items:center; justify-content:space-between; padding:16px 24px;}
  .brand{font-family:'Fraunces',serif; font-size:18px;}
  .nav-links{display:flex; gap:22px; font-size:14px; color:var(--muted);}
  .nav-links a{text-decoration:none;} .nav-links a:hover{color:var(--text);}
  @media (max-width:640px){ .nav-links{display:none;} }

  /* hero */
  .hero{padding:60px 0 40px; border-bottom:1px solid var(--line); position:relative; overflow:hidden;}
  .blob{position:absolute; border-radius:50%; filter:blur(60px); opacity:.22; pointer-events:none;}
  .blob-a{width:360px; height:360px; background:var(--teal); top:-140px; right:-100px; animation:drift1 16s ease-in-out infinite;}
  .blob-b{width:280px; height:280px; background:var(--gold); bottom:-120px; left:-80px; animation:drift2 20s ease-in-out infinite;}
  @keyframes drift1{0%,100%{transform:translate(0,0)} 50%{transform:translate(-30px,40px)}}
  @keyframes drift2{0%,100%{transform:translate(0,0)} 50%{transform:translate(30px,-30px)}}
  @media (prefers-reduced-motion:reduce){ .blob-a,.blob-b{animation:none;} }

  .hero-grid{display:grid; grid-template-columns:1.25fr 1fr; gap:36px; align-items:center; position:relative;}
  @media (max-width:720px){ .hero-grid{grid-template-columns:1fr;} }
  .kicker{font-size:13px; color:var(--teal); margin-bottom:14px;}
  .hero h1{font-size:44px; line-height:1.1; max-width:12ch;}
  .hero p.lead{color:var(--muted); max-width:46ch; margin-top:18px; font-size:16.5px;}
  .cta-row{display:flex; gap:12px; margin-top:28px; flex-wrap:wrap;}
  .btn{display:inline-block; padding:11px 18px; border-radius:2px; font-size:14px; text-decoration:none; border:1px solid var(--line); transition:border-color .15s, background .15s, transform .15s;}
  .btn-primary{background:var(--gold); color:#161810; border-color:var(--gold); font-weight:600;}
  .btn-primary:hover{background:#dab338; transform:translateY(-1px);}
  .btn-ghost:hover{border-color:var(--teal); color:var(--teal); transform:translateY(-1px);}

  /* hero illustration: animated field / data grid */
  .grid-art{width:100%; height:auto; display:block;}
  .cell{fill:var(--bg-alt); stroke:var(--line);}
  .cell.hot{fill:var(--teal); opacity:.55; animation:pulse 3.2s ease-in-out infinite;}
  .cell.hot2{fill:var(--gold); opacity:.5; animation:pulse 3.2s ease-in-out infinite 1.1s;}
  @keyframes pulse{0%,100%{opacity:.25} 50%{opacity:.75}}
  .flow{stroke:var(--gold); stroke-width:1.5; fill:none; stroke-dasharray:6 6; animation:dash 4s linear infinite;}
  @keyframes dash{to{stroke-dashoffset:-120;}}
  @media (prefers-reduced-motion:reduce){ .cell.hot,.cell.hot2,.flow{animation:none;} }

  /* sections */
  section{padding:56px 0; border-bottom:1px solid var(--line); position:relative;}
  section h2{font-size:26px; margin-bottom:8px;}
  section .sub{color:var(--muted); max-width:56ch; margin-bottom:32px; font-size:15px;}

  .field-row{display:grid; grid-template-columns:52px 1fr; gap:20px; padding:22px 0; border-top:1px solid var(--line); transition:transform .2s;}
  .field-row:last-child{border-bottom:1px solid var(--line);}
  .field-row:hover{transform:translateX(4px);}
  .icon{width:26px; height:26px; stroke:var(--gold); fill:none; stroke-width:1.6; transition:stroke .2s, transform .2s;}
  .field-row:hover .icon{stroke:var(--teal); transform:scale(1.1);}
  .field-row h3{font-size:18px; margin-bottom:6px; font-weight:500;}
  .field-row p{margin:0; color:var(--muted); font-size:14.5px; max-width:54ch;}
  @media (max-width:560px){ .field-row{grid-template-columns:1fr; gap:8px;} }

  .stack-group{margin-bottom:22px;}
  .stack-group-label{font-family:'IBM Plex Mono',monospace; font-size:12px; color:var(--muted); margin-bottom:10px;}
  .tags{display:flex; flex-wrap:wrap; gap:8px;}
  .tag{font-family:'IBM Plex Mono',monospace; font-size:12.5px; padding:6px 10px; border:1px solid var(--line); color:var(--text); transition:border-color .15s, transform .15s;}
  .tag:hover{border-color:var(--teal); transform:translateY(-2px);}

  .focus-grid{display:grid; grid-template-columns:1fr 1fr; gap:1px; background:var(--line); border:1px solid var(--line);}
  @media (max-width:640px){ .focus-grid{grid-template-columns:1fr;} }
  .focus-card{background:var(--bg); padding:28px; transition:background .2s;}
  .focus-card:hover{background:var(--bg-alt);}
  .focus-card .icon{width:30px; height:30px; margin-bottom:14px;}
  .focus-card h3{font-size:19px; margin-bottom:10px;}
  .focus-card p{color:var(--muted); font-size:14.5px; margin:0;}

  .steps{position:relative; padding-left:8px;}
  .steps::before{content:"";position:absolute; left:23px; top:6px; bottom:6px; width:1px; background:var(--line);}
  .step{display:grid; grid-template-columns:48px 1fr; gap:18px; padding:16px 0; position:relative;}
  .step-num{font-family:'IBM Plex Mono',monospace; color:var(--gold); font-size:14px; background:var(--bg); z-index:1;}
  .step h3{font-size:16px; margin-bottom:4px; font-weight:500;}
  .step p{margin:0; color:var(--muted); font-size:14px;}

  .contact h2{font-size:30px; max-width:16ch; margin-bottom:14px;}
  .contact p.lead{color:var(--muted); max-width:48ch; margin-bottom:26px;}
  footer{padding:28px 0 40px;}
  .quote{color:var(--muted); font-family:'Fraunces',serif; font-style:italic; font-size:14px; margin:0 0 18px;}
  .copy{color:#6b6a5c; font-size:12.5px;}
</style>
</head>
<body>

<header>
  <div class="nav wrap">
    <div class="brand">Bekmurod Akhmadov</div>
    <nav class="nav-links">
      <a href="#expertise">Expertise</a>
      <a href="#stack">Stack</a>
      <a href="#focus">Domains</a>
      <a href="#contact">Contact</a>
    </nav>
  </div>
</header>

<section class="hero">
  <div class="blob blob-a"></div>
  <div class="blob blob-b"></div>
  <div class="wrap hero-grid">
    <div>
      <div class="kicker mono">backend developer · php / yii2</div>
      <h1>Complex business logic. Clear, reliable systems.</h1>
      <p class="lead">I build PHP &amp; Yii2 backends that connect business workflows, relational data, and external services — mainly across AgroTech and CRM products.</p>
      <div class="cta-row">
        <a class="btn btn-primary" href="https://t.me/the_codeholic">Message on Telegram</a>
        <a class="btn btn-ghost" href="mailto:xbek1321@gmail.com">Send an email</a>
      </div>
    </div>
    <svg class="grid-art" viewBox="0 0 260 220" xmlns="http://www.w3.org/2000/svg" aria-hidden="true">
      <g>
        <rect class="cell" x="10" y="10" width="50" height="50"/>
        <rect class="cell hot" x="70" y="10" width="50" height="50"/>
        <rect class="cell" x="130" y="10" width="50" height="50"/>
        <rect class="cell" x="190" y="10" width="50" height="50"/>
        <rect class="cell" x="10" y="70" width="50" height="50"/>
        <rect class="cell" x="70" y="70" width="50" height="50"/>
        <rect class="cell hot2" x="130" y="70" width="50" height="50"/>
        <rect class="cell" x="190" y="70" width="50" height="50"/>
        <rect class="cell" x="10" y="130" width="50" height="50"/>
        <rect class="cell hot" x="70" y="130" width="50" height="50"/>
        <rect class="cell" x="130" y="130" width="50" height="50"/>
        <rect class="cell" x="190" y="130" width="50" height="50"/>
      </g>
      <path class="flow" d="M95 35 H155 V95 H35 V155 H95"/>
    </svg>
  </div>
</section>

<section id="expertise">
  <div class="wrap reveal">
    <h2>Built around the problems that matter</h2>
    <p class="sub">The areas I focus on in every project, from business rules to query speed.</p>

    <div class="field-row">
      <svg class="icon" viewBox="0 0 24 24"><rect x="3" y="3" width="18" height="6" rx="1"/><rect x="3" y="15" width="18" height="6" rx="1"/><path d="M7 9v6M17 9v6"/></svg>
      <div><h3>Backend architecture</h3><p>Translating business rules into clear service boundaries, reusable components, and maintainable application logic.</p></div>
    </div>
    <div class="field-row">
      <svg class="icon" viewBox="0 0 24 24"><path d="M4 12h4M16 12h4M9 6l3 6-3 6M15 6l-3 6 3 6" stroke-linecap="round"/></svg>
      <div><h3>APIs &amp; integrations</h3><p>Designing REST endpoints with consistent validation, predictable responses, versioning, and useful documentation.</p></div>
    </div>
    <div class="field-row">
      <svg class="icon" viewBox="0 0 24 24"><ellipse cx="12" cy="6" rx="8" ry="3"/><path d="M4 6v12c0 1.7 3.6 3 8 3s8-1.3 8-3V6"/><path d="M4 12c0 1.7 3.6 3 8 3s8-1.3 8-3"/></svg>
      <div><h3>Database engineering</h3><p>Shaping relational schemas around application needs, writing SQL, and speeding up expensive queries through indexing and analysis.</p></div>
    </div>
    <div class="field-row">
      <svg class="icon" viewBox="0 0 24 24"><path d="M12 3l7 3v6c0 4.5-3 7.5-7 9-4-1.5-7-4.5-7-9V6l7-3z"/></svg>
      <div><h3>Identity &amp; access</h3><p>Implementing authentication and authorization flows with explicit roles, permissions, and business access rules.</p></div>
    </div>
    <div class="field-row">
      <svg class="icon" viewBox="0 0 24 24"><rect x="4" y="5" width="16" height="4"/><rect x="4" y="11" width="16" height="4"/><path d="M10 19h6l-2-2m2 2l-2 2"/></svg>
      <div><h3>Background processing</h3><p>Moving suitable workloads into background jobs and asynchronous flows to keep application behaviour responsive.</p></div>
    </div>
    <div class="field-row">
      <svg class="icon" viewBox="0 0 24 24"><path d="M3 17l4-6 3 3 5-8 6 11" stroke-linecap="round" stroke-linejoin="round"/></svg>
      <div><h3>Performance &amp; reliability</h3><p>Investigating bottlenecks, handling failure paths, and making application behaviour legible through logs and monitoring.</p></div>
    </div>
  </div>
</section>

<section id="stack">
  <div class="wrap reveal">
    <h2>The toolkit behind the work</h2>
    <p class="sub">PHP and Yii2 are my core. The rest supports data, deployment, integrations, and everyday development.</p>

    <div class="stack-group"><div class="stack-group-label">backend</div>
      <div class="tags"><span class="tag">PHP</span><span class="tag">Yii2</span><span class="tag">Laravel (basic)</span></div></div>
    <div class="stack-group"><div class="stack-group-label">data &amp; cache</div>
      <div class="tags"><span class="tag">PostgreSQL</span><span class="tag">MySQL</span><span class="tag">Redis</span></div></div>
    <div class="stack-group"><div class="stack-group-label">infrastructure</div>
      <div class="tags"><span class="tag">Docker</span><span class="tag">Nginx</span><span class="tag">Linux</span></div></div>
    <div class="stack-group"><div class="stack-group-label">api &amp; messaging</div>
      <div class="tags"><span class="tag">Postman</span><span class="tag">OpenAPI</span><span class="tag">Swagger</span><span class="tag">RabbitMQ</span><span class="tag">Kafka</span></div></div>
    <div class="stack-group"><div class="stack-group-label">workflow &amp; ui</div>
      <div class="tags"><span class="tag">Git</span><span class="tag">GitHub</span><span class="tag">JavaScript</span><span class="tag">jQuery</span></div></div>
  </div>
</section>

<section id="focus">
  <div class="wrap reveal">
    <h2>Software connected to real operations</h2>
    <p class="sub">Two domains I currently build for.</p>
    <div class="focus-grid">
      <div class="focus-card">
        <svg class="icon" viewBox="0 0 24 24"><path d="M12 3c4 2 6 5 6 9a6 6 0 0 1-12 0c0-4 2-7 6-9z"/><path d="M12 21v-9"/></svg>
        <h3>AgroTech</h3>
        <p>Backend systems supporting agricultural business workflows, structured records, and connections to external services. Focus: business logic, data organization, and integrations.</p>
      </div>
      <div class="focus-card">
        <svg class="icon" viewBox="0 0 24 24"><circle cx="8" cy="8" r="3"/><circle cx="17" cy="8" r="3"/><path d="M3 20c0-3 2.5-5 5-5s5 2 5 5M13 20c0-2.5 2-4.5 4.5-4.5S22 17.5 22 20"/></svg>
        <h3>CRM</h3>
        <p>Application features that help teams manage business processes, organize information, and control access. Focus: workflows, relational data, and user permissions.</p>
      </div>
    </div>
  </div>
</section>

<section>
  <div class="wrap reveal">
    <h2>Understand. Build. Improve.</h2>
    <p class="sub">Five steps I follow on every project.</p>
    <div class="steps">
      <div class="step"><div class="step-num">01</div><div><h3>Understand</h3><p>Clarify the business workflow, user roles, constraints, and edge cases.</p></div></div>
      <div class="step"><div class="step-num">02</div><div><h3>Design</h3><p>Define data relationships, API contracts, and access rules.</p></div></div>
      <div class="step"><div class="step-num">03</div><div><h3>Build</h3><p>Implement focused components and explicit business logic.</p></div></div>
      <div class="step"><div class="step-num">04</div><div><h3>Verify</h3><p>Check critical paths, validation, permissions, and integration failures.</p></div></div>
      <div class="step"><div class="step-num">05</div><div><h3>Improve</h3><p>Investigate bottlenecks, refine queries, and refactor with purpose.</p></div></div>
    </div>
  </div>
</section>

<section id="contact" class="contact">
  <div class="wrap reveal">
    <h2>Have a backend challenge? Let's talk it through.</h2>
    <p class="lead">APIs, integrations, databases, or complex business logic — happy to discuss the technical details.</p>
    <div class="cta-row">
      <a class="btn btn-primary" href="https://t.me/the_codeholic">Message on Telegram</a>
      <a class="btn btn-ghost" href="mailto:xbek1321@gmail.com">xbek1321@gmail.com</a>
      <a class="btn btn-ghost" href="https://www.linkedin.com/in/bekmurod-ahmadov-368892263/">LinkedIn</a>
      <a class="btn btn-ghost" href="https://www.instagram.com/bek_akhmadov01/">Instagram</a>
    </div>
  </div>
</section>

<footer>
  <div class="wrap">
    <p class="quote">"First make it work, then make it right, then make it fast."</p>
    <p class="copy">© 2026 Bekmurod Akhmadov · Backend Engineer</p>
  </div>
</footer>

<script>
  try{
    var els = document.querySelectorAll('.reveal');
    if('IntersectionObserver' in window){
      var io = new IntersectionObserver(function(entries){
        entries.forEach(function(e){ if(e.isIntersecting){ e.target.classList.add('in'); io.unobserve(e.target); } });
      }, {threshold:.15});
      els.forEach(function(el){ io.observe(el); });
    } else {
      els.forEach(function(el){ el.classList.add('in'); });
    }
  }catch(e){}
</script>

</body>
</html>
