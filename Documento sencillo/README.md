## Estructura de un documento LaTeX.

La estructura de un documento en LaTeX es la siguiente

```latex
\documentclass{clase}
...
\begin{document}
...
\end{document}
```

donde *clase* es un tipo de documento válido de LaTeX (ver [Tipos de documento](../Tipos de documento/about.qmd)), p.e. `article`.

El documento se divide en dos partes:

- el *encabezamiento* o *preámbulo*: todas las declaraciones contenidas entre `\documentclass`{.latex} y `\begin{document}`{.latex}.
- *cuerpo*: el texto contenido entre `\begin{document}`{.latex} y `\end{document}`{.latex}.

Cualquier contenido a continuación de `\end{document}`{.latex} es ignorado.

### Comandos, entornos y *bloques*

LaTeX es un *lenguaje de programación* y cualquier *orden* o *comando* comienza siempre con el símbolo `\` seguido de una palabra (donde se distinguen mayúsculas de minúsculas). La sintaxis habitual de un comando es:

```latex
\nombrecomando[opciones]{argumentos}
```

LaTeX proporciona también los *entornos*:

```latex
\begin{nombreEntorno}
contenido
\end{nombreEntorno}
```

que afectan a todo el *contenido*.

Finalmente, LaTeX también permite delimitar *bloques* mediante
```latex
{
bloque
}
```
Por defecto, el interior de un *entorno* tiene la categoría de bloque.

Existen comandos especiales que no llevan argumento y afectan a todo el bloque (o el entorno) donde son invocados. Ver ejemplos en la sección [Tipos de letra](#tipos-de-letra).

Además, algunos caracteres tienen una utilidad especial y su uso está reservado:

| Símbolo | Uso                                   | Comando LaTeX    |
| ------- | ------------------------------------- | ---------------- |
| #       | Argumento de un macro                 | `\#`             |
| $       | Iniciar o terminar un modo matemático | `\$`             |
| %       | Comienzo de un comentario             | `\%`             |
| ^       | Superíndice en modo matemático        | `\^{} `          |
| &       | Alineación en tablas o matrices       | `\&`             |
| _       | Subíndice en modo matemático          | `\_`             |
| { }     | Delimitadores de argumentos o bloques | `\{`, `\}`       |
| ~       | Espacio no separable                  | `\~{}`           |
| \       | Carácter de escape para comandos      | `\textbackslash` |

