#  PROJETO ROSSMANN PREDICTIONS
<img src="https://raw.githubusercontent.com/felipejaguiar/sales-predictions/main/img/Rossmann_Logo.png" alt="logo" style="zoom:80%;" />

base de dados em: https://www.kaggle.com/competitions/rossmann-store-sales/data


# Questão de Negócio
Rossmann é uma grande rede de drogarias e perfumarias que atua em diversos países do mercado europeu. Visando melhorar a estrutura física e o design de suas lojas, a empresa decidiu focar em reformas. Para auxiliar no processo de tomada de decisão, sobre quais lojas reformar, o CFO requisitou aos gerentes, previsões de venda para cada loja. Logo a questão de negócio é:

👉 Qual a previsão de venda de cada loja para as próximas 6 semanas?


# Premissas do Negócio
As premissas são alterações feitas nos dados originais a fim de melhorar a qualidade da análise. Para o projeto, tomou-se as seguintes premissas:

🟪 Dados de venda iguais a 0 foram retirados;

🟪 Dados de lojas fechadas foram retirados;

🟪 Para distância entre competidores, percebeu-se que os dados faltantes poderiam ser de inexistência de concorrência ou distância muito alta, portanto assumiu-se um valor superior a distância máxima encontrada no conjunto de dados. 

🟪 Dada a existência de competidores, os dados faltantes de abertura das lojas competidoras relacionados ao mês e anos, foram atribuídos pelas datas de venda das lojas; 

🟪 Os dados falantes sobre período de promoções seguiram a mesma base de alteração dos de abertura das lojas, só que para semana e ano.


# Planejamento da Solução

Aplicação do CRISP:
<img src="https://raw.githubusercontent.com/felipejaguiar/sales-predictions/main/img/Fluxogramas(1).png" alt="logo3" style="zoom:80%;" />

Passos:

 1️⃣ Descrição dos Dados - Observar a quantidade, tipos, existência de dados faltantes, estatística descritiva, dos dados;
 
 2️⃣ Feature Engineering - Decompor as features buscando novos atributos que contribuam para a melhor descrição dos dados que serão modelados;
 
 3️⃣ Filtragem de Variáveis - Selecionar e/ou excluir linhas e colunas que não agregam ao propósito do projeto e do negócio; 
 
 4️⃣ Análise Exploratória do Dados - Análisar o impacto das variáveis e sua importância no modelo, buscando melhor entendimento das correlações e gerando insights;
 
 5️⃣ Preparação dos Dados - Preparar os dados para a adaptação do modelo (Normalização, Reescala e Transformação;
 
 6️⃣ Seleção de Variáveis - Selecionar os atributos mais importantes para o modelo;
 
 7️⃣ Modelos de Machine Learning - Aplicar modelos de machine learning;
 
 8️⃣ Hyperparameter Fine Tunning - Encontrar o conjunto de parâmetros que maximiza o aprendizado do modelo;
 
 9️⃣ Interpretação e Tradução dos Resultados - Interpretar e traduzir os resultados obtidos pelo modelo, em resultados de negócio;
 
 🔟 Deploy do Modelo em Produção - Disponibilizar o modelo para sua futura análise e utilização por terceiros;
 

# Principais Insights

H1: Maior número de promoções ativas, mais vendas.

❌ FALSA: Lojas com somente a primeira promoção ativa, vendem mais.

H2: As vendas aumentam com o passar dos anos.

❌ FALSA: As vendas diminuem no geral com o passar dos anos.

H3: As lojas apresentam mais vendas no segundo semestre do ano.

❌ FALSA: As vendas diminuem consideravelmente no segundo semestre do ano.

H4: As lojas apresentam mais vendas antes do dia 10 de cada mês.

✅ VERDADEIRA: As vendas são maiores no período anterior ao dia 10 de cada mês no geral.

H5: As lojas apresentam menos vendas durante os fins de semana.

✅ VERDADEIRA: As vendas são consideravelmente maiores durante a semana em relação aos fins de semana.


# Demonstração de Resultados

Para fazer as predições foram avaliados 5 modelos, que são: Average, Linear Regression, Lasso (Linear Regression Regularized), Random Forest e XGBoost. E estes foram os resultados para a etapa de validação:
|Model Name		|MAE CV		|MAPE CV	|RMSE CV	         |
|------------------------------|------------------------------|--------------------|--------------------------|
|Random Forest 	|836.61 +/- 217.1	|0.12 +/- 0.02	|1254.3 +/- 316.17    |
|Linear Regression	|2081.73 +/- 295.63	|0.3 +/- 0.02	|2952.52 +/- 468.37  |
|Lasso			|2116.38 +/- 341.5	|0.29 +/- 0.01	|3057.75 +/- 504.26  |
|XGBoost Regressor	|7049.2 +/- 588.65	|0.95 +/- 0.0	|7715.2 +/- 689.51    |

Mesmo apresentando um erro maior em relação aos outros na etapa de análise das métricas, o modelo escolhido foi o XGBoost, pois na etapa de hyperparameter fine tunning obteve o melhor resultado em relação ao Random Forest (que seria o escolhido, mas devido a exigência de um maior espaço de publicação que acarretaria mais custos a empresa, não foi). Abaixo estão dispostas as métricas e resultados para o XGBoost:
 |         Model Name	|          MAE	   |       MAPE	 |         RMSE          |
 |-----------------------------|----------------------|------------------|----------------------|
|   XGBoost Regressor	|     767.867031   |    0.115342	 |   1104.999627   |

Traduzindo para o negócio realizou-se uma soma total das vendas nas predições, considerando os erros, e foram obtidos os seguintes resultados para o melhor e pior cenário:

|                  Predições                 |                Pior cenário               |          Melhor cenário         |
|---------------------------------------|---------------------------------------|----------------------------------|
|            $285.982.336,00           |           $285.122.909,38           |         $286.841.799,87       |


✳️ As predições de venda para cada loja nas próximas 6 semanas foi disponibilizada no Telegram e podem ser acessadas a qualquer momento. Para isso, basta abrir a conversa e teclar "/" e o número da loja, por exemplo: /22. O link de acesso direto a conversa é: https://t.me/prossmann_bo 

# Conclusão e Próximos Passos
Logo, o primeiro objetivo do projeto foi alcançado, pois conseguiu-se predizer as vendas de cada loja da rede nas próximas 6 semanas, cumprindo assim a tarefa repassada pelo gerente e sendo possível auxiliar diretamente na tomada de decisão do CFO.
Cabe ressaltar que o projeto tem altas possibilidades de melhoria, como, algumas lojas apresentaram certa dificuldade para estabelecer uma previsão com pouca variabilidade, poderiam ter uma análise específica sobre elas; ou uma otimização no método de busca dos hiper parâmetros para melhorar os resultados do modelo, por exemplo. Uma nova aplicação do ciclo CRISP também aumentaria as chances de diminuir a margem de erro das predições, através de uma análise mais profunda das features impactantes e até buscando obter novas. 

Ferramentas:

<a href = "www.python.org"><img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" target="_blank"></a>
<a href = "www.jupyter.org"><img src="https://img.shields.io/badge/Made%20with-Jupyter-orange?style=for-the-badge&logo=Jupyter" target="_blank"></a>
<a href = "https://id.heroku.com/login"><img src="https://img.shields.io/badge/Heroku-430098?style=for-the-badge&logo=heroku&logoColor=white"></a>
<a href = "https://t.me/prossmann_bot"><img src="https://img.shields.io/badge/Telegram-2CA5E0?style=for-the-badge&logo=telegram&logoColor=white" target="_blank"></a>


