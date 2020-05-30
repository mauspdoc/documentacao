# Array

É um tipo de estrutura de dados que permite relacionar diversas variáveis do mesmo tipo. Isso ocorre devido a uma locação contínua na memória.

Para criar um array :

```c
tipo_dos_itens nome_do_array[tamanho];
```

Exemplo :

```c
int n[5] // um array com 5 itens do tipo int
```

Note que todos os itens precisam ser do mesmo tipo.  A posição dos itens em um array começa do zero.

Para acessar o item de um array :

```c
nome_do_array[posição do item]
```

# Populando um array com itens 

Para criar um array e popular com itens, defina o array e coloque os itens do array entre chaves { } separando cada item por vírgula.

Exemplo :

```c
int n[5] = {32, 27, 64, 18, 95};
```

Acessando os itens do array :

```
n[0] --> 32
n[1] --> 27
n[2] --> 64
n[3] --> 18
n[4] --> 95
```

Podemos também definir um array :

```c
int n[5];
```

E em seguida acessar cada posição do array e definir o valor para aquela posição :

```c
n[0] = 32;
n[1] = 27;
n[2] = 64;
n[3] = 18;
n[4] = 95;
```

> size_t é um tipo de dado especial muito usado para tamanhos ou valores que não podem ser negativos.
>
> O tipo de size_t depende da plataforma, pode ser long unsigned int , unsigned int , unsigned long long. O tipo de size_t depende da plataforma.

Para visualizar isso em um código completo :

```c
#include <stdio.h>
int main(){
	int n[5];
	n[0] = 32;
	n[1] = 27;
	n[2] = 64;
	n[3] = 18;
	n[4] = 95;
	for(size_t i = 0; i < 5 ; i++){
		printf("A posicao %lu do array possui o valor %i \n",i,n[i]);
		}
	return 0;
	}
```

> o size_t foi usado para ser o tipo de "i" no loop for, pois não carrega valores negativos e aguenta um maior intervalo de números nesse caso. 

O resultado deve ser algo parecido com :

<img src="../../../../Projetos/C/Array/imagens/1.png" style="zoom:67%;" />

## Array com tamanho omitido

Um array pode ser criado sem especificar seu tamanho , veja o exemplo a seguir :

```c
int n[] = {1,2,3};
```

Ao compilar, o tamanho do array será conforme a quantidade de itens dentro das chaves { }.

Logo, o array do exemplo acima possui o tamanho 3.

## Usando define para definir tamanho dos arrays

Às vezes é interessante tornar o código mais simples possível,  um código simples de manter e modificar. Isso pode ser aplicado para arrays, podemos usar o *define*, uma forma de definir constantes para o programa, para atingir esse objetivo :

```c
#include <stdio.h>
#define TAMANHO 5 // Tamanho maximo do array
int main(){
    int s[TAMANHO]; // Define o array
    
    for(size_t k = 0; k < TAMANHO; k++){
        s[k] = k * k; // Introduz valores ao array
    }
    printf("%s %13s \n","Elemento", "Valor");
    for(size_t j = 0; j < TAMANHO; j++ ){
        printf("%7lu %13d \n",j,s[j]); // Exibe cada item do array 
    }
}
```

> A seguinte parte do código merece ser relembrada :
>
> ```c
> printf("%s %13s \n","Elemento", "Valor");
> ```
>
> no segundo %s temos o seguinte :
>
> ```
> %13s
> ```
>
> Isso é uma forma de mandar o programa se afastar 13 espaços até exibir a mensagem.

Resultado disso :

<img src="../../../../Projetos/C/Array/imagens/2.png" style="zoom:67%;" />

Definir o tamanho do array como uma constante facilita bastante qualquer modificação do programa, pois só é preciso mudar um valor para manter o programa em funcionamento.

## Arrays especiais

Caso a quantidade de itens do array seja menor do que o tamanho do array, as posições não completadas do array serão preechidas com zeros :

```c
int a[10] = {1, 2, 3, 4, 5, 6};
/* Seus valores são {1, 2, 3, 4, 5, 6, 0, 0, 0, 0}*/
```

> O único problema é a quantidade de itens do array ser maior que o tamanho especificado para o array.

# Array Multi-dimensional

Um item de um array pode ser inclusive outro array. Para isso precisamos seguir a seguinte expressão :

```c
tipo A1[itens do A1][ tamanho dos arrays itens];
```

Exemplo :

```c
int b[2][3]; // Array com 2 arrays, sendo que cada array tem tamanho 3.
```

Atribuindo valores :

```c
int b[2][3] = {{2,4,6},{1,3,5}};
```

Podemos pensar nisso como uma matriz :

```
		c1  c2 c3
linha 1	{2, 4, 6}
linha 2	{1, 3, 5}
```

Ou seja :

```
		coluna 1 | coluna 2 | coluna 3 
linha 1     2		  4			 6
linha 2		1		  3  		 5
```

Para acessar os valores de um array :

```
array[linha][coluna]
```

Voltando ao seguinte exemplo :

``` c
int b[2][3] = {{2,4,6},{1,3,5}};
```

```
b[0][0] --> 2
b[0][1] --> 4
b[0][2] --> 6
b[1][0] --> 1
b[1][1] --> 3
b[1][2] --> 5
```

