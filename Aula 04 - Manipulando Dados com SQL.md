# ✍️ **Aula 4: Manipulando Dados com SQL (DML)**

## 🎯 Objetivos da Aula

* Entender como inserir, atualizar e deletar dados no banco.
* Aplicar os comandos básicos de **DML**: `INSERT`, `UPDATE`, `DELETE`.
* Evitar erros comuns em operações de escrita.
* Praticar com exemplos reais no sistema escolar criado na aula anterior.

---

## 🧩 O que é DML?

DML significa **Data Manipulation Language**, ou seja, **linguagem de manipulação de dados**. Com ela, conseguimos **alterar os dados de uma tabela** (sem mudar a estrutura).

Os principais comandos são:

|  Comando | Função Principal          |
| -------: | ------------------------- |
| `INSERT` | Adiciona novos dados      |
| `UPDATE` | Atualiza dados existentes |
| `DELETE` | Remove dados              |

---

## ✨ `INSERT INTO` – Adicionando Dados

A sintaxe básica:

```sql
INSERT INTO nome_tabela (coluna1, coluna2, ...)
VALUES (valor1, valor2, ...);
```

### 📚 Exemplo: Inserindo um curso

```sql
INSERT INTO curso (nome)
VALUES ('Técnico em Desenvolvimento de Sistemas');
```

### 👩‍🏫 Exemplo: Inserindo um professor

```sql
INSERT INTO professor (nome, email)
VALUES ('Daniel Souza', 'dhdsouza@senacrs.com.br');
```

### 🤓 Dica:

Você pode inserir múltiplos valores de uma vez:

```sql
INSERT INTO curso (nome)
VALUES 
('Administração'),
('Logística'),
('Redes de Computadores');
```

---

## 🔁 `UPDATE` – Atualizando Dados

A sintaxe básica:

```sql
UPDATE nome_tabela
SET coluna1 = novo_valor1, coluna2 = novo_valor2
WHERE condição;
```

> [!IMPORTANT]
> Sempre use `WHERE`, senão todos os registros da tabela serão alterados!

<div align="center">
    <img src="https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExN2JuNXF1c2s4OG0ydGF2bGNtdnd5MXdpcm54azBlNzF5dHc2bjM2YSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/xT4uQ7N8UNsoeFAjVS/giphy.gif" alt="Você está demitido">
    <p>
        Fonte: <em><a href="https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExN2JuNXF1c2s4OG0ydGF2bGNtdnd5MXdpcm54azBlNzF5dHc2bjM2YSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/xT4uQ7N8UNsoeFAjVS/giphy.gif" target="_blank">https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExN2JuNXF1c2s4OG0ydGF2bGNtdnd5MXdpcm54azBlNzF5dHc2bjM2YSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/xT4uQ7N8UNsoeFAjVS/giphy.gif</a></em>
    </p>
</div>  

### ✏️ Exemplo: Corrigindo nome de um professor

```sql
UPDATE professor
SET nome = 'Daniel H. de Souza'
WHERE id_professor = 1;
```

### ⚠️ Sem `WHERE`:

```sql
-- Isso vai mudar todos os nomes dos professores para "Zé":
UPDATE professor
SET nome = 'Zé';
```

> 😱 Cuidado com esse erro! Sempre revise a cláusula `WHERE`.

---

## ❌ `DELETE` – Removendo Dados

A sintaxe básica:

```sql
DELETE FROM nome_tabela
WHERE condição;
```

### 🧹 Exemplo: Deletando um aluno

```sql
DELETE FROM aluno
WHERE id_aluno = 3;
```

### 💀 Exemplo Perigoso:

```sql
DELETE FROM aluno;
```

> 😨 Isso remove **todos os alunos** da tabela! Cuidado redobrado com comandos sem `WHERE`.

---

## 🧪 Exemplos Práticos Completos

### 1️⃣ Inserindo um aluno

```sql
INSERT INTO aluno (nome, email)
VALUES ('Maria Oliveira', 'maria@senac.com');
```

### 2️⃣ Matriculando o aluno na turma 1

```sql
INSERT INTO matricula (id_aluno, id_turma, data_matricula)
VALUES (1, 1, '2025-07-23');
```

### 3️⃣ Atualizando o nome do curso

```sql
UPDATE curso
SET nome = 'Técnico em Sistemas'
WHERE id_curso = 1;
```

### 4️⃣ Removendo uma matrícula

```sql
DELETE FROM matricula
WHERE id_matricula = 1;
```

---

## 🧯 Cuidados e Boas Práticas

✅ Sempre use `WHERE` para evitar desastres.   
✅ Teste com `SELECT` antes de atualizar ou deletar:   

```sql
SELECT * FROM aluno WHERE id_aluno = 3;
```

✅ Faça **backup** antes de comandos destrutivos.    
✅ Prefira atualizações atômicas (uma coisa por vez).    

---

## 🏁 Atividade Proposta

1. **Insira** pelo menos 3 alunos, 2 professores, 2 cursos e 2 turmas.
2. **Atualize** o nome de um curso e o email de um professor.
3. **Delete** um aluno e uma matrícula.
4. Faça um `SELECT * FROM <nome_da_tabela>` para verificar os dados após cada operação.
