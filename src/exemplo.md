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


??? Checkpoint
Você consegue imaginar qual seria o primeiro passo para a implementação do Bucket Sort? 

A dica está no próprio nome do algoritmo.

::: Gabarito
Já que o algoritmo funciona com base na ordenação de elementos por baldes, temos que criar esses baldes!

A quantidade de baldes será a mesma que o número intervalos (n) recebido como argumento da função. A maneira mais comum de criá-los é definir cada um deles como uma lista inicialmente vazia.

:::
???

Bom, agora já temos os baldes criados. Falta inserir os elementos em seus respectivos baldes. A posição em que o elemento do array será inserido é definida por `md index = n * array[i]`.

Vamos entender isso melhor por meio de um exemplo!
??? Checkpoint

Simule o passo a passo da separação do array de 7 elementos mostrado abaixo, com o uso de 10 baldes. 

`int array[] = {13, 68, 35, 17, 92, 94, 61}`

::: Gabarito
;bucket

:::
???

Por simplicidade preferimos ordenar números no exercício anterior, mas na realidade, poderiamos ordenar qualquer coisa com o Bucket Sort. Como estes 7 elementos aqui:
::: 7 Elementos

![](7cats.jpg)

:::


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



::: Recapitulando
O funcionamento do Bucket Sort pode ser resumido em quatro passos:

1. **Criação** dos n baldes a partir do conhecimento do intervalo (inicializados como listas vazias).
2. **Inserção** dos elementos em seus respectivos baldes - na posição `md index = n * array[i]`.
3. **Ordenar** cada balde separadamente usando o mesmo ou outros algoritmos.
4. **Concatenar** os conteúdos de todos os baldes em ordem crescente.
:::


??? Checkpoint
Agora que você entendeu muito bem como o Bucket Sort funciona, tente implementar um pseudocódigo deste algoritmo.


::: Gabarito
``` c
void bucketSort (int Array[], int numero_baldes) {
    Para i entre 0 e n-1:
        faça Balde[i] uma lista vazia
    Para i entre 0 e n-1:
        insira o elemento Array[i] em Balde[numero_baldes * Array[i]]
    Para i entre 0 e n-1:
        ordene a lista Balde[i] com o INSERTION SORT
    Concatene todas as listas Balde em ordem crescente
}
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

Na situação do **melhor caso**, quando os elementos são uniformemente distribuídos entre os baldes, consideraremos duas complexidades: a complexidade para fazer os baldes, sendo $n$ a quantidade de elementos do array e $k$ o número de baldes.


??? Checkpoint
Para facilitar o processo de aquisição da complexidade vamos tentar criar um pseudocódigo do passo 4 sobre o funcionamento do bucket sort, ou seja, aquela que pega os elementos de cada balde e coloca em um array.

::: Gabarito
``` c
For each bucket b:
    For each element x in b:
        Append x to the array.
```
:::
???

Qual é a complexidade afinal? Bom, agora que temos o pseudocódigo, podemos quebrar um pouco mais a cabeça para pensar qual seria então a complexidade.

??? Checkpoint
A partir dessa análise, qual é o tempo de execução total?

::: Gabarito
Bem, existem $k$ intervalos diferentes, então o loop mais externo deve levar pelo menos $O(k)$ tempo, porque temos que olhar em cada intervalo. Já o loop interno será executado um total de $O(n)$ vezes, porque há um total de $n$ elementos distribuídos pelos baldes. Logo a complexidade do melhor caso é $O(n + k)$.
:::
???

E por fim há também o **pior caso**, quando os elementos são muito próximos, de forma a serem colocados em poucos baldes, a complexidade acaba dependendo diretamente do algoritmo usado para a ordenação dentro dos baldes: o **Insertion Sort**.
Então, dado que o código em C de Insertion Sort é:

``` c
void insertion_sort(int v[], int n) {
    for (int i = 1; i < n; i++) {   // n é o tamanho da array
        int temp = v[i];            // para todo i de 1 a n-1
        
        int j;

        /* Desloca todos os elementos entre j e i-1
        para a direita, sobrescrevendo v[j] */

        for (j = i; j > 0; j--) {
            if (v[j - 1] <= temp) {
                break;
            }
            v[j] = v[j - 1];
        }

        v[j] = temp;
    }
}
```

??? Checkpoint
Como é possível estimar a complexidade do **Insertion Sort** a partir da receita da [Aula 6](https://ensino.hashi.pro.br/desprog/aula6/index.html)

::: Gabarito
Vamos chamar de $x$ a quantidade de iterações do loop externo e vamos chamar de $y$ a quantidade de iterações de uma execução do loop interno em função de $i$.

Como $i = 1 + 1*k$ e sabemos que  $i < n$ depois de $x - 1$ iterações, temos: 
$$ x < n $$

Como $j = i - 1*k$ e sabemos que $j > 0$ depois de $y - 1$ iterações, temos:
$$y < i+1$$

Os valores de $i$ ao longo do loop externo são:
$$i = 1,2,3,....,x$$

ou seja, o total de iterações de todas as execuções do loop interno é menor que 
$$(1+1)+(2+1)+(3+1)+...+(x+1)$$
$$= 2+3+4+...+(x+1)$$

Isso é uma soma de PA com

* primeiro elemento $2$;
* último elemento $x+1$;
* quantidade de elementos $x$,

ou seja, 

$$(2+x+1)*\frac{x}{2}$$
$$(x+3)*\frac{x}{2}$$
$$<(n+3)*\frac{n}{2}$$
$$=\frac{n^2 + 3n}{2}$$

Portanto, pelas regras de simplificação, a complexidade do código é $O(n^2)$ e, consequentemente, a complexidade do pior caso do **Bucket Sort** é $O(n^2)$ também.

**Obs.:** Esse cálculo foi retirado da [Aula 7](https://ensino.hashi.pro.br/desprog/aula7/index.html), mas para reforçar o aprendizado colocamos ele aqui novamente.

:::
???

Temos ainda o caso de complexidade de **caso médio**, o qual ocorre quando os elementos são distribuídos aleatóriamente no array de entrada. Mesmo que os elementos não sejam distribuídos de maneira uniforme, a classificação do intervalo é executada em tempo **linear** assim como no **melhor caso**.

<!-- No **melhor caso**, quando os elementos são uniformemente distribuídos entre os baldes, a complexidade geral será **linear**. Nesta situação, a complexidade para fazer os baldes é **O(n)** e aquela para classificar os elementos de cada balde é **O(k)**.

Já a complexidade de **caso médio** ocorre quando os elementos são distribuídos aleatóriamente no array de entrada. Mesmo que os elementos não sejam distribuídos de maneira uniforme, a classificação do intervalo é executada também em tempo **linear**.

E por fim há também o **pior caso**, quando os elementos são muito próximos, de forma a serem colocados em poucos baldes, a complexidade acaba dependendo diretamente do algoritmo usado para a ordenação dentro dos baldes: o **Insertion Sort**. -->


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

