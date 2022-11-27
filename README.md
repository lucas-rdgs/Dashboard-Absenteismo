# Dashboard Absenteismo

# <center><img src="https://github.com/lucas-rdgs/Dashboard-Absenteismo/blob/main/capa.jpg" align="center" style="width:50%"/></center>

## 1. Questão de negócio
<p align="justify">O absenteísmo, também conhecido como absentismo ou ausentismo, é um indicador de Recursos Humanos usado para medir a ausência dos funcionários durante seus expedientes, que podem ser por faltas, atrasos ou saídas adiantadas. Certo grau de absenteísmo não impacta negativamente o andamento das atividades de uma empresa, no entanto se for elevado, pode trazer graves prejuízos.</p>

<p align="justify">Os períodos de férias dos colaboradores, vale ressaltar, não são levados em conta para o cálculo deste indicador, já que são direitos garantidos de todos os funcionários.</p>

<p align="justify">O cálculo do absenteísmo é feito pela seguinte equação:</p>

<img src="https://github.com/lucas-rdgs/Dashboard-Absenteismo/blob/main/Equacao.png">

<p align="justify">Na área de Recursos Humanos não há um consenso de um resultado ideal para o indicador, já que os impactos deste indicador não são os mesmos em todas as organizações. Porém, é de ampla concordância que se busca sempre reduzir o absenteísmo em qualquer empresa.</p>

### 1.2. Visão geral do conjunto de dados
O conjunto de dados original contém um arquivo .csv composto por 8336 linhas e 13 colunas descritas a seguir:

| **Coluna**     | **Descrição**                                      |
|:---------------|:---------------------------------------------------|
| EmployeeNumber | ID único do funcionário                            |
| Surname        | Sobrenome do funcionário                           |
| GivenName      | Primeiro nome do funcionário                       |
| Gender         | Gênero do funcionário. M = masculino; F = feminino |
| City           | Cidade de residência do funcionário                |
| JobTitle       | Cargo do funcionário                               |
| DepartmentName | Nome do departamento do funcionário                |
| StoreLocation  | Cidade de trabalho do funcionário                  |
| Division       | Divisão da empresa                                 |
| Age            | Idade do funcionário                               |
| LengthService  | Tempo, em anos, de trabalho na empresa             |
| AbsentHours    | Tempo, em horas, de ausência                       |
| BusinessUnit   | Unidade da empresa                                 |

## 2. Premissas do negócio
Para a realização deste dashboard, serão levadas em conta algumas premissas:

- Os dados utilizados correspondem a um ano de trabalho, de janeiro a dezembro;
- Não serão consideradas, para cada funcionário, 30 dias corridos referentes às suas férias;
- Todos os funcionários possuem a mesma carga horária de 40 horas semanais, ao longo de 52 semanas;
- Serão desconsiderados, ainda, 11 dias de trabalho de todos os funcionários, referentes aos feriados de:
  - Ano novo: 1 dia
  - Sexta-feira Santa: 1 dia
  - Tirandentes: 1 dia
  - Dia do Trabalho: 1 dia
  - Dia da Independência do Brasil: 1 dia
  - Dia de Nossa Senhora Aparecida: 1 dia
  - Dia de Finados: 1 dia
  - Proclamação da República: 1 dia
  - Natal: 1 dia
  - 2 feriados estaduais ou municipais
 - Não serão contabilizadas horas de atraso e saídas antecipadas, assim como serão descartadas licenças ou outros afastamentos.


## 3. Planejamento da solução
### 3.1 O método SAPE (Saída - Processo - Entrada)
#### Saída (Produto final)
Este projeto fornecerá um dashboard interativo construído no <i>software</i> Microsoft Power BI, contendo dois relatórios:
- Visão geral: contendo o resultado do indicador tanto para o panorama geral da empresa quanto para cada função, departamento, divisão e localidade;
- Visão por funcionário: contendo a ausência de cada funcionário para gerenciamento individual, através de navegação por filtros de função, departamento, divisão e localidade.

