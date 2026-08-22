# Amazon Bedrock — Funcionalidades e Design de Aplicações

## Visão Geral

Amazon Bedrock é o serviço central de IA generativa da AWS e o **mais cobrado na prova AIF-C01** (Domínio 3 = 28%). Este bloco cobre funcionalidades, critérios de seleção de FM, vector databases e trade-offs de customização.

---

## Critérios de Seleção de Foundation Models

O Exam Guide exige saber identificar os critérios para escolher um FM pré-treinado. A seleção depende do caso de uso.

| Critério | O que avaliar | Impacto |
|----------|--------------|---------|
| **Custo** | Preço por token (entrada/saída), modelo de pricing | Trade-off direto com qualidade |
| **Modalidade** | Texto, imagem, áudio, vídeo, multimodal | O modelo precisa processar/gerar o tipo de dado requerido |
| **Latência** | Tempo de resposta (ms a segundos) | Aplicações interativas exigem modelos mais rápidos (geralmente menores) |
| **Multilíngue** | Suporte a idiomas específicos | Nem todos os modelos funcionam bem em todos os idiomas |
| **Tamanho do modelo** | Número de parâmetros | Maior = mais capaz mas mais caro e lento |
| **Complexidade do modelo** | Capacidade de raciocínio e tarefas complexas | Tarefas simples não precisam do modelo mais complexo |
| **Personalização** | Possibilidade de fine-tuning, continued pre-training | Alguns modelos permitem mais customização que outros |
| **Tamanho de entrada/saída** | Context window, max output tokens | Documentos longos exigem context window grande |
| **Prompt caching** | Suporte a reutilização de prefixos processados | Reduz custo e latência para prompts repetitivos |

### Framework de decisão para seleção

```
Tarefa simples (classificação, extração)?
├── SIM → Modelo menor (custo-efetivo, baixa latência)
│
└── NÃO → Tarefa complexa (raciocínio, geração longa)?
    ├── SIM → Modelo maior (mais capaz)
    │
    └── Precisa processar imagens/vídeo/áudio?
        ├── SIM → Modelo multimodal
        └── NÃO → Modelo texto-only (geralmente mais barato)
```

> **DICA PARA A PROVA:** Se a questão menciona "menor custo" + "tarefa simples" → modelo menor. Se menciona "raciocínio complexo" + "múltiplas etapas" → modelo maior. Se menciona "processar imagens e texto" → multimodal.

---

## Parâmetros de Inferência e Efeito nas Respostas

*(Detalhes completos no D2 C-03. Resumo contextualizado para design de aplicações:)*

| Parâmetro | Efeito | Aplicação no design |
|-----------|--------|-------------------|
| **Temperature** | Controla diversidade/criatividade | Factual → baixa; Criativo → alta |
| **Tamanho de entrada** | Mais tokens = mais custo + latência | Prompts concisos economizam |
| **Tamanho de saída (max tokens)** | Limita comprimento da resposta | Definir limites adequados à tarefa |
| **Top-p / Top-k** | Controla pool de tokens candidatos | Ajuste fino de diversidade |

---

## Vector Databases — Serviços AWS

O Exam Guide lista explicitamente os serviços AWS para armazenar embeddings em bancos vetoriais.

| Serviço AWS | Descrição | Uso com RAG |
|-------------|-----------|-------------|
| **Amazon OpenSearch Service** | Motor de busca com suporte a vetores (k-NN) | Padrão no Bedrock Knowledge Bases |
| **Amazon Aurora** | PostgreSQL com extensão pgvector | Quando já usa Aurora como banco principal |
| **Amazon Neptune** | Banco de grafos com suporte a vetores | Quando precisa de relações entre entidades + busca vetorial |
| **Amazon RDS para PostgreSQL** | PostgreSQL gerenciado com pgvector | Alternativa gerenciada com pgvector sem Aurora |

### Quando escolher cada um

| Cenário | Vector DB recomendado |
|---------|----------------------|
| RAG padrão com Bedrock Knowledge Bases | OpenSearch Service (integração nativa) |
| Já tem dados em Aurora PostgreSQL | Aurora com pgvector (evita duplicar dados) |
| Precisa de busca vetorial + relações complexas (grafos) | Amazon Neptune |
| Quer simplicidade com PostgreSQL padrão | Amazon RDS para PostgreSQL com pgvector |

---

## Funcionalidades do Bedrock

### Knowledge Bases (RAG Gerenciado)

*(Detalhes completos no C-02. Resumo:)*
- Implementa RAG de forma gerenciada
- Fontes: S3, web crawler, Confluence, SharePoint
- Chunking → embeddings → vector database → retrieval → geração
- Citações automáticas nas respostas

### Agents

*(Detalhes completos no C-04. Resumo:)*
- FMs que planejam e executam ações (tool use)
- Action Groups (Lambda), Knowledge Bases, Instructions
- Padrão ReAct (Reason → Act → Observe)

