# Simulado Final 1 — AWS Certified AI Practitioner (AIF-C01)

**60 questões | 90 minutos | Aprovação: 700/1000**

Distribuição por domínio (proporcional à prova real):
- Domínio 1 (Fundamentos de IA e ML): 12 questões
- Domínio 2 (Fundamentos de IA Generativa): 15 questões
- Domínio 3 (Aplicações de Foundation Models): 17 questões
- Domínio 4 (IA Responsável): 8 questões
- Domínio 5 (Segurança, Conformidade e Governança): 8 questões

**Instruções:** Responda cada questão antes de expandir a resposta. Cronometre 90 minutos para simular a prova real.

---

## Questões

### 1.
Uma seguradora quer usar Machine Learning para determinar se sinistros reportados são fraudulentos ou legítimos. A empresa possui um banco de dados com milhares de sinistros já avaliados por analistas humanos. Qual abordagem de ML requer o MENOR esforço para implementar essa solução?

A) Treinar um modelo de clustering para agrupar sinistros por similaridade e inferir fraude
B) Treinar um modelo de classificação supervisionada usando o histórico rotulado
C) Implementar aprendizado por reforço onde um agente aprende a detectar padrões de fraude
D) Usar aprendizado não-supervisionado para encontrar anomalias nos dados de sinistros

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ Dados rotulados disponíveis + classificar binário (fraude/legítimo) = classificação supervisionada. É a abordagem mais direta.

❌ **A)** Clustering não prevê classes — apenas agrupa. Não usa os rótulos existentes.
❌ **C)** Reforço é para decisões sequenciais com recompensa — overkill e complexo para este cenário.
❌ **D)** Anomalia funcionaria mas ignora os rótulos disponíveis. Supervisionado com rótulos é mais preciso e simples.
</details>

---

### 2.
Uma equipe de ciência de dados treinou um modelo de previsão de demanda. O modelo atinge RMSE de 12 no conjunto de treino e RMSE de 45 no conjunto de teste. A equipe aumentou a quantidade de dados de treino em 50%, mas o problema persiste. Qual é a ação MAIS provável para resolver o problema?

A) Coletar ainda mais dados de treino
B) Aplicar regularização ou reduzir a complexidade do modelo
C) Usar um modelo mais complexo com mais parâmetros
D) Remover o conjunto de validação para dar mais dados ao treino

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ Gap grande treino (12) vs teste (45) = overfitting. Mais dados não resolveu → regularizar ou simplificar o modelo para generalizar melhor.

❌ **A)** Já tentaram mais dados e não resolveu — o problema é complexidade, não volume.
❌ **C)** Mais complexidade = mais overfitting. Piora o problema.
❌ **D)** Remover validação impede de detectar overfitting e ajustar hiperparâmetros.
</details>

---

### 3.
Uma empresa de call center quer transcrever automaticamente as gravações de atendimento e depois analisar o sentimento dos clientes durante a ligação. Quais serviços AWS devem ser usados NESSA ORDEM?

A) Amazon Polly → Amazon Comprehend
B) Amazon Transcribe → Amazon Comprehend
C) Amazon Lex → Amazon Translate
D) Amazon Comprehend → Amazon Transcribe

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ Transcribe (áudio→texto) DEPOIS Comprehend (análise de sentimento do texto). A ordem importa — primeiro converter, depois analisar.

❌ **A)** Polly faz o inverso (texto→áudio). Não transcreve.
❌ **C)** Lex é chatbot, Translate é tradução. Nenhum faz transcrição nem sentimento.
❌ **D)** Ordem invertida — Comprehend não processa áudio, precisa do texto primeiro.
</details>

---

### 4.
Uma rede varejista precisa prever a demanda de 5.000 produtos em 200 lojas para os próximos 3 meses usando dados históricos de vendas diárias. A equipe de negócios não tem experiência em ML e quer uma solução gerenciada. Qual serviço é MAIS adequado?

A) Amazon SageMaker Autopilot para criar modelos customizados de regressão
B) Amazon Personalize para gerar recomendações de estoque
C) Amazon Forecast para previsão gerenciada de séries temporais
D) Amazon Bedrock para gerar previsões com um LLM

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: C**

✅ Forecast = gerenciado + séries temporais + sem expertise ML necessária. Projetado exatamente para previsão de demanda.

❌ **A)** Autopilot requer mais conhecimento técnico e não é otimizado para séries temporais.
❌ **B)** Personalize é para recomendação de itens a usuários, não previsão de demanda.
❌ **D)** Bedrock/LLMs não são para previsão tabular de séries temporais.
</details>

---

### 5.
Um modelo de regressão apresenta erro alto tanto nos dados de treino quanto nos de teste, mesmo após múltiplas iterações de treinamento. A equipe suspeita de underfitting. Qual combinação de ações é MAIS provável de resolver o problema?

A) Adicionar regularização L2 e reduzir o learning rate
B) Usar um modelo mais complexo e adicionar features relevantes
C) Aplicar early stopping e aumentar o dropout
D) Coletar mais dados e aumentar a regularização

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ Underfitting = modelo simples demais. Solução: mais capacidade (modelo complexo) + features melhores (mais informação).

❌ **A)** Regularização combate overfitting — aqui o modelo já é simples demais.
❌ **C)** Early stopping e dropout combatem overfitting (reduzem capacidade). Piora underfitting.
❌ **D)** Mais regularização piora underfitting. Mais dados ajuda pouco se o modelo não tem capacidade.
</details>

---

### 6.
Uma empresa de saúde está construindo um modelo para detectar uma condição rara que afeta 0.3% da população. O modelo atual tem 99.7% de acurácia. A equipe médica reporta que o modelo não está detectando pacientes doentes. Qual é a causa mais provável e a métrica que deveria ser monitorada?

A) O modelo está com overfitting; monitorar a loss function
B) O modelo está prevendo sempre "saudável" devido ao desbalanceamento; monitorar o recall da classe positiva
C) O modelo está com underfitting; monitorar a acurácia do treino
D) Os dados de treino contêm viés; monitorar SHAP values

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ 99.7% acurácia com 99.7% de classe negativa = modelo prevê tudo como "saudável" e acerta pela maioria. Recall da classe positiva (doentes) seria ~0%.

❌ **A)** Overfitting causaria gap treino/teste, não acurácia inflada por desbalanceamento.
❌ **C)** Underfitting teria baixa acurácia em ambos os conjuntos.
❌ **D)** Viés é possível, mas a causa direta aqui é desbalanceamento + métrica inadequada.
</details>

---

### 7.
Em um pipeline de ML, uma equipe decide usar 70% dos dados para treino, 15% para validação e 15% para teste. Qual afirmação sobre o uso desses conjuntos está CORRETA?

