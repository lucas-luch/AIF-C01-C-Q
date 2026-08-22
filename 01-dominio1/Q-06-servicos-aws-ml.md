# Questões — Serviços AWS de ML

---

### Questão 1

Um analista de negócios sem experiência em programação precisa construir um modelo de previsão de vendas usando dados históricos. Qual serviço AWS é mais adequado?

A) Amazon SageMaker Studio  
B) Amazon SageMaker Canvas  
C) Amazon Bedrock  
D) AWS Glue  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Amazon SageMaker Canvas**

✅ **Por que B está correta:** SageMaker Canvas oferece uma interface visual (no-code/low-code) que permite analistas de negócio construir modelos de ML sem escrever código — drag-and-drop com dados tabulares.

❌ **Por que as outras estão erradas:**
- **A)** SageMaker Studio é uma IDE completa que requer conhecimento de programação (Python, notebooks).
- **C)** Bedrock é para IA generativa (Foundation Models), não para previsão tabular.
- **D)** Glue é para ETL/preparação de dados, não construção de modelos.

</details>

---

### Questão 2

Uma empresa precisa converter gravações de áudio de atendimento ao cliente em texto para análise posterior. Qual serviço deve ser usado?

A) Amazon Polly  
B) Amazon Comprehend  
C) Amazon Transcribe  
D) Amazon Lex  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: C) Amazon Transcribe**

✅ **Por que C está correta:** Amazon Transcribe converte fala (áudio) em texto (speech-to-text) — exatamente o que o cenário pede.

❌ **Por que as outras estão erradas:**
- **A)** Polly faz o inverso: converte texto em fala (text-to-speech).
- **B)** Comprehend analisa texto já existente (sentimento, entidades). Não converte áudio.
- **D)** Lex é para construir chatbots, não para transcrever áudio offline.

</details>

---

### Questão 3

Uma empresa de 5.000 funcionários quer permitir que qualquer colaborador faça perguntas em linguagem natural sobre documentos internos (políticas de RH, manuais técnicos, procedimentos) e receba respostas precisas extraídas diretamente desses documentos. A empresa não quer construir ou treinar modelos customizados. Qual serviço AWS é mais adequado?

A) Amazon Athena para consultar os documentos armazenados no S3 com SQL  
B) Amazon Kendra para busca empresarial inteligente com NLP sobre documentos corporativos  
C) Amazon Comprehend para extrair entidades e sentimento dos documentos  
D) Amazon Bedrock Knowledge Bases para implementar RAG com Foundation Models  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Amazon Kendra para busca empresarial inteligente com NLP sobre documentos corporativos**

✅ **Por que B está correta:** Amazon Kendra é um serviço de busca empresarial inteligente que usa NLP para entender perguntas em linguagem natural e retornar respostas precisas de documentos corporativos — sem necessidade de treinar modelos. Integra com múltiplas fontes (S3, SharePoint, Confluence, etc.).

❌ **Por que as outras estão erradas:**
- **A)** Athena executa consultas SQL em dados estruturados/semi-estruturados no S3 — requer conhecimento de SQL e não entende linguagem natural sobre documentos textuais.
- **C)** Comprehend analisa texto (sentimento, entidades, tópicos) mas não faz busca nem responde perguntas — processa texto, não busca informação.
- **D)** Knowledge Bases com Bedrock é uma opção válida para RAG, mas requer configuração de FM + vector database + indexação. O cenário pede algo direto "sem construir modelos" — Kendra é totalmente gerenciado para busca.

</details>

---

### Questão 4

Qual é a principal diferença entre Amazon SageMaker Autopilot e Amazon SageMaker JumpStart?

A) Autopilot usa Foundation Models; JumpStart treina modelos do zero  
B) Autopilot gera modelos automaticamente a partir dos seus dados; JumpStart oferece modelos pré-treinados para deploy  
C) Autopilot é sem código; JumpStart requer Python avançado  
D) Ambos fazem a mesma coisa — são sinônimos  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Autopilot gera modelos automaticamente a partir dos seus dados; JumpStart oferece modelos pré-treinados para deploy**

