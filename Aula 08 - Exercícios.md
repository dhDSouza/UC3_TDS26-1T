# 📝 Exercícios da Aula 8

## Utilizem este banco de dados para a resolução dos exercícios 🎲

```sql
-- =========================================
-- TABELA USUÁRIOS
-- =========================================

CREATE TABLE usuarios (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE,
    cidade VARCHAR(100),
    idade INT
);

-- =========================================
-- TABELA CATEGORIAS
-- =========================================

CREATE TABLE categorias (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(100) NOT NULL
);

-- =========================================
-- TABELA PRODUTOS
-- =========================================

CREATE TABLE produtos (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(100) NOT NULL,
    preco DECIMAL(10,2) NOT NULL,
    
    id_categoria INT NULL,

    CONSTRAINT fk_produtos_categoria
        FOREIGN KEY (id_categoria)
        REFERENCES categorias(id)
        ON DELETE SET NULL
        ON UPDATE CASCADE
);

-- =========================================
-- TABELA PEDIDOS
-- =========================================

CREATE TABLE pedidos (
    id INT AUTO_INCREMENT PRIMARY KEY,

    id_usuario INT NULL,
    id_produto INT NULL,

    quantidade INT NOT NULL,
    data_pedido DATETIME DEFAULT CURRENT_TIMESTAMP,

    CONSTRAINT fk_pedidos_usuario
        FOREIGN KEY (id_usuario)
        REFERENCES usuarios(id)
        ON DELETE SET NULL
        ON UPDATE CASCADE,

    CONSTRAINT fk_pedidos_produto
        FOREIGN KEY (id_produto)
        REFERENCES produtos(id)
        ON DELETE SET NULL
        ON UPDATE CASCADE
);

-- =========================================
-- INSERTS USUÁRIOS
-- =========================================

INSERT INTO usuarios (nome, email, cidade, idade) VALUES
('João Silva', 'joao@gmail.com', 'Porto Alegre', 25),
('Maria Oliveira', 'maria@gmail.com', 'Canoas', 32),
('Carlos Souza', 'carlos@gmail.com', 'São Paulo', 41),
('Ana Lima', 'ana@gmail.com', 'Curitiba', 29),
('Fernanda Costa', 'fernanda@gmail.com', 'Porto Alegre', 37),
('Lucas Pereira', 'lucas@gmail.com', 'Canoas', 19),
('Juliana Martins', 'juliana@gmail.com', 'São Paulo', 34),
('Rafael Alves', 'rafael@gmail.com', 'Novo Hamburgo', 22),
('Patrícia Gomes', 'patricia@gmail.com', 'Curitiba', 45),
('Bruno Rocha', 'bruno@gmail.com', 'Porto Alegre', 31);

-- =========================================
-- INSERTS CATEGORIAS
-- =========================================

INSERT INTO categorias (nome) VALUES
('Games'),
('Informática'),
('Eletrônicos'),
('Periféricos'),
('Livros');

-- =========================================
-- INSERTS PRODUTOS
-- =========================================

INSERT INTO produtos (nome, preco, id_categoria) VALUES
('Notebook Gamer Dell', 5500.00, 2),
('Mouse Gamer RGB', 250.00, 4),
('Teclado Mecânico', 450.00, 4),
('PlayStation 5', 4200.00, 1),
('Xbox Series X', 3900.00, 1),
('Monitor 24 Polegadas', 899.90, 3),
('Notebook Lenovo', 3200.00, 2),
('Cadeira Gamer', 1200.00, 1),
('Headset Gamer', 350.00, 4),
('Smartphone Samsung', 2100.00, 3),
('Notebook Ultra', 6100.00, 2),
('Game Retro Console', 180.00, 1),
('Webcam HD', 150.00, 3),
('SSD 1TB', 650.00, 2),
('Mouse Pad Gamer', 80.00, 4),
('Controle Xbox', 299.90, 1),
('Livro SQL Completo', 99.90, 5),
('Notebook Acer Nitro', 4800.00, 2),
('TV 50 Polegadas', 2800.00, 3),
('GameCube Usado', 700.00, 1),
('Notebook Positivo', 1900.00, 2),
('Game Station Pro', 230.00, 1),
('Caixa de Som Bluetooth', 320.00, 3),
('Monitor Gamer 27', 1800.00, 3),
('Notebook Samsung Book', 3500.00, 2);

-- =========================================
-- INSERTS PEDIDOS
-- =========================================

INSERT INTO pedidos (id_usuario, id_produto, quantidade) VALUES
(1, 1, 1),
(2, 4, 2),
(3, 2, 1),
(4, 10, 1),
(5, 8, 1),
(6, 12, 3),
(7, 18, 1),
(8, 15, 2),
(9, 6, 1),
(10, 20, 1),
(1, 3, 1),
(2, 5, 1),
(3, 7, 2),
(4, 9, 1),
(5, 11, 1),
(6, 13, 2),
(7, 14, 1),
(8, 16, 1),
(9, 17, 3),
(10, 24, 1);
```

## Exercícios 🏋️

1. Liste os nomes e preços dos produtos que custam mais de 200, ordenados do maior para o menor. 
2. Mostre apenas as cidades únicas dos clientes cadastrados. 
3. Liste os nomes dos produtos que contêm "game" no nome. 
4. Mostre os 3 produtos mais baratos. 
5. Liste os nomes dos clientes que moram em "Porto Alegre" ou "Canoas". 
6. Liste o nome e a cidade dos clientes que moram em Canoas. 
7. Mostre todos os clientes com idade entre 30 e 40 anos. 
8. Liste o nome e preço dos produtos que contenham "Note" no nome. 
9. Mostre todos os clientes que moram em São Paulo, Porto Alegre ou Curitiba. 
10. Liste todos os produtos da categoria Games, ordenados do mais caro para o mais barato. 
11. Mostre apenas os 5 primeiros produtos mais caros da tabela. 
12. Liste os 3 clientes mais jovens (nome, idade e cidade). 
13. Mostre os produtos com preço menor que 100 reais. 
14. Liste nome e categoria dos produtos que custam mais de 1000 reais e sejam da categoria Informática ou Eletrônicos. 
15. Mostre apenas as cidades distintas onde há clientes cadastrados. 
16. Liste todos os clientes que não moram em São Paulo. 
17. Mostre todos os produtos cujo preço não esteja entre 200 e 800 reais.
