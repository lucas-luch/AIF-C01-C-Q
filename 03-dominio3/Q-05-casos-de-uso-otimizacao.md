# Questões — Casos de Uso e Otimização

---

### Questão 1

Uma empresa quer minimizar custos de inferência para uma tarefa simples de classificação de sentimento (positivo/negativo). Qual estratégia é mais eficaz?

A) Usar o maior modelo disponível para máxima acurácia  
B) Usar um modelo menor que atenda os requisitos de qualidade  
C) Usar Provisioned Throughput com o modelo mais caro  
D) Aumentar max_tokens para respostas mais detalhadas  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Usar um modelo menor que atenda os requisitos de qualidade**

✅ **Por que B está correta:** Para tarefas simples como classificação binária de sentimento, modelos menores são suficientes e custam significativamente menos por token. A regra é: usar o menor modelo que atenda os requisitos.

❌ **Por que as outras estão erradas:**
- **A)** Modelo maior = mais caro por token. Overkill para tarefa simples.
- **C)** Provisioned Throughput com modelo caro seria o oposto de minimizar custo.
- **D)** Mais tokens = mais custo. Para sentimento, a resposta é curta ("positivo" ou "negativo").

</details>

---

### Questão 2

Qual métrica é mais adequada para avaliar a qualidade de um modelo que gera traduções de texto?

A) ROUGE  
B) BLEU  
C) F1 Score  
D) RMSE  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) BLEU**

✅ **Por que B está correta:** BLEU (Bilingual Evaluation Understudy) foi projetada especificamente para avaliar qualidade de tradução automática, medindo a precisão de n-grams comparados a uma tradução de referência humana.

❌ **Por que as outras estão erradas:**
- **A)** ROUGE é para resumos (recall-oriented), não tradução.
- **C)** F1 Score é para classificação, não geração de texto.
- **D)** RMSE é para regressão numérica.

</details>

---

### Questão 3

Uma empresa precisa processar 500.000 documentos para extrair resumos. Não há necessidade de resposta em tempo real. Qual abordagem otimiza custo?

A) Real-time endpoint no Bedrock  
B) Batch inference  
C) Provisioned Throughput  
D) Multiple concurrent API calls  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Batch inference**

✅ **Por que B está correta:** Batch inference processa grandes volumes de dados de uma vez com desconto sobre o preço on-demand. Sem necessidade de real-time, batch é a opção mais custo-efetiva.

❌ **Por que as outras estão erradas:**
- **A)** Real-time = mais caro e desnecessário quando não precisa de resposta imediata.
- **C)** Provisioned Throughput é para workloads constantes em tempo real, não lotes únicos.
- **D)** Chamadas concorrentes on-demand seriam mais caras que batch.

</details>

---

### Questão 4

Uma empresa está avaliando dois modelos no Bedrock para seu chatbot. Quer medir tanto métricas automáticas quanto a percepção de qualidade dos usuários internos. Qual abordagem de avaliação é mais completa?

A) Apenas ROUGE e BLEU  
B) Apenas avaliação humana  
C) Bedrock Model Evaluation com métricas automáticas + avaliação humana  
D) Apenas monitorar latência em produção  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: C) Bedrock Model Evaluation com métricas automáticas + avaliação humana**

✅ **Por que C está correta:** Model Evaluation do Bedrock suporta ambos: métricas automáticas (ROUGE, BLEU, BERTScore) para avaliação objetiva + avaliação humana para qualidade subjetiva. A combinação é a mais completa.

❌ **Por que as outras estão erradas:**
- **A)** Métricas automáticas sozinhas não capturam qualidade subjetiva (tom, utilidade, naturalidade).
- **B)** Avaliação humana sozinha é cara e não escala — combinar com automática é melhor.
- **D)** Latência mede performance, não qualidade das respostas.

</details>

---

### Questão 5

Uma empresa quer usar IA generativa para gerar código a partir de descrições em linguagem natural, explicar código existente e sugerir correções. Qual serviço AWS é mais adequado?

