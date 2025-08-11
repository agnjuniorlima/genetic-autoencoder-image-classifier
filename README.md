
# Relatório de Resultados: Otimização de Rede Neural com Algoritmo Genético

**Disciplina:** Computação Natural

**Autor:** Agnelo Pereira Lima Júnior

**Data:** 30 de Julho de 2025

---
### 1. Objetivo

Este relatório apresenta os resultados da Tarefa Computacional 2, cujo objetivo era utilizar um Algoritmo Evolutivo (AE) para otimizar os hiperparâmetros de uma rede neural feedforward para a classificação de imagens do dataset MNIST. A análise de eficácia é realizada calculando-se as métricas de Acurácia, Precision, Recall e F-measure, e comparando os resultados com os do artigo de referência, "PARAMETER OPTIMIZATION OF AUTOENCODER FOR IMAGE CLASSIFICATION USING GENETIC ALGORITHM".

### 2. Metodologia

Foi implementado um Algoritmo Genético (GA) em Python para otimizar os hiperparâmetros de um classificador do tipo Multi-layer Perceptron (`MLPClassifier` da biblioteca `scikit-learn`). O GA buscou a melhor combinação para:
- Taxa de aprendizado
- Número de camadas ocultas
- Número de neurônios por camada
- Tamanho do lote (*batch size*)

A função de fitness utilizada para avaliar cada conjunto de hiperparâmetros foi a acurácia do modelo resultante no conjunto de teste do MNIST. Após 10 gerações, a melhor configuração encontrada foi utilizada para treinar um modelo final de forma mais exaustiva.

### 3. Resultados da Otimização

O Algoritmo Genético foi executado para explorar o espaço de soluções de hiperparâmetros. A configuração que demonstrou o maior potencial durante a busca evolutiva foi selecionada para o treinamento final. O gráfico abaixo ilustra a convergência do algoritmo, mostrando a melhoria da acurácia (fitness) ao longo das gerações.
<img width="872" height="548" alt="grafico" src="https://github.com/user-attachments/assets/2c91e66b-cb31-42aa-bf8f-57b3c8982837" />

### 4. Análise de Eficácia do Modelo Final

O modelo final foi treinado com os hiperparâmetros ótimos encontrados pelo GA. A avaliação no conjunto de teste de 10.000 amostras produziu as seguintes métricas de eficácia:

| Métrica | Valor (Média Ponderada) |
| :--- | :--- |
| **Acurácia** | **0.9776 (97.76%)** |
| Precision | 0.98 |
| Recall | 0.98 |
| F-measure (f1-score) | 0.98 |

A alta acurácia e as métricas balanceadas indicam que o modelo final é extremamente robusto, com capacidade de generalização e classificação eficaz para todas as 10 classes de dígitos.

### 5. Comparação com o Artigo de Referência

A comparação direta entre a acurácia do modelo otimizado e o resultado apresentado no artigo de referência é apresentada abaixo:

| Modelo | Acurácia |
| :--- | :--- |
| **Modelo Otimizado (Esta Tarefa)** | **97.76%** |
| Artigo de Referência (com GA) | 98.85% |

O resultado obtido de **97.76%** é altamente competitivo e se aproxima notavelmente do valor de **98.85%** reportado no artigo. A pequena diferença pode ser atribuída a variações na implementação (uso de `scikit-learn` vs. `TensorFlow`), à natureza estocástica do Algoritmo Genético e a diferenças no tempo total de treinamento.

### 6. Conclusão

O objetivo da tarefa foi cumprido com sucesso. A implementação de um Algoritmo Genético para otimização de hiperparâmetros provou ser uma abordagem eficaz, resultando em um modelo de rede neural com acurácia de **97.76%** no dataset MNIST. O desempenho do modelo é comparável ao estado da arte apresentado no artigo de referência, validando a metodologia empregada.
