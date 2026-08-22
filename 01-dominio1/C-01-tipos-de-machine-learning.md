# Conceitos Básicos de IA e Tipos de Machine Learning

## Hierarquia de Conceitos

A prova AIF-C01 exige que você saiba **definir e diferenciar** os termos fundamentais de IA. Eles formam uma hierarquia:

```
IA (Inteligência Artificial)
 └── ML (Machine Learning)
      └── Deep Learning
           └── IA Generativa (GenAI)

IA Agêntica → padrão arquitetural que combina FM + raciocínio + ferramentas
```

### Definições

| Termo | Definição |
|-------|-----------|
| **Inteligência Artificial (IA)** | Campo amplo da ciência da computação que busca criar sistemas capazes de realizar tarefas que normalmente exigem inteligência humana (percepção, raciocínio, decisão, linguagem). |
| **Machine Learning (ML)** | Subconjunto da IA em que sistemas aprendem padrões a partir de dados, sem serem explicitamente programados para cada tarefa. |
| **Deep Learning (DL)** | Subconjunto de ML que usa **redes neurais** com múltiplas camadas (profundas) para aprender representações complexas dos dados. |
| **Rede Neural** | Modelo computacional inspirado no cérebro humano, composto por camadas de neurônios artificiais que processam dados de entrada e geram saídas. |
| **IA Generativa (GenAI)** | Subconjunto de deep learning focado em **gerar novos conteúdos** (texto, imagem, áudio, código, vídeo) a partir de padrões aprendidos em grandes volumes de dados. |
| **Large Language Model (LLM)** | Tipo de foundation model treinado em grandes volumes de texto, especializado em tarefas de linguagem natural. |
| **IA Agêntica** | Padrão arquitetural em que um sistema de IA combina um modelo de base com capacidades de **planejamento, raciocínio, memória e uso de ferramentas** para executar tarefas de forma autônoma ou semi-autônoma. |

### Outros termos fundamentais

| Termo | Definição |
|-------|-----------|
| **Modelo** | Representação matemática treinada para fazer previsões ou gerar saídas a partir de dados de entrada. |
| **Algoritmo** | Conjunto de regras ou procedimentos que o modelo segue para aprender a partir dos dados. |
| **Treinamento** | Processo em que o modelo ajusta seus parâmetros internos usando dados para melhorar seu desempenho na tarefa. |
| **Inferência** | Uso do modelo já treinado para gerar previsões ou saídas a partir de dados novos. |
| **Viés (Bias)** | Erro sistemático que pode surgir dos dados ou do modelo, potencialmente levando a resultados injustos ou imprecisos. |
| **Imparcialidade (Fairness)** | Propriedade desejada de um sistema de IA que trata diferentes grupos de forma equitativa. |
| **Ajuste (Fine-tuning)** | Processo de adaptar um modelo pré-treinado a uma tarefa ou domínio específico usando dados adicionais. |
| **Visão Computacional** | Área da IA que permite a máquinas interpretar e processar informações visuais (imagens, vídeos). |
| **Processamento de Linguagem Natural (NLP/PLN)** | Área da IA que permite a máquinas compreender, interpretar e gerar linguagem humana. |

### Semelhanças e diferenças

| Aspecto | IA | ML | Deep Learning | GenAI | IA Agêntica |
|---------|----|----|---------------|-------|-------------|
| Escopo | Mais amplo | Subconjunto de IA | Subconjunto de ML | Subconjunto de DL | Padrão arquitetural |
| Aprende com dados? | Nem sempre | Sim | Sim | Sim | Usa modelos treinados |
| Requer redes neurais? | Não | Não necessariamente | Sim | Sim | Tipicamente sim (usa FMs) |
| Gera conteúdo novo? | Não necessariamente | Não necessariamente | Não necessariamente | Sim (foco principal) | Pode gerar como parte da execução |
| Executa tarefas autonomamente? | Depende | Não | Não | Não por si só | Sim (planejamento + ferramentas) |

> **DICA PARA A PROVA:** Quando a questão pergunta "qual é a relação entre X e Y", pense na hierarquia. ML está contido em IA. GenAI está contida em DL. IA Agêntica não é um "nível" da hierarquia — é um padrão que *usa* FMs/GenAI como componente.

---

## Tipos de Aprendizado

### Aprendizado Supervisionado (Supervised Learning)

O modelo treina com **dados rotulados** — cada entrada (input) tem uma resposta correta associada (label). O objetivo é aprender a mapear entrada → saída para fazer previsões em dados novos.

#### Classificação
- A saída é uma **categoria discreta** (classe)
- Exemplos: spam/não-spam, fraude/legítima, diagnóstico positivo/negativo
- Algoritmos comuns: Logistic Regression, Decision Trees, Random Forest, SVM, Neural Networks

