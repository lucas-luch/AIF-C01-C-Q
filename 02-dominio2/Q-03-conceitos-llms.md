# Questões — Conceitos de LLMs

---

### Questão 1

Uma empresa de seguros está implantando um chatbot para responder perguntas sobre apólices. O chatbot deve fornecer respostas consistentes e factualmente precisas — duas perguntas idênticas devem gerar respostas praticamente iguais. Qual configuração de inferência é mais adequada?

A) Temperature = 1.0 para gerar respostas naturais e variadas  
B) Temperature = 0 ou próximo de 0 para maximizar consistência e determinismo  
C) Top-p = 1.0 para considerar todo o vocabulário disponível  
D) Max tokens = máximo para garantir respostas completas  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Temperature = 0 ou próximo de 0 para maximizar consistência e determinismo**

✅ **Por que B está correta:** Temperature baixa faz o modelo escolher os tokens mais prováveis a cada passo, gerando respostas previsíveis e consistentes. Para informações de apólices (factuais e reguladas), consistência é crítica.

❌ **Por que as outras estão erradas:**
- **A)** Temperature 1.0 introduz variação — respostas diferentes para a mesma pergunta, inaceitável para informações contratuais.
- **C)** Top-p = 1.0 considera toda a distribuição de probabilidade, permitindo tokens menos prováveis — reduz consistência.
- **D)** Max tokens controla comprimento da resposta, não consistência ou factualidade.

</details>

---

### Questão 2

Uma empresa implantou um assistente de IA generativa que responde perguntas sobre seus produtos. Um cliente reportou que o assistente afirmou com confiança que o produto "X-Pro" tem garantia de 5 anos, quando na realidade a garantia é de 2 anos. O texto gerado era fluente e convincente. Qual fenômeno de LLMs explica esse comportamento?

A) Data drift — os dados de treinamento ficaram desatualizados  
B) Alucinação (hallucination) — o modelo gerou informação plausível mas factualmente incorreta  
C) Overfitting — o modelo memorizou dados errados de treinamento  
D) Underfitting — o modelo não tem capacidade suficiente para a tarefa  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Alucinação (hallucination) — o modelo gerou informação plausível mas factualmente incorreta**

✅ **Por que B está correta:** O cenário descreve exatamente alucinação: informação apresentada com confiança, texto fluente e convincente, mas factualmente falsa. LLMs geram texto estatisticamente provável, não necessariamente verdadeiro.

❌ **Por que as outras estão erradas:**
- **A)** Data drift é degradação de performance ao longo do tempo por mudança nos dados de entrada — não se aplica a LLMs gerando fatos incorretos.
- **C)** Overfitting causa performance ruim em dados novos, não geração de informações inventadas.
- **D)** Underfitting resultaria em respostas de baixa qualidade geral, não em respostas fluentes com dados falsos específicos.

</details>

---

### Questão 3

Uma empresa implantou um chatbot com RAG e temperatura baixa, mas ainda observa alucinações ocasionais quando clientes fazem perguntas sobre produtos que não estão na base de conhecimento. A equipe quer uma camada adicional de proteção. Qual abordagem complementa o RAG para reduzir alucinações neste cenário?

A) Aumentar o tamanho do modelo para melhorar a capacidade de raciocínio  
B) Adicionar instruções no prompt para que o modelo responda "não sei" quando não encontrar informação no contexto fornecido  
C) Aumentar a temperature para gerar respostas mais diversas e encontrar a correta  
D) Usar fine-tuning para ensinar o modelo sobre todos os produtos futuros  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Adicionar instruções no prompt para que o modelo responda "não sei" quando não encontrar informação no contexto fornecido**

✅ **Por que B está correta:** Quando a base de conhecimento não contém a resposta, o RAG retorna contexto irrelevante ou vazio. Um prompt restritivo ("responda APENAS com base no contexto; se não encontrar, diga que não tem essa informação") previne que o modelo "invente" uma resposta.

