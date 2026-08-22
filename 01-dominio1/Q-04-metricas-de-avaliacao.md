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

Uma empresa de mídia está usando IA generativa para criar resumos automáticos de artigos de notícias. A equipe precisa avaliar se os resumos gerados capturam os pontos-chave dos artigos originais. Qual métrica é projetada especificamente para avaliar a qualidade de resumos de texto?

A) BLEU, que mede precisão de n-grams comparando com referências  
B) ROUGE, que mede cobertura do conteúdo de referência nos resumos gerados  
C) AUC-ROC, que mede a capacidade discriminativa do modelo  
D) Perplexidade, que mede quão bem o modelo prevê a próxima palavra  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) ROUGE, que mede cobertura do conteúdo de referência nos resumos gerados**

✅ **Por que B está correta:** ROUGE (Recall-Oriented Understudy for Gisting Evaluation) mede a sobreposição entre o texto gerado e uma referência, focando em recall — quantos dos conceitos/termos importantes do original aparecem no resumo. Foi projetada especificamente para avaliação de resumos.

❌ **Por que as outras estão erradas:**
- **A)** BLEU mede precisão (do gerado, quanto está na referência) e foi projetada para tradução automática, não resumos. ROUGE foca em recall (da referência, quanto está no gerado).
- **C)** AUC-ROC é para modelos de classificação binária — não se aplica a avaliação de texto gerado.
- **D)** Perplexidade mede a fluência/qualidade linguística do modelo, não se o resumo captura os pontos corretos.

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



---

### Questão 6

Uma empresa de e-commerce desenvolveu um sistema de recomendação de produtos. A equipe quer avaliar se os itens recomendados na posição #1 são realmente os mais relevantes para o usuário. Qual métrica é MAIS adequada para avaliar ranking de recomendações?

A) Acurácia — percentual de recomendações corretas  
B) RMSE — erro médio entre a posição prevista e real  
C) Precision@K — proporção de itens relevantes entre os K primeiros recomendados  
D) ROUGE — sobreposição com uma lista de referência  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: C) Precision@K — proporção de itens relevantes entre os K primeiros recomendados**

✅ **Por que C está correta:** Precision@K mede quantos dos K primeiros itens recomendados são realmente relevantes. Para recomendação onde a posição importa (item #1 deve ser o melhor), métricas de ranking como Precision@K são adequadas.

❌ **Por que as outras estão erradas:**
- **A)** Acurácia binária não captura qualidade de RANKING — trata todas as posições igualmente.
- **B)** RMSE é para regressão numérica, não avaliação de listas ordenadas.
- **D)** ROUGE é para avaliação de resumos de texto, não sistemas de recomendação.

</details>

---

### Questão 7

Um modelo de detecção de fraude em cartão de crédito opera em tempo real. O banco definiu que o custo de um falso negativo (fraude não detectada — cliente perde dinheiro) é 100x maior que o custo de um falso positivo (transação legítima bloqueada — inconveniente temporário). Qual estratégia de threshold e métrica é MAIS alinhada com esse requisito de negócio?

A) Maximizar precisão com threshold alto — bloquear apenas quando há altíssima certeza de fraude  
B) Maximizar recall com threshold baixo — bloquear na menor suspeita de fraude, aceitando mais FPs  
C) Usar F1 Score com threshold padrão de 0.5 — equilibrar precisão e recall igualmente  
D) Minimizar RMSE — reduzir o erro geral do modelo  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Maximizar recall com threshold baixo — bloquear na menor suspeita de fraude, aceitando mais FPs**

✅ **Por que B está correta:** Se FN custa 100x mais que FP, a prioridade é não perder NENHUMA fraude real (maximizar recall). Threshold baixo significa que qualquer suspeita mínima dispara bloqueio — mais falsos alarmes, mas menos fraudes escapam.

❌ **Por que as outras estão erradas:**
- **A)** Threshold alto maximiza precisão mas REDUZ recall — fraudes com confiança média passam despercebidas. Dado que FN é 100x pior que FP, isso é catastrófico.
- **C)** F1 equilibra FP e FN igualmente — mas aqui eles NÃO são iguais (FN é 100x pior). Equilíbrio não reflete o custo assimétrico.
- **D)** RMSE é para regressão. Fraude é classificação binária.

