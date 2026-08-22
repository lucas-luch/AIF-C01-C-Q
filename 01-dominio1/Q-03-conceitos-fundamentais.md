# Questões — Conceitos Fundamentais de ML

---

### Questão 1

Um modelo de classificação atinge 99% de acurácia nos dados de treino, mas apenas 62% nos dados de teste. Qual problema isso indica?

A) Underfitting  
B) Overfitting  
C) Data drift  
D) Bias nos dados de treino  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Overfitting**

✅ **Por que B está correta:** Alta performance no treino + baixa no teste é o padrão clássico de overfitting. O modelo memorizou os dados de treino em vez de aprender padrões generalizáveis.

❌ **Por que as outras estão erradas:**
- **A)** Underfitting causa performance ruim tanto no treino quanto no teste.
- **C)** Data drift ocorre após deploy em produção, não durante avaliação treino/teste.
- **D)** Bias nos dados poderia causar previsões tendenciosas, mas não explica a discrepância treino vs teste.

</details>

---

### Questão 2

Um modelo de regressão apresenta acurácia de 45% tanto nos dados de treino quanto nos dados de teste. Qual é a solução mais provável?

A) Adicionar regularização  
B) Reduzir o número de features  
C) Usar um modelo mais complexo ou adicionar features relevantes  
D) Aumentar o dropout  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: C) Usar um modelo mais complexo ou adicionar features relevantes**

✅ **Por que C está correta:** Performance ruim em ambos (treino e teste) indica underfitting — o modelo é simples demais. A solução é aumentar a capacidade do modelo ou fornecer features mais informativas.

❌ **Por que as outras estão erradas:**
- **A)** Regularização combate overfitting (reduz complexidade). No underfitting, o modelo já é simples demais.
- **B)** Reduzir features tornaria o modelo ainda mais simples — pioraria o underfitting.
- **D)** Dropout também combate overfitting reduzindo capacidade. Aqui precisamos de MAIS capacidade.

</details>

---

### Questão 3

Uma equipe está treinando um modelo de previsão de demanda no Amazon SageMaker. O cientista de dados configurou learning rate = 0.001 e epochs = 50 antes de iniciar o treinamento. Durante o treino, o algoritmo ajustou automaticamente milhões de pesos internos. Qual afirmação descreve corretamente a diferença entre esses elementos?

A) Learning rate e epochs são parâmetros do modelo; os pesos ajustados são hiperparâmetros  
B) Learning rate e epochs são hiperparâmetros definidos antes do treino; os pesos são parâmetros aprendidos durante o treino  
C) Todos são parâmetros — a diferença é apenas quem os configura (humano vs máquina)  
D) Learning rate é um hiperparâmetro, mas epochs é um parâmetro porque afeta diretamente o modelo  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Learning rate e epochs são hiperparâmetros definidos antes do treino; os pesos são parâmetros aprendidos durante o treino**

✅ **Por que B está correta:** Hiperparâmetros (learning rate, epochs, batch size) são configurações definidas pelo humano ANTES do treinamento. Parâmetros (pesos, coeficientes) são ajustados automaticamente pelo algoritmo DURANTE o treinamento. São conceitos distintos com funções diferentes.

❌ **Por que as outras estão erradas:**
- **A)** Inverte a definição — learning rate e epochs são hiperparâmetros (definidos antes), não parâmetros.
- **C)** A diferença não é apenas "quem configura" — é QUANDO e COMO são determinados (antes do treino vs durante).
- **D)** Epochs é um hiperparâmetro assim como learning rate — define quantas vezes o modelo vê os dados, não é um peso aprendido.

</details>

---

### Questão 4

Uma equipe quer reduzir o overfitting de um modelo de rede neural. Quais técnicas são apropriadas? **(Selecione DUAS)**

A) Adicionar mais camadas à rede  
B) Aplicar regularização (L2)  
C) Treinar por mais epochs  
D) Usar early stopping  
E) Remover dados do conjunto de validação  

<details>
<summary>🔍 Ver resposta</summary>

**Respostas: B e D**

✅ **Por que B está correta:** Regularização L2 penaliza pesos grandes, forçando o modelo a ser mais simples e generalizável — combate diretamente o overfitting.

