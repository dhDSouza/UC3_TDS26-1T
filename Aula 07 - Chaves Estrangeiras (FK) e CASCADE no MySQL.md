# 📚 Aula 7: Chave Estrangeira (FK) e CASCADE no MySQL

## 🧠 O que é uma Chave Estrangeira (Foreign Key)?

Uma **chave estrangeira** (FK - *foreign key*) é uma **restrição de integridade referencial** entre duas tabelas.
Ela garante que o valor de uma coluna em uma tabela (tabela filha) **corresponda a um valor existente** em outra tabela (tabela pai).

🔗 Exemplo clássico:

* Um **pedido** precisa estar relacionado a um **usuário**.
* Um **pedido** também pode estar relacionado a um **produto**.

---

## 🏗️ Estrutura de Tabelas

Criando as tabelas:

* `usuarios`
* `produtos`
* `pedidos`

A tabela `pedidos` terá duas FKs: uma para `usuarios.id` e outra para `produtos.id`.

---

## ✅ Criando tabelas com FK e CASCADE direto no `CREATE TABLE`

```sql
CREATE TABLE usuarios (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(100),
    email VARCHAR(100)
);

CREATE TABLE produtos (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(100),
    preco DECIMAL(10, 2)
);

CREATE TABLE pedidos (
    id INT AUTO_INCREMENT PRIMARY KEY,
    id_usuario INT,
    id_produto INT,
    quantidade INT,
    data_pedido DATETIME DEFAULT CURRENT_TIMESTAMP,

    -- Definindo FKs com CASCADE
    FOREIGN KEY (id_usuario) REFERENCES usuarios(id)
        ON DELETE CASCADE
        ON UPDATE CASCADE,

    FOREIGN KEY (id_produto) REFERENCES produtos(id)
        ON DELETE SET NULL
        ON UPDATE CASCADE
);
```

### 🛡️ O que essas FKs fazem?

* `ON DELETE CASCADE` → Se deletar um usuário, todos os pedidos dele serão **automaticamente deletados**.
* `ON DELETE SET NULL` → Se deletar um produto, o campo `id_produto` nos pedidos ficará **NULL** (mantendo o histórico do pedido).
* `ON UPDATE CASCADE` → Se atualizar o `id` do usuário ou produto, o campo correspondente nos pedidos também será atualizado automaticamente.

---

## 🛠️ Adicionando FK com CASCADE após a criação

Se a tabela `pedidos` foi criada **sem FKs**, podemos adicionar depois:

```sql
ALTER TABLE pedidos
ADD CONSTRAINT fk_pedidos_usuarios
FOREIGN KEY (id_usuario) REFERENCES usuarios(id)
ON DELETE CASCADE
ON UPDATE CASCADE;

ALTER TABLE pedidos
ADD CONSTRAINT fk_pedidos_produtos
FOREIGN KEY (id_produto) REFERENCES produtos(id)
ON DELETE SET NULL
ON UPDATE CASCADE;
```

---

## ⚠️ Regras importantes

* Os **tipos de dados** da FK e da PK precisam ser **iguais ou compatíveis**.
* O valor da FK **deve existir** na tabela pai (exceto se for `NULL`).
* A tabela pai precisa ter uma **PRIMARY KEY ou UNIQUE** na coluna referenciada.
* O CASCADE é útil para manter a **integridade dos dados automaticamente**, mas deve ser usado com cuidado para evitar exclusões em massa sem querer.

---

## 🧪 Verificando e Removendo FKs

Ver FKs:

```sql
SHOW CREATE TABLE pedidos;
```

Remover FK:

```sql
ALTER TABLE pedidos
DROP FOREIGN KEY fk_pedidos_usuarios;
```

---

## 📝 Lista de Exercícios

1. Crie a tabela `categorias` com os campos `id` e `nome`.
2. Altere a tabela `produtos` para adicionar o campo `id_categoria` (INT).
3. Crie uma FK na tabela `produtos` referenciando `categorias(id)` com:
   * `ON DELETE SET NULL`
   * `ON UPDATE CASCADE`
4. Insira registros de teste nas tabelas `usuarios`, `categorias`, `produtos` e `pedidos`.
5. Tente inserir um pedido com `id_usuario` inexistente. O que acontece?
6. Delete um `usuario` que possua pedidos e verifique o comportamento do `CASCADE`.
7. Delete uma `categoria` que possua produtos e verifique se o campo `id_categoria` foi setado para `NULL`.
8. Remova a FK `id_produto` da tabela `pedidos`.
