# Questões — Tipos de Machine Learning

## Instruções
- Questões no estilo da prova AWS Certified AI Practitioner (AIF-C01)
- Clique em "Ver resposta" para revelar o gabarito explicado
- Tente responder antes de verificar!

---

### Questão 1

Uma empresa de e-commerce quer prever o valor total que um cliente gastará nos próximos 12 meses com base no histórico de compras rotulado. Qual tipo de aprendizado de máquina é mais adequado?

A) Aprendizado Não-Supervisionado  
B) Aprendizado por Reforço  
C) Aprendizado Supervisionado — Classificação  
D) Aprendizado Supervisionado — Regressão  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: D) Aprendizado Supervisionado — Regressão**

✅ **Por que D está correta:** O cenário tem dados rotulados (histórico de compras com valores conhecidos) e quer prever um **valor numérico contínuo** (quanto o cliente vai gastar). Isso é regressão supervisionada.

❌ **Por que as outras estão erradas:**
- **A)** Não-supervisionado não usa dados rotulados e não faz previsões de valores — encontra padrões.
- **B)** Reforço é para agentes que aprendem por tentativa e erro com recompensas, não para previsão de valores a partir de histórico.
- **C)** Classificação prevê **categorias** (spam/não-spam), não valores numéricos. "Quanto vai gastar" é um valor contínuo, não uma classe.

</details>

---

### Questão 2

Uma equipe de segurança quer agrupar padrões de tráfego de rede para identificar comportamentos similares, sem ter exemplos previamente categorizados. Qual abordagem é mais apropriada?

A) Aprendizado Supervisionado  
B) Aprendizado Não-Supervisionado  
C) Aprendizado por Reforço  
D) Aprendizado Semi-Supervisionado  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Aprendizado Não-Supervisionado**

✅ **Por que B está correta:** O cenário pede para "agrupar" padrões "sem exemplos previamente categorizados" (sem rótulos). Clustering é a tarefa clássica de aprendizado não-supervisionado.

❌ **Por que as outras estão erradas:**
- **A)** Supervisionado requer dados rotulados (categorias já definidas), o que o cenário explicitamente diz não ter.
- **C)** Reforço envolve um agente interagindo com um ambiente por tentativa e erro — não se aplica a agrupamento de dados.
- **D)** Semi-supervisionado requer pelo menos alguns dados rotulados. O cenário diz que não há exemplos categorizados.

</details>

---

### Questão 3

A AWS oferece o serviço DeepRacer, onde um carro virtual aprende a dirigir em uma pista tomando decisões e recebendo feedback sobre seu desempenho. Qual tipo de ML melhor descreve esse processo?

A) Aprendizado Supervisionado  
B) Aprendizado Não-Supervisionado  
C) Aprendizado por Reforço  
D) Aprendizado Auto-Supervisionado  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: C) Aprendizado por Reforço**

✅ **Por que C está correta:** O DeepRacer é o exemplo canônico de Reinforcement Learning na AWS. Um agente (carro) interage com um ambiente (pista), toma ações (acelerar, virar) e recebe recompensas/penalidades baseadas no desempenho. Aprende por tentativa e erro.

❌ **Por que as outras estão erradas:**
- **A)** Supervisionado precisaria de um dataset rotulado com "ação correta para cada situação". O DeepRacer não tem isso — ele descobre sozinho.
- **B)** Não-supervisionado encontra padrões em dados estáticos, não envolve interação agente-ambiente com recompensas.
- **D)** Auto-supervisionado gera rótulos a partir dos próprios dados (como masking em LLMs). O DeepRacer aprende por interação, não por predição de dados mascarados.

</details>

---

### Questão 4

Uma empresa tem milhões de imagens de produtos, mas apenas 2% delas possuem rótulos de categoria. A empresa quer classificar todas as imagens. Qual abordagem de ML melhor aproveita essa situação?

A) Aprendizado Supervisionado  
B) Aprendizado Não-Supervisionado  
C) Aprendizado Semi-Supervisionado  
D) Aprendizado por Reforço  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: C) Aprendizado Semi-Supervisionado**

