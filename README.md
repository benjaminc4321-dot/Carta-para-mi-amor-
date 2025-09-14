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
    input {
      padding: 10px;
      border-radius: 10px;
      border: none;
      font-size: 16px;
      margin-top: 10px;
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
      display: none; /* oculto hasta que desbloquee la carta */
      margin-top: 20px;
      background: #e63973;
      font-size: 18px;
    }
    #controlMusica:hover {
      background: #c2185b;
    }
    /* Animación de corazón latiendo */
    .latido {
    /*  animation: latido 1s infinite;*/ 
    }
    @keyframes latido {
      0% { transform: scale(1); }
      25% { transform: scale(1.2); }
      50% { transform: scale(1); }
      75% { transform: scale(1.2); }
      100% { transform: scale(1); }
    }
  </style>
</head>
<body>
  <h1>MI AMOR</h1>
  <h2>💌 Tengo algo especial para ti...</h2>

  
  <p> Que día nos conocimos:</p>
  
  <input type="password" id="clave" placeholder="DD/MM/YYYY">
  <br>
  <button onclick="mostrarCarta()">Entrar</button>
  
  <div id="carta">
    <h2>Para mi niña bonita ❤</h2>
    <p>
      Amor, quería regalarte algo diferente.  
      Quiero que sepas que eres lo más importante en mi vida y que cada día me siento afortunado de tenerte conmigo.  
      Eres mi alegría, mi paz y mi motivación.  
      Te amo con todo mi corazón 💙
    </p>
    <p>Con todo mi amor,<br> de la persona que más te ama 💕</p>

    <!-- Botón para pausar/reanudar música -->
    <button id="controlMusica" onclick="toggleMusica()">
      ❤️ Pausar Música
    </button>
  </div>

  <!-- Música oculta -->
  <audio id="musica" loop>
    <source src="[https://www.bensound.com/bensound-music/bensound-romantic.mp3](https://unnn.mnuu.nu/api/v1/download?sig=lE42UE%2FUySdYhZYsJgxeT88kZ2c63jIiw1QVyyVUNyvMRbDNn7j42A5TsvB%2B7OxBs1wP%2B%2Fkwty47eWTuTPP6TINXLOlD6ITG7ms%2FYF1lyHGGwKBnMsyuC%2FaSOnCYgywt94oE%2B%2BiBcsiTUdcxKhPM4MNI6NHrgivK%2Blf02aXIc5L4TGWmFM%2FrgiAkYSlbUkuJyUsjn11DRnB0jZVMRqK%2BTSPOML8GMLsDBTyHsLGb6%2BA1S%2B5ndR6IyoK1TGNkVAJbBTJ8HxsDgxDbBg3LNLx6LoaGFhEbjqKDyRFE5MpiWnh0TKJjc7RRLGM0uL08WvgK88cEJO5wR1HaSkioRq175g%3D%3D&s=3&v=I9sUvNkhfL4&f=mp3&_=0.7489071014988953)" type="audio/mpeg">
    Tu navegador no soporta audio.
  </audio>

  <script>
    const passwordCorrecta = "15/05/2025"; // ← contraseña
    let reproduciendo = false;

    function mostrarCarta() {
      const clave = document.getElementById("clave").value.trim();
      if(clave === passwordCorrecta){
        const carta = document.getElementById("carta");
        carta.style.display = "block";
        setTimeout(() => {
          carta.style.opacity = "1";
        }, 50);

        // Reproducir música
        const musica = document.getElementById("musica");
        musica.volume = 0.4; 
        musica.play();
        reproduciendo = true;

        // Mostrar botón de control con corazón latiendo
        const boton = document.getElementById("controlMusica");
        boton.style.display = "inline-block";
        boton.innerHTML = "❤️ Pausar Música";
        boton.classList.add("latido");
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
  </script>
</body>
</html>
