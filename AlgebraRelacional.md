## **Algebra Relacional**

<br>

####

| Empregado  |             |           |               |
| ---------- | ----------- | --------- | ------------- |
| Matricula: | Nome:       | Endereço: | Sexo:         |
| Salário:   | Supervisor: |           | Departamento: |

<br>

> σ: Representa uma operação de seleção que retorna uma tabela com a mesma quantidade de colunas e uma menor quantidade de linhas, ou uma quantidade de linhas iguais as da tabela original

> π: Representa uma operação de seleção por atributo, reduzindo a quantidade de colunas selecionadas, porém mantendo a mesma quantidade de linhas

<br>

#### 1. Encontre os nomes de todos os empregados que trabalham para a Companhia Soft Sell

<br>

<br>

### Empregado

|                     |                   |           |        |          | |  |  |
| --- | --- | --- | --- | --- | --- | ---| --- |
| Matricula do Empregado | Nome do Empregado | Endereço | Salário  | Supervisor | Codigo do Departamento |
| 01                  | Fernando          | Rua São Paulo, Nº 85, Bairro Boa Passagem, RN |  2.500,00 | Armando Silva| 01|
| 02                  | Arthur            |  Rua São Pedro, Nº 023, Bairro Boa Passagem, RN|   3.400,00 | Afonso Nogueira | 02
| 03                  | Pamela  Silva          |  Rua Santo Antonio, Nº 023, Bairro Paraiba, RN|   1.400,00 | Afonso Nogueira | 03
| 04                  | Luísa Lima    |  Rua Qualquer, Nº 023, Bairro Guadalupe, SP|   1.000,00 | Pamela Silva | 03 |

<br>
<br>
<br>
R1 <= σ nome_companhia = "soft sell" (Companhia)
R1 |x| cnpj = cnpj_trab (Trabalha)

<br>

#### 2. Encontre os nomes de todos os nomes das cidades dos empregados trabalham na Soft Sell

<br>

> R1 <= σ nome_companhia = "soft sell" (Companhia)

> R2 <= R1 |x| cnpj = cidade_empregado (Trabalha)

> R3 <= R2 |x| codigo_empregado (Empregado)

> R4 <= π cidade_empregado (R3)

<br>

> R1 <= σ nome_companhia = "soft sell" (Companhia)

> R2 <= R1 |x| cnpj = cidade_empregado (Trabalha)

> R3 <= R2 |x| codigo_empregado (Empregado)

> R4 <= π cidade_empregado (R3)
