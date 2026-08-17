# Simulado Final 2 — AWS Certified AI Practitioner (AIF-C01)

**60 questões | 90 minutos | Aprovação: 700/1000**

Distribuição por domínio:
- Domínio 1 (Fundamentos de IA e ML): 12 questões
- Domínio 2 (Fundamentos de IA Generativa): 15 questões
- Domínio 3 (Aplicações de Foundation Models): 17 questões
- Domínio 4 (IA Responsável): 8 questões
- Domínio 5 (Segurança, Conformidade e Governança): 8 questões

**Instruções:** Responda cada questão antes de expandir a resposta. Cronometre 90 minutos.

---

## Questões

### 1.
Uma fintech quer construir um modelo que aprenda a otimizar a alocação de portfólio em tempo real, ajustando investimentos com base nas respostas do mercado (ganhos ou perdas). O sistema deve aprender continuamente qual estratégia maximiza o retorno. Qual tipo de ML é MAIS adequado?

A) Aprendizado Supervisionado — Regressão
B) Aprendizado Não-Supervisionado — Clustering
C) Aprendizado por Reforço
D) Aprendizado Semi-Supervisionado

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: C**

✅ Otimizar decisões em tempo real + feedback (ganho/perda) + maximizar recompensa = aprendizado por reforço. Agente aprende por interação contínua.

❌ **A)** Regressão prevê valores a partir de dados históricos — não otimiza decisões em tempo real com feedback.
❌ **B)** Clustering agrupa dados — não toma decisões nem aprende com recompensas.
❌ **D)** Semi-supervisionado mistura rótulos — não é sobre decisões sequenciais com feedback.
</details>

---

### 2.
Uma empresa de telecomunicações tem milhões de registros de comportamento de clientes mas apenas 500 estão rotulados como "churn" ou "ativo" (rotulagem é cara pois requer análise manual). A empresa quer classificar todos os clientes. Qual abordagem MAXIMIZA o uso dos dados disponíveis?

A) Treinar supervisionado apenas com os 500 rotulados
B) Usar aprendizado semi-supervisionado que aproveita os poucos rótulos + dados não-rotulados
C) Clustering não-supervisionado ignorando os rótulos existentes
D) Aprendizado por reforço

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ Poucos rótulos + muitos dados sem rótulo = semi-supervisionado é projetado para isso. Usa os 500 rótulos para guiar aprendizado nos milhões sem rótulo.

❌ **A)** Supervisionado com 500 desperdiça milhões de dados não-rotulados.
❌ **C)** Clustering ignora os rótulos valiosos existentes e não classifica em churn/ativo.
❌ **D)** Reforço é para decisões sequenciais com recompensa — não se aplica aqui.
</details>

---

### 3.
Um cientista de dados precisa comparar dois modelos de classificação para diagnóstico médico. O Modelo A tem AUC-ROC de 0.92 e o Modelo B tem AUC-ROC de 0.78. O que isso indica?

A) Modelo A é 14% mais rápido que Modelo B
B) Modelo A tem melhor capacidade de distinguir entre classes positiva e negativa, independente do threshold
C) Modelo A usa menos memória
D) Ambos são equivalentes pois a diferença é pequena

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ AUC-ROC mede capacidade de separar classes. 0.92 > 0.78 = Modelo A distingue melhor doentes de saudáveis, independentemente do ponto de corte escolhido.

❌ **A)** AUC-ROC não mede velocidade.
❌ **C)** AUC-ROC não tem relação com memória.
❌ **D)** 0.92 vs 0.78 é uma diferença significativa em diagnóstico médico.
</details>

---

### 4.
Uma empresa tem um modelo de previsão de preços em produção. O RMSE aumentou 40% em 3 meses. Investigando, descobrem que um boom imobiliário trouxe imóveis de luxo que não existiam no treino. Qual ação RESOLVE o problema a longo prazo?

A) Aumentar regularização do modelo atual
B) Re-treinar o modelo com dados atualizados que incluem os novos imóveis de luxo
C) Reduzir a complexidade do modelo
D) Aumentar early stopping

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ Dados mudaram (novos tipos de imóveis). O modelo precisa ver esses dados para aprender os novos padrões. Re-treinar com dados atualizados é a solução definitiva.

❌ **A)** Regularização não resolve — o modelo não conhece os dados novos.
❌ **C)** Simplificar não resolve — o problema é falta de dados, não complexidade.
❌ **D)** Early stopping previne overfitting — não resolve falta de dados novos.
</details>

---

### 5.
Uma empresa de RH quer: (1) agrupar candidatos por perfil similar E (2) prever quais terão melhor performance. Qual combinação de abordagens é necessária?

A) Dois modelos supervisionados
B) Não-supervisionado (clustering) + Supervisionado (classificação/regressão)
C) Apenas clustering resolve ambos
D) Apenas reforço

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ Agrupar sem categorias predefinidas = clustering (não-supervisionado). Prever performance = supervisionado. São problemas distintos que requerem abordagens diferentes.

❌ **A)** Agrupar sem categorias NÃO é supervisionado — é clustering.
❌ **C)** Clustering agrupa mas não prevê performance.
❌ **D)** Reforço é para decisões sequenciais — não se aplica a nenhum dos dois problemas.
</details>

---

### 6.
Um modelo de detecção de fraude tem: Precisão = 98%, Recall = 40%. O que isso significa na prática?

A) O modelo detecta quase todas as fraudes
B) Quando o modelo diz "fraude", quase sempre está certo, mas deixa 60% das fraudes reais passarem despercebidas
C) O modelo tem alta acurácia geral
D) O modelo está com underfitting

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ Precisão 98% = quando diz "fraude", acerta 98%. Recall 40% = só detecta 40% das fraudes reais. 60% das fraudes passam despercebidas — perigoso para fraude financeira.

❌ **A)** Recall 40% = detecta MENOS da metade — longe de "quase todas".
❌ **C)** Acurácia não é mencionada e pode ser alta mesmo com recall baixo em dados desbalanceados.
❌ **D)** O modelo funciona bem quando diz "fraude" (precisão alta) — não é underfitting.
</details>

