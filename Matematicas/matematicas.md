Hay dos formas de escribir matemáticas: en la misma línea o centrado en una línea separada.

* Para escribir matemáticas *en línea* agrupamos el texto entre dólares. Por ejemplo,

```latex
$\cos(x+y)^{2}=\sqrt{2+x^2}$
```

produce $\cos(x+y)^{2}=\sqrt{2+x^2}$.

* Para escribir matemáticas centradas en una línea separada, agrupamos la fórmula de la forma `\[... \]` o con dólares dobles. Es recomendable la primera opción. Por ejemplo

```latex
\[
  \frac{x+y}{2x-1}=\sqrt{\log(x)^2+1}
\]
```

produce 
$$
  \frac{x+y}{2x-1}=\sqrt{\log(x)^2+1}
$$

El entorno *equation* produce el mismo resultado y añade una marca a la ecuación para poder hacer referencia con posterioridad a ella:

```latex
\begin{equation} \label{eq:identidad}
  e^{i\pi}+1=0 
\end{equation}
```

Los estilos que LaTeX usa por defecto para escribir matemáticas son:

- `textstyle`: matemáticas en línea
- `displaystyle`: matemáticas centradas en línea separada
- `scriptstyle`: sub y superíndices
- `scriptscriptstyle`: sub y superíndices de segundo nivel

Podemos forzar a LaTeX a escribir como lo hace en línea separada añadiendo la orden `\displaystyle`. 

