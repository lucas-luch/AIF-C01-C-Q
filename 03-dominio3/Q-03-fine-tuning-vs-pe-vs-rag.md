# Questões — Fine-tuning vs Prompt Engineering vs RAG

---

### Questão 1

Uma empresa de saúde quer que seu assistente virtual responda perguntas usando informações de protocolos médicos internos que são atualizados semanalmente. Qual abordagem é mais adequada?

A) Fine-tuning semanal do modelo  
B) RAG conectado à base de protocolos  
C) Chain-of-thought prompting  
D) Continued pre-training  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) RAG conectado à base de protocolos**

✅ **Por que B está correta:** Dados que mudam semanalmente = RAG é ideal. Basta re-indexar os novos protocolos. Sem re-treinamento, sem custo de fine-tuning repetido, informação sempre atualizada.

❌ **Por que as outras estão erradas:**
- **A)** Fine-tuning semanal seria extremamente caro e demorado — impraticável.
- **C)** Chain-of-thought melhora raciocínio, mas não traz dados externos atualizados.
- **D)** Continued pre-training é ainda mais caro que fine-tuning e não se repete semanalmente.

</details>

---

### Questão 2

Um escritório de advocacia quer que o FM gere contratos sempre no mesmo formato padronizado com terminologia jurídica precisa. Prompt engineering sozinho não está mantendo a consistência. Qual é o próximo passo?

A) Usar RAG com exemplos de contratos  
B) Fazer fine-tuning com pares de input/output de contratos  
C) Aumentar a temperature  
D) Usar um modelo maior  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Fazer fine-tuning com pares de input/output de contratos**

✅ **Por que B está correta:** Quando o problema é estilo, formato e terminologia consistente que prompt engineering não resolve, fine-tuning é a abordagem certa. Ajusta os pesos do modelo para gerar outputs no padrão jurídico.

❌ **Por que as outras estão erradas:**
- **A)** RAG traz informação factual, mas não muda o estilo/formato de geração.
- **C)** Temperature alta aumenta variação — pioraria a consistência.
- **D)** Modelo maior não garante aderência ao formato específico — o problema é estilo, não capacidade.

</details>

---

### Questão 3

Uma startup quer rapidamente testar se um FM consegue classificar emails de suporte em 5 categorias. Qual abordagem deve tentar PRIMEIRO?

A) Fine-tuning com dataset de emails classificados  
B) RAG com base de emails anteriores  
C) Prompt engineering com few-shot (exemplos de cada categoria)  
D) Continued pre-training com corpus de emails  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: C) Prompt engineering com few-shot (exemplos de cada categoria)**

✅ **Por que C está correta:** Sempre começar com prompt engineering — é gratuito, imediato e frequentemente suficiente. Few-shot com exemplos de cada categoria geralmente funciona bem para classificação.

❌ **Por que as outras estão erradas:**
- **A)** Fine-tuning é caro e demorado — só fazer se PE não for suficiente.
- **B)** RAG traz informação, mas classificação é melhor resolvida com exemplos no prompt.
- **D)** Continued pre-training é a opção mais cara e desnecessária para classificação simples.

</details>

---

### Questão 4

Qual abordagem NÃO requer re-treinamento do Foundation Model? **(Selecione DUAS)**

A) Fine-tuning  
B) Prompt Engineering  
C) Continued Pre-training  
D) RAG  
E) RLHF  

<details>
<summary>🔍 Ver resposta</summary>

**Respostas: B e D**

✅ **Por que B está correta:** Prompt Engineering opera apenas na inferência — formula o prompt de forma otimizada sem alterar nenhum peso do modelo.

✅ **Por que D está correta:** RAG busca informação externa e injeta como contexto durante a inferência — o modelo base permanece inalterado.

❌ **Por que as outras estão erradas:**
- **A)** Fine-tuning modifica pesos do modelo = re-treinamento parcial.
- **C)** Continued Pre-training treina o modelo com dados novos = re-treinamento.
- **E)** RLHF treina o modelo com feedback humano = re-treinamento.

