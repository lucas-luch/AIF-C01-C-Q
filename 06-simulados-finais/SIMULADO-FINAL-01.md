# Simulado Final 1 — AWS Certified AI Practitioner (AIF-C01)

**60 questões | 90 minutos | Aprovação: 700/1000**

Distribuição por domínio (proporcional à prova real):
- Domínio 1 (Fundamentos de IA e ML): 12 questões
- Domínio 2 (Fundamentos de IA Generativa): 15 questões
- Domínio 3 (Aplicações de Foundation Models): 17 questões
- Domínio 4 (IA Responsável): 8 questões
- Domínio 5 (Segurança, Conformidade e Governança): 8 questões

**Instruções:** Responda todas as questões antes de consultar o gabarito no final. Cronometre 90 minutos para simular a prova real.

---

## Questões

### 1.
Uma seguradora quer usar Machine Learning para determinar se sinistros reportados são fraudulentos ou legítimos. A empresa possui um banco de dados com milhares de sinistros já avaliados por analistas humanos. Qual abordagem de ML requer o MENOR esforço para implementar essa solução?

A) Treinar um modelo de clustering para agrupar sinistros por similaridade e inferir fraude  
B) Treinar um modelo de classificação supervisionada usando o histórico rotulado  
C) Implementar aprendizado por reforço onde um agente aprende a detectar padrões de fraude  
D) Usar aprendizado não-supervisionado para encontrar anomalias nos dados de sinistros  

---

### 2.
Uma equipe de ciência de dados treinou um modelo de previsão de demanda. O modelo atinge RMSE de 12 no conjunto de treino e RMSE de 45 no conjunto de teste. A equipe aumentou a quantidade de dados de treino em 50%, mas o problema persiste. Qual é a ação MAIS provável para resolver o problema?

A) Coletar ainda mais dados de treino  
B) Aplicar regularização ou reduzir a complexidade do modelo  
C) Usar um modelo mais complexo com mais parâmetros  
D) Remover o conjunto de validação para dar mais dados ao treino  

---

### 3.
Uma empresa de call center quer transcrever automaticamente as gravações de atendimento e depois analisar o sentimento dos clientes durante a ligação. Quais serviços AWS devem ser usados NESSA ORDEM?

A) Amazon Polly → Amazon Comprehend  
B) Amazon Transcribe → Amazon Comprehend  
C) Amazon Lex → Amazon Translate  
D) Amazon Comprehend → Amazon Transcribe  

---

### 4.
Uma rede varejista precisa prever a demanda de 5.000 produtos em 200 lojas para os próximos 3 meses usando dados históricos de vendas diárias. A equipe de negócios não tem experiência em ML e quer uma solução gerenciada. Qual serviço é MAIS adequado?

A) Amazon SageMaker Autopilot para criar modelos customizados de regressão  
B) Amazon Personalize para gerar recomendações de estoque  
C) Amazon Forecast para previsão gerenciada de séries temporais  
D) Amazon Bedrock para gerar previsões com um LLM  

---

### 5.
Um modelo de regressão apresenta erro alto tanto nos dados de treino quanto nos de teste, mesmo após múltiplas iterações de treinamento. A equipe suspeita de underfitting. Qual combinação de ações é MAIS provável de resolver o problema?

A) Adicionar regularização L2 e reduzir o learning rate  
B) Usar um modelo mais complexo e adicionar features relevantes  
C) Aplicar early stopping e aumentar o dropout  
D) Coletar mais dados e aumentar a regularização  

---

### 6.
Uma empresa de saúde está construindo um modelo para detectar uma condição rara que afeta 0.3% da população. O modelo atual tem 99.7% de acurácia. A equipe médica reporta que o modelo não está detectando pacientes doentes. Qual é a causa mais provável e a métrica que deveria ser monitorada?

A) O modelo está com overfitting; monitorar a loss function  
B) O modelo está prevendo sempre "saudável" devido ao desbalanceamento; monitorar o recall da classe positiva  
C) O modelo está com underfitting; monitorar a acurácia do treino  
D) Os dados de treino contêm viés; monitorar SHAP values  

---

### 7.
Em um pipeline de ML, uma equipe decide usar 70% dos dados para treino, 15% para validação e 15% para teste. Qual afirmação sobre o uso desses conjuntos está CORRETA?

A) O conjunto de teste é usado para ajustar hiperparâmetros durante o desenvolvimento  
B) O conjunto de validação é usado uma única vez ao final para medir performance real  
C) O conjunto de validação é usado durante o desenvolvimento para ajustar hiperparâmetros, e o conjunto de teste é reservado para avaliação final  
D) O conjunto de treino e validação devem ser combinados para o treinamento final  

---

### 8.
Uma equipe de ML está decidindo entre dois modelos para detecção de fraude em cartão de crédito. O Modelo A tem recall de 95% e precisão de 60%. O Modelo B tem recall de 70% e precisão de 95%. Considerando que fraudes não detectadas causam perdas financeiras significativas, qual modelo escolher e por quê?

