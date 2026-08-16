# Tipos de Machine Learning

## Visão Geral

Machine Learning (ML) é um subconjunto da Inteligência Artificial que permite que sistemas aprendam e melhorem a partir de dados, sem serem explicitamente programados para cada tarefa. A prova AIF-C01 exige que você saiba **identificar qual tipo de ML usar** em cada cenário.

---

## Aprendizado Supervisionado (Supervised Learning)

O modelo treina com **dados rotulados** — cada entrada (input) tem uma resposta correta associada (label). O objetivo é aprender a mapear entrada → saída para fazer previsões em dados novos.

### Classificação
- A saída é uma **categoria discreta** (classe)
- Exemplos:
  - Email: spam ou não-spam
  - Transação: fraude ou legítima
  - Imagem: gato, cachorro ou pássaro
  - Diagnóstico: positivo ou negativo
- Algoritmos comuns: Logistic Regression, Decision Trees, Random Forest, SVM, Neural Networks

### Regressão
- A saída é um **valor numérico contínuo**
- Exemplos:
  - Prever preço de imóvel
  - Prever demanda de vendas
  - Prever temperatura
  - Estimar tempo de entrega
- Algoritmos comuns: Linear Regression, Polynomial Regression, Neural Networks

### Quando identificar na prova
Palavras-chave: "dados rotulados", "histórico classificado", "prever uma categoria", "prever um valor numérico", "dados de treino com respostas conhecidas".

---

## Aprendizado Não-Supervisionado (Unsupervised Learning)

O modelo trabalha com **dados sem rótulos**. Não existe resposta "correta" — o objetivo é encontrar padrões, estruturas ou agrupamentos ocultos nos dados.

### Clustering (Agrupamento)
- Agrupa dados similares em clusters
- Exemplos:
  - Segmentação de clientes por comportamento
  - Agrupar documentos por tema
  - Identificar comunidades em redes sociais
- Algoritmos comuns: K-Means, DBSCAN, Hierarchical Clustering

### Redução de Dimensionalidade
- Reduz o número de variáveis mantendo a informação essencial
- Útil para visualização e pré-processamento
- Algoritmos comuns: PCA (Principal Component Analysis), t-SNE

### Detecção de Anomalias
- Identifica pontos fora do padrão (outliers)
- Exemplos: detectar falhas em equipamentos, transações incomuns
- Nota: pode ser feito com supervisionado também, mas quando não há rótulos, é não-supervisionado

### Quando identificar na prova
Palavras-chave: "sem rótulos", "agrupar", "segmentar", "encontrar padrões", "dados não categorizados", "descobrir estruturas ocultas".

---

## Aprendizado por Reforço (Reinforcement Learning)

Um **agente** interage com um **ambiente**, executa **ações**, observa o **estado** resultante e recebe **recompensas** (positivas) ou **penalidades** (negativas). O objetivo é aprender uma **política (policy)** que maximize a recompensa acumulada ao longo do tempo.

### Conceitos-chave
| Conceito | Descrição |
|----------|-----------|
| **Agente** | O "aprendiz" que toma decisões |
| **Ambiente** | O mundo com o qual o agente interage |
| **Estado** | Situação atual do ambiente |
| **Ação** | O que o agente pode fazer |
| **Recompensa** | Feedback numérico (positivo ou negativo) |
| **Política** | Estratégia que o agente aprende (estado → ação) |

### Exemplos
- AWS DeepRacer (carro autônomo em pista virtual)
- Jogos (AlphaGo, Atari)
- Robótica (controle de movimentos)
- Otimização de rotas e recursos
- Sistemas de recomendação adaptativos

### Quando identificar na prova
Palavras-chave: "tentativa e erro", "recompensa", "penalidade", "agente", "interagir com ambiente", "decisões sequenciais", "maximizar recompensa", "DeepRacer".

---

## Aprendizado Semi-Supervisionado

Combinação: **poucos dados rotulados** + **muitos dados não-rotulados**.

- Útil quando rotular dados é caro ou demorado (ex: imagens médicas que precisam de especialistas)
- O modelo usa os poucos rótulos para guiar o aprendizado nos dados não-rotulados
- Mais eficiente que supervisionado puro quando rótulos são escassos

### Quando identificar na prova
Palavras-chave: "poucos dados rotulados", "rotulagem cara", "grande volume de dados sem rótulo + alguns com rótulo".

---

## Aprendizado Auto-Supervisionado (Self-Supervised Learning)

O modelo **gera seus próprios rótulos** a partir dos dados de entrada, sem anotação humana.

- Técnica: mascarar parte da entrada e treinar o modelo para prever a parte oculta
- Exemplo: masked language modeling — esconder uma palavra e prever qual é (base do BERT)
- É a base do pré-treinamento dos **LLMs modernos** (GPT, Claude, Llama)
- Permite treinar com enormes quantidades de dados não-rotulados

### Quando identificar na prova
Palavras-chave: "pré-treinamento de LLMs", "modelo gera seus próprios rótulos", "masked prediction", "foundation models pré-treinados".

---

## Resumo Comparativo

| Tipo | Dados | Objetivo | Exemplo |
|------|-------|----------|---------|
| Supervisionado | Rotulados | Prever categoria ou valor | Detectar fraude |
| Não-Supervisionado | Sem rótulos | Encontrar padrões | Segmentar clientes |
| Reforço | Interação com ambiente | Maximizar recompensa | DeepRacer |
| Semi-Supervisionado | Poucos rótulos + muitos sem | Aprender com pouca supervisão | Imagens médicas |
| Auto-Supervisionado | Sem rótulos (cria os próprios) | Pré-treinar modelos | Treinamento de LLMs |

---

## Serviços AWS Relacionados

| Serviço | Relação com tipos de ML |
|---------|------------------------|
| **Amazon SageMaker** | Suporta todos os tipos de ML (treino, deploy, monitoramento) |
| **Amazon Personalize** | Usa reforço para recomendações |
| **AWS DeepRacer** | Aprendizado por reforço |
| **Amazon Comprehend** | Supervisionado (NLP pré-treinado) |
| **Amazon Rekognition** | Supervisionado (visão computacional) |
| **Amazon Forecast** | Supervisionado (séries temporais) |
| **Amazon Fraud Detector** | Supervisionado (classificação) |

---

*Próximo bloco: Ciclo de Vida de ML (ML Pipeline)*
