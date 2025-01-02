<!DOCTYPE html>
<html lang="pt-br">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Catálogo de Produtos</title>
  <link rel="stylesheet" href="styles.css">
  <style>
    /* Adicionando algumas estilizações básicas */
    .product {
      border: 1px solid #ddd;
      margin: 10px;
      padding: 10px;
      display: inline-block;
      width: 30%;
      text-align: center;
      border-radius: 8px;
    }

    .product img {
      width: 100%;
      max-width: 200px;
      height: auto;
      border-radius: 5px;
    }

    .product h3 {
      font-size: 1.2em;
      margin-top: 10px;
    }

    .product p {
      font-size: 1em;
    }

    .filter {
      margin-bottom: 20px;
    }

    .filter select {
      padding: 10px;
      font-size: 1em;
      border-radius: 5px;
    }

    .product-list {
      display: flex;
      flex-wrap: wrap;
    }
  </style>
</head>
<body>
  <header>
    <h1>Catálogo de Produtos</h1>
  </header>

  <!-- Filtro de categorias -->
  <div class="filter">
    <label for="category">Filtrar por categoria:</label>
    <select id="category">
      <!-- As opções serão carregadas dinamicamente -->
    </select>
  </div>

  <!-- Lista de produtos -->
  <div class="product-list" id="product-list">
    <!-- Os produtos serão carregados dinamicamente -->
  </div>

  <script>
    // Função para carregar dados do Google Sheets
    const sheetURL = 'https://docs.google.com/spreadsheets/d/e/2PACX-1vQulmY7T7U6PseDk2kouwSzi7E_Fp_i8rxwuLawd4I77MPQvLP3PRGtWWE5_Oz0_MoPyQ2GqQYppGL-/pub?output=csv';

    // Função para carregar os dados da planilha
    function loadData() {
      fetch(sheetURL)
        .then(response => response.text())
        .then(data => {
          const rows = data.split('\n');
          const categories = new Set();
          const products = [];

          rows.forEach(row => {
            const cols = row.split(',');
            const productName = cols[0].trim();
            const productImage = cols[1].trim();
            const productCategory = cols[2].trim();
            const productDescription = cols[3].trim();

            // Adicionar categoria ao conjunto
            categories.add(productCategory);

            // Adicionar produto à lista
            products.push({ productName, productImage, productCategory, productDescription });
          });

          // Preencher o filtro de categorias
          const categorySelect = document.getElementById('category');
          categories.forEach(category => {
            const option = document.createElement('option');
            option.value = category;
            option.textContent = category;
            categorySelect.appendChild(option);
          });

          // Exibir os produtos
          const productList = document.getElementById('product-list');
          products.forEach(product => {
            const productElement = document.createElement('div');
            productElement.classList.add('product');
            productElement.innerHTML = `
              <img src="images/${product.productImage}" alt="${product.productName}">
              <h3>${product.productName}</h3>
              <p>${product.productDescription}</p>
            `;
            productList.appendChild(productElement);
          });

          // Adicionar evento de filtro de categoria
          categorySelect.addEventListener('change', () => {
            const selectedCategory = categorySelect.value;
            productList.innerHTML = ''; // Limpar lista atual
            const filteredProducts = products.filter(product => selectedCategory === '' || product.productCategory === selectedCategory);
            filteredProducts.forEach(product => {
              const productElement = document.createElement('div');
              productElement.classList.add('product');
              productElement.innerHTML = `
                <img src="images/${product.productImage}" alt="${product.productName}">
                <h3>${product.productName}</h3>
                <p>${product.productDescription}</p>
              `;
              productList.appendChild(productElement);
            });
          });
        })
        .catch(error => console.error('Erro ao carregar os dados:', error));
    }

    // Carregar os dados quando a página for carregada
    window.onload = loadData;
  </script>
</body>
</html>
