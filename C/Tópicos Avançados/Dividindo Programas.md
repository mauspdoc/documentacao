# Dividindo Programas

# Include

Usar a diretiva *include* permite "incluir" programas externos no código.

```c
#include <stdio.h>
```

 Essa é uma forma de incluir o cabeçalho ( veja o 'h' no final indicando 'header' de cabeçalho) : stdio.h . Ao fazer esse tipo de include entre < > , o programa irá pesquisar entre os arquivos padrão do sistema para as bibliotecas.

> Os arquivos 'padrão' do sistema usados na linguagem C possuem o seguinte endereço :
>
> Para sistemas operacionais linux :
>
> ```
> /usr/include/
> ```
>
> Nessa pasta é possível ver os arquivos cabeçalhos que são incluídos nos programas.

Caso for incluir programas desenvolvidos pessoalmente, não deve usar < > , pois programas pessoais podem estar em diretórios diferentes do padrão. Para incluir programas personalizados, deve-se indicar o caminho até eles entre " " .

```c
#include "teste.h"
```

Isso busca o cabeçalho teste dentro da pasta atual, mas poderíamos fornecer o caminho completo também.