```latex
Sean $f(x)=\frac{x}{2}$ y $\displaystyle g(x)=\frac{x}{3}$ las funciones
````

Es preferible no forzar estos cambios y, seguramente, la solución más razonable sea escribir la función $g$ en una línea separada.



## Espaciado

Los espacios dentro del modo matemático no se tienen en cuenta.

El espacio dentro las fórmulas es distinto al espacio en modo texto. Compara lo siguiente:

```latex
Sea $x=1,2$ o $3$ con sea $x=1$, $2$ o $3$
```

La forma correcta de escribirlo es la *segunda* si queremos que LaTeX use el espaciado que se considera correcto.

### ¿Cómo ajustar los espacios?

Se puede añadir o quitar espacio manualmente. Las formas más comunes de
hacerlo son

* Añadir (poco) `\,` añade un espacio pequeño.

```latex
\[
  \int_{0}^{1} f(x)\, dx = \sqrt{x}\, n
\]
```

* Añadir (algo más) `\quad` y `\qquad` añaden la longitud de una letra m 
  o de dos. Son espacios dinámicos (pueden variar un poco para ajustar 
  las líneas).

```latex
\[
  f(x)= \frac{\sin (1+x)}{\log (1+x)} \quad (x > -1)
\]
```

## Delimitadores

Los paréntesis y los corchetes se suelen usar en matemáticas para agrupar operaciones. En LaTeX los delimitadores incluidos por defecto son

| Delimitador                 | Ejemplo                     | Resultado                   |
| --------------------------- | --------------------------- | --------------------------- |
| Paréntesis `(...)`          | `(x+y)^{2}`                 | $(x+y)^{2}$                 |
| Corchetes `[...]`           | `[x+y]`                     | $[x+y]$                     |
| Llaves `\{...\}`            | `\{2n : n \in \mathbb{N}\}` | $\{2n : n \in \mathbb{N}\}$ |
| Ángulos `\langle...\rangle` | `\langle x,y \rangle`       | $\langle x,y \rangle$       |
| Barra                       | `|z|`                    | $|z|$         |

Las barras, sencillas o dobles, que usamos habitualmente para escribir el módulo o la norma de un vector se escriben con `\lvert z \rvert ` y `\lVert z \rVert`. Puede ser cómodo añadir en la cabecera un comando definido a propósito para esto:

```latex
\providecommand{\abs}[1]{\lvert#1\rvert}
\providecommand{\norm}[1]{\lVert#1\rVert
```

::: {.callout-warning title="¿Para qué tanta barra?"}
  Hay símbolos que son muy parecidos, pero su aspecto es distinto dependiendo de cómo los escribimos: `|`, `\vert`, `\mid` o `\divides` dan como resultado una barra.  La diferencia entre uno y otro, para distinguirlos de alguna forma, es que  `lvert` y `rvert` son delimitadores, es lo que usamos por ejemplo al escribir un valor absoluto. `mid` indica una relación binaria y añade un poco de espacio antes y después. `divides` es también un operador de tipo relación y es lo que deberíamos usar para indicar que 2 divide a 4.
:::

### Tamaño automático de los delimitadores

LaTeX puede ajustar el tamaño de los delimitadores al tamaño de lo que delimitan. En este caso es obligatorio indicar donde empieza y donde acaba con los prefijos `left` y `right`. 

```latex
  \[
    \left[ \left( 1+x^{2} \right) +\frac{y}{2} \right]
  \]
````

$$
    \left[ \left( 1+x^{2} \right) +\frac{y}{2} \right]
$$

Los delimitadores pueden ser distintos a un lado y otro y si se quiere que no aparezca nada en la salida el correspondiente delimitador se cambia por un punto.

```latex
  \[
    \left. \left( 1+x^{2} \right\} +\frac{y}{2} \right]
  \]
```

$$
  \left. \left( 1+x^{2} \right\} +\frac{y}{2} \right]
$$

### Ajuste manual del tamaño

`\bigl \Bigl \biggl \Biggl`, de menor a mayor, y sus correspondientes versiones para el delimitador por la derecha permiten ajustar de forma manual el tamaño de los delimitadores.

```latex
  \bigl (x +(y+z) \Bigr) \neq \biggl[ x+ y^{2} \Biggr\}
```

$$
  \bigl (x +(y+z) \Bigr) \neq \biggl[ x+ y^{2} \Biggr\}
$$

## Construcciones básicas

### Operaciones aritméticas, subíndices y superíndices

```latex
$a + b$, $a - b$, $-a$, $a / b$, $a b$, $a \cdot b$, $a \times b$, $a \div b$
```

produce $a + b$, $a - b$, $-a$, $a / b$, $a b$, $a \cdot b$, $a \times b$, $a \div b$.

Puedes escribir subíndices y superíndices de la siguiente forma:

```latex
\[ 
  n^{2}$, $x^{1/x}$, $x_{n}$, $\lim_{x \to \infty}
\]
```

que da como resultado

$$
n^{2}, x^{1/x}, x_{n}, \lim_{x \to \infty}
$$

Se pueden anidar y usar subíndices y superíndices al mismo tiempo:

```latex
\[
  \sum_{n=1}^{\infty} x^{x^n}
\]
```

$$
\sum_{n=1}^{\infty} x^{x^n}
$$

El comando `\substack` para líneas centradas

```latex
\[
  \sum_{\substack{i=1\\j=123}} i+j
\]
```

permite incluir subíndices o superíndices que ocupen varias líneas.
$$
\sum_{\substack{i=1\\j=123}} i+j
$$

### Fracciones y números binómicos

Las fracciones se escriben con el comando `\frac{numerador}{denominador}`

```latex
\frac{a}{b}, \tfrac{1}{2},\dfrac{1}{2}
```

produce
$\frac{a}{b}$, $\tfrac{1}{2}$, $\dfrac{1}{2}$

`frac` se ajusta su tamaño dependiendo del contexto: si está en una línea es pequeño (como `tfrac`), si está en una línea separada aumenta (como `dfrac`). Podemos forzar un comportamiento u otro usando `tfrac` o `dfrac`.

`\binom{a}{b}` produce $\binom{a}{b}$. Al igual que con frac, puede alterar su tamaño usando `tbinom{a}{b}` o `dbinom{a}{b}` y se obtiene $\tbinom{a}{b}$ y $\dbinom{a}{b}$.

### Puntos suspensivos

En lugar de escribir tres puntos seguidos, `\dots, \ldots, \cdots` producen puntos suspensivos con el espaciado correcto. `\dots` intenta adaptarse al entorno. `\ldots` da como resultado puntos "bajos" y `\cdots`centrados. Un ejemplo:

```latex
x=1,2,\ldots 3, x+y+\cdots +z, x\times y \times \dots z
```

produce $x=1,2,\ldots 3$, $x+y+\cdots +z$, $x\times y \times \dots \times z$.

### Arrays y matrices

#### Arrays

El entorno *array* sirve para escribir objetos agrupados por filas y columnas. Hay que indicar cuántas columnas queremos y cómo van a estar alineadas (a la izquierda, centradas o a la derecha). Las columnas se separan con `&` y las filas nuevas se crean con `\\`. Una malla vacía 3x3 sería así:

```latex
\[
  \left. 
  \begin{array}{lc|r}  % 3 columnas izq., centrada, derecha
    2 & 3 & \cos(x) \\
    -1 & 1 & 0 \\
    2 & 1 &  \\
  \end{array}
  \right\}
\]
```

$$
  \left.
  \begin{array}{lc|r}
    2 & 3 & \cos(x) \\
    -1 & 1 & 0 \\
    2 & 1 &  \\
  \end{array}
  \right\}
