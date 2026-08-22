# Questões — Arquitetura Transformer

---

### Questão 1

Uma startup está escolhendo uma arquitetura de modelo para processar documentos longos de forma eficiente. A equipe de ML reporta que o modelo atual baseado em RNNs demora 12 horas para treinar e não consegue capturar relações entre palavras distantes no texto. Qual é a principal vantagem de migrar para uma arquitetura Transformer?

A) Transformers consomem menos memória GPU, reduzindo custos de treinamento  
B) Transformers processam tokens em paralelo e capturam dependências de longa distância via self-attention  
C) Transformers eliminam a necessidade de grandes datasets para pré-treinamento  
D) Transformers usam convoluções (CNN) internamente para capturar padrões locais de forma mais eficiente  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Transformers processam tokens em paralelo e capturam dependências de longa distância via self-attention**

✅ **Por que B está correta:** O cenário descreve dois problemas de RNNs: (1) treinamento lento (porque processam sequencialmente) e (2) perda de contexto em textos longos. Transformers resolvem ambos: paralelização massiva acelera o treino, e self-attention permite que qualquer token "olhe" diretamente para qualquer outro, independente da distância.

❌ **Por que as outras estão erradas:**
- **A)** Transformers geralmente usam MAIS memória (atenção é O(n²) no comprimento da sequência) — o trade-off é mais memória por mais velocidade.
- **C)** Transformers requerem datasets enormes para pré-treinamento — essa é uma de suas desvantagens.
- **D)** Transformers NÃO usam convoluções internamente — usam mecanismo de atenção. CNNs são uma arquitetura diferente.

</details>

---

### Questão 2

Uma equipe de ciência de dados está explicando a um gerente de produto por que o chatbot da empresa consegue entender que "banco" significa "instituição financeira" em uma frase e "assento" em outra. Qual mecanismo da arquitetura Transformer permite essa compreensão contextual?

A) Positional encoding, que identifica o significado de cada palavra pelo idioma detectado  
B) Self-attention, que calcula a relevância de cada token em relação a todos os outros na sequência  
C) Tokenização, que divide palavras ambíguas em subpalavras com significado fixo  
D) Backpropagation, que ajusta os significados das palavras durante a inferência  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Self-attention, que calcula a relevância de cada token em relação a todos os outros na sequência**

✅ **Por que B está correta:** Self-attention permite que cada token "olhe" para todos os outros e calcule pesos de relevância. Isso significa que o significado de "banco" é determinado pelo contexto ao redor (palavras como "conta corrente" vs "sentar") — exatamente como funciona a desambiguação.

❌ **Por que as outras estão erradas:**
- **A)** Positional encoding adiciona informação de ORDEM (posição 1, 2, 3...), não de significado semântico ou idioma.
- **C)** Tokenização é um pré-processamento mecânico — divide texto em tokens sem interpretar significado contextual.
- **D)** Backpropagation é usado no TREINAMENTO para ajustar pesos, não durante a inferência (uso).

</details>

---

### Questão 3

Uma empresa está desenvolvendo um assistente de código que deve gerar funções Python a partir de descrições em linguagem natural, token por token. A equipe precisa escolher a variante de Transformer mais adequada. Considerando que modelos como GPT, Claude e Llama utilizam geração autoregressiva, qual arquitetura é mais apropriada?

A) Encoder-only, que compreende o contexto completo antes de gerar qualquer saída  
B) Decoder-only, que gera texto autoregressivamente token por token  
C) Encoder-Decoder, que primeiro codifica a entrada completa e depois decodifica a saída  
D) RNN bidirecional, que processa a sequência nos dois sentidos para geração  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Decoder-only, que gera texto autoregressivamente token por token**

✅ **Por que B está correta:** O cenário pede geração autoregressiva (token por token) e cita GPT, Claude e Llama — todos são decoder-only. Essa arquitetura gera o próximo token baseado nos tokens anteriores, ideal para geração de código e texto.

