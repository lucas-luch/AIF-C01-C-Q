# Segurança de Dados em IA

## Visão Geral

O Domínio 5 cobre como proteger dados, modelos e infraestrutura de IA na AWS. Representa 14% da prova — as questões são diretas se você conhece os serviços de segurança.

---

## Criptografia

### Em Trânsito (in transit)
- **TLS/SSL** — toda comunicação com serviços AWS é criptografada
- HTTPS obrigatório para APIs do Bedrock, SageMaker, etc.
- Protege dados entre seu app e a AWS

### Em Repouso (at rest)
- **AWS KMS** (Key Management Service) — gerencia chaves de criptografia
- Dados em S3, EBS, RDS automaticamente criptografados
- Modelos treinados armazenados criptografados
- Chaves gerenciadas pela AWS (SSE-S3) ou pelo cliente (SSE-KMS, CMK)

### Para a prova
- "Proteger dados em trânsito" → TLS
- "Proteger dados armazenados" → KMS + criptografia em repouso
- "Cliente controla as chaves" → CMK (Customer Managed Keys) no KMS

---

## Isolamento de Rede

### VPC (Virtual Private Cloud)
- Rede privada isolada na AWS
- Modelos SageMaker podem rodar em VPC privada
- Controle total sobre tráfego de entrada/saída

### VPC Endpoints / AWS PrivateLink
- Acesso a serviços AWS **sem passar pela internet**
- Tráfego fica dentro da rede AWS
- Usado para: Bedrock, SageMaker, S3, etc.
- **Quando usar:** requisitos de segurança que proíbem tráfego via internet pública

### Security Groups e NACLs
- Firewalls virtuais que controlam tráfego
- Security Groups: nível de instância (stateful)
- NACLs: nível de subnet (stateless)

---

## Privacidade de Dados no Bedrock

### Garantias
- Dados de entrada (prompts) **NÃO** são usados para treinar modelos base
- Dados ficam na região AWS escolhida
- Logs de modelo são opcionais (opt-in)
- Fine-tuning cria cópia privada do modelo (seus dados não vazam)

### Opt-out
- Por padrão, dados já NÃO são compartilhados no Bedrock
- Diferente de alguns serviços onde opt-out é necessário
- Compliance com requisitos de residência de dados

---

## Controle de Acesso a Dados de ML

| Tipo de dado | Proteção |
|-------------|----------|
| Dados de treino (S3) | Bucket policies + IAM + criptografia |
| Modelos treinados | SageMaker + KMS + IAM |
| Embeddings (vector DB) | OpenSearch security + IAM |
| Prompts/respostas (logs) | CloudWatch Logs + KMS + acesso restrito |
| Fine-tuning datasets | S3 + IAM roles específicos |

---

## Multi-tenancy e Isolamento

### Preocupações
- Dados de um cliente não devem ser acessíveis por outro
- Modelos customizados são privados
- Fine-tuning não contamina o modelo base para outros clientes

### Como a AWS garante
- Isolamento computacional por conta AWS
- Criptografia com chaves separadas por cliente
- VPC isolation para SageMaker
- Bedrock: cada inferência é isolada

---

## Data Residency (Residência de Dados)

### O que é
Garantir que dados são processados e armazenados em regiões geográficas específicas (compliance com leis locais).

### Implicações para IA
- Escolher região AWS que atenda requisitos legais
- Verificar se o serviço/modelo está disponível na região necessária
- LGPD (Brasil), GDPR (EU) podem exigir dados em regiões específicas
- Bedrock: disponibilidade de modelos varia por região

---

## Resumo para a Prova

| Requisito de segurança | Solução AWS |
|------------------------|-------------|
| Criptografar dados armazenados | AWS KMS + encryption at rest |
| Criptografar dados em trânsito | TLS/HTTPS |
| Acessar Bedrock sem internet | VPC Endpoints / PrivateLink |
| Isolar rede do modelo | VPC + Security Groups |
| Garantir que dados não treinem modelo base | Bedrock (padrão) |
| Dados devem ficar em região específica | Escolher região AWS correta |
| Controlar quem acessa o modelo | IAM policies |
| Chaves de criptografia gerenciadas pelo cliente | AWS KMS CMK |

---

## Cenários de Prova — Segurança

| Cenário descrito na questão | O que testam | Resposta |
|-----------------------------|-------------|----------|
| "Empresa regulada proíbe tráfego via internet para serviços de IA" | Isolamento de rede | VPC Endpoints / PrivateLink |
| "Dados de treino contêm PII e precisam de proteção em repouso" | Criptografia at rest | KMS + S3 SSE-KMS |
| "Empresa quer controlar as chaves de criptografia" | CMK vs AWS-managed | AWS KMS com Customer Managed Keys |
| "LGPD exige que dados de clientes brasileiros fiquem no Brasil" | Data residency | Região sa-east-1 (São Paulo) |
| "Empresa preocupada que Bedrock use seus dados para treinar" | Privacidade | Bedrock garante: dados NÃO treinam modelos base |
| "Precisa de rede privada entre SageMaker e S3" | Tráfego interno | VPC Endpoint para S3 |

---

*Próximo bloco: IAM e controle de acesso para serviços de IA*
