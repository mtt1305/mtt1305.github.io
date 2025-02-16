<!DOCTYPE html>
<html lang="pt">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Somente perguntinhas bobas meu bem 💖</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      text-align: center;
      background-color: #ffe6e6;
      padding: 50px;
    }
    #pergunta {
      font-size: 20px;
      margin-bottom: 20px;
    }
    .botao {
      display: block;
      margin: 10px auto;
      padding: 10px 15px;
      font-size: 18px;
      border: none;
      background-color: #ff4d4d;
      color: white;
      cursor: pointer;
      border-radius: 5px;
    }
    .botao:hover {
      background-color: #cc0000;
    }
    #resultado {
      font-size: 22px;
      font-weight: bold;
      margin-top: 20px;
    }
  </style>
</head>
<body>

  <h1>Somente perguntinhas bobas meu bem 💖</h1>
  <p id="pergunta"></p>
  <div id="botoes">
    <!-- Botões serão gerados aqui -->
  </div>
  <p id="resultado"></p>

  <script>
    // Array de perguntas e respostas
    const questions = [
      {
        pergunta: "Qual fruta eu gosto mais?",
        opcoes: [
          { texto: "Moranguinhos", correct: true },
          { texto: "Abacaxizinho", correct: false }
        ],
        messageCorrect: "Parabéns, amorr <3",
        messageWrong: "Ouch, tenta de novo!"
      },
      {
        pergunta: "Qual é a cor do nosso amor?",
        opcoes: [
          { texto: "Vermelho", correct: true },
          { texto: "Azul", correct: false }
        ],
        messageCorrect: "Exato! Nosso amor é paixão!",
        messageWrong: "Hmm, não é essa, tenta de novo!"
      }
      // Adicione mais perguntas conforme desejar...
    ];

    let currentQuestionIndex = 0;

    // Função para mostrar a pergunta atual
    function showQuestion() {
      const questionElement = document.getElementById("pergunta");
      const buttonsDiv = document.getElementById("botoes");
      const resultadoElement = document.getElementById("resultado");

      // Limpa a mensagem de resultado
      resultadoElement.innerText = "";

      // Atualiza o texto da pergunta
      questionElement.innerText = questions[currentQuestionIndex].pergunta;

      // Limpa botões antigos
      buttonsDiv.innerHTML = "";

      // Cria os botões de opção
      questions[currentQuestionIndex].opcoes.forEach(opcao => {
        const button = document.createElement("button");
        button.className = "botao";
        button.innerText = opcao.texto;
        button.onclick = function() {
          verificarResposta(opcao.correct);
        };
        buttonsDiv.appendChild(button);
      });
    }

    // Função para verificar a resposta
    function verificarResposta(acertou) {
      const resultadoElement = document.getElementById("resultado");
      if (acertou) {
        resultadoElement.innerText = questions[currentQuestionIndex].messageCorrect;
        // Após um delay, passa para a próxima pergunta
        setTimeout(() => {
          currentQuestionIndex++;
          if (currentQuestionIndex < questions.length) {
            showQuestion();
          } else {
            // Fim do quiz
            document.getElementById("pergunta").innerText = "";
            document.getElementById("botoes").innerHTML = "";
            resultadoElement.innerText = "Você completou o quiz! Parabéns!";
          }
        }, 1500); // 1.5 segundos de delay
      } else {
        resultadoElement.innerText = questions[currentQuestionIndex].messageWrong;
      }
    }

    // Inicia o quiz mostrando a primeira pergunta
    showQuestion();
  </script>

</body>
</html>