$$

Como ves se pueden añadir líneas verticales con `|` entre dos columnas y también horizontales (`\hline` al comienzo de una fila).

#### El entorno *cases*

Un uso habitual de este entorno es definir funciones a trozos: suelen tener una llave al comenzar, nada por la derecha y línea a línea se van explicando los casos:

```latex
\[ 
  f(x) = 
  \begin{cases}
   1+x^2, & \text{si $x<0$,}\\
   e^x,  & \text{si $x>0$,}\\
   1, & \text{si $x=0$.}
\end{cases}
\]
```
$$
  f(x) =
  \begin{cases}
   1+x^2, & \text{si $x<0$,}\\
   e^x,  & \text{si $x>0$,}\\
   1, & \text{si $x=0$.}
\end{cases}
$$

Si la fórmula que define la función es muy alta se puede usar `dcases` en lugar de `cases` de forma análoga a las fracciones.

#### Matrices

Las matrices son un caso particular de arrays. El paquete *amsmath* tiene varios tipos predefinidos dependiendo de los delimitadores que se quieran usar. En este caso no hay que declarar ni tamaño ni alineación:

`matrix` no tiene delimitadores:
```latex
\[
  \begin{matrix}
  a_{11} & a_{12} & a_{13} \\
  a_{21} & a_{22} & a_{23}
  \end{matrix}
\]
```

$$
  \begin{matrix}
  a_{11} & a_{12} & a_{13} \\
  a_{21} & a_{22} & a_{23}
  \end{matrix}
$$  

`pmatrix`, `bmatrix` y `Bmatrix` usan, respectivamente, paréntesis, corchetes y llaves.

```latex
\[
  \begin{pmatrix}
  a_{11} & a_{12} & a_{13} \\
  a_{21} & a_{22} & a_{23}
  \end{pmatrix} 
  \quad
  \begin{bmatrix}
  a_{11} & a_{12} & a_{13} \\
  a_{21} & a_{22} & a_{23}
  \end{bmatrix}
  \quad
  \begin{Bmatrix}
  a_{11} & a_{12} & a_{13} \\
  a_{21} & a_{22} & a_{23}
  \end{Bmatrix}
\]
```

$$
  \begin{pmatrix}
  a_{11} & a_{12} & a_{13} \\
  a_{21} & a_{22} & a_{23}
  \end{pmatrix} 
  \quad
  \begin{bmatrix}
  a_{11} & a_{12} & a_{13} \\
  a_{21} & a_{22} & a_{23}
  \end{bmatrix}
  \quad
  \begin{Bmatrix}
  a_{11} & a_{12} & a_{13} \\
  a_{21} & a_{22} & a_{23}
  \end{Bmatrix}
$$  

Las matrices, por su tamaño, suelen escribirse en modo matemático en línea separada, pero si es pequeña se puede intentar: `smallmatrix`

