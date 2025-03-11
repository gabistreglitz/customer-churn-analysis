# customer-churn-analysis
A Telco vem enfrentando desafios na retenção de clientes, com um aumento significativo na taxa de churn nos últimos períodos. Esse problema impacta diretamente a receita da empresa, tornando essencial identificar os principais fatores que levam ao cancelamento dos serviços e implementar estratégias eficazes de retenção.

## Descrição da empresa e seu problema
- Telco é uma empresa de telefonia que oferece planos de internet, streaming e serviços de segurança online. No entanto, tem enfrentado dificuldades com a alta rotatividade de clientes.
- O principal desafio na retenção de clientes é identificar os motivos que influenciam a decisão de cancelamento do serviço. Diante disso, os colaboradores da empresa precisam treinar um algoritmo para identificar os clientes com alta probabilidade de churn.
- Assim, após a classificação, é possível entrar em contato com os clientes insatisfeitos para oferecer promoções e dar discontos, de maneira que a empresa melhore a sua relação com eles.

## Objetivo
- Gerar insights através dos dados;
- Produzir informações visuais sobre a base de clientes da empresa;
- Classificar e identificar os clientes insatisfeitos através de um algoritmo de Machine Learning.

## Entendendo os dados
- O dataset foi coletado do Kaggle: https://www.kaggle.com/datasets/blastchar/telco-customer-churn/data;
- O dataset apresenta informações sobre:

    **1.** Clientes que cancelaram o serviço no último mês – essa informação está na coluna Churn;
  
    **2.** Serviços contratados por cada cliente – telefone, múltiplas linhas, internet, segurança online, backup online, proteção de dispositivos, suporte técnico e streaming de TV e filmes;
  
    **3.** Informações da conta do cliente – tempo como cliente, tipo de contrato, método de pagamento, cobrança sem papel, cobranças mensais e cobranças totais;

    **4.** Informações demográficas dos clientes – gênero, faixa etária e se possuem parceiros ou dependentes.