A) O conjunto de teste é usado para ajustar hiperparâmetros durante o desenvolvimento
B) O conjunto de validação é usado uma única vez ao final para medir performance real
C) O conjunto de validação é usado durante o desenvolvimento para ajustar hiperparâmetros, e o conjunto de teste é reservado para avaliação final
D) O conjunto de treino e validação devem ser combinados para o treinamento final

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: C**

✅ Validação = ajustar hiperparâmetros durante desenvolvimento (usado múltiplas vezes). Teste = avaliação final imparcial (usado UMA vez no final).

❌ **A)** Invertido — teste é reservado para o final, não para ajustar hiperparâmetros.
❌ **B)** Invertido — validação é usado durante desenvolvimento, não uma única vez.
❌ **D)** Combinar comprometeria a capacidade de ajustar hiperparâmetros separadamente.
</details>

---

### 8.
Uma equipe de ML está decidindo entre dois modelos para detecção de fraude em cartão de crédito. O Modelo A tem recall de 95% e precisão de 60%. O Modelo B tem recall de 70% e precisão de 95%. Considerando que fraudes não detectadas causam perdas financeiras significativas, qual modelo escolher e por quê?

A) Modelo B, porque a alta precisão significa menos investigações desnecessárias
B) Modelo A, porque recall alto garante que quase todas as fraudes reais são detectadas
C) Qualquer um, pois ambos têm performance similar
D) Nenhum — é necessário otimizar a acurácia primeiro

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ "Fraudes não detectadas = perdas significativas" → custo de FN é alto → priorizar recall. Modelo A detecta 95% das fraudes (vs 70% do B).

❌ **A)** Precisão alta reduz falsos positivos, mas deixa 30% das fraudes passarem — inaceitável dado o custo.
❌ **C)** 95% vs 70% de recall é uma diferença enorme em fraude financeira.
❌ **D)** Acurácia é enganosa em dados desbalanceados (fraude é rara).
</details>

---

### 9.
Um analista de negócios sem experiência em programação precisa construir um modelo para prever churn de clientes usando dados tabulares de CRM. A empresa quer a solução com o MENOR esforço técnico possível. Qual combinação de serviço e abordagem é mais adequada?

A) Amazon SageMaker Studio com notebooks Jupyter e XGBoost
B) Amazon Bedrock com um Foundation Model para analisar os dados
C) Amazon SageMaker Canvas com interface visual drag-and-drop
D) AWS Glue DataBrew para preparação seguido de Amazon Comprehend

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: C**

✅ "Sem programação" + "menor esforço" + "dados tabulares" = Canvas (visual, no-code, drag-and-drop). Feito para analistas de negócio.

❌ **A)** Studio com notebooks requer Python e conhecimento de ML.
❌ **B)** Bedrock/FMs são para GenAI, não para previsão tabular de churn.
❌ **D)** DataBrew prepara dados mas Comprehend é NLP — não faz previsão de churn tabular.
</details>


---

### 10.
Uma empresa de e-commerce quer prever o valor total de compras que cada cliente fará no próximo trimestre E segmentar clientes em grupos de comportamento similar. Quais DOIS tipos de tarefa de ML são necessários?

A) Classificação e Detecção de Anomalias
B) Regressão e Clustering
C) Regressão e Classificação
D) Clustering e Recomendação

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ Prever valor (número) = regressão. Agrupar sem categorias predefinidas = clustering. São problemas distintos que requerem abordagens diferentes.

❌ **A)** Classificação prevê categorias, não valores. Anomalia detecta outliers.
❌ **C)** Segmentar sem categorias predefinidas é clustering, não classificação.
❌ **D)** Recomendação sugere itens — não prevê valor de compras.
</details>

---

### 11.
Uma equipe implantou um modelo de classificação de emails há 6 meses. O modelo apresentava 94% de F1 Score no deploy. Agora o F1 caiu para 78%, mas nenhum código foi alterado. Uma análise mostra que novos tipos de spam surgiram que não existiam nos dados de treino. Qual tipo de drift está ocorrendo?

A) Data drift — a distribuição dos inputs mudou
B) Concept drift — a relação entre inputs e labels mudou
C) Model drift causado por degradação de hardware
D) Feature drift — as features estão sendo calculadas incorretamente

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ Novos tipos de spam = o QUE é spam mudou (relação input→label). Antes "promoção de crypto" não era spam, agora é. Isso é concept drift.

❌ **A)** Data drift é quando a distribuição dos inputs muda. Aqui o CONCEITO de spam é que mudou.
❌ **C)** Hardware não causa degradação de métricas de classificação.
❌ **D)** Features calculadas incorretamente causaria erro imediato, não gradual.
</details>

---

### 12.
Uma empresa precisa extrair informações estruturadas (nome do cliente, valor, data de vencimento) de milhares de faturas em PDF. Após extrair, quer classificar as faturas por urgência. Quais serviços, em ordem, atendem a esse pipeline?

A) Amazon Rekognition → Amazon Comprehend
B) Amazon Textract → Amazon Comprehend (custom classification)
C) Amazon Comprehend → Amazon Textract
D) Amazon Kendra → Amazon Lex

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ Textract extrai dados estruturados de PDFs (formulários, tabelas) → Comprehend classifica o texto extraído por categoria. Ordem correta.

❌ **A)** Rekognition é para objetos/faces em imagens, não extração de dados de documentos.
❌ **C)** Ordem invertida — Comprehend não lê PDFs diretamente.
❌ **D)** Kendra é busca; Lex é chatbot. Nenhum extrai dados de faturas.
</details>

---

### 13.
Uma empresa quer construir um chatbot que responde perguntas sobre produtos usando um Large Language Model. O LLM gera respostas fluentes mas ocasionalmente inventa especificações técnicas que não existem. Qual afirmação MELHOR descreve esse comportamento e a solução recomendada?

A) O modelo está com underfitting; a solução é treinar com mais dados de produtos
B) O modelo está alucinando; a solução é implementar RAG para ancorar respostas em documentação real
C) O modelo precisa de temperature mais alta para gerar respostas mais precisas
D) O modelo precisa de fine-tuning para aprender todas as especificações

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ "Inventa especificações" = alucinação clássica. RAG busca dados reais dos produtos e injeta como contexto, forçando respostas fundamentadas.

❌ **A)** Underfitting teria respostas genéricas/ruins, não "fluentes mas inventadas".
❌ **C)** Temperature alta PIORA alucinações (mais aleatoriedade).
❌ **D)** Fine-tuning não garante factualidade — modelo pode memorizar MAS também inventar sobre produtos novos.
</details>

---

