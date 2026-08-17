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
| **Custo** | USD 100 |
| **Idiomas disponíveis** | Inglês, Japonês, Coreano, Chinês Simplificado, entre outros |
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

## Mapa de Conteúdo por Domínio

### Domínio 1 — Fundamentos de IA e ML (20%)

| Bloco | Tópicos-chave |
|-------|---------------|
| C-01 Tipos de ML | Supervisionado, Não-Supervisionado, Reforço, Semi, Auto-supervisionado |
| C-02 Ciclo de Vida | Pipeline completo, divisão treino/validação/teste, data drift |
| C-03 Conceitos Fundamentais | Overfitting, underfitting, bias-variance trade-off, regularização |
| C-04 Métricas | Acurácia, precisão, recall, F1, AUC-ROC, RMSE, ROUGE, BLEU |
| C-05 Tipos de Tarefas | Classificação, regressão, clustering, anomalias, NLP, visão computacional |
| C-06 Serviços AWS | SageMaker, Comprehend, Rekognition, Textract, Forecast, Personalize, etc. |

### Domínio 2 — Fundamentos de IA Generativa (24%)

| Bloco | Tópicos-chave |
|-------|---------------|
| C-01 Foundation Models e LLMs | O que são, diferença de ML tradicional, open-weight vs proprietary |
| C-02 Arquitetura Transformer | Attention, self-attention, encoder/decoder, tokenização, positional encoding |
| C-03 Conceitos de LLMs | Tokens, context window, temperature, top-p, embeddings, alucinações, grounding |
| C-04 Prompt Engineering | Zero-shot, few-shot, chain-of-thought, system prompt, templates |
| C-05 Serviços AWS GenAI | Bedrock, Titan, Q Business, Q Developer, PartyRock, pricing, Q vs Kendra |

### Domínio 3 — Aplicações de Foundation Models (28%)

| Bloco | Tópicos-chave |
|-------|---------------|
| C-01 Amazon Bedrock | Modelos, Knowledge Bases, Agents, Guardrails, fine-tuning, evaluation, Clarify para GenAI |
| C-02 RAG | Fluxo, chunking, vector database, embeddings, cosine similarity |
| C-03 Fine-tuning vs PE vs RAG | Framework de decisão, quando usar cada um, combinações |
| C-04 Agents | ReAct pattern, Action Groups, Lambda, diferença de RAG |
| C-05 Casos de Uso e Otimização | Cenários empresariais, seleção de modelo, métricas GenAI, otimização de custo |

### Domínio 4 — Diretrizes para IA Responsável (14%)

| Bloco | Tópicos-chave |
|-------|---------------|
| C-01 Princípios | Fairness, explicabilidade, transparência, robustez, AI Service Cards |
| C-02 Viés e Mitigação | Tipos de viés, métricas de fairness, SageMaker Clarify, mitigação por etapa |
| C-03 Guardrails e Human-loop | Bedrock Guardrails, A2I, Model Cards, detecção de alucinações |

### Domínio 5 — Segurança, Conformidade e Governança (14%)

| Bloco | Tópicos-chave |
|-------|---------------|
| C-01 Segurança de Dados | KMS, TLS, VPC Endpoints, PrivateLink, data residency, privacidade Bedrock |
| C-02 IAM e Controle de Acesso | Least privilege, SCPs, CloudTrail, CloudWatch, Model Invocation Logging |
| C-03 Conformidade e Privacidade | LGPD, GDPR, PII, Macie, Guardrails PII, Artifact, responsabilidade compartilhada |
| C-04 Governança de Modelos | Model Registry, Lineage Tracking, Pipelines, Model Monitor, MLOps |

---

## Formato das Questões na Prova

### Múltipla escolha (1 resposta correta)
- 4 alternativas (A, B, C, D)
- A maioria das questões é deste tipo
- Cenário de negócio → escolher a melhor solução

### Múltipla resposta (2+ respostas corretas)
- 5 ou 6 alternativas
- O enunciado diz quantas selecionar (ex: "Selecione DUAS respostas")
- Precisa acertar todas as corretas para pontuar

### Estilo das questões
- **Cenário** — descreve uma situação de negócio e pede a melhor solução
- **Conceitual** — testa entendimento de um conceito (ex: "O que é RAG?")
- **Melhor prática** — qual abordagem é recomendada pela AWS
- **Comparação** — quando usar X vs Y

### Palavras-chave que direcionam a resposta
| Palavra no enunciado | Significado |
|---------------------|-------------|
| "Menor esforço operacional" | Serviço gerenciado/serverless |
| "Custo mínimo" | Modelo menor, batch, ou on-demand para volume baixo |
| "Sem re-treinamento" | RAG ou Prompt Engineering (não fine-tuning) |
| "Dados atualizados" | RAG |
| "Tom/estilo consistente" | Fine-tuning |
| "Sem código" | SageMaker Canvas ou PartyRock |
| "Auditar" | CloudTrail |
| "Explicar decisão" | SageMaker Clarify (SHAP) |
| "Filtrar conteúdo" | Bedrock Guardrails |

---

## Dicas de Estudo

1. **Foque nos domínios 2 e 3** — representam 52% da prova
2. **Conheça bem o Amazon Bedrock** — é o serviço mais cobrado
3. **Entenda QUANDO usar cada serviço** — não precisa saber configurar, mas sim escolher
4. **Entenda RAG, fine-tuning e prompt engineering** — e quando usar cada um
5. **Faça questões diariamente** — volume de prática é essencial
6. **Official Practice Questions da AWS** — calibre o nível de dificuldade real

---

## Cronograma de Estudo (15/08 → 28/09)

| Semana | Período | Foco | Atividades |
|--------|---------|------|-----------|
| 1 | 15-21/ago | Domínio 1 (parte 1) | Blocos C-01 a C-03 + questões |
| 2 | 22-28/ago | Domínio 1 (parte 2) + início D2 | Blocos C-04 a C-06 + simulado D1 |
| 3 | 29/ago-04/set | Domínio 2 | Todos os blocos D2 + simulado D2 |
| 4 | 05-11/set | Domínio 3 (parte 1) | Blocos C-01 a C-03 |
| 5 | 12-18/set | Domínio 3 (parte 2) + D4 + D5 | Blocos C-04/C-05 + D4 + D5 + simulados |
| 6 | 19-27/set | Revisão + Simulados Finais | Simulados completos + cheat sheet + gaps |
| **PROVA** | **28/set** | 🎯 | **Dia do exame** |

---

## Links Oficiais

- [Página oficial do exame AIF-C01](https://aws.amazon.com/certification/certified-ai-practitioner/)
- [Exam Guide (PDF)](https://d1.awsstatic.com/training-and-certification/docs-ai-practitioner/AWS-Certified-AI-Practitioner_Exam-Guide.pdf)
- [Sample Questions](https://d1.awsstatic.com/training-and-certification/docs-ai-practitioner/AWS-Certified-AI-Practitioner_Sample-Questions.pdf)
- [AWS Skill Builder — Official Practice Questions (gratuito)](https://explore.skillbuilder.aws/learn/course/internal/view/elearning/19554/aws-certified-ai-practitioner-official-practice-question-set)
- [AWS AI Service Cards](https://aws.amazon.com/machine-learning/responsible-machine-learning/ai-service-cards/)
- [Amazon Bedrock — Documentação](https://docs.aws.amazon.com/bedrock/)

---

*Última atualização: 17/08/2026*
*Meta: Aprovação em 28/09/2026*