> Podemos criar um array multi-dimensional omitindo o valor do primeiro colchete [ ]:
>
> ```c
> int b[][3] = {{2,4,6}, {1,3,5}};
> ```
>
> Isso é equivalente a :
>
> ```c
> int b[2][3] = {{2,4,6},{1,3,5}};
> ```



# Aplicações

## Descobrindo a quantidade de itens de um array

Pode ser tentador usar *sizeof* de qualquer jeito, esse operador mede o tamanho em bytes de alguma estrutura.

Exemplo do uso do sizeof :

```c
#include <stdio.h>

int main(){
	int n = 1;
	printf("tamanho de um inteiro : %li bytes \n",sizeof(n));
}
```

Ao executar irá exibir o valor em bytes de um int.

<img src="../../../../Projetos/C/Array/imagens/3.png" style="zoom:67%;" />

Porém caso aplicar o operador *sizeof* diretamente no array, o retorno será o tamanho total(os itens que o compõe ) do array em bytes.

O seguinte código esclarece isso :

```c
#include <stdio.h>
int main(){
	int n[5] = {1,2,3,4,5};
	printf("tamanho do array : %li bytes \n",sizeof(n));
	printf("tamanho do primeiro item : %li bytes",sizeof(n[0]));
}
```

Ao executar :

![](../../../../Projetos/C/Array/imagens/4.png)

Como o array tem 5 itens do tipo int e cada int ocupa 4 bytes , então temos que o array contendo 20 bytes. 

Essa informação pode parecer óbvia, mas é importante, pois para saber a quantidade de itens de um array, basta dividir o tamanho total pelo tamanho de um dos itens dele. 

> Isso funciona justamente porque todos os itens de um array são do mesmo tipo 

O seguinte código mostra isso :

```c
#include <stdio.h>
int main(){
	int n[5] = {1,2,3,4,5};
	printf("tamanho do array : %li bytes \n", sizeof(n)); // Tamanho do array
	printf("tamanho do primeiro item : %li bytes \n",sizeof(n[0])); // Tamanho do primeiro
	printf("o array possui : %li itens \n", sizeof(n)/sizeof(n[0])); // Itens do array
}
```

A divisão do tamanho do array pelo tamanho de um dos seus itens está representado na seguinte expressão :

```
sizeof(n)/sizeof(n[0])
```

O resultado do código :

![](../../../../Projetos/C/Array/imagens/5.png)

## Descobrindo a quantidade de itens de arrays multi-dimensionais

O processo não é muito diferente do que visto antes.

Vamos analisar o seguinte código :

```c
#include <stdio.h>
int main(){
	int n[][3] = {{2,4,6},{1,3,5}};
	printf("O tamanho do array n : %li bytes \n",sizeof(n));
	printf("O tamanho de um item do array n : %li bytes \n",sizeof(n[0][0]));
	printf("A quantidade de itens do array n : %li itens",sizeof(n)/sizeof(n[0][0]));
}
```

> Um array precisa ter um tamanho maior que zero para obviamente existir, por isso o acesso do primeiro item do primeiro array.
>
> ```c
> sizeof(n[0][0])
> ```



# Códigos finais

## Para inverter os itens de uma lista 

```c
#include <stdio.h>
#include <stdlib.h>

int main(){
    char lista[] = {'A','B','C','D','E'};
    // Informacoes da lista
    
    // Tamanho da lista
    int tamanho_da_lista = sizeof(lista)/sizeof(lista[0]);
    // j --> Ultimo indice da lista 
    int j = tamanho_da_lista - 1;
    // i --> Primeiro indice da lista
    int i = 0;
    // variavel para armazenar os valores que serao trocados no intuito de saber o valor passado
    int variavel_temporaria;
    while(i < j){
        // Guardando o valor do item que sera alterado para ter ideia do seu valor passado
        variavel_temporaria = lista[i];
        // Primeiro item alterado
        lista[i] = lista[j];
        // Segundo item alterado com base no valor passado do primeiro item
        // Esse valor passado esta armazenado na variavel temporaria
        lista[j] = variavel_temporaria;

        // Incremento
        i++;
        // Decrescimo
        j--;
    }
    
    // Exibindo a lista
    printf("lista:");
    for (size_t i = 0; i < tamanho_da_lista ; i++)
    {
        printf("%c",lista[i]);
    }
}
```

## Eco do programa

```c
#include <stdio.h>

/* ->|Arquivo eco.c|<-
*Objetivo :
*----
*Exibe no terminal os argumentos passados para o programa
*----
*/

int main(int argsQ , char * args[]) {
  //argsQ --> Quantidade de argumentos
  //args --> Array de ponteiros para os argumentos 
  // o primeiro elemento de args deve ser o nome do programa

  // Checa se ha argumentos suficientes para a msg
  if(argsQ > 1 ) {
    
    // Para exibir cada elemento,menos o primeiro,do array args
    for(int i = 1; i < argsQ ; i++ ){
      printf("%s ",args[i]);
    }

    printf("\n"); // Saltar uma linha apos exibir
  
  }
  // Caso contrario, exibe uma msg padrao
  else{
    printf("Desculpe, tamanho insuficiente\n");
  }
}
```

Depois de compilado, basta executar o programa no terminal passando argumentos extras além do nome do programa :

```bash
./eco Ola pessoinha
>Ola pessoinha
```

