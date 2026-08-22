# Métricas de Avaliação de Modelos

## Visão Geral

Métricas de avaliação medem a qualidade das previsões de um modelo. A prova AIF-C01 exige que você saiba **qual métrica usar** dependendo do tipo de problema, contexto de negócio e tipo de modelo (ML tradicional vs. foundation models).

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
- **Limitação:** enganosa em dados desbalanceados
- Exemplo: se 95% dos emails são legítimos, um modelo que SEMPRE diz "legítimo" tem 95% de acurácia mas é inútil para detectar spam

### Precisão (Precision)
- **Fórmula:** TP / (TP + FP)
- Dos que o modelo disse serem positivos, quantos realmente são?
- **Priorizar quando:** falsos positivos são custosos
- Exemplo: filtro de spam — bloquear email legítimo (FP) irrita o usuário

### Recall (Sensibilidade / Revocação)
- **Fórmula:** TP / (TP + FN)
- Dos positivos reais, quantos o modelo detectou?
- **Priorizar quando:** falsos negativos são perigosos
- Exemplo: detecção de câncer — perder um caso real (FN) pode custar uma vida

### F1 Score
- **Fórmula:** 2 × (Precisão × Recall) / (Precisão + Recall)
- Média harmônica entre precisão e recall
- Útil quando precisamos balancear ambos
- Penaliza mais quando um dos dois é muito baixo

### AUC-ROC
- **AUC** = Area Under the Curve
- **ROC** = Receiver Operating Characteristic
- Mede a capacidade do modelo de distinguir entre classes em diferentes thresholds
- Valor de 0 a 1 (0.5 = aleatório, 1.0 = perfeito)
- **Útil para:** comparar modelos independentemente do threshold escolhido

---

## Quando Usar Cada Métrica de Classificação

| Contexto | Métrica prioritária | Motivo |
|----------|---------------------|--------|
| Dados balanceados, visão geral | Acurácia | Funciona bem quando classes são equilibradas |
| Detecção de fraude, doenças | Recall | Perder um caso real (FN) é muito custoso |
| Filtro de spam, alertas | Precisão | Alarmes falsos (FP) causam problemas |
| Classes desbalanceadas | F1 Score ou AUC-ROC | Acurácia seria enganosa |
| Comparar múltiplos modelos | AUC-ROC | Independe do threshold |

---

## Métricas para Regressão

| Métrica | O que mede | Quando usar |
|---------|-----------|-------------|
| **RMSE** (Root Mean Squared Error) | Raiz da média dos erros ao quadrado. Penaliza erros grandes. | Quando erros grandes são muito indesejados |
| **MAE** (Mean Absolute Error) | Média do valor absoluto dos erros. Trata todos igualmente. | Quando outliers não devem dominar a avaliação |
| **R²** (Coeficiente de Determinação) | Quanto da variação nos dados o modelo explica (0 a 1). | Quando quer entender o "poder explicativo" do modelo |

---

## Métricas para IA Generativa / Foundation Models

### Métricas automáticas baseadas em referência

| Métrica | O que mede | Uso típico | Limitação |
|---------|-----------|------------|-----------|
| **ROUGE** | Sobreposição de n-grams entre texto gerado e texto de referência | Resumos de texto | Mede sobreposição textual, não qualidade semântica. Um texto pode dizer o mesmo com palavras diferentes e ter ROUGE baixo. |
| **BLEU** | Precisão de n-grams do texto gerado comparada a referência(s) humana(s) | Tradução automática | Mesmo problema: textos semanticamente corretos mas com palavras diferentes recebem pontuação baixa. |
| **BERTScore** | Similaridade semântica usando embeddings contextuais | Geração de texto em geral | Mais robusto que BLEU/ROUGE para capturar equivalência semântica, mas depende do modelo de embeddings usado. |
| **Perplexidade** | Quão "surpreso" o modelo fica com o texto (inverso da probabilidade) | Qualidade do language model | Baixa perplexidade indica previsão mais confiável do próximo token, mas **não garante** que a resposta seja factual, útil ou segura. |

> **CUIDADO:** BLEU e ROUGE medem **sobreposição textual**, não compreensão ou qualidade. Um resumo pode ser excelente semanticamente mas receber ROUGE baixo por usar sinônimos. Essas métricas são úteis como indicadores rápidos, não como avaliação definitiva.

### Avaliação humana

- Julgamento subjetivo por humanos qualificados
- **Quando usar:** qualidade geral, criatividade, tom, factualidade, adequação ao contexto
- **Vantagem:** captura nuances que métricas automáticas não detectam
- **Desvantagem:** custosa, lenta, difícil de escalar, pode ter variância entre avaliadores
- **Amazon Bedrock Model Evaluation** suporta configuração de avaliações humanas

### LLM-as-a-judge (LLM como avaliador)

**Conceito:** Usar um LLM (geralmente mais capaz) para avaliar os outputs de outro modelo, seguindo critérios definidos.

**Quando usar:**
- Quando avaliação humana é custosa demais para a escala necessária
- Para triagem rápida antes de avaliação humana
- Para avaliar dimensões como coerência, relevância, completude

**Vantagens:**
- Escalável e rápido
- Pode seguir rubrics/critérios definidos consistentemente
- Disponível via Amazon Bedrock Model Evaluation

