# Introdução

Vamos começar pelo famoso "Hello World !", para isso use o seguinte código :

```dart
main(){
  print("Hello World!");
}
```

A saída é :

```
Hello World!
```

> Comentários em Dart são feitos usando :
>
> 1. // < Texto>
> 2. /* < Texto > */
>
> A primeira opção permite comentar apenas uma linha, enquanto que a segunda forma é para comentários de múltiplas linhas.

O que temos nesse código é uma função main( ), essa função deve estar presente em todos os códigos Dart, ela é o ponto de partida do código ao ser executado,por isso é tão importante. Dentro da função main () temos outra função, essa é responsável por exibir mensagens na tela : print().

Outro ponto importante é a presença de ' '; ''(ponto-vírgula) , não é sem sentido, isso indica o término de um comando, caso esquecer de colocar no fim das sentenças, o compilador irá alertar o erro :

Vamos adicionar um pouco mais para perceber a construção e a utilização de funções, que são pedaços de código reutilizáveis.

```dart
main() {
  print("Hello World!");
  engracado(); // Adicionado
}

// A seguinte parte foi adicionada
engracado(){
  print("A vida é engraçada");
}
```

O que esperar disso ? Bem, uma função é executada ao ser chamada pelo nome. Nessa parte definimos uma nova função cujo nome é "engracado" :

```dart
engracado(){
  print("A vida é engraçada");
}
```

Essa função tem "a função" de executar print("A vida é engraçada") , então a ser chamada deve exibir a mensagem "A vida é engraçada". Mas somente se for chamada pelo nome, isso ocorre dentro da função main( ), pois ela é o ponto de entrada do programa.

```dart
main() {
  print("Hello World!");
  engracado(); // Chamando a funcao
}
```

Então a iniciar o programa devemos esperar duas mensagens :

```
Hello World!
A vida é engraçada
```

> Uma função é basicamente :
>
> ```
> nome-da-funcao(<possiveis-parametros>){corpo}
> ```
>
> Parâmetros nada mais é do que os itens necessários para a  função funcionar corretamente e o corpo é a parte a ser executada ao ser chamada.

