<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Delivery de Comidas</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <!-- Cabeçalho -->
    <header>
        <nav>
            <ul>
                <li><a href="#">Início</a></li>
                <li><a href="#menu">Cardápio</a></li>
                <li><a href="#contato">Contato</a></li>
                <li><a href="#sobre">Sobre</a></li>
            </ul>
        </nav>
    </header>

    <!-- Banner -->
    <section class="banner">
        <h1>Bem-vindo ao Nosso Delivery!</h1>
        <p>Seu pedido entregue em minutos</p>
        <button onclick="window.location.href='#menu'">Peça Agora</button>
    </section>

    <!-- Cardápio -->
    <section id="menu">
        <h2>Cardápio</h2>
        <div class="menu-items">
            <div class="menu-item">
                <img src="https://via.placeholder.com/150" alt="Pizza">
                <h3>Pizza Margherita</h3>
                <p>R$ 30,00</p>
                <button onclick="adicionarAoCarrinho('Pizza Margherita', 30)">Adicionar ao Carrinho</button>
            </div>
            <div class="menu-item">
                <img src="https://via.placeholder.com/150" alt="Hamburguer">
                <h3>Hamburguer</h3>
                <p>R$ 25,00</p>
                <button onclick="adicionarAoCarrinho('Hamburguer', 25)">Adicionar ao Carrinho</button>
            </div>
            <!-- Adicione mais itens conforme necessário -->
        </div>
    </section>

    <!-- Carrinho de Compras -->
    <section id="carrinho">
        <h2>Carrinho</h2>
        <ul id="carrinho-lista"></ul>
        <p id="total">Total: R$ 0,00</p>
        <button onclick="finalizarCompra()">Finalizar Compra</button>
    </section>

    <!-- Contato -->
    <section id="contato">
        <h2>Contato</h2>
        <form id="form-contato">
            <label for="nome">Nome:</label>
            <input type="text" id="nome" name="nome" required>

            <label for="email">Email:</label>
            <input type="email" id="email" name="email" required>

            <label for="mensagem">Mensagem:</label>
            <textarea id="mensagem" name="mensagem" required></textarea>

            <button type="submit">Enviar</button>
        </form>
    </section>

    <!-- Sobre -->
    <section id="sobre">
        <h2>Sobre Nós</h2>
        <p>Oferecemos a melhor comida da cidade com entrega rápida e segura. Acesse nosso cardápio e faça o seu pedido agora mesmo!</p>
    </section>

    <footer>
        <p>&copy; 2024 Delivery de Comidas | Todos os direitos reservados</p>
    </footer>

    <script src="script.js"></script>
</body>
</html>
/* Reset básico */
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: Arial, sans-serif;
    line-height: 1.6;
    background-color: #f4f4f4;
}

header {
    background-color: #333;
    color: white;
    padding: 1rem;
}

header nav ul {
    list-style: none;
    text-align: center;
}

header nav ul li {
    display: inline;
    margin: 0 15px;
}

header nav ul li a {
    color: white;
    text-decoration: none;
    font-size: 1.2rem;
}

.banner {
    background-color: #ff9900;
    color: white;
    text-align: center;
    padding: 50px 0;
}

.banner h1 {
    font-size: 3rem;
}

.banner button {
    padding: 10px 20px;
    background-color: #333;
    color: white;
    border: none;
    font-size: 1.2rem;
    cursor: pointer;
}

section {
    padding: 20px;
}

#menu .menu-items {
    display: flex;
    justify-content: space-around;
    flex-wrap: wrap;
}

.menu-item {
    background-color: white;
    padding: 15px;
    border-radius: 5px;
    margin: 10px;
    text-align: center;
    width: 250px;
}

.menu-item img {
    width: 100%;
    border-radius: 5px;
}

#carrinho {
    background-color: #fff;
    padding: 20px;
    margin-top: 20px;
    text-align: center;
}

form input, form textarea {
    width: 100%;
    padding: 10px;
    margin: 10px 0;
}

footer {
    text-align: center;
    padding: 10px;
    background-color: #333;
    color: white;
    position: fixed;
    width: 100%;
    bottom: 0;
}
let carrinho = [];

function adicionarAoCarrinho(item, preco) {
    carrinho.push({ item, preco });
    atualizarCarrinho();
}

function atualizarCarrinho() {
    const listaCarrinho = document.getElementById('carrinho-lista');
    listaCarrinho.innerHTML = ''; // Limpa a lista de itens
    let total = 0;
    
    carrinho.forEach(item => {
        const li = document.createElement('li');
        li.textContent = `${item.item} - R$ ${item.preco.toFixed(2)}`;
        listaCarrinho.appendChild(li);
        total += item.preco;
    });
    
    document.getElementById('total').textContent = `Total: R$ ${total.toFixed(2)}`;
}

function finalizarCompra() {
    if (carrinho.length > 0) {
        alert('Compra finalizada com sucesso!');
        carrinho = [];
        atualizarCarrinho();
    } else {
        alert('Seu carrinho está vazio!');
    }
}

// Função de envio de formulário de contato (mock)
document.getElementById('form-contato').addEventListener('submit', function(event) {
    event.preventDefault();
    alert('Mensagem enviada com sucesso!');
});