Estos símbolos tienen funciones especiales en LaTeX y deben utilizarse con un backslash (`\`) para ser impresos literalmente en el documento.

## Encabezamiento o preámbulo

El preámbulo se compone de todas las *declaraciones* y *paquetes* que incluyamos entre `\documentclass`{.latex} y `\begin{document}`{.latex}.

LaTeX es **modular**: su comportamiento y características pueden ser modificados o ampliados a través del uso de *paquetes*.

Un **paquete** es un *conjunto de instrucciones* de LaTeX diseñado para resolver un problema concreto del documento.

Para cargar un paquete escribiremos el siguiente *comando* en el preámbulo del documento:

```latex
\usepackage[opciones]{paquete}
```

Existen multitud de paquetes que cubren la mayoría de las necesidades del usuario: aspecto del documento, manejo de índice, glosario, referencias, idioma, hipervínculos,... Buscar en [CTAN](https://www.ctan.org).

Si tienes algún problema o quieres hacer algo específico en LaTeX seguramente exista un paquete que lo resuelva.

## Ejemplo de un documento

A continuación presentamos nuestro primer documento de LaTeX

```latex
\documentclass{article}

% Indicamos que el documento va a escribirse en castellano
\usepackage[spanish]{babel}

% Cargamos un paquete para poder incluir gráficos
\usepackage{graphicx}

% Activamos los hipervínculos del documento
\usepackage[hidelinks]{hyperref}

% Añadimos la información sobre título autoría 
\title{Taller de \LaTeX{} para alumnos del Grado en Matemáticas}
\author{Los asistentes a dicho curso}
\date{\today}

\begin{document}
% Imprime la información del título proporcionada antes
\maketitle

Cuerpo del documento. Los       espacios en        blanco  y 
saltos de línea      no cuentan. 


Una o más líneas en blanco comienzan un nuevo párrafo.
una línea en blanco. 

También podemos escribir fórmulas en *línea* con el texto: $a^2+b^2=c^2$; o en *bloque*:
\[
f(x)=\cos(x)+\frac{1}{x}
\]
\end{document}
```

## Generar el documento: proceso de *compilación*

Como hemos indicado anteriormente, LaTeX es un lenguaje de programación cuya *salida* no es un programa de ordenador, sino un documento (generalmente en PDF). Una vez escrito el *código* de nuestro documento en un fichero `documento.tex` deberemos *procesarlo* mediante LaTeX (generalmente mediante `pdfLaTeX` o alguna de sus variantes [`XeLaTeX`](https://xetex.sourceforge.net), [`LuaLaTeX`](https://www.luatex.org),...) para obtener el documento.

En dicho proceso puede haber *errores* que deberemos subsanar y se generan una serie de ficheros auxiliares que, una vez terminado el proceso, no son necesarios y podemos borrar. Entre estos ficheros se encuentran:

- `.log`: Mensajes del procesador. Contiene los errores, en caso de haberlos, y suele ser mostrado en el editor.
- `.aux`: Contiene información sobre las referencias, la bibliografía, el índice, etc. para generar las referencias cruzadas y los enlaces en el documento.
- `.toc`, `.lof`, `.lot`: Información relativa a índices, lista de figuras y lista de tablas.
- `.bbl`,  `.blg`, `.bst`: Ficheros relacionados con la bibliografía.

## Título, resumen y tabla de contenidos

Según la [clase de documento](../Tipos de documento/about.qmd), estarán disponibles unas opciones y otras para indicar los datos de título, autoría, resumen, ... del documento.

### Título

El título y datos de autores se visualiza con `\maketitle`{.latex} y se *declara* (en la mayoría de clases de documento) mediante los comandos `\author`{.latex}, `\title`{.latex} y `\date`{.latex}.

### Resumen

```latex
\begin{abstract}
Esto es una prueba de cómo hacer algunas cosas en \LaTeX.
\end{abstract}
```

### Tabla de contenidos

Podemos añadir una tabla de contenidos con `\tableofcontents`{.latex}

## Elementos del texto

### Líneas y párrafos

La unida básica de estructura es el párrafo que se delimita por al menos una línea vacía antes y después de él.

- Uno o más espacios son tratados como un espacio.
- También se trata como un espacio el salto de línea.
- Una o varias líneas en blanco separan los párrafos. El comando `\par`{.latex} tiene el mismo efecto.
- LaTeX, por defecto, *sangra* el texto al comienzo de cada párrafo. Esto puede evitarse usando el comando `\noindent`{.latex} al inicio de la línea.
- `\linebreak`{.latex} o `\\`{.latex} inicia una nueva línea sin completar la línea en curso.
- `\newpage` inicia una nueva página sin completar la página en curso.
- `\pagebreak`{.latex} fuerza un salto de página.

Los párrafos se pueden alinear a la izquierda (entorno `flushleft`), derecha (entorno `flushright`) o centrados (entorno `center`).

### Secciones

Podemos organizar un documento jerárquicamente creando diferentes *secciones*  con el comando `\section`{.latex}. Éstas pueden contener subsecciones: `\subsection`{.latex}, y subsubsecciones. Finalmente, tenemos párrafos, `\paragraph`{.latex}, y subpárrafos

| Comando          | Nivel |
| ---------------- | :---: |
| `\part`          |  -1   |
| `\chapter`       |   0   |
| `\section`       |   1   |
| `\subsection`    |   2   |
| `\subsubsection` |   3   |
| `\paragraph`     |   4   |
| `\subparagraph`  |   5   |


Observaciones:
- Salvo que el documento que estemos escribiendo sea muy técnico no es recomendable usar más de tres niveles de jerarquía (p.e. `\chapter`{.latex}, `\section`{.latex} y `\subsection`{.latex} en un libro o bien `\section`{.latex}, `\subsection`{.latex} y `\subsubsection` en un artículo). No obstante, LaTeX nos proporciona estos 7 niveles de jerarquía.
- Los niveles `\paragraph`{.latex} y `subparagraph`{.latex} difieren de `\section`{.latex} `\subsection`{.latex} y `\subsubsection`{.latex} en que no comienzan una nueva línea. El nivel `\part`{.latex} comienza una nueva página en las clases `book` y `report` pero no en la clase `article`.
- Si cambios de clase, estos comandos podrían no estar disponibles o bien cambiar su estilo.
- El comando `\chapter`{.latex} únicamente está disponible en la clase `book` y siempre comienza una nueva página.

Véase <http://en.wikibooks.org/wiki/LaTeX/Document_Structure>

### Listas

Hay listas numeradas y sin numerar. Se pueden anidar, y el tipo de numeración cambia con la profundidad de anidamiento

```latex
\begin{enumerate}
\item Aquellas que van enumeradas.
    \begin{enumerate}
    \item \ldots que además se pueden anidar.
    \end{enumerate}

\item Aquellas sin enumerar:
\begin{itemize}
\item[$\diamond$] damos varios apartados,
\begin{itemize}
\item y podemos también anidar.
\end{itemize}
\end{itemize}
\end{enumerate}
```

--------------------------------------------------------------------------------

## Tablas

Las tablas que presentamos aquí son muy sencillas, se pueden además unir celdas o separarlas

```latex
\begin{tabular}{lcr}
1 & 2 & 3 \\
Pepe & Juan & Manuel
\end{tabular}
```

O bien con bordes

```latex
\begin{tabular}{l||c|c|c|} \hline
Posición & 1 & 2 & 3 \\ \hline \hline
Nombre & Pepe & Juan & Manuel\\ \hline
\end{tabular}
```

--------------------------------------------------------------------------------

## Tipos de letra

Tenemos varios tipos de letra y tamaños básicos

| Comando   | Tipo                             |
| --------- | -------------------------------- |
| `\textbf` | **negrita**                      |
| `\textit` | _itálica_                        |
| `\textsl` | inclinada                        |
| `\texttt` | ancho fijo (máquina de escribir) |
| `\textsc` | versalitas (mayúsculas pequeñas) |

... o bien podemos `\emph{enfatizar}` una `\textit{parte del texto \emph{dentro} de otro}`

En la siguiente tabla se recogen todos los comando para modificar el aspecto (familia, grosor, perfil y tamaño) de la tipografía. Podemos combinar un comando de cada columna. En las tres primeras columnas tenemos dos comandos para lo mismo: el primero de ellos (p.e. `\textbf` para negrita) cambia la apariencia a su argumento (p.e. `\textbf{texto en negrita}`) mientras que el segundo (p.e. `\bfseries`) afecta a todo un *bloque* (p.e. `{\bfseries texto en negrita}`).

| Familia     | Estilo            |                  | Tamaño          |
| ----------- | ----------------- | ---------------- | --------------- |
|             | Grosor (*series*) | Perfil (*shape*) |                 |
| Serif       | Normal            | Recto            | `\tiny`         |
| `\textrm`   | `\textmd`         | `\textup`        | `\scriptsize`   |
| `\rmfamily` | `\mdseries`       | `\upshape`       | `\footnotesize` |
|             | Negrita           | Cursiva          | `\small`        |
|             | `\textbf`         | `\textit`        | `\normalsize`   |
|             | `\bfseries`       | `\itshape`       | `\large`        |
| Sans-serif  |                   | Inclinada        | `\Large`        |
| `\textsf`   |                   | `\textsl`        | `\LARGE`        |
| `\sffamily` |                   | `\slshape`       | `\huge`         |
| Mono        |                   | Versalitas       | `\Huge`         |
| `\texttt`   |                   | `\textsc`        |                 |
| `\ttfamily` |                   | `\scshape`       |                 |

--------------------------------------------------------------------------------

## Fórmulas

Existen dos tipos de fórmulas

- En línea como por ejemplo `$x^2+1$` que produce $x^2+1$
- En modo ventana o centrado: `\[x^2+1\]` que se ve como

$$x^2+1$$

Los delimitadores `$..$` se pueden substituir por `\(..\)`.

Antiguamente se usaba la sintaxis `$$ fórmula $$` para fórmulas centradas pero actualmente es preferible usar siempre `\[fórmula\]` (de hecho esta última ofrece más funcionalidades como `\qedhere`{.latex})

--------------------------------------------------------------------------------

## Creación de comandos y entornos

Como en cualquier lenguaje de programación, LaTeX nos permite extender su funcionalidad definiendo nuestros propios comandos y entornos. Esto se hace siempre en el *preámbulo* del documento (antes de `\begin{document}`).

La sintaxis básica para ello es la siguiente:

### Comandos
```latex
\newcommand{\nombre}[n]{definición}
```
donde `n` es el número de argumentos que va a tener nuestro comando y `definición` es su definición donde cada argumento se referencia mediante `#x`, donde `x` es el lugar que ocupa el argumento (número natural). 

Por ejemplo, mediante la definición
```latex
\newcommand{\parcial}[2]{\frac{\partial #1}{\partial #2}}
```
podemos usar `\parcial{f}{x}`{.latex} para escribir
$$
\frac{\partial f}{\partial x}
$$

Los comandos pueden definirse sin ningún argumento, por ejemplo:
```latex
\newcommand{\R}{\mathbb{R}} % números reales
```

Si queremos **re**definir un comando existente deberemos usar el comando `\renewcommand`{.latex} cuya sintaxis es la misma que `\newcommand`. **No es aconsejable redefinir comandos existentes**.

### Entornos
La sintaxis básica para definir un entorno es la siguiente:
```latex
\newenvironment{nombreEntorno}[n]{inicio}{fin}
```
donde `n` es el número de argumentos que va a tener el entorno.

Por ejemplo, para definir un entorno muy básico para ejercicios podemos escribir en el preámbulo de nuestro documento:
```latex
\newenvironment{ejercicio}[1]{\textbf{Ejercicio número #1}}{\qed}
```
y usarlo mediante
```latex
\begin{ejercicio}{1}
Escribe esto con otras palabras.
\end{ejercicio}
```
De esta forma escribimos el contador de ejercicio de forma manual

Para automatizarlo, podemos definir nuestro propio [contador](https://es.overleaf.com/learn/latex/Counters):

```latex
\newcounter{ejer_num}
\setcounter{ejer_num}{1}
\newenvironment{ejer}{
  \textbf{Ejercicio \arabic{ejer_num}: \stepcounter{ejer_num}}
  \begin{itshape}
  }
  {\end{itshape}
}
```

--------------------------------------------------------------------------------

### Entornos predefinidos

Muchos paquetes definen sus propios entornos para tareas concretas o proporcionan mecanismos para crear entornos nuevos. El paquete [`amsthm`](https://ctan.org/pkg/amsthm) permite crear entornos para enunciados matemáticos (teoremas, proposiciones,...).

Podemos numerar con la sección

```latex
\newtheorem{teorema}{Teorema}[section]
```

Y otros entornos con el contador que acabamos de crear

```latex
\newtheorem{nota}[teorema]{Aclaración}
```

```latex
\begin{teorema}\label{tonto}
Las ranas son verdes.
\end{teorema}
\begin{proof}
Así lo decía Aristóteles, y nosotros no vamos a llevarle la contraria.
\end{proof}
```

Luego podremos referenciar a este teorema como Teorema `\ref{tonto}`.

--------------------------------------------------------------------------------

## Referencias cruzadas

LaTeX permite *etiquetar* cualquier elemento en el texto (un párrafo, una figura, una ecuación, un elemento de una lista, un entorno,...) y luego *hacer referencia* a él (para ello habitualmente dicho elemento deberá tener un número asociado como ocurre habitualmente). 

Para ello tenemos que hacer dos pasos:

1. Etiquetar el elemento incluyendo el comando `\label{etiqueta}`{.latex} dentro del mismo (habitualente al inicio). La **etiqueta** debe ser una *cadena de texto* única (sin acentos ni caracteres especiales aunque podemos incluir guiones `-` y `:`)
2. Insertar una referencia a dicho elemento mediante el comando `\ref{etiqueta}`{.latex}. También podemos imprimir la página donde se ecuentra el elemento etiquetado mediante el comando `\pageref{etiqueta}`{.latex}.



## Figuras e imágenes

El paquete `graphicx` nos permite insertar gráficos con el comando `\includegraphics`

```latex
\includegraphics[width=2.5cm]{imagen.jpg}
```

Podemos también crear una figura con esa imágen

```latex
\begin{figure}
\includegraphics[width=3cm]{superficie.jpg}  
\caption{Superficie diferenciable en el espacio euclídeo.}
\label{fig:superficie-diferenciable}
\end{figure}

En la Figura~\ref{fig:superficie-diferenciable}
```

Observa el uso del carácter `~` entre el texto "Figura" y la referencia: esto hace que el número de referencia siempre vaya acompañado del texto y no permite que LaTeX los separe (por ejemplo, al hacer un salto de línea). Es una buena práctica incluirlo siempre.

El paquete [`hyperref`](https://ctan.org/pkg/hyperref) amplia la funcionalidad de las referencias cruzadas (por ejemplo añadiendo un enlace en el pdf para *saltar* entre la referencia y elemento de forma sencilla) y define un nuevo comando `\autoref`{.latex} que imprime automáticamente la descripción de la referencia dependiendo de su tipo (es decir, antepone automáticamente el texto "Figura" al hacer `\autoref{fig:superficie-diferenciable}`{.latex} puesto que detecta automáticamente que dicha etiqueta está dentro de un entorno `figure`).

--------------------------------------------------------------------------------

## Indentación

Ya hemos indicado que podemos cambiar la disposición del texto alineándolo a la izquierda (con el entorno `flushleft`), a la derecha (con el entorno `flushright`) o centrados (entorno `center`). Por ejemplo:

```latex
\begin{center}
Texto a centrar.

Puede ser más de un párrafo.
\end{center}
```

También podemos desplazar el texto horizontal (con los comandos `\hspace{longitud}`{.latex}, `\hfill`{.latex} o verticalmente (`\vspace{longitud}`{.latex} y `\vfill`{.latex}).

## La bibliografía

### Incluir la bibliografía de forma *manual*: entorno `thebibliography`

Para insertar manualmente la bibliografía el entorno `thebibliography`, cuya sintaxis es la siguiente:

```latex
\begin{thebibliography}{n}
    \bibitem[identificador]{etiqueta} Elemento bibliográfico (libro, artículo,...)
\end{thebibliography}
```

donde `n` es el *número máximo* de elementos de la lista y únicamente se usa como referencia para el espacio entre el identificador del elemento bibliográfico y su descripción.

El argumento opcional `[identificador]` se usa para indicar de forma manual qué identificador queremos para el elemento bibliográfico, es decir, de qué forma se va a imprimir en el documento una referencia a dicho elemento.

Para hacer referencia a un elemento de la bibliografía usaremos el comando `\cite{etiqueta}`.

Por ejemplo:

```latex
\begin{thebibliography}{9}
\bibitem{lshort} Tobias Oetiker, Hubert Partl, Irene Hyna and Elisabeth Schlegl,
  The not so short introduction to \LaTeX2e,
    \href{http://www.ctan.org/tex-archive/info/lshort/english/lshort.pdf}{ctan.org}.
\end{thebibliography}
```

y una referencia a dicho elemento sería: *recomendamos la lectura de `\cite{lshort}`*.

Las principales desventajas de este método son las siguientes:

1. Los elementos bibliográficos debemos incluirlos manualmente dentro de `thebibliography`.

2. Si el estilo bibliográfico de nuestro documento exige que la bibliografía esté, por ejemplo, ordenada alfabéticamente por autores deberemos reordenar manualmente la lista nosotros mismos.

3. Si queremos cambiar el *estilo* del elemento bibliográfico (el orden en que parecen los datos de autor/título/revista/año y su estilo tipográfico cursiva/negrita) deberemos hacerlo manualmente para cada una de las entradas.

En la sección [Bibliografía](../Bibliografia/about.qmd) se propone una forma óptima de *gestionar* la bibliografía de un documento mediante la creación de *bases de datos* de referencias bibliográficas (ficheros `bibtex`, de forma manual o usando un gestor) y la inserción automática de la bibliografía en un documento LaTeX (mediante `bibtex` o `biblatex`).

## Más información

Un resumen de todo lo dicho y más lo podéis encontrar en el [chuletario](http://osl.ugr.es/CTAN/info/latexcheat/latexcheat-esmx/latexsheet-esmx.pdf) de LaTeX.

En vuestra instalación de LaTeX tenéis toda la documentación necesaria, e incluso el "[lshort.pdf](http://osl.ugr.es/CTAN/info/lshort/spanish/lshort-a4.pdf)" o cómo aprender LaTeX en 147 minutos.

[Overleaf](https://www.overleaf.com/learn/latex/Learn_LaTeX_in_30_minutes) ofrece un excelente tutorial de inicio.
