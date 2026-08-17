# Questões — Arquitetura Transformer

---

### Questão 1

Qual é a principal vantagem da arquitetura Transformer sobre RNNs (Redes Neurais Recorrentes) para processamento de linguagem?

A) Transformers usam menos memória  
B) Transformers processam tokens em paralelo, permitindo treinamento muito mais rápido  
C) Transformers não precisam de GPUs  
D) Transformers são mais simples de implementar  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Transformers processam tokens em paralelo, permitindo treinamento muito mais rápido**

✅ **Por que B está correta:** RNNs processam sequencialmente (token por token), o que é lento e não paralelizável. Transformers usam self-attention para processar todos os tokens em paralelo, acelerando dramaticamente o treinamento.

❌ **Por que as outras estão erradas:**
- **A)** Transformers geralmente usam MAIS memória (atenção é O(n²) no tamanho da sequência).
- **C)** Transformers requerem GPUs massivamente — são computacionalmente intensivos.
- **D)** A arquitetura Transformer é mais complexa que RNNs simples.

</details>

---

### Questão 2

O que o mecanismo de self-attention permite que um LLM faça?

A) Memorizar todo o dataset de treinamento  
B) Calcular a relevância de cada token em relação a todos os outros tokens na sequência  
C) Gerar imagens a partir de texto  
D) Acessar informações da internet em tempo real  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Calcular a relevância de cada token em relação a todos os outros tokens na sequência**

✅ **Por que B está correta:** Self-attention permite que cada token "olhe" para todos os outros tokens e determine quais são mais relevantes para entender o contexto. Isso captura relações de longa distância.

❌ **Por que as outras estão erradas:**
- **A)** LLMs aprendem padrões, não memorizam literalmente o dataset.
- **C)** Geração de imagens requer arquiteturas específicas (diffusion models), não apenas attention.
- **D)** LLMs não acessam a internet — processam apenas o input fornecido.

</details>

---

### Questão 3

Modelos como GPT, Claude e Llama usam principalmente qual parte da arquitetura Transformer?

A) Apenas o Encoder  
B) Apenas o Decoder  
C) Encoder-Decoder completo  
D) Nenhuma — usam RNNs  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Apenas o Decoder**

✅ **Por que B está correta:** GPT, Claude e Llama são modelos decoder-only. Geram texto autoregressivamente (token por token), usando apenas a parte decoder do Transformer original.

❌ **Por que as outras estão erradas:**
- **A)** Encoder-only é usado por modelos como BERT (compreensão, não geração).
- **C)** Encoder-Decoder é usado por modelos como T5 (tradução, resumo).
- **D)** Todos os LLMs modernos são baseados em Transformers, não RNNs.

</details>

---

### Questão 4

O que é tokenização no contexto de LLMs?

A) O processo de criptografar os dados antes do processamento  
B) O processo de dividir texto em unidades menores que o modelo processa  
C) O processo de converter texto em imagens  
D) O processo de validar a autenticidade do input  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) O processo de dividir texto em unidades menores que o modelo processa**

✅ **Por que B está correta:** Tokenização converte texto em tokens (subpalavras, palavras ou caracteres) que são as unidades processáveis pelo modelo. Define o custo (por token) e os limites de context window.

❌ **Por que as outras estão erradas:**
- **A)** Tokenização não é criptografia — é pré-processamento de texto.
- **C)** Conversão texto→imagem é geração de imagem, não tokenização.
- **D)** Tokenização não valida nada — apenas divide texto em unidades.

</details>

---

### Questão 5

Por que Transformers usam positional encoding?

A) Para criptografar a posição dos dados na memória  
B) Para adicionar informação de ordem das palavras, já que processam tokens em paralelo  
C) Para comprimir o texto e usar menos memória  
D) Para identificar o idioma do texto  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Para adicionar informação de ordem das palavras, já que processam tokens em paralelo**

✅ **Por que B está correta:** Como Transformers processam todos os tokens simultaneamente (paralelo), perdem a noção de sequência. Positional encoding injeta informação de posição para que o modelo saiba a ordem das palavras.

❌ **Por que as outras estão erradas:**
- **A)** Não é criptografia — é codificação de posição sequencial.
- **C)** Não comprime texto — adiciona informação extra a cada token.
- **D)** Detecção de idioma é uma tarefa diferente, não relacionada a positional encoding.

</details>

