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

>A chave primária é um campo que indentifica únicamente o elemento que queremos representar através do esquema de tabelas, nesse caso, como estamos querendo representar pessoas (Paciente e Funcionário). Teremos como possivel canditado ao cargo de chave-primária, o atributo: Matricula. Porém, só a matricula é capaz de me ajudar a melhorar essa tabela? 

Pensemos o seguinte: Eu posso ter mais de um cargo? Se a resposta for sim, então usar apenas a matricula não vai evitar que haja repetição no banco. Pois a matricula está vinculada a um único individuo. Logo, podemos criar uma chave composta que seria (Matricula, cargo). Agora vamos ao segundo passo:

<br>

#### **1.1** Analisamos a tabela e verificamos se há necessidade da aplicação da primeira regra de normalização que diz que todo atributo na tabela deve ser atômico. Sendo assim, não pode haver campos com valores compostos.

<br>

#### Endereço, contêm informações acerca da rua, bairro dentre outros atributos que poderiam aparecer de forma separada na tabela. Sendo assim, aplicaremos a primeira regra de normalização nesse campo, dividindo-o em: Rua, Bairro e Número.


<br>

#### **O resultado após a implementação da primeira regra será:**



|  Dados Cadastrais do Funcionário |   |   |   |   |
|---|---|---|---|---|
| Matricula:  | Nome:  |  
| Data Nasc.  | Nacionalidade:   | Sexo:   | 
| Est. Civil    | RG:    | CIC:   |  
| Rua:    | Telefone:    | Data de Admissão:   |  
| Bairro:      | Número:  |   

|  Cargos Ocupados |   |   |   |   |
|---|---|---|---|---|
| Cargo:  | Dt Inicio:   | Dt Fim:   |  
| Cargo:  | Dt Inicio:   | Dt Fim:   |  

|  Dependentes |   |   |   |   |
|---|---|---|---|---|
| Nome:  | Dt Nascimento:   | 
| Nome:  | Dt Nascimento:   | 

<br>

> OBS: O endereço poderia ter permanecido como está se você quisesse considerar o campo como uma String gingante e única, mas eu preferi analisar dessa forma, para colocarmos em prática todas as regras de normalização

<br>

#### **1.2** Agora que não temos nenhum elemento composto, aplicaremos a segunda regra de normalização que avalia a relação de dependencia em relação aos componentes. 

<br>

>Aqui veremos a importancia de termos selecionado uma chave primária para a tabela toda.

#### **Relação de Dependencia: Matricula**

<br>
<br>

- Nome depende de Matricula? Sim. Pois sempre que eu buscar por minha matricula, eu devo ser capaz de encontrar meu nome.

<br>

