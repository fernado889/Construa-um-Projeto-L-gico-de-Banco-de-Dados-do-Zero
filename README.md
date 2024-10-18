# Construa-um-Projeto-L-gico-de-Banco-de-Dados-do-Zero
Entidades Principais
Livros

ID_Livro (PK)
Título
Autor
ISBN
Ano_Publicacao
Categoria (FK)
Autores

ID_Autor (PK)
Nome
Data_Nascimento
Categorias

ID_Categoria (PK)
Nome_Categoria
Usuários

ID_Usuario (PK)
Nome
Email
Data_Cadastro
Empréstimos

ID_Emprestimo (PK)
ID_Livro (FK)
ID_Usuario (FK)
Data_Empréstimo
Data_Devolucao
Relacionamentos
Um livro pode ter um ou mais autores (muitos-para-muitos).
Um livro pertence a uma categoria (um-para-muitos).
Um usuário pode fazer vários empréstimos (um-para-muitos).
Um empréstimo refere-se a um único livro e a um único usuário (muitos-para-um).
[Livros] 1 --- N [Autores]
[Livros] N --- 1 [Categorias]
[Usuários] 1 --- N [Empréstimos]
[Livros] 1 --- N [Empréstimos]
CREATE TABLE Autores (
    ID_Autor INT PRIMARY KEY AUTO_INCREMENT,
    Nome VARCHAR(100) NOT NULL,
    Data_Nascimento DATE
);

CREATE TABLE Categorias (
    ID_Categoria INT PRIMARY KEY AUTO_INCREMENT,
    Nome_Categoria VARCHAR(50) NOT NULL
);

CREATE TABLE Livros (
    ID_Livro INT PRIMARY KEY AUTO_INCREMENT,
    Titulo VARCHAR(150) NOT NULL,
    ISBN VARCHAR(20),
    Ano_Publicacao INT,
    ID_Categoria INT,
    FOREIGN KEY (ID_Categoria) REFERENCES Categorias(ID_Categoria)
);

CREATE TABLE Usuarios (
    ID_Usuario INT PRIMARY KEY AUTO_INCREMENT,
    Nome VARCHAR(100) NOT NULL,
    Email VARCHAR(100) NOT NULL,
    Data_Cadastro DATE
);

CREATE TABLE Emprestimos (
    ID_Emprestimo INT PRIMARY KEY AUTO_INCREMENT,
    ID_Livro INT,
    ID_Usuario INT,
    Data_Empréstimo DATE,
    Data_Devolucao DATE,
    FOREIGN KEY (ID_Livro) REFERENCES Livros(ID_Livro),
    FOREIGN KEY (ID_Usuario) REFERENCES Usuarios(ID_Usuario)
);
