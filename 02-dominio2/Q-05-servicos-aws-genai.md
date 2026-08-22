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

Uma empresa de e-commerce está expandindo internacionalmente e precisa de um modelo que garanta privacidade dos dados dos clientes franceses sob o GDPR. A equipe está avaliando o Amazon Bedrock. Qual garantia o Bedrock oferece que é relevante para essa preocupação?

A) O Bedrock processa dados exclusivamente em data centers europeus quando solicitado  
B) Os dados de entrada e saída NÃO são usados para treinar os modelos base e permanecem isolados na conta/região do cliente  
C) O Bedrock anonimiza automaticamente todos os dados de cidadãos europeus  
D) O Bedrock não armazena nenhum dado em nenhuma circunstância, eliminando riscos de compliance  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Os dados de entrada e saída NÃO são usados para treinar os modelos base e permanecem isolados na conta/região do cliente**

✅ **Por que B está correta:** O Bedrock garante isolamento de dados: prompts e respostas permanecem privados na conta/região do cliente e não são compartilhados com provedores de modelos para treinamento. Isso atende requisitos de privacidade como GDPR quanto ao uso secundário de dados.

❌ **Por que as outras estão erradas:**
- **A)** Bedrock está disponível em regiões europeias, mas o cliente que escolhe a região — não é automático "quando solicitado". Além disso, a garantia de privacidade vai além de localização geográfica.
- **C)** Bedrock NÃO anonimiza automaticamente — o cliente deve implementar proteção de PII via Guardrails.
- **D)** Bedrock pode armazenar logs se o Model Invocation Logging estiver habilitado (opt-in). A afirmação "nenhum dado em nenhuma circunstância" é falsa.

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



---

### Questão 7

Uma empresa de consultoria quer que seus analistas possam fazer perguntas sobre relatórios financeiros internos usando linguagem natural. Os documentos estão no SharePoint e S3, e as respostas devem respeitar permissões de acesso existentes (cada analista só vê documentos de seus clientes). A equipe NÃO quer construir infraestrutura de busca customizada. Qual serviço é MAIS adequado?

A) Amazon Kendra para busca empresarial com conectores nativos  
B) Amazon Q Business com integração a SharePoint e S3 respeitando ACLs  
C) Amazon Bedrock Knowledge Bases com vector database  
D) Amazon Comprehend para análise dos documentos  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Amazon Q Business com integração a SharePoint e S3 respeitando ACLs**

✅ **Por que B está correta:** Q Business é o assistente empresarial GenAI que integra nativamente com SharePoint, S3, Confluence etc., E respeita permissões de acesso (ACLs) existentes. Combina busca + geração + controle de acesso sem infraestrutura customizada.

❌ **Por que as outras estão erradas:**
- **A)** Kendra faz busca inteligente, mas Q Business é mais completo (GenAI + integração + ACLs nativos). Kendra requer mais configuração para controle de acesso.
- **C)** Knowledge Bases requer configurar vector database, chunking e indexação — mais infraestrutura que Q Business pré-integrado.
- **D)** Comprehend analisa texto (sentimento, entidades) — não responde perguntas sobre documentos.

</details>

---

### Questão 8

Uma empresa está prototipando um assistente de vendas com IA generativa. O VP de vendas quer testar conceitos RAPIDAMENTE antes de aprovar orçamento. A equipe precisa de algo que NÃO requer conta AWS, é gratuito, e permite experimentar com prompts em minutos. Qual opção atende TODOS esses requisitos?

A) Amazon Bedrock com free tier  
B) PartyRock — playground gratuito sem conta AWS  
C) Amazon SageMaker Studio Lab — ambiente gratuito de ML  
D) Amazon Q Developer — assistente de código gratuito  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) PartyRock — playground gratuito sem conta AWS**

✅ **Por que B está correta:** PartyRock é gratuito, não requer conta AWS, não requer cartão de crédito, e permite criar apps de IA generativa em minutos com interface visual. Perfeito para prototipagem rápida e validação de conceito.

❌ **Por que as outras estão erradas:**
- **A)** Bedrock requer conta AWS + tem custo por token (mesmo com free tier, precisa de conta).
- **C)** Studio Lab é para ML com notebooks Jupyter — requer cadastro e é focado em ciência de dados, não prototipagem de chatbot.
- **D)** Q Developer é para geração de código em IDE — não é playground para testar chatbots de vendas.

</details>

---

### Questão 9

Uma empresa implantou um chatbot com Amazon Bedrock que processa dados de clientes (nomes, CPF, emails). O DPO (Data Protection Officer) exige que: (1) dados pessoais sejam mascarados nas respostas do chatbot, (2) o chatbot nunca discuta preços de concorrentes, e (3) respostas com conteúdo ofensivo sejam bloqueadas. Qual funcionalidade do Bedrock implementa TODOS esses requisitos?

A) Bedrock Knowledge Bases com filtros de busca  
B) Bedrock Guardrails com PII filters, denied topics e content filters  
C) Bedrock Model Evaluation para detectar problemas  
D) Bedrock Fine-tuning para ensinar o modelo a filtrar  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Bedrock Guardrails com PII filters, denied topics e content filters**

✅ **Por que B está correta:** Guardrails oferece TODOS os três: PII filters (mascarar CPF/email), denied topics (bloquear discussão de concorrentes), content filters (bloquear conteúdo ofensivo). É a camada de proteção unificada do Bedrock.

❌ **Por que as outras estão erradas:**
- **A)** Knowledge Bases buscam informação — não filtram PII, tópicos ou conteúdo.
- **C)** Model Evaluation compara modelos em métricas — não filtra em tempo real.
- **D)** Fine-tuning pode melhorar comportamento, mas não garante bloqueio absoluto — Guardrails é enforcement.

</details>

---

### Questão 10

Uma empresa migrou de um chatbot tradicional (baseado em regras) para IA generativa com Amazon Bedrock. O custo mensal aumentou significativamente. O arquiteto quer reduzir custos SEM degradar qualidade para a maioria das interações. Qual estratégia é MAIS eficaz?

A) Trocar para o modelo mais barato disponível, independente da qualidade  
B) Usar modelo menor para tarefas simples (FAQ) e modelo maior apenas para tarefas complexas (raciocínio)  
C) Reduzir a context window de todos os modelos  
D) Desabilitar logging para economizar armazenamento  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Usar modelo menor para tarefas simples e modelo maior apenas para tarefas complexas**

✅ **Por que B está correta:** Model routing — classificar a complexidade da tarefa e direcionar para o modelo adequado. FAQs simples funcionam com modelos menores/baratos (Titan, Haiku). Raciocínio complexo justifica modelos maiores/caros. Reduz custo médio sem degradar qualidade onde importa.

❌ **Por que as outras estão erradas:**
- **A)** Modelo mais barato pode degradar qualidade em tarefas complexas — viola o requisito "sem degradar".
- **C)** Context window é propriedade fixa do modelo — não é configurável para "reduzir custo".
- **D)** Logging tem custo mínimo comparado a tokens — economia negligível. Além disso, pode violar compliance.

</details>
