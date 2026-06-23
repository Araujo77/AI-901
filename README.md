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

# Modelos de linguagem semântica (NLP)

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


# Processamento de Linguagem Natural (PLN)

O processamento de linguagem natural é um campo da IA que permite que computadores entendam e respondam à linguagem humana. Ele preenche a lacuna entre a comunicação humana e o processamento computacional, combinando técnicas de linguística computacional, aprendizado de máquina e aprendizado profundo.

O PLN analisa grandes volumes de texto ou fala para ajudar os computadores a reconhecer padrões, extrair informações relevantes e gerar respostas semelhantes às humanas. É usado em aplicações do mundo real, como motores de busca, ferramentas de tradução de idiomas, suporte ao cliente automatizado e assistentes digitais pessoais como Siri, Alexa e Cortana.

# Coeficientes Cepstrais de Frequência Mel (MFCCs)

O MFCC é a técnica de extração de recursos mais comum no reconhecimento de fala. Ele imita como o ouvido humano percebe o som enfatizando frequências onde a energia da fala se concentra e compactando intervalos menos importantes.

Como funciona o MFCC
Dividir áudio em quadros: Divida o sinal em janelas sobrepostas de 20 a 30 milissegundos.
Aplicar a transformação Fourier: converta cada quadro do domínio de tempo em domínio de frequência, revelando quais tons estão presentes.
Escala mapeada para Mel: ajuste os intervalos de frequência para corresponder à sensibilidade auditiva humana — distinguimos melhor os tons graves do que os agudos.
Extrair coeficientes: Compute um pequeno conjunto de números (geralmente 13 coeficientes) que resumem a forma espectral de cada quadro.
O resultado é uma sequência de vetores de recursos , um por quadro, que captura como o áudio soa sem armazenar cada exemplo. Esses vetores se tornam a entrada para modelagem acústica.

Os vetores são extraídos por coluna, com cada vetor representando os 13 coeficientes das características MFCC para cada quadro temporal.

Frame 1: [ -113.2,  45.3,  12.1,  -3.4,  7.8,  ... ]  # 13 coefficients
Frame 2: [ -112.8,  44.7,  11.8,  -3.1,  7.5,  ... ]
Frame 3: [ -110.5,  43.9,  11.5,  -2.9,  7.3,  ... ]


# Modelagem acústica: reconhecer phonemes

Os modelos acústicos aprendem a relação entre recursos de áudio e phonemes — as menores unidades de som que distinguem palavras. O inglês usa cerca de 44 phonemes; por exemplo, a palavra "gato" é composta por três phonemes: /k/, /æ/, e /t/.

De recursos a phonemes
Os modelos acústicos modernos usam arquiteturas de transformador, um tipo de rede de aprendizado profundo que se destaca em tarefas de sequência. O transformador processa os vetores de recurso MFCC e prevê qual fonema é mais provável em cada momento no tempo.

## Modelos de transformador alcançam previsão efetiva de fonemas por meio de:

Mecanismo de atenção: O modelo examina os quadros ao redor para resolver a ambiguidade. Por exemplo, o fonema /t/ soa diferente no início de "top" e no final de "bat".
Processamento paralelo: Ao contrário dos modelos recorrentes mais antigos, os transformadores analisam vários quadros simultaneamente, melhorando a velocidade e a precisão.
Previsões contextualizadas: A rede aprende que determinadas sequências de phoneme ocorrem com frequência na fala natural.
A saída da modelagem acústica é uma distribuição de probabilidade sobre fonemas para cada quadro de áudio. Por exemplo, o quadro 42 pode mostrar 80% de confiança para /æ/, 15% para /ɛ/ e 5% para outros fonemas.

# Modelagem de idioma: prever sequências de palavras

As previsões de phoneme por si só não garantem a transcrição precisa. O modelo acústico pode confundir "deles" e "lá" porque eles compartilham fonemas idênticos. Os modelos de linguagem resolvem a ambiguidade aplicando conhecimento de vocabulário, gramática e padrões comuns de palavras. Algumas maneiras pelas quais o modelo guia a previsão de sequência de palavras incluem:

Padrões estatísticos: o modelo sabe que "O clima está bom" aparece com mais frequência em dados de treinamento do que "O se é bom".
Consciência de contexto: depois de ouvir "Eu preciso", o modelo espera verbos como "ir" ou "concluir", não substantivos como "tabela".
Adaptação de domínio: Modelos de linguagem personalizados treinados em terminologia médica ou legal melhoram a precisão para cenários especializados.
Decodificação: selecione a melhor hipótese de texto
Algoritmos de decodificação pesquisam milhões de sequências de palavras possíveis para encontrar a transcrição que melhor corresponde às previsões do modelo acústico e de linguagem. Esse estágio equilibra duas metas concorrentes: manter-se fiel ao sinal de áudio ao produzir texto legível e gramaticalmente correto.

