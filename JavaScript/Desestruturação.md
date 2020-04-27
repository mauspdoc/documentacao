# Desestruturação

# Atribuição por desestruturação

Permite atribuir valores para variáveis usando arrays ou objetos.

## Array

Arrays são do seguinte tipo :

```javascript
var <nome> = [...]
```

Exemplo :

```javascript
var mArray = [1,2,3,4]
```

Para acessar itens do array usamos :

```
<nome>[posição]
```

Exemplo :

```javascript
mArray[0]
>1
mArray[1]
>2
mArray[2]
>3
mArray[3]
>4
```

## Atribuindo usando arrays

Primeiro podemos declarar um array :

```javascript
var mArray = [1,2,3,4]
```

Podemos atribuir valores para variáveis ao colocá-las dentro de colchetes :

```javascript
var [a,b,c,d] = mArray
/* var a,b,c,d = mArray esta errado */
/* Poderiamos ter feito direto var a,b,c,d = [1,2,3,4] */
a
>1
b
>2
c
>3
d
>4
```

A quantidade de  variáveis não precisa coincidir com a quantidade de itens do array:

```javascript
var [e,f] = mArray
e
>1
f
>2
```

## Atribuindo o resto de um array

```javascript
var [a, ...b] = [1,2,3,4]
a
>1
b
>[ 2, 3, 4 ]
```

Podemos usar três pontos '...' para afirmar que o resto do array não utilizada para atribuição deve ser atribuído para a variável que surge após o três pontos.

## Atribuindo usando objetos

A mais básica possível :

```javascript
var o = {p:22,q:33} // objeto
var {p,q} = o // p --> 22 , q --> 33
p
>22
q
>33
```

Veja que o nome das variáveis precisam coincidir com algum item do objeto.

```javascript
var o = {p:22,q:33} // objeto
var {x} = o
x
>
```

Como não temos o nome da variável dentro do objeto, a variável vai possuir um indefinido.

Poderíamos consertar isso da seguinte forma :

```javascript
var o = {p:22,q:33} // objeto
var {x} = o
x
>
o.x = 44 // Agora o objeto possui {p:22,q:33,x:44}
({x} = o)
x
>44
```

Pode ter se perguntado sobre o uso do parênteses :

```javascript
var o = {k:2}
var k;
{k} = o // Errado
```

Dessa forma o JS interpreta a seguinte parte  como um bloco só :

```javascript
{k} = 0
```

Por isso devemos usar parênteses :

```javascript
({k} = o) // Certo
```

> Caso estiver declarando a variável , não precisa do parênteses graças a palavra-chave como o 'var':
>
> ```javascript
> var {k} = o
> ```
>
> Nesse caso não precisamos de parênteses