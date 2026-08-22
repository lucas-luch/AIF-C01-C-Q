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
| "LGPD exige proteção adequada de dados de clientes brasileiros" | Data residency / compliance | Região apropriada + criptografia + controle de acesso |
| "Empresa preocupada que Bedrock use seus dados para treinar" | Privacidade | Bedrock garante: dados NÃO treinam modelos base |
| "Precisa de rede privada entre SageMaker e S3" | Tráfego interno | VPC Endpoint para S3 |

---

## Segurança de Aplicações de IA Generativa

O Exam Guide exige reconhecer as considerações de segurança específicas para sistemas GenAI. Essas são ameaças que vão além da segurança de infraestrutura tradicional.

### Ameaças e Proteções

| Ameaça | Descrição | Mitigação |
|--------|-----------|-----------|
| **Prompt injection** | Input malicioso que tenta alterar comportamento do modelo (ignorar instruções, revelar system prompt) | Guardrails, input validation, separação de instrução vs dados do usuário |
| **Data leakage (vazamento de dados)** | Modelo expõe dados sensíveis do treinamento ou do contexto nas respostas | PII filters (Guardrails), data minimization, output validation |
| **Output tóxico** | Modelo gera conteúdo prejudicial, ofensivo ou perigoso | Content filters (Guardrails), denied topics |
| **Toxicidade** | Outputs com linguagem discriminatória, violenta ou sexual | Guardrails content filters, red teaming |

### Filtragem e Validação de Output

| Técnica | O que faz | Ferramenta AWS |
|---------|-----------|---------------|
| **Output filtering** | Bloquear respostas que contenham conteúdo proibido | Bedrock Guardrails (content/word/PII filters) |
| **Output validation** | Verificar se a resposta é coerente e segura antes de entregar | Guardrails grounding check, lógica de aplicação |
| **Grounding check** | Verificar se a resposta está ancorada no contexto fornecido | Bedrock Guardrails (contextual grounding) |
| **Confidence scoring** | Atribuir score de confiança à resposta para decidir se entregar ou escalar | Lógica de aplicação + thresholds |

### Camadas de segurança para GenAI

```
[Input do usuário]
    → Input guardrails (filtrar injection, PII, tópicos proibidos)
        → [Foundation Model processa]
            → Output guardrails (filtrar toxicidade, PII, grounding)
                → Output validation (lógica de aplicação)
                    → [Resposta ao usuário]
```

> **DICA PARA A PROVA:** Se a questão menciona "prevenir que o modelo revele instruções internas" → prompt injection protection. Se menciona "evitar que dados sensíveis apareçam nas respostas" → output filtering + PII filter. Se menciona "verificar que a resposta é fiel ao contexto" → grounding check.

---

## Detecção de Alucinações e Técnicas de Grounding

O Exam Guide exige explicitamente: "métodos de detecção de alucinações e técnicas de fundamentação para melhorar precisão de output."

### Técnicas de Grounding (Fundamentação)

| Técnica | Como funciona | Efetividade |
|---------|---------------|-------------|
| **RAG** | Busca informação em fontes externas e injeta como contexto | Alta — ancora respostas em dados reais |
| **Validação de output** | Verifica se a resposta é consistente com as fontes fornecidas | Média-alta — detecta quando extrapola |
| **Pontuação de confiança (confidence scoring)** | Atribui probabilidade de corretude, escalona para humano se baixa | Média — ajuda na triagem |
| **Citação de fontes** | Modelo cita de onde tirou a informação (facilitando verificação) | Média — não impede alucinação mas facilita detectar |
| **Knowledge Bases for Bedrock** | RAG gerenciado com citações automáticas | Alta — integra retrieval + geração + citação |

### Guardrails — Contextual Grounding

| Feature | O que faz |
|---------|-----------|
| **Grounding check** | Verifica se a resposta é suportada pelo contexto fornecido (fonte de referência) |
| **Relevance check** | Verifica se a resposta é relevante para a pergunta do usuário |
| **Threshold configurável** | Define o nível mínimo de grounding aceitável (0-1) |
| **Ação se falhar** | Bloquear resposta ou retornar mensagem padrão |