❌ **Por que as outras estão erradas:**
- **A)** Encoder-only (como BERT) é otimizado para compreensão (classificação, NER, embeddings), não para geração de texto.
- **C)** Encoder-Decoder (como T5) é usado para tarefas de transformação (tradução, resumo) onde entrada e saída são distintas — funciona, mas não é a arquitetura dos modelos citados.
- **D)** RNNs bidirecionais são arquiteturas anteriores ao Transformer — lentas e não usadas em LLMs modernos.

</details>

---

### Questão 4

Uma equipe de desenvolvimento está estimando os custos de inferência no Amazon Bedrock. O gerente de projeto nota que a mesma pergunta escrita em inglês ("What is S3?") e em alemão ("Was ist S3?") gera custos ligeiramente diferentes, apesar de terem o mesmo significado. Qual conceito explica essa diferença de custo?

A) Self-attention, que requer mais cálculos para idiomas com gramática complexa  
B) Tokenização, que divide textos em unidades de tamanhos diferentes dependendo do idioma e vocabulário  
C) Positional encoding, que usa vetores maiores para idiomas com palavras mais longas  
D) Temperature, que varia automaticamente baseada no idioma detectado  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Tokenização, que divide textos em unidades de tamanhos diferentes dependendo do idioma e vocabulário**

✅ **Por que B está correta:** Tokenização converte texto em tokens (as unidades de processamento e cobrança). Idiomas diferentes produzem quantidades diferentes de tokens para o mesmo significado (alemão tende a gerar mais tokens que inglês). Como Bedrock cobra por token, o custo varia.

❌ **Por que as outras estão erradas:**
- **A)** Self-attention não "custa mais" por gramática — processa o mesmo número de tokens independente do idioma.
- **C)** Positional encoding tem tamanho fixo por token — não varia com o tamanho das palavras.
- **D)** Temperature é um parâmetro configurado pelo usuário, não muda automaticamente por idioma.

</details>

---

### Questão 5

Uma empresa de e-commerce está construindo um modelo para analisar reviews de produtos. O modelo precisa entender que "entrega não foi rápida" é negativo, mesmo que "rápida" isoladamente seja positivo. A equipe está avaliando por que Transformers processam a ordem das palavras corretamente apesar de processar todos os tokens em paralelo. Qual componente resolve esse problema?

A) Self-attention, que automaticamente detecta negações no texto  
B) Positional encoding, que injeta informação sobre a posição de cada token na sequência  
C) O tokenizador BPE, que preserva a ordem das palavras durante a divisão  
D) Camadas de normalização, que mantêm a sequência original durante o processamento  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Positional encoding, que injeta informação sobre a posição de cada token na sequência**

✅ **Por que B está correta:** Como Transformers processam todos os tokens simultaneamente (em paralelo), sem positional encoding não saberiam a ordem. Positional encoding adiciona um vetor de posição a cada token, preservando a informação sequencial. Isso permite distinguir "não foi rápida" de "foi rápida não" (onde as posições relativas mudam o significado).

❌ **Por que as outras estão erradas:**
- **A)** Self-attention calcula relevância entre tokens, mas sem informação posicional trataria "não rápida" igual a "rápida não".
- **C)** O tokenizador divide o texto em unidades, mas não adiciona informação de posição ao modelo — apenas cria os tokens.
- **D)** Camadas de normalização estabilizam o treinamento (batch norm, layer norm) — não codificam posição.

</details>

---

### Questão 6

Uma empresa está migrando de um modelo de linguagem baseado em LSTM (Long Short-Term Memory) para um Transformer. O CTO pergunta quais são os trade-offs dessa migração. Quais afirmações estão corretas? **(Selecione DUAS)**

A) Transformers treinam mais rápido porque paralelizam o processamento dos tokens  
B) Transformers usam menos memória que LSTMs para sequências longas  
C) Transformers capturam dependências de longa distância melhor que LSTMs  
D) Transformers são mais simples de implementar que LSTMs  
E) Transformers não precisam de GPUs para treinamento eficiente  

<details>
<summary>🔍 Ver resposta</summary>

**Respostas: A e C**