A) Modelo B, porque a alta precisão significa menos investigações desnecessárias  
B) Modelo A, porque recall alto garante que quase todas as fraudes reais são detectadas  
C) Qualquer um, pois ambos têm performance similar  
D) Nenhum — é necessário otimizar a acurácia primeiro  

---

### 9.
Um analista de negócios sem experiência em programação precisa construir um modelo para prever churn de clientes usando dados tabulares de CRM. A empresa quer a solução com o MENOR esforço técnico possível. Qual combinação de serviço e abordagem é mais adequada?

A) Amazon SageMaker Studio com notebooks Jupyter e XGBoost  
B) Amazon Bedrock com um Foundation Model para analisar os dados  
C) Amazon SageMaker Canvas com interface visual drag-and-drop  
D) AWS Glue DataBrew para preparação seguido de Amazon Comprehend  

---

### 10.
Uma empresa de e-commerce quer prever o valor total de compras que cada cliente fará no próximo trimestre E segmentar clientes em grupos de comportamento similiar. Quais DOIS tipos de tarefa de ML são necessários?

A) Classificação e Detecção de Anomalias  
B) Regressão e Clustering  
C) Regressão e Classificação  
D) Clustering e Recomendação  

---

### 11.
Uma equipe implantou um modelo de classificação de emails há 6 meses. O modelo apresentava 94% de F1 Score no deploy. Agora o F1 caiu para 78%, mas nenhum código foi alterado. Uma análise mostra que novos tipos de spam surgiram que não existiam nos dados de treino. Qual tipo de drift está ocorrendo?

A) Data drift — a distribuição dos inputs mudou  
B) Concept drift — a relação entre inputs e labels mudou  
C) Model drift causado por degradação de hardware  
D) Feature drift — as features estão sendo calculadas incorretamente  

---

### 12.
Uma empresa precisa extrair informações estruturadas (nome do cliente, valor, data de vencimento) de milhares de faturas em PDF. Após extrair, quer classificar as faturas por urgência. Quais serviços, em ordem, atendem a esse pipeline?

A) Amazon Rekognition → Amazon Comprehend  
B) Amazon Textract → Amazon Comprehend (custom classification)  
C) Amazon Comprehend → Amazon Textract  
D) Amazon Kendra → Amazon Lex  

---

### 13.
Uma empresa quer construir um chatbot que responde perguntas sobre produtos usando um Large Language Model. O LLM gera respostas fluentes mas ocasionalmente inventa especificações técnicas que não existem. Qual afirmação MELHOR descreve esse comportamento e a solução recomendada?

A) O modelo está com underfitting; a solução é treinar com mais dados de produtos  
B) O modelo está alucinando; a solução é implementar RAG para ancorar respostas em documentação real  
C) O modelo precisa de temperature mais alta para gerar respostas mais precisas  
D) O modelo precisa de fine-tuning para aprender todas as especificações  

---

### 14.
Um arquiteto está avaliando diferentes Foundation Models para uma aplicação. O modelo precisa processar documentos que contêm tanto texto quanto imagens (diagramas técnicos) para responder perguntas. Qual capacidade do modelo é ESSENCIAL?

A) Alta context window  
B) Capacidade multimodal (processar texto e imagem)  
C) Suporte a fine-tuning  
D) Baixo custo por token  

---

### 15.
Uma empresa está decidindo entre usar um modelo decoder-only (como Claude) e um modelo encoder-only (como BERT) para seu caso de uso. Qual cenário é MAIS adequado para um modelo encoder-only?

A) Gerar respostas longas para perguntas de clientes  
B) Classificar tickets de suporte em categorias predefinidas  
C) Criar resumos de documentos  
D) Manter conversas multi-turno com clientes  

---

### 16.
Uma empresa precisa que seu LLM gere SEMPRE a mesma resposta para perguntas factuais idênticas (como "Qual é a política de devolução?"), garantindo consistência no atendimento. Qual configuração de inferência atende esse requisito?

A) Temperature = 1.0 e top-p = 0.95 para máxima qualidade  
B) Temperature = 0 para respostas determinísticas  
C) Max tokens = 1000 para respostas completas  
D) Top-k = 100 para considerar mais opções  

---

### 17.
Uma empresa está comparando custos de usar um LLM. A aplicação envia prompts longos (3.000 tokens em média) mas espera respostas curtas (100 tokens). Qual fator de custo será DOMINANTE e como otimizar?

A) Tokens de saída dominam; reduzir max_tokens  
B) Tokens de entrada dominam; reduzir o tamanho do prompt  
C) Ambos custam igual; não há otimização possível  
D) O custo é fixo por request independente de tokens  

---

