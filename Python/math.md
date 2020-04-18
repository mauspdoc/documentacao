# Módulo math

O módulo math já vem pré instalado com python , basta importar usando :

```python
import math
```

## Constantes

### Pi

Use o seguinte código para usar o valor de Pi :

```python
pi = math.pi # ou use apenas math.pi caso queira usar diretamente
```

### Tau

Essa constante é igual a 2Pi, use isso para obter o valor:

```python
tau = math.tau # ou apenas math.tau
```

### O Número de euler (*e*)

Basta usar : 

```python
log_natural = math.e # ou apenas math.e
```

## Arredondar

*Caso tente arredondar um inteiro, o valor retornado será ele mesmo*

### Arredondar números para valores maiores

Use a função do módulo math :

```python
math.ceil(numero) 
```

Exemplo:

```python
math.ceil(4.5)
>>>5
```

### Arredondar números para valores menores

Use a função do módulo math :

```python
math.floor(4.5)
>>>4
```

## Operações

### Logaritmo 

Use a seguinte função do módulo math :

```python
math.log(<numero>, <base>)
```

Se você omitir a base, o python entenderá como um log natural.

Exemplo :

```python
math.log( 4, 2 )
>>>2.0
math.log( 8, 2 )
>>>3.0
```

#### Log na base 2

Há duas formas de se calcular isso :

```python
math.log(<numero>,2) # Calcula um número qualquer na base 2
```

Entretanto, existe uma função que é mais precisa ainda :

```python
math.log2(<numero>) # Calcula um número na base 2
```

Exemplo :

```python
math.log(3,2)
>>>1.5849625007211563
math.log2(3)
>>>1.584962500721156
```

#### Log na base 10 

Há duas formas de se calcular isso :

```python
math.log(80,10)
1.9030899869919433
```

Entretanto, existe uma função que é mais precisa ainda :

```python
math.log10(80)
>>>1.9030899869919435
```

### Potência

Use a seguinte função :

```python
math.pow(<base>,<expoente>)
```

Exemplo :

```python
math.pow(2,4)
>>>16.0
```

O mesmo pode ser obtido sem usar o módulo math:

```python
2**4 # numero ** expoente
>>>16
```

Podemos também usar uma função própria do python, que não precise do módulo math :

```python
pow(2,4) # pow(númreo,expoente)
>>>16
```

Disso tudo, a função do módulo math ainda é mais rápida, devido a velocidade da linguagem C na qual ela foi construída.

### Raiz quadrada 

Use a função do módulo math :

```python
math.sqrt(<numero>)
```

Exemplo :

```python
math.sqrt(4)
>>>2
math.sqrt(16)
>>>16
math.sqrt(32)
>>>5.656854249492381
```

### Trigonometria

| Tipo     | Função     | Exemplo             |
| -------- | ---------- | ------------------- |
| Seno     | math.sin() | math.sin(math.pi/2) |
| Cosseno  | math.cos() | math.cos(math.pi)   |
| Tangente | math.tan() | math.tan(math.pi/4) |

Observe que qualquer valor de ângulo a ser passado para essas funções deve ser em radiano.

Há uma função também para calcular a hipotenusa de uma triângulo retângulo , basta fornecer o tamanhos dos catetos para a função :

```python
math.hypot(<lado1>,<lado2>)
```

Exemplo:

```python
math.hypot(3,4)
>>>5.0
math.hypot(6,8)
>>>10.0
```

### Fatorial

Use a função do módulo math :

```python
math.factorial(<numero>)
```

Exemplo :

```python
math.factorial(4)
>>>24
math.factorial(3)
>>>6
math.factorial(12)
>>>479001600
```