```latex
La matriz $A = 
  \left(
  \begin{smallmatrix} 
  1 & 2 \\ 
  3 & 4 
  \end{smallmatrix}
  \right)$ se ve bien en una línea
  ```

La matriz $A =
  \left(
  \begin{smallmatrix} 
  1 & 2 \\ 
  3 & 4 
  \end{smallmatrix}
  \right)$ se ve bien en una línea

### Integrales, sumatorios, raíces

Hay varios símbolos de integral incluidos que se adaptan al modo matemático en el que se esté

```latex
$\oint \iint \iiint \iiiint \idotsint$
\[
  \int_{a}^{b} f(x)\, \mathrm{d}x
\]
```

$\oint \iint \iiint \iiiint \idotsint$
$$
\int_{a}^{b} f(x)\, \mathrm{d}x
$$ 

#### Raíces

`\sqrt{num}`y `\sqrt[n]{num}` permiten escribir raíces cuadradas y raíces n-ésimas.

```latex
$\sqrt{3}$, $\sqrt[4]{3}$ $\sqrt[\leftroot{2} \uproot{1} 6]{3}$
```

$\sqrt{3}$, $\sqrt[4]{3}$ $\sqrt[\leftroot{2} \uproot{1} 6]{3}$

### Llaves y flechas

`\overbrace`, `\underbrace`, `\overline`, `\underline` se usan para añadir llaves o líneas por encima o bajo un texto o fórmula.

```latex
\[
 \overbrace{a+\underbrace{b+c}_{z}+d}^{n}
\]
```

produce
$$
\overbrace{a+\underbrace{b+c}_{z}+d}^{n}
$$

`\overleftarrow`, `\underleftarrow`, `\overrightarrow`, `\underrightarrow`,
`\overleftrightarrow` permiten escribir flechas que se estiran para acomodar texto sobre o bajo ellas. Las versiones *left* y *right* indican el sentido de las flechas.

```latex
\[
  \overleftarrow{a+b+c}, \quad \underrightarrow{x+y}
\]
```

da como resultado
$$
  \overleftarrow{a+b+c}, \quad \underrightarrow{x+y}
$$


`\xrightarrow[debajo]{arriba}`y `\xleftrightarrow[debajo]{arriba}` permiten escribir flechas extensibles con texto encima y debajo. Por ejemplo,

```latex
\[
  x\xrightarrow[a+b]{a-b+c}, \quad x\xleftarrow[a+b]{a-b+c} y
\]
```

produce
$$
  x\xrightarrow[a+b]{a-b+c}, \quad x\xleftarrow[a+b]{a-b+c} y
$$

## Texto en matemáticas

La orden `\text{texto}` permite incluir texto dentro de una fórmula con el mismo aspecto que el entorno

```latex
\[
  f(x)=x^2,\text{ si $x>0$ y $\cos(x)$ en otro caso}
\]
```

$$
f(x)=x^2,\text{ si $x>0$ y $\cos(x)$ en otro caso}
$$

### Acentos y gorros

`\hat{a}`, `\acute{a}`, `\breve{a}`,  `\dot`, `\tilde`, `\mathring{A}` produce
$\hat{a}, \acute{a}, \breve{a},  \dot{a}, \tilde{a}, \mathring{A}$

También se pueden escribir flechas sobre un texto usando `\vec{a}` o `\overrightarrow{abc}`

Con el paquete *esvect* se pueden representar vectores mejor

```latex
\vv{a},  \; \vv{abc} , \; \vv*{a}{n}
```

## Tipos de letra en modo matemático

| Tipo               | Código          | Resultado        |
| ------------------ | --------------- | ---------------- |
| Negrita            | `\mathbf{a}`    | $\mathbf{a}$     |
| Caligráfica        | `\mathcal{A}`   | $\mathcal{A}$    |
| Itálica            | `\mathit{ab}`   | $\mathit{ab}$    |
| Recta              | `\mathrm{d}`    | $\mathrm{d}$     |
| Negrita de pizarra | `\matbb{N,R,Q}` | $\mathbb{N,R,Q}$ |
| Gótica             | `\mathfrak{A}`  | $\mathfrak{A}$   |
| ¿Script?           | `\mathscr{A}`   | $\mathscr{A}$    |

