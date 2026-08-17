# Questões — Segurança, Conformidade e Governança

---

### Questão 1

Uma empresa com requisitos regulatórios precisa garantir que os dados enviados ao Amazon Bedrock não trafeguem pela internet pública. Qual recurso deve usar?

A) HTTPS  
B) VPC Endpoints / AWS PrivateLink  
C) Security Groups  
D) AWS WAF  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) VPC Endpoints / AWS PrivateLink**

✅ **Por que B está correta:** VPC Endpoints (PrivateLink) permitem que o tráfego entre sua VPC e o Bedrock permaneça dentro da rede AWS, sem passar pela internet pública. Atende requisitos regulatórios de isolamento de rede.

❌ **Por que as outras estão erradas:**
- **A)** HTTPS criptografa o tráfego, mas ele ainda passa pela internet pública.
- **C)** Security Groups controlam tráfego de/para instâncias, não o caminho de rede até o serviço.
- **D)** WAF protege contra ataques web em APIs, não garante tráfego privado.

</details>

---

### Questão 2

Uma empresa quer saber quem invocou um Foundation Model no Bedrock e quando. Qual serviço fornece essa informação?

A) Amazon CloudWatch  
B) AWS CloudTrail  
C) Amazon Macie  
D) AWS Config  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) AWS CloudTrail**

✅ **Por que B está correta:** CloudTrail registra todas as chamadas de API na conta AWS — quem fez, quando, de onde, com quais parâmetros. É o serviço de auditoria para "quem fez o quê".

❌ **Por que as outras estão erradas:**
- **A)** CloudWatch monitora métricas e logs operacionais, não auditoria de API calls.
- **C)** Macie detecta dados sensíveis no S3, não audita chamadas.
- **D)** Config monitora compliance de configurações de recursos, não invocações.

</details>

---

### Questão 3

Qual é a principal garantia do Amazon Bedrock em relação à privacidade dos dados dos clientes?

A) Dados são automaticamente anonimizados antes do processamento  
B) Dados dos clientes NÃO são usados para treinar ou melhorar os modelos base  
C) Dados são armazenados apenas por 24 horas  
D) Todos os dados são processados on-premises  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Dados dos clientes NÃO são usados para treinar ou melhorar os modelos base**

✅ **Por que B está correta:** Bedrock garante que seus prompts, respostas e dados de fine-tuning permanecem privados e não são usados para treinar os modelos base de nenhum provedor.

❌ **Por que as outras estão erradas:**
- **A)** Bedrock não anonimiza automaticamente — você implementa via Guardrails PII se necessário.
- **C)** Não há limite de 24 horas — logs são opcionais e com retenção configurável.
- **D)** Bedrock é um serviço cloud, não on-premises.

</details>

---

### Questão 4

Uma empresa precisa garantir que dados pessoais (PII) não apareçam nas respostas do chatbot e detectar se há dados sensíveis nos buckets S3 usados para treino. Quais serviços usar? **(Selecione DUAS)**

A) Bedrock Guardrails (PII filter)  
B) Amazon Personalize  
C) Amazon Macie  
D) Amazon Forecast  
E) AWS Glue  

<details>
<summary>🔍 Ver resposta</summary>

**Respostas: A e C**

✅ **Por que A está correta:** Bedrock Guardrails com PII filter detecta e mascara/bloqueia dados pessoais (CPF, email, telefone) nas respostas do chatbot — proteção em tempo de inferência.

✅ **Por que C está correta:** Amazon Macie usa ML para detectar dados sensíveis (PII, credenciais, dados financeiros) armazenados em buckets S3 — auditoria dos dados de treino.

❌ **Por que as outras estão erradas:**
- **B)** Personalize é para recomendações, não proteção de dados.
- **D)** Forecast é previsão de séries temporais.
- **E)** Glue é ETL — processa dados mas não detecta PII automaticamente.

</details>

---

### Questão 5

Uma equipe de ML quer controlar quais versões de modelos podem ser implantadas em produção, com aprovação humana obrigatória. Qual serviço gerencia isso?

A) Amazon S3 versioning  
B) SageMaker Model Registry  
C) AWS CodeDeploy  
D) Amazon ECR  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) SageMaker Model Registry**

✅ **Por que B está correta:** Model Registry versiona modelos, gerencia status (Pending/Approved/Rejected) e permite workflow de aprovação humana antes do deploy em produção — governança de modelos.

❌ **Por que as outras estão erradas:**
- **A)** S3 versioning versiona objetos, não gerencia workflow de aprovação de modelos.
- **C)** CodeDeploy é para deploy de aplicações, não governança de modelos ML.
- **D)** ECR armazena container images, não gerencia aprovação de modelos.

</details>

---

### Questão 6

Uma empresa detectou que a performance do seu modelo de previsão de demanda degradou 15% nos últimos 30 dias. Qual serviço teria detectado isso automaticamente?

A) AWS CloudTrail  
B) SageMaker Model Monitor  
C) Amazon Inspector  
D) AWS Trusted Advisor  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) SageMaker Model Monitor**

✅ **Por que B está correta:** Model Monitor monitora continuamente a qualidade do modelo em produção — detecta model drift (degradação de performance), data drift e mudanças em fairness. Gera alertas quando métricas excedem thresholds.

❌ **Por que as outras estão erradas:**
- **A)** CloudTrail audita chamadas de API, não monitora qualidade de modelos.
- **C)** Inspector verifica vulnerabilidades de segurança em instâncias/containers.
- **D)** Trusted Advisor dá recomendações de custo/segurança/performance de infraestrutura AWS, não de modelos ML.

</details>