---

### 7.
Uma equipe está usando Amazon SageMaker Autopilot. Qual é a PRINCIPAL vantagem sobre construir modelos manualmente no SageMaker Studio?

A) Autopilot é gratuito
B) Autopilot testa automaticamente múltiplos algoritmos e configurações, gerando o melhor modelo sem escolher algoritmos manualmente
C) Autopilot só funciona com dados de imagem
D) Autopilot não requer dados de entrada

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ Autopilot = AutoML. Testa múltiplos algoritmos, faz feature engineering e tuning automaticamente. Gera leaderboard com melhor modelo. Mínimo esforço do usuário.

❌ **A)** Autopilot não é gratuito — cobra pelo compute usado.
❌ **C)** Autopilot funciona com dados tabulares, não imagem especificamente.
❌ **D)** Precisa de dados — você fornece o dataset tabular.
</details>

---

### 8.
Qual é a diferença entre Amazon Kendra e Amazon Athena para buscar informações?

A) Ambos são idênticos
B) Kendra entende perguntas em linguagem natural e busca semanticamente em documentos; Athena executa queries SQL estruturadas em dados no S3
C) Athena entende linguagem natural; Kendra requer SQL
D) Kendra é para imagens; Athena é para texto

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ Kendra = busca NLP (linguagem natural em documentos, semântica). Athena = SQL analítico (queries estruturadas em dados no S3). Propósitos completamente diferentes.

❌ **A)** São serviços fundamentalmente diferentes.
❌ **C)** Invertido — Kendra é linguagem natural, Athena é SQL.
❌ **D)** Kendra é para documentos de texto, não imagens.
</details>

---

### 9.
Uma empresa quer monitorar se seu modelo em produção mantém a qualidade e alertar automaticamente quando a performance degradar. Quais serviços combinados atendem?

A) CloudTrail + IAM
B) SageMaker Model Monitor + CloudWatch Alarms
C) SageMaker Clarify + S3
D) Bedrock Guardrails + Lambda

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ Model Monitor detecta degradação (drift de dados e modelo) + CloudWatch Alarms envia alertas quando métricas ultrapassam limites. Monitoramento + notificação automática.

❌ **A)** CloudTrail = auditoria de API calls. IAM = permissões. Nenhum monitora qualidade de modelo.
❌ **C)** Clarify = viés/explicabilidade. S3 = armazenamento. Não monitoram produção continuamente.
❌ **D)** Guardrails = filtro de conteúdo GenAI. Não monitora modelos de ML.
</details>

---

### 10.
Uma empresa treina um modelo com regularização L2 muito forte (lambda = 100). O modelo apresenta erro alto tanto no treino quanto no teste. Qual é a causa?

A) Overfitting devido à regularização
B) Underfitting — a regularização excessiva simplificou demais o modelo
C) Data drift
D) O modelo é perfeito

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ Regularização excessiva = penaliza DEMAIS a complexidade = modelo fica simples demais = underfitting (erro alto em ambos os conjuntos).

❌ **A)** Regularização COMBATE overfitting — não causa. Se fosse overfitting, treino estaria bom.
❌ **C)** Data drift é problema de produção, não de treinamento.
❌ **D)** Erro alto em ambos ≠ perfeito.
</details>

---

### 11.
Uma empresa quer analisar 100.000 avaliações de clientes para identificar temas mais discutidos (sem categorias predefinidas) E classificar cada avaliação como positiva/negativa. Qual serviço AWS resolve AMBAS as necessidades com menor esforço?

A) Amazon Comprehend (topic modeling + sentiment analysis)
B) Amazon Translate + Amazon Lex
C) Amazon Textract + Amazon Polly
D) Amazon Rekognition + Amazon Personalize

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: A**

✅ Comprehend faz topic modeling (descobre temas sem categorias) E sentiment analysis (positivo/negativo) — resolve ambos com um único serviço gerenciado.

❌ **B)** Translate = tradução. Lex = chatbot. Nenhum faz topic modeling ou sentimento.
❌ **C)** Textract = extrair texto de docs. Polly = text-to-speech. Irrelevantes.
❌ **D)** Rekognition = imagens. Personalize = recomendações. Irrelevantes.
</details>

---

### 12.
Uma empresa quer criar chatbots conversacionais com reconhecimento de intenção e extração de slots (nome, data, número de pedido). Qual serviço AWS é projetado para isso?

A) Amazon Comprehend
B) Amazon Lex
C) Amazon Polly
D) Amazon Bedrock

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ Lex = chatbots com NLU (Natural Language Understanding): reconhecimento de intenção + extração de slots. Projetado especificamente para interfaces conversacionais.

❌ **A)** Comprehend analisa texto (sentimento, entidades) mas não é chatbot.
❌ **C)** Polly = text-to-speech. Não conversa nem extrai intenções.
❌ **D)** Bedrock é plataforma de FMs — pode-se construir chatbot mas Lex é o serviço dedicado para NLU tradicional.
</details>


---

### 13.
Uma empresa quer usar IA generativa mas está preocupada com o custo de pré-treinamento de um Foundation Model do zero. Qual abordagem permite usar IA generativa SEM o custo de pré-treinamento?

A) Pré-treinar um modelo próprio na AWS
B) Acessar modelos já pré-treinados via Amazon Bedrock (paga apenas pela inferência)
C) Usar apenas ML tradicional
D) Treinar do zero em SageMaker

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ Bedrock = acesso a FMs já pré-treinados via API. Sem custo de pré-treinamento (bilhões de $). Paga apenas tokens de inferência.

❌ **A)** Pré-treinar do zero = exatamente o que quer evitar (custo altíssimo).
❌ **C)** ML tradicional não resolve se a necessidade é GenAI.
❌ **D)** Treinar do zero em SageMaker = mesmo problema de custo.
</details>

---

