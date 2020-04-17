# Manim

## Uso Básico

### Preview de alguma cena

```python
python -m manim example_scenes.py SquareToCircle -pl
```

examples_scenes.py : Arquivo que contém a cena desejada

SquareToCircle: Nome da Classe que está contida no arquivo

-pl : Preview + Low(qualidade)

## Texto

### Uso básico

Use o objeto TextMobject:

```python
TextMobject("Texto aqui")
```

> ! O texto é feito por LaTex:
>
> "é uma linguagem para formatação de textos" - wikibooks

Para exibir qualquer Mobject deve-se usar:

```python
self.add(TextMobject("Texto aqui"))  # Adiciona de forma estática
# ou 
self.play(Write(TextMobject("Texto aqui"))) # Isso para exibir animações
```

## 

### Equações Matemáticas

Como dito, O TextMobeject usa o LaTex para renderizar a parte textual:

```python
from manimlib.imports import *

class Equations(Scene):
    def construct(self):
        # Fazendo equações
        first_eq = TextMobject("$$J(\\theta) = -\\frac{1}{m} [\\sum_{i=1}^{m} y^{(i)} \\log{h_{\\theta}(x^{(i)})} + (1-y^{(i)}) \\log{(1-h_{\\theta}(x^{(i)}))}] $$")
        second_eq = ["$J(\\theta_{0}, \\theta_{1})$", "=", "$\\frac{1}{2m}$", "$\\sum\\limits_{i=1}^m$", "(", "$h_{\\theta}(x^{(i)})$", "-", "$y^{(i)}$", "$)^2$"]

        second_mob = TextMobject(*second_eq)

        for i,item in enumerate(second_mob):
            if(i != 0):# soma(a=2,b=3)
                item.next_to(second_mob[i-1],RIGHT)

        eq2 = VGroup(*second_mob)

        des1 = TextMobject("Com Manim você pode escrever equações como essa...")
        des2 = TextMobject("Ou essa...")
        des3 = TextMobject("E parece legal!!")

        #Coloring equations
        second_mob.set_color_by_gradient("#33ccff","#ff00ff")

        #Positioning equations
        des1.shift(2*UP)
        des2.shift(2*UP)

        #Animating equations
        self.play(Write(des1))
        self.play(Write(first_eq))
        self.play(ReplacementTransform(des1, des2), Transform(first_eq, eq2))
        self.wait(1)

        for i, item in enumerate(eq2):
            if (i<2):
                eq2[i].set_color(color=PURPLE)
            else:
                eq2[i].set_color(color="#00FFFF")

        self.add(eq2)
        self.wait(1)
        self.play(FadeOutAndShiftDown(eq2), FadeOutAndShiftDown(first_eq), Transform(des2, des3))
        self.wait(2)
```

A parte Latex :

```python
first_eq = TextMobject("$$J(\\theta) = -\\frac{1}{m} [\\sum_{i=1}^{m} y^{(i)} log{h_{\\theta}(x^{(i)})} + (1-y^{(i)}) \\log{(1-h_{\\theta}(x^{(i)}))}] $$")
second_eq = ["$J(\\theta_{0}, \\theta_{1})$m array com:m array com:m array com:m array com:", "=", "$\\frac{1}{2m}$","$\\sum\\limits_{i=1}^m$", "(", "$h_{\\theta}(x^{(i)})$", "-", "$y^{(i)}$", "$)^2$"]
```

Alguma explicações adicionais:

> Com a função **enumerate** podemos  ampliar as funcionalidades de for facilmente.Vejamos como imprimir uma lista, em que temos o índice entre colchetes e o valor à sua direita:
>
> > ```python
> > L = [5,9,3]
> > x = 0
> > for e in L:
> >     print(f"indice [{x}] , item {e}")
> >     x += 1
> > ```
>
> O mesmo poderia ser feito de forma  mais fácil com:
>
> > ```python
> > L = [5,9,3]
> > for x,e in enumerate(L):
> >     printf(f"indice [{x}], item {e}")
> > ```
>
> Enumerate retorna uma tupla onde o primeiro valor é o índice e o segundo valor é o elemento . 
>
> ```python
> x,e = (0,5) # (Indice1,Elemento1)
> x,e = (1,9) # (Indice2,Elemento2)
> x,e = (2,3) # (Indice3,Elemento3)
> ```
>
> 

