<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Para mi Amor 💙</title>
  <style>
    body {
      font-family: "Segoe UI", sans-serif;
      background: linear-gradient(135deg, #a2d2ff, #ffc8dd);
      text-align: center;
      padding: 50px 20px;
      color: #333;
      overflow-x: hidden;
      min-height: 100vh;
    }

    /* Corazones flotando en el fondo */
    body::before {
      content: "💖 💕 💗 💓";
      position: fixed;
      top: -10%;
      left: 50%;
      font-size: 40px;
      animation: fondoCorazones 15s linear infinite;
      opacity: 0.3;
      z-index: 0;
    }
    @keyframes fondoCorazones {
      0% { transform: translateX(0) translateY(0); }
      100% { transform: translateX(-50vw) translateY(110vh); }
    }

    /* Animación de inicio */
    #inicio h1, #inicio h2 {
      opacity: 0;
      transform: translateY(-20px);
      animation: aparecer 1.5s forwards;
    }
    #inicio h2 {
      animation-delay: 0.5s;
    }
    @keyframes aparecer {
      to {
        opacity: 1;
        transform: translateY(0);
      }
    }

    /* Caja carta */
    #carta {
      display: none;
      background: white;
      padding: 30px;
      border-radius: 15px;
      box-shadow: 0px 4px 15px rgba(0,0,0,0.2);
      max-width: 600px;
      margin: 30px auto;
      font-size: 18px;
      line-height: 1.6;
      opacity: 0;
      transition: opacity 1s ease-in-out;
      position: relative;
      z-index: 1;
    }

    input {
      padding: 10px;
      border-radius: 10px;
      border: none;
      font-size: 16px;
      margin-top: 10px;
      text-align: center;
    }

    button {
      margin-top: 15px;
      padding: 10px 20px;
      border: none;
      border-radius: 10px;
      background: #ff85a1;
      color: white;
      font-size: 16px;
      cursor: pointer;
    }
    button:hover {
      background: #ff5d85;
    }

    #controlMusica {
      display: none;
      margin-top: 40px;
      background: #e63973;
      font-size: 18px;
    }
    #controlMusica:hover {
      background: #c2185b;
    }
    .latido {
      animation: latido 1s infinite;
    }
    @keyframes latido {
      0% { transform: scale(1); }
      25% { transform: scale(1.2); }
      50% { transform: scale(1); }
      75% { transform: scale(1.2); }
      100% { transform: scale(1); }
    }

    /* Pregunta romántica */
    #pregunta {
      display: none;
      margin-top: 40px;
    }
    #pregunta h1 {
      font-size: 40px;
      color: #d63384;
      margin-bottom: 30px;
    }
    .opciones {
      display: flex;
      justify-content: center;
      gap: 40px;
      position: relative;
    }
    .opcion {
      padding: 20px 40px;
      border-radius: 15px;
      font-size: 24px;
      font-weight: bold;
      cursor: pointer;
      transition: transform 0.3s ease;
    }
    .opcion:hover {
      transform: scale(1.1);
    }
    .si {
      background: #ff4d6d;
      color: white;
      animation: brillo 1.5s infinite alternate;
    }
    .no {
      background: #6c757d;
      color: white;
      position: relative;
    }
    @keyframes brillo {
      from { box-shadow: 0 0 10px #ff4d6d; }
      to { box-shadow: 0 0 30px #ff4d6d; }
    }

    /* Corazones animados */
    .corazon {
      position: fixed;
      font-size: 25px;
      animation: flotar 4s linear infinite;
      z-index: 999;
      pointer-events: none;
    }
    @keyframes flotar {
      from { transform: translateY(100vh) scale(1); opacity: 1; }
      to { transform: translateY(-10vh) scale(1.5); opacity: 0; }
    }

    /* Máquina de escribir */
    .typewriter {
      overflow: hidden;
      white-space: nowrap;
      border-right: 3px solid #ff4d6d;
      animation: typing 5s steps(50, end), blink .7s step-end infinite;
    }
    @keyframes typing {
      from { width: 0; }
      to { width: 100%; }
    }
    @keyframes blink {
      from, to { border-color: transparent; }
      50% { border-color: #ff4d6d; }
    }

    /* Mensaje sorpresa */
    #sorpresa {
      display: none;
      font-size: 40px;
      color: #ff4d6d;
      margin-top: 20px;
      font-weight: bold;
    }

    /* Responsive */
    @media (max-width: 600px) {
      #carta {
        font-size: 16px;
        padding: 20px;
      }
      .opcion {
        font-size: 18px;
        padding: 15px 20px;
      }
      #pregunta h1 {
        font-size: 28px;
      }
    }
  </style>
