# Serviços AWS de IA/ML

## Visão Geral

A prova AIF-C01 testa sua capacidade de **escolher o serviço certo** para cada cenário. Você não precisa saber configurar APIs — precisa saber **quando usar cada um** e entender a **diferença entre serviço, feature, modelo e framework**.

### Conceitos importantes

| Conceito | O que é | Exemplo |
|----------|---------|---------|
| **Serviço** | Produto AWS gerenciado com funcionalidade específica | Amazon Bedrock, Amazon SageMaker AI |
| **Feature/Recurso** | Funcionalidade dentro de um serviço | SageMaker Model Monitor (feature do SageMaker AI) |
| **Modelo** | Artefato de IA/ML que gera previsões ou conteúdo | Claude, Amazon Nova, Llama |
| **Framework** | Biblioteca para construir modelos | PyTorch, TensorFlow |
| **Modalidade de deploy** | Como o modelo é disponibilizado em produção | Real-time endpoint, batch, serverless |

---

## 1. Plataforma de ML (Build Your Own)

| Serviço | O que faz | Quando usar |
|---------|-----------|-------------|
| **Amazon SageMaker AI** | Plataforma completa: notebooks, treino, deploy, monitoramento | Construir e operar modelos customizados |
| **SageMaker Canvas** | ML sem código (visual, drag-and-drop) | Analistas de negócio sem experiência em código |
| **SageMaker Autopilot** | AutoML — gera modelos automaticamente | Experimentar rápido sem escolher algoritmo manualmente |
| **SageMaker JumpStart** | Hub de modelos pré-treinados (open-source e proprietários) para deploy | Usar/customizar um modelo existente rapidamente |

---

## 2. Serviços de IA Pré-treinados (APIs Prontas)

Não precisa treinar — chama a API e recebe a resposta.

| Serviço | Categoria | O que faz |
|---------|-----------|-----------|
| **Amazon Comprehend** | NLP | Sentimento, entidades, idioma, tópicos, PII |
| **Amazon Translate** | NLP | Tradução entre idiomas |
| **Amazon Transcribe** | Áudio | Fala → texto (speech-to-text) |
| **Amazon Polly** | Áudio | Texto → fala (text-to-speech) |
| **Amazon Lex** | Conversação | Chatbots com compreensão de linguagem natural (NLU) |
| **Amazon Rekognition** | Visão | Objetos, faces, moderação, texto em imagens, vídeo |
| **Amazon Textract** | Documentos | Extrair texto, formulários e tabelas de documentos |
| **Amazon Kendra** | Busca | Busca empresarial inteligente com NLP |
| **Amazon Personalize** | Recomendação | Recomendações personalizadas (múltiplas técnicas incluindo RL) |
| **Amazon Forecast** | Séries temporais | Previsão de demanda, vendas, etc. |
| **Amazon Fraud Detector** | Segurança | Detectar fraude em transações |

---

## 3. IA Generativa e Foundation Models

| Serviço | O que faz | Quando usar |
|---------|-----------|-------------|
| **Amazon Bedrock** | Acesso serverless a múltiplos foundation models (Claude, Nova, Llama, etc.) via API | Construir aplicações com GenAI sem gerenciar infraestrutura de modelo |
| **Amazon Nova** | Família de foundation models da AWS (otimizados para custo-performance) | Quando quer FMs nativos AWS com boa relação custo-benefício |
| **Agentes do Amazon Bedrock** | Criar agentes que usam FMs + ferramentas para executar tarefas | Automação de workflows com raciocínio e ações |
| **Amazon Bedrock AgentCore** | Infraestrutura gerenciada para deploy e governança de agentes | Segurança, identidade e controle de agentes em produção |
| **Amazon Q** | Assistente de IA generativa para produtividade empresarial e desenvolvimento | Perguntas sobre dados internos, geração de código, análise de negócio |
| **PartyRock** | Playground para criar apps com GenAI sem código | Experimentação e prototipagem rápida, educação |

---

## 4. Ferramentas de Desenvolvimento com IA

| Serviço | O que faz | Quando usar |
|---------|-----------|-------------|
| **Kiro** | IDE com IA integrada para desenvolvimento de software | Desenvolvimento assistido por IA (geração de código, specs, agentes) |
| **Strands Agents** | Framework open-source para construir agentes de IA | Desenvolver agentes customizados com controle total do código |
| **Amazon Q Developer** | Assistente de código dentro de IDEs | Geração, explicação, refatoração e debugging de código |

---

## 5. Dados, Analytics e Preparação

| Serviço | O que faz |
|---------|-----------|
| **Amazon S3** | Armazenamento de datasets e artefatos de modelo |
| **AWS Glue** | ETL serverless (extrair, transformar, carregar) |
| **AWS Glue DataBrew** | Preparação visual de dados (limpeza sem código) |
| **Amazon Athena** | Consultas SQL interativas em dados no S3 |
| **AWS Lake Formation** | Gerenciar data lakes com governança |
| **Amazon EMR** | Big data processing (Spark, Hadoop) |
| **Amazon Redshift** | Data warehouse para analytics |
| **Amazon Quick** | Dashboards e BI com IA integrada (ex-QuickSight) |

