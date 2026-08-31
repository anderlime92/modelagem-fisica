# Referência de comandos SQL para Modelagem Física


## Criação do banco de dados

```sql
CREATE DATABASE flybynight CHARACTER SET utf8mb4;
```

## Criação da tabela fornecedor

```sql
CREATE TABLE fornecedores(
    id INT PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(100) NOT NULL
);
```