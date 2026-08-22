# Coverage Matrix — AIF-C01 Exam Guide vs. Arquivos C-

*Última atualização: 2026-08-22*
*Baseado no Exam Guide vigente (docs.aws.amazon.com)*

## Legenda

| Status | Significado |
|--------|-------------|
| ✅ FULL | Cobertura adequada |
| 🟡 PARTIAL | Cobertura existente mas pode ser expandida |
| ❌ MISSING | Ausência de cobertura |
| ⚠️ NEEDS REVIEW | Precisa de verificação adicional |

---

## Domínio 1 — Fundamentos de IA e ML (20%)

### Tarefa 1.1 — Explicar conceitos e terminologias básicos de IA

| Objetivo | Status | Arquivo(s) | Notas |
|----------|--------|-----------|-------|
| Definir termos básicos (IA, ML, DL, redes neurais, NLP, CV, modelo, algoritmo, treinamento, inferência, viés, imparcialidade, ajuste, LLM, GenAI, IA agêntica) | ✅ FULL | D1 C-01 | Hierarquia de conceitos + tabela de definições |
| Semelhanças/diferenças entre IA, ML, GenAI, DL, IA agêntica | ✅ FULL | D1 C-01 | Tabela comparativa + diagrama hierárquico |
| Tipos de inferência (batch, real-time, assíncrona, serverless) | ✅ FULL | D1 C-01 | Seção dedicada com tabela e dicas |
| Tipos de dados (rotulados/não-rotulados, tabulares, séries temporais, imagem, texto, estruturados/não-estruturados) | ✅ FULL | D1 C-01 | 3 tabelas: por rótulo, por estrutura, por modalidade |
| Tipos de aprendizado (supervisionado, não-supervisionado, reforço) | ✅ FULL | D1 C-01 | Incluindo semi e auto-supervisionado |

### Tarefa 1.2 — Identificar casos de uso práticos de IA

| Objetivo | Status | Arquivo(s) | Notas |
|----------|--------|-----------|-------|
| Aplicações onde IA/ML agrega valor | ✅ FULL | D1 C-05 | Tabela "Quando IA é apropriado" |
| Quando AI/ML NÃO é apropriado | ✅ FULL | D1 C-05 | Seção dedicada com cenários |
| Técnicas de ML para casos de uso (regressão, classificação, clustering) | ✅ FULL | D1 C-05 | Mapeamento cenário → tarefa → serviço |
| Exemplos reais (CV, NLP, fala, recomendação, fraude, previsão, knowledge bases, IA agêntica) | ✅ FULL | D1 C-05 | Todas presentes |
| Serviços gerenciados (SageMaker AI, Transcribe, Translate, Comprehend, Lex, Polly) | ✅ FULL | D1 C-06 | Tabela completa de serviços |
| Quando FM vs ML tradicional é apropriado | ✅ FULL | D1 C-05 + C-06 | Seção dedicada com critérios |

### Tarefa 1.3 — Descrever ciclo de vida do desenvolvimento de ML

| Objetivo | Status | Arquivo(s) | Notas |
|----------|--------|-----------|-------|
| Componentes de um pipeline de AI/ML | ✅ FULL | D1 C-02 | 7 etapas detalhadas |
| Origens de modelos (open-source vs custom) | ✅ FULL | D1 C-02 | Tabela com 3 tipos |
| Métodos de servir em produção (API gerenciada vs auto-hospedada) | ✅ FULL | D1 C-02 | Tabela de trade-offs |
| Serviços relevantes (Bedrock, Q, Quick, Kiro, SageMaker AI) | ✅ FULL | D1 C-02 + C-06 | Tabela atualizada |
| MLOps (experimentação, processos repetíveis, dívida técnica, etc.) | ✅ FULL | D1 C-02 | Seção dedicada com conceitos e serviços |
| Métricas de modelo e métricas de negócio | ✅ FULL | D1 C-02 + C-04 | Ambas cobertas |

---

## Domínio 2 — Fundamentos de IA Generativa (24%)

### Tarefa 2.1 — Explicar os conceitos básicos de IA generativa

