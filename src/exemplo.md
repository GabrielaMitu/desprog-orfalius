Bucket Sort
======

Ideia Geral do Algoritmo  
---------

Um algoritmo de ordenação é usado para reorganizar uma determinada matriz ou elementos de lista de acordo com um operador de comparação nos elementos. O operador de comparação é usado para decidir a nova ordem do elemento na respectiva estrutura de dados.
Existem muitos algoritmos de ordenação diferentes, com vários prós e contras. Nesse Handout iremos focar no algoritmo **Bucket Sort**.


Antes de pensar em como o algoritmo funciona, vamos começar com algo mais simples: 
porque será que o algoritmo se chama Bucket Sort? O que ele tem a ver com baldes?

![](bucket.jpg)

Baldes são recipientes, em que se pode botar tanto liquidos como sólidos então no 
caso do algoritmo vamos usar diversos baldes para botar o que formos organizar.


Uso prático
---------

Uma vantagem do **Bucket Sort** é a possibilidade de usá-lo como um algoritmo de **classificação externo**. 

Então, como exemplo de aplicação, se for necessário classificar um array muito grande que não cabe na memória, será possível transmitir a lista pela memória RAM, distribuir os itens em baldes armazenados em arquivos externos e em seguida classificar cada arquivo na memória RAM independentemente.

![](ram.png)


Agora, vamos imaginar uma situação hipotética:

Um belo dia, você e seus amigos encontraram um jogo de BINGO e resolveu ordenar as bolas em ordem crescente para armazená-las de forma organizada. No jogo existem 75 bolas. Ordená-las diretamente levaria muito tempo, mas você percebeu que tinha 5 pequenos baldes à disposição.


![](bingo.png)


Uma maneira que poderíamos utilizar esses baldes para tornar a ordenação mais rápida seria estabelecer cada balde como um intervalo numérico. Como existem 75 bolas e 5 baldes, cada balde teria ao final da ordenação 15 bolas. Desta forma, seguiríamos os seguintes passos: 


1. No primeiro, colocaríamos as bolas de 1 a 15, no segundo, as bolas de 16 a 30 e assim por diante.


2. Ao final teríamos apenas que organizar os baldes individualmente, ou seja, cada um organizaria um balde. 


3. Concatenando as bolas dos baldes em ordem crescente teríamos então o resultado ordenado desejado.


Essa é a ideia fundamental do Bucket Sort. A entrada a ser ordenada, um array, é dividida em intervalos (os chamados “baldes” ou “buckets”). Em seguida, esses buckets são ordenados separadamente e, após concatenados, resultam na saída, correspondente ao array de entrada agora ordenado.


Funcionamento em detalhes
---------

O mais comum é o Bucket Sort implementado na forma de função, que recebe um array e um número de intervalos (n) que serão utilizados para a ordenação.

Vamos agora entender o passo a passo de seu funcionamento

**Passo 1**


Já que o algoritmo funciona com base na ordenação de elementos por baldes, temos que criar esses baldes!

A quantidade de baldes será a mesma que o número intervalos (n) recebido como argumento da função. A maneira mais comum de criá-los é definir cada um deles como uma lista inicialmente vazia.


**Passo 2**

Bom, agora já temos os baldes criados. Falta inserir os elementos em seus respectivos baldes. A posição em que o elemento do array será inserido é definida por `md index = n * array[i]`.

Vamos entender isso melhor por meio de um exemplo!
??? Checkpoint

Simule o passo a passo da separação do array de 7 elementos mostrado abaixo, com o uso de 10 baldes. Você pode considerar o intervalo total dos números de 0 a 99 e que cada balde armazena 10 valores.

`int array[] = {13, 68, 35, 17, 92, 94, 61}`

::: Gabarito
;bucket

:::
???

Por simplicidade preferimos ordenar números no exercício anterior, mas na realidade, poderiamos ordenar qualquer coisa com o Bucket Sort. Como estes 7 elementos aqui:
::: 7 Elementos

![](7cats.jpg)

:::

**Passo 3**

