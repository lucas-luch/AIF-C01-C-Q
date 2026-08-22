# Questões — Agents

---

### Questão 1

Qual é a principal diferença entre um chatbot com RAG e um Agent com Bedrock Agents?

A) RAG é mais inteligente que Agents  
B) RAG busca informação; Agents buscam informação E executam ações em sistemas  
C) Agents não podem usar Knowledge Bases  
D) RAG requer Lambda; Agents não  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) RAG busca informação; Agents buscam informação E executam ações em sistemas**

✅ **Por que B está correta:** RAG é read-only — busca contexto e gera resposta textual. Agents vão além: podem raciocinar, decidir ações e executá-las (chamar APIs, atualizar dados, disparar processos).

❌ **Por que as outras estão erradas:**
- **A)** "Inteligente" não é a distinção — a diferença é a capacidade de executar ações.
- **C)** Agents PODEM usar Knowledge Bases como fonte de informação.
- **D)** É o inverso — Agents usam Lambda para executar ações; RAG não precisa de Lambda.

</details>

---

### Questão 2

Um cliente pede ao chatbot: "Cancele meu pedido #5678 e me envie um email de confirmação". Qual arquitetura é necessária para atender esse pedido?

A) RAG com Knowledge Base de pedidos  
B) Prompt engineering com few-shot  
C) Bedrock Agent com action groups para cancelamento e envio de email  
D) Fine-tuning do modelo com exemplos de cancelamento  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: C) Bedrock Agent com action groups para cancelamento e envio de email**

✅ **Por que C está correta:** O cenário requer EXECUTAR ações (cancelar pedido + enviar email) — isso é exatamente o que Agents fazem. O Agent raciocina sobre os passos necessários e chama as action groups (Lambda functions) para cada ação.

❌ **Por que as outras estão erradas:**
- **A)** RAG só busca informação — não pode cancelar pedidos nem enviar emails.
- **B)** Prompt engineering gera texto — não executa ações em sistemas.
- **D)** Fine-tuning muda o estilo do modelo — não dá capacidade de executar ações.

</details>

---

### Questão 3

Quais componentes são necessários para um Bedrock Agent funcionar? **(Selecione DUAS)**

A) Um Foundation Model para raciocínio  
B) Um vector database obrigatório  
C) Action Groups com Lambda functions para executar ações  
D) Fine-tuning obrigatório do modelo  
E) Amazon Rekognition para processamento visual  

<details>
<summary>🔍 Ver resposta</summary>

**Respostas: A e C**

✅ **Por que A está correta:** O FM é o "cérebro" do Agent — raciocina sobre o que fazer, interpreta a instrução do usuário e decide quais ações executar.

✅ **Por que C está correta:** Action Groups definem as ações que o Agent pode executar. Cada action é implementada como Lambda function que o Agent pode invocar.

❌ **Por que as outras estão erradas:**
- **B)** Vector database é opcional (usado se o Agent tiver Knowledge Base), não obrigatório.
- **D)** Fine-tuning é opcional — Agents funcionam com modelos base.
- **E)** Rekognition é para visão computacional — não é componente de Agents.

</details>

---

### Questão 4

O que é o pattern "ReAct" usado por Bedrock Agents?

A) Um framework de interface de usuário  
B) Um ciclo de Reason (raciocinar) → Act (agir) → Observe (observar) repetido até completar a tarefa  
C) Uma forma de treinar modelos mais rapidamente  
D) Um tipo de embedding  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Um ciclo de Reason (raciocinar) → Act (agir) → Observe (observar) repetido até completar a tarefa**

✅ **Por que B está correta:** ReAct é o pattern onde o Agent: (1) raciocina sobre o que fazer, (2) executa uma ação, (3) observa o resultado, e repete até resolver o problema completo. É o loop central do comportamento de Agents.

❌ **Por que as outras estão erradas:**
- **A)** Não é UI framework — é um padrão de raciocínio para LLMs.
- **C)** Não é sobre treinamento — é sobre inferência e execução.
- **D)** Embeddings são vetores numéricos — nada a ver com ReAct.

</details>

---

### Questão 5

Em qual cenário um Agent é necessário em vez de apenas RAG?

A) Responder perguntas sobre documentos internos  
B) Processar uma devolução de produto consultando o sistema e atualizando o status  
C) Resumir um relatório longo  
D) Traduzir um documento para outro idioma  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Processar uma devolução de produto consultando o sistema e atualizando o status**

✅ **Por que B está correta:** Processar devolução requer AÇÕES: consultar sistema (read) + atualizar status (write). Isso necessita de um Agent com action groups — RAG sozinho só lê informação.

❌ **Por que as outras estão erradas:**
- **A)** Responder perguntas sobre docs = RAG é suficiente (apenas leitura).
- **C)** Resumir relatório = prompt engineering ou RAG (apenas geração de texto).
- **D)** Tradução = FM com prompt adequado (apenas geração de texto).

</details>



---

### Questão 6

Um hotel quer um assistente de IA que possa: verificar disponibilidade de quartos no sistema de reservas, criar reservas, processar pagamentos e enviar confirmação por email — tudo em uma única conversa com o hóspede. Qual arquitetura no Amazon Bedrock é necessária?

A) Knowledge Base com documentos sobre quartos e preços  
B) Bedrock Agent com action groups para cada operação (reservas, pagamentos, email)  
C) Fine-tuning do modelo com exemplos de reservas anteriores  
D) Guardrails configuradas para bloquear informação financeira  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Bedrock Agent com action groups para cada operação**

✅ **Por que B está correta:** O cenário requer EXECUTAR múltiplas ações em sistemas externos (verificar disponibilidade, criar reserva, processar pagamento, enviar email). Isso exige um Agent que raciocine sobre os passos e chame action groups (Lambda) para cada operação.

