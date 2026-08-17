# Simulado Final 2 — AWS Certified AI Practitioner (AIF-C01)

**60 questões | 90 minutos | Aprovação: 700/1000**

Distribuição por domínio:
- Domínio 1 (Fundamentos de IA e ML): 12 questões
- Domínio 2 (Fundamentos de IA Generativa): 15 questões
- Domínio 3 (Aplicações de Foundation Models): 17 questões
- Domínio 4 (IA Responsável): 8 questões
- Domínio 5 (Segurança, Conformidade e Governança): 8 questões

**Instruções:** Responda todas as questões antes de consultar o gabarito. Cronometre 90 minutos.

---

## Questões

### 1.
Uma fintech quer construir um modelo que aprenda a otimizar a alocação de portfólio em tempo real, ajustando investimentos com base nas respostas do mercado (ganhos ou perdas). O sistema deve aprender continuamente qual estratégia maximiza o retorno. Qual tipo de ML é MAIS adequado?

A) Aprendizado Supervisionado — Regressão  
B) Aprendizado Não-Supervisionado — Clustering  
C) Aprendizado por Reforço  
D) Aprendizado Semi-Supervisionado  

---

### 2.
Uma empresa de telecomunicações tem milhões de registros de comportamento de clientes mas apenas 500 estão rotulados como "churn" ou "ativo" (rotulagem é cara pois requer análise manual). A empresa quer classificar todos os clientes. Qual abordagem MAXIMIZA o uso dos dados disponíveis?

A) Treinar supervisionado apenas com os 500 rotulados  
B) Usar aprendizado semi-supervisionado que aproveita os poucos rótulos + dados não-rotulados  
C) Clustering não-supervisionado ignorando os rótulos existentes  
D) Aprendizado por reforço  

---

### 3.
Um cientista de dados precisa comparar dois modelos de classificação para diagnóstico médico. O Modelo A tem AUC-ROC de 0.92 e o Modelo B tem AUC-ROC de 0.78. O que isso indica sobre a capacidade dos modelos?

A) Modelo A é 14% mais rápido que Modelo B  
B) Modelo A tem melhor capacidade de distinguir entre classes positiva e negativa, independente do threshold  
C) Modelo A usa menos memória  
D) Ambos são equivalentes pois a diferença é pequena  

---

### 4.
Uma empresa tem um modelo de previsão de preços de imóveis em produção. A equipe percebe que o RMSE aumentou 40% em 3 meses. Investigando, descobrem que a cidade teve um boom de imóveis de luxo que não existiam nos dados de treino. Qual ação RESOLVE o problema a longo prazo?

A) Aumentar regularização do modelo atual  
B) Re-treinar o modelo com dados atualizados que incluem os novos imóveis de luxo  
C) Reduzir a complexidade do modelo  
D) Aumentar early stopping  

---

### 5.
Uma empresa de RH quer um sistema que: (1) agrupe candidatos por perfil similar E (2) preveja quais candidatos terão melhor performance no cargo. Qual combinação de abordagens de ML é necessária?

A) Dois modelos supervisionados  
B) Não-supervisionado (clustering para agrupar) + Supervisionado (classificação/regressão para prever performance)  
C) Apenas clustering resolve ambos  
D) Apenas reforço  

---

### 6.
Um modelo de detecção de fraude em transações financeiras tem: Precisão = 98%, Recall = 40%. Isso significa que:

A) O modelo detecta quase todas as fraudes  
B) Quando o modelo diz "fraude", quase sempre está certo, mas deixa 60% das fraudes reais passarem despercebidas  
C) O modelo tem alta acurácia  
D) O modelo está com underfitting  

---

### 7.
Uma equipe está usando Amazon SageMaker Autopilot. Qual é a PRINCIPAL vantagem do Autopilot em relação a construir modelos manualmente no SageMaker Studio?

A) Autopilot é gratuito  
B) Autopilot testa automaticamente múltiplos algoritmos e configurações, gerando o melhor modelo sem necessidade de escolher algoritmos manualmente  
C) Autopilot só funciona com dados de imagem  
D) Autopilot não requer dados de entrada  

---

### 8.
Qual é a diferença entre Amazon Kendra e Amazon Athena para buscar informações?

A) Ambos são idênticos  
B) Kendra entende perguntas em linguagem natural e busca semanticamente em documentos; Athena executa queries SQL estruturadas em dados no S3  
C) Athena entende linguagem natural; Kendra requer SQL  
D) Kendra é para imagens; Athena é para texto  

---

### 9.
Uma empresa precisa monitorar continuamente se seu modelo de classificação em produção está mantendo a qualidade esperada e alertar automaticamente quando a performance degradar. Quais serviços combinados atendem esse requisito?

