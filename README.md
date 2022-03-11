# Avaliação de crédito :bank:

Nesse repositório foi desenvolvido um projeto de avaliação de crédito, tal projeto foi realizado durante o bootcamp datascience da Alura. No projeto foi realizado a análise exploratória com entendimento como o mercado financeiro define quem será concedito crédito, também foi realizado na aprendizagem de máquina o treinamento superficionado e por fim foi feito o deploy da aplicação.

## Análise exploratória :chart_with_upwards_trend:

Para a análise exploratória foi utilizado o dataset editado pela Alura baseado no dataset disponibilizado no Kaggle. Tal dataset é composto de duas base de dados um com os dados dos clientes e outro utilizado para a aprendizagem de máquina com o conjunto alvo. 

### Conjunto de dados dos clientes

Na base de dados dos clientes encontramos uma base com um conjunto de informações que são uteis para definição do cliente, com informações categóricas e contínuas. entre elas:

| Categóricas binárias     | Categóricas não binárias | Contínuas            |
| :----------------------- | :----------------------- | :------------------- |
| Tem carro                | Categoria de renda       | Idade                |
| Tem casa própria         | Grau de escolaridade     | Quantidade de filhos |
| Tem telefone do trabalho | Estado civil             | Rendimento anual     |
| Tem telefone fixo        | Moradia                  | Anos empregado       |
| Tem e-mail               | Ocupação                 | Tamanho da família   |

Tal dataset apresenta 438.557 clientes no qual foram utilizados 425.822 clientes após a remoção de linhas repetidas e outliers, uma redução menor que 3% no conjunto original.

A partir da análise de dados observamos de grande parte dos clientes tem rendimento na faixa entre R$ 100.000 e R$ 150.000 anuais com uma média de       R$ 176.384 anuais.

![redimento anual](https://github.com/monclai/Avaliacao_credito/blob/main/images/redimento_anual.png?width=1225&height=670)

Também observamos que grande parte dos clientes não definiram qual profissão realiza.

![](https://github.com/monclai/Avaliacao_credito/blob/main/images/ocupacao.png)

Observando tal fato, e relacionando com o rendimento, temos que o redimento médio na base de dados está altamente correlacionado com os clientes de definiram como ocupação _outros_. Como podemos ver no gráfico abaixo.

![](https://github.com/monclai/Avaliacao_credito/blob/main/images/redimento_anual.outros.png)

### Conjunto de dados alvo

No conjunto de dados alvo temos um conjunto com 45.985 clientes, sendo esse um valor 89% menor que o conjunto total de clientes, demonstrando assim que um há um seleto grupo de clientes que tiveram o crédito aprovado. sabendo disso foram feitas agregações de dados com base no mês de referência e a faixa de atraso além da análise vintage, sendo esta uma análise muito utilizado no mercado financeiro, feito isso foi determinado que seriam considerados bons clientes aqueles que tivessem uma faixa de atraso de até 60 dias.


![](https://github.com/monclai/Avaliacao_credito/blob/main/images/clientes_maus_faixa_atraso.png)


## Aprendizagem de máquina

Para aprendizagem de máquina devemos primeiro observa os dados, que nesse dataset se apresentava de forma desbalanceada.

| Alvo |    0    |   1    |
| :--: | :-----: | :----: |
|      | 97.726% | 2.273% |

Sabendo disso foi feito um pipeline que realizou o treinamento identificando o conjunto de variáveis categóricas e contínuas, além de realizar o oversampling como forma de balancear os dados; feito o treinamento com diversos modelos, foi concluido que o modelo de florestas randomicas é o que apresentou melhores resultados. Como pode ser visto abaixo:


![](https://github.com/monclai/Avaliacao_credito/blob/main/images/matriz_confusao.png)

AUC 0.8340043216670643  
KS Ks_2sampResult(statistic=0.9653534998241294, pvalue=0.0)

Classification Report

|              | precision | recall | f1-score | support |
| ------------ | --------- | ------ | -------- | ------- |
| 0            | 0.99      | 0.99   | 0.99     | 5557    |
| 1            | 0.47      | 0.36   | 0.41     | 129     |
|              |           |        |          |         |
| accuracy     |           |        | 0.98     | 5686    |
| macro avg    | 0.73      | 0.68   | 0.70     | 5686    |
| weighted avg | 0.97      | 0.98   | 0.97     | 5686    |

## Deploy

Para o deploy foi utilizado o streamlit que permitiu a criação de um interface de forma simples para avaliação com base no modelo sobre a concessão de crédito.

__links:__

[Atividade Kaggle](https://www.kaggle.com/rikdifos/credit-card-approval-prediction)

[Base de dados editada pela Alura](https://github.com/alura-cursos/Avaliacao_Credito/tree/main/dados)

[Deploy da aplicação no streamlit](https://share.streamlit.io/monclai/avaliacao_credito/main/simulador_avaliacao_credito.py)


