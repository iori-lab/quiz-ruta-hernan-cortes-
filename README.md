# quiz-ruta-hernan-cortes-
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Quiz: Ruta de Hernán Cortés</title>
  <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap" rel="stylesheet"/>
  <style>
    body {
      font-family: 'Roboto', sans-serif;
      background: linear-gradient(135deg, #74ebd5 0%, #acb6e5 100%);
      margin: 0;
      padding: 0;
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 100vh;
      position: relative;
    }

    .animated-background {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      overflow: hidden;
      z-index: -1;
    }

    .bubble {
      position: absolute;
      bottom: -150px;
      width: 40px;
      height: 40px;
      background: rgb(238, 240, 241);
      border-radius: 50%;
      animation: rise 20s infinite ease-in;
    }

    .bubble:nth-child(1) { left: 20%; width: 60px; height: 60px; animation-duration: 25s; }
    .bubble:nth-child(2) { left: 40%; width: 30px; height: 30px; animation-duration: 18s; }
    .bubble:nth-child(3) { left: 60%; width: 50px; height: 50px; animation-duration: 22s; }
    .bubble:nth-child(4) { left: 80%; width: 40px; height: 40px; animation-duration: 20s; }
    .bubble:nth-child(5) { left: 90%; width: 35px; height: 35px; animation-duration: 26s; }

    @keyframes rise {
      0% { transform: translateY(0) scale(1); opacity: 0.4; }
      50% { opacity: 0.8; }
      100% { transform: translateY(-1000px) scale(1.2); opacity: 0; }
    }

    #container {
      background-color: #f4f1f1;
      border-radius: 16px;
      padding: 40px;
      max-width: 900px;
      width: 100%;
      box-shadow: 0 20px 40px rgba(0, 0, 0, 0.2);
      text-align: center;
      animation: fadeIn 1s ease-in-out;
      z-index: 1;
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(20px); }
      to { opacity: 1; transform: translateY(0); }
    }

    h1 { color: #3f51b5; margin-bottom: 20px; }
    .question { font-size: 20px; margin: 20px 0; }

    .question-block {
      display: flex;
      gap: 20px;
      align-items: center;
      justify-content: center;
      margin-bottom: 20px;
      flex-wrap: wrap;
    }

    .question-image {
      max-width: 280px;
      max-height: 200px;
      border-radius: 12px;
      box-shadow: 0 8px 16px rgba(0,0,0,0.2);
      flex-shrink: 0;
    }

    .options {
      display: flex;
      flex-direction: column;
      gap: 10px;
      flex: 1;
      min-width: 200px;
    }

    .option {
      padding: 12px 20px;
      font-size: 16px;
      border: none;
      border-radius: 10px;
      background-color: #0497f399;
      cursor: pointer;
      transition: all 0.3s ease;
    }

    .option:hover { background-color: #e0e0e0; }
    .option-correct { background-color: #05fc15 !important; }
    .option-incorrect { background-color: #fa0303 !important; }

    button {
      background-color: #3f51b5;
      color: white;
      padding: 12px 24px;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      margin-top: 20px;
      font-size: 16px;
      transition: background 0.3s ease;
    }

    button:hover { background-color: #303f9f; }
    #result h2 { color: #4caf50; }

    /* ✅ BLOQUE RESPONSIVO PARA TELÉFONOS */
    @media (max-width: 600px) {
      #container {
        padding: 20px;
      }

      .question-block {
        flex-direction: column;
        align-items: center;
      }

      .question-image {
        width: 100%;
        max-width: 300px;
        height: auto;
      }

      .option {
        font-size: 18px;
        padding: 14px;
      }

      button {
        font-size: 18px;
      }
    }
  </style>
</head>
<body>
  <div class="animated-background">
    <div class="bubble"></div>
    <div class="bubble"></div>
    <div class="bubble"></div>
    <div class="bubble"></div>
    <div class="bubble"></div>
  </div>

  <div id="container">
    <div id="start-screen">
      <h1>Quiz: Ruta de Hernán Cortés</h1>
      <button onclick="startQuiz()">Comenzar Quiz</button>
    </div>

    <div id="quiz" style="display:none;">
      <div class="question" id="question"></div>
      <div class="question-block">
        <img id="questionImage" class="question-image" src="" alt="" style="display:none;" />
        <div id="options" class="options"></div>
      </div>
      <div>
        <progress id="progressBar" value="0" max="100" style="width: 100%; height: 20px;"></progress>
        <p><span id="progressPercent">0%</span></p>
      </div>
    </div>

    <div id="result" style="display:none;"></div>
  </div>

  <script>
  const questions = [
  {
    question: "¿En qué año llegó Hernán Cortés a México?",
    options: ["1517", "1519", "1521", "1492"],
    answer: 1,
    image: "img/HernanCortes.jpg"
  },
  {
    question: "¿Cuál fue el primer lugar donde desembarcó Cortés?",
    options: ["Yucatán", "Tenochtitlan", "Veracruz", "Tabasco"],
    answer: 0,
    image: "img/llegada.jpg"
  },
  {
    question: "¿Qué ciudad fundó Cortés tras desembarcar?",
    options: ["Puebla", "Tenochtitlan", "Villa Rica de la Vera Cruz", "Tlaxcala"],
    answer: 2,
    image: "img/imagen3.jpg"
  },
  {
    question: "¿Qué hizo Cortés con sus naves al llegar?",
    options: ["Las escondió", "Las quemó", "Las reparó", "Las vendió"],
    answer: 1,
    image: "img/imagen4.jpg"
  },
  {
    question: "¿Qué grupo indígena fue aliado de Cortés?",
    options: ["Mexicas", "Tlaxcaltecas", "Zapotecas", "Purepechas"],
    answer: 1,
    image: "img/imagen5.jpg"
  },
  {
    question: "¿Cómo se llamó la intérprete de Cortés?",
    options: ["Doña Inés", "Malintzin", "Xochitl", "Citlali"],
    answer: 1,
    image: "img/imagen6.jpg"
  },
  {
    question: "¿Qué ciudad estaba sobre un lago y fue conquistada por Cortés?",
    options: ["Texcoco", "Tlatelolco", "Tenochtitlan", "Cholula"],
    answer: 2,
    image: "img/imagen7.jpg"
  },
  {
    question: "¿Quién era el emperador mexica cuando llegó Cortés?",
    options: ["Cuitláhuac", "Moctezuma II", "Cuauhtémoc", "Nezahualcóyotl"],
    answer: 1,
    image: "img/moctezuma.jpg"
  },
  {
    question: "¿Qué papel jugó la religión en la conquista?",
    options: ["Ninguno", "Los indígenas eran monoteístas", "Confusión religiosa", "Conversión forzada"],
    answer: 3,
    image: "img/imagen9.jpg"
  },
  {
    question: "¿Qué evento sangriento ocurrió en el Templo Mayor durante la conquista?",
    options: ["Matanza de Tóxcatl", "Noche Triste", "Sitio de Tenochtitlan", "Combate de Tlaxcala"],
    answer: 0,
    image: "img/imagen10.jpg"
  },
  {
    question: "¿Qué fue la Noche Triste?",
    options: ["Una fiesta", "Una rendición", "Una derrota de los españoles", "La muerte de Moctezuma"],
    answer: 2,
    image: "img/img11.jpg"
  },
  {
    question: "¿Qué ruta siguió Cortés hacia el altiplano?",
    options: ["Costa del Pacífico", "Costa del Golfo", "Sierra Madre Oriental", "Valle del Mezquital"],
    answer: 1,
    image: "img/imagen12.jpg"
  },
  {
    question: "¿Qué ciudad fue destruida para construir la Ciudad de México?",
    options: ["Tlaxcala", "Texcoco", "Tenochtitlan", "Cholula"],
    answer: 2,
    image: "img/ten.jpg"
  },
  {
    question: "¿Qué institución envió a Cortés al Nuevo Mundo?",
    options: ["Corona española", "Iglesia católica", "Virreinato", "Casa de Contratación"],
    answer: 0,
    image: "img/14.jpg"
  },
  {
    question: "¿Qué rey gobernaba España durante la conquista?",
    options: ["Carlos I", "Felipe II", "Fernando el Católico", "Carlos V"],
    answer: 3,
    image: "img/15.jpg"
  },
  {
    question: "¿Cuál fue el último emperador mexica?",
    options: ["Cuitláhuac", "Moctezuma II", "Cuauhtémoc", "Itzcóatl"],
    answer: 2,
    image: "img/imagen16.jpg"
  },
  {
    question: "¿Qué técnica militar usaron los españoles?",
    options: ["Armas de piedra", "Guerra de guerrillas", "Caballería y cañones", "Batallas navales"],
    answer: 2,
    image: "img/17.jpg"
  },
  {
    question: "¿Qué enfermedad debilitó a los mexicas?",
    options: ["Malaria", "Viruela", "Sarampión", "Dengue"],
    answer: 1,
    image: "img/18.jpg"
  },
  {
    question: "¿Qué ciudad fue aliada de Cortés contra los mexicas?",
    options: ["Tlaxcala", "Tlatelolco", "Texcoco", "Chiapas"],
    answer: 0,
    image: "img/19.jpg"
  },
  {
    question: "¿Qué documento justificaba la conquista de nuevas tierras?",
    options: ["La Biblia", "El Requerimiento", "La Bula Papal", "Las Leyes de Indias"],
    answer: 1,
    image: "img/20.jpg"
  }
];
    

    let currentQuestion = 0;
    let score = 0;
    let startTime;

    function startQuiz() {
      document.getElementById("start-screen").style.display = "none";
      document.getElementById("quiz").style.display = "block";
      document.getElementById("result").style.display = "none";
      currentQuestion = 0;
      score = 0;
      startTime = new Date();
      showQuestion();
    }

    function showQuestion() {
      const q = questions[currentQuestion];
      document.getElementById("question").textContent = q.question;

      const img = document.getElementById("questionImage");
      if (q.image) {
        img.src = q.image;
        img.style.display = "block";
      } else {
        img.style.display = "none";
      }

      const optionsDiv = document.getElementById("options");
      optionsDiv.innerHTML = "";

      q.options.forEach((opt, index) => {
        const btn = document.createElement("button");
        btn.textContent = String.fromCharCode(65 + index) + '. ' + opt;
        btn.className = "option";
        btn.onclick = () => checkAnswer(index, btn);
        optionsDiv.appendChild(btn);
      });

      updateProgressBar();
    }

    function updateProgressBar() {
      const percent = Math.round((currentQuestion / questions.length) * 100);
      document.getElementById("progressBar").value = percent;
      document.getElementById("progressPercent").textContent = percent + "%";
    }

    function checkAnswer(selected, btn) {
      const q = questions[currentQuestion];
      const buttons = document.querySelectorAll(".option");

      buttons.forEach((b, i) => {
        b.disabled = true;
        if (i === q.answer) b.classList.add("option-correct");
        else if (i === selected) b.classList.add("option-incorrect");
      });

      if (selected === q.answer) score++;

      setTimeout(() => {
        currentQuestion++;
        if (currentQuestion < questions.length) {
          showQuestion();
        } else {
          showResult();
        }
      }, 1000);
    }

 function showResult() {
  const endTime = new Date();
  const timeTaken = Math.floor((endTime - startTime) / 1000);
  const minutes = Math.floor(timeTaken / 60);
  const seconds = timeTaken % 60;
  const porcentaje = Math.round((score / questions.length) * 100);
  let velocidad = "";
  let personaje = "";
  let personajeImg = "";

  if (timeTaken <= 30) velocidad = "Velocidad: ¡Rápido! ⚡";
  else if (timeTaken <= 60) velocidad = "Velocidad: Promedio ⏳";
  else velocidad = "Velocidad: Lento ❌";

  if (porcentaje >= 90) {
    personaje = "Eres Hernán Cortés 🧭";
    personajeImg = "img/hernan.jpg";
  } else if (porcentaje >= 75) {
    personaje = "Eres Malintzin 👩‍🦰";
    personajeImg = "img/malinche.jpg";
  } else if (porcentaje >= 50) {
    personaje = "Eres un Tlaxcalteca aliado 🛡";
    personajeImg = "img/tlaxcalteca.jpg";
  } else if (porcentaje >= 25) {
    personaje = "Eres un explorador perdido 🗺";
    personajeImg = "img/explorador.jpg";
  } else {
    personaje = "Eres un náufrago desorientado 🌊";
    personajeImg = "img/naufrago.jpg";
  }

  document.getElementById("quiz").style.display = "none";
  const resultDiv = document.getElementById("result");
  resultDiv.innerHTML = `
    <h2>¡Has terminado el quiz!</h2>
    <p>Puntaje final: <strong>${score} de ${questions.length}</strong></p>
    <p>Porcentaje: <strong>${porcentaje}%</strong></p>
    <p>Tiempo: <strong>${minutes} min ${seconds} seg</strong></p>
    <p>${velocidad}</p>
    <h3>${personaje}</h3>
    <img src="${personajeImg}" alt="Personaje" style="max-width:200px; margin-top: 10px; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.2);" />
    <br><br>
    <button onclick="startQuiz()">Reintentar Quiz</button>
  `;
  resultDiv.style.display = "block";
}

    window.onload = () => {
      document.getElementById("start-screen").style.display = "block";
    };
  </script>
</body>
</html>
