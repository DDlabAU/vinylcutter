<html lang="da">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Vinylskærer i DDlab — Liquid Glass</title>
  <style>
    /* ===== CSS RESET (lightweight) ===== */
    *,*::before,*::after{box-sizing:border-box}
    html{line-height:1.5;-webkit-text-size-adjust:100%;scroll-behavior:smooth}
    body{margin:0;font-family:ui-sans-serif,system-ui,-apple-system,Segoe UI,Roboto,Inter,Arial,"Apple Color Emoji","Segoe UI Emoji";}
    img{max-width:100%;display:block;height:auto}
    a{color:inherit}

    /* ===== THEME ===== */
    :root{
      --bg-1:#0f172a;      /* slate-900 */
      --bg-2:#111827;      /* gray-900 */
      --accent:#60a5fa;    /* blue-400 */
      --accent-2:#a78bfa;  /* violet-400 */
      --ring: 0 0 0 3px color-mix(in oklab, var(--accent) 40%, transparent);
      --max-w: 1200px;
      --sidebar-w: 240px;
      --gap: 20px;
      --radius: 16px;
      --shadow: 0 10px 30px rgba(0,0,0,.25);
    }

    /* ===== BACKDROP / LIQUID GLASS UTILS ===== */
    .glass{
      background:
        linear-gradient(135deg, color-mix(in oklab, #fff 18%, transparent), color-mix(in oklab, #fff 6%, transparent));
      border:1px solid color-mix(in oklab, #fff 35%, transparent);
      backdrop-filter:blur(14px) saturate(140%);
      -webkit-backdrop-filter:blur(14px) saturate(140%);
      border-radius:var(--radius);
      box-shadow:var(--shadow);
    }
    .chip{display:inline-block;padding:.25rem .6rem;border-radius:999px;border:1px solid color-mix(in oklab,#fff 25%,transparent);}

    /* ===== BACKGROUND (animated blobs, reduced for motion-sensitive users) ===== */
    body::before,
    body::after{
      content:"";position:fixed;inset:-20%;z-index:-2;filter:blur(70px);opacity:.6;pointer-events:none;
      background:
        radial-gradient(600px 420px at 15% 20%, color-mix(in oklab,var(--accent) 60%, transparent) 0%, transparent 60%),
        radial-gradient(520px 380px at 85% 25%, color-mix(in oklab,var(--accent-2) 65%, transparent) 0%, transparent 60%),
        radial-gradient(700px 520px at 50% 90%, color-mix(in oklab,#34d399 55%, transparent) 0%, transparent 60%);
      animation:float 26s ease-in-out infinite alternate;
    }
    @keyframes float{to{transform:translate3d(2%, -1%, 0) scale(1.02)}}
    @media (prefers-reduced-motion: reduce){body::before,body::after{animation:none}}

    /* Subtle dark canvas to increase contrast with glass */
    body{color:#eef1f7;background:radial-gradient(1200px 900px at 50% 0%, #0b1020 0%, var(--bg-2) 55%) fixed;
      background-color:var(--bg-2);
    }

    /* ===== LAYOUT ===== */
    .layout{max-width:min(var(--max-w), calc(100vw - (var(--sidebar-w) + var(--gap) + 32px)));margin:0 auto; padding:24px 24px 80px; padding-right:calc(var(--sidebar-w) + var(--gap));}
    main{min-width:0}

    /* Sticky/Fixed sidebar */
    aside{position:fixed;right:16px;top:14vh;width:var(--sidebar-w);z-index:50}
    .toc{padding:12px}
    .toc h3{margin:6px 10px 10px;font-size:14px;letter-spacing:.02em;opacity:.9}
    .toc a{display:block;margin:6px;padding:9px 10px;border-radius:12px;text-decoration:none;color:#e6e9f2;outline:none;transition:.25s ease}
    .toc a:hover{background:color-mix(in oklab,#fff 9%, transparent);box-shadow:0 0 0 1px color-mix(in oklab,#fff 14%, transparent), 0 6px 18px rgba(0,0,0,.25)}
    .toc a:focus-visible{box-shadow:var(--ring)}
    .toc a.active{background:color-mix(in oklab,#fff 16%, transparent)}

    /* Hero */
    header.hero {
    margin-bottom: 18px;
    }

    header.hero img {
    width: 60%;                
    height: auto;          
    display: block;            
    margin: 0 auto;          
    border-radius: 18px;
    border: 1px solid color-mix(in oklab, #fff 25%, transparent);
    box-shadow: var(--shadow);
    }

    header.hero h1 {
    font-size: clamp(28px, 4vw, 44px);
    line-height: 1.1;
    margin: 14px 4px 6px;
    }

    header.hero p {
    opacity: .9;
    margin: 0 4px 10px;
    }

    /* Section cards */
    section.box{padding:18px 18px 16px;margin:20px 0;}
    section.box h2{margin:0 0 8px;font-size:clamp(18px,2.2vw,26px)}
    section.box p, section.box li, section.box dd{color:#e9edf7;opacity:.95}
    section.box a{color:#dbeafe}
    section.box a:hover{text-decoration:underline}

    /* Color accents via top border glow */
    .accent-green{box-shadow:inset 0 1px 0 0 #34d39944, 0 10px 30px rgba(0,0,0,.25)}
    .accent-blue{box-shadow:inset 0 1px 0 0 #60a5fa44, 0 10px 30px rgba(0,0,0,.25)}
    .accent-orange{box-shadow:inset 0 1px 0 0 #f59e0b44, 0 10px 30px rgba(0,0,0,.25)}
    .accent-purple{box-shadow:inset 0 1px 0 0 #c084fc44, 0 10px 30px rgba(0,0,0,.25)}
    .accent-teal{box-shadow:inset 0 1px 0 0 #2dd4bf44, 0 10px 30px rgba(0,0,0,.25)}
    .accent-indigo{box-shadow:inset 0 1px 0 0 #818cf844, 0 10px 30px rgba(0,0,0,.25)}

    /* Lists & description list */
    ul{padding-left:1.2rem}
    dt{font-weight:700;margin-top:.5rem}
    dd{margin:0 0 .6rem 0}

    /* Responsive */
    @media (max-width: 980px){
      .layout{max-width:100%;padding-right:24px}
      aside{position:static;width:auto;margin:0 24px 16px}
      .toc{border-radius:16px}
    }

    /* Fallback if no backdrop-filter support */
    @supports not ((backdrop-filter: blur(1px)) or (-webkit-backdrop-filter: blur(1px))){
      .glass{background:rgba(20,24,38,.88)}
    }
  </style>
</head>
<body>
  <div id="top"></div>

  <div class="layout">
    <main>
      <header class="hero">
        <a href="Cricut.png" target="_blank" rel="noopener">
          <img src="Cricut.png" alt="Cricut Maker 3" />
        </a>
        <h1>Cricut Maker 3</h1>
        <p class="chip glass">DD Lab · Vinylskærer</p>
      </header>

      <section id="intro" class="box glass accent-green">
        <p>
          Cricut Maker 3 er en avanceret skæremaskine, der kan håndtere mere end 300 forskellige materialer – fra tyndt papir og vinyl til stof, læder og tyndt træ. Den giver dig mulighed for at lave alt fra simple klistermærker til komplekse prototyper med høj præcision.
          <br>Maskinen kan både skære, præge, gravere og ridse, og med funktionen <b>print‑then‑cut</b> kan du printe dine egne designs og derefter få dem skåret ud i perfekte konturer.
          <br>Alt styres gennem softwaren <b>Design Space</b>, hvor du kan uploade dine egne filer eller bruge færdige skabeloner.
          <br><br>Det gør Cricut Maker 3 til et fleksibelt værktøj – uanset om du vil lave kreative projekter, personlige gaver eller eksperimentere med nye materialer i værkstedet.
          <br><br>Maskinen kan findes i DD Lab (kan ikke lånes ud). Spørg en DD Lab ansat om hjælp, for hurtigere at komme i gang.
        </p>
        <p>
          <a class="chip glass" href=" https://www.youtube.com/watch?v=S_hH581tj6M" target="_blank" rel="noopener">Start med denne video</a>
        </p>
      </section>

      <section id="mats" class="box glass accent-blue">
        <h2>Tilgængelige måtter</h2>
        <p><b>LightGrip</b><br>til lette materialer som printerpapir, tyndt karton eller vellum. Holder fast uden at rive.</p>
        <p><b>StandardGrip</b><br>til almindelige materialer som karton, vinyl og jern‑på‑folie. Den mest brugte “allround” måtte.</p>
        <p><b>StrongGrip</b><br>til tunge eller meget stive materialer som kraftigt karton, glitterkarton, chipboard eller træfinér.</p>
        <p><b>FabricGrip</b><br>specielt til stof. Bruges sammen med stofklinger, holder stoffet fast uden at ødelægge fibrene.</p>
        <p><a class="chip glass" href="https://cricut.com/blog/which-cricut-mat-should-you-use/" target="_blank" rel="noopener">Mat Guide (officiel)</a></p>
        <a href="mats.png" target="_blank" rel="noopener">
          <img class="glass" style="border-radius:14px;border:1px solid color-mix(in oklab,#fff 25%, transparent)" src="mats.png" alt="Cricut måtter" />
        </a>
      </section>

      <section id="general" class="box glass accent-orange">
        <h2>Generelt for alle måtter</h2>
        <ul>
          <li>Læg altid det gennemsigtige beskyttelsesark på efter brug, så de ikke samler støv.</li>
          <li>Brug en skraber til at fjerne små stykker papir/vinyl og en spatel til at løfte tingene nænsomt af.</li>
          <li>Undgå fingre på klæben – fedt fra huden ødelægger limen.</li>
          <li>Rens forsigtigt med en fnugfri klud og evt. lidt mildt vand (ikke sæbe eller sprit).</li>
          <li>Læg aldrig måtten i direkte sol eller varme – klæben kan tørre ud.</li>
        </ul>
      </section>

      <section id="specific" class="box glass accent-purple">
        <h2>Specifikt for hver måtte</h2>
        <dl>
          <dt>LightGrip</dt>
          <dd>Pas på at materialer ikke løsner sig midt i skæringen (især tyndt papir). Sørg for at glatte det godt fast.</dd>
          <dt>StandardGrip</dt>
          <dd>Kan være lidt for stærk til meget tynde materialer – her risikerer man, at papiret flosser, når man tager det af.</dd>
          <dt>StrongGrip</dt>
          <dd>Klæben er meget kraftig – brug ofte malertape eller maskeringstape rundt i kanterne, så materialet sidder ekstra fast. Vær forsigtig, når du fjerner materialet, ellers kan det knække.</dd>
          <dt>FabricGrip</dt>
          <dd>Brug kun til stof og med den rigtige klinge (rotary blade). Undgå at bruge papir eller vinyl på den.</dd>
        </dl>
      </section>

      <section id="materiale" class="box glass accent-teal">
        <h2>Materiale</h2>
        <p>Vi har som regel forskellige typer akryl og papir til rådighed. Da vi udelukkende anvender officielle og bedst egnede materialer, er de desværre for dyre til at kunne tilbydes gratis. Derfor skal der betales for materialer i forbindelse med projekter – både undervisningsrelaterede og fritidsprojekter.</p>
        <p><a class="chip glass" href="https://auwebshop.au.dk/udstyr/materialer" target="_blank" rel="noopener">Betal inde på vores Webshop</a></p>
        <h3>Self anskaffet materiale</h3>
        <p>Det er muligt selv at skaffe materiale, da brugen af maskinen er gratis. Det kræver at man køber kompatibelt materiale af officiel udbyder (eller tilsvarende høj kvalitet).</p>
        <p>Tjek eventuelt: <a class="chip glass" href="https://www.elgiganten.dk/computer-kontor/printere-kontor/digital-skaremaskine" target="_blank" rel="noopener">Elgiganten</a> <a class="chip glass" href="https://makerstudio.dk/alt-til-cricut-joy_163" target="_blank" rel="noopener">makerstudio</a></p>
        
        <h3>Eksempler på materialer</h3>
        <p><b>Smart akryl</b> (permanent)<br>Selvklæbende vinyl med stærk lim, beregnet til langtidsholdbare projekter. Tåler vand og sollys og bruges fx på glas, metal, plastik og skilte.</p>
        <p><b>Smart akryl (flytbar)</b><br>Ligner den permanente version, men med en mildere lim. Kan fjernes uden at efterlade mærker.</p>
        <p><b>Smart papir</b><br>Klæbende bagside, så du kan skære og sætte direkte på projektet uden lim. Bruges til kort, scrapbooking eller klistermærker.</p>
        <p><b>Smart papir (transparent / vandfast)</b><br>En klar, vandafvisende variant af smart papir – perfekt til etiketter, glas eller udendørs brug.</p>
        <p><b>Iron‑on (varmeoverførsel / HTV)</b><br>Materiale der overføres med varme på stof, tekstiler eller poser. Fås i mange farver, metallic eller glimmer.</p>
        <h4>Flere materialer Cricut Maker 3 kan bruge:</h4>
        <p>Karton og papir (almindelig, glimmer, kraft)<br>
        Stof (med backing)<br>
        Læder og imiteret læder<br>
        Balsatræ og finer<br>
        Skumark (foam)<br>
        Vinyl (ikke‑smart, bruges med måtte)<br>
        Transfer tape (til at flytte udskårne designs)</p>

        <h3>Materialer på lager</h3>
    <p><em>Udvalget kan variere i den nærmeste tid, da vi tester forskellige typer.</em></p>
    <ul>
    <li>Almindeligt A4-klistermærkepapir</li>
    <li>A4-klistermærkepapir, vandfast og skinnende</li>
    <li>A4-klistermærkepapir, vandfast, skinnende og transparent</li>
    <li>A4-klistermærkepapir, vandfast og transparent</li>
    <li>A4-klistermærkepapir, vandfast og hvidt</li>
    <li>Vinylruller i forskellige farver — både permanent og flytbar</li>
    </ul>
      </section>

      <section id="software" class="box glass accent-indigo">
        <h2>Software</h2>
        <p>Hent software for at komme i gang med Vinylcutter'en. Den rigtige version er: <b>"Cricut Maker 3"</b></p>
        <p>De essentielle funktioner er GRATIS. Der er add‑ons og in‑app purchases, dem skal I som udgangspunkt se bort fra.</p>
        <p><a class="chip glass" href="https://design.cricut.com" target="_blank" rel="noopener">https://design.cricut.com</a></p>
        <h4>Links</h4>
        <p><a class="chip glass" href="https://help.cricut.com/hc/en-us/articles/1500007912041-All-About-Smart-Materials" target="_blank" rel="noopener">All about smart materials</a></p>
        <p><a class="chip glass" href="https://help.cricut.com/hc/en-us/articles/360009387274-How-to-Print-Then-Cut-in-Design-Space" target="_blank" rel="noopener">Print‑Then‑Cut (klistermærker)</a></p>
      </section>

      <section id="inspiration" class="box glass accent-indigo">
        <h2>Inspiration</h2>
        <p><a class="chip glass" href="https://www.youtube.com/@Cricut/videos" target="_blank" rel="noopener">https://www.youtube.com/@Cricut/videos</a></p>
        <p><a class="chip glass" href="https://help.cricut.com/hc/en-us/articles/360061650414-How-to-use-the-Offset-feature-in-Design-Space" target="_blank" rel="noopener">Tilføj offset/outline til dit design</a></p>
        <h4>Formål</h4>
        <p>Skær illustrationer af grænseflader ud i smart‑papir eller vinyl – fx knapper, ikoner og overlays, du kan flytte rundt på skærmmockups, whiteboards eller fysiske modeller.</p>
        <p>Kombinér Cricut‑skårne dele (pap, akryl, tyndt træ) med Arduino, MakeyMakey eller sensorer, så du får små, klikbare brugerflader.</p>
        <p>Skær logos, skiltning, stickers og etiketter til installationer, udstillinger eller projektdemoer.</p>
        <p>Mere på vej. Har du fundet eller selv skabt noget godt? Send det til os :)</p>
      </section>
    </main>

    <!-- RIGHT SIDEBAR NAV -->
    <aside aria-label="Menu" class="glass toc">
      <h3>Navigation</h3>
      <a href="#top">Top</a>
      <a href="#mats">Tilgængelige måtter</a>
      <a href="#general">Generelt</a>
      <a href="#specific">Specifikt pr. måtte</a>
      <a href="#materiale">Materiale</a>
      <a href="#software">Software</a>
      <a href="#inspiration">Inspiration</a>
    </aside>
  </div>

  <script>
    const ids = ["top","intro","mats","general","specific","software","inspiration"];
    const sections = ids.map(id => document.getElementById(id)).filter(Boolean);
    const navLinks = [...document.querySelectorAll('.toc a')];

    const setActive = (id) => {
      navLinks.forEach(link => link.classList.toggle('active', link.getAttribute('href') === '#' + id));
    };

    // Fallback: set top active on load
    setActive('top');

    const observer = new IntersectionObserver((entries) => {
      // Choose the entry nearest to viewport top and intersecting
      const visible = entries
        .filter(e => e.isIntersecting)
        .sort((a,b) => a.boundingClientRect.top - b.boundingClientRect.top)[0];
      if(visible){ setActive(visible.target.id || 'top'); }
    }, { rootMargin: "-20% 0px -70% 0px", threshold: [0, 0.2, 0.6] });

    sections.forEach(sec => observer.observe(sec));
  </script>
</body>
</html>
