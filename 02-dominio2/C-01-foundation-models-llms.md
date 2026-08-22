# Foundation Models e LLMs

## Visão Geral

Foundation Models (Modelos de Base) são o pilar central da IA generativa moderna. A prova AIF-C01 dedica 24% das questões ao Domínio 2 — é essencial entender **o que são**, **como funcionam**, **seu ciclo de vida** e os conceitos de **IA agêntica**.

---

## O que são Foundation Models?

Modelos de grande escala pré-treinados em enormes quantidades de dados que podem ser **adaptados para múltiplas tarefas** sem treinar do zero para cada uma.

### Características

- **Pré-treinados** em grandes corpora (bilhões de tokens de texto, imagens, etc.)
- **Multi-propósito** — um único modelo resolve diversas tarefas
- **Adaptáveis** — podem ser refinados (fine-tuning) ou usados com prompt engineering
- **Capacidades emergentes** — habilidades que surgem com a escala (raciocínio, código, matemática)

### Exemplos de Foundation Models

| Modelo | Provedor | Tipo | Disponível no Bedrock |
|--------|----------|------|----------------------|
| Claude | Anthropic | Texto, multimodal | Sim |
| Amazon Nova | AWS | Texto, multimodal, imagem, vídeo | Sim |
| Amazon Titan | AWS | Texto, embeddings, imagem | Sim |
| Llama | Meta | Texto (open-weight) | Sim |
| Mistral / Mixtral | Mistral AI | Texto | Sim |
| Stable Diffusion | Stability AI | Imagem (difusão) | Sim |
| Cohere Command | Cohere | Texto | Sim |

> **Nota:** A lista de modelos no Bedrock é dinâmica — novos modelos são adicionados periodicamente. Para a prova, o importante é entender os **tipos** e **critérios de seleção**, não memorizar listas.

---

## Large Language Models (LLMs)

LLMs são um **subconjunto** de Foundation Models especializados em linguagem.

### Capacidades
- Geração de texto (artigos, emails, código)
- Resumo de documentos
- Tradução entre idiomas
- Perguntas e respostas (Q&A)
- Raciocínio e análise
- Geração e explicação de código

### Como são treinados
1. **Pré-treinamento** — modelo processa bilhões de tokens (self-supervised: next-token prediction ou masked language modeling)
2. **Fine-tuning** (opcional) — ajuste com dados específicos do domínio
3. **RLHF** (Reinforcement Learning from Human Feedback) — alinhamento com preferências humanas para ser mais útil, seguro e honesto

---

## Modelos Multimodais

Modelos que processam e/ou geram **múltiplos tipos de dados** (texto + imagem + áudio + vídeo).

| Capacidade | Exemplo |
|-----------|---------|
| Texto + imagem como entrada | Claude (vision): descrever/analisar imagens |
| Texto → imagem | Amazon Nova Canvas, Stable Diffusion |
| Texto → vídeo | Amazon Nova Reel |
| Áudio como entrada | Modelos com speech understanding |

> **DICA PARA A PROVA:** "Multimodal" significa que o modelo aceita e/ou gera múltiplas modalidades. Não confundir com modelos que apenas processam texto sobre imagens.

---

## Modelos de Difusão

Modelos de geração de imagens que funcionam por um processo de **adicionar ruído** e depois **remover ruído** (denoising) para criar imagens a partir de descrições textuais.

**Conceito:** O modelo aprende a reverter um processo de corrupção — começando de ruído puro e gradualmente refinando até gerar uma imagem coerente.

**Exemplos:** Stable Diffusion, Amazon Titan Image Generator, Amazon Nova Canvas

> **CUIDADO:** Modelos de difusão **não são** baseados na arquitetura Transformer pura. Eles usam uma arquitetura distinta (tipicamente U-Net com cross-attention). Quando o Exam Guide menciona "modelos de difusão" está diferenciando-os dos LLMs baseados em Transformers.

---

## Ciclo de Vida do Foundation Model

O Exam Guide exige entender as etapas do ciclo de vida de um FM.

| Etapa | Descrição |
|-------|-----------|
| **1. Seleção de dados** | Escolher e curar os dados de pré-treinamento (volume, qualidade, diversidade, licenciamento) |
| **2. Seleção de modelo** | Escolher arquitetura, tamanho (parâmetros), trade-offs custo/performance |
| **3. Pré-treinamento** | Treino massivo com grandes corpora (semanas/meses de computação em GPUs) |
| **4. Fine-tuning** | Ajuste com dados específicos (opcional, para especializar) |
| **5. Avaliação** | Medir performance em benchmarks e métricas relevantes |
| **6. Deploy (implantação)** | Disponibilizar para inferência (API, endpoint) |
| **7. Feedback** | Coletar feedback de uso, monitorar qualidade, iterar |