</details>

---

### Questão 5

Uma empresa quer que seu modelo entenda profundamente a terminologia de engenharia aeronáutica, que é muito diferente do que modelos gerais conhecem. Qual abordagem é mais adequada?

A) Prompt Engineering com system prompt técnico  
B) RAG com manuais de aviação  
C) Continued Pre-training com grandes volumes de texto aeronáutico  
D) Aumentar max_tokens  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: C) Continued Pre-training com grandes volumes de texto aeronáutico**

✅ **Por que C está correta:** Quando o modelo não **entende** um domínio (terminologia, conceitos, relações), continued pre-training ensina esse conhecimento treinando com grandes volumes de texto do domínio. É mais profundo que RAG (que apenas busca) ou PE (que apenas instrui).

❌ **Por que as outras estão erradas:**
- **A)** System prompt pode definir contexto, mas não ensina vocabulário novo ao modelo.
- **B)** RAG traz informação sob demanda, mas o modelo pode não entender a terminologia dos chunks retornados.
- **D)** Max tokens afeta comprimento da resposta, não compreensão do domínio.

</details>



---

### Questão 6

Uma empresa de moda quer que seu FM gere descrições de roupas em um "tom editorial fashion" específico da marca — sofisticado, minimalista e com vocabulário próprio. Testaram prompt engineering com exemplos de tom, mas o modelo inconsistentemente reverte ao tom genérico. Os dados de estilo NÃO mudam ao longo do tempo. Qual é o próximo passo MAIS eficaz?

A) RAG com catálogo de produtos para trazer informações factuais  
B) Fine-tuning com centenas de exemplos de descrições no tom editorial desejado  
C) Continued Pre-training com todo o arquivo de revistas de moda  
D) Aumentar temperature para gerar texto mais criativo  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Fine-tuning com exemplos no tom editorial desejado**

✅ **Por que B está correta:** O problema é ESTILO/TOM consistente que PE não mantém. Fine-tuning ajusta os pesos do modelo para internalizar esse comportamento — torna o tom parte do modelo, não apenas instrução. Dados de estilo são estáveis (não mudam).

❌ **Por que as outras estão erradas:**
- **A)** RAG traz informação factual (preços, materiais), mas não muda o TOM de escrita do modelo.
- **C)** Continued Pre-training ensina conhecimento de domínio (vocabulário), mas é overkill para ajustar tom — e muito mais caro que fine-tuning.
- **D)** Temperature alta gera mais variação, mas variação ≠ tom específico da marca.

</details>

---

### Questão 7

Uma empresa de energia quer que seu FM entenda terminologia altamente especializada de engenharia nuclear que NÃO existe nos dados de pré-treinamento do modelo. Os termos são tão específicos que o modelo não consegue nem interpretar os prompts corretamente. Qual abordagem é MAIS profunda?

A) Prompt engineering com definições dos termos no system prompt  
B) RAG com manuais técnicos de engenharia nuclear  
C) Continued Pre-training com grande volume de literatura técnica nuclear  
D) Fine-tuning com pares pergunta/resposta sobre nuclear  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: C) Continued Pre-training com grande volume de literatura técnica nuclear**

✅ **Por que C está correta:** Quando o modelo NÃO ENTENDE a terminologia (não está no pré-treinamento), a solução mais profunda é continued pre-training — expor o modelo a grandes volumes de texto do domínio para "aprender" o vocabulário, relações e conceitos. É como dar educação básica no domínio.

❌ **Por que as outras estão erradas:**
- **A)** Definições no prompt ajudam pouco se o modelo não tem representação interna dos conceitos — é como dar um glossário a alguém que não sabe nada do assunto.
- **B)** RAG traz documentos relevantes, mas se o modelo não entende os termos NOS documentos, não ajuda.
- **D)** Fine-tuning muda comportamento/formato, mas pressupõe que o modelo ENTENDE o domínio — aqui o modelo nem compreende os termos.

</details>

---

### Questão 8