A) Amazon Bedrock com Claude  
B) Amazon Q Developer  
C) Amazon SageMaker  
D) AWS Lambda  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Amazon Q Developer**

✅ **Por que B está correta:** Amazon Q Developer é o assistente de código GenAI da AWS projetado especificamente para: gerar código, explicar código, sugerir correções, fazer debugging e transformar aplicações. Integrado diretamente em IDEs.

❌ **Por que as outras estão erradas:**
- **A)** Bedrock com Claude pode gerar código, mas Q Developer é o serviço dedicado com integração IDE.
- **C)** SageMaker é para construir modelos ML, não assistência de código.
- **D)** Lambda executa código, não gera ou explica.

</details>



---

### Questão 6

Uma empresa processa 1 milhão de emails de suporte por mês e quer classificar cada um em 5 categorias. A latência não é crítica (pode levar horas). O custo é a principal preocupação. Qual estratégia no Bedrock minimiza o custo TOTAL?

A) Real-time inference com o modelo mais barato disponível  
B) Batch inference para processar em lote com desconto sobre preço on-demand  
C) Provisioned Throughput com capacidade reservada 24/7  
D) Múltiplas chamadas on-demand paralelas para processar rapidamente  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Batch inference para processar em lote com desconto**

✅ **Por que B está correta:** Sem requisito de latência + volume alto + custo como prioridade = batch inference. Bedrock batch oferece desconto significativo sobre on-demand e processa grandes volumes assincronamente.

❌ **Por que as outras estão erradas:**
- **A)** Real-time on-demand custa mais por token que batch — desnecessário sem requisito de latência.
- **C)** Provisioned Throughput é para latência consistente e alta demanda contínua — overkill e caro para processamento que pode levar horas.
- **D)** Chamadas paralelas on-demand = custo on-demand total sem desconto de batch.

</details>

---

### Questão 7

Uma empresa está decidindo entre usar Amazon Comprehend (serviço pré-treinado de NLP) ou Amazon Bedrock com um LLM para classificar sentimento de reviews. Os reviews são simples (1-2 frases) e a classificação é padrão (positivo/negativo/neutro). Qual opção é MAIS custo-efetiva para esse caso?

A) Bedrock com Claude — mais inteligente e preciso para qualquer tarefa de NLP  
B) Amazon Comprehend — serviço otimizado para sentiment analysis a custo menor que LLMs  
C) Treinar modelo customizado no SageMaker — máximo controle  
D) Bedrock com modelo menor para reduzir custo por token  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Amazon Comprehend — serviço otimizado para sentiment analysis a custo menor**

✅ **Por que B está correta:** Para análise de sentimento padrão em textos curtos, Comprehend é mais barato que LLMs (não precisa de geração de texto — apenas classifica). É um serviço purpose-built, otimizado para essa tarefa específica.

❌ **Por que as outras estão erradas:**
- **A)** Claude é muito capaz, mas usar um LLM para classificação simples é like "matar formiga com canhão" — caro e desnecessário.
- **C)** SageMaker customizado requer expertise ML, dados de treino, manutenção — overkill para sentimento padrão.
- **D)** Mesmo modelo menor no Bedrock será mais caro que Comprehend para classificação simples — LLMs são para geração, não tarefas simples de NLP.

</details>

---

### Questão 8

Uma empresa de seguros usa IA generativa para redigir propostas de seguro personalizadas. Cada proposta precisa incluir dados do cliente (nome, endereço, valor do bem) que estão no CRM. O modelo NÃO deve alucinar dados do cliente. Qual arquitetura garante dados corretos nas propostas?

A) Fine-tuning do modelo com exemplos de propostas anteriores  
B) RAG conectado ao CRM para buscar dados reais do cliente e injetá-los no contexto  
C) Prompt engineering com instruções detalhadas sobre formato da proposta  
D) Temperature = 0 para eliminar aleatoriedade nos dados  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) RAG conectado ao CRM para buscar dados reais do cliente**

