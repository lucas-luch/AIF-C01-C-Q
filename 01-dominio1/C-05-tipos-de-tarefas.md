# Tipos de Tarefas de ML

## Visão Geral

Cada problema de negócio se mapeia a um tipo de tarefa de ML. A prova AIF-C01 pede que você **identifique a tarefa correta** a partir de um cenário descrito.

---

## Classificação

Prever uma **categoria discreta** (classe) a partir dos dados de entrada.

### Classificação Binária
- Duas classes possíveis
- Exemplos: spam/não-spam, fraude/legítima, aprovado/reprovado
- Serviço AWS: Amazon Fraud Detector, Amazon Comprehend (sentimento positivo/negativo)

### Classificação Multiclasse
- Três ou mais classes possíveis
- Exemplos: tipo de produto (eletrônico, roupa, alimento), idioma do texto, espécie de planta
- Serviço AWS: Amazon Comprehend (detecção de idioma), Amazon Rekognition (objetos)

### Classificação Multi-label
- Cada item pode ter **múltiplas** classes simultaneamente
- Exemplos: um artigo pode ser sobre "tecnologia" E "negócios", uma imagem pode ter "pessoa" E "carro"

---

## Regressão

Prever um **valor numérico contínuo**.

### Exemplos
- Prever preço de imóvel
- Prever demanda de vendas no próximo mês
- Estimar tempo de entrega
- Prever temperatura
- Estimar custo de um projeto

### Serviços AWS
- Amazon Forecast (séries temporais)
- Amazon SageMaker (modelos customizados)

### Como distinguir de classificação na prova
- Se a resposta é um **número** (quanto, quando, qual valor) → Regressão
- Se a resposta é uma **categoria** (qual tipo, sim/não) → Classificação

---

## Clustering (Agrupamento)

Encontrar **grupos naturais** nos dados sem categorias predefinidas.

### Exemplos
- Segmentar clientes por comportamento de compra
- Agrupar documentos por tema
- Identificar comunidades em redes sociais
- Agrupar genes com expressão similar

### Características
- Não-supervisionado (sem rótulos)
- O número de clusters pode ser definido (K-Means) ou descoberto automaticamente (DBSCAN)
- Não "prevê" — agrupa

### Serviços AWS
- Amazon SageMaker (K-Means built-in)
- Amazon Personalize (segmentação de usuários)

---

## Detecção de Anomalias

Identificar **pontos fora do padrão** (outliers) nos dados.

### Exemplos
- Detectar transações fraudulentas
- Identificar falhas em equipamentos industriais (manutenção preditiva)
- Detectar intrusões em redes de computadores
- Identificar comportamento anormal de usuário

### Abordagens
- **Supervisionada:** quando há exemplos rotulados de anomalias (fraude/não-fraude)
- **Não-supervisionada:** quando anomalias são raras e sem rótulos — modelo aprende o "normal" e detecta desvios

### Serviços AWS
- Amazon Fraud Detector
- Amazon Lookout for Metrics (anomalias em métricas)
- Amazon DevOps Guru (anomalias em operações)
- Amazon SageMaker (Random Cut Forest)

---

## Recomendação

Sugerir **itens relevantes** para um usuário com base em preferências e comportamento.

### Exemplos
- Recomendar produtos em e-commerce
- Sugerir filmes/músicas
- Recomendar artigos/notícias
- "Clientes que compraram X também compraram Y"

### Abordagens
- **Filtragem Colaborativa** — baseada no comportamento de usuários similares
- **Filtragem por Conteúdo** — baseada nas características dos itens
- **Híbrida** — combina ambas

### Serviços AWS
- **Amazon Personalize** — serviço gerenciado de recomendações (usa reinforcement learning)

---

## Previsão de Séries Temporais (Forecasting)

Prever valores futuros com base em dados históricos ordenados no tempo.

### Exemplos
- Prever demanda de estoque
- Prever receita futura
- Prever consumo de energia
- Prever tráfego web

### Características
- Dados ordenados cronologicamente
- Sazonalidade e tendências
- Diferente de regressão simples: considera a dimensão temporal

### Serviço AWS
- **Amazon Forecast** — serviço gerenciado para séries temporais

---

## Processamento de Linguagem Natural (NLP)

Processar e entender **texto e linguagem humana**.

### Tarefas de NLP
| Tarefa | Descrição | Serviço AWS |
|--------|-----------|-------------|
| Análise de sentimento | Positivo/negativo/neutro | Amazon Comprehend |
| Extração de entidades | Nomes, datas, locais | Amazon Comprehend |
| Tradução | Converter entre idiomas | Amazon Translate |
| Transcrição | Áudio → texto | Amazon Transcribe |
| Síntese de fala | Texto → áudio | Amazon Polly |
| Chatbot | Conversa interativa | Amazon Lex |
| Busca semântica | Encontrar documentos relevantes | Amazon Kendra |

---

## Visão Computacional (Computer Vision)

Processar e entender **imagens e vídeos**.

### Tarefas
| Tarefa | Descrição | Serviço AWS |
|--------|-----------|-------------|
| Detecção de objetos | Encontrar e localizar objetos em imagens | Amazon Rekognition |
| Reconhecimento facial | Identificar/comparar rostos | Amazon Rekognition |
| OCR | Extrair texto de imagens/documentos | Amazon Textract |
| Moderação de conteúdo | Detectar conteúdo impróprio | Amazon Rekognition |
| Classificação de imagem | Categorizar imagens | Amazon Rekognition Custom Labels |

---

## Resumo para a Prova — Mapeamento Cenário → Tarefa

| Cenário descrito | Tarefa | Serviço AWS provável |
|-----------------|--------|---------------------|
| "Prever se é fraude ou legítima" | Classificação binária | Fraud Detector |
| "Prever o valor de vendas" | Regressão / Forecasting | Forecast, SageMaker |
| "Agrupar clientes por comportamento" | Clustering | SageMaker (K-Means) |
| "Detectar transações incomuns" | Detecção de anomalias | Fraud Detector |
| "Recomendar produtos" | Recomendação | Personalize |
| "Analisar sentimento de reviews" | NLP - Sentimento | Comprehend |
| "Extrair texto de documentos" | Visão computacional - OCR | Textract |
| "Identificar objetos em imagens" | Visão computacional | Rekognition |
| "Prever demanda futura" | Séries temporais | Forecast |

---

*Próximo bloco: Serviços AWS de ML*
