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

Um CISO (Chief Information Security Officer) está avaliando o Amazon Bedrock para uso com dados corporativos sensíveis. A principal preocupação é que os prompts enviados e as respostas geradas possam ser usados para melhorar os modelos de terceiros (Anthropic, Meta, etc.), expondo informações proprietárias. Qual garantia o Bedrock oferece para mitigar essa preocupação?

A) O Bedrock anonimiza automaticamente todos os dados antes de enviá-los aos provedores de modelos  
B) Os dados dos clientes (prompts e respostas) NÃO são usados para treinar ou melhorar os modelos base de nenhum provedor  
C) O Bedrock armazena os dados apenas por 24 horas e depois os exclui permanentemente  
D) O Bedrock executa todos os modelos dentro da VPC do cliente, sem tráfego para servidores AWS  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Os dados dos clientes (prompts e respostas) NÃO são usados para treinar ou melhorar os modelos base de nenhum provedor**

✅ **Por que B está correta:** Bedrock garante contratualmente que seus prompts, respostas e dados de fine-tuning permanecem privados e isolados por conta/região. Nenhum provedor de modelo (Anthropic, Meta, Stability AI, etc.) tem acesso para treinamento.

❌ **Por que as outras estão erradas:**
- **A)** Bedrock NÃO anonimiza automaticamente — se você precisa mascarar PII, deve implementar via Guardrails (PII filter) explicitamente.
- **C)** Não existe regra de 24 horas. Logs de invocação são opcionais (opt-in via Model Invocation Logging) com retenção configurável pelo cliente.
- **D)** Bedrock é um serviço gerenciado que roda na infraestrutura AWS, não dentro da VPC do cliente. Para tráfego privado, usa-se VPC Endpoints/PrivateLink (mas o processamento ainda é na AWS).

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



---

### Questão 7

Uma empresa multinacional processa dados de clientes europeus com Amazon Bedrock. O DPO exige que os dados nunca saiam da região europeia E que haja evidência de compliance com GDPR para auditorias. Quais serviços/configurações implementam AMBOS os requisitos? **(Selecione DUAS)**

A) Usar Bedrock na região eu-west-1 (Irlanda) para manter dados na Europa  
B) Amazon Macie para encontrar e classificar dados pessoais nos buckets S3  
C) AWS Artifact para acessar relatórios de compliance e acordos de processamento de dados  
D) Amazon Forecast para prever riscos de compliance  
E) AWS DeepRacer para treinar modelos de detecção de risco  

<details>
<summary>🔍 Ver resposta</summary>

**Respostas: A e C**

✅ **Por que A está correta:** Usar Bedrock em região europeia garante que dados são processados e armazenados na UE — atende requisito de residência de dados do GDPR.

✅ **Por que C está correta:** AWS Artifact fornece relatórios de compliance (SOC, ISO, GDPR DPA) para auditorias — evidência documentada de que a AWS atende requisitos regulatórios.

❌ **Por que as outras estão erradas:**
- **B)** Macie detecta PII no S3 — útil mas não garante residência de dados nem fornece relatórios de compliance.
- **D)** Forecast é previsão de séries temporais — irrelevante para compliance.
- **E)** DeepRacer é plataforma educacional de RL — irrelevante.

</details>

---

### Questão 8

Uma empresa de fintech precisa implementar o princípio do menor privilégio para acesso ao Amazon Bedrock. Diferentes equipes devem ter diferentes níveis de acesso: desenvolvedores podem invocar modelos; cientistas de dados podem fazer fine-tuning; auditores podem apenas ler logs. Qual serviço implementa esse controle granular?

A) Amazon Bedrock Guardrails para controlar o que cada equipe pode perguntar  
B) AWS IAM com policies específicas por role (InvokeModel, CreateModelCustomizationJob, GetModelInvocationLog)  
C) VPC Security Groups para separar tráfego por equipe  
D) AWS KMS para criptografar dados por equipe  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) AWS IAM com policies específicas por role**

✅ **Por que B está correta:** IAM permite criar roles com permissions granulares por ação do Bedrock: `bedrock:InvokeModel` para devs, `bedrock:CreateModelCustomizationJob` para cientistas, `bedrock:GetModelInvocationLogging*` para auditores. É o mecanismo de autorização da AWS.

❌ **Por que as outras estão erradas:**
- **A)** Guardrails filtram CONTEÚDO das respostas — não controlam QUEM pode fazer qual operação.
- **C)** Security Groups controlam tráfego de rede (IPs/portas) — não permissões de API.
- **D)** KMS gerencia chaves de criptografia — não controla acesso a operações específicas.

