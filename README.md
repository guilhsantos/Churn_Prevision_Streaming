# Previsão de Churn em Streaming

## Descrição do Projeto

Este projeto visa prever o churn (cancelamento) de assinantes em um serviço de streaming, utilizando técnicas de análise e modelagem de dados. O objetivo é identificar os fatores que contribuem para a saída de clientes e desenvolver um modelo preditivo eficaz.

## Dataset Utilizado

O dataset utilizado contém informações sobre assinantes de um serviço de streaming, incluindo dados demográficos e comportamentais. As principais colunas do dataset são:

- **Age**: Idade do assinante
- **Gender**: Gênero do assinante
- **Time_on_platform**: Tempo (em segundos) que o assinante passou na plataforma
- **Devices_connected**: Número de dispositivos conectados
- **Subscription_type**: Tipo de assinatura (e.g., Basic, Standard, Premium)
- **Num_streaming_services**: Número de serviços de streaming utilizados
- **Num_active_profiles**: Número de perfis ativos
- **Avg_rating**: Avaliação média do assinante
- **Churned**: Indicador de churn (0: Não, 1: Sim)
- **User_id**: Código de identificação do assinante

## Passos Realizados

### Passo 1: Análise Exploratória dos Dados
No primeiro passo, o dataset foi carregado utilizando a biblioteca Pandas. Uma análise inicial foi realizada para entender sua estrutura, que incluiu:

- **Visualização das primeiras entradas**: Uso do método `.head()` para inspecionar os dados.
- **Verificação de valores nulos**: Identificação de colunas com dados ausentes usando o método `.isnull().sum()`.
- **Análise estatística básica**: Geração de estatísticas descritivas utilizando `.describe()` para identificar padrões, tendências e outliers.
- **Visualizações**: Criação de gráficos como histogramas e boxplots para entender a distribuição dos dados e detectar anomalias.

### Passo 2: Tratamento dos Dados
Nesta etapa, os dados foram tratados para garantir a qualidade e a integridade das informações. As ações incluíram:

- **Substituição de valores nulos**: Valores ausentes em colunas selecionadas foram preenchidos com 0 para evitar impactos nas análises subsequentes.
- **Remoção de linhas com dados críticos faltantes**: Linhas com valores ausentes em colunas essenciais (como Churned) foram removidas para manter a acurácia do modelo.
- **Transformação de valores da coluna Churned**: Os valores binários de 0 e 1 foram convertidos para 'No' e 'Yes', facilitando a interpretação dos resultados.
- **Conversão de tipos de dados**: Tipos de dados foram ajustados para garantir que cada coluna estivesse no formato adequado para análise (e.g., conversão de datas).

### Passo 3: Modelagem dos Dados - Regressão Logística
As variáveis independentes (X) e dependentes (y) foram definidas com base nas colunas relevantes do dataset. O processo envolveu:

- **Codificação one-hot para variáveis categóricas**: Transformação de variáveis categóricas, como o tipo de assinatura e gênero, em variáveis binárias.
- **Separação dos dados em conjuntos de treinamento e teste**: A divisão foi realizada utilizando `train_test_split`, onde 80% dos dados foram utilizados para treinamento e 20% para teste.
- **Treinamento do modelo de Regressão Logística**: O modelo foi treinado com o conjunto de dados de treinamento.
- **Avaliação do desempenho**: O desempenho do modelo foi avaliado usando a matriz de confusão e um relatório de classificação, que incluiu métricas como precisão, revocação e F1-score.

### Passo 4: Modelagem dos Dados - Random Forest
O algoritmo de Random Forest foi aplicado para desenvolver um modelo preditivo. As etapas incluíram:

- **Criação do modelo**: Um modelo de Random Forest foi criado com parâmetros padrão.
- **Treinamento do modelo**: O modelo foi treinado com o conjunto de dados de treinamento.
- **Avaliação do desempenho**: O desempenho do modelo foi avaliado utilizando a matriz de confusão e métricas como precisão e revocação.
- **Importância das variáveis**: A importância de cada variável foi calculada, permitindo identificar quais fatores mais influenciam a previsão de churn.

### Passo 5: Tuning - Regressão Logística
Para otimizar a performance do modelo de Regressão Logística, foi realizado um processo de tuning que envolveu:

- **GridSearchCV**: Utilização do GridSearchCV para encontrar a combinação ideal de hiperparâmetros, como `C` e `solver`.
- **Avaliação de diferentes combinações**: Várias combinações de hiperparâmetros foram testadas para maximizar a acurácia do modelo.
- **Escolha do melhor modelo**: O melhor modelo foi selecionado com base nas métricas de desempenho.

### Passo 5: Tuning - Random Forest
O tuning do modelo Random Forest foi realizado para melhorar ainda mais seu desempenho, incluindo:

- **GridSearchCV**: Utilização do GridSearchCV para ajustar hiperparâmetros como o número de árvores (`n_estimators`), profundidade máxima (`max_depth`) e número mínimo de amostras para divisão (`min_samples_split`).
- **Teste de diferentes configurações**: Várias configurações foram testadas para encontrar a melhor combinação que minimizasse o erro de previsão.
- **Avaliação de desempenho**: A performance do modelo otimizado foi comparada com a versão anterior, utilizando a matriz de confusão e métricas de desempenho.

## Resultados

Os modelos de previsão foram avaliados usando a matriz de confusão e métricas como precisão, revocação e F1-score. A análise dos resultados permitiu identificar os fatores que influenciam o churn e compreender a importância das variáveis nos modelos. Isso proporcionou insights valiosos sobre o comportamento dos assinantes.

## Conclusão

Este projeto destaca a importância da análise de dados e do uso de modelos preditivos na retenção de clientes em serviços de streaming. Os insights obtidos podem ser utilizados para desenvolver estratégias de marketing e engajamento que visem reduzir o churn, garantindo um serviço mais eficaz e uma maior satisfação do cliente.
