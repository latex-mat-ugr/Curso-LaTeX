# Tipos de documento

## Tipos básicos de LaTeX
Todo documento de LaTeX comienza con la declaración de la *clase* o *tipo de documento* mediante el comando `\documentclass`. Las clases por defecto más usadas en LaTeX son:

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
- Un [paquete para calcular el área de impresión](https://www.ctan.org/pkg/typearea) 
- paquetes para cambiar y definir fácilmente estilos de página

La [documentación](https://osl.ugr.es/CTAN/macros/latex/contrib/koma-script/doc/scrguien.pdf) es extensa y a veces muy técnica pero merece la pena usar este tipo de documentos por las siguientes razones:


La clase [memoir](https://ctan.org/pkg/memoir)

## Miscelánea

### La clase Eduard Tufte

### Las clases definidas por la American Mathematical Society
