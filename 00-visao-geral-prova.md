# AWS Certified AI Practitioner (AIF-C01) — Visão Geral da Prova

## Informações Gerais

| Item | Detalhe |
|------|---------|
| **Código do exame** | AIF-C01 |
| **Nível** | Foundational (nível básico) |
| **Formato** | 65 questões (múltipla escolha e múltipla resposta) |
| **Duração** | 90 minutos |
| **Pontuação** | Escala de 100 a 1000 |
| **Nota de aprovação** | 700 |
| **Custo** | USD 75 |
| **Idiomas disponíveis** | Inglês, Português (Brasil), entre outros |
| **Modalidade** | Presencial (centro de testes) ou online proctored |
| **Validade** | 3 anos |

---

## Domínios do Exame e Pesos

| Domínio | Descrição | Peso |
|---------|-----------|------|
| 1 | Fundamentos de IA e ML | 20% |
| 2 | Fundamentos de IA Generativa | 24% |
| 3 | Aplicações de Modelos de Fundação (Foundation Models) | 28% |
| 4 | Diretrizes para IA Responsável | 14% |
| 5 | Segurança, Conformidade e Governança para Soluções de IA | 14% |

**Observação:** Os domínios 2 e 3 juntos representam **52% da prova** — IA Generativa é o foco principal.

---

## Domínio 1: Fundamentos de IA e ML (20%)

### Conceitos-chave

- **Tipos de Machine Learning:**
  - **Aprendizado Supervisionado** — treina com dados rotulados (classificação, regressão)
  - **Aprendizado Não-Supervisionado** — encontra padrões em dados sem rótulos (clustering, redução de dimensionalidade)
  - **Aprendizado por Reforço** — agente aprende por tentativa e erro com recompensas
  - **Aprendizado Semi-Supervisionado** — mistura de dados rotulados e não rotulados
  - **Aprendizado Auto-Supervisionado** — modelo gera seus próprios rótulos a partir dos dados

- **Ciclo de vida de ML (ML Pipeline):**
  1. Definição do problema de negócio
  2. Coleta e preparação de dados
  3. Feature engineering
  4. Treinamento do modelo
  5. Avaliação do modelo
  6. Deploy (implantação)
  7. Monitoramento e re-treinamento

- **Conceitos fundamentais:**
  - **Overfitting** — modelo memoriza os dados de treino, performa mal em dados novos
  - **Underfitting** — modelo simples demais, não captura os padrões
  - **Bias (viés)** — erro sistemático nas previsões
  - **Variance (variância)** — sensibilidade a flutuações nos dados de treino
  - **Dados de treino / validação / teste** — divisão do dataset para treinar, ajustar e avaliar
  - **Hiperparâmetros** — configurações definidas antes do treino (learning rate, epochs, batch size)
  - **Features** — variáveis de entrada usadas pelo modelo
  - **Labels** — a resposta correta (nos dados supervisionados)
  - **Inferência** — usar o modelo treinado para fazer previsões em dados novos

- **Métricas de avaliação:**
  - **Acurácia** — % de previsões corretas
  - **Precisão** — dos positivos previstos, quantos são realmente positivos
  - **Recall (Sensibilidade)** — dos positivos reais, quantos foram detectados
  - **F1 Score** — média harmônica entre precisão e recall
  - **AUC-ROC** — capacidade de distinguir entre classes
  - **RMSE / MAE** — métricas para regressão

- **Tipos de tarefas:**
  - **Classificação** — prever uma categoria (spam/não-spam, fraude/legítimo)
  - **Regressão** — prever um valor numérico (preço, temperatura)
  - **Clustering** — agrupar dados similares sem rótulos
  - **Detecção de anomalias** — identificar outliers
  - **Recomendação** — sugerir itens relevantes

### Serviços AWS relacionados

