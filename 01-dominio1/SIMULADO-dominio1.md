# Mini-Simulado — Domínio 1: Fundamentos de IA e ML

**Instruções:** 10 questões, ~14 minutos (proporção da prova real). Tente responder todas antes de ver o gabarito.

---

### Q1

Uma empresa de telecomunicações quer prever quais clientes vão cancelar o serviço nos próximos 30 dias usando histórico de uso rotulado. Qual tipo de ML e tarefa?

A) Não-supervisionado — Clustering  
B) Supervisionado — Classificação  
C) Supervisionado — Regressão  
D) Reforço  

---

### Q2

Um modelo de ML atinge 93% de acurácia no treino e 91% no teste. Outro modelo atinge 99% no treino e 68% no teste. Qual afirmação é correta?

A) O primeiro modelo está com underfitting  
B) O segundo modelo está com overfitting  
C) Ambos estão com overfitting  
D) Ambos estão funcionando bem  

---

### Q3

Uma equipe precisa converter gravações de chamadas de atendimento em texto para análise. Qual serviço AWS?

A) Amazon Polly  
B) Amazon Comprehend  
C) Amazon Transcribe  
D) Amazon Lex  

---

### Q4

Em um dataset de detecção de fraude, 99.5% das transações são legítimas e 0.5% são fraude. Um modelo que sempre prevê "legítima" terá 99.5% de acurácia. Por que isso é problemático?

A) O modelo está com underfitting  
B) A acurácia é enganosa em dados desbalanceados — recall para fraude será 0%  
C) O modelo precisa de mais epochs de treino  
D) A acurácia sempre é a melhor métrica  

---

### Q5

Qual etapa do ciclo de vida de ML é responsável por detectar data drift e degradação de performance após o modelo ir para produção?

A) Avaliação  
B) Feature Engineering  
C) Treinamento  
D) Monitoramento  

---

### Q6

Uma empresa detectou que a performance do modelo caiu significativamente 3 meses após o deploy, sem mudanças no código. A causa mais provável é:

A) Bug no código do modelo  
B) Data drift — os dados em produção mudaram em relação ao treino  
C) Underfitting  
D) O endpoint foi mal configurado  

---

### Q7

Qual serviço AWS oferece ML sem código (no-code) com interface visual para analistas de negócio?

A) Amazon SageMaker Studio  
B) Amazon SageMaker Canvas  
C) Amazon Bedrock  
D) Amazon Athena  

---

### Q8 (Múltipla Resposta)

Quais técnicas combatem overfitting? **(Selecione DUAS)**

A) Regularização (L1/L2)  
B) Adicionar mais camadas à rede neural  
C) Early stopping  
D) Treinar por mais epochs  
E) Remover dados de validação  

---

### Q9

Uma empresa quer prever a demanda de vendas para os próximos 6 meses usando dados históricos mensais de vendas. Qual serviço AWS é mais adequado?

A) Amazon Personalize  
B) Amazon Forecast  
C) Amazon Comprehend  
D) Amazon Rekognition  

---

### Q10

Qual é a função do conjunto de dados de VALIDAÇÃO no ciclo de treino?

A) Treinar o modelo com mais dados  
B) Avaliar a performance final do modelo  
C) Ajustar hiperparâmetros durante o treinamento  
D) Gerar previsões em produção  

---

## Gabarito

<details>
<summary>🔍 Ver todas as respostas</summary>

| # | Resposta | Justificativa resumida |
|---|----------|----------------------|
| Q1 | B | Dados rotulados + prever categoria (cancela/não) = classificação supervisionada |
| Q2 | B | 99% treino / 68% teste = gap enorme = overfitting. Primeiro modelo (93/91) está bem |
| Q3 | C | Transcribe = áudio → texto (speech-to-text) |
| Q4 | B | Em dados muito desbalanceados, acurácia é enganosa. Recall para a classe rara é o que importa |
| Q5 | D | Monitoramento é a etapa pós-deploy que detecta drift e degradação |
| Q6 | B | Performance degrada ao longo do tempo sem mudanças no modelo = data drift |
| Q7 | B | SageMaker Canvas = ML visual sem código para analistas de negócio |
| Q8 | A, C | Regularização penaliza complexidade; Early stopping para treino antes de memorizar |
| Q9 | B | Forecast = previsão de séries temporais (demanda, vendas) |
| Q10 | C | Validação serve para ajustar hiperparâmetros. Teste é para avaliação final |

**Resultado:**
- 10/10: Excelente — pronto para avançar
- 8-9/10: Bom — revise os que errou
- 6-7/10: Revise os blocos C-03 (conceitos) e C-06 (serviços)
- <6/10: Releia todos os conceitos do Domínio 1

</details>