#### Regressão
- A saída é um **valor numérico contínuo**
- Exemplos: prever preço de imóvel, demanda de vendas, tempo de entrega
- Algoritmos comuns: Linear Regression, Polynomial Regression, Neural Networks

#### Quando identificar na prova
Palavras-chave: "dados rotulados", "histórico classificado", "prever uma categoria", "prever um valor numérico", "dados de treino com respostas conhecidas".

---

### Aprendizado Não-Supervisionado (Unsupervised Learning)

O modelo trabalha com **dados sem rótulos**. Não existe resposta "correta" — o objetivo é encontrar padrões, estruturas ou agrupamentos ocultos nos dados.

#### Clustering (Agrupamento)
- Agrupa dados similares em clusters
- Exemplos: segmentação de clientes, agrupamento de documentos por tema
- Algoritmos comuns: K-Means, DBSCAN, Hierarchical Clustering

#### Redução de Dimensionalidade
- Reduz o número de variáveis mantendo a informação essencial
- Útil para visualização e pré-processamento
- Algoritmos comuns: PCA, t-SNE

#### Detecção de Anomalias (abordagem não-supervisionada)
- Identifica pontos fora do padrão quando não há rótulos — o modelo aprende o "normal" e detecta desvios
- Exemplos: detectar falhas em equipamentos, transações incomuns

> **CUIDADO:** Detecção de anomalias pode ser feita com aprendizado supervisionado (quando há exemplos rotulados de anomalias) ou não-supervisionado (quando não há). O tipo depende dos dados disponíveis.

#### Quando identificar na prova
Palavras-chave: "sem rótulos", "agrupar", "segmentar", "encontrar padrões", "dados não categorizados", "descobrir estruturas ocultas".

---

### Aprendizado por Reforço (Reinforcement Learning)

Um **agente** interage com um **ambiente**, executa **ações**, observa o **estado** resultante e recebe **recompensas** (positivas) ou **penalidades** (negativas). O objetivo é aprender uma **política (policy)** que maximize a recompensa acumulada ao longo do tempo.

#### Conceitos-chave

| Conceito | Descrição |
|----------|-----------|
| **Agente** | O "aprendiz" que toma decisões |
| **Ambiente** | O mundo com o qual o agente interage |
| **Estado** | Situação atual do ambiente |
| **Ação** | O que o agente pode fazer |
| **Recompensa** | Feedback numérico (positivo ou negativo) |
| **Política** | Estratégia aprendida (estado → ação) |

#### Exemplos
- AWS DeepRacer (carro autônomo em pista virtual)
- Jogos (AlphaGo, Atari)
- Robótica, otimização de rotas
- RLHF (Reinforcement Learning from Human Feedback) — usado para alinhar LLMs

#### Quando identificar na prova
Palavras-chave: "tentativa e erro", "recompensa", "penalidade", "agente interagindo com ambiente", "decisões sequenciais", "maximizar recompensa", "DeepRacer".

---

### Aprendizado Semi-Supervisionado

Combinação: **poucos dados rotulados** + **muitos dados não-rotulados**.

- Útil quando rotular dados é caro ou demorado (ex: imagens médicas)
- O modelo usa os poucos rótulos para guiar o aprendizado nos dados não-rotulados

#### Quando identificar na prova
Palavras-chave: "poucos dados rotulados", "rotulagem cara", "grande volume sem rótulo + alguns com rótulo".

---

### Aprendizado Auto-Supervisionado (Self-Supervised Learning)

O modelo **gera seus próprios rótulos** a partir dos dados de entrada, sem anotação humana.

- Técnica: mascarar parte da entrada e treinar o modelo para prever a parte oculta
- Exemplo: masked language modeling (base do BERT), next-token prediction (base do GPT)
- É a base do pré-treinamento dos **foundation models** modernos
- Permite treinar com enormes quantidades de dados não-rotulados

#### Quando identificar na prova
Palavras-chave: "pré-treinamento de LLMs", "modelo gera seus próprios rótulos", "foundation models pré-treinados".

---

## Resumo Comparativo — Tipos de Aprendizado

| Tipo | Dados | Objetivo | Exemplo |
|------|-------|----------|---------|
| Supervisionado | Rotulados | Prever categoria ou valor | Detectar fraude |
| Não-Supervisionado | Sem rótulos | Encontrar padrões | Segmentar clientes |
| Reforço | Interação com ambiente | Maximizar recompensa | DeepRacer, RLHF |
| Semi-Supervisionado | Poucos rótulos + muitos sem | Aprender com pouca supervisão | Imagens médicas |
| Auto-Supervisionado | Sem rótulos (cria os próprios) | Pré-treinar modelos | Treinamento de FMs |