| Objetivo | Status | Arquivo(s) | Notas |
|----------|--------|-----------|-------|
| Conceitos fundamentais (tokens, chunking, embeddings, vetores, PE, LLMs, FMs, multimodais, difusão) | ✅ FULL | D2 C-01 + C-02 + C-03 | Distribuídos entre arquivos |
| Casos de uso de GenAI (imagem, áudio, vídeo, resumo, assistentes, tradução, código, suporte, pesquisa, recomendação) | ✅ FULL | D2 C-01 + D2 C-05 | |
| Ciclo de vida do FM (seleção → pré-treinamento → fine-tuning → avaliação → deploy → feedback) | ✅ FULL | D2 C-01 | Tabela completa |
| Precificação baseada em tokens e efeito no custo/performance | ✅ FULL | D2 C-03 | Seção expandida |
| Engenharia de contexto | ✅ FULL | D2 C-01 | Seção dedicada |
| IA agêntica (MCP, multiagente, memória, ferramentas, orquestração) | ✅ FULL | D2 C-01 | Seção completa com MCP detalhado |

### Tarefa 2.2 — Recursos e limitações da GenAI

| Objetivo | Status | Arquivo(s) | Notas |
|----------|--------|-----------|-------|
| Vantagens da GenAI (adaptabilidade, conversação, geração de conteúdo) | ✅ FULL | D2 C-01 | ML Tradicional vs GenAI |
| Desvantagens (alucinações, interpretabilidade, imprecisão, não-determinismo) | ✅ FULL | D2 C-03 | Seção de alucinações + parâmetros |
| Fatores de seleção de modelos (tipo, performance, recursos, compliance, custo, latência, complexidade) | ✅ FULL | D3 C-01 | Seção de critérios de seleção |
| Valor comercial e métricas (ROI, eficiência, taxa de conversão, acurácia) | ✅ FULL | D1 C-02 + D1 C-04 | Métricas de negócio |

### Tarefa 2.3 — Infraestrutura e tecnologias AWS para GenAI

| Objetivo | Status | Arquivo(s) | Notas |
|----------|--------|-----------|-------|
| Serviços AWS para GenAI (Bedrock, SageMaker AI, JumpStart, Quick, Kiro, Strands, AgentCore) | ✅ FULL | D2 C-05 | Todos listados com descrição |
| Vantagens de usar serviços AWS (acessibilidade, eficiência, custo, velocidade) | ✅ FULL | D2 C-05 | Seção dedicada |
| Benefícios da infraestrutura AWS (proteção, conformidade, segurança) | ✅ FULL | D2 C-05 | Tabela de vantagens |
| Trade-offs de custos (tokens, provisioned, cobertura regional) | ✅ FULL | D2 C-05 | Tabela de trade-offs |

---

## Domínio 3 — Aplicações de Foundation Models (28%)

### Tarefa 3.1 — Considerações sobre design de aplicações com FMs

| Objetivo | Status | Arquivo(s) | Notas |
|----------|--------|-----------|-------|
| Critérios de seleção de FM (custo, modalidade, latência, multilíngue, tamanho, prompt caching) | ✅ FULL | D3 C-01 | 9 critérios + framework de decisão |
| Efeito dos parâmetros de inferência (temperature, tamanho I/O) | ✅ FULL | D2 C-03 + D3 C-01 | Coberto em ambos |
| RAG e aplicações empresariais (Knowledge Bases) | ✅ FULL | D3 C-02 | Fluxo completo |
| Vector databases AWS (OpenSearch, Aurora, Neptune, RDS PostgreSQL) | ✅ FULL | D3 C-01 + C-02 | 4 serviços listados |
| Trade-offs de custo (PE, fine-tuning, RAG, distillation) | ✅ FULL | D3 C-01 | Tabela comparativa |
| Função dos agentes de IA e aplicações comerciais | ✅ FULL | D3 C-01 + C-04 | Tabela de aplicações |

### Tarefa 3.2 — Escolher técnicas eficazes de engenharia de prompts

| Objetivo | Status | Arquivo(s) | Notas |
|----------|--------|-----------|-------|
| Componentes de um prompt (contexto, instrução, negative prompts) | ✅ FULL | D2 C-04 | Tabela de componentes |
| Técnicas (zero-shot, one-shot, few-shot, CoT, templates) | ✅ FULL | D2 C-04 | Todas detalhadas |
| Benefícios e boas práticas | ✅ FULL | D2 C-04 | Seção de boas práticas |
| Riscos (injection, poisoning, hijacking, jailbreaking) | ✅ FULL | D2 C-04 | Seção completa de riscos |
| Prompt versioning e management (Bedrock Prompt Management) | ✅ FULL | D2 C-04 | Seção dedicada |

### Tarefa 3.3 — Treinamento e ajuste fino de FMs

