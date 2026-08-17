# Guardrails, Human-in-the-Loop e AI Service Cards

## Visão Geral

Este bloco cobre as ferramentas práticas da AWS para implementar IA responsável em produção.

---

## Amazon Bedrock Guardrails

### O que são
Filtros configuráveis que controlam inputs e outputs de Foundation Models para uso seguro.

### Tipos de Proteção

| Filtro | O que faz | Exemplo |
|--------|-----------|---------|
| **Content filters** | Bloqueia por categoria (hate, violence, sexual, insults) | Bloquear respostas com discurso de ódio |
| **Denied topics** | Lista de temas proibidos | "Não fale sobre concorrentes" |
| **Word filters** | Bloqueia palavras específicas | Bloquear profanidades ou marcas |
| **PII filters** | Detecta/redige dados pessoais | Mascarar CPF, email, telefone na resposta |
| **Grounding check** | Verifica se resposta está ancorada no contexto | Detectar quando modelo "inventa" informação |
| **Contextual grounding** | Mede fidelidade ao contexto fornecido | Score de alucinação |

### Quando usar Guardrails
- Chatbots públicos (risco de conteúdo inadequado)
- Aplicações reguladas (saúde, finanças)
- Proteção contra prompt injection
- Compliance com políticas corporativas
- Proteção de dados pessoais (PII)

### Como funcionam
```
Input do usuário → [Guardrail filtra input] → FM processa → [Guardrail filtra output] → Resposta ao usuário
```
- Aplicados ANTES (input) e DEPOIS (output) do FM
- Se bloqueado, retorna mensagem configurável (não a resposta do FM)

---

## Human-in-the-Loop

### Conceito
Incluir revisão humana em pontos críticos do pipeline de IA, onde decisões automatizadas podem ter alto impacto.

### Amazon Augmented AI (A2I)
- Serviço gerenciado para implementar revisão humana
- Integra com serviços de IA (Textract, Rekognition, ou custom)
- Define **condições** para escalar para humano:
  - Confiança abaixo de threshold (ex: < 90%)
  - Amostras aleatórias para auditoria
  - Categorias específicas de risco

### Fluxo A2I
```
1. IA faz previsão
2. Confiança < threshold?
   ├── NÃO → previsão aceita automaticamente
   └── SIM → enviada para revisão humana
3. Humano revisa e corrige
4. Resultado final entregue
```

### Quando usar human-in-the-loop
| Cenário | Motivo |
|---------|--------|
| Diagnósticos médicos | Impacto na saúde — IA como assistente, humano decide |
| Decisões de crédito | Regulamentação exige explicação humana |
| Moderação de conteúdo | Edge cases que IA não resolve |
| Extração de documentos | Dados ambíguos ou baixa confiança |
| Deploy de modelos | Aprovação humana antes de produção |

---

## AWS AI Service Cards

### O que são
Documentação pública de transparência que a AWS publica para seus serviços de IA.

### Conteúdo de um Service Card
| Seção | O que descreve |
|-------|----------------|
| Intended use cases | Para que o serviço foi projetado |
| Limitations | O que o serviço NÃO faz bem |
| Responsible AI design choices | Decisões éticas no design |
| Deployment best practices | Como usar de forma responsável |
| Performance metrics | Métricas por subgrupo/cenário |
| Fairness evaluations | Avaliações de equidade |

### Serviços com AI Service Cards
- Amazon Rekognition (detecção facial, moderação)
- Amazon Textract
- Amazon Transcribe
- Amazon Lex
- Outros serviços de IA gerenciados

### Para a prova
- AI Service Cards = transparência e documentação de limitações
- Demonstram compromisso da AWS com IA responsável
- Ajudam clientes a entender quando usar (e quando NÃO usar) um serviço

---

## Model Cards (SageMaker)

### O que são
Documentação estruturada sobre um modelo ML customizado — quem criou, para que serve, como foi avaliado, limitações.

### Diferença: AI Service Cards vs Model Cards
| Aspecto | AI Service Cards | Model Cards |
|---------|------------------|-------------|
| Para quem | Serviços de IA da AWS (Rekognition, etc.) | Seus modelos customizados |
| Quem cria | AWS | Você/sua equipe |
| Onde vive | Documentação pública AWS | SageMaker Model Registry |
| Propósito | Transparência do serviço | Governança do seu modelo |

---

## Alucinações — Detecção e Mitigação

### Detectar
- Bedrock Guardrails (grounding check)
- Comparar output vs fontes fornecidas
- Métricas de factualidade (BERTScore vs referência)
- Avaliação humana em amostras

### Mitigar
| Técnica | Efetividade |
|---------|-------------|
| RAG | Alta — ancora em dados reais |
| Guardrails (grounding) | Alta — detecta e bloqueia |
| Temperature baixa | Média — reduz criatividade/variação |
| System prompt restritivo | Média — "Só use informações do contexto" |
| Human review | Alta — mas custoso |
| Citações/referências | Média — facilita verificação |

---

## Resumo para a Prova

| Conceito | Serviço/Ferramenta |
|----------|-------------------|
| Filtrar conteúdo perigoso em LLMs | Bedrock Guardrails |
| Mascarar PII em respostas | Bedrock Guardrails (PII filter) |
| Detectar alucinações | Bedrock Guardrails (grounding check) |
| Revisão humana quando confiança é baixa | Amazon A2I |
| Transparência sobre serviços da AWS | AWS AI Service Cards |
| Documentar seus modelos customizados | SageMaker Model Cards |
| Bloquear tópicos específicos | Bedrock Guardrails (denied topics) |

---

## Cenários de Prova — Como Aparecem

| Cenário na questão | Armadilha | Resposta correta |
|-------------------|-----------|------------------|
| "Chatbot gera respostas sobre temas proibidos mesmo com system prompt dizendo para não fazê-lo" | System prompt pode ser burlado com prompt injection | **Guardrails (denied topics)** — camada independente do prompt |
| "Empresa quer que chatbot não revele CPFs de clientes" | Pensar em fine-tuning para "desaprender" PII | **Guardrails (PII filter)** — mascara/bloqueia em tempo real |
| "Modelo de extração de docs tem 92% de acurácia mas erros custam caro" | Aceitar o modelo como está por ser "bom o suficiente" | **A2I** com threshold — erros caros = revisão humana nos casos incertos |
| "Empresa lançou modelo e quer ser transparente sobre limitações" | Publicar apenas um README genérico | **Model Cards** (para seu modelo) com limitações, métricas, uso pretendido |
| "Chatbot inventa dados financeiros que não estão nos documentos fornecidos" | RAG sozinho resolve | **Guardrails grounding check** + RAG (dupla proteção) |
| "Regulador pede prova de que o serviço Rekognition foi avaliado por fairness" | Criar avaliação do zero | **AWS AI Service Cards** (já publicadas pela AWS) |

---

*Próximo: Mini-simulado Domínio 4*
