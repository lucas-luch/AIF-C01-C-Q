# IAM e Controle de Acesso para Serviços de IA

## Visão Geral

IAM (Identity and Access Management) controla **quem pode fazer o quê** nos serviços de IA da AWS.

---

## Princípios de IAM

### Menor Privilégio (Least Privilege)
- Conceder APENAS as permissões necessárias para a tarefa
- Negar tudo por padrão, permitir explicitamente
- Revisar e remover permissões não utilizadas

### Separação de Responsabilidades
- Quem treina modelos ≠ quem faz deploy ≠ quem acessa produção
- Roles diferentes para cada etapa do pipeline

---

## IAM para SageMaker

### Execution Role
- Role que o SageMaker assume para executar jobs
- Precisa de acesso a: S3 (dados), ECR (containers), KMS (chaves)
- Uma role por propósito (treino, inferência, processamento)

### Permissões típicas
| Ação | Permissão necessária |
|------|---------------------|
| Ler dados de treino | s3:GetObject no bucket de dados |
| Salvar modelo | s3:PutObject no bucket de saída |
| Criar endpoint | sagemaker:CreateEndpoint |
| Invocar endpoint | sagemaker:InvokeEndpoint |
| Usar KMS | kms:Decrypt, kms:GenerateDataKey |

---

## IAM para Amazon Bedrock

### Permissões principais
| Ação | Permission |
|------|-----------|
| Invocar modelo | bedrock:InvokeModel |
| Listar modelos | bedrock:ListFoundationModels |
| Criar Knowledge Base | bedrock:CreateKnowledgeBase |
| Invocar Agent | bedrock:InvokeAgent |
| Gerenciar Guardrails | bedrock:CreateGuardrail |

### Model Access
- Antes de usar um modelo no Bedrock, deve **solicitar acesso** (model access request)
- Controle adicional além do IAM
- Permite governança sobre quais modelos a organização pode usar

---

## Resource-based Policies

### O que são
Políticas anexadas ao recurso (não ao usuário) — definem quem pode acessar o recurso.

### Exemplos
- **S3 bucket policy** — quem pode ler os dados de treino
- **KMS key policy** — quem pode usar a chave para criptografar/descriptografar
- **SageMaker endpoint policy** — quem pode invocar o endpoint

---

## Service Control Policies (SCPs)

### O que são
Políticas no AWS Organizations que limitam o que contas podem fazer — nível organizacional.

### Uso para IA
- Restringir quais regiões podem ser usadas (data residency)
- Bloquear acesso a modelos específicos no Bedrock
- Forçar uso de VPC endpoints
- Prevenir que equipes criem recursos de IA sem aprovação

---

## Logging e Auditoria

### AWS CloudTrail
- Registra **todas** as chamadas de API na conta
- Quem chamou, quando, de onde, com quais parâmetros
- Essencial para auditoria e compliance
- Responde: "Quem invocou o modelo Bedrock às 3h da manhã?"

### Amazon CloudWatch
- Métricas de uso (invocações, latência, erros)
- Logs de inferência (opcional)
- Alarmes quando métricas excedem limites

### Bedrock Model Invocation Logging
- Log detalhado de inputs e outputs (opt-in)
- Pode enviar para S3 ou CloudWatch Logs
- Útil para auditoria e debugging
- **Cuidado:** pode conter dados sensíveis — proteger com acesso restrito

---

## Resumo para a Prova

| Cenário | Solução |
|---------|---------|
| "Quem invocou o modelo?" | CloudTrail |
| "Menor privilégio para equipe de ML" | IAM policies específicas por role |
| "SageMaker precisa ler dados do S3" | Execution Role com s3:GetObject |
| "Bloquear uso de certos modelos na organização" | SCPs no Organizations |
| "Auditar chamadas ao Bedrock" | CloudTrail + Model Invocation Logging |
| "Controlar acesso ao endpoint de inferência" | IAM policy com sagemaker:InvokeEndpoint |
| "Forçar VPC endpoint" | SCP + IAM condition keys |

---

## Cenários de Prova — IAM e Auditoria

| Cenário descrito | Armadilha comum | Resposta correta |
|-----------------|-----------------|------------------|
| "Saber QUEM fez uma chamada ao Bedrock e QUANDO" | Confundir com CloudWatch (métricas) | **CloudTrail** (auditoria de API calls) |
| "Limitar quais FMs a equipe pode usar no Bedrock" | Pensar em Guardrails (filtra conteúdo, não acesso) | **IAM policies** com condição em bedrock:ModelId |
| "50 contas AWS — nenhuma pode acessar Bedrock sem VPC endpoint" | Configurar IAM conta por conta | **SCPs** no Organizations (política organizacional) |
| "Logs de inferência contêm PII — precisam ser protegidos" | Desabilitar logging | **Model Invocation Logging** com destino criptografado (KMS) + IAM restritivo |
| "Data scientist quer criar endpoint em produção" | Dar admin access | **IAM com least privilege**: DataScientist pode treinar mas NÃO pode CreateEndpoint |
| "Equipe de compliance quer ver o que o chatbot respondeu na semana passada" | CloudTrail (só mostra que API foi chamada, não o conteúdo) | **Model Invocation Logging** (registra inputs + outputs) |

---

*Próximo bloco: Conformidade e privacidade (LGPD, GDPR, PII)*
