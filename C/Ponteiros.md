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

# Inicialização E Atribuição

Se um ponteiro não for inicializado ( não conter nenhum endereço), ele aponta para um lugar indefinido, isso ocorre quando um ponteiro é apenas declarado:

![](imagens/7.png)

> Um ponteiro pode apontar para "lugar nenhum" , também conhecido pelo valor NULL.
>
> Para isso há duas formas de se fazer.
>
> A primeira forma é atribuir o valor constante NULL para um ponteiro :
>
> ```C
> int *p = NULL;
> ```
>
> A segunda forma é atribuir o valor inteiro 0 para o ponteiro :
>
> ```c
> int *p = 0;
> ```
>
> ![](imagens/8.png)
>
> O seguinte código ilustra uma forma de observar ao executar um programa :
>
> ```c
>   #include <stdio.h>
> 
> int main(void) {
>   int *a,*b; // Declaramos dois ponteiros a e b
>   a = NULL; // Apontamos o ponteiro a para lugar nenhum
>   b = 0; // Apontamos o ponteiro b para lugar nenhum
>   
>   printf("O ponteiro a ponta para %p \n",a);// %p exibe valores hexadecimal
>   printf("O ponteiro b aponta para %p \n",b); 
> }
> ```
>
> O resultado deve ser algo parecido com o seguinte :
>
> ![](imagens/9.png)

## Operador de endereçamento ( & )

O operador & retorna o endereço de alguma variável.

>  Um teste rápido para ver o operador em prática :
>
> ```c
> #include <stdio.h>
> 
> int main(){
> 	int n = 4;
> 	printf("O local da variavel n : %p \n",&n);
> }
> ```
>
> O esperado ao executar é receber o endereço onde a variável n se encontra :
>
> ![](imagens/10.png)

O processo de atribuir valores para um ponteiro é relativamente simples :

```
<tipo> * <nome-do-ponteiro> ;
<nome-do-ponteiro> = &<variavel>
```

Exemplo :

```c
int b = 4;
int *bPonteiro;
bPonteiro = &b;
```

Assim temos que o ponteiro declarado bPonteiro recebe o endereço da variável *b* na linha 3.

O processo pode ser direto, o exemplo acima é equivalente a :

```c
int b = 4;
int *bPonteiro = &b;
```

> Vamos mostrar que um ponteiro realmente carrega o endereço de outra variável com o seguinte código:
>
> ```c
> #include <stdio.h>
> 
> int main(){
> 	int b = 10; // conteudo de b : 10
> 	int *bPonteiro = &b; // O conteudo do ponteiro : endereco da variabel b
> 	printf("O endereço da variabel b : %p \n",&b); 
> 	printf("O endereço carregado pelo pointeiro *bPonteiro : %p \n",bPonteiro);
>     printf("O endereco do ponteiro *bPonteiro : %p \n",&bPonteiro); 
> }
> ```
>
> O endereço da memória pode variar de execução para execução , o importante é notar que ambos os endereços são iguais :
>
> ![](imagens/11.png)
>
> Ponto interessante de sempre lembrar é o de que o ponteiro carrega um endereço de outra variável, entretanto, o próprio ponteiro está localizado em outra região da memória, uma região própria.



## Operador de acesso ( * )

O operador ( * ) acessa o conteúdo de algum endereço.

 