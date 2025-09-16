<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Para mi Amor 💙</title>
  <style>
    body {
      font-family: "Segoe UI", sans-serif;
      background: linear-gradient(135deg, #a2d2ff, #ffc8dd);
      text-align: center;
      padding: 50px;
      color: #333;
      overflow-x: hidden;
    }
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
    }
    input, button {
      padding: 10px 20px;
      border-radius: 10px;
      border: none;
      font-size: 16px;
      margin-top: 15px;
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
    /* Estilo de la gran pregunta */
    #pregunta {
      display: none;
      margin-top: 40px;
    }
    #pregunta h1 {
      font-size: 50px;
      color: #d63384;
      margin-bottom: 30px;
    }
    .opciones {
      display: flex;
      justify-content: center;
      gap: 40px;
    }
    .opcion {
      padding: 20px 40px;
      border-radius: 15px;
      font-size: 28px;
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
  </style>
</head>
<body>
  <!-- INICIO ocultable -->
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
    <p> 
      Mi amor hoy quise escribirte, no porque me falten las palabras cuando estoy contigo, sino porque a veces siento que lo que llevo dentro no cabe en un solo “te amo”...
    </p>
    <p>
      Amor, deseo con todo mi ser hacerte sentir amada todos los días... prometo estar contigo, crecer contigo, caminar contigo...
    </p>
    <p>
      Y mientras terminaba esta carta, me di cuenta de algo que cada palabra que te he escrito es más que amor, es una declaración.
    </p>

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

    <p id="mensajeFinal" style="display:none;">
      No importa cuántos kilómetros haya entre nosotros... Con todo mi amor de tu amorcito hermoso ❤️🥺
    </p>

    <!-- Botón de música al final -->
    <button id="controlMusica" onclick="toggleMusica()">❤️ Pausar Música</button>
  </div>

  <!-- 🎶 Música -->
 <audio id="musica" loop>
    <source src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3" type="audio/mpeg">
  </audio>
  <script>
    const passwordCorrecta = "15/05/2025"; 
    let reproduciendo = false;

    function mostrarCarta() {
      const clave = document.getElementById("clave").value.trim();
      if(clave === passwordCorrecta){
        // Ocultar inicio
        document.getElementById("inicio").style.display = "none";

        // Mostrar carta
        const carta = document.getElementById("carta");
        carta.style.display = "block";
        setTimeout(() => {
          carta.style.opacity = "1";
        }, 50);

        // Música
        const musica = document.getElementById("musica");
        musica.volume = 0.4; 
        musica.play();
        reproduciendo = true;

        // Mostrar botón de música
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
      alert("💖 Sabía que dirías que sí, mi amor 💖");
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