### Relação com serviços AWS

| Etapa | Serviço AWS relevante |
|-------|----------------------|
| Seleção de modelo | Amazon Bedrock (catálogo), SageMaker JumpStart |
| Fine-tuning | Amazon Bedrock (customization), Amazon SageMaker AI |
| Avaliação | Amazon Bedrock Model Evaluation |
| Deploy | Amazon Bedrock (serverless), SageMaker AI (endpoints) |
| Feedback/Monitoramento | CloudWatch, Bedrock logging |

---

## ML Tradicional vs IA Generativa

| Aspecto | ML Tradicional | IA Generativa |
|---------|----------------|---------------|
| **Saída** | Estruturada (classe, número) | Não-estruturada (texto, imagem, código) |
| **Objetivo** | Predizer, classificar, agrupar | Criar conteúdo novo |
| **Dados de treino** | Específicos para cada tarefa | Enormes e generalistas |
| **Modelo por tarefa** | Um modelo para cada problema | Um modelo para múltiplas tarefas |
| **Customização** | Treinar com dados rotulados | Prompt engineering, RAG ou fine-tuning |
| **Exemplo** | "Este email é spam?" → sim/não | "Escreva um email sobre X" → texto completo |

---

## Open-weight vs Proprietário

| Aspecto | Open-weight | Proprietário |
|---------|-------------|-------------|
| **Pesos do modelo** | Disponíveis publicamente | Acesso apenas via API |
| **Onde rodar** | Sua infraestrutura ou via Bedrock | Apenas via API do provedor / Bedrock |
| **Exemplos** | Llama, Mistral | Claude, Amazon Nova |
| **Customização** | Full fine-tuning possível | Limitada ao que a API permite |
| **Custo de operação** | Infra própria (pode ser menor em escala) | Pay-per-token (previsível) |
| **Na AWS** | SageMaker JumpStart (deploy na sua conta) ou Bedrock | Amazon Bedrock |

---

## Engenharia de Contexto (Context Engineering)

**Conceito:** Prática de gerenciar, otimizar e estruturar **tudo que entra no contexto** de um foundation model para maximizar a qualidade da resposta.

Enquanto prompt engineering foca em **como formular a instrução**, context engineering foca em **o que colocar no contexto como um todo**: qual informação incluir, em que ordem, como estruturar, o que omitir.

### Elementos do contexto

| Elemento | Descrição |
|----------|-----------|
| **System prompt** | Instruções de comportamento e regras |
| **Contexto do usuário** | Informações sobre quem está perguntando |
| **Documentos recuperados (RAG)** | Informações relevantes de fontes externas |
| **Histórico de conversa** | Mensagens anteriores para continuidade |
| **Ferramentas disponíveis** | Definições de tools que o modelo pode usar |
| **Exemplos (few-shot)** | Exemplos de entrada/saída desejados |

### Por que é importante

- A **qualidade da resposta** depende diretamente da qualidade do contexto
- Context window é limitada — é preciso decidir **o que incluir e o que omitir**
- Informação irrelevante pode confundir o modelo
- Ordem e estrutura afetam como o modelo processa

> **DICA PARA A PROVA:** Se a questão menciona "otimizar o que é fornecido ao modelo" ou "gerenciar informação no contexto", pense em context engineering. É mais amplo que prompt engineering.

---

## IA Agêntica — Conceitos Fundamentais

O Exam Guide AIF-C01 inclui IA agêntica como tópico explícito no Domínio 2. É preciso entender os conceitos fundamentais.

### O que é um Agente de IA?

Um sistema que combina um foundation model com capacidades de **planejamento, raciocínio, memória e uso de ferramentas** para executar tarefas de forma autônoma ou semi-autônoma.

**Diferença fundamental:** Um FM sozinho apenas gera texto. Um *agente* usa o FM para **planejar**, **decidir quais ações tomar**, **executar ações via ferramentas** e **iterar** até completar a tarefa.

### Componentes de um Agente

| Componente | Função |
|-----------|--------|
| **Foundation Model** | "Cérebro" — raciocínio, planejamento, geração |
| **Ferramentas (Tools)** | Ações que o agente pode executar (APIs, bancos de dados, buscas) |
| **Memória** | Armazenar contexto entre interações (curto e longo prazo) |
| **Planejamento** | Decompor tarefas complexas em etapas |
| **Orquestração** | Coordenar execução das etapas e decisões |

