# Serviços AWS de IA Generativa

## Visão Geral

A AWS oferece um ecossistema de serviços para IA generativa. A prova AIF-C01 foca em **quando usar cada um**, suas diferenças, as vantagens da infraestrutura AWS e os trade-offs de custo.

---

## Amazon Bedrock

O serviço central de IA generativa da AWS.

### O que é
- Plataforma **serverless** para acessar Foundation Models via API
- Não precisa gerenciar infraestrutura de modelo
- Acesso a modelos de múltiplos provedores em uma única interface

### Modelos disponíveis (exemplos)

| Provedor | Modelos | Tipo |
|----------|---------|------|
| AWS | Amazon Nova (Pro, Lite, Micro, Canvas, Reel) | Texto, multimodal, imagem, vídeo |
| AWS | Amazon Titan (Text, Embeddings, Image) | Texto, embeddings, imagem |
| Anthropic | Claude | Texto, multimodal |
| Meta | Llama | Texto (open-weight) |
| Mistral AI | Mistral, Mixtral | Texto |
| Cohere | Command, Embed | Texto, embeddings |
| Stability AI | Stable Diffusion | Imagem |

> **Nota:** A lista de modelos é dinâmica. Para a prova, entenda os tipos e critérios de seleção, não memorize modelos específicos.

### Funcionalidades-chave

| Feature | O que faz |
|---------|-----------|
| **Knowledge Bases** | RAG gerenciado — conecta FMs a dados (S3, web) |
| **Agents** | FMs que executam ações (tool use, APIs, Lambda) |
| **Guardrails** | Filtros de conteúdo, PII, tópicos bloqueados, segurança |
| **Fine-tuning** | Ajustar modelo com dados próprios |
| **Continued Pre-training** | Treinar com dados adicionais do domínio |
| **Model Evaluation** | Comparar modelos com métricas automáticas e humanas |
| **Prompt Management** | Versionamento e gerenciamento de prompts |
| **Provisioned Throughput** | Capacidade dedicada para workloads consistentes |
| **Batch Inference** | Processar grandes volumes com desconto |

### Privacidade e Segurança no Bedrock

- No Amazon Bedrock, os dados do cliente **não são usados para treinar ou melhorar os modelos base** — esta é uma política específica do Bedrock
- Dados processados na região AWS selecionada
- Criptografia em trânsito e em repouso
- Integração com IAM, CloudTrail, VPC (PrivateLink)
- Isolamento de dados entre clientes

> **CUIDADO:** A garantia de que "dados não treinam modelos" é uma política do Amazon Bedrock especificamente. Não generalize para todos os serviços ou provedores.

---

## Amazon Nova

Família de Foundation Models **desenvolvidos pela AWS**, otimizados para diferentes trade-offs de custo e performance.

| Modelo | Tipo | Otimizado para |
|--------|------|---------------|
| **Nova Micro** | Texto | Latência mínima e custo mais baixo |
| **Nova Lite** | Texto, multimodal | Equilíbrio custo-performance |
| **Nova Pro** | Texto, multimodal | Capacidade máxima |
| **Nova Canvas** | Imagem | Geração e edição de imagens |
| **Nova Reel** | Vídeo | Geração de vídeo |

### Diferenciais
- Treinados pela AWS com foco em segurança e responsabilidade
- Otimizados para a infraestrutura AWS (latência, custo)
- Integração nativa com serviços Bedrock (Guardrails, Knowledge Bases, Agents)

> **DICA PARA A PROVA:** Se a questão menciona "FM da AWS" ou "modelo nativo da AWS otimizado para custo", pense em Amazon Nova. Se menciona "embeddings AWS", pode ser Amazon Titan Embeddings.

---

## Amazon Bedrock AgentCore

Infraestrutura gerenciada para **deploy, segurança e governança de agentes de IA** em produção.

### Componentes

| Componente | Função |
|-----------|--------|
| **Runtime** | Ambiente de execução gerenciado para agentes |
| **Identity** | Gerenciamento de identidade e autenticação de agentes |
| **Gateway** | Ponto de entrada e roteamento para agentes |
| **Memory** | Gerenciamento de memória de curto e longo prazo |
| **Observability** | Monitoramento, logging e tracing de agentes |
| **Policy** | Regras e permissões que controlam o que agentes podem fazer |

### Quando usar
- Agentes em produção que precisam de segurança e controle
- Quando é necessário governança sobre o que agentes podem acessar/fazer
- Ambientes enterprise com requisitos de compliance

