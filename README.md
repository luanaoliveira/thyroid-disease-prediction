# Diagnóstico de Doenças da Tireoide com Machine Learning

Projeto final desenvolvido no curso **Profissão: Cientista de Dados — EBAC**, com o objetivo de construir um modelo de Machine Learning para apoiar a classificação de diagnósticos relacionados a doenças da tireoide.

## English Summary

Final Data Science project focused on predicting thyroid disease diagnosis using Machine Learning techniques. The project includes data preprocessing, exploratory data analysis, model comparison, hyperparameter tuning and final model interpretation.

## Contexto do Projeto

Este projeto simula uma situação real de Ciência de Dados, em que uma stakeholder da área médica solicita uma solução capaz de auxiliar na análise de diagnósticos relacionados à tireoide.

A base de dados contém informações clínicas, históricas, demográficas e laboratoriais de pacientes. A proposta é identificar padrões nos dados e desenvolver um modelo de classificação com bom desempenho preditivo.

## Objetivo

O objetivo principal deste projeto é desenvolver um modelo de classificação capaz de prever a variável-alvo `binaryClass`, utilizando informações dos pacientes e exames laboratoriais.

Como o problema está relacionado à área da saúde, a avaliação do modelo não foi baseada apenas na acurácia. Também foram consideradas métricas como precisão, recall, F1-score e matriz de confusão, com atenção especial ao equilíbrio entre as classes.

## Base de Dados

A base utilizada no projeto foi:

```text
Base_M43_Pratique_Hypothyroid.csv
```

O conjunto de dados possui:

* 3.772 registros;
* 30 variáveis inicialmente;
* variáveis clínicas e demográficas;
* informações sobre histórico médico e uso de medicamentos;
* resultados de exames laboratoriais;
* variável-alvo: `binaryClass`.

## Etapas do Projeto

O projeto foi desenvolvido seguindo as principais etapas de um fluxo de Ciência de Dados:

1. Entendimento do problema;
2. Carregamento da base de dados;
3. Análise inicial dos dados;
4. Tratamento de valores ausentes;
5. Conversão de tipos de dados;
6. Análise exploratória de dados;
7. Pré-processamento para modelagem;
8. Divisão entre treino e teste;
9. Treinamento de modelos;
10. Avaliação dos modelos;
11. Ajuste de hiperparâmetros;
12. Interpretação do modelo final;
13. Recomendações para o stakeholder;
14. Conclusão final.

## Tratamento e Preparação dos Dados

Durante a etapa de preparação dos dados, foram realizados os seguintes tratamentos:

* Substituição dos valores `"?"` por `NaN`;
* Remoção da coluna `TBG`, pois todos os seus registros estavam ausentes;
* Conversão das variáveis numéricas que estavam armazenadas como texto;
* Tratamento de valor inconsistente na variável `age`;
* Preenchimento de valores ausentes numéricos com a mediana;
* Preenchimento de valores ausentes categóricos com a moda;
* Codificação das variáveis categóricas com One-Hot Encoding.

Após o tratamento, a base ficou adequada para a análise exploratória e para a etapa de modelagem.

## Análise Exploratória de Dados

Durante a análise exploratória, foi identificado um forte desbalanceamento na variável-alvo:

* Classe `P`: aproximadamente 92,28%;
* Classe `N`: aproximadamente 7,71%.

Esse desbalanceamento tornou necessário avaliar os modelos com métricas além da acurácia, como precisão macro, recall macro e F1-score macro.

Também foram analisadas as distribuições das variáveis numéricas, boxplots, variáveis categóricas e correlações com a variável-alvo. A análise indicou que variáveis laboratoriais como `TSH`, `FTI`, `TT4` e `T3` apresentam relevância para a classificação.

## Modelos Avaliados

Foram avaliados os seguintes modelos de classificação:

* Regressão Logística;
* Árvore de Decisão;
* Random Forest;
* Support Vector Machine;
* Gradient Boosting.

Os modelos sensíveis à escala dos dados, como Regressão Logística e SVM, foram treinados com os dados padronizados.

## Modelo Final

O modelo escolhido para a solução final foi o **Gradient Boosting**, após ajuste de hiperparâmetros com `GridSearchCV`.

Os melhores hiperparâmetros encontrados foram:

```text
learning_rate = 0.05
max_depth = 4
n_estimators = 50
```

A escolha do modelo foi baseada principalmente no **F1-score macro**, pois essa métrica considera o desempenho das classes de forma equilibrada, sendo mais adequada para bases desbalanceadas.

## Resultados Finais

O modelo final apresentou os seguintes resultados no conjunto de teste:

| Métrica           | Resultado |
| ----------------- | --------: |
| Acurácia          |    99,60% |
| Precisão Macro    |    98,23% |
| Recall Macro      |    98,99% |
| F1-score Macro    |    98,61% |
| F1-score Weighted |    99,60% |

A matriz de confusão mostrou que o modelo final cometeu apenas 3 erros em 755 registros do conjunto de teste, indicando alto desempenho preditivo mesmo diante do desbalanceamento entre as classes.

## Interpretação dos Resultados

A análise de importância das variáveis mostrou que o exame `TSH` foi o principal atributo utilizado pelo modelo.

Outras variáveis relevantes foram:

* `on thyroxine`;
* `FTI`;
* `TT4`;
* `thyroid surgery`;
* `T4U`;
* `T3`.

Esses resultados indicam que exames laboratoriais e informações clínicas relacionadas à tireoide tiveram papel importante na classificação realizada pelo modelo.

## Recomendações para o Stakeholder

O modelo apresentou desempenho elevado e pode ser considerado uma ferramenta de apoio à decisão clínica.

No entanto, por se tratar de um problema relacionado à área da saúde, recomenda-se que o modelo seja utilizado apenas como suporte à análise médica, e não como substituto da avaliação de profissionais especializados.

Em um contexto real, seria necessário validar o modelo com novos dados, acompanhar seu desempenho ao longo do tempo e revisar periodicamente suas previsões.

Também é importante confirmar o significado clínico das classes `P` e `N` com o stakeholder ou com a documentação da base, garantindo que a interpretação dos resultados esteja alinhada ao diagnóstico correto.

## Conclusão

O projeto cumpriu o objetivo proposto ao desenvolver uma solução completa de Ciência de Dados para apoiar a classificação de diagnósticos relacionados à tireoide.

Foram realizadas etapas de entendimento do problema, preparação dos dados, análise exploratória, treinamento de diferentes modelos, avaliação de desempenho, ajuste de hiperparâmetros e interpretação dos resultados.

O modelo final, Gradient Boosting ajustado, apresentou acurácia de aproximadamente 99,60% e F1-score macro de aproximadamente 98,61%, demonstrando forte capacidade preditiva.

Apesar dos bons resultados, a aplicação prática do modelo exigiria validações adicionais com dados reais e acompanhamento por profissionais da área médica.

## Tecnologias Utilizadas

* Python;
* Pandas;
* NumPy;
* Matplotlib;
* Seaborn;
* Scikit-learn;
* Jupyter Notebook;
* Git e GitHub.

## Estrutura do Repositório

```text
thyroid-disease-prediction/
│
├── Base_M43_Pratique_Hypothyroid.csv
├── thyroid_disease_prediction_M43_final_project.ipynb
├── README.md
├── LICENSE
└── .gitignore
```

## Autora

Desenvolvido por **Luana Oliveira** como projeto final do curso **Profissão: Cientista de Dados - EBAC**.
