# Engenharia de Prompts — Testes e Refinamentos

Esta seção documenta os testes realizados no **Gemini Notebook** para avaliar como diferentes formas de construção de prompts influenciam a qualidade das respostas, a experiência de aprendizagem e a interação da ferramenta com as fontes disponibilizadas.

---

## Teste 1 — Prompt aberto

### Objetivo

Avaliar como o Gemini Notebook estrutura uma explicação quando recebe uma solicitação genérica sobre um conceito matemático.

### Prompt utilizado

```text
Explique produto vetorial.
```

### Resultado observado

O Gemini Notebook apresentou uma resposta estruturada abordando:

- definição do produto vetorial;
- direção, sentido e módulo do vetor resultante;
- regra da mão direita;
- interpretação geométrica da área do paralelogramo;
- cálculo por determinante;
- condição de paralelismo;
- obtenção de vetor normal a um plano;
- relação com produto misto e volume.

A resposta utilizou diferentes fontes disponíveis no notebook e apresentou referências aos materiais consultados.

### Pontos positivos

- boa organização do conteúdo;
- integração entre interpretação algébrica e geométrica;
- utilização das fontes cadastradas;
- apresentação de propriedades e aplicações do conceito.

### Limitações identificadas

Apesar de correta e abrangente, a resposta apresentou várias informações simultaneamente e não desenvolveu um exemplo numérico passo a passo.

Para um estudante que esteja aprendendo o conteúdo pela primeira vez, conceitos como determinante, ortogonalidade e vetor normal podem exigir explicações intermediárias adicionais.

### Aprendizado obtido

O teste demonstrou que prompts muito amplos podem gerar respostas completas, porém pouco direcionadas ao nível de conhecimento do estudante.

A partir dessa observação, os prompts seguintes passaram a especificar o nível de conhecimento esperado, a estrutura desejada para a resposta e a necessidade de apresentar todas as etapas da resolução.

---

## Teste 2 — Prompt estruturado para aprendizagem

### Objetivo

Verificar se a definição explícita da estrutura da resposta melhora a qualidade didática e o nível de detalhamento apresentado pelo Gemini Notebook.

### Prompt utilizado

```text
Explique produto vetorial considerando que estou aprendendo o conteúdo pela primeira vez.

Organize a explicação nesta ordem:

1. O que é produto vetorial;
2. Para que ele serve;
3. Interpretação geométrica;
4. Fórmula utilizada;
5. Um exemplo numérico fácil resolvido passo a passo;
6. Explique a origem de cada valor utilizado no cálculo;
7. Mostre como verificar se o resultado está correto;
8. Apresente um exercício semelhante para eu tentar resolver sozinho.

Não pule nenhuma etapa da resolução.
```

### Resultado observado

Diferentemente do primeiro teste, a resposta foi organizada seguindo exatamente a sequência solicitada no prompt.

O Gemini Notebook:

- apresentou primeiro o conceito de produto vetorial;
- explicou suas principais aplicações;
- relacionou o conteúdo à interpretação geométrica;
- apresentou a fórmula antes de iniciar os cálculos;
- resolveu um exemplo numérico passo a passo;
- explicou a origem das componentes utilizadas;
- realizou uma verificação matemática do resultado por meio do produto escalar;
- criou um exercício semelhante para prática independente.

No exemplo apresentado, foram utilizados os vetores:

$$
\vec{u} = (5,4,3)
$$

$$
\vec{v} = (1,0,1)
$$

O resultado obtido foi:

$$
\vec{u} \times \vec{v} = (4,-2,-4)
$$

A própria resposta realizou uma verificação matemática utilizando a propriedade de ortogonalidade do produto vetorial.

Os produtos escalares do vetor resultante com os dois vetores originais resultaram em zero, confirmando que o vetor encontrado era perpendicular a ambos.

### Pontos positivos

- maior adequação ao nível de conhecimento informado;
- sequência didática bem definida;
- resolução sem saltos significativos entre as etapas;
- explicação da origem dos valores utilizados;
- inclusão de uma etapa de verificação do resultado;
- criação de exercício para aprendizagem ativa;
- utilização das fontes do notebook ao longo da resposta.

### Limitações identificadas

A estrutura da resposta atendeu ao objetivo proposto, incluindo um exemplo resolvido passo a passo e, posteriormente, um novo exercício para prática independente.

Entretanto, ao apresentar o exercício, o Gemini Notebook também forneceu imediatamente o gabarito. Embora isso permita conferência, a antecipação do resultado pode reduzir o esforço de resolução independente.

### Refinamento

Em um teste posterior, foi acrescentada a instrução para que o exercício fosse apresentado **sem gabarito** e para que a ferramenta aguardasse a tentativa do estudante antes de fornecer qualquer correção.

### Aprendizado obtido

A comparação com o primeiro teste mostrou que especificar o nível do estudante, a sequência da explicação e as etapas obrigatórias da resolução melhora significativamente a utilidade da resposta para fins de aprendizagem.