### 18.
Um desenvolvedor precisa que o LLM resolva o seguinte problema: "Uma loja vende 3 tipos de produto. Produto A custa R$10 com 20% de desconto. Produto B custa R$25 sem desconto. O cliente comprou 2 do A e 1 do B. Calcule o total." Qual técnica de prompt MAIS aumenta a chance de resposta correta?

A) Zero-shot direto  
B) Few-shot com exemplos de outros cálculos  
C) Chain-of-thought pedindo raciocínio passo a passo  
D) Aumentar temperature para explorar mais possibilidades  

---

### 19.
Qual afirmação sobre embeddings está CORRETA?

A) Embeddings são representações vetoriais onde textos semanticamente similares ficam próximos no espaço vetorial  
B) Embeddings são usados exclusivamente para tradução automática  
C) Embeddings convertem vetores em texto legível  
D) Embeddings funcionam apenas com idioma inglês  

---

### 20.
Uma empresa usa Amazon Bedrock e quer testar qual Foundation Model (Claude, Titan ou Llama) gera as melhores respostas para perguntas de suporte técnico. A empresa tem 500 pares de pergunta/resposta-esperada. Qual funcionalidade do Bedrock é MAIS adequada?

A) Bedrock Knowledge Bases com os 3 modelos  
B) Bedrock Model Evaluation com dataset customizado  
C) Bedrock Agents testando cada modelo  
D) Fine-tuning dos 3 modelos e comparação manual  

---

### 21.
Uma empresa quer que seu chatbot funcione em português, mas tem mais dados de treinamento em inglês. O modelo responde melhor em inglês. Qual afirmação sobre tokens e idiomas é CORRETA?

A) Todos os idiomas usam o mesmo número de tokens para conteúdo equivalente  
B) Português geralmente requer mais tokens que inglês para o mesmo conteúdo, aumentando custo e usando mais context window  
C) O idioma não afeta a tokenização  
D) Modelos não podem processar português  

---

### 22.
Uma empresa quer um chatbot empresarial que responda perguntas usando documentos internos do SharePoint e Confluence, respeitando as permissões de acesso existentes (cada funcionário só vê documentos que tem permissão). Qual serviço AWS atende TODOS esses requisitos?

A) Amazon Bedrock com Knowledge Bases  
B) Amazon Q Business  
C) Amazon Kendra  
D) PartyRock  

---

### 23.
Uma empresa está decidindo entre usar Amazon Bedrock (API) versus hospedar um modelo open-weight (Llama) no SageMaker. Qual cenário justifica MELHOR a hospedagem própria no SageMaker?

A) A empresa quer o menor esforço operacional possível  
B) A empresa precisa de controle total sobre a infraestrutura e customizações profundas no modelo  
C) A empresa quer acesso a múltiplos provedores de modelos  
D) A empresa quer escalar automaticamente sem gerenciar servidores  

---

### 24.
Uma equipe de inovação quer demonstrar rapidamente o valor de IA generativa para a diretoria, criando um protótipo funcional de chatbot em menos de 1 hora, sem código e sem custo. Qual ferramenta é MAIS adequada?

A) Amazon Bedrock com Claude  
B) Amazon SageMaker JumpStart  
C) PartyRock  
D) Amazon Q Developer  

---

### 25.
Qual processo no treinamento de LLMs modernos usa feedback humano para ensinar o modelo a ser mais útil, inofensivo e honesto, APÓS o pré-treinamento inicial?

A) Self-supervised pre-training  
B) RLHF (Reinforcement Learning from Human Feedback)  
C) Transfer Learning  
D) Continued Pre-training  

---

### 26.
Uma empresa testou prompt engineering para gerar emails de vendas. As respostas são corretas mas o tom é inconsistente — às vezes formal demais, às vezes casual. O prompt já inclui instruções detalhadas de tom. Qual é o PRÓXIMO passo recomendado?

A) Implementar RAG com exemplos de emails anteriores  
B) Fine-tuning com centenas de exemplos de emails no tom desejado  
C) Aumentar a temperature para mais variação  
D) Trocar o Foundation Model por um menor  

---

### 27.
Um desenvolvedor está usando Amazon Q Developer no IDE. Qual das seguintes NÃO é uma capacidade do serviço?

A) Gerar código a partir de comentários em linguagem natural  
B) Explicar código legado complexo  
C) Treinar modelos customizados de ML  
D) Sugerir correções de bugs e vulnerabilidades  

---

### 28.
Uma empresa implementou RAG com Bedrock Knowledge Bases. Os documentos fonte são manuais técnicos atualizados trimestralmente. A equipe quer que as respostas do chatbot reflitam SEMPRE a versão mais recente. Qual ação é necessária quando os manuais são atualizados?

A) Re-treinar (fine-tuning) o Foundation Model com os novos manuais  
B) Sincronizar/re-indexar os documentos na Knowledge Base  
C) Alterar o system prompt para mencionar a nova versão  
D) Trocar o Foundation Model por uma versão mais recente  