✅ **Por que A está correta:** Transformers processam todos os tokens em paralelo (via self-attention), enquanto LSTMs processam sequencialmente (token por token). Isso torna o treinamento significativamente mais rápido em hardware paralelo (GPUs/TPUs).

✅ **Por que C está correta:** Self-attention permite conexão direta entre qualquer par de tokens independente da distância. LSTMs perdem informação gradualmente em sequências longas (vanishing gradient), mesmo com gates de memória.

❌ **Por que as outras estão erradas:**
- **B)** Transformers geralmente usam MAIS memória — self-attention é O(n²) em relação ao comprimento da sequência.
- **D)** Transformers são mais complexos (multi-head attention, positional encoding, feedforward layers) — apenas parecem simples porque existem frameworks prontos.
- **E)** Transformers são intensivos em GPU/TPU — treinar um sem hardware paralelo é impraticável.

</details>

---

## Resultado

Acertou todas? Se não, revise os conceitos em `C-02-arquitetura-transformer.md`.

**Dica para a prova:** A AWS não pergunta detalhes de implementação de Transformers, mas espera que você entenda:
- Por que Transformers são mais rápidos (paralelização)
- O que self-attention permite (contexto, relevância entre tokens)
- Encoder-only vs Decoder-only vs Encoder-Decoder (e quais modelos usam qual)
- O que é tokenização e como impacta custos
- Por que positional encoding é necessário (perda de ordem no processamento paralelo)


---

### Questão 7

Uma empresa precisa processar documentos jurídicos de 50.000 palavras em uma única chamada. O arquiteto nota que modelos baseados em Transformer padrão têm dificuldade com sequências muito longas porque a complexidade computacional da self-attention cresce quadraticamente. Qual é a implicação prática desse trade-off?

A) Modelos com context window maiores são sempre mais baratos porque processam mais de uma vez  
B) Modelos com context windows maiores requerem significativamente mais memória e compute, impactando custo e latência  
C) O tamanho da context window não afeta custo nem performance  
D) Documentos longos devem ser sempre divididos em chunks de 100 tokens para contornar a limitação  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Context windows maiores requerem mais memória e compute, impactando custo e latência**

✅ **Por que B está correta:** Self-attention é O(n²) — dobrar o comprimento da sequência quadruplica o custo computacional. Modelos com 128K tokens de context processam muito mais que modelos de 8K, mas com custo significativo de memória, latência e preço por token.

❌ **Por que as outras estão erradas:**
- **A)** Context window maior é geralmente MAIS caro, não mais barato — mais tokens = mais compute.
- **C)** Afeta diretamente — é o principal trade-off de Transformers.
- **D)** RAG com chunks é UMA solução, mas nem sempre adequada (contratos jurídicos podem precisar de contexto completo).

</details>

---

### Questão 8

Uma equipe está escolhendo um modelo para duas tarefas: (1) classificar emails em categorias, e (2) gerar respostas automáticas para clientes. Considerando as variantes de Transformer, qual combinação é MAIS adequada?

A) Encoder-only para ambas as tarefas — mais eficiente  
B) Encoder-only para classificação (compreensão) + Decoder-only para geração de respostas  
C) Decoder-only para ambas — modelos modernos são multi-tarefa  
D) RNN para classificação + Transformer para geração  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: C) Decoder-only para ambas — modelos modernos são multi-tarefa**

✅ **Por que C está correta:** Na prática atual, modelos decoder-only (GPT, Claude, Llama) fazem AMBAS as tarefas via prompt: classificam texto E geram respostas. São suficientemente capazes para compreensão E geração. A distinção encoder/decoder era mais relevante academicamente.

❌ **Por que as outras estão erradas:**
- **A)** Encoder-only (BERT) NÃO gera texto — é projetado para compreensão, não geração.
- **B)** Tecnicamente correto academicamente, mas na prática moderna um único decoder-only faz ambas as tarefas com excelente qualidade.
- **D)** RNNs são obsoletas para essa escala — Transformers são superiores em ambas as tarefas.

**Nota para a prova:** A AWS testa se você sabe que LLMs modernos (decoder-only) são multi-tarefa. Na prática do Bedrock, um modelo faz classificação E geração.

</details>
