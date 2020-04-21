# Requests 

Segundo o site oficial : 

> Requests é uma biblioteca HTTP para Python simples e elegante, feita para seres humanos. 

Para instalar basta :

> pip install requests

Ao usar no seu código sempre certifique-se de importar :

```python
import requests
```

# Fazendo uma requisição

## Get

```python
r = requests.get(<endereço>)
```

Exemplo :

```python
r = requests.get('https://github.com/timeline.json')
```



## Post

```
r = requests.post(<endereço>)
```

Exemplo :

```python
r = requests.post("http://httpbin.org/post")
```



## Delete

```
r = requests.delete(<endereço>)
```

Exemplo :

```python
r = requests.delete("http://httpbin.org/delete")
```



## Head

```
r = requests.head(<endereço>)
```

Exemplo :

```python
r = requests.head("http://httpbin.org/get")
```



## Options

```
r = requests.options(<endereço>)
```

Exemplo :

```python
r = requests.options("http://httpbin.org/get")
```



## Put

```
r = requests.put(<endereço>)
```

Exemplo :

```python
r = requests.put("http://httpbin.org/put")
```

# Lendo o conteúdo da requisição

```python
import requests 
r = requests.get('https://api.github.com/users/gustavoguanabara/events')
r.text # Exibe o conteudo da requisição já decodificado
```

Resultado :

```
[{"id":"12059702457","type":"PushEvent","actor":{"id":8683378,"login":"gustavoguanabara","display_login":"gustavoguanabara","gravatar_id":...
```

## Caso a requisição não seja texto

```python
r.content
```

Dessa forma um resposta binária será recebida, muito útil para receber imagens da internet.