---

### 29.
Uma equipe está projetando uma arquitetura RAG. Os documentos são manuais técnicos de 200+ páginas. As perguntas dos usuários são específicas (ex: "Qual é a pressão máxima da válvula X?"). A equipe está obtendo respostas irrelevantes. Qual ajuste na pipeline de RAG MAIS provavelmente resolve o problema?

A) Usar um Foundation Model maior  
B) Reduzir o tamanho dos chunks e melhorar o modelo de embeddings  
C) Aumentar a temperature do FM  
D) Adicionar mais documentos à base  

---

### 30.
Um chatbot de suporte precisa: (1) responder perguntas sobre produtos usando documentação e (2) criar tickets no sistema JIRA quando o cliente pede. Qual arquitetura Bedrock é MÍNIMA necessária?

A) Apenas Knowledge Bases  
B) Apenas Guardrails  
C) Agent com Knowledge Base (para docs) + Action Group (para criar tickets)  
D) Apenas Fine-tuning  

---

### 31.
Uma empresa já tem RAG funcionando bem para perguntas sobre docs. Agora quer que o chatbot TAMBÉM processe devoluções consultando a API de pedidos e atualizando o status. O que ADICIONAR à arquitetura?

A) Mais documentos na Knowledge Base  
B) Fine-tuning do modelo  
C) Bedrock Agent com Action Groups que chamam a API de pedidos  
D) Guardrails mais restritivos  

---

### 32.
Uma empresa precisa gerar resumos de 500.000 contratos legais armazenados no S3. Não há urgência — o resultado pode levar dias. O custo deve ser minimizado. Qual abordagem no Bedrock é MAIS econômica?

A) Invocar o modelo via API on-demand para cada contrato sequencialmente  
B) Usar batch inference para processar todos os contratos em lote  
C) Configurar Provisioned Throughput e processar em tempo real  
D) Fine-tuning de um modelo específico para contratos legais  

---

### 33.
Qual afirmação sobre ROUGE e BLEU está CORRETA?

A) ROUGE é usada para avaliar tradução; BLEU é usada para avaliar resumos  
B) ROUGE mede recall de n-grams (orientada a resumos); BLEU mede precisão de n-grams (orientada a tradução)  
C) Ambas medem exatamente a mesma coisa  
D) ROUGE e BLEU são métricas de classificação  

---

### 34.
Uma empresa quer reduzir custos de inferência para uma tarefa de classificação de sentimento (positivo/negativo/neutro) que atualmente usa um modelo grande. As respostas estão corretas mas o custo é alto. Qual estratégia combina menor custo COM manutenção da qualidade?

A) Trocar para um modelo menor que ainda atinge acurácia aceitável para a tarefa  
B) Aumentar temperature para respostas mais curtas  
C) Remover o system prompt para economizar tokens  
D) Usar Provisioned Throughput com o mesmo modelo grande  

---

### 35.
Uma empresa quer que seu LLM entenda profundamente jargão e terminologia de engenharia civil que modelos gerais não conhecem bem. Prompt engineering com termos técnicos no system prompt não é suficiente — o modelo confunde termos. Qual abordagem resolve MAIS profundamente esse problema?

A) RAG com normas técnicas de engenharia civil  
B) Continued pre-training com grandes volumes de texto de engenharia civil  
C) Few-shot com exemplos de termos  
D) Aumentar context window  

---

### 36.
Qual é a PRINCIPAL diferença funcional entre Bedrock Knowledge Bases e Bedrock Agents?

A) Knowledge Bases são mais caras que Agents  
B) Knowledge Bases buscam informação para fundamentar respostas; Agents podem buscar informação E executar ações em sistemas externos  
C) Agents não podem acessar Knowledge Bases  
D) Knowledge Bases requerem fine-tuning; Agents não  

---

### 37.
Uma empresa está decidindo o modelo de precificação do Bedrock. A aplicação tem tráfego previsível de 10.000 requests/hora durante horário comercial e zero fora. Qual modelo de pricing é MAIS econômico?

A) On-demand (paga por token)  
B) Provisioned Throughput (capacidade reservada)  
C) Batch inference  
D) Free tier  

---

### 38.
Uma empresa quer bloquear o chatbot de responder sobre 3 temas: concorrentes, política e religião. Também quer mascarar qualquer CPF ou email que apareça nas respostas. Qual funcionalidade do Bedrock configura AMBOS os requisitos em um único lugar?

A) Knowledge Bases com filtros  
B) Guardrails (denied topics + PII filters)  
C) Fine-tuning com exemplos negativos  
D) System prompt com instruções  

---

### 39.
Uma empresa de e-commerce quer recomendar produtos a usuários usando dados de comportamento (cliques, compras, tempo na página). A empresa NÃO quer construir algoritmos de recomendação do zero. Qual serviço oferece recomendações gerenciadas com o menor esforço?