✅ **Por que B está correta:** Dados específicos do cliente (nome, endereço, valor) DEVEM vir de fonte real (CRM), não da memória do modelo. RAG busca os dados corretos e injeta no contexto — o modelo gera a proposta usando dados verificáveis.

❌ **Por que as outras estão erradas:**
- **A)** Fine-tuning ensina estilo/formato, mas NÃO tem acesso a dados atuais de clientes específicos.
- **C)** Prompt engineering define formato, mas sem dados reais do CRM, o modelo inventaria nomes/endereços.
- **D)** Temperature 0 torna a geração determinística, mas o modelo ainda pode gerar dados incorretos se não tiver a informação correta no contexto.

</details>

---

### Questão 9

Uma empresa está avaliando o custo-benefício de diferentes abordagens para seu chatbot. A tabela mostra custo e qualidade medidos:

| Abordagem | Custo/mês | Qualidade (escala 1-10) |
|-----------|-----------|------------------------|
| Modelo grande (Claude Sonnet) | $15.000 | 9.2 |
| Modelo médio (Haiku) | $3.000 | 7.8 |
| Modelo pequeno (Titan Lite) | $800 | 6.1 |

A equipe quer qualidade ≥ 7.5 com MENOR custo possível. Qual é a escolha MAIS racional?

A) Claude Sonnet — qualidade máxima justifica o investimento  
B) Haiku — atende o requisito de qualidade (7.8 ≥ 7.5) com custo 5x menor que Sonnet  
C) Titan Lite — menor custo é sempre a melhor escolha  
D) Combinar os três modelos em todas as interações  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Haiku — atende o requisito com custo 5x menor**

✅ **Por que B está correta:** O requisito é qualidade ≥ 7.5. Haiku atinge 7.8 (acima do threshold) por $3.000/mês. Sonnet é 5x mais caro para ganho marginal (9.2 vs 7.8) que o requisito não exige. A regra é: menor modelo que atende os requisitos.

❌ **Por que as outras estão erradas:**
- **A)** Qualidade acima do requisito a 5x do custo é desperdício — o requisito é ≥ 7.5, não "máxima".
- **C)** Titan Lite (6.1) NÃO atende o requisito de ≥ 7.5 — economia que viola requisitos não é "melhor escolha".
- **D)** Usar três modelos em todas as interações é ineficiente e mais caro que qualquer opção individual.

</details>

---

### Questão 10

Uma empresa quer implementar IA generativa para três casos de uso diferentes. Qual combinação CORRETA de serviço AWS para cada caso?

| Caso de uso | Serviço |
|-------------|---------|
| 1. Gerar relatórios personalizados | ? |
| 2. Detectar sentimento de reviews | ? |
| 3. Transcrever reuniões gravadas | ? |

A) 1: Bedrock, 2: Bedrock, 3: Bedrock — um serviço para tudo  
B) 1: Bedrock (geração de texto), 2: Comprehend (NLP pré-treinado), 3: Transcribe (speech-to-text)  
C) 1: SageMaker, 2: SageMaker, 3: SageMaker — máximo controle  
D) 1: Q Business, 2: Rekognition, 3: Polly  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Bedrock para geração, Comprehend para sentimento, Transcribe para transcrição**

✅ **Por que B está correta:** Cada serviço é otimizado para sua tarefa: Bedrock (IA generativa — gera texto), Comprehend (NLP — classifica sentimento sem LLM), Transcribe (converte áudio→texto). Usar o serviço purpose-built é mais eficiente e geralmente mais barato.

❌ **Por que as outras estão erradas:**
- **A)** Bedrock PODE fazer tudo, mas usar LLM para sentimento simples ou transcrição de áudio é ineficiente e caro.
- **C)** SageMaker requer expertise ML para cada caso — desnecessário quando serviços gerenciados existem.
- **D)** Q Business é para perguntas sobre documentos internos; Rekognition é visão computacional; Polly é text-to-speech. Nenhum se encaixa.

</details>