## Cores

### Padrão

Dentro do arquivo manimlib/constants.py podemos encontrar uma seção com cores padrões dentro de um dicionário:

```python
COLOR_MAP = {
    "DARK_BLUE": "#236B8E",
    "DARK_BROWN": "#8B4513",
    "LIGHT_BROWN": "#CD853F",
    "BLUE_E": "#1C758A",
    "BLUE_D": "#29ABCA",
    "BLUE_C": "#58C4DD",
    "BLUE_B": "#9CDCEB",
    "BLUE_A": "#C7E9F1",
    "TEAL_E": "#49A88F",
    "TEAL_D": "#55C1A7",
    "TEAL_C": "#5CD0B3",
    "TEAL_B": "#76DDC0",
    "TEAL_A": "#ACEAD7",
    "GREEN_E": "#699C52",
    "GREEN_D": "#77B05D",
    "GREEN_C": "#83C167",
    "GREEN_B": "#A6CF8C",
    "GREEN_A": "#C9E2AE",
    "YELLOW_E": "#E8C11C",
    "YELLOW_D": "#F4D345",
    "YELLOW_C": "#FFFF00",
    "YELLOW_B": "#FFEA94",
    "YELLOW_A": "#FFF1B6",
    "GOLD_E": "#C78D46",
    "GOLD_D": "#E1A158",
    "GOLD_C": "#F0AC5F",
    "GOLD_B": "#F9B775",
    "GOLD_A": "#F7C797",
    "RED_E": "#CF5044",
    "RED_D": "#E65A4C",
    "RED_C": "#FC6255",
    "RED_B": "#FF8080",
    "RED_A": "#F7A1A3",
    "MAROON_E": "#94424F",
    "MAROON_D": "#A24D61",
    "MAROON_C": "#C55F73",
    "MAROON_B": "#EC92AB",
    "MAROON_A": "#ECABC1",
    "PURPLE_E": "#644172",
    "PURPLE_D": "#715582",
    "PURPLE_C": "#9A72AC",
    "PURPLE_B": "#B189C6",
    "PURPLE_A": "#CAA3E8",
    "WHITE": "#FFFFFF",
    "BLACK": "#000000",
    "LIGHT_GRAY": "#BBBBBB",
    "LIGHT_GREY": "#BBBBBB",
    "GRAY": "#888888",
    "GREY": "#888888",
    "DARK_GREY": "#444444",
    "DARK_GRAY": "#444444",
    "DARKER_GREY": "#222222",
    "DARKER_GRAY": "#222222",
    "GREY_BROWN": "#736357",
    "PINK": "#D147BD",
    "LIGHT_PINK": "#DC75CD",
    "GREEN_SCREEN": "#00FF00",
    "ORANGE": "#FF862F",
}
```



## Posicionamento

### Padrão

Dentro do arquivo manimlib/constants.py temos uma seção:

```python
ORIGIN = np.array((0., 0., 0.))
UP = np.array((0., 1., 0.))
DOWN = np.array((0., -1., 0.))
RIGHT = np.array((1., 0., 0.))
LEFT = np.array((-1., 0., 0.))
IN = np.array((0., 0., -1.))
OUT = np.array((0., 0., 1.))
X_AXIS = np.array((1., 0., 0.))
Y_AXIS = np.array((0., 1., 0.))
Z_AXIS = np.array((0., 0., 1.))

# Useful abbreviations for diagonals
UL = UP + LEFT
UR = UP + RIGHT
DL = DOWN + LEFT
DR = DOWN + RIGHT

TOP = FRAME_Y_RADIUS * UP
BOTTOM = FRAME_Y_RADIUS * DOWN
LEFT_SIDE = FRAME_X_RADIUS * LEFT
RIGHT_SIDE = FRAME_X_RADIUS * RIGHT

```

Veja como ele fornece coordenadas por meio de uma matrix $ (x,y,z)$  usando o numpy.

