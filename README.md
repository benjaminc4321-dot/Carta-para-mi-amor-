b
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
  </style>
</head>
<body>
  <h1>💌 Tengo algo especial para ti...</h1>
  <h2>MI AMOR</h2>
  
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
  </div>

  <!-- Música oculta -->
  <audio id="musica" loop>
    <source src="https://www.bensound.com/bensound-music/bensound-romantic.mp3" type="audio/mpeg">
    Tu navegador no soporta audio.
  </audio>

  <script>
    const passwordCorrecta = "15/05/2025"; // ← contraseña

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
        musica.volume = 0.4; // volumen bajito
        musica.play();
      } else {
        alert("Día en el que hablamos por Omegle 💕 (Formato: DD/MM/YYYY)");
      }
    }
  </script>
</body>
</html>
