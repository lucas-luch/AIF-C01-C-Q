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

Qual é a diferença entre parâmetros e hiperparâmetros de um modelo?

A) Parâmetros são definidos pelo humano; hiperparâmetros são aprendidos pelo modelo  
B) Parâmetros são aprendidos durante o treino; hiperparâmetros são definidos antes do treino  
C) Parâmetros se referem apenas a redes neurais; hiperparâmetros se referem a qualquer modelo  
D) Não há diferença — são sinônimos  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Parâmetros são aprendidos durante o treino; hiperparâmetros são definidos antes do treino**

✅ **Por que B está correta:** Parâmetros (pesos, coeficientes) são ajustados automaticamente pelo algoritmo durante o treino. Hiperparâmetros (learning rate, epochs, batch size) são configurações definidas pelo humano antes de iniciar o treinamento.

❌ **Por que as outras estão erradas:**
- **A)** É o inverso — parâmetros são aprendidos, hiperparâmetros são definidos pelo humano.
- **C)** Ambos os conceitos se aplicam a qualquer modelo, não apenas redes neurais.
- **D)** São conceitos distintos com papéis diferentes.

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

Um modelo de ML é descrito como tendo "alto bias e baixa variância". Isso significa que:

A) O modelo é muito complexo e sensível a mudanças nos dados  
B) O modelo faz suposições simplificadoras e consistentemente erra de forma similar  
C) O modelo tem excelente performance em treino e teste  
D) O modelo foi treinado com dados enviesados  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) O modelo faz suposições simplificadoras e consistentemente erra de forma similar**

✅ **Por que B está correta:** Alto bias = modelo simples demais que faz suposições erradas sobre os dados. Baixa variância = estável, não muda muito com dados diferentes. Resultado: consistentemente erra na mesma direção (underfitting).

❌ **Por que as outras estão erradas:**
- **A)** Isso descreve baixo bias + alta variância (overfitting).
- **C)** Alto bias implica underfitting — performance ruim em ambos.
- **D)** "Bias" aqui é um conceito estatístico (viés do modelo), não viés nos dados de treino.

</details>