---

## Tipos de Dados em Modelos de IA

O Exam Guide exige reconhecer os diferentes tipos de dados usados em IA/ML.

### Por presença de rótulo

| Tipo | Descrição | Uso principal |
|------|-----------|---------------|
| **Rotulados (Labeled)** | Cada exemplo tem uma resposta/classe associada | Aprendizado supervisionado |
| **Não-rotulados (Unlabeled)** | Dados sem resposta conhecida | Aprendizado não-supervisionado, pré-treinamento |

### Por estrutura

| Tipo | Descrição | Exemplos |
|------|-----------|----------|
| **Estruturados** | Organizados em formato fixo (linhas e colunas) | Bancos de dados relacionais, planilhas, CSV |
| **Não-estruturados** | Sem formato fixo predefinido | Texto livre, imagens, áudio, vídeo |
| **Semi-estruturados** | Possuem alguma organização mas não se encaixam em tabelas | JSON, XML, logs |

### Por modalidade

| Tipo | Descrição | Serviço AWS relevante |
|------|-----------|----------------------|
| **Tabulares** | Dados em linhas e colunas (estruturados) | Amazon SageMaker AI, Amazon Redshift |
| **Texto** | Linguagem natural, documentos | Amazon Comprehend, Amazon Bedrock |
| **Imagem** | Fotos, imagens médicas, satélite | Amazon Rekognition |
| **Áudio/Fala** | Gravações de voz, músicas | Amazon Transcribe, Amazon Polly |
| **Séries temporais** | Dados ordenados cronologicamente | Amazon Forecast |
| **Vídeo** | Sequências de imagens com contexto temporal | Amazon Rekognition Video |

> **DICA PARA A PROVA:** Quando a questão menciona "dados tabulares" ou "dados estruturados com colunas", geralmente aponta para ML tradicional (supervisionado). Quando menciona "texto livre", "imagens" ou "áudio", pode apontar para deep learning ou serviços de IA pré-treinados.

---

## Tipos de Inferência

Inferência é o uso do modelo treinado para gerar previsões ou outputs em dados novos. A AIF-C01 exige reconhecer os diferentes modos de inferência.

| Modo | Descrição | Quando usar | Exemplo |
|------|-----------|-------------|---------|
| **Real-time (tempo real)** | Resposta imediata (milissegundos a poucos segundos). Endpoint sempre ativo aguardando requisições. | Aplicações interativas que precisam de resposta instantânea | Chatbot, detecção de fraude em transação |
| **Batch (lote)** | Processa um grande conjunto de dados de uma vez, sem necessidade de resposta imediata. | Grandes volumes de dados, processamento periódico | Classificar milhões de emails, gerar relatórios noturnos |
| **Assíncrona** | Requisição é enviada e a resposta é entregue depois (fila). Útil para payloads grandes ou processamento demorado. | Inputs grandes, tolerância a latência maior | Processar documentos longos, gerar vídeos |
| **Serverless** | Endpoint que escala automaticamente (incluindo para zero) sem infraestrutura provisionada. Paga por uso. | Tráfego imprevisível ou intermitente, otimização de custo | APIs com uso esporádico |

> **CUIDADO:** "Serverless inference" no contexto de SageMaker AI refere-se a uma modalidade de endpoint gerenciado que escala para zero quando ocioso. **Não deve ser confundida com AWS Lambda**, embora Lambda também seja serverless. São serviços distintos com propósitos diferentes.

> **DICA PARA A PROVA:** Se a questão menciona "tráfego imprevisível" + "otimizar custos" → serverless. Se menciona "processar milhões de registros periodicamente" → batch. Se menciona "resposta instantânea para o usuário" → real-time.

---

## Serviços AWS Relacionados

| Serviço | Relação com tipos de ML |
|---------|------------------------|
| **Amazon SageMaker AI** | Plataforma completa — suporta todos os tipos de ML (treino, deploy, monitoramento) |
| **Amazon Personalize** | Utiliza técnicas incluindo reinforcement learning para recomendações |
| **AWS DeepRacer** | Aprendizado por reforço |
| **Amazon Comprehend** | Modelos pré-treinados de NLP (supervisionado) |
| **Amazon Rekognition** | Modelos pré-treinados de visão computacional (deep learning) |
| **Amazon Forecast** | Previsão de séries temporais (supervisionado) |
| **Amazon Fraud Detector** | Detecção de fraude (classificação supervisionada) |
| **Amazon Bedrock** | Acesso a foundation models (GenAI, deep learning) |

---
