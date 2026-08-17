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

Uma empresa quer permitir que funcionários façam perguntas em linguagem natural sobre documentos internos e recebam respostas precisas. Qual serviço é mais adequado?

A) Amazon Athena  
B) Amazon Kendra  
C) Amazon Comprehend  
D) Amazon Translate  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Amazon Kendra**

✅ **Por que B está correta:** Amazon Kendra é um serviço de busca empresarial inteligente que usa NLP para entender perguntas em linguagem natural e encontrar respostas precisas em documentos corporativos.

❌ **Por que as outras estão erradas:**
- **A)** Athena executa consultas SQL em dados no S3 — requer SQL, não linguagem natural.
- **C)** Comprehend analisa texto (sentimento, entidades) mas não faz busca em documentos.
- **D)** Translate traduz entre idiomas, não busca informação.

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

