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



---

### Questão 6

Uma empresa de mídia usa Amazon Bedrock para gerar resumos de artigos. Em horário de pico (8h-18h), processam 500 requisições/segundo com latência máxima de 200ms. Fora do pico, o volume cai para 5 requisições/segundo. A equipe quer otimizar custo mantendo a latência em pico. Qual modelo de preços do Bedrock é MAIS adequado?

A) On-demand para todo o tráfego — paga por token sem compromisso  
B) Provisioned Throughput para o horário de pico + on-demand fora do pico  
C) Batch inference para processar todos os artigos de uma vez  
D) Provisioned Throughput 24/7 para garantir latência consistente  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Provisioned Throughput para pico + on-demand fora do pico**

✅ **Por que B está correta:** Provisioned Throughput garante capacidade reservada (latência consistente em pico). On-demand fora do pico evita pagar por capacidade ociosa. Combinação otimiza custo vs performance.

❌ **Por que as outras estão erradas:**
- **A)** On-demand em 500 req/s pode ter throttling e latência variável — não garante 200ms sob carga.
- **C)** Batch é para processamento assíncrono — não atende latência de 200ms em tempo real.
- **D)** Provisioned 24/7 paga por capacidade que fica 80% ociosa (5 req/s quando cai) — desperdício.

</details>

---

### Questão 7

Uma equipe de produto quer testar 3 Foundation Models diferentes no Bedrock para seu caso de uso de sumarização de contratos antes de escolher qual usar em produção. Precisam avaliar: qualidade do resumo, toxicidade da saída, e latência. Qual funcionalidade do Bedrock permite essa comparação sistematizada?

A) Bedrock Guardrails — aplicar filtros e comparar comportamento  
B) Bedrock Model Evaluation — comparar modelos com métricas automáticas e/ou humanas  
C) Bedrock Knowledge Bases — testar com diferentes fontes de dados  
D) Bedrock Agents — orquestrar chamadas aos 3 modelos  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Bedrock Model Evaluation — comparar modelos com métricas automáticas e/ou humanas**

✅ **Por que B está correta:** Model Evaluation permite: selecionar múltiplos modelos, definir métricas (ROUGE para qualidade, toxicidade, latência), usar datasets customizados, e gerar relatório comparativo. Projetado exatamente para seleção de modelo.

❌ **Por que as outras estão erradas:**
- **A)** Guardrails filtram conteúdo em produção — não comparam performance de modelos.
- **C)** Knowledge Bases implementam RAG — não comparam modelos entre si.
- **D)** Agents executam ações — não avaliam nem comparam modelos.

</details>

---

### Questão 8

Uma empresa de healthcare quer usar Bedrock para responder perguntas médicas dos pacientes baseando-se APENAS em protocolos aprovados pela equipe médica. Os protocolos são atualizados mensalmente. Qual arquitetura no Bedrock atende esse requisito SEM re-treinar o modelo?

A) Fine-tuning mensal com os novos protocolos  
B) Knowledge Bases conectada ao S3 com os protocolos + re-indexação mensal  
C) Guardrails para bloquear respostas não-médicas  
D) Agents para chamar APIs do sistema hospitalar  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Knowledge Bases conectada ao S3 com os protocolos + re-indexação mensal**

✅ **Por que B está correta:** Knowledge Bases implementa RAG gerenciado. Protocolos no S3 são indexados (chunking + embeddings). Quando atualizados, basta re-indexar — o modelo base permanece o mesmo. Respostas são ancoradas nos documentos reais.

❌ **Por que as outras estão erradas:**
- **A)** Fine-tuning mensal é caro, demorado, e não garante que o modelo use APENAS os protocolos (pode alucinar).
- **C)** Guardrails filtram conteúdo indesejado mas não trazem informação dos protocolos para as respostas.
- **D)** Agents executam ações em sistemas — o cenário é busca de informação, não execução de ações.

</details>

---

### Questão 9

Um cliente do Bedrock pergunta: "Se eu fizer fine-tuning de um modelo no Bedrock, outra empresa que use o mesmo modelo base terá acesso ao meu modelo customizado?" Qual é a resposta CORRETA sobre isolamento de dados no Bedrock?

A) Sim — modelos fine-tuned são compartilhados para melhorar o modelo base  
B) Não — o modelo customizado é privado, armazenado na sua conta, e inacessível para outros clientes ou o provedor do modelo  
C) Depende — modelos open-weight são compartilhados, proprietários são isolados  
D) Não existe fine-tuning no Bedrock — apenas prompt engineering  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Não — o modelo customizado é privado e inacessível para outros**

✅ **Por que B está correta:** No Bedrock, modelos fine-tuned são artefatos privados da conta do cliente. Dados de treino, modelos resultantes e logs permanecem isolados. Provedores de modelo NÃO têm acesso à conta de deployment do Bedrock.

❌ **Por que as outras estão erradas:**
- **A)** Bedrock garante que dados e modelos customizados NUNCA são compartilhados com outros clientes ou provedores.
- **C)** O isolamento é o mesmo independente do modelo base (open-weight ou proprietário) — dentro do Bedrock, é sempre privado.
- **D)** Bedrock OFERECE fine-tuning — é uma funcionalidade disponível para múltiplos modelos.

</details>

---

### Questão 10

Uma empresa está planejando custos para sua aplicação de IA generativa no Bedrock. A aplicação recebe perguntas curtas (~50 tokens) e gera respostas longas (~500 tokens). O gerente financeiro pergunta como a cobrança funciona. Qual afirmação é CORRETA sobre o modelo de preços on-demand do Bedrock?

A) Cobra um preço fixo por requisição independente do tamanho  
B) Cobra separadamente por tokens de entrada e tokens de saída, com saída geralmente mais cara  
C) Cobra apenas por tokens de entrada — a saída é gratuita  
D) Cobra por minuto de processamento do modelo  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Cobra separadamente por tokens de entrada e saída, com saída geralmente mais cara**

✅ **Por que B está correta:** Bedrock on-demand cobra por 1.000 tokens de input E por 1.000 tokens de output separadamente. Tokens de output são tipicamente 3-5x mais caros que input. No cenário, 500 tokens de saída custam significativamente mais que 50 de entrada.

❌ **Por que as outras estão erradas:**
- **A)** NÃO é preço fixo por requisição — varia com volume de tokens (uma resposta de 50 tokens custa menos que uma de 500).
- **C)** Saída NÃO é gratuita — é a parte MAIS cara da cobrança.
- **D)** NÃO cobra por minuto — cobra por token processado (model on-demand) ou por hora de capacidade reservada (Provisioned).

</details>