> **DICA PARA A PROVA:** Se a questão menciona "segurança de agentes em produção", "controle de identidade de agentes" ou "governança de agentes", pense em Amazon Bedrock AgentCore. Se menciona "criar agentes que executam ações", pense em Agentes do Amazon Bedrock.

---

## Amazon Q

Assistente de IA generativa da AWS.

### Amazon Q Business
- Chatbot empresarial conectado a dados da organização
- Integra com: S3, SharePoint, Salesforce, Confluence, Slack, etc.
- Responde perguntas com base nos documentos internos
- **Respeita permissões existentes** (controle de acesso nativo)

### Amazon Q Developer
- Assistente de código para desenvolvedores
- Geração, explicação, debugging, refatoração de código
- Análise e modernização de aplicações legadas
- Integrado em IDEs

---

## Ferramentas de Desenvolvimento com IA

| Serviço | O que faz | Quando usar |
|---------|-----------|-------------|
| **Kiro** | IDE com IA integrada (specs, agentes, hooks) | Desenvolvimento assistido por IA completo |
| **Strands Agents** | Framework open-source para construir agentes de IA | Desenvolver agentes customizados com controle total |
| **Amazon Q Developer** | Assistente de código em IDEs | Geração e debugging de código |

---

## SageMaker JumpStart

Hub de modelos pré-treinados (open-source e proprietários) para **deploy na sua conta AWS**.

| Aspecto | SageMaker JumpStart | Amazon Bedrock |
|---------|--------------------:|:--------------:|
| **Modelos** | Open-source (Llama, Falcon, etc.) + proprietários | Múltiplos provedores via API |
| **Infraestrutura** | Você gerencia endpoints na sua conta | Serverless (AWS gerencia) |
| **Customização** | Full fine-tuning com controle total | Fine-tuning via API do Bedrock |
| **Custo** | Paga pela infra (instâncias) | Paga por token ou throughput |
| **Quando usar** | Precisa de controle total sobre o modelo e infra | Quer simplicidade e serverless |

---

## Amazon Quick (ex-QuickSight)

- Serviço de Business Intelligence com IA integrada
- Gerar dashboards e análises com linguagem natural
- Anteriormente chamado "Amazon QuickSight", renomeado para "Amazon Quick"

---

## PartyRock

- **Playground gratuito** para criar apps com IA generativa sem código
- Não requer conta AWS
- Interface visual para experimentação rápida
- Usa modelos Amazon Bedrock por baixo
- **Não é para produção** — é para aprendizado e prototipagem

---

## Model Customization Options

| Opção | Dados necessários | O que muda | Custo | Quando usar |
|-------|-------------------|-----------|-------|-------------|
| **Prompt Engineering** | Nenhum | Nada no modelo | Zero adicional | Primeiro passo sempre |
| **RAG (Knowledge Bases)** | Documentos (S3, web) | Nada no modelo (busca externa) | Médio (infra de busca) | Dados atualizados/proprietários |
| **Fine-tuning** | Pares input/output (centenas-milhares) | Ajusta pesos (comportamento/estilo) | Alto | Tom/estilo/formato específico |
| **Continued Pre-training** | Texto corrido do domínio (milhões de tokens) | Ajusta pesos (conhecimento do domínio) | Muito alto | Terminologia/domínio que o modelo desconhece |
| **Model Distillation (Destilação)** | Outputs de um modelo maior | Cria modelo menor com performance similar | Médio-alto | Reduzir custo/latência mantendo qualidade |
| **Custom Model Import** | Modelo treinado externamente | Traz para o Bedrock | Variável | Modelo open-weight customizado fora da AWS |

### Model Distillation (Destilação)

**Conceito:** Treinar um modelo **menor** (student) para imitar o comportamento de um modelo **maior** (teacher), obtendo performance próxima com custo/latência menores.

**Quando usar:**
- Modelo grande funciona bem mas é caro demais para produção
- Precisa de latência menor que o modelo grande oferece
- Volume alto onde o custo por token é crítico

**Trade-off:** O modelo destilado geralmente é ~90-95% tão bom quanto o original em tarefas específicas, mas com custo significativamente menor.

---

## Vantagens da Infraestrutura AWS para GenAI

O Exam Guide pede reconhecer as vantagens de usar a infraestrutura AWS para aplicações de IA generativa.