## Decodificação de pesquisa de feixe

A técnica mais comum, a pesquisa de feixe, mantém uma lista de seleção (o "feixe") de transcrições parciais de pontuação superior à medida que processa cada quadro de áudio. A cada etapa, a hipótese é estendida com a próxima palavra mais provável, enquanto os caminhos de baixa pontuação são eliminados, mantendo apenas os melhores candidatos.

Para um enunciado de três segundos, o decodificador pode avaliar milhares de hipóteses antes de selecionar "Envie o relatório até sexta-feira" sobre alternativas como "Envie o relatório comprar sexta-feira".

# Pós-processamento: refinar a saída
O decodificador produz texto bruto que geralmente requer limpeza antes da apresentação. O pós-processamento aplica regras de formatação e correções para melhorar a legibilidade e a precisão.

## Tarefas comuns pós-processamento

Capitalização: Converta "olá meu nome é Sam" em "Olá, meu nome é Sam".
Restauração de pontuação: Adicione períodos, vírgulas e pontos de interrogação com base em prosódia e gramática.
Formatação de número: Altere "mil vinte e três" para "1.023".
Filtragem de palavrões: Mascarar ou remover palavras inadequadas quando exigido pela política.
Normalização inversa de texto: Converta formas faladas como "três da tarde" em "15:00".
Pontuação de confiança: Sinalizar palavras de baixa confiança para revisão humana em aplicativos críticos, como transcrição médica.
A Fala do Azure retorna a transcrição final junto com metadados, como carimbos de data/hora no nível de palavra e pontuações de confiança, permitindo que seu aplicativo destaque segmentos incertos ou acione comportamentos de fallback.

# Como o pipeline funciona em conjunto

Cada estágio se baseia no anterior:

A captura de áudio fornece o sinal bruto.
O pré-processamento extrai recursos do MFCC que realçam padrões de fala.
A modelagem acústica prevê probabilidades de phoneme usando redes transformadoras.
A modelagem de linguagem aplica o vocabulário e o conhecimento gramatical.
A decodificação procura a melhor sequência de palavras.
O pós-processamento formata o texto para leitores humanos.
Ao separar preocupações, os sistemas modernos de reconhecimento de fala alcançam alta precisão entre linguagens, acentos e condições acústicas. Quando a qualidade da transcrição fica aquém, muitas vezes você pode rastrear o problema para um estágio — captura de áudio ruim, treinamento de modelo de linguagem insuficiente ou pós-processamento excessivamente agressivo — e ajustar adequadamente.

A síntese de fala, também chamada de TTS (conversão de texto em fala), converte o texto escrito em áudio falado. Você encontra síntese de fala quando assistentes virtuais leem notificações, aplicativos de navegação anunciam instruções ou ferramentas de acessibilidade ajudam os usuários a consumir conteúdo escrito audivelmente.

Os sistemas de síntese de fala processam o texto em quatro estágios distintos. Em cada estágio, a entrada é transformada incrementalmente, desenvolvendo-se até se tornar uma forma de onda de áudio final que soa natural e inteligível.

# Normalização de texto: padronizar o texto

A normalização de texto prepara o texto bruto para a pronúncia expandindo abreviações, números e símbolos em formas faladas.

Considere a sentença: "Dr. Smith ordenou 3 itens por US$ 25,50 em 15/12/2023."

Um sistema de normalização converte-o em: "O Doutor Smith pediu três itens por 25 dólares e 50 centavos em 15 de dezembro, dois mil e vinte e três."

As tarefas comuns de normalização incluem:

Expandir abreviações ("Dr." torna-se "Doctor", "Inc." torna-se "Incorporated")
Converter números em palavras ("3" torna-se "três", "25,50" torna-se "vinte e cinco pontos cinco zero")
Lidar com datas e horários ("15/12/2023" torna-se "15 de dezembro, dois mil vinte e três")
Símbolos de processamento e caracteres especiais ("$" se torna "dólares", "@" se torna "at")
Resolução de homógrafos com base no contexto ("leitura" como tempo presente versus tempo passado)

A normalização de texto impede que o sistema tente pronunciar símbolos ou dígitos brutos, o que produziria uma saída não natural ou incompreensível.

Análise linguística: mapear texto para phonemes
A análise linguística quebra o texto normalizado em phonemes (as menores unidades de som) e determina como pronunciar cada palavra. O estágio de análise linguística:

