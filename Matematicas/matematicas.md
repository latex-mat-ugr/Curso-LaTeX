# Matemáticas


Hay dos formas de escribir matemáticas: en la misma línea o centrado en una línea separada.

* Para escribir matemáticas *en línea* agrupamos el texto entre dólares. Por ejemplo,
```latex
$\cos(x+y)^{2}=\sqrt{2+x^2}$
```
produce $\cos(x+y)^{2}=\sqrt{2+x^2}$.

* Para escribir matemáticas centradas en una línea separada, agrupamos la fórmula entre \\[ \\] o con dólares dobles. Es recomendable la primera opción. Por ejemplo
```latex
$$
\frac{x+y}{2x-1}=\sqrt{\log(x)^2+1}
$$
```
produce
$$
\frac{x+y}{2x-1}=\sqrt{\log(x)^2+1}
$$

***

### Espaciado

Los espacios dentro del modo matemático no se tienen en cuenta.

El espacio dentro las fórmulas es distinto al espacio en modo texto. Compara lo siguiente:
```latex
Sea $x=1,2$ o $3$ con sea $x=1$, $2$ o $3$
```
La forma correcta de escribirlo es la *segunda* si queremos que LaTeX use el espaciado que se considera correcto.

***

## Construcciones básicas

### Operaciones aritméticas, subíndices y superíndices
```latex
$a + b$, $a - b$, $-a$, $a / b$, $a b$, $a \cdot b$, $a \times b$, $a \div b$
```
produce
$a + b$, $a - b$, $-a$, $a / b$, $a b$, $a \cdot b$, $a \times b$, $a \div b$
Puedes escribir subíndices y superíndices de la siguiente forma:
```latex
n^{2}, x^{1/x}, x_{n}, lim_{x \to \infty}
```
que da como resultado
$$
n^{2}, x^{1/x}, x_{n}, \lim_{x \to \infty}
$$

Se pueden anidar y usar subíndices y superíndices al mismo tiempo:
```latex
\sum_{n=1}^{\infty} x^{x^n}
```
$$
\sum_{n=1}^{\infty} x^{x^n}
$$

***

### Fracciones

Las fracciones se escriben con el comando `\frac{numerador}{denominador}`

```latex
\frac{a}{b}, \tfrac{1}{2},\dfrac{1}{2}
```
produce
$\frac{a}{b}$, $\tfrac{1}{2}$, $\dfrac{1}{2}$

`frac` se ajusta su tamaño dependiendo del contexto: si está en una línea es pequeño (como `tfrac`), si está en una línea separada aumenta (como `dfrac`). Podemos forzar un comportamiento u otro usando `tfrac` o `dfrac`.

***

### Números binómicos

`\binom{a}{b}` produce $\binom{a}{b}$. Al igual que con frac, se
puede alterar su tamaño usando `tbinom{a}{b}` o `dbinom{a}{b}` y se obtiene $\tbinom{a}{b}$ y $\dbinom{a}{b}$.

***

### Puntos suspensivos

En lugar de escribir tres puntos seguidos, `\dots, \ldots, \cdots` producen puntos suspensivos con el espaciado correcto. `\dots` intenta adaptarse al entorno. `\ldots` da como resultado puntos "bajos" y `\cdots`centrados. Un ejemplo:
```latex
x=1,2,\ldots 3, x+y+\cdots +z, x\times y \times \dots z
```
produce $x=1,2,\ldots 3$, $x+y+\cdots +z$, $x\times y \times \dots \times z$

***

### Integrales

Varios símbolos de integral
```latex
$\oint \iint \iiint \iiiint \idotsint$
```
$\oint \iint \iiint \iiiint \idotsint$

***

### Raíces

`\sqrt{num}`y `\sqrt[n]{num}` permiten escribir raíces cuadradas y raíces n-ésimas.

```latex
$\sqrt{3}$, $\sqrt[4]{3}$ $\sqrt[\leftroot{2} \uproot{1} 6]{3}$
```
$\sqrt{3}$, $\sqrt[4]{3}$ $\sqrt[\leftroot{2} \uproot{1} 6]{3}$

***

## Texto en matemáticas

La orden \text{texto} permite incluir texto dentro de una fórmula con el mismo aspecto que el entorno
```latex
$$
f(x)=x^2,\text{ si $x>0$ y $\cos(x)$ en otro caso}
$$
```
$$
f(x)=x^2,\text{ si $x>0$ y $\cos(x)$ en otro caso}
$$

***

### Acentos, gorros,...

`\hat{a}`, `\acute{a}`, `\breve{a}`,  `\dot`, `\tilde`, `\mathring{A}` produce
$\hat{a}, \acute{a}, \breve{a},  \dot{a}, \tilde{a}, \mathring{A}$