| Vantagem | Descrição |
|----------|-----------|
| **Acessibilidade** | Acesso a múltiplos FMs de diferentes provedores em uma única plataforma |
| **Menor barreira de entrada** | Serverless — não precisa gerenciar GPUs, infraestrutura de modelo |
| **Eficiência** | Integração nativa entre serviços (Bedrock + S3 + IAM + CloudTrail) |
| **Custo-benefício** | Pagar por uso, modelos de diferentes preços, otimização com batch/caching |
| **Velocidade de comercialização** | APIs prontas, RAG gerenciado, agents sem construir do zero |
| **Proteção** | Dados não usados para treinar modelos (Bedrock), isolamento de dados |
| **Conformidade** | Certificações (SOC, ISO, HIPAA eligible), regions específicas |
| **Segurança** | IAM, criptografia, VPC PrivateLink, Guardrails |
| **Responsabilidade** | Ferramentas de IA responsável (Guardrails, Clarify, Model Cards) |

---

## Trade-offs de Custos — Serviços GenAI AWS

| Trade-off | Opção A | Opção B | Decisão depende de |
|-----------|---------|---------|-------------------|
| **On-demand vs Provisioned** | Paga por token (flexível) | Capacidade reservada (consistente) | Volume e previsibilidade |
| **Modelo grande vs pequeno** | Mais capaz, mais caro | Menos capaz, mais barato | Complexidade da tarefa |
| **Bedrock vs JumpStart** | Serverless, paga por token | Infra própria, paga por instância | Controle vs simplicidade |
| **Real-time vs Batch** | Resposta imediata, custo cheio | Sem urgência, desconto ~50% | Requisito de latência |
| **Uma região vs multi-região** | Menor custo | Mais disponibilidade/redundância | Requisitos de DR/compliance |

> **DICA PARA A PROVA:** Se a questão menciona "reduzir custo" + "não precisa de resposta imediata" → batch. Se menciona "latência consistente" + "volume alto previsível" → provisioned throughput. Se menciona "flexibilidade" + "volume variável" → on-demand.

---

## Comparação: Quando Usar Cada Serviço

| Necessidade | Serviço |
|-------------|---------|
| Construir app GenAI em produção (serverless) | **Amazon Bedrock** |
| FM nativo AWS otimizado para custo | **Amazon Nova** |
| Deploy de modelo open-source com controle total | **SageMaker JumpStart** |
| Agentes que executam ações | **Agentes do Amazon Bedrock** |
| Segurança/governança de agentes em produção | **Amazon Bedrock AgentCore** |
| Chatbot empresarial com dados internos + permissões | **Amazon Q Business** |
| Assistente de código no IDE | **Amazon Q Developer** / **Kiro** |
| Construir agentes customizados (código) | **Strands Agents** |
| Experimentar GenAI sem código e sem custo | **PartyRock** |
| BI com IA generativa | **Amazon Quick** |
| Busca empresarial (retornar documentos) | **Amazon Kendra** |
| Embeddings para busca semântica | **Amazon Titan Embeddings** (via Bedrock) |
| RAG gerenciado | **Bedrock Knowledge Bases** |
| Filtrar conteúdo/PII/toxicidade | **Bedrock Guardrails** |

---

## Amazon Q Business vs Amazon Kendra

| Aspecto | Amazon Kendra | Amazon Q Business |
|---------|--------------|-------------------|
| **O que faz** | Busca empresarial com NLP (retorna trechos) | Assistente GenAI (gera respostas elaboradas) |
| **Saída** | Links e trechos relevantes | Resposta em linguagem natural com citações |
| **Permissões** | Suporta ACLs | Respeita permissões existentes nativamente |
| **Quando usar** | "Encontrar documentos" | "Responder perguntas sintetizando informação" |

> **DICA PARA A PROVA:** "Buscar/encontrar documentos" → Kendra. "Responder perguntas usando dados internos" → Q Business.

---

## Resumo para a Prova

| Pergunta | Resposta |
|----------|----------|
| "Acesso serverless a múltiplos FMs?" | Amazon Bedrock |
| "FM nativo da AWS otimizado para custo?" | Amazon Nova |
| "Embeddings AWS?" | Amazon Titan Embeddings (via Bedrock) |
| "Assistente GenAI para empresas?" | Amazon Q Business |
| "Assistente de código?" | Amazon Q Developer / Kiro |
| "Experimentar GenAI grátis?" | PartyRock |
| "RAG gerenciado?" | Bedrock Knowledge Bases |
| "FM que executa ações?" | Agentes do Amazon Bedrock |
| "Segurança de agentes em produção?" | Amazon Bedrock AgentCore |
| "Filtrar conteúdo inadequado/PII?" | Bedrock Guardrails |
| "Framework para construir agentes?" | Strands Agents |
| "Reduzir custo com modelo menor treinado pelo maior?" | Model Distillation |
| "Gerenciar versões de prompts?" | Bedrock Prompt Management |
| "Dados do cliente usados para treinar modelos no Bedrock?" | NÃO (política do Bedrock) |

---
