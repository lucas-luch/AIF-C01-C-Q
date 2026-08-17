# Ciclo de Vida de ML (ML Pipeline)

## Visão Geral

O ciclo de vida de Machine Learning é o processo completo desde a identificação de um problema de negócio até a manutenção do modelo em produção. A prova AIF-C01 exige que você saiba **identificar cada etapa** e o que acontece em cada uma.

---

## Etapas do ML Pipeline

### 1. Definição do Problema de Negócio

- Identificar **qual problema** se quer resolver com ML
- Definir métricas de sucesso (KPIs do negócio)
- Avaliar se ML é a abordagem adequada (nem tudo precisa de ML)
- Definir o tipo de tarefa: classificação, regressão, clustering, etc.

**Pergunta-chave:** "Qual decisão este modelo vai ajudar a tomar?"

### 2. Coleta e Preparação de Dados

- **Coleta:** reunir dados relevantes de diversas fontes
- **Limpeza:** tratar dados faltantes, duplicados, inconsistentes
- **Transformação:** normalização, codificação de variáveis categóricas
- **Integração:** combinar dados de múltiplas fontes
- **Análise Exploratória (EDA):** entender distribuições, correlações, outliers

**Serviços AWS:** S3 (armazenamento), Glue (ETL), Athena (consultas), Lake Formation (data lake)

### 3. Feature Engineering

- Selecionar as variáveis (features) mais relevantes para o modelo
- Criar novas features a partir das existentes
- Reduzir dimensionalidade quando necessário
- Encoding de variáveis categóricas (one-hot, label encoding)
- Scaling/normalização de variáveis numéricas

**Importância:** Features de qualidade importam mais que algoritmos sofisticados.

### 4. Treinamento do Modelo

- Escolher o algoritmo adequado ao problema
- Dividir dados em **treino / validação / teste** (ex: 70/15/15)
- Treinar o modelo nos dados de treino
- Ajustar hiperparâmetros usando dados de validação
- Experimentar múltiplos algoritmos e comparar resultados

**Serviços AWS:** SageMaker (notebooks, training jobs, built-in algorithms)

### 5. Avaliação do Modelo

- Testar o modelo nos dados de **teste** (nunca vistos durante treino)
- Calcular métricas apropriadas (acurácia, F1, RMSE, etc.)
- Comparar com baseline (modelo simples ou regra de negócio)
- Verificar overfitting/underfitting
- Decidir se o modelo atende os critérios de aceitação

### 6. Deploy (Implantação)

- Colocar o modelo em produção para fazer previsões em dados reais
- Tipos de deploy:
  - **Real-time endpoint** — resposta imediata (API)
  - **Batch transform** — processar lotes de dados periodicamente
  - **Edge deployment** — rodar no dispositivo local (IoT)
- Testes A/B para comparar modelo novo vs antigo

**Serviços AWS:** SageMaker Endpoints, SageMaker Batch Transform, Lambda + API Gateway

### 7. Monitoramento e Re-treinamento

- Monitorar performance do modelo ao longo do tempo
- Detectar **data drift** — dados em produção mudam em relação ao treino
- Detectar **model drift** — performance do modelo degrada
- Definir alertas e triggers para re-treinamento
- Re-treinar periodicamente ou quando a performance cair

**Serviços AWS:** SageMaker Model Monitor, CloudWatch

---

## Data Drift vs Model Drift

| Conceito | Descrição | Exemplo |
|----------|-----------|---------|
| **Data Drift** | Distribuição dos dados de entrada muda ao longo do tempo | Clientes com perfil diferente começam a usar o sistema |
| **Model Drift** | Performance do modelo degrada (previsões ficam piores) | Taxa de acerto cai de 95% para 80% em 3 meses |
| **Concept Drift** | A relação entre input e output muda | O que era "fraude" antes não é mais (novo tipo de fraude surge) |

---

## Divisão de Dados

| Conjunto | Propósito | Uso |
|----------|-----------|-----|
| **Treino** (~70%) | Aprender padrões | O modelo treina com esses dados |
| **Validação** (~15%) | Ajustar hiperparâmetros | Usado durante o treino para tuning |
| **Teste** (~15%) | Avaliação final | Usado UMA vez ao final para medir performance real |

**Regra de ouro:** O modelo NUNCA deve ver os dados de teste durante o treino ou ajuste.

---

## Resumo para a Prova

| Etapa | Pergunta que responde |
|-------|----------------------|
| Definição do problema | "O que queremos resolver?" |
| Coleta e preparação | "Que dados temos e como organizá-los?" |
| Feature engineering | "Quais variáveis são relevantes?" |
| Treinamento | "Qual algoritmo e configuração usar?" |
| Avaliação | "O modelo é bom o suficiente?" |
| Deploy | "Como colocar em produção?" |
| Monitoramento | "O modelo continua funcionando bem?" |

---

## Serviços AWS no Pipeline

| Etapa | Serviços |
|-------|----------|
| Coleta/Preparação | S3, Glue, Athena, Lake Formation, EMR |
| Feature Engineering | SageMaker Processing, Glue DataBrew |
| Treinamento | SageMaker Training, SageMaker Autopilot |
| Avaliação | SageMaker Experiments, Clarify |
| Deploy | SageMaker Endpoints, Lambda, Batch Transform |
| Monitoramento | SageMaker Model Monitor, CloudWatch |

---

*Próximo bloco: Conceitos Fundamentais (overfitting, underfitting, bias, variance)*