A) CloudTrail + IAM  
B) SageMaker Model Monitor + CloudWatch Alarms  
C) SageMaker Clarify + S3  
D) Bedrock Guardrails + Lambda  

---

### 10.
Uma empresa treina um modelo com regularização L2 muito forte (lambda = 100). O modelo apresenta erro alto tanto no treino quanto no teste. Qual é a causa?

A) Overfitting devido à regularização  
B) Underfitting — a regularização excessiva simplificou demais o modelo  
C) Data drift  
D) O modelo é perfeito  

---

### 11.
Uma empresa quer analisar 100.000 avaliações de clientes para identificar os temas mais discutidos (sem categorias predefinidas) E classificar cada avaliação como positiva/negativa. Qual combinação de serviços AWS resolve AMBAS as necessidades com menor esforço?

A) Amazon Comprehend (topic modeling para temas + sentiment analysis para classificação)  
B) Amazon Translate + Amazon Lex  
C) Amazon Textract + Amazon Polly  
D) Amazon Rekognition + Amazon Personalize  

---

### 12.
Uma empresa quer criar chatbots conversacionais para atendimento ao cliente com reconhecimento de intenção e extração de slots (informações do cliente como nome, data, número de pedido). Qual serviço é projetado especificamente para isso?

A) Amazon Comprehend  
B) Amazon Lex  
C) Amazon Polly  
D) Amazon Bedrock  

---

### 13.
Uma empresa quer usar IA generativa mas está preocupada com o custo de pré-treinamento de um Foundation Model do zero. Qual abordagem permite usar IA generativa SEM o custo de pré-treinamento?

A) Pré-treinar um modelo próprio na AWS  
B) Acessar modelos já pré-treinados via Amazon Bedrock (paga apenas pela inferência)  
C) Usar apenas ML tradicional  
D) Treinar do zero em SageMaker  

---

### 14.
Uma empresa está avaliando dois modelos no Bedrock. O Modelo A tem context window de 8K tokens e custa $0.01/1K tokens. O Modelo B tem context window de 200K tokens e custa $0.05/1K tokens. A aplicação precisa processar documentos de 50+ páginas (~80K tokens). Qual modelo deve ser escolhido e por quê?

A) Modelo A porque é mais barato  
B) Modelo B porque o documento excede a context window do Modelo A, tornando-o inutilizável para esse caso  
C) Qualquer um funciona  
D) Nenhum — documentos longos não podem ser processados por LLMs  

---

### 15.
Qual afirmação sobre modelos "decoder-only" (GPT, Claude, Llama) está CORRETA?

A) Processam toda a entrada de uma vez mas geram saída token por token (autoregressive)  
B) Geram toda a saída de uma vez em paralelo  
C) Só funcionam para tradução  
D) Não usam mecanismo de attention  

---

### 16.
Uma empresa usa um LLM para gerar conteúdo criativo de marketing (slogans, ideias de campanha). As respostas estão muito repetitivas e previsíveis. Qual ajuste de parâmetro resolve?

A) Reduzir temperature para 0  
B) Aumentar temperature (ex: 0.8-1.0) para mais diversidade e criatividade  
C) Reduzir max_tokens  
D) Aumentar context window  

---

### 17.
Uma empresa implementou um chatbot com system prompt: "Responda APENAS com base no contexto fornecido. Se a informação não estiver no contexto, diga 'Não tenho essa informação'." Mas o modelo frequentemente ignora essa instrução e gera respostas inventadas. Qual PRÓXIMA medida é mais eficaz?

A) Aumentar temperature  
B) Implementar RAG + Bedrock Guardrails com grounding check  
C) Fazer fine-tuning para o modelo aprender a dizer "não sei"  
D) Usar um modelo menor  

---

### 18.
Um desenvolvedor está criando um prompt template para um sistema de classificação de tickets. Qual é a vantagem de usar prompt templates em produção versus prompts ad-hoc?

A) Templates são mais criativos  
B) Templates garantem consistência, são reutilizáveis e permitem injetar variáveis dinamicamente  
C) Templates são obrigatórios no Bedrock  
D) Templates custam menos tokens  

---

### 19.
Uma empresa quer que seu chatbot responda em português brasileiro, com tom informal e limite de 3 frases por resposta. Onde essas instruções devem ser configuradas?

A) No fine-tuning  
B) No system prompt  
C) Na context window  
D) No vector database  

---

### 20.
Qual é a relação entre tokens, custo e latência em um LLM?

A) Tokens não afetam custo nem latência  
B) Mais tokens de saída = mais custo E mais latência (geração sequencial token por token)  
C) Tokens de entrada são mais caros que de saída  
D) Latência é fixa independente do número de tokens  