Também ficou evidente que pequenos detalhes nas instruções influenciam o comportamento da IA.

Para utilizar o Gemini Notebook como tutor, tornou-se necessário especificar que o gabarito não deveria ser apresentado antes da tentativa de resolução do estudante.

---

## Teste 3 — Tutoria, correção e aprendizagem ativa

### Objetivo

Avaliar se o Gemini Notebook consegue acompanhar a resolução de um exercício, identificar erros e orientar o estudante sem fornecer imediatamente a resposta correta.

### Exercício proposto

O Gemini Notebook apresentou um novo exercício envolvendo os vetores:

$$
\vec{u} = (3,1,2)
$$

$$
\vec{v} = (1,2,0)
$$

A atividade solicitava:

1. calcular o produto vetorial entre os dois vetores;
2. verificar a ortogonalidade do resultado utilizando o produto escalar com cada vetor original.

Diferentemente do teste anterior, o exercício foi apresentado **sem gabarito**, permitindo que a resolução fosse realizada de forma independente.

### Teste da correção

Para avaliar o comportamento da ferramenta como tutor, foi inserido propositalmente um erro durante a verificação do produto escalar.

Após obter corretamente:

$$
\vec{u} \times \vec{v} = (-4,2,5)
$$

foi realizada corretamente a primeira verificação:

$$
(-4)\cdot3 + 2\cdot1 + 5\cdot2 = -12 + 2 + 10 = 0
$$

Na verificação com o segundo vetor, entretanto, foi apresentada propositalmente a seguinte resposta:

$$
-4 + 4 + 5 = 5
$$

### Comportamento observado

O Gemini Notebook identificou corretamente que o erro estava na terceira componente do produto escalar.

Em vez de apresentar diretamente a resposta final, a ferramenta chamou atenção para a operação:

$$
5\cdot0
$$

e solicitou que o cálculo fosse revisto.

Quando foi solicitada uma dica adicional, o Gemini Notebook lembrou a propriedade de que qualquer número multiplicado por zero resulta em zero e apresentou a expressão:

$$
(-4) + 4 + 0
$$

novamente solicitando que o estudante concluísse o cálculo.

### Pontos positivos

- identificou corretamente a etapa em que ocorreu o erro;
- não substituiu imediatamente a resolução do estudante pela resposta correta;
- utilizou perguntas para orientar a correção;
- apresentou uma dica progressiva quando solicitado;
- manteve o estudante participando do processo de resolução;
- utilizou o erro como oportunidade de reforçar um conceito matemático básico.

Esse comportamento aproximou a interação de uma dinâmica de **tutoria**, em vez de simplesmente fornecer uma solução pronta.

### Limitação identificada

Apesar de a resposta principal preservar o processo de raciocínio, foi identificada uma limitação na experiência de aprendizagem.

Após a interação, uma das sugestões automáticas de continuação apresentadas pela interface continha a frase:

> **“Isso mesmo! O resultado é 0.”**

Essa sugestão antecipava exatamente o resultado que ainda deveria ser calculado pelo estudante.

Assim, mesmo que a resposta principal da IA evitasse revelar a solução, um elemento auxiliar da interface poderia permitir que o usuário chegasse à conclusão sem efetivamente completar o cálculo.

### Cicatriz identificada

Esse comportamento mostrou que a aprendizagem ativa não depende apenas da formulação do prompt ou da resposta principal produzida pela IA.

Elementos auxiliares da interface, como sugestões automáticas de continuação, também podem influenciar o processo de resolução e eventualmente antecipar informações que deveriam ser descobertas pelo estudante.

Portanto, ao utilizar ferramentas de IA como apoio educacional, é importante manter uma postura crítica não apenas diante das respostas geradas, mas também diante dos recursos adicionais apresentados pela própria ferramenta.

### Aprendizado obtido

O teste demonstrou que o Gemini Notebook pode atuar de maneira eficiente na identificação e correção progressiva de erros, especialmente quando recebe instruções para não apresentar imediatamente a solução.

Ao mesmo tempo, evidenciou uma limitação importante: mesmo quando o fluxo principal da conversa favorece o raciocínio independente, sugestões automáticas podem interferir nesse processo.

A experiência reforçou que o uso da IA como ferramenta de aprendizagem exige participação ativa do estudante, avaliação crítica das informações apresentadas e cuidado para que recursos de conveniência não substituam o esforço necessário à construção do raciocínio.

---

## Teste 4 — Comparação entre fontes

### Objetivo

Avaliar a capacidade do Gemini Notebook de consultar diferentes fontes da base de conhecimento, identificar convergências e diferenças entre abordagens didáticas e sintetizar essas informações de forma estruturada.

### Prompt utilizado