Uma empresa implementou as três abordagens para diferentes casos de uso. O CFO pede uma comparação de custo. Qual ORDENAÇÃO de custo (do menor para o maior) é CORRETA?

A) Fine-tuning < RAG < Prompt Engineering  
B) Prompt Engineering < RAG < Fine-tuning < Continued Pre-training  
C) RAG < Prompt Engineering < Fine-tuning  
D) Continued Pre-training < Fine-tuning < Prompt Engineering  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Prompt Engineering < RAG < Fine-tuning < Continued Pre-training**

✅ **Por que B está correta:** PE = custo zero de preparação (apenas texto no prompt). RAG = custo de infraestrutura (vector DB, embeddings, indexação). Fine-tuning = custo de compute para treinar + dados anotados. Continued Pre-training = custo massivo de compute com grandes volumes de dados.

❌ **Por que as outras estão erradas:**
- **A)** Fine-tuning NÃO é mais barato que RAG — requer tempo de GPU, dados curados, e re-treino a cada mudança.
- **C)** RAG não é mais barato que PE — PE não requer nenhuma infraestrutura adicional.
- **D)** Continued Pre-training é o MAIS caro (não o mais barato) — inverte completamente.

</details>

---

### Questão 9

Uma equipe debate quando usar RAG vs Fine-tuning. Qual regra prática CORRETA diferencia quando usar cada um?

A) RAG para qualquer melhoria de qualidade; fine-tuning é obsoleto  
B) RAG para informação que muda frequentemente; fine-tuning para comportamento/estilo que deve ser consistente e estável  
C) Fine-tuning para informação atualizada; RAG para estilo  
D) Ambos são intercambiáveis — escolha qualquer um  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) RAG para informação mutável; fine-tuning para comportamento estável**

✅ **Por que B está correta:** RAG = dados que mudam (FAQs, preços, documentos atualizados) — basta re-indexar sem re-treinar. Fine-tuning = comportamento consistente (tom, formato, terminologia) que NÃO muda — ajusta pesos uma vez.

❌ **Por que as outras estão erradas:**
- **A)** Fine-tuning NÃO é obsoleto — é a solução certa para estilo/comportamento que PE não resolve.
- **C)** Inverte a regra — fine-tuning NÃO atualiza informação facilmente (requer re-treino). RAG NÃO muda estilo.
- **D)** NÃO são intercambiáveis — resolvem problemas diferentes (informação vs comportamento).

</details>

---

### Questão 10

Uma empresa está usando IA generativa para três necessidades distintas. Para CADA necessidade, qual abordagem é a MAIS adequada?

| Necessidade | Situação |
|-------------|----------|
| 1. Chatbot responde sobre política de devoluções atualizada semanalmente | Dados mudam frequentemente |
| 2. Modelo gera emails sempre no formato jurídico formal da empresa | Estilo consistente |
| 3. Classificar tickets em 3 categorias com alta acurácia | Tarefa simples, primeiro teste |

A) 1: Fine-tuning, 2: RAG, 3: Continued Pre-training  
B) 1: RAG, 2: Fine-tuning, 3: Prompt Engineering (few-shot)  
C) 1: Prompt Engineering, 2: Prompt Engineering, 3: Prompt Engineering  
D) 1: RAG, 2: RAG, 3: RAG  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) 1: RAG, 2: Fine-tuning, 3: Prompt Engineering (few-shot)**

✅ **Por que B está correta:** Regra: (1) dados que mudam → RAG (re-indexa sem re-treinar). (2) Estilo consistente que PE não mantém → fine-tuning. (3) Tarefa simples, primeiro teste → PE com few-shot (mais rápido e barato para validar).

❌ **Por que as outras estão erradas:**
- **A)** Inverte 1 e 2 — fine-tuning para dados semanais é impraticável; RAG para estilo não funciona.
- **C)** PE pode ser insuficiente para consistência de formato jurídico (necessidade 2) — o cenário diz que é específico da empresa.
- **D)** RAG não resolve estilo/formato (necessidade 2) nem é necessário para classificação simples (necessidade 3).

</details>