También se pueden escribir flechas sobre un texto usando `\vec{a}` o
`\overrightarrow{abc}`

Con el paquete *esvect* se pueden representar vectores mejor
```latex
\vv{a},  \; \vv{abc} , \; \vv*{a}{n}
```

***

## Operadores

LaTeX tiene predefinidos algunas funciones usuales, pero podemos añadir lo que deseemos con la orden `\DeclareMathOperator`. Para ello es necesario cargar el paquete amsmath

$\cos (x)$, $\sin(x)$, $\tan(x)$, $\arccos(x)$, $\log(x)$, $\ln (x)$, $\exp(x)$,...
Usando
```latex
\DeclareMathOperator{\dist}{distancia}
```
en la cabecera del documento, está disponible el comando `\distancia`

***

## Sub y superíndices de nuevo

El comando `\texttt{substack}` para líneas centradas
```latex
$$
\sum_{\substack{i=1\\j=123}} i+j
$$
```
permite incluir subíndices o superíndices que ocupen varias líneas.
$$
\sum_{\substack{i=1\\j=123}} i+j
$$

***

## Llaves y flechas


`\overbrace`, `\underbrace`, `\overline`, `\underline` se usan para añadir llaves o líneas por encima o bajo un texto o fórmula.
```latex
$$
\overbrace{a+\underbrace{b+c}_{z}+d}^{n}
$$
```
produce
$$
\overbrace{a+\underbrace{b+c}_{z}+d}^{n}
$$

`\overleftarrow`, `\underleftarrow`, `\overrightarrow`, `\underrightarrow`,
`\overleftrightarrow` permiten escribir flechas que se estiran para acomodar texto sobre o bajo ellas. Las versiones *left* y *right* indican el sentido de las flechas.
```latex
$$
\overleftarrow{a+b+c}, \quad \underrightarrow{x+y}
$$
```
da como resultado
$$
\overleftarrow{a+b+c}, \quad \underrightarrow{x+y}
$$

***

### Más flechas

`\xrightarrow[debajo]{arriba}`y `\xleftrightarrow[debajo]{arriba}` permiten escribir flechas extensibles con texto encima y debajo. Por ejemplo,
```latex
$$
x\xrightarrow[a+b]{a-b+c}, \quad x\xleftarrow[a+b]{a-b+c} y
$$
```
produce
$$
x\xrightarrow[a+b]{a-b+c}, \quad x\xleftarrow[a+b]{a-b+c} y
$$

***

## Más matemáticas

### Espacios

Se puede añadir o quitar espacio manualmente. Las formas más comunes de
hacerlo son

* Añadir (poco) `\,` añade un espacio pequeño.
```latex
$$
\int_{0}^{1} f(x)\, dx = \sqrt{x}\, n
$$
```

* Añadir (algo más) `\quad` y `\qquad` añaden la
longitud de una letra m o de dos. Son espacios dinámicos (pueden variar
un poco para ajustar las líneas).
```latex
$$
f(x)=\cos (x), \quad \forall\,  x \in [0,1]
$$
```

* Quitar (poco) `\!` quita un espacio pequeño. Compara el espacio que separa las funciones en la siguiente expresión
```latex
$$
\sin x/\log x \qquad \sin x /\! \log x
$$
```

***

## Entornos multilínea

Pueden ser de dos tipos: ajustados o alineados.

### Entornos ajustados

Hay dos: *gather* y *multline*. El primero de ellos muestra las ecuaciones
centradas una tras otra. Se usa `\\` para partir líneas en la expresión. Por ejemplo
```latex
$$
\begin{gather}
x+y+z_1\\+\int_0^1 f(x)\, \mathrm{d}x +\cos \left( \sqrt{x} \, \right)
\end{gather}
$$
```
$$
\begin{gather}
x+y+z_1\\ +\int_0^1 f(x)\, \mathrm{d}x +\cos \left( \sqrt{x} \, \right)
\end{gather}
$$
El segundo, multline, alinea la primera fórmula a la izquierda, la última a la
derecha y las intermedias, si las hay, las centra.
```latex
$$
\begin{multline}
x+y+z_1 + \lim_{x \to 0} \int_{0}^{x^2} f(x)\,\mathrm{d}x +
\frac{x-1}{x+1} \\
+x+y+z+\omega+\int_0^1 f(x)\, \mathrm{d}x +\cos \left( \sqrt{x} \, \right)
\end{multline}
$$
```
$$
\begin{multline}
x+y+z_1 + \lim_{x \to 0} \int_{0}^{x^2} f(x)\,\mathrm{d}x +
\frac{x-1}{x+1} \\
+x+y+z+\omega+\int_0^1 f(x)\, \mathrm{d}x +\cos \left( \sqrt{x} \, \right)
\end{multline}
$$

***

### Entornos alineados

Hay varios entornos de este tipo, dependiendo de cómo estén alineadas
las columnas. Además de `\\` para añadir una línea nueva, `&` se usa para indicar las columnas.

En primer lugar, *align* muestra las columnas centradas.
```latex
$$
\left.
\begin{align}
 x+y & = 6 \\
2x-3y & = 4
\end{align}
\right\}
$$
```
$$
\left.
\begin{align}
 x+y & = 6 \\
2x-3y & = 4
\end{align}
\right\}
$$

*flalign* es una variante de align que alinea a la izquierda la primera
columna y a la derecha la última
```latex
$$
\begin{flalign}
 x+y +2 z	& = 6 	& 2u+4v & =8   \\
2x-3y & = 4 & 3u-4v  & = 10
\end{flalign}
$$
```
Por último, *alignat*, que tiene un comportamiento un poco distinto: hay
que decir cuántas columnas hay y añadir los espacios entre ellas
manualmente.
```latex
$$
\begin{alignat}{4}
   f(x) &= x + yz              & g(x) &= x + y + z\\
   h(x) &= xy + xz + yz \qquad & k(x) &= (x+y)(x+z)(y+z)
    \notag
\end{alignat}
$$
```
$$
\begin{alignat}{4}
   f(x) &= x + yz              & g(x) &= x + y + z\\
   h(x) &= xy + xz + yz \qquad & k(x) &= (x+y)(x+z)(y+z)
    \notag
\end{alignat}
$$
Es útil en casos como el siguiente:
```latex
$$
\begin{alignat}{3}
            x &= x  (y+z) &
            &\quad\text{(propiedad distributiva)}\\
              &= (x  y) + (x z) & &
               \quad\text{(usamos ahora que $x=0$)}\notag\\
              &= y z
\end{alignat}
$$
```
$$
\begin{alignat}{3}
            x &= x  (y+z) &
            &\quad\text{(propiedad distributiva)}\\
              &= (x  y) + (x z) & &
               \quad\text{(usamos ahora que $x=0$)}\notag\\
              &= y z
\end{alignat}
$$

***

### Entornos subsidiarios

align, alignat y gather tienen versiones subsidiarias que tienen que ir dentro de un entorno matemático.
```latex
$$
\begin{aligned}[c]
 x &= 3 + \mathbf{p} + \alpha\\
      y &= 4 + \mathbf{q}\\
      z &= 5 + \mathbf{r}\\
      u &=6 + \mathbf{s}
   \end{aligned}
   \text{\quad usande\quad}
   \begin{gathered}[b]
      \mathbf{p} = 5 + a + \alpha\\
      \mathbf{q} = 12\\
      \mathbf{r} = 13\\
      \mathbf{s} = 11 + d
   \end{gathered}
$$
```
```latex
$$
\left.
\begin{aligned}[c]
wx&=u\\
wy&=v\\
w&=10
\end{aligned}
\right\}
\qquad\Longleftrightarrow\qquad
\begin{aligned}[c]
x&=u/w\\
y&=v/w\\
\end{aligned}
$$
```
El entorno más flexible es split. Se puede usar sólo
```latex
$$
\begin{split}
                (x_{1}x_{2}&x_{3}x_{4}x_{5}x_{6})^{2}\\
                           &+ (x_{1}x_{2}x_{3}x_{4}x_{5}
                            + x_{1}x_{3}x_{4}x_{5}x_{6}
                            + x_{1}x_{2}x_{4}x_{5}x_{6}
                            + x_{1}x_{2}x_{3}x_{5}x_{6})^{2}
\end{split}
$$
```
$$
\begin{split}
                (x_{1}x_{2}&x_{3}x_{4}x_{5}x_{6})^{2}\\
                           &+ (x_{1}x_{2}x_{3}x_{4}x_{5}
                            + x_{1}x_{3}x_{4}x_{5}x_{6}
                            + x_{1}x_{2}x_{4}x_{5}x_{6}
                            + x_{1}x_{2}x_{3}x_{5}x_{6})^{2}
\end{split}
$$
o dentro de otro y se alinea como corresponda
```latex
$$
\begin{align}
	\left.
  \begin{split}
             f(x) & =    (x_{1}x_{2} ) \\
		           & = x+y
	\end{split}
  \right\}
  \implies y+z
\end{align}
$$
```
$$
\begin{align}
	\left.
  \begin{split}
             f(x) & =    (x_{1}x_{2} ) \\
		           & = x+y
	\end{split}
  \right\}
  \implies y+z
\end{align}
$$
