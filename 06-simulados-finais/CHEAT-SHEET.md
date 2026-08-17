# Cheat Sheet — AIF-C01 (Revisão Rápida Pré-Prova)

---

## Mapeamento Serviço → Caso de Uso

| Serviço | Quando usar |
|---------|-------------|
| **Amazon Bedrock** | App GenAI em produção com FMs (serverless) |
| **Bedrock Knowledge Bases** | RAG gerenciado (respostas baseadas em docs) |
| **Bedrock Agents** | FM que executa ações (APIs, Lambda) |
| **Bedrock Guardrails** | Filtrar conteúdo, PII, tópicos bloqueados |
| **Amazon Titan** | FMs da própria AWS (texto, embeddings, imagem) |
| **Amazon Q Business** | Assistente GenAI empresarial com dados internos |
| **Amazon Q Developer** | Assistente de código (gerar, explicar, debugar) |
| **PartyRock** | Playground GenAI gratuito sem conta AWS |
| **SageMaker** | Construir modelo ML customizado (treino + deploy) |
| **SageMaker Canvas** | ML sem código (analistas de negócio) |
| **SageMaker Autopilot** | AutoML automático |
| **SageMaker JumpStart** | Hub de modelos pré-treinados |
| **SageMaker Clarify** | Detectar viés + explicar previsões (SHAP) |
| **SageMaker Model Monitor** | Monitorar drift em produção |
| **SageMaker Model Registry** | Versionar modelos + aprovação de deploy |
| **Amazon Comprehend** | NLP pré-treinado (sentimento, entidades, PII) |
| **Amazon Rekognition** | Visão computacional (objetos, faces, moderação) |
| **Amazon Textract** | Extrair texto/dados de documentos (OCR+) |
| **Amazon Transcribe** | Áudio → texto |
| **Amazon Polly** | Texto → áudio |
| **Amazon Translate** | Tradução entre idiomas |
| **Amazon Lex** | Chatbots conversacionais |
| **Amazon Kendra** | Busca empresarial inteligente |
| **Amazon Personalize** | Recomendações personalizadas |
| **Amazon Forecast** | Previsão de séries temporais |
| **Amazon Fraud Detector** | Detecção de fraude |
| **Amazon A2I** | Human-in-the-loop (revisão humana) |
| **Amazon Macie** | Detectar dados sensíveis no S3 |
| **AWS CloudTrail** | Auditoria (quem fez o quê) |
| **AWS KMS** | Criptografia (chaves) |
| **AWS Artifact** | Relatórios de compliance |

---

## Decisões-Chave

### Tipo de ML
| Pista no cenário | Tipo |
|-----------------|------|
| Dados rotulados + prever categoria | Supervisionado — Classificação |
| Dados rotulados + prever valor | Supervisionado — Regressão |
| Sem rótulos + agrupar | Não-Supervisionado — Clustering |
| Agente + recompensa + tentativa e erro | Reforço |
| Poucos rótulos + muitos sem | Semi-Supervisionado |
| Pré-treino de LLMs / prever token mascarado | Auto-Supervisionado |

### Prompt Engineering vs RAG vs Fine-tuning
| Pista no cenário | Abordagem |
|-----------------|-----------|
| Primeiro passo / sem custo / imediato | Prompt Engineering |
| Dados atualizados / proprietários / reduzir alucinações | RAG |
| Mudar estilo / tom / formato consistente | Fine-tuning |
| Modelo não entende o domínio | Continued Pre-training |

### Métricas
| Pista | Métrica |
|-------|---------|
| Detectar todos os positivos (FN é caro) | Recall |
| Evitar falsos alarmes (FP é caro) | Precisão |
| Dados desbalanceados | F1 ou AUC-ROC |
| Resumos | ROUGE |
| Tradução | BLEU |
| Regressão com erro grande perigoso | RMSE |

### Overfitting vs Underfitting
| Sinal | Problema | Solução |
|-------|----------|---------|
| Treino alto, teste baixo | Overfitting | Regularização, early stopping, mais dados |
| Ambos baixos | Underfitting | Modelo mais complexo, mais features |

---

## Parâmetros de Inferência

| Parâmetro | Baixo | Alto |
|-----------|-------|------|
| Temperature | Factual, consistente | Criativo, diverso |
| Top-p | Focado | Variado |
| Max tokens | Respostas curtas (barato) | Respostas longas (caro) |

---

## Segurança — Resposta Rápida

| Precisa de... | Use... |
|--------------|--------|
| Criptografia em repouso | KMS + SSE |
| Criptografia em trânsito | TLS/HTTPS |
| Tráfego sem internet | VPC Endpoints / PrivateLink |
| Auditoria de API calls | CloudTrail |
| Controle de acesso | IAM (least privilege) |
| Dados não treinar modelo base | Bedrock (garantia padrão) |
| Compliance reports | AWS Artifact |
| Detectar PII no S3 | Macie |
| Mascarar PII em respostas | Guardrails PII filter |

---

## Cross-References (Conceitos que Cruzam Domínios)

| Conceito | Aparece em |
|----------|-----------|
| RAG | D2 (conceito), D3 (implementação Bedrock), D4 (mitigar alucinações) |
| Alucinações | D2 (conceito), D3 (RAG como solução), D4 (guardrails, grounding) |
| Viés/Bias | D1 (bias-variance trade-off), D4 (fairness, Clarify) |
| Embeddings | D2 (conceito), D3 (RAG, vector database) |
| SageMaker Clarify | D4 (viés, explicabilidade), D5 (governança, monitoramento) |
| Guardrails | D3 (Bedrock features), D4 (IA responsável), D5 (segurança) |
| Model Monitor | D1 (monitoramento no pipeline), D5 (governança) |
| KMS/IAM | D5 (segurança), presente em todos os domínios como base |

---

## Números para Lembrar

| Item | Valor |
|------|-------|
| Questões | 65 |
| Tempo | 90 min (~83s por questão) |
| Aprovação | 700 / 1000 |
| Domínio mais pesado | D3 — Aplicações de FMs (28%) |
| D2 + D3 juntos | 52% da prova |
| Custo do exame | USD 100 |

---

*Boa prova! 🎯*
