# Dashboard Absenteismo

# <center><img src="https://github.com/lucas-rdgs/Dashboard-Absenteismo/blob/main/capa.jpg" align="center" style="width:50%"/></center>

## 1. Questão de negócio
<p align="justify">O absenteísmo, também conhecido como absentismo ou ausentismo, é um indicador de Recursos Humanos usado para medir a ausência dos funcionários durante seus expedientes, que podem ser por faltas, atrasos ou saídas adiantadas. Certo grau de absenteísmo não impacta negativamente o andamento das atividades de uma empresa, no entanto se for elevado, pode trazer graves prejuízos.</p>

<p align="justify">Os períodos de férias dos colaboradores, vale ressaltar, não são levados em conta para o cálculo deste indicador, já que são direitos garantidos de todos os funcionários.</p>

<p align="justify">O cálculo do absenteísmo é feito pela seguinte equação:</p>

<img src="https://github.com/lucas-rdgs/Dashboard-Absenteismo/blob/main/Equacao.png">

<p align="justify">Na área de Recursos Humanos não há um consenso de um resultado ideal para o indicador, já que os impactos deste indicador não são os mesmos em todas as organizações. Porém, é de ampla concordância que se busca sempre reduzir o absenteísmo em qualquer empresa.</p>

<p align="justify">Assim, o objetivo deste projeto é criar um dashboard que permita analisar virtualmente as taxas de absenteísmo da empresa distribuídos por departamento, localização, gênero, além, evidentemente, da visão geral do indicador contabilizando todos os funcionários. Através de gráficos e tabelas, o usuário poderá gerar insights acionáveis sobre este importante KPI para então criar planos de ação para sua manutenção.</p>

### 1.1. Visão geral do conjunto de dados
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
### 3.1. O método SAPE (Saída - Processo - Entrada)
#### Saída (Produto final)
Este projeto fornecerá um dashboard interativo construído no <i>software</i> Microsoft Power BI, contendo dois relatórios:

- Visão geral: contendo o resultado do indicador tanto para o panorama geral da empresa quanto para cada função, departamento, divisão e localidade;
- Visão por funcionário: contendo a ausência de cada funcionário para gerenciamento individual, através de navegação por filtros de função, departamento, divisão e localidade.

#### Processo (Passo-a-passo)
<strong>ETL</strong><br/>
<strong>1. Extração de dados:</strong>
- Download do conjunto de dados no portal do Kaggle;
- Carregamento do arquivo "MFGEmployees4.csv" no Power BI;
<br/>

<strong>2. Tratamento de dados</strong><br/>
<b>2.1. Tratamento inicial</b>
- Análise inicial das tabelas, entendimento de seus conteúdos;
- Conferência do tipo de dados de cada coluna e alteração, caso necessário;
- Conferência de dados faltantes e tratamento, caso necessário;
- Conferência de dados inválidos ou incorretos e tratamento, caso necessário;
<br/>

<b>2.2. Feature Engineering</b>
- Criação da coluna FullName, com a concatenação das colunas GivenName e Surname, com o nome completo de cada funcionário;
- Criação da coluna TotalHours, com a quantidade total de horas de trabalho de cada funcionário, após desconto dos feriados descritos na seção <b>2. Premissas do negócio</b>, totalizando 1992 horas anuais;
<br/>

<strong>3. Carregamento</strong>
- Aplicação das modificações na tabela original, para a criação de medidas, gráficos, cartões e filtros nos relatórios do dashboard.
<br/>

<strong>Dashboards</strong>
- Criação de medida para cálculo do indicador absenteísmo, pela equação apresentada anteriormente;
- Definição de paleta de cores para os visuais.

<br/>
<strong>Relatórios</strong><br/>

<b>1. Visão geral</b>
- Cartões com:
  - A quantidade total de funcionários;
  - A média de horas ausentes por funcionário;
  - A taxa de absenteísmo por gênero;
  - A taxa global de absenteísmo, ou seja, o KPI total da empresa.

- Gráfico de colunas com o KPI por unidade de negócio (BusinessUnit), com recurso de drill down para as respectivas divisões (Division) e departamentos (DepartmentName);
- Tabela com o KPI por cidade;
- Botões de navegação para os outros relatórios.

<p align="justify">Todos os cartões, barras e colunas terão suas cores formatadas automaticamente. A cor verde indicará que o KPI está dentro da meta de <strong>3,00%</strong>. Quando o valor for superior à meta, será aplicada a cor vermelha.</p>
 