A) Amazon Bedrock com prompt engineering  
B) Amazon Personalize  
C) Amazon SageMaker com modelo customizado  
D) Amazon Comprehend  

---

### 40.
Em uma arquitetura RAG, o que "cosine similarity" mede quando busca chunks relevantes?

A) O tamanho dos vetores  
B) A similaridade direcional (ângulo) entre o vetor da query e os vetores dos chunks  
C) A distância física entre servidores  
D) O número de tokens em comum  

---

### 41.
Uma empresa implementou um Agent que pode consultar o sistema de pedidos e processar devoluções. O Agent está funcionando, mas ocasionalmente executa devoluções para pedidos que não são elegíveis (prazo expirado). Qual camada adicional ajuda a prevenir esse comportamento?

A) Aumentar temperature  
B) Adicionar validações na Lambda function do Action Group (verificar elegibilidade antes de executar)  
C) Usar um modelo menor  
D) Remover a Knowledge Base  

---

### 42.
Uma empresa precisa decidir entre Bedrock on-demand e Provisioned Throughput. Qual cenário justifica MELHOR o uso de Provisioned Throughput?

A) Prototipagem com volume baixo e imprevisível  
B) Carga constante e previsível onde latência consistente é crítica  
C) Processamento único de um grande lote de dados  
D) Uso esporádico por poucos usuários internos  

---

### 43.
Qual afirmação sobre fine-tuning no Amazon Bedrock está CORRETA?

A) Fine-tuning altera o modelo base compartilhado com todos os clientes  
B) Fine-tuning cria uma cópia privada do modelo ajustada com seus dados, sem afetar o modelo base  
C) Fine-tuning não requer nenhum dado — apenas configuração  
D) Fine-tuning está disponível para todos os modelos no Bedrock  

---

### 44.
Uma empresa quer que avaliadores humanos internos classifiquem a qualidade das respostas de seu chatbot em escalas de 1-5 para "utilidade" e "factualidade". Qual funcionalidade do Bedrock suporta isso nativamente?

A) Guardrails  
B) Model Evaluation (com avaliação humana)  
C) Agents  
D) Knowledge Bases  

---

### 45.
Um modelo de concessão de crédito está aprovando 90% dos candidatos de uma região urbana rica mas apenas 50% de uma região rural de baixa renda, para candidatos com perfis financeiros similares. Qual PRIMEIRA ação a equipe deve tomar?

A) Remover a variável "região" do modelo e re-treinar  
B) Usar SageMaker Clarify para analisar métricas de viés por subgrupo e entender a causa raiz  
C) Ignorar, pois a diferença pode ser justificada  
D) Aplicar o mesmo threshold de aprovação para todos  

---

### 46.
Uma empresa de saúde usa IA para pré-triagem de exames de imagem. Quando a confiança do modelo está abaixo de 90%, o caso deve ser encaminhado para revisão por um radiologista. Qual arquitetura implementa esse fluxo?

A) SageMaker Model Monitor  
B) Amazon Augmented AI (A2I) com threshold de confiança configurado  
C) Bedrock Guardrails  
D) SageMaker Clarify  

---

### 47.
Uma regulamentação exige que a empresa explique a clientes POR QUE seus pedidos de empréstimo foram negados, identificando os fatores que mais contribuíram para a decisão. Qual ferramenta AWS fornece essa explicação?

A) Amazon CloudWatch  
B) SageMaker Clarify (SHAP values / feature importance)  
C) AWS CloudTrail  
D) Amazon Bedrock Guardrails  

---

### 48.
Uma empresa está usando Bedrock Guardrails com "grounding check" habilitado. O que esse recurso detecta?

A) Quando o modelo está lento  
B) Quando o modelo gera informação que NÃO está presente no contexto fornecido (potencial alucinação)  
C) Quando o modelo recusa responder  
D) Quando o modelo usa linguagem informal  

---

### 49.
Uma empresa publicou seu modelo de classificação de imagens e quer documentar para a comunidade: para que o modelo foi projetado, suas limitações conhecidas, métricas de fairness por grupo demográfico, e práticas recomendadas de uso. Qual artefato deve criar?

A) Um README no GitHub  
B) SageMaker Model Card com documentação estruturada  
C) Um endpoint de monitoramento  
D) Uma AWS AI Service Card  

---

### 50.
Um modelo de IA é treinado com dados de currículos de funcionários contratados nos últimos 10 anos. A empresa historicamente contratou predominantemente homens para cargos de engenharia. O modelo agora penaliza candidatas mulheres. Qual tipo de viés E solução são mais relevantes?

A) Viés de medição; usar métricas diferentes  
B) Viés histórico; coletar dados mais diversos e aplicar técnicas de debiasing  
C) Viés algorítmico; trocar o algoritmo  
D) Viés de automação; desativar o modelo  

---

### 51.
Qual é a diferença entre AWS AI Service Cards e SageMaker Model Cards?

