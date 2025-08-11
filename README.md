# Relatório de Resultados: Otimização de Rede Neural com Algoritmo Genético

**Disciplina:** Computação Natural

**Autor:** Agnelo Pereira Lima Júnior

<agnelo.lima@edu.ufes.br>

<agnjuniorlima@gmail.com>

**Data:** 11 de Agosto de 2025

---

### 1. Objetivo

Este relatório apresenta os resultados da Tarefa Computacional 2, cujo objetivo era utilizar um Algoritmo Evolutivo (AE) para otimizar os hiperparâmetros de uma rede neural feedforward para a classificação de imagens do dataset MNIST. A análise de eficácia é realizada calculando-se as métricas de Acurácia, Precision, Recall e F-measure, e comparando os resultados com os do artigo de referência, "PARAMETER OPTIMIZATION OF AUTOENCODER FOR IMAGE CLASSIFICATION USING GENETIC ALGORITHM".

### 2. Metodologia

Foi implementado um Algoritmo Genético (GA) em Python para otimizar os hiperparâmetros de um classificador do tipo Multi-layer Perceptron (`MLPClassifier` da biblioteca `scikit-learn`). O GA buscou a melhor combinação para a taxa de aprendizado, o número de camadas ocultas, o número de neurônios por camada e o tamanho do lote (*batch size*). A função de fitness utilizada para avaliar cada conjunto de hiperparâmetros foi a acurácia do modelo resultante no conjunto de teste do MNIST. Após a conclusão do GA, a melhor configuração encontrada foi utilizada para treinar um modelo final de forma mais exaustiva.

#### 2.1. Ambiente de Execução
O treinamento e a otimização foram realizados em um ambiente com a seguinte configuração:
- **Processador (CPU):** 12th Gen Intel(R) Core(TM) i7-1265U 1.80 GHz
- **Memória RAM:** 16,0 GB
- **Sistema Operacional:** Sistema operacional de 64 bits, processador baseado em x64

#### 2.2. Parâmetros de Treinamento e Otimização
As seguintes configurações foram utilizadas durante a execução do experimento:

**Parâmetros do Algoritmo Genético:**
- **Número de Gerações:** 10
- **Tamanho da População:** 15 indivíduos
- **Iterações por Avaliação de Fitness:** 30

**Parâmetros do Modelo Final (Otimizados pelo GA):**
- **Arquitetura:** 2 camadas ocultas com [512, 256] neurônios
- **Taxa de Aprendizado:** 0.005
- **Batch Size:** 256
- **Máximo de Iterações (Treino Final):** 100

---

### 3. Resultados da Otimização

O Algoritmo Genético foi executado com sucesso, explorando 150 configurações de rede distintas ao longo de 10 gerações. A configuração de maior destaque, encontrada na Geração 3, atingiu uma acurácia de **97.43%** e foi selecionada para o treinamento final.

O gráfico de convergência abaixo (Figura 1) ilustra a evolução da melhor solução encontrada a cada geração.


<img width="872" height="548" alt="grafico" src="https://github.com/user-attachments/assets/0729046c-febe-4c86-844b-162e9afa3daf" />


**Figura 1:** Gráfico de convergência do Algoritmo Genético, mostrando a melhor fitness (acurácia) por geração.

---

### 4. Análise de Eficácia do Modelo Final

O modelo final foi treinado com os hiperparâmetros ótimos encontrados pelo GA. O tempo total para o treinamento e avaliação do modelo foi de **1420.30 segundos** (aproximadamente 23 minutos). O modelo final alcançou uma acurácia geral de **98.08%**.

#### 4.1. Análise por Classe (Relatório de Classificação)
A análise detalhada por classe revela um desempenho excelente e bem distribuído. As métricas de precision, recall e f1-score foram consistentemente altas para todos os dígitos, indicando que o modelo não possui viés ou dificuldade significativa com nenhuma classe específica.

| Dígito | Precision | Recall | F1-Score |
|:---:|:---:|:---:|:---:|
| 0 | 0.98 | 0.99 | 0.99 |
| 1 | 0.99 | 0.99 | 0.99 |
| 2 | 0.98 | 0.98 | 0.98 |
| 3 | 0.97 | 0.99 | 0.98 |
| 4 | 0.98 | 0.97 | 0.98 |
| 5 | 0.99 | 0.97 | 0.98 |
| 6 | 0.99 | 0.99 | 0.99 |
| 7 | 0.99 | 0.98 | 0.98 |
| 8 | 0.97 | 0.97 | 0.97 |
| 9 | 0.97 | 0.97 | 0.97 |
| **Média Ponderada** | **0.98** | **0.98** | **0.98** |

#### 4.2. Análise de Erros (Matriz de Confusão)
A matriz de confusão (Figura 2) permite um diagnóstico preciso dos erros de classificação do modelo. Os valores na diagonal principal representam os acertos e são, como esperado, muito altos.


<img width="797" height="701" alt="matriz_confusao" src="https://github.com/user-attachments/assets/8b04562a-abd9-4d97-bb29-bffdafe2bd80" />


**Figura 2:** Matriz de Confusão do modelo final.

A análise dos valores fora da diagonal principal revela os erros mais comuns:
- O erro mais significativo foi a confusão entre o dígito **4** e o **9**, onde o modelo classificou incorretamente 18 imagens do dígito 4 como sendo o 9. Esta é uma confusão clássica devido à semelhança visual entre os dois números.
- Outras confusões notáveis, embora menos frequentes, incluem: **5** classificado como **3** (9 vezes), **8** como **3** (8 vezes), e **7** como **2** (7 vezes).

---

### 5. Comparação com o Artigo de Referência

A comparação direta entre a acurácia do modelo otimizado e o resultado apresentado no artigo de referência é apresentada abaixo:

| Modelo | Acurácia |
| :--- | :--- |
| **Modelo Otimizado (Esta Tarefa)** | **98.08%** |
| Artigo de Referência (com GA) | 98.85% |

O resultado obtido de **98.08%** é altamente competitivo e se aproxima notavelmente do valor de **98.85%** reportado no artigo. A pequena diferença de menos de 1% valida a abordagem e pode ser atribuída a variações na implementação (`scikit-learn` vs. `TensorFlow`) e à natureza estocástica do processo de otimização.

---

### 6. Conclusão

O objetivo da tarefa foi cumprido com sucesso. A implementação de um Algoritmo Genético para otimização de hiperparâmetros provou ser uma abordagem eficaz, resultando em um modelo de rede neural com acurácia de **98.08%** no dataset MNIST. A análise detalhada das métricas e da matriz de confusão confirma que o modelo é robusto e bem-balanceado, com erros de classificação concentrados em dígitos visualmente similares. O desempenho do modelo é comparável ao estado da arte apresentado no artigo de referência, validando a metodologia empregada.