✅ **Por que D está correta:** Early stopping interrompe o treino quando a performance no conjunto de validação começa a piorar, prevenindo que o modelo memorize os dados.

❌ **Por que as outras estão erradas:**
- **A)** Mais camadas = mais complexidade = mais overfitting.
- **C)** Mais epochs = mais tempo memorizando = mais overfitting.
- **E)** Remover dados de validação impede de detectar overfitting e ajustar hiperparâmetros.

</details>

---

### Questão 5

Uma equipe de ML está avaliando dois modelos de previsão de churn. O Modelo A usa regressão linear e consistentemente prevê taxas de churn 8% abaixo do valor real em todos os datasets testados. O Modelo B usa uma rede neural profunda e prevê valores muito diferentes dependendo de qual amostra de dados é usada (às vezes 15% acima, às vezes 20% abaixo). Qual é a caracterização correta desses modelos?

A) Modelo A tem alta variância; Modelo B tem alto bias  
B) Modelo A tem alto bias e baixa variância; Modelo B tem baixo bias e alta variância  
C) Ambos os modelos estão com overfitting  
D) Modelo A tem underfitting; Modelo B tem os dados enviesados  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Modelo A tem alto bias e baixa variância; Modelo B tem baixo bias e alta variância**

✅ **Por que B está correta:** Modelo A erra consistentemente na mesma direção (-8% sempre) = alto bias (suposição simplificadora) + baixa variância (estável entre datasets). Modelo B varia muito entre datasets = alta variância (sensível aos dados) — indicando overfitting potencial.

❌ **Por que as outras estão erradas:**
- **A)** Inverte os diagnósticos — consistência de erro = baixa variância (Modelo A), não alta.
- **C)** Modelo A não tem overfitting — tem underfitting (erro consistente, modelo simples demais).
- **D)** A primeira parte está parcialmente certa (Modelo A = underfitting), mas o problema do Modelo B é alta variância, não dados enviesados.

</details>



---

### Questão 6

Uma empresa treinou um modelo de deep learning com 500 milhões de parâmetros para classificar 3 categorias de produtos. O modelo atinge 99.8% no treino e 72% no teste. A equipe já tentou adicionar mais dados sem melhora significativa. Qual combinação de técnicas é MAIS provável de resolver o problema? **(Selecione DUAS)**

A) Aumentar o número de camadas da rede neural  
B) Aplicar dropout nas camadas intermediárias  
C) Remover o conjunto de validação  
D) Implementar early stopping baseado na performance de validação  
E) Treinar por mais epochs para convergir melhor  

<details>
<summary>🔍 Ver resposta</summary>

**Respostas: B e D**

✅ **Por que B está correta:** Dropout "desliga" neurônios aleatoriamente durante o treino, forçando a rede a não depender de padrões específicos — regularização que combate overfitting.

✅ **Por que D está correta:** Early stopping interrompe o treino quando a validação para de melhorar — previne que o modelo continue memorizando dados de treino.

❌ **Por que as outras estão erradas:**
- **A)** Mais camadas = mais parâmetros = mais capacidade de memorizar = PIORA o overfitting.
- **C)** Sem validação, não há como detectar quando parar ou ajustar hiperparâmetros.
- **E)** Mais epochs = mais tempo vendo os mesmos dados = mais memorização = mais overfitting.

</details>

---

### Questão 7

Uma equipe de ML está debatendo se deve usar um modelo de árvore de decisão simples ou uma rede neural profunda para prever aprovação de empréstimos. O regulador exige que cada decisão de negação seja explicável ao cliente. Qual consideração de trade-off é MAIS relevante para essa decisão?

A) Redes neurais são sempre mais precisas, então devem ser usadas apesar da complexidade  
B) O trade-off entre interpretabilidade (árvore) e capacidade preditiva (rede neural) é o fator decisivo dado o requisito regulatório  
C) Árvores de decisão não conseguem lidar com dados tabulares complexos  
D) Redes neurais são mais baratas de treinar que árvores de decisão  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) O trade-off entre interpretabilidade e capacidade preditiva é o fator decisivo dado o requisito regulatório**

✅ **Por que B está correta:** O requisito regulatório de explicabilidade ("explicar cada negação") favorece modelos interpretáveis (árvore de decisão mostra o caminho lógico). Redes neurais podem ser mais precisas mas são "caixas pretas". O trade-off interpretabilidade vs performance é a consideração central.

