#                    Vou utilizar essa página para rascunhos dos meus estudos relacionados a IA


1. O que é um LLM ( modelo de linguagem grande )?
R: Um tipo de modelo de IA projetado para gerar texto semelhante ao humano.

2. Qual é a finalidade da tokenização?
    R: Para dividir o texto em unidades menores.

3. O que são inserções?
   R: Representações baseadas em vetor de tokens que capturam seu significado semântico.

4. O que uma camada de atenção faz em um modelo de transformador?
   R: Examina as relações entre cada token e os tokens ao seu redor.

 5. Qual é a finalidade de um prompt do sistema?
    R: Para fornecer contexto e instruções ao modelo de IA.

  6. O que é um agente no contexto da IA?
     R: Um sistema de IA que pode executar tarefas em nome de um usuário.

     # Análise de Frequência
Talvez a maneira mais óbvia de verificar os tópicos discutidos em um documento seja simplesmente contar o número de vezes que cada token normalizado aparece. A suposição é que os termos usados com mais frequência no documento podem ajudar a identificar os assuntos ou temas discutidos. Simplificando, se você puder determinar as palavras mais usadas em um determinado documento, muitas vezes você poderá ter uma boa ideia do que se trata o documento.

  # Tokenização
  A primeira etapa na análise de um corpo de texto (conhecido como corpus) é dividi-lo em tokens. Para simplificar, você pode pensar em cada palavra distinta no texto como um token. Na realidade, os tokens podem ser gerados para palavras parciais ou combinações de palavras e pontuação.

Por exemplo, considere esta frase de um famoso discurso presidencial dos EUA: "We choose to go to the moon". A frase pode ser dividida nos seguintes tokens, com identificadores numéricos:

1.We

2.choose

3.to

4.go

5.to

6.the

7.moon

Observe que "to" (número de token 3) é usado duas vezes no corpus. A frase "We choose to go to the moon" pode ser representada pelos tokens.

Com cada token atribuído a um valor discreto, podemos contar facilmente sua frequência no texto e usá-lo para determinar os termos mais usados; que pode ajudar a identificar o assunto principal do texto.

# Normalização de texto

Antes de gerar tokens, você pode optar por normalizar o texto removendo a pontuação e alterando todas as palavras para maiúsculas e minúsculas. Para análise que depende apenas da frequência de palavras, essa abordagem melhora o desempenho geral. No entanto, algum significado semântico pode ser perdido - por exemplo, considere a frase "Mr Banks has worked in many banks.". Talvez você queira que sua análise diferencie entre a pessoa "Mr Banks" e a "banks" em que ele trabalhou. Talvez você também queira considerar "banks." como um token separado de "banks", porque a inclusão de um ponto indica que a palavra aparece no final de uma frase.

# Remoção de palavras irrelevantes

Palavras irrelevantes são palavras que devem ser excluídas da análise. Por exemplo, "the", "a"ou "it" tornar o texto mais fácil para as pessoas lerem, mas adicionarem pouco significado semântico. Excluindo essas palavras, uma solução de análise de texto pode ser mais capaz de identificar as palavras importantes.

# Extração de N-grama

Localizando frases de vários termos, como "artificial intelligence" ou "natural language processing". Uma única frase de palavra é um unigrama, uma frase de duas palavras é um bigram, uma frase de três palavras é um trigrama, e assim por diante. Em muitos casos, considerando a exibição frequente de sequências de palavras como grupos, um algoritmo de análise de texto pode fazer melhor sentido do texto.

# Lematização

Uma técnica usada para consolidar palavras retirando terminações como "s", "ing", "ed" e assim por diante, antes de contá-las; para que as palavras com a mesma raiz etimológica, como "powering", "powered" e "powerful", sejam interpretadas como sendo o mesmo token ("power").

Outra abordagem para reduzir palavras à sua forma básica ou de dicionário (conhecida como lema). Diferente da derivação, que simplesmente corta terminações de palavras, a lematização usa regras linguísticas e vocabulário para garantir que a forma resultante seja uma palavra válida (por exemplo, "running": → "run", "global" → "globe").

# Marcação de partes de fala (POS)