✅ **Por que C está correta:** O cenário tem **poucos dados rotulados** (2%) + **muitos dados não-rotulados** (98%). Semi-supervisionado é projetado exatamente para essa situação — usa os rótulos disponíveis para guiar o aprendizado nos dados sem rótulo.

❌ **Por que as outras estão erradas:**
- **A)** Supervisionado puro usaria apenas os 2% rotulados e descartaria os 98% restantes — desperdício de dados.
- **B)** Não-supervisionado ignoraria completamente os rótulos existentes e apenas agruparia sem classificar nas categorias corretas.
- **D)** Reforço não se aplica — não há agente interagindo com ambiente nem conceito de recompensa aqui.

</details>

---

### Questão 5

Um banco quer classificar transações como "fraudulenta" ou "legítima" com base em um histórico de transações já classificadas por analistas. Qual é o tipo de ML e tarefa corretos?

A) Não-Supervisionado — Clustering  
B) Supervisionado — Regressão  
C) Supervisionado — Classificação  
D) Reforço — Policy Optimization  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: C) Supervisionado — Classificação**

✅ **Por que C está correta:** Os dados são rotulados (analistas já classificaram como fraude/legítima) e a saída desejada é uma **categoria discreta** (fraude ou legítima = 2 classes). Isso é classificação supervisionada.

❌ **Por que as outras estão erradas:**
- **A)** Clustering agrupa sem rótulos. Aqui os rótulos existem e o objetivo é classificar em categorias conhecidas, não descobrir agrupamentos.
- **B)** Regressão prevê valores numéricos contínuos. "Fraude/legítima" é uma categoria binária, não um número.
- **D)** Reforço é para agentes que aprendem por interação com ambiente. Classificar transações a partir de histórico rotulado não envolve agente, ambiente ou recompensa.

</details>

---

### Questão 6

Uma empresa de streaming de música quer descobrir grupos de ouvintes com gostos similares para criar playlists temáticas. Não existem categorias pré-definidas de ouvintes. Qual abordagem é mais adequada?

A) Aprendizado Supervisionado — Classificação  
B) Aprendizado Supervisionado — Regressão  
C) Aprendizado Não-Supervisionado — Clustering  
D) Aprendizado por Reforço  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: C) Aprendizado Não-Supervisionado — Clustering**

✅ **Por que C está correta:** Quer "descobrir grupos" sem "categorias pré-definidas". Isso é exatamente clustering — agrupar dados similares sem rótulos predefinidos.

❌ **Por que as outras estão erradas:**
- **A)** Classificação precisa de categorias já definidas para treinar. O cenário diz que não existem categorias pré-definidas.
- **B)** Regressão prevê valores numéricos — não se aplica a agrupamento de ouvintes.
- **D)** Reforço envolve agente aprendendo por interação. Agrupar ouvintes é análise de dados, não decisão sequencial.

</details>

---

### Questão 7

Um cientista de dados está pré-treinando um modelo de linguagem usando bilhões de sentenças da internet. O modelo aprende a prever palavras mascaradas nas frases. Qual tipo de aprendizado está sendo utilizado?

A) Aprendizado Supervisionado  
B) Aprendizado Não-Supervisionado  
C) Aprendizado Auto-Supervisionado  
D) Aprendizado por Reforço  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: C) Aprendizado Auto-Supervisionado**

✅ **Por que C está correta:** O modelo gera seus próprios rótulos (mascara uma palavra e tenta prever qual é). Não há anotação humana — os "rótulos" vêm da própria estrutura dos dados. Isso é self-supervised learning, a base do pré-treinamento de LLMs como BERT, GPT e Claude.

❌ **Por que as outras estão erradas:**
- **A)** Supervisionado requer rótulos fornecidos por humanos. Aqui os rótulos são gerados automaticamente pelo próprio processo de masking.
- **B)** Não-supervisionado não tem conceito de "prever algo" — encontra padrões sem target. Aqui há um target claro (a palavra mascarada).
- **D)** Reforço envolve agente, ambiente e recompensas. Prever palavras mascaradas é uma tarefa de predição, não de interação com ambiente.

</details>

---

### Questão 8

