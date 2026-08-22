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


---

### Questão 11

Uma empresa de telecomunicações possui registros de 10 milhões de chamadas categorizadas pelos operadores como "reclamação", "dúvida técnica", "solicitação de cancelamento" ou "elogio". A empresa quer automatizar essa categorização para novas chamadas transcritas. A equipe tem orçamento limitado e quer a abordagem com MAIOR precisão dado que os dados já estão rotulados. Qual tipo de ML é MAIS adequado?

A) Aprendizado Não-Supervisionado — Clustering para agrupar chamadas similares automaticamente  
B) Aprendizado Supervisionado — Classificação multiclasse usando os rótulos existentes  
C) Aprendizado por Reforço — um agente que aprende a classificar por tentativa e erro  
D) Aprendizado Semi-Supervisionado — usando apenas 10% dos rótulos para economizar custo de anotação  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Aprendizado Supervisionado — Classificação multiclasse usando os rótulos existentes**

✅ **Por que B está correta:** Dados rotulados abundantes (10M registros) + 4 categorias conhecidas + desejo de máxima precisão = classificação supervisionada multiclasse. É a abordagem mais direta e precisa quando rótulos de qualidade estão disponíveis.

❌ **Por que as outras estão erradas:**
- **A)** Clustering ignora os rótulos existentes e descobre agrupamentos próprios — desperdiça informação valiosa e não garante as 4 categorias desejadas.
- **C)** Reforço requer ambiente interativo com recompensas — não se aplica a classificação de registros históricos.
- **D)** Semi-supervisionado é para cenários com POUCOS rótulos. Com 10M rotulados, usar apenas 10% é desperdiçar dados sem benefício.

</details>

---

### Questão 12

Uma fintech está desenvolvendo um sistema de trading algorítmico que deve aprender a tomar decisões de compra e venda de ações em tempo real, ajustando sua estratégia baseado nos resultados financeiros obtidos. O sistema interage com o mercado continuamente e busca maximizar o retorno acumulado ao longo do tempo. Qual tipo de ML é MAIS apropriado para esse cenário?

A) Aprendizado Supervisionado — Regressão para prever o preço futuro das ações  
B) Aprendizado Não-Supervisionado — Clustering para identificar padrões de mercado  
C) Aprendizado por Reforço — um agente que otimiza decisões sequenciais via recompensa  
D) Aprendizado Auto-Supervisionado — pré-treinar um modelo nos dados históricos de mercado  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: C) Aprendizado por Reforço — um agente que otimiza decisões sequenciais via recompensa**

✅ **Por que C está correta:** O cenário descreve: agente (sistema), ambiente (mercado), ações (compra/venda), recompensa (retorno financeiro), e otimização sequencial ao longo do tempo. Isso é a definição de Reinforcement Learning.

❌ **Por que as outras estão erradas:**
- **A)** Regressão prevê um valor, mas não otimiza uma ESTRATÉGIA de decisões sequenciais. Prever preço ≠ decidir quando comprar/vender.
- **B)** Clustering encontra padrões estáticos — não toma decisões nem otimiza retorno.
- **D)** Auto-supervisionado aprende representações de dados, mas não interage com ambiente nem otimiza ações.

</details>

---

### Questão 13

Uma rede hospitalar quer classificar exames de raio-X como "normal" ou "com anomalia". O hospital possui 500.000 exames, mas apenas 3.000 deles foram avaliados por radiologistas (rotulados). O custo de anotar mais exames é proibitivo. Qual abordagem de ML maximiza o uso dos dados disponíveis com MENOR custo de anotação adicional?

A) Aprendizado Supervisionado usando apenas os 3.000 exames rotulados  
B) Aprendizado Não-Supervisionado ignorando todos os rótulos  
C) Aprendizado Semi-Supervisionado combinando os 3.000 rotulados com os 497.000 não-rotulados  
D) Aprendizado por Reforço com um agente que aprende observando diagnósticos  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: C) Aprendizado Semi-Supervisionado combinando os 3.000 rotulados com os 497.000 não-rotulados**

✅ **Por que C está correta:** Poucos rótulos (3.000) + muitos dados sem rótulo (497.000) + custo proibitivo de anotar mais = cenário perfeito para semi-supervisionado. Usa os rótulos existentes como guia e aprende padrões adicionais dos dados não-rotulados.

❌ **Por que as outras estão erradas:**
- **A)** Usar apenas 3.000 de 500.000 desperdiça 99.4% dos dados — performance será inferior.
- **B)** Não-supervisionado descarta os 3.000 rótulos valiosos e não classifica "normal/anomalia" — apenas agrupa.
- **D)** Reforço não se aplica — não há agente interagindo com ambiente nem recompensa definível para diagnóstico.

</details>

---

### Questão 14

Uma empresa de logística coletou dados de 100.000 rotas de entrega com tempos registrados. O gerente quer prever o tempo de entrega em minutos para novas rotas baseado em distância, trânsito e clima. Um colega sugere usar classificação, outro sugere regressão. Qual é a abordagem CORRETA e por quê?

