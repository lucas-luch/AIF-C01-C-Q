# Questões — Serviços AWS de IA Generativa

---

### Questão 1

Uma empresa quer construir uma aplicação de IA generativa em produção usando múltiplos Foundation Models sem gerenciar infraestrutura. Qual serviço AWS deve usar?

A) Amazon SageMaker  
B) Amazon Bedrock  
C) PartyRock  
D) Amazon Comprehend  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Amazon Bedrock**

✅ **Por que B está correta:** Amazon Bedrock oferece acesso serverless a múltiplos Foundation Models (Claude, Titan, Llama, etc.) via API, sem necessidade de gerenciar infraestrutura — ideal para produção.

❌ **Por que as outras estão erradas:**
- **A)** SageMaker requer gerenciar endpoints e infraestrutura. É para ML customizado, não acesso serverless a FMs.
- **C)** PartyRock é playground gratuito para experimentação — não é para produção.
- **D)** Comprehend é NLP pré-treinado (sentimento, entidades), não IA generativa.

</details>

---

### Questão 2

Um estudante quer experimentar criação de aplicativos com IA generativa sem custo e sem conta AWS. Qual serviço é adequado?

A) Amazon Bedrock  
B) Amazon SageMaker Canvas  
C) PartyRock  
D) Amazon Q  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: C) PartyRock**

✅ **Por que C está correta:** PartyRock é um playground gratuito da AWS onde qualquer pessoa pode criar apps com IA generativa sem conta AWS, sem cartão de crédito e sem código — perfeito para aprendizado e experimentação.

❌ **Por que as outras estão erradas:**
- **A)** Bedrock requer conta AWS e tem custo por token.
- **B)** SageMaker Canvas requer conta AWS e é para ML tabular, não GenAI.
- **D)** Amazon Q requer acesso empresarial ou conta AWS.

</details>

---

### Questão 3

Qual funcionalidade do Amazon Bedrock implementa RAG de forma gerenciada?

A) Bedrock Agents  
B) Bedrock Guardrails  
C) Bedrock Knowledge Bases  
D) Bedrock Fine-tuning  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: C) Bedrock Knowledge Bases**

✅ **Por que C está correta:** Knowledge Bases implementam RAG gerenciado — processam documentos (chunking + embeddings), armazenam em vector database, e na hora da query buscam contexto relevante para o FM gerar respostas fundamentadas.

❌ **Por que as outras estão erradas:**
- **A)** Agents executam ações (APIs, Lambda) — podem USAR Knowledge Bases mas são mais que RAG.
- **B)** Guardrails filtram conteúdo (segurança) — não buscam informação.
- **D)** Fine-tuning ajusta pesos do modelo — diferente de buscar informação externa.

</details>

---

### Questão 4

Uma empresa quer que seus funcionários possam fazer perguntas em linguagem natural sobre documentos internos (SharePoint, Confluence) com controle de acesso. Qual serviço é mais adequado?

A) Amazon Kendra  
B) Amazon Q Business  
C) PartyRock  
D) Amazon Comprehend  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Amazon Q Business**

✅ **Por que B está correta:** Amazon Q Business é um assistente GenAI empresarial que integra com fontes de dados corporativas (SharePoint, Confluence, S3, Slack, etc.) e respeita permissões de acesso existentes — exatamente o cenário descrito.

❌ **Por que as outras estão erradas:**
- **A)** Kendra é busca empresarial inteligente, mas Q Business é mais completo com GenAI + integração nativa com múltiplas fontes + controle de acesso.
- **C)** PartyRock é playground sem integração empresarial.
- **D)** Comprehend analisa texto (sentimento, entidades), não responde perguntas sobre documentos.

</details>

---

### Questão 5

Qual é a principal garantia de privacidade do Amazon Bedrock em relação aos dados dos clientes?

A) Dados são armazenados em servidores on-premises do cliente  
B) Dados de entrada e saída NÃO são usados para treinar os modelos base  
C) Todos os dados são automaticamente anonimizados  
D) Bedrock não armazena nenhum dado em nenhuma circunstância  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Dados de entrada e saída NÃO são usados para treinar os modelos base**

✅ **Por que B está correta:** O Bedrock garante que seus prompts e respostas não são usados para treinar ou melhorar os modelos base de nenhum provedor. Seus dados permanecem privados na sua conta/região.

❌ **Por que as outras estão erradas:**
- **A)** Bedrock é um serviço cloud — dados ficam na AWS, não on-premises.
- **C)** Bedrock não anonimiza automaticamente — você precisa implementar (Guardrails PII filter).
- **D)** Bedrock pode armazenar logs se habilitado (Model Invocation Logging é opt-in).

</details>

---

### Questão 6

Qual serviço AWS é um assistente de IA generativa para desenvolvedores que ajuda com geração, explicação e debugging de código?

A) Amazon CodeGuru  
B) Amazon Q Developer  
C) AWS Cloud9  
D) Amazon Bedrock  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Amazon Q Developer**

✅ **Por que B está correta:** Amazon Q Developer (anteriormente CodeWhisperer) é o assistente de código GenAI da AWS integrado em IDEs. Gera código, explica, faz debugging, sugere correções e pode transformar/modernizar aplicações.

❌ **Por que as outras estão erradas:**
- **A)** CodeGuru faz code review e profiling de performance, mas não é assistente GenAI de código.
- **C)** Cloud9 é uma IDE na nuvem — ambiente de desenvolvimento, não assistente de código.
- **D)** Bedrock é a plataforma de FMs — Q Developer é construído sobre ele para o caso de uso específico de código.

</details>

