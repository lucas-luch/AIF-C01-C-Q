# Serviços AWS de ML

## Visão Geral

A prova AIF-C01 testa sua capacidade de **escolher o serviço certo** para cada cenário. Você não precisa saber configurar APIs — precisa saber **quando usar cada um**.

---

## Categorias de Serviços

### 1. Plataforma de ML (Build Your Own)

| Serviço | O que faz | Quando usar |
|---------|-----------|-------------|
| **Amazon SageMaker** | Plataforma completa: notebooks, treino, deploy, monitoramento | Quando precisa construir modelo customizado |
| **SageMaker Canvas** | ML sem código (visual, drag-and-drop) | Analistas de negócio sem experiência em código |
| **SageMaker Autopilot** | AutoML — gera modelos automaticamente | Quando quer experimentar rápido sem escolher algoritmo |
| **SageMaker JumpStart** | Hub de modelos pré-treinados para deploy rápido | Quando quer usar um modelo existente como ponto de partida |

### 2. Serviços de IA Pré-treinados (APIs Prontas)

Não precisa treinar — chama a API e recebe a resposta.

| Serviço | Categoria | O que faz |
|---------|-----------|-----------|
| **Amazon Comprehend** | NLP | Sentimento, entidades, idioma, tópicos, PII |
| **Amazon Translate** | NLP | Tradução entre idiomas |
| **Amazon Transcribe** | Áudio | Fala → texto (speech-to-text) |
| **Amazon Polly** | Áudio | Texto → fala (text-to-speech) |
| **Amazon Lex** | Conversação | Chatbots com NLU |
| **Amazon Rekognition** | Visão | Objetos, faces, moderação, texto em imagens |
| **Amazon Textract** | Documentos | Extrair texto, formulários e tabelas de documentos |
| **Amazon Kendra** | Busca | Busca empresarial inteligente com NLP |
| **Amazon Personalize** | Recomendação | Recomendações personalizadas |
| **Amazon Forecast** | Séries temporais | Previsão de demanda, vendas, etc. |
| **Amazon Fraud Detector** | Segurança | Detectar fraude em transações |

### 3. IA Generativa

| Serviço | O que faz | Quando usar |
|---------|-----------|-------------|
| **Amazon Bedrock** | Acesso serverless a Foundation Models | Construir aplicações com IA generativa |
| **Amazon Q** | Assistente de IA generativa | Produtividade empresarial e desenvolvimento |
| **Amazon Q Developer** | Assistente de código | Geração, explicação e transformação de código |
| **PartyRock** | Playground de apps com GenAI | Experimentar sem código, prototipagem rápida |

### 4. Dados e Preparação

| Serviço | O que faz |
|---------|-----------|
| **Amazon S3** | Armazenamento de datasets e artefatos |
| **AWS Glue** | ETL serverless (extrair, transformar, carregar) |
| **AWS Glue DataBrew** | Preparação visual de dados (limpeza sem código) |
| **Amazon Athena** | Consultas SQL interativas em dados no S3 |
| **AWS Lake Formation** | Gerenciar data lakes com governança |
| **Amazon EMR** | Big data processing (Spark, Hadoop) |

---

## Pares Comuns na Prova

| Cenário | Serviço correto | Serviço "distrator" |
|---------|----------------|---------------------|
| Extrair texto de PDF | **Textract** | Comprehend (analisa texto, não extrai de docs) |
| Analisar sentimento de texto | **Comprehend** | Textract (extrai texto, não analisa) |
| Traduzir texto | **Translate** | Comprehend (detecta idioma mas não traduz) |
| Áudio → texto | **Transcribe** | Polly (faz o inverso: texto → áudio) |
| Texto → áudio | **Polly** | Transcribe (faz o inverso: áudio → texto) |
| Chatbot conversacional | **Lex** | Comprehend (analisa mas não conversa) |
| Busca inteligente em docs | **Kendra** | Athena (SQL, não busca semântica) |
| Recomendações | **Personalize** | Forecast (previsão, não recomendação) |
| Previsão de demanda | **Forecast** | Personalize (recomendação, não previsão) |
| Detectar fraude | **Fraud Detector** | Rekognition (imagens, não transações) |
| Detectar objetos em imagem | **Rekognition** | Textract (texto em docs, não objetos) |

---

## SageMaker — Componentes Importantes

| Componente | Função |
|-----------|--------|
| **Studio** | IDE web para ML (notebooks, experimentos) |
| **Training Jobs** | Treinar modelos em infraestrutura gerenciada |
| **Endpoints** | Deploy real-time (API) |
| **Batch Transform** | Inferência em lote |
| **Model Monitor** | Monitorar drift e qualidade em produção |
| **Clarify** | Detectar viés e explicar previsões |
| **Autopilot** | AutoML automático |
| **JumpStart** | Modelos pré-treinados prontos para deploy |
| **Canvas** | ML visual sem código |
| **Feature Store** | Repositório centralizado de features |
| **Pipelines** | CI/CD para ML (MLOps) |

---

## Regra de Ouro para a Prova

1. **Problema padrão + não quer treinar modelo?** → Serviço de IA pré-treinado (Comprehend, Rekognition, etc.)
2. **Precisa de modelo customizado?** → SageMaker
3. **Quer usar IA generativa (texto, código, imagens)?** → Amazon Bedrock
4. **Quer ML sem código?** → SageMaker Canvas
5. **Quer experimentar GenAI sem código?** → PartyRock

---

*Próximo: Mini-simulado Domínio 1*