</details>

---

### Questão 8

Uma empresa de mídia usa IA generativa para traduzir artigos do inglês para 15 idiomas. A equipe precisa automatizar a avaliação de qualidade das traduções comparando com traduções de referência feitas por humanos. Qual métrica é ESPECIFICAMENTE projetada para avaliar tradução automática?

A) ROUGE — mede cobertura do conteúdo original no texto gerado  
B) BLEU — mede precisão de n-grams do texto gerado contra referências humanas  
C) BERTScore — mede similaridade semântica usando embeddings  
D) Perplexidade — mede quão fluente o modelo é na geração  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) BLEU — mede precisão de n-grams do texto gerado contra referências humanas**

✅ **Por que B está correta:** BLEU (Bilingual Evaluation Understudy) foi criada ESPECIFICAMENTE para avaliar tradução automática. Compara n-grams (sequências de palavras) da tradução com referências humanas, medindo precisão.

❌ **Por que as outras estão erradas:**
- **A)** ROUGE foi projetada para resumos (recall-oriented). Funciona para texto, mas BLEU é específica de tradução.
- **C)** BERTScore é válida para avaliação semântica geral, mas não é específica de tradução como BLEU.
- **D)** Perplexidade mede a fluência do modelo de linguagem, não a qualidade de tradução comparada a referências.

</details>

---

### Questão 9

Uma empresa implantou um modelo de classificação binária (aprovado/reprovado) para triagem de currículos. A equipe de RH reporta que "muitos candidatos bons estão sendo reprovados" (alto FN) mas "quando o modelo aprova, geralmente é um bom candidato" (alto precision). Qual métrica está BAIXA e precisa ser melhorada?

A) Precisão — o modelo erra quando diz "aprovado"  
B) Recall — o modelo está perdendo muitos candidatos realmente bons  
C) Acurácia — o modelo erra em geral  
D) AUC-ROC — o modelo não discrimina bem entre as classes  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Recall — o modelo está perdendo muitos candidatos realmente bons**

✅ **Por que B está correta:** "Muitos bons reprovados" = alto FN = recall baixo (TP/(TP+FN)). "Quando aprova, geralmente acerta" = precisão alta. Diagnóstico: precisão ok, recall precisa melhorar.

❌ **Por que as outras estão erradas:**
- **A)** O enunciado DIZ que "quando aprova, geralmente acerta" — precisão está ALTA, não baixa.
- **C)** Acurácia geral pode estar ok (se rejeita corretamente muitos candidatos fracos), mas esconde o problema de FN.
- **D)** AUC-ROC mede discriminação geral — o problema específico é recall, não discriminação geral.

</details>

---

### Questão 10

Uma empresa está avaliando um modelo de IA generativa para atendimento ao cliente. A equipe quer medir se as respostas do chatbot são factualmente corretas, relevantes para a pergunta e gramaticalmente fluentes. Nenhuma métrica automática sozinha captura todos esses aspectos. Qual abordagem de avaliação é MAIS completa?

A) Usar apenas ROUGE para comparar com respostas de referência  
B) Combinar métricas automáticas (ROUGE, BERTScore) com avaliação humana no Amazon Bedrock Model Evaluation  
C) Medir apenas a perplexidade do modelo como indicador geral de qualidade  
D) Monitorar apenas a latência e throughput das respostas em produção  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Combinar métricas automáticas com avaliação humana no Amazon Bedrock Model Evaluation**

✅ **Por que B está correta:** O cenário pede avaliação de múltiplos aspectos (factualidade, relevância, fluência). Métricas automáticas capturam parte, mas qualidade subjetiva requer humanos. Bedrock Model Evaluation suporta ambos — avaliação automática e humana combinadas.

❌ **Por que as outras estão erradas:**
- **A)** ROUGE sozinha mede sobreposição de texto — não captura factualidade nem relevância semântica.
- **C)** Perplexidade mede fluência linguística mas NÃO factualidade nem relevância.
- **D)** Latência/throughput são métricas de performance operacional, não de qualidade das respostas.

</details>
