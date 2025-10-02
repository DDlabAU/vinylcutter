<!DOCTYPE html>
<html lang="da">
<head>
  <meta charset="UTF-8" />
  <title>Vinylskærer i DDlab</title>
  <style>
    html { scroll-behavior: smooth; }
    *, *::before, *::after { box-sizing: border-box; }
    body {
      font-family: Arial, sans-serif;
      line-height: 1.6;
      margin: 0;
      background: #fafafa;
      color: #111;
    }

    /* CONTENT LAYOUT – centered container; no grid */
    .layout {
      /* reclaim middle space while reserving room for the fixed sidebar */
      --sidebar-w: 200px;
      --sidebar-gap: 20px;
      --container-max: 1200px;
      max-width: min(
        var(--container-max),
        calc(100vw - (var(--sidebar-w) + var(--sidebar-gap) + 40px))
      );
      margin: 0 auto;
      padding: 16px 20px 40px;
      padding-right: calc(var(--sidebar-w) + var(--sidebar-gap));
    }

    main { min-width: 0; }

    /* FIXED SIDEBAR hugging the scrollbar */
    aside {
      position: fixed;
      right: 10px;
      top: 20%;
      width: var(--sidebar-w);
      z-index: 2000;
    }

    .toc {
      border: 2px solid #e5e7eb;
      background: #ffffff;
      border-radius: 12px;
      padding: 12px;
      box-shadow: 0 2px 10px rgba(0,0,0,0.06);
    }
    .toc h3 {
      margin: 6px 8px 10px;
      font-size: 16px; font-weight: 700;
    }
    .toc a {
      display: block;
      margin: 6px 6px;
      padding: 8px 10px;
      text-decoration: none;
      color: #333;
      border-radius: 8px;
      transition: box-shadow 0.25s ease, background 0.25s ease, color 0.25s ease;
      outline: none;
    }
    .toc a:hover  { background: #e0f2fe; box-shadow: 0 0 8px rgba(33,150,243,0.5); }
    .toc a:active { background: #2196F3; color: #fff; box-shadow: inset 0 2px 6px rgba(0,0,0,0.3); }
    .toc a:focus  { box-shadow: 0 0 0 3px rgba(33,150,243,.35); }
    .toc a.active { background: #2196F3; color: #fff; }

    /* Section boxes */
    .box { border: 2px solid; padding: 15px; border-radius: 10px; margin: 20px 0; background: #fff; }
    .green  { border-color:#4CAF50; background:#f0fff0; }
    .blue   { border-color:#2196F3; background:#f0f8ff; }
    .orange { border-color:#FF9800; background:#fff8e1; }
    .purple { border-color:#9C27B0; background:#f3e5f5; }
    .teal   { border-color:#10B981; background:#ecfdf5; }
    .indigo { border-color:#6366F1; background:#eef2ff; }

    /* Responsive: on small screens, drop the fixed menu above content */
    @media (max-width: 900px) {
      .layout { 
        max-width: 100%;
        padding-right: 20px;
      }
      aside { position: static; width: auto; margin: 0 20px 12px; }
      .toc { width: 100%; }
    }

    @media (prefers-reduced-motion: reduce) {
      html { scroll-behavior: auto; }
      .toc a { transition: none; }
    }
  </style>
</head>
<body>
  <div id="top"></div>

  <div class="layout">
    <main>
      <a href="cricut-maker-3.jpeg" target="_blank" rel="noopener">
        <img src="cricut-maker-3.jpeg" alt="Cricut Maker 3" style="max-width:100%; height:auto; border-radius:10px;">
      </a>

      <h1 id="intro">Vinylskærer i DDlab</h1>
      <div class="box green">
        Cricut Maker 3 er en avanceret skæremaskine, der kan håndtere mere end 300 forskellige materialer – fra tyndt papir og vinyl til stof, læder og tyndt træ. Den giver dig mulighed for at lave alt fra simple klistermærker til komplekse prototyper med høj præcision.
        <br>Maskinen kan både skære, præge, gravere og ridse, og med funktionen print-then-cut kan du printe dine egne designs og derefter få dem skåret ud i perfekte konturer.
        <br>Alt styres gennem softwaren <b>Design Space</b>, hvor du kan uploade dine egne filer eller bruge færdige skabeloner.
        <br><br>Det gør Cricut Maker 3 til et fleksibelt værktøj – uanset om du vil lave kreative projekter, personlige gaver eller eksperimentere med nye materialer i værkstedet.
      </div>

      <div id="mats" class="box blue">
        <h2>Tilgængelige måtter</h2>
        <b>LightGrip</b><br>
        til lette materialer som printerpapir, tyndt karton eller vellum. Holder fast uden at rive.
        <br><br>
        <b>StandardGrip</b><br>
        til almindelige materialer som karton, vinyl og jern-på-folie. Den mest brugte “allround” måtte.
        <br><br>
        <b>StrongGrip</b><br>
        til tunge eller meget stive materialer som kraftigt karton, glitterkarton, chipboard eller træfinér.
        <br><br>
        <b>FabricGrip</b><br>
        specielt til stof. Bruges sammen med stofklinger, holder stoffet fast uden at ødelægge fibrene.
        <br><br>
        <a href="https://cricut.com/blog/which-cricut-mat-should-you-use/" target="_blank" rel="noopener">Mat Guide (officiel)</a><br><br>

        <a href="mats.png" target="_blank" rel="noopener">
          <img src="mats.png" alt="Cricut måtter" style="max-width:100%; height:auto; border-radius:10px;">
        </a>
      </div>

      <div id="general" class="box orange">
        <h2>Generelt for alle måtter:</h2>
        <ul>
          <li>Læg altid det gennemsigtige beskyttelsesark på efter brug, så de ikke samler støv.</li>
          <li>Brug en skraber til at fjerne små stykker papir/vinyl og en spatel til at løfte tingene nænsomt af.</li>
          <li>Undgå fingre på klæben – fedt fra huden ødelægger limen.</li>
          <li>Rens forsigtigt med en fnugfri klud og evt. lidt mildt vand (ikke sæbe eller sprit).</li>
          <li>Læg aldrig måtten i direkte sol eller varme – klæben kan tørre ud.</li>
        </ul>
      </div>

      <div id="specific" class="box purple">
        <h2>Specifikt for hver måtte:</h2>
        <dl>
          <dt><strong>LightGrip</strong></dt>
          <dd>Pas på at materialer ikke løsner sig midt i skæringen (især tyndt papir). Sørg for at glatte det godt fast.</dd>

          <dt><strong>StandardGrip</strong></dt>
          <dd>Kan være lidt for stærk til meget tynde materialer – her risikerer man, at papiret flosser, når man tager det af.</dd>

          <dt><strong>StrongGrip</strong></dt>
          <dd>Klæben er meget kraftig – brug ofte malertape eller maskeringstape rundt i kanterne, så materialet sidder ekstra fast. Husk at være forsigtig, når du fjerner materialet, ellers kan det knække.</dd>

          <dt><strong>FabricGrip</strong></dt>
          <dd>Brug kun til stof og med den rigtige klinge (rotary blade). Undgå at bruge papir eller vinyl på den, for det kan ødelægge overfladen og gøre den ubrugelig til stof.</dd>
        </dl>
      </div>

      <div id="software" class="box teal">
        <h2>Software</h2>
        <p>Hent software for at komme i gang med Vinylcutter'en.</p>
        <p><a href="https://design.cricut.com" target="_blank" rel="noopener">https://design.cricut.com</a></p>
      </div>

      <div id="inspiration" class="box indigo">
        <h2>Inspiration</h2>
        <p><a href="https://www.youtube.com/@Cricut/videos" target="_blank" rel="noopener">https://www.youtube.com/@Cricut/videos</a></p>
        <p>Mere på vej. Har du fundet eller selv skabt noget godt? Send det til os :)</p>
      </div>
    </main>

    <!-- FIXED RIGHT SIDEBAR NAV -->
    <aside aria-label="Indholdsfortegnelse">
      <nav class="toc">
        <h3>Navigation</h3>
        <a href="#top">Top</a>
        <a href="#intro">Intro</a>
        <a href="#mats">Tilgængelige måtter</a>
        <a href="#general">Generelt</a>
        <a href="#specific">Specifikt pr. måtte</a>
        <a href="#software">Software</a>
        <a href="#inspiration">Inspiration</a>
      </nav>
    </aside>
  </div>

  <!-- Scrollspy: highlight current section -->
  <script>
    const sections = document.querySelectorAll('#top, #intro, #mats, #general, #specific, #software, #inspiration');
    const navLinks = document.querySelectorAll('.toc a');

    function onScroll() {
      let current = 'top';
      const offset = 120;
      sections.forEach(sec => {
        const rectTop = sec.getBoundingClientRect().top;
        if (rectTop - offset <= 0) current = sec.id || 'top';
      });
      navLinks.forEach(link => {
        link.classList.toggle('active', link.getAttribute('href') === '#' + current);
      });
    }

    document.addEventListener('scroll', onScroll, { passive: true });
    window.addEventListener('load', onScroll);
  </script>
</body>
</html>
