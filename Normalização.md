## Normalização

#### 1. Normalize a tabela abaixo com o objetivo de armazenar os dados cadastrais dos funcionários de uma empresa. Leve em consideração que o funcionário pode ter vários cargos e dependentes.


|  Dados Cadastrais do Funcionário |   |   |   |   |
|---|---|---|---|---|
| Matricula:  | Nome:  |   |   |   |
| Data Nasc.  | Nacionalidade:   | Sexo:   |   |   |
| Est. Civil    | RG:    | CIC:   |   |   |
| Endereço:    | Telefone:    | Data de Admissão:   |   |   |

|  Cargos Ocupados |   |   |   |   |
|---|---|---|---|---|
| Cargo:  | Dt Inicio:   | Dt Fim:   |   |   |
| Cargo:  | Dt Inicio:   | Dt Fim:   |   |   |

|  Dependentes |   |   |   |   |
|---|---|---|---|---|
| Nome:  | Dt Nascimento:   |  |   |   |
| Nome:  | Dt Nascimento:   |  |   |   |


#### **1.0** Selecionamos a chave primaria para a tabela, esta pode ser composta ou simples

<br>

>A chave primária é um campo que indentifica únicamente o elemento que queremos representar através do esquema de tabelas, nesse caso, como estamos querendo representar pessoas (Paciente e Funcionário). Teremos como possivel canditado ao cargo de chave-primária, o atributo: Matricula. Porém, só a matricula é capaz de iddentificar um elemento na tabela? 

<br>

Pensemos o seguinte: Eu posso ter mais de um cargo? Se a resposta for sim, então usar apenas a matricula não vai evitar que haja repetição no banco. Pois a matricula está vinculada a um único individuo. Logo, podemos criar uma chave composta que seria (Matricula, cargo). Agora vamos ao segundo passo:

<br>

#### **1.1** Analisamos a tabela e verificamos se há necessidade da aplicação da primeira regra de normalização que diz que todo atributo na tabela deve ser atômico. Sendo assim, não pode haver campos com valores compostos.

<br>

#### Se o endereço possuir informações que se repetem, sendo ele multivalorado, então devemos separá-lo da tabela, aplicando assim a primeira forma de normalização.


<br>

#### **O resultado após a implementação da primeira regra será:**



|  Dados Cadastrais do Funcionário |   |   |   |   |
|---|---|---|---|---|
| Matricula:  | Nome:  |  
| Data Nasc.  | Nacionalidade:   | Sexo:   | 
| Est. Civil    | RG:    | CIC:   |  

|  Cargos Ocupados |   |   |   |   |
|---|---|---|---|---|
| Cargo:  | Dt Inicio:   | Dt Fim:   |  
| Cargo:  | Dt Inicio:   | Dt Fim:   |  

|  Dependentes |   |   |   |   |
|---|---|---|---|---|
| Nome:  | Dt Nascimento:   | 
| Nome:  | Dt Nascimento:   | 

<br>
<br>
<br>

|  Endereço |   |   |   |   |
|---|---|---|---|---|
| Bairro:   | Rua:  |  Nº: |  


> Observe que as informações são separadas da tabela principal.

> Outra coisa interessante é que nessa nova tabela criada, teremos ua FK, ou chave estrageira que referencia a chave primária da tabela principal.

<br>

#### **1.2** Agora que não temos nenhum elemento multivalorado, aplicaremos a segunda regra de normalização que avalia a relação de dependencia entre os atributos, dessa mesma tabela.


> A segunda regra de normalização, diz que os elementos complementares (os demais atributos), devem depender unicamente da chave primária.

<br>

>Aqui veremos a importancia de termos selecionado uma chave primária para a tabela toda.

#### **Relação de Dependencia da Chave**

<br>
<br>

- Nome depente/determina de Matricula? Sim. Pois, cada pessoa que trabalha possuí uma matricula que determina seu vinculo com a instituição e através dela podemos chegar a informações como: nome, idade, dentre outras coisas.

- Matricula depende/determina de Nome? Não, pois eu posso ter pessoas com nomes exatamente iguais e matriculas diferentes, por se tratar de pessoas distintas.

- Matricula determina Dt. Nascimento? Sim. Pelas mesmas razões pelas quais nome é determinado por matricula.

- Matricula determina cargo? Não. Pois eu posso ter o mesmo individuo ocupando dois cargos diferentes.


>Para ficar mais fácil de visualizar mostraremos essa relação em forma de tabela 

<br>



|  Relação de Dependencia da Chave |   |   |   |   |
|---|---|---|---|---|
| Matricula   → Nome   |  
| Cargo   ¬→  Nome  |
| (Matricula, Cargo) ¬⇒ Nome |
| Matricula  → Dt. Nascimento |
| Cargo   ¬→ Dt. Nascimento |
| (Matricula, Cargo) ¬⇒ Dt. Nascimento |
| Matricula  → Dt. Nascimento |
| Cargo   ¬→ Dt. Nascimento |
| (Matricula, Cargo) ¬⇒ Dt. Nascimento |

