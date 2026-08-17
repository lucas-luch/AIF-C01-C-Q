# Questões — Métricas de Avaliação

---

### Questão 1

Um hospital está desenvolvendo um modelo para detectar câncer em exames de imagem. O custo de não detectar um caso real (falso negativo) é muito maior que o custo de um alarme falso (falso positivo). Qual métrica deve ser priorizada?

A) Precisão  
B) Acurácia  
C) Recall  
D) RMSE  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: C) Recall**

✅ **Por que C está correta:** Recall mede quantos dos positivos reais foram detectados (TP / (TP + FN)). Quando falsos negativos são perigosos (perder um câncer real), maximizar recall é prioridade — queremos pegar TODOS os casos.

❌ **Por que as outras estão erradas:**
- **A)** Precisão prioriza evitar falsos positivos. Aqui, um falso positivo (alarme extra) é aceitável.
- **B)** Acurácia não diferencia entre tipos de erro e pode ser enganosa em dados desbalanceados (câncer é raro).
- **D)** RMSE é para regressão (valores numéricos), não classificação.

</details>

---

### Questão 2

Um sistema de email classifica mensagens como spam ou legítimas. Bloquear um email legítimo (falso positivo) é muito prejudicial ao negócio. Qual métrica deve ser otimizada?

A) Recall  
B) Precisão  
C) F1 Score  
D) AUC-ROC  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Precisão**

✅ **Por que B está correta:** Precisão = TP / (TP + FP). Maximizar precisão minimiza falsos positivos — quando o modelo diz "spam", queremos ter alta confiança de que realmente é spam, para não bloquear emails legítimos.

❌ **Por que as outras estão erradas:**
- **A)** Recall priorizaria detectar todo spam, aceitando mais falsos positivos — o oposto do desejado.
- **C)** F1 equilibra precisão e recall igualmente. Aqui a prioridade é clara: minimizar FP.
- **D)** AUC-ROC é boa para comparar modelos, mas não endereça especificamente o custo de FP.

</details>

---

### Questão 3

Um modelo tem 97% de acurácia em um dataset onde 97% dos exemplos pertencem à classe "legítima" e apenas 3% são "fraude". Este modelo é eficaz?

A) Sim, 97% é uma acurácia excelente  
B) Não, o modelo provavelmente prevê tudo como "legítima" sem detectar fraudes  
C) Sim, desde que o RMSE também seja baixo  
D) Depende apenas do número de epochs usado no treino  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Não, o modelo provavelmente prevê tudo como "legítima" sem detectar fraudes**

✅ **Por que B está correta:** Em dados muito desbalanceados, um modelo que SEMPRE prevê a classe majoritária (legítima) atinge acurácia igual à proporção da classe dominante (97%). Mas recall para fraude seria 0% — inútil para o objetivo real.

❌ **Por que as outras estão erradas:**
- **A)** Acurácia é enganosa em dados desbalanceados. 97% parece bom mas pode significar zero detecção de fraude.
- **C)** RMSE é métrica de regressão, irrelevante aqui.
- **D)** O número de epochs não resolve o problema de métrica inadequada para dados desbalanceados.

</details>

---

### Questão 4

Qual métrica é usada para avaliar a qualidade de um modelo que gera resumos de texto?

A) BLEU  
B) ROUGE  
C) AUC-ROC  
D) RMSE  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) ROUGE**

✅ **Por que B está correta:** ROUGE (Recall-Oriented Understudy for Gisting Evaluation) mede a sobreposição entre o texto gerado e um texto de referência. Foi projetada especificamente para avaliar resumos.

❌ **Por que as outras estão erradas:**
- **A)** BLEU é usada para avaliar tradução automática, não resumos.
- **C)** AUC-ROC é para classificação binária, não geração de texto.
- **D)** RMSE é para regressão numérica.

</details>

---

### Questão 5

Uma empresa precisa prever o preço de imóveis e quer uma métrica que penalize mais fortemente erros de previsão grandes. Qual métrica é mais adequada?

A) MAE  
B) RMSE  
C) R²  
D) F1 Score  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) RMSE**

✅ **Por que B está correta:** RMSE (Root Mean Squared Error) eleva os erros ao quadrado antes de calcular a média, o que penaliza desproporcionalmente erros grandes. Se um erro de R$100K é muito pior que dois erros de R$50K, RMSE reflete isso.

❌ **Por que as outras estão erradas:**
- **A)** MAE trata todos os erros igualmente (valor absoluto), sem penalizar mais os grandes.
- **C)** R² indica poder explicativo do modelo, mas não penaliza erros grandes especificamente.
- **D)** F1 Score é para classificação, não regressão.

</details>