---

### 21.
Uma empresa tem um Foundation Model que funciona bem para tarefas gerais mas não conhece a terminologia específica do setor de mineração (nomes de minerais, processos industriais, equipamentos). O modelo confunde termos técnicos. Qual abordagem resolve MAIS profundamente?

A) Few-shot com exemplos de termos  
B) RAG com glossário de termos  
C) Continued pre-training com milhões de tokens de textos técnicos de mineração  
D) Guardrails  

---

### 22.
Qual das seguintes NÃO é uma capacidade do Amazon Bedrock?

A) Acessar Foundation Models de múltiplos provedores via API  
B) Criar Knowledge Bases para RAG  
C) Treinar modelos de ML tabular (classificação, regressão) do zero  
D) Configurar Guardrails para filtrar conteúdo  

---

### 23.
Uma empresa avalia se deve usar Amazon Bedrock ou Amazon Q Business para um chatbot corporativo. A empresa precisa que o chatbot: respeite permissões existentes (cada funcionário vê apenas docs autorizados), integre com Confluence e SharePoint, e funcione out-of-the-box. Qual serviço atende TODOS esses requisitos com menor esforço?

A) Amazon Bedrock com Knowledge Bases customizadas  
B) Amazon Q Business  
C) Amazon Kendra  
D) PartyRock  

---

### 24.
Um CTO quer demonstrar valor de IA generativa para o board em 1 semana. Precisa de um protótipo funcional que mostre geração de texto, sem equipe de ML e com investimento mínimo. Qual caminho é MAIS realista?

A) Treinar um LLM do zero no SageMaker  
B) Usar Amazon Bedrock para construir um protótipo com API calls a um FM existente  
C) Contratar uma equipe de 5 cientistas de dados  
D) Fazer fine-tuning extensivo  

---

### 25.
O que é "multi-head attention" em um Transformer?

A) O modelo tem múltiplas cabeças de processamento em paralelo, cada uma capturando diferentes tipos de relações (sintáticas, semânticas, etc.)  
B) O modelo processa múltiplos documentos simultaneamente  
C) O modelo tem múltiplas saídas  
D) O modelo usa múltiplas GPUs  

---

### 26.
Qual é a garantia de privacidade do Bedrock que diferencia de usar LLMs via APIs de terceiros diretamente?

A) Bedrock é mais barato  
B) No Bedrock, dados do cliente permanecem na conta/região AWS e NÃO são usados para treinar modelos. Controle via IAM, KMS e VPC Endpoints  
C) Bedrock não armazena nada  
D) Não há diferença  

---

### 27.
Uma empresa quer gerar imagens de produtos com IA no Bedrock. Qual modelo oferece watermarking automático (marca invisível para rastreabilidade)?

A) Stable Diffusion  
B) Amazon Titan Image Generator  
C) Claude  
D) Llama  

---

### 28.
Uma empresa implementou RAG com Knowledge Bases no Bedrock. O chatbot responde corretamente perguntas que estão nos documentos. Porém, para perguntas fora do escopo dos documentos, o modelo inventa respostas. Qual combinação resolve?

A) Adicionar mais documentos  
B) Guardrails com grounding check + instrução no prompt para dizer "não tenho essa informação" quando o contexto não contém a resposta  
C) Aumentar temperature  
D) Fine-tuning  

---

### 29.
Uma empresa tem um pipeline RAG funcional. Os chunks são de 2000 tokens cada. As perguntas dos usuários são muito específicas (ex: "Qual é o prazo de garantia do produto X?"). As respostas frequentemente incluem informação irrelevante junto com a correta. Qual ajuste MAIS provavelmente melhora a precisão?

A) Aumentar o tamanho dos chunks para 5000 tokens  
B) Reduzir o tamanho dos chunks (ex: 300-500 tokens) para retornar trechos mais focados  
C) Usar um modelo maior  
D) Aumentar temperature  

---

### 30.
Uma empresa bancária precisa que seu assistente virtual: responda perguntas sobre produtos (conta, cartão, investimentos) usando docs internos E permita que o cliente solicite bloqueio de cartão, que é processado via API interna. Qual arquitetura mínima no Bedrock?

A) Apenas Knowledge Bases  
B) Apenas Fine-tuning  
C) Bedrock Agent com Knowledge Base (para docs) + Action Group com Lambda (para bloquear cartão via API)  
D) Apenas Guardrails  

---

### 31.
Uma empresa quer reduzir a latência das respostas do chatbot. Atualmente usa on-demand com um modelo grande. As perguntas são frequentemente repetidas (80% dos clientes perguntam as mesmas 50 coisas). Qual estratégia combinada MAIS reduz latência?