Rotulando cada token com sua categoria gramatical, como substantivo, verbo, adjetivo ou advérbio. Essa técnica usa regras linguísticas e, muitas vezes, modelos estatísticos para determinar a marca correta com base no próprio token e em seu contexto dentro da frase.


# TF/IDF - frequência de termo/frequência de documento inverso (TF-IDF)

A análise de frequência simples na qual você conta o número de ocorrências de cada token pode ser uma maneira eficaz de analisar um único documento, mas quando você precisa diferenciar vários documentos dentro do mesmo corpus, você precisa de uma maneira de determinar quais tokens são mais relevantes em cada documento individual.

# Frequência de Termos – Frequência inversa de Documentos (TF-IDF) 

é uma técnica que calcula pontuações com base na frequência com que uma palavra ou termo aparece em um documento em comparação com sua frequência mais geral em toda a coleção de documentos. Usando essa técnica, um alto grau de relevância é considerado para palavras que aparecem com frequência em um documento específico, mas relativamente pouco frequentes em uma ampla gama de outros documentos. Para calcular TF-IDF para termos em um documento individual, você pode usar o seguinte processo de três etapas:

## Calcular frequência de termo (TF): 

Trata-se simplesmente de quantas vezes uma palavra aparece em um documento. Por exemplo, se a palavra "agent" aparecer 6 vezes em um documento, então tf(agent) = 6.

## Calcular a frequência inversa de documentos (IDF): 

Isso verifica o quão comum ou rara é uma palavra em todos os documentos. Se uma palavra aparecer em cada documento, ela não será especial. A fórmula usada para calcular o IDF é idf(t) = log(N / df(t)) (onde N está o número total de documentos e df(t) é o número de documentos que contêm a palavra t)

## Combine-os para calcular TF-IDF: 

Multiplique TF e IDF para obter a pontuação: tfidf(t, d) = tf(t, d) * log(N / df(t))

# Técnicas de aprendizado de máquina "saco de palavras"
## Recipiente de palavras

É o nome dado a uma técnica de extração de recursos que representa tokens de texto como um vetor de frequências ou ocorrências de palavras, ignorando a gramática e a ordem das palavras. Essa representação torna-se a entrada para algoritmos de aprendizado de máquina como Naive Bayes, um classificador probabilístico que aplica o teorema de Bayes para prever a classe provável de um documento com base na frequência de palavras.

Por exemplo, você pode usar essa técnica para treinar um modelo de machine learning que executa a filtragem de spam por email. As palavras "miracle cure", "lose weight fast"e "anti-envelhecimento", podem aparecer com mais frequência em emails de spam sobre produtos de saúde duvidosos do que seus e-mails regulares, e um modelo treinado pode sinalizar mensagens contendo essas palavras como spam em potencial.

Você pode implementar a análise de sentimento usando o mesmo método para classificar o texto por tom emocional. O pacote de palavras fornece os recursos e o modelo usa esses recursos para estimar probabilidades e atribuir rótulos de sentimento como "positivo" ou "negativo".

# TextRank

TextRank é um algoritmo baseado em gráfico não supervisionado que modela o texto como uma rede de nós interconectados. Por exemplo, cada frase em um documento pode ser considerada um nó e as conexões (bordas) entre elas são pontuadas com base na similaridade das palavras que contêm. TextRank é comumente usado para resumir texto com base na identificação de um subconjunto de frases em um documento que melhor represente seu assunto geral.

O algoritmo TextRank aplica o mesmo princípio que o algoritmo PageRank do Google (que classifica páginas da Web com base em links entre elas) ao texto. A ideia principal é que uma frase é importante se for semelhante a muitas outras frases importantes. O algoritmo funciona pelas seguintes etapas:

Crie um grafo: cada frase se torna um nó, e as bordas que as conectam são ponderadas pela similaridade (geralmente medida usando sobreposição de palavras ou similaridade de cosseno entre vetores de frase).

Calcular classificações iterativamente: a pontuação de cada nó é calculada com base nas pontuações dos nós conectados a ele. A fórmula é: TextRank(Sᵢ) = (1-d) + d * Σ(wⱼᵢ / Σwⱼₖ) * TextRank(Sⱼ) (onde d é um fator de amortecimento, normalmente 0,85, wⱼᵢ é o peso da borda da frase j para a frase i, e a soma é realizada sobre todas as frases conectadas a i).