A) São o mesmo documento  
B) AI Service Cards documentam serviços gerenciados da AWS; Model Cards documentam modelos customizados criados pelo cliente  
C) Model Cards são públicos; AI Service Cards são privados  
D) AI Service Cards são para código; Model Cards para dados  

---

### 52.
"Red teaming" no contexto de IA Responsável significa:

A) Usar equipes vestindo camisetas vermelhas para testar o sistema  
B) Testar proativamente o modelo com inputs adversariais para encontrar falhas, viés e vulnerabilidades antes do deploy  
C) Treinar o modelo com dados rotulados em vermelho  
D) Monitorar métricas em dashboard vermelho  

---

### 53.
Uma empresa tem requisitos regulatórios que exigem: (1) todo acesso ao Bedrock deve ser auditável e (2) o tráfego não pode transitar pela internet pública. Quais DOIS serviços/recursos atendem respectivamente esses requisitos?

A) CloudWatch para auditoria + Security Groups para tráfego  
B) CloudTrail para auditoria + VPC Endpoints (PrivateLink) para tráfego privado  
C) Macie para auditoria + HTTPS para tráfego  
D) Config para auditoria + WAF para tráfego  

---

### 54.
Uma empresa quer garantir que apenas a equipe de ML possa invocar endpoints SageMaker, que a equipe de dados possa acessar apenas os buckets S3 de dados, e que ninguém possa acessar as chaves KMS sem aprovação. Qual princípio de segurança está sendo aplicado?

A) Defense in depth  
B) Least privilege (menor privilégio) com separação de responsabilidades  
C) Zero trust  
D) Security through obscurity  

---

### 55.
Uma empresa quer que prompts e respostas do Bedrock sejam registrados para auditoria posterior, mas está preocupada que esses logs possam conter dados sensíveis de clientes. Qual combinação de medidas é MAIS adequada?

A) Desabilitar logging completamente  
B) Habilitar Model Invocation Logging com acesso restrito (IAM) + criptografia (KMS)  
C) Salvar logs em bucket S3 público para transparência  
D) Usar apenas CloudTrail que já registra tudo  

---

### 56.
Uma equipe quer automatizar o pipeline: quando novos dados chegam ao S3 → processamento automático → re-treinamento → avaliação → se métricas OK → registrar modelo → aprovar → deploy. Qual serviço orquestra todo esse fluxo?

A) AWS Step Functions  
B) SageMaker Pipelines  
C) Amazon EventBridge  
D) AWS CodePipeline  

---

### 57.
Uma organização com 50 contas AWS quer garantir que NENHUMA conta possa usar certos Foundation Models no Bedrock considerados de alto risco. Qual mecanismo aplica essa restrição organizacional?

A) IAM policies em cada conta  
B) Service Control Policies (SCPs) no AWS Organizations  
C) Security Groups  
D) Bedrock Guardrails  

---

### 58.
O que "ML Lineage Tracking" do SageMaker permite que uma equipe faça quando um modelo em produção apresenta previsões incorretas?

A) Corrigir automaticamente as previsões  
B) Rastrear quais dados, transformações e configurações de treino originaram aquele modelo específico  
C) Fazer rollback automático do endpoint  
D) Alertar o usuário final  

---

### 59.
Uma equipe detectou que as previsões de um modelo de recomendação degradaram 15% no último mês. Qual serviço teria detectado isso automaticamente com alertas?

A) AWS CloudTrail  
B) SageMaker Model Monitor + CloudWatch Alarms  
C) Amazon Inspector  
D) AWS Trusted Advisor  

---

### 60. (Múltipla Resposta)
Uma empresa precisa proteger dados de treino de ML em repouso e garantir que chaves de criptografia sejam gerenciadas centralmente. Quais DOIS recursos atendem esses requisitos?

A) VPC Endpoints para tráfego privado  
B) AWS KMS para gerenciamento centralizado de chaves  
C) TLS para criptografia em trânsito  
D) S3 Server-Side Encryption com chaves KMS (SSE-KMS)  
E) Security Groups para controle de rede  

---

## Gabarito

<details>
<summary>🔍 Ver gabarito completo</summary>

