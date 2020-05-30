# Estruturas

Estrutura(structure) é uma coleção de membros, sendo possível ter esses de diferentes tipos.

# Declarando uma estrutura

## Primeira Forma

```c
struct <nome> {
    <corpo>
}; // Importante terminar com ;
```

O corpo é o local onde se coloca as variáveis da estrutura, sendo que podem ser de tipos diferentes.

Exemplo :

```c
struct humano
{
    int idade;
    char nome[100];
    char sobrenome[100];
};
```

Essa estrutura possui o nome "humano", dentro da estrutura temos a idade, o nome e o sobrenome. Todas essas variáveis possuem tipos diferentes.

Ao utilizar essa estrutura, vamos utilizar como se fosse um tipo qualquer :

```c
struct <nome-da-estrutura> <nome-da-variavel>;
```

No caso do exemplo :

```c
struct humano mauricio;
```

A variável mauricio será a variável para se referir à estrutura humano, poderíamos reaproveitar essa estrutura para outras variáveis :

```c
struct humano bia;
struct humano pedro;
```

E cada uma dessas variáveis possuem a estrutura humano específica para a variável.

Mas para atribuir os valores para a estrutura, a melhor forma é declarar a estrutura e iniciar os valores :

```c
struct <nome-da-estrutura> <nome-da-variavel> = {<valores>};
```

Exemplo :

```c
struct humano mauricio = {19,"Mauricio","Ferraz"};
```

Devemos atribuir os valores de acordo com a ordem que foram organizados na estrutura.

```c
struct humano bia = {22,"Bia","Lira"};
struct humano pedro = {25,"Pedro","Balcani"};
```

> Caso queira atribuir valores fora de ordem, podemos especificar para qual membro da estrutura queremos atribuir :
>
> ```c
> struct humano mauricio = {.nome = "Mauricio", .sobrenome = "Ferraz", .idade = 19};
> ```
>
> Veja que usamos *.nome-do-membro* para especificar para qual membro da estrutura atribuir.
>
> Dessa forma não precisamos seguir a ordem da forma que a estrutura foi criada.



## Segunda Forma

Podemos fazer uma estrutura e referencia-la por nome fazendo dela um tipo como typedef, responsável por criar "apelidos" para os tipos existentes.

```c
typedef struct {
    <corpo>
} <nome-da-estrutura>; //Importante lembrar do ;
```

A nossa estrutura humana pode ser reescrita da seguinte forma :

```c
typedef struct {
    int idade;
    char nome[100];
    char sobrenome[100];
} humano;
```

Mas ao utilizar muda um pouco, pois o "humano" é um "atalho" o tipo "struct" e o seu corpo inteiro.

```c
<nome-da-estrutura> <nome-da-variavel> = {<valores>};
```

> Dessa forma não é necessário colocar struct ao fazer uma referência para uma estrutura como visto na primeira forma.

```c
humano mauricio = {19, "Mauricio", "Ferraz"};
```

>  Para acessar os valores de uma estrutura usamos :
>
> ```
> variavel.<componente-da-estrutura>
> ```
>
> Por exemplo :
>
> ```c
> humano mauricio = {19, "Mauricio", "Ferraz"};
> /*
> mauricio.idade --> acessa a idade(19)
> mauricio.nome --> acessa o nome("Mauricio")
> mauricio.sobrenome --> acessa o sobrenome("Ferraz")
> */
> ```

## (Códigos finais)

Código para contextualizar a estrutura feita até agora :

Usando a primeira forma :

```c
#include <stdio.h>
#include <stdlib.h>

struct humano{
    int idade;
    char nome[100];
    char sobrenome[100];
};

int main()
{
    struct humano mauricio = {19, "Mauricio", "Ferraz"};
    printf("Eu sou o %s %s,",mauricio.nome,mauricio.sobrenome);
    printf("tenho %i anos",mauricio.idade);
}
```

Usando a segunda forma :

```c
#include <stdio.h>
#include <stdlib.h>

typedef struct {
    int idade;
    char nome[100];
    char sobrenome[100];
} humano;

int main()
{
    humano mauricio = {19, "Mauricio", "Ferraz"};
    printf("Eu sou o %s %s,",mauricio.nome,mauricio.sobrenome);
    printf("tenho %i anos",mauricio.idade);
}
```

> Lembrando que uma forma válida para a linha 12  também é :
>
> ```c
>  humano mauricio = {.nome = "Mauricio", .idade = 19, .sobrenome = "Ferraz"};
> ```