### Guardrails

Filtros e controles para uso seguro em produção.

| Tipo de proteção | O que faz |
|-----------------|-----------|
| **Content filters** | Bloqueia conteúdo violento, sexual, insultos |
| **Denied topics** | Tópicos que o modelo não pode abordar |
| **Word filters** | Bloqueia palavras/frases específicas |
| **PII filters** | Detecta e redige dados pessoais |
| **Grounding check** | Verifica se a resposta está ancorada no contexto |
| **Contextual grounding** | Detecta alucinações comparando resposta vs fonte |

> **CUIDADO:** Guardrails é uma **camada adicional** de proteção. Não substitui system prompts bem escritos — ambos devem ser usados juntos. System prompt define comportamento; Guardrails bloqueia violações.

### Fine-tuning e Continued Pre-training

| Opção | Dados | Objetivo | Custo |
|-------|-------|----------|-------|
| **Fine-tuning** | Pares input/output (centenas-milhares) | Ajustar estilo/comportamento | Alto |
| **Continued Pre-training** | Texto corrido do domínio (milhões de tokens) | Ensinar conhecimento novo | Muito alto |
| **Model Distillation** | Outputs de modelo maior (teacher) | Criar modelo menor com performance similar | Médio-alto |

### Model Evaluation

- Comparar modelos com métricas automáticas (ROUGE, BLEU, BERTScore)
- Avaliação humana configurável
- LLM-as-a-judge
- Datasets customizados com exemplos reais

### Prompt Management

- Versionamento de prompts
- Templates com variáveis
- Comparação de performance entre versões

### Provisioned Throughput

- Capacidade dedicada para workloads previsíveis
- Latência consistente garantida
- Modelo de preço: por unidade de capacidade/tempo

---

## Trade-offs de Custo entre Abordagens de Customização

O Exam Guide pede explicitamente entender os trade-offs de custo.

| Abordagem | Custo de setup | Custo de inferência | Tempo para implementar | Qualidade |
|-----------|---------------|--------------------|-----------------------|-----------|
| **Prompt Engineering** | Nenhum | Padrão (tokens) | Imediato | Boa para tarefas simples |
| **RAG** | Médio (infra de busca) | Padrão + busca | Dias | Boa + dados atualizados |
| **Fine-tuning** | Alto (treino) | Pode ser menor (prompts mais curtos) | Semanas | Excelente para estilo/formato |
| **Continued Pre-training** | Muito alto | Similar ao fine-tuning | Semanas-meses | Necessário para domínios novos |
| **Model Distillation** | Médio-alto | Menor (modelo menor) | Dias-semanas | ~90-95% do modelo original |
| **In-context learning (few-shot)** | Nenhum | Maior (mais tokens de input) | Imediato | Boa para formato/padrão |

### Cenários de decisão de custo

| Cenário | Abordagem mais custo-efetiva |
|---------|------------------------------|
| Volume baixo, tarefa variada | Prompt engineering (on-demand) |
| Volume alto, tarefa específica | Fine-tuning (prompts mais curtos = menos tokens) |
| Dados mudam frequentemente | RAG (sem retreino) |
| Modelo grande funciona mas é caro demais | Model distillation |
| Volume alto e previsível | Provisioned Throughput |
| Volume alto sem urgência | Batch inference (desconto ~50%) |
| Prefixo de prompt se repete | Prompt caching |

---

## Função dos Agentes de IA — Aplicações Comerciais

O Exam Guide 3.1 pede definir a função de agentes e suas aplicações comerciais.

| Aplicação comercial | O que o agente faz |
|--------------------|-------------------|
| **Atendimento ao cliente** | Consulta pedidos, processa devoluções, escalona para humano |
| **Vendas** | Consulta estoque, calcula preços, gera propostas |
| **RH / People Ops** | Responde dúvidas de políticas, agenda entrevistas |
| **Pesquisa e análise** | Busca em múltiplas fontes, sintetiza relatórios |
| **Automação de TI** | Consulta logs, identifica problemas, executa remediação |
| **Financeiro** | Processa despesas, gera relatórios, consulta compliance |

---

## Resumo para a Prova

| Pergunta | Resposta |
|----------|----------|
| "Critérios para escolher um FM?" | Custo, modalidade, latência, multilíngue, tamanho, personalização, prompt caching |
| "Onde armazenar embeddings na AWS?" | OpenSearch, Aurora, Neptune, RDS PostgreSQL |
| "Reduzir custo com modelo menor treinado pelo maior?" | Model distillation |
| "Abordagem de menor custo para tarefa simples?" | Prompt engineering com modelo menor |
| "Dados que mudam frequentemente?" | RAG (sem retreino) |
| "Volume alto com latência consistente?" | Provisioned Throughput |
| "Filtrar conteúdo + verificar grounding?" | Guardrails for Amazon Bedrock |
| "Guardrails substitui system prompt?" | NÃO — são complementares |

---
