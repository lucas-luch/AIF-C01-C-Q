# Foundation Models e LLMs

## Visão Geral

Foundation Models (Modelos de Fundação) são o pilar central da IA generativa moderna. A prova AIF-C01 dedica 24% das questões a este domínio — é essencial entender **o que são**, **como funcionam** e **como se diferenciam do ML tradicional**.

---

## O que são Foundation Models?

Modelos de grande escala pré-treinados em enormes quantidades de dados que podem ser **adaptados para múltiplas tarefas** sem treinar do zero para cada uma.

### Características
- **Pré-treinados** em grandes corpora (bilhões de textos, imagens, etc.)
- **Multi-propósito** — um único modelo resolve diversas tarefas
- **Adaptáveis** — podem ser refinados (fine-tuning) para casos específicos
- **Emergent capabilities** — habilidades que surgem com a escala (reasoning, code, math)

### Exemplos de Foundation Models
| Modelo | Empresa | Tipo |
|--------|---------|------|
| Claude | Anthropic | Texto (multimodal) |
| GPT-4 | OpenAI | Texto (multimodal) |
| Llama | Meta | Texto (open-weight) |
| Amazon Titan | AWS | Texto, embeddings, imagem |
| Stable Diffusion | Stability AI | Imagem |
| Mistral | Mistral AI | Texto |
| Cohere Command | Cohere | Texto |

---

## Large Language Models (LLMs)

LLMs são um **subconjunto** de Foundation Models especializados em linguagem.

### O que fazem
- Geração de texto (artigos, emails, código)
- Resumo de documentos
- Tradução entre idiomas
- Perguntas e respostas (Q&A)
- Raciocínio e análise
- Geração e explicação de código

### Como são treinados
1. **Pré-treinamento** — modelo processa bilhões de tokens de texto (self-supervised)
2. **Fine-tuning** (opcional) — ajuste com dados específicos do domínio
3. **RLHF** (Reinforcement Learning from Human Feedback) — alinhamento com preferências humanas

---

## ML Tradicional vs IA Generativa

| Aspecto | ML Tradicional | IA Generativa |
|---------|----------------|---------------|
| **Saída** | Estruturada (classe, número) | Não-estruturada (texto, imagem, código) |
| **Objetivo** | Predizer, classificar, agrupar | Criar conteúdo novo |
| **Dados de treino** | Específicos para cada tarefa | Enormes e generalistas |
| **Modelo por tarefa** | Um modelo para cada problema | Um modelo para múltiplas tarefas |
| **Customização** | Treinar do zero | Prompt engineering ou fine-tuning |
| **Exemplo** | "Este email é spam?" → sim/não | "Escreva um email sobre X" → texto completo |

---

## Tipos de IA Generativa

| Tipo | O que gera | Exemplo de modelo |
|------|-----------|-------------------|
| Text-to-text | Texto a partir de texto | Claude, Titan Text, Llama |
| Text-to-image | Imagem a partir de descrição | Stable Diffusion, Titan Image |
| Text-to-code | Código a partir de descrição | Amazon Q Developer |
| Text-to-speech | Áudio a partir de texto | Amazon Polly (não GenAI puro) |
| Speech-to-text | Texto a partir de áudio | Amazon Transcribe |
| Multimodal | Processa múltiplos tipos (texto + imagem) | Claude (vision), GPT-4 |

---

## Conceitos Importantes para a Prova

### Pré-treinamento vs Fine-tuning
- **Pré-treinamento:** treino inicial massivo (bilhões de tokens, semanas de computação, caro)
- **Fine-tuning:** ajuste adicional com dados específicos (menor, mais rápido, mais barato)
- Analogia: pré-treinamento é a "educação geral", fine-tuning é a "especialização"

### Open-weight vs Proprietary
- **Open-weight (Llama, Mistral):** pesos do modelo disponíveis, pode rodar em sua infraestrutura
- **Proprietary (Claude, GPT-4):** acesso apenas via API, pesos não disponíveis
- Na AWS: Amazon Bedrock dá acesso a ambos os tipos via API gerenciada

### Escala e Parâmetros
- Modelos maiores (mais parâmetros) geralmente são mais capazes
- Mais parâmetros = mais caro para inferência
- Trade-off: qualidade vs custo vs latência

---

## Serviços AWS Relacionados

| Serviço | Papel |
|---------|-------|
| **Amazon Bedrock** | Acesso serverless a múltiplos FMs (Claude, Titan, Llama, etc.) |
| **Amazon Titan** | Família de FMs da AWS (texto, embeddings, imagem) |
| **SageMaker JumpStart** | Hub com FMs para deploy em sua conta |
| **Amazon Q** | Assistente GenAI empresarial (usa FMs por baixo) |
| **Amazon Q Developer** | Assistente de código com GenAI |
| **PartyRock** | Playground gratuito para experimentar apps GenAI |

---

## Resumo para a Prova

| Conceito | O que lembrar |
|----------|---------------|
| Foundation Model | Modelo grande, pré-treinado, multi-propósito |
| LLM | Tipo de FM especializado em linguagem |
| Pré-treinamento | Treino massivo inicial (self-supervised) |
| Fine-tuning | Ajuste com dados específicos |
| RLHF | Alinhar modelo com preferências humanas |
| Multimodal | Processa texto + imagem + outros |
| Open-weight | Pesos disponíveis (Llama, Mistral) |
| Amazon Bedrock | Forma de acessar FMs na AWS |

---

*Próximo bloco: Arquitetura Transformer*
