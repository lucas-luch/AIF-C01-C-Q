# Tipos de Tarefas e Casos de Uso de IA

## Visão Geral

Cada problema de negócio se mapeia a um tipo de tarefa de ML ou IA. A prova AIF-C01 exige que você saiba **identificar a tarefa correta** a partir de um cenário, reconhecer **quando IA é (ou não é) apropriada**, e distinguir **quando usar FM vs. ML tradicional**.

---

## Tarefas de ML Tradicionais

*(Para definições detalhadas de cada tipo de aprendizado, ver C-01)*

### Classificação

Prever uma **categoria discreta** (classe) a partir dos dados de entrada.

| Subtipo | Descrição | Exemplo | Serviço AWS |
|---------|-----------|---------|-------------|
| **Binária** | Duas classes | Fraude/legítima | Amazon Fraud Detector |
| **Multiclasse** | Três+ classes | Tipo de produto, idioma | Amazon Comprehend |
| **Multi-label** | Múltiplas classes por item | Artigo sobre "tech" E "negócios" | Amazon SageMaker AI |

### Regressão

Prever um **valor numérico contínuo**.
- Exemplos: preço de imóvel, demanda de vendas, tempo de entrega
- Serviços: Amazon SageMaker AI, Amazon Forecast (séries temporais)

**Como distinguir na prova:** Se a resposta é um **número** → Regressão. Se é uma **categoria** → Classificação.

### Clustering (Agrupamento)

Encontrar **grupos naturais** nos dados sem categorias predefinidas.
- Não-supervisionado (sem rótulos)
- Exemplos: segmentar clientes por comportamento, agrupar documentos por tema
- Serviços: Amazon SageMaker AI (K-Means built-in), Amazon Personalize (segmentação)

### Detecção de Anomalias

Identificar **pontos fora do padrão** (outliers) nos dados.
- Exemplos: transações fraudulentas, falhas em equipamentos, intrusões em rede
- Pode ser supervisionada (exemplos rotulados de anomalias) ou não-supervisionada (aprender o "normal")
- Serviços: Amazon Fraud Detector, Amazon SageMaker AI (Random Cut Forest)

### Recomendação

Sugerir **itens relevantes** com base em preferências e comportamento.
- Abordagens: filtragem colaborativa, filtragem por conteúdo, híbrida
- Serviço: **Amazon Personalize** (utiliza múltiplas técnicas, incluindo reinforcement learning)

### Previsão de Séries Temporais (Forecasting)

Prever valores futuros com base em dados históricos ordenados no tempo.
- Exemplos: prever demanda de estoque, receita futura, consumo de energia
- Diferente de regressão simples: considera a dimensão temporal, sazonalidade, tendências
- Serviço: **Amazon Forecast**

---

## Tarefas de NLP (Processamento de Linguagem Natural)

| Tarefa | Descrição | Serviço AWS |
|--------|-----------|-------------|
| Análise de sentimento | Classificar como positivo/negativo/neutro | Amazon Comprehend |
| Extração de entidades (NER) | Identificar nomes, datas, locais no texto | Amazon Comprehend |
| Detecção de PII | Identificar informações pessoais sensíveis | Amazon Comprehend |
| Tradução | Converter entre idiomas | Amazon Translate |
| Transcrição (speech-to-text) | Áudio → texto | Amazon Transcribe |
| Síntese de fala (text-to-speech) | Texto → áudio | Amazon Polly |
| Chatbot / Assistente | Conversa interativa com NLU | Amazon Lex |
| Busca semântica | Encontrar documentos relevantes por significado | Amazon Kendra |

---

## Tarefas de Visão Computacional

| Tarefa | Descrição | Serviço AWS |
|--------|-----------|-------------|
| Detecção de objetos | Encontrar e localizar objetos em imagens | Amazon Rekognition |
| Reconhecimento facial | Identificar/comparar rostos | Amazon Rekognition |
| OCR (extração de texto) | Extrair texto de imagens/documentos | Amazon Textract |
| Moderação de conteúdo | Detectar conteúdo impróprio | Amazon Rekognition |
| Classificação de imagem | Categorizar imagens | Amazon Rekognition |

---

## IA Agêntica como Caso de Uso

Agentes de IA representam uma aplicação que combina modelos de base com capacidades autônomas para executar tarefas complexas.

**Exemplos de aplicação:**
- Automação de workflows empresariais (pesquisa → análise → ação)
- Assistentes que acessam ferramentas e APIs externas para resolver problemas
- Orquestração de múltiplas etapas sem intervenção manual a cada passo

**Serviços AWS:** Agentes do Amazon Bedrock, Strands Agents, Amazon Bedrock AgentCore

> **DICA PARA A PROVA:** Se a questão descreve um cenário onde o sistema precisa "planejar etapas", "usar ferramentas" ou "executar ações automaticamente", pense em IA agêntica / agents.

---

## Bases de Conhecimento (Knowledge Bases)