| Objetivo | Status | Arquivo(s) | Notas |
|----------|--------|-----------|-------|
| Elementos de treinamento (pré-treinamento, fine-tuning, continued pre-training, distillation) | ✅ FULL | D3 C-03 | Todos detalhados |
| Métodos de fine-tuning (instruções, adaptação de domínio, transfer learning, continued pre-training) | ✅ FULL | D3 C-03 | Incluindo transfer learning |
| Preparação de dados (curadoria, governança, tamanho, rotulagem, representatividade, RLHF) | ✅ FULL | D3 C-03 | Seção completa |

### Tarefa 3.4 — Métodos para avaliar desempenho do FM

| Objetivo | Status | Arquivo(s) | Notas |
|----------|--------|-----------|-------|
| Abordagens (avaliação humana, benchmarks, Bedrock Model Evaluation) | ✅ FULL | D1 C-04 + D3 C-05 | |
| Métricas (ROUGE, BLEU, BERTScore, LLM-as-judge) | ✅ FULL | D1 C-04 + D3 C-05 | Com limitações |
| Avaliar se FM atende objetivos de negócio | ✅ FULL | D3 C-05 | Métricas de negócio |
| Avaliar performance de aplicações FM (RAG, agents, workflows) | ✅ FULL | D3 C-05 | Seção dedicada |
| Métricas de alinhamento de negócio (task completion, satisfação, custo/interação) | ✅ FULL | D3 C-05 + D1 C-04 | |

---

## Domínio 4 — Diretrizes de IA Responsável (14%)

### Tarefa 4.1 — Desenvolvimento de sistemas de IA responsáveis

| Objetivo | Status | Arquivo(s) | Notas |
|----------|--------|-----------|-------|
| Características (viés, imparcialidade, inclusão, robustez, segurança, veracidade) | ✅ FULL | D4 C-01 | 8 características definidas |
| Ferramentas (Guardrails for Amazon Bedrock) | ✅ FULL | D4 C-03 | Seção completa |
| Práticas responsáveis para escolher modelo (sustentabilidade, ambiental) | ✅ FULL | D4 C-01 | Seção dedicada |
| Riscos legais (IP, viés, confiança do cliente, risco do usuário, alucinações) | ✅ FULL | D4 C-01 | 5 riscos com mitigações |
| Características de datasets (inclusão, diversidade, curadoria, balanceamento) | ✅ FULL | D4 C-01 | Tabela + problemas |
| Efeitos do viés e variância (grupos demográficos, imprecisão, overfitting/underfitting) | ✅ FULL | D4 C-02 | Seção dedicada |
| Ferramentas para detectar/monitorar (Clarify, Model Monitor, A2I, auditorias humanas, análise de subgrupos) | ✅ FULL | D4 C-02 | Todas cobertas |

### Tarefa 4.2 — Modelos transparentes e explicáveis

| Objetivo | Status | Arquivo(s) | Notas |
|----------|--------|-----------|-------|
| Diferenças entre modelos transparentes/explicáveis e os que não são | ✅ FULL | D4 C-01 + C-03 | Trade-offs performance vs interpretabilidade |
| Ferramentas (Model Cards, Clarify, Bedrock Model Evaluations, código aberto) | ✅ FULL | D4 C-03 | Todas cobertas |
| Trade-offs segurança vs transparência | ✅ FULL | D4 C-03 | Seção dedicada |
| Design centrado no ser humano (feedback, transparência de decisões) | ✅ FULL | D4 C-03 | 4 princípios |

---

## Domínio 5 — Segurança, Conformidade e Governança (14%)

### Tarefa 5.1 — Métodos para proteger sistemas de IA

| Objetivo | Status | Arquivo(s) | Notas |
|----------|--------|-----------|-------|
| Serviços/recursos de segurança (IAM, KMS, Macie, PrivateLink, responsabilidade compartilhada, AgentCore Identity/Policy, Guardrails) | ✅ FULL | D5 C-01 + C-02 | Todos cobertos |
| Citação de fontes e documentação de origens (linhagem, catalogação, Model Cards) | ✅ FULL | D5 C-01 | Seção dedicada |
| Práticas de engenharia de dados segura (qualidade, privacidade, acesso, integridade) | ✅ FULL | D5 C-01 + C-03 | |
| Considerações de segurança (prompt injection, data leakage, output filtering, criptografia, auditoria, toxicidade) | ✅ FULL | D5 C-01 | Seção completa |
| Detecção de alucinações e grounding (RAG, validação, confidence scoring) | ✅ FULL | D5 C-01 | Seção dedicada |

