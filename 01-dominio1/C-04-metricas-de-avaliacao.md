# Métricas de Avaliação de Modelos

## Visão Geral

Métricas de avaliação medem a qualidade das previsões de um modelo. A prova AIF-C01 exige que você saiba **qual métrica usar** dependendo do tipo de problema e contexto de negócio.

---

## Métricas para Classificação

### Matriz de Confusão

Base para todas as métricas de classificação binária:

|  | Previsto: Positivo | Previsto: Negativo |
|--|--------------------|--------------------|
| **Real: Positivo** | TP (True Positive) | FN (False Negative) |
| **Real: Negativo** | FP (False Positive) | TN (True Negative) |

- **TP:** modelo acertou o positivo
- **TN:** modelo acertou o negativo
- **FP:** modelo disse positivo, mas era negativo (alarme falso)
- **FN:** modelo disse negativo, mas era positivo (caso perdido)

### Acurácia (Accuracy)
- **Fórmula:** (TP + TN) / Total
- % de previsões corretas (positivas e negativas)
- **Problema:** enganosa em dados desbalanceados
- Exemplo: se 95% dos emails são legítimos, um modelo que SEMPRE diz "legítimo" tem 95% de acurácia mas é inútil para detectar spam

### Precisão (Precision)
- **Fórmula:** TP / (TP + FP)
- Dos que o modelo disse serem positivos, quantos realmente são?
- **Importante quando:** falsos positivos são caros
- Exemplo: diagnóstico médico — dizer que alguém está doente quando não está gera procedimentos desnecessários

### Recall (Sensibilidade / Revocação)
- **Fórmula:** TP / (TP + FN)
- Dos positivos reais, quantos o modelo detectou?
- **Importante quando:** falsos negativos são perigosos
- Exemplo: detecção de câncer — perder um caso real (FN) é pior que um alarme falso (FP)

### F1 Score
- **Fórmula:** 2 × (Precisão × Recall) / (Precisão + Recall)
- Média harmônica entre precisão e recall
- Útil quando precisamos balancear ambos
- Penaliza mais quando um dos dois é muito baixo

### AUC-ROC
- **AUC** = Area Under the Curve
- **ROC** = Receiver Operating Characteristic
- Mede a capacidade do modelo de distinguir entre classes
- Valor de 0 a 1 (0.5 = aleatório, 1.0 = perfeito)
- **Útil para:** comparar modelos independente do threshold escolhido

---

## Quando Usar Cada Métrica de Classificação

| Contexto | Métrica prioritária | Motivo |
|----------|--------------------:|--------|
| Dados balanceados, visão geral | Acurácia | Funciona bem quando classes são equilibradas |
| Detecção de fraude | Recall | Perder uma fraude (FN) é muito caro |
| Filtro de spam | Precisão | Bloquear email legítimo (FP) irrita o usuário |
| Classes desbalanceadas | F1 Score ou AUC-ROC | Acurácia seria enganosa |
| Comparar múltiplos modelos | AUC-ROC | Independe do threshold |

---

## Métricas para Regressão

### RMSE (Root Mean Squared Error)
- Raiz da média dos erros ao quadrado
- Penaliza erros grandes mais fortemente
- Na mesma unidade da variável alvo
- **Usar quando:** erros grandes são muito indesejados

### MAE (Mean Absolute Error)
- Média do valor absoluto dos erros
- Trata todos os erros igualmente
- Mais robusta a outliers que RMSE
- **Usar quando:** outliers não devem dominar a avaliação

### R² (Coeficiente de Determinação)
- Quanto da variação nos dados o modelo explica
- Valor de 0 a 1 (1 = explica toda a variação)
- **Usar quando:** quer entender o "poder explicativo" do modelo

---

## Métricas para IA Generativa / LLMs

| Métrica | O que mede | Uso |
|---------|-----------|-----|
| **ROUGE** | Sobreposição de n-grams entre texto gerado e referência | Resumos |
| **BLEU** | Qualidade de tradução comparada a referência humana | Tradução |
| **BERTScore** | Similaridade semântica usando embeddings | Geração de texto |
| **Perplexidade** | Quão "surpreso" o modelo fica com o texto | Qualidade do language model |
| **Avaliação humana** | Julgamento subjetivo de humanos | Qualidade geral, criatividade |

### Para a prova
- ROUGE → resumos (compara n-grams gerados vs referência)
- BLEU → tradução (precisão dos n-grams gerados)
- Avaliação humana → quando métricas automáticas não capturam qualidade (criatividade, tom, factualidade)

---

## Resumo para a Prova

| Situação na questão | Métrica correta |
|--------------------|-----------------|
| "Detectar todos os casos positivos" | Recall |
| "Evitar falsos alarmes" | Precisão |
| "Balancear detecção e alarmes" | F1 Score |
| "Dados desbalanceados" | F1 ou AUC-ROC (não acurácia) |
| "Comparar modelos" | AUC-ROC |
| "Prever valor numérico, penalizar erros grandes" | RMSE |
| "Avaliar qualidade de resumo" | ROUGE |
| "Avaliar qualidade de tradução" | BLEU |

---

*Próximo bloco: Tipos de Tarefas (classificação, regressão, clustering, anomalias)*
