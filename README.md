# customer-churn-analysis
A Telco vem enfrentando desafios na retenção de clientes, com um aumento significativo na taxa de churn nos últimos períodos. Esse problema impacta diretamente a receita da empresa, tornando essencial identificar os principais fatores que levam ao cancelamento dos serviços e implementar estratégias eficazes de retenção.

## Descrição da empresa e o problema
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
- **Importações**: importações de bibliotecas e pacotes, definição de configurações e carregamento dos dados;
- **Descrição dos dados**: apresenta-se o dataset, suas dimensões, colunas com descrições, tipos de dados;
- **Pré-processamento e exploração**: renomeia-se colunas, checar a presença de dados faltantes e usar o método SimpleImputer para preencher NAN's, verificar o tipo de dados de cada coluna e ajustar para o tipo adequado, checar linhas duplicadas, checar valores únicos;
