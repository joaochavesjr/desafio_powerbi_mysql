# Desafio Power BI com MySQL na Azure
Este projeto foi originado pela integração da base de dados do MySQL com Power BI. O objetivo consiste em realizar uma pequena caracterização dos dados. Os valores são originados de uma base de teste.

## Passos de normalização:
- Removidas colunas (constraints e valores nulos);
- Campo salario da tabela employee alterado para número decimal fixo;

## Mesclar consultas employee e department:
```
select concat(e.Fname, "  ", e.Minit, " ", e.Lname) as Nome, d.dname as Departamento from employee as e
inner join departament as d where e.dno = d.dnumber;
```

## Juncao dos colaboradores e respectivos nomes dos gerentes:
```
select concat (e.Fname, "  ", e.Minit, " ", e.Lname) as Gerente,
concat(g.Fname, "  ", g.Minit, " ", g.Lname) as Nome from employee e
inner join employee g where g.Super_ssn = e.ssn;
```

## Mescle os nomes de departamentos e localização:
```
select concat(l.dlocation, "-", d.dname) as DepLocation from departament d
inner join dept_locations l where d.dnumber = l.dnumber;
```
