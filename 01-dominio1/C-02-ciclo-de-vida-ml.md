# Ciclo de Vida de ML (ML Pipeline)

## Visão Geral

O ciclo de vida de Machine Learning é o processo completo desde a identificação de um problema de negócio até a manutenção do modelo em produção. A prova AIF-C01 exige que você saiba **identificar cada etapa**, os serviços AWS relevantes, e os conceitos de MLOps.

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

**Serviços AWS:** S3 (armazenamento), AWS Glue (ETL), Athena (consultas), Lake Formation (data lake)

### 3. Feature Engineering

- Selecionar as variáveis (features) mais relevantes para o modelo
- Criar novas features a partir das existentes
- Reduzir dimensionalidade quando necessário
- Encoding de variáveis categóricas (one-hot, label encoding)
- Scaling/normalização de variáveis numéricas

**Importância:** Features de qualidade frequentemente importam mais que algoritmos sofisticados.

### 4. Treinamento do Modelo

- Escolher o algoritmo adequado ao problema
- Dividir dados em **treino / validação / teste** (ex: 70/15/15)
- Treinar o modelo nos dados de treino
- Ajustar hiperparâmetros usando dados de validação
- Experimentar múltiplos algoritmos e comparar resultados

**Serviços AWS:** Amazon SageMaker AI (notebooks, training jobs, built-in algorithms, Autopilot)

### 5. Avaliação do Modelo

- Testar o modelo nos dados de **teste** (nunca vistos durante treino)
- Calcular métricas técnicas apropriadas (acurácia, F1, RMSE, etc.)
- Avaliar métricas de negócio (ver seção abaixo)
- Comparar com baseline (modelo simples ou regra de negócio)
- Verificar overfitting/underfitting
- Decidir se o modelo atende os critérios de aceitação

### 6. Deploy (Implantação)

- Colocar o modelo em produção para fazer previsões em dados reais
- Escolher o método de servir adequado (ver seção "Métodos de Servir em Produção")
- Testes A/B para comparar modelo novo vs antigo

**Serviços AWS:** Amazon SageMaker AI Endpoints, SageMaker Batch Transform, Amazon Bedrock (para FMs)

### 7. Monitoramento e Retreinamento

- Monitorar performance do modelo ao longo do tempo
- Detectar **data drift** — dados em produção mudam em relação ao treino
- Detectar **model drift** — performance do modelo degrada
- Definir alertas e triggers para retreinamento
- Retreinar periodicamente ou quando a performance cair

**Serviços AWS:** SageMaker Model Monitor, Amazon CloudWatch

---

## Data Drift vs Model Drift

| Conceito | Descrição | Exemplo |
|----------|-----------|---------|
| **Data Drift** | Distribuição dos dados de entrada muda ao longo do tempo | Clientes com perfil diferente começam a usar o sistema |
| **Model Drift** | Performance do modelo degrada (previsões ficam piores) | Taxa de acerto cai de 95% para 80% em 3 meses |
| **Concept Drift** | A relação entre input e output muda | O que era "fraude" antes não é mais (novo tipo de fraude surge) |

> **DICA PARA A PROVA:** Se a questão descreve "o modelo parou de funcionar bem depois de alguns meses" sem que o modelo tenha mudado, pense em data drift ou concept drift. A solução típica é retreinar com dados recentes.

---

## Divisão de Dados

| Conjunto | Propósito | Uso |
|----------|-----------|-----|
| **Treino** (~70%) | Aprender padrões | O modelo treina com esses dados |
| **Validação** (~15%) | Ajustar hiperparâmetros | Usado durante o treino para tuning |
| **Teste** (~15%) | Avaliação final | Usado ao final para medir performance real |

**Regra importante:** O modelo não deve ver os dados de teste durante o treino ou ajuste — isso comprometeria a avaliação imparcial.

---

## MLOps (Machine Learning Operations)

MLOps são as práticas e ferramentas para levar modelos de ML à produção de forma **confiável, repetível e escalável**. É análogo a DevOps, mas aplicado ao ciclo de vida de ML.

### Conceitos fundamentais de MLOps

| Conceito | Descrição |
|----------|-----------|
| **Experimentação** | Rastrear experimentos (parâmetros, métricas, artefatos) para reprodutibilidade |
| **Processos repetíveis** | Pipelines automatizados que permitem treinar e deployar modelos de forma consistente |
| **Sistemas dimensionáveis** | Infraestrutura que escala conforme demanda (dados maiores, mais modelos) |
| **Dívida técnica** | Custo acumulado de decisões rápidas (código mal estruturado, dados não documentados, modelos sem monitoramento) |
| **Prontidão para produção** | Critérios que um modelo precisa atender antes de ir para produção (performance, testes, documentação) |
| **Monitoramento de modelos** | Acompanhar continuamente performance, drift e integridade dos dados em produção |
| **Retreinamento** | Atualizar o modelo com dados novos quando a performance degrada |

### Serviços AWS para MLOps

| Serviço/Feature | Função no MLOps |
|-----------------|-----------------|
| **SageMaker Pipelines** | Orquestração de pipelines de ML (CI/CD para modelos) |
| **SageMaker Model Monitor** | Monitoramento contínuo de drift e qualidade |
| **SageMaker Experiments** | Rastreamento de experimentos e comparação de resultados |
| **SageMaker Model Registry** | Versionamento e catalogação de modelos |
| **Amazon CloudWatch** | Alertas e métricas de infraestrutura |