> (Matricula, Cargo) ¬⇒ Nome ("lê-se: Matricula e cargo não determina totalmente nome")

> Para se determinar totalmente, devemos ter duas negações. Logo, nenhuma das partes separada da chave deve conseguir identificar unicamente o campo em questão.



<br>


#### 2. Considere a tabela a seguir e verifique se ela está normalizada. Caso não esteja, normalize.


<br>

  Cliente|   |   |   |   |
|---|---|---|---|---|
| Código   |  Nome |  Telefone | Endereço
| 001| José| 9-0010-0010, 9-8810-8810| Rua seis, 36, Samanaú, Caicó - RN, 59.300-000
| 002| Maria| 9-9911-9911| Rua Projetada, 888, Jardim Europa, Patos - PB, 58.700-000
| 003| Marcos | 9-4444-8888, 9-3333-7777| Silberchartz, 1, Liberdade, São Paulo - SP, 565.985-150


> 1FN: Não deve haver elementos multivalorados na tabela, caso isso ocorra o elemento em questão devera ser retirado. 

***

Como **telefone** é multivalor, essa coluna será colocada em uma outra tabela e ficaremos com o seguinte cenário.



<br>



  Cliente|   |   |   |   |
|---|---|---|---|---|
| Código   |  Nome | Endereço | 
| 001| José| Rua seis, 36, Samanaú, Caicó - RN, 59.300-000 
| 002| Maria|Rua Projetada, 888, Jardim Europa, Patos - PB, 58.700-000
| 003| Marcos | Silberchartz, 1, Liberdade, São Paulo - SP, 565.985-150

<br>

 Telefone |   |   |   |   |
|---|---|---|---|---|
| Código   |  Telefone|
| 001| 9-0010-0010|
| 001| 9-8810-8810|
| 002| 9-9911-9911|
| 003| 9-4444-8888
| 003| 9-3333-7777

<br>

> 2FN: A chave deve conseguir identificar unicamente um elemento da tabela


<br>
Chave: Código

<br>

- Codigo → Nome
- Codigo → Endereço

Portanto, a tabela está na 2FN, uma vez que código determina totalmente nome e endereço

<br>

>3FN: Os elementos complementares só devem depender da chave

<br>

- Nome ¬→ Endereço

<br>

  Cliente|   |   |   |   |
|---|---|---|---|---|
| Código   |  Nome | Endereço | 
| 001| José| Rua seis, 36, Samanaú, Caicó - RN, 59.300-000 
| 002| Maria|Rua Projetada, 888, Jardim Europa, Patos - PB, 58.700-000
| 003| Marcos | Silberchartz, 1, Liberdade, São Paulo - SP, 565.985-150

<br>

 Telefone |   |   |   |   |
|---|---|---|---|---|
| Código   |  Telefone| 
| 01| 9-0010-0010|
| 02| 9-8810-8810|
| 03| 9-9911-9911|
| 04| 9-4444-8888
| 05| 9-3333-7777

<br>

#### Nesse caso, podemos fazer o seguinte. Dividimos o valor de Endereço, para conseguirmos analisar melhor essas relações de dependencia.

<br>

Então teriamos: Uma **Rua** dependendendo de uma **Cidade** e esta sendo dependente de **Estado**


Endereço        |                |              |    |           |    |
|---|---|---|---|---|---|
| Rua           | Bairro         | Cidade       | Nº | CEP       |UF|
|  Silberchartz | Liberdade      | São Paulo    |  1 |565.985-150|SP |
|  Rua Projetada| Jardim Europa  | Patos        |888 | 58.700-000|PB |
|  Rua seis     |  Samanaú       | Caicó        | 36 | 59.300-000| RN |

<br>

Agora que temos esses dados separados, podemos visualizar melhor a relação de dependência.

ItemPedido|   |   |   |   | |   | |
|---|---|---|---|---|---|---|---|
| ID Pedido  |  dt. Pedido | cód. Produto | nomeProduto | cód. Categoria | nomeCategoria | qtd | valorUnitário |
|1|24/10/2017|35| HD 500 Gb   |1|Uso Pessoal     |2|100,00
|2|24/10/2017|34| HD 1 Tb     |2|Uso Profissional|1|250,00
|3|25/10/2017|34| HD 1 Tb     |2|Uso Profissional|4|250,00
|4|26/10/2017|35| HD 500 Gb   |1|Uso Pessoal     |6|100,00
|1|24/10/2017|34| HD 1 Tb     |2|Uso Profissional|1|250,00