Segmenta o texto em palavras e sílabas.
Pesquisa pronúncias de palavras em léxicos (dicionários de pronúncia).
Aplica regras G2P ou modelos neurais para lidar com palavras desconhecidas.
Marca limites sílabos e identifica sílabas estressadas.
Determina o contexto fonético para sons adjacentes.
Conversão de grafema para fonema
A conversão G2P (grapheme-to-phoneme) mapeia letras escritas (grafemes) para sons de pronúncia (phonemes). A ortografia em inglês não indica de forma confiável a pronúncia, portanto, os sistemas G2P usam regras e padrões aprendidos.

Por exemplo:

A palavra "embora" é convertida para /θoʊ/
A palavra "through" é convertida para "/θruː/"
A palavra "tosse" se pronuncia como /kɔːf/.
Cada palavra contém as letras "ough", mas a pronúncia difere drasticamente.

Os sistemas G2P modernos usam redes neurais treinadas em dicionários de pronúncia. Esses modelos aprendem padrões entre ortografia e som, manipulando palavras incomuns, nomes adequados e variações regionais mais normalmente do que sistemas baseados em regras.

Ao determinar phonemes, a análise linguística geralmente usa um modelo de transformador para ajudar a considerar o contexto. Por exemplo, a palavra "read" é pronunciada de forma diferente em "Eu leio livros" (presente do indicativo: /riːd/) versus "Eu li esse livro ontem" (pretérito perfeito: /rɛd/).

Geração de prosódia: determinar a pronúncia
Prosody refere-se aos padrões de ritmo, estresse e entonação que fazem a fala soar natural. A geração de prosódia determina como dizer palavras, não apenas quais sons produzir.

Elementos de prosódia
Prosody abrange várias características vocais:

Contornos de tom: padrões de tom crescentes ou decrescentes que sinalizam perguntas versus instruções
Duração: quanto tempo manter cada som, criando ênfase ou ritmo natural
Intensidade: variações de volume que realçam palavras importantes
Pausas: quebras entre frases ou sentenças que ajudam na compreensão
Padrões de estresse: quais sílabas recebem ênfase em palavras e frases
Prosody tem um efeito significativo sobre como o texto falado é interpretado. Por exemplo, considere como a seguinte frase muda de significado dependendo de qual sílaba ou palavra é enfatizada:

"Eu nunca disse que ele comeu o bolo."
"Eu nunca disse que ele comeu o bolo."
Eu nunca disse que ele comeu o bolo.
"Eu nunca disse que ele comeu o bolo."

# Predição de prosódia baseada em Transformer

Sistemas modernos de síntese de fala usam redes neurais transformadoras para prever prosódia. Os transformadores se destacam na compreensão do contexto em frases inteiras, não apenas em palavras adjacentes.

## O processo de geração de prosódia

Codificação de entrada: o transformador recebe a sequência de phoneme com recursos linguísticos (pontuação, parte da fala, estrutura de frases)
Análise contextual: mecanismos de autoatendimento identificam relações entre palavras (por exemplo, quais substantivos fazem referência a um pronome, em que os limites da frase caem)
Previsão de prosódia: o modelo gera valores previstos para tom, duração e energia em cada fonema
Fatores de estilo: o sistema considera o estilo de fala (neutro, expressivo, conversacional) e características do alto-falante
Os transformadores preveem prosódia aprendendo com milhares de horas de fala gravada emparelhada com transcrições. O modelo descobre padrões: as perguntas sobem em tom no final, vírgulas sinalizam breves pausas, palavras enfatizadas se alongam ligeiramente e palavras finais de frase geralmente caem em tom.

# Fatores que influenciam as escolhas prosódicas

Sintaxe: limites de cláusula indicam onde pausar
Semântica: Conceitos importantes recebem ênfase
Contexto do discurso: informações ou respostas contrastantes a perguntas podem trazer estresse extra
Identidade do locutor: cada voz tem intervalo de tom e taxa de fala características
Tom emocional: Excitação, preocupação ou neutralidade moldam padrões prosódicos
As previsões prosódicas criam uma especificação de destino: "Produza o fonema /æ/ a 180 Hz por 80 milissegundos com intensidade moderada e depois pausar por 200 milissegundos".


# Avaliação do módulo

1. Que atividade acontece durante a fase de pré-processamento do reconhecimento de fala?
   R: Os vetores de características são extraídos da onda sonora para modelagem.

  2. O que são phonemes?
     R: A menor unidade de som em fala

3. Por que é importante gerar prosódia na síntese de fala?
 R: A prosódia garante uma pronúncia natural e cadência de fala.


















































