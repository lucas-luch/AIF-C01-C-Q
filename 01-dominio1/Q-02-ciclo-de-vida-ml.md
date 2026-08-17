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