</details>

---

### Questão 9

Uma empresa está usando Amazon Bedrock e quer habilitar logging de todas as invocações (prompts e respostas) para auditoria interna. Porém, os prompts contêm dados sensíveis de clientes. Qual configuração garante logging para auditoria SEM expor dados sensíveis a equipes não-autorizadas?

A) Habilitar Model Invocation Logging com output para S3 + criptografia com chave KMS gerenciada com acesso restrito  
B) Desabilitar logging completamente para proteger dados  
C) Habilitar CloudTrail — que já registra prompts automaticamente  
D) Usar Guardrails para mascarar PII antes do logging  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: A) Model Invocation Logging com S3 + criptografia KMS com acesso restrito**

✅ **Por que A está correta:** Model Invocation Logging é opt-in e envia logs (prompts + responses) para S3 e/ou CloudWatch. Criptografia com KMS + IAM policies restritivas garante que apenas auditores autorizados acessem. Logging COM proteção.

❌ **Por que as outras estão erradas:**
- **B)** Desabilitar logging viola o requisito de auditoria — não é solução.
- **C)** CloudTrail registra CHAMADAS de API (quem, quando, parâmetros), mas NÃO os prompts/respostas em si.
- **D)** Guardrails mascara PII nas respostas ao USUÁRIO — não filtra o que é armazenado nos logs de invocação.

</details>

---

### Questão 10

Uma empresa está definindo a estratégia de governança para seu pipeline de ML. O CISO exige rastreabilidade completa: saber quais dados treinaram qual versão do modelo, quem aprovou o deploy, e qual modelo está servindo em produção. Quais serviços AWS implementam essa rastreabilidade end-to-end? **(Selecione DUAS)**

A) SageMaker Model Registry — versiona modelos com status de aprovação e metadata de linhagem  
B) Amazon S3 Versioning — versiona os dados de treino  
C) SageMaker ML Lineage Tracking — rastreia relação entre dados, modelos e endpoints  
D) Amazon CloudFront — distribui o modelo globalmente  
E) Amazon Rekognition — analisa imagens dos dashboards  

<details>
<summary>🔍 Ver resposta</summary>

**Respostas: A e C**

✅ **Por que A está correta:** Model Registry versiona modelos, gerencia status (Pending/Approved/Rejected) com quem aprovou, e conecta ao endpoint de produção — rastreabilidade de modelo.

✅ **Por que C está correta:** ML Lineage Tracking rastreia automaticamente as relações: quais dados → geraram qual artefato → treinaram qual modelo → deployado em qual endpoint. Rastreabilidade completa end-to-end.

❌ **Por que as outras estão erradas:**
- **B)** S3 Versioning versiona objetos, mas não conecta dados a modelos ou endpoints — é peça isolada sem linhagem.
- **D)** CloudFront é CDN para distribuição de conteúdo web — irrelevante para ML governance.
- **E)** Rekognition é visão computacional — irrelevante.

</details>

---

### Questão 11

Uma empresa quer garantir que dados usados para fine-tuning no Bedrock estejam criptografados tanto em repouso (armazenados no S3) quanto em trânsito (sendo enviados ao Bedrock). Qual combinação garante criptografia em AMBOS os cenários?

A) S3 Server-Side Encryption (SSE-KMS) para repouso + TLS 1.2+ para trânsito  
B) Apenas HTTPS é suficiente para ambos cenários  
C) Apenas VPC Endpoints garantem criptografia completa  
D) Amazon Macie criptografa dados automaticamente quando detecta PII  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: A) SSE-KMS para repouso + TLS 1.2+ para trânsito**

✅ **Por que A está correta:** SSE-KMS criptografa dados armazenados no S3 (at rest) com chaves gerenciadas. TLS 1.2+ criptografa dados sendo transmitidos (in transit) entre S3/aplicação e Bedrock. Juntos cobrem ambos os estados.

❌ **Por que as outras estão erradas:**
- **B)** HTTPS (TLS) protege dados em trânsito, mas NÃO dados armazenados no S3.
- **C)** VPC Endpoints mantêm tráfego na rede AWS (privacidade) mas não são mecanismo de criptografia.
- **D)** Macie DETECTA dados sensíveis mas NÃO os criptografa — é ferramenta de discovery, não proteção.

</details>