### 14.
Uma empresa está avaliando dois modelos. O Modelo A tem context window de 8K tokens e custa $0.01/1K tokens. O Modelo B tem context window de 200K tokens e custa $0.05/1K tokens. A aplicação precisa processar documentos de 50+ páginas (~80K tokens). Qual modelo deve ser escolhido?

A) Modelo A porque é mais barato
B) Modelo B porque o documento excede a context window do Modelo A, tornando-o inutilizável
C) Qualquer um funciona
D) Nenhum — documentos longos não podem ser processados por LLMs

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ 80K tokens > 8K (context window do A). Modelo A literalmente não pode processar o documento. Modelo B (200K) pode. Custo maior mas é a ÚNICA opção funcional.

❌ **A)** Mais barato mas impossível de usar — 8K não suporta 80K tokens.
❌ **C)** Modelo A não funciona para esse caso. Não são intercambiáveis.
❌ **D)** LLMs modernos com context windows grandes processam documentos longos.
</details>

---

### 15.
Qual afirmação sobre modelos "decoder-only" (GPT, Claude, Llama) está CORRETA?

A) Processam toda a entrada de uma vez mas geram saída token por token (autoregressive)
B) Geram toda a saída de uma vez em paralelo
C) Só funcionam para tradução
D) Não usam mecanismo de attention

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: A**

✅ Decoder-only: entrada processada em paralelo (attention), saída gerada sequencialmente (token por token, cada token depende dos anteriores = autoregressive).

❌ **B)** Saída é sequencial (token por token), não paralela.
❌ **C)** Tradução é encoder-decoder (T5). Decoder-only gera texto geral.
❌ **D)** Transformers TODOS usam attention — é o mecanismo central.
</details>

---

### 16.
Uma empresa usa um LLM para gerar conteúdo criativo de marketing. As respostas estão muito repetitivas e previsíveis. Qual ajuste resolve?

A) Reduzir temperature para 0
B) Aumentar temperature (ex: 0.8-1.0) para mais diversidade e criatividade
C) Reduzir max_tokens
D) Aumentar context window

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ "Repetitivo e previsível" = temperature muito baixa. Aumentar temperature = mais aleatoriedade = mais diversidade e criatividade.

❌ **A)** Temperature 0 = MAIS previsível e repetitivo. Piora o problema.
❌ **C)** Max tokens controla comprimento, não criatividade.
❌ **D)** Context window é propriedade fixa do modelo — não é ajustável por request.
</details>

---

### 17.
Uma empresa implementou um chatbot com system prompt restritivo. Mas o modelo frequentemente ignora e gera respostas inventadas. Qual PRÓXIMA medida é mais eficaz?

A) Aumentar temperature
B) Implementar RAG + Bedrock Guardrails com grounding check
C) Fazer fine-tuning para o modelo aprender a dizer "não sei"
D) Usar um modelo menor

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ System prompt sozinho pode ser contornado. RAG fornece contexto factual + Guardrails grounding check bloqueia quando a resposta não está fundamentada. Dupla proteção robusta.

❌ **A)** Temperature alta = mais aleatoriedade = mais alucinações. Piora.
❌ **C)** Fine-tuning pode ajudar mas é caro e não garante. RAG + Guardrails é mais imediato e robusto.
❌ **D)** Modelo menor pode ser MENOS capaz de seguir instruções.
</details>

---

### 18.
Qual é a vantagem de usar prompt templates em produção versus prompts ad-hoc?

A) Templates são mais criativos
B) Templates garantem consistência, são reutilizáveis e permitem injetar variáveis dinamicamente
C) Templates são obrigatórios no Bedrock
D) Templates custam menos tokens

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ Templates = consistência (mesma estrutura) + reutilizáveis (DRY) + variáveis dinâmicas ({contexto}, {pergunta}). Essencial para aplicações em escala.

❌ **A)** Criatividade vem da temperature, não do template.
❌ **C)** Templates não são obrigatórios — são best practice.
❌ **D)** Templates podem usar mais tokens (instruções fixas + variáveis) — mas ganham em qualidade.
</details>

---

### 19.
Uma empresa quer que seu chatbot responda em português brasileiro, com tom informal e limite de 3 frases. Onde configurar?

A) No fine-tuning
B) No system prompt
C) Na context window
D) No vector database

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ System prompt = define comportamento geral (idioma, tom, formato, limites). É o lugar correto para regras de interação.

❌ **A)** Fine-tuning é para mudanças profundas — system prompt resolve instruções de formato.
❌ **C)** Context window é capacidade do modelo, não configuração de comportamento.
❌ **D)** Vector database armazena embeddings para RAG — não configura tom.
</details>

---

### 20.
Qual é a relação entre tokens de saída, custo e latência em um LLM?

A) Tokens de saída não afetam custo nem latência
B) Mais tokens de saída = mais custo E mais latência (geração sequencial token por token)
C) Tokens de entrada são mais caros que de saída
D) Latência é fixa independente do número de tokens

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ Saída é gerada sequencialmente (token por token) = mais tokens = mais tempo (latência) E mais custo (cobra por token). Saída geralmente custa mais por token que entrada.

❌ **A)** Tokens de saída afetam AMBOS significativamente.
❌ **C)** Geralmente invertido — saída é mais cara que entrada por token.
❌ **D)** Latência é proporcional aos tokens gerados (sequencial).
</details>

---

### 21.
Uma empresa tem um FM que confunde termos técnicos de mineração. PE não resolve. Qual abordagem resolve MAIS profundamente?

A) Few-shot com exemplos de termos
B) RAG com glossário de termos
C) Continued pre-training com milhões de tokens de textos técnicos de mineração
D) Guardrails

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: C**

✅ "Confunde termos" = não ENTENDE o domínio nos pesos. Continued pre-training treina com grandes volumes do domínio, ensinando vocabulário e relações no nível mais profundo.

