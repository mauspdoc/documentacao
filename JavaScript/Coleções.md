# Arrays

## Criando Arrays

Há duas formas de se criar um Array :

* Usando o construtor Array( )
* Usando Arrays literais [ ]

> Com array literal : 
>
> ```javascript
> myArray = [1,2,3,4,5]
> ```
>
> Com o construtor :
>
> ```javascript
> myArray = Array(1,2,3,4,5)
> ```
>
> 

## Adicionando ou removendo itens de um Array

* push adiciona um item para o final do array
* unshift adiciona um item para o início do array
* pop remove um item do início do array
* shift remove um item do início do array

> Usando o seguinte array :
>
> ```javascript
> myArray = [1,2,3,4,5]
> ```
>
> Usando push :
>
> ```javascript
> myArray.push(2020)
> // myArray = [1,2,3,4,5,2020]
> ```
>
> Usando o pop :
>
> ```javascript
> myArray.pop()
> // myArray = [1,2,3,4,5]
> ```
>
> Usando unshift :
>
> ```javascript
> myArray.unshift(2020)
> // myArray = [2020,1,2,3,4,5]
> ```
>
> Usando shift :
>
> ```javascript
> myArray.shift(2020)
> // myArray = [1,2,3,4,5]
> ```
>
> 

## Usando localização para deletar um item do array

> Usar delete array[index] não modificar o array corretamente, apenas exclui o item, mas não reorganiza o array, permanece um "buraco" no array com um item "undefined"

Pode-se usar o método splice em um array.

> array.splice(< index >, < quantidade a ser deletada >)

Exemplo :

```javascript
myArray = [1,2,3,4,5]
myArray.splice(1,4)
// myArray = [1]
```

> Revertendo o efeito :
>
> ```javascript
> myArray.push(1,2,3,4,5)
> ```



## Operações com Array

