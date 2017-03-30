# Taller de LaTeX para alumnos de Grado en Matemáticas::Libro

![fc](../Imagenes/fc.jpg)

[Pedro A. García Sánchez](http://www.ugr.es/local/pedro), <pedro@ugr.es>

***

## Estructura

Además de la estructura básica que vimos en un documento sencillo, el cuerpo de un libro se puede dividir en tres partes

`\frontmatter`

`\mainmatter`

`\backmatter`

***

## frontmatter

En esta parte pondremos el título, tabla de contenidos y prólogo

También podemos poner aquí las dedicatorias y agradecimientos (aunque estos últimos también se pueden poner en el `backmatter`)

Lás páginas en el `frontmatter` van numeradas con números romanos

```latex
\frontmatter

\maketitle

\include{inicio}

\tableofcontents
```

***

## mainmatter

En esta parte del libro las páginas se numeran con números indoarábigos

```latex
\mainmatter

\include{introduccion}

\part{Cosas varias}

\chapter{Un capítulo}
...
```

Además de `section` y `paragraph` (y sub...), tenemos partes y capítulos

***

## backmatter

Aquí colocaremos la bibliographía y los índices de contenido, de resultados...

También podemos añadir apéndices

```latex
\backmatter

\cleardoublepage
\phantomsection

\bibliography{taller}
\bibliographystyle{plain}

\cleardoublepage
\phantomsection


\printindex
```

***

## Hipervínculos

Los comandos
```latex
\cleardoublepage
\phantomsection
```
los usamos para compatibilidad con `hyperref`
