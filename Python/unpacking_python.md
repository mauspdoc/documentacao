## Desestruturando atribuições

### Desestruturando como valores

```python
a,b = (1,2) # Tupla
print(a)
>>> 1  
print(b)
>>> 2
```

> ! Ocorrerá erro se tentar unpack valores maiores que o tamanho do iterable(objeto alvo da operação do interador)
>
> ```python
> a,b,c = [1]
> # Gera erro
> ```
>
> 

### Ignorando algum valor

```python
a,_ = (1,2)
print(a)
>>>1
a,_,c = (1,2,3)
print(a)
>>>1
print(c)
>>>3
```

## Packing(empacotar) e Unpack(empacotar) de argumentos  e parâmetros de uma função

### Lista

```python
lista = [1, 2, 3, 4]argumentoargumento
print(*lista) # Use o * antes de uma lista para extrair seus valores como argumento 
>>> 1 2 3 4
```

 O exemplo acima equivale a:

```python
print(1, 2, 3, 4) # Cada valor da lista vira um argumento para a função
```

Aplicando a ideia para uma função própria:

```python
def fun(a,b,c):
    print(a+b+c)
lista = [1, 2, 3]
fun(*lista) # Cada item da lista será usada como um argumento 
>>>6 
 
```

> Observação: Se a quantidade de itens da lista não se encaixar na quantidade de argumentos, então ocorre erro.

Pode-se ainda utilizar dentro dos parâmetros de uma função o " * ":

```python
def fun(*lista):
    print lista
    
lista = [1,2,3] # Ou uma tupla(1,2,3)
fun(lista)
>>>([1,2,3]) # Caso fosse a tupla >>>((1,2,3))
```

argumento = argumento = argumento = Do exemplo acima, se tira a lição de  que ao usar " * " dentro dos parâmetros da função, qualquer lista/tupla será empacotada em uma tupla.

> Observação: 
>
> ```python
> tupla = (1 , 2, 3) # Caso tenhamos uma tupla
> lista = list(tupla) # list(...) converte os itens da tupla em lista
> print(lista)
> >>>[1 , 2, 3]
> ```

Sabendo da possibidade de $lista \longrightarrow tupla$ , podemos usar " * " dentro dos parâmetros como uma forma de lidar com qualquer tamanho de argumentos que sejam passados para a função:

```python
def fun(*lista): # Lista/Tuplas como argumentos serão convertidas em uma única tupla
    argumento = list(lista) # Convertendo a lista/tupla(argumento) ---> tupla ---> lista
    for e in argumento:
        for i in e:
            print(e)
lista = [1, 2, 3]
fun(lista) 
>>>1
>>>2
>>>3
```

> O que ocorre dentro da função:
>
> ```
> fun(lista)
> ```
>
> A função recebe a lista como argumento e a empacota em uma tupla:
>
> ```python
> ([ 1 , 2, 3])
> ```
>
> Ao executar list(lista)  temos $tupla\longrightarrow lista$:
>
> ```python
> [[1 , 2, 3]] # Cuidado, convertemos os itens da tupla(que tinha uma lista como item) para uma lista, logo o item da tupla(lista) está dentro de uma lista.
> ```
>
> Justamente por esse motivo devemos lidar cuidadosamento com esse tipo de empacotamento e transformação($tupla\longrightarrow lista $). Devido a isso foi preciso fazer duas interações sobre essa lista que contém uma lista:
>
> ```python
> for e in argumento: # Acessa os itens da lista1( so tem um item : uma outra lista2)
>     for i in e: # Acessa os itens da lista2 
>         print(i)
> ```
>
> 

#### Funções extras

Inserir uma lista na outra:

```python
a = ['a']
b = ['b']
c = [*a,*b] # Os itens da lista 'a' e os itens da lista 'b' estão são inseridos na lista 'c'
print(c)
>>>['a','b']
```

Sem isso:

```python
a = ['a']
d = [a] # A lista 'a' está sendo incluida na lista 'd' 
print(d) 
>>>[['a']]
```



### Dicionário

Para o dicionário há uma forma reservada para ele " ** ".

Caso usado em parâmetros de função:

```python
def fun(**dicionario):
    print(dicionario)
```

A função acima permite transformar argumentos em dicionario:

```
fun(a = 2, b = 3, c = 4, d = 5) # Cada atribuição será tratada como chave = valor
>>>{'a':2,'b':3,'c':4,'d':5} # Para assim formar um dicionário
```

Podemos explorar isso como bem desejarmos, veja outro exemplo:

```python
def fun(**dicionario):
    return dicionario
```

Podemos transformar argumentos em dicionário:

```python
meu_dic = fun(a = 2, b = 3) # Não confunda tanto a ponto de colocar ' ' em a e b
meu_dic['a']
>>>2
meu_dic['b']
>>>3

```

> Em fun(a = 2 , b = 3 ) , tanto a quanto b é considerado  parâmetro para a função , a função recebe os argumentos do usuário e converte cada atribuição aos parâmetros como chave:valor e insere num dicionário

Em uma situação diferente, caso seja usado:

```python
função(**{dicionario})
```

Isso traz consequências interessantes como:

```python
def soma(a,b): # A função possui 2 parâmetros(a e b) que serão somados
	print(a+b)
numeros = {'a':2,'b':3} # Dicionario com chaves( que são idênticos aos parâmetro da função)
soma(**numeros) # Ao fazer isso, cada chave será idêntificada ao seu parâmetro e seu valor é passado como argumentos 
>>>5
```

> Essa parte:
>
> ```python
> soma(**numeros)
> ```
>
> É equivalente à:
>
> ```python
> soma(a = 2 , b = 3)
> ```
>
> 