A) Usar modelo maior  
B) Implementar cache de respostas para perguntas frequentes + considerar modelo menor para perguntas simples  
C) Aumentar max_tokens  
D) Adicionar mais documentos ao RAG  

---

### 32.
Qual é a PRINCIPAL diferença entre "fine-tuning" e "continued pre-training" no Bedrock?

A) São a mesma coisa  
B) Fine-tuning usa pares input/output para ajustar comportamento; continued pre-training usa grandes volumes de texto corrido para ensinar conhecimento novo  
C) Fine-tuning é gratuito; continued pre-training é pago  
D) Continued pre-training é mais rápido que fine-tuning  

---

### 33.
Uma empresa precisa avaliar se as respostas do chatbot são factualmente corretas, úteis e no tom adequado. Métricas automáticas como ROUGE não capturam essas nuances. Qual abordagem de avaliação é necessária?

A) Apenas BLEU  
B) Avaliação humana (human evaluation) com avaliadores internos  
C) Apenas perplexidade  
D) Apenas AUC-ROC  

---

### 34.
Uma empresa processa 10 requests/minuto ao Bedrock e quer pagar o MÍNIMO possível. Qual modelo de precificação é adequado para esse volume baixo?

A) Provisioned Throughput  
B) On-demand (paga por token usado)  
C) Reserva anual  
D) Batch inference  

---

### 35.
Um Agent do Bedrock está configurado com 3 action groups: (1) consultar estoque, (2) criar pedido, (3) processar devolução. Um cliente pergunta "Quanto custa o produto X?". O Agent deve:

A) Executar as 3 ações em sequência  
B) Raciocinar que a pergunta é sobre preço, decidir que "consultar estoque" é a ação relevante, executá-la e retornar o preço  
C) Gerar uma resposta inventada sem usar nenhuma ação  
D) Pedir ao cliente para reformular  

---

### 36.
Qual é o benefício de usar Amazon OpenSearch Serverless como vector database em uma arquitetura RAG versus um banco relacional?

A) OpenSearch é mais barato para dados tabulares  
B) OpenSearch é otimizado para busca por similaridade vetorial (nearest neighbors), fundamental para RAG; bancos relacionais não são otimizados para isso  
C) Bancos relacionais são melhores para busca semântica  
D) Não há diferença  

---

### 37.
Uma empresa está usando Bedrock e quer garantir que certas equipes possam apenas usar modelos de texto (não imagem) e apenas modelos com context window > 100K tokens. Onde configurar esse controle?

A) Guardrails  
B) IAM policies com condições específicas para modelos permitidos  
C) System prompt  
D) Vector database  

---

### 38.
Qual afirmação sobre "Bedrock Model Access" está CORRETA?

A) Todos os modelos estão disponíveis automaticamente para qualquer conta  
B) Antes de usar um modelo, a conta deve solicitar acesso (model access request), adicionando uma camada de governança  
C) Model access é gerenciado pelo provedor do modelo, não pela AWS  
D) Model access é configurado via system prompt  

---

### 39.
Uma empresa quer um modelo que gere código, explique decisões arquiteturais e sugira refatorações, tudo integrado ao IDE dos desenvolvedores. Qual serviço atende com o MENOR esforço de integração?

A) Amazon Bedrock com Claude via API customizada  
B) Amazon Q Developer (integrado nativamente a IDEs)  
C) Amazon SageMaker com modelo de código customizado  
D) Amazon Lex  

---

### 40.
Em uma arquitetura RAG, o que acontece se o modelo de embeddings usado para indexar os documentos for DIFERENTE do modelo usado para gerar o embedding da query?

A) Nenhum problema  
B) A busca por similaridade será ineficaz pois os vetores estão em espaços diferentes e não são comparáveis  
C) O sistema gera erro automático  
D) Os resultados serão melhores por diversidade  

---

### 41.
Uma empresa implementou RAG + Guardrails. O chatbot responde bem para perguntas cobertas pela base. Para perguntas não cobertas, o grounding check do Guardrails bloqueia a resposta. Mas a mensagem de bloqueio padrão é genérica. Como melhorar a experiência?

A) Desabilitar grounding check  
B) Configurar uma mensagem customizada no Guardrails (ex: "Não encontrei essa informação nos documentos disponíveis. Posso ajudar com outra coisa?")  
C) Aumentar temperature  
D) Adicionar fine-tuning  

---

### 42.
Uma empresa está decidindo entre "chunking fixo" (ex: 500 tokens) e "chunking semântico" (dividir por parágrafos/seções) para seus documentos. Qual cenário favorece chunking SEMÂNTICO?

