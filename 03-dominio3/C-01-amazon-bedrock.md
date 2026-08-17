# Amazon Bedrock — Funcionalidades

## Visão Geral

Amazon Bedrock é o serviço central de IA generativa da AWS e o **mais cobrado na prova AIF-C01**. Este bloco aprofunda suas funcionalidades além do básico.

---

## Modelos Disponíveis

### Seleção de Modelo
Fatores para escolher um FM no Bedrock:
- **Tarefa:** geração de texto, embeddings, imagem, multimodal
- **Qualidade:** modelos maiores são mais capazes mas mais caros
- **Latência:** modelos menores respondem mais rápido
- **Custo:** precificação por token varia entre provedores
- **Idiomas:** cobertura varia entre modelos
- **Context window:** limite de entrada + saída

### Precificação
- **On-demand:** paga por token processado (entrada + saída)
- **Provisioned Throughput:** capacidade reservada para workloads previsíveis
- **Batch inference:** processamento em lote com desconto (não real-time)

---

## Knowledge Bases (RAG Gerenciado)

### O que é
Serviço que implementa RAG de forma gerenciada — conecta Foundation Models a suas fontes de dados.

### Fluxo
1. Você carrega documentos em uma fonte (S3, web crawler, etc.)
2. Bedrock processa os documentos: chunking → embeddings → armazena em vector database
3. Na hora da query: busca chunks relevantes → injeta como contexto → FM gera resposta

### Componentes
| Componente | Papel |
|-----------|-------|
| Data source | Onde estão seus documentos (S3, Confluence, SharePoint, web) |
| Chunking | Divide documentos em pedaços menores |
| Embedding model | Converte chunks em vetores |
| Vector database | Armazena vetores (OpenSearch Serverless, Pinecone, etc.) |
| Retrieval | Busca chunks similares à query |
| FM | Gera resposta usando os chunks como contexto |

### Quando usar
- Respostas baseadas em documentos internos/proprietários
- Reduzir alucinações com dados factuais
- Manter informação atualizada sem re-treinar o modelo

---

## Agents (Agentes)

### O que são
Foundation Models que podem **planejar e executar ações** — não apenas gerar texto, mas interagir com sistemas.

### Ciclo de um Agent
1. Recebe instrução do usuário
2. **Raciocina** sobre o que precisa fazer (ReAct: Reason + Act)
3. Decide qual **ação** executar
4. Executa a ação (chama API/Lambda)
5. **Observa** o resultado
6. Repete até completar a tarefa
7. Gera resposta final

### Componentes
| Componente | Função |
|-----------|--------|
| Foundation Model | Raciocínio e tomada de decisão |
| Action Groups | Ações que o agent pode executar (Lambda functions) |
| Knowledge Bases | Informação que o agent pode consultar |
| Instructions | Regras e comportamento do agent |

### Exemplos de uso
- Agent de atendimento que consulta pedidos e processa devoluções
- Agent de pesquisa que busca em múltiplas fontes e sintetiza
- Agent de vendas que consulta estoque e cria cotações

---

## Guardrails

### O que são
Filtros e controles que limitam o comportamento do FM para uso seguro em produção.

### Tipos de proteção
| Tipo | O que faz |
|------|-----------|
| **Content filters** | Bloqueia conteúdo violento, sexual, insultos, etc. |
| **Denied topics** | Lista de tópicos que o modelo não pode abordar |
| **Word filters** | Bloqueia palavras/frases específicas |
| **PII filters** | Detecta e redige dados pessoais (CPF, email, telefone) |
| **Grounding check** | Verifica se a resposta está ancorada no contexto fornecido |
| **Contextual grounding** | Detecta alucinações comparando resposta vs fonte |

### Quando usar
- Chatbots voltados ao público
- Aplicações reguladas (saúde, finanças)
- Quando há risco de uso indevido
- Para compliance com políticas corporativas

---

## Fine-tuning no Bedrock

### O que é
Ajustar os pesos de um FM usando seus dados específicos.

### Quando usar
- O modelo precisa de **estilo/tom** muito específico
- Domínio especializado com vocabulário próprio
- Prompt engineering e RAG não são suficientes

### Processo
1. Preparar dataset (pares input/output ou texto do domínio)
2. Criar training job no Bedrock
3. Modelo é fine-tuned (cópia privada)
4. Deploy do modelo customizado

### Continued Pre-training
- Diferente de fine-tuning: ensina **conhecimento novo** ao modelo
- Usa grandes volumes de texto do domínio (não pares input/output)
- Mais caro e intensivo que fine-tuning
- Para quando o modelo precisa entender terminologia especializada

---

## Model Evaluation

### O que é
Comparar múltiplos modelos do Bedrock em métricas relevantes para seu caso de uso.

### Tipos de avaliação
- **Automática:** métricas quantitativas (ROUGE, BLEU, acurácia)
- **Humana:** avaliadores classificam qualidade das respostas
- **Comparativa:** qual modelo é melhor para SUA tarefa específica

---

## SageMaker Clarify para IA Generativa

Clarify não é só para ML tabular — também avalia FMs:

### O que faz para GenAI
| Funcionalidade | Descrição |
|---------------|-----------|
| **Avaliação de qualidade** | Medir ROUGE, BLEU, BERTScore, perplexidade |
| **Detecção de toxicidade** | Identificar conteúdo ofensivo nas respostas |
| **Detecção de viés em texto** | Estereótipos, linguagem tendenciosa |
| **Factual knowledge** | Comparar respostas com referência para detectar alucinações |
| **Robustez** | Testar como o modelo se comporta com inputs adversariais |

### Quando usar na prova
- "Avaliar fairness de um FM" → Clarify (bias em texto gerado)
- "Detectar se modelo gera estereótipos" → Clarify (toxicity/bias)
- "Comparar qualidade de modelos com métricas" → Model Evaluation + Clarify

---

## Resumo para a Prova

| Funcionalidade | Para que serve |
|---------------|----------------|
| Knowledge Bases | RAG gerenciado (respostas baseadas em seus docs) |
| Agents | FM que executa ações (chama APIs, Lambda) |
| Guardrails | Filtros de segurança e conteúdo |
| Fine-tuning | Ajustar estilo/comportamento do modelo |
| Continued Pre-training | Ensinar conhecimento novo ao modelo |
| Model Evaluation | Comparar modelos para seu caso de uso |
| Provisioned Throughput | Capacidade dedicada para produção |

---

*Próximo bloco: RAG (Retrieval-Augmented Generation)*