### 14.
Um arquiteto está avaliando diferentes Foundation Models para uma aplicação. O modelo precisa processar documentos que contêm tanto texto quanto imagens (diagramas técnicos) para responder perguntas. Qual capacidade do modelo é ESSENCIAL?

A) Alta context window
B) Capacidade multimodal (processar texto e imagem)
C) Suporte a fine-tuning
D) Baixo custo por token

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ Processar texto + imagem juntos = multimodal é ESSENCIAL. Sem isso, o modelo literalmente não "vê" os diagramas.

❌ **A)** Context window grande ajuda, mas se o modelo não processa imagens, não resolve.
❌ **C)** Fine-tuning é opcional — multimodal é o requisito funcional.
❌ **D)** Custo é importante mas secundário — sem multimodal, o custo é irrelevante.
</details>

---

### 15.
Uma empresa está decidindo entre usar um modelo decoder-only (como Claude) e um modelo encoder-only (como BERT) para seu caso de uso. Qual cenário é MAIS adequado para um modelo encoder-only?

A) Gerar respostas longas para perguntas de clientes
B) Classificar tickets de suporte em categorias predefinidas
C) Criar resumos de documentos
D) Manter conversas multi-turno com clientes

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ Encoder-only (BERT) = compreensão de texto. Classificar tickets é tarefa de compreensão (entender o texto e atribuir categoria).

❌ **A)** Gerar respostas longas = geração de texto = decoder-only.
❌ **C)** Resumos = geração = decoder-only ou encoder-decoder.
❌ **D)** Conversação multi-turno = geração contínua = decoder-only.
</details>

---

### 16.
Uma empresa precisa que seu LLM gere SEMPRE a mesma resposta para perguntas factuais idênticas (como "Qual é a política de devolução?"), garantindo consistência no atendimento. Qual configuração de inferência atende esse requisito?

A) Temperature = 1.0 e top-p = 0.95 para máxima qualidade
B) Temperature = 0 para respostas determinísticas
C) Max tokens = 1000 para respostas completas
D) Top-k = 100 para considerar mais opções

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ Temperature 0 = sempre escolhe o token mais provável = mesma resposta para mesmo input = determinístico e consistente.

❌ **A)** Temperature 1.0 = variação a cada geração — inconsistente.
❌ **C)** Max tokens controla comprimento, não consistência.
❌ **D)** Top-k alto = mais opções = mais variação — oposto de consistência.
</details>

---

### 17.
Uma empresa está comparando custos de usar um LLM. A aplicação envia prompts longos (3.000 tokens em média) mas espera respostas curtas (100 tokens). Qual fator de custo será DOMINANTE e como otimizar?

A) Tokens de saída dominam; reduzir max_tokens
B) Tokens de entrada dominam; reduzir o tamanho do prompt
C) Ambos custam igual; não há otimização possível
D) O custo é fixo por request independente de tokens

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ 3000 tokens entrada vs 100 saída. Mesmo que saída custe mais por token, o volume de entrada (30x maior) domina o custo total. Otimizar = prompts mais concisos.

❌ **A)** Saída já é curta (100 tokens) — pouco a otimizar ali.
❌ **C)** Custos são diferentes por tipo e volume — otimização é possível.
❌ **D)** Bedrock cobra por token, não por request.
</details>

---

### 18.
Um desenvolvedor precisa que o LLM resolva o seguinte problema: "Uma loja vende 3 tipos de produto. Produto A custa R$10 com 20% de desconto. Produto B custa R$25 sem desconto. O cliente comprou 2 do A e 1 do B. Calcule o total." Qual técnica de prompt MAIS aumenta a chance de resposta correta?

A) Zero-shot direto
B) Few-shot com exemplos de outros cálculos
C) Chain-of-thought pedindo raciocínio passo a passo
D) Aumentar temperature para explorar mais possibilidades

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: C**

✅ Problema multi-step com cálculos → chain-of-thought decompõe em etapas. Estudos mostram melhora significativa em raciocínio aritmético com CoT.

❌ **A)** Zero-shot pode pular etapas em problemas com múltiplos cálculos.
❌ **B)** Few-shot ajuda no formato, mas CoT é mais eficaz para raciocínio matemático.
❌ **D)** Temperature alta = mais aleatoriedade = mais chance de erro em cálculos.
</details>

---

### 19.
Qual afirmação sobre embeddings está CORRETA?

A) Embeddings são representações vetoriais onde textos semanticamente similares ficam próximos no espaço vetorial
B) Embeddings são usados exclusivamente para tradução automática
C) Embeddings convertem vetores em texto legível
D) Embeddings funcionam apenas com idioma inglês

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: A**

✅ Embeddings = vetores numéricos onde proximidade = similaridade semântica. "Cachorro" e "cão" ficam próximos. Base do RAG e busca semântica.

❌ **B)** Embeddings são usados para RAG, busca semântica, clustering — não apenas tradução.
❌ **C)** Invertido — embeddings convertem TEXTO em vetores (não vetores em texto).
❌ **D)** Embeddings funcionam com qualquer idioma (multilíngues disponíveis).
</details>

---

### 20.
Uma empresa usa Amazon Bedrock e quer testar qual Foundation Model (Claude, Titan ou Llama) gera as melhores respostas para perguntas de suporte técnico. A empresa tem 500 pares de pergunta/resposta-esperada. Qual funcionalidade do Bedrock é MAIS adequada?

A) Bedrock Knowledge Bases com os 3 modelos
B) Bedrock Model Evaluation com dataset customizado
C) Bedrock Agents testando cada modelo
D) Fine-tuning dos 3 modelos e comparação manual

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ "Comparar modelos" + "dataset de avaliação" = Model Evaluation. Suporta métricas automáticas + humanas com seu dataset.

❌ **A)** Knowledge Bases é para RAG, não para comparar modelos.
❌ **C)** Agents executam ações — não são ferramenta de avaliação.
❌ **D)** Fine-tuning dos 3 seria caro e desnecessário para apenas avaliar.
</details>


---

### 21.
Uma empresa quer que seu chatbot funcione em português, mas tem mais dados de treinamento em inglês. O modelo responde melhor em inglês. Qual afirmação sobre tokens e idiomas é CORRETA?

A) Todos os idiomas usam o mesmo número de tokens para conteúdo equivalente
B) Português geralmente requer mais tokens que inglês para o mesmo conteúdo, aumentando custo e usando mais context window
C) O idioma não afeta a tokenização
D) Modelos não podem processar português

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ Tokenizadores foram otimizados para inglês. Português usa subwords diferentes → mais tokens para mesmo conteúdo → mais custo e mais context window consumida.