A) Documentos sem estrutura definida (textos corridos)  
B) Documentos bem estruturados com seções claras (manuais técnicos, FAQs, guias)  
C) Documentos muito curtos (1 parágrafo)  
D) Áudio transcrito  

---

### 43.
Uma aplicação usa Bedrock on-demand e processa 1 milhão de requests/dia. A empresa quer REDUZIR custos sem perder qualidade. Qual combinação de estratégias tem MAIOR impacto?

A) Aumentar temperature + usar modelo maior  
B) Cache de respostas frequentes + modelo menor para tarefas simples + prompts mais concisos  
C) Fine-tuning + Provisioned Throughput  
D) Adicionar mais action groups  

---

### 44.
Qual é a vantagem de "batch inference" no Bedrock versus chamadas on-demand?

A) Respostas em tempo real  
B) Custo reduzido para processamento em lote que não requer resposta imediata  
C) Maior qualidade de respostas  
D) Menor quantidade de tokens  

---

### 45.
Uma empresa de seguros usa ML para calcular prêmios. O regulador exige que a empresa demonstre que o modelo não discrimina com base em etnia, gênero ou idade. Qual processo COMPLETO atende essa exigência?

A) Apenas monitorar acurácia geral  
B) Usar SageMaker Clarify para analisar bias pre/post-training, monitorar fairness metrics por subgrupo em produção, e documentar resultados em Model Cards  
C) Apenas remover variáveis demográficas do modelo  
D) Apenas usar Guardrails  

---

### 46.
Uma empresa implementou A2I (human-in-the-loop) para revisão de documentos. O modelo de extração acerta 95% das vezes. A empresa quer enviar para revisão humana APENAS os 5% de baixa confiança para reduzir custo de revisores. Qual configuração implementa isso?

A) Enviar 100% para revisão sempre  
B) Configurar threshold de confiança no A2I — apenas previsões com confiança < X% são encaminhadas para revisão  
C) Remover o A2I completamente  
D) Usar apenas Guardrails  

---

### 47.
Uma empresa treinou um modelo de aprovação de crédito. O regulador solicita que para cada decisão negada, a empresa apresente os 3 fatores que MAIS contribuíram para a negativa. Qual output do SageMaker Clarify atende diretamente esse pedido?

A) Feature importance global  
B) SHAP values da previsão individual (mostra contribuição de cada feature para AQUELA decisão)  
C) AUC-ROC do modelo  
D) Métricas de bias  

---

### 48.
Qual é o papel do Bedrock Guardrails "contextual grounding" em relação ao "content filter"?

A) São a mesma coisa  
B) Content filter bloqueia por TIPO de conteúdo (violência, sexual, etc.); contextual grounding verifica se a resposta está FUNDAMENTADA no contexto fornecido (detecta alucinações)  
C) Contextual grounding é para imagens; content filter é para texto  
D) Content filter é mais importante  

---

### 49.
Uma empresa quer garantir que seu chatbot NUNCA discuta temas financeiros (investimentos, criptomoedas, ações). O system prompt diz "Não fale sobre finanças", mas usuários conseguem contornar com prompts criativos. Qual solução é mais ROBUSTA?

A) Melhorar o system prompt com mais instruções  
B) Bedrock Guardrails com denied topics configurado para temas financeiros (aplicado independente do prompt)  
C) Fine-tuning para desaprender sobre finanças  
D) Reduzir temperature  

---

### 50.
Qual é a importância de "red teaming" ANTES do deploy de um sistema de IA?

A) Reduzir custos operacionais  
B) Identificar proativamente falhas, vulnerabilidades e outputs perigosos que testes normais não encontram  
C) Melhorar a velocidade de inferência  
D) Documentar o modelo  

---

### 51.
Uma empresa precisa garantir que dados sensíveis de clientes (PII) não fiquem em logs de inferência do Bedrock acessíveis a toda a equipe de engenharia. Qual combinação implementa isso?

A) Não habilitar logging  
B) Habilitar Model Invocation Logging com destino criptografado (KMS) + IAM policies restritivas que limitam acesso aos logs  
C) Salvar logs em bucket S3 público  
D) Usar apenas CloudTrail  

---

### 52.
Uma empresa com múltiplas contas AWS quer impor que TODAS as contas devem usar VPC Endpoints para acessar Bedrock (nenhum acesso via internet). Qual mecanismo aplica essa política organizacionalmente?

A) IAM policies em cada conta  
B) Service Control Policies (SCPs) com condição de VPC endpoint  
C) Security Groups  
D) Bedrock Guardrails  

---

### 53.
Qual serviço AWS fornece relatórios de auditoria prontos (SOC, ISO, PCI) que comprovam a conformidade da INFRAESTRUTURA AWS?