❌ **Por que as outras estão erradas:**
- **A)** Modelos maiores podem ser mais capazes, mas ainda alucinam quando não têm informação — tamanho não resolve ausência de dados.
- **C)** Temperature alta PIORA alucinações — gera tokens menos prováveis, aumentando invenção.
- **D)** Fine-tuning não pode cobrir "todos os produtos futuros" — e RAG já é a solução para dados mutáveis.

</details>

---

### Questão 4

Uma empresa está arquitetando uma solução de IA generativa e precisa processar contratos de 200 páginas inteiros em uma única chamada ao modelo. O arquiteto afirma que o principal limitador é a "context window" do modelo escolhido. O que essa limitação significa na prática?

A) O tempo máximo que uma sessão de chat pode ficar ativa antes de expirar  
B) O número máximo de tokens (entrada + saída) que o modelo pode processar em uma única interação  
C) A quantidade máxima de documentos que podem ser indexados na Knowledge Base  
D) O número máximo de usuários simultâneos que podem interagir com o modelo  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) O número máximo de tokens (entrada + saída) que o modelo pode processar em uma única interação**

✅ **Por que B está correta:** Context window define o limite total de tokens processáveis por chamada. Para contratos de 200 páginas, o texto tokenizado precisa caber na window junto com espaço para a resposta. Se exceder, o conteúdo é truncado.

❌ **Por que as outras estão erradas:**
- **A)** Timeout de sessão é configuração de infraestrutura, não propriedade do modelo.
- **C)** Knowledge Base pode indexar volumes ilimitados de documentos — a context window limita quanto pode ser injetado por query, não o índice total.
- **D)** Usuários simultâneos dependem de throughput/infraestrutura, não da context window.

</details>

---

### Questão 5

Uma empresa está implementando busca semântica para que clientes encontrem produtos usando descrições em linguagem natural (ex: "sapato confortável para caminhada longa"). A equipe precisa converter as descrições dos produtos em representações que permitam busca por similaridade de significado. Qual tecnologia é essencial para isso?

A) Tokenização com BPE (Byte-Pair Encoding) para dividir as descrições em subpalavras  
B) Embeddings para representar texto como vetores numéricos onde significados similares ficam próximos  
C) Fine-tuning do modelo base com dados de produtos para melhorar a classificação  
D) Guardrails para filtrar buscas com conteúdo inadequado  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Embeddings para representar texto como vetores numéricos onde significados similares ficam próximos**

✅ **Por que B está correta:** Embeddings convertem texto em vetores no espaço numérico onde a proximidade reflete similaridade semântica. "Sapato para caminhada" ficaria próximo de "tênis de trilha" — permitindo busca por significado, não por keywords exatas.

❌ **Por que as outras estão erradas:**
- **A)** Tokenização divide texto em unidades processáveis, mas não cria representações semânticas comparáveis — é um pré-processamento, não a solução de busca.
- **C)** Fine-tuning muda o comportamento de geração do modelo — não é necessário para criar embeddings de busca.
- **D)** Guardrails filtram conteúdo indesejado — não têm relação com busca semântica.

</details>

---

### Questão 6

Uma empresa está usando um LLM no Amazon Bedrock para gerar resumos executivos de relatórios financeiros. Os resumos estão ficando muito longos (3-4 parágrafos) e o custo por requisição está alto. A equipe quer limitar os resumos a 1 parágrafo curto. Qual parâmetro de inferência resolve DIRETAMENTE o problema de custo e comprimento?

A) Reduzir a temperature para gerar respostas mais focadas  
B) Reduzir max_tokens para limitar o número de tokens na resposta gerada  
C) Reduzir top-p para limitar a diversidade do vocabulário usado  
D) Mudar para um modelo com context window menor  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Reduzir max_tokens para limitar o número de tokens na resposta gerada**

