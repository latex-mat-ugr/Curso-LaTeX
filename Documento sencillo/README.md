## Estructura de un documento LaTeX.

La estructura de un documento en LaTeX es la siguiente

```latex
\documentclass{clase}

\begin{document}
...
\end{document}
```
donde *clase* es un tipo de documento válido de LaTeX (ver [Tipos de documento](../Tipos de documento/about.qmd)), p.e. `article`. 

El documento se divide en dos partes: 

- el *encabezamiento* o *preámbulo*: todas las declaraciones contenidas entre `\documentclass`{.latex} y `\begin{document}`{.latex}.
- *cuerpo*: el texto contenido entre `\begin{document}`{.latex} y `\end{document}`{.latex}.

Cualquier contenido a continuación de `\end{document}`{.latex} es ignorado.

### Comandos y entorno
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

Además, algunos caracteres tienen una utilidad especial y su uso está reservado:

| Símbolo | Uso                                            | Comando LaTeX |
|---------|------------------------------------------------|---------------|
| #       | Argumento de un macro                          | `\#`          |
| $       | Iniciar o terminar un modo matemático          | `\$`          |
| %       | Comienzo de un comentario                      | `\%`          |
| ^       | Superíndice en modo matemático                 | `\^{} `       |
| &       | Alineación en tablas o matrices                | `\&`          |
| _       | Subíndice en modo matemático                   | `\_`          |
| { }     | Delimitadores de argumentos o bloques          | `\{`, `\}`    |
| ~       | Espacio no separable                           | `\~{}`        |
| \       | Carácter de escape para comandos               | `\textbackslash` |

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
\title{Taller de \LaTeX\ para alumnos del Grado en Matemáticas}
\author{Los asistentes a dicho curso}
\date{\today}

\begin{document}
% Imprime la información del título proporcionada antes
\maketitle

Cuerpo del documento. Los       espacios en        blanco  y 
saltos de línea      no cuentan. 

Si queremos empezar un párrafo nuevo sólo tenemos que dejar 
una línea en blanco. 

