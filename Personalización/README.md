Personalización de un documento en LaTeX
========================================

Veremos a continuación diversos modos de personalizar un documento en LaTeX para adaptarlo a nuestras necesidades. Cubriremos los siguientes aspectos:

1. Creación de comandos y entornos propios
2. Diseño de página: cambiar tamaño de página y márgenes. Los paquetes `geometry` y `typearea`
3. Diseño de cabecera y pie de página: los paquetes `fancyhdr` y `scrlayer-scrpage`
4. Personalización de capítulos y secciones: los paquetes `titlesec` y `fancychap`
5. Selección de una tipografía: [The LaTeX font Catalogue](http://www.tug.dk/FontCatalogue/). Uso de las fuentes del sistema: [XeLaTeX](http://xetex.sourceforge.net/). Fuentes de iconos con el paquete `fontawesome`.


## Creación de órdenes y entornos propios

LaTeX posee multitud de órdenes para cada una de las tareas necesarias en la edición de textos. Sin embargo, es a veces útil definir nuestras propias órdenes o entornos para agilizar la edición de un documento. 

### Nuevas órdenes: la orden `\newcommand`
Veamos en primer un ejemplo sencillo. Para escribir en matemáticas el conjunto de los números reales usamos el comando `$\mathbb{R}$`. Si estamos editando un documento y tenemos que incluir muchas veces dicho conjunto de números es más conveniente definir un comando más corto para ello. Así, si escribimos en el *preámbulo* de nuestro documento la siguiente línea:
```tex
\newcommand{\R}{\mathbb{R}}
```

entonces tendremos a nuestra disposición la nueva orden `\R` para el conjunto de los números reales.

La sintaxis para definir un comando nuevo en LaTeX es la siguiente:

```tex
\newcommand{\nuevocomando}[n]{definición}
```

donde `[n]` es un parámetro opcional que indica el número `n` de *argumentos* que va a tener el nuevo comando. Si no se especifica nada el comando creado no tendrá argumentos (como en el ejemplo anterior `\R`). En el siguiente ejemplo se crea un comando que aceptará exactamente dos parámetros

```tex
\newcommand[2]{\parcial}{\frac{\partial #1}{\partial #2}}
```

nos permite escribir `\parcial{f}{x}` e imprimirá la derivada parcial de la función `f` con respecto a la variable `x`. Observemos que los identificadores `#1` y `#2` se sustituyen en la definición del comando por el primer y segundo argumento proporcionado.

La única precaución que tenemos que tener es que el comando que estamos definiendo no puede existir, en cuyo caso LaTeX nos dará un error. Si lo que queremos es realmente cambiar un comando ya existente deberemos usar la orden `\renewcommand` cuya sintaxis es idéntica a `\newcommand`.

## Entornos: la orden `\newenvironment`

Para definir un entorno nuevo usaremos la orden `\newenvironment` cuya sintaxis es la siguiente:

```tex
\newenvironment{nombre}[n]{inicio}{fin}
```

donde `[n]` es un parámetro opcional que indica el número `n` de argumentos que va a aceptar el entorno. Una vez definido lo usaremos de la forma habitual:

```tex
\begin{nombre}
Texto
\end{nombre}
```

Al igual que ocurría con la definición de un comando, la única precaución que tenemos que tener es que el entorno que estamos definiendo no puede existir, en cuyo caso LaTeX nos dará un error. Si lo que queremos es realmente cambiar un entorno ya existente deberemos usar la orden `\renewenvironment` cuya sintaxis es idéntica a `\newenvironment`.

TODO: hablar del espacio en los entornos con \ignorespace (ver lshort).

En el archivo [`comandosyentornos.tex`](comandosyentornos.tex) podemos ver varios ejemplos diferentes del uso de estos dos tipos de órdenes.

## Diseño de página

Al inicio de cualquier documento en LaTeX se ha de indicar el tipo (o la clase) del mismo mediante la orden `\documentclass` (ver la sección [Tipos de documento](Tipos de documento) para más información). Cada tipo de documento define sus propios márgenes (superior, inferior y laterales), suele reservar un área para las notas al margen y suele fijar, normalmente mediante una opción indicada en el comando `\documentclass`, el tamaño de papel en el que se imprimirá el documento. En la siguiente imagen podemos ver dibujadas las diferentes secciones en las que es dividida una página 

![Diseño de página extraído de "The not so short introduction to LaTeX2e"](img/page-design.png)

Para mostrar dicho esquema basta cargar el paquete `showframe`. LaTeX permite cambiar las medidas de cada uno de dichos elementos pero no es aconsejable aventurarse a ello salvo que sepamos algo sobre las reglas de maquetación de página.

Para personalizar nuestro documento, en lugar de cambiar manualmente la anchura de los márgenes, texto, altura de la cabecera, etc, cargaremos un paquete específico para ello. Los dos paquetes más habituales son los siguientes:
- [`geometry`](https://www.ctan.org/pkg/geometry): permite modificar los márgenes de un documento de forma muy sencilla. Por ejemplo, supongamos que tenemos que crear un documento con las siguientes especificaciones: *el tamaño del papel será un a4. El texto debe tener 16.5cm de anchura por 22cm de altura. El margen superior debe ser de 3cm y el margen izquierdo 2.3cm. El pie de página debe situarse bajo el área reservada para el texto*. Para conseguir dicho documento basta escribir:

```tex
\documentclass[a4paper]{article}
\usepackage[total={16.5cm, 22cm},
            top=3cm, left=2.3cm, includefoot]{geometry}
```

donde por supuesto podemos cambiar `article` por la clase de documento que deseemos.

- `typearea`: El paquete `geometry`
