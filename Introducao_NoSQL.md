
# 📌 Introdução ao NoSQL

## ✅ O que é NoSQL?
**NoSQL** significa **"Not Only SQL"**. É uma abordagem para bancos de dados que não utilizam exclusivamente o modelo relacional (tabelas, linhas e colunas).  
Foi criada para lidar com:
- **Grandes volumes de dados** (Big Data)
- **Alta velocidade de leitura e escrita**
- **Escalabilidade horizontal** (várias máquinas)

---

## ✅ Escalabilidade
- **Horizontal (Sharding):** Particionamento dos dados entre diferentes nós (servidores), permitindo melhor distribuição e escalabilidade.
- **Vertical:** Aumentar poder de processamento em um único servidor (mais CPU, RAM).

---

## ✅ Modelo BASE (em vez de ACID)
Em sistemas distribuídos, o NoSQL normalmente segue o **modelo BASE**, que significa:
- **Basically Available:** Sistema sempre disponível.
- **Soft-State:** O estado pode mudar mesmo sem entrada (por replicação).
- **Eventually Consistent:** Consistência eventual, não imediata (trade-off para alta disponibilidade).

---

## ✅ Características e Vantagens do NoSQL
✔ Flexibilidade (sem esquema fixo)  
✔ Escalabilidade (fácil para crescer horizontalmente)  
✔ Alta performance em leitura/escrita massiva  

---

## ✅ Tipos de Bancos NoSQL
Existem 4 categorias principais:

### 1. **Document Store**  
- Armazena dados como **documentos** (JSON, BSON, XML).
- Ex.: **MongoDB**, CouchDB.  
- **Exemplo de documento JSON:**
```json
{
  "nome": "Brayan",
  "idade": 18,
  "linguagens": ["Python", "SQL"]
}
```

---

### 2. **Key-Value Store**
- Cada dado é armazenado como um par **chave → valor**.
- Ideal para cache e dados simples.
- Ex.: **Redis**, **Amazon DynamoDB**.
- **Exemplo:**
```
"usuario:1001" -> "Brayan"
```
✔ Bom desempenho em aplicações na nuvem  
✖ Menor capacidade de busca complexa  

---

### 3. **Wide-Column Store** (Armazenamento por colunas)
- Armazena dados em **famílias de colunas**.
- Estrutura:
  - **Keyspace:** Conjunto de tabelas (similar ao database).
  - **Column Family/Table:** Agrupamento de colunas (similar a uma tabela).
  - **Row Key:** Identifica uma linha (similar à Primary Key).
  - **Column:** Par Nome-Valor com Timestamp.
- Ex.: **Apache Cassandra**, HBase.

---

### 4. **Graph Store**
- Estrutura baseada em **nós (entidades)** e **arestas (relacionamentos)**.
- Ideal para **redes sociais**, **mecanismos de recomendação**, **detecção de fraude**.
- Ex.: **Neo4j**, OrientDB.

---

## ✅ Exemplos de uso do NoSQL
- **Redes sociais:** Relacionamentos complexos (Graph DB).
- **E-commerce:** Catálogos dinâmicos (Document DB).
- **Big Data e Analytics:** Consultas massivas (Wide-Column DB).
- **Cache e Sessões:** Dados temporários (Key-Value DB).

---

## ✅ Comparação SQL x NoSQL
| Característica          | **SQL**                 | **NoSQL**                   |
|--------------------------|-------------------------|--------------------------------|
| Estrutura               | Tabelas, Linhas        | Flexível (JSON, Chave-Valor) |
| Linguagem               | SQL                    | Depende do DB (Mongo → BSON) |
| Consistência            | ACID                   | BASE                          |
| Escalabilidade          | Vertical               | Horizontal                    |

---

## ✅ Conclusão
NoSQL **não substitui SQL**, mas complementa em cenários que exigem:
- Grandes volumes de dados
- Alta disponibilidade
- Estrutura flexível
- Performance em larga escala

---

### 🔗 **Principais Bancos NoSQL**
- MongoDB (Documentos)
- Redis (Chave-Valor)
- Cassandra (Colunas)
- Neo4j (Grafos)
