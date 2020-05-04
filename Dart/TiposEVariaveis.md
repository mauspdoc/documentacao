# Tipos

Os seguintes tipos serão conhecidos melhor à medida que avança no aprendizado de Dart :

* Numbers ( É dividido entre int e double)
* Strings ( Uma sequência de caracteres)
* Booleans ( Valores verdade ou falso)
* Lists
* Maps
* Runes
* Symbols

# Variáveis

Ao declarar uma variável podemos escolher entre seguir um estilo tipado, ou seja, declarando explicitamente os tipos das variáveis ou podemos deixar o próprio Dart entender por si o tipo da variável.

Para declarar uma variável sem especificar :

```dart
var < nome-da-variavel > = valor_da_variavel ;
```

> Variável sem inicializar  ( sem atribuição ) :
>
> ```dart
> var < nome-da-variavel >;
> ```
>
> Exemplo :
>
> ```dart
> var idade;
> ```
>
> Se caso não atribuir nada para a variável, nesse caso o valor dela será null :
>
> ```dart
> main() {
>     var idade;
> 	print(idade);
> }
> ```
>
> O resultado será :
>
> ```
> null
> ```
>
> Inclusive, o tipo da variável será Null. Isso ocorre mesmo se especificar o tipo da variável.

 Por exemplo :

```dart
var msg = "Olá Mundo";
```

Entretanto, podemos declarar uma variável especificando seu tipo :

```dart
< tipo > <nome-da-variavel > = < atribuição > ; // Atribuição pode ser feita depois
```



```dart
String msg = "Olá Mundo";
```

```dart
int numero = 2;
```

## Quais as consequências de explicitar ou não o tipo ?

Vamos comparar dois códigos semelhantes, o primeiro a seguir não está correto :

```dart
main() {
  String msg = 2;
  print(msg);
}
```

O Dart não executa esse código, pois entende que o usuário especificou a variável como String , ou seja, uma sequência de caracteres , por isso não aceita números. Então, o Dart avisa desse pequeno erro.

Entretanto, se a variável for declarada usando *var*, ou seja, sem especificar o tipo :

```dart
main() {
  var msg = 2;
  print(msg);
}
```

Esse código executa, pois o usuário deixou de controlar o tipo e o Dart entende a variável como int ( número inteiro) , isso pode sair dos planos de um programador que esperava uma variável "textual" e não numérica. 

> Caso quiser testar o tipo de suas variáveis através do código :
>
> ```dart
> main(){
>   var numero = 2;
>   var fracionado = 2.5;
>   var verdade = true;
>   var texto = "Ola Mundo!";
>   var sem_valor;
>   print("1-Numero 2- Fracionado 3- Verdade 4- Texto 5- Função Print 6- sem_valor");
>   print(numero.runtimeType);
>   print(fracionado.runtimeType);
>   print(verdade.runtimeType);
>   print(texto.runtimeType);
>   print(print is Function); // print é uma função ?
>   print(sem_valor.runtimeType);
> }
> ```
>
> Usamos runtimeType para 'extrair' o tipo de variáveis , ao executar o tipo será exibido. 
>
> Usamos "print is Function" por não ser bem uma variável, podemos usar isso para outros tipos , podemos inclusive usar o código de cima remodelado :
>
> ```dart
> main(){
>   var numero = 2;
>   var fracionado = 2.5;
>   var verdade = true;
>   var texto = "Ola Mundo!";
>   var sem_valor;
>   print("1-Numero 2- Fracionado 3- Verdade 4- Texto 5- Função Print 6- sem_valor");
>   print(numero is int); // numero é um int ?
>   print(fracionado is double); // fracionado é um double ?
>   print(verdade is bool); // verdade é um bool ?
>   print(texto is String); // texto é uma String ?
>   print(print is Function); // print é uma Função ?
>   print(sem_valor is Null); // sem_valor é um Null ?
> }
> ```
>
> Vamos receber true se a afirmação for verdade. 