**Limitações:**
- O LLM avaliador também pode errar ou ter vieses
- Não substitui completamente avaliação humana para decisões críticas
- Qualidade depende dos critérios/prompts fornecidos ao avaliador

> **DICA PARA A PROVA:** Se a questão menciona "avaliar outputs de FM em escala" ou "avaliação automatizada de qualidade", LLM-as-a-judge é uma opção relevante. Se menciona "avaliar criatividade" ou "julgamento subjetivo", avaliação humana.

### Métricas de alinhamento e segurança

| Métrica | O que avalia |
|---------|-------------|
| **Factuality (Factualidade)** | O output contém informações factualmente corretas? |
| **Groundedness (Fundamentação)** | O output é fiel ao contexto/fontes fornecidas? (especialmente relevante para RAG) |
| **Safety (Segurança)** | O output é livre de conteúdo nocivo, tóxico ou inapropriado? |

- **Factuality** e **Groundedness** são relacionados mas distintos: factuality é sobre verdade objetiva; groundedness é sobre fidelidade às fontes fornecidas ao modelo
- **Safety** avalia toxicidade, parcialidade, conteúdo nocivo — ferramentas como Guardrails for Amazon Bedrock ajudam a implementar isso

> **CUIDADO:** Groundedness alto não garante factuality — se as fontes fornecidas contêm erros, o modelo pode ser "grounded" nas fontes mas factualmente incorreto.

---

## Métricas de Negócio para Aplicações de IA

A AIF-C01 exige reconhecer que métricas técnicas não são suficientes — o impacto de negócio precisa ser avaliado.

| Métrica | O que mede | Exemplo |
|---------|-----------|---------|
| **Taxa de conclusão de tarefas** | % de tarefas que o sistema completa com sucesso | Chatbot resolve 75% das consultas sem escalar para humano |
| **Satisfação do usuário** | Percepção de valor pelo usuário final | NPS, CSAT, ratings |
| **Custo por interação** | Quanto custa cada inferência/interação com o modelo | $0.02 por consulta ao chatbot |
| **Produtividade** | Ganho de eficiência vs. processo anterior | Redução de 40% no tempo de análise de documentos |
| **Engajamento** | Adoção e uso recorrente | Usuários ativos diários, taxa de retenção |

---

## Avaliação de Aplicações de FM (RAG, Agents, Workflows)

Avaliar uma **aplicação** construída com FM é diferente de avaliar o **modelo isolado**. A aplicação tem múltiplos componentes que afetam o resultado final.

### Diferença: avaliar modelo vs. avaliar aplicação

| Aspecto | Avaliação do modelo | Avaliação da aplicação |
|---------|--------------------|-----------------------|
| Escopo | Output do modelo dado um input | Resultado end-to-end para o usuário |
| Inclui | Qualidade da geração | Retrieval + geração + pós-processamento + UX |
| Métricas | BLEU, ROUGE, BERTScore | Task completion, user satisfaction, latência total |
| Ferramenta | Amazon Bedrock Model Evaluation | Testes end-to-end, feedback do usuário, logging |

### Abordagens de avaliação

| Abordagem | Descrição | Quando usar |
|-----------|-----------|-------------|
| **Benchmarks** | Conjuntos de dados padronizados para comparar modelos | Selecionar qual FM usar |
| **Avaliação humana** | Humanos avaliam outputs em cenários reais | Validar qualidade antes de ir a produção |
| **Amazon Bedrock Model Evaluation** | Serviço gerenciado para avaliar FMs com métricas automáticas e humanas | Comparar modelos no Bedrock, avaliar com critérios customizados |
| **Avaliação end-to-end** | Testar a aplicação completa (RAG, agent) em cenários de uso real | Validar que a aplicação resolve o problema de negócio |

> **DICA PARA A PROVA:** Se a questão pergunta "como avaliar a performance de uma aplicação RAG", a resposta envolve métricas como groundedness (o output é fiel aos documentos recuperados?), task completion e user satisfaction — não apenas BLEU/ROUGE do modelo isolado.

---

## Resumo para a Prova

| Situação na questão | Métrica/abordagem correta |
|--------------------|--------------------------|
| "Detectar todos os casos positivos" | Recall |
| "Evitar falsos alarmes" | Precisão |
| "Balancear detecção e alarmes" | F1 Score |
| "Dados desbalanceados" | F1 ou AUC-ROC (não acurácia) |
| "Comparar modelos" | AUC-ROC |
| "Prever valor numérico, penalizar erros grandes" | RMSE |
| "Avaliar qualidade de resumo" | ROUGE (com limitações) |
| "Avaliar qualidade de tradução" | BLEU (com limitações) |
| "Avaliar se output é fiel às fontes" | Groundedness |
| "Avaliar se output é factualmente correto" | Factuality |
| "Avaliar outputs de FM em escala" | LLM-as-a-judge |
| "Avaliar criatividade/subjetividade" | Avaliação humana |
| "Medir impacto de negócio da IA" | Taxa de conclusão, satisfação, ROI, custo/interação |
| "Avaliar aplicação RAG end-to-end" | Groundedness + task completion + user satisfaction |

---
