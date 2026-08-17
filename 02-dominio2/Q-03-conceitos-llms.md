# Questões — Conceitos de LLMs

---

### Questão 1

Um desenvolvedor quer que um LLM gere respostas factualmente precisas e consistentes para perguntas sobre políticas da empresa. Qual configuração de temperature é mais adequada?

A) Temperature = 1.0 (alta criatividade)  
B) Temperature = 0 ou próximo de 0 (determinístico)  
C) Temperature = 2.0 (máxima diversidade)  
D) Temperature não afeta a qualidade das respostas  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Temperature = 0 ou próximo de 0 (determinístico)**

✅ **Por que B está correta:** Temperature baixa faz o modelo escolher os tokens mais prováveis, gerando respostas mais previsíveis, focadas e factualmente consistentes — ideal para informações de políticas.

❌ **Por que as outras estão erradas:**
- **A)** Temperature alta aumenta aleatoriedade — respostas criativas mas menos confiáveis.
- **C)** Temperature 2.0 geraria respostas quase aleatórias — péssimo para informação factual.
- **D)** Temperature afeta diretamente a consistência e diversidade das respostas.

</details>

---

### Questão 2

O que é "alucinação" (hallucination) no contexto de LLMs?

A) Quando o modelo demora muito para responder  
B) Quando o modelo gera informação que parece plausível mas é factualmente incorreta  
C) Quando o modelo não consegue processar a entrada  
D) Quando o modelo repete a mesma resposta múltiplas vezes  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Quando o modelo gera informação que parece plausível mas é factualmente incorreta**

✅ **Por que B está correta:** Alucinação é quando o LLM "inventa" informação com confiança — parece verdadeiro, o texto é fluente, mas o conteúdo é falso (dados, referências, funcionalidades inexistentes).

❌ **Por que as outras estão erradas:**
- **A)** Latência alta é um problema de performance, não alucinação.
- **C)** Não processar entrada é um erro técnico, não alucinação.
- **D)** Repetição é um problema de geração diferente (repetition/loop).

</details>

---

### Questão 3

Uma empresa está criando um chatbot e quer reduzir as alucinações do LLM. Qual abordagem é MAIS eficaz?

A) Aumentar a temperature  
B) Usar RAG para ancorar respostas em documentos reais  
C) Usar um modelo maior  
D) Aumentar o max_tokens  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Usar RAG para ancorar respostas em documentos reais**

✅ **Por que B está correta:** RAG busca informação factual de fontes reais e a injeta no contexto, forçando o modelo a basear suas respostas em dados verificáveis — a técnica mais eficaz contra alucinações.

❌ **Por que as outras estão erradas:**
- **A)** Aumentar temperature PIORA alucinações (mais aleatoriedade).
- **C)** Modelos maiores podem ser mais capazes, mas ainda alucinam sem grounding.
- **D)** Max tokens afeta comprimento, não factualidade.

</details>

---

### Questão 4

O que é a "context window" de um LLM?

A) A interface visual onde o usuário digita  
B) O número máximo de tokens que o modelo pode processar em uma única interação  
C) O período de tempo que o modelo fica disponível  
D) A quantidade de modelos que podem rodar simultaneamente  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) O número máximo de tokens que o modelo pode processar em uma única interação**

✅ **Por que B está correta:** Context window define o limite total de tokens (entrada + saída) que o modelo processa por vez. Se exceder, o conteúdo é truncado ou gera erro.

❌ **Por que as outras estão erradas:**
- **A)** Isso é a interface de usuário (UI), não context window.
- **C)** Context window é sobre capacidade de processamento, não disponibilidade temporal.
- **D)** Isso se refere a capacidade de infraestrutura, não ao modelo em si.

</details>

---

### Questão 5

Embeddings são usados em qual cenário?

A) Para criptografar dados sensíveis  
B) Para representar texto como vetores numéricos e permitir busca semântica  
C) Para comprimir modelos e reduzir custo  
D) Para traduzir texto entre idiomas  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Para representar texto como vetores numéricos e permitir busca semântica**

✅ **Por que B está correta:** Embeddings convertem texto em vetores numéricos onde textos com significado similar ficam próximos no espaço vetorial. Isso permite busca por similaridade semântica — base do RAG.

❌ **Por que as outras estão erradas:**
- **A)** Embeddings não são criptografia — são representações, não proteção.
- **C)** Embeddings não comprimem modelos — são usados para representar dados.
- **D)** Tradução é feita pelo modelo (encoder-decoder), não pelos embeddings isoladamente.

</details>

---

### Questão 6

Um modelo de IA generativa está gerando respostas muito longas e o custo está alto. Qual parâmetro deve ser ajustado para controlar isso?

A) Temperature  
B) Top-p  
C) Max tokens  
D) Context window  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: C) Max tokens**

✅ **Por que C está correta:** Max tokens define o limite máximo de tokens na resposta gerada. Reduzir esse valor limita o comprimento da saída, reduzindo custo (paga-se por token de saída).

❌ **Por que as outras estão erradas:**
- **A)** Temperature controla criatividade/aleatoriedade, não comprimento.
- **B)** Top-p controla diversidade do vocabulário, não comprimento.
- **D)** Context window é fixo do modelo — não é configurável por request.

</details>

