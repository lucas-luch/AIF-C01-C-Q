# Serviços AWS de IA Generativa

## Visão Geral

A AWS oferece um ecossistema de serviços para IA generativa. A prova AIF-C01 foca em **quando usar cada um** e suas diferenças.

---

## Amazon Bedrock

O serviço principal de IA generativa da AWS.

### O que é
- Plataforma **serverless** para acessar Foundation Models via API
- Não precisa gerenciar infraestrutura
- Acesso a modelos de múltiplos provedores

### Modelos disponíveis
| Provedor | Modelos |
|----------|---------|
| Anthropic | Claude (texto, multimodal) |
| Amazon | Titan Text, Titan Embeddings, Titan Image |
| Meta | Llama |
| Mistral AI | Mistral, Mixtral |
| Cohere | Command, Embed |
| Stability AI | Stable Diffusion (imagens) |

### Funcionalidades-chave
| Feature | O que faz |
|---------|-----------|
| **Knowledge Bases** | Conecta FMs a dados (RAG gerenciado) |
| **Agents** | FMs que executam ações (chamam APIs, Lambda) |
| **Guardrails** | Filtros de conteúdo, PII, tópicos bloqueados |
| **Fine-tuning** | Ajustar modelo com seus dados |
| **Continued Pre-training** | Treinar com dados adicionais do domínio |
| **Model Evaluation** | Comparar modelos em métricas específicas |
| **Provisioned Throughput** | Capacidade dedicada para workloads consistentes |

### Privacidade e Segurança
- Seus dados **NÃO** são usados para treinar os modelos base
- Dados processados em sua região AWS
- Criptografia em trânsito e repouso
- Integração com IAM, CloudTrail, VPC

---

## Amazon Titan

Família de Foundation Models desenvolvidos pela própria AWS.

| Modelo | Tipo | Uso |
|--------|------|-----|
| Titan Text | Geração de texto | Resumo, chat, geração de conteúdo |
| Titan Embeddings | Vetores | Busca semântica, RAG |
| Titan Image Generator | Imagens | Geração e edição de imagens |
| Titan Multimodal Embeddings | Vetores multimodais | Busca por texto E imagem |

### Diferencial do Titan
- Treinados pela AWS com foco em segurança e responsabilidade
- Built-in watermarking em imagens geradas (rastreabilidade)
- Integração nativa com serviços AWS

---

## Amazon Q

Assistente de IA generativa da AWS para **produtividade empresarial**.

### Amazon Q Business
- Chatbot empresarial conectado a dados da empresa
- Integra com: S3, SharePoint, Salesforce, Confluence, Slack, etc.
- Responde perguntas com base nos documentos internos
- Controle de acesso (respeita permissões existentes)

### Amazon Q Developer
- Assistente de código para desenvolvedores
- Funções: geração de código, explicação, debugging, transformação
- Integrado em IDEs (VS Code, IntelliJ, etc.)
- Pode analisar e modernizar aplicações legadas

### Amazon Q in QuickSight
- IA generativa para Business Intelligence
- Gerar dashboards e análises com linguagem natural

---

## PartyRock

### O que é
- **Playground gratuito** para criar apps com IA generativa sem código
- Não requer conta AWS nem cartão de crédito
- Interface visual: arraste widgets (texto, imagem, chatbot)

### Quando usar
- Aprendizado e experimentação
- Prototipagem rápida de ideias
- Demonstrações e provas de conceito
- Educação sobre IA generativa

### Limitações
- Não é para produção
- Modelos e capacidades limitadas vs Bedrock completo
- Sem integração com infraestrutura AWS

---

## Comparação: Quando Usar Cada Um

| Necessidade | Serviço |
|-------------|---------|
| Construir app GenAI em produção | **Amazon Bedrock** |
| Experimentar GenAI sem código e sem custo | **PartyRock** |
| Chatbot empresarial com dados internos + permissões | **Amazon Q Business** |
| Busca empresarial inteligente (sem geração) | **Amazon Kendra** |
| Assistente de código no IDE | **Amazon Q Developer** |
| Embeddings para busca semântica | **Bedrock + Titan Embeddings** |
| Gerar imagens com IA | **Bedrock + Stable Diffusion ou Titan Image** |
| ML sem código (dados tabulares) | **SageMaker Canvas** (não GenAI) |

