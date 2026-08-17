# Mini-Simulado — Domínio 4: Diretrizes para IA Responsável

**Instruções:** 10 questões, ~14 minutos.

---

### Q1

Um modelo de contratação está rejeitando candidatos de certas regiões do país de forma desproporcional. Qual ferramenta AWS investiga isso?

A) Amazon Bedrock Guardrails  
B) SageMaker Clarify  
C) Amazon CloudWatch  
D) AWS Config  

---

### Q2

Uma empresa quer filtrar PII (dados pessoais) das respostas do chatbot automaticamente. Qual funcionalidade usar?

A) SageMaker Model Monitor  
B) Bedrock Guardrails (PII filter)  
C) Amazon Macie  
D) AWS IAM  

---

### Q3

O que são SHAP values?

A) Uma métrica de performance do modelo  
B) A contribuição de cada feature para uma previsão específica  
C) Um tipo de regularização  
D) Uma técnica de prompt engineering  

---

### Q4

Um modelo de diagnóstico médico tem confiança abaixo de 80% em uma previsão. A empresa quer que esses casos sejam revisados por um médico humano. Qual serviço implementa isso?

A) SageMaker Autopilot  
B) Amazon Augmented AI (A2I)  
C) Amazon Bedrock  
D) AWS Lambda  

---

### Q5

Qual tipo de viés ocorre quando os dados de treino refletem discriminações históricas que existiam na sociedade?

A) Viés de automação  
B) Viés de medição  
C) Viés histórico  
D) Viés algorítmico  

---

### Q6

Qual é a principal técnica para reduzir alucinações em chatbots com IA generativa?

A) Aumentar temperature  
B) RAG (ancorar em dados reais)  
C) Usar modelo menor  
D) Remover system prompt  

---

### Q7

Bedrock Guardrails pode fazer qual das seguintes coisas?

A) Treinar modelos customizados  
B) Bloquear tópicos específicos e filtrar conteúdo ofensivo  
C) Criar vector databases  
D) Fazer deploy de endpoints  

---

### Q8

O que documentam as AWS AI Service Cards?

A) Instruções de instalação dos serviços  
B) Uso pretendido, limitações e avaliações de fairness dos serviços de IA  
C) Preços e billing  
D) Configurações de IAM  

---

### Q9

Uma empresa treinou um modelo apenas com dados de clientes jovens (18-25 anos). O modelo funciona mal com clientes de 50+ anos. Qual ação corretiva é mais importante?

A) Usar regularização  
B) Coletar e incluir dados representativos de todas as faixas etárias  
C) Aumentar epochs de treino  
D) Usar um modelo maior  

---

### Q10 (Múltipla Resposta)

Quais são princípios de IA Responsável da AWS? **(Selecione DUAS)**

A) Maximizar velocidade de inferência a qualquer custo  
B) Fairness (equidade entre grupos)  
C) Explicabilidade (entender decisões do modelo)  
D) Usar apenas modelos proprietários  
E) Evitar monitoramento para reduzir custos  

---

## Gabarito

<details>
<summary>🔍 Ver todas as respostas</summary>

| # | Resposta | Justificativa resumida |
|---|----------|----------------------|
| Q1 | B | SageMaker Clarify detecta viés por subgrupo (região, gênero, etc.) |
| Q2 | B | Guardrails PII filter mascara/bloqueia dados pessoais em outputs |
| Q3 | B | SHAP = contribuição de cada feature para UMA previsão específica |
| Q4 | B | A2I = human-in-the-loop quando confiança < threshold |
| Q5 | C | Viés histórico = dados refletem discriminações passadas da sociedade |
| Q6 | B | RAG ancora em dados reais — técnica mais eficaz contra alucinações |
| Q7 | B | Guardrails = denied topics + content filters + PII + grounding check |
| Q8 | B | Service Cards = transparência sobre uso pretendido, limitações, fairness |
| Q9 | B | Dados não-representativos = coletar dados diversos é a correção fundamental |
| Q10 | B, C | Fairness e Explicabilidade são princípios core de IA Responsável |

**Resultado:**
- 10/10: Excelente
- 8-9/10: Bom — revise os erros
- 6-7/10: Foco em Guardrails, Clarify e tipos de viés
- <6/10: Releia C-01 a C-03 do Domínio 4

</details>