> Note uma parte importante do código:
>
> ```python
> TOP = FRAME_Y_RADIUS * UP
> BOTTOM = FRAME_Y_RADIUS * DOWN
> LEFT_SIDE = FRAME_X_RADIUS * LEFT
> RIGHT_SIDE = FRAME_X_RADIUS * RIGHT
> ```
>
> Essa parte contém referência que usam FRAME_Y_RADIUS e FRAME_X_RADIUS que estão contidas nesse código:
>
> ```python
> DEFAULT_PIXEL_HEIGHT = PRODUCTION_QUALITY_CAMERA_CONFIG["pixel_height"]
> DEFAULT_PIXEL_WIDTH = PRODUCTION_QUALITY_CAMERA_CONFIG["pixel_width"]
> DEFAULT_FRAME_RATE = 60
> 
> DEFAULT_POINT_DENSITY_2D = 25
> DEFAULT_POINT_DENSITY_1D = 250
> 
> DEFAULT_STROKE_WIDTH = 4
> FRAME_HEIGHT = 8.0
> FRAME_WIDTH = FRAME_HEIGHT * DEFAULT_PIXEL_WIDTH / DEFAULT_PIXEL_HEIGHT
> FRAME_Y_RADIUS = FRAME_HEIGHT / 2
> FRAME_X_RADIUS = FRAME_WIDTH / 2
> ```
>
> PRODUCTION_QUALITY_CAMERA_CONFIG é um dicionário que define a qualidade do vídeo:
>
> ```python
> PRODUCTION_QUALITY_CAMERA_CONFIG = {
>     "pixel_height": 1440,
>     "pixel_width": 2560,
>     "frame_rate": 60,
> }
> 
> HIGH_QUALITY_CAMERA_CONFIG = {
>     "pixel_height": 1080,
>     "pixel_width": 1920,
>     "frame_rate": 60,
> }
> 
> MEDIUM_QUALITY_CAMERA_CONFIG = {
>     "pixel_height": 720,
>     "pixel_width": 1280,
>     "frame_rate": 30,
> }
> 
> LOW_QUALITY_CAMERA_CONFIG = {
>     "pixel_height": 480,
>     "pixel_width": 854,
>     "frame_rate": 15,
> }
> 
> ```
>
> 

### Borda e Canto

Um método que pode ser aplicado a um mobject é to_corner(posição) e e to_edge(posição). Veja o código das duas :

```python
# mobject.py
def to_corner(self, corner=LEFT + DOWN, buff=DEFAULT_MOBJECT_TO_EDGE_BUFFER):
        return self.align_on_border(corner, buff)

def to_edge(self, edge=LEFT, buff=DEFAULT_MOBJECT_TO_EDGE_BUFFER):
        return self.align_on_border(edge, buff)    
```

>  Essa constante  DEFAULT_MOBJECT_TO_EDGE_BUFFER  consta em constants.py: 
>
> ```python
> # constants.py
> SMALL_BUFF = 0.1
> MED_SMALL_BUFF = 0.25
> MED_LARGE_BUFF = 0.5
> LARGE_BUFF = 1
> 
> DEFAULT_MOBJECT_TO_EDGE_BUFFER = MED_LARGE_BUFF
> DEFAULT_MOBJECT_TO_MOBJECT_BUFFER = MED_SMALL_BUFF
> ```

Exemplo de seu uso:

O seguinte código move um texto para o canto esquerdo superior:

```python
class Cena1(Scene):
    def construct(self):
        texto1 = self.texto(["1"])
        texto1.to_corner(TOP+LEFT)
        self.play(Write(texto1))
        self.wait(2)
    def texto(self,textMo):
        lista = textMo
        objeto = TextMobject(*lista)
        return objeto

```

Porém o mesmo efeito pode ser adquido com o seu método irmão:

```python
from manimlib.imports import *
import numpy as np
class Cena1(Scene):
    def construct(self):
        texto1 = self.texto(["1"])
        texto1.to_edge(TOP+LEFT) # Acaba tendo o mesmo efeito de to_corner()
        self.play(Write(texto1))
        self.wait(2)
    def texto(self,textMo):
        lista = textMo
        objeto = TextMobject(*lista)
        return objeto
```



