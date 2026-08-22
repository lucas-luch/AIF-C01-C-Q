# Questões — Ciclo de Vida de ML

---

### Questão 1

Uma equipe de ciência de dados percebeu que a acurácia do modelo de previsão de churn caiu significativamente nos últimos 2 meses, apesar de não ter havido mudanças no modelo. O que provavelmente está acontecendo?

A) Overfitting no treinamento original  
B) Data drift nos dados de produção  
C) O modelo foi implantado em um endpoint errado  
D) Feature engineering inadequado  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Data drift nos dados de produção**

✅ **Por que B está correta:** Quando a performance degrada ao longo do tempo sem mudanças no modelo, a causa mais provável é que os dados em produção mudaram (data drift). Os padrões que o modelo aprendeu já não representam a realidade atual.

❌ **Por que as outras estão erradas:**
- **A)** Overfitting causaria performance ruim desde o início em dados novos, não uma degradação gradual ao longo de meses.
- **C)** Endpoint errado causaria falha imediata, não degradação gradual.
- **D)** Feature engineering inadequado teria sido detectado na avaliação antes do deploy.

</details>

---

### Questão 2

Em qual etapa do ciclo de vida de ML a equipe divide os dados em conjuntos de treino, validação e teste?

A) Definição do problema de negócio  
B) Coleta e preparação de dados  
C) Treinamento do modelo  
D) Avaliação do modelo  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: C) Treinamento do modelo**

✅ **Por que C está correta:** A divisão dos dados em treino/validação/teste ocorre no início da fase de treinamento. O conjunto de treino alimenta o modelo, o de validação ajusta hiperparâmetros, e o de teste é reservado para avaliação final.

❌ **Por que as outras estão erradas:**
- **A)** Na definição do problema não se trabalha com dados ainda.
- **B)** Coleta e preparação envolve limpeza, transformação e análise exploratória — a divisão formal ocorre quando se está pronto para treinar.
- **D)** Na avaliação os dados de teste já estão separados — usa-se eles, não os divide neste momento.

</details>

---

### Questão 3

Uma empresa quer processar milhões de imagens de produtos para classificação. Qual tipo de deploy é mais adequado para processar esse volume de forma eficiente?

A) Real-time endpoint  
B) Batch transform  
C) Edge deployment  
D) A/B testing  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Batch transform**

✅ **Por que B está correta:** Batch transform é ideal para processar grandes volumes de dados de uma vez, sem necessidade de resposta em tempo real. Processa lotes de dados e gera previsões em massa.

❌ **Por que as outras estão erradas:**
- **A)** Real-time endpoint é para previsões individuais com baixa latência — ineficiente e caro para milhões de itens.
- **C)** Edge deployment é para rodar modelos em dispositivos locais (IoT, mobile) — não para processamento em lote na nuvem.
- **D)** A/B testing é uma estratégia de comparação de modelos, não um tipo de deploy para processamento em massa.

</details>

---

### Questão 4

Qual serviço AWS é usado para monitorar a qualidade e detectar drift de um modelo em produção?

A) Amazon SageMaker Autopilot  
B) Amazon SageMaker Model Monitor  
C) AWS Glue DataBrew  
D) Amazon Athena  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Amazon SageMaker Model Monitor**

✅ **Por que B está correta:** SageMaker Model Monitor detecta desvios na qualidade dos dados (data drift), na qualidade do modelo (model drift), e viés — exatamente o serviço para monitoramento pós-deploy.

❌ **Por que as outras estão erradas:**
- **A)** Autopilot automatiza a criação de modelos (AutoML), não o monitoramento em produção.
- **C)** Glue DataBrew é para preparação visual de dados, não monitoramento.
- **D)** Athena executa consultas SQL no S3, não monitora modelos.

</details>

---

### Questão 5

Qual é a diferença principal entre data drift e concept drift?

A) Data drift afeta apenas dados de treino; concept drift afeta dados de teste  
B) Data drift é quando a distribuição dos inputs muda; concept drift é quando a relação entre input e output muda  
C) Data drift é detectado antes do deploy; concept drift só ocorre durante o treinamento  
D) Data drift e concept drift são sinônimos  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Data drift é quando a distribuição dos inputs muda; concept drift é quando a relação entre input e output muda**

✅ **Por que B está correta:** Data drift = os dados de entrada mudam de perfil (ex: clientes com características diferentes). Concept drift = o que o modelo deveria prever muda (ex: o conceito de "fraude" evolui). São fenômenos distintos.

