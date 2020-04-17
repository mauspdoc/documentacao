# Iteradores

Segundo a documentação oficial:

> Um iterador é um objeto que representa um fluxo de dados; Este objeto retorna os dados um elemento por vez. Um iterador Python deve suportar um método chamado: meth: iterator .__ next__ que não leva argumentos e sempre retorna o próximo elemento do fluxo. Se não houver mais elementos no fluxo,: meth: iterator .__ next__ deve aumentar a exceção: exc:` StopIteration`. Os iteradores não precisam ser finitos; no entanto, é perfeitamente razoável escrever um iterador que produza um fluxo infinito de dados.
>
> A função built-in: func: iter leva um objeto arbitrário e tenta retornar um iterador que retornará os conteúdos ou elementos do objeto, caso o contrario retorna: exc:` TypeError` se o objeto não suportar a iteração. Vários dos tipos de dados internos do Python suportam a iteração, sendo as listas e os dicionários mais comuns. Um objeto é chamado: : iterable se você pode obter um iterador para ele.
>
> Você pode experimentar a interface de iteração manualmente:
>
> ```python
> L = [1, 2, 3]
> it = iter(L)
> it  
> <...iterator object at ...>
> it.__next__()  # same as next(it)
> 1
> next(it)
> 2
> next(it)
> 3
> next(it) # Erro porque não há mais nada na lista para iterar
> Traceback (most recent call last):
>   File "<stdin>", line 1, in <module>
> StopIteration
> 
> ```
>
> Python espera objetos iteráveis em vários contextos diferentes, sendo o mais importante a palavra-chave: forstatement. Na declaração `` para X em Y``, Y deve ser um iterador ou algum objeto para o qual: func: iter pode criar um iterador. Estas duas declarações são equivalentes:
>
> ```python
> for i in iter(obj):
>     print(i)
> 
> for i in obj:
>     print(i)
> ```

# Geradores

## Expressões Geradoras

São parecidas com lista compreensivas, porém são delimitadas por parênteses.

```python
(expressão for <elemento> in iterador)
```

Exemplo 1 :

```python
x = (x + 2 for x in range(10))
```

Isso retorna um objeto gerador, que pode ser iterável:

```python
for e in x:
    print(e)
 # Isso exibe um item de cada vez de 'x', ou seja, --> 2,3,4,5,6,7,8,9,10,11
```

Caso queira transformar em uma lista:

```python
lista = list(x)
print(lista)
>>>[2, 3, 4, 5, 6, 7, 8, 9, 10, 11]
```

>  Cuidado básico, nesse caso podemos iterar sobre o gerador apenas uma vez:
>
> ```python
> gerador = (x for x in range(10))
> lista = list(gerador)
> print(lista)
> >>>[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
> lista2 = list(gerador)
> print(lista2)
> >>>[]
> ```
>
> Ao criar um objeto generator, lembre-se sempre de fazer uma iteração:
>
> ```python
> gerador = (x for x in range(10))
> print(gerador)
> >>><generator object <genexpr> at 0x7f86c9e527d0> # Exemplo
> ```
>
> Pelo simples motivo do corpo não ser executado de uma vez , o uso de memória é muito otimizado, sendo ideal usar geradores para um grande volume de dados 
>
> Comparação encontrada no [Towards Data Science ](https://towardsdatascience.com/reduce-memory-usage-and-make-your-python-code-faster-using-generators-bd79dbfeb4c):
>
> ```python
> # Aplicação normal
> import memory_profiler
> import time
> def check_even(numbers):
>     even = []
>     for num in numbers:
>         if num % 2 == 0: 
>             even.append(num*num)
>             
>     return even
> if __name__ == '__main__':
>     m1 = memory_profiler.memory_usage()
>     t1 = time.clock()
>     cubes = check_even(range(100000000))
>     t2 = time.clock()
>     m2 = memory_profiler.memory_usage()
>     time_diff = t2 - t1
>     mem_diff = m2[0] - m1[0]
>     print(f"Levou {time_diff} Secs e {mem_diff} Mb para executar esse metodo")
> ```
>
> Resultado:
>
> ```
> >>>Levou 21.876470000000005 Secs e 1929.703125 Mb para executar esse metodo
> ```
>
> Com uma função geradora:
>
> ```python
> import memory_profiler
> import time
> def check_even(numbers):
>     for num in numbers:
>         if num % 2 == 0:
>             yield num * num 
>     
> if __name__ == '__main__':
>     m1 = memory_profiler.memory_usage()
>     t1 = time.clock()
>     cubes = check_even(range(100000000))
>     t2 = time.clock()
>     m2 = memory_profiler.memory_usage()
>     time_diff = t2 - t1
>     mem_diff = m2[0] - m1[0]
>     print(f"Levou {time_diff} Secs e {mem_diff} Mb para executar esse metodo")
> ```
>
> Resultado:
>
> ```
> Levou 2.9999999995311555e-05 Secs e 0.02656277 Mb para executar esse metodo
> ```
>
> 