❌ **A)** Idiomas diferentes produzem quantidades diferentes de tokens.
❌ **C)** Idioma afeta diretamente a tokenização (subwords variam por língua).
❌ **D)** Modelos modernos são multilíngues — processam português.
</details>

---

### 22.
Uma empresa quer um chatbot empresarial que responda perguntas usando documentos internos do SharePoint e Confluence, respeitando as permissões de acesso existentes (cada funcionário só vê documentos que tem permissão). Qual serviço AWS atende TODOS esses requisitos?

A) Amazon Bedrock com Knowledge Bases
B) Amazon Q Business
C) Amazon Kendra
D) PartyRock

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ Q Business = assistente GenAI + integração nativa com SharePoint/Confluence + respeita permissões de acesso existentes automaticamente. Atende TODOS os requisitos.

❌ **A)** Bedrock KB suporta RAG mas não respeita permissões de acesso automaticamente — requer implementação custom.
❌ **C)** Kendra é busca (retorna trechos), não assistente GenAI que gera respostas elaboradas.
❌ **D)** PartyRock é playground sem integração empresarial.
</details>

---

### 23.
Uma empresa está decidindo entre usar Amazon Bedrock (API) versus hospedar um modelo open-weight (Llama) no SageMaker. Qual cenário justifica MELHOR a hospedagem própria no SageMaker?

A) A empresa quer o menor esforço operacional possível
B) A empresa precisa de controle total sobre a infraestrutura e customizações profundas no modelo
C) A empresa quer acesso a múltiplos provedores de modelos
D) A empresa quer escalar automaticamente sem gerenciar servidores

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ "Controle total" + "customizações profundas" = SageMaker (você gerencia tudo). Bedrock é para quem quer serverless com menor esforço.

❌ **A)** Menor esforço = Bedrock (serverless, gerenciado).
❌ **C)** Múltiplos provedores = Bedrock (oferece Claude, Titan, Llama, Mistral, etc.).
❌ **D)** Auto-scaling sem gerenciar = Bedrock (serverless).
</details>

---

### 24.
Uma equipe de inovação quer demonstrar rapidamente o valor de IA generativa para a diretoria, criando um protótipo funcional de chatbot em menos de 1 hora, sem código e sem custo. Qual ferramenta é MAIS adequada?

A) Amazon Bedrock com Claude
B) Amazon SageMaker JumpStart
C) PartyRock
D) Amazon Q Developer

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: C**

✅ "1 hora" + "sem código" + "sem custo" = PartyRock (playground gratuito, visual, sem conta AWS).

❌ **A)** Bedrock tem custo e requer conta AWS + código.
❌ **B)** JumpStart requer conta AWS + conhecimento de SageMaker.
❌ **D)** Q Developer é assistente de código, não ferramenta de prototipagem sem código.
</details>

---

### 25.
Qual processo no treinamento de LLMs modernos usa feedback humano para ensinar o modelo a ser mais útil, inofensivo e honesto, APÓS o pré-treinamento inicial?

A) Self-supervised pre-training
B) RLHF (Reinforcement Learning from Human Feedback)
C) Transfer Learning
D) Continued Pre-training

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ RLHF = pós pré-treinamento, usa feedback humano para alinhar o modelo (útil, seguro, honesto). É reinforcement learning guiado por preferências humanas.

❌ **A)** Self-supervised é o pré-treinamento inicial (prever próximo token), não alinhamento.
❌ **C)** Transfer learning reaproveita conhecimento entre tarefas — conceito geral.
❌ **D)** Continued pre-training ensina conhecimento novo, não alinha com preferências.
</details>

---

### 26.
Uma empresa testou prompt engineering para gerar emails de vendas. As respostas são corretas mas o tom é inconsistente — às vezes formal demais, às vezes casual. O prompt já inclui instruções detalhadas de tom. Qual é o PRÓXIMO passo recomendado?

A) Implementar RAG com exemplos de emails anteriores
B) Fine-tuning com centenas de exemplos de emails no tom desejado
C) Aumentar a temperature para mais variação
D) Trocar o Foundation Model por um menor

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ PE tentado com instruções detalhadas + tom inconsistente = próximo passo é fine-tuning para internalizar o estilo. Ajusta os pesos para esse comportamento.

❌ **A)** RAG traz informação factual, não muda estilo de escrita.
❌ **C)** Mais temperature = mais variação = mais inconsistência. Piora.
❌ **D)** Modelo menor geralmente é MENOS capaz de seguir instruções de tom.
</details>

---

### 27.
Um desenvolvedor está usando Amazon Q Developer no IDE. Qual das seguintes NÃO é uma capacidade do serviço?

A) Gerar código a partir de comentários em linguagem natural
B) Explicar código legado complexo
C) Treinar modelos customizados de ML
D) Sugerir correções de bugs e vulnerabilidades

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: C**

✅ Q Developer gera, explica e corrige código. NÃO treina modelos de ML — isso é SageMaker.

❌ **A)** Q Developer gera código a partir de linguagem natural — capacidade core.
❌ **B)** Explicar código legado é uma funcionalidade do Q Developer.
❌ **D)** Sugerir correções de bugs e vulnerabilidades é uma funcionalidade do Q Developer.
</details>

---

### 28.
Uma empresa implementou RAG com Bedrock Knowledge Bases. Os documentos fonte são manuais técnicos atualizados trimestralmente. A equipe quer que as respostas do chatbot reflitam SEMPRE a versão mais recente. Qual ação é necessária quando os manuais são atualizados?

A) Re-treinar (fine-tuning) o Foundation Model com os novos manuais
B) Sincronizar/re-indexar os documentos na Knowledge Base
C) Alterar o system prompt para mencionar a nova versão
D) Trocar o Foundation Model por uma versão mais recente

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ RAG = re-indexar quando docs mudam. O FM não precisa ser alterado — a informação atualizada vem da base de documentos.

❌ **A)** Fine-tuning não é necessário — RAG é justamente a alternativa a re-treinar.
❌ **C)** System prompt não conhece o conteúdo dos manuais — não resolve.
❌ **D)** O FM não precisa mudar — é a base de documentos que precisa ser atualizada.
</details>

---

### 29.
Uma equipe está projetando uma arquitetura RAG. Os documentos são manuais técnicos de 200+ páginas. As perguntas dos usuários são específicas (ex: "Qual é a pressão máxima da válvula X?"). A equipe está obtendo respostas irrelevantes. Qual ajuste na pipeline de RAG MAIS provavelmente resolve o problema?

A) Usar um Foundation Model maior
B) Reduzir o tamanho dos chunks e melhorar o modelo de embeddings
C) Aumentar a temperature do FM
D) Adicionar mais documentos à base

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ Perguntas específicas + respostas irrelevantes = chunks muito grandes (contexto diluído) ou embeddings ruins (busca imprecisa). Chunks menores + embeddings melhores = retrieval mais preciso.

