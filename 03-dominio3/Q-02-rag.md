# Questões — RAG (Retrieval-Augmented Generation)

---

### Questão 1

Uma empresa quer que seu chatbot responda perguntas sobre manuais de produtos que são atualizados mensalmente, sem re-treinar o modelo. Qual abordagem é mais adequada?

A) Fine-tuning mensal  
B) RAG com Knowledge Base conectada aos manuais  
C) Aumentar a context window do modelo  
D) Prompt engineering com zero-shot  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) RAG com Knowledge Base conectada aos manuais**

✅ **Por que B está correta:** RAG busca informação atualizada dos manuais no momento da query, sem necessidade de re-treinar o modelo. Quando os manuais são atualizados, basta re-indexar — o modelo continua o mesmo.

❌ **Por que as outras estão erradas:**
- **A)** Fine-tuning mensal seria caro, demorado e desnecessário.
- **C)** Context window é propriedade fixa do modelo — não é algo que "aumenta" para resolver o problema.
- **D)** Zero-shot sem contexto dos manuais geraria respostas baseadas apenas no conhecimento do pré-treinamento — possivelmente desatualizadas ou incorretas.

</details>

---

### Questão 2

Qual é a sequência correta do fluxo RAG quando um usuário faz uma pergunta?

A) Gerar resposta → Buscar documentos → Exibir ao usuário  
B) Converter query em embedding → Buscar chunks similares → Injetar contexto → FM gera resposta  
C) Fine-tunar modelo → Gerar resposta → Verificar factualidade  
D) Tokenizar pergunta → Treinar modelo → Gerar resposta  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Converter query em embedding → Buscar chunks similares → Injetar contexto → FM gera resposta**

✅ **Por que B está correta:** O fluxo RAG é: (1) query vira embedding, (2) busca por similaridade no vector database retorna chunks relevantes, (3) chunks são injetados como contexto no prompt, (4) FM gera resposta baseada no contexto.

❌ **Por que as outras estão erradas:**
- **A)** Gerar antes de buscar = sem contexto = alucinação. A busca vem ANTES da geração.
- **C)** RAG não envolve fine-tuning — é justamente uma alternativa a ele.
- **D)** RAG não treina o modelo — usa o modelo existente com contexto injetado.

</details>

---

### Questão 3

O que é um "vector database" no contexto de RAG?

A) Um banco de dados relacional para armazenar documentos  
B) Um banco que armazena embeddings e permite busca por similaridade semântica  
C) Um cache de respostas do modelo  
D) Um banco de dados de logs de inferência  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Um banco que armazena embeddings e permite busca por similaridade semântica**

✅ **Por que B está correta:** Vector databases armazenam vetores (embeddings) e realizam busca por nearest neighbors — encontram os vetores mais similares ao vetor da query. É o componente central da busca semântica no RAG.

❌ **Por que as outras estão erradas:**
- **A)** Bancos relacionais armazenam dados estruturados com SQL, não são otimizados para busca vetorial.
- **C)** Cache de respostas é uma otimização separada, não é o vector database.
- **D)** Logs de inferência ficam em CloudWatch/S3, não em vector databases.

</details>

---

### Questão 4

Uma empresa implementou RAG mas as respostas do chatbot ainda não são precisas — muitas vezes o contexto retornado não é relevante. Qual componente deve ser otimizado?

A) O Foundation Model usado  
B) A estratégia de chunking e a qualidade dos embeddings  
C) A temperature do modelo  
D) O número de tokens na resposta  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) A estratégia de chunking e a qualidade dos embeddings**

✅ **Por que B está correta:** Se o contexto retornado não é relevante, o problema está na retrieval (busca). Chunking inadequado (pedaços muito grandes ou pequenos) e embeddings de baixa qualidade resultam em busca imprecisa.

❌ **Por que as outras estão erradas:**
- **A)** Se o contexto certo chegar ao FM, ele gera boa resposta. O problema está na busca, não no FM.
- **C)** Temperature afeta criatividade da geração, não a qualidade da busca.
- **D)** Max tokens afeta comprimento, não relevância do contexto.

</details>

---

### Questão 5

Qual é a principal vantagem do RAG sobre fine-tuning para manter informação atualizada?

A) RAG é mais barato que fine-tuning em todos os cenários  
B) RAG permite atualizar a base de dados sem re-treinar o modelo  
C) RAG gera respostas mais criativas que fine-tuning  
D) RAG funciona sem nenhuma infraestrutura adicional  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) RAG permite atualizar a base de dados sem re-treinar o modelo**

✅ **Por que B está correta:** Com RAG, basta atualizar os documentos na fonte (S3) e re-indexar. O modelo permanece o mesmo — a informação atualizada é injetada em tempo de query. Com fine-tuning, seria necessário re-treinar a cada atualização.

❌ **Por que as outras estão erradas:**
- **A)** RAG requer infraestrutura de busca (vector DB) — nem sempre é mais barato.
- **C)** Criatividade depende do modelo e temperature, não do RAG.
- **D)** RAG REQUER infraestrutura adicional (vector database, indexação, embeddings).

</details>