| # | Resp | Domínio | Justificativa |
|---|------|---------|---------------|
| 1 | B | D1 | Dados rotulados disponíveis + classificar binário = supervisionado. Clustering (A) não prevê classes. Reforço (C) é para decisões sequenciais. Anomalia (D) funcionaria mas classificação direta com dados rotulados é mais simples. |
| 2 | B | D1 | Gap treino/teste = overfitting. Mais dados não resolveu → regularizar ou reduzir complexidade. C piora, D remove controle de qualidade. |
| 3 | B | D1 | Transcribe (áudio→texto) DEPOIS Comprehend (sentimento do texto). Polly faz o inverso. Ordem importa. |
| 4 | C | D1 | Forecast = gerenciado + séries temporais + sem ML expertise. Autopilot requer mais conhecimento. Personalize é recomendação. Bedrock não é para forecasting tabular. |
| 5 | B | D1 | Underfitting = modelo simples demais. Solução: mais complexidade + features melhores. A e C combatem overfitting (oposto). |
| 6 | B | D1 | 99.7% acurácia com 99.7% de classe negativa = modelo prevê tudo como saudável. Recall da classe positiva seria ~0%. |
| 7 | C | D1 | Validação para tuning durante desenvolvimento; teste reservado para medição final imparcial uma única vez. |
| 8 | B | D1 | "Fraudes não detectadas = perdas" → priorizar recall (detectar todas as fraudes). Modelo A pega 95% das fraudes vs 70% do B. |
| 9 | C | D1 | "Sem programação" + "menor esforço" + "dados tabulares" = Canvas (visual, no-code). Studio requer código. |
| 10 | B | D1 | Prever valor (regressão) + agrupar sem categorias (clustering). Classificação requer categorias predefinidas. |
| 11 | B | D1 | Novos tipos de spam = o QUE é spam mudou (relação input→label). Isso é concept drift, não apenas mudança na distribuição dos inputs. |
| 12 | B | D1 | Textract extrai dados de PDFs → Comprehend classifica o texto extraído. Rekognition é para imagens/objetos, não documentos. |
| 13 | B | D2 | "Inventa especificações" = alucinação. RAG ancora em docs reais. Fine-tuning não garante factualidade. Temperature alta piora. |
| 14 | B | D2 | Processar texto + imagem juntos = multimodal. Context window grande ajuda mas não resolve se o modelo não "vê" imagens. |
| 15 | B | D2 | Encoder-only (BERT) = compreensão/classificação. Decoder-only = geração. Classificar tickets é compreensão. |
| 16 | B | D2 | Temperature 0 = determinístico = mesma resposta sempre para mesmo input. Garante consistência. |
| 17 | B | D2 | 3000 tokens entrada × custo_input vs 100 tokens saída × custo_output. Mesmo com saída mais cara por token, o volume de entrada domina. Otimizar prompt = menos custo. |
| 18 | C | D2 | Problema multi-step com cálculos → chain-of-thought. Few-shot ajuda mas CoT é mais eficaz para raciocínio aritmético. |
| 19 | A | D2 | Embeddings = vetores onde similaridade semântica = proximidade no espaço. Base do RAG e busca semântica. |
| 20 | B | D2 | "Comparar modelos" + "dataset de avaliação" = Model Evaluation. Não é RAG nem Agents (são funcionalidades de produção). |
| 21 | B | D2 | Português usa mais tokens (subwords diferentes) → mais custo e mais context window consumida. |
| 22 | B | D2 | SharePoint + Confluence + permissões de acesso = Amazon Q Business. Bedrock KB não respeita permissões automaticamente. Kendra é busca mas Q Business é mais completo com GenAI. |
| 23 | B | D2 | "Controle total" + "customizações profundas" = SageMaker. Bedrock é para quem quer menor esforço operacional. |
| 24 | C | D2 | "1 hora" + "sem código" + "sem custo" = PartyRock. Bedrock tem custo. SageMaker requer setup. |
| 25 | B | D2 | RLHF = alinhamento pós-pré-treinamento com feedback humano para ser útil/seguro/honesto. |
| 26 | B | D2 | PE já tentado com instruções detalhadas + tom inconsistente = próximo passo é fine-tuning para internalizar o estilo. RAG traz informação, não muda tom. |
| 27 | C | D2 | Q Developer gera/explica/corrige código. NÃO treina modelos de ML — isso é SageMaker. |
| 28 | B | D3 | RAG = re-indexar quando docs mudam. O FM não precisa ser re-treinado. System prompt não resolve (info está nos docs). |
| 29 | B | D3 | Perguntas específicas + docs longos + respostas irrelevantes = chunks muito grandes (contexto diluído) ou embeddings ruins. Reduzir chunks melhora precisão. |
| 30 | C | D3 | Responder perguntas (KB) + executar ação em JIRA (Action Group) = Agent completo. Apenas KB não cria tickets. |
| 31 | C | D3 | RAG funciona para leitura. Para AÇÕES (processar devolução, atualizar status) precisa de Agent com Action Groups. |
| 32 | B | D3 | "Sem urgência" + "minimizar custo" + volume alto = batch inference (processamento em lote com desconto). |
| 33 | B | D3 | ROUGE = recall-oriented (resumos). BLEU = precision-oriented (tradução). Medem coisas complementares. |
| 34 | A | D3 | Tarefa simples (3 classes) → modelo menor é suficiente e muito mais barato. Temperature/system prompt não afetam custo significativamente. PT com modelo grande = mais caro. |
| 35 | B | D3 | "Modelo confunde termos" = não ENTENDE o domínio. Continued pre-training ensina vocabulário novo. RAG traz info mas modelo pode não interpretar corretamente se não entende os termos. |
| 36 | B | D3 | KB = RAG (busca + resposta). Agents = busca + ações. Agents PODEM usar KBs como fonte de informação. |
| 37 | B | D3 | Tráfego previsível + constante em horário comercial = Provisioned Throughput (preço por tempo, capacidade garantida). On-demand = bom para imprevisível. |
| 38 | B | D3 | Denied topics (3 temas bloqueados) + PII filters (CPF/email) = Guardrails. System prompt pode ser contornado. Fine-tuning não bloqueia confiávelmente. |
| 39 | B | D3 | "Recomendações gerenciadas" + "menor esforço" = Personalize. Bedrock pode mas requer construir a lógica. SageMaker requer construir tudo. |
| 40 | B | D3 | Cosine similarity = ângulo entre vetores = mede direção/significado similar, não magnitude. Base da busca semântica. |
| 41 | B | D3 | Agent executa ações via Lambda. Validações de negócio (elegibilidade) devem estar na Lambda, não no FM. O FM decide "quero cancelar", a Lambda valida "posso cancelar?". |
| 42 | B | D3 | PT = latência consistente + capacidade garantida + volume constante. On-demand = variável. Batch = sem latência. |
| 43 | B | D3 | Fine-tuning no Bedrock cria CÓPIA PRIVADA. Não altera o modelo base compartilhado. Seus dados não afetam outros clientes. |
| 44 | B | D3 | Avaliação humana com escala customizada = Model Evaluation (human evaluation workflow). Guardrails filtram, não avaliam qualidade. |
| 45 | B | D4 | Primeiro: entender a causa com dados (Clarify). Remover feature direto (A) pode não resolver (proxies). Ignorar (C) é irresponsável. Threshold fixo (D) não endereça a causa. |
| 46 | B | D4 | Confiança < threshold → encaminhar para humano = A2I (Augmented AI). Model Monitor detecta drift, não encaminha para revisão. |
| 47 | B | D4 | "Explicar POR QUE" + "fatores que contribuíram" = SHAP values do Clarify. CloudTrail = quem chamou API. CloudWatch = métricas. |
| 48 | B | D4 | Grounding check = verifica se a resposta está fundamentada no contexto fornecido. Detecta quando o modelo "inventa" informação. |
| 49 | B | D4 | Modelo CUSTOMIZADO do cliente → Model Card. AI Service Cards são da AWS sobre seus serviços gerenciados. README não é estruturado. |
| 50 | B | D4 | Dados refletem discriminação histórica = viés histórico. Solução: dados mais diversos + debiasing técnico (Clarify pode ajudar). |
| 51 | B | D4 | AI Service Cards = AWS documenta SEUS serviços. Model Cards = VOCÊ documenta SEU modelo. Diferentes autores e propósitos. |
| 52 | B | D4 | Red teaming = teste adversarial proativo. Encontrar falhas antes que usuários encontrem. Prática de segurança de IA. |
| 53 | B | D5 | CloudTrail = auditoria de API calls. VPC Endpoints = tráfego privado sem internet. CloudWatch é métricas, não auditoria. |
| 54 | B | D5 | Cada equipe só tem as permissões que precisa = least privilege. Separação clara entre papéis = separação de responsabilidades. |
| 55 | B | D5 | Logging necessário para auditoria, mas proteger com IAM (quem acessa) + KMS (criptografar logs). Desabilitar (A) viola requisito. Público (C) é inseguro. |
| 56 | B | D5 | Pipeline completo de ML (dados → treino → avaliação → registro → deploy) = SageMaker Pipelines. Step Functions é genérico. CodePipeline é para app code. |
| 57 | B | D5 | Restrição organizacional em 50 contas = SCPs. IAM individual não escala. Security Groups = rede. Guardrails = conteúdo. |
| 58 | B | D5 | Lineage = rastrear origem. "Qual dado treinou esse modelo?" + "Quais transformações foram aplicadas?" Essencial para debugging. |
| 59 | B | D5 | Model Monitor detecta degradação + CloudWatch Alarms notifica. CloudTrail = API calls. Inspector = vulnerabilidades. |
| 60 | B,D | D5 | KMS = gerenciamento centralizado de chaves. SSE-KMS = criptografia em repouso usando essas chaves. VPC/TLS = tráfego, não repouso. |

---

### Cálculo de Resultado

- **54-60 corretas (90%+):** Excelente — muito provavelmente aprovado
- **48-53 corretas (80-89%):** Bom — confortavelmente acima do threshold
- **42-47 corretas (70-79%):** Na borda — revise os domínios com mais erros
- **<42 corretas (<70%):** Precisa de mais estudo — foque nos domínios fracos

**Distribuição dos seus erros por domínio ajuda a priorizar a revisão.**

</details>