</head>
<body>
  <!-- INICIO -->
  <div id="inicio">
    <h1>MI AMOR</h1>
    <h2>💌 Tengo algo especial para ti...</h2>
    
    <p> Que día nos conocimos:</p>
    <input type="password" id="clave" placeholder="DD/MM/YYYY">
    <br>
    <button onclick="mostrarCarta()">Entrar</button>
  </div>
  
  <!-- CARTA -->
  <div id="carta">
    <h2>Para mi niña bonita ❤</h2>
    <p class="typewriter">
      Mi amor hoy quise escribirte, no porque me falten palabras cuando estoy contigo, sino porque a veces siento que lo que llevo dentro no cabe en un solo “te amo”.
    </p>
    <p>
      Quiero que sepas, desde lo más profundo de mi corazón, lo importante que eres para mí, eres mi alegría, mi paz, y el motivo más grande por el que sonrío cada día...
    </p>

    <!-- Pregunta romántica -->
    <div id="pregunta">
      <h1>¿Puedo ser tu novio? 💍</h1>
      <div class="opciones">
        <div class="opcion si" onclick="aceptar()">Siii 💖</div>
        <div class="opcion no" onclick="rechazar()">No 😢</div>
      </div>
    </div>

    <div id="sorpresa">💍 Eres el amor de mi vida 💍</div>

    <!-- Botón de música al final -->
    <button id="controlMusica" onclick="toggleMusica()">❤️ Pausar Música</button>
  </div>

  <!-- Música -->
  <audio id="musica" loop>
    <source src="musica.mp3" type="audio/mpeg">
    Tu navegador no soporta audio.
  </audio>

  <script>
    const passwordCorrecta = "15/05/2025"; 
    let reproduciendo = false;

    // Verificar si ya entró
    if(localStorage.getItem("entro") === "true"){
      mostrarCarta(true);
    }

    function mostrarCarta(yaEntro = false) {
      const clave = document.getElementById("clave").value.trim();
      if(yaEntro || clave === passwordCorrecta){
        localStorage.setItem("entro", "true");
        document.getElementById("inicio").style.display = "none";

        const carta = document.getElementById("carta");
        carta.style.display = "block";
        setTimeout(() => {
          carta.style.opacity = "1";
        }, 50);

        const musica = document.getElementById("musica");
        musica.volume = 0.4; 
        musica.play();
        reproduciendo = true;

        const boton = document.getElementById("controlMusica");
        boton.style.display = "inline-block";
        boton.innerHTML = "❤️ Pausar Música";
        boton.classList.add("latido");

        document.getElementById("pregunta").style.display = "block";
      } else {
        alert("Día en el que hablamos por Omegle 💕 (Formato: DD/MM/YYYY)");
      }
    }

    function toggleMusica() {
      const musica = document.getElementById("musica");
      const boton = document.getElementById("controlMusica");

      if (reproduciendo) {
        musica.pause();
        boton.innerHTML = "💔 Reanudar Música";
        boton.classList.remove("latido");
        reproduciendo = false;
      } else {
        musica.play();
        boton.innerHTML = "❤️ Pausar Música";
        boton.classList.add("latido");
        reproduciendo = true;
      }
    }

    function aceptar() {
      for (let i = 0; i < 30; i++) {
        crearCorazon();
      }
      document.getElementById("sorpresa").style.display = "block";
      document.getElementById("sorpresa").animate([
        { transform: "scale(0)", opacity: 0 },
        { transform: "scale(1.2)", opacity: 1 },
        { transform: "scale(1)", opacity: 1 }
      ], { duration: 1000, easing: "ease-out" });
    }

    function rechazar() {
      const noBtn = document.querySelector(".no");
      noBtn.style.position = "absolute";
      noBtn.style.top = Math.random() * window.innerHeight * 0.8 + "px";
      noBtn.style.left = Math.random() * window.innerWidth * 0.8 + "px";
    }

    function crearCorazon() {
      const corazon = document.createElement("div");
      corazon.classList.add("corazon");
      corazon.textContent = "💖";
      corazon.style.left = Math.random() * 100 + "vw";
      corazon.style.animationDuration = (3 + Math.random() * 2) + "s";
      document.body.appendChild(corazon);
      setTimeout(() => {
        corazon.remove();
      }, 5000);
    }
  </script>
</body>
</html>
