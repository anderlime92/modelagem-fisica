```sql
CREATE DATABASE microblog CHARACTER SET utf8mb4;
```

```sql
CREATE TABLE usuarios (
    id INT PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(100) NOT NULL,
    tipo ENUM('admin', 'editor')
    email VARCHAR(100) UNIQUE
    senha VARCHAR(255)
)
```

```sql
CREATE TABLE noticias (
    id INT PRIMARY KEY AUTO_INCREMENT,
    data DATETIME NOT NULL DEFAULT CURRENT_TIMESTAMP
    titulo VARCHAR(100)
    texto TEXT NULL
    imagem VARCHAR(100)
    resumo VARCHAR(260)
    destaque ENUM('sim', 'nao')
    usuario_id INT NOT NULL
    categorias_id INT NOT NULL
    FOREIGN KEY (usuario_id) REFERENCES usuario(id)
    FOREIGN KEY (categoria_id) REFERENCES categoria(id)
)
```

```sql
CREATE TABLE categorias (
    id INT PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(100) NOT NULL,
    conteudo TEXT NULL
    tipo ENUM('atualidades', 'etc')
)
```