Aplicação de IA que conecta modelos a fontes de dados atualizadas para responder perguntas com informações específicas da organização.

- Implementação típica: RAG (Retrieval-Augmented Generation)
- Serviço AWS: **Knowledge Bases for Amazon Bedrock**
- Exemplos: helpdesk interno, busca em documentação técnica, assistente de vendas

---

## Quando IA/ML É Apropriado

| Cenário | IA/ML agrega valor |
|---------|-------------------|
| Decisões baseadas em padrões em grandes volumes de dados | ✅ Sim |
| Tarefas repetitivas que precisam de escalabilidade | ✅ Sim |
| Automação de processos que envolvem linguagem, visão ou previsão | ✅ Sim |
| Personalização em escala (recomendações, conteúdo) | ✅ Sim |
| Auxílio à tomada de decisão humana | ✅ Sim |

## Quando IA/ML NÃO É Apropriado

| Cenário | Por que não usar ML |
|---------|-------------------|
| Resultado determinístico necessário (sempre a mesma saída para a mesma entrada) | ML é probabilístico — pode gerar outputs diferentes |
| Custo-benefício negativo | Custo de desenvolver/operar ML supera o valor gerado |
| Dados insuficientes para treinar ou avaliar | Modelo não terá base para aprender padrões |
| Regra simples resolve o problema | Complexidade desnecessária (ex: if/else resolve) |
| Requisitos de explicabilidade completa em cada decisão | Muitos modelos de DL/FM são caixas-pretas |

> **DICA PARA A PROVA:** Se a questão descreve um cenário com "resultado exato necessário" ou "lógica de negócio fixa", ML provavelmente NÃO é a resposta. Se descreve "análise custo-benefício mostra que o investimento não se justifica", também não.

---

## FM vs. ML Tradicional — Quando Escolher

| Critério | Foundation Model (FM) | ML Tradicional |
|----------|----------------------|----------------|
| **Tipo de dados** | Texto, imagem, áudio, multimodal | Dados tabulares/estruturados |
| **Tarefa** | Geração, resumo, conversação, raciocínio | Classificação, regressão, clustering em dados estruturados |
| **Explicabilidade** | Geralmente baixa (caixa-preta) | Pode ser alta (árvores de decisão, regressão logística) |
| **Requisitos regulatórios** | Mais difícil demonstrar conformidade | Mais fácil auditar e explicar |
| **Volume de dados de treino** | Pode funcionar com poucos exemplos (few-shot, zero-shot) | Geralmente precisa de mais dados rotulados |
| **Custo de inferência** | Geralmente mais alto (tokens) | Geralmente mais baixo (endpoints menores) |
| **Flexibilidade** | Alta (adapta a múltiplas tarefas via prompt) | Cada modelo para uma tarefa específica |
| **Prototipagem** | Rápida (prompt engineering) | Mais lenta (coleta de dados → treino) |

### Quando FM é mais apropriado:
- Tarefas de linguagem natural (geração, resumo, Q&A, tradução)
- Prototipagem rápida (testar ideias com prompt engineering)
- Dados não-estruturados (texto livre, imagens)
- Quando flexibilidade entre tarefas é importante

### Quando ML tradicional é mais apropriado:
- Dados tabulares/estruturados (vendas, transações, sensores)
- Requisitos de explicabilidade (regulação, auditoria)
- Previsões numéricas precisas (regressão)
- Custo de inferência é crítico
- Problema bem-definido com dados rotulados disponíveis

> **DICA PARA A PROVA:** Se a questão menciona "dados tabulares" + "regulação" + "explicabilidade", a resposta tende a ML tradicional. Se menciona "texto livre" + "geração" + "poucos exemplos", tende a FM.

---

## Resumo para a Prova — Mapeamento Cenário → Tarefa/Serviço

| Cenário descrito | Tarefa | Serviço AWS provável |
|-----------------|--------|---------------------|
| "Prever se é fraude ou legítima" | Classificação binária | Amazon Fraud Detector |
| "Prever o valor de vendas" | Regressão / Forecasting | Amazon Forecast, SageMaker AI |
| "Agrupar clientes por comportamento" | Clustering | SageMaker AI (K-Means) |
| "Detectar transações incomuns" | Detecção de anomalias | Amazon Fraud Detector |
| "Recomendar produtos" | Recomendação | Amazon Personalize |
| "Analisar sentimento de reviews" | NLP - Sentimento | Amazon Comprehend |
| "Extrair texto de documentos" | OCR | Amazon Textract |
| "Identificar objetos em imagens" | Visão computacional | Amazon Rekognition |
| "Prever demanda futura" | Séries temporais | Amazon Forecast |
| "Responder perguntas sobre docs internos" | Knowledge base / RAG | Knowledge Bases for Amazon Bedrock |
| "Automatizar workflow com múltiplas etapas" | IA agêntica | Agentes do Amazon Bedrock |
| "Gerar conteúdo de texto/código" | IA generativa | Amazon Bedrock |

---