❌ **Por que as outras estão erradas:**
- **A)** Knowledge Base apenas LÊ informação — não pode criar reservas, processar pagamentos ou enviar emails.
- **C)** Fine-tuning muda estilo de geração — não dá capacidade de executar ações em sistemas.
- **D)** Guardrails filtram conteúdo — não executam ações nem integram com sistemas.

</details>

---

### Questão 7

Uma empresa implementou um Bedrock Agent para processamento de pedidos. O Agent deve: (1) consultar status do pedido, (2) aplicar desconto se elegível, (3) confirmar com o cliente antes de finalizar. O Agent executou os passos 1 e 2 automaticamente mas não pediu confirmação no passo 3. Qual funcionalidade resolve esse problema?

A) Aumentar a temperature para gerar respostas mais variadas  
B) Configurar "return control" para pausar e solicitar confirmação humana antes de ações críticas  
C) Adicionar mais exemplos de confirmação no prompt  
D) Usar Guardrails para bloquear ações sem confirmação  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Configurar "return control" para pausar e solicitar confirmação antes de ações críticas**

✅ **Por que B está correta:** Bedrock Agents suporta "return control" — pausa a execução antes de uma ação específica e retorna controle ao aplicativo/usuário para confirmação. Ideal para ações irreversíveis (pagamentos, cancelamentos).

❌ **Por que as outras estão erradas:**
- **A)** Temperature afeta criatividade de texto, não fluxo de execução de ações.
- **C)** Exemplos no prompt podem ajudar na geração de texto, mas não pausam execução de action groups.
- **D)** Guardrails filtram conteúdo (texto), não controlam fluxo de execução de ações.

</details>

---

### Questão 8

Um arquiteto está decidindo entre implementar RAG (Knowledge Bases) ou um Agent para um assistente de suporte técnico. O assistente deve: responder perguntas usando manuais internos E abrir tickets no Jira quando o problema não pode ser resolvido em texto. Qual é a arquitetura CORRETA?

A) Apenas Knowledge Base — busca informação e gera respostas  
B) Apenas Agent sem Knowledge Base — executa ações direto  
C) Agent com Knowledge Base integrada — busca informação dos manuais E executa ação de abrir ticket  
D) Fine-tuning — ensinar o modelo a abrir tickets  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: C) Agent com Knowledge Base integrada — busca informação E executa ações**

✅ **Por que C está correta:** O cenário requer AMBOS: buscar informação (RAG via Knowledge Base) E executar ações (abrir ticket no Jira via action group). Agents podem integrar Knowledge Bases como fonte de informação enquanto mantêm capacidade de ação.

❌ **Por que as outras estão erradas:**
- **A)** Knowledge Base sozinha só LÊ informação — não pode abrir tickets no Jira.
- **B)** Agent sem Knowledge Base poderia abrir tickets mas não teria acesso aos manuais para responder perguntas técnicas.
- **D)** Fine-tuning não dá capacidade de integração com sistemas externos.

</details>

---

### Questão 9

Uma empresa quer que seu Agent pesquise voos, compare preços e reserve o mais barato automaticamente. O Agent usa o padrão ReAct. Qual sequência descreve CORRETAMENTE um ciclo do ReAct neste cenário?

A) Reserve o voo → Pesquise opções → Compare preços  
B) Raciocine sobre o pedido → Execute ação (pesquisar voos) → Observe resultado → Raciocine novamente → Execute (reservar)  
C) Treine o modelo → Faça fine-tuning → Deploy em produção  
D) Gere todas as respostas possíveis → Selecione a melhor → Apresente ao usuário  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Raciocine → Execute ação → Observe resultado → Raciocine → Execute**

✅ **Por que B está correta:** ReAct = Reason + Act + Observe em ciclo. (1) Raciocina: "preciso pesquisar voos para essa data", (2) Age: chama API de busca de voos, (3) Observa: "encontrei 5 opções", (4) Raciocina: "o mais barato é o voo X, vou reservar", (5) Age: chama API de reserva. Loop até completar.

❌ **Por que as outras estão erradas:**
- **A)** Reservar ANTES de pesquisar é a ordem inversa — sem lógica.
- **C)** Treinar/fine-tuning é fase de desenvolvimento, não execução em tempo real de um Agent.
- **D)** Isso descreve beam search (decodificação), não o padrão ReAct de raciocínio e ação.

</details>

---

### Questão 10

Uma empresa quer que seu Agent tenha acesso a ferramentas externas (APIs de clima, calculadoras, bancos de dados) usando um protocolo padronizado e aberto. Qual protocolo permite que o Agent se conecte a múltiplas ferramentas de diferentes provedores de forma interoperável?

A) REST API — padrão web para comunicação entre serviços  
B) MCP (Model Context Protocol) — protocolo aberto para conectar LLMs a ferramentas e fontes de dados  
C) GraphQL — linguagem de consulta para APIs  
D) gRPC — protocolo de chamada remota de procedimento  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) MCP (Model Context Protocol) — protocolo aberto para conectar LLMs a ferramentas e fontes de dados**

✅ **Por que B está correta:** MCP é um protocolo aberto (não exclusivo de nenhum provedor) que padroniza como LLMs/Agents se conectam a ferramentas, APIs e fontes de dados. Permite interoperabilidade entre diferentes provedores de LLM e ferramentas.

❌ **Por que as outras estão erradas:**
- **A)** REST é um estilo arquitetural genérico — não é específico para conexão LLM↔ferramentas nem padroniza o formato de interação.
- **C)** GraphQL é para consultar dados de APIs — não padroniza integração LLM↔ferramentas.
- **D)** gRPC é para comunicação eficiente entre serviços — genérico, não específico para LLMs.

</details>