## Desenvolvimento do projeto
- **Importações**: Importações de bibliotecas e pacotes, definição de configurações e carregamento dos dados;
- **Descrição dos dados**: Apresenta-se o dataset, suas dimensões, colunas com descrições, tipos de dados;
- **Pré-processamento e exploração**: Renomeação das colunas, verificação de dados faltantes e utilização do método SimpleImputer para preencher valores ausentes (NaNs), ajuste dos tipos de dados conforme necessário, identificação de linhas duplicadas e análise de valores únicos.
- **Análise exploratória dos dados (EDA)**: Nesta etapa, o objetivo é visualizar e comparar as principais variáveis, interpretando os resultados para responder a questões relacionadas ao churn. Além disso, foram aplicadas técnicas estatísticas para organizar e exibir a relação entre duas ou mais variáveis categóricas, incluindo o teste do qui-quadrado, que verifica se há uma associação significativa entre elas. Dessa forma, as principais conclusões da Análise Exploratória dos Dados (EDA) foram:

  **1.** Na variável target, observa-se que a maioria dos clientes permanece com o serviço (73,6%), enquanto 26,4% cancelaram. No entanto, esse conjunto de dados está desbalanceado, o que pode impactar o treinamento dos modelos de Machine Learning, fazendo com que a previsão tenda a classificar mais clientes como "não churn".

  ![image](https://github.com/user-attachments/assets/ab406bf5-cfff-4c5f-bf75-50959b3a404d)

  
  **2.** Nas variáveis numéricas "tenure", "monthlycharges", "totalcharges" e "seniorcitizen". Foi possível identificar nos gráficos:

     - **Tenure (Tempo de contrato):** O histograma mostra uma alta taxa de churn a partir de 0 meses, o que pode indicar que muitos clientes assinam o serviço e o cancelam logo depois. Além disso, há uma acumulação significativa em torno de 70 meses, sugerindo que alguns clientes permanecem por um longo período antes de cancelar. Fora esses pontos, a distribuição é mais dispersa, cobrindo diferentes estágios de permanência no serviço. No boxplot, alguns outliers indicam que certos clientes continuam assinantes por um período prolongado antes de cancelar. De forma Mongeral, os dados sugerem que clientes mais novos têm maior probabilidade de churn.
     - **MonthlyCharges (Cobrança Mensal):** A análise do histograma sugere que clientes que pagam valores mensais mais baixos tendem a apresentar menor taxa de churn. Para valores mais altos, a distribuição parece mais uniforme. No boxplot, observa-se que clientes que pagam US$ 80,00 ou mais tendem a ter uma taxa de churn mais alta.
     - **TotalCharges (Cobranças Total):** O histograma indica que a maioria dos clientes que cancelam o serviço não acumula um valor significativo em TotalCharges. No boxplot, a mediana dos clientes que deram churn é significativamente menor do que a dos clientes retidos, confirmando que muitos cancelam antes de acumular um alto valor total de cobrança. Além disso, no grupo Churn = Yes, há vários outliers, mostrando que alguns clientes cancelam o serviço mesmo após acumularem um alto valor total de cobrança. Isso sugere que, enquanto a maioria dos cancelamentos ocorre entre clientes novos ou de baixa receita, também há casos em que clientes de longo prazo decidem cancelar.
     - **SeniorCitizen (Clientes idosos):** A maioria dos clientes não são idosos. No entanto, entre aqueles que são, há uma tendência maior de churn.
  ![image](https://github.com/user-attachments/assets/496f19ce-57fd-43d1-b771-0d1c95192755)
  ![image](https://github.com/user-attachments/assets/cb8de959-dcc2-470f-a189-7fbba342a7fa)

   **3.** Nas variáveis categóricas "contract", "paymentmethod", "dependents", "partner", "gender", "internetservice", "techsupport", "onlinesecurity". Foi possível identificar nos gráficos:

     - **Contrato x Churn:** A análise mostra que há uma quantidade considerável de churn no tipo de contrato Mensal (Month-to-Month), o que era esperado, já que esse modelo oferece maior flexibilidade para cancelamento. Por outro lado, contratos de um ano e dois anos apresentam taxas de churn menores, sugerindo que compromissos de longo prazo reduzem a probabilidade de cancelamento.
     - **Método de Pagamento x Churn:** O método de pagamento por Cheque Eletrônico apresenta uma taxa de churn significativamente alta. Em contraste, pagamentos por Transferência Bancária e Cartão de Crédito, que são automáticos, apresentam taxas de churn menores. Isso pode indicar que clientes que utilizam Cheque Eletrônico podem ter dificuldades com pagamentos ou menor comprometimento com o serviço.
  ![image](https://github.com/user-attachments/assets/519f58b1-8bf6-47de-bcf5-0cae5aacde43)
     - **Dependentes x Churn:** A análise sugere que clientes sem dependentes apresentam uma taxa de churn maior em comparação com aqueles que possuem dependentes.
     - **Parceiros x Churn:** Da mesma forma, clientes sem parceiro também apresentam uma taxa de churn mais alta.
     - **Gênero x Churn:** De acordo com o teste Qui-Quadrado, não há evidências estatísticas de que o gênero influencie o churn. Portanto, essa variável pode ser removida da análise, pois não será útil para o modelo. (**Observação:** Em relação às variáveis Dependents (Dependentes) e Partner (Parceiro), clientes que possuem dependentes ou parceiros tendem a permanecer no serviço por mais tempo.
Isso pode ocorrer porque a decisão de cancelamento não depende exclusivamente do assinante.)
   ![image](https://github.com/user-attachments/assets/d82cb238-5c69-4cd4-b998-0497f4f8baec)
     - **Serviço de Internet x Churn:** Os dados mostram que clientes que utilizam Fibra Óptica possuem uma taxa de churn alta, o que pode indicar uma experiência insatisfatória com esse serviço. Já os clientes que utilizam DSL são menos propensos a cancelar.
     - **Suporte Técnico x Churn:** A análise indica que clientes sem suporte técnico apresentam uma alta taxa de churn, enquanto aqueles que possuem esse serviço têm taxas significativamente menores. Isso sugere que o suporte técnico pode ser um fator importante na retenção de clientes.
     - **Segurança Online x Churn:** Clientes que não possuem segurança online apresentam uma taxa de churn muito maior em comparação com aqueles que possuem esse serviço. Isso sugere que a segurança online pode agregar valor ao serviço e contribuir para a retenção de clientes.
  ![image](https://github.com/user-attachments/assets/5e327ef1-3855-436f-b8a6-2f38ef19434b)
- **Feature Engineering**: Nesta etapa, aplicamos o método LabelEncoder() às variáveis categóricas para convertê-las em valores numéricos. Além disso, utilizamos o mapa de correlação e o método VIF (Variance Inflation Factor) para identificar correlações entre as variáveis e verificar a presença de multicolinearidade, permitindo selecionar as mais relevantes para os modelos de Machine Learning. O conjunto de dados foi dividido em treino e teste, e o método SMOTE foi aplicado aos dados de treino para balancear as classes. Por fim, realizamos o escalonamento das variáveis com MinMaxScaler para garantir que todas fiquem na mesma escala.
- **Machine Learning**: os seguintes modelos de ML foram testados e avaliados a partir das métricas: Acurácia, Precisão, Recall, F1 Score, ROC AUC, Cross-Val ROC AUC, Classification Report e Matriz de Confusão.

     - LightLGBM, Random Forest, Logistic Regression, Decision Tree, KNN, XGBoost.
     - Os modelos LightGBM, Random Forest e XGBoost apresentaram as melhores performances e foram selecionados para aplicação de Cross-Validation e Hyperparameter Tuning.
     - Após a otimização dos hiperparâmetros utilizando RandomizedSearchCV e a comparação dos modelos por meio das curvas ROC e Precision-Recall, o modelo LightGBM demonstrou um bom equilíbrio entre recall e precision, além de bons resultados nas métricas avaliadas. Dessa forma, foi considerado o modelo de melhor desempenho geral.

## Conclusões do Projeto
- Durante a análise, foi possível identificar as principais variáveis que contribuem para o cancelamento dos clientes. Entre elas, destaca-se MonthlyCharges, indicando que clientes que pagam mensalidades mais altas têm maior probabilidade de cancelar o serviço. Além disso, a variável PaymentMethod, especialmente o método de pagamento via cheque eletrônico, está associada a uma alta taxa de churn, possivelmente devido a dificuldades que os clientes enfrentam com esse tipo de pagamento. Outra variável importante é Contract, que apresenta uma alta taxa de churn no plano mensal, sugerindo que muitos clientes assinam o serviço e cancelam nos primeiros meses, demonstrando uma baixa fidelização.
- Diante dessas informações, a empresa poderia adotar estratégias para reduzir o churn, como oferecer descontos nas mensalidades e incentivar métodos de pagamento mais estáveis, como transferência bancária e cartão de crédito, que são processados automaticamente e podem ajudar a evitar cancelamentos. Além disso, a implementação de programas de fidelidade pode ser uma abordagem eficaz para aumentar a retenção de clientes, uma vez que a variável Tenure indica que clientes que permanecem por mais tempo no serviço têm menor risco de churn.

## Avaliação da Precisão do Modelo
- Após ajustes e comparações entre diferentes modelos, o LightGBM se destacou como a melhor opção para a previsão de churn. Com uma acurácia de 89%, o modelo demonstra uma alta capacidade preditiva no conjunto de dados analisado. Além disso, ao observar as métricas de precisão e recall, percebe-se um bom equilíbrio:

     - Classe 0 (Clientes que não cancelaram): O modelo atingiu 91% de precisão e 95% de recall, indicando que consegue prever corretamente a maioria dos clientes que permanecem ativos.
     - Classe 1 (Clientes que cancelaram): O recall de 73% sugere que o modelo consegue identificar a maior parte dos clientes propensos ao churn, enquanto a precisão de 84% indica uma taxa de acerto razoável ao prever cancelamentos.
- A média ponderada das métricas reforça a consistência do modelo, com um F1-score geral de 89%, mostrando que ele equilibra bem precisão e recall, minimizando erros críticos.
