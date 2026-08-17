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

