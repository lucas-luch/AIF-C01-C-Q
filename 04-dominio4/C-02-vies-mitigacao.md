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
- **Análise de qualidade do rótulo** — verificar se anotações estão corretas e consistentes

### Durante treinamento
- Regularização de fairness (penalizar predições desiguais)
- Adversarial debiasing
- Re-sampling ou re-weighting de dados

### Pós-treinamento (avaliação)
- Avaliar métricas por subgrupo (não apenas global)
- Comparar performance entre grupos demográficos
- Ajustar thresholds por grupo se necessário
- **Análise de subgrupos** — avaliar performance em cada segmento demográfico separadamente

### Em produção
- Monitoramento contínuo de fairness metrics
- Alertas quando disparidade excede limites
- Pipeline de re-treinamento quando drift é detectado
- **Auditorias humanas** — revisão periódica dos outputs por especialistas humanos para identificar padrões de viés que métricas automáticas podem não capturar

---

## Auditorias Humanas

Revisões periódicas feitas por pessoas qualificadas para avaliar se o sistema de IA está operando de forma justa.

| Aspecto | Descrição |
|---------|-----------|
| **O que é** | Revisão manual de amostras de outputs/decisões por especialistas |
| **Quando usar** | Periodicamente em produção, antes de deploy, após mudanças significativas |
| **Quem faz** | Especialistas em fairness, representantes dos grupos afetados, equipe de compliance |
| **O que busca** | Padrões de discriminação, estereótipos, erros sistemáticos que métricas não capturam |
| **Ferramenta AWS** | Amazon Augmented AI (A2I) para fluxos de revisão; SageMaker Clarify para análise quantitativa |

> **DICA PARA A PROVA:** Se a questão menciona "detectar viés que métricas automáticas não capturam" ou "revisão periódica de fairness", a resposta envolve auditorias humanas.

---

## Análise de Subgrupos

Avaliar performance e fairness do modelo **separadamente para cada grupo demográfico** relevante, em vez de apenas métricas globais.

### Por que análise global não é suficiente

| Situação | Métrica global | Realidade por subgrupo |
|----------|---------------|----------------------|
| Modelo de crédito com 85% de acurácia | Parece bom | 95% para homens, 60% para mulheres |
| Detector facial com 99% de precisão | Excelente | 99.5% pele clara, 85% pele escura |
| Modelo de recrutamento "neutro" | Sem viés aparente | Recomenda 3x mais homens para cargos técnicos |

### Como fazer
- Definir subgrupos relevantes (gênero, raça, idade, região, etc.)
- Calcular métricas (accuracy, precision, recall, F1) para cada subgrupo
- Comparar disparidades entre subgrupos
- Ferramenta: **SageMaker Clarify** (suporta análise por subgrupo nativamente)

---

## Efeitos do Viés e da Variância

O Exam Guide pede descrever efeitos em: grupos demográficos, imprecisão, overfitting e underfitting.

### Efeitos em grupos demográficos

| Efeito | Descrição | Consequência real |
|--------|-----------|------------------|
| **Performance desigual** | Modelo funciona pior para grupos sub-representados | Grupo minoritário recebe decisões piores |
| **Exclusão** | Modelo não reconhece/atende certo grupo | Sistema é inutilizável para parte da população |
| **Discriminação amplificada** | Modelo amplifica padrões discriminatórios dos dados | Reforça desigualdades existentes |
| **Dano à confiança** | Grupos afetados perdem confiança no sistema | Adoção reduzida, risco reputacional |

### Relação com overfitting e underfitting

| Problema | Conexão com viés |
|----------|-----------------|
| **Overfitting** | Modelo memoriza padrões do grupo majoritário — funciona bem para ele mas generaliza mal para grupos menores |
| **Underfitting** | Modelo não captura a complexidade dos padrões de grupos sub-representados (poucos dados para aprender) |
| **Variância alta** | Modelo é instável para grupos com poucos dados — previsões inconsistentes |
| **Bias alto** | Suposições simplificadoras do modelo afetam desproporcionalmente grupos que não se encaixam no "padrão" assumido |

> **DICA PARA A PROVA:** Se a questão conecta "modelo funciona mal para um subgrupo" + "dados desbalanceados", pense em: viés de seleção (dados) + possível overfitting para o grupo majoritário. Solução: dados mais representativos + análise de subgrupos.

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