<b>2. Áreas</b>
- Cartões com:
  - A quantidade total de funcionários;
  - A média de horas ausentes por funcionário;
  - A taxa de absenteísmo por gênero;
  - A taxa global de absenteísmo, ou seja, o KPI total da empresa.

- Filtros de:
  - Divisão;
  - Função do empregado;
  - Gênero.

- Gráfico de barras com o KPI por departamentos (DepartmentName);
- Gráfico de dispersão com o KPI por tamanho do departamento;
- Tabela com o KPI por cidade;


<b>3. Funcionários</b>
- Tabela com o KPI para cada funcionário, com informações de matrícula, nome completo, função, divisão, departamento, quantidade de horas ausentes e taxa de absenteísmo.

- Caixas de busca por: matrícula e nome completo.

- Filtros de:
  - Área de trabalho: unidade de negócio, divisão e departamento;
  - Funcão.
  
- Botões de navegação para os outros relatórios.

#### Entrada
- Os dados deste projeto foram retirados do portal Kaggle e estão disponíveis no link:

    [https://www.kaggle.com/datasets/HRAnalyticRepository/absenteeism-dataset?resource=download](https://www.kaggle.com/datasets/HRAnalyticRepository/absenteeism-dataset?resource=download)
    
 ## 4. Análise dos relatórios
<p align="justify">Navegando pelos relatórios pode-se analisar com mais profundidade a composição do KPI e perguntas podem ser </p>


### 4.1. Visão Geral
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

### 4.2. Visão por Área
<img src="https://github.com/lucas-rdgs/Dashboard-Absenteismo/blob/main/visao_por_area.png" align="center" style="width:100%"/>

<p align="justify">Além do gráfico de barras com os valores totais de cada departamento, o gráfico inferior relaciona também o tamanho de cada departamento, por quantidade de funcionários. Sua análise permite um direcionamento mais efetivo das ações, já que, por exemplo, por mais que o departamento Recruitment possua o KPI em 3,16% frente a 3,08% de Bakery, este último possui 1449 funcionários, enquanto Recruitment possui apenas 14. Ações direcionadas a departamentos maiores impactam mais o indicador final global da empresa.</p>

<p align="justify">O relatório Visão por Áreas apresenta, também, uma tabela com a %Absenteísmo por localidade, assim como um gráfico de barras com o KPI por departamento. Porém, neste relatório é possível que sejam filtradas as divisões e a função dos funcionários, além do gênero, para que possam ser feitas análises mais aprofundadas, por cada um dos gestores das divisões e dos departamentos.</p>

![](https://github.com/lucas-rdgs/Dashboard-Absenteismo/blob/main/gif_visao_areas.gif)

<p align="justify">Dos 21 departamentos, 7 que possuem resultados acima da meta fazem com que o resultado geral do KPI fique acima dos 3,00%, e por meio deste relatório pode-se escolher com maior assertividade os departamentos em que as ações mais rápidas devem ser tomadas.</p>

<p align="justify">Destes 7 departamentos, 4 são da divisão de Stores e os outrs 3 são de responsabilidade da divisão Human Resources.</p>

### 4.3. Visão Individual
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
<p align="justify">Este comportamento é mais facilmente percebido na unidade Stores, que com seus 8163 funcionários corresponde a 98% do headcount. Nos departamentos restantes, a maior taxa de absenteísmo encontra-se em Human Resources, que possui o maior número de funcionários, com 2,73%.</p>

### Insight 3: O absenteísmo é maior entre as mulheres
<p align="justify">Diversos podem ser as causas para que as mulheres apresentem maiores taxas de ausências do que os homens. Porém, esta diferença é pronunciada, já que o KPI calculado apenas para as mulheres é de 3,35%, enquanto os homens apresentam 2,81%. A proporção de ambos os gêneros no quadro geral de funcionários é semelhante: 4120 funcionárias compõem 49,4% do total.</p>


## 6. Conclusão
<p align="justify">Em qualquer empresa é normal que haja faltas, saídas antecipadas ou atrasos inesperados, porém as ausências têm de ser controladas e gerenciadas. Para isso, um indicador muito utilizado na área de Recursos Humanos é o absenteísmo, que calcula as horas de ausência percentuais, ou seja, quanto os funcionários estão ausentes emm relação ao tempo total esperado de trabalho. Cada organização, conhecendo seu modelo de negócio e seus resultados financeiros, pode gerar metas para as taxas de absenteísmo, sendo globais, por setor ou departamento, ou até mesmo individualmente.</p>

<p align="justify">Uma ferramenta visual, com cartões, gráficos e tabelas foi desenvolvida no software Microsoft Power BI para gerenciamento das horas ausentes dos funcionários de uma empresa fictícia localizada no Canadá, com dados anuais de horas de trabalho. Nele, há 3 relatórios que proporciona diferentes níveis hierárquicos uma análise aprofundada dos números. No primeiro, os números gerais, com informações mais enxutas, são apresentadas visando que haja uma visão global da empresa, para que possam ser geradas ações para as unidades de negócio responsáveis. O segundo relatório permite que líderes de unidades de negócio, divisões e departamentos analisem os números de suas respectivas áreas. Finalmente, um último relatório possui os números descritos por funcionário, para que gestores diretos possam traçar planos individualiados ou para menor grupos de funcionários.</p>

<p align="justify">Após análises dos números apresentados em formas visuais, mais rapidamente são gerados insights que podem gerar ações com o objetivo de reduzir o absenteísmo na empresa, que no final do ano dos dados fechou o KPI em 3,08%, acima da meta estipulada de 3,00%. A unidade de negócio com maiores taxas de absenteísmo são as lojas, ou Stores, que estão decentralizadas da sede administrativa da empresa, localizada em Vancouver. Nesta, departamentos com maiores quantidades de funcionários devem receber ações de redução e manutenção de absenteísmo, já que eles possuem impacto maior no cálculo.</p>

<p align="justify">Sugestões de grupos de maior prioridade para direcionamento de planos de ação e contramedidas podem, então, ser feitas a partir das análises dos relatórios:</p>

| **Direcionamento**                                                                                                                           | **%Absenteísmo** | **Justificativa**                                                                        |
|:---------------------------------------------------------------------------------------------------------------------------------------------|:-----------------:|:-------------------------------------------------------------------------------------------|
| <p align="justify">Divisão de vendas (Stores), em ordem decrescente de prioridade: Processed Foods, Customer Service, Dairy e Bakery</p>                            |             3,09% | <p align="justify">Unidade de negócio com 98% do headcount, com 5 departamentos com resultado acima da meta</p> |
| <p align="justify">Na sede administrativa de Vancouver, divisão de Human Resources, em ordem decrescente de prioridade: Recruitment, Training, Employee Records</p> |             3,10% | <p align="justify">Divisão com resultados negativos. 3 departamentos com resultados acima da meta</p>           |
| <p align="justify">Ações direcionadas às mulheres</p>                                                                                                               |             3,35% | <p align="justify">49% do headcount formado por mulheres, que apresentam resultado acima da meta</p>            |


## 7. Próximos passos
<p align="justify">Os projetos de visualização de dados podem sempre ser aperfeiçoados à medida que as necessidades do negócio se alteram naturalmente. Neste primeiro ciclo de desenvolvimento, foram utilizadas premissas de jornadas de trabalho iguais a todos os funcionários, dias de férias e folgar por feriados. Para aperfeiçoar o projeto, podem ser levadas em conta outros regimes de trabalho depedendo da localidade do trabalhador, seu departamento ou nível hierárquico.</p>

<p align="justify">Um ponto importante que pode ser levado em conta é a determinação de metas diferentes para departamentos ou níveis hierárquicos diferentes. Áreas em que há um grande número de funcionários impacta o número global da empresa em proporções diferentes, e uma meta mais agressiva pode ser adotada. Outra estratégia comumente utilizada é a definição de metas diferentes ao longo do ano, para que o resultado final anual seja alcançado de maneira menos desafiadora.</p>

<p align="justify">Em relação aos artifícios visuais utilizados nos relatórios, é natural que haja alterações dependendo dos objetivos dos gestores no manejo do indicador, com o momento da empresa ou com as informações necessários. Sempre se deve manter em mente que um ambiente de trabalho saudável a comunicação é vital para que as expectativas sejam setadas com sucesso e que os objetivos sejam alcançados de maneira rápida e eficiente. Dito isto, os usuários finais podem sugerir alterações aos relatórios apresentados e cabe ao responsável pelo dashboard analisar a viabilidade e tempo de execução.</p>

## 8. Tecnologias
[<img src="https://logos-world.net/wp-content/uploads/2022/02/Microsoft-Power-BI-Symbol.png" style="height: 50px" align="left"/>](https://powerbi.microsoft.com/pt-br/)<br/><br/>

## 9. Sobre o autor
Olá! Meu nome é Lucas Rodrigues.<br/>
Conecte-se comigo no meu [Linkedin](https://www.linkedin.com/in/lucasrodrigues3/).
