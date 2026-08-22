# Questões — Tipos de Tarefas de ML

---

### Questão 1

Uma rede de varejo com 2 milhões de clientes quer identificar grupos com padrões de compra similares para criar campanhas de marketing direcionadas. A equipe de marketing não tem categorias predefinidas de clientes — querem que os padrões emerjam dos dados. Qual tarefa de ML é mais adequada?

A) Classificação supervisionada usando as categorias de produtos como rótulos  
B) Regressão para prever o valor de compra de cada grupo  
C) Clustering para descobrir agrupamentos naturais nos dados sem rótulos predefinidos  
D) Detecção de anomalias para identificar clientes com comportamento atípico  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: C) Clustering para descobrir agrupamentos naturais nos dados sem rótulos predefinidos**

✅ **Por que C está correta:** "Identificar grupos" + "sem categorias predefinidas" + "padrões emerjam dos dados" = clustering. O modelo descobre segmentos naturais baseado em similaridade de comportamento.

❌ **Por que as outras estão erradas:**
- **A)** Classificação requer categorias já definidas para treinar — o cenário explicitamente diz que não existem.
- **B)** Regressão prevê valores numéricos para cada cliente, não agrupa clientes similares.
- **D)** Detecção de anomalias encontra outliers (comportamento anormal), não cria segmentos de clientes para marketing.

</details>

---

### Questão 2

Uma empresa de streaming quer sugerir filmes aos usuários com base no histórico de visualização de outros usuários com gostos similares. Qual serviço AWS é mais adequado?

A) Amazon Forecast  
B) Amazon Personalize  
C) Amazon Comprehend  
D) Amazon Kendra  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Amazon Personalize**

✅ **Por que B está correta:** Amazon Personalize é o serviço gerenciado para recomendações. Usa filtragem colaborativa (comportamento de usuários similares) para sugerir itens relevantes — exatamente o cenário descrito.

❌ **Por que as outras estão erradas:**
- **A)** Forecast é para previsão de séries temporais (demanda, receita), não recomendações.
- **C)** Comprehend faz NLP (sentimento, entidades), não recomendações.
- **D)** Kendra é busca empresarial inteligente, não sistema de recomendação.

</details>

---

### Questão 3

Uma empresa de logística processa 50.000 entregas por dia e quer prever o tempo estimado de entrega em horas para cada pedido, levando em conta distância, tráfego histórico e condições climáticas. A previsão será exibida ao cliente no momento da compra. Qual tipo de tarefa de ML é essa?

A) Classificação multiclasse — categorizar entregas como "rápida", "normal" ou "lenta"  
B) Regressão — prever um valor numérico contínuo (horas até entrega)  
C) Clustering — agrupar pedidos por similaridade de tempo  
D) Recomendação — sugerir a melhor opção de frete ao cliente  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Regressão — prever um valor numérico contínuo (horas até entrega)**

✅ **Por que B está correta:** "Prever tempo em horas" é prever um valor numérico contínuo (ex: 4.5 horas, 23.2 horas) — regressão. O modelo aprende a relação entre features (distância, tráfego, clima) e o tempo de entrega.

❌ **Por que as outras estão erradas:**
- **A)** Classificar em "rápida/normal/lenta" perderia a precisão numérica que o cenário requer — o cliente quer ver "Entrega em 4h", não "Entrega normal".
- **C)** Clustering agrupa dados similares sem fazer previsões — não gera um tempo estimado para cada pedido.
- **D)** Recomendação sugere itens a usuários. Prever tempo não é recomendar frete, é calcular uma estimativa.

</details>

---

### Questão 4

Uma empresa precisa extrair automaticamente nomes, datas e valores de milhares de faturas em PDF. Qual serviço AWS é mais adequado?

A) Amazon Comprehend  
B) Amazon Textract  
C) Amazon Rekognition  
D) Amazon Translate  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Amazon Textract**

✅ **Por que B está correta:** Amazon Textract extrai texto, formulários e tabelas de documentos (PDFs, imagens). É projetado especificamente para entender a estrutura de documentos e extrair dados de campos.

❌ **Por que as outras estão erradas:**
- **A)** Comprehend analisa texto já extraído (sentimento, entidades). Não lê PDFs diretamente.
- **C)** Rekognition é para visão computacional (objetos, faces, moderação), não extração de texto estruturado de documentos.
- **D)** Translate traduz texto entre idiomas, não extrai texto de documentos.

</details>

---

### Questão 5

Uma empresa de manufatura opera 200 máquinas CNC 24/7 e coleta dados de sensores (temperatura, vibração, pressão) em tempo real. A equipe de manutenção quer ser alertada quando uma máquina começar a se comportar de forma diferente do padrão histórico, permitindo intervenção antes da falha. Qual tarefa de ML melhor se aplica?

A) Classificação multiclasse para categorizar o tipo de falha iminente  
B) Regressão para prever o número de dias até a próxima falha  
C) Detecção de anomalias para identificar desvios do comportamento normal da máquina  
D) Clustering para agrupar máquinas com padrões de desgaste similares  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: C) Detecção de anomalias para identificar desvios do comportamento normal da máquina**

✅ **Por que C está correta:** O cenário pede identificar "comportamento diferente do padrão histórico" — isso é exatamente detecção de anomalias. O modelo aprende o perfil normal dos sensores e alerta quando os valores desviam significativamente.

❌ **Por que as outras estão erradas:**
- **A)** Classificação de tipo de falha requer histórico rotulado de cada categoria de falha. O cenário quer detectar QUALQUER desvio, não categorizar tipos específicos.
- **B)** Regressão de tempo-até-falha (RUL — Remaining Useful Life) é uma abordagem válida mas diferente. O cenário foca em "comportamento diferente" (anomalia), não em "quanto tempo falta" (previsão numérica).
- **D)** Clustering agruparia máquinas por similaridade — útil para planejamento, mas não gera alertas em tempo real de comportamento anormal.

</details>

---

### Questão 6

Qual serviço AWS deve ser usado para analisar o sentimento (positivo, negativo, neutro) de milhares de avaliações de clientes?

A) Amazon Lex  
B) Amazon Polly  
C) Amazon Comprehend  
D) Amazon Transcribe  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: C) Amazon Comprehend**

✅ **Por que C está correta:** Amazon Comprehend é o serviço de NLP que realiza análise de sentimento, extração de entidades, detecção de idioma e tópicos — tudo pré-treinado, sem necessidade de criar modelo.

❌ **Por que as outras estão erradas:**
- **A)** Lex é para construir chatbots conversacionais, não análise de sentimento.
- **B)** Polly converte texto em fala (text-to-speech), não analisa conteúdo.
- **D)** Transcribe converte áudio em texto (speech-to-text), não analisa sentimento.

</details>