❌ **Por que as outras estão erradas:**
- **A)** "Sempre mais precisas" é falso — para dados tabulares, gradient boosting (baseado em árvores) frequentemente supera deep learning.
- **C)** Falso — árvores (especialmente ensemble como XGBoost) lidam muito bem com dados tabulares.
- **D)** Falso — árvores de decisão são tipicamente muito mais baratas de treinar que redes neurais.

</details>

---

### Questão 8

Um modelo de classificação foi treinado com dataset onde 70% é classe A e 30% é classe B. Em produção, a distribuição mudou para 50%/50%. A performance em produção está pior que nos testes. Qual conceito MELHOR explica essa degradação?

A) Overfitting — o modelo memorizou a proporção 70/30 do treino  
B) Data drift — a distribuição dos dados de entrada mudou em relação ao treino  
C) Concept drift — o significado das classes mudou  
D) Underfitting — o modelo não tinha capacidade suficiente  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Data drift — a distribuição dos dados de entrada mudou em relação ao treino**

✅ **Por que B está correta:** A proporção das classes mudou de 70/30 para 50/50 — a distribuição estatística dos dados em produção divergiu dos dados de treino. Isso é data drift (especificamente, prior probability shift).

❌ **Por que as outras estão erradas:**
- **A)** Overfitting causaria gap treino/teste antes do deploy — o cenário diz que testes foram bons.
- **C)** Concept drift é quando a RELAÇÃO features→target muda (o que define A e B muda). Aqui apenas a proporção mudou.
- **D)** Underfitting causaria performance ruim desde o início, não degradação após deploy.

</details>

---

### Questão 9

Uma empresa está treinando um modelo de regressão para prever preço de imóveis. O cientista de dados aplicou feature engineering: criou a feature "preço_por_m²" dividindo "preço" por "área". Qual problema POTENCIAL essa feature pode causar?

A) Overfitting — features derivadas sempre causam overfitting  
B) Data leakage — a feature contém informação do target (preço) que não estaria disponível em produção  
C) Underfitting — features adicionais sempre simplificam o modelo  
D) Multicolinearidade — mas isso melhora a performance  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Data leakage — a feature contém informação do target (preço) que não estaria disponível em produção**

✅ **Por que B está correta:** Se o target é "preço" e a feature é "preço/área", você está vazando o target para o input. Em produção, não teremos o preço para calcular essa feature. O modelo terá performance artificialmente alta no treino e falhará em produção.

❌ **Por que as outras estão erradas:**
- **A)** Features derivadas não causam overfitting automaticamente — o problema específico aqui é leakage.
- **C)** Features adicionais AUMENTAM complexidade, não simplificam.
- **D)** Multicolinearidade não é o problema principal — e ela geralmente NÃO melhora performance.

</details>

---

### Questão 10

Uma equipe está selecionando hiperparâmetros para um modelo de gradient boosting. Testaram 50 combinações diferentes de learning rate, max depth e n_estimators no conjunto de validação, escolhendo a melhor. Qual risco essa abordagem apresenta?

A) Underfitting — muitas combinações testadas simplificam demais o modelo  
B) Overfitting ao conjunto de validação — a performance reportada pode não refletir dados novos  
C) Data leakage — os hiperparâmetros vazam informação do teste  
D) Concept drift — testar muitas combinações causa mudança no conceito  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Overfitting ao conjunto de validação — a performance reportada pode não refletir dados novos**

✅ **Por que B está correta:** Ao testar 50 combinações e escolher a melhor no MESMO conjunto de validação, você pode estar selecionando hiperparâmetros que se adaptam especificamente a esse conjunto. O teste final em dados nunca vistos (conjunto de teste separado) é necessário para estimar performance real.

❌ **Por que as outras estão erradas:**
- **A)** Testar combinações não simplifica o modelo — seleção de hiperparâmetros busca a melhor configuração.
- **C)** Hiperparâmetros são definidos antes do treino — não "vazam" informação do teste. O risco é diferente.
- **D)** Concept drift é mudança na relação dados→target ao longo do tempo — não é causado por seleção de hiperparâmetros.

</details>
