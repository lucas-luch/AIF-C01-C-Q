# Questões — Casos de Uso e Otimização

---

### Questão 1

Uma empresa quer minimizar custos de inferência para uma tarefa simples de classificação de sentimento (positivo/negativo). Qual estratégia é mais eficaz?

A) Usar o maior modelo disponível para máxima acurácia  
B) Usar um modelo menor que atenda os requisitos de qualidade  
C) Usar Provisioned Throughput com o modelo mais caro  
D) Aumentar max_tokens para respostas mais detalhadas  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Usar um modelo menor que atenda os requisitos de qualidade**

✅ **Por que B está correta:** Para tarefas simples como classificação binária de sentimento, modelos menores são suficientes e custam significativamente menos por token. A regra é: usar o menor modelo que atenda os requisitos.

❌ **Por que as outras estão erradas:**
- **A)** Modelo maior = mais caro por token. Overkill para tarefa simples.
- **C)** Provisioned Throughput com modelo caro seria o oposto de minimizar custo.
- **D)** Mais tokens = mais custo. Para sentimento, a resposta é curta ("positivo" ou "negativo").

</details>

---

### Questão 2

Qual métrica é mais adequada para avaliar a qualidade de um modelo que gera traduções de texto?

A) ROUGE  
B) BLEU  
C) F1 Score  
D) RMSE  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) BLEU**

✅ **Por que B está correta:** BLEU (Bilingual Evaluation Understudy) foi projetada especificamente para avaliar qualidade de tradução automática, medindo a precisão de n-grams comparados a uma tradução de referência humana.

❌ **Por que as outras estão erradas:**
- **A)** ROUGE é para resumos (recall-oriented), não tradução.
- **C)** F1 Score é para classificação, não geração de texto.
- **D)** RMSE é para regressão numérica.

</details>

---

### Questão 3

Uma empresa precisa processar 500.000 documentos para extrair resumos. Não há necessidade de resposta em tempo real. Qual abordagem otimiza custo?

A) Real-time endpoint no Bedrock  
B) Batch inference  
C) Provisioned Throughput  
D) Multiple concurrent API calls  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Batch inference**

✅ **Por que B está correta:** Batch inference processa grandes volumes de dados de uma vez com desconto sobre o preço on-demand. Sem necessidade de real-time, batch é a opção mais custo-efetiva.

❌ **Por que as outras estão erradas:**
- **A)** Real-time = mais caro e desnecessário quando não precisa de resposta imediata.
- **C)** Provisioned Throughput é para workloads constantes em tempo real, não lotes únicos.
- **D)** Chamadas concorrentes on-demand seriam mais caras que batch.

</details>

---

### Questão 4

Uma empresa está avaliando dois modelos no Bedrock para seu chatbot. Quer medir tanto métricas automáticas quanto a percepção de qualidade dos usuários internos. Qual abordagem de avaliação é mais completa?

A) Apenas ROUGE e BLEU  
B) Apenas avaliação humana  
C) Bedrock Model Evaluation com métricas automáticas + avaliação humana  
D) Apenas monitorar latência em produção  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: C) Bedrock Model Evaluation com métricas automáticas + avaliação humana**

✅ **Por que C está correta:** Model Evaluation do Bedrock suporta ambos: métricas automáticas (ROUGE, BLEU, BERTScore) para avaliação objetiva + avaliação humana para qualidade subjetiva. A combinação é a mais completa.

❌ **Por que as outras estão erradas:**
- **A)** Métricas automáticas sozinhas não capturam qualidade subjetiva (tom, utilidade, naturalidade).
- **B)** Avaliação humana sozinha é cara e não escala — combinar com automática é melhor.
- **D)** Latência mede performance, não qualidade das respostas.

</details>

---

### Questão 5

Uma empresa quer usar IA generativa para gerar código a partir de descrições em linguagem natural, explicar código existente e sugerir correções. Qual serviço AWS é mais adequado?

A) Amazon Bedrock com Claude  
B) Amazon Q Developer  
C) Amazon SageMaker  
D) AWS Lambda  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Amazon Q Developer**

✅ **Por que B está correta:** Amazon Q Developer é o assistente de código GenAI da AWS projetado especificamente para: gerar código, explicar código, sugerir correções, fazer debugging e transformar aplicações. Integrado diretamente em IDEs.

❌ **Por que as outras estão erradas:**
- **A)** Bedrock com Claude pode gerar código, mas Q Developer é o serviço dedicado com integração IDE.
- **C)** SageMaker é para construir modelos ML, não assistência de código.
- **D)** Lambda executa código, não gera ou explica.

</details>

