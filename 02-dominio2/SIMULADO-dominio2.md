# Mini-Simulado — Domínio 2: Fundamentos de IA Generativa

**Instruções:** 10 questões, ~14 minutos. Responda todas antes de verificar o gabarito.

---

### Q1

Um Foundation Model é melhor descrito como:

A) Um modelo treinado para uma única tarefa de classificação  
B) Um modelo de grande escala pré-treinado que pode ser adaptado para múltiplas tarefas  
C) Um modelo que funciona apenas na AWS  
D) Um modelo que não pode ser customizado após o pré-treinamento  

---

### Q2

Uma empresa quer respostas factuais e consistentes sobre políticas internas. Qual configuração de temperature usar?

A) Temperature = 1.5  
B) Temperature = 0 ou próximo de 0  
C) Temperature = 1.0  
D) Temperature não importa  

---

### Q3

O que o mecanismo de self-attention permite em um Transformer?

A) Treinar sem GPUs  
B) Que cada token calcule sua relevância em relação a todos os outros tokens  
C) Processar apenas textos curtos  
D) Memorizar todo o dataset de treino  

---

### Q4

Um desenvolvedor fornece 3 exemplos de classificação antes de pedir ao LLM que classifique um novo texto. Qual técnica está usando?

A) Zero-shot  
B) Chain-of-thought  
C) Few-shot  
D) Fine-tuning  

---

### Q5

O que é uma "alucinação" de LLM?

A) Quando o modelo demora muito para responder  
B) Quando o modelo gera informação que parece correta mas é factualmente falsa  
C) Quando o modelo recusa responder  
D) Quando o modelo não entende o idioma  

---

### Q6

Qual serviço AWS é um playground gratuito para experimentar apps com IA generativa sem conta AWS?

A) Amazon Bedrock  
B) Amazon SageMaker  
C) PartyRock  
D) Amazon Q  

---

### Q7

Qual é a vantagem principal de Transformers sobre RNNs?

A) Usam menos memória  
B) Processam tokens em paralelo, permitindo treinamento muito mais rápido  
C) São mais simples de implementar  
D) Funcionam sem dados de treino  

---

### Q8

Para construir uma aplicação GenAI em produção com acesso serverless a múltiplos Foundation Models, qual serviço usar?

A) Amazon Comprehend  
B) Amazon Bedrock  
C) PartyRock  
D) Amazon SageMaker Canvas  

---

### Q9

Qual abordagem deve ser tentada PRIMEIRO para melhorar a qualidade de respostas de um FM?

A) Fine-tuning  
B) Continued Pre-training  
C) Prompt Engineering  
D) RLHF  

---

### Q10 (Múltipla Resposta)

Quais são técnicas para reduzir alucinações em LLMs? **(Selecione DUAS)**

A) Aumentar a temperature  
B) RAG (ancorar em dados reais)  
C) Usar Bedrock Guardrails com grounding check  
D) Aumentar max_tokens  
E) Usar modelos menores sempre  

---

## Gabarito

<details>
<summary>🔍 Ver todas as respostas</summary>

| # | Resposta | Justificativa resumida |
|---|----------|----------------------|
| Q1 | B | FM = grande, pré-treinado, multi-propósito, adaptável |
| Q2 | B | Temperature baixa = determinístico, factual, consistente |
| Q3 | B | Self-attention permite que cada token "olhe" para todos os demais |
| Q4 | C | Exemplos antes da tarefa = few-shot |
| Q5 | B | Alucinação = conteúdo plausível mas falso/inventado |
| Q6 | C | PartyRock = playground gratuito sem conta AWS |
| Q7 | B | Paralelização é a vantagem chave — treinamento ordens de magnitude mais rápido |
| Q8 | B | Bedrock = serverless + múltiplos FMs + produção |
| Q9 | C | Sempre começar com PE (grátis, imediato) antes de RAG ou fine-tuning |
| Q10 | B, C | RAG ancora em fatos; Guardrails grounding detecta alucinações |

**Resultado:**
- 10/10: Excelente — domina os fundamentos de GenAI
- 8-9/10: Bom — revise os que errou
- 6-7/10: Revise C-03 (conceitos LLMs) e C-04 (prompt engineering)
- <6/10: Releia todos os conceitos do Domínio 2

</details>

