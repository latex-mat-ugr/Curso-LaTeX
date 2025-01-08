# Tipos de documento

Todo documento de LaTeX comienza con la declaración de la *clase* o *tipo de documento* mediante el comando `\documentclass`. Existen [multitud de clases](https://ctan.org/topic/class) distintas según el propósito del documento. Describiremos aquí algunas de las más utilizadas.

## Tipos básicos de LaTeX
Las clases por defecto más usadas en LaTeX son:

- `article`: Para artículos en revistas científicas, informes,...
- `report`: para pequeños libros, informes largos,...
- `book`: para libros

Los documentos se estructuran en diferentes secciones. La clase `article` permite los siguientes comandos de estructura (de mayor a menor nivel):

1. `\section{}`
1. `\subsection{}`
1. `\subsubsection{}`
1. `\paragraph{}`
1. `\subparagraph{}`

Aunque las dos últimas no son habitualmente usadas. Además, la clase `report` y la clase `book` permiten usar el comando `\chapter{}` para dividir el documento en capítulos. Por defecto estos comandos tienen usan una numeración jerárquica de mayor a menor nivel pero tienen una versión *con asterisco* para producir un encabezado (de capítulo, sección, subsección,...) sin numerar. Por ejemplo `\section*{Introducción}` producirá una nueva sección sin numeración.

Existe además una opción de estructura adicional que no afectan a la numeración: `\part{}`, usada para dividir cualquier documento en partes.

Evidentemente dichos tipos de documento pueden no ser suficientes para nuestras necesidades. Por ejemplo, para crear transparencias se usa un tipo de clase diferente `beamer`. 

## Transparencias: la clase *beamer*
La clase `beamer` es tan extensa y específica que precisa de una explicación detallada a parte. Consulta la carpeta [Beamer](Beamer) para más detalles.

## El paquete [KOMA-Script](https://www.ctan.org/pkg/koma-script)
Este paquete proporciona un reemplazo moderno para las clases `article`, `report` y `book` cuidando especialmente la tipografía y la versatilidad. Añade además una clase `letter`. Además también ofrece:
- Un [paquete para calcular el diseño de página](https://www.ctan.org/pkg/typearea) 
- paquetes para cambiar y definir fácilmente estilos de página

La [documentación](https://osl.ugr.es/CTAN/macros/latex/contrib/koma-script/doc/scrguien.pdf) es extensa y a veces muy técnica pero merece la pena usar este tipo de documentos por las siguientes razones:
- Todos los elementos del mismo pueden personalizarse de forma sencilla.
- Permite cambiar varios parámetros del diseño e página y el paquete se encarga de recalcular los tamaños del texto y márgenes siguiendo las prácticas tipográficas más adecuadas.


## Miscelánea
En la sección precedente hemos introducido las clases de documento del paquete `KOMA-script` por incluir tipos de documento que cubren la mayoría de necesidades de un usuario medio. Sin embargo, existen multitud de clases de documento a disposición del usuario. En [CTAN](https://ctan.org/topic/class) se puede ver una lista de paquetes que proporcionan clases de documento alternativas. En esta sección vamos a mencionar algunas de ellas por su calidad y personalización.

### La clase `memoir`
La [clase memoir](https://www.ctan.org/pkg/memoir?lang=en) es otra clase de documento popular entre los usuarios de LaTeX con un gran cantidad de opciones de personalización. Su completo [manual](http://mirrors.nxthost.com/ctan/macros/latex/contrib/memoir/memman.pdf) nos permitirá sacarle todo el partido a la misma.

### La clase Edward Tufte
El proyecto [Tufte-LaTeX](https://tufte-latex.github.io/tufte-latex/) ha creado dos clases de documento inspiradas en los trabajos de de [Edward Tufte](https://www.edwardtufte.com/tufte/) profesor emérito de la universidad de Yale autor de cuatro influyentes libros sobre visualización de datos. 

Se trata de dos [clases de documento](https://ctan.org/pkg/tufte-latex) para LaTeX [`handout`](http://mirrors.nxthost.com/ctan/macros/latex/contrib/tufte-latex/sample-handout.pdf) y [`book`](http://mirrors.nxthost.com/ctan/macros/latex/contrib/tufte-latex/sample-book.pdf) cuya característica principal es una cuidada tipografía y amplios márgenes para la inclusión de abundantes notas, referencias e imágenes.

Podemos recrear hasta cierto punto la clase `tufte-handout` personalizando la clase `scrartcl`. La [plantilla-KOMA-margen-amplio](plantilla-KOMA-margen-amplio.tex) ha usado la clase `scrartcl` cambiando el tipo de fuente, el diseño de página (para permitir un amplio margen) y el paquete `sidenote` (con ciertas modificaciones) para incluir notas y figuras al margen.

### Las clases definidas por la American Mathematical Society
La American Mathematical Society (AMS), responsable de los populares paquetes para matemáticas [`amsmath`](https://www.ctan.org/pkg/amsmath), y [`amsthm`](https://www.ctan.org/pkg/amsthm), creó [tres clases de documento](https://www.ctan.org/pkg/amscls) para su uso en LaTeX que siguen la guía de estilo de sus publicaciones:
- [`amsart`](https://www.ctan.org/pkg/amsart) para artículos de investigación.
- [`amsbook`](https://www.ctan.org/pkg/amsbook) para la creación de libros. 
- [`amsproc`](https://www.ctan.org/pkg/amsproc) para actas de un congreso.

Si nos gusta el estilo de dichos documentos podemos usarlos sin problemas para nuestros propios documentos.
