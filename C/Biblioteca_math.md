# Biblioteca Math

Na linguagem C existe uma biblioteca para a área da matemática, para usar em um programa basta incluir no código, da seguinte forma :

```c
#include <math.h>
```

> Em alguns compiladores como o gcc é preciso adicionar um comando extra para indicar a necessidade de buscar bibliotecas externas :
>
> ```bash
> gcc arquivo.c -lm
> ```
>
> Acrescente o "-lm"

| Funções   | Descrição                                |
| --------- | ---------------------------------------- |
| sqrt(x)   | raiz quadrada de x                       |
| cbrt(x)   | raiz cubica de x                         |
| exp(x)    | função exponencial                       |
| log(x)    | logaritmo natural de x                   |
| log10(x)  | logaritmo de x na base 10                |
| fabs(x)   | valor absoluto de x como ponto flutuante |
| ceil(x)   | arredonda para o maior inteiro           |
| floor()   | arredonda para o menor inteiro           |
| pow(x,y)  | x elevado a y                            |
| fmod(x,y) | resto de x/y como ponto flutuante        |
| sin(x)    | seno de x (radiano)                      |
| cos(x)    | cosseno de x (radiano)                   |
| tan(x)    | tangente de x (radiano)                  |

# Exemplo 1

```c
#include <stdio.h>
#include <math.h>
/* A biblioteca math fornece as funcoes matematicas */


/* Definimos a consante Pi para usar nos calculos*/
#define PI 3.14159265359 

// A seguir esta um funcao prototipo, ela apenas verifica se os tipos estao corretos
// O prototipo serve para checar se o tipo passado para funcao confere

double grauPi(double y);

int main(){
    double angulo = 90.0 ;
    double angulo_radiano = grauPi(angulo);
    double seno = sin(angulo_radiano);
    printf("O seno de %.2f : %.2f \n",angulo,seno);
    return 0;
}

// Funcao para converter graus para radiano 
double grauPi(double y){
    double angulo = (y*PI)/180.0 ;
    return angulo;
}
```

Um ponto interessante é definir a constante PI para usar no programa, isso precisa ser feito de forma manual, é interessante para funções trigonométricas, pois os ângulos precisam ser em radianos. 

Primeiro começamos declarando que vamos usar a biblioteca de matemática do C :

```c
#include <stdio.h>
#include <math.h>
/* A biblioteca math fornece as funcoes matematicas */
```

Depois é importante usar *define* para fazer de PI uma constante que possa ser usada pelo programa. 

```c
/* Definimos a consante Pi para usar nos calculos*/
#define PI 3.14159265359 
```

Usar valores radianos pode não ser tão intuitivo, por isso uma função que converte  o ângulo em graus para radiano.

Uma parte importante é declarar uma função protótipo, ela é útil ao compilar para o compilador se certificar de que os valores usados nas funções estão corretos em relação ao tipo. Não é necessário fazer toda a função, deve apenas declarar os tipos que a função irá precisar :

```c
// A seguir esta um funcao prototipo, ela apenas verifica se os tipos estao corretos
// O prototipo serve para checar se o tipo passado para funcao confere

double grauPi(double y);
```

 Então, o programa vai se certificar de que a função retorne um valor do tipo double e que o valor passado para a função seja do tipo double.

Essa função foi definida após a função main() :

```c
// Funcao para converter graus para radiano 
double grauPi(double y){
    double angulo = (y*PI)/180.0 ;
    return angulo;
}
```

Ela retorna um valor do tipo double e seu parâmetro (valor que precisa ser passado pra função) precisa ser um double , isso está conforme à função prototipo. Ela será a responsável por receber o valor em graus e terá como o retorno um ângulo em radiano. Isso é muito importante para facilitar o uso das funções trigonométricas.

Agora vamos focar na função main () :

```c
int main(){
    double angulo = 90.0 ; // Angulo em graus
    double angulo_radiano = grauPi(angulo); // Angulo em radianos
    double seno = sin(angulo_radiano); // Seno do angulo em radianos
    printf("O seno de %.2f : %.2f \n",angulo,seno);
    return 0;
}
```

Declaramos nossas variáveis básicas :

```c
double angulo = 90.0 ; // Angulo em graus
double angulo_radiano = grauPi(angulo); // Angulo em radianos
double seno = sin(angulo_radiano); // Seno do angulo em radianos
```

Próximos passos, o objetivo é exibir na tela os valores do código :

```c
printf("O seno de %.2f : %.2f \n",angulo,seno);
```

 