❌ **A)** Few-shot é temporário (context window) — não permanente.
❌ **B)** RAG traz info mas se o modelo confunde os termos nos chunks, interpreta errado.
❌ **D)** Guardrails filtra output — não ensina terminologia.
</details>

---

### 22.
Qual NÃO é uma capacidade do Amazon Bedrock?

A) Acessar Foundation Models de múltiplos provedores via API
B) Criar Knowledge Bases para RAG
C) Treinar modelos de ML tabular (classificação, regressão) do zero
D) Configurar Guardrails para filtrar conteúdo

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: C**

✅ Bedrock é para GenAI (Foundation Models). ML tabular do zero é SageMaker (Autopilot, Canvas, Studio).

❌ **A)** Bedrock oferece Claude, Titan, Llama, Mistral, etc. via API — é capacidade core.
❌ **B)** Knowledge Bases é funcionalidade nativa do Bedrock.
❌ **D)** Guardrails é funcionalidade nativa do Bedrock.
</details>

---

### 23.
Uma empresa avalia Bedrock vs Q Business para chatbot corporativo. Precisa: respeitar permissões existentes, integrar Confluence/SharePoint, funcionar out-of-the-box. Qual atende TODOS com menor esforço?

A) Amazon Bedrock com Knowledge Bases customizadas
B) Amazon Q Business
C) Amazon Kendra
D) PartyRock

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ Q Business = permissões nativas + conectores Confluence/SharePoint + GenAI + out-of-the-box. Atende tudo com menor esforço de implementação.

❌ **A)** Bedrock KB requer implementar controle de permissões manualmente — mais esforço.
❌ **C)** Kendra é busca (retorna trechos), não gera respostas elaboradas com GenAI.
❌ **D)** PartyRock é playground — não é para produção empresarial.
</details>

---

### 24.
CTO quer demonstrar GenAI para o board em 1 semana. Protótipo funcional, sem equipe de ML, investimento mínimo. Caminho MAIS realista?

A) Treinar um LLM do zero no SageMaker
B) Usar Amazon Bedrock para construir um protótipo com API calls a um FM existente
C) Contratar equipe de 5 cientistas de dados
D) Fazer fine-tuning extensivo

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ "1 semana" + "sem equipe de ML" + "investimento mínimo" = Bedrock com API calls a FM existente. Protótipo funcional rapidamente.

❌ **A)** Treinar do zero = meses + milhões de $ — impossível em 1 semana.
❌ **C)** Contratar equipe = meses de processo seletivo.
❌ **D)** Fine-tuning extensivo = semanas + precisa de dados + equipe técnica.
</details>

---

### 25.
O que é "multi-head attention" em um Transformer?

A) Múltiplas cabeças de atenção em paralelo, cada uma capturando diferentes tipos de relações
B) O modelo processa múltiplos documentos simultaneamente
C) O modelo tem múltiplas saídas
D) O modelo usa múltiplas GPUs

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: A**

✅ Multi-head = múltiplas "perspectivas" de attention rodando em paralelo. Uma head pode focar em relações sintáticas, outra em semânticas. Resultado mais rico.

❌ **B)** Não é sobre múltiplos documentos — é sobre múltiplas perspectivas sobre o MESMO input.
❌ **C)** Saída é única — as heads são internas ao processamento.
❌ **D)** GPUs são hardware — multi-head é arquitetura do modelo.
</details>

---

### 26.
Qual garantia de privacidade diferencia o Bedrock de usar LLMs via APIs de terceiros diretamente?

A) Bedrock é mais barato
B) No Bedrock, dados permanecem na sua conta/região AWS e NÃO treinam modelos. Controle via IAM, KMS e VPC Endpoints
C) Bedrock não armazena nada
D) Não há diferença

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ Bedrock = dados na sua conta AWS + não treinam modelos + controle de segurança (IAM, KMS, VPC). APIs de terceiros podem ter políticas menos transparentes sobre uso de dados.

❌ **A)** Custo não é garantia de privacidade.
❌ **C)** Bedrock pode armazenar logs se habilitado (opt-in). A garantia é que NÃO treina.
❌ **D)** Há diferenças significativas de controle e transparência.
</details>

---

### 27.
Qual modelo de imagem no Bedrock oferece watermarking automático para rastreabilidade?

A) Stable Diffusion
B) Amazon Titan Image Generator
C) Claude
D) Llama

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ Titan Image Generator tem watermarking invisível built-in — marca gerada automaticamente para identificar imagens criadas por IA. Diferencial de rastreabilidade da AWS.

❌ **A)** Stable Diffusion não tem watermarking nativo.
❌ **C)** Claude é modelo de texto (e multimodal para ENTENDER imagens, não gerar).
❌ **D)** Llama é modelo de texto.
</details>

---

### 28.
RAG implementado com Knowledge Bases. Chatbot responde corretamente para perguntas cobertas pelos docs. Para perguntas FORA do escopo, inventa respostas. Qual combinação resolve?

A) Adicionar mais documentos
B) Guardrails com grounding check + instrução no prompt para dizer "não tenho essa informação"
C) Aumentar temperature
D) Fine-tuning

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ Guardrails grounding check detecta quando resposta não está fundamentada no contexto + prompt instrui comportamento adequado para esses casos. Dupla proteção.

❌ **A)** Mais docs não resolve o problema de perguntas fora de QUALQUER escopo.
❌ **C)** Temperature alta piora alucinações.
❌ **D)** Fine-tuning não previne alucinações confiávelmente.
</details>

---

### 29.
Chunks de 2000 tokens para perguntas muito específicas estão gerando respostas com informação irrelevante misturada. Qual ajuste melhora?

A) Aumentar chunks para 5000 tokens
B) Reduzir chunks (ex: 300-500 tokens) para retornar trechos mais focados
C) Usar modelo maior
D) Aumentar temperature

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ Chunks grandes = contexto diluído. Perguntas específicas precisam de trechos focados. Chunks menores retornam a informação exata pedida sem ruído.

