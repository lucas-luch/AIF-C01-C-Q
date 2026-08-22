# Questões — Tipos de Tarefas de ML

---

### Questão 1

Uma rede de varejo com 2 milhões de clientes quer identificar grupos com padrões de compra similares para criar campanhas de marketing direcionadas. A equipe de marketing não tem categorias predefinidas de clientes — querem que os padrões emerjam dos dados. Qual tarefa de ML é mais adequada?

A) Classificação supervisionada usando as categorias de produtos como rótulos  
B) Regressão para prever o valor de compra de cada grupo  
C) Clustering para descobrir agrupamentos naturais nos dados sem rótulos predefinidos  
D) Detecção de anomalias para identificar clientes com comportamento atípico  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: C) Clustering para descobrir agrupamentos naturais nos dados sem rótulos predefinidos**

✅ **Por que C está correta:** "Identificar grupos" + "sem categorias predefinidas" + "padrões emerjam dos dados" = clustering. O modelo descobre segmentos naturais baseado em similaridade de comportamento.

❌ **Por que as outras estão erradas:**
- **A)** Classificação requer categorias já definidas para treinar — o cenário explicitamente diz que não existem.
- **B)** Regressão prevê valores numéricos para cada cliente, não agrupa clientes similares.
- **D)** Detecção de anomalias encontra outliers (comportamento anormal), não cria segmentos de clientes para marketing.

</details>

---

### Questão 2

Uma empresa de streaming quer sugerir filmes aos usuários com base no histórico de visualização de outros usuários com gostos similares. Qual serviço AWS é mais adequado?

A) Amazon Forecast  
B) Amazon Personalize  
C) Amazon Comprehend  
D) Amazon Kendra  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Amazon Personalize**

✅ **Por que B está correta:** Amazon Personalize é o serviço gerenciado para recomendações. Usa filtragem colaborativa (comportamento de usuários similares) para sugerir itens relevantes — exatamente o cenário descrito.

❌ **Por que as outras estão erradas:**
- **A)** Forecast é para previsão de séries temporais (demanda, receita), não recomendações.
- **C)** Comprehend faz NLP (sentimento, entidades), não recomendações.
- **D)** Kendra é busca empresarial inteligente, não sistema de recomendação.

</details>

---

### Questão 3

Uma empresa de logística processa 50.000 entregas por dia e quer prever o tempo estimado de entrega em horas para cada pedido, levando em conta distância, tráfego histórico e condições climáticas. A previsão será exibida ao cliente no momento da compra. Qual tipo de tarefa de ML é essa?

A) Classificação multiclasse — categorizar entregas como "rápida", "normal" ou "lenta"  
B) Regressão — prever um valor numérico contínuo (horas até entrega)  
C) Clustering — agrupar pedidos por similaridade de tempo  
D) Recomendação — sugerir a melhor opção de frete ao cliente  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Regressão — prever um valor numérico contínuo (horas até entrega)**

✅ **Por que B está correta:** "Prever tempo em horas" é prever um valor numérico contínuo (ex: 4.5 horas, 23.2 horas) — regressão. O modelo aprende a relação entre features (distância, tráfego, clima) e o tempo de entrega.

❌ **Por que as outras estão erradas:**
- **A)** Classificar em "rápida/normal/lenta" perderia a precisão numérica que o cenário requer — o cliente quer ver "Entrega em 4h", não "Entrega normal".
- **C)** Clustering agrupa dados similares sem fazer previsões — não gera um tempo estimado para cada pedido.
- **D)** Recomendação sugere itens a usuários. Prever tempo não é recomendar frete, é calcular uma estimativa.

</details>

---

### Questão 4

Uma empresa precisa extrair automaticamente nomes, datas e valores de milhares de faturas em PDF. Qual serviço AWS é mais adequado?

A) Amazon Comprehend  
B) Amazon Textract  
C) Amazon Rekognition  
D) Amazon Translate  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Amazon Textract**

✅ **Por que B está correta:** Amazon Textract extrai texto, formulários e tabelas de documentos (PDFs, imagens). É projetado especificamente para entender a estrutura de documentos e extrair dados de campos.

❌ **Por que as outras estão erradas:**
- **A)** Comprehend analisa texto já extraído (sentimento, entidades). Não lê PDFs diretamente.
- **C)** Rekognition é para visão computacional (objetos, faces, moderação), não extração de texto estruturado de documentos.
- **D)** Translate traduz texto entre idiomas, não extrai texto de documentos.

</details>

---

### Questão 5