```text
Compare a abordagem utilizada pelo Professor Grings e pela Univesp para explicar produto vetorial.

Identifique:

1. conceitos abordados em comum;
2. diferenças na forma de apresentação;
3. exemplos utilizados;
4. vantagens didáticas de cada abordagem;
5. pontos que se complementam.

Baseie a comparação apenas nas fontes disponíveis neste notebook e indique quais fontes foram utilizadas.
```

### Resultado observado

O Gemini Notebook organizou a comparação em cinco dimensões e indicou as fontes utilizadas para construir a resposta.

Entre os principais pontos em comum identificados estavam:

- definição do produto vetorial no espaço tridimensional;
- ortogonalidade do vetor resultante;
- cálculo utilizando determinante;
- interpretação geométrica do módulo como área;
- regra da mão direita;
- anticomutatividade;
- utilização do produto vetorial na determinação de vetores normais;
- relação com produto misto e cálculo de volumes.

### Diferenças identificadas

Segundo a síntese produzida pelo Gemini Notebook, as fontes do **Professor Grings** apresentaram uma abordagem predominantemente prática, visual e orientada à resolução de exercícios, com atenção ao desenvolvimento dos cálculos e à verificação dos resultados.

Já os conteúdos da **Univesp** foram associados a uma apresentação mais formal e estruturada academicamente, relacionando o produto vetorial a outros conceitos da disciplina e a aplicações posteriores.

A comparação também mostrou diferenças no tipo de exemplo utilizado. As fontes do Professor Grings concentraram-se principalmente em cálculos numéricos, equações de planos e aplicações geométricas, enquanto as fontes da Univesp incluíram, além dos exemplos algébricos, relações entre versores e aplicações associadas a outros conteúdos matemáticos e físicos.

### Complementaridade das fontes

Um dos resultados mais relevantes do teste foi a identificação de complementaridade entre as duas abordagens.

A síntese do Gemini Notebook indicou que os conteúdos da Univesp contribuem principalmente para a construção da fundamentação conceitual e formal, enquanto as aulas do Professor Grings favorecem a compreensão operacional e a prática de resolução de exercícios.

Dessa forma, a utilização conjunta das duas fontes permite combinar teoria, interpretação geométrica e prática de cálculo.

### Fontes utilizadas pelo Gemini Notebook

A resposta indicou, entre outras, as seguintes fontes disponíveis no notebook:

1. *Análise Curricular e Mapeamento Didático da Disciplina de Geometria Analítica e Álgebra Linear*;
2. *Estudo Didático-Analítico da Álgebra Vetorial, Geometria Analítica e Superfícies Quádricas*;
3. *Geometria Analítica e Álgebra Linear — Aula 12 — Produtos Vetorial e Misto*;
4. *Geometria Analítica e Álgebra Linear — Aula 11 — Distâncias*;
5. *GRINGS — Geometria Analítica — Produto Vetorial — Aula 7*;
6. *GRINGS — Produto Vetorial — Geometria Analítica*;
7. *GRINGS — Equação Geral do Plano a partir de 3 pontos — Geometria Analítica*.

### Pontos positivos

- utilização simultânea de diferentes fontes da base;
- identificação de conceitos em comum;
- comparação estruturada entre abordagens didáticas;
- indicação das fontes utilizadas;
- capacidade de relacionar materiais que originalmente foram produzidos de forma independente;
- geração de uma síntese útil para decidir como utilizar cada fonte durante os estudos.

### Limitações e cuidados

A comparação produzida pela IA representa uma **síntese das fontes consultadas**, e não uma avaliação definitiva sobre a metodologia de cada professor ou instituição.

Por esse motivo, classificações como “mais prática” ou “mais formal” devem ser interpretadas dentro do conjunto específico de materiais disponíveis no notebook.

Esse teste também reforçou a importância de verificar quais fontes foram utilizadas na geração da resposta antes de aceitar comparações ou generalizações produzidas pela IA.

### Aprendizado obtido

O teste mostrou uma das principais vantagens de trabalhar com uma base ampla de fontes: o Gemini Notebook pode ser utilizado não apenas para localizar informações isoladas, mas também para **relacionar materiais, comparar abordagens e sintetizar diferentes perspectivas sobre um mesmo conteúdo**.

Essa capacidade torna a ferramenta útil para identificar quais materiais podem ser mais adequados para compreensão conceitual, resolução de exercícios, revisão ou aprofundamento.

---

## Síntese da evolução dos testes

| Teste | Estratégia | Principal resultado |
|---|---|---|
| **1** | Prompt aberto | Resposta ampla, porém pouco direcionada ao nível do estudante |
| **2** | Prompt estruturado | Explicação organizada, exemplo passo a passo e exercício |
| **3** | Tutoria e correção | Identificação de erro sem fornecimento imediato da resposta |
| **4** | Comparação entre fontes | Síntese e relação entre diferentes abordagens didáticas |

Os quatro testes demonstram que o uso do Gemini Notebook pode evoluir de uma consulta simples para atividades de **explicação estruturada, tutoria, correção e análise comparativa de fontes**.