| Serviço | Função |
|---------|--------|
| **Amazon SageMaker** | Plataforma completa para construir, treinar e implantar modelos ML |
| **Amazon S3** | Armazenamento de datasets |
| **AWS Glue** | ETL e preparação de dados |
| **Amazon Athena** | Consultas SQL em dados no S3 |
| **Amazon EMR** | Processamento de big data |
| **Amazon Comprehend** | NLP pré-treinado (sentimento, entidades, idioma) |
| **Amazon Rekognition** | Visão computacional (imagens e vídeos) |
| **Amazon Translate** | Tradução de texto |
| **Amazon Polly** | Texto para fala |
| **Amazon Transcribe** | Fala para texto |
| **Amazon Forecast** | Previsão de séries temporais |
| **Amazon Personalize** | Recomendações personalizadas |
| **Amazon Textract** | Extração de texto e dados de documentos |
| **Amazon Kendra** | Busca empresarial inteligente |
| **Amazon Lex** | Chatbots conversacionais |
| **Amazon Fraud Detector** | Detecção de fraude |

---

## Domínio 2: Fundamentos de IA Generativa (24%)

### Conceitos-chave

- **Foundation Models (Modelos de Fundação):**
  - Modelos de grande escala pré-treinados em enormes quantidades de dados
  - Podem ser adaptados para múltiplas tarefas (multi-purpose)
  - Exemplos: GPT, Claude, Llama, Titan, Stable Diffusion

- **Large Language Models (LLMs):**
  - Tipo de foundation model especializado em linguagem
  - Treinados em grandes corpora de texto
  - Capacidades: geração de texto, resumo, tradução, Q&A, código

- **Arquitetura Transformer:**
  - Base dos LLMs modernos
  - Mecanismo de **atenção (attention)** — permite focar nas partes relevantes da entrada
  - **Self-attention** — cada token "olha" para todos os outros tokens
  - Componentes: encoder (entende) e decoder (gera)

- **Conceitos de LLMs:**
  - **Tokens** — unidades de texto processadas pelo modelo (palavras, subpalavras)
  - **Context window** — quantidade máxima de tokens que o modelo processa por vez
  - **Embeddings** — representações numéricas (vetores) de palavras/frases
  - **Temperature** — controla aleatoriedade na geração (0 = determinístico, 1 = criativo)
  - **Top-p / Top-k** — controlam a diversidade das respostas
  - **Tokens de entrada vs saída** — afetam custo e latência
  - **Alucinação (Hallucination)** — modelo gera informação plausível mas falsa
  - **Grounding** — ancorar as respostas em dados reais para reduzir alucinações

- **Tipos de IA Generativa:**
  - **Geração de texto** — artigos, código, resumos, traduções
  - **Geração de imagens** — a partir de descrições textuais (text-to-image)
  - **Geração de código** — assistentes de programação
  - **Geração de áudio/vídeo** — síntese de mídia
  - **Multimodal** — modelos que processam múltiplos tipos de dados (texto + imagem)

- **Prompt Engineering:**
  - **Zero-shot** — pergunta direta sem exemplos
  - **Few-shot** — fornecer alguns exemplos antes da pergunta
  - **Chain-of-thought** — pedir raciocínio passo a passo
  - **System prompt** — instrução que define o comportamento do modelo
  - **Prompt template** — estrutura reutilizável para prompts

- **Diferenças entre ML tradicional e IA Generativa:**
  - ML tradicional: prediz, classifica, agrupa → saída estruturada
  - IA Generativa: cria conteúdo novo → saída não-estruturada (texto, imagem)
  - ML tradicional precisa de dados específicos para cada tarefa
  - Foundation models são pré-treinados e adaptáveis a múltiplas tarefas

### Serviços AWS relacionados

