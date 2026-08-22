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



---

### Questão 6

Uma empresa implementou RAG com Bedrock Knowledge Bases. O retrieval está retornando chunks relevantes, mas as respostas do FM ainda contêm informações que NÃO estão nos chunks retornados. A equipe suspeita que o modelo está "complementando" com conhecimento do pré-treinamento. Qual é a solução MAIS eficaz?

A) Aumentar o número de chunks retornados de 3 para 20  
B) Adicionar instrução no prompt: "Responda APENAS com base nos documentos fornecidos. Não use conhecimento externo."  
C) Trocar para um modelo maior que alucine menos  
D) Reduzir a temperature para 0 para eliminar aleatoriedade  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Adicionar instrução restritiva no prompt**

✅ **Por que B está correta:** Quando o retrieval funciona mas o FM "complementa", o problema é a instrução. Um prompt restritivo ("use APENAS o contexto fornecido") direciona o modelo a não usar conhecimento do pré-treinamento. É a combinação RAG + prompt engineering.

❌ **Por que as outras estão erradas:**
- **A)** Mais chunks não resolvem o modelo inventando ALÉM dos chunks — podem até confundir mais com informação irrelevante.
- **C)** Modelos maiores podem alucinar igualmente — tamanho não resolve uso indevido de conhecimento prévio.
- **D)** Temperature 0 torna respostas determinísticas mas o modelo AINDA usa conhecimento do pré-treinamento se não for instruído a restringir.

</details>

---

### Questão 7

Uma empresa está configurando RAG e precisa decidir o tamanho dos chunks para indexação. Seus documentos são manuais técnicos com seções de 2-3 parágrafos que cobrem um tópico completo cada. A equipe quer maximizar a relevância do contexto retornado. Qual estratégia de chunking é MAIS adequada?

A) Chunks de 50 tokens — máxima granularidade para precisão  
B) Chunks alinhados com as seções temáticas dos documentos (~300-500 tokens) preservando contexto completo  
C) Um único chunk por documento inteiro (~10.000 tokens) para não perder contexto  
D) Chunks fixos de 100 tokens com 0% de overlap  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Chunks alinhados com seções temáticas preservando contexto completo**

✅ **Por que B está correta:** Seções de 2-3 parágrafos que cobrem um tópico completo são unidades naturais de informação. Chunking por seção preserva contexto semântico — o FM recebe informação completa e coerente sobre o tema buscado.

❌ **Por que as outras estão erradas:**
- **A)** 50 tokens fragmentam informação — um chunk não terá contexto suficiente para uma resposta útil.
- **C)** 10.000 tokens por documento excede o que pode ser injetado no prompt (e a maioria será irrelevante para a query).
- **D)** 100 tokens sem overlap cria fronteiras artificiais que cortam frases no meio — perda de coerência.

</details>

---

### Questão 8

Uma empresa está usando Bedrock Knowledge Bases com OpenSearch Serverless como vector database. O custo de busca está alto. Qual fator MAIS afeta o custo do componente de retrieval no RAG?

A) O tamanho do Foundation Model usado para geração  
B) O número e dimensionalidade dos embeddings armazenados no vector database  
C) A temperature configurada para geração  
D) O número de tokens na resposta final  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) O número e dimensionalidade dos embeddings no vector database**

✅ **Por que B está correta:** O custo de retrieval depende do volume de dados indexados (número de chunks) e da dimensão dos vetores (1024, 1536, etc.). Mais chunks = mais storage + mais compute para busca por similaridade. Embeddings de alta dimensão também custam mais.

❌ **Por que as outras estão erradas:**
- **A)** Tamanho do FM afeta custo de GERAÇÃO, não de retrieval (busca).
- **C)** Temperature é parâmetro de inferência do FM — não afeta custo de busca vetorial.
- **D)** Tokens de resposta afetam custo de GERAÇÃO no FM, não retrieval no vector DB.

</details>

---

### Questão 9

Uma empresa farmacêutica quer implementar RAG para que pesquisadores consultem papers científicos. Os papers contêm fórmulas químicas, tabelas de dados e figuras. A equipe nota que o RAG retorna chunks irrelevantes quando pesquisadores buscam informações de tabelas. Qual é a causa MAIS provável?

A) O modelo de embeddings é muito pequeno  
B) Tabelas e dados estruturados são mal representados pelo chunking/embedding de texto padrão  
C) A context window do FM é insuficiente  
D) O vector database não suporta dados científicos  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Tabelas e dados estruturados são mal representados pelo chunking/embedding de texto padrão**

✅ **Por que B está correta:** Embeddings de texto são otimizados para prosa/parágrafos. Tabelas, quando convertidas em texto plano, perdem estrutura (linhas, colunas, relações entre dados) — os embeddings resultantes não capturam o significado tabular. Solução: pré-processamento especializado para tabelas.

❌ **Por que as outras estão erradas:**
- **A)** Modelo de embeddings maior ajuda em geral, mas não resolve o problema fundamental de representação de tabelas.
- **C)** Context window suficiente não ajuda se os chunks errados são recuperados.
- **D)** Vector databases são agnósticos ao tipo de dado — o problema está na qualidade dos embeddings, não no banco.

</details>

---

### Questão 10

Uma empresa implementou RAG e mede a qualidade com duas métricas: "retrieval accuracy" (chunks corretos retornados) e "generation quality" (resposta final útil). O retrieval accuracy é 95% mas generation quality é apenas 60%. Qual componente precisa ser melhorado PRIMEIRO?

A) O modelo de embeddings — para melhorar retrieval  
B) O prompt do FM e/ou o FM usado — para melhorar como o modelo utiliza o contexto retornado  
C) O vector database — para busca mais rápida  
D) O tamanho dos chunks — para melhorar retrieval  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) O prompt do FM e/ou o FM usado — para melhorar geração a partir do contexto**

✅ **Por que B está correta:** Retrieval está bom (95%) — os documentos certos chegam ao FM. O problema é na GERAÇÃO: o FM não está usando bem o contexto. Solução: melhorar o prompt (instruções mais claras) ou trocar para um FM mais capaz de síntese/compreensão.

❌ **Por que as outras estão erradas:**
- **A)** Embeddings/retrieval já está em 95% — não é o gargalo.
- **C)** Velocidade do vector DB não afeta qualidade das respostas.
- **D)** Tamanho dos chunks afeta retrieval — que já está bom.

</details>