> **CUIDADO:** Grounding reduz significativamente alucinações mas **não elimina por completo**. Use em camadas: RAG + grounding check + output validation para máxima proteção.

---

## Segurança de Agentes — Amazon Bedrock AgentCore

O Exam Guide lista explicitamente **AgentCore Identity** e **AgentCore Policy** como recursos de segurança.

### AgentCore Identity

| Aspecto | Descrição |
|---------|-----------|
| **O que é** | Gerenciamento de identidade para agentes de IA — "quem o agente é" |
| **Problema que resolve** | Agentes acessam múltiplos sistemas — precisam de identidade controlada |
| **Como funciona** | Define credenciais e permissões do agente em cada sistema externo |
| **Benefício** | Auditabilidade — saber exatamente o que cada agente pode acessar |

### AgentCore Policy

| Aspecto | Descrição |
|---------|-----------|
| **O que é** | Regras e permissões que controlam o que o agente pode fazer |
| **Problema que resolve** | Agentes autônomos podem executar ações perigosas se sem controle |
| **Como funciona** | Define limites explícitos: quais tools pode usar, quais dados pode acessar, quais ações pode executar |
| **Benefício** | Segurança — agente não pode exceder suas permissões |

> **DICA PARA A PROVA:** "Controlar o que um agente pode acessar/fazer" → AgentCore Policy. "Gerenciar identidade do agente em sistemas externos" → AgentCore Identity. Ambos são sobre **governança de agentes em produção**.

---

## Trilha de Auditoria e Registro de Interações de IA

O Exam Guide exige reconhecer requisitos de registro para interações de IA.

### Requisitos

| Tipo de log | O que registrar | Serviço AWS |
|-------------|----------------|-------------|
| **API calls** | Quem chamou, quando, de onde | AWS CloudTrail |
| **Inputs/outputs do modelo** | Prompts e respostas (para auditoria de conteúdo) | Bedrock Model Invocation Logging |
| **Ações de agentes** | Quais tools foram invocadas, com quais parâmetros | AgentCore Observability, CloudWatch |
| **Decisões de guardrails** | O que foi bloqueado e por quê | Bedrock Guardrails logging |
| **Métricas de uso** | Volume, latência, erros | Amazon CloudWatch |

### Considerações de segurança para logs
- Logs de interações podem conter **dados sensíveis** (PII nos prompts)
- Proteger com criptografia (KMS) e acesso restrito (IAM)
- Definir período de retenção adequado
- Equilibrar necessidade de auditoria vs. privacidade

---

## Citação de Fontes e Documentação de Origens

O Exam Guide menciona "conceito de citação de fontes e documentação de origens de dados" como prática de segurança.

### Linhagem de dados (Data Lineage)

| Conceito | Descrição | Ferramenta AWS |
|----------|-----------|---------------|
| **Linhagem** | Rastrear a origem e transformações dos dados usados no modelo | SageMaker ML Lineage Tracking |
| **Catalogação** | Organizar e documentar datasets disponíveis | AWS Glue Data Catalog, AWS Lake Formation |
| **Citação no output** | Modelo indica de onde extraiu a informação na resposta | Bedrock Knowledge Bases (citações automáticas) |

### Por que importa para segurança
- **Auditabilidade:** Provar que dados de treino são legítimos e licenciados
- **Confiabilidade:** Citações permitem verificar se informação é factual
- **Compliance:** Demonstrar proveniência dos dados para reguladores
- **Debugging:** Quando modelo erra, rastrear o dado que causou o erro

### SageMaker Model Cards neste contexto
- Documentam o modelo: dados usados, métricas, limitações
- Servem como "certidão de nascimento" do modelo
- Suportam auditoria e governança

> **DICA PARA A PROVA:** Se a questão menciona "documentar de onde vieram os dados do modelo" → linhagem (SageMaker Lineage). Se menciona "modelo cita de onde tirou a informação na resposta" → citação de fontes (Knowledge Bases). Se menciona "documentar limitações e uso pretendido do modelo" → Model Cards.

---