❌ **A)** Chunks maiores = MAIS informação irrelevante no contexto. Piora.
❌ **C)** Se o contexto errado chega ao FM, modelo maior não resolve.
❌ **D)** Temperature não afeta a qualidade da retrieval.
</details>

---

### 30.
Banco precisa que assistente virtual: responda sobre produtos (docs) E permita bloqueio de cartão (ação via API). Arquitetura mínima no Bedrock?

A) Apenas Knowledge Bases
B) Apenas Fine-tuning
C) Bedrock Agent com Knowledge Base + Action Group (Lambda para API)
D) Apenas Guardrails

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: C**

✅ Docs = KB (RAG). Bloquear cartão = ação em sistema = Action Group com Lambda. Agent orquestra ambos: raciocina, decide se buscar info ou executar ação.

❌ **A)** KB só busca informação — não bloqueia cartões.
❌ **B)** Fine-tuning não dá capacidade de chamar APIs.
❌ **D)** Guardrails filtra — não responde perguntas nem executa ações.
</details>

---

### 31.
Empresa quer reduzir latência. 80% das perguntas dos clientes são repetidas (mesmas 50 perguntas). Qual estratégia MAIS reduz latência?

A) Usar modelo maior
B) Cache de respostas para perguntas frequentes + modelo menor para perguntas simples
C) Aumentar max_tokens
D) Adicionar mais documentos ao RAG

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ 80% repetidas = cache elimina 80% das chamadas ao modelo (latência ~0 para cache hit). Modelo menor para os 20% restantes = resposta mais rápida. Impacto combinado enorme.

❌ **A)** Modelo maior = MAIS lento (mais parâmetros para processar).
❌ **C)** Max tokens maior = MAIS latência (gera mais tokens sequencialmente).
❌ **D)** Mais docs pode tornar retrieval mais lento, não mais rápido.
</details>

---

### 32.
Diferença entre "fine-tuning" e "continued pre-training" no Bedrock?

A) São a mesma coisa
B) Fine-tuning usa pares input/output para ajustar comportamento; continued pre-training usa grandes volumes de texto para ensinar conhecimento novo
C) Fine-tuning é gratuito; continued pre-training é pago
D) Continued pre-training é mais rápido

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ Fine-tuning = dados estruturados (input→output) para mudar COMO o modelo se comporta. Continued pre-training = texto corrido para ensinar O QUE o modelo sabe. Objetivos e formatos diferentes.

❌ **A)** Propósitos e dados completamente diferentes.
❌ **C)** Ambos são pagos (compute de treinamento).
❌ **D)** Continued pre-training é geralmente MAIS demorado (mais dados).
</details>

---

### 33.
Empresa precisa avaliar se respostas são factuais, úteis e no tom certo. Métricas automáticas (ROUGE) não capturam nuances. Qual abordagem?

A) Apenas BLEU
B) Avaliação humana (human evaluation)
C) Apenas perplexidade
D) Apenas AUC-ROC

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ Factualidade, utilidade e tom = qualidade subjetiva que métricas automáticas não medem. Avaliação humana captura nuances que ROUGE/BLEU perdem.

❌ **A)** BLEU é para tradução — mesmo problema de não capturar nuances subjetivas.
❌ **C)** Perplexidade mede o language model, não utilidade ou tom.
❌ **D)** AUC-ROC é para classificação, não geração de texto.
</details>

---

### 34.
10 requests/minuto ao Bedrock. Volume baixo. Qual modelo de pricing é adequado?

A) Provisioned Throughput
B) On-demand (paga por token usado)
C) Reserva anual
D) Batch inference

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ Volume baixo e variável = on-demand (paga apenas o que usa). PT seria desperdício de capacidade reservada para 10 req/min.

❌ **A)** PT faz sentido para milhares de req/hora — overkill para 10/min.
❌ **C)** Não existe "reserva anual" como modelo de pricing no Bedrock.
❌ **D)** Batch é para processamento em lote offline — não para requests de usuários.
</details>

---

### 35.
Agent com 3 action groups (estoque, criar pedido, devolução). Cliente pergunta "Quanto custa o produto X?". O Agent deve:

A) Executar as 3 ações em sequência
B) Raciocinar que precisa consultar estoque/preço, executar apenas essa ação, e retornar a resposta
C) Gerar resposta inventada sem usar nenhuma ação
D) Pedir ao cliente para reformular

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ Agent raciocina (ReAct): pergunta sobre preço → preciso consultar → apenas "consultar estoque" é relevante → executa → retorna preço. Não executa ações desnecessárias.

❌ **A)** Executar tudo é ineficiente e incorreto — criar pedido e devolução não fazem sentido aqui.
❌ **C)** Inventar preço = alucinação. Agent deve SEMPRE usar suas ferramentas quando disponíveis.
❌ **D)** A pergunta é clara — não precisa reformular.
</details>

---

### 36.
Benefício de OpenSearch Serverless como vector database vs banco relacional para RAG?

A) OpenSearch é mais barato para dados tabulares
B) OpenSearch é otimizado para busca por similaridade vetorial (nearest neighbors), fundamental para RAG
C) Bancos relacionais são melhores para busca semântica
D) Não há diferença

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ OpenSearch = otimizado para k-nearest neighbors em vetores (indexação vetorial, busca ANN). Bancos relacionais não têm indexação vetorial eficiente — performance de busca semântica incomparável.

❌ **A)** OpenSearch não é para dados tabulares — é para busca (texto e vetores).
❌ **C)** Invertido — OpenSearch é melhor para busca semântica que bancos relacionais.
❌ **D)** Há diferença enorme de performance e adequação.
</details>

---

### 37.
Empresa quer limitar quais modelos do Bedrock certas equipes podem usar. Onde configurar?

A) Guardrails
B) IAM policies com condições específicas para modelos permitidos
C) System prompt
D) Vector database

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ "Quais modelos cada equipe pode usar" = controle de acesso = IAM policies com condição em bedrock:ModelId. Segurança, não conteúdo.

❌ **A)** Guardrails filtra CONTEÚDO de outputs — não controla ACESSO a modelos.
❌ **C)** System prompt instrui o modelo — não limita acesso.
❌ **D)** Vector database armazena embeddings — irrelevante para controle de acesso.
</details>

---

### 38.
"Bedrock Model Access" — qual afirmação está CORRETA?

A) Todos os modelos estão disponíveis automaticamente
B) Antes de usar um modelo, a conta deve solicitar acesso (model access request), adicionando governança
C) Model access é gerenciado pelo provedor, não pela AWS
D) Model access é configurado via system prompt

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ Model Access = camada adicional de governança. Conta deve explicitamente solicitar acesso a cada modelo antes de poder usá-lo. Previne uso acidental.

❌ **A)** Modelos NÃO estão disponíveis automaticamente — acesso deve ser solicitado.
❌ **C)** É gerenciado pela AWS no console do Bedrock (o cliente solicita).
❌ **D)** System prompt instrui o modelo — não controla acesso a ele.
</details>

---

### 39.
Empresa quer assistente de código integrado ao IDE com menor esforço de integração. Qual serviço?

A) Amazon Bedrock com Claude via API customizada
B) Amazon Q Developer (integrado nativamente a IDEs)
C) Amazon SageMaker com modelo de código customizado
D) Amazon Lex

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ Q Developer = nativo em IDEs (VS Code, IntelliJ, etc.). Zero esforço de integração — instala a extensão e funciona.

❌ **A)** Bedrock via API requer construir toda a integração com o IDE — mais esforço.
❌ **C)** SageMaker modelo customizado = construir e integrar tudo do zero.
❌ **D)** Lex é chatbot conversacional — não é assistente de código.
</details>

---

### 40.
Em RAG, se o modelo de embeddings para indexar docs é DIFERENTE do modelo para a query, o que acontece?

A) Nenhum problema
B) A busca será ineficaz pois os vetores estão em espaços diferentes e não são comparáveis
C) O sistema gera erro automático
D) Os resultados serão melhores por diversidade

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ Modelos de embedding diferentes = espaços vetoriais diferentes. Comparar vetores de espaços distintos é como comparar metros com milhas — semanticamente sem sentido. Busca retorna resultados irrelevantes.

❌ **A)** É um problema grave — busca não funciona.
❌ **C)** Não gera erro técnico — apenas retorna resultados ruins (falha silenciosa).
❌ **D)** Diversidade não ajuda se os vetores não são comparáveis.
</details>

---

### 41.
RAG + Guardrails implementados. Para perguntas não cobertas, grounding check bloqueia. Mensagem de bloqueio é genérica. Como melhorar UX?

A) Desabilitar grounding check
B) Configurar mensagem customizada no Guardrails
C) Aumentar temperature
D) Fine-tuning

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ Guardrails permite configurar mensagem customizada quando bloqueia (ex: "Não encontrei essa informação. Posso ajudar com outra coisa?"). Melhor UX sem reduzir proteção.

❌ **A)** Desabilitar = permitir alucinações — piora a situação.
❌ **C)** Temperature não afeta o comportamento do Guardrails.
❌ **D)** Fine-tuning não controla mensagens de bloqueio do Guardrails.
</details>

---

### 42.
Docs bem estruturados com seções claras (manuais técnicos, FAQs). Qual estratégia de chunking é melhor?

A) Chunking fixo (500 tokens independente do conteúdo)
B) Chunking semântico (dividir por seções/parágrafos do documento)
C) Sem chunking (documento inteiro como um chunk)
D) Chunking por caractere

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ Docs estruturados com seções claras → chunking semântico preserva contexto natural. Cada seção = um chunk com significado completo. Evita cortar no meio de uma explicação.

❌ **A)** Fixo pode cortar no meio de uma seção, perdendo contexto.
❌ **C)** Doc inteiro = chunk gigante = diluição de contexto na retrieval.
❌ **D)** Por caractere é muito granular e perde significado.
</details>

---

### 43.
1 milhão de requests/dia no Bedrock. Quer REDUZIR custos sem perder qualidade. Combinação com MAIOR impacto?

A) Aumentar temperature + modelo maior
B) Cache de respostas frequentes + modelo menor para tarefas simples + prompts concisos
C) Fine-tuning + Provisioned Throughput
D) Adicionar mais action groups

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ Cache (elimina chamadas repetidas) + modelo menor (custo por token) + prompts concisos (menos tokens por chamada) = impacto combinado alto em 1M req/dia.

❌ **A)** Temperature + modelo maior = piora criatividade e custo. Oposto do desejado.
❌ **C)** Fine-tuning não reduz custo de inferência. PT pode ser mais caro se volume não justifica.
❌ **D)** Action groups são funcionalidade, não otimização de custo.
</details>

---

### 44.
Vantagem de batch inference vs on-demand no Bedrock?

A) Respostas em tempo real
B) Custo reduzido para processamento que não requer resposta imediata
C) Maior qualidade de respostas
D) Menor quantidade de tokens

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ Batch = desconto sobre on-demand (~50% cheaper) em troca de não ter resposta imediata. Ideal para processamento em massa offline.

❌ **A)** Batch NÃO é real-time — é o trade-off.
❌ **C)** Mesma qualidade (mesmo modelo) — a diferença é timing e preço.
❌ **D)** Mesma quantidade de tokens — processados em lote em vez de um por vez.
</details>

---

### 45.
Empresa de seguros usa ML para calcular prêmios. Regulador exige demonstrar que não discrimina por etnia, gênero ou idade. Processo COMPLETO?

A) Apenas monitorar acurácia geral
B) SageMaker Clarify (bias pre/post-training) + monitorar fairness em produção + documentar em Model Cards
C) Apenas remover variáveis demográficas
D) Apenas usar Guardrails

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ Processo completo: (1) Clarify detecta bias antes/depois do treino, (2) Model Monitor monitora fairness em produção contínua, (3) Model Cards documentam resultados para auditoria.

❌ **A)** Acurácia geral mascara disparidades entre subgrupos.
❌ **C)** Remover variáveis não resolve — proxies existem (CEP → raça, estado civil → gênero).
❌ **D)** Guardrails é para GenAI conteúdo — não para bias em modelos de pricing.
</details>

---

### 46.
Modelo de extração acerta 95%. Empresa quer enviar para revisão humana APENAS os 5% de baixa confiança. Configuração?

A) Enviar 100% para revisão
B) Configurar threshold de confiança no A2I — apenas confiança < X% vai para revisão
C) Remover A2I
D) Apenas Guardrails

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ A2I com threshold = apenas baixa confiança vai para humanos. 95% processados automaticamente, 5% revisados. Balança custo (poucos revisores) × qualidade (erros caros são revisados).

❌ **A)** 100% = caro e desnecessário para os 95% corretos.
❌ **C)** Remover = nenhuma revisão = erros caros passam despercebidos.
❌ **D)** Guardrails filtra conteúdo GenAI — não gerencia revisão de extração de docs.
</details>

---

### 47.
Regulador pede os 3 fatores que MAIS contribuíram para negar empréstimo a um cliente. Qual output atende?

A) Feature importance global
B) SHAP values da previsão individual
C) AUC-ROC do modelo
D) Métricas de bias

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ SHAP individual = contribuição de cada feature para AQUELA decisão específica. Ex: "renda -40%, dívida -35%, histórico -25%". Explicação per-client.

❌ **A)** Global mostra importância média — não explica decisão individual.
❌ **C)** AUC-ROC mede performance geral — não explica decisões.
❌ **D)** Bias metrics mostram fairness entre grupos — não explicam decisão individual.
</details>

---

### 48.
Diferença entre Guardrails "content filter" e "contextual grounding"?

A) São a mesma coisa
B) Content filter bloqueia por TIPO de conteúdo (violência, sexual); contextual grounding verifica se resposta está FUNDAMENTADA no contexto (detecta alucinações)
C) Contextual grounding é para imagens
D) Content filter é mais importante

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ Content filter = categorias (hate, violence, sexual, insults). Contextual grounding = verifica fidelidade ao contexto fornecido (alucinação). Propósitos complementares.

❌ **A)** Funcionalidades diferentes com triggers diferentes.
❌ **C)** Contextual grounding é para texto, não imagens.
❌ **D)** Ambos são importantes — depende do caso de uso.
</details>

---

### 49.
Chatbot não deve discutir finanças. System prompt diz isso mas usuários contornam com prompts criativos. Solução ROBUSTA?

A) Melhorar system prompt
B) Bedrock Guardrails com denied topics para temas financeiros
C) Fine-tuning para desaprender sobre finanças
D) Reduzir temperature

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ Guardrails denied topics = camada de proteção INDEPENDENTE do prompt. Aplicado no input E output. Não pode ser burlado por prompt injection.

❌ **A)** System prompt mais elaborado ainda pode ser contornado por prompt injection criativo.
❌ **C)** Fine-tuning não "desaprende" confiávelmente e pode degradar capacidades gerais.
❌ **D)** Temperature não afeta se o modelo responde ou não sobre temas específicos.
</details>

---

### 50.
Importância de red teaming ANTES do deploy?

A) Reduzir custos
B) Identificar proativamente falhas, vulnerabilidades e outputs perigosos que testes normais não encontram
C) Melhorar velocidade
D) Documentar o modelo

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ Red teaming = encontrar falhas que testes "happy path" não revelam. Inputs adversariais, edge cases, viés oculto, prompt injection. Essencial ANTES de expor a usuários reais.

❌ **A)** Red teaming tem CUSTO (equipe dedicada) — não reduz custos operacionais.
❌ **C)** Não é sobre velocidade de inferência.
❌ **D)** Documentação é Model Cards — red teaming é teste adversarial.
</details>

---

### 51.
Dados sensíveis em logs de inferência do Bedrock. Não pode desabilitar logging (auditoria exigida). Como proteger?

A) Não habilitar logging
B) Model Invocation Logging com destino criptografado (KMS) + IAM restritivo
C) S3 público para transparência
D) Apenas CloudTrail

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ Logging necessário (auditoria) + proteger PII = criptografar destino (KMS) + restringir quem acessa (IAM). Atende ambos os requisitos.

❌ **A)** Viola requisito de auditoria.
❌ **C)** Dados sensíveis em bucket público = vazamento de dados. Inaceitável.
❌ **D)** CloudTrail registra que API foi chamada, NÃO o conteúdo (prompts/respostas). Insuficiente.
</details>

---

### 52.
Organização com múltiplas contas quer forçar VPC Endpoints para Bedrock em TODAS as contas. Mecanismo?

A) IAM policies em cada conta
B) Service Control Policies (SCPs) com condição de VPC endpoint
C) Security Groups
D) Bedrock Guardrails

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ SCPs = política organizacional aplicada uniformemente. Condição: negar bedrock:* se não vier de VPC endpoint. Garante compliance em todas as contas sem configurar individualmente.

❌ **A)** IAM conta por conta não escala e pode ser burlado por admins locais.
❌ **C)** Security Groups controlam tráfego de instâncias — não forçam uso de VPC endpoint.
❌ **D)** Guardrails filtra conteúdo — não controla rota de rede.
</details>

---

### 53.
Empresa precisa de relatórios SOC 2, ISO 27001 e PCI DSS da infraestrutura AWS. Onde encontrar?

A) AWS CloudTrail
B) AWS Artifact
C) AWS Config
D) Amazon Inspector

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ Artifact = portal self-service de compliance reports da AWS (SOC, ISO, PCI, HIPAA, etc.). Download de relatórios prontos.

❌ **A)** CloudTrail = seus logs de API calls — não relatórios de compliance da AWS.
❌ **C)** Config = compliance de configuração dos SEUS recursos — não da infraestrutura AWS.
❌ **D)** Inspector = vulnerabilidades em suas instâncias — não relatórios de compliance da AWS.
</details>

