<!DOCTYPE html>
<html lang="pt-br">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Drogaria Santa Maria Pinheirinho</title>
  <style>
    /* Resetando alguns estilos padrões do navegador */
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    /* Estilos gerais */
    body {
      font-family: Arial, sans-serif;
      line-height: 1.6;
      background-color: #f4f4f4;
      color: #333;
    }

    header {
      background-color: #4CAF50;
      color: #fff;
      padding: 20px 0;
      text-align: center;
    }

    header h1 {
      font-size: 2.5rem;
    }

    main {
      padding: 20px;
      max-width: 1200px;
      margin: 0 auto;
    }

    h2 {
      text-align: center;
      margin-bottom: 20px;
    }

    #produtos {
      display: flex;
      flex-wrap: wrap;
      justify-content: space-between;
    }

    .produto {
      background-color: #fff;
      padding: 15px;
      margin: 10px;
      border-radius: 8px;
      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
      width: 45%;
      text-align: center;
    }

    .produto h3 {
      margin-bottom: 10px;
    }

    .produto a {
      color: #4CAF50;
      text-decoration: none;
    }

    .produto a:hover {
      text-decoration: underline;
    }

    table {
      width: 100%;
      border-collapse: collapse;
      margin-top: 20px;
    }

    table, th, td {
      border: 1px solid #ddd;
    }

    th, td {
      padding: 12px;
      text-align: center;
    }

    iframe {
      width: 100%;
      height: 600px;
      border: none;
    }

    footer {
      background-color: #333;
      color: #fff;
      padding: 10px 0;
      text-align: center;
      margin-top: 20px;
    }
  </style>
</head>
<body>
  <header>
    <h1>Drogaria Santa Maria Pinheirinho</h1>
    <p>Bem-vindo à nossa drogaria! Confira nossos produtos e entre em contato via WhatsApp.</p>
  </header>

  <main>
    <section id="produtos">
      <h2>Nosso Catálogo de Produtos</h2>
      <!-- Exemplos de produtos -->
      <div class="produto">
        <h3>Produto 1</h3>
        <p>Descrição do produto 1. <a href="https://wa.me/35988490590" target="_blank">Fale conosco no WhatsApp</a></p>
      </div>
      <div class="produto">
        <h3>Produto 2</h3>
        <p>Descrição do produto 2. <a href="https://wa.me/35988490590" target="_blank">Fale conosco no WhatsApp</a></p>
      </div>
    </section>

    <section id="tabela-produtos">
      <h2>Produtos Disponíveis (do Google Sheets)</h2>
      <!-- Exibindo CSV de maneira simples -->
      <table id="produtos-tabela">
        <thead>
          <tr>
            <th>Produto</th>
            <th>Descrição</th>
            <th>Preço</th>
          </tr>
        </thead>
        <tbody>
          <!-- Conteúdo será inserido aqui com JavaScript -->
        </tbody>
      </table>
    </section>
  </main>

  <footer>
    <p>&copy; 2025 Drogaria Santa Maria Pinheirinho. Todos os direitos reservados.</p>
  </footer>

  <script>
    // Função para carregar e exibir o conteúdo do CSV
    fetch('https://docs.google.com/spreadsheets/d/e/2PACX-1vQulmY7T7U6PseDk2kouwSzi7E_Fp_i8rxwuLawd4I77MPQvLP3PRGtWWE5_Oz0_MoPyQ2GqQYppGL-/pub?output=csv')
      .then(response => response.text())
      .then(data => {
        const rows = data.split('\n');
        const table = document.querySelector('#produtos-tabela tbody');

        rows.forEach((row, index) => {
          if (index > 0) { // Ignorar a primeira linha (cabeçalho)
            const columns = row.split(',');
            const tr = document.createElement('tr');

            columns.forEach(col => {
              const td = document.createElement('td');
              td.textContent = col;
              tr.appendChild(td);
            });

            table.appendChild(tr);
          }
        });
      })
      .catch(error => console.error('Erro ao carregar o CSV:', error));
  </script>
</body>
</html>
