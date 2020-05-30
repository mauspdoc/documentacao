# Array Dinâmico

## Usando malloc para alocar espaço para um array

O malloc permite alocar o espaço desejado e retorna o endereço desse espaço alocado.

```c
malloc(sizeof(int) * 5);
```

O código acima, por exemplo, aloca espaço suficiente para 5 int.

> Nesses casos a melhor forma de saber o quanto de espaço alocar para um tipo é usando o siseof(tipo).

Então, usando isso podemos criar um array :

```c
int n = 5;
int *pArray = malloc(sizeof(int) * n);
```

O pArray nada mais é do que um ponteiro que aponta para o tipo int, ele recebe o endereço retornado por malloc ao alocar espaço para n inteiros (nesse caso temos n sendo igual a 5). Com o pArray podemos usa-lo da mesma forma como um Array.

```c
#include <stdio.h>
#include <stdlib.h>

int main(){
    int n = 10;
    int *pArray = malloc(sizeof(int) * n);
    // Atribuindo valores para cada item desse 'array'
    for (size_t i = 0; i < n; i++)
    {
       pArray[i] = i+2;
    }
    // Exibindo cada item do array
    for (size_t i = 0; i < n; i++)
    {
        printf("index %i - %i \n",i,pArray[i]);
    }
}
```

Ao executar, o esperado é :

```
index 0 - 2 
index 1 - 3 
index 2 - 4 
index 3 - 5 
index 4 - 6 
index 5 - 7 
index 6 - 8 
index 7 - 9 
index 8 - 10 
index 9 - 11
```

 ## Usando Realloc

Podemos usar a função realloc em elementos criados usando malloc,calloc ou realloc.

Com o realloc vamos aumentar nosso array para aguentar mais um item : 

```c
#include <stdio.h>
#include <stdlib.h>

int main(){
    int n = 10;
    int *pArray = malloc(sizeof(int) * n);
    for (size_t i = 0; i < n; i++)
    {
       pArray[i] = i+2;
    }
	// A partir de agora vamos tentar realocar espaco
    // Agora queremos 11 elementos no array
    n = 11;
    // realloc precisa saber qual estrutura sera afetada e em quanto precisa alterar 
    pArray = realloc(pArray,sizeof(int)*(n)); 
    // Assim podemos alterar o nosso elemento 11, pois temos espaco para isso
    pArray[10] = 2020;
    
    for (size_t i = 0; i < n; i++)
    {
        printf("index %i - %i \n",i,pArray[i]);
    }   
}
```

Resultado esperado :

```
index 0 - 2 
index 1 - 3 
index 2 - 4 
index 3 - 5 
index 4 - 6 
index 5 - 7 
index 6 - 8 
index 7 - 9 
index 8 - 10 
index 9 - 11 
index 10 - 2020
```