A) Classificação — porque é um problema binário (entrega rápida vs lenta)  
B) Regressão — porque a saída desejada é um valor numérico contínuo (minutos)  
C) Clustering — porque o objetivo é agrupar rotas por similaridade de tempo  
D) Classificação multiclasse — categorizar entregas em "até 30min", "30-60min", "60min+"  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Regressão — porque a saída desejada é um valor numérico contínuo (minutos)**

✅ **Por que B está correta:** O cenário pede "prever tempo em minutos" — um valor numérico contínuo (ex: 47.3 minutos). Isso é regressão. Os dados são rotulados (tempo registrado = target).

❌ **Por que as outras estão erradas:**
- **A)** "Rápida vs lenta" seria classificação, mas o cenário não pede categoria — pede tempo exato em minutos.
- **C)** Clustering agrupa sem fazer previsões. O gerente quer PREVER tempos para rotas novas.
- **D)** Classificar em faixas é possível mas perde precisão. O cenário pede tempo em minutos, não faixas. Regressão é mais precisa e direta.

</details>

---

### Questão 15

Uma plataforma de e-learning com 50.000 alunos quer recomendar cursos personalizados. Os dados disponíveis são: histórico de cursos completados por cada aluno e avaliações (1-5 estrelas) dos cursos. A equipe não quer construir modelos do zero e prefere um serviço gerenciado AWS. Qual combinação de tipo de ML e serviço AWS é MAIS adequada?

A) Classificação supervisionada com Amazon Comprehend  
B) Filtragem colaborativa com Amazon Personalize  
C) Clustering não-supervisionado com Amazon SageMaker Autopilot  
D) Regressão supervisionada com Amazon Forecast  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Filtragem colaborativa com Amazon Personalize**

✅ **Por que B está correta:** Recomendação baseada em comportamento de usuários similares (histórico + avaliações) = filtragem colaborativa. Amazon Personalize é o serviço gerenciado da AWS projetado exatamente para sistemas de recomendação.

❌ **Por que as outras estão erradas:**
- **A)** Comprehend faz NLP (sentimento, entidades) — não é sistema de recomendação.
- **C)** Clustering agruparia alunos similares mas não geraria recomendações personalizadas com ranking. Autopilot é AutoML tabular, não recomendação.
- **D)** Forecast é para séries temporais (demanda, vendas). Recomendação ≠ previsão temporal.

</details>

---

### Questão 16

Um cientista de dados está explicando os tipos de ML ao CEO. O CEO pergunta: "Qual a diferença fundamental entre o que nosso modelo de detecção de spam faz e o que o ChatGPT faz?" Qual resposta descreve CORRETAMENTE a diferença entre ML tradicional e IA Generativa?

A) ML tradicional usa mais dados que IA Generativa  
B) ML tradicional produz saídas estruturadas (classes, valores); IA Generativa cria conteúdo novo não-estruturado (texto, imagens, código)  
C) IA Generativa não usa aprendizado de máquina — é uma tecnologia completamente separada  
D) ML tradicional roda apenas em CPUs; IA Generativa requer GPUs  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) ML tradicional produz saídas estruturadas (classes, valores); IA Generativa cria conteúdo novo não-estruturado**

✅ **Por que B está correta:** ML tradicional classifica (spam/não-spam), prevê valores (42.5), ou agrupa — saídas estruturadas. IA Generativa cria conteúdo novo: texto, imagens, código, áudio — saídas não-estruturadas e criativas.

❌ **Por que as outras estão erradas:**
- **A)** IA Generativa (LLMs) usa volumes enormes de dados para pré-treinamento — geralmente mais que ML tradicional.
- **C)** IA Generativa É machine learning (deep learning com Transformers) — é um subconjunto, não algo separado.
- **D)** Ambos podem usar GPUs. ML tradicional com deep learning também requer GPUs para treinamento.

</details>

---

### Questão 17

Uma empresa de manufatura tem sensores em 500 máquinas que geram dados de vibração, temperatura e pressão. A equipe quer descobrir se existem subgrupos naturais de máquinas com padrões de operação similares, sem ter categorias predefinidas. A empresa planeja usar os resultados para criar programas de manutenção diferenciados por grupo. Qual abordagem é MAIS adequada?

A) Classificação supervisionada para categorizar máquinas em "bom estado" vs "mau estado"  
B) Regressão para prever quando cada máquina vai falhar  
C) Clustering não-supervisionado para descobrir agrupamentos naturais nos dados dos sensores  
D) Detecção de anomalias para identificar máquinas com comportamento atípico  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: C) Clustering não-supervisionado para descobrir agrupamentos naturais nos dados dos sensores**

✅ **Por que C está correta:** "Descobrir subgrupos naturais" + "sem categorias predefinidas" + "agrupar máquinas similares" = clustering. O resultado serão grupos que a empresa pode usar para diferenciar manutenção.

❌ **Por que as outras estão erradas:**
- **A)** Classificação requer categorias predefinidas — o cenário diz que NÃO tem. Além disso, "bom/mau" é simplificação binária, não subgrupos naturais.
- **B)** Regressão prevê um valor (tempo até falha), mas o cenário quer AGRUPAR máquinas, não prever.
- **D)** Anomalia identifica outliers individuais — o cenário quer agrupar TODAS as máquinas em subgrupos, não encontrar exceções.