Uma empresa quer usar Machine Learning para otimizar automaticamente os preços de seus produtos em tempo real, ajustando baseado na resposta dos clientes (compram mais ou menos). O sistema deve aprender continuamente qual estratégia de preço maximiza a receita. Qual tipo de ML é mais apropriado?

A) Aprendizado Supervisionado — Regressão  
B) Aprendizado Não-Supervisionado — Clustering  
C) Aprendizado Semi-Supervisionado  
D) Aprendizado por Reforço  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: D) Aprendizado por Reforço**

✅ **Por que D está correta:** O sistema toma ações (ajustar preços), observa a resposta do ambiente (clientes compram mais ou menos), e busca maximizar uma recompensa (receita). É um loop contínuo de ação → feedback → ajuste — exatamente aprendizado por reforço.

❌ **Por que as outras estão erradas:**
- **A)** Regressão prevê um valor a partir de dados históricos, mas não otimiza decisões em tempo real com feedback contínuo.
- **B)** Clustering agrupa dados — não toma decisões nem otimiza estratégias.
- **C)** Semi-supervisionado mistura dados rotulados/não-rotulados para classificar. Não envolve otimização contínua por feedback.

</details>

---

### Questão 9 (Múltipla Resposta)

Uma equipe de data science está avaliando qual tipo de Machine Learning usar para diferentes projetos. Quais das seguintes afirmações estão corretas? **(Selecione DUAS)**

A) Aprendizado supervisionado requer dados rotulados para treinamento  
B) Aprendizado não-supervisionado é ideal para prever valores numéricos  
C) Aprendizado por reforço usa um dataset fixo de entrada e saída para treinar  
D) Clustering é uma tarefa de aprendizado não-supervisionado  
E) Aprendizado supervisionado não pode ser usado para classificação  

<details>
<summary>🔍 Ver resposta</summary>

**Respostas: A e D**

✅ **Por que A está correta:** Por definição, aprendizado supervisionado treina com dados rotulados (entrada + resposta correta).

✅ **Por que D está correta:** Clustering (agrupar dados similares sem categorias pré-definidas) é a tarefa clássica de aprendizado não-supervisionado.

❌ **Por que as outras estão erradas:**
- **B)** Prever valores numéricos é regressão (supervisionado). Não-supervisionado encontra padrões, não faz previsões de valores.
- **C)** Reforço NÃO usa dataset fixo — aprende por interação com o ambiente (tentativa e erro com recompensas).
- **E)** Classificação é justamente uma das principais tarefas de aprendizado supervisionado.

</details>

---

### Questão 10

Qual serviço AWS é um exemplo prático de aprendizado por reforço?

A) Amazon Comprehend  
B) Amazon Rekognition  
C) AWS DeepRacer  
D) Amazon Forecast  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: C) AWS DeepRacer**

✅ **Por que C está correta:** O AWS DeepRacer é um serviço/plataforma educacional da AWS que usa aprendizado por reforço para treinar um carro autônomo virtual a navegar em uma pista. O carro (agente) aprende por tentativa e erro, recebendo recompensas por dirigir bem.

❌ **Por que as outras estão erradas:**
- **A)** Amazon Comprehend usa NLP pré-treinado (supervisionado) para análise de sentimento, entidades e idioma.
- **B)** Amazon Rekognition usa visão computacional (supervisionado) para detectar objetos, faces e texto em imagens.
- **D)** Amazon Forecast usa aprendizado supervisionado para previsão de séries temporais.

</details>

---

## Resultado

Acertou todas? Se não, revise os conceitos em `01-tipos-de-machine-learning.md` focando nos tipos que errou.

**Dica para a prova:** Identifique as palavras-chave no enunciado:
- Dados rotulados + prever categoria → Supervisionado (Classificação)
- Dados rotulados + prever valor → Supervisionado (Regressão)
- Sem rótulos + agrupar/segmentar → Não-Supervisionado
- Agente + recompensa + tentativa e erro → Reforço
- Poucos rótulos + muitos sem → Semi-Supervisionado
- Modelo cria próprios rótulos / pré-treinamento LLM → Auto-Supervisionado
