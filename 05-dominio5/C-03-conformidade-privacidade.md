# Conformidade e Privacidade (LGPD, GDPR, PII)

## Visão Geral

Conformidade (compliance) garante que o uso de IA respeita leis e regulamentações. A prova testa se você sabe quais controles aplicar.

---

## Regulamentações Relevantes

| Lei | Região | Foco |
|-----|--------|------|
| **LGPD** | Brasil | Proteção de dados pessoais |
| **GDPR** | União Europeia | Proteção de dados, direito ao esquecimento |
| **HIPAA** | EUA | Dados de saúde |
| **SOC 2** | Global | Segurança e disponibilidade de serviços |
| **ISO 27001** | Global | Gestão de segurança da informação |

### Implicações para IA
- Dados pessoais em datasets de treino → consentimento necessário
- Direito ao esquecimento → possibilidade de remover dados
- Data residency → processar dados na região adequada
- Explicabilidade → justificar decisões automatizadas (GDPR Art. 22)

### LGPD — Nota importante

> **CUIDADO:** A LGPD **não exige explicitamente** que dados de cidadãos brasileiros sejam armazenados no Brasil. O que a LGPD exige é **proteção adequada** dos dados pessoais, independentemente de onde estejam. Transferências internacionais são permitidas quando há garantias adequadas de proteção (ex: país com nível adequado de proteção, cláusulas contratuais padrão, consentimento específico). Na prática, muitas organizações optam por manter dados no Brasil (sa-east-1) como medida adicional de compliance, mas isso é uma decisão de negócio, não uma imposição legal absoluta.

---

## Estratégias de Governança de Dados

O Exam Guide exige reconhecer estratégias de governança de dados para sistemas de IA.

| Estratégia | Descrição | Ferramenta/Serviço AWS |
|-----------|-----------|----------------------|
| **Ciclos de vida de dados** | Definir estágios dos dados (criação → uso → arquivamento → exclusão) | S3 Lifecycle Policies |
| **Logging (registro)** | Registrar acessos, modificações e uso dos dados | CloudTrail, CloudWatch Logs |
| **Residência de dados** | Garantir que dados estão na região geográfica adequada | Escolha de região AWS, SCPs |
| **Monitoramento** | Acompanhar uso, qualidade e segurança dos dados continuamente | CloudWatch, Macie, Config |
| **Observação (Observability)** | Visibilidade completa sobre fluxo e processamento dos dados | CloudWatch, X-Ray, OpenSearch |
| **Retenção** | Definir por quanto tempo dados são mantidos e quando excluir | S3 Lifecycle, DynamoDB TTL, políticas de retenção |

### Ciclo de vida dos dados em IA

```
1. Coleta → consentimento, minimização, qualidade
2. Armazenamento → criptografia, acesso restrito, região adequada
3. Processamento → auditoria, linhagem, governança
4. Uso (treino/inferência) → isolamento, privacidade
5. Archival → retenção definida, acesso limitado
6. Exclusão → deletion policies, direito ao esquecimento
```

> **DICA PARA A PROVA:** Se a questão menciona "definir por quanto tempo manter dados" → retenção. Se menciona "rastrear quem acessou dados" → logging. Se menciona "garantir dados na região certa" → residência. Se menciona "visibilidade do fluxo de dados" → observação/observability.

---

## PII (Personally Identifiable Information)

### O que é
Dados que identificam uma pessoa: nome, CPF, email, telefone, endereço, dados bancários.

### Riscos em IA
- PII nos dados de treino → pode vazar nas respostas do modelo
- PII nos prompts → pode ser logada ou armazenada
- PII nas respostas → expor dados sensíveis ao usuário

### Proteções

| Técnica | Serviço AWS | Quando usar |
|---------|-------------|-------------|
| Detectar PII em texto | Amazon Comprehend (PII detection) | Pré-processamento de dados |
| Mascarar PII em respostas | Bedrock Guardrails (PII filter) | Chatbots em produção |
| Detectar dados sensíveis no S3 | Amazon Macie | Auditoria de data lakes |
| Anonimizar dados de treino | Glue + custom logic | Antes de treinar modelos |

### Bedrock Guardrails — PII Filter
- Detecta automaticamente: nomes, emails, telefones, CPF, cartão de crédito, etc.
- Ações: **bloquear** (rejeitar resposta) ou **mascarar** (substituir por ****)
- Aplicado em inputs E outputs

---

## Data Minimization

### Princípio
Coletar e processar APENAS os dados necessários para o propósito específico.

### Aplicação em IA
- Não incluir campos desnecessários no dataset de treino
- Remover PII quando não é relevante para o modelo
- Anonimizar quando possível (substituir por IDs genéricos)
- Definir políticas de retenção (por quanto tempo guardar dados)

---

## Retenção e Exclusão de Dados

| Aspecto | Prática |
|---------|---------|
| Dados de treino | Definir período de retenção, excluir após uso |
| Logs de inferência | Retenção limitada, acesso restrito |
| Modelos treinados | Versionamento + política de exclusão |
| Fine-tuning datasets | Excluir após treinamento se não necessários |

### S3 Lifecycle Policies
- Automatizar exclusão de dados após período definido
- Mover para Glacier (arquivamento barato) antes de excluir
- Compliance com "direito ao esquecimento"

---

## AWS Artifact

### O que é
Portal self-service para acessar relatórios de compliance da AWS.

### O que oferece
- Relatórios SOC (SOC 1, SOC 2, SOC 3)
- Certificações ISO
- Relatórios PCI DSS
- Attestations de compliance

### Para a prova
- "Onde encontrar relatórios de compliance da AWS?" → AWS Artifact
- Demonstra que a **infraestrutura** AWS está em compliance
- Responsabilidade do cliente: garantir que **seu uso** dos serviços também está

---

## Modelo de Responsabilidade Compartilhada para IA

| AWS é responsável por | Cliente é responsável por |
|----------------------|--------------------------|
| Segurança da infraestrutura | Configurar IAM corretamente |
| Criptografia disponível | Ativar criptografia nos dados |
| Compliance dos serviços | Compliance do uso dos serviços |
| Isolamento multi-tenant | Não expor dados sensíveis em prompts |
| Modelos base seguros | Guardrails e filtros em suas apps |
| Disponibilidade | Monitoramento e backup |

---

## Resumo para a Prova

| Cenário | Solução |
|---------|---------|
| "Detectar dados pessoais em texto" | Amazon Comprehend (PII) |
| "Mascarar PII nas respostas do chatbot" | Bedrock Guardrails (PII filter) |
| "Encontrar dados sensíveis no S3" | Amazon Macie |
| "Relatórios de compliance da AWS" | AWS Artifact |
| "Excluir dados após período" | S3 Lifecycle Policies |
| "Dados precisam ficar no Brasil" | Considerar região sa-east-1 (São Paulo) — decisão de negócio, não obrigação absoluta da LGPD |
| "Direito ao esquecimento" | Política de exclusão + lifecycle rules |
| "Justificar decisão automatizada" | Explicabilidade (SageMaker Clarify) |

---

*Próximo bloco: Governança de modelos (registry, lineage, monitoramento)*
