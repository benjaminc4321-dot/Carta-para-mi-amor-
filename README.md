<!doctype html>
<html lang="es">
<head>
  <meta charset="utf-8" />
  <title>Para mi Amor 💙</title>
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <style>
    body {
      font-family: "Segoe UI", sans-serif;
      background: linear-gradient(135deg, #a2d2ff, #ffc8dd);
      text-align: center;
      padding: 30px;
      color: #333;
      overflow-x: hidden;
    }
    #carta {
      display: none;
      background: white;
      padding: 20px;
      border-radius: 15px;
      box-shadow: 0px 4px 15px rgba(0,0,0,0.2);
      max-width: 700px;
      margin: 30px auto;
      font-size: 18px;
      line-height: 1.6;
      opacity: 0;
      transition: opacity 1s ease-in-out;
    }

    /* FOTO */
    .fotoBox {
      display: flex;
      justify-content: center;
      margin-top: 15px;
    }
    #foto {
      width: 200px;
      height: 200px;
      object-fit: cover;
      border-radius: 16px;
      box-shadow: 0 6px 18px rgba(0,0,0,0.2);
      cursor: pointer;
      transition: transform .25s ease;
    }
    #foto:hover { transform: scale(1.05); }

    /* Modal visor */
    .modal {
      display: none;
      position: fixed;
      inset: 0;
      background: rgba(0,0,0,0.6);
      align-items: center;
      justify-content: center;
      z-index: 9999;
    }
    .modal img {
      max-width: 90%;
      max-height: 80%;
      border-radius: 12px;
      box-shadow: 0 10px 40px rgba(0,0,0,0.5);
    }
    .cerrar {
      position: absolute;
      top: 20px;
      right: 30px;
      font-size: 28px;
      color: white;
      cursor: pointer;
    }

    input, button {
      padding: 10px 18px;
      border-radius: 10px;
      border: none;
      font-size: 16px;
      margin-top: 12px;
      cursor: pointer;
    }
    button {
      background: #ff85a1;
      color: white;
    }
    button:hover {
      background: #ff5d85;
    }

    #controlMusica {
      display: none;
      margin-top: 20px;
      background: #e63973;
      font-size: 18px;
    }
    .latido { animation: latido 1s infinite; }
    @keyframes latido {
      0% { transform: scale(1); } 25% { transform: scale(1.15); } 50% { transform: scale(1); } 75% { transform: scale(1.15); } 100% { transform: scale(1); }
    }

    #pregunta { display: none; margin-top: 20px; }
    #pregunta h1 { font-size: 46px; color: #d63384; margin-bottom: 20px; }
    .opciones { display:flex; justify-content:center; gap:30px; flex-wrap:wrap; }
    .opcion { padding: 16px 28px; border-radius: 12px; font-size: 24px; font-weight:700; cursor:pointer; transition: transform .2s; }
    .opcion:hover { transform: scale(1.05); }
    .si { background:#ff4d6d; color:white; animation: brillo 1.5s infinite alternate; }
    .no { background:#6c757d; color:white; }
    @keyframes brillo { from { box-shadow: 0 0 8px #ff4d6d } to { box-shadow: 0 0 28px #ff4d6d } }

    .corazon { position: fixed; font-size: 25px; animation: flotar 4s linear infinite; z-index: 999; pointer-events: none; }
    @keyframes flotar {
      from { transform: translateY(100vh) scale(1); opacity:1 }
      to   { transform: translateY(-10vh) scale(1.5); opacity:0 }
    }

    #mensajeFinal { display:none; margin-top:18px; }
  </style>
</head>
<body>
  <div id="inicio">
    <h1>MI AMOR</h1>
    <h2>💌 Tengo algo especial para ti...</h2>
    <p>¿Qué día nos conocimos?</p>
    <input type="password" id="clave" placeholder="DD/MM/YYYY" />
    <br />
    <button onclick="mostrarCarta()">Entrar</button>
  </div>

  <div id="carta">
    <h2>Para mi niña bonita ❤</h2>

    <p>Mi amor hoy quise escribirte... 💖</p>

    <p>Amor, deseo con todo mi ser hacerte sentir amada todos los días... 💖</p>

    <p>Y mientras terminaba esta carta... es una declaración.</p>

    <!-- Botón siguiente -->
    <button id="btnSiguiente" onclick="mostrarPregunta()">➡️ Siguiente</button>

    <!-- Pregunta romántica -->
    <div id="pregunta">
      <h1>¿Puedo ser tu novio? 💍</h1>
      <div class="opciones">
        <div class="opcion si" onclick="aceptar()">Siii 💖</div>
        <div class="opcion no" onclick="rechazar()">No 😢</div>
      </div>
    </div>

    <p id="mensajeFinal">
      No importa cuántos kilómetros haya entre nosotros...  
      Con todo mi amor de tu amorcito hermoso ❤️🥺
    </p>

    <!-- FOTO aquí después del texto final -->
   <div class="fotoBox" id="fotoBox" style="display:none;">
  <img id="foto" 
       src="https://drive.google.com/uc?export=view&id=1k0tUZ9Nb59tlBOxg4O1g-cZVe9P22VlB" 
       alt="Mi amorcito hermoso" />
</div>

    <button id="controlMusica" onclick="toggleMusica()">❤️ Pausar Música</button>
  </div>

  <!-- Modal visor -->
  <div id="modal" class="modal" onclick="cerrarModal(event)">
    <span class="cerrar" onclick="cerrarModal(event)">✖</span>
    <img id="modalImg" src="" alt="Foto grande" />
  </div>

  <audio id="musica" loop>
    <source src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3" type="audio/mpeg">
  </audio>

  <script>
    const passwordCorrecta = "15/05/2025"; 
    let reproduciendo = false;

    function mostrarCarta(){
      const clave = document.getElementById("clave").value.trim();
      if(clave === passwordCorrecta){
        document.getElementById("inicio").style.display = "none";
        const carta = document.getElementById("carta");
        carta.style.display = "block";
        setTimeout(()=> carta.style.opacity = "1", 50);

        const musica = document.getElementById("musica");
        musica.volume = 0.4; 
        musica.play().catch(()=>{});
        reproduciendo = true;

        const boton = document.getElementById("controlMusica");
        boton.style.display = "inline-block";
        boton.innerHTML = "❤️ Pausar Música";
        boton.classList.add("latido");
      } else {
        alert("Día en el que hablamos por Omegle 💕 (Formato: DD/MM/YYYY)");
      }
    }

    function mostrarPregunta(){
      document.getElementById("pregunta").style.display = "block";
      document.getElementById("btnSiguiente").style.display = "none";
      document.getElementById("mensajeFinal").style.display = "block";
      document.getElementById("fotoBox").style.display = "flex"; // aquí aparece la foto
    }

    function toggleMusica(){
      const musica = document.getElementById("musica");
      const boton = document.getElementById("controlMusica");
      if(reproduciendo){ musica.pause(); boton.innerHTML = "💔 Reanudar Música"; boton.classList.remove("latido"); reproduciendo=false; }
      else { musica.play(); boton.innerHTML = "❤️ Pausar Música"; boton.classList.add("latido"); reproduciendo=true; }
    }

    function aceptar(){
      for(let i=0;i<30;i++) crearCorazon();
      alert("💖 Sabía que dirías que sí, mi amor 💖");
    }

    function rechazar(){
      const noBtn = document.querySelector(".no");
      noBtn.style.position = "absolute";
      noBtn.style.top = Math.random() * window.innerHeight * 0.7 + "px";
      noBtn.style.left = Math.random() * window.innerWidth * 0.7 + "px";
    }

    function crearCorazon(){
      const c = document.createElement("div");
      c.className = "corazon";
      c.textContent = "💖";
      c.style.left = Math.random()*100 + "vw";
      c.style.animationDuration = (3 + Math.random()*2) + "s";
      document.body.appendChild(c);
      setTimeout(()=> c.remove(), 5000);
    }

    // Modal para la foto
    const modal = document.getElementById("modal");
    const modalImg = document.getElementById("modalImg");

    document.addEventListener("click", function(e){
      if(e.target.id === "foto"){
        modalImg.src = e.target.src;
        modal.style.display = "flex";
      }
    });

    function cerrarModal(){
      modal.style.display = "none";
      modalImg.src = "";
    }
  </script>
</body>
</html>
