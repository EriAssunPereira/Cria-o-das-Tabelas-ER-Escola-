# Cria-o-das-Tabelas-ER-Escola-

Aqui estão os comandos SQL para criar as tabelas com base no modelo ER fornecido:

```sql
CREATE TABLE aluno (
    Matricula_aluno INT(3),
    Nome_aluno CHAR(40),
    Endereço VARCHAR(100),
    Telefone INT(12),
    Cidade CHAR(30),
    PRIMARY KEY (Matricula_aluno)
);

CREATE TABLE professor (
    Matricula_professor INT(5),
    Nome_professor VARCHAR(40),
    Titulação VARCHAR(40),
    Telefone VARCHAR(15),
    Cidade VARCHAR(40),
    PRIMARY KEY (Matricula_professor)
);

CREATE TABLE disciplina (
    cod_disciplina INT(3),
    Nome_disciplina CHAR(20),
    PRIMARY KEY (cod_disciplina)
);

CREATE TABLE turma (
    ano INT(4),
    semestre INT(1),
    cod_disciplina INT(3),
    Matricula_professor INT(5),
    PRIMARY KEY (ano, semestre, cod_disciplina),
    FOREIGN KEY (cod_disciplina) REFERENCES disciplina(cod_disciplina),
    FOREIGN KEY (Matricula_professor) REFERENCES professor(Matricula_professor)
);

CREATE TABLE turma_aluno (
    ano INT(4),
    semestre INT(1),
    cod_disciplina INT(3),
    Matricula_aluno INT(3),
    PRIMARY KEY (ano, semestre, cod_disciplina, Matricula_aluno),
    FOREIGN KEY (ano, semestre, cod_disciplina) REFERENCES turma(ano, semestre, cod_disciplina),
    FOREIGN KEY (Matricula_aluno) REFERENCES aluno(Matricula_aluno)
);

CREATE TABLE nota (
    ano INT(4),
    semestre INT(1),
    cod_disciplina INT(3),
    Cod_avaliacao INT(3),
    Matricula_aluno INT(3),
    Nota INT(2),
    PRIMARY KEY (ano, semestre, cod_disciplina, Cod_avaliacao, Matricula_aluno),
    FOREIGN KEY (ano, semestre, cod_disciplina, Matricula_aluno) REFERENCES turma_aluno(ano, semestre, cod_disciplina, Matricula_aluno)
);
```

Esses comandos criam as tabelas e definem as chaves primárias e estrangeiras conforme o modelo ER.
