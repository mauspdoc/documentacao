# Animações com matplotlib

## Introdução

### Requisitos

Modulos python:

1. numpy
2. matplotlib

Programas para salvar a animação em video(escolha um desses):

1. ffmpeg
2. imagemagick

### Quais funções do matplotlib permitem a animação:

FuncAnimation --> Faz animações ao chamar repetidamente a função func

ArtistAnimation --> Animação feita com um conjunto fixo de objetos Artist  

## Primeiro Codigo

```python
import numpy as np
from matplotlib import pyplot as plt
from matplotlib.animation import FuncAnimation
plt.style.use('seaborn-pastel')

# Criando uma figura basica(7-9)
fig = plt.figure()
ax = plt.axes(xlim=(0, 4), ylim=(-2, 2))
line, = ax.plot([], [], lw=3)
# A função init faz a animação acontecer
# Inicializa os dados
def init():
    line.set_data([], [])
    return line,
def animate(i): #animate(i=quantidade de frames)
    x = np.linspace(0, 4, 1000)
    y = np.sin(2 * np.pi * (x - 0.01 * i))
    line.set_data(x, y)
    return line,

anim = FuncAnimation(fig, animate, init_func=init,
                               frames=200, interval=20,
                                blit=True)#blit força renderizar apenas as partes que mudaram do grafico


anim.save('sine_wave.gif', writer='imagemagick')

```

