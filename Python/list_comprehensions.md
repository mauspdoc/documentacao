# List Comprehensions

## Formas

List comprehensions é uma forma de criar uma lista usando uma interação que pode ou não ter condições:

1. ```python
   [<expresão> for <elemento> in <interable>]
   ```

   Por exemplo:

   ```python
   numeros = [x+2 for x in range(1,10)]# range(inicio,fim,passo) cria um sequência de números
   ```

   A condição $x+2$  define que será somado 2 ao elemento x, sendo que esse elemento x está no $range(1,10)$ :

   ```python
   >>>numeros
   [3,4,5,6,7,9,10,11] # O range havia fonercido os números 1,2,3,4,5,6,7,8,9
   ```

2. ```python
   [<expressão> for <elemento> in <interable> if <condição>]
   ```

   Essa é uma forma com condição, como no exemplo abaixo:

   ```python
   pares = [x for x in range(1,11) if x%2 == 0] 
   # x%2 == 0 indica que somente números pares serão admitidos 
   # 9%2 == 0 é falso, logo o 9 não é incluido
   # 4%2 == 0 é verdade, logo 4 é incluido
   ```

   Se a condição for verdadeiro, o elemento será admitido na lista:

   ```
   >>>pares
   [2,4,8,10]
   ```

   Exemplo com o uso do **else**:

   A forma com essa condicional deve ser praticada com cuidado, a condição ocorre antes do loop for:

   ```
   [<elemento> <condição> <loop>]
   ```

   Veja :

   ```python
   [x if x in 'aeiou' else '*' for x in 'apple']
   #[<elemento> if ... else ... <loop>]
   ```

   



Mais alguns exemplos das  formas acima:

```python
[s.upper() for s in "Hello World"]
# ['H','E','L','L','O',' ','W','O','R','L','D']
```

## Lists comprehensions aninhadas

Note que em [<expresão> for < elemento > in < interable >]  , a expressão pode ser qualquer coisa, inclusive outra list comprehension.

Exemplo 1:

```python
 matrix = [[1, 2, 3, 4],[5, 6, 7, 8],[9, 10, 11, 12],]
```

> A matriz representada por esse código é  uma de 3 linhas e 4 colunas:

$$
\begin{pmatrix} 1 & 2 & 3 & 4 \\ 5 & 6 & 7 & 8 \\ 9 & 10 & 11 & 12 \end{pmatrix}
$$

Agora vamos aninhar list comprehension:

```python
[[linha[i] for linha in matrix] for i in range(4)]
```

```python
>>> [[1, 5, 9], [2, 6, 10], [3, 7, 11], [4, 8, 12]]
```

# Dictionary Comprehension

## Noções primárias para uma melhor compreensão

### Função zip

Faz uma interação simultânea em cada um dos seus argumentos e retorna um objeto zip. Ele pega um item de um $ argumento_{1}$ e pega um item do $argumento_{2}$ e empacota em uma tupla e continua a fazer isso. 

```python
x = [1, 2, 3]
y = [4, 5, 6]
list(zip(x,y)) # zip() não retorna nada printável por si , é preciso converter
>>>[(1,4), (2,5), (3,6)] 
```

> Tenha cuidado:
>
> ```python
> x = [1,2,3]
> y = [4,5,6]
> zipado = zip(x,y) 
> list(zipado)
> >>>[(1,4), (2,5), (3,6)] 
> # Caso tentarmos novamente
> list(zipado)
> >>>[] # Dessa vez sem objetos retornados pela variável
> ```
>
> Atribuir o zip() a uma variável e depois transformar em uma lista/tupla mais de uma vez pode gerar efeitos indesejados.
>
> Segundo a documentação oficial:
>
> > "Faz um iterador que agrega elementos de cada um dos iteráveis."

Dica muito importante sobre o uso de dados:

> Documentação oficial:
>
> "As expressões do gerador retornam um iterador que calcula os valores conforme necessário, não precisando materializar todos os valores ao mesmo tempo. Isso significa que as compreensões da lista não são úteis se você estiver trabalhando com iteradores que retornam um fluxo infinito ou uma quantidade muito grande de dados. As expressões do gerador são preferíveis nessas situações."