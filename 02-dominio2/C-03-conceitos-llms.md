# Conceitos de LLMs

## Visão Geral

Este bloco cobre os parâmetros e conceitos operacionais de Large Language Models que aparecem com frequência na prova AIF-C01.

---

## Tokens

### O que são
Unidades básicas que o LLM processa. Não são necessariamente palavras completas — geralmente são subpalavras.

### Regras práticas
- 1 token ≈ 4 caracteres em inglês (≈ ¾ de uma palavra)
- Português usa ~30% mais tokens que inglês para o mesmo conteúdo
- Espaços e pontuação também consomem tokens
- Código geralmente usa mais tokens por "ideia" que texto natural

### Por que importa na prova
- **Custo:** modelos cobram por token (entrada + saída separados)
- **Limites:** context window é medido em tokens
- **Latência:** mais tokens de saída = mais tempo de resposta

---

## Context Window (Janela de Contexto)

### O que é
Quantidade máxima de tokens que o modelo pode processar em uma única interação (entrada + saída combinados).

### Implicações
- **Context window pequeno:** modelo "esquece" informação distante
- **Context window grande:** pode processar documentos longos, mas custa mais
- Se a entrada excede o limite, o conteúdo é truncado ou gera erro

### Tamanhos típicos
| Modelo | Context window |
|--------|---------------|
| Modelos antigos | 4K - 8K tokens |
| Modelos atuais | 128K - 200K+ tokens |

### Para a prova
- RAG é uma solução quando o contexto necessário excede a context window
- Context window limita quanto "conhecimento" pode ser injetado via prompt

---

## Parâmetros de Inferência

### Temperature
| Valor | Comportamento | Caso de uso |
|-------|--------------|-------------|
| 0 (ou próximo) | Determinístico, focado, repetível | Fatos, dados, tarefas objetivas |
| 0.5 - 0.7 | Balanceado | Uso geral |
| 1.0+ | Criativo, diverso, imprevisível | Brainstorming, ficção, criatividade |

**Resumo:** Temperature baixa = previsível e factual. Temperature alta = criativo e variado.

### Top-p (Nucleus Sampling)
- Seleciona tokens do "núcleo" de probabilidades que somam p%
- Top-p = 0.9 → considera tokens que juntos cobrem 90% da probabilidade
- Mais baixo = mais focado, mais alto = mais diverso
- Complementar à temperature

### Top-k
- Considera apenas os K tokens mais prováveis
- Top-k = 50 → escolhe entre os 50 tokens mais prováveis
- Limita diretamente o vocabulário de escolha

### Max Tokens (comprimento de saída)
- Número máximo de tokens que o modelo gerará na resposta
- Não garante que use todos — pode parar antes se completar a resposta
- Afeta custo e latência

### Stop Sequences
- Tokens/frases que fazem o modelo parar de gerar
- Útil para controlar formato da saída

---

## Embeddings

### O que são
Representações numéricas (vetores) de texto em espaço multidimensional.

### Para que servem
- **Busca semântica:** encontrar textos com significado similar
- **RAG:** converter documentos e queries em vetores para comparação
- **Clustering:** agrupar textos por significado
- **Classificação:** usar como features para outros modelos

### Como funcionam
- Textos com significado similar ficam "próximos" no espaço vetorial
- "cachorro" e "cão" terão vetores próximos
- "cachorro" e "avião" terão vetores distantes
- Medida de similaridade: cosine similarity

### Serviço AWS
- **Amazon Titan Embeddings** — gera embeddings de texto via Bedrock
- **Amazon OpenSearch** — armazena e busca por vetores (vector database)

---

## Alucinação (Hallucination)

### O que é
Quando o modelo gera informação que parece plausível e confiante, mas é **factualmente incorreta ou inventada**.

### Por que acontece
- LLMs predizem o próximo token mais provável — não "verificam fatos"
- Treinados para gerar texto fluente, não necessariamente verdadeiro
- Podem "inventar" referências, datas, nomes que não existem

### Exemplos
- Citar um paper acadêmico que não existe
- Inventar funcionalidades de um serviço AWS
- Gerar código com APIs inexistentes

### Mitigação
| Técnica | Como funciona |
|---------|---------------|
| **RAG** | Ancora respostas em documentos reais antes de gerar |
| **Grounding** | Conectar o modelo a fontes de verdade |
| **Guardrails** | Filtrar respostas com validações |
| **Human-in-the-loop** | Revisão humana antes de publicar |
| **Temperature baixa** | Reduz criatividade e variação |
| **Citações** | Pedir que o modelo cite fontes (facilita verificação) |

---

## Grounding

### O que é
Ancorar as respostas do modelo em dados reais e verificáveis, em vez de depender apenas do conhecimento do pré-treinamento.

### Técnicas
- **RAG** — buscar informação relevante e injetar no contexto
- **Knowledge bases** — conectar o modelo a bases de dados atualizadas
- **Ferramentas/Agents** — modelo pode consultar APIs e sistemas reais
- **System prompts** — instruir o modelo a se ater a fatos fornecidos

---

## Interação entre Parâmetros

Na prática (e na prova), os parâmetros são usados em conjunto:

| Cenário de negócio | Temperature | Top-p | Max tokens | Resultado |
|-------------------|-------------|-------|------------|-----------|
| FAQ de atendimento (respostas factuais) | 0 | 1.0 | 200 | Determinístico, curto, preciso |
| Geração de slogans criativos | 0.9 | 0.95 | 100 | Variado, criativo, conciso |
| Resumo de contrato (factual + completo) | 0.2 | 0.9 | 1000 | Focado mas com espaço para completude |
| Chatbot geral (balanceado) | 0.5 | 0.9 | 500 | Equilibrado entre consistência e naturalidade |