#### Processo (Passo-a-passo)
<strong>ETL</strong>
1. Extração de dados:
- Download do conjunto de dados no portal do Kaggle;
- Carregamento do arquivo "MFGEmployees4.csv" no Power BI;

2. Tratamento de dados
2.1. Tratamento inicial
- Análise inicial das tabelas, entendimento de seus conteúdos;
- Conferência do tipo de dados de cada coluna e alteração, caso necessário;
- Conferência de dados faltantes e tratamento, caso necessário;
- Conferência de dados inválidos ou incorretos e tratamento, caso necessário;

2.2. Feature Engineering
- Criação da coluna FullName, com a concatenação das colunas GivenName e Surname, com o nome completo de cada funcionário;
- Criação da coluna TotalHours, com a quantidade total de horas de trabalho de cada funcionário, após desconto dos feriados descritos na seção <strong>2. Premissas do negócio</strong>, totalizando 1992 horas anuais;

3. Carregamento
- Aplicação das modificações na tabela original, para a criação de medidas, gráficos, cartões e filtros nos relatórios do dashboard.


<strong>Dashboards</strong>
- Criação de medida para cálculo do indicador absenteísmo, pela equação apresentada anteriormente;
- Definição de paleta de cores para os visuais.

Relatórios
1. Visão geral
- Cartões com:
  - A quantidade total de funcionários;
  - A média de horas ausentes por funcionário;
  - A taxa global de absenteísmo, ou seja, o KPI total da empresa.
  
 - Gráfico de rosca com as taxas de absenteísmo separadas por gênero, masculino e feminino;
 - Gráfico de barras com o KPI por unidade de negócio (BusinessUnit), com recurso de drill down para as respectivas divisões (Division) e departamento (DepartmentName);
 
 Todos os cartões, barras e colunas terão suas cores formatadas automaticamente. A cor verde indicará que o KPI está dentro da meta de <strong>3%</strong>. Quando o valor for superior à meta, será aplicada a cor vermelha.
 
2. Áreas
- 

3. Funcionários
- 

Paleta de cores<br/>
Target:<br/>
![#07540A](https://placehold.co/15x15/07540A/07540A.png) `#07540A` <br/>
![#E54B4B](https://placehold.co/15x15/E54B4B/E54B4B.png) `#E54B4B`

Paleta de azuis:

![#03045E](https://placehold.co/15x15/03045E/03045E.png) `#03045E` <br/>
![#023E8A](https://placehold.co/15x15/023E8A/023E8A.png) `#023E8A` <br/>
![#0077B6](https://placehold.co/15x15/0077B6/0077B6.png) `#07540A` <br/>
![#0096C7](https://placehold.co/15x15/0096C7/0096C7.png) `#07540A` <br/>
![#48CAE4](https://placehold.co/15x15/48CAE4/48CAE4.png)
![#90E0EF](https://placehold.co/15x15/90E0EF/90E0EF.png)
![#ADE8F4](https://placehold.co/15x15/ADE8F4/ADE8F4.png)
![#CAF0F8](https://placehold.co/15x15/CAF0F8/CAF0F8.png)



#### Entrada
- Os dados deste projeto foram retirados do portal Kaggle e estão disponíveis no link:

    [https://www.kaggle.com/datasets/HRAnalyticRepository/absenteeism-dataset?resource=download](https://www.kaggle.com/datasets/HRAnalyticRepository/absenteeism-dataset?resource=download)
    
 ### 4. Insights
<p align="justify">A análise exploratória dos dados proporciona alguns insights:</p>

#### Insight 1: 
<p align="justify"></p>

#### Insight 2: 
<p align="justify"></p>

#### Insight 3: 
<p align="justify"></p>

## 5. Resultados financeiros para o negócio
<p align="justify"></p>

## 6. Conclusão
<p align="justify"></p>

## 8. Próximos passos
<p align="justify"></p>

## 9. Tecnologias

## 10. Sobre o autor
Olá! Meu nome é Lucas Rodrigues.<br/>
Conecte-se comigo no meu [Linkedin](https://www.linkedin.com/in/lucasrodrigues3/).