| Serviço | Função |
|---------|--------|
| **Amazon Bedrock** | Acesso a foundation models via API (Claude, Titan, Llama, etc.) |
| **Amazon Titan** | Família de FMs da própria AWS (texto, embeddings, imagem) |
| **Amazon CodeWhisperer / Amazon Q Developer** | Assistente de código com IA generativa |
| **Amazon Q** | Assistente empresarial de IA generativa |
| **PartyRock** | Playground para experimentar apps com IA generativa (sem código) |

---

## Domínio 3: Aplicações de Foundation Models (28%)

### Conceitos-chave

- **Amazon Bedrock — Funcionalidades:**
  - Acesso serverless a múltiplos foundation models
  - Modelos disponíveis: Anthropic Claude, Amazon Titan, Meta Llama, Cohere, Stability AI, Mistral
  - **Knowledge Bases** — conecta FMs a fontes de dados (RAG)
  - **Agents** — FMs que podem executar ações (chamar APIs, consultar DBs)
  - **Guardrails** — filtros de conteúdo e controles de segurança
  - **Fine-tuning** — ajustar um FM com seus dados específicos
  - **Continued Pre-training** — treinar o modelo com dados adicionais do domínio
  - **Model evaluation** — avaliar e comparar modelos no Bedrock

- **RAG (Retrieval-Augmented Generation):**
  - Combina busca de informações + geração de texto
  - Reduz alucinações ao ancorar respostas em dados reais
  - Fluxo: pergunta → busca em base de conhecimento → contexto relevante → FM gera resposta
  - Usa embeddings e bancos vetoriais para busca semântica
  - Serviços: Bedrock Knowledge Bases, OpenSearch, Kendra

- **Fine-tuning vs Prompt Engineering vs RAG:**
  - **Prompt Engineering** — mais simples, sem custo de treinamento, limitado pelo context window
  - **RAG** — traz informação externa atualizada, sem re-treinar o modelo
  - **Fine-tuning** — ajusta pesos do modelo, bom para estilo/formato específico, mais caro
  - **Continued Pre-training** — ensina conhecimento novo ao modelo, mais intensivo

- **Agents (Agentes):**
  - FMs que planejam e executam tarefas complexas
  - Podem chamar APIs, consultar bases de dados, executar código
  - Ciclo: raciocinar → decidir ação → executar → observar resultado → repetir
  - Bedrock Agents: integra FM com Lambda functions e knowledge bases

- **Casos de uso empresariais:**
  - Chatbots e assistentes virtuais
  - Geração e resumo de documentos
  - Busca semântica em bases de conhecimento
  - Extração de informações de documentos
  - Geração de código e documentação técnica
  - Personalização de conteúdo
  - Análise de sentimento e feedback

- **Otimização de modelos:**
  - Seleção do modelo correto para o caso de uso (custo vs performance)
  - Ajuste de hiperparâmetros de inferência (temperature, max tokens)
  - Latência vs qualidade
  - Custo por token (entrada vs saída)
  - Caching de respostas

### Serviços AWS relacionados

| Serviço | Função |
|---------|--------|
| **Amazon Bedrock** | Plataforma principal para FMs |
| **Amazon SageMaker JumpStart** | Hub de modelos pré-treinados para deploy |
| **Amazon OpenSearch** | Banco vetorial para RAG |
| **Amazon Kendra** | Busca empresarial inteligente (pode ser fonte para RAG) |
| **AWS Lambda** | Execução de código para Agents |
| **Amazon S3** | Armazenamento de documentos para Knowledge Bases |
| **Amazon CloudWatch** | Monitoramento de inferências |

---

## Domínio 4: Diretrizes para IA Responsável (14%)

### Conceitos-chave

- **Princípios de IA Responsável da AWS:**
  - **Fairness (Equidade)** — modelo não deve discriminar grupos
  - **Explicabilidade (Explainability)** — entender por que o modelo tomou uma decisão
  - **Transparência** — ser claro sobre o uso de IA
  - **Robustez** — modelo funciona bem em condições diversas
  - **Privacidade** — proteger dados pessoais
  - **Segurança** — prevenir uso malicioso
  - **Governança** — controles organizacionais para IA

