# Casos de Uso Empresariais e Otimização de Modelos

## Visão Geral

A prova AIF-C01 apresenta cenários de negócio e pede que você escolha a **arquitetura e modelo corretos**. Este bloco cobre casos de uso comuns e critérios de otimização.

---

## Casos de Uso com IA Generativa

### Geração e Resumo de Conteúdo
| Caso | Descrição | Abordagem |
|------|-----------|-----------|
| Resumo de documentos | Condensar relatórios longos | Prompt engineering + FM de texto |
| Geração de emails | Criar comunicações personalizadas | Fine-tuning (tom) ou PE (geral) |
| Criação de marketing | Textos publicitários, posts | PE com examples (few-shot) |
| Documentação técnica | Gerar docs de código/APIs | Amazon Q Developer |

### Busca e Q&A
| Caso | Descrição | Abordagem |
|------|-----------|-----------|
| FAQ empresarial | Perguntas sobre políticas internas | RAG + Knowledge Bases |
| Busca em documentos | Encontrar info em milhares de PDFs | RAG ou Amazon Kendra |
| Suporte ao cliente | Responder dúvidas de produto | RAG + Agents (se precisa executar ações) |

### Código e Desenvolvimento
| Caso | Descrição | Abordagem |
|------|-----------|-----------|
| Geração de código | Escrever funções a partir de descrição | Amazon Q Developer |
| Explicação de código | Entender código legado | Amazon Q Developer |
| Transformação de código | Migrar entre linguagens/versões | Amazon Q Developer (transform) |
| Revisão de código | Sugerir melhorias | Amazon Q Developer |

### Análise e Extração
| Caso | Descrição | Abordagem |
|------|-----------|-----------|
| Extração de dados | Dados de formulários e faturas | Amazon Textract + FM |
| Classificação de documentos | Categorizar por tipo/urgência | Comprehend ou FM (few-shot) |
| Análise de sentimento | Feedback de clientes | Amazon Comprehend ou FM |

---

## Otimização: Escolhendo o Modelo Certo

### Critérios de Seleção

| Critério | Modelo maior | Modelo menor |
|----------|-------------|-------------|
| Qualidade de resposta | ✅ Melhor | ❌ Pode ser insuficiente |
| Custo | ❌ Mais caro | ✅ Mais barato |
| Latência | ❌ Mais lento | ✅ Mais rápido |
| Tarefas complexas | ✅ Necessário | ❌ Pode falhar |
| Tarefas simples | Overkill | ✅ Suficiente |

### Regra da prova
- **Classificação simples, extração de dados** → modelo menor (custo-efetivo)
- **Raciocínio complexo, geração longa** → modelo maior (qualidade necessária)
- **Alta demanda com baixa latência** → modelo menor + provisioned throughput
- **"Menor custo operacional"** → modelo menor que atenda os requisitos

---

## Parâmetros de Inferência — Otimização

| Parâmetro | Para otimizar qualidade | Para otimizar custo/latência |
|-----------|------------------------|------------------------------|
| Temperature | 0.3-0.5 (factual) | Sem impacto direto |
| Max tokens | Mais alto (respostas completas) | Mais baixo (respostas concisas) |
| Top-p | 0.9 (diversidade controlada) | Sem impacto direto |
| Stop sequences | Não limitar | Limitar para respostas curtas |

---

## Métricas de Avaliação para GenAI

### Métricas Automáticas
| Métrica | Mede | Caso de uso |
|---------|------|-------------|
| ROUGE | Sobreposição com referência (recall-oriented) | Resumos |
| BLEU | Precisão de n-grams vs referência | Tradução |
| BERTScore | Similaridade semântica via embeddings | Qualquer geração |
| Perplexidade | Quão "surpreso" o modelo fica | Qualidade do modelo |

### Avaliação Humana
- Quando usar: qualidade subjetiva, criatividade, tom, factualidade
- Mais cara e lenta, mas captura nuances que métricas automáticas perdem
- Amazon Bedrock Model Evaluation suporta avaliação humana

### Bedrock Model Evaluation
- Comparar modelos lado a lado no seu caso de uso
- Métricas automáticas + avaliação humana
- Datasets customizados com seus exemplos reais

---

## Otimização de Custo

| Estratégia | Como funciona | Economia |
|-----------|---------------|----------|
| Modelo menor para tarefas simples | Usar modelo mais barato quando possível | Alta |
| Batch inference | Processar em lote (não real-time) | Média-alta |
| Prompt conciso | Menos tokens de entrada | Média |
| Max tokens limitado | Menos tokens de saída | Média |
| Cache de respostas | Reutilizar respostas para queries iguais | Alta (queries repetidas) |
| Provisioned Throughput | Preço por tempo (para volume alto e previsível) | Variável |

---

## Resumo para a Prova

| Cenário | Solução |
|---------|---------|
| "Responder perguntas sobre docs internos" | RAG (Bedrock Knowledge Bases) |
| "Gerar código a partir de descrição" | Amazon Q Developer |
| "Chatbot que executa ações no sistema" | Bedrock Agents |
| "Menor custo para tarefa simples" | Modelo menor + prompt otimizado |
| "Baixa latência em produção" | Modelo menor + Provisioned Throughput |
| "Avaliar qual modelo é melhor" | Bedrock Model Evaluation |
| "Processar milhares de documentos" | Batch inference |
| "Resumo com qualidade medida" | ROUGE como métrica |
| "Qualidade subjetiva" | Avaliação humana |

---

## Armadilhas Comuns na Prova (Domínio 3)

| Armadilha | Por que está errada | Correta |
|-----------|--------------------:|---------|
| "Usar fine-tuning para dados que mudam" | Fine-tuning é caro e estático — cada mudança requer re-treinar | RAG (atualiza sem re-treinar) |
| "Usar Bedrock para ML tabular" | Bedrock é para GenAI/FMs, não classificação tabular | SageMaker (Autopilot/Canvas) |
| "Agent quando só precisa responder perguntas" | Agent é overkill se não precisa executar AÇÕES | Knowledge Bases (RAG) é suficiente |
| "RAG quando o problema é estilo/tom" | RAG traz dados, não muda comportamento do modelo | Fine-tuning |
| "Modelo maior = sempre melhor" | Modelo maior = mais caro + mais lento. Se modelo menor resolve, é preferível | Modelo menor que atenda requisitos |
| "Guardrails substitui system prompt" | Guardrails é camada adicional de proteção, não substitui instruções | Ambos juntos (prompt + guardrails) |
| "Cache resolve todos os problemas de custo" | Cache só funciona para perguntas idênticas/repetidas | Depende do padrão de uso |

---

*Próximo: Mini-simulado Domínio 3*