### Tarefa 5.2 — Governança e conformidade

| Objetivo | Status | Arquivo(s) | Notas |
|----------|--------|-----------|-------|
| Serviços de governança (Config, Inspector, Audit Manager, Artifact, CloudTrail, Trusted Advisor) | ✅ FULL | D5 C-04 + C-02 | Todos cobertos |
| Estratégias de governança de dados (ciclos de vida, logging, residência, monitoramento, observação, retenção) | ✅ FULL | D5 C-03 | Seção dedicada |
| Processos de governança (políticas, cadência de revisão, frameworks, Scoping Matrix, transparência, treinamento) | ✅ FULL | D5 C-04 | Seção completa |

---

## Serviços In-Scope — Cobertura

### Machine Learning
| Serviço | Coberto? | Arquivo(s) |
|---------|----------|-----------|
| Amazon A2I | ✅ | D4 C-03 |
| Amazon Bedrock | ✅ | D2 C-05, D3 C-01 |
| Agentes Bedrock | ✅ | D3 C-04 |
| Amazon Comprehend | ✅ | D1 C-06 |
| Amazon Kendra | ✅ | D1 C-06, D2 C-05 |
| Amazon Lex | ✅ | D1 C-06 |
| Amazon Nova | ✅ | D2 C-05 |
| Amazon Personalize | ✅ | D1 C-06 |
| Amazon Polly | ✅ | D1 C-06 |
| Amazon Rekognition | ✅ | D1 C-06 |
| Amazon SageMaker AI | ✅ | D1 C-06, D1 C-02 |
| SageMaker JumpStart | ✅ | D2 C-05 |
| Amazon Textract | ✅ | D1 C-06 |
| Amazon Transcribe | ✅ | D1 C-06 |
| Amazon Translate | ✅ | D1 C-06 |
| AWS Transform | ✅ | D1 C-06 |

### Developer Tools
| Serviço | Coberto? | Arquivo(s) |
|---------|----------|-----------|
| Kiro | ✅ | D1 C-06, D2 C-05 |
| Strands Agents | ✅ | D1 C-06, D2 C-05, D3 C-04 |
| Amazon Q | ✅ | D1 C-06, D2 C-05 |

### Segurança, Identidade e Compliance
| Serviço | Coberto? | Arquivo(s) |
|---------|----------|-----------|
| AWS Artifact | ✅ | D5 C-03 |
| AWS Audit Manager | ✅ | D5 C-04 |
| IAM | ✅ | D5 C-02 |
| Amazon Inspector | ✅ | D5 C-04 |
| AWS KMS | ✅ | D5 C-01 |
| Amazon Macie | ✅ | D5 C-03 |
| AWS Secrets Manager | 🟡 PARTIAL | Não mencionado explicitamente |

### Gerenciamento e Governança
| Serviço | Coberto? | Arquivo(s) |
|---------|----------|-----------|
| AWS CloudTrail | ✅ | D5 C-02 |
| Amazon CloudWatch | ✅ | D5 C-02 |
| AWS Config | ✅ | D5 C-04 |
| AWS Trusted Advisor | ✅ | D5 C-04 |
| AWS Well-Architected Tool | 🟡 PARTIAL | Não mencionado explicitamente |

### Analytics
| Serviço | Coberto? | Arquivo(s) |
|---------|----------|-----------|
| Amazon Quick | ✅ | D1 C-06, D2 C-05 |
| Amazon OpenSearch Service | ✅ | D3 C-01, D3 C-02 |
| AWS Glue | ✅ | D1 C-02 |
| AWS Lake Formation | ✅ | D1 C-02 |

### Banco de Dados
| Serviço | Coberto? | Arquivo(s) |
|---------|----------|-----------|
| Amazon Aurora | ✅ | D3 C-01 |
| Amazon Neptune | ✅ | D3 C-01 |
| Amazon RDS | ✅ | D3 C-01 |

---

## Gaps Residuais

| Item | Status | Prioridade | Nota |
|------|--------|-----------|------|
| AWS Secrets Manager | 🟡 Não mencionado | BAIXA | Relevância limitada para AIF-C01 |
| AWS Well-Architected Tool | 🟡 Não mencionado | BAIXA | Relevância limitada para AIF-C01 |
| Alguns serviços de dados (EMR, Redshift, DynamoDB, ElastiCache) | 🟡 Mencionados brevemente | BAIXA | Não são foco do exame de IA |

---

*Matriz gerada após reforma completa dos 23 arquivos C-.*