**Regra para a prova:** Temperature e top-p controlam DIVERSIDADE. Max tokens controla COMPRIMENTO. Context window é o LIMITE TOTAL (input + output). São dimensões independentes.

**Interação temperature + top-p:**
- Quando ambos são baixos → resposta muito restrita (poucas opções de token)
- Quando ambos são altos → resposta mais livre (maior variedade)
- Na prática: geralmente ajustar UM deles é suficiente. A prova tende a focar em temperature como o controle principal de criatividade vs. determinismo.

> **CUIDADO:** Não interprete top-p como "mais alto = mais aleatório" de forma simplista. Top-p = 0.9 significa considerar tokens que cobrem 90% da massa de probabilidade — o efeito depende da distribuição. Se o modelo está muito confiante em um token, mesmo top-p alto resultará em output focado.

---

## Latência e Custo

| Fator | Impacto no custo | Impacto na latência |
|-------|-------------------|---------------------|
| Tokens de entrada (prompt) | ↑ custo | ↑ tempo de processamento |
| Tokens de saída (resposta) | ↑↑ custo (geralmente mais caro) | ↑↑ latência (geração sequencial) |
| Tamanho do modelo | ↑ custo por token | ↑ latência |
| Temperature | Sem impacto | Sem impacto significativo |

---

## Precificação Baseada em Tokens

O Exam Guide exige entender como a precificação por tokens afeta custo e performance.

### Estrutura de preço típica

| Componente | Descrição | Impacto |
|-----------|-----------|---------|
| **Tokens de entrada** | Cada token do prompt é cobrado | Prompts longos = mais caro |
| **Tokens de saída** | Cada token gerado é cobrado (geralmente 3-5x mais caro que entrada) | Respostas longas = custo significativo |
| **Modelo escolhido** | Modelos maiores/mais capazes custam mais por token | Trade-off: qualidade vs custo |

### Efeito no design de aplicações

| Decisão de design | Impacto no custo | Impacto na qualidade |
|-------------------|------------------|---------------------|
| Prompts concisos | ↓ custo | Pode manter qualidade se bem estruturado |
| Limitar max_tokens | ↓ custo | Pode truncar respostas |
| Usar modelo menor para tarefas simples | ↓↓ custo | Adequado para tarefas simples |
| Prompt caching (ver abaixo) | ↓ custo e latência | Sem impacto na qualidade |
| Batch inference | ↓↓ custo (desconto ~50%) | Sem impacto, mas não é real-time |

> **DICA PARA A PROVA:** Se a questão menciona "otimizar custo de inferência", pense em: modelo menor para tarefas simples, prompts concisos, prompt caching, batch inference. Se menciona "tokens de saída são caros", a solução é limitar max_tokens ou usar modelo menor.

---

## Prompt Caching

**Conceito:** Técnica que reutiliza o processamento de **prefixos de prompt** que se repetem entre requisições, evitando recomputá-los a cada chamada.

### Como funciona
- Muitas aplicações usam o mesmo system prompt + contexto base em todas as requisições
- Sem cache: o modelo processa o prefixo inteiro a cada chamada
- Com cache: o processamento do prefixo é armazenado e reutilizado

### Benefícios

| Benefício | Descrição |
|-----------|-----------|
| **Redução de custo** | Tokens cacheados custam menos que tokens processados do zero |
| **Redução de latência** | Menos tokens para processar = resposta mais rápida |
| **Mesmo resultado** | O output não muda — cache é transparente para a qualidade |

### Quando é útil
- Aplicações com **system prompt longo** que se repete (RAG com contexto fixo)
- **Few-shot prompts** com muitos exemplos fixos
- Chatbots com **instruções extensas** que não mudam entre mensagens

### Quando NÃO ajuda
- Cada requisição tem um prompt completamente diferente
- Prompts curtos (overhead do cache não compensa)

> **DICA PARA A PROVA:** Se a questão descreve "prompt longo que se repete em muitas requisições" + "reduzir custo/latência", prompt caching é a resposta. O Exam Guide menciona prompt caching como critério de seleção de modelo (Domínio 3).

---

## Otimizações de Custo e Performance

| Estratégia | Reduz custo? | Reduz latência? | Observação |
|-----------|-------------|-----------------|------------|
| Modelo menor para tarefas simples | ✅ | ✅ | Funciona para classificação, extração simples |
| Limitar max_tokens | ✅ | ✅ | Pode truncar se limite muito baixo |
| Prompt conciso | ✅ | ✅ | Menos tokens de entrada |
| Prompt caching | ✅ | ✅ | Para prefixos repetidos |
| Batch inference | ✅✅ | ❌ (não é real-time) | Para processamento em massa |
| Provisioned Throughput | Depende do volume | ✅ (consistente) | Para volume alto e previsível |
| Cache de respostas (aplicação) | ✅✅ | ✅✅ | Para queries idênticas repetidas |

---

## Resumo para a Prova

| Conceito | Palavra-chave na questão |
|----------|--------------------------|
| Temperature alta | "criativo", "diverso", "variado" |
| Temperature baixa | "factual", "consistente", "determinístico" |
| Context window | "documento longo", "limite de entrada", "truncar" |
| Embeddings | "busca semântica", "similaridade", "vetores" |
| Alucinação | "informação falsa", "inventa fatos", "não-factual" |
| RAG | "reduzir alucinações", "ancorar em dados reais" |
| Grounding | "fonte de verdade", "verificável" |
| Tokens | "custo", "limite", "precificação" |

---

*Próximo bloco: Prompt Engineering*
