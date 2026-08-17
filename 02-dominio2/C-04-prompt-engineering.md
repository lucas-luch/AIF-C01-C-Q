# Prompt Engineering

## Visão Geral

Prompt Engineering é a arte de **formular instruções** para obter a melhor resposta de um LLM. A prova AIF-C01 testa se você sabe **qual técnica usar** em cada cenário.

---

## Técnicas de Prompt Engineering

### Zero-Shot

Pergunta direta sem fornecer exemplos. O modelo usa apenas seu conhecimento prévio.

```
Classifique o sentimento desta review: "O produto chegou rápido e funciona bem"
```

**Quando usar:** Tarefas simples onde o modelo já tem capacidade suficiente.

---

### Few-Shot

Fornecer **alguns exemplos** antes da pergunta para guiar o formato e estilo da resposta.

```
Classifique o sentimento:
Review: "Adorei o produto!" → Positivo
Review: "Péssima qualidade." → Negativo
Review: "O produto chegou rápido e funciona bem" → ?
```

**Quando usar:** Quando zero-shot não produz o formato/qualidade desejados, ou para tarefas com padrão específico.

---

### Chain-of-Thought (CoT)

Pedir que o modelo **raciocine passo a passo** antes de dar a resposta final.

```
Um cliente comprou 3 itens a R$50 cada com 10% de desconto. 
Quanto pagou no total? Pense passo a passo.
```

**Quando usar:** Problemas de raciocínio, matemática, lógica, análise multi-etapa.

**Variação:** "Let's think step by step" — trigger simples que ativa raciocínio passo a passo.

---

### System Prompt (Instrução de Sistema)

Define o **comportamento, persona e regras** que o modelo deve seguir em todas as respostas.

```
System: Você é um assistente especializado em AWS. 
Responda sempre em português. 
Se não souber algo, diga "não tenho certeza".
Cite a documentação oficial quando possível.
```

**Quando usar:** Sempre — define o contexto e limites da interação.

---

### Prompt Template (Template Reutilizável)

Estrutura padronizada com variáveis que são preenchidas dinamicamente.

```
Dado o seguinte contexto:
{contexto}

Responda a pergunta: {pergunta}

Se a resposta não estiver no contexto, diga "informação não disponível".
```

**Quando usar:** Aplicações em produção que precisam de consistência (RAG, chatbots, automações).

---

## Boas Práticas de Prompt Engineering

### Seja Específico
- ❌ "Fale sobre AWS"
- ✅ "Explique as 3 principais diferenças entre S3 Standard e S3 Glacier em termos de custo e latência de acesso"

### Defina o Formato de Saída
- "Responda em formato de tabela com colunas: Serviço, Caso de Uso, Custo"
- "Liste 5 pontos em bullet points"
- "Responda em no máximo 3 frases"

### Forneça Contexto Relevante
- Incluir informações necessárias no prompt
- Delimitar seções claramente (usar separadores como ---, ###)

### Use Constraints (Restrições)
- "Responda APENAS com base no texto fornecido"
- "Não invente informações"
- "Se não souber, diga que não sabe"

---

## Comparação das Técnicas

| Técnica | Complexidade | Custo (tokens) | Quando usar |
|---------|-------------|----------------|-------------|
| Zero-shot | Baixa | Baixo | Tarefas simples que o modelo já sabe fazer |
| Few-shot | Média | Médio | Quando precisa de formato específico ou tarefa nova |
| Chain-of-thought | Média | Médio-alto | Raciocínio complexo, matemática, lógica |
| System prompt | Baixa | Baixo | Sempre (define comportamento base) |
| Template | Baixa | Variável | Aplicações em produção com inputs dinâmicos |

---

## Prompt Engineering vs Fine-tuning vs RAG

| Aspecto | Prompt Engineering | Fine-tuning | RAG |
|---------|-------------------|-------------|-----|
| **Custo** | Sem custo adicional | Alto (treino) | Médio (infraestrutura de busca) |
| **Velocidade de implementação** | Imediato | Dias/semanas | Horas/dias |
| **Conhecimento novo** | Limitado pela context window | Integra ao modelo | Busca em base externa |
| **Estilo/formato** | Bom | Excelente | Bom |
| **Dados atualizados** | Não (pré-treinamento fixo) | Parcialmente | Sim (base atualizada) |
| **Quando usar** | Primeira abordagem sempre | Estilo/comportamento específico | Dados proprietários atualizados |

**Regra para a prova:** Tente prompt engineering primeiro → se não basta, RAG para dados atualizados → fine-tuning para comportamento especializado.

---

## Resumo para a Prova

| Cenário na questão | Técnica correta |
|-------------------|-----------------|
| "Classificar sem exemplos" | Zero-shot |
| "Dar exemplos antes da pergunta" | Few-shot |
| "Raciocinar passo a passo" | Chain-of-thought |
| "Definir persona ou regras" | System prompt |
| "Aplicação com inputs variáveis em produção" | Prompt template |
| "Modelo precisa de dados atualizados" | RAG (não prompt engineering puro) |
| "Modelo precisa mudar estilo de escrita" | Fine-tuning |

---

*Próximo bloco: Serviços AWS de IA Generativa (Bedrock, Titan, Q, PartyRock)*
