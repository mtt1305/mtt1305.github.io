<!DOCTYPE html>
<html lang="pt">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Somente perguntinhas bobinhaaaas :}</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      text-align: center;
      background-color: #ffe6e6;
      padding: 50px;
    }
    #inicio {
      display: block;
    }
    #quiz {
      display: none;
    }
    #pergunta {
      font-size: 24px;
      margin-bottom: 20px;
    }
    .botoes {
      display: flex;
      justify-content: center;
      gap: 20px;
      margin-top: 20px;
    }
    .botao {
      padding: 15px 25px;
      font-size: 20px;
      border: none;
      background-color: #ff4d4d;
      color: white;
      cursor: pointer;
      border-radius: 10px;
      width: 150px;
    }
    .botao:hover {
      background-color: #cc0000;
    }
    #resultado {
      font-size: 22px;
      font-weight: bold;
      margin-top: 20px;
    }
    #botao-inicio {
      padding: 15px 30px;
      font-size: 22px;
      border: none;
      background-color: #ff4d4d;
      color: white;
      cursor: pointer;
      border-radius: 10px;
    }
    #botao-inicio:hover {
      background-color: #cc0000;
    }
  </style>
</head>
<body>

  <!-- Tela Inicial -->
  <div id="inicio">
    <h1>Um quiz feito sobre nosso amor 💖</h1>
    <p>Vamos ver o quanto você me conhece, meu bem!</p>
    <button id="botao-inicio" onclick="iniciarQuiz()">Começar</button>
  </div>

  <!-- Quiz -->
  <div id="quiz">
    <h1>Somente perguntinhas bobinhaaaas :}</h1>
    <p id="pergunta"></p>
    <div class="botoes" id="botoes"></div>
    <p id="resultado"></p>
  </div>

  <script>
    const questions = [
      { pergunta: "Qual fruta eu gosto mais?", opcoes: [{ texto: "Moranguinhos", correct: true }, { texto: "Abacaxizinho", correct: false }] },
      { pergunta: "Qual é minha cor favorita?", opcoes: [{ texto: "Vermelho", correct: false }, { texto: "Azul", correct: true }] },
      { pergunta: "O que eu mais gosto de fazer no tempo livre?", opcoes: [{ texto: "Jogar", correct: true }, { texto: "Ler", correct: false }] },
      { pergunta: "Qual minha sobremesa favorita?", opcoes: [{ texto: "Torta de limão", correct: true }, { texto: "Chocolate", correct: false }] }
    ];

    let currentQuestionIndex = 0;

    function iniciarQuiz() {
      document.getElementById("inicio").style.display = "none";
      document.getElementById("quiz").style.display = "block";
      showQuestion();
    }

    function showQuestion() {
      const questionElement = document.getElementById("pergunta");
      const buttonsDiv = document.getElementById("botoes");
      const resultadoElement = document.getElementById("resultado");
      
      resultadoElement.innerText = "";
      questionElement.innerText = questions[currentQuestionIndex].pergunta;
      buttonsDiv.innerHTML = "";

      questions[currentQuestionIndex].opcoes.forEach(opcao => {
        const button = document.createElement("button");
        button.className = "botao";
        button.innerText = opcao.texto;
        button.onclick = function() { verificarResposta(opcao.correct); };
        buttonsDiv.appendChild(button);
      });
    }

    function verificarResposta(acertou) {
      const resultadoElement = document.getElementById("resultado");
      if (acertou) {
        resultadoElement.innerText = "Parabéns, amorr <3";
        setTimeout(() => {
          currentQuestionIndex++;
          if (currentQuestionIndex < questions.length) {
            showQuestion();
          } else {
            document.getElementById("pergunta").innerText = "PARABÉNS AMOOOOR!! EU AMO VOCÊ!";
            document.getElementById("botoes").innerHTML = "";
            resultadoElement.innerText = "";
          }
        }, 1500);
      } else {
        resultadoElement.innerText = "Ouch, tenta de novo!";
      }
    }
  </script>

</body>
</html>
