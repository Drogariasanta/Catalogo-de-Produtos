<html lang="pt-br">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Drogaria Santa Maria Pinheirinho</title>
  <style>
    /* Resetando estilos padrão */
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    /* Estilo geral */
    body {
      font-family: Arial, sans-serif;
      background-color: #f4f4f4;
      color: #333;
      line-height: 1.6;
    }

    /* Cabeçalho */
    header {
      background-color: #4CAF50;
      color: #fff;
      text-align: center;
      padding: 20px;
    }

    header h1 {
      font-size: 2.5rem;
    }

    header p {
      font-size: 1rem;
    }

    /* Seção dos produtos */
    main {
      max-width: 1200px;
      margin: 20px auto;
      padding: 20px;
    }

    h2 {
      text-align: center;
      margin-bottom: 20px;
      font-size: 2rem;
    }

    /* Filtro de categorias */
    #filtro {
      text-align: center;
      margin-bottom: 20px;
    }

    #filtro select {
      padding: 10px;
      font-size: 1rem;
      border-radius: 5px;
      border: 1px solid #ccc;
    }

    #produtos {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
      gap: 20px;
    }

    .produto {
      background-color: #fff;
      border-radius: 8px;
      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
      padding: 20px;
      text-align: center;
      transition: transform 0.3s;
      position: relative;
    }

    .produto:hover {
      transform: scale(1.05);
    }

    .produto img {
      max-width: 100%;
      height: auto;
      border-radius: 8px;
    }

    .produto h3 {
      margin: 15px 0;
      font-size: 1.5rem;
    }

    .produto p {
      font-size: 1.1rem;
      margin-bottom: 15px;
    }

    .produto a {
      display: inline-block;
      padding: 10px 20px;
      background-color: #4CAF50;
      color: #fff;
      text-decoration: none;
      border-radius: 5px;
      font-weight: bold;
      transition: background-color 0.3s;
    }

    .produto a:hover {
      background-color: #45a049;
    }

    /* Rodapé */
    footer {
      background-color: #333;
      color: #fff;
      text-align: center;
      padding: 10px 0;
      margin-top: 30px;
    }

  </style>
</head>
<body>
  <header>
    <h1>Drogaria Santa Maria Pinheirinho</h1>
    <p>Seu bem-estar é nossa prioridade. Confira nossos produtos e entre em contato!</p>
  </header>

  <main>
    <h2>Catálogo de Produtos</h2>

    <!-- Filtro de categorias -->
    <div id="filtro">
      <select id="categoriaFiltro">
        <option value="">Selecione uma Categoria</option>
        <!-- As opções de categorias serão carregadas via JavaScript -->
      </select>
    </div>

    <section id="produtos">
      <!-- Os produtos serão carregados aqui via JavaScript -->
    </section>
  </main>

  <footer>
    <p>&copy; 2025 Drogaria Santa Maria Pinheirinho. Todos os direitos reservados.</p>
  </footer>

  <script>
    // Função para carregar os dados do CSV e exibir os produtos
    fetch('https://docs.google.com/spreadsheets/d/e/2PACX-1vQulmY7T7U6PseDk2kouwSzi7E_Fp_i8rxwuLawd4I77MPQvLP3PRGtWWE5_Oz0_MoPyQ2GqQYppGL-/pub?output=csv')
      .then(response => response.text())
      .then(data => {
        const rows = data.split('\n');
        const section = document.querySelector('#produtos');
        const categoriaFiltro = document.querySelector('#categoriaFiltro');
        const categorias = new Set();

        rows.forEach((row, index) => {
          if (index > 0) { // Ignorar a primeira linha (cabeçalho)
            const columns = row.split(',');

            // Adicionar as categorias no filtro (sem duplicatas)
            categorias.add(columns[4]);

            // Criar o HTML para cada produto
            const produtoHTML = `
              <div class="produto" data-categoria="${columns[4]}">
                <img src="images/${columns[3]}" alt="${columns[0]}">
                <h3>${columns[0]}</h3>
                <p>${columns[1]}</p>
                <p>Preço: ${columns[2]}</p>
                <a href="https://wa.me/35988490590" target="_blank">Fale conosco no WhatsApp</a>
              </div>
            `;

            // Adicionar o produto à seção
            section.innerHTML += produtoHTML;
          }
        });

        // Adicionar as categorias ao filtro
        categorias.forEach(categoria => {
          categoriaFiltro.innerHTML += `<option value="${categoria}">${categoria}</option>`;
        });

        // Filtro por categoria
        categoriaFiltro.addEventListener('change', function() {
          const categoriaSelecionada = this.value;
          const produtos = document.querySelectorAll('.produto');

          produtos.forEach(produto => {
            if (categoriaSelecionada === '' || produto.dataset.categoria === categoriaSelecionada) {
              produto.style.display = 'block';
            } else {
              produto.style.display = 'none';
            }
          });
        });
      })
      .catch(error => console.error('Erro ao carregar o CSV:', error));
  </script>
</body>
</html>