También podemos escribir fórmulas
\[
f(x)=\cos(x)+\frac{1}{x}
\]
\end{document}
```

## Generar el documento: proceso de *compilación*

Como hemos indicado anteriormente, LaTeX es un lenguaje de programación cuya *salida* no es un programa de ordenador sino un documento (generalmente en `pdf`). Una vez escrito el *código* de nuestro documento en un fichero `documento.tex` deberemos *procesarlo* mediante LaTeX (generalmente mediante `pdfLaTeX` o alguna de sus variantes [`XeLaTeX`](https://xetex.sourceforge.net), [`LuaLaTeX`](https://www.luatex.org),...) para obtener el documento. 

En dicho proceso puede haber *errores* que debermos subsanar y se generan una serie de ficheros auxiliares que, una vez terminado el proceso, no son necesarios y podemos borrar. Entre estos ficheros se encuentran:

  - `.log`: Mensajes del procesador. Contiene los errores, en caso de haberlos, y suele ser mostrado en el editor.
  - `.aux`: Contiene información sobre las referencias, la bibliografía, el índice, etc. para generar las referencias cruzadas y los enlaces en el documento.
  - `.toc`, `.lof`, `.lot`: Información relativa a índices, lista de figuras y lista de tablas.
  - `.bbl`,  `.blg`, `.bst`: Ficheros relacionados con la bibliografía.



## Título, resumen y tabla de contenidos

Según la [clase de documento](../Tipos de documento/about.qmd), estarán disponibles unas opciones y otras para indicar los datos de título, autoría, resumen,... del documento.

### Título

El título y datos de autores se visualiza con `\maketitle`{.latex} y se *declara* (en la mayoría de clases de documento) mediante los comandos `\author`{.latex} y  `\title`{.latex}.

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
- `\newline`{.latex} o `\\`{.latex} inicia una nueva línea sin completar la línea en curso.
- `\linebreak[opcion]`{.latex} inicia una nueva línea justificando la línea en curso.
- `\newpage` inicia una nueva página sin completar la página en curso.
- `\pagebreak`{.latex} fuerza un salto de página.

Los párrafos se pueden alinear a la izquierda (entorno `flushleft`), derecha (entorno `flushright`) o centrados (entorno `center`).


### Secciones

Podemos crear seccions (en un libro también capítulos y partes) con el comando `\section`{.latex}. Éstas pueden contener subsecciones: `\subsection`{.latex}, y subsubseciones. Finalmente tenemos párrafos, `\paragraph`{.latex}, y subpárrafos

Comando          | Nivel
---------------- | :---:
`\part`          |  -1
`\chapter`       |   0
`\section`       |   1
`\subsection`    |   2
`\subsubsection` |   3
`\paragraph`     |   4
`\subparagraph`  |   5

Véase <http://en.wikibooks.org/wiki/LaTeX/Document_Structure>


### Listas

Hay listas numeradas y sin numerar. Se pueden anidar, y el tipo de numeración cambia con la profundicad de anidamiento

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

Comando   | Tipo
--------- | -------------------
`\textbf` | **negrita**
`\textit` | _itálica_
`\textsl` | helvética
`\texttt` | courier
`\textsc` | pequeñas Mayúsculas

... o bien podemos `\emph{enfatizar}` una `\textit{parte del texto \emph{dentro} de otro}`

En la siguiente table se recogen todos los comando para modificar el aspecto (familia, grosor, perfil y tamaño) de la tipografía. Podemos combinar un comando de cada columna. En las tres primeras columnas tenemos dos comandos para lo mismo: el primero de ellos (p.e. `\textbf` para negrita) cambia la apariencia a su argumento (p.e. `\textbf{texto en negrita}`) mientras que el segundo (p.e. `\bfseries`) afecta a todo un *bloque* (p.e. `{\bfseries texto en negrita}`).

| Familia    | Estilo                            | Tamaño                  |
|------------|---------------------------------  |-------------------------|
|            | Grosor (*series*) | Perfil (*shape*)  |                         |
| Serif      | Normal          | Recto           | `\tiny`                   |
| `\textrm`    | `\textmd`         | `\textup`         | `\scriptsize`             |
| `\rmfamily`  | `\mdseries`       | `\upshape`        | `\footnotesize`           |
|            | Negrita         | Cursiva         | `\small`                  |
|            | `\textbf`         | `\textit`         | `\normalsize`             |
|            | `\bfseries`       | `\itshape`        | `\large`                  |
| sans-serif |                 | Inclinada       | `\Large`                  |
| `\textsf`    |                 | `\textsl`         | `\LARGE`                  |
| `\sffamily`  |                 | `\slshape`        | `\huge`                   |
| Mono       |                 | Versalitas      | `\Huge`                   |
| `\texttt`    |                 | `\textsc`         |                         |
| `\ttfamily`  |                 | `\scshape`        |                         |


--------------------------------------------------------------------------------

## Fórmulas

Existen dos tipos de fórmulas

- En línea como por ejemplo `$x^2+1$` que produce $x^2+1$
- En modo ventana o centrado: `$$x^2+1$$` que se ve como

$$x^2+1$$

Los delimitadores `$..$` se pueden substituir por `\(..\)` y

```
$$..$$
```

por

```
\[..\]
```

(entre otros, de hecho este último ofrece más funcionalidades como `\qedhere`)

--------------------------------------------------------------------------------

## Entornos

```latex
\newenvironment{ejercicio}[1]{\textbf{Ejercicio número #1}}{\qed}
```

```latex
\begin{ejercicio}{1}
Escribe esto con otras palabras.
\end{ejercicio}
```

De esta forma escribimos el contador de ejercicio de forma manual

Para automatizarlo, hacemos lo siguiente

```
\newcounter{ejer_num}
\setcounter{ejer_num}{1}
\newenvironment{ejer}{
  \textbf{Ejercicio \arabic{ejer_num}: \stepcounter{ejer_num}}
  \begin{itshape}
  }
  {\end{itshape}}
```

--------------------------------------------------------------------------------

## Entornos predefinidos

Podemos numerar con la sección

```
\newtheorem{teorema}{Teorema}[section]
```

Y otros entornos con el contador que acabamos de crear

```
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

Luego podremos referenciar a este teorema como Teorema `\ref{tonto}`

--------------------------------------------------------------------------------

## Figuras e imágenes

El paquete `graphicx` nos permite insertar gráficos con el comando `\includegraphics`

```
\includegraphics[width=2.5cm]{imagen.jpg}
```

Podemos también crear una figura con esa imágen

```latex
\begin{figure}
\includegraphics[width=3cm]{imagen.jpg}  
\caption{Algo que encontré por
\href{http://www3.interscience.wiley.com/journal/13087/home/ForAuthors.html}{ahí.}
}
\label{uno}
\end{figure}
```

--------------------------------------------------------------------------------

## Indentación

Podemos escribir texto centrado con

```latex
\begin{center}
Texto a centrar.

Puede ser más de un párrafo.
\end{center}
```

Y desplazarlo a la derecha con `\hfill`

--------------------------------------------------------------------------------

## La bibliografía

Para insertar la bibliografía se usa bien `bibtex` (que veremos más adelante) o el entorno `thebibliography`

```latex
\begin{thebibliography}{10}
\bibitem{lshort} Tobias Oetiker, Hubert Partl, Irene Hyna and Elisabeth Schlegl,
  The not so short introduction to \LaTeX2e,
    \href{http://www.ctan.org/tex-archive/info/lshort/english/lshort.pdf}{ctan.org}.
\end{thebibliography}
```

--------------------------------------------------------------------------------

## Más información

Un resumen de todo lo dicho y más lo podéis encontrar en el [chuletario](http://osl.ugr.es/CTAN/info/latexcheat/latexcheat-esmx/latexsheet-esmx.pdf) de LaTeX

En vuestra instalación de LaTeX tenéis toda la documentación necesaria, e incluso el "[lshort.pdf](http://osl.ugr.es/CTAN/info/lshort/spanish/lshort-a4.pdf)" o cómo aprender LaTeX en 147 minutos

[Overleaf](https://www.overleaf.com/learn/latex/Learn_LaTeX_in_30_minutes) ofrece un excelente tutorial de inicio.
