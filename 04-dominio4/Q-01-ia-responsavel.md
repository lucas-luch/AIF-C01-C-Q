# Questões — IA Responsável

---

### Questão 1

Um modelo de aprovação de crédito está aprovando 85% dos candidatos homens mas apenas 55% das candidatas mulheres. Qual ferramenta AWS deve ser usada para investigar esse problema?

A) Amazon Bedrock Guardrails  
B) Amazon SageMaker Clarify  
C) Amazon CloudWatch  
D) Amazon Rekognition  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Amazon SageMaker Clarify**

✅ **Por que B está correta:** SageMaker Clarify detecta e mede viés em modelos — analisa previsões por subgrupo (gênero, idade, etc.) e gera relatórios de fairness. É a ferramenta certa para investigar disparidade de aprovação entre gêneros.

❌ **Por que as outras estão erradas:**
- **A)** Guardrails filtram conteúdo de LLMs, não detectam viés em modelos de classificação.
- **C)** CloudWatch monitora métricas operacionais (latência, erros), não fairness.
- **D)** Rekognition é visão computacional — não analisa modelos de crédito.

</details>

---

### Questão 2

Uma empresa quer entender POR QUE seu modelo de ML negou crédito a um cliente específico. Qual técnica deve usar?

A) Aumentar a acurácia do modelo  
B) SHAP values para explicar a previsão individual  
C) Re-treinar o modelo com mais dados  
D) Usar um modelo maior  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) SHAP values para explicar a previsão individual**

✅ **Por que B está correta:** SHAP values mostram a contribuição de cada feature para uma previsão específica. Exemplo: "renda contribuiu -30%, histórico de pagamento +20%, dívida atual -50%". Explica exatamente por que AQUELE cliente foi negado.

❌ **Por que as outras estão erradas:**
- **A)** Acurácia não explica decisões individuais.
- **C)** Mais dados podem melhorar o modelo, mas não explicam decisões já tomadas.
- **D)** Modelo maior pode ser mais preciso, mas geralmente é MENOS explicável (caixa-preta maior).

</details>

---

### Questão 3

Qual é o propósito das AWS AI Service Cards?

A) Gerenciar billing e custos dos serviços de IA  
B) Fornecer transparência sobre limitações, uso pretendido e avaliações de fairness dos serviços de IA  
C) Configurar permissões IAM para serviços de IA  
D) Monitorar performance de modelos em produção  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Fornecer transparência sobre limitações, uso pretendido e avaliações de fairness dos serviços de IA**

✅ **Por que B está correta:** AI Service Cards são documentação de transparência publicada pela AWS para seus serviços de IA. Descrevem: uso pretendido, limitações, decisões de design, métricas de fairness e melhores práticas.

❌ **Por que as outras estão erradas:**
- **A)** Billing é gerenciado no console AWS / Cost Explorer, não em Service Cards.
- **C)** Permissões IAM são configuradas via policies/roles, não Service Cards.
- **D)** Monitoramento é feito por SageMaker Model Monitor / CloudWatch.

</details>

---

### Questão 4

Uma empresa usa um LLM para atendimento ao cliente e quer prevenir que o modelo gere conteúdo ofensivo ou discuta tópicos concorrentes. Qual ferramenta implementa isso?

A) SageMaker Clarify  
B) Amazon Bedrock Guardrails  
C) SageMaker Model Monitor  
D) AWS Config  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Amazon Bedrock Guardrails**

✅ **Por que B está correta:** Guardrails permite configurar content filters (bloquear ofensivo) e denied topics (bloquear discussão sobre concorrentes) — aplicados a inputs e outputs do LLM em produção.

❌ **Por que as outras estão erradas:**
- **A)** Clarify detecta viés em modelos, não filtra conteúdo de LLMs.
- **C)** Model Monitor detecta drift de dados/modelo, não filtra conteúdo.
- **D)** AWS Config monitora compliance de recursos AWS, não conteúdo de IA.

</details>

---

### Questão 5

Quando o Amazon Augmented AI (A2I) deve ser usado?

A) Para treinar modelos mais rapidamente  
B) Para incluir revisão humana quando a IA tem baixa confiança em suas previsões  
C) Para criptografar dados em trânsito  
D) Para otimizar custos de inferência  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Para incluir revisão humana quando a IA tem baixa confiança em suas previsões**

✅ **Por que B está correta:** A2I implementa human-in-the-loop — quando a confiança do modelo está abaixo de um threshold ou em categorias de risco, a previsão é encaminhada para revisão humana antes da decisão final.

❌ **Por que as outras estão erradas:**
- **A)** A2I não acelera treinamento — opera na inferência (pós-previsão).
- **C)** Criptografia é função de TLS/KMS, não A2I.
- **D)** A2I adiciona custo (humanos revisando), não otimiza custos.

</details>

---

### Questão 6

Um modelo de IA foi treinado com dados predominantemente de clientes de São Paulo. Quando usado em Manaus, as previsões são muito piores. Qual tipo de viés isso representa?

A) Viés algorítmico  
B) Viés de seleção (selection bias)  
C) Viés de automação  
D) Viés de medição  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Viés de seleção (selection bias)**

✅ **Por que B está correta:** Os dados de treino não representam a população completa — foram coletados apenas de uma região (São Paulo). Quando aplicado em contexto diferente (Manaus), as previsões falham. Isso é viés de seleção/amostragem.

❌ **Por que as outras estão erradas:**
- **A)** Viés algorítmico é quando o algoritmo amplifica padrões indesejados — aqui o problema é nos dados.
- **C)** Viés de automação é confiar demais no output da IA — não é o caso descrito.
- **D)** Viés de medição é quando a métrica é inadequada — aqui o problema é representatividade dos dados.

</details>