> **DICA PARA A PROVA:** Se a questão menciona "automatizar pipeline de ML", "processos repetíveis" ou "CI/CD para modelos", a resposta geralmente envolve SageMaker Pipelines. Se menciona "detectar degradação em produção", pense em SageMaker Model Monitor.

---

## Origens de Modelos

O Exam Guide exige reconhecer as diferentes fontes de onde um modelo pode vir.

| Origem | Descrição | Quando usar | Serviço AWS |
|--------|-----------|-------------|-------------|
| **Pré-treinado open-source** | Modelos treinados pela comunidade, disponíveis publicamente (ex: Hugging Face, Llama) | Quando existe um modelo adequado e se quer customizar ou usar diretamente | SageMaker JumpStart, SageMaker AI |
| **Pré-treinado proprietário** | Modelos treinados por provedores (ex: Claude, Amazon Nova, Titan) | Quando se quer usar via API sem gerenciar infraestrutura de modelo | Amazon Bedrock |
| **Customizado (treinado do zero)** | Modelo treinado pela própria organização com dados internos | Quando o problema é muito específico e nenhum modelo existente atende | Amazon SageMaker AI |

> **CUIDADO:** "Pré-treinado" não significa "pronto para qualquer tarefa". Um modelo pré-treinado pode precisar de fine-tuning ou prompt engineering para funcionar bem no caso de uso específico.

---

## Métodos de Servir em Produção

Como disponibilizar um modelo treinado para uso em aplicações.

| Método | Descrição | Vantagens | Desvantagens |
|--------|-----------|-----------|--------------|
| **API gerenciada** | Serviço AWS hospeda e gerencia o modelo (Bedrock, SageMaker AI Endpoints) | Menor complexidade operacional, escalabilidade automática | Menos controle, custo pode ser maior em alto volume |
| **API auto-hospedada** | Organização deploya o modelo em sua própria infraestrutura (ECS, EKS, EC2) | Controle total, possível otimização de custo em escala | Maior complexidade operacional, responsabilidade de manter |

### Trade-offs

| Critério | API Gerenciada | API Auto-Hospedada |
|----------|----------------|---------------------|
| Complexidade operacional | Baixa | Alta |
| Controle sobre infraestrutura | Limitado | Total |
| Escalabilidade | Automática | Precisa configurar |
| Custo em baixo volume | Geralmente menor | Pode ser maior (infra ociosa) |
| Custo em alto volume | Pode ser maior | Potencialmente menor |
| Tempo para produção | Rápido | Mais demorado |

> **DICA PARA A PROVA:** Se a questão enfatiza "reduzir overhead operacional" ou "focar no problema de negócio, não na infraestrutura", a resposta tende a ser API gerenciada (Bedrock, SageMaker AI endpoints).

---

## Métricas de Avaliação — Modelo e Negócio

A AIF-C01 distingue entre métricas técnicas (de modelo) e métricas de negócio.

### Métricas de Modelo (técnicas)

| Métrica | Uso |
|---------|-----|
| **Acurácia** | Proporção de previsões corretas (cuidado com dados desbalanceados) |
| **Precisão** | Dos positivos previstos, quantos são reais |
| **Recall** | Dos positivos reais, quantos foram detectados |
| **F1 Score** | Média harmônica de precisão e recall |

*(Detalhes completos no C-04 — Métricas de Avaliação)*

### Métricas de Negócio

| Métrica | O que mede |
|---------|-----------|
| **ROI (Retorno sobre Investimento)** | Valor gerado pelo modelo vs. custo de desenvolvimento e operação |
| **Custo por usuário** | Quanto custa servir previsões/interações para cada usuário |
| **Custos de desenvolvimento** | Investimento em dados, treinamento, infraestrutura, equipe |
| **Feedback do cliente** | Satisfação e percepção de valor pelos usuários finais |

### Relação entre métricas técnicas e de negócio

Um modelo com excelentes métricas técnicas (F1 alto) pode ter ROI negativo se:
- O custo de operação é desproporcional ao valor gerado
- O problema resolvido não é prioritário para o negócio
- A integração com processos existentes é complexa demais

> **DICA PARA A PROVA:** Questões que mencionam "avaliar se o projeto de ML vale a pena" ou "justificar investimento" pedem métricas de negócio (ROI, custo). Questões que mencionam "o modelo está bom o suficiente?" pedem métricas técnicas (F1, acurácia).

---

## Serviços AWS no Pipeline

| Etapa | Serviços |
|-------|----------|
| Coleta/Preparação | S3, AWS Glue, Athena, Lake Formation, Amazon EMR |
| Feature Engineering | SageMaker AI Processing, AWS Glue DataBrew |
| Treinamento | Amazon SageMaker AI (Training, Autopilot), SageMaker JumpStart |
| Avaliação | SageMaker Experiments, SageMaker Clarify, Amazon Bedrock Model Evaluation |
| Deploy | SageMaker AI Endpoints, Batch Transform, Amazon Bedrock |
| Monitoramento/MLOps | SageMaker Model Monitor, SageMaker Pipelines, CloudWatch |
| Desenvolvimento assistido por IA | Amazon Q, Kiro |
| Visualização/Análise | Amazon Quick |

---
