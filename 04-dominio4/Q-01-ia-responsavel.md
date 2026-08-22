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

Uma empresa de saúde desenvolveu um modelo de IA para priorizar pacientes em filas de espera. O regulador exige documentação sobre as limitações do modelo, os cenários de uso pretendido e as avaliações de fairness realizadas. Onde a AWS publica esse tipo de informação para seus próprios serviços de IA?

A) AWS Well-Architected Framework — pilar de Excelência Operacional  
B) AWS AI Service Cards — documentação de transparência com limitações, uso pretendido e fairness  
C) AWS Shared Responsibility Model — define o que é responsabilidade do cliente vs AWS  
D) Amazon SageMaker Model Cards — registro de metadados dos modelos customizados do cliente  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) AWS AI Service Cards — documentação de transparência com limitações, uso pretendido e fairness**

✅ **Por que B está correta:** AI Service Cards são documentação de transparência publicada pela AWS para seus serviços de IA (Rekognition, Textract, etc.). Descrevem: uso pretendido, limitações conhecidas, decisões de design, e métricas de fairness — exatamente o que o regulador pede como referência.

❌ **Por que as outras estão erradas:**
- **A)** Well-Architected Framework cobre melhores práticas de arquitetura cloud (não específico de IA/fairness).
- **C)** Shared Responsibility Model define divisão de segurança (AWS cuida da infra, cliente cuida dos dados/apps), não transparência de IA.
- **D)** SageMaker Model Cards são para SEUS modelos customizados — você cria para documentar os próprios modelos. AI Service Cards são o que a AWS publica sobre os serviços DELA.

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

Uma empresa de varejo implantou um modelo de ML para aprovar ou rejeitar pedidos de crédito automaticamente. O regulador exige que decisões de alto impacto financeiro tenham supervisão humana antes de serem finalizadas, especialmente quando o modelo tem baixa confiança. Qual serviço AWS implementa esse requisito?

A) Amazon SageMaker Clarify para detectar viés antes da aprovação  
B) Amazon Augmented AI (A2I) para incluir revisão humana quando a confiança é baixa  
C) Amazon Bedrock Guardrails para bloquear decisões financeiras do modelo  
D) SageMaker Model Monitor para detectar degradação do modelo e pausar decisões  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Amazon Augmented AI (A2I) para incluir revisão humana quando a confiança é baixa**

✅ **Por que B está correta:** A2I implementa human-in-the-loop — quando a confiança do modelo está abaixo de um threshold configurável, a decisão é encaminhada para revisão humana antes de ser finalizada. Atende exatamente o requisito regulatório descrito.

❌ **Por que as outras estão erradas:**
- **A)** Clarify detecta viés e explica previsões, mas não intercepta decisões em tempo real para revisão humana.
- **C)** Guardrails filtram conteúdo de LLMs (texto) — não se aplicam a modelos de classificação/crédito.
- **D)** Model Monitor detecta drift e gera alertas, mas não intercepta decisões individuais para revisão humana em tempo real.

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



---

### Questão 7

Uma empresa de recrutamento usa um modelo de ML para ranquear candidatos. A equipe descobriu que candidatos com nomes associados a minorias étnicas recebem scores sistematicamente mais baixos, mesmo com qualificações idênticas. Qual tipo de viés é MAIS provável e qual a causa raiz?

A) Viés algorítmico — o algoritmo escolhido é inerentemente discriminatório  
B) Viés nos dados de treinamento — os dados históricos refletem decisões humanas preconceituosas  
C) Viés de automação — os recrutadores confiam demais no modelo  
D) Viés de medição — a métrica usada é inadequada  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Viés nos dados de treinamento — dados históricos refletem decisões preconceituosas**

✅ **Por que B está correta:** Se o modelo aprendeu com decisões históricas de humanos que discriminavam (consciente ou inconscientemente), ele reproduz esse padrão. O viés está nos DADOS (rótulos históricos com preconceito), não no algoritmo em si.

❌ **Por que as outras estão erradas:**
- **A)** Algoritmos são neutros — aprendem padrões dos dados. O mesmo algoritmo com dados sem viés não discriminaria.
- **C)** Viés de automação é quando humanos aceitam output da IA sem questionar — é um problema diferente (no uso, não no modelo).
- **D)** Viés de medição seria usar métrica errada para avaliar. Aqui o modelo está ativamente discriminando, não sendo mal-avaliado.

</details>

---

### Questão 8

Uma empresa quer avaliar se seu modelo de IA generativa gera respostas ofensivas, estereotipadas ou perigosas. Precisa testar isso ANTES de lançar em produção com uma avaliação estruturada. Qual abordagem de responsible AI é MAIS adequada?

A) Deployar em produção e monitorar reclamações de usuários  
B) Red teaming — testar adversarialmente o modelo com prompts projetados para provocar respostas problemáticas  
C) Aumentar o tamanho do modelo para melhorar a qualidade geral  
D) Usar apenas temperature = 0 para eliminar respostas imprevisíveis  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Red teaming — testar adversarialmente antes do deploy**