### Amazon Q Business vs Amazon Kendra — Diferença Sutil

| Aspecto | Amazon Kendra | Amazon Q Business |
|---------|--------------|-------------------|
| **O que faz** | Busca empresarial com NLP (retorna trechos relevantes) | Assistente GenAI completo (gera respostas elaboradas) |
| **Saída** | Links e trechos de documentos relevantes | Resposta gerada em linguagem natural com citações |
| **Permissões** | Suporta ACLs | Respeita permissões existentes nativamente |
| **Integrações** | Conectores para múltiplas fontes | Conectores + plugins para ações |
| **Quando usar** | Quando quer busca (encontrar documentos) | Quando quer respostas (entender + sintetizar) |
| **Na prova** | "Buscar documentos relevantes" | "Responder perguntas usando dados internos com controle de acesso" |

**Dica para a prova:** Se o cenário menciona "responder perguntas" + "documentos internos" + "permissões de acesso" → **Q Business**. Se menciona apenas "encontrar documentos relevantes" ou "busca" → **Kendra**.

---

## Bedrock — Detalhes de Precificação

| Modelo de Pricing | Como funciona | Quando usar |
|-------------------|---------------|-------------|
| **On-demand** | Paga por token (entrada + saída separados) | Volume variável, prototipagem, baixo volume |
| **Provisioned Throughput** | Paga por unidade de capacidade/tempo (reservada) | Volume alto e constante, latência consistente |
| **Batch inference** | Paga por token com desconto (~50% off) | Volume alto sem urgência (pode levar horas) |

### Detalhes importantes para a prova
- **Tokens de saída são mais caros** que de entrada (geralmente 3-5x mais)
- **Modelos maiores** custam mais por token que menores
- **Provisioned Throughput** faz sentido quando o custo on-demand excede o custo reservado (volume previsível)
- **Batch** tem desconto significativo mas não é real-time

### Cenários de otimização de custo
| Cenário | Solução mais econômica |
|---------|----------------------|
| 10 requests/dia | On-demand |
| 10.000 requests/hora constantes | Provisioned Throughput |
| Processar 500K docs uma vez | Batch inference |
| Tarefa simples (classificação) | Modelo menor on-demand |
| 80% das perguntas são repetidas | Cache + on-demand |
| Prompts muito longos | Encurtar prompts (menos tokens de entrada) |

---

## Bedrock — Model Customization Options

| Opção | Dados necessários | O que muda | Custo | Quando usar |
|-------|-------------------|-----------|-------|-------------|
| **Prompt Engineering** | Nenhum | Nada no modelo | Zero | Primeiro passo sempre |
| **RAG (Knowledge Bases)** | Documentos (S3, web) | Nada no modelo (busca externa) | Médio (infra) | Dados atualizados/proprietários |
| **Fine-tuning** | Pares input/output (centenas-milhares) | Ajusta pesos (comportamento) | Alto | Tom/estilo/formato específico |
| **Continued Pre-training** | Texto corrido do domínio (milhões de tokens) | Ajusta pesos (conhecimento) | Muito alto | Terminologia nova que o modelo não entende |
| **Custom Model Import** | Modelo já treinado externamente | Traz seu modelo para o Bedrock | Variável | Modelo open-weight customizado fora da AWS |

---

## Resumo para a Prova

| Pergunta | Resposta |
|----------|----------|
| "Acesso serverless a múltiplos FMs?" | Amazon Bedrock |
| "FM da própria AWS?" | Amazon Titan |
| "Assistente GenAI para empresas?" | Amazon Q Business |
| "Assistente de código?" | Amazon Q Developer |
| "Experimentar GenAI grátis sem conta AWS?" | PartyRock |
| "RAG gerenciado?" | Bedrock Knowledge Bases |
| "FM que executa ações?" | Bedrock Agents |
| "Filtrar conteúdo inadequado?" | Bedrock Guardrails |
| "Dados do cliente usados para treinar modelos?" | NÃO — Bedrock garante privacidade |

---

*Próximo: Mini-simulado Domínio 2*