A) AWS CloudTrail  
B) AWS Artifact  
C) AWS Config  
D) Amazon Inspector  

---

### 54.
Uma equipe fez deploy de um novo modelo via SageMaker. Após 2 semanas, querem entender EXATAMENTE quais dados, transformações e hiperparâmetros foram usados para esse modelo específico. Qual funcionalidade fornece essa informação?

A) CloudWatch Logs  
B) SageMaker ML Lineage Tracking  
C) CloudTrail  
D) S3 versioning  

---

### 55.
Uma empresa quer que apenas a role "MLEngineer" possa criar endpoints SageMaker em produção, enquanto a role "DataScientist" pode apenas treinar modelos. Qual recurso AWS implementa essa separação?

A) Security Groups com regras por role  
B) IAM policies com permissões específicas por role (least privilege)  
C) KMS key policies  
D) VPC NACLs  

---

### 56.
Qual é a diferença entre SageMaker Model Monitor e SageMaker Clarify em produção?

A) São idênticos  
B) Model Monitor detecta drift de dados/performance; Clarify detecta drift de viés/fairness e fornece explicabilidade  
C) Clarify é para desenvolvimento; Model Monitor é para produção  
D) Model Monitor é gratuito; Clarify é pago  

---

### 57.
Uma empresa precisa demonstrar para auditoria: (1) quem acessou o modelo, (2) quando, (3) de qual IP, (4) com quais parâmetros. Qual serviço fornece TODAS essas informações?

A) Amazon CloudWatch  
B) AWS CloudTrail  
C) SageMaker Model Monitor  
D) Amazon Macie  

---

### 58.
Qual é a diferença entre "criptografia em repouso" e "criptografia em trânsito" no contexto de IA?

A) São a mesma coisa  
B) Em repouso protege dados armazenados (S3, EBS) com KMS; em trânsito protege dados sendo transferidos (entre app e AWS) com TLS/HTTPS  
C) Em repouso é para modelos; em trânsito é para dados  
D) Apenas uma é necessária  

---

### 59. (Múltipla Resposta)
Uma empresa quer governança completa de modelos ML. Quais funcionalidades do SageMaker atendem: versionamento de modelos, aprovação de deploy, e automação do pipeline? **(Selecione DUAS)**

A) SageMaker Model Registry (versionamento + aprovação)  
B) SageMaker Canvas  
C) SageMaker Pipelines (automação do pipeline)  
D) SageMaker Autopilot  
E) SageMaker JumpStart  

---

### 60.
No modelo de responsabilidade compartilhada para IA na AWS, qual das seguintes é responsabilidade do CLIENTE, não da AWS?

A) Segurança física dos data centers  
B) Patching do sistema operacional das instâncias gerenciadas  
C) Garantir que dados de treino não contenham viés discriminatório e que modelos sejam avaliados por fairness  
D) Manutenção da rede global da AWS  

---

## Gabarito

<details>
<summary>🔍 Ver gabarito completo</summary>

