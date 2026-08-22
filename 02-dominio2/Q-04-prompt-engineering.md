# Questões — Prompt Engineering

---

### Questão 1

Um desenvolvedor quer que o LLM classifique tickets de suporte em categorias. Ele fornece 3 exemplos de tickets já classificados antes de pedir a classificação do novo ticket. Qual técnica está usando?

A) Zero-shot  
B) Few-shot  
C) Chain-of-thought  
D) Fine-tuning  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Few-shot**

✅ **Por que B está correta:** Few-shot = fornecer alguns exemplos (shots) antes da tarefa real para guiar o modelo no formato e comportamento desejado. 3 exemplos de tickets classificados = few-shot learning.

❌ **Por que as outras estão erradas:**
- **A)** Zero-shot não usa exemplos — faz a pergunta diretamente.
- **C)** Chain-of-thought pede raciocínio passo a passo, não exemplos de classificação.
- **D)** Fine-tuning modifica os pesos do modelo — requer treinamento, não apenas exemplos no prompt.

</details>

---

### Questão 2

Uma equipe quer que o LLM resolva problemas matemáticos complexos com maior acurácia. Qual técnica de prompt engineering é mais adequada?

A) Zero-shot  
B) Few-shot  
C) Chain-of-thought (raciocínio passo a passo)  
D) Reduzir a temperature para 0  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: C) Chain-of-thought (raciocínio passo a passo)**

✅ **Por que C está correta:** Chain-of-thought instrui o modelo a "pensar passo a passo", decompondo problemas complexos. Estudos mostram melhora significativa em tarefas de raciocínio e matemática.

❌ **Por que as outras estão erradas:**
- **A)** Zero-shot sem guia de raciocínio tende a pular etapas em problemas complexos.
- **B)** Few-shot ajuda no formato, mas não garante raciocínio correto em problemas novos.
- **D)** Temperature baixa torna a resposta mais consistente, mas não melhora a capacidade de raciocínio.

</details>

---

### Questão 3

Qual é o propósito de um "system prompt" em uma interação com LLM?

A) Criptografar a comunicação entre usuário e modelo  
B) Definir o comportamento, regras e persona que o modelo deve seguir  
C) Treinar o modelo com novos dados  
D) Limitar o número de tokens na resposta  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Definir o comportamento, regras e persona que o modelo deve seguir**

✅ **Por que B está correta:** System prompt é uma instrução que define como o modelo deve se comportar em todas as respostas — persona, regras, limitações, idioma, formato, etc.

❌ **Por que as outras estão erradas:**
- **A)** Criptografia é função de TLS/HTTPS, não do system prompt.
- **C)** System prompt não treina o modelo — apenas direciona durante a inferência.
- **D)** Limitar tokens é função do parâmetro max_tokens, não do system prompt.

</details>

---

### Questão 4

Uma empresa de telecomunicações está construindo um chatbot para atendimento ao cliente. As respostas devem ser baseadas EXCLUSIVAMENTE nos documentos de FAQ e políticas da empresa — o chatbot nunca deve gerar informações que não estejam nesses documentos. A equipe testou apenas prompt engineering, mas o modelo ainda inventa informações quando não encontra a resposta. Qual combinação resolve o problema?

A) Fine-tuning do modelo com os documentos de FAQ para internalizar todo o conhecimento  
B) RAG para buscar documentos relevantes + prompt engineering com instrução restritiva ("responda APENAS com base no contexto fornecido")  
C) Aumentar a context window usando um modelo maior para caber todos os documentos  
D) Few-shot prompting com exemplos de respostas corretas para cada categoria de pergunta  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) RAG para buscar documentos relevantes + prompt engineering com instrução restritiva**

✅ **Por que B está correta:** RAG busca a informação relevante dos documentos e injeta no contexto. Combinado com prompt restritivo ("responda APENAS com base no contexto fornecido; se não encontrar, diga que não tem essa informação"), minimiza alucinações e garante respostas fundamentadas nos documentos reais.

