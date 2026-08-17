# Mini-Simulado — Domínio 5: Segurança, Conformidade e Governança

**Instruções:** 10 questões, ~14 minutos.

---

### Q1

Uma empresa precisa garantir que chamadas ao Amazon Bedrock não passem pela internet pública por requisitos regulatórios. Qual recurso usar?

A) AWS WAF  
B) VPC Endpoints (PrivateLink)  
C) HTTPS  
D) Security Groups  

---

### Q2

Qual serviço registra TODAS as chamadas de API feitas na conta AWS, permitindo auditoria completa?

A) Amazon CloudWatch  
B) AWS CloudTrail  
C) Amazon GuardDuty  
D) AWS Trusted Advisor  

---

### Q3

Uma equipe de ML quer controlar versões de modelos e exigir aprovação humana antes do deploy em produção. Qual serviço usar?

A) Amazon S3 versioning  
B) SageMaker Model Registry  
C) AWS CodePipeline  
D) Amazon ECR  

---

### Q4

Qual serviço AWS detecta dados sensíveis (PII, credenciais) armazenados em buckets S3?

A) Amazon Inspector  
B) Amazon Macie  
C) AWS Config  
D) Amazon Comprehend  

---

### Q5

No modelo de responsabilidade compartilhada para IA, qual é responsabilidade do CLIENTE?

A) Segurança física dos data centers  
B) Configurar IAM corretamente e ativar criptografia nos dados  
C) Manter os Foundation Models base atualizados  
D) Isolamento multi-tenant na infraestrutura  

---

### Q6

Uma empresa precisa de relatórios de compliance SOC 2 e ISO 27001 da AWS. Onde encontrar?

A) AWS CloudTrail  
B) AWS Artifact  
C) AWS Config  
D) Amazon Macie  

---

### Q7

Qual princípio de segurança determina que cada role/usuário deve ter APENAS as permissões necessárias para sua tarefa?

A) Defense in depth  
B) Least privilege (menor privilégio)  
C) Zero trust  
D) Separation of concerns  

---

### Q8

Um modelo em produção está com performance degradando. Qual serviço detecta isso automaticamente?

A) CloudTrail  
B) SageMaker Model Monitor  
C) AWS Config  
D) Amazon Inspector  

---

### Q9 (Múltipla Resposta)

Quais são formas de proteger dados em repouso na AWS? **(Selecione DUAS)**

A) HTTPS/TLS  
B) AWS KMS (criptografia com chaves gerenciadas)  
C) VPC Endpoints  
D) S3 Server-Side Encryption (SSE)  
E) Security Groups  

---

### Q10

O que é "ML Lineage Tracking" no SageMaker?

A) Monitorar latência de endpoints  
B) Rastrear a origem completa de um modelo: dados → transformações → treino → deploy  
C) Versionar código-fonte  
D) Gerenciar billing de treinamento  

---

## Gabarito

<details>
<summary>🔍 Ver todas as respostas</summary>

| # | Resposta | Justificativa resumida |
|---|----------|----------------------|
| Q1 | B | VPC Endpoints/PrivateLink = tráfego fica dentro da rede AWS |
| Q2 | B | CloudTrail = audit log de todas as API calls (quem, quando, o quê) |
| Q3 | B | Model Registry = versionamento + approval workflow para modelos |
| Q4 | B | Macie = ML para detectar dados sensíveis no S3 |
| Q5 | B | Cliente é responsável por IAM, criptografia, configuração dos serviços |
| Q6 | B | Artifact = portal de relatórios de compliance da AWS |
| Q7 | B | Least privilege = apenas permissões necessárias, nada além |
| Q8 | B | Model Monitor = detecta data drift, model drift, bias drift |
| Q9 | B, D | KMS gerencia chaves; SSE criptografa objetos no S3 em repouso |
| Q10 | B | Lineage = rastreio completo do pipeline (dados → modelo → endpoint) |

**Resultado:**
- 10/10: Excelente
- 8-9/10: Bom — revise os erros
- 6-7/10: Foco em IAM, KMS, CloudTrail, Model Registry
- <6/10: Releia C-01 a C-04 do Domínio 5

</details>

