# Presentaciones con Beamer

Al igual que en $\LaTeX$ existen clases para escribir artículos o libros existe la clase
Beamer que es específica para generar presentaciones en formato PDF.
De hecho, Beamer significa videoproyector en alemán. 

La principal ventaja es que el contenido de la transparencia se escribirá en código $\LaTeX$ al igual que se hace en un artículo o en un libro por lo que permite "reciclar" material ya editado préviamente. Esto simplifica mucho nuestra labor ya que, en este caso, hay seleccionar información que se incluirá en las transparencias y diseñar cómo aparecerá (posibilidad de incluir efectos dinámicos).

A continuación mostramos un ejemplo básico de documento Beamer sobre el que basaremos nuestra presentación.


```latex
\documentclass{beamer}
% Este es el contenido del fichero presentacion.tex
\usetheme{Berlin}

\usepackage[utf8]{inputenc}
\usepackage[spanish]{babel}

\title{Presentaciones creadas con el paquete Beamer}
\author{Tu mismo}
\date{\today}

\begin{document}
%
\begin{frame}
\titlepage
\end{frame}
%
\begin{frame}
\frametitle{Índice de la presentación}
\tableofcontents
\end{frame}
%
\section{Organización de contenidos usando Beamer}
%
% Incluir frames organizados en secciones y/o subsecciones
%
\end{document}
```

## Aspecto general de la presentación
Antes de comenzar una presentación hay que escoger un tema mediante el comando `\usetheme` que determinará el aspecto último de nuestra presentación. En el ejemplo anterior se ha usado el tema Berlin aunque como se puede ver en la [Beamer theme gallery](https://deic.uab.cat/~iblanes/beamer_gallery/index.html)
hay disponibles una gran variedad de temas en los que además, opcionalmente se pueden elegir colores y fuentes.
Así por ejemplo, si tras la elección del tema Berlín, se se añaden los comandos

```latex
\usecolortheme{seagull}
\usefonttheme[onlysmall]{structurebold}
```
podemos modificar los colores que se usen en el tema y el tipo de letra. 


Una vez que se ha declarado el aspecto básico que van a tener nuestras transparencias se declaran los datos necesarios para generar la primera transparencia que son el título, autor/es y la fecha. Si además se quiere que en esta primera página aparezca algún logo  se puede hacer mediante los comandos:

```latex
\titlegraphic{\includegraphics[width=2cm]{./ugr.png}}
```
si se quiere que el logo aparezca únicamente en el título o bien 
```latex
\logo{\includegraphics[width=2cm]{./ugr.png}}
```
si lo que se quiere es que el logo aparezca en todas las páginas donde el tema lo tenga declarado.

En la plantilla anterior la primera transparencia, declarada en un entorno `frame`, se crea de manera autormática con el comando `titlepage` a partir de la 
información declarada en el preámbulo.

De manera análoga se ha generado una segunda transparencia con el índice de la presentación mediante el comando `tableofcontents`. En este aparecerán los títulos de las secciones o subsecciones que se hayan declarado en la presentación de la misma manera que se hace en cualquier otro tipo de documento generado con $\LaTeX$.


## Organización del mensaje

Como ya se ha comentado, el entorno Beamer permite mostrar cualquier contenido escrito en $\LaTeX$. 
Eso sí, tendremos que dividir estos contenidos en las diferentes diapositivas que vayamos a presentar empleando para ello entornos `frame` como el siguiente
```latex
\begin{frame}{Beamer admite escritura en \LaTeX\ y más:}
\begin{enumerate}
\item Fórmulas: 
$\max\left\{2^{x+y}\int_a^b e^{\frac{x^2}{2}}\lim_{x\to 1}x^{x-1},1\right\}.$
\item Resultados Matemáticos:
\begin{theorem}\label{tonto}
Las ranas son verdes.
\end{theorem}
\item tablas
\begin{tabular}{|l|c|c|c|} \hline
Posición & 1 & 2 & 3 \\ \hline \hline
Nombre & Pepe & Juan & Manuel\\ \hline
\end{tabular}
\item y cualquier otro contenido...
\end{enumerate}
\end{frame}
```

No obstante, Beamer tiene algunas funcionalidades extra que, empleadas en una presentación, pueden servir para potenciar el mensaje.

### Encapsulado de contenidos en bloques
La clase Beamer predefine unos entornos de tipo `block` que sirven para encapsular contenidos con un encabezamiento. Los temas determinan distintos diseños del bloque dependiendo de que sean de tipo:
`block` (bloque normal), `alertblock` o `exampleblock` 

```latex
\begin{frame}
\frametitle{Encapsulado de contenidos en bloques}
\begin{block}{Bloque normal}
Texto en un bloque normal
\end{block}
%
\begin{exampleblock}{Ejemplo}<uncover@2>
Bloque con un ejemplo: $f(x) = x^2$
\end{exampleblock}
%
\begin{alertblock}<3->{Advertencia}
¡Ojo con dividir por cero!
\end{alertblock}
\end{frame}
```
Existen otros entornos como `theorems`, `definition`o `proof` que pueden ser de utilidad
dependiendo del público al que nos dirijamos. 

 

### Inclusión de gráficos y texto
El uso de gráficos y diagramas en las presentaciones
es altamente recomendable aunque no siempre nos va a interesar que un gráfico ocupe toda una diapositiva. Es por esto que puede ser útil mostrarlo empleando dos columnas mediante el entorno `columns` de la siguiente manera

```latex
\begin{frame}{Uso conjunto de gráficos y texto}
\begin{columns}[t]
\column{5cm}
En esta columna\\
podemos escribir\\
texto y en la contigua insertar una imagen. 
\column<only@2->[T]{5cm}
\includegraphics[height=3cm]{ugr.png}
\end{columns}
\end{frame}
```

## Pausas y especificaciones de acción

Beamer permite ir mostrando los contenidos poco a poco mediante el comando `pause`
```latex
\begin{frame}{Pausar dentro de una misma transparencia}
\begin{itemize}
\item 2 es primo (dos divisores: 1 y 2).
\pause
\item 3 es primo (dos divisores: 1 y 3).
\pause
\item 4 no es primo (\alert{tres} divisores: 1, 2, y 4).
\end{itemize}
\end{frame}
```


No obstante, como se ha visto en los ejemplos anteriores, se puede obtener un control mucho mayor empleando `especificadores de acción`,  modificadores opcionales de la forma `<action>`. Así por ejemplo:

  - `<2->` implica que dicho objeto se añadirá a la transparencia a partir de la segunda transparencia en adelante, 
  - `<uncover@2>` inplica qu el objeto se ha introducido desde la primera transparencia, pero se mostrará a partir de la segunda
  - mientras que 
`<only@2>`implica que estará presente únicamente en la segunda transparencia (no aparece ni en la primera ni de la tercera en adelante).


Otra opción interesante es crear animaciones simples donde cada imagen de la animación se hace aparecer en una transparencia distinta:

```latex
\begin{frame}{Animación mediante especificadores de acción}
\includegraphics<1>[height=2.5cm]{ugr.png}%
\includegraphics<2>[height=3cm]{ugr.png}%
\includegraphics<3>[height=3.5cm]{ugr.png}%
\includegraphics<4>[height=4cm]{ugr.png}%
\includegraphics<5>[height=4.5cm]{ugr.png}%
\end{frame}
```

En la [Guía completa de la clase Beamer](https://tug.ctan.org/macros/latex/contrib/beamer/doc/beameruserguide.pdf) encontraremos indicaciones técnicas sobre cómo usar los comandos de esta clase además de consejos muy razonables sobre cómo preparar una charla.

## Referencias e información complementaria
Muchas veces una presentación será publicada/distribuida para que esta sirva como fuente de información complementaria para aquellas personas del público que estén interesadas en el tema. Por tanto es muy útil que se incluyan en esta:

 - Datos de contacto del autor en la portada mediante el comando:
 ```latex
  \author[Nom corto]{Nombre largo del autor \\ \texttt{autor@entidad.es}}
 ```
 - hipervínculos a publicaciones/repositorios online donde encontrar material relacionado
 ```latex
\href{https://tug.ctan.org/macros/latex/contrib/beamer/doc/beameruserguide.pdf}{\color{blue}{Guía completa de Beamer}}
 ```
  - o incluso una reducida bibliografía si es el caso 
 ```latex
 \begin{frame}
\frametitle{Referenciar/vincular bibliografía para profundizar}
\begin{thebibliography}{10}
\bibitem{Tantau2025}[Tantau et al, 2025]
Till Tantau, Joseph Wright, Vedran Miletic.
\newblock The Beamer class, User Guide for version $3.76$,
\newblock \emph{\href{https://tug.ctan.org/macros/latex/contrib/beamer/doc/beameruserguide.pdf}{ctan.org}}, 2025.
\end{thebibliography}
\end{frame}
 ```
que puede ser citada en cualquier transparencia de la presentación mediante el comando:
 ```latex
\cite{Tantau2025}
 ```


## Recomendaciones a la hora de preparar/exponer unas transparencias

### Consejos para diseñar tu presentación

> Saber expresar una idea es tan importante como la idea misma

Aristóteles

Una buena presentación requiere de:

- contenido de calidad,
- mostrado en su justa medida
- y con una estructura clara,
- que ha de ser expuesto con confianza y naturalidad.


Por tanto, antes de empezar a escribir tu presentación:

- Ten en cuenta tanto el tiempo del que dispones para hacer la presentación como el público al que va dirigida y su conocimiento sobre el tema. No olvides aplicar la ley de la audiencia ignorante: 

> "Someone important in the audience always knows less than you
think everyone should know, even if you take the Ignorant Audience Law into account".

- Genera un esquema básico de la presentación que podría ser una propuesta del índice de esta. 
Un buen comienzo en la elaboración de tu presentación sería trasladar dicho esquema a tu fichero empleando secciones y subsecciones.

- Completa este esquema añadiendo transparencias de forma adecuada. Una buena señal es que los títulos de tus transparencias sean informativos del contenido de las mismas y que, leidos uno tras otro, transmitan un mensaje con sentido. Sigue la máxima de mostrar el significado antes que los detalles.

- Las transparencias deben tener entre 20 y 40 palabras formando frases cortas. Si todo estuviese escrito en las transparencias el orador sobra...

- Sintetiza en la presentación argumentos complejos en los que no sea posible entrar en profundidad. 

- Define todos los conceptos nuevos.

- Incluye gráficos y diagramas que ayuden en la comprensión. Cuida que sean visibles las etiquetas y números de los ejes las gráficas que muestras. Ten en cuenta que estas gráficas han de ser explicadas durante la presentación.

- No uses numeración para ecuaciones y resultados matemáticos. Intenta proporcionarles nombres descriptivos (Ej: Ecuación de Vlasov-Poisson, Teorema de existencia y unicidad...).

- Termina tu presentación con una conclusión.

- Repasa tu última versión del pdf generado poniendo particular atención en:
  - revisar y corregir erratas,
  - en el buen funcionamiento de las referencias cruzadas y vínculos,
  - y que las fuentes/símbolos se vean correctamente
  en distintos visores de pdf (Acrobat Reader, xpdf, evince, okular, Vista Previa,...).
  
### Consejos para la defensa de tu presentación

Una vez has terminado de generar tu fichero, 
practica el discurso que acompañará a tus transparencias, usando lenguaje claro y conciso, y el tiempo que dedicas a ello. 
Una transparencia por minuto es un límite al que 
es mejor no llegar. Y recuerda que hablar más rápido no es una opción ya que esto agotará la atención/paciencia de la audiencia:

> La atención de la audiencia es como un pez escurridizo: difícil de pescar y
más difícil aún de retener. 

Algunos consejos al respecto son:

- Si no les escuchas, no te extrañe que luego no te atiendan. 
- Toma como punto de partida lo que tenéis en común. 
- Exponer con confianza y naturalidad
- Guia su atención mediante: 
    - posturas, expresiones, gestos,
    - la mirada,
    - la entonación y entusiasmo,
    - las pausas,...


Si es necesario eliminar alguna transparencias, bien la comentas o bien puedes emplear el comando 
`\includeonlyframes{labelframe1,...}`.
Una alternativa interesante es dejar algunas 
de esas transparencias ya preparadas al final de tu presentación por si te sirven para responder a posibles preguntas.

El comentario anterior es sólo una de las cosas que puedes hacer para preparar con antelación el turno de preguntas. Si estás defendiendo un documento ten a mano una copia del mismo (¿Fe de erratas?).

Durante el turno de preguntas:

  - Escucha, escucha, escucha... y no interrumpas.
  - No hacer juicios sin base. Respuestas fundamentadas, sencillas y breves.
  - Acepta las críticas objetivas.
  - Si objetas, hazlo con respeto y elegancia.
  - Evita confrontaciones.



Estas y otras recomendaciones se pueden ver desarrolladas en:

- [Sec. 5, Guía completa de la clase Beamer](https://tug.ctan.org/macros/latex/contrib/beamer/doc/beameruserguide.pdf).
- G. Álvarez Marañon, El arte de presentar, Centro Libros, 2012.
- J. Doumont, Trees, maps and theorems, Pricipiae, 2014.