✅ **Por que B está correta:** Max tokens define o limite máximo de tokens gerados na saída. Reduzir esse valor limita o comprimento da resposta E reduz custo diretamente (paga-se por token de saída no Bedrock on-demand).

❌ **Por que as outras estão erradas:**
- **A)** Temperature controla aleatoriedade/criatividade — respostas com temperature baixa podem ser igualmente longas.
- **C)** Top-p limita quais tokens são considerados na geração (diversidade), mas não o comprimento.
- **D)** Context window é propriedade fixa do modelo, não um parâmetro ajustável por request. E uma window menor não garante respostas mais curtas.

</details>

---

## Resultado

Acertou todas? Se não, revise os conceitos em `C-03-conceitos-llms.md`.

**Dica para a prova:** A AWS testa esses conceitos em cenários práticos:
- Temperature baixa → respostas factual/consistentes; alta → criativas/variadas
- Alucinação → RAG + prompt restritivo como principal mitigação
- Context window → limitação de tokens por interação (impacta documentos longos)
- Embeddings → base da busca semântica e RAG
- Max tokens → controle direto de custo e comprimento de saída


---

### Questão 7

Uma empresa está configurando inferência no Bedrock e precisa entender a diferença entre temperature e top-p. Um desenvolvedor pergunta: "Se eu usar temperature = 0.7 E top-p = 0.9 ao mesmo tempo, o que acontece?" Qual é a resposta CORRETA?

A) Apenas um pode ser usado por vez — o outro é ignorado  
B) Ambos funcionam juntos: top-p filtra o vocabulário disponível, temperature ajusta a distribuição de probabilidade dentro desse vocabulário filtrado  
C) Temperature e top-p são sinônimos — fazem a mesma coisa  
D) Top-p anula o efeito de temperature em todos os cenários  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Ambos funcionam juntos — top-p filtra, temperature ajusta distribuição**

✅ **Por que B está correta:** Top-p (nucleus sampling) seleciona o subconjunto de tokens mais prováveis cuja probabilidade cumulativa atinge p. Temperature ajusta quão "afiada" ou "suave" é a distribuição DENTRO desse subconjunto. Juntos, controlam diversidade de formas complementares.

❌ **Por que as outras estão erradas:**
- **A)** Na maioria dos modelos no Bedrock, ambos podem ser configurados simultaneamente.
- **C)** Fazem coisas diferentes — top-p corta vocabulário, temperature redistribui probabilidades.
- **D)** Top-p não anula temperature — trabalham em camadas diferentes do processo de sampling.

</details>

---

### Questão 8

Uma empresa usa um LLM para geração de conteúdo criativo (poemas, slogans, brainstorming). As saídas estão muito previsíveis e repetitivas. Qual combinação de parâmetros é MAIS adequada para aumentar criatividade?

A) Temperature = 0, Top-p = 0.1 — máximo foco e precisão  
B) Temperature = 0.9, Top-p = 0.95 — alta diversidade e criatividade  
C) Max tokens = 10 — respostas curtas são mais criativas  
D) Temperature = 0, Max tokens = máximo — mais texto = mais criatividade  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Temperature = 0.9, Top-p = 0.95 — alta diversidade e criatividade**

✅ **Por que B está correta:** Temperature alta (0.9) suaviza a distribuição de probabilidade, permitindo tokens menos prováveis. Top-p alto (0.95) considera 95% do vocabulário provável. Juntos, geram saídas variadas, surpreendentes e criativas.

❌ **Por que as outras estão erradas:**
- **A)** Temperature 0 + Top-p 0.1 = máximo determinismo — o OPOSTO de criatividade.
- **C)** Max tokens controla COMPRIMENTO, não criatividade. Respostas curtas podem ser igualmente previsíveis.
- **D)** Temperature 0 gera o token mais provável a cada passo — texto longo mas repetitivo e previsível.

</details>
