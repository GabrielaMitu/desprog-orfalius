Bucket Sort
======

Ideia Geral do Algoritmo
---------

Um algoritmo de classificação é usado para reorganizar uma determinada matriz ou elementos de lista de acordo com um operador de comparação nos elementos. O operador de comparação é usado para decidir a nova ordem do elemento na respectiva estrutura de dados.
Existem muitos algoritmos de classificação diferentes, com vários prós e contras. Nesse Handout iremos focar no algoritmo **Bucket Sort**.

Antes de pensar em como o algoritmo funciona, vamos começar com algo mais simples: 
porque será que o algoritmo se chama Bucket Sort? O que ele tem a ver com baldes?

![](bucket.jpg)

Baldes são recipientes, em que se pode botar tanto liquidos como sólidos então no 
caso do algoritmo vamos usar diversos baldes para botar o que formos organizar.

Vamos começar imaginando uma situação hipotética:

Um belo dia, você encontrou um jogo de Bingo e resolveu ordenar as bolas em ordem crescente para armazená-las de forma organizada. No jogo existem 75 bolas. Ordená-las diretamente levaria muito tempo, mas você percebeu que tinha 5 pequenos baldes à disposição.


![](bingo.png)



??? Checkpoint

De que maneira poderíamos utilizar esses baldes para tornar a ordenação mais rápida?

::: Gabarito
Poderíamos estabelecer cada balde como um intervalo numérico. Como existem 75 bolas e 5 baldes, cada balde teria ao final da ordenação 15 bolas se organizadas de forma equilibrada. No primeiro, colocaríamos as bolas de 1 a 15, no segundo, as bolas de 16 a 30 e assim por diante.

Desse modo, ao final teríamos apenas que organizar os baldes individualmente (cada balde sendo organizado por uma pessoa ao mesmo tempo). Concatenando as bolas dos baldes em ordem crescente teríamos então o resultado ordenado desejado.
:::

???


E essa é a ideia fundamental do Bucket Sort. 
Então ideal pra nossa entrada é que ela tenha:

* Intervalo conhecido;

* Distribuição uniforme;

O intervalo é importante porque ela é necessária na divisão de intervalos (os chamados “baldes” ou "buckets")

Essa distribuição uniforme é interessante porque ela ajuda com que os elementos estejam bem distribuídos entre os baldes, evitando que a organização de um balde seja muito mais trabalhosa que outro balde.

Funcionamento em detalhes
---------
O mais comum é o Bucket Sort ser implementado na forma de função, que recebe um array e um número de intervalos (n) que serão utilizados para a ordenação.

A implementação pode ser feita em quatro passos:
1. Criação dos n baldes a partir do conhecimento do intervalo (inicializados como listas vazias).
2. Inserção dos elementos em seus respectivos baldes - a posição em que o elemento do array será inserido é definida por `md index = n * array[i]`.
3. Ordenar cada balde separadamente usando o mesmo ou outros algoritmos.
4. Concatenar os conteúdos de todos os baldes em ordem crescente.

