# Previsão de Temperatura a partir de Dados de Qualidade do Ar

Este repositório contém o MVP (Produto Mínimo Viável) para a disciplina de *Machine Learning & Analytics*, focado em resolver um problema de regressão para prever a temperatura ambiente com base em dados de sensores de poluição.

**Autor:** Felipe Grumser
**Dataset:** [Air Quality UCI](https://archive.ics.uci.edu/dataset/360/air+quality)

---

## 🎯 Objetivo do Projeto

O objetivo principal deste trabalho é construir e avaliar um modelo de Machine Learning capaz de estimar a temperatura (`T` em °C) utilizando como variáveis preditoras as concentrações horárias de poluentes (CO, Benzeno, NOx, etc.) e medições de umidade.

O projeto demonstra um ciclo completo de desenvolvimento de um modelo, desde a preparação dos dados até a avaliação final e análise de limitações.

---

## 📂 Estrutura do Projeto

Este trabalho foi desenvolvido em duas etapas principais:

1.  **Análise Exploratória de Dados (Sprint Anterior):** Uma análise inicial completa foi realizada para entender, limpar e preparar o dataset. O notebook dessa etapa está disponível no repositório [MPV_Exploratoria](https://github.com/fgrumser/MPV_Exploratoria).
2.  **Modelagem de Machine Learning (Este Repositório):** O notebook `MVP_ML_&_Analytics_Felipe_Grumser (1).ipynb` contém todo o processo de modelagem, treinamento e avaliação.

---

## 🛠️ Metodologia e Etapas

O notebook de Machine Learning segue uma estrutura clara e documentada:

1.  **Definição do Problema:** O problema foi definido como uma tarefa de **Regressão** supervisionada.

2.  **Preparação e Limpeza dos Dados:**
    * O dataset pré-tratado da sprint anterior foi carregado diretamente de uma URL pública.
    * Uma limpeza final foi realizada para remover 114 registros que continham valores ausentes (`NaN`), garantindo a qualidade dos dados para o treinamento.

3.  **Análise Exploratória Focada:** Uma breve análise de correlação foi feita para validar a relação entre as `features` e a variável alvo, confirmando que as medições de umidade (`AH` e `RH`) eram os preditores lineares mais fortes.

4.  **Pré-processamento com Pipelines:**
    * Os dados foram divididos em conjuntos de **treino (80%)** e **teste (20%)**.
    * Um `Pipeline` do Scikit-learn foi criado para aplicar a **padronização (`StandardScaler`)** às `features`, garantindo consistência e prevenindo vazamento de dados.

5.  **Modelagem e Avaliação Comparativa:**
    * **Baseline:** Um `DummyRegressor` foi usado como ponto de partida para estabelecer um piso de qualidade.
    * **Modelos Candidatos:** Foram comparados um modelo linear (`Ridge`) e um modelo de ensemble (`RandomForestRegressor`).
    * **Resultados:** O `RandomForestRegressor` demonstrou uma superioridade massiva, superando os outros modelos com facilidade.

6.  **Otimização e Análise Final:**
    * O `RandomizedSearchCV` foi utilizado para otimizar os hiperparâmetros do `RandomForestRegressor`.
    * O modelo final foi avaliado no conjunto de teste, e uma **análise de overfitting** foi realizada para garantir a capacidade de generalização do modelo.

---

## 🏆 Resultados Finais

O modelo final, um **`RandomForestRegressor` otimizado**, alcançou um desempenho excepcional no conjunto de dados de teste:

| Métrica | Valor | Descrição |
| :--- | :--- | :--- |
| **RMSE (Erro Médio)** | **~0.34 °C** | Em média, as previsões do modelo erraram por apenas 0.34 graus Celsius. |
| **R² (Coef. de Determinação)**| **~99.85%** | O modelo foi capaz de explicar mais de 99.8% da variabilidade da temperatura. |
| **MAE (Erro Médio Absoluto)**| **~0.14 °C** | Outra medida do erro médio, confirmando a alta precisão. |

A análise de overfitting mostrou que o desempenho no conjunto de treino e no de teste foram muito próximos, indicando que o modelo generaliza bem para novos dados.

---

## 🚀 Como Executar

1.  **Ambiente:** O projeto foi desenvolvido em um notebook do **Google Colab** (`.ipynb`).
2.  **Dependências:** As principais bibliotecas utilizadas são `Pandas`, `Scikit-learn`, `Matplotlib` e `Seaborn`. Nenhuma instalação adicional é necessária, pois todas já vêm incluídas no ambiente padrão do Colab.
3.  **Execução:** Basta abrir o arquivo `MVP_ML_&_Analytics_Felipe_Grumser (1).ipynb` no Google Colab e executar as células em ordem. Os dados são carregados automaticamente de uma URL pública.

---

## 📦 Artefatos Salvos

* `final_model.joblib`: Um arquivo contendo o pipeline completo do modelo `RandomForestRegressor` final, já treinado e pronto para ser carregado e utilizado para fazer novas previsões.