❌ **Por que as outras estão erradas:**
- **A)** Ambos ocorrem em dados de produção (após deploy), não estão limitados a treino/teste.
- **C)** Ambos são problemas de produção, detectados durante monitoramento — não antes do deploy nem durante treinamento.
- **D)** São conceitos diferentes com causas e soluções distintas.

</details>

---

### Questão 6 (Múltipla Resposta)

Quais são responsabilidades da etapa de "Coleta e Preparação de Dados" no ciclo de vida de ML? **(Selecione DUAS)**

A) Treinar o modelo com algoritmo escolhido  
B) Tratar dados faltantes e duplicados  
C) Definir hiperparâmetros do modelo  
D) Realizar análise exploratória dos dados (EDA)  
E) Implantar o modelo em um endpoint  

<details>
<summary>🔍 Ver resposta</summary>

**Respostas: B e D**

✅ **Por que B está correta:** Limpeza de dados (tratar faltantes, duplicados, inconsistências) é parte central da preparação.

✅ **Por que D está correta:** Análise Exploratória (EDA) é feita durante a preparação para entender distribuições, correlações e outliers antes de modelar.

❌ **Por que as outras estão erradas:**
- **A)** Treinar o modelo é etapa posterior (Treinamento).
- **C)** Hiperparâmetros são definidos na etapa de Treinamento.
- **E)** Implantação é a etapa de Deploy.

</details>



---

### Questão 7

Uma equipe implantou um modelo de scoring de crédito há 6 meses. A taxa de inadimplência real está 40% maior que o previsto pelo modelo, mas os dados de entrada (renda, idade, histórico) não mudaram significativamente de perfil. Qual tipo de drift MAIS provavelmente explica essa degradação?

A) Data drift — a distribuição das features de entrada mudou  
B) Concept drift — a relação entre as features e o target mudou  
C) Model drift — os pesos do modelo se corromperam em produção  
D) Feature drift — novas features surgiram que não existiam no treino  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Concept drift — a relação entre as features e o target mudou**

✅ **Por que B está correta:** Os inputs NÃO mudaram (confirmado no enunciado), mas o output está errado. Isso indica que a RELAÇÃO entre features e inadimplência mudou (ex: uma crise econômica alterou o comportamento de pagamento de pessoas com o mesmo perfil). Isso é concept drift.

❌ **Por que as outras estão erradas:**
- **A)** Data drift é quando os inputs mudam de perfil — o cenário explicita que NÃO mudaram.
- **C)** "Pesos corrompidos em produção" não é um fenômeno real de ML — modelos deployados são estáticos.
- **D)** Feature drift não é um termo padrão. A ausência de features novas não explica degradação.

</details>

---

### Questão 8

Uma empresa de e-commerce está no início do ciclo de vida de ML para um sistema de recomendação. A equipe coletou dados brutos de 3 fontes: banco transacional, logs de navegação e reviews de clientes. Os dados contêm formatos inconsistentes, valores faltantes e duplicatas. Qual etapa do ciclo de vida estão executando e qual serviço AWS é MAIS adequado para essa tarefa?

A) Treinamento do modelo — Amazon SageMaker Autopilot  
B) Coleta e preparação de dados — AWS Glue DataBrew  
C) Avaliação do modelo — Amazon SageMaker Model Monitor  
D) Deploy — Amazon SageMaker Endpoints  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Coleta e preparação de dados — AWS Glue DataBrew**

✅ **Por que B está correta:** Dados brutos com formatos inconsistentes, valores faltantes e duplicatas = etapa de preparação/limpeza. Glue DataBrew é a ferramenta visual de preparação de dados da AWS (no-code, 250+ transformações prontas).

❌ **Por que as outras estão erradas:**
- **A)** Autopilot treina modelos — os dados ainda não estão prontos para treino.
- **C)** Model Monitor monitora modelos em PRODUÇÃO — não existe modelo ainda.
- **D)** Endpoints são para inferência após deploy — estamos nas etapas iniciais.

</details>

---

### Questão 9

Uma empresa treinou um modelo de classificação de imagens que atingiu 95% de acurácia no conjunto de teste. Após o deploy em produção, a equipe quer ser notificada automaticamente se a qualidade das previsões degradar OU se os dados de entrada começarem a divergir dos dados de treino. Qual serviço AWS implementa AMBOS os monitoramentos?

A) Amazon CloudWatch com alarmes customizados  
B) Amazon SageMaker Model Monitor  
C) AWS CloudTrail para auditar chamadas de inferência  
D) Amazon SageMaker Clarify para detectar viés contínuo  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Amazon SageMaker Model Monitor**

