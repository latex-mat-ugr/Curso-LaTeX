# Taller de LaTeX para alumnos de Grado en Matemáticas::Transparencias

![fc](../Imagenes/fc.jpg)

[Pedro A. García Sánchez](http://www.ugr.es/local/pedro), <pedro@ugr.es>

***

## Estructura

El tipo de documento `beamer` es parecido a un artículo o libro

```latex

\documentclass{beamer}

%probad a descomentar alguna de las siguientes
%\usetheme{Goettingen}
%\usetheme{Berkeley}
%\usetheme{Boadilla}
%\usetheme{Copenhagen}

\usepackage[utf8]{inputenc}
\usepackage[spanish]{babel}

\title[Taller de \LaTeX]{Taller de \LaTeX\ AMAT}
\author[Los presentes]{Estudiantes de Grado en Matemáticas}
\institute[UGR]{Universidad de Granada}

\begin{document}

\maketitle

\section*{Introducción}

```

***

## Frames

Cada transparencia se corresponde con un cuatro o frame

```latex
\begin{frame}{Con su título}

...

\end{frame}
```

El título es opcional

***

## Itemize

En `beamer` se pueden hacer pausas cada vez que hay una lista, haciendo que cambie de color el ítem del que estemos hablando en ese momento

```latex
\begin{frame}
\begin{itemize}[<+-|alert@+>]
\item Este taller está pensado como pequeña introducción al \LaTeX

\item Intentaremos dar algunas pequeñas pinceladas sobe su uso

\item Para m\'as detalles véase la documentación de beamer.
\end{itemize}
\end{frame}
```
***

## Bloques

Dentro de una transparencia podemos usar bloques

Hay varios predefinidos

```latex
\begin{block}{Bloques}
En beamer existen varios tipos de bloques....
Y en ellos podemos escribir lo que queramos.
\end{block}

Podemos poner texto fuera de los bloques

\begin{alertblock}{Bloques de alerta}
En éstos escribimos cosas a resaltar.
\end{alertblock}

\begin{exampleblock}{Ejemplos}
Y en estos los ejemplos, por ejemplo.
\end{exampleblock}
```

Los colores y forma (bordes) cambian dependiendo del estilo seleccionado

***

## Pausas

Con el comando `\pause` podemos hacer que se muestre el texto de una transparencia hasta dicha marca

El proceso se puede repetir tantas veces como queramos

```latex

Algo nuevo

\pause

Otra cosa

\pause

Y otra cosa más
```

***

## Sobreimpresiones

A veces es útil poder mostrar variaciones de texto o formas, creando cuadros dentro de los cuadros

```latex
\begin{overprint}

\onslide<1>

Y en estos los ejemplos, por ejemplo.

\onslide<2>

Y en estos los ejemplos, por ejemplo. Ligeramente modificado.

\onslide<3>

O cualquier otra cosa.

\end{overprint}
```

***

## Bibliografía

```latex
\begin{thebibliography}{10}
\bibitem{lshort} Tobias Oetiker, Hubert Partl, Irene Hyna and Elisabeth Schlegl,
The not so short introduction to \LaTeX2e,
 \href{http://www.ctan.org/tex-archive/info/lshort/english/lshort.pdf}{ctan.org}.
\end{thebibliography}

```

El código anterior, al igual que `\maketitle`, crea una nueva transparencia conteniendo la bibliografía

***

## Recomendaciones

- No hacer demasiadas transparencias

- Cada transparencia no debe superar las 12 líneas

- El estilo debe ser sencillo para no distraer a la audiencia

- No abusar de las pausas
