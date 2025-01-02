<!DOCTYPE html>
<html lang="pt-br">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Catálogo de Produtos</title>
  <link rel="stylesheet" href="styles.css">
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 0;
      background-color: #f4f4f4;
    }
    header {
      background-color: #4CAF50;
      color: white;
      text-align: center;
      padding: 20px;
    }
    .filter {
      margin: 20px;
      text-align: center;
    }
    .filter select {
      padding: 10px;
      font-size: 1em;
      border-radius: 5px;
    }
    .product-list {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
    }
    .product {
      border: 1px solid #ddd;
      margin: 15px;
      padding: 15px;
      background-color: white;
      width: 200px;
      border-radius: 8px;
      text-align: center;
      box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
    }
    .product img {
      width: 100%;
      height: 150px;
      object-fit: cover;
      border-radius: 5px;
    }
    .product h3 {
      margin: 10px 0;
      font-size: 1.2em;
    }
    .product p {
      font-size: 1em;
      color: #555;
    }
  </style>
</head>
<body>

<header>
  <h1>Catálogo de Produtos</h1>
</header>

<div class="filter">
  <label for="category">Filtrar por categoria:</label>
  <select id="category">
    <option value="">Todas as categorias</option>
    <!-- As opções de categorias serão carregadas dinamicamente -->
  </select>
</div>

<div class="product-list" id="product-list">
  <!-- Os produtos serão carregados dinamicamente aqui -->
</div>

<script>
  const sheetURL = 'https://docs.google.com/spreadsheets/d/e/2PACX-1vQulmY7T7U6PseDk2kouwSzi7E_Fp_i8rxwuLawd4I77MPQvLP3PRGtWWE5_Oz0_MoPyQ2GqQYppGL-/pub?output=csv';

  function loadData() {
    fetch(sheetURL)
      .then(response => response.text())
      .then(data => {
        const rows = data.split('\n');
        const categories = new Set();
        const products = [];

        rows.forEach(row => {
          const cols = row.split(',');
          const productName = cols[0]?.trim();
          const productImage = cols[1]?.trim();
          const productCategory = cols[2]?.trim();
          const productDescription = cols[3]?.trim();

          if (productName && productImage && productCategory && productDescription) {
            categories.add(productCategory);

            products.push({
              productName,
              productImage,
              productCategory,
              productDescription,
            });
          }
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
        function displayProducts(filteredProducts) {
          productList.innerHTML = '';
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
        }

        displayProducts(products);

        // Adicionar evento de filtro de categoria
        categorySelect.addEventListener('change', () => {
          const selectedCategory = categorySelect.value;
          const filteredProducts = selectedCategory
            ? products.filter(product => product.productCategory === selectedCategory)
            : products;
          displayProducts(filteredProducts);
        });
      })
      .catch(error => console.error('Erro ao carregar os dados:', error));
  }

  window.onload = loadData;
</script>

</body>
</html>
