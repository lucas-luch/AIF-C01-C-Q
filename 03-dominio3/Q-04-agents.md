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