Extraia as frases mais bem classificadas: após a convergência, as frases com as pontuações mais altas são selecionadas como o resumo.

Por exemplo, considere o seguinte documento sobre computação em nuvem:

Cloud computing provides on-demand access to computing resources. Computing resources include servers, storage, and networking. Azure is Microsoft's cloud computing platform. Organizations use cloud platforms to reduce infrastructure costs. Cloud computing enables scalability and flexibility.

Para gerar um resumo deste documento, o processo TextRank começa dividindo este documento em frases:

Cloud computing provides on-demand access to computing resources.
Computing resources include servers, storage, and networking.
Azure is Microsoft's cloud computing platform.
Organizations use cloud platforms to reduce infrastructure costs.
Cloud computing enables scalability and flexibility.
Em seguida, as bordas são criadas entre frases com pesos baseados na similaridade (sobreposição de palavras). Para este exemplo, os pesos de borda podem ser:

Frase 1 <-> Frase 2: 0,5 (compartilhamentos "computing resources")
Sentença 1 <-> Sentença 3: 0,6 (compartilhamentos "cloud computing")
Sentença 1 <-> Sentença 4: 0,2 (compartilhamentos "cloud")
Sentença 1 <-> Sentença 5: 0,7 (compartilhamentos "cloud computing")
Sentença 2 <-> Sentença 3: 0.2 (sobreposição limitada)
Sentença 2 <-> Sentença 4: 0.1 (sobreposição limitada)
Sentença 2 <-> Sentença 5: 0,1 (compartilhamentos "computing")
Sentença 3 <-> Sentença 4: 0,5 (compartilhamentos "cloud platforms")
Sentença 3 <-> Sentença 5: 0,4 (compartilhamentos "cloud computing")
Sentença 4 <-> Sentença 5: 0.3 (sobreposição limitada)

<img width="404" height="314" alt="image" src="https://github.com/user-attachments/assets/fc0b1e4c-e75d-4f57-b6f1-dad1e68ce3e2" />

Depois de calcular iterativamente as pontuações do TextRank usando esses pesos, as frases 1, 3 e 5 podem receber as pontuações mais altas, pois se conectam bem a outras frases através de terminologia e conceitos compartilhados. Essas frases seriam selecionadas para formar um resumo conciso: "Cloud computing provides on-demand access to computing resources. Azure is Microsoft's cloud computing platform. Cloud computing enables scalability and flexibility."
TextRank também pode ser aplicado no nível da palavra para extração de palavras-chave, em que palavras (em vez de frases) se tornam nós e as bordas representam a co-ocorrência dentro de uma janela fixa. As palavras mais bem classificadas são extraídas como termos-chave que representam os principais tópicos do documento.

# Modelos de linguagem semântica

Como o estado da arte para NLP avançou, a capacidade de treinar modelos que encapsulam a relação semântica entre tokens levou ao surgimento de poderosos modelos de linguagem de aprendizado profundo. No cerne desses modelos está a codificação dos tokens de linguagem como vetores (matrizes de valores múltiplos) conhecidos como inserções.

Essa abordagem baseada em vetor para modelagem de texto tornou-se comum com técnicas como Word2Vec e GloVe, nas quais tokens de texto são representados como vetores densos com várias dimensões. Durante o treinamento de modelo, os valores de dimensão são atribuídos para refletir características semânticas de cada token com base em seu uso no texto de treinamento. As relações matemáticas entre os vetores podem então ser exploradas para executar tarefas comuns de análise de texto com mais eficiência do que técnicas puramente estatísticas mais antigas. Um avanço mais recente nessa abordagem é usar uma técnica chamada atenção para considerar cada token no contexto e calcular a influência dos tokens ao seu redor. As inserções contextualizadas resultantes, como as encontradas na família gpt de modelos, fornecem a base da IA generativa moderna.