---

## 6. Migração e Modernização com IA

| Serviço | O que faz |
|---------|-----------|
| **AWS Transform** | Serviço de IA agêntica para migração e modernização de workloads (Windows, mainframe, VMware, código) |

---

## Pares Comuns na Prova (Diferenciação)

| Cenário | Serviço correto | Distrator comum | Diferença |
|---------|----------------|-----------------|-----------|
| Extrair texto de PDF/docs | **Textract** | Comprehend | Textract *extrai* de documentos; Comprehend *analisa* texto já extraído |
| Analisar sentimento de texto | **Comprehend** | Textract | Comprehend analisa significado; Textract extrai de imagens/docs |
| Traduzir texto | **Translate** | Comprehend | Comprehend detecta idioma mas não traduz |
| Áudio → texto | **Transcribe** | Polly | Polly faz o inverso (texto → áudio) |
| Texto → áudio | **Polly** | Transcribe | Transcribe faz o inverso (áudio → texto) |
| Chatbot conversacional | **Lex** | Comprehend | Lex gerencia diálogo; Comprehend apenas analisa texto |
| Busca inteligente em docs | **Kendra** | Athena | Kendra é busca semântica; Athena é SQL em dados estruturados |
| Recomendações | **Personalize** | Forecast | Personalize recomenda itens; Forecast prevê valores futuros |
| Previsão de demanda | **Forecast** | Personalize | Forecast faz forecasting; Personalize faz recomendação |
| Detectar fraude | **Fraud Detector** | Rekognition | Fraud Detector é para transações; Rekognition para imagens |
| Gerar texto/código com FM | **Bedrock** | SageMaker AI | Bedrock é acesso serverless a FMs; SageMaker é para treinar/deployar modelos próprios |
| Treinar modelo customizado | **SageMaker AI** | Bedrock | SageMaker treina modelos; Bedrock usa modelos prontos |

---

## SageMaker AI — Componentes Principais

| Componente | Função |
|-----------|--------|
| **Studio** | IDE web para ML (notebooks, experimentos) |
| **Training Jobs** | Treinar modelos em infraestrutura gerenciada |
| **Endpoints** | Deploy real-time (API) |
| **Batch Transform** | Inferência em lote |
| **Model Monitor** | Monitorar drift e qualidade em produção |
| **Clarify** | Detectar viés e explicar previsões |
| **Autopilot** | AutoML automático |
| **JumpStart** | Modelos pré-treinados prontos para deploy/fine-tuning |
| **Canvas** | ML visual sem código |
| **Feature Store** | Repositório centralizado de features |
| **Pipelines** | CI/CD para ML (MLOps) |
| **Model Registry** | Versionamento e catalogação de modelos |

---

## Quando Usar FM vs. ML Tradicional (Perspectiva de Serviço)

| Cenário | Abordagem | Serviço AWS |
|---------|-----------|-------------|
| Gerar/resumir/traduzir texto | FM (GenAI) | Amazon Bedrock, Amazon Nova |
| Classificar dados tabulares | ML tradicional | Amazon SageMaker AI |
| Detectar fraude em transações | ML tradicional (classificação) | Amazon Fraud Detector |
| Chatbot inteligente com contexto | FM + RAG | Amazon Bedrock + Knowledge Bases |
| Prever demanda numérica | ML tradicional (forecasting) | Amazon Forecast |
| Automação de workflow com decisões | FM + agente | Agentes do Bedrock, Strands Agents |
| Analisar sentimento | API pré-treinada | Amazon Comprehend |
| Problema padrão, não quer treinar | API pré-treinada | Comprehend, Rekognition, etc. |
| ML sem código para business analyst | AutoML | SageMaker Canvas |
| Experimentar GenAI sem código | Playground | PartyRock |

> **CUIDADO:** Não existe uma regra absoluta de "FM é sempre melhor" ou "ML tradicional é sempre melhor". A escolha depende do tipo de dados, requisitos de explicabilidade, custo, latência e complexidade do problema. Ver C-05 para critérios detalhados de decisão.

---

## Regras Práticas para a Prova

1. **Problema padrão de NLP/visão/áudio + não quer treinar?** → Serviço de IA pré-treinado (Comprehend, Rekognition, Transcribe, etc.)
2. **Precisa de modelo customizado com dados próprios?** → Amazon SageMaker AI
3. **Quer usar IA generativa (gerar texto, código, imagens)?** → Amazon Bedrock (acesso a múltiplos FMs) ou Amazon Nova (FM nativo AWS)
4. **Quer ML sem código para analistas?** → SageMaker Canvas
5. **Precisa de agente que executa tarefas autonomamente?** → Agentes do Amazon Bedrock ou Strands Agents
6. **Quer usar modelo open-source pré-treinado com deploy rápido?** → SageMaker JumpStart
7. **Quer dashboard/BI com IA?** → Amazon Quick

> **CUIDADO:** Essas são heurísticas para orientar na prova. Em cenários reais, a escolha pode ser mais nuançada dependendo de requisitos específicos de custo, latência, compliance e equipe.

---