✅ **Por que B está correta:** Model Monitor detecta AMBOS: data quality monitoring (inputs divergindo dos dados de treino = data drift) E model quality monitoring (previsões degradando = model drift). Gera alertas automáticos via CloudWatch quando thresholds são violados.

❌ **Por que as outras estão erradas:**
- **A)** CloudWatch monitora métricas de infraestrutura (latência, CPU). Não analisa distribuição estatística de features nem qualidade de previsões ML.
- **C)** CloudTrail audita QUEM fez chamadas de API — não monitora qualidade das previsões.
- **D)** Clarify detecta viés e explica previsões, mas não monitora drift de dados nem degradação contínua em produção da mesma forma que Model Monitor.

</details>

---

### Questão 10

Uma equipe precisa re-treinar um modelo de previsão de vendas mensalmente com novos dados. O pipeline deve ser: extrair dados do S3 → preparar features → treinar modelo → avaliar → registrar no Model Registry → deploy se aprovado. Qual serviço AWS orquestra esse pipeline end-to-end de forma AUTOMATIZADA?

A) AWS Step Functions para orquestrar Lambda functions  
B) Amazon SageMaker Pipelines  
C) AWS CodePipeline para CI/CD  
D) Amazon EventBridge para disparar jobs  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Amazon SageMaker Pipelines**

✅ **Por que B está correta:** SageMaker Pipelines é projetado especificamente para MLOps — orquestra pipelines de ML com etapas de processamento, treinamento, avaliação e registro de modelo. Integra nativamente com Model Registry e SageMaker.

❌ **Por que as outras estão erradas:**
- **A)** Step Functions é um orquestrador genérico — funciona, mas SageMaker Pipelines é a solução nativa de MLOps com integração direta ao ecossistema ML.
- **C)** CodePipeline é para CI/CD de aplicações de software, não pipelines de ML.
- **D)** EventBridge dispara eventos, mas não orquestra um pipeline multi-etapa completo com avaliação e aprovação.

</details>

---

### Questão 11

Uma startup está definindo a arquitetura de ML e precisa decidir como implantar o modelo. O modelo será usado por um aplicativo mobile que exige respostas em menos de 100ms, com tráfego variável (picos de 10.000 requisições/segundo em promoções). Qual tipo de deploy é MAIS adequado?

A) Batch transform processando requisições em lotes a cada hora  
B) Real-time endpoint com auto-scaling configurado para o tráfego variável  
C) Edge deployment no dispositivo mobile do usuário  
D) Endpoint assíncrono com fila de processamento  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Real-time endpoint com auto-scaling configurado para o tráfego variável**

✅ **Por que B está correta:** Latência < 100ms + tráfego variável com picos = real-time endpoint com auto-scaling. O endpoint escala horizontalmente durante picos e reduz em períodos calmos.

❌ **Por que as outras estão erradas:**
- **A)** Batch transform processa lotes periodicamente — não atende requisito de latência < 100ms em tempo real.
- **C)** Edge no mobile reduziria latência, mas modelos complexos podem não caber no dispositivo e não mencionam requisitos offline.
- **D)** Endpoint assíncrono processa via fila — adiciona latência (segundos a minutos), não atende < 100ms.

</details>

---

### Questão 12

Uma equipe de ML descobriu que seu modelo de previsão de churn tem desempenho excelente em clientes urbanos mas péssimo em clientes rurais. A hipótese é que os dados de treino têm 95% clientes urbanos e 5% rurais. Em qual etapa do ciclo de vida esse problema deveria ter sido identificado PRIMEIRO?

A) Deploy — ao monitorar previsões em produção por segmento  
B) Coleta e preparação — ao analisar a representatividade dos dados (EDA)  
C) Treinamento — ao verificar a loss function durante o treino  
D) Definição do problema — ao definir os requisitos de negócio  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Coleta e preparação — ao analisar a representatividade dos dados (EDA)**

✅ **Por que B está correta:** Análise Exploratória de Dados (EDA) durante a preparação deveria revelar o desbalanceamento geográfico (95/5). Esse é o momento correto para identificar problemas de representatividade ANTES de treinar.

❌ **Por que as outras estão erradas:**
- **A)** Descobrir em produção é válido (Model Monitor), mas é TARDE demais — o problema deveria ser pego antes.
- **C)** Loss function mede erro geral, não por segmento. O desbalanceamento passaria despercebido no treino sem análise específica.
- **D)** Definição do problema especifica O QUE resolver, não analisa dados — dados ainda não foram coletados nessa etapa.

</details>