## Operadores y funciones

LaTeX tiene predefinidos algunas funciones usuales. Estas funciones/operadores se
escriben con letra recta siempre. Algunos de estos operadores o funciones además 
pueden tener límites que se añaden como subíndices o superíndices.

| código    | salida   | código    | salida    | código    | salida    |
| --------- | -------- | --------- | --------- | --------- | --------- |
| `\arccos` | $\arccos$ | `\cos`    | $\cos$    | `\csc`    | $\csc$    |
| `\exp`    | $\exp$   | `\ker`    | $\ker$    | `\limsup` | $\limsup$ |
| `\min`    | $\min$   | `\sinh`   | $\sinh$   | `\arcsin` | $\arcsin$  |
| `\cosh`   | $\cosh$  | `\deg`    | $\deg$    | `\gcd`    | $\gcd$    |
| `\lg`     | $\lg$    | `\ln`     | $\ln$     | `\Pr`     | $\Pr$     |
| `\sup`    | $\sup$   | `\arctan` | $\arctan$ | `\cot`    | $\cot$    |
| `\det`    | $\det$   | `\hom`    | $\hom$    | `\lim`    | $\lim$    |
| `\log`    | $\log$   | `\sec`    | $\sec$    | `\tan`    | $\tan$    |
| `\arg`    | $\arg$   | `\coth`   | $\coth$   | `\dim`    | $\dim$    |
| `\inf`    | $\inf$   | `\liminf` | $\liminf$ | `\max`    | $\max$    |
| `\sin`    | $\sin$   | `\tanh`   | $\tanh$   |           |           |

```latex
\[
  \cos^{2}(x)+\sin^{2}(x)= \lim_{x \to 0} \frac{\sin(x)}{x} 
\]
```

Podemos añadir el operador que deseemos con la orden `\DeclareMathOperator`. Para ello es necesario cargar el paquete *amsmath*.

```latex
\DeclareMathOperator{\dist}{distancia}
```

en la cabecera del documento, está disponible el comando `\distancia`

Si hemos usado el paquete *babel* con la opción *spanish* se añaden las funciones `\sen`, `\tg`, `\arcsen`  y `\arctg` además de, por defecto, acentuar algunos operadores como `\lim`, `\min` o `\max`.

## Símbolos

