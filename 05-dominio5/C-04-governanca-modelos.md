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

| Cenário na prova | Resposta |
|-----------------|----------|
| "Qual versão está em produção?" | Model Registry |
| "Com quais dados o modelo foi treinado?" | Lineage Tracking |
| "Automatizar treino e deploy" | SageMaker Pipelines |
| "Modelo piorou ao longo do tempo" | Model Monitor (detect drift) |
| "Aprovar modelo antes de ir para produção" | Model Registry (approval) |
| "Reproduzir o treinamento" | Lineage + Pipelines |

---

*Próximo: Mini-simulado Domínio 5*
