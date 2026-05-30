<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Comedor Público Mathias Alexander Salzmann</title>
  <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&family=Oswald:wght@500&display=swap" rel="stylesheet">
  <style>
    body {
      font-family: 'Roboto', sans-serif;
      margin: 0;
      background: linear-gradient(270deg, #ff5722, #4caf50, #2196f3);
      background-size: 800% 800%;
      animation: rgbFondo 15s ease infinite;
      color: #fff;
      text-align: center;
      transition: background 0.5s, color 0.5s;
    }
    @keyframes rgbFondo {
      0% {background-position:0% 50%}
      50% {background-position:100% 50%}
      100% {background-position:0% 50%}
    }

    /* Hero con video */
    .hero {
      position: relative;
      height: 100vh;
      overflow: hidden;
    }
    .hero video {
      position: absolute;
      top: 0; left: 0;
      width: 100%; height: 100%;
      object-fit: cover;
      z-index: -1;
    }
    .hero h1 {
      font-family: 'Oswald', sans-serif;
      font-size: 56px;
      margin-top: 40vh;
      text-shadow: 2px 2px 6px #000;
    }

    /* Menú sticky */
    nav {
      background-color: rgba(0,0,0,0.8);
      padding: 15px;
      position: sticky;
      top: 0;
      z-index: 1000;
      display: flex;
      justify-content: center;
      gap: 20px;
    }
    nav a {
      color: white;
      text-decoration: none;
      font-weight: bold;
      padding: 10px 20px;
      border-radius: 20px;
      transition: all 0.3s ease;
    }
    nav a:hover {
      background: #ff9800;
      transform: translateY(-3px);
    }

    section {
      padding: 60px 20px;
      max-width: 900px;
      margin: auto;
      opacity: 0;
      transform: translateY(30px);
      transition: all 1s ease;
    }
    section.visible {
      opacity: 1;
      transform: translateY(0);
    }

    /* Botón CTA */
    .cta {
      background: #ff5722;
      color: white;
      padding: 15px 30px;
      border: none;
      border-radius: 30px;
      font-size: 18px;
      cursor: pointer;
      transition: all 0.3s ease;
    }
    .cta:hover {
      background: #e64a19;
      transform: scale(1.1);
    }

    /* Footer */
    footer {
      background: rgba(0,0,0,0.9);
      padding: 20px;
      margin-top: 40px;
    }
    footer a { color: lightblue; text-decoration: none; }
    footer a:hover { text-decoration: underline; }

    /* Botón ir arriba */
    #topBtn {
      position: fixed;
      bottom: 20px;
      right: 20px;
      background: #4caf50;
      color: white;
      border: none;
      border-radius: 50%;
      width: 50px; height: 50px;
      font-size: 20px;
      cursor: pointer;
      display: none;
    }

    /* Modo oscuro */
    .dark {
      background: #111;
      color: #eee;
    }
  </style>
</head>
<body>
  <!-- Hero con video -->
  <div class="hero">
    <video autoplay loop muted>
      <source src="https://www.w3schools.com/howto/rain.mp4" type="video/mp4">
    </video>
    <h1>Comedor Público Mathias Alexander Salzmann</h1>
  </div>

  <!-- Menú -->
  <nav>
    <a href="#inicio">Inicio</a>
    <a href="#historia">Historia</a>
    <a href="#imagenes">Imágenes</a>
    <a href="#donacion">Donación</a>
    <a href="#video">Video</a>
    <a href="#contacto">Contacto</a>
    <button onclick="toggleTheme()" class="cta">🌙/☀️</button>
  </nav>

  <!-- Secciones -->
  <section id="inicio">
    <h2>Bienvenidos</h2>
    <p>Dando cariño a los miembros, subdirector Samuel Capella.</p>
    <button class="cta">💰 Donar Ahora</button>
  </section>

  <section id="historia">
    <h2>Nuestra Historia</h2>
    <p>Mathias Salzmann, de pequeño, vendía cobre y cartón. Hoy, con éxito económico, decidió devolverle a su barrio creando este comedor solidario.</p>
  </section>

  <section id="imagenes">
    <h2>Imágenes</h2>
    <img src="TU_IMAGEN.png" alt="Imagen subida" width="300">
  </section>

  <section id="donacion">
    <h2>Alias de Donación</h2>
    <p><strong>Mathias.salzmann.cobre.carton</strong></p>
  </section>

  <section id="video">
    <h2>Video</h2>
    <iframe width="560" height="315" src="https://www.youtube.com/embed/AHt9nG-Ar4I?autoplay=1&mute=1"></iframe>
  </section>

  <section id="contacto">
    <h2>Contacto</h2>
    <p>comedorlatablada@gmail.com</p>
  </section>

  <!-- Footer -->
  <footer>
    <p>© 2026 Comedor Público Mathias Alexander Salzmann - La Tablada</p>
    <p>Hecho con ❤️ para la comunidad</p>
    <p><a href="https://es.wikipedia.org/wiki/La_Tablada" target="_blank">La Tablada</a> | 
       <a href="https://es.wikipedia.org/wiki/Comedor" target="_blank">Comedor</a> | 
       <a href="https://es.wikipedia.org/wiki/Solidaridad" target="_blank">Solidaridad</a></p>
  </footer>

  <!-- Botón ir arriba -->
  <button id="topBtn" onclick="window.scrollTo({top:0, behavior:'smooth'})">↑</button>

  <!-- Música con controles -->
  <audio id="bgMusic" autoplay loop>
    <source src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3" type="audio/mpeg">
  </audio>
  <div style="position:fixed;bottom:80px;right:20px;background:#000;padding:10px;border-radius:10px;">
    <button onclick="toggleMusic()">Play/Pause</button>
    <input type="range" min="0" max="1" step="0.1" value="0.3" onchange="setVolume(this.value)">
  </div>

  <script>
    // Scroll animations
    const sections = document.querySelectorAll("section");
    window.addEventListener("scroll", () => {
      sections.forEach(sec => {
        const rect = sec.getBoundingClientRect();
        if(rect.top < window.innerHeight - 100) sec.classList.add("visible");
      });
      document.getElementById("topBtn").style.display = window.scrollY > 200 ? "block" : "none";
    });

    // Música
    const music = document.getElementById("bgMusic");
    function toggleMusic(){
      if(music.paused){ music.play(); } else { music.pause(); }
    }
    function setVolume(val){ music.volume = val; }

    // Modo oscuro/claro
    function toggleTheme(){
      document.body.classList.toggle("dark");
    }
  </script>
</body>
</html>