| # | Resp | Domínio | Justificativa |
|---|------|---------|---------------|
| 1 | C | D1 | Otimizar decisões em tempo real com feedback (ganho/perda) = reforço. Não há dados rotulados fixos; o agente aprende por interação. |
| 2 | B | D1 | Poucos rótulos + muitos dados sem rótulo = semi-supervisionado aproveita ambos. Supervisionado puro desperdiça os dados não-rotulados. |
| 3 | B | D1 | AUC-ROC mede capacidade de distinguir entre classes. 0.92 > 0.78 = Modelo A separa melhor positivos de negativos independente do threshold. |
| 4 | B | D1 | Dados mudaram (novos imóveis). Modelo precisa de dados atualizados para aprender os novos padrões. Regularização/simplificação não resolve — o modelo precisa ver os dados novos. |
| 5 | B | D1 | Agrupar sem categorias = clustering (não-supervisionado). Prever performance = supervisionado. São problemas distintos. |
| 6 | B | D1 | Precisão 98% = quando diz fraude, acerta 98% das vezes. Recall 40% = detecta apenas 40% das fraudes reais. 60% passam despercebidas. |
| 7 | B | D1 | Autopilot = AutoML que testa múltiplos algoritmos, faz feature engineering e tuning automaticamente. Menor esforço para o usuário. |
| 8 | B | D1 | Kendra = linguagem natural + busca semântica em docs. Athena = SQL em dados estruturados no S3. Propósitos diferentes. |
| 9 | B | D1 | Model Monitor detecta degradação + CloudWatch Alarms envia notificações quando thresholds são violados. |
| 10 | B | D1 | Regularização excessiva = penaliza demais a complexidade = modelo muito simples = underfitting. |
| 11 | A | D1 | Comprehend faz topic modeling (temas sem categorias) E sentiment analysis (positivo/negativo) — resolve ambos com um serviço. |
| 12 | B | D1 | Lex = chatbots com NLU (reconhecimento de intenção + extração de slots). Comprehend analisa texto mas não conversa. |
| 13 | B | D2 | Bedrock = FMs já pré-treinados, paga apenas inferência. Sem custo bilionário de pré-treinamento. |
| 14 | B | D2 | 80K tokens > 8K (context window do A). Modelo A literalmente não pode processar o documento. Modelo B (200K) pode. Custo maior mas é a única opção funcional. |
| 15 | A | D2 | Decoder-only: processa input em paralelo (attention), mas GERA output sequencialmente (token por token, autoregressive). |
| 16 | B | D2 | "Repetitivo e previsível" = temperature muito baixa. Aumentar temperature traz diversidade e criatividade. |
| 17 | B | D2 | System prompt sozinho pode ser contornado. RAG fornece contexto factual + Guardrails grounding check bloqueia quando resposta não está no contexto. Dupla proteção. |
| 18 | B | D2 | Templates = consistência em produção + variáveis dinâmicas (injetar ticket, nome, contexto) + reutilizáveis. Ad-hoc é inconsistente. |
| 19 | B | D2 | System prompt define comportamento geral: idioma, tom, formato, limites. É o lugar correto para essas instruções. |
| 20 | B | D2 | Saída é gerada sequencialmente (token por token) = mais tokens = mais tempo E mais custo. Entrada é processada em paralelo (menos impacto na latência). |
| 21 | C | D2 | "Confunde termos" = não ENTENDE o domínio. Continued pre-training ensina vocabulário novo no nível mais profundo. RAG traz info sob demanda mas não resolve confusão terminológica. |
| 22 | C | D2 | Bedrock é para GenAI (Foundation Models). ML tabular (classificação/regressão do zero) é SageMaker. Bedrock não treina modelos tabulares. |
| 23 | B | D2 | "Permissões existentes" + "Confluence + SharePoint" + "out-of-the-box" = Q Business. Bedrock KB requer construir integração de permissões. |
| 24 | B | D2 | "1 semana" + "sem equipe de ML" + "investimento mínimo" (não zero) = Bedrock com API. PartyRock é mais rápido mas limitado demais para impressionar board. |
| 25 | A | D2 | Multi-head = múltiplas "perspectivas" de attention em paralelo. Cada head captura relações diferentes. Resultado mais rico. |
| 26 | B | D2 | Bedrock = dados na sua conta/região + não treina modelos + IAM/KMS/VPC. APIs de terceiros podem ter políticas menos transparentes. |
| 27 | B | D2 | Titan Image Generator tem watermarking invisível built-in (rastreabilidade). Stable Diffusion e outros não oferecem nativamente. |
| 28 | B | D3 | Para perguntas fora do escopo: Guardrails grounding detecta falta de fundamentação + prompt instrui comportamento adequado. Combinação previne alucinações em edge cases. |
| 29 | B | D3 | Chunks de 2000 tokens com perguntas específicas = contexto diluído. Chunks menores (300-500) retornam trechos mais focados na informação pedida. |
| 30 | C | D3 | Perguntas sobre docs = Knowledge Base. Bloquear cartão = ação em API = Action Group (Lambda). Agent orquestra ambos. |
| 31 | B | D3 | 80% perguntas repetidas = cache tem altíssimo hit rate (reduz 80% das chamadas). Modelo menor para as restantes reduz custo por chamada. |
| 32 | B | D3 | Fine-tuning = pares input/output (ajustar comportamento). Continued pre-training = texto corrido (ensinar conhecimento). Objetivos e dados diferentes. |
| 33 | B | D3 | Factualidade, utilidade e tom = qualidade subjetiva que métricas automáticas não medem. Precisa de humanos avaliando. |
| 34 | B | D3 | 10 req/min = volume baixo e variável. On-demand é ideal (paga só o que usa). PT = caro para volume baixo. Batch = não é real-time. |
| 35 | B | D3 | Agent raciocina (ReAct): pergunta sobre preço → preciso consultar catálogo → action group "consultar estoque" → retorna preço → responde. Não executa ações desnecessárias. |
| 36 | B | D3 | OpenSearch = otimizado para k-nearest neighbors em vetores. Bancos relacionais não têm indexação vetorial eficiente. Performance de busca semântica é incomparável. |
| 37 | B | D3 | "Quais modelos cada equipe pode usar" = IAM policies com condições (ex: bedrock:ModelId). Guardrails filtram conteúdo, não acesso a modelos. |
| 38 | B | D3 | Model Access = governança adicional. Conta solicita acesso antes de poder invocar. Previne uso acidental de modelos não aprovados. |
| 39 | B | D3 | "Integrado ao IDE" + "menor esforço de integração" = Q Developer (nativo em VS Code, IntelliJ). Bedrock via API requer construir integração. |
| 40 | B | D3 | Embeddings de modelos diferentes vivem em espaços vetoriais diferentes. Comparar vetores de espaços distintos = busca ineficaz. DEVE usar o mesmo modelo para indexação e query. |
| 41 | B | D3 | Guardrails permite configurar mensagem customizada quando bloqueiam. UX melhor que mensagem genérica. Não precisa desabilitar a proteção. |
| 42 | B | D3 | Docs bem estruturados com seções claras = chunking semântico preserva contexto natural (uma seção = um chunk). Fixo pode cortar no meio de uma seção. |
| 43 | B | D3 | Cache (elimina 80% das chamadas) + modelo menor (custo por chamada) + prompts concisos (menos tokens) = impacto combinado alto. Fine-tuning + PT = mais caro. |
| 44 | B | D3 | Batch = processamento em lote com desconto. Sem urgência de resposta imediata = mais barato que on-demand. |
| 45 | B | D4 | Processo completo: (1) Clarify detecta bias pre/post-training, (2) Model Monitor monitora fairness em produção, (3) Model Cards documentam. Apenas remover variáveis não resolve (proxies existem). |
| 46 | B | D4 | A2I com threshold = apenas baixa confiança vai para humanos. 95% processados automaticamente. 5% revisados. Balança custo x qualidade. |
| 47 | B | D4 | SHAP individual = contribuição de cada feature para AQUELA decisão específica. "Renda contribuiu -40%, dívida contribuiu -35%, idade contribuiu -25%". |
| 48 | B | D4 | Content filter = categorias de conteúdo (violência, sexual). Contextual grounding = resposta fundamentada no contexto (detecta alucinações). Propósitos diferentes. |
| 49 | B | D4 | System prompt pode ser burlado com prompt injection. Guardrails denied topics são aplicados INDEPENDENTEMENTE do prompt — camada de proteção separada e mais robusta. |
| 50 | B | D4 | Red teaming encontra vulnerabilidades que testes normais (happy path) não revelam. Essencial antes de expor sistema a usuários reais. |
| 51 | B | D5 | Logging necessário (auditoria) + proteger PII nos logs = criptografia KMS + IAM restritivo. Não logar (A) viola requisito de auditoria. |
| 52 | B | D5 | Política organizacional em TODAS as contas = SCPs. IAM individual não garante compliance em 100% das contas. SCPs = guardrail organizacional. |
| 53 | B | D5 | Artifact = portal de compliance reports da AWS (SOC, ISO, PCI). CloudTrail = suas API calls. Config = configuração de recursos. |
| 54 | B | D5 | Lineage Tracking = rastrear toda a origem do modelo: quais dados, quais transformações, quais hiperparâmetros, qual job de treino. |
| 55 | B | D5 | IAM policies por role: MLEngineer → sagemaker:CreateEndpoint. DataScientist → sagemaker:CreateTrainingJob (sem CreateEndpoint). Separação clara. |
| 56 | B | D5 | Model Monitor = drift de dados e performance. Clarify = drift de bias/fairness + explicabilidade. Complementares, não idênticos. |
| 57 | B | D5 | CloudTrail registra: identidade (quem), timestamp (quando), source IP (de onde), request parameters (com quais parâmetros). Tudo em um lugar. |
| 58 | B | D5 | Em repouso = dados parados (disco, S3) protegidos com KMS. Em trânsito = dados movendo (rede) protegidos com TLS. Ambos necessários. |
| 59 | A,C | D5 | Model Registry = versionar + aprovar. Pipelines = automatizar fluxo. Canvas = no-code ML. Autopilot = AutoML. JumpStart = modelos prontos. |
| 60 | C | D5 | Responsabilidade compartilhada: AWS cuida da infraestrutura. CLIENTE cuida dos dados, modelos e uso responsável. Viés nos dados é responsabilidade do cliente. |

---

### Cálculo de Resultado

- **54-60 corretas (90%+):** Excelente — muito provavelmente aprovado
- **48-53 corretas (80-89%):** Bom — confortavelmente acima do threshold
- **42-47 corretas (70-79%):** Na borda — revise os domínios com mais erros
- **<42 corretas (<70%):** Precisa de mais estudo — foque nos domínios fracos

**Compare seus erros entre Simulado 1 e 2. Padrões repetidos = seus gaps prioritários.**

</details>

