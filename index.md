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
    }

    header h1 {
      text-align: center;
      font-size: 2.5rem;
    }

    header p {
      text-align: center;
      font-size: 1.2rem;
    }

    main {
      padding: 20px;
    }

    #produtos {
      display: flex;
      flex-wrap: wrap;
      justify-content: space-around;
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

    footer {
      background-color: #333;
      color: #fff;
      padding: 10px 0;
      text-align: center;
    }

    /* Estilos para a tabela do Google Sheets */
    table {
      width: 100%;
      border-collapse: collapse;
      margin-top: 20px;
    }

    table, th, td {
      border: 1px solid #ddd;
    }

    th, td {
      padding: 8px;
      text-align: left;
    }

    th {
      background-color: #4CAF50;
      color: white;
    }
  </style>
</head>
<body>
  <header>
    <div class="container">
      <h1>Drogaria Santa Maria Pinheirinho</h1>
      <p>Bem-vindo à nossa drogaria! Confira nossos produtos e entre em contato via WhatsApp.</p>
    </div>
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
      <!-- Link do Google Sheets embutido -->
      <p>Abaixo estão alguns dados que foram extraídos do Google Sheets:</p>
      <iframe src="https://docs.google.com/spreadsheets/d/e/2PACX-1vSzFS_yXXXjsR9gP1r_Bs5X4C9tQqKgZofUb_oN2f9qV4iLZv4GG7CddMIq_/pubhtml?gid=0&single=true" width="100%" height="600px"></iframe>
    </section>
  </main>

  <footer>
    <div class="container">
      <p>&copy; 2025 Drogaria Santa Maria Pinheirinho. Todos os direitos reservados.</p>
    </div>
  </footer>
</body>
</html>
