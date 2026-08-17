# Questões — Tipos de Tarefas de ML

---

### Questão 1

Uma rede de varejo quer segmentar seus clientes em grupos com base no comportamento de compra, sem ter categorias predefinidas. Qual tarefa de ML é mais adequada?

A) Classificação  
B) Regressão  
C) Clustering  
D) Detecção de anomalias  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: C) Clustering**

✅ **Por que C está correta:** "Segmentar em grupos" + "sem categorias predefinidas" = clustering. O modelo descobre agrupamentos naturais nos dados.

❌ **Por que as outras estão erradas:**
- **A)** Classificação requer categorias já definidas para treinar.
- **B)** Regressão prevê valores numéricos, não agrupa.
- **D)** Detecção de anomalias identifica outliers, não cria segmentos.

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

Uma empresa de logística quer prever o tempo de entrega em horas para cada pedido. Qual tipo de tarefa é essa?

A) Classificação  
B) Regressão  
C) Clustering  
D) Recomendação  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Regressão**

✅ **Por que B está correta:** "Prever tempo em horas" é prever um valor numérico contínuo — regressão.

❌ **Por que as outras estão erradas:**
- **A)** Classificação prevê categorias, não valores numéricos.
- **C)** Clustering agrupa dados, não faz previsões.
- **D)** Recomendação sugere itens, não prevê valores.

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

Uma empresa de manufatura quer identificar quando uma máquina está se comportando de forma anormal para agendar manutenção preventiva. Qual tarefa de ML melhor se aplica?

A) Classificação multiclasse  
B) Regressão  
C) Detecção de anomalias  
D) Recomendação  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: C) Detecção de anomalias**

✅ **Por que C está correta:** "Comportamento anormal" é a definição de anomalia. O modelo aprende o padrão normal da máquina e identifica desvios que podem indicar falha iminente — manutenção preditiva clássica.

❌ **Por que as outras estão erradas:**
- **A)** Classificação multiclasse precisaria de categorias definidas de falhas. O cenário quer detectar qualquer comportamento fora do normal.
- **B)** Regressão preveria um valor (ex: dias até falha), mas o cenário quer detectar o comportamento anormal em si.
- **D)** Recomendação sugere itens a usuários — não se aplica a monitoramento de máquinas.

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

