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
    /* Botão secreto */
    #secret-container {
      position: fixed;
      bottom: 20px;
      right: 20px;
      z-index: 999;
    }
    #secret-btn {
      background-color: transparent;
      border: none;
      font-size: 24px;
      cursor: pointer;
      opacity: 0.7;
    }
    #secret-btn:hover {
      opacity: 1;
    }
    #secret-message {
      background-color: rgba(255, 255, 255, 0.9);
      border: 2px solid #ff4d4d;
      padding: 10px 20px;
      border-radius: 10px;
      margin-top: 5px;
      font-size: 16px;
      display: none;
    }
  </style>
</head>
<body>

  <!-- Tela Inicial -->
  <div id="inicio">
    <h1>Um quiz feito sobre nós, amor d=</h1>
    <p>Vamos ver o quanto você... nos conhece?? Meu bem!</p>
    <button id="botao-inicio" onclick="iniciarQuiz()">Começar</button>
  </div>

  <!-- Quiz -->
  <div id="quiz">
    <h1>Somente perguntinhas bobinhaaaas :}</h1>
    <p id="pergunta"></p>
    <div class="botoes" id="botoes"></div>
    <p id="resultado"></p>
  </div>

  <!-- Botão secreto -->
  <div id="secret-container">
    <button id="secret-btn" onclick="toggleSecret()">❤️</button>
    <div id="secret-message">Ansiosa? 87%</div>
  </div>

  <script>
    const questions = [
      { 
        pergunta: "Qual fruta nós 2 adoramos?", 
        opcoes: [
          { texto: "Uvinhas crock crock", correct: true, msg: "desejos" }, 
          { texto: "Abacaxizinho", correct: false }
        ] 
      },
      { 
        pergunta: "Qual é a cor do nosso amor?", 
        opcoes: [
          { texto: "Branco e Preto mesclados", correct: false }, 
          { texto: "Azul e Verde claro mesclados", correct: true, msg: "nossas favoritasss" }
        ] 
      },
      { 
        pergunta: "ablubluble", 
        opcoes: [
          { texto: "concordo em partes", correct: true, msg: "EU TE AMOOOOO" }, 
          { texto: "sla estranho", correct: false }
        ] 
      },
      { 
        pergunta: "Qual a melhor hora para se fazer um pedido?", 
        opcoes: [
          { texto: "4:47", correct: true, msg: "anavitó - ria 📍" }, 
          { texto: "4:43", correct: false }
        ] 
      },
      { 
        pergunta: "Quando nos falamos pela 1° vez?", 
        opcoes: [
          { texto: "17/08/2023", correct: false }, 
          { texto: "29/08/2023", correct: true, msg: "(no wpp) acho que foi o melhor da minha vida" }
        ] 
      },
      { 
        pergunta: "Quantos anos eu tenho?", 
        opcoes: [
          { texto: "14", correct: true, msg: "CTZ Q ERROU PRIMEIRO" }, 
          { texto: "11", correct: false }
        ] 
      },
      { 
        pergunta: "Quer namorar comigo?", 
        opcoes: [
          { texto: "CLAROOO", correct: true, msg: "UHUUUUUUUUUUU" }, 
          { texto: "QUEROOO", correct: true, msg: "UHUUUUUUUUUUU" }
        ] 
      }
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
        button.onclick = function() { verificarResposta(opcao.correct, opcao.msg); };
        buttonsDiv.appendChild(button);
      });
    }

    function verificarResposta(acertou, mensagem) {
      const resultadoElement = document.getElementById("resultado");
      if (acertou) {
        resultadoElement.innerText = mensagem || "Acertoooouu!! <3";
        setTimeout(() => {
          currentQuestionIndex++;
          if (currentQuestionIndex < questions.length) {
            showQuestion();
          } else {
            document.getElementById("pergunta").innerText = "PARABÉNS AMOOOOR!! EU AMO VOCÊ!";
            document.getElementById("botoes").innerHTML = "";
            resultadoElement.innerText = "";
          }
        }, 2000);
      } else {
        resultadoElement.innerText = "Ouch, tenta de novo!";
      }
    }

    function toggleSecret() {
      const secretMessage = document.getElementById("secret-message");
      secretMessage.style.display = secretMessage.style.display === "none" ? "block" : "none";
    }
  </script>

</body>
</html>