- **Viés (Bias) em IA:**
  - **Viés nos dados** — dados de treino não representativos
  - **Viés de seleção** — amostragem tendenciosa
  - **Viés de medição** — métricas inadequadas
  - **Viés algorítmico** — modelo amplifica padrões indesejados
  - **Mitigação**: dados diversos, auditorias, métricas de fairness, monitoramento contínuo

- **Explicabilidade e Interpretabilidade:**
  - Modelos "caixa-preta" vs modelos interpretáveis
  - Feature importance — quais variáveis mais influenciam a decisão
  - SHAP values — contribuição de cada feature para uma previsão específica
  - Importância de explicar decisões em contextos regulados (crédito, saúde)

- **Alucinações e mitigação:**
  - RAG para ancorar respostas em fatos
  - Guardrails para filtrar conteúdo inadequado
  - Human-in-the-loop — revisão humana antes de ações críticas
  - Validação de saídas

- **AWS AI Service Cards:**
  - Documentação de transparência para serviços de IA da AWS
  - Descrevem: caso de uso pretendido, limitações, métricas de fairness, design choices

### Serviços AWS relacionados

| Serviço | Função |
|---------|--------|
| **Amazon SageMaker Clarify** | Detectar viés em dados e modelos, explicabilidade |
| **Amazon SageMaker Model Monitor** | Monitorar drift e qualidade do modelo em produção |
| **Amazon Bedrock Guardrails** | Filtros de conteúdo, tópicos bloqueados, PII filtering |
| **Amazon Augmented AI (A2I)** | Human-in-the-loop para revisão de previsões |
| **AWS AI Service Cards** | Documentação de transparência |

---

## Domínio 5: Segurança, Conformidade e Governança (14%)

### Conceitos-chave

- **Segurança de dados em IA:**
  - Criptografia em trânsito (TLS) e em repouso (KMS)
  - Controle de acesso aos dados de treino e modelos
  - Isolamento de dados entre clientes (multi-tenancy)
  - VPC endpoints para acesso privado aos serviços de IA
  - Data residency — onde os dados são processados/armazenados

- **IAM e controle de acesso:**
  - Políticas IAM para serviços de IA (Bedrock, SageMaker)
  - Princípio do menor privilégio
  - Service roles para SageMaker e Bedrock
  - Resource-based policies

- **Conformidade e regulamentação:**
  - LGPD, GDPR, HIPAA — implicações para IA
  - Dados de treinamento vs dados de inferência
  - Retenção e exclusão de dados
  - Audit trails — rastrear quem fez o quê

- **Governança de modelos:**
  - Model Registry — versionar e catalogar modelos
  - Lineage tracking — rastreio da origem dos dados
  - Aprovações de deploy
  - Monitoramento de performance em produção
  - Política de re-treinamento

- **Privacidade:**
  - PII detection e redaction
  - Opt-out de uso de dados para treinamento
  - Data minimization — usar apenas dados necessários
  - Anonimização e pseudonimização

### Serviços AWS relacionados

| Serviço | Função |
|---------|--------|
| **AWS IAM** | Controle de acesso e permissões |
| **AWS KMS** | Gerenciamento de chaves de criptografia |
| **AWS CloudTrail** | Auditoria de chamadas de API |
| **AWS Config** | Conformidade de recursos |
| **Amazon Macie** | Detecção de dados sensíveis no S3 |
| **AWS PrivateLink / VPC Endpoints** | Acesso privado aos serviços de IA |
| **SageMaker Model Registry** | Governança e versionamento de modelos |
| **Amazon Bedrock** | Opções de privacidade (dados não usados para treinar modelos) |
| **AWS Artifact** | Relatórios de conformidade |

---

## Formato das Questões na Prova

### Múltipla escolha (1 resposta correta)
- 4 alternativas (A, B, C, D)
- Apenas 1 correta
- A maioria das questões é deste tipo