### Uso de Ferramentas (Tool Use)

Capacidade do agente de **invocar ferramentas externas** para obter informações ou executar ações que o FM sozinho não pode fazer.

**Exemplos de ferramentas:**
- Consultar banco de dados
- Chamar API externa
- Executar código
- Enviar email
- Buscar informação na web

**Fluxo:** FM decide que precisa de uma informação → seleciona a ferramenta adequada → invoca a ferramenta → recebe resultado → incorpora no raciocínio

### Gerenciamento de Memória

| Tipo | Descrição | Exemplo |
|------|-----------|---------|
| **Memória de curto prazo** | Contexto da interação atual (conversation history) | Mensagens anteriores no chat |
| **Memória de longo prazo** | Informações persistidas entre sessões | Preferências do usuário, tarefas anteriores |

### Orquestração de Workflow

Coordenação de múltiplas etapas e decisões para completar uma tarefa complexa.

**Exemplo:** "Reservar uma viagem" → pesquisar voos → comparar preços → verificar hotel → agendar → confirmar

O agente decide a sequência, lida com erros, e adapta o plano conforme resultados intermediários.

### Padrões de Sistemas Multiagente

Múltiplos agentes especializados colaborando para resolver problemas complexos.

| Padrão | Descrição |
|--------|-----------|
| **Especialização** | Cada agente tem um domínio/habilidade (um pesquisa, outro analisa, outro executa) |
| **Comunicação entre agentes** | Agentes trocam informações e delegam tarefas entre si |
| **Orquestrador** | Um agente coordena os demais, distribui tarefas e consolida resultados |

### Model Context Protocol (MCP)

**O que é:** Protocolo aberto (criado pela Anthropic) que padroniza como agentes de IA se conectam a **sistemas externos** (ferramentas, dados, APIs).

**Problema que resolve:** Sem MCP, cada integração entre agente e ferramenta precisa de código customizado. MCP cria uma interface **padronizada e reutilizável**.

**Arquitetura:**

| Componente | Função |
|-----------|--------|
| **MCP Client** | O agente/aplicação que precisa acessar ferramentas (ex: IDE, chatbot) |
| **MCP Server** | Serviço que expõe ferramentas, recursos ou prompts via protocolo padronizado |
| **Tools** | Ações que o servidor disponibiliza (ex: buscar documento, executar query) |
| **Resources** | Dados/contexto que o servidor fornece (ex: conteúdo de arquivos, schema de DB) |
| **Prompts** | Templates de prompts que o servidor pode oferecer |

**Analogia:** MCP é para agentes de IA o que USB é para periféricos — uma interface padrão que permite conectar qualquer ferramenta a qualquer agente compatível.

> **DICA PARA A PROVA:** Se a questão menciona "conectar agentes a sistemas externos de forma padronizada" ou "protocolo para integração de ferramentas", a resposta é MCP. Se menciona "agente que executa ações", pense em tool use. Se menciona "múltiplos agentes colaborando", pense em sistemas multiagente.

---

## Resumo para a Prova

| Conceito | O que lembrar |
|----------|---------------|
| Foundation Model | Modelo grande, pré-treinado, multi-propósito, adaptável |
| LLM | FM especializado em linguagem |
| Multimodal | Processa/gera múltiplos tipos de dados (texto+imagem+áudio+vídeo) |
| Modelo de difusão | Gera imagens por denoising, não é Transformer puro |
| Pré-treinamento | Treino massivo inicial (self-supervised) |
| Fine-tuning | Ajuste com dados específicos |
| RLHF | Alinhar modelo com preferências humanas |
| Ciclo de vida FM | Dados → modelo → treino → tune → avaliação → deploy → feedback |
| Context engineering | Gerenciar/otimizar tudo que entra no contexto do modelo |
| Agente de IA | FM + ferramentas + memória + planejamento + orquestração |
| Tool use | Agente invoca ferramentas externas para executar ações |
| MCP | Protocolo padrão para conectar agentes a sistemas externos |
| Multiagente | Múltiplos agentes especializados colaborando |
| Open-weight | Pesos disponíveis (Llama, Mistral) — deploy em infra própria |
| Amazon Bedrock | Acesso serverless a FMs na AWS |
| Amazon Nova | Família de FMs nativos da AWS |

---
