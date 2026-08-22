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

## Design Centrado no Ser Humano (Human-Centered Design)

O Exam Guide exige reconhecer princípios de design centrado no ser humano para IA explicável.

### Princípios

| Princípio | Descrição | Exemplo |
|-----------|-----------|---------|
| **Mecanismos de feedback do usuário** | Usuários devem poder reportar problemas, corrigir outputs e expressar insatisfação | Botão "esta resposta foi útil?", formulário de feedback, opção de corrigir |
| **Transparência de decisões de IA** | Usuários devem entender quando e por que uma decisão foi tomada por IA | Explicar "esta recomendação é baseada em X", indicar nível de confiança |
| **Controle humano** | Usuários devem poder contestar, modificar ou reverter decisões da IA | Opção de "falar com humano", botão de override |
| **Comunicação clara** | Linguagem acessível sobre capacidades e limitações | Disclaimers claros: "esta é uma sugestão, não um diagnóstico" |

### Por que importa para a prova
- O Exam Guide conecta design centrado no humano com explicabilidade
- A ideia central: IA deve **servir** ao humano, não substituí-lo em decisões críticas sem supervisão
- Sistemas devem ser projetados **com** os usuários, não apenas **para** eles

> **DICA PARA A PROVA:** Se a questão menciona "permitir que usuários entendam decisões da IA" ou "mecanismos de feedback", pense em design centrado no ser humano. Se menciona "revisão humana de decisões de baixa confiança", pense em human-in-the-loop (A2I).

---

## Trade-offs entre Segurança e Transparência do Modelo

O Exam Guide exige identificar **concessões** (trade-offs) entre segurança e transparência.

### O dilema

| Mais transparência | Mais segurança |
|-------------------|----------------|
| Publicar como o modelo funciona | Esconder detalhes para evitar exploração |
| Abrir pesos do modelo (open-source) | Manter modelo proprietário (dificulta uso malicioso) |
| Explicar cada decisão ao usuário | Limitar informação para evitar gaming do sistema |
| Compartilhar métricas e limitações | Reter informação que poderia ser usada contra o sistema |

### Exemplos práticos

| Cenário | Transparência pede | Segurança pede | Trade-off |
|---------|-------------------|----------------|-----------|
| Modelo de detecção de fraude | Explicar por que transação foi bloqueada | Não revelar as regras (fraudadores poderiam evitá-las) | Explicação genérica sem revelar lógica interna |
| Guardrails de conteúdo | Publicar quais tópicos são bloqueados | Não publicar (atacantes usariam para contornar) | Documentar princípios mas não regras exatas |
| Modelo open-source | Qualquer pessoa pode auditar | Qualquer pessoa pode encontrar vulnerabilidades | Depende do contexto: pesquisa vs. produção |

### Avaliação do desempenho vs. interpretabilidade

| Tipo de modelo | Performance | Interpretabilidade | Trade-off |
|---------------|-------------|-------------------|-----------|
| Regressão linear | Menor | Alta | Entende facilmente mas pode ser insuficiente |
| Random Forest | Média | Média | Equilíbrio razoável |
| Deep Learning / LLM | Alta | Baixa | Melhor performance mas difícil explicar |

> **DICA PARA A PROVA:** Se a questão apresenta cenário de "modelo com alta performance mas difícil de explicar" vs "modelo explicável mas menos preciso", está testando o trade-off performance vs. interpretabilidade. A escolha depende do contexto (regulação, risco, necessidade de auditoria).

---

## Modelos de Código Aberto, Dados e Licenciamento

O Exam Guide menciona "modelos de código aberto, dados e licenciamento" como ferramentas para identificar modelos transparentes e explicáveis.

### Modelos open-source/open-weight

| Aspecto | Modelo proprietário | Modelo open-weight |
|---------|--------------------|--------------------|
| **Transparência** | Baixa — é caixa-preta | Alta — pesos disponíveis para inspeção |
| **Auditabilidade** | Limitada ao que o provedor expõe | Completa — pode analisar internamente |
| **Reprodutibilidade** | Dependente do provedor | Pode reproduzir resultados independentemente |
| **Risco** | Dependência do provedor | Responsabilidade total do operador |
| **Exemplos** | Claude, GPT | Llama, Mistral |

### Licenciamento

| Aspecto | Por que importa para IA responsável |
|---------|-------------------------------------|
| **Licença dos dados de treino** | Dados foram coletados legalmente? Respeitam copyright? |
| **Licença do modelo** | Modelo pode ser usado comercialmente? Tem restrições de uso? |
| **Licença de output** | Quem detém direitos sobre conteúdo gerado pelo modelo? |
| **Restrições de uso** | Algumas licenças proíbem usos específicos (ex: vigilância, armas) |

### Para a prova
- **Transparência** beneficia-se de código aberto (permite auditoria)
- **Licenciamento** é um aspecto de governança e compliance
- Modelos open-weight permitem mais explicabilidade (pode analisar internamente)
- Porém, open-weight não garante automaticamente que o modelo é justo ou seguro

> **DICA PARA A PROVA:** Se a questão menciona "auditar internamente o modelo" ou "reproduzir resultados", modelo open-weight é necessário. Se menciona "reduzir risco de licenciamento", a resposta envolve verificar licenças de dados e modelo.

---

## Amazon Bedrock Model Evaluations para Transparência

Bedrock Model Evaluations não serve apenas para performance — também ajuda na transparência e explicabilidade:

| Funcionalidade | Como apoia transparência |
|---------------|-------------------------|
| Comparação de modelos | Documenta qual modelo é melhor e por quê |
| Métricas de safety | Quantifica quão seguro é o modelo |
| Métricas por subgrupo | Identifica disparidades entre grupos |
| Avaliação humana | Captura percepção qualitativa de especialistas |
| Relatórios | Gera evidência auditável de avaliação |

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