### Múltipla resposta (2+ respostas corretas)
- 5 ou 6 alternativas
- O enunciado diz quantas selecionar (ex: "Selecione DUAS respostas")
- Precisa acertar todas as corretas para pontuar

### Estilo das questões
- **Cenário** — descreve uma situação de negócio e pede a melhor solução
- **Conceitual** — testa entendimento de um conceito (ex: "O que é RAG?")
- **Melhor prática** — qual abordagem é recomendada pela AWS
- **Comparação** — quando usar X vs Y

### Dicas importantes
- Questões NÃO exigem experiência hands-on com código
- Foco em QUANDO usar cada serviço, não em COMO configurar
- Eliminação de alternativas absurdas ajuda muito
- Palavras-chave no enunciado geralmente apontam para a resposta
- "Mais eficiente", "menor custo", "menos esforço operacional" — guiam a resposta

---

## Dicas de Estudo

1. **Siga o curso do Stephane Maarek** como base teórica — cobre todos os domínios
2. **Faça questões diariamente** — é o método mais eficiente para fixar conceitos
3. **Foque nos domínios 2 e 3** — representam 52% da prova
4. **Conheça bem o Amazon Bedrock** — é o serviço mais cobrado na prova
5. **Entenda QUANDO usar cada serviço** — não precisa saber configurar, mas sim escolher
6. **Leia as AWS AI Service Cards** — fonte oficial de transparência
7. **Entenda RAG, fine-tuning e prompt engineering** — e quando usar cada um
8. **Não decore — entenda** — a prova testa compreensão, não memorização

---

## Cronograma de Estudo (15/08 → 28/09)

| Semana | Período | Foco | Atividades |
|--------|---------|------|-----------|
| 1 | 15-21/ago | Domínio 1 (parte 1) | Curso Udemy + conceitos ML + questões |
| 2 | 22-28/ago | Domínio 1 (parte 2) + início D2 | Fechar D1 + começar IA Generativa |
| 3 | 29/ago-04/set | Domínio 2 | LLMs, Transformers, Prompt Engineering |
| 4 | 05-11/set | Domínio 3 (parte 1) | Bedrock, RAG, Knowledge Bases |
| 5 | 12-18/set | Domínio 3 (parte 2) + D4 + D5 | Agents, Fine-tuning + IA Responsável + Segurança |
| 6 | 19-27/set | Revisão + Simulados | Simulados completos + revisão de gaps |
| **PROVA** | **28/set** | 🎯 | **Dia do exame** |

---

## Links Oficiais

- [Página oficial do exame AIF-C01](https://aws.amazon.com/certification/certified-ai-practitioner/)
- [Exam Guide (PDF)](https://d1.awsstatic.com/training-and-certification/docs-ai-practitioner/AWS-Certified-AI-Practitioner_Exam-Guide.pdf)
- [Sample Questions](https://d1.awsstatic.com/training-and-certification/docs-ai-practitioner/AWS-Certified-AI-Practitioner_Sample-Questions.pdf)
- [AWS Skill Builder — Curso gratuito preparatório](https://explore.skillbuilder.aws/learn/course/internal/view/elearning/19554/aws-certified-ai-practitioner-official-practice-question-set)
- [AWS AI Service Cards](https://aws.amazon.com/machine-learning/responsible-machine-learning/ai-service-cards/)
- [Amazon Bedrock — Documentação](https://docs.aws.amazon.com/bedrock/)

---

## Próximos Passos

→ **Agora:** Leia esta visão geral para ter o mapa mental da prova
→ **Depois:** Comece o Domínio 1 no curso do Stephane Maarek
→ **Em paralelo:** Vamos começar o banco de questões do Domínio 1 (`01-dominio1-fundamentos-ia-ml.md`)

---

*Última atualização: 15/08/2026*
*Meta: Aprovação em 28/09/2026*