❌ **Por que as outras estão erradas:**
- **A)** Fine-tuning muda o estilo do modelo mas NÃO previne alucinações — o modelo pode gerar informação plausível que não existe nos docs. Além disso, quando os FAQs mudam, seria necessário re-treinar.
- **C)** Mesmo com context window enorme, colocar TODOS os documentos no prompt é impraticável e caro. RAG busca apenas o trecho relevante — muito mais eficiente.
- **D)** Few-shot ajuda no formato de resposta, mas não resolve o problema central: o modelo não tem acesso aos documentos corretos e inventa quando não sabe.

</details>

---

### Questão 5

Qual é a ordem recomendada para tentar melhorar a qualidade das respostas de um FM?

A) Fine-tuning → RAG → Prompt Engineering  
B) Prompt Engineering → RAG → Fine-tuning  
C) RAG → Fine-tuning → Prompt Engineering  
D) Fine-tuning → Prompt Engineering → RAG  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Prompt Engineering → RAG → Fine-tuning**

✅ **Por que B está correta:** Sempre começar com prompt engineering (mais barato e rápido). Se não basta, adicionar RAG (dados atualizados sem re-treinar). Só fazer fine-tuning como último recurso (caro e demorado).

❌ **Por que as outras estão erradas:**
- **A)** Começar por fine-tuning é custoso e desnecessário na maioria dos casos.
- **C)** RAG antes de PE pula a solução mais simples.
- **D)** Fine-tuning primeiro é o caminho mais caro e lento.

</details>



---

### Questão 6

Uma equipe está usando um LLM para responder perguntas de compliance regulatório. O modelo precisa seguir regras ESTRITAS: nunca dar conselho legal, sempre citar a norma aplicável, e responder em formato bullet point. Essas regras devem se aplicar a TODAS as interações sem que o usuário precise repeti-las. Qual mecanismo é MAIS adequado?

A) Few-shot prompting — fornecer exemplos de respostas corretas em cada mensagem  
B) System prompt — definir comportamento, regras e formato que persistem em todas as interações  
C) Fine-tuning — re-treinar o modelo com exemplos de compliance  
D) RAG — buscar as regras em uma Knowledge Base a cada pergunta  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) System prompt — definir comportamento, regras e formato que persistem em todas as interações**

✅ **Por que B está correta:** System prompt define regras "globais" que se aplicam a toda interação sem repetição. Ideal para restrições constantes (formato, persona, limitações). Persiste durante toda a sessão.

❌ **Por que as outras estão erradas:**
- **A)** Few-shot ocupa context window em cada mensagem e precisa ser repetido — ineficiente para regras permanentes.
- **C)** Fine-tuning é overkill para definir formato/regras — e modificar regras exigiria re-treinar.
- **D)** RAG busca informação variável — regras fixas não precisam ser "buscadas" a cada interação.

</details>

---

### Questão 7

Um desenvolvedor criou um prompt: "Classifique o seguinte ticket de suporte como: Técnico, Financeiro ou Geral. Ticket: {input}". O modelo classifica corretamente 70% das vezes. A equipe quer melhorar para >90% SEM fine-tuning. Qual técnica é o próximo passo MAIS eficaz?

A) Adicionar exemplos de cada categoria no prompt (few-shot)  
B) Aumentar a temperature para explorar mais opções  
C) Reduzir max_tokens para forçar respostas curtas  
D) Remover as categorias e deixar o modelo decidir livremente  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: A) Adicionar exemplos de cada categoria no prompt (few-shot)**

✅ **Por que A está correta:** O prompt atual é zero-shot (sem exemplos). Adicionar 2-3 exemplos de cada categoria (few-shot) mostra ao modelo exatamente o padrão esperado — melhora significativa em classificação sem custo de fine-tuning.

❌ **Por que as outras estão erradas:**
- **B)** Temperature alta AUMENTA variação — piora consistência de classificação.
- **C)** Max tokens afeta comprimento, não acurácia de classificação.
- **D)** Remover categorias tornaria o output imprevisível — impossível de integrar em sistemas.

</details>

---

### Questão 8

Uma empresa construiu um assistente de IA generativa para suporte técnico. O assistente deve SEMPRE basear suas respostas em documentação oficial do produto. A equipe implementou RAG mas o modelo ainda às vezes "complementa" com informação que não está nos documentos recuperados. Qual instrução no prompt é MAIS eficaz para eliminar esse comportamento?

A) "Responda de forma completa e detalhada"  
B) "Baseie sua resposta EXCLUSIVAMENTE no contexto fornecido. Se a informação não estiver no contexto, responda: 'Não encontrei essa informação na documentação.'"  
C) "Use seu conhecimento geral para complementar quando necessário"  
D) "Aumente o nível de detalhe das respostas"  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Instrução restritiva com fallback explícito**

✅ **Por que B está correta:** Instruir o modelo a usar APENAS o contexto fornecido + definir o que fazer quando não encontra (fallback explícito) reduz dramaticamente alucinações. O modelo precisa de permissão explícita para dizer "não sei".

❌ **Por que as outras estão erradas:**
- **A)** "Completa e detalhada" ENCORAJA o modelo a inventar para preencher lacunas.
- **C)** "Complementar com conhecimento geral" é exatamente o comportamento indesejado (fonte de alucinações).
- **D)** "Mais detalhe" pode gerar mais conteúdo inventado para parecer completo.

</details>

---

### Questão 9

Uma equipe está otimizando prompts para um chatbot de vendas. Testam três versões: (1) zero-shot simples, (2) few-shot com 3 exemplos, (3) few-shot com 10 exemplos. A versão 3 gera respostas melhores mas cada chamada custa 3x mais que a versão 2. Qual é o PRINCIPAL fator que explica o aumento de custo?

A) Mais exemplos requerem um modelo maior para processar  
B) Mais exemplos = mais tokens de entrada = mais custo por chamada (Bedrock cobra por token)  
C) Few-shot com muitos exemplos ativa fine-tuning automático que é cobrado separadamente  
D) A temperature precisa ser maior com mais exemplos, gerando mais tokens de saída  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Mais exemplos = mais tokens de entrada = mais custo por chamada**

✅ **Por que B está correta:** No Bedrock (pay-per-token), cada token de entrada é cobrado. 10 exemplos vs 3 exemplos = significativamente mais tokens no prompt = custo proporcional. É o trade-off direto entre qualidade e custo em prompt engineering.

❌ **Por que as outras estão erradas:**
- **A)** O mesmo modelo processa ambas as versões — não muda de modelo por tamanho do prompt.
- **C)** Few-shot NÃO é fine-tuning — exemplos ficam no prompt e são processados em tempo de inferência. Não há treino.
- **D)** Temperature não muda automaticamente com exemplos — é um parâmetro independente.

</details>

---

### Questão 10

Uma empresa precisa melhorar as respostas de um LLM que erra em problemas de lógica e cálculos. A equipe testou: (1) zero-shot → 40% correto, (2) few-shot → 55% correto, (3) chain-of-thought → 85% correto. Por que chain-of-thought é MAIS eficaz para tarefas de raciocínio?

A) Chain-of-thought usa um modelo maior internamente  
B) Chain-of-thought força o modelo a decompor o problema em etapas intermediárias, reduzindo erros de lógica  
C) Chain-of-thought acessa a internet para verificar cálculos  
D) Chain-of-thought ativa fine-tuning em tempo real  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Chain-of-thought força decomposição em etapas intermediárias, reduzindo erros de lógica**

✅ **Por que B está correta:** Chain-of-thought ("pense passo a passo") obriga o modelo a gerar raciocínio explícito antes da resposta final. Cada etapa intermediária serve como "scaffold" para a próxima, reduzindo saltos lógicos que causam erros.

❌ **Por que as outras estão erradas:**
- **A)** O mesmo modelo é usado — chain-of-thought é técnica de prompt, não troca de modelo.
- **C)** LLMs não acessam internet — processam apenas o que está no prompt/contexto.
- **D)** Nenhum fine-tuning ocorre — é puramente uma técnica de inferência via prompt.

</details>
