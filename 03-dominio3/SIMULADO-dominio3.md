# Mini-Simulado — Domínio 3: Aplicações de Foundation Models

**Instruções:** 10 questões, ~14 minutos. O domínio mais pesado da prova (28%).

---

### Q1

Uma empresa quer que seu chatbot responda perguntas usando documentação interna atualizada semanalmente, sem re-treinar o modelo. Qual abordagem?

A) Fine-tuning semanal  
B) RAG com Bedrock Knowledge Bases  
C) Prompt engineering zero-shot  
D) Continued Pre-training  

---

### Q2

Um chatbot precisa consultar o sistema de pedidos e processar devoluções automaticamente. Qual funcionalidade do Bedrock é necessária?

A) Knowledge Bases  
B) Guardrails  
C) Agents com Action Groups  
D) Model Evaluation  

---

### Q3

Uma empresa quer mudar o estilo de escrita do FM para gerar sempre no tom formal corporativo. Prompt engineering não está mantendo a consistência. Qual próximo passo?

A) RAG  
B) Fine-tuning  
C) Aumentar temperature  
D) Usar vector database  

---

### Q4

Qual componente de um sistema RAG é responsável por dividir documentos grandes em pedaços menores?

A) Embedding model  
B) Vector database  
C) Chunking  
D) Foundation Model  

---

### Q5

Uma empresa implementou RAG mas as respostas não são relevantes — o contexto retornado não corresponde às perguntas. Qual componente otimizar?

A) Temperature do FM  
B) Estratégia de chunking e modelo de embeddings  
C) Max tokens da resposta  
D) Tamanho do Foundation Model  

---

### Q6

Qual é o modelo de precificação padrão (on-demand) do Amazon Bedrock?

A) Assinatura mensal fixa  
B) Paga por hora  
C) Paga por token processado (entrada e saída)  
D) Gratuito  

---

### Q7

Uma empresa precisa processar 200.000 documentos para gerar resumos, sem necessidade de tempo real. Qual abordagem minimiza custo?

A) Real-time API calls  
B) Batch inference  
C) Provisioned Throughput  
D) Fine-tuning  

---

### Q8

Qual métrica avalia qualidade de resumos gerados por IA?

A) BLEU  
B) RMSE  
C) ROUGE  
D) F1 Score  

---

### Q9 (Múltipla Resposta)

Quais abordagens NÃO requerem re-treinar o Foundation Model? **(Selecione DUAS)**

A) Fine-tuning  
B) RAG  
C) Continued Pre-training  
D) Prompt Engineering  
E) RLHF  

---

### Q10

Uma empresa de medicina quer que o FM entenda profundamente terminologia médica especializada que modelos gerais não conhecem. Qual abordagem mais profunda?

A) Prompt Engineering com system prompt médico  
B) RAG com artigos médicos  
C) Continued Pre-training com corpus médico  
D) Bedrock Guardrails  

---

## Gabarito

<details>
<summary>🔍 Ver todas as respostas</summary>

| # | Resposta | Justificativa resumida |
|---|----------|----------------------|
| Q1 | B | Dados mudam semanalmente + sem re-treinar = RAG |
| Q2 | C | Executar ações (consultar + processar) = Agents |
| Q3 | B | Estilo/tom consistente que PE não resolve = Fine-tuning |
| Q4 | C | Chunking divide documentos em pedaços para indexação |
| Q5 | B | Contexto ruim = problema na retrieval (chunking + embeddings) |
| Q6 | C | Bedrock cobra por token (entrada + saída separados) |
| Q7 | B | Volume alto + não real-time = Batch inference (mais barato) |
| Q8 | C | ROUGE = resumos. BLEU = tradução |
| Q9 | B, D | RAG e PE operam na inferência sem alterar o modelo |
| Q10 | C | Entender terminologia nova = continued pre-training (mais profundo que RAG) |

**Resultado:**
- 10/10: Excelente — domina o domínio mais pesado
- 8-9/10: Bom — revise os que errou
- 6-7/10: Foco em C-02 (RAG) e C-03 (Fine-tuning vs PE vs RAG)
- <6/10: Este é 28% da prova — releia todos os blocos do Domínio 3

</details>

