# Paquetes útiles en LaTeX

Cualquier distribución trae cientos de paquetes adicionales que resuelven problemas concretos o añaden alguna nueva capacidad a LaTeX.

## Microtype

Hace pequeñas modificaciones que mejoran el aspecto como separación entre palabras o longitud de líneas. Se carga añadiendo en la cabecera

```latex
\usepackage{microtype}
```

## Hyperref

Permite añadir enlaces internos y externos.

```latex
\documentclass{article}
...
\usepackage[pdfusetitle]{hyperref}
...
\begin{document}
\section{Primera}\label{sect:etiqueta1}
...
Como se puede ver en \autoref{sect:etiqueta1} o en la Sección~\ref{sect:etiqueta1}
...
\end{document}
```

Se puede personalizar casi todo: colores de enlaces, referencias a páginas y bibliografías, etc.

## Babel

Adapta el documento al idioma que se desee.

```latex
\usepackage[spanish]{babel}
```

Se puede usar más de un idioma en un documento

```latex
\usepackage[main=english,spanish]{babel}
```

da el mismo resultado que

```latex
\usepackage[spanish,english]{babel}
```

en ambos casos, el idioma principal del documento es el inglés.

Hay varias formas de cambiar el idioma de una parte del documento:

```latex
\begin{otherlanguage}{dutch}
escribimos en holandés
\end{otherlanguage}
o un texto \foreignlanguage{english}{short} o cambiar el idioma
\selectlanguage{english}
...
```

## mathtools

Añade algunas construcciones matemáticas usuales y arregla algunos fallos de otros paquetes.

Por ejemplo, podemos usar siempre el entorno `equation` y que el compilador sólo numere las ecuaciones que se citen de forma automática.

```latex
\usepackage{mathtools}
\mathtoolsset{
    showonlyrefs=true % o false
}
```

Entre otras cosas incluye

- Símbolos que cambian de tamaño automáticamente como parénteis, flechas,...
- Manejo de etiquetas en ecuaciones,
- Algunos entornos nuevos para ecuaciones que ocupen varias líneas.


## Nag

Comprueba que no se usan algunas órdenes no recomendadas o en desuso. Sólo muestra un aviso al compilar. No cambia nada.

```latex
\usepackage{nag}
```

## Geometry

Permite indicar el tamaño del papel y modificar márgenes de forma sencilla.

```latex
\usepackage[a4aper,margin=3cm]{geometry}
```

o cada margen de forma individual

```latex
\usepackage[a4aper,leftmargin=3cm,rightmargin=1cm,topmargin=2.5cm]{geometry}
```

## Siunitx

Permite escribir unidades de la forma correcta. Cargamos el paquete

```latex
\usepackage{siunitx}
```

Escribimos las cantidades de la forma `\SI{cantidad}{unidad}`, por ejemplo

```latex
\SI{2}{\kilometer\per\second} \neq \SI{2.3}{\square\volt\cubic\lumen\per\farad}
```

La orden `\SI{}{}` está compuesta por dos que se pueden usar por separado `\num{}` y `\si{}` que escriben el número y las unidades.