✅ **Por que B está correta:** Red teaming é a prática de testar modelos com prompts adversariais projetados para revelar comportamentos indesejados (toxicidade, estereótipos, jailbreaks) ANTES do deploy. É uma etapa fundamental de responsible AI.

❌ **Por que as outras estão erradas:**
- **A)** Esperar reclamações em produção expõe usuários a conteúdo problemático — irresponsável e potencialmente ilegal.
- **C)** Modelo maior não garante comportamento seguro — modelos grandes podem ser tão ou mais tóxicos.
- **D)** Temperature 0 não elimina respostas problemáticas — apenas torna output determinístico (pode ser deterministicamente ofensivo).

</details>

---

### Questão 9

Uma seguradora implantou um modelo que automaticamente rejeita pedidos de indenização. Um cliente recebeu rejeição sem explicação. O regulador exige que toda decisão automatizada que impacte financeiramente o cliente tenha explicação compreensível. Qual combinação de práticas de IA responsável atende AMBOS os requisitos (explicabilidade + supervisão)?

A) Aumentar a acurácia do modelo para reduzir rejeições incorretas  
B) Implementar explicabilidade (SHAP values) para cada decisão + Amazon A2I para revisão humana de rejeições  
C) Usar apenas Guardrails para filtrar respostas sem explicação  
D) Re-treinar o modelo com mais dados para eliminar erros  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Explicabilidade (SHAP) + A2I para revisão humana de rejeições**

✅ **Por que B está correta:** SHAP values explicam POR QUE o modelo rejeitou (quais fatores contribuíram — atende explicabilidade). A2I encaminha rejeições para revisão humana antes de notificar o cliente (atende supervisão). Juntos, cumprem ambos os requisitos regulatórios.

❌ **Por que as outras estão erradas:**
- **A)** Mais acurácia não fornece explicação ao cliente nem supervisão humana.
- **C)** Guardrails filtram conteúdo de LLMs — não explicam decisões de modelos de classificação nem implementam revisão humana.
- **D)** Mais dados podem melhorar o modelo, mas não explicam decisões individuais nem adicionam supervisão.

</details>

---

### Questão 10

Uma empresa está documentando seu modelo de ML para compliance. O regulador exige documentação sobre: propósito do modelo, limitações conhecidas, métricas de fairness por subgrupo, e dados de treinamento usados. Qual ferramenta AWS permite criar essa documentação de forma estruturada?

A) AWS CloudTrail — registra chamadas de API  
B) Amazon SageMaker Model Cards — documentação estruturada de modelos com propósito, limitações e métricas  
C) Amazon SageMaker Model Monitor — monitora drift em produção  
D) AWS AI Service Cards — documentação dos serviços pré-treinados da AWS  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Amazon SageMaker Model Cards — documentação estruturada de modelos**

✅ **Por que B está correta:** Model Cards permitem documentar: propósito/uso pretendido, limitações, métricas de performance por subgrupo (fairness), dados de treinamento, e considerações éticas. É a ferramenta da AWS para documentação de governança de modelos CUSTOMIZADOS.

❌ **Por que as outras estão erradas:**
- **A)** CloudTrail audita QUEM fez QUAL ação (chamadas de API) — não documenta características do modelo.
- **C)** Model Monitor monitora drift em tempo real — não cria documentação de governança.
- **D)** AI Service Cards documentam os serviços pré-treinados da AWS (Rekognition, Textract) — não os modelos CUSTOMIZADOS do cliente.

</details>

---

### Questão 11 (Múltipla Resposta)

Uma empresa está implementando práticas de IA responsável. Quais princípios fazem parte do framework de Responsible AI da AWS? **(Selecione DUAS)**

A) Maximizar lucro é o principal objetivo de IA responsável  
B) Fairness — sistemas devem tratar subgrupos de forma equitativa  
C) Velocidade — modelos devem sempre priorizar latência sobre segurança  
D) Transparência — limitações e capacidades devem ser documentadas e comunicadas  
E) Complexidade — modelos mais complexos são mais responsáveis  

<details>
<summary>🔍 Ver resposta</summary>

**Respostas: B e D**

✅ **Por que B está correta:** Fairness é pilar central de IA responsável — modelos não devem discriminar por gênero, raça, idade ou outras características protegidas.

✅ **Por que D está correta:** Transparência é fundamental — usuários e stakeholders devem entender o que o modelo faz, suas limitações, e como decisões são tomadas.

❌ **Por que as outras estão erradas:**
- **A)** Lucro não é um princípio de IA responsável — responsabilidade pode implicar custos adicionais (revisão humana, auditoria).
- **C)** Segurança nunca deve ser sacrificada por velocidade — é um trade-off, não uma prioridade absoluta.
- **E)** Complexidade geralmente REDUZ explicabilidade — modelos mais simples são frequentemente mais responsáveis.

</details>
