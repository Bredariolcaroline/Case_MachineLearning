# Case_MachineLearning

 O dataset utilizado nesse projeto contém dados sociodemográficos e firmográficos de 2.240 clientes de uma empresa.

 Há dados sobre campanhas e se os clientes foram receptivos a essas campanhas ou não.

 Esse projeto está dividido em dois códigos, sendo que um deles tem uma etapa inicial e o outro engloba um etapa de PCA (Princiapl Component Analysis), através do qual foi realizado uma redução de dimensionalidade.

 ## Objetivos
 - Realizar análise exploratória de dados
 - Segmentação de clientes
 - Construção de modelo de classificação visando prever se um cliente irá comprar

## Análise exploratória
 Foi realizada uma etapa inicial de análises através do Profile Report, verificando de forma mais direta alguns dados e a partir disso, pudemos verificar duplicidade e nulidade de dados, verificação de possíveis outliers, além de quais fatures poderiam ser analisadas e até mesmo, se necessitavam de algum tipo de tratamento.

 Para facilitar a visualização, decidimos realizar uma segregação das idades, separando-as em grupos:
  - jovem-adulto:18-30
  - adulto: 31-45
  - adulto_senior: 46-60
  - idoso: 61+

 Criação de duas colunas para separar entre gastos com produtos regulares e com produtos considerados 'Gold': MntTotal e MntRegularProds.

 Junção das colunas KidHome e TeenHome em uma colun chamada Children, falando apenas sobre ter filhos ou não, sem segregá-los entre crianças e adolescentes.

 Para a coluna MaritalStatus que continha muitas informações, que em alguns casos pareciam repetitivas, as informações foram reunidas em 'Partner' ou 'Single', apenas.

Utilização do get_dummies do Pandas para transformação de colunas categóricas em colunas indicadoras para possibilitar o uso de algoritmos e verificação de correlação entre as features.

## Pré-processamento
Utilização de OneHotEncoder, StandarScaler, MinMaxScaler e PowerTransformer para padronização dos dados.
 * Colocar gráficos
## Definição do melhor número de clusters
Utilização de Elbow Method e Silhouette Method para verificação de clusters.

## Criação de Pipeline
Foi realizada uma etapa de PCA (Principal Component Analysis), que é uma técnica de redução de dimensionalidade com o objetivo de transformar um conjunto de variáveis correlacionadas em variáveis não correlaciondas na qual pode ocorrer perda de informações, porém de modo a manter as mais importantes e descartar as de menor importância mas faz-se necessário testar e verificar se obteve um bom funcionamento no conjunto de dados.

 ## Características de cada cluster
### Cluster 0:
-renda alta
-gasto alto
-muito provalmente não tem filhos
-mais propenso a aceitar campanhas
-cluster sem pessoas com escolaridade básica
-sem um perfil de idade que se destaque

### Cluster 1:
-renda intermediária
-gasto intermediário
-provalmente tem filhos
-pode aceitar campanhas
-pessoas com idade mais elevada

### Cluster 2:
-renda baixa
-gasto baixo
-provalmente tem filhos
-baixa propensão a aceitar campanhas
-único cluster com porcentagem significativa de pessoas com escolaridade básica (>96%)
-pessoas mais jovens

## Testes em busca do melhor modelo
A partir da verificação de métricas, escolhemos o modelo que melhor se adequou para nossos dados, levando em consideração principalmente ROC, Precisão e Recall.

# GridSearchCV
Após a escolha do modelo,  os melhores hiperparâmetros foram buscados por meio do GridSearCV

# Finalizando...
A partir de gráficos, visualizamos que houve melhora no nosso modelo após o uso dos hiperparâmetros sugeridos pelo GridSearchCV
ROC_curve: anteriormente 0,71 e agora 0,78
Precision Recall: anteriormente 0,42 e agora 0,58

* colocas gráficos para comparar
