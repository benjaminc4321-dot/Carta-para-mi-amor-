
<html lang="es">
<head>
  <meta charset="utf-8" />
  <title></title>
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

    <p>Mi amor hoy quise escribirte, no porque me falten las palabras cuando estoy contigo, sino porque a veces siento que lo que llevo dentro no cabe en un solo “te amo”. Quiero que sepas, desde lo más profundo de mi corazón, lo importante que eres para mí, eres mi alegría, mi paz, y el motivo más grande por el que sonrío cada día, estar contigo me hace inmensamente feliz, aveces me detengo a pensar en cómo llegaste a mi vida, y no puedo evitar sentirme afortunado, eres esa persona con la que todo se siente más bonito, más sencillo, más real, sé que nuestra relación no es fácil, la distancia, a veces, duele más de lo que decimos, pero también sé que nuestro amor es más fuerte que cualquier kilómetro entre nosotros, porque aunque hoy no pueda abrazarte, ni tomar tu mano, te llevo conmigo en cada pensamiento, en cada suspiro, en cada sueño que tengo contigo, estamos lejos, si, pero eso solo significa que nos estamos preparando para estar tan cerca que nada ni nadie pueda separarnos.</p>

    <p>Amor, deseo con todo mi ser hacerte sentir amada todos los días, aún desde la distancia, quiero que nunca te falte un abrazo mío, aunque por ahora sea imaginario, una palabra de aliento, un “te amo” que te recuerde lo valiosa que eres, me esfuerzo, y me seguiré esforzando, por ser alguien que sume a tu vida, que te cuide, que te haga sentir en paz, segura, feliz estés donde estés, más allá de las palabras, quiero que lo nuestro funcione, y que cada paso que demos juntos nos acerque más a eso que tanto soñamos, construir una vida a tu lado, casarnos, compartir los días buenos y también los difíciles, y saber que siempre nos tendremos el uno al otro, ese sueño que hemos grabado en nuestras conversaciones, en nuestros planes, en cada promesa que nos hemos hecho lo quiero vivir contigo, amor. Quiero que se haga realidad, prometo seguir amándote con fuerza, con paciencia, con entrega, prometo estar contigo, crecer contigo, caminar contigo, y cuando llegue ese día, cuando al fin estemos juntos, volveré a prometerte, frente al mundo, todo lo que ya hoy te prometo con el corazón.</p>

    <p>Y mientras terminaba esta carta, me di cuenta de algo que cada palabra que te he escrito es más que amor, es una declaración.Así que no quiero terminar sin preguntarte:
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

    <p id="mensajeFinal">
     No importa cuántos kilómetros haya entre nosotros, lo que siento por ti los atraviesa todos. Yo te elijo, aún en la distancia, y te seguiré eligiendo cuando por fin estemos frente a frente.Gracias por ser tú, gracias por elegirme cada día, yo te elijo a ti, siempre, incluso en la distancia y mucho más cuando por fin no haya ninguna. Con todo mi amor de tu amorcito hermoso ❤️🥺
     
      Hoy tal vez nos tocó pedirlo de esta manera, a la distancia, a través de una pantalla… pero te prometo que cuando nos veamos será diferente. Con el corazón latiendo a mil, frente a frente, te volveré a pedir, por milésima vez, que seas mi novia. Esta vez sin distancia, sin pantallas, solo tú y yo, mirándonos a los ojos y escuchando un “sí” que nos pertenezca solo a nosotros.
    </p>

    
  </div>

  <script>
    const passwordCorrecta = "15/05/2025"; 

    function mostrarCarta(){
      const clave = document.getElementById("clave").value.trim();
      if(clave === passwordCorrecta){
        document.getElementById("inicio").style.display = "none";
        const carta = document.getElementById("carta");
        carta.style.display = "block";
        setTimeout(()=> carta.style.opacity = "1", 50);
      } else {
        alert("Día en el que hablamos por Omegle 💕 (Formato: DD/MM/YYYY)");
      }
    }

    function mostrarPregunta(){
      document.getElementById("pregunta").style.display = "block";
      document.getElementById("btnSiguiente").style.display = "none";
      document.getElementById("mensajeFinal").style.display = "block";
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
  </script>
</body>
</html>