# Representando o texto como vetores
Os vetores representam pontos no espaço multidimensional, definidos por coordenadas ao longo de vários eixos. Cada vetor descreve uma direção e uma distância da origem. Tokens semanticamente semelhantes devem resultar em vetores que têm uma orientação semelhante– em outras palavras, eles apontam em direções semelhantes.

Por exemplo, considere as seguintes inserções tridimensionais para algumas palavras comuns:

Palavra	Vector
dog	[0.8, 0.6, 0.1]
puppy	[0.9, 0.7, 0.4]
cat	[0.7, 0.5, 0.2]
kitten	[0.8, 0.6, 0.5]
young	[0.1, 0.1, 0.3]
ball	[0.3, 0.9, 0.1]
tree	[0.2, 0.1, 0.9]

Podemos visualizar esses vetores no espaço tridimensional, conforme mostrado aqui:

<img width="592" height="480" alt="image" src="https://github.com/user-attachments/assets/765f6750-a1b7-4c60-a6b4-6ac15eb30c59" />


Diagrama de uma visualização 3D de vetores de palavras.

Os vetores para "dog" e "cat" são semelhantes (ambos animais domésticos), como são "puppy" e "kitten" (ambos animais jovens). As palavras "tree", "young"e ball" têm orientações vetoriais distintamente diferentes, refletindo seus diferentes significados semânticos.

A característica semântica codificada nos vetores possibilita o uso de operações baseadas em vetor que comparam palavras e permitem comparações analíticas.

Localizando termos relacionados
Como a orientação dos vetores é determinada por seus valores de dimensão, palavras com significados semânticos semelhantes tendem a ter orientações semelhantes. Isso significa que você pode usar cálculos como a similaridade de cosseno entre vetores para fazer comparações significativas.

Por exemplo, para determinar o "elemento destoante" entre "dog", "cat" e "tree", você pode calcular a similaridade do cosseno entre pares de vetores. A similaridade do cosseno é calculada como:

cosine_similarity(A, B) = (A · B) / (||A|| * ||B||)

Onde A · B está o produto ponto e ||A|| é a magnitude do vetor A.

Calculando semelhanças entre as três palavras:

dog [0.8, 0.6, 0.1] e cat [0.7, 0.5, 0.2]:

Produto ponto: (0,8 × 0,7) + (0,6 × 0,5) + (0,1 × 0,2) = 0,56 + 0,30 + 0,02 = 0,88
Magnitude de dog: √(0,8² + 0,6² + 0,1²) = √(0,64 + 0,36 + 0,01) = √1,01 ≈ 1,005
Magnitude de cat: √(0,7² + 0,5² + 0,2²) = √(0,49 + 0,25 + 0,04) = √0,78 ≈ 0,883
Similaridade cosseno: 0,88 / (1,005 × 0,883) ≈ 0,992 (alta similaridade)
dog [0.8, 0.6, 0.1] e tree [0.2, 0.1, 0.9]:

<img width="595" height="482" alt="image" src="https://github.com/user-attachments/assets/78c5234e-2e4b-475b-94fc-b0693cc5a687" />


Produto ponto: (0,8 × 0,2) + (0,6 × 0,1) + (0,1 × 0,9) = 0,16 + 0,06 + 0,09 = 0,31
Magnitude de tree: √(0,2² + 0,1² + 0,9²) = √(0,04 + 0,01 + 0,81) = √0,86 ≈ 0,927
Similaridade cosseno: 0,31 / (1,005 × 0,927) ≈ 0,333 (similaridade baixa)
cat [0.7, 0.5, 0.2] e tree [0.2, 0.1, 0.9]:

Produto ponto: (0,7 × 0,2) + (0,5 × 0,1) + (0,2 × 0,9) = 0,14 + 0,05 + 0,18 = 0,37
Similaridade cosseno: 0,37 / (0,883 × 0,927) ≈ 0,452 (similaridade baixa)
Diagrama da visualização da similaridade do cosseno, mostrando vetores de cachorro, gato e árvore.

Os resultados mostram isso "dog" e "cat" são altamente semelhantes (0,992), enquanto "tree" têm menor semelhança com ambos "dog" (0,333) e "cat" (0,452). Portanto, tree é claramente a exceção.





























































