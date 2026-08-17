# Questões — Amazon Bedrock

---

### Questão 1

Uma empresa precisa que seu chatbot bloqueie respostas sobre tópicos financeiros e mascare dados pessoais (CPF, email) nas respostas. Qual funcionalidade do Bedrock deve usar?

A) Knowledge Bases  
B) Agents  
C) Guardrails  
D) Model Evaluation  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: C) Guardrails**

✅ **Por que C está correta:** Guardrails permite configurar denied topics (bloquear temas financeiros) e PII filters (mascarar/bloquear CPF, email) — exatamente as duas necessidades do cenário.

❌ **Por que as outras estão erradas:**
- **A)** Knowledge Bases são para RAG (buscar informação), não filtrar conteúdo.
- **B)** Agents executam ações em sistemas, não filtram conteúdo.
- **D)** Model Evaluation compara modelos, não filtra outputs.

</details>

---

### Questão 2

Uma empresa quer ajustar um Foundation Model para gerar relatórios no formato e terminologia específicos do setor jurídico. Qual funcionalidade do Bedrock é mais adequada?

A) Guardrails  
B) Knowledge Bases  
C) Fine-tuning  
D) Provisioned Throughput  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: C) Fine-tuning**

✅ **Por que C está correta:** Fine-tuning ajusta os pesos do modelo para adotar estilo, formato e terminologia específicos — ideal quando o modelo precisa consistentemente gerar outputs em formato jurídico com vocabulário especializado.

❌ **Por que as outras estão erradas:**
- **A)** Guardrails filtram conteúdo, não mudam o estilo de geração.
- **B)** Knowledge Bases trazem informação factual, não mudam formato/terminologia.
- **D)** Provisioned Throughput é sobre capacidade de inferência, não customização.

</details>

---

### Questão 3

Qual é o modelo de precificação padrão do Amazon Bedrock para inferência?

A) Paga por hora de uso do endpoint  
B) Paga por token processado (entrada e saída)  
C) Assinatura mensal fixa  
D) Gratuito para todos os modelos  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Paga por token processado (entrada e saída)**

✅ **Por que B está correta:** O modelo on-demand do Bedrock cobra por token de entrada e por token de saída separadamente. Tokens de saída geralmente são mais caros que de entrada.

❌ **Por que as outras estão erradas:**
- **A)** Não é por hora — é por token (a menos que use Provisioned Throughput).
- **C)** Não existe assinatura mensal fixa para Bedrock.
- **D)** Bedrock não é gratuito (PartyRock é o playground gratuito).

</details>

---

### Questão 4

Uma empresa precisa comparar qual Foundation Model funciona melhor para seu caso de uso específico de resumo de contratos. Qual funcionalidade do Bedrock deve usar?

A) Guardrails  
B) Model Evaluation  
C) Agents  
D) Provisioned Throughput  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Model Evaluation**

✅ **Por que B está correta:** Model Evaluation permite comparar múltiplos modelos no Bedrock usando métricas automáticas e/ou avaliação humana com datasets customizados — exatamente para decidir qual modelo é melhor para seu caso.

❌ **Por que as outras estão erradas:**
- **A)** Guardrails filtram conteúdo, não comparam modelos.
- **C)** Agents executam ações, não avaliam modelos.
- **D)** Provisioned Throughput é sobre capacidade, não avaliação.

</details>

---

### Questão 5 (Múltipla Resposta)

Quais são funcionalidades disponíveis no Amazon Bedrock? **(Selecione DUAS)**

A) Treinamento de modelos ML tabulares com AutoML  
B) Knowledge Bases para implementar RAG gerenciado  
C) Análise de sentimento pré-treinada  
D) Agents que podem executar ações chamando APIs  
E) Processamento de big data com Spark  

<details>
<summary>🔍 Ver resposta</summary>

**Respostas: B e D**

✅ **Por que B está correta:** Bedrock Knowledge Bases implementam RAG completo: indexação de documentos, embeddings, vector search e geração com contexto.

✅ **Por que D está correta:** Bedrock Agents combinam FM + Action Groups (Lambda) para raciocinar e executar ações em sistemas reais.

❌ **Por que as outras estão erradas:**
- **A)** AutoML tabular é SageMaker Autopilot, não Bedrock.
- **C)** Análise de sentimento pré-treinada é Amazon Comprehend, não Bedrock.
- **E)** Big data com Spark é Amazon EMR, não Bedrock.

</details>

