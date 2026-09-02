# Comandos para modelagem física do Microblog

```sql

-- Criar o banco
CREATE DATABASE microblog CHARACTER SET utf8mb4;

-- Criar tabela usuarios
CREATE TABLE usuarios(
    id INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(100) NOT NULL,
    email VARCHAR(100) NOT NULL UNIQUE,
    senha VARCHAR(255) NOT NULL,
    tipo ENUM('editor', 'admin') NOT NULL
);

-- Criar tabela categorias
CREATE TABLE categorias(
    id INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(100) NOT NULL
);

-- Criar tabela noticias
CREATE TABLE noticias(
    id INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
    titulo VARCHAR(100) NOT NULL,
    resumo TEXT NOT NULL,
    texto TEXT NOT NULL,
    imagem VARCHAR(100) NOT NULL,
    destaque ENUM('sim', 'nao') NOT NULL,

    -- Automaticamente obter a data/hora e registrar
    data DATETIME NOT NULL DEFAULT CURRENT_TIMESTAMP,

    -- Nomenclatura recomendada(singular, não plural)
    -- nometabelasingular_nomecolunapk
    usuario_id INT NOT NULL,
    categoria_id INT NOT NULL,

    -- Cria relacionamentos e chave estrangeira (FK)
    -- Caso o usuário ou categoria seja excluído, as notícias e categorias ficarão setadas como null
    -- (ou seja, sem associação com nenhum usuário e/ou categoria)
    FOREIGN KEY(usuario_id) REFERENCES usuarios(id) ON DELETE SET NULL,
    FOREIGN KEY(categoria_id) REFERENCES categorias(id) ON DELETE SET NULL
);

```