---

### 54.
Equipe fez deploy de modelo há 2 semanas. Quer saber quais dados, transformações e hiperparâmetros foram usados. Qual funcionalidade?

A) CloudWatch Logs
B) SageMaker ML Lineage Tracking
C) CloudTrail
D) S3 versioning

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ Lineage Tracking = rastreia toda a cadeia: dados de origem → transformações → hiperparâmetros → job de treino → modelo → endpoint. Responde "de onde veio esse modelo?".

❌ **A)** CloudWatch tem logs de execução, mas não o grafo completo de origem.
❌ **C)** CloudTrail mostra quem CRIOU o endpoint — não os dados/configs usados.
❌ **D)** S3 versioning versiona objetos — não rastreia relações entre dados e modelos.
</details>

---

### 55.
Role "MLEngineer" pode criar endpoints em produção. Role "DataScientist" pode apenas treinar. Qual recurso implementa?

A) Security Groups
B) IAM policies com permissões específicas por role
C) KMS key policies
D) VPC NACLs

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ IAM policies: MLEngineer → sagemaker:CreateEndpoint permitido. DataScientist → sagemaker:CreateTrainingJob permitido, CreateEndpoint negado. Least privilege por role.

❌ **A)** Security Groups = firewall de rede — não controla permissões de API.
❌ **C)** KMS policies controlam quem usa chaves de criptografia — não permissões de SageMaker.
❌ **D)** NACLs = firewall de subnet — não controla permissões de serviço.
</details>

---

### 56.
Diferença entre SageMaker Model Monitor e SageMaker Clarify em produção?

A) São idênticos
B) Model Monitor detecta drift de dados/performance; Clarify detecta drift de viés/fairness e fornece explicabilidade
C) Clarify é para desenvolvimento; Model Monitor é para produção
D) Model Monitor é gratuito; Clarify é pago

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ Model Monitor = "o modelo está piorando?" (data quality, model quality). Clarify = "o modelo está sendo justo?" (bias drift, fairness metrics) + explicabilidade. Complementares.

❌ **A)** Propósitos diferentes — um monitora qualidade, outro monitora fairness.
❌ **C)** Ambos podem ser usados em produção (monitoramento contínuo).
❌ **D)** Ambos têm custo associado.
</details>

---

### 57.
Empresa precisa para auditoria: quem acessou, quando, de qual IP, com quais parâmetros. Qual serviço fornece TUDO?

A) Amazon CloudWatch
B) AWS CloudTrail
C) SageMaker Model Monitor
D) Amazon Macie

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ CloudTrail registra: identidade (quem) + timestamp (quando) + source IP (de onde) + request parameters (com quais parâmetros). Tudo em um log de auditoria.

❌ **A)** CloudWatch = métricas operacionais e logs de aplicação — não auditoria completa de API.
❌ **C)** Model Monitor = qualidade do modelo — não auditoria de acesso.
❌ **D)** Macie = detectar PII no S3 — não auditoria de chamadas.
</details>

---

### 58.
Diferença entre criptografia em repouso e em trânsito?

A) São a mesma coisa
B) Em repouso protege dados armazenados (S3, EBS) com KMS; em trânsito protege dados sendo transferidos (rede) com TLS/HTTPS
C) Em repouso é para modelos; em trânsito é para dados
D) Apenas uma é necessária

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ Em repouso = dados parados no disco/storage (KMS criptografa). Em trânsito = dados movendo na rede (TLS/HTTPS criptografa). Ambos necessários para proteção completa.

❌ **A)** Protegem dados em ESTADOS diferentes — complementares.
❌ **C)** Ambos se aplicam a dados E modelos — não são separados assim.
❌ **D)** Ambos são necessários — um sem o outro deixa vulnerabilidades.
</details>

---

### 59. (Múltipla Resposta)
Governança completa de modelos ML: versionamento, aprovação e automação de pipeline. Quais funcionalidades? **(Selecione DUAS)**

A) SageMaker Model Registry (versionamento + aprovação)
B) SageMaker Canvas
C) SageMaker Pipelines (automação do pipeline)
D) SageMaker Autopilot
E) SageMaker JumpStart

<details>
<summary>🔍 Ver resposta</summary>

**Respostas: A e C**

✅ **A)** Model Registry = versionar modelos + workflow de aprovação (Pending → Approved → Deployed).
✅ **C)** Pipelines = CI/CD para ML (automatizar processamento → treino → avaliação → registro → deploy).

❌ **B)** Canvas = ML sem código (criação, não governança).
❌ **D)** Autopilot = AutoML automático (criação, não governança).
❌ **E)** JumpStart = modelos pré-treinados prontos (uso, não governança).
</details>

---

### 60.
No modelo de responsabilidade compartilhada para IA, qual é responsabilidade do CLIENTE?

A) Segurança física dos data centers
B) Patching do SO das instâncias gerenciadas
C) Garantir que dados de treino não contenham viés discriminatório e avaliar modelos por fairness
D) Manutenção da rede global AWS

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: C**

✅ Responsabilidade compartilhada: AWS cuida da infraestrutura. CLIENTE cuida de COMO usa — dados (viés), modelos (fairness), segurança da aplicação, configuração correta.

❌ **A)** Data centers = responsabilidade da AWS (segurança da infraestrutura).
❌ **B)** Instâncias GERENCIADAS = AWS faz patching (se for serverless/managed).
❌ **D)** Rede global = responsabilidade da AWS.
</details>

---

## Resultado

Conte suas respostas corretas:
- **54-60 (90%+):** Excelente — muito provavelmente aprovado
- **48-53 (80-89%):** Bom — confortavelmente acima do threshold
- **42-47 (70-79%):** Na borda — revise os domínios com mais erros
- **<42 (<70%):** Precisa de mais estudo — foque nos domínios fracos

**Compare erros entre Simulado 1 e 2. Padrões repetidos = seus gaps prioritários.**