❌ **A)** Se o contexto errado chega ao FM, modelo maior não ajuda.
❌ **C)** Temperature afeta geração, não qualidade da busca.
❌ **D)** Mais documentos pode piorar se o problema é na precisão da busca.
</details>

---

### 30.
Um chatbot de suporte precisa: (1) responder perguntas sobre produtos usando documentação e (2) criar tickets no sistema JIRA quando o cliente pede. Qual arquitetura Bedrock é MÍNIMA necessária?

A) Apenas Knowledge Bases
B) Apenas Guardrails
C) Agent com Knowledge Base (para docs) + Action Group (para criar tickets)
D) Apenas Fine-tuning

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: C**

✅ Perguntas sobre docs = KB (RAG). Criar tickets = ação em sistema externo = Action Group (Lambda). Agent orquestra ambos.

❌ **A)** KB só busca informação — não cria tickets.
❌ **B)** Guardrails filtra conteúdo — não responde perguntas nem cria tickets.
❌ **D)** Fine-tuning muda estilo — não dá capacidade de interagir com JIRA.
</details>

---

### 31.
Uma empresa já tem RAG funcionando bem para perguntas sobre docs. Agora quer que o chatbot TAMBÉM processe devoluções consultando a API de pedidos e atualizando o status. O que ADICIONAR à arquitetura?

A) Mais documentos na Knowledge Base
B) Fine-tuning do modelo
C) Bedrock Agent com Action Groups que chamam a API de pedidos
D) Guardrails mais restritivos

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: C**

✅ RAG funciona para leitura (Q&A). Para AÇÕES (consultar + atualizar) precisa de Agent com Action Groups. É uma adição ao que já existe.

❌ **A)** Mais docs não dá capacidade de executar ações.
❌ **B)** Fine-tuning não dá capacidade de chamar APIs.
❌ **D)** Guardrails restringem, não adicionam funcionalidades.
</details>

---

### 32.
Uma empresa precisa gerar resumos de 500.000 contratos legais armazenados no S3. Não há urgência — o resultado pode levar dias. O custo deve ser minimizado. Qual abordagem no Bedrock é MAIS econômica?

A) Invocar o modelo via API on-demand para cada contrato sequencialmente
B) Usar batch inference para processar todos os contratos em lote
C) Configurar Provisioned Throughput e processar em tempo real
D) Fine-tuning de um modelo específico para contratos legais

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ "Sem urgência" + "minimizar custo" + volume alto = batch inference (processamento em lote com desconto ~50% vs on-demand).

❌ **A)** On-demand sequencial = preço cheio + lento.
❌ **C)** Provisioned Throughput = capacidade reservada (caro para processamento único).
❌ **D)** Fine-tuning é para mudar comportamento, não para reduzir custo de processamento.
</details>

---

### 33.
Qual afirmação sobre ROUGE e BLEU está CORRETA?

A) ROUGE é usada para avaliar tradução; BLEU é usada para avaliar resumos
B) ROUGE mede recall de n-grams (orientada a resumos); BLEU mede precisão de n-grams (orientada a tradução)
C) Ambas medem exatamente a mesma coisa
D) ROUGE e BLEU são métricas de classificação

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ ROUGE = Recall-Oriented (quanto do referência aparece no gerado) → resumos. BLEU = Precision-Oriented (quanto do gerado está correto) → tradução.

❌ **A)** Invertido — ROUGE é resumos, BLEU é tradução.
❌ **C)** Medem coisas diferentes (recall vs precision de n-grams).
❌ **D)** São métricas de geração de texto, não classificação.
</details>

---

### 34.
Uma empresa quer reduzir custos de inferência para uma tarefa de classificação de sentimento (positivo/negativo/neutro) que atualmente usa um modelo grande. As respostas estão corretas mas o custo é alto. Qual estratégia combina menor custo COM manutenção da qualidade?

A) Trocar para um modelo menor que ainda atinge acurácia aceitável para a tarefa
B) Aumentar temperature para respostas mais curtas
C) Remover o system prompt para economizar tokens
D) Usar Provisioned Throughput com o mesmo modelo grande

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: A**

✅ Tarefa simples (3 classes) → modelo menor é suficiente e muito mais barato por token. Mantém qualidade porque a tarefa não exige modelo grande.

❌ **B)** Temperature não afeta comprimento nem custo diretamente.
❌ **C)** Remover system prompt pode degradar qualidade — economia mínima.
❌ **D)** PT com modelo grande = custo reservado alto. Não resolve o custo por token.
</details>

---

### 35.
Uma empresa quer que seu LLM entenda profundamente jargão e terminologia de engenharia civil que modelos gerais não conhecem bem. Prompt engineering com termos técnicos no system prompt não é suficiente — o modelo confunde termos. Qual abordagem resolve MAIS profundamente esse problema?

A) RAG com normas técnicas de engenharia civil
B) Continued pre-training com grandes volumes de texto de engenharia civil
C) Few-shot com exemplos de termos
D) Aumentar context window

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ "Confunde termos" = não ENTENDE o domínio. Continued pre-training ensina vocabulário novo no nível mais profundo dos pesos. RAG traz info mas se o modelo não entende os termos dos chunks, as respostas continuam ruins.

❌ **A)** RAG traz documentos mas o modelo pode interpretar errado se não entende a terminologia.
❌ **C)** Few-shot é limitado pela context window e não ensina permanentemente.
❌ **D)** Context window é propriedade fixa do modelo — não é configurável.
</details>

---

### 36.
Qual é a PRINCIPAL diferença funcional entre Bedrock Knowledge Bases e Bedrock Agents?

A) Knowledge Bases são mais caras que Agents
B) Knowledge Bases buscam informação para fundamentar respostas; Agents podem buscar informação E executar ações em sistemas externos
C) Agents não podem acessar Knowledge Bases
D) Knowledge Bases requerem fine-tuning; Agents não

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ KB = RAG (busca + resposta fundamentada). Agents = busca + ações (chamam APIs, atualizam sistemas). Agents são um superset que pode usar KBs.

❌ **A)** Custo depende do uso, não é a diferença funcional.
❌ **C)** Agents PODEM (e geralmente USAM) Knowledge Bases como fonte de informação.
❌ **D)** Nenhum dos dois requer fine-tuning obrigatoriamente.
</details>

---

### 37.
Uma empresa está decidindo o modelo de precificação do Bedrock. A aplicação tem tráfego previsível de 10.000 requests/hora durante horário comercial e zero fora. Qual modelo de pricing é MAIS econômico?

