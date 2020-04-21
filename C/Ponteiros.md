# Ponteiros

Definição mais simples :

> Ponteiros é uma variável que armazena o endereço de um local na memória.

Perceba que ponteiros são variáveis, então eles também estão em algum endereço da memória.

![](imagens/ponteiros.jpg)

Um ponteiro guarda o endereço de outra variável como mostra na figura acima.



# Uso

Para declarar um ponteiro basta usar a seguinte expressão :

```
<tipo do ponteiro> * <nome>;   
```

> O uso de espaços em branco ao redor do asterisco * é irrelevante.

O operador asterisco ( * ) informa ao compilador que a variável não guarda um valor, mas sim um endereço de memória.

É importante se atentar ao tipo do ponteiro, esse tipo precisa corresponder com o tipo da variável do endereço guardado. 

```
int * p --> Aponta para uma variável do tipo int
float * p --> Aponta para uma variável do tipo float
char * p --> Aponta para uma variável do tipo char
```

 A forma mais fácil de ler um ponteiro é da direita para esquerda :

> variável de nome p :
>
> int * **p**
>
> *p* é um ponteiro :
>
> int *** p**
>
> p é um ponteiro que aponta para um int ( inteiro ) :
>
> **int * p**

Cuidados importantes :

> Na linguagem C é possível declarar múltiplas variáveis de uma única vez :
>
> ```c
> #include <stdio.h>
> 
> int main() {
>  int a,b;
>  a = 4;
>  b = 6;
> 
> }
> ```
>
> O exemplo acima ilustra a declaração das variáveis do tipo int : a, b.
>
> Entretando, isso não é tão simples para ponteiros :
>
> ```c
> int *xPtr, x;
> ```
>
> Pode parecer uma declaração de múltiplos ponteiros, mas não é verdade , o que temos é :
>
> 1. *xPtr --> Ponteiro que aponta para um int
> 2. x --> variável do tipo int
>
> O que define se é uma variável ou um ponteiro é a presença do ( * ).
>
> A forma correta de declarar múltiplos ponteiros de uma única vez é :
>
> ```c
> int *aPtr, *bPtr;
> ```
>
>  Então, vamos fazer um exemplo mais interessante :
>
> ```c
> int *a, *b , c;
> ```
>
> Temos dois ponteiros : a, b ; uma variável do tipo int : c.