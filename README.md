# projeto-3T
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Organizador de Objetivos Futuros</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 0;
      background-color: #f4f4f9;
      color: #333;
    }

    .container {
      max-width: 800px;
      margin: 20px auto;
      padding: 20px;
      background: #ffffff;
      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
      border-radius: 8px;
    }

    h1, h2 {
      text-align: center;
    }

    form {
      display: flex;
      flex-direction: column;
      gap: 10px;
      margin-bottom: 20px;
    }

    input, button {
      padding: 10px;
      font-size: 16px;
    }

    button {
      background-color: #007BFF;
      color: white;
      border: none;
      cursor: pointer;
      border-radius: 4px;
    }

    button:hover {
      background-color: #0056b3;
    }

    #goalsList ul {
      list-style: none;
      padding: 0;
    }

    #goalsList li {
      background: #e9ecef;
      margin: 5px 0;
      padding: 10px;
      border-radius: 4px;
      display: flex;
      justify-content: space-between;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>Organizador de Objetivos Futuros</h1>
    <form id="goalForm">
      <input type="text" id="goalName" placeholder="Nome do objetivo" required>
      <input type="number" id="goalTarget" placeholder="Valor meta (ex: 100)" required>
      <input type="number" id="goalProgress" placeholder="Progresso atual" required>
      <input type="date" id="goalDeadline" placeholder="Data limite" required>
      <button type="submit">Adicionar Objetivo</button>
    </form>

    <div id="goalsList">
      <h2>Lista de Objetivos</h2>
      <ul id="list"></ul>
    </div>
  </div>

  <script>
    document.getElementById('goalForm').addEventListener('submit', function(e) {
      e.preventDefault();

      // Captura os valores do formulário
      const name = document.getElementById('goalName').value;
      const target = parseFloat(document.getElementById('goalTarget').value);
      const progress = parseFloat(document.getElementById('goalProgress').value);
      const deadline = document.getElementById('goalDeadline').value;

      // Calcula o progresso percentual
      const percentage = ((progress / target) * 100).toFixed(2);

      // Cria um novo item de lista
      const list = document.getElementById('list');
      const listItem = document.createElement('li');
      listItem.innerHTML = `
        <span><strong>${name}</strong> - Meta: ${target}, Progresso: ${progress} (${percentage}%), Prazo: ${deadline}</span>
        <button onclick="this.parentElement.remove()">Remover</button>
      `;

      list.appendChild(listItem);

      // Limpa os campos do formulário
    document.getElementById('goalForm').reset();
    });
  </script>
</body>
</html>