A) On-demand (paga por token)
B) Provisioned Throughput (capacidade reservada)
C) Batch inference
D) Free tier

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ Tráfego previsível + alto volume constante = Provisioned Throughput (capacidade reservada por tempo, mais barato que on-demand em volume alto).

❌ **A)** On-demand com 10K req/hora seria muito mais caro que capacidade reservada.
❌ **C)** Batch não é real-time — inadequado para requisições de horário comercial.
❌ **D)** Bedrock não tem free tier significativo para esse volume.
</details>

---

### 38.
Uma empresa quer bloquear o chatbot de responder sobre 3 temas: concorrentes, política e religião. Também quer mascarar qualquer CPF ou email que apareça nas respostas. Qual funcionalidade do Bedrock configura AMBOS os requisitos em um único lugar?

A) Knowledge Bases com filtros
B) Guardrails (denied topics + PII filters)
C) Fine-tuning com exemplos negativos
D) System prompt com instruções

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ Guardrails = denied topics (3 temas bloqueados) + PII filters (CPF/email mascarados). Uma única configuração resolve ambos.

❌ **A)** KB é para RAG, não para filtrar conteúdo.
❌ **C)** Fine-tuning com exemplos negativos não garante bloqueio confiável.
❌ **D)** System prompt pode ser burlado com prompt injection — não é robusto.
</details>

---

### 39.
Uma empresa de e-commerce quer recomendar produtos a usuários usando dados de comportamento (cliques, compras, tempo na página). A empresa NÃO quer construir algoritmos de recomendação do zero. Qual serviço oferece recomendações gerenciadas com o menor esforço?

A) Amazon Bedrock com prompt engineering
B) Amazon Personalize
C) Amazon SageMaker com modelo customizado
D) Amazon Comprehend

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ Personalize = recomendações gerenciadas. Dados de comportamento → treina modelos automaticamente → recomendações personalizadas. Menor esforço.

❌ **A)** Bedrock pode gerar sugestões de texto mas não é sistema de recomendação com aprendizado contínuo.
❌ **C)** SageMaker requer construir tudo do zero — oposto de "menor esforço".
❌ **D)** Comprehend é NLP — não faz recomendações.
</details>

---

### 40.
Em uma arquitetura RAG, o que "cosine similarity" mede quando busca chunks relevantes?

A) O tamanho dos vetores
B) A similaridade direcional (ângulo) entre o vetor da query e os vetores dos chunks
C) A distância física entre servidores
D) O número de tokens em comum

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ Cosine similarity mede o ângulo entre dois vetores — quanto mais alinhados (mesma direção), mais similares semanticamente. Valor de -1 a 1 (1 = idênticos em significado).

❌ **A)** Magnitude/tamanho dos vetores é ignorada — cosine mede direção.
❌ **C)** Não tem relação com infraestrutura física.
❌ **D)** Tokens em comum seria overlap lexical, não similaridade semântica.
</details>

---

### 41.
Uma empresa implementou um Agent que pode consultar o sistema de pedidos e processar devoluções. O Agent está funcionando, mas ocasionalmente executa devoluções para pedidos que não são elegíveis (prazo expirado). Qual camada adicional ajuda a prevenir esse comportamento?

A) Aumentar temperature
B) Adicionar validações na Lambda function do Action Group (verificar elegibilidade antes de executar)
C) Usar um modelo menor
D) Remover a Knowledge Base

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ Validações de negócio (elegibilidade) devem estar na Lambda (Action Group), não no FM. O FM decide a INTENÇÃO, a Lambda valida se é PERMITIDO.

❌ **A)** Temperature afeta geração de texto, não lógica de negócio.
❌ **C)** Modelo menor pode ser menos capaz de raciocinar — não resolve validação.
❌ **D)** Remover KB perde a capacidade de responder perguntas sobre docs.
</details>

---

### 42.
Uma empresa precisa decidir entre Bedrock on-demand e Provisioned Throughput. Qual cenário justifica MELHOR o uso de Provisioned Throughput?

A) Prototipagem com volume baixo e imprevisível
B) Carga constante e previsível onde latência consistente é crítica
C) Processamento único de um grande lote de dados
D) Uso esporádico por poucos usuários internos

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ PT = latência consistente + capacidade garantida + volume constante previsível. Ideal para produção com SLA de latência.

❌ **A)** Volume baixo e imprevisível = on-demand (paga só o que usa).
❌ **C)** Lote único sem urgência = batch inference.
❌ **D)** Uso esporádico = on-demand (PT seria desperdício de capacidade reservada).
</details>

---

### 43.
Qual afirmação sobre fine-tuning no Amazon Bedrock está CORRETA?

A) Fine-tuning altera o modelo base compartilhado com todos os clientes
B) Fine-tuning cria uma cópia privada do modelo ajustada com seus dados, sem afetar o modelo base
C) Fine-tuning não requer nenhum dado — apenas configuração
D) Fine-tuning está disponível para todos os modelos no Bedrock

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ Fine-tuning no Bedrock cria CÓPIA PRIVADA. Não altera o modelo base compartilhado. Seus dados não afetam outros clientes.

❌ **A)** Modelo base é imutável — fine-tuning gera cópia separada.
❌ **C)** Fine-tuning requer dataset de pares input/output.
❌ **D)** Nem todos os modelos suportam fine-tuning no Bedrock.
</details>

---

### 44.
Uma empresa quer que avaliadores humanos internos classifiquem a qualidade das respostas de seu chatbot em escalas de 1-5 para "utilidade" e "factualidade". Qual funcionalidade do Bedrock suporta isso nativamente?

A) Guardrails
B) Model Evaluation (com avaliação humana)
C) Agents
D) Knowledge Bases

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ Model Evaluation suporta avaliação humana com critérios customizados (escalas, métricas subjetivas). Projetado para exatamente esse caso.

❌ **A)** Guardrails filtram conteúdo — não avaliam qualidade.
❌ **C)** Agents executam ações — não são ferramenta de avaliação.
❌ **D)** Knowledge Bases buscam informação — não avaliam qualidade.
</details>

---

### 45.
Um modelo de concessão de crédito está aprovando 90% dos candidatos de uma região urbana rica mas apenas 50% de uma região rural de baixa renda, para candidatos com perfis financeiros similares. Qual PRIMEIRA ação a equipe deve tomar?

A) Remover a variável "região" do modelo e re-treinar
B) Usar SageMaker Clarify para analisar métricas de viés por subgrupo e entender a causa raiz
C) Ignorar, pois a diferença pode ser justificada
D) Aplicar o mesmo threshold de aprovação para todos

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ Primeiro: entender a CAUSA com dados (Clarify analisa viés por subgrupo). Pode haver variáveis proxy. Agir sem diagnóstico pode piorar.