### Aproximar um objeto(mobject) de outro

1. mobject1.next_to(mobject2 , posição):

   > ```python
   > class Braces(Scene):
   >     def construct(self):
   >         # Primeira equação
   >         # Lado A(Esquerdo),Lado B(Direito)
   >         eq1A = TextMobject("4x + 3y")
   >         eq1 = TexMobject("=")
   >         eq1B = TexMobject("0")
   >         eq2A = TextMobject("5x - 2y")
   >         eq2 = TextMobject("=")
   >         eq2B = TextMobject("3")
   > 
   >         # Decidindo onde ficará a igualdade
   >         eq1.next_to(eq1A,RIGHT) # A igualdade fica proximo de eq1A pelo lado direito
   >         # O "0" ficará ao lado da igualdade que está ao lado do "4x + 3y"
   >         eq1B.next_to(eq1,RIGHT)
   > ```

2. mobject1.move_to(ponto/mobject)

   > ```python
   > def move_to(self, point_or_mobject, aligned_edge=ORIGIN,
   >                 coor_mask=np.array([1, 1, 1])):
   >         if isinstance(point_or_mobject, Mobject):
   >             target = point_or_mobject.get_critical_point(aligned_edge)
   >         else:
   >             target = point_or_mobject
   >         point_to_align = self.get_critical_point(aligned_edge)
   >         self.shift((target - point_to_align) * coor_mask)
   >         return self
   > ```
   >
   > Arquivo que contém essa função no mobject.py.
   >
   > 
   >
   > Veja também o método get_critical_point():
   >
   > ```python
   > def get_critical_point(self, direction):
   >         """
   >         Picture a box bounding the mobject.  Such a box has
   >         9 'critical points': 4 corners, 4 edge center, the
   >         center.  This returns one of them.
   >         """
   >         result = np.zeros(self.dim)
   >         all_points = self.get_points_defining_boundary()
   >         if len(all_points) == 0:
   >             return result
   >         for dim in range(self.dim):
   >             result[dim] = self.get_extremum_along_dim(
   >                 all_points, dim=dim, key=direction[dim]
   >             )
   >         return result
   > ```
   >
   > o 'dim' é uma informação contida no início, no  dicionário:
   >
   > ```python
   > CONFIG = {
   >         "color": WHITE,
   >         "name": None,
   >         "dim": 3,
   >         "target": None,
   >     }
   > ```
   >
   >   

### Direções 

Do arquivo mobject.py temos os seguintes métodos que podem ser aplicados aos mobject:

```python
	def get_edge_center(self, direction):
        return self.get_critical_point(direction)

    def get_corner(self, direction):
        return self.get_critical_point(direction)

    def get_center(self):
        return self.get_critical_point(np.zeros(self.dim))

    def get_center_of_mass(self):
        return np.apply_along_axis(np.mean, 0, self.get_all_points())

    def get_boundary_point(self, direction):
        all_points = self.get_points_defining_boundary()
        index = np.argmax(np.dot(all_points, np.array(direction).T))
        return all_points[index]

    def get_top(self):
        return self.get_edge_center(UP)

    def get_bottom(self):
        return self.get_edge_center(DOWN)

    def get_right(self):
        return self.get_edge_center(RIGHT)

    def get_left(self):
        return self.get_edge_center(LEFT)

    def get_zenith(self):
        return self.get_edge_center(OUT)

    def get_nadir(self):
        return self.get_edge_center(IN)
```

## Chaves

Chaves é definido por Braces( ). Seu texto pode ser editado pelo método get_text("texto aqui").

```python
class Cena2(Scene):
    def construct(self):
        texto1 = self.texto(['$ 2 \\times 2 $'])
        conjunto_de_textos = [texto1]
        self.play(Write(texto1))

        self.wait(2)
        self.chaves(texto1,DOWN,"$ 2^2 $",2)

    def texto(self,textMo):
        lista = textMo
        objeto = TextMobject(*lista)
        return objeto
    def alinhamento_eq(self,textMO):
        for i,item in enumerate(textMO):
            if i != 0 :
                item.next_to(textMO[i-1],RIGHT)
    def chaves(self,item,posicao,texto,tempo):
        chave1 = Brace(item,posicao)
        texto1Chave1 = chave1.get_text(texto)
        self.play(GrowFromCenter(chave1),Write(texto1Chave1))
        self.wait(tempo)
```



