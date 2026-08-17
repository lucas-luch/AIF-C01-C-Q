# RAG (Retrieval-Augmented Generation)

## Visão Geral

RAG é um padrão arquitetural que combina **busca de informação** + **geração de texto**. É o conceito mais importante do Domínio 3 e aparece com muita frequência na prova.

---

## O que é RAG?

Retrieval-Augmented Generation = buscar informação relevante em uma base de dados e injetá-la como contexto para o FM gerar uma resposta fundamentada.

### Problema que resolve
- LLMs têm **knowledge cutoff** — não sabem sobre eventos após o pré-treinamento
- LLMs **alucinam** — inventam informação plausível mas falsa
- LLMs não conhecem **dados proprietários** da sua empresa
- Context window é limitada — não dá para colocar todos os docs no prompt

### Solução RAG
Em vez de re-treinar o modelo, **buscar** a informação relevante no momento da query e incluir no prompt.

---

## Fluxo RAG

```
1. Usuário faz uma pergunta
        ↓
2. Query é convertida em embedding (vetor)
        ↓
3. Busca semântica no vector database → chunks relevantes
        ↓
4. Chunks são injetados como contexto no prompt
        ↓
5. FM gera resposta baseada no contexto
        ↓
6. Resposta entregue ao usuário (com citações)
```

---

## Componentes do RAG

### Indexação (offline, feita uma vez)
1. **Documentos** → divididos em **chunks** (pedaços menores)
2. **Chunks** → convertidos em **embeddings** (vetores numéricos)
3. **Embeddings** → armazenados em **vector database**

### Retrieval (online, a cada query)
1. **Query** → convertida em embedding
2. **Busca** por chunks com vetores mais similares (cosine similarity)
3. **Top-K chunks** retornados como contexto

### Generation
1. Prompt = instrução + contexto (chunks) + pergunta do usuário
2. FM gera resposta baseada no contexto fornecido
3. Se bem instruído, modelo se limita ao contexto (menos alucinação)

---

## Chunking (Divisão de Documentos)

| Estratégia | Descrição | Quando usar |
|-----------|-----------|-------------|
| Fixed-size | Chunks de tamanho fixo (ex: 512 tokens) | Padrão, funciona na maioria dos casos |
| Semantic | Divide por significado (parágrafos, seções) | Documentos bem estruturados |
| Overlapping | Chunks com sobreposição (ex: 50 tokens de overlap) | Evitar perder contexto nas bordas |
| Hierarchical | Parent-child (resumo + detalhe) | Documentos longos e complexos |

---

## Vector Database (Banco Vetorial)

Armazena embeddings e permite busca por similaridade.

### Serviços AWS
| Serviço | Tipo |
|---------|------|
| **Amazon OpenSearch Serverless** | Vector search gerenciado (default no Bedrock) |
| **Amazon Aurora PostgreSQL** | pgvector extension |
| **Amazon Neptune** | Graph + vector |

### Como funciona a busca
- Converte query em vetor
- Calcula distância/similaridade com vetores armazenados
- Retorna os K mais similares (nearest neighbors)
- Métrica comum: cosine similarity

---

## RAG vs Fine-tuning vs Prompt Engineering

| Aspecto | Prompt Engineering | RAG | Fine-tuning |
|---------|-------------------|-----|-------------|
| **Dados atualizados** | ❌ | ✅ | Parcialmente |
| **Dados proprietários** | Limitado (context window) | ✅ | ✅ |
| **Custo de implementação** | Baixo | Médio | Alto |
| **Reduz alucinações** | Parcialmente | ✅ (forte) | Parcialmente |
| **Muda estilo/tom** | Limitado | ❌ | ✅ |
| **Velocidade de implementação** | Imediato | Dias | Semanas |
| **Necessita re-treinar?** | Não | Não | Sim |

### Quando usar cada um
- **Prompt Engineering primeiro** → sempre começar aqui
- **RAG** → quando precisa de dados atualizados/proprietários
- **Fine-tuning** → quando precisa mudar comportamento/estilo fundamental do modelo
- **Combinação** → RAG + fine-tuning para casos avançados

---

## RAG no Amazon Bedrock

### Bedrock Knowledge Bases
- Implementação gerenciada de RAG
- Fontes: S3, web crawler, Confluence, SharePoint
- Embedding: Amazon Titan Embeddings ou Cohere Embed
- Vector store: OpenSearch Serverless (padrão), Pinecone, Redis
- Chunking: fixo ou semântico (configurável)

### Vantagens do gerenciado
- Sem necessidade de construir pipeline de indexação
- Atualização automática quando docs mudam
- Integração nativa com Bedrock Agents
- Citações automáticas nas respostas

---

## Resumo para a Prova

| Conceito | O que lembrar |
|----------|---------------|
| RAG | Buscar + gerar (reduz alucinações, traz dados atualizados) |
| Embedding | Representação vetorial de texto para busca semântica |
| Vector database | Armazena e busca por similaridade de vetores |
| Chunking | Dividir docs em pedaços menores para indexação |
| Cosine similarity | Métrica para medir semelhança entre vetores |
| Knowledge Bases | RAG gerenciado no Bedrock |
| Quando usar RAG | Dados proprietários, informação atualizada, reduzir alucinações |
| RAG vs Fine-tuning | RAG = dados novos sem re-treinar; Fine-tuning = mudar comportamento |

---

*Próximo bloco: Fine-tuning vs Prompt Engineering vs RAG*
