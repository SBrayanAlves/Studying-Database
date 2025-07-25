
# 📚 Conteúdo Completo - Banco de Dados

---

## 📌 Introdução ao Banco de Dados

### O que é um banco de dados?

> Uma **coleção organizada de informações** ou **dados estruturados**.

### Esquema de comunicação:

```
API → Banco de Dados ← Web ← Cliente
                  ↑
               Nuvem
```

---

## 🗂 Tipos de Banco de Dados

### ✅ Banco de Dados Relacional

- Armazena dados **estruturados**, organizados em **tabelas** (linhas e colunas).
- Relações entre tabelas.
- Exemplos: `MySQL`, `PostgreSQL`, `SQL Server`, `Oracle`.

#### Exemplo de tabelas relacionais:

**Tabela: Clientes**
```
Id | Nome    | Sobrenome | Email           | AceitaComunicados | DataCadastro
---|---------|-----------|------------------|--------------------|--------------
1  | Leonardo| Buta      | email@gmail.com | 1                  | 29/04/2025
2  | Peter   | Anderson  | email@gmail.com | 0                  | 29/04/2025
3  | Taylor  | Adams     | email@gmail.com | 1                  | 29/04/2025
```

**Tabela: Endereços**
```
Id | Rua   | Bairro   | Cidade   | Estado   | IdCliente
---|-------|----------|----------|----------|----------
1  | Rua 1 | Bairro 1 | Cidade 1 | Estado 1 | 1
```

---

### 📦 Banco de Dados Não Relacional (NoSQL)

- Dados **não estruturados** ou **semi-estruturados**.
- Exemplo: `MongoDB`

#### Exemplo de JSON (semi-estruturado):

```json
[
  {
    "Id": 1,
    "Nome_Produto": "Material de escritório",
    "Preco": 25.00,
    "DataVenda": "2025-04-23T01:23:26",
    "Desconto": null
  },
  {
    "Id": 2,
    "Nome_Produto": "Licença de Software",
    "Preco": 110.00,
    "DataVenda": "2025-04-23T01:23:26",
    "Desconto": 10,
    "Cupom": "1234"
  }
]
```

---

## 🧠 DBMS - Sistema de Gerenciamento de Banco de Dados

**DBMS (Database Management System)**: software para acessar, manipular e gerenciar um banco de dados.

Exemplos: `MySQL`, `PostgreSQL`, `Oracle`, `SQL Server`, `SQLite`

---

## 📘 Introdução ao SQL

### Linguagens no SQL

- **DQL** - Consulta: `SELECT`
- **DML** - Manipulação: `INSERT`, `UPDATE`, `DELETE`
- **DDL** - Definição: `CREATE`, `ALTER`, `DROP`
- **DCL** - Controle: `GRANT`, `REVOKE`
- **DTL** - Transação: `BEGIN`, `COMMIT`, `ROLLBACK`

