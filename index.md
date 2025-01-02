---
layout: default
---

<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Catálogo de Produtos - Drogaria Santa Maria Pinheirinho</title>
    <style>
        /* Estilos básicos */
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f4f4f9;
        }

        header {
            background-color: #6200ea;
            color: white;
            padding: 20px;
            text-align: center;
        }

        .container {
            width: 90%;
            margin: auto;
            padding: 20px;
        }

        .product {
            display: flex;
            justify-content: space-between;
            align-items: center;
            background-color: #fff;
            margin: 10px 0;
            padding: 15px;
            border-radius: 8px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
        }

        .product img {
            max-width: 150px;
            border-radius: 8px;
        }

        .product-info {
            flex: 1;
            margin-left: 15px;
        }

        .product-info h3 {
            margin: 0 0 5px;
        }

        .product-info p {
            margin: 0;
            color: #555;
        }

        .contact-btn {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 5px;
            background-color: #25d366;
            color: white;
            padding: 10px 15px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            text-decoration: none;
            font-weight: bold;
            font-size: 14px;
        }

        .contact-btn i {
            font-size: 18px;
        }

        .contact-btn:hover {
            background-color: #1da851;
        }
    </style>
</head>
<body>

<header>
    <h1>Bem-vindo à Drogaria Santa Maria Pinheirinho</h1>
</header>

<div class="container">
    <h2>Catálogo de Produtos</h2>

    <!-- Exemplo de produto -->
    <div class="product">
        <img src="https://via.placeholder.com/150" alt="Produto 1">
        <div class="product-info">
            <h3>Produto 1</h3>
            <p>Descrição do Produto 1</p>
        </div>
        <a href="https://wa.me/55988490590?text=Gostaria%20de%20saber%20mais%20sobre%20o%20Produto%201" class="contact-btn">
            <i class="fab fa-whatsapp"></i> Contatar via WhatsApp
        </a>
    </div>

    <!-- Exemplo de outro produto -->
    <div class="product">
        <img src="https://via.placeholder.com/150" alt="Produto 2">
        <div class="product-info">
            <h3>Produto 2</h3>
            <p>Descrição do Produto 2</p>
        </div>
        <a href="https://wa.me/55988490590?text=Gostaria%20de%20saber%20mais%20sobre%20o%20Produto%202" class="contact-btn">
            <i class="fab fa-whatsapp"></i> Contatar via WhatsApp
        </a>
    </div>

</div>

</body>
</html>