✅ **Por que B está correta:** Autopilot é AutoML — você dá seus dados e ele testa múltiplos algoritmos e hiperparâmetros automaticamente. JumpStart é um hub de modelos já treinados (incluindo Foundation Models) que você pode deployar ou adaptar.

❌ **Por que as outras estão erradas:**
- **A)** JumpStart inclui FMs mas não é só isso; Autopilot não usa FMs, treina modelos tabulares.
- **C)** Ambos podem ser usados via interface visual no Studio. JumpStart não exige Python avançado.
- **D)** São serviços com propósitos diferentes.

</details>

---

### Questão 5 (Múltipla Resposta)

Uma equipe precisa preparar dados brutos antes de treinar um modelo de ML. Quais serviços AWS são apropriados para ETL e preparação de dados? **(Selecione DUAS)**

A) Amazon SageMaker Endpoints  
B) AWS Glue  
C) Amazon Bedrock  
D) AWS Glue DataBrew  
E) Amazon Fraud Detector  

<details>
<summary>🔍 Ver resposta</summary>

**Respostas: B e D**

✅ **Por que B está correta:** AWS Glue é o serviço serverless de ETL (Extract, Transform, Load) — extrai dados de diversas fontes, transforma e carrega para o destino.

✅ **Por que D está correta:** Glue DataBrew é a interface visual de preparação de dados — permite limpar, normalizar e transformar datasets sem código.

❌ **Por que as outras estão erradas:**
- **A)** SageMaker Endpoints são para deploy de modelos (inferência), não preparação de dados.
- **C)** Bedrock é para IA generativa com Foundation Models, não ETL.
- **E)** Fraud Detector é para detecção de fraude, não preparação de dados.

</details>



---

### Questão 6

Uma startup de saúde quer criar um modelo de ML para prever risco cardiovascular usando dados tabulares (idade, colesterol, pressão arterial, etc.). A equipe tem um cientista de dados júnior que conhece Python básico. Quer a abordagem que AUTOMATIZE ao máximo a seleção de algoritmo e hiperparâmetros. Qual serviço é MAIS adequado?

A) Amazon SageMaker Canvas — interface visual sem código  
B) Amazon SageMaker Autopilot — AutoML que testa múltiplos algoritmos automaticamente  
C) Amazon Bedrock — usar um LLM para analisar os dados  
D) Amazon Comprehend — classificação pré-treinada  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Amazon SageMaker Autopilot — AutoML que testa múltiplos algoritmos automaticamente**

✅ **Por que B está correta:** Autopilot é AutoML: você fornece os dados, ele testa múltiplos algoritmos (XGBoost, linear, etc.) com diferentes hiperparâmetros automaticamente e retorna o melhor modelo. O cientista júnior com Python básico consegue usar no SageMaker Studio.

❌ **Por que as outras estão erradas:**
- **A)** Canvas é no-code para analistas de NEGÓCIO sem programação. O cientista sabe Python e precisa de mais controle/automação avançada.
- **C)** Bedrock/LLMs não são para previsão tabular (dados numéricos estruturados) — são para geração de texto.
- **D)** Comprehend faz NLP (sentimento, entidades) — não treina modelos customizados com dados tabulares.

</details>

---

### Questão 7

Uma empresa de varejo com 200 lojas precisa de previsão de demanda para 50.000 SKUs considerando sazonalidade, promoções e feriados. A equipe de supply chain NÃO tem experiência em ML e precisa de uma solução totalmente gerenciada que se integre com dados de séries temporais do S3. Qual serviço é MAIS adequado?

A) Amazon SageMaker com algoritmo DeepAR customizado  
B) Amazon Forecast com dados de séries temporais e metadados de itens  
C) Amazon Personalize para recomendar produtos baseado em demanda  
D) Amazon Bedrock para analisar tendências de vendas com IA generativa  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Amazon Forecast com dados de séries temporais e metadados de itens**

✅ **Por que B está correta:** Forecast é totalmente gerenciado, projetado para séries temporais com variáveis externas (promoções, feriados). Não requer experiência ML — importa dados do S3 e gera previsões automaticamente.

