# Governança de Modelos

## Visão Geral

Governança de modelos garante controle, rastreabilidade e qualidade ao longo do ciclo de vida de modelos em produção.

---

## Model Registry (Registro de Modelos)

### O que é
Repositório centralizado para catalogar, versionar e gerenciar modelos ML.

### SageMaker Model Registry
| Funcionalidade | Descrição |
|---------------|-----------|
| Versionamento | Cada modelo tem versão numerada |
| Status | Pending → Approved → Deployed (ou Rejected) |
| Metadados | Métricas, hiperparâmetros, dataset usado |
| Approval workflow | Aprovação humana antes de deploy |
| Groups | Agrupar versões do mesmo modelo |

### Benefícios
- Saber qual versão está em produção
- Histórico completo de versões anteriores
- Rollback facilitado (voltar versão anterior)
- Governança com aprovação antes de deploy

---

## Model Lineage (Linhagem)

### O que é
Rastreio completo da origem e transformações de um modelo — "de onde veio cada coisa".

### O que rastreia
```
Dados de origem (S3)
    ↓
Transformações (Glue, Processing)
    ↓
Features usadas (Feature Store)
    ↓
Algoritmo e hiperparâmetros
    ↓
Job de treinamento
    ↓
Métricas de avaliação
    ↓
Modelo resultante
    ↓
Endpoint de deploy
```

### Por que importa
- **Auditoria:** "Com quais dados este modelo foi treinado?"
- **Reprodutibilidade:** recriar o modelo exatamente
- **Debugging:** "Por que o modelo está errado?" → verificar dados e processo
- **Compliance:** demonstrar que o processo foi adequado

### SageMaker ML Lineage Tracking
- Rastreia automaticamente: datasets, jobs, modelos, endpoints
- Visualização de grafo de dependências
- Integrado ao SageMaker Pipelines

---

## MLOps (ML Operations)

### O que é
Práticas de DevOps aplicadas ao ciclo de vida de ML — automatizar treino, avaliação, deploy e monitoramento.

### SageMaker Pipelines
- CI/CD para ML
- Define pipeline como código (DAG de steps)
- Steps: processamento → treino → avaliação → registro → deploy
- Execução automatizada e reprodutível
- Integra com Model Registry (aprovação automática ou manual)

### Benefícios de MLOps
- Reprodutibilidade dos experimentos
- Deploy consistente e automatizado
- Rollback rápido se modelo degradar
- Monitoramento contínuo pós-deploy
- Auditoria completa do processo

---

## Monitoramento em Produção

### SageMaker Model Monitor
| Tipo de monitoramento | O que detecta |
|----------------------|---------------|
| Data Quality | Mudanças na distribuição dos dados de entrada |
| Model Quality | Degradação da performance (accuracy, etc.) |
| Bias Drift | Mudanças nas métricas de fairness |
| Feature Attribution | Mudanças na importância das features |

### Alertas e Ações
- CloudWatch Alarms quando métricas excedem thresholds
- Triggers automáticos para re-treinamento
- Notificações para equipe de ML
- Dashboard de saúde do modelo

---

## Aprovações e Controle de Deploy

### Workflow típico
```
1. Modelo treinado → registrado no Model Registry (status: Pending)
2. Avaliação automática (métricas vs threshold)
3. Se passar → aprovação humana (ou automática)
4. Status: Approved
5. Deploy em staging → testes
6. Deploy em produção
7. Monitoramento contínuo
```

### Boas práticas
- Nunca deploy direto em produção sem avaliação
- A/B testing para comparar modelo novo vs atual
- Canary deployment — deploy para % pequeno de tráfego primeiro
- Rollback automático se métricas caírem

---

## Resumo para a Prova

| Conceito | Serviço/Ferramenta |
|----------|-------------------|
| Versionar modelos | SageMaker Model Registry |
| Rastrear origem dos dados e modelos | SageMaker ML Lineage Tracking |
| CI/CD para ML | SageMaker Pipelines |
| Monitorar drift em produção | SageMaker Model Monitor |
| Aprovação antes de deploy | Model Registry (approval workflow) |
| Alertas de degradação | CloudWatch Alarms |
| Auditar quem fez deploy | CloudTrail |
| Documentar modelo | SageMaker Model Cards |
| Framework de governança de segurança GenAI | Generative AI Security Scoping Matrix |
| Compliance de configuração de recursos | AWS Config |
| Vulnerabilidades de infraestrutura | Amazon Inspector |
| Recomendações de boas práticas | AWS Trusted Advisor |

---

## Generative AI Security Scoping Matrix

O Exam Guide menciona explicitamente a "Matriz de Controles de Segurança da IA Generativa" como framework de governança.

### O que é
Framework/ferramenta que ajuda organizações a identificar **quais controles de segurança são necessários** para suas aplicações de IA generativa, baseado no tipo de uso e nível de risco.

### Finalidade
- Mapear riscos de segurança por tipo de aplicação GenAI
- Definir controles proporcionais ao risco
- Padronizar avaliação de segurança entre equipes
- Facilitar comunicação entre segurança e desenvolvimento