Uma empresa de manufatura opera 200 máquinas CNC 24/7 e coleta dados de sensores (temperatura, vibração, pressão) em tempo real. A equipe de manutenção quer ser alertada quando uma máquina começar a se comportar de forma diferente do padrão histórico, permitindo intervenção antes da falha. Qual tarefa de ML melhor se aplica?

A) Classificação multiclasse para categorizar o tipo de falha iminente  
B) Regressão para prever o número de dias até a próxima falha  
C) Detecção de anomalias para identificar desvios do comportamento normal da máquina  
D) Clustering para agrupar máquinas com padrões de desgaste similares  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: C) Detecção de anomalias para identificar desvios do comportamento normal da máquina**

✅ **Por que C está correta:** O cenário pede identificar "comportamento diferente do padrão histórico" — isso é exatamente detecção de anomalias. O modelo aprende o perfil normal dos sensores e alerta quando os valores desviam significativamente.

❌ **Por que as outras estão erradas:**
- **A)** Classificação de tipo de falha requer histórico rotulado de cada categoria de falha. O cenário quer detectar QUALQUER desvio, não categorizar tipos específicos.
- **B)** Regressão de tempo-até-falha (RUL — Remaining Useful Life) é uma abordagem válida mas diferente. O cenário foca em "comportamento diferente" (anomalia), não em "quanto tempo falta" (previsão numérica).
- **D)** Clustering agruparia máquinas por similaridade — útil para planejamento, mas não gera alertas em tempo real de comportamento anormal.

</details>

---

### Questão 6

Qual serviço AWS deve ser usado para analisar o sentimento (positivo, negativo, neutro) de milhares de avaliações de clientes?

A) Amazon Lex  
B) Amazon Polly  
C) Amazon Comprehend  
D) Amazon Transcribe  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: C) Amazon Comprehend**

✅ **Por que C está correta:** Amazon Comprehend é o serviço de NLP que realiza análise de sentimento, extração de entidades, detecção de idioma e tópicos — tudo pré-treinado, sem necessidade de criar modelo.

❌ **Por que as outras estão erradas:**
- **A)** Lex é para construir chatbots conversacionais, não análise de sentimento.
- **B)** Polly converte texto em fala (text-to-speech), não analisa conteúdo.
- **D)** Transcribe converte áudio em texto (speech-to-text), não analisa sentimento.

</details>



---

### Questão 7

Uma companhia aérea quer prever a demanda de passageiros para os próximos 6 meses em cada uma de suas 150 rotas, levando em conta sazonalidade (férias, feriados) e tendências históricas. A equipe de negócios não tem experiência em ML e quer a solução gerenciada com MENOR esforço operacional. Qual serviço AWS é MAIS adequado?

A) Amazon SageMaker Autopilot para criar modelos de regressão automaticamente  
B) Amazon Forecast para previsão gerenciada de séries temporais com sazonalidade  
C) Amazon Personalize para recomendar rotas populares aos clientes  
D) Amazon Bedrock para gerar previsões usando um Foundation Model  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Amazon Forecast para previsão gerenciada de séries temporais com sazonalidade**

✅ **Por que B está correta:** Previsão temporal + sazonalidade + múltiplas séries (150 rotas) + gerenciado + sem expertise ML = Amazon Forecast. Projetado especificamente para forecasting com algoritmos que capturam automaticamente padrões sazonais.

❌ **Por que as outras estão erradas:**
- **A)** Autopilot é AutoML tabular genérico — não é otimizado para séries temporais com sazonalidade.
- **C)** Personalize gera recomendações de itens para usuários, não previsão de demanda agregada.
- **D)** LLMs não são projetados para previsão quantitativa de séries temporais — podem gerar texto SOBRE previsões, mas não calcular forecasts confiáveis.

</details>

---

### Questão 8

Uma empresa de mídia social precisa analisar 50.000 comentários por hora para identificar automaticamente: (1) o sentimento (positivo/negativo/neutro), (2) os tópicos mencionados, e (3) o idioma de cada comentário. A equipe quer usar um ÚNICO serviço AWS sem treinar modelos. Qual serviço atende TODOS os três requisitos?

A) Amazon Translate — traduz e detecta idioma  
B) Amazon Comprehend — análise de sentimento, tópicos e detecção de idioma pré-treinados  
C) Amazon Lex — chatbot com compreensão de linguagem natural  
D) Amazon Textract — extração de texto de documentos  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Amazon Comprehend — análise de sentimento, tópicos e detecção de idioma pré-treinados**

✅ **Por que B está correta:** Comprehend oferece TODOS: sentiment analysis, topic modeling, language detection — tudo pré-treinado, sem necessidade de criar modelos. Processa texto em escala.

