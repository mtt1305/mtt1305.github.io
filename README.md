<!DOCTYPE html>
<html lang="pt">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Quiz do Nosso Amor 💖</title>
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

    <h1>Quiz do Nosso Amor 💖</h1>
    <p id="pergunta">Pergunta 1</p> <!-- Edite aqui -->

    <button class="botao" onclick="verificarResposta(true)">Opção Correta</button> <!-- Edite aqui -->
    <button class="botao" onclick="verificarResposta(false)">Opção Errada</button> <!-- Edite aqui -->

    <p id="resultado"></p>

    <script>
        function verificarResposta(acertou) {
            let resultado = document.getElementById("resultado");
            if (acertou) {
                resultado.innerText = "CORRETA ✅";
            } else {
                resultado.innerText = "INCORRETA ❌";
            }
        }
    </script>

</body>
</html>
