# 🛠️ Atividade Complementar – Do DER ao SQL

## 🎯 Objetivo

Transformar diagramas de Entidade-Relacionamento (DER) em código SQL, criando bancos de dados completos no MySQL a partir de modelos conceituais.

---

# 📚 Diagramas

## 🎮 Loja de Games

```mermaid
erDiagram

CLIENTE {
    INT id_cliente PK
    VARCHAR nome
    VARCHAR email
    VARCHAR telefone
}

PEDIDO {
    INT id_pedido PK
    DATE data_pedido
    DECIMAL valor_total
    INT id_cliente FK
}

JOGO {
    INT id_jogo PK
    VARCHAR titulo
    VARCHAR genero
    DECIMAL preco
}

ITEM_PEDIDO {
    INT id_item PK
    INT quantidade
    DECIMAL subtotal
    INT id_pedido FK
    INT id_jogo FK
}

CLIENTE ||--o{ PEDIDO : realiza
PEDIDO ||--o{ ITEM_PEDIDO : possui
JOGO ||--o{ ITEM_PEDIDO : contem
```

---

## 🏥 Clínica Médica

```mermaid
erDiagram

PACIENTE {
    INT id_paciente PK
    VARCHAR nome
    DATE data_nascimento
    VARCHAR telefone
}

MEDICO {
    INT id_medico PK
    VARCHAR nome
    VARCHAR especialidade
    VARCHAR crm
}

CONSULTA {
    INT id_consulta PK
    DATE data_consulta
    TIME horario
    VARCHAR observacoes
    INT id_paciente FK
    INT id_medico FK
}

RECEITA {
    INT id_receita PK
    VARCHAR medicamento
    VARCHAR dosagem
    INT id_consulta FK
}

PACIENTE ||--o{ CONSULTA : agenda
MEDICO ||--o{ CONSULTA : realiza
CONSULTA ||--o{ RECEITA : gera
```

---

## 📖 Sistema de Biblioteca

```mermaid
erDiagram

USUARIO {
    INT id_usuario PK
    VARCHAR nome
    VARCHAR email
    VARCHAR telefone
}

LIVRO {
    INT id_livro PK
    VARCHAR titulo
    VARCHAR autor
    VARCHAR genero
    INT ano_publicacao
}

EMPRESTIMO {
    INT id_emprestimo PK
    DATE data_emprestimo
    DATE data_devolucao
    VARCHAR status
    INT id_usuario FK
    INT id_livro FK
}

FUNCIONARIO {
    INT id_funcionario PK
    VARCHAR nome
    VARCHAR cargo
}

REGISTRO_EMPRESTIMO {
    INT id_registro PK
    INT id_emprestimo FK
    INT id_funcionario FK
    DATETIME data_registro
}

USUARIO ||--o{ EMPRESTIMO : realiza
LIVRO ||--o{ EMPRESTIMO : participa
EMPRESTIMO ||--|| REGISTRO_EMPRESTIMO : gera
FUNCIONARIO ||--o{ REGISTRO_EMPRESTIMO : registra
```

---

# 📝 Instruções

1. Para cada diagrama:

   * Crie um **banco de dados** separado no `MySQL Workbench`.
   * Crie todas as tabelas, colunas, chaves primárias e estrangeiras conforme o modelo.

2. Após criar as tabelas:

   * Insira pelo menos **5 registros em cada tabela** utilizando `INSERT INTO`.
   * Realize:

     * **2 comandos `UPDATE`**
     * **2 comandos `DELETE`**

3. Após finalizar:

   * Salve os códigos SQL em arquivos separados (`der1.sql`, `der2.sql`, `der3.sql`).
   * Compacte todos os arquivos em `.zip`.
   * Envie na [discussão](https://github.com/dhDSouza/UC3_TDS26-1T/discussions/4).

---

# ⚠️ Regras

* Utilize nomes de tabelas e colunas iguais aos do DER.
* Utilize corretamente os tipos de dados (`VARCHAR`, `INT`, `DATE`, `DECIMAL`...).
* Utilize corretamente as `PRIMARY KEY` e `FOREIGN KEY`.
* Utilize `AUTO_INCREMENT` quando necessário.
* Os comandos devem executar sem erros no MySQL.