❌ **Por que as outras estão erradas:**
- **A)** SageMaker com DeepAR requer expertise ML para configurar, treinar e deployar — não é "totalmente gerenciado" para equipe sem experiência.
- **C)** Personalize recomenda itens a usuários individuais — não prevê demanda agregada por loja/SKU.
- **D)** LLMs não fazem previsão quantitativa confiável de séries temporais — são para texto.

</details>

---

### Questão 8

Uma empresa precisa moderar conteúdo visual (imagens) em uma plataforma de mídia social. O sistema deve detectar automaticamente: nudez, violência e texto ofensivo em imagens. A equipe quer usar serviços pré-treinados sem criar modelos. Qual serviço AWS é MAIS adequado?

A) Amazon Textract para extrair texto das imagens  
B) Amazon Rekognition para moderação de conteúdo (nudez, violência) e detecção de texto  
C) Amazon Comprehend para analisar o conteúdo textual das imagens  
D) Amazon Bedrock Guardrails para filtrar conteúdo inadequado  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Amazon Rekognition para moderação de conteúdo e detecção de texto**

✅ **Por que B está correta:** Rekognition oferece Content Moderation (detecta nudez, violência, drogas em imagens) E Text Detection (extrai texto de imagens). Ambos pré-treinados, sem necessidade de modelos customizados.

❌ **Por que as outras estão erradas:**
- **A)** Textract extrai texto de DOCUMENTOS (PDFs, formulários), não faz moderação de conteúdo visual.
- **C)** Comprehend analisa texto ESCRITO — não processa imagens diretamente.
- **D)** Guardrails filtra texto de LLMs — não analisa imagens.

</details>

---

### Questão 9

Um banco quer implementar um sistema que automaticamente detecte transações fraudulentas em tempo real. A equipe de fraude NÃO tem cientistas de dados e quer um serviço que já inclua modelos pré-treinados para fraude, aceitando regras de negócio customizáveis. Qual serviço é MAIS adequado?

A) Amazon SageMaker para treinar um modelo customizado de detecção de fraude  
B) Amazon Fraud Detector — serviço gerenciado com modelos pré-treinados para fraude  
C) Amazon GuardDuty para detectar ameaças de segurança  
D) Amazon Macie para encontrar dados sensíveis  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Amazon Fraud Detector — serviço gerenciado com modelos pré-treinados para fraude**

✅ **Por que B está correta:** Fraud Detector é um serviço gerenciado que combina modelos de ML pré-treinados pela AWS (baseados em 20+ anos de experiência da Amazon) com regras de negócio customizáveis. Não requer expertise em ML.

❌ **Por que as outras estão erradas:**
- **A)** SageMaker requer cientistas de dados para construir e treinar modelos — o cenário diz que a equipe NÃO tem essa expertise.
- **C)** GuardDuty detecta ameaças de segurança em contas AWS (acesso não autorizado, malware) — não fraude em transações financeiras.
- **D)** Macie detecta dados sensíveis (PII) armazenados no S3 — não é para detecção de fraude transacional.

</details>

---

### Questão 10

Uma empresa global quer construir um chatbot multilíngue para atendimento ao cliente que entenda intents, extraia slots (informações) das frases do usuário e integre com backends existentes. O chatbot deve suportar voz e texto. Qual serviço AWS é projetado especificamente para isso?

A) Amazon Comprehend para entender a intenção do texto  
B) Amazon Lex para construir interfaces conversacionais com NLU  
C) Amazon Polly para converter as respostas em fala  
D) Amazon Q Business para responder perguntas sobre documentos internos  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Amazon Lex para construir interfaces conversacionais com NLU**

✅ **Por que B está correta:** Lex é o serviço de construção de chatbots da AWS. Suporta: NLU (intents + slots), voz e texto, integração com Lambda/backends, e múltiplos idiomas. É a mesma tecnologia do Alexa.

❌ **Por que as outras estão erradas:**
- **A)** Comprehend ANALISA texto (sentimento, entidades) mas não constrói chatbots conversacionais com fluxo de diálogo.
- **C)** Polly converte texto em fala (TTS) — é um COMPONENTE de output, não uma plataforma de chatbot completa.
- **D)** Q Business responde perguntas sobre documentos corporativos — não é um framework de chatbot com intents/slots/integração de backend.

</details>
