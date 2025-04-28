# ATV2_Modulo2

create table alunos(
  id_aluno serial primary key,
  nome text not null,
  turma text not null,
  curso text not null
);

insert into alunos(nome, turma, curso) values 
('Sarah Araújo Duarte', 'T15', 'Ciência da Computação'),
('Paulo Vitor Barros de Almeida', 'T15', 'Sistemas de Informação'),
('Maria Arielly Lima de Oliveira', 'T15', 'Engenharia de Software'),
('Nicolli Venino Santana', 'T15', 'Engenharia da Computação'),
('Alessandra Nascimento Santos Sena', 'T15', 'Engenharia de Software'),
('Luana de Jesus Lima', 'T15', 'Sistemas de Informação'),
('Lucas Aquilino Pomin', 'T15', 'Engenharia da Computação'),
('Vivian de Assis Peres', 'T15', 'ADM Tech'),
('Hugo de Freitas Montan', 'T15', 'ADM Tech'),
('Breno Farias Gomes Da Silva', 'T15', 'Ciência da Computação');

select * from alunos;

create table cursos(
  id_cursos serial primary key,
  curso text not null,
  duracao_curso int
);

insert into cursos (curso, duracao_curso) values
('Ciência da Computação', '4'),
('Engenharia de Software', '4'),
('Engenharia da Computação', '4'),
('ADM Tech', '4');

add table cursos (curso, duracao_curso) values ('Sistemas de Informação', 4)

select * from cursos;

create table matricula (
  id_matricula serial primary key,
  aluno_id int references alunos(id_aluno) on delete cascade,
  cursos_id int references cursos(id_cursos) on delete cascade,
  data_matricula DATE DEFAULT CURRENT_DATE
);

insert into matricula values (1, 1), (2, 2 );


select a.nome as alunos, c.curso as cursos, m.data_matricula
from matricula m
JOIN alunos a ON m.aluno_id = a.id_aluno
JOIN cursos c ON m.cursos_id = c.id_cursos;

