# Funções

Uma função é um pedaço de código que pode ser reutilizado e permite diminuir repetições desnecessárias à medida que o programa cresce.

# Declarando uma função

Para isso podemos usar a palavra-chave "function" da seguinte forma :

```javascript
function <nome-da-funcao>(){corpo}
```

Por exemplo :

```javascript
function quadrado(x){
    return x*x
}
```

A função definida possui o nome "quadrado", mas apenas definimos uma função, para executar uma função precisamos invocar, chamar pelo seu nome e incluindo sempre os parênteses:

```javascript
quadrado(2)
>4
```

Outro exemplo :

```javascript
function ola(){
    console.log("Olá")
}
```

Isso foi uma declaração. Para usar :

```javascript
ola()
>Olá
```

> O return indica o que a função irá retornar ao ser chamada.

# Funções Arrow

Essa é uma forma de declarar funções introduzida no ES6.

```javascript
let nomedafuncao = (argumentos) => { corpo da função }
```

 Exemplo :

```javascript
let imprimir = () => {console.log("Oie")}
imprimir()
>Oie
```

> O uso de chaves { } para expressões de uma linha é opcional.
>
> ```javascript
> let imprimir = () => console.log("Oie")
> ```
>
> Essa forma ainda é válida.