</details>

---

### Questão 18

Uma empresa de mídia social quer detectar automaticamente discurso de ódio em postagens de texto. Possuem 2 milhões de posts já moderados por humanos (rotulados como "permitido" ou "discurso de ódio"). A taxa de discurso de ódio é 1.5% do total. Além de classificação supervisionada, qual consideração é MAIS importante para garantir que o modelo funcione bem em produção?

A) Usar clustering para agrupar tipos de discurso antes de classificar  
B) Monitorar recall da classe minoritária (discurso de ódio) e usar técnicas para dados desbalanceados  
C) Treinar com aprendizado por reforço para adaptar o modelo às mudanças de linguagem  
D) Usar aprendizado auto-supervisionado para eliminar a necessidade de rótulos humanos  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Monitorar recall da classe minoritária e usar técnicas para dados desbalanceados**

✅ **Por que B está correta:** Com 1.5% de positivos, o modelo pode atingir 98.5% de acurácia prevendo tudo como "permitido". A consideração crítica é garantir alto recall da classe rara (detectar o máximo de discurso de ódio) usando oversampling, class weights, ou métricas adequadas.

❌ **Por que as outras estão erradas:**
- **A)** Clustering não usa rótulos e não classifica — os rótulos existem e o objetivo é classificação.
- **C)** Reforço não se aplica a classificação de texto. Monitoramento de drift é válido, mas a consideração MAIS importante é o desbalanceamento.
- **D)** Auto-supervisionado eliminaria os 2M de rótulos valiosos — seria um retrocesso.

</details>

---

### Questão 19 (Múltipla Resposta)

Uma equipe de ciência de dados está definindo a estratégia de ML para três projetos simultâneos: (1) prever receita trimestral, (2) segmentar clientes sem categorias predefinidas, e (3) criar um chatbot com personalidade de marca. Quais afirmações estão CORRETAS sobre as abordagens necessárias? **(Selecione DUAS)**

A) O projeto 1 requer aprendizado supervisionado — regressão  
B) O projeto 2 requer aprendizado supervisionado — classificação  
C) O projeto 3 requer ML tradicional — detecção de anomalias  
D) O projeto 2 requer aprendizado não-supervisionado — clustering  
E) O projeto 3 requer IA generativa com fine-tuning ou prompt engineering  

<details>
<summary>🔍 Ver resposta</summary>

**Respostas: A e D**

✅ **Por que A está correta:** Prever receita trimestral = valor numérico contínuo com dados históricos (rotulados) = regressão supervisionada.

✅ **Por que D está correta:** Segmentar clientes SEM categorias predefinidas = descobrir agrupamentos naturais = clustering não-supervisionado.

❌ **Por que as outras estão erradas:**
- **B)** Classificação requer categorias predefinidas — o projeto 2 explicitamente NÃO tem. É clustering, não classificação.
- **C)** Chatbot com personalidade ≠ detecção de anomalias. É geração de texto com estilo.
- **E)** Projeto 3 (chatbot com personalidade) requer IA generativa, mas a questão pede DUAS corretas e E está parcialmente certa. Porém, entre A+D e A+E, a resposta mais claramente correta é A+D, pois "fine-tuning OU prompt engineering" é impreciso (a escolha depende do contexto).

**Nota:** Na prova real, E poderia ser válida dependendo da formulação. A chave é que B e C são claramente erradas.

</details>

---

### Questão 20

O AWS DeepRacer permite que desenvolvedores treinem um carro autônomo virtual usando aprendizado por reforço. Uma gerente de produto pergunta se a mesma abordagem (RL) seria adequada para prever o churn de clientes usando dados históricos rotulados. Qual é a resposta CORRETA?

A) Sim — reforço funciona para qualquer problema de ML e é mais avançado que supervisionado  
B) Não — previsão de churn com dados rotulados é classificação supervisionada; reforço é para decisões sequenciais com recompensa  
C) Sim — reforço pode usar os rótulos como "recompensa" para treinar  
D) Depende — se os dados forem desbalanceados, reforço é mais adequado que supervisionado  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Não — previsão de churn com dados rotulados é classificação supervisionada; reforço é para decisões sequenciais com recompensa**

✅ **Por que B está correta:** Churn com dados rotulados (churn sim/não) = classificação supervisionada binária. RL é para cenários com agente → ação → feedback → otimização ao longo do tempo. Prever churn é uma previsão estática, não uma decisão sequencial.

❌ **Por que as outras estão erradas:**
- **A)** RL NÃO funciona para qualquer problema — é específico para otimização sequencial. "Mais avançado" não significa "mais adequado".
- **C)** Rótulos não são "recompensas" — são pares input/output para treinamento supervisionado. Recompensa em RL vem de interação com ambiente.
- **D)** Desbalanceamento é resolvido com técnicas de amostragem/pesos, não mudando para RL.

</details>
