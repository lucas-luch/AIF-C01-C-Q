# Arquitetura Transformer

## Visão Geral

O Transformer é a arquitetura de rede neural por trás de todos os LLMs modernos (GPT, Claude, Llama, Titan). A prova AIF-C01 não exige detalhes matemáticos, mas pede que você entenda os **conceitos de alto nível** e **por que** essa arquitetura revolucionou a IA.

---

## Por que Transformers?

Antes dos Transformers, modelos de linguagem usavam RNNs (Redes Neurais Recorrentes) que processavam texto **sequencialmente** (palavra por palavra). Problemas:
- Lentas (não paralelizáveis)
- Esqueciam contexto distante (vanishing gradient)
- Difíceis de treinar em textos longos

O Transformer (2017, paper "Attention Is All You Need") resolveu isso com o mecanismo de **atenção (attention)**.

---

## Mecanismo de Atenção (Attention)

### O que é
Permite que cada token na sequência "olhe" para TODOS os outros tokens e decida **quais são mais relevantes** para entender o contexto.

### Self-Attention
- Cada palavra calcula sua relação com todas as outras palavras da frase
- Exemplo: "O gato sentou no **tapete** porque **ele** era macio"
  - Self-attention permite que "ele" se conecte a "tapete" (não a "gato")
- Isso funciona em **paralelo** — todas as relações são calculadas simultaneamente

### Multi-Head Attention
- Múltiplas "cabeças" de atenção olham para diferentes tipos de relações
- Uma cabeça pode focar em relações sintáticas, outra em semânticas
- Resultado mais rico e nuançado

---

## Componentes do Transformer

### Encoder (Codificador)
- **Entende** a entrada
- Processa todo o texto de entrada e cria representações internas
- Usado em modelos como BERT (compreensão de texto)
- Bom para: classificação, análise de sentimento, NER

### Decoder (Decodificador)
- **Gera** a saída
- Produz texto token por token (autoregressive)
- Usado em modelos como GPT (geração de texto)
- Bom para: geração de texto, chat, completar frases

### Encoder-Decoder
- Combina ambos
- Encoder entende a entrada, Decoder gera a saída
- Usado em: tradução, resumo (T5, BART)

---

## Tipos de Modelos por Arquitetura

| Arquitetura | Exemplos | Tarefa principal |
|-------------|----------|-----------------|
| Encoder-only | BERT | Compreensão (classificação, NER, Q&A extractivo) |
| Decoder-only | GPT, Claude, Llama, Titan | Geração de texto |
| Encoder-Decoder | T5, BART | Tradução, resumo |

**Para a prova:** A maioria dos LLMs modernos (Claude, GPT, Llama) são **decoder-only** — geram texto token por token.

---

## Tokenização

### O que é
Processo de dividir texto em unidades (tokens) que o modelo processa.

### Tipos
- **Palavra inteira:** "inteligência" = 1 token
- **Subpalavra (mais comum):** "inteligência" = "intel" + "igência" (2 tokens)
- **Caractere:** cada letra é um token (ineficiente)

### Por que importa
- Define o **custo** (precificação por token)
- Define o **limite** de contexto (context window em tokens)
- Afeta idiomas: português geralmente usa mais tokens que inglês para o mesmo texto

---

## Processo de Geração (Autoregressive)

1. Modelo recebe a entrada (prompt) tokenizada
2. Calcula probabilidades para o próximo token
3. Seleciona um token (baseado em temperature, top-p, etc.)
4. Adiciona o token gerado à sequência
5. Repete até atingir condição de parada (max tokens, token de fim)

**Importante:** A geração é sequencial (token por token), mesmo que o processamento da entrada seja paralelo.

---

## Positional Encoding

- Transformers processam todos os tokens em paralelo (não sequencial)
- Problema: perdem a noção de ordem das palavras
- Solução: **positional encoding** — adiciona informação de posição a cada token
- Permite que o modelo saiba que "O gato comeu o peixe" ≠ "O peixe comeu o gato"

---

## Como Isso Aparece na Prova — Cenários

| Cenário descrito na questão | Conceito testado | Resposta |
|-----------------------------|-----------------|----------|
| "Modelo que processa texto E imagem para responder perguntas" | Multimodal (usa encoder para ambos + decoder para gerar) | Requer modelo multimodal (ex: Claude com vision) |
| "Empresa precisa classificar milhares de emails por categoria" | Tarefa de compreensão → encoder-only é eficiente | BERT-like / Amazon Comprehend |
| "Chatbot que gera respostas longas para clientes" | Tarefa de geração → decoder-only | GPT/Claude/Llama via Bedrock |
| "Modelo precisa traduzir documentos técnicos entre idiomas" | Tarefa seq-to-seq → encoder-decoder | Modelos T5-like ou Amazon Translate |
| "A resposta do modelo é diferente cada vez para o mesmo input" | Geração autoregressive + sampling (temperature > 0) | Configurar temperature = 0 para consistência |
| "Texto em português gera custo maior que em inglês" | Tokenização — subpalavras diferentes por idioma | Português usa ~30% mais tokens |

---

## Resumo para a Prova

| Conceito | O que lembrar |
|----------|---------------|
| Transformer | Arquitetura base de todos os LLMs modernos |
| Attention | Permite que tokens "olhem" para todos os outros — captura contexto |
| Self-attention | Cada token calcula relevância com todos os demais |
| Multi-head attention | Múltiplas perspectivas de atenção capturam relações diferentes |
| Encoder | Entende texto (BERT) — bom para classificação |
| Decoder | Gera texto (GPT, Claude, Llama) — bom para chat e geração |
| Autoregressive | Gera um token por vez, usando os anteriores como contexto |
| Tokenização | Divide texto em unidades processáveis — afeta custo e limites |
| Positional encoding | Dá noção de ordem ao modelo |
| Paralelização | Vantagem chave sobre RNNs — treina muito mais rápido |

---

*Próximo bloco: Conceitos de LLMs (tokens, context window, temperature, alucinações)*