> Materiais:
> - [Oracle Relational Database](https://www.oracle.com/br/database/what-is-a-relational-database/)
> - [SQL Tutorial](https://www.sqltutorial.org/)

---

## 🧱 Modelagem de Dados: MER e DER

- **MER**: Modelo Entidade-Relacionamento
- **DER**: Diagrama Entidade-Relacionamento

Ferramentas:
- https://app.creately.com/
- https://app.quickdatabasediagrams.com/

### Conceitos:

- **Entidade**: substantivo concreto ou abstrato
- **Atributo**: características da entidade
- **Relacionamento**: associações entre entidades
- **Cardinalidade**:
  - 1:1 (um para um)
  - 1:N (um para muitos)
  - N:N (muitos para muitos)

---

## 📋 Tabelas, Colunas e Registros

### Comando: `CREATE TABLE`

```sql
CREATE TABLE usuarios (
  id INT,
  nome VARCHAR(100) NOT NULL COMMENT 'Nome do usuário',
  email VARCHAR(100) NOT NULL COMMENT 'Email do usuário',
  endereco VARCHAR(100) NOT NULL COMMENT 'Endereço do usuário',
  data_nascimento DATE NOT NULL COMMENT 'Data de nascimento do usuário'
);
```

...

(Truncado aqui por limite. Continuarei na próxima célula.)

---

## 🔁 Operações CRUD

### `INSERT`

```sql
INSERT INTO usuarios (id, nome, email, data_nascimento, endereco)
VALUES (1, 'Brayan', 'email@gmail.com', '1999-10-25', 'Av das Rosas, 100');
```

### `SELECT`

```sql
SELECT * FROM usuarios;
SELECT nome, email FROM usuarios WHERE id = 1;
```

### `UPDATE`

```sql
UPDATE usuarios
SET id = 4
WHERE email = 'email@gmail.com';
```

### `DELETE`

```sql
DELETE FROM usuarios
WHERE nome = 'Sebastiao';
```

---

## 🛠 Alterando e Excluindo Tabelas

### `DROP TABLE`

```sql
DROP TABLE usuarios;
```

### `ALTER TABLE`

Permite:
- Adicionar/alterar/excluir colunas
- Modificar restrições e índices
- Renomear tabela

---

## 🔑 Chaves

### Chave Primária

```sql
CREATE TABLE exemplo (
  id INT PRIMARY KEY AUTOINCREMENT
);
```

### Chave Estrangeira

```sql
CREATE TABLE pedidos (
  id INT PRIMARY KEY,
  cliente_id INT,
  FOREIGN KEY (cliente_id) REFERENCES clientes(id)
);
```

**Restrições:**
- `ON DELETE`: ação ao excluir pai
- `ON UPDATE`: ação ao atualizar pai
- Ações: `CASCADE`, `SET NULL`, `SET DEFAULT`, `RESTRICT`

---

## 🧹 Normalização

### 1FN – Atomicidade

Cada campo deve conter **valores indivisíveis**.

### 2FN – Dependência Total

Todos os atributos não-chave devem depender totalmente da chave primária.

### 3FN – Eliminação de Dependências Transitivas

Nenhum atributo não-chave deve depender de outro não-chave.

Referência: [Normalização - Wikipédia](https://pt.wikipedia.org/wiki/Normaliza%C3%A7%C3%A3o_de_dados)

---

## 🔗 JOINs e Subconsultas

### JOINs

#### `INNER JOIN`

```sql
SELECT * FROM usuarios us
INNER JOIN reservas rs ON us.id = rs.id_usuario;
```

#### `LEFT JOIN`

```sql
SELECT * FROM tabela1
LEFT JOIN tabela2 ON tabela1.coluna = tabela2.coluna;
```

#### `RIGHT JOIN`

```sql
SELECT * FROM reservas rs
RIGHT JOIN destinos ds ON rs.id_destino = ds.id;
```

#### `FULL JOIN`

```sql
SELECT * FROM tabela1
FULL JOIN tabela2 ON tabela1.coluna = tabela2.coluna;
```

### Subconsultas

```sql
SELECT * FROM destinos
WHERE id NOT IN (SELECT id_destino FROM reservas);
```

---

## 📊 Funções Agregadas e Agrupamento

### Funções Agregadas

- `COUNT()`
- `SUM()`
- `AVG()`
- `MIN()`
- `MAX()`

### Agrupamento

```sql
SELECT cidade, COUNT(*) FROM usuarios
GROUP BY cidade;
```

---

## 📈 Índices e Plano de Execução

### `EXPLAIN`

```sql
EXPLAIN
SELECT * FROM usuarios WHERE nome = "Sebastiao Brayan";
```

### Criar Índice

```sql
CREATE INDEX idx_nome ON usuarios (nome);
```

Referência: [MariaDB - ADD INDEX](https://mariadb.com/kb/en/alter-table/#add-index)

---
