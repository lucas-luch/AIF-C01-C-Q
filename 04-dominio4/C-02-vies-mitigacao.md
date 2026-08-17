# Viés em IA e Mitigação

## Visão Geral

Viés (bias) em sistemas de IA é um tema recorrente na prova. Você precisa entender **onde surge**, **como detectar** e **como mitigar**.

---

## Onde o Viés Surge no Pipeline de ML

| Etapa | Tipo de viés | Exemplo |
|-------|-------------|---------|
| Coleta de dados | Viés de seleção | Coletar dados apenas de uma região/grupo |
| Rotulagem | Viés do anotador | Rotulador com preconceitos inconscientes |
| Feature engineering | Proxy variables | Usar CEP como proxy para raça |
| Treinamento | Viés algorítmico | Modelo amplifica padrões discriminatórios |
| Avaliação | Viés de medição | Métrica que favorece grupo majoritário |
| Deploy | Viés de aplicação | Usar modelo em contexto diferente do pretendido |

---

## Tipos de Métricas de Fairness

| Métrica | O que mede |
|---------|-----------|
| **Demographic Parity** | Proporção de outcomes positivos é igual entre grupos |
| **Equalized Odds** | Taxas de TP e FP são iguais entre grupos |
| **Disparate Impact** | Razão entre taxas de aprovação dos grupos |
| **Counterfactual Fairness** | Decisão mudaria se a pessoa fosse de outro grupo? |

---

## Mitigação em Cada Etapa

### Pré-treinamento (dados)
- Coletar dados diversos e representativos
- Balancear datasets por grupos demográficos
- Remover features que são proxies de atributos protegidos
- Auditar a composição dos dados

### Durante treinamento
- Regularização de fairness (penalizar predições desiguais)
- Adversarial debiasing
- Re-sampling ou re-weighting de dados

### Pós-treinamento (avaliação)
- Avaliar métricas por subgrupo (não apenas global)
- Comparar performance entre grupos demográficos
- Ajustar thresholds por grupo se necessário

### Em produção
- Monitoramento contínuo de fairness metrics
- Alertas quando disparidade excede limites
- Pipeline de re-treinamento quando drift é detectado

---

## SageMaker Clarify — Funcionalidades

### Detecção de Viés (Bias Detection)

**Pre-training bias metrics** (antes de treinar):
- Analisa o dataset para identificar desequilíbrios
- Ex: classe "aprovado" é 80% homens — potencial viés

**Post-training bias metrics** (após treinar):
- Analisa previsões do modelo por subgrupo
- Ex: modelo aprova 90% dos homens mas apenas 60% das mulheres

### Explicabilidade
- **SHAP values** — quanto cada feature contribuiu para uma previsão
- **Feature importance** — ranking global de importância
- Gera relatórios visuais de explicabilidade

### Integração
- Integrado ao SageMaker Pipeline
- Pode rodar automaticamente a cada re-treinamento
- Relatórios salvos em S3

---

## Para IA Generativa (LLMs)

### Tipos de viés em LLMs
- **Viés de representação:** estereótipos em texto gerado
- **Viés de alocação:** recomendar ações diferentes para grupos diferentes
- **Viés de linguagem:** performance diferente entre idiomas

### Mitigação em LLMs
| Técnica | Como ajuda |
|---------|-----------|
| Guardrails | Filtrar outputs com estereótipos |
| Prompt engineering | Instruir modelo a ser neutro e inclusivo |
| Human evaluation | Avaliadores diversos revisam outputs |
| Diverse training data | Dados de pré-treinamento mais equilibrados |
| Red teaming | Testar proativamente por viés |

---

## Resumo para a Prova

| Pergunta | Resposta |
|----------|----------|
| "Detectar viés nos dados antes de treinar?" | SageMaker Clarify (pre-training bias) |
| "Detectar viés nas previsões do modelo?" | SageMaker Clarify (post-training bias) |
| "Entender por que o modelo decidiu X?" | SageMaker Clarify (SHAP) |
| "Filtrar outputs com viés em LLMs?" | Bedrock Guardrails |
| "Monitorar fairness em produção?" | SageMaker Model Monitor + Clarify |
| "Dados de treino não-representativos?" | Viés de seleção → coletar dados diversos |
| "Modelo amplifica discriminação?" | Viés algorítmico → regularização + auditoria |

---

*Próximo bloco: Explicabilidade e interpretabilidade*