En las siguientes tablas están algunos de los símbolos más comunes. La lista no es completa. En CTAN se puede consultar la [*Comprehensive LaTeX Symbol List*](https://ctan.org/pkg/comprehensive), una lista exhaustiva de símbolos y los paquetes necesarios para usarlos.

### Letras griegas

| Código          | Salida          | Código                 | Salida                 | Código            | Salida            |
| --------------- | --------------- | ---------------------- | ---------------------- | ----------------- | ----------------- |
| `\alpha `       | $\alpha$        | `\beta`                | $\beta$                | `\gamma \Gamma`   | $\gamma \Gamma$   |
| `\delta \Delta` | $\delta \Delta$ | `\epsilon \varepsilon` | $\epsilon \varepsilon$ | `\zeta`           | $\zeta$           |
| `\eta`          | $\eta$          | `\theta \Theta`        | $\theta \Theta$        | `\vartheta`       | $\vartheta$       |
| `\gamma \Gamma` | $\gamma \Gamma$ | `\kappa`               | $\kappa$               | `\lambda \Lambda` | $\lambda \Lambda$ |
| `\mu`           | $\mu$           | `\nu`                  | $\nu$                  | `\xi \Xi`         | $\xi \Xi$         |
| `\tau`          | $\tau$        | `\pi \Pi`              | $\pi \Pi$              | `\rho \varrho`    | $\rho \varrho$    |
| `\sigma \Sigma` | $\sigma \Sigma$ | `\varsigma`            | $\varsigma$            | `\upsilon`        | $\upsilon$        |
| `\phi \Phi`     | $\phi \Phi$     | `\varphi`              | $\varphi$              | `\chi`            | $\chi$            |
| `\psi \Psi`     | $\psi \Psi$     | `\omega \Omega`        | $\omega \Omega$        |                   |                   |

### Relaciones binarias

|          |          |           |           |           |           |             |             |
| -------- | -------- | --------- | --------- | --------- | --------- | ----------- | ----------- |
| `\times` | $\times$ | `\div`    | $\div$    | `\cup`    | $\cup$    | `\cap`      | $\cap       |
| `\leq`   | $\leq$   | `\geq`    | $\geq$    | `\neq`    | $\neq$    | `\perp`     | $\perp$     |
| `\in`    | $\in$    | `\notin`  | $\notin$  | `\subset` | $\subset$ | `\subseteq` | $\subseteq$ |
| `\oplus` | $\oplus$ | `\otimes` | $\otimes$ | `\equiv`  | $\equiv$  | `\cong`     | $\cong$     |

### Algunos símbolos comunes

```latex
  \infty \forall \nabla \exists \partial 
  \emptyset \square \blacksquare
```

$$
  \infty \ \forall \ \nabla \ \exists \ \partial \ \emptyset \ \square \ \blacksquare
$$

## Entornos multilínea

Pueden ser de dos tipos: ajustados o alineados.

### Entornos ajustados

Hay dos: *gather* y *multline*. El primero de ellos muestra las ecuaciones
centradas una tras otra. Se usa `\\` para partir líneas en la expresión. Por ejemplo

```latex
\begin{gather}
x+y+z_1\\+\int_0^1 f(x)\, \mathrm{d}x +\cos \left( \sqrt{x} \, \right)
\end{gather}
```

$$
\begin{gather}
x+y+z_1\\ +\int_0^1 f(x)\, \mathrm{d}x +\cos \left( \sqrt{x} \, \right)
\end{gather}
$$
El segundo, multline, alinea la primera fórmula a la izquierda, la última a la
derecha y las intermedias, si las hay, las centra.

```latex
\begin{multline}
x+y+z_1 + \lim_{x \to 0} \int_{0}^{x^2} f(x)\,\mathrm{d}x +
\frac{x-1}{x+1} \\
+x+y+z+\omega+\int_0^1 f(x)\, \mathrm{d}x +\cos \left( \sqrt{x} \, \right)
\end{multline}
```

$$
\begin{multline}
x+y+z_1 + \lim_{x \to 0} \int_{0}^{x^2} f(x)\,\mathrm{d}x +
\frac{x-1}{x+1} \\
+x+y+z+\omega+\int_0^1 f(x)\, \mathrm{d}x +\cos \left( \sqrt{x} \, \right)
\end{multline}
$$

### Entornos alineados

Hay varios entornos de este tipo, dependiendo de cómo estén alineadas
las columnas. Además de `\\` para añadir una línea nueva, `&` se usa para separar las columnas.

En primer lugar, *align* muestra las columnas centradas.

```latex
\[ \left.
\begin{align}
 x+y & = 6 \\
2x-3y & = 4
\end{align}
\right\}
\]
````

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

$$
\begin{flalign}
 x+y +2 z	& = 6 	& 2u+4v & =8   \\
2x-3y & = 4 & 3u-4v  & = 10
\end{flalign}
$$

Por último, *alignat*, que tiene un comportamiento un poco distinto: hay
que decir cuántas columnas hay y añadir los espacios entre ellas
manualmente.

```latex
\[
\begin{alignat}{4}
   f(x) &= x + yz              & g(x) &= x + y + z\\
   h(x) &= xy + xz + yz \qquad & k(x) &= (x+y)(x+z)(y+z)
    \notag
\end{alignat}
\]
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
\[
\begin{alignat}{3}
            x & = x  (y+z) &  & \quad\text{(propiedad distributiva)}\\
              &= (x  y) + (x z) & &
               \quad\text{(usamos ahora que $x=0$)}\notag\\
              &= y z
\end{alignat}
\]
```

$$
\begin{alignat}{3}
            x &= x  (y+z) &
            &\quad\text{(propiedad distributiva)}\\
              &= (x  y) + (x z) & &
               \quad\text{(usamos ahora que $x=0$)}\notag\\
              & = y z
\end{alignat}
$$



### Entornos subsidiarios

align, alignat y gather tienen versiones subsidiarias que tienen que ir dentro de un entorno matemático.

```latex
\begin{aligned}[c]
 x &= 3 + \mathbf{p} + \alpha\\
      y &= 4 + \mathbf{q}\\
      z &= 5 + \mathbf{r}\\
      u &=6 + \mathbf{s}
   \end{aligned}
   \text{\quad usando\quad}
   \begin{gathered}[b]
      \mathbf{p} = 5 + a + \alpha\\
      \mathbf{q} = 12\\
      \mathbf{r} = 13\\
      \mathbf{s} = 11 + d
   \end{gathered}
```

$$
\begin{aligned}[c]
 x &= 3 + \mathbf{p} + \alpha\\
      y &= 4 + \mathbf{q}\\
      z &= 5 + \mathbf{r}\\
      u &=6 + \mathbf{s}
   \end{aligned}
   \text{\quad usando\quad}
   \begin{gathered}[b]
      \mathbf{p} = 5 + a + \alpha\\
      \mathbf{q} = 12\\
      \mathbf{r} = 13\\
      \mathbf{s} = 11 + d
   \end{gathered}
$$   

```latex
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
```

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

El entorno más flexible es *split*. Se puede usar sólo

```latex
\begin{split}
                (x_{1}x_{2}&x_{3}x_{4}x_{5}x_{6})^{2}\\
                           &+ (x_{1}x_{2}x_{3}x_{4}x_{5}
                            + x_{1}x_{3}x_{4}x_{5}x_{6}
                            + x_{1}x_{2}x_{4}x_{5}x_{6}
                            + x_{1}x_{2}x_{3}x_{5}x_{6})^{2}
\end{split}
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
\begin{align}
	\left.
  \begin{split}
             f(x) & =    (x_{1}x_{2} ) \\
		           & = x+y
	\end{split}
  \right\}
  \implies y+z