❌ **A)** Remover "região" direto pode não resolver (existem proxies como CEP, renda média da área).
❌ **C)** Ignorar disparidade significativa é irresponsável — precisa investigar.
❌ **D)** Threshold fixo sem análise pode prejudicar grupos já desfavorecidos.
</details>

---

### 46.
Uma empresa de saúde usa IA para pré-triagem de exames de imagem. Quando a confiança do modelo está abaixo de 90%, o caso deve ser encaminhado para revisão por um radiologista. Qual arquitetura implementa esse fluxo?

A) SageMaker Model Monitor
B) Amazon Augmented AI (A2I) com threshold de confiança configurado
C) Bedrock Guardrails
D) SageMaker Clarify

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ A2I = human-in-the-loop com threshold configurável. Confiança < 90% → encaminha para humano. Exatamente o fluxo descrito.

❌ **A)** Model Monitor detecta drift, não encaminha casos para revisão humana.
❌ **C)** Guardrails filtra conteúdo de LLMs, não gerencia revisão de imagens médicas.
❌ **D)** Clarify explica previsões e detecta viés, não implementa fluxo de revisão.
</details>

---

### 47.
Uma regulamentação exige que a empresa explique a clientes POR QUE seus pedidos de empréstimo foram negados, identificando os fatores que mais contribuíram para a decisão. Qual ferramenta AWS fornece essa explicação?

A) Amazon CloudWatch
B) SageMaker Clarify (SHAP values / feature importance)
C) AWS CloudTrail
D) Amazon Bedrock Guardrails

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ SHAP values = contribuição de cada feature para UMA decisão específica. "Renda contribuiu -40%, dívida contribuiu -35%". Explicação individual.

❌ **A)** CloudWatch monitora métricas operacionais — não explica decisões de ML.
❌ **C)** CloudTrail = quem chamou qual API — auditoria, não explicabilidade.
❌ **D)** Guardrails filtra conteúdo de GenAI — não explica modelos de classificação.
</details>

---

### 48.
Uma empresa está usando Bedrock Guardrails com "grounding check" habilitado. O que esse recurso detecta?

A) Quando o modelo está lento
B) Quando o modelo gera informação que NÃO está presente no contexto fornecido (potencial alucinação)
C) Quando o modelo recusa responder
D) Quando o modelo usa linguagem informal

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ Grounding check verifica se a resposta do modelo está fundamentada no contexto fornecido. Se gera algo que não está no contexto = possível alucinação → bloqueia.

❌ **A)** Latência é monitorada por CloudWatch, não Guardrails.
❌ **C)** Recusa não é o que grounding detecta.
❌ **D)** Tom informal seria filtrado por content filter ou system prompt, não grounding.
</details>

---

### 49.
Uma empresa publicou seu modelo de classificação de imagens e quer documentar para a comunidade: para que o modelo foi projetado, suas limitações conhecidas, métricas de fairness por grupo demográfico, e práticas recomendadas de uso. Qual artefato deve criar?

A) Um README no GitHub
B) SageMaker Model Card com documentação estruturada
C) Um endpoint de monitoramento
D) Uma AWS AI Service Card

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ Modelo CUSTOMIZADO do cliente → Model Card (documentação estruturada: uso pretendido, limitações, métricas, fairness).

❌ **A)** README é genérico — Model Card é estruturado e integrado ao SageMaker.
❌ **C)** Endpoint monitora inferência, não documenta o modelo.
❌ **D)** AI Service Cards são da AWS sobre SEUS serviços gerenciados — não sobre modelos do cliente.
</details>

---

### 50.
Um modelo de IA é treinado com dados de currículos de funcionários contratados nos últimos 10 anos. A empresa historicamente contratou predominantemente homens para cargos de engenharia. O modelo agora penaliza candidatas mulheres. Qual tipo de viés E solução são mais relevantes?

A) Viés de medição; usar métricas diferentes
B) Viés histórico; coletar dados mais diversos e aplicar técnicas de debiasing
C) Viés algorítmico; trocar o algoritmo
D) Viés de automação; desativar o modelo

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ Dados refletem discriminação passada = viés histórico. Solução: dados diversos + debiasing (Clarify para detectar, regularização de fairness, dados balanceados).

❌ **A)** Viés de medição é quando a métrica é inadequada — aqui o problema está nos dados.
❌ **C)** Trocar algoritmo não resolve se os dados continuam enviesados.
❌ **D)** Desativar é extremo — é possível mitigar sem eliminar a ferramenta.
</details>

---

### 51.
Qual é a diferença entre AWS AI Service Cards e SageMaker Model Cards?

A) São o mesmo documento
B) AI Service Cards documentam serviços gerenciados da AWS; Model Cards documentam modelos customizados criados pelo cliente
C) Model Cards são públicos; AI Service Cards são privados
D) AI Service Cards são para código; Model Cards para dados

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ AI Service Cards = AWS documenta SEUS serviços (Rekognition, Textract). Model Cards = VOCÊ documenta SEU modelo. Autores e propósitos diferentes.

❌ **A)** São documentos diferentes com autores diferentes.
❌ **C)** Invertido — AI Service Cards são públicas. Model Cards podem ser internas.
❌ **D)** Ambos são sobre modelos/serviços de IA, não sobre código vs dados.
</details>

---

### 52.
"Red teaming" no contexto de IA Responsável significa:

A) Usar equipes vestindo camisetas vermelhas para testar o sistema
B) Testar proativamente o modelo com inputs adversariais para encontrar falhas, viés e vulnerabilidades antes do deploy
C) Treinar o modelo com dados rotulados em vermelho
D) Monitorar métricas em dashboard vermelho

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ Red teaming = teste adversarial proativo. Equipe tenta "quebrar" o modelo com inputs maliciosos, edge cases, e cenários de viés ANTES de expor a usuários.

❌ **A/C/D)** Todas são interpretações literais incorretas de "red" — é uma analogia militar (red team = equipe adversária).
</details>

---

### 53.
Uma empresa tem requisitos regulatórios que exigem: (1) todo acesso ao Bedrock deve ser auditável e (2) o tráfego não pode transitar pela internet pública. Quais DOIS serviços/recursos atendem respectivamente esses requisitos?

A) CloudWatch para auditoria + Security Groups para tráfego
B) CloudTrail para auditoria + VPC Endpoints (PrivateLink) para tráfego privado
C) Macie para auditoria + HTTPS para tráfego
D) Config para auditoria + WAF para tráfego

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ CloudTrail = registra TODAS as API calls (quem, quando, o quê). VPC Endpoints = tráfego fica dentro da rede AWS sem internet pública.

