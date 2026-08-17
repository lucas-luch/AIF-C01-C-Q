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

Uma empresa está construindo um chatbot de FAQ. As respostas devem ser baseadas APENAS em documentos fornecidos, sem informação inventada. Qual combinação é mais adequada?

A) Fine-tuning do modelo  
B) RAG + prompt engineering com instrução restritiva  
C) Aumentar a temperature para respostas mais completas  
D) Zero-shot sem contexto adicional  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) RAG + prompt engineering com instrução restritiva**

✅ **Por que B está correta:** RAG busca a informação relevante dos documentos e injeta no contexto. Combinado com prompt engineering ("responda APENAS com base no contexto fornecido"), minimiza alucinações e garante respostas fundamentadas.

❌ **Por que as outras estão erradas:**
- **A)** Fine-tuning muda o estilo, mas não previne alucinações nem traz dados atualizados.
- **C)** Temperature alta aumenta aleatoriedade — piora o problema.
- **D)** Zero-shot sem contexto forçaria o modelo a usar apenas conhecimento interno — alucinações prováveis.

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