\end{align}
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

## Teoremas y demostraciones

Se pueden definir fácilmente tantos entornos como se necesiten. Con el paquete *amsthm* cargado en la cabecera tenemos disponible la orden `\newtheorem{teorema}{Teorema}` para definir nuevos entornos.

```latex
\newtheorem{nombre del entorno}[opcional subentorno de]
  {Salida del entorno}[opcional nivel de numeración]
```

Una versión común sería la siguiente: tenemos los entornos teorema, propo, lema, definición, ejemplo y observ.

```latex
\theoremstyle{theorem}
\newtheorem{teorema}{Teorema}[section]
\newtheorem{propo}[teorema]{Proposición}
\newtheorem{lema}[teorema]{Lema}
\theoremstyle{definition}
\newtheorem{definicion}[teorema]{Definición}
\newtheorem{ejemplo}[teorema]{Ejemplo}
\theoremstyle{remark}
\newtheorem{observ}{Observación}[section]
```

Los estilos *theorem*, *definition* y *remark* escriben, o no, el contenido en itálica. Pruébalos. 

Además de etiquetarlos para futuras referencias, se le puede añadir una descripción a cualquiera de ellos.

```latex
\begin{lema}[de Fermat]
  Si una función derivable tiene un extremo local en un punto 
  interior de un intervalo, la derivada en dicho punto se anula
\end{lema}
\begin{proof}
  Explicación
\end{proof}
```

### Demostraciones

El entorno *proof*, sin numerar, viene predefinido y se usa para delimitar el principio y final de una demostración. Si el final de la demostración ocurre en una ecuación o una lista se puede usar `\qedhere` para indiciar dónde debería aparecer el símbolo de final de demostración.