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

### Banco de Dados:

|      |      |        |               |           |
| ---- | ---- | ------ | ------------- | --------- |
| CNPJ | Nome | Cidade | Cod_Empregado | CNPJ_Trab |

<br>

### Empregado

|                     |                   |           |        |          |
| ------------------- | ----------------- | --------- | ------ | -------- |
| Código do Empregado | Nome do Empregado | Rua       | Cidade | Salário  |
| 01                  | Fernando          | São Paulo | Caicó  | 2.500,00 |
| 02                  | Arthur            | São Pedro | Caicó  | 3.400,00 |

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
