# lifeissnake

<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Formulário Barbearia</title>
    <style>
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            background: #f2f2f2;
            margin: 0;
            font-family: Arial, sans-serif;
        }
        .form-container {
            background: white;
            padding: 20px;
            max-width: 600px;
            width: 90%;
            border-radius: 8px;
            box-shadow: 0 4px 8px rgba(0,0,0,0.1);
        }
        .form-container h2 {
            text-align: center;
            color: #333;
        }
        label {
            display: block;
            margin-top: 10px;
            font-weight: bold;
        }
        input, select {
            width: 100%;
            padding: 8px;
            margin-top: 5px;
            border: 1px solid #ccc;
            border-radius: 4px;
        }
        .radio-group {
            display: flex;
            gap: 20px;
            margin-top: 5px;
        }
        button {
            background: #28a745;
            color: white;
            border: none;
            padding: 10px 20px;
            margin-top: 20px;
            cursor: pointer;
            border-radius: 4px;
            width: 100%;
            font-size: 16px;
        }
        button:hover {
            background: #218838;
        }
        .resultado {
            margin-top: 20px;
            padding: 15px;
            background: #e9ffe9;
            border: 1px solid #28a745;
            border-radius: 4px;
        }
    </style>
</head>
<body>
    <div class="form-container">
        <h2>Agendamento de Atendimento</h2>
        <form id="formAtendimento">
            <label for="nome">Nome completo</label>
            <input type="text" id="nome" required>

            <label for="cpf">CPF</label>
            <input type="text" id="cpf" placeholder="000.000.000-00" required>

            <label for="servico">Tipo de corte desejado</label>
            <select id="servico" required>
                <option value="corte">Corte de cabelo</option>
                <option value="corte_barba">Corte + barba</option>
                <option value="barba">Barba</option>
            </select>

            <label for="data">Data do atendimento</label>
            <input type="date" id="data" required>

            <label>Atendimento quinzenal?</label>
            <div class="radio-group">
                <label><input type="radio" name="quinzenal" value="sim" required> Sim</label>
                <label><input type="radio" name="quinzenal" value="nao"> Não</label>
            </div>

            <button type="submit">Confirmar Atendimento</button>
        </form>

        <div id="resumo" class="resultado" style="display: none;"></div>
    </div>

    <script>
        document.getElementById('formAtendimento').addEventListener('submit', function(event) {
            event.preventDefault();

            const nome = document.getElementById('nome').value;
            const cpf = document.getElementById('cpf').value;
            const servico = document.getElementById('servico').value;
            const data = document.getElementById('data').value;
            const quinzenal = document.querySelector('input[name="quinzenal"]:checked').value;

            let preco = 0;

            if (servico === 'corte') preco = 40;
            else if (servico === 'corte_barba') preco = 60;
            else if (servico === 'barba') preco = 30;

            if (quinzenal === 'sim') {
                preco *= 0.9; // aplica 10% de desconto
            }

            const servicoTexto = servico === 'corte' ? 'Corte de cabelo'
                                : servico === 'corte_barba' ? 'Corte + barba'
                                : 'Barba';

            document.getElementById('resumo').style.display = 'block';
            document.getElementById('resumo').innerHTML = `
                <strong>Atendimento confirmado!</strong><br>
                Nome: ${nome}<br>
                CPF: ${cpf}<br>
                Serviço: ${servicoTexto}<br>
                Data: ${new Date(data).toLocaleDateString()}<br>
                Atendimento quinzenal: ${quinzenal === 'sim' ? 'Sim' : 'Não'}<br>
                Valor ${quinzenal === 'sim' ? 'com desconto' : 'total'}: R$ ${preco.toFixed(2)}
            `;
        });
    </script>
</body>
</html>

<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="style.css">
    <title>ex2.10_c</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Noto+Sans+JP:wght@100..900&family=Special+Gothic+Condensed+One&display=swap" rel="stylesheet">
</head>

<body>

    <div class="container">
        <div class="title">
            <h1>Supermercado JS</h1>
        </div>
        <div class="inputs">
            <div class="product">
                <p>Produto: </p>
                <input type="text" id="inProduct">
            </div>
            <div class="preco">
                <p>Preço: </p>
                <input type="text" id="inPreco">
            </div>
            <button id="btn-promotion" class="btn">Ver Promoção</button>

            <h3 id="first-out"></h3>
            <h3 id="second-out"></h3>
        </div>

    </div>
    <script src="script.js"></script>
</body>

</html>

const button = document.getElementById('btn-promotion');

button.addEventListener('click', () => {
  const produto = document.getElementById('inProduct').value;
  const saida = document.getElementById('first-out');
  
  saida.innerHTML = `Nome do produto: ${produto}` ;
  saida.innerHTML = `Nome do produto: ${produto}` ;
  saida.innerHTML = `Nome do produto: ${produto}` ;
})