### Categorias típicas de risco avaliadas
- Acesso a dados sensíveis
- Interação com usuários externos
- Execução de ações autônomas (agents)
- Geração de conteúdo público
- Integração com sistemas críticos

> **DICA PARA A PROVA:** Se a questão menciona "framework para avaliar controles de segurança de aplicações GenAI" ou "matriz de escopo de segurança", a resposta é Generative AI Security Scoping Matrix.

---

## Processos de Governança

O Exam Guide exige reconhecer processos para seguir protocolos de governança.

### Frameworks de Governança

| Elemento | Descrição |
|----------|-----------|
| **Políticas** | Regras escritas sobre uso aceitável de IA na organização |
| **Cadência de revisão** | Periodicidade com que modelos/sistemas são reavaliados (ex: trimestral) |
| **Estratégias de revisão** | Como as revisões são conduzidas (peer review, comitê, automática) |
| **Padrões de transparência** | O que deve ser documentado e comunicado (Model Cards, Service Cards) |
| **Requisitos de treinamento de equipe** | Treinamento obrigatório para quem desenvolve/opera IA (IA responsável, segurança, compliance) |

### Cadência de Revisão

| O que revisar | Frequência sugerida | Motivo |
|---------------|--------------------:|--------|
| Performance do modelo | Contínua (Model Monitor) | Detectar degradação rapidamente |
| Fairness/viés | Trimestral ou quando dados mudam | Viés pode surgir com drift |
| Compliance | Anual ou quando regulação muda | Manter conformidade |
| Segurança | Contínua + auditoria periódica | Ameaças evoluem |
| Documentação (Model Cards) | A cada nova versão do modelo | Manter atualizado |

### Requisitos de Treinamento de Equipe

| Quem | Treinamento necessário |
|------|----------------------|
| Desenvolvedores de IA | Segurança de GenAI, IA responsável, privacidade |
| Data scientists | Viés, fairness, preparação de dados, MLOps |
| Gestores/stakeholders | Riscos legais, governança, ética em IA |
| Equipe de segurança | Ameaças específicas de GenAI (injection, jailbreaking) |
| Equipe de compliance | Regulamentações aplicáveis, documentação necessária |

---

## Serviços AWS de Governança e Compliance

O Exam Guide lista explicitamente estes serviços para governança.

### AWS Config

| Aspecto | Descrição |
|---------|-----------|
| **O que faz** | Monitora e registra configurações de recursos AWS continuamente |
| **Para IA** | Verificar se recursos de ML/GenAI estão configurados conforme regras (criptografia ativa, VPC configurada, etc.) |
| **Exemplo** | Regra: "Todos os endpoints SageMaker devem ter criptografia KMS" — Config detecta violações |
| **Benefício** | Compliance contínuo — detecta desvios de configuração automaticamente |

### Amazon Inspector

| Aspecto | Descrição |
|---------|-----------|
| **O que faz** | Avalia vulnerabilidades de segurança em workloads (EC2, containers, Lambda) |
| **Para IA** | Verificar se infraestrutura que hospeda modelos tem vulnerabilidades |
| **Exemplo** | Detectar CVEs em containers que rodam modelos, patches faltando |
| **Benefício** | Segurança proativa da infraestrutura de ML |

### AWS Trusted Advisor

| Aspecto | Descrição |
|---------|-----------|
| **O que faz** | Recomendações automáticas de boas práticas (custo, segurança, performance, tolerância a falhas) |
| **Para IA** | Identificar recursos sub-utilizados, configurações inseguras, oportunidades de otimização |
| **Exemplo** | "Endpoint SageMaker provisionado mas com 5% de uso — considere serverless" |
| **Benefício** | Otimização e governança automática |

### AWS Audit Manager

| Aspecto | Descrição |
|---------|-----------|
| **O que faz** | Automatiza coleta de evidências para auditorias de compliance |
| **Para IA** | Gerar relatórios de compliance para reguladores |
| **Exemplo** | Coletar evidências de que criptografia está ativa, IAM está configurado, logs existem |
| **Benefício** | Simplifica auditorias de compliance |

---

## Cenários de Prova Atualizados

| Cenário na prova | Resposta |
|-----------------|----------|
| "Qual versão está em produção?" | Model Registry |
| "Com quais dados o modelo foi treinado?" | Lineage Tracking |
| "Automatizar treino e deploy" | SageMaker Pipelines |
| "Modelo piorou ao longo do tempo" | Model Monitor (detect drift) |
| "Aprovar modelo antes de ir para produção" | Model Registry (approval) |
| "Verificar que recursos estão configurados corretamente" | AWS Config |
| "Encontrar vulnerabilidades na infraestrutura" | Amazon Inspector |
| "Recomendações de boas práticas de custo/segurança" | AWS Trusted Advisor |
| "Coletar evidências para auditoria de compliance" | AWS Audit Manager |
| "Framework para avaliar segurança de apps GenAI" | Generative AI Security Scoping Matrix |
| "Definir políticas de uso de IA na organização" | Framework de governança (políticas + cadência + treinamento) |

---