Agora temos nossos elementos divididos em seus respectivos intervalos. Porém ainda temos um problema! [Os elementos dentro dos baldes estão fora de ordem!](https://i.kym-cdn.com/entries/icons/original/000/027/475/Screen_Shot_2018-10-25_at_11.02.15_AM.png)

Vamos ordená-los então! Mas como exatamente isso ocorre? 
Podemos utilizar uma versão recursiva do Bucket Sort ou algum outro algoritmo de ordenação.
Mas qual algoritmo seria o mais indicado se o objetivo fosse a máxima eficiência? Vamos consultar as  [tabelas de ordenação](https://ensino.hashi.pro.br/desprog/aula9/tabelas.html), para descobrir!


??? Checkpoint

Qual das tabelas deveríamos escolher para analisar qual algoritmo é o melhor em conjunto com o bucket sort em termos de eficiência?

**Dica**: No contexto deste handout, estamos considerando situações em que o número de elementos em cada balde é pequeno.

::: Gabarito
Como queremos a ordenação mais rápida possível dos elementos, vamos considerar a tabela da recomendação de tempo na prática. 

A Tabela de de Tempo na Prática de um algoritmo com “n” **pequeno**!

![](tabela.png)

Por exemplo, um “n” enorme, como 5 bilhões de elementos em um array, logicamente não é recomendado usar o bucket sort, em razão da quantidade de intervalos ("baldes") que seriam necessários criar, além de que até poderia ultrapassar o espaço de memória disponível.

:::
???

Certo, agora que já sabemos onde procurar, falta apenas escolher o algoritmo que será utilizado!


??? Checkpoint

Agora sim, qual algoritmo seria o mais indicado para ordenar os elementos **dentro** dos baldes dado que há uma quantidade de elementos n pequena em cada balde? 


::: Gabarito
De acordo com a tabela, apesar de existirem poucas informações relacionadas a certos algoritmos devido ao fato de que algumas complexidades são próximas demais para estabelecer uma ordem consistente, podemos observar que o **Insertion Sort** é aquele que mais se destaca tanto quando o array está em ordem crescente ou sem ordem aparente.

:::
???

**Passo 4**

Estamos quase no final da implementação, mas ainda falta um passo muito importante!
Até agora temos os elementos inseridos em baldes, ordenados de forma crescente. Dentro de cada balde, os elementos também já estão na ordem correta.


??? Checkpoint
Considerando que o objetivo do Bucket Sort é obter um vetor de saída ordenado, você consegue imaginar qual seria o passo final para sua implementação?

(A resposta é tão simples quanto parece)

::: Gabarito
Temos que juntar tudo!
Ou, em outras palavras, se concatenarmos os conteúdos de cada balde, teremos um vetor de saída ordenado, como desejado.
:::
???

E pronto, conseguimos organizar nossos elementos! [Fácil não?](https://www.youtube.com/watch?v=WWaLxFIVX1s)



??? Checkpoint
Agora que você entendeu muito bem como o Bucket Sort funciona, tente pensar nos 4 passos responsáveis pela implementação do Bucket Sort e seus devidos pseudocódigos, considerando que temos apenas o array a ser ordenado e o número n de elementos:


Quais seriam então os 4 passos e seus devidos pseudocódigos? 

**Dica**: Reveja o passo a passo do bingo.

::: Primeiro passo

1. **Criação** dos n baldes a partir do conhecimento do intervalo (inicializados como listas vazias). Pseudocódigo:

``` python
    Para i entre 0 e n-1:
        faça B[i] uma lista vazia
```
:::

::: Segundo passo

2. **Inserção** dos elementos em seus respectivos baldes - a posição em que o elemento do array será inserido é definida por `md index = n * array[i]`. Psedocódigo:

``` c
    Para i entre 0 e n-1:
        faça B[i] uma lista vazia
    Para i entre 0 e n-1:
        insira o elemento A[i] em B[n*A[i]]
```

:::

::: Terceiro passo

3. **Ordenar** cada balde separadamente usando o mesmo ou outros algoritmos. Psedocódigo:

``` c
    Para i entre 0 e n-1:
        faça B[i] uma lista vazia
    Para i entre 0 e n-1:
        insira o elemento A[i] em B[n*A[i]]
    Para i entre 0 e n-1:
        ordene a lista B[i] com o INSERTION SORT
```

:::

::: Quarto passo

4. **Concatenar** os conteúdos de todos os baldes em ordem crescente. Psedocódigo:

``` c
    Para i entre 0 e n-1:
        faça B[i] uma lista vazia
    Para i entre 0 e n-1:
        insira o elemento A[i] em B[n*A[i]]
    Para i entre 0 e n-1:
        ordene a lista B[i] com o INSERTION SORT
    Concatene todas as listas B em ordem crescente

```
:::
???




Complexidade
---------
Com as informações anteriores, já é possível supor quais contextos representam o melhor e o pior caso do Bucket Sort.

Então para fazer essas suposições não precisamos nem calcular a complexidade, certo? Vou deixar a própria complexidade responder essa...

::: Resposta

![](no.png)

:::


??? Checkpoint

Tente pensar em um contexto que representa o **pior caso** de complexidade e um que represente o **melhor caso** de complexidade do bucket sort, ou seja, aquele que tornaria o algoritmo mais eficiente.


::: Gabarito
* **Melhor caso**: Os elementos estão distribuídos bem uniformemente em cada um dos baldes.


* **Pior caso**: Muitos elementos acumulados em um ou poucos baldes e presença de muitos baldes vazios.

:::
???

**{green}(Melhor Caso)**

Vamos entender melhor esses casos de complexidade. Começando pelo melhor caso.
Para isso, vamos analisar passo a passo o pseudocódigo do algoritmo.


??? Checkpoint
Você consegue estimar a complexidade apenas do trecho de código referente ao passo 1?

::: Gabarito
Como temos que percorrer o loop n vezes, a complexidade desse trecho será O(n)!
:::
??? 

No próximo loop, podemos seguir a mesma lógica para inserir os elementos em cada balde.

A parte mais interessante é ordenar os elementos com o **Insertion Sort**. 

??? Checkpoint
Vamos relembrar um pouco deste algoritmo. Você se lembra quais eram as complexidades de cada caso do Insertion Sort?

::: Gabarito
![](insertion_complexidade.jpg)
:::
???

Mas você deve estar se perguntando... qual seria a vantagem da utilização do Bucket Sort se o algoritmo efetivamente usado para a ordenação tem complexidade quadrática no caso médio e no pior caso?

A vantagem está justamente em seu melhor caso, que é O(n)!

Vamos entender melhor porque isso acontece.

Cada balde possui n/k elementos. Considerando a complexidade do Insertion Sort, podemos concluir que cada balde terá uma complexidade quadrática em n/k. No melhor caso, o k será proporcional a n, de forma que a complexidade desta etapa seja linear.


Portanto, no melhor caso, a complexidade total do Bucket Sort será linear!

**{red}(Pior Caso)**

E por fim há também o **pior caso**. Quando os elementos são muito próximos, de forma a serem colocados em poucos baldes, a complexidade acaba dependendo diretamente do algoritmo usado para a ordenação dentro dos baldes: o **Insertion Sort**.

Em razão da receita obtida da [Aula 6](https://ensino.hashi.pro.br/desprog/aula6/index.html) e da implementação do Insertion Sort da [Aula 7](https://ensino.hashi.pro.br/desprog/aula7/index.html), a complexidade do código é $O(n^2)$ 

??? Checkpoint
Com essas informações, consegue deduzir qual seria a complexidade de pior caso do Bucket Sort?

::: Gabarito
Como foi dito, a complexidade do Bucket Sort acaba dependendo diretamente do Insertion Sort, é só lembrar da situação em que todos os elementos estão concentrados em poucos ou apenas um bucket. Desta forma, consequentemente, a complexidade do pior caso do **Bucket Sort** é $O(n^2)$ também.
:::
???


Temos ainda o caso de complexidade de **caso médio**, o qual ocorre quando os elementos são distribuídos aleatóriamente no array de entrada. Mesmo que os elementos não sejam distribuídos de maneira uniforme, a classificação do intervalo é executada em tempo **linear** assim como no **melhor caso**.


Desta maneira, os casos de complexidade podem ser resumidos de acordo com a seguinte tabela:
 
| Caso     | Complexidade |
|--------------|----------|
| Melhor       |  O(n+k)  |
| Médio        | O(n+k)   |
| Pior         | O(n^2)   |

Vantagens e desvantagens
---------
Até agora nós vimos o que é e como funciona o **Bucket Sort**, então com base nisso já poderiamos observar quais vantagens e desvantagens esse algoritmo tem, e não há melhor maneira que vendo seu melhor e seu pior caso.


* **Melhor caso:** Depois que os elementos são distribuídos em baldes, cada um deles pode ser processado independentemente dos outros e de forma paralela. Como resultado, a classificação de intervalos funciona melhor e mais rápido quando os elementos do array dado são bem distribuídos em todos os baldes com cada um deles contendo um número igual de elementos.


* **Pior caso:** Se há uma má distribuição dos buckets, o algoritmo poderá acabar realizando uma enorme quantidade de trabalho extra, sem benefício ou benefício mínimo.

Posto isso, ainda está faltando um atributo bastante crucial na escolha de um algoritmo: a **velocidade**. Afinal, onde se encontra o Bucket Sort em relação à velocidade em comparação com outros algoritmos?

Esta é uma das características mais interessantes do Bucket Sort, pois ele é um algoritmo que não funciona totalmente sozinho como já mencionamos. Ele é responsável pela organização dos buckets, mas quem faz realmente a ordenação do array dentro de cada bucket é o **Insertion Sort**.

Além disso, o bucket sort tem outra vantagem de que a complexidade do intervalo pode ainda ser estável dependendo do algoritmo usado para classificar os elementos do intervalo. No caso, **como o Insertion Sort é estável, logo, o Bucket Sort também é estável**.

??? Checkpoint

Com o conhecimento adquirido até agora e para reforçar o aprendizado, liste **3 vantagens** e **2 desvantagens** do Bucket Sort

::: Gabarito
![](comparacao.png)

:::
???

