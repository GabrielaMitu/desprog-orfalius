Bucket Sort
======

Introdução
---------

Antes de pensar em como o algoritmo funciona, vamos começar com algo mais simples: 
porque será que o algoritmo se chama Bucket Sort? O que ele tem a ver com baldes?

![](bucket.png)

Baldes são recipientes, em que se pode botar tanto liquidos como sólidos então no 
caso do algoritmo vamos usar diversos baldes para botar o que formos organizar.

Podemos ordenar tanto números como palavras letras e etc. 

A nossa lista de entrada precisa obrigatoriamente ter:

* Intervalo conhecido;

* ter sido feita com distribuição uniforme

Ou seja se a entrada for bastante crescente ou descrescente o algoritmo não vai 
funcionar tão bem.



Você também pode criar

1. listas;

2. ordenadas,



e imagens. Lembre que todas as imagens devem estar em uma subpasta *img*.

![](logo.png)

Para tabelas, usa-se a [notação do
MultiMarkdown](https://fletcher.github.io/MultiMarkdown-6/syntax/tables.html),
que é muito flexível. Vale a pena abrir esse link para saber todas as
possibilidades.

| coluna a | coluna b |
|----------|----------|
| 1        | 2        |

Ao longo de um texto, você pode usar *itálico*, **negrito**, {red}(vermelho) e
[[tecla]]. Também pode usar uma equação LaTeX: $f(n) \leq g(n)$. Se for muito
grande, você pode isolá-la em um parágrafo.

$$\lim_{n \rightarrow \infty} \frac{f(n)}{g(n)} \leq 1$$

Para inserir uma animação, use `md ;` seguido do nome de uma pasta onde as
imagens estão. Essa pasta também deve estar em *img*.

;bucket

Você também pode inserir código, inclusive especificando a linguagem.

``` py
def f():
    print('hello world')
```

``` c
void f() {
    printf("hello world\n");
}
```

Se não especificar nenhuma, o código fica com colorização de terminal.

```
hello world
```


!!! Aviso
Este é um exemplo de aviso, entre `md !!!`.
!!!


??? Exercício

Este é um exemplo de exercício, entre `md ???`.

::: Gabarito
Este é um exemplo de gabarito, entre `md :::`.
:::

???
