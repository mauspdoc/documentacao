# Boolean na linguagem C

Por muito tempo não havia nenhuma implementação que desse suporte aos valores booleanos( valores como verdadeiro e falso). Vou começar mostrando como seria possível usar esses valores sem nenhuma biblioteca do C e depois a aplicação da  biblioteca <stdbool.h>

# Criando valores booleanos

Podemos associar os valores verdade(true) e falso(false) como números da seguinte forma:

> 0  = false
>
> 1 = true

Para isso devemos informar ao compilador que deve tratar falso como 0 e true como 1 quando usarmos esses novos valores.

Fazer isso exige usar #define, o uso dele permite criar "links" ou associações.

```c
#define FALSE 0
#define TRUE 1
```

Agora sempre que usarmos FALSE ou TRUE, o compilador irá substituir isso por 0 ou 1.

```c
int primeiro_valor = TRUE;
int segundo_valor = FALSE;
```

 Nesse caso, primeiro_valor recebe TRUE, mas no fim das contas o valor real é 1. Entretanto,isso é útil para muitos programas.

> Note que usamos o tipo int, pois se trata de valores números inteiros.

Agora vamos suprimir o uso do tipo int para tornar mais óbvio do que se trata a variável. Para isso vamos usar #define novamente.

```c
#define FALSE 0
#define TRUE 1
#define BOOL int // Adicionado
```

Depois disso, agora podemos usar o tipo BOOL , mas no final de tudo será tratado como int.

Agora o nosso código fica :

```c
BOOL primeiro_valor = TRUE;
BOOL segundo_valor = FALSE;
```

Pronto, isso é uma boa implementação extra-oficial.

Caso quiser, podemos usar o seguinte código para exibir se é verdadeiro ou falso :

```c
#include <stdio.h>

#define FALSE 0
#define TRUE 1
#define BOOL int
int main(){
    BOOL primeiro_valor = TRUE;
    BOOL segundo_valor = FALSE;

    if(primeiro_valor == TRUE ){
        printf("primeiro_valor é verdadeiro \n");
    }
    
    if(segundo_valor == FALSE ){
        printf("segundo_valor é falso \n");
    }
}
```

## Biblioteca stdbool.h

Vamos agora usar a biblioteca stdbool.h para realizar as mesmas operações da seção anterior, para isso devemos inclui-la  em nosso código :

```c
#include <stdbool.h>
```

 O tipo booleano definida por ela é :

```c
_Bool <nome-da-variavel> = valor
```

Esse valor pode ser verdadeiro (true) ou falso (false) :

```c
_Bool n1 = false;
_Bool n2 = true;
```

Então o último código da seção passada fica da seguinte forma agora :

```c
#include <stdio.h>
#include <stdbool.h>

int main(){
    _Bool primeiro_valor = true;
    _Bool segundo_valor = false;

    if(primeiro_valor == true ){
        printf("primeiro_valor é verdadeiro \n");
    }
    
    if(segundo_valor == false ){
        printf("segundo_valor é falso \n");
    }
}
```

> Um projeto legal para testar essa biblioteca , um pequeno chat entre você e você mesmo representando o PC :
>
> ```c
> #include <stdio.h>
> #include <stdbool.h>
> 
> #define TAMANHO 40 // Define o tamanho maximo das mensagens
> 
> // Prototipos 
> void praCadaItem(char [],char [] , int ); // Podemos omitir os nomes
> 
> int main(){
>     _Bool loop = true; // Permite o programa rodar sem parar enquanto for true
>     _Bool vez_do_pc = false; // Indica o momento do PC conversar no chat
>     
>     while(loop == true){
>         
>         // Definindo o usuario atual
>         char usuario[TAMANHO];
>       	// Mensagem a ser exibida 
>         char msg[TAMANHO];
>         if(vez_do_pc == true){
>             char pc[] = "PC";
>            	// A funcao sobrescreve os valores de usuario[] para inserir "PC" 
>             praCadaItem(usuario,pc,3);
>             // Trocando o valor para alternar de usuario na proxima
>             vez_do_pc = false;
>         }
>         else{
>             char voce[] = "você";
>             // A funcao sobrescreve os valores de usuario[] para inserir "você"
>             praCadaItem(usuario,voce,5);
>             // Isso indica ao programa que agora é a vez do PC no chat
>             vez_do_pc = true;
>         }
> 		
>         printf("%s: ",usuario);
>         
>         scanf("%99[^\n]%*c",msg);
> 
>     }
> }
> 
> void praCadaItem(char array[],char mensagem[] , int tamanho_da_mensagem)
> {
>     for(size_t i = 0; i < tamanho_da_mensagem ; i++){
>         array[i] = mensagem[i];
>     }
> }
> ```
>
> 