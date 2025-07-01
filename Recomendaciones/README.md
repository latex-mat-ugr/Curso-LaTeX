A continuación damos una lista de recomendaciones a seguir al elaborar un documento científico. La lista de recomendaciones está dividida en diferentes categorías para que sea más sencillo buscar un problema o caso de uso concreto. Para elaborar la lista se han tenido en cuenta tanto nuestra experiencia personal así como el documento [Consejos de estilo para un texto con contenido matemático y su código LaTeX](https://anamat.unizar.es/latex/Sesion5.pdf). 

Es conveniente consultar también la guía [Ortotipografía y notaciones matemáticas](https://www.texnia.com/archive/ortomatem.pdf) donde se analiza de forma más exhaustiva el uso de los símbolos matemáticos en un texto.


## Estructura

Consultar la sección [Tipos de documento](../Tipos de documento/about.qmd) para más información.

- Cualquier documento, especialmente si tiene cierta longitud, debe estar jerárquicamente estructurado siguiendo una lógica. Los distintos niveles jerárquicos disponibles en LaTeX son, por orden de mayor a menor nivel de jerarquía: `\part`, `\chapter`, `\section`, `\subsection`, `\subsubsection` y `paragraph`. ¡Sí, el párrafo es el último nivel de jerarquía! Para indicar comienzo de un párrafo no es necesario usar ningún comando (aunque existe el entorno `paragraph`) sino simplemente dejar una línea en blanco al final del mismo (no importa el número de líneas que dejemos). Es una mala práctica usar el comando `\\` para iniciar un párrafo puesto que su uso es únicamente para comenzar una nueva línea.
- Es una mala práctica incluir un capítulo sin secciones (excepto para la introducción del documento, que jerárquicamente suele corresponder a un capítulo).

## Redacción

Consultar la sección [Tipos de documento](../Matematicas/about.qmd) para más información.

- Aunque se trate de un documento matemático, debe de estar bien escrito con una buena puntuación y sin faltas de ortografía o gramaticales. Es recomendable usar un corrector ortográfico durante la redacción del mismo.
- Redacta correctamente, con un lenguaje preciso y sin complicaciones innecesarias.
- Intenta ponerte en el lugar del público al que te diriges (el documento va dirigido a expertos en la temática del mismo o no, va dirigido a matemáticos o a un público en general). 
- Haz un uso moderado de los símbolos y abreviaturas matemáticas y evita su uso en las oraciones (p.e. usar el símbolo $\Rightarrow$ en mitad de un párrafo en lugar de la palabra *implica*). Todos los símbolos deben de estar definidos previamente 
- En caso de que el documento contenga mucha nomenclatura específica, crear un *glosario de términos* al final del documento (e indicar la existencia del mismo en la introducción).
- Las fórmulas matemáticas que acompañan un texto científico deben de ser tratadas como palabras y puntuadas adecuadamente:
	- Separadas por comas si estamos dando una lista de ecuaciones
	- Finalizando la ecuación con un punto si es el final de la oración.
- Es mala práctica comenzar una oración con una ecuación.
- El texto citado debe ir entre comillas (en LaTeX las comillas se abren con \`\` y se cierran con `''`) y acompañado de una referencia a la fuente original. Puedes usar el entorno `quote` (para citas textuales breves) o `quotation` en LaTeX. Si se hace uso de dichos entornos no es necesario, así lo señala la RAE, entrecomillar las citas.


## Enunciados matemáticos

Consultar la sección [Tipos de documento](../Matematicas/about.qmd) para más información.

- Los resultados matemáticos (lemas, proposiciones, teoremas y corolarios) deben de estar redactados siguiendo el orden: declaración de objetos matemáticos, hipótesis y tesis. 
- Los corolarios habitualmente aparecen después de un teorema y son resultados que se deducen de éste.
- Las proposiciones suelen ser resultados de menor categoría que un teorema aunque de interés por si mismas.
- Los lemas suelen ser resultados de tipo técnico necesarios para la demostración de un teorema y pueden ir tanto antes del enunciado del teorema como entre el enunciado de este y su demostración. En este último caso, hay que indicar al inicio del entorno `proof` que vamos a comenzar la demostración del teorema principal mediante el argumento opcional del entorno `proof` y una referencia al teorema usando `\ref`:
	```tex
	\begin{teorema}\label{thm:doCarmo}
	Enunciado
	\end{teorema}

	\begin{lema}\label{lm:resultado-tecnico-1}
	Enunciado 1
	\end{lema}
	\begin{proof}
	Demostración lema
	\end{proof}
	
	\begin{lema}\label{lm:resultado-tecnico-2}
	Enunciado 2
	\end{lema}
	\begin{proof}
	Demostración lema
	\end{proof}

	\begin{proof}[Demostración del \autoref{thm:doCarmo}]
	Demostración teorema: gracias a los lemas~\ref{lm:resultado-tecnico-1} y~\ref{lm:resultado-tecnico-2}...
	\end{proof}
	```


## Referencias

Consultar la sección [Bibliografía](../Bibliografia/about.qmd) para conocer cómo incluir referencias bibliográficas en un documento LaTeX.

- Todas las referencias incluidas en el documento deben de aparecer citadas en algún lugar del mismo con el comando `\cite`. Es una mala práctica incluir referencias sin citar.
- Al incluir un resultado (especialmente si no se incluye una demostración) es conveniente citar la fuente original donde encontrar una demostración además de cualquier otra fuente relevante (p.e. demostraciones alternativas) al mismo. Para indicar la autoría y añadir la referencia a un teorema (o proposición o lema) se usa el argumento opcional (entre corchetes `[` `]`) de dicho tipo de entornos:
	```tex
	\begin{teorema}[do Carmo~\cite{doCarmo92}, 1992]
	Enunciado
	\end{teorema}
	```
- *Estilo*: al incluir una referencia y hacer mención expresa los autores, p.e. en `Do Carmo \cite{doCarmo92}` es recomendable añadir el símbolo `~` entre el nombre del autor y el comando `\cite`. Dicho símbolo evita que LaTeX separe en distintas líneas distintas el nombre del autor y su referencia. De forma similar, al incluir una referencia con `\ref` también se hace uso del mismo símbolo, p.e. `Ver teorema~\ref{thm:DoCarmo}`.


## LaTeX
- Corrige todos los errores de LaTeX tan pronto aparezcan al compilar. En ocasiones es muy difícil localizar un error que ha quedado sin corregir.
- Intenta obtener al final una *composición* limpia, sin errores ni advertencias. Especialmente, sin avisos de *overfull* o *underfull*. Estos avisos nos indican dificultades que ha tenido LaTeX al componer el texto y que han dado como resultado líneas de anchura mayor o menor que la anchura predefinida para el texto. Para mostrar visualmente las advertencias de *overfull* incluye el comando
	```tex
	\overfullrule=10pt
	```
	en el preámbulo del documento.
	Consulta [Understanding underfull and overfull box warnings - Overleaf, Editor de LaTeX online](https://es.overleaf.com/learn/how-to/Understanding_underfull_and_overfull_box_warnings) para más información al respecto.
- Evita incluir paquetes o definiciones en el preámbulo que no vas a usar o que desconoces su uso (p.e. al copiar y pegar de otros sitios).
- Como regla general deja que LaTeX establezca el espacio vertical y horizontal por sí mismo. Aunque existen comandos para modificar el espacio vertical (p.e. `\bigskip`, `\medskip`, `\smallskip`, `\vskip`, `\vspace`) y horizontal (p.e. `\ `, `\,`, `\!`, `\quad`, `\qquad`, `\hskip`) no los uses sin una buena razón.
- No uses `\\` para terminar un párrafo. Deja en su lugar una línea en blanco. La orden `\\` tiene su función en tablas y alineamientos.
- Sé moderado a la hora de destacar palabra en el texto (en cursivo con `\emph`, en negrita con `\textbf`,...). Una página llena de cursivas, negritas, texto entre comillas, mayúsculas, recuadros, colores y tamaños es **difícil** de leer.
- Usa las órdenes `\sen`, `\cos`, `\tg`, `\lim`, `\max`, `\min`,... que producen los operadores matemáticos en letra *recta*. Si un operador no está definido puedes crear un comando para el mismo incluyendo el preámbulo
	```tex
	\DeclareMathOperator{\grad}{grad} % gradiente
	```
- Para incluir texto en una fórmula usa la orden `\text`. Por ejemplo
	```tex
	\[
	(-1)^n = 
	\begin{cases}
	1, &\text{si } n \text{ es par,} \\
	-1, &\text{si } n \text{ es impar.}
	\end{cases}
	\]
	```
	observa que dentro del comando `\text` el espacio en blanco funciona como en el texto normal.
- Existe una gran variedad de entornos para escribir una fórmula que no cabe en una línea o agrupar varias fórmulas: `align`, `aligned`, `split`, `multline`, `gather`,... Consulta la [guía del paquete `amsmath`](https://ctan.fisiquimicamente.com/macros/latex/required/amsmath/amsldoc.pdf). Por ejemplo, si partes una fórmula en dos líneas, los símbolos de relación (=, <, >,...), operación (+, -) o implicación ($\Rightarrow$, ...) y, en general, los símbolos que unen dos términos o dos miembros de la fórmula nunca deben quedar al final de la línea, sino comenzando la siguiente.
- Nunca se debe numerar a mano. Usar siempre `\label` para etiquetar un elemento (teorema, fórmula, figura, tabla,...) y `\ref` para referenciarlo. ¡Atención! Las fórmulas es mejor referenciarlas con `\eqref`. El comando `\autoref` se encargará por nosotros de determinar el tipo de elemento y lo formateará de forma adecuada.
- Las figuras y tablas deben siempre ir etiquetadas (con el comando `\label`) y referenciadas en el texto (con `\ref` o `\autoref`). Evitas frases como *en la siguiente figura* y usa en su lugar *en la figura~\ref{fig:etiqueta}*.