E pronto, conseguimos organizar nossos elementos! [Fácil não?](https://www.youtube.com/watch?v=WWaLxFIVX1s)

Vamos simular a seguir o passo a passo de uma ordenação de um array de 7 elementos, com o uso de 10 baldes.

Teoricamente poderiamos ordenar qualquer coisa como estes 7 elementos aqui:
::: 7 Elementos

![](7cats.jpg)

:::
Mas por simplicidade preferimos ordenar números:

;bucket


Como exatamente ocorre essa ordenação dentro de cada balde do passo 3? 
Podemos utilizar uma versão recursiva do Bucket Sort ou então algum outro algoritmo de ordenação.
Mas qual algoritmo seria o mais indicado se o objetivo fosse a máxima eficiência? Vamos consultar as  [tabelas de ordenação](https://ensino.hashi.pro.br/desprog/aula9/tabelas.html), para descobrir!


??? Checkpoint

Qual das tabelas deveríamos escolher para analisar qual algoritmo é o melhor em conjunto com o bucket sort em eficiência?

**Dica**: Pense na quantidade de elementos presentes em cada balde. Idealmente, ela é grande ou pequena?

::: Gabarito
Como queremos uma ordenação mais rápida possível dos elementos, vamos considerar a tabela da recomendação de tempo na prática. 

A Tabela de de Tempo na Prática de um algoritmo com “n” **pequeno**!

![](tabela.png)

Por exemplo, um “n” enorme, como 5 bilhões de elementos em um array, logicamente não é recomendado usar o bucket sort, em razão da quantidade de intervalos ("baldes") que seriam necessários criar, além de que até poderia ultrapassar o espaço de memória disponível.

:::
???

Certo, agora que já sabemos onde procurar, falta apenas escolher o algoritmo que será utilizado!


??? Checkpoint

Agora sim, qual algoritmo seria o mais indicado para ordenar os elementos **dentro** dos baldes? 


::: Gabarito
De acordo com a tabela, apesar de existirem poucas informações relacionadas a certos algoritmos devido ao fato de que algumas complexidades são próximas demais para estabelecer uma ordem consistente, podemos observar que o **Insertion Sort** é aquele que mais se destaca tanto quando o array está em ordem crescente ou sem ordem aparente.

:::
???

O que vimos até aqui?
---------

::: Resumão
1. O **Bucket Sort** coloca os elementos da lista de entrada em baldes e define o número de baldes dependendo do tamanho dele.
2. O ideal é que a distribuição dos elementos seja **uniforme** para não deixar alguns baldes sobrecarregados e outros vazios.
3. **Dentro** de cada balde é usado outro algoritmo de ordenação. Pela tabela concluimos que o melhor para isso é o **Insertion Sort**.
:::


Complexidade
---------
Com as informações anteriores, já é possível supor quais contextos representam o melhor e o pior caso dele.

Então não precisamos nem calcular a complexidade certo? Vou deixar a própria complexidade responder essa...

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

Vantagens e desvantagens
---------
Até agora nós vimos o que é e como funciona o **Bucket Sort**, então com base nisso já poderiamos observar quais vantagens e desvantagens esse algoritmo tem, e não há melhor maneira que vendo seu melhor e seu pior caso.


* **Melhor caso:** Depois que os elementos são distribuídos em baldes, cada um deles pode ser processado independentemente dos outros e de forma paralela. Como resultado, a classificação de intervalos funciona melhor e mais rápido quando os elementos do array dado são bem distribuídos em todos os baldes com cada um deles contendo um número igual de elementos.


* **Pior caso:** Se há uma má distribuição dos buckets, o algoritmo poderá acabar realizando uma enorme quantidade de trabalho extra, sem benefício ou benefício mínimo.

Posto isso, ainda está faltando um atributo bastante crucial na escolha de um algoritmo: a **velocidade**. Afinal, onde se encontra o Bucket Sort em relação à velocidade em comparação com outros algoritmos?

Esta é uma das características mais interessantes do Bucket Sort, pois ele é um algoritmo que não funciona totalmente sozinho!! Ele é responsável pela organização dos buckets, mas quem faz realmente a ordenação do array dentro de cada bucket é o **Insertion Sort**, como já vimos.

Além disso, o bucket sort tem outra vantagem de que a complexidade do intervalo pode ainda ser estável dependendo do algoritmo usado para classificar os elementos do intervalo. No caso, **como o Insertion Sort é estável, logo, o Bucket Sort também é estável**.

??? Checkpoint

Com o conhecimento adquirido até agora e para reforçar o aprendizado, liste 3 vantagens e 2 desvantagens do Bucket Sort

::: Gabarito
![](comparacao.png)

:::
???

Uso prático
---------

Uma outra vantagem do **Bucket Sort** é a possibilidade de usá-lo como um algoritmo de classificação externo. 

Então, como exemplo de aplicação, se for necessário classificar um array muito grande que não cabe na memória, será possível transmitir a lista pela memória RAM, distribuir os itens em baldes armazenados em arquivos externos e em seguida classificar cada arquivo na memória RAM independentemente.

![](ram.png)




??? Desafio

Escreva um pseudocódigo da implementação do Bucket Sort.



::: Gabarito
``` c
void bucketSort (int A[], int n) {
    Para i entre 0 e n-1:
        faça B[i] uma lista vazia
    Para i entre 0 e n-1:
        insira o elemento A[i] em B[n*A[i]]
    Para i entre 0 e n-1:
        ordene a lista B[i] com o INSERTION SORT
    Concatene todas as listas B em ordem crescente
}
```
:::
???

------------------------------------------------