## Animações [^1] 

### Transform

```python
class AddingMoreText(Scene):
    def construct(self):
        quote = TextMobject("Imaginação é  mais importante que conhecimento")
        quote.set_color(RED)
        quote.to_edge(UP)
        quote2 = TextMobject("Uma pessoa que nunca errou,nunca fez nada novo")
        quote2.set_color(YELLOW)
        author=TextMobject("-Albert Einstein")
        author.scale(0.75)
        author.next_to(quote.get_corner(DOWN+RIGHT),DOWN)

        self.add(quote) # Adiciona de forma estática
        self.add(author)
        self.wait(2) # Espera 2s
        self.play(Transform(quote,quote2),          ApplyMethod(author.move_to,quote2.get_corner(DOWN+RIGHT)+DOWN+2*LEFT))
        
        self.play(ApplyMethod(author.scale,1.5))
        author.match_color(quote2)
        self.play(FadeOut(quote))
```

A ideia básica é transformar um objeto 1 em um objeto 2:

```python
self.play(Transform(objeto1,objeto2))
```

No exemplo acima vemos uma transformação que torna "quote" em "quote2". Lembre-se que animações devem ser feitos em self.play():

```python
 self.play(Transform(quote,quote2),ApplyMethod(author.move_to,quote2.get_corner(DOWN+RIGHT)+DOWN+2*LEFT))
```

### ApplyMethod



### Fade

1. FadeOut
2. FadeIn
3. FadeInFrom
4. FadeInFromDown
5.  FadeOutAndShift
6. FadeOutAndShiftDown
7. FadeInFromPoint
8. FadeInFromLarge

### Indicação

1. FocusOn
2. Indicate
3. Flash
4. CircleIndicate
5. ShowPassingFlash
6. ShowCreationThenDestruction
7. ShowCreationThenFadeOut
8. AnimationOnSurroundingRectangle
9. ShowPassingFlashAround
10. ShowCreationThenDestructionAround
11. ShowCreationThenFadeAround
12. ApplyWave
13. WiggleOutThenIn
14. TurnInsideOut

### Rotating

### GrowArrow

### GrowFromCenter

[^1]: Para mais informações veja o arquivo /animation



## Gráfico 

### Exemplo 1

Gráficos são do tipo GraphScene(diferente do Scene comum). O dicionário CONFIG permite configurar algumas coisas do gráfico e como sempre a classe deve conter o construct.

```python
class Plot1(GraphScene):
    CONFIG = {
        "y_max" : 50,
        "y_min" : 0,
        "x_max" : 7,
        "x_min" : 0,
        "y_tick_frequency" : 5, 
        "x_tick_frequency" : 0.5, 
        "axes_color" : BLUE, 
        "y_labeled_nums": range(0,60,10),
        "x_labeled_nums": list(np.arange(2, 7.0+0.5, 0.5)),
        "x_label_decimal":1,
        "y_label_direction": RIGHT,
        "x_label_direction": UP,
        "y_label_decimal":3
    }
    def construct(self):
        self.setup_axes(animate=True)
        graph = self.get_graph(lambda x : x**2,color = GREEN,x_min = 2,x_max = 4)
        self.play(ShowCreation(graph),run_time = 2) # run_time controle o tempo de animação 
        self.wait() # Espera um pouco após executar a animação
```

Veja que o gráfico terá eixos com y variando de 0 a 50, enquanto x varia de 0 a 7:

```python
"y_max":50,
"y_min":0,
"x_max":7,
"x_min":0
```

A função executada recebera apenas valores de x que vão de 2 até 4:

```python
graph = self.get_graph(lambda x : x**2,color = GREEN,x_min = 2,x_max = 4) 
# Veja o x_min e x_max, os valores que serão passados pra função 
# A função terá cor verde(GREEN), enquanto os eixos são azuis(BLUE)
```

