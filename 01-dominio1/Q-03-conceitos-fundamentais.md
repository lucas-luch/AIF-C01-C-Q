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

