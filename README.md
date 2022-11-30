# Dashboard Absenteismo

# <center><img src="https://github.com/lucas-rdgs/Dashboard-Absenteismo/blob/main/capa.jpg" align="center" style="width:50%"/></center>

## 1. Questão de negócio
<p align="justify">O absenteísmo, também conhecido como absentismo ou ausentismo, é um indicador de Recursos Humanos usado para medir a ausência dos funcionários durante seus expedientes, que podem ser por faltas, atrasos ou saídas adiantadas. Certo grau de absenteísmo não impacta negativamente o andamento das atividades de uma empresa, no entanto se for elevado, pode trazer graves prejuízos.</p>

<p align="justify">Os períodos de férias dos colaboradores, vale ressaltar, não são levados em conta para o cálculo deste indicador, já que são direitos garantidos de todos os funcionários.</p>

<p align="justify">O cálculo do absenteísmo é feito pela seguinte equação:</p>

<img src="https://github.com/lucas-rdgs/Dashboard-Absenteismo/blob/main/Equacao.png">

<p align="justify">Na área de Recursos Humanos não há um consenso de um resultado ideal para o indicador, já que os impactos deste indicador não são os mesmos em todas as organizações. Porém, é de ampla concordância que se busca sempre reduzir o absenteísmo em qualquer empresa.</p>

<p align="justify">Assim, o objetivo deste projeto é criar um dashboard que permita analisar virtualmente as taxas de absenteísmo da empresa distribuídos por departamento, localização, gênero, além, evidentemente, da visão geral do indicador contabilizando todos os funcionários. Através de gráficos e tabelas, o usuário poderá gerar insights acionáveis sobre este importante KPI para então criar planos de ação para sua manutenção.</p>

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
    
 ## 4. Análise dos relatórios
<p align="justify">Navegando pelos relatórios pode-se analisar com mais profundidade a composição do KPI e perguntas podem ser </p>


### 4.1 Visão Geral
<img src="https://github.com/lucas-rdgs/Dashboard-Absenteismo/blob/main/visao_geral.png" align="center" style="width:100%"/>

<p align="justify">No relatório Visão Geral, há três cartões que possuem o número total de funcionários da empresa, a média de horas ausentes de toda a empresa e, finalmente, a taxa de absenteísmo geral. Assim, os 8336 funcionários possuem, em média, 61,28 horas ausentes no ano, o que confere à empresa um absenteísmo de 3,08%. O resultado está em vermelho pois está acima da meta, ou seja, ações precisam ser tomadas para que este número diminua para dentro da meta de 3,00%.</p>

<p align="justify">No gráfico de colunas, nota-se que a unidade de negócio Stores possui 3,09% de ausência, acima da meta, enquanto a unidade HeadOffice apresenta resultado positivo de 2,36% de absenteísmo. Este gráfico possui o recurso de Drill Down, que permite acessar os dados da hierarquia BusinessUnit - Division - DepartmentName. O vídeo a seguir exemplifica este recurso:</p>

![](https://github.com/lucas-rdgs/Dashboard-Absenteismo/blob/main/gif_visao_geral.gif)

<p align="justify">Quatro dos sete departamentos da unidade Stores fecharam o ano com o resultado acima da meta de 3,00%, quanto outros dois estão muito próximos da meta, com 2,99%, sendo pontos de atenção. O departamento Store Management fechou o KPI com 2,56%.</p>

<img src="https://github.com/lucas-rdgs/Dashboard-Absenteismo/blob/main/visao_geral_stores.png" align="center" style="width:100%"/>

<p align="justify">Os resultados da unidade HeadOffice serão apresentados a seguir, resumidamente:</p>

| **Divisão**            | **% Absenteísmo** |
|:-----------------------|------------------:|
| HumanResources         |             2,73% |
| Legal                  |             2,58% |
| Executive              |             2,43% |
| InfoTech               |             2,01% |
| Finance and Accounting |             2,01% |

<p align="justify">O absenteísmo é maior entre as mulheres, cujo resultado do indicador é de 3,35%, enquanto a taxa para os homens é de 2,81%.</p>

<p align="justify">É possível, ainda, fazer uma análise das localidades nas quais os funcionários mais estiveram ausentes percentualmente utilizando a tabela deste relatório</p>

### 4.2 Visão por Área
<img src="https://github.com/lucas-rdgs/Dashboard-Absenteismo/blob/main/visao_por_area.png" align="center" style="width:100%"/>

<p align="justify">O relatório Visão por Áreas apresenta, também, uma tabela com a %Absenteísmo por localidade, assim como um gráfico de barras com o KPI por departamento. Porém, neste relatório é possível que sejam filtradas as divisões e a função dos funcionários, além do gênero, para que possam ser feitas análises mais aprofundadas, por cada um dos gestores das divisões e dos departamentos.</p>

![](https://github.com/lucas-rdgs/Dashboard-Absenteismo/blob/main/gif_visao_areas.gif)

<p align="justify">Dos 21 departamentos, 7 que possuem resultados acima da meta fazem com que o resultado geral do KPI fique acima dos 3,00%, e por meio deste relatório pode-se escolher com maior assertividade os departamentos em que as ações mais rápidas devem ser tomadas.</p>

<p align="justify">Destes 7 departamentos, 4 são da divisão de Stores e os outrs 3 são de responsabilidade da divisão Human Resources.</p>

### 4.3 Visão Individual
<img src="https://github.com/lucas-rdgs/Dashboard-Absenteismo/blob/main/visao_individual.png" align="center" style="width:100%"/>

<p align="justify">Para um gerenciamento pais próximo dos funcionários com altas taxas de absenteísmo, o relatório Visão Individual possibilita que os gestores utilizem filtros de matrícula e nome, assim como áreas e funções, para criar ações individualizadas.</p>

![](https://github.com/lucas-rdgs/Dashboard-Absenteismo/blob/main/gif_visao_individual.gif)


 ## 5. Insights
<p align="justify">Após a construção de gráficos e tabelas, é possível explorar os dados para gerar insights:</p>

### Insight 1: Departamentos localizados em Vancouver possuem absenteísmo menor que aqueles que possuem funcionários localizados em outras cidades
<p align="justify">A empresa possui trabalhadores alocados em 243 cidades diferentes, e este número elevado se dá pela unidade Stores, ou seja, as lojas físicas da emrpesa. Por outro lado, os departamentos da unidade House Office trabalham apenas na cidade de Vancouver. Assim, espera-se que as horas ausentes sejam menores, proporcionalmente, quando todos os trabalhadores atuam em apenas um local.</p>

<p align="justify">Os departamentos da unidade House Office apresentam um absenteísmo de 2,36%, enquanto Stores tem o valor de 3,09%.</p>

<p align="justify">Planos de ação destinados às diversas lojas físicas devem ser coordenados para reduzir o valor do indicador nestes locais. Em menor prioridade, porém com maior facilidade de execução, ações centralizadas aos trabalhadores da cidade de Vancouver também devem ser aplicadas.</p>

### Insight 2: Divisões com maior quantidade de funcionários devem possuir absenteísmo maior
<p align="justify">Este comportamento é mais facilmente percebido na unidade Stores, que com seus 8163 funcionários corresponde a 98% do headcount. </p>

### Insight 3: 
<p align="justify"></p>



## 6. Conclusão
<p align="justify"></p>

## 8. Próximos passos
<p align="justify"></p>

## 9. Tecnologias

## 10. Sobre o autor
Olá! Meu nome é Lucas Rodrigues.<br/>
Conecte-se comigo no meu [Linkedin](https://www.linkedin.com/in/lucasrodrigues3/).