❌ **Por que as outras estão erradas:**
- **A)** Translate faz tradução e detecta idioma, mas NÃO faz análise de sentimento nem tópicos.
- **C)** Lex constrói chatbots conversacionais — não analisa sentimento nem tópicos de texto em batch.
- **D)** Textract extrai texto de imagens/PDFs — não analisa sentimento nem tópicos.

</details>

---

### Questão 9

Uma empresa de RH recebe 10.000 currículos em PDF por mês e precisa extrair automaticamente: nome do candidato, formação acadêmica, anos de experiência e habilidades técnicas — todos em campos estruturados de formulário. Qual combinação de serviços é MAIS eficiente?

A) Amazon Rekognition para ler o PDF e Amazon Comprehend para extrair entidades  
B) Amazon Textract para extrair texto/formulários e Amazon Comprehend para identificar entidades nomeadas  
C) Amazon Transcribe para converter o PDF em texto e Amazon Translate para padronizar  
D) Amazon Bedrock para ler e interpretar os PDFs com um LLM  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Amazon Textract para extrair texto/formulários e Amazon Comprehend para identificar entidades nomeadas**

✅ **Por que B está correta:** Textract extrai texto e dados estruturados de PDFs (formulários, tabelas). Comprehend identifica entidades nomeadas (nomes, organizações, datas) no texto extraído. Juntos, resolvem o pipeline completo.

❌ **Por que as outras estão erradas:**
- **A)** Rekognition é visão computacional (objetos, faces, moderação) — não lê PDFs nem extrai texto de documentos.
- **C)** Transcribe converte ÁUDIO em texto — não processa PDFs. Translate traduz idiomas, não padroniza dados.
- **D)** Bedrock com LLM funcionaria, mas não é a solução mais eficiente/custo-efetiva para extração estruturada em escala. Textract é otimizado para esse caso de uso específico.

</details>

---

### Questão 10

Uma empresa de transporte quer criar um assistente virtual que permita aos motoristas reportar problemas usando voz (ex: "pneu furado na rodovia BR-101 km 45"). O assistente deve: (1) converter fala em texto, (2) extrair a localização e tipo de problema do texto, e (3) classificar a urgência. Qual sequência de serviços AWS é CORRETA?

A) Amazon Polly → Amazon Comprehend → Amazon Lex  
B) Amazon Transcribe → Amazon Comprehend → modelo de classificação customizado  
C) Amazon Lex → Amazon Translate → Amazon Textract  
D) Amazon Rekognition → Amazon Transcribe → Amazon Forecast  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Amazon Transcribe → Amazon Comprehend → modelo de classificação customizado**

✅ **Por que B está correta:** (1) Transcribe converte fala→texto, (2) Comprehend extrai entidades (localização, tipo de problema) do texto, (3) classificação de urgência requer modelo customizado. A sequência é lógica e usa cada serviço na sua função.

❌ **Por que as outras estão erradas:**
- **A)** Polly faz o INVERSO (texto→fala). Lex é chatbot, não classificador de urgência.
- **C)** Lex é chatbot, Translate traduz idiomas, Textract lê documentos — nenhum processa voz nem classifica urgência.
- **D)** Rekognition é visão computacional (imagens), Forecast é previsão temporal — irrelevantes para processamento de voz.

</details>

---

### Questão 11

Uma loja online quer identificar produtos que estão sendo retornados com frequência anormalmente alta em relação ao histórico. Não há categorias predefinidas de "retorno normal" vs "retorno anormal" — a equipe quer que o sistema aprenda o padrão histórico e alerte quando algo foge da norma. Qual tarefa de ML é MAIS adequada?

A) Classificação binária — treinar com exemplos de "retorno normal" e "retorno anormal"  
B) Regressão — prever o número exato de retornos por produto  
C) Detecção de anomalias — identificar desvios do padrão histórico normal  
D) Recomendação — sugerir produtos com menor taxa de retorno  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: C) Detecção de anomalias — identificar desvios do padrão histórico normal**

✅ **Por que C está correta:** "Frequência anormalmente alta" + "sem categorias predefinidas" + "aprende o padrão e alerta desvios" = detecção de anomalias. O modelo define o que é "normal" e identifica outliers.

❌ **Por que as outras estão erradas:**
- **A)** Classificação requer rótulos de "normal/anormal" predefinidos — o cenário diz que NÃO existem.
- **B)** Regressão prevê um valor, mas não identifica se esse valor é "anormal" em relação ao histórico.
- **D)** Recomendação sugere itens a usuários — problema completamente diferente de detectar retornos anormais.

</details>
