# String 

# String Literais

Uma string literal é uma sequência de caracteres entre aspas duplas:

> "Venha tomar um sorvete comigo"

## Continuando uma String Literal

Podemos usar um " \ "para continuar uma string em outra linha. A continuação da string precisa ser feita imediatamente no início da outra linha.

```c
#include <stdio.h>

int main() {
  printf("Hello \
World!");
}
```

Ao ser executado :

```
Hello World!
```

Apesar de ser interessante, esse método quebra a indentação, o que pode ser uma desvantagem.

Outra forma de fazer  é separar a frase em strings adjacentes. 

```c
#include <stdio.h>

int main() {
  printf("Hello ""World!"); // Temos duas strings
}
```

Ao ser executado :

```
Hello World!
```

O importante é as string serem adjacentes, a única coisa que pode ficar entre elas é o espaço vazio.

Poderíamos fazer o mesmo da seguinte forma :

```c
#include <stdio.h>

int main() {
  printf("Hello " 
  "World!");
}
```

Assim, podemos ver que esse método respeita a indentação.

## Como strings literais são armazenadas 

C trata strings literais como um array de caracteres.

Então "abc" é tratado como um array  com os itens {'a','b','c','\0'}, é possível notar o "\0" no final, isso indica o término de uma string. 

Vamos entender melhor com o seguinte código :

```c
#include <stdio.h>

int main() {
  char mensagem[] = {'O','l','\0','a'}; // Array de caracteres
  printf("%s",mensagem);
}
```

 

Ao executar :

```
Ol
```

Isso acontece pois o compilador sempre procura o "\0" para saber o fim de uma string.

> O código acima é equivalente a :
>
> ```c
> #include <stdio.h>
> 
> int main(void) {
>   char mensagem[] = "Ol\0 a";
>   printf("%s",mensagem);
>   return 0;
> }
> ```

Vamos para o exemplo mais simples :

```c
#include <stdio.h>

int main() {
  char mensagem[] = "abc"; // Array de caracteres
  int tamanho = sizeof(mensagem)/sizeof(char); // Isso fornece a quantidade de itens
  printf("%d",tamanho); 
}
```

> Veja que o sizeof(mensagem) fornece o tamanho em bytes do array, ou seja, todos os itens dele em bytes. Sabendo que cada item é do tipo char, então, podemos dividir todo o tamanho do array(contendo todos os chars) pelo tamanho de um char, dessa forma sabemos quantos itens há no array.

Ao ser executado :

```
4
```

Evidenciando que não há apenas 'abc' e sim um caractere extra.

Então, o que é passado de fato para a função printf() é a localização(pointer para a letra) da primeira letra, no caso do exemplo acima, a letra 'a'. 