❌ **A)** CloudWatch é métricas/logs operacionais, não auditoria de API calls. Security Groups controlam tráfego mas não garantem rota privada.
❌ **C)** Macie detecta PII no S3, não audita chamadas. HTTPS criptografa mas ainda passa pela internet.
❌ **D)** Config monitora configuração de recursos. WAF protege contra ataques web.
</details>

---

### 54.
Uma empresa quer garantir que apenas a equipe de ML possa invocar endpoints SageMaker, que a equipe de dados possa acessar apenas os buckets S3 de dados, e que ninguém possa acessar as chaves KMS sem aprovação. Qual princípio de segurança está sendo aplicado?

A) Defense in depth
B) Least privilege (menor privilégio) com separação de responsabilidades
C) Zero trust
D) Security through obscurity

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ Cada equipe só tem as permissões que precisa (least privilege) + papéis separados com acessos distintos (separação de responsabilidades). Princípio fundamental de IAM.

❌ **A)** Defense in depth é sobre múltiplas camadas de segurança — relacionado mas não é o conceito principal aqui.
❌ **C)** Zero trust é "nunca confiar, sempre verificar" — conceito mais amplo.
❌ **D)** Security through obscurity = esconder como funciona. Não é prática recomendada.
</details>

---

### 55.
Uma empresa quer que prompts e respostas do Bedrock sejam registrados para auditoria posterior, mas está preocupada que esses logs possam conter dados sensíveis de clientes. Qual combinação de medidas é MAIS adequada?

A) Desabilitar logging completamente
B) Habilitar Model Invocation Logging com acesso restrito (IAM) + criptografia (KMS)
C) Salvar logs em bucket S3 público para transparência
D) Usar apenas CloudTrail que já registra tudo

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ Logging necessário (auditoria) + proteger dados sensíveis = Model Invocation Logging habilitado + destino criptografado (KMS) + IAM restritivo (apenas quem precisa acessa).

❌ **A)** Desabilitar viola o requisito de auditoria.
❌ **C)** S3 público com dados de clientes = vazamento de dados. Absurdo.
❌ **D)** CloudTrail registra que a API foi chamada, mas NÃO o conteúdo (prompts/respostas).
</details>

---

### 56.
Uma equipe quer automatizar o pipeline: quando novos dados chegam ao S3 → processamento automático → re-treinamento → avaliação → se métricas OK → registrar modelo → aprovar → deploy. Qual serviço orquestra todo esse fluxo?

A) AWS Step Functions
B) SageMaker Pipelines
C) Amazon EventBridge
D) AWS CodePipeline

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ SageMaker Pipelines = CI/CD para ML. Orquestra todo o pipeline: processamento → treino → avaliação → registro → aprovação → deploy. Integrado com Model Registry.

❌ **A)** Step Functions é orquestrador genérico — funciona mas não é otimizado para ML.
❌ **C)** EventBridge é event bus (trigger), não orquestrador de pipeline completo.
❌ **D)** CodePipeline é para deploy de aplicações de software, não modelos ML.
</details>

---

### 57.
Uma organização com 50 contas AWS quer garantir que NENHUMA conta possa usar certos Foundation Models no Bedrock considerados de alto risco. Qual mecanismo aplica essa restrição organizacionalmente?

A) IAM policies em cada conta
B) Service Control Policies (SCPs) no AWS Organizations
C) Security Groups
D) Bedrock Guardrails

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ SCPs = restrição organizacional aplicada a TODAS as contas de uma vez. Garante compliance uniforme em 50 contas sem configurar cada uma.

❌ **A)** IAM em cada conta não escala (50 contas × manutenção manual) e pode ser burlado por admins locais.
❌ **C)** Security Groups controlam rede, não acesso a modelos.
❌ **D)** Guardrails filtra conteúdo de outputs — não bloqueia acesso a modelos.
</details>

---

### 58.
O que "ML Lineage Tracking" do SageMaker permite que uma equipe faça quando um modelo em produção apresenta previsões incorretas?

A) Corrigir automaticamente as previsões
B) Rastrear quais dados, transformações e configurações de treino originaram aquele modelo específico
C) Fazer rollback automático do endpoint
D) Alertar o usuário final

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ Lineage = rastrear TODA a origem: quais dados de treino, quais transformações, quais hiperparâmetros, qual job gerou aquele modelo. Essencial para debugging e reprodutibilidade.

❌ **A)** Lineage não corrige previsões — ajuda a entender a causa raiz.
❌ **C)** Rollback é ação manual ou automatizada por Model Monitor, não por Lineage.
❌ **D)** Alertas são do CloudWatch Alarms, não do Lineage.
</details>

---

### 59.
Uma equipe detectou que as previsões de um modelo de recomendação degradaram 15% no último mês. Qual serviço teria detectado isso automaticamente com alertas?

A) AWS CloudTrail
B) SageMaker Model Monitor + CloudWatch Alarms
C) Amazon Inspector
D) AWS Trusted Advisor

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B**

✅ Model Monitor detecta degradação de qualidade (model quality monitoring) + CloudWatch Alarms notifica quando thresholds são violados. Detecção automática.

❌ **A)** CloudTrail audita API calls — não monitora qualidade de previsões.
❌ **C)** Inspector verifica vulnerabilidades de segurança em instâncias.
❌ **D)** Trusted Advisor dá recomendações de custo/segurança de infraestrutura, não de modelos.
</details>

---

### 60. (Múltipla Resposta)
Uma empresa precisa proteger dados de treino de ML em repouso e garantir que chaves de criptografia sejam gerenciadas centralmente. Quais DOIS recursos atendem esses requisitos?

A) VPC Endpoints para tráfego privado
B) AWS KMS para gerenciamento centralizado de chaves
C) TLS para criptografia em trânsito
D) S3 Server-Side Encryption com chaves KMS (SSE-KMS)
E) Security Groups para controle de rede

<details>
<summary>🔍 Ver resposta</summary>

**Respostas: B e D**

✅ **B)** KMS = gerenciamento centralizado de chaves de criptografia (criar, rotacionar, controlar acesso).
✅ **D)** SSE-KMS = criptografia em repouso dos dados no S3 usando chaves do KMS.

❌ **A)** VPC Endpoints = tráfego privado (rede), não criptografia em repouso.
❌ **C)** TLS = criptografia em TRÂNSITO, não em repouso.
❌ **E)** Security Groups = firewall de rede, não criptografia.
</details>

---

## Resultado

Conte suas respostas corretas:
- **54-60 (90%+):** Excelente — muito provavelmente aprovado
- **48-53 (80-89%):** Bom — confortavelmente acima do threshold
- **42-47 (70-79%):** Na borda — revise os domínios com mais erros
- **<42 (<70%):** Precisa de mais estudo — foque nos domínios fracos
