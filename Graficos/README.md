Todos sabemos que en un documento generado con $\LaTeX{}$ podemos incorporar  gráficos. 

Lo que no es tan conocido es que, al insertarlos, permite editarlos ligeramente. Seleccionar parte de la imagen, redimensionar, girar, superponer, simetrizar, incluir texto son algunas de las modificaciones que podemos realizar sobre una imagen al incluirla en un documento de una manera sencilla sin necesidad de recurrir a un editor de gráfico como se explica en la [primera sección](#inserciónedición-de-gráficos)

No obstante, la inclusión de muchos documentos gráficos en un mismo documento tiene varios inconvenientes:
- dan como resultado documentos muy pesados,
- y pese a ello, la calidad de los gráficos insertados no siempre es óptima.

Para resolver estos inconvenientes $\LaTeX$ adoptó hace tiempo la estrategia
*Do it yourself*. Esto es,  el propio $\LaTeX$ interpreta una serie de instrucciones mediante las que crea el gráfico. El resultado son imágenes de la más alta calidad y de peso muy reducido, aunque para ello hay que invertir en tiempo de aprendizaje. En la [segunda sección](#creación-de-gráficos) mostramos la potencialidad de esta capacidad de $\LaTeX$.

En el fichero [presentacion1.pdf](presentacion1.pdf) hay varios ejemplos de cómo insertar gráficos en documentos LaTeX, mientras que en [presentacion2.pdf](presentacion2.pdf) se muestra cómo generar gráficos empleando el propio LaTeX. Estos ficheros, además de estar disponibles en [nuestro repositorio de Github](https://github.com/latex-mat-ugr/Curso-LaTeX/tree/master/Graficos), están encastrados al final de cada sección para su visualización. Los ficheros [presentacion1.tex](presentacion1.tex) y [presentacion2.tex](presentacion2.tex) contienen los ficheros en LaTeX para generar las presentaciones Beamer anteriores por lo que sirven a su vez como ejemplos. La compilación de estos ficheros requiere de los ficheros de gráficos contenidos en la carpeta gráficos.


## Inserción/edición de gráficos.

### Generalidades sobre documentos gráficos
A la hora de preparar un gráfico para insertarlo en un documento $\LaTeX{}$ hemos de tener en cuenta que:
- el resultado final dependerá mucho de cómo éste se haya generado y 
- que el fichero en el que se guarde no puede estar en un formato cualquiera.  

En general hemos de tener en cuenta que hay dos grupos básicos de gráficos: los mapas de bits (también llamados imágenes de pixeles) y gráficos vectoriales. Básicamente los primeros son una gran tabla donde se indica el color de cada punto del gráfico (pixel) mientras que los segundos son ficheros donde se guardan una serie de instrucciones para generar el gráfico. Por lo general los mapas de bits son más pesados y poco adecuados para el redimensionado que los gráficos vectoriales. Por lo tanto, hay que evitar el uso de mapas de bits cuando la naturaleza de gráfico nos lo permita, lo que es imposible el caso de fotografías, capturas de pantalla, imágenes descargadas de la red, ...

Por último si queremos generar un fichero PDF con $\LaTeX{}$ los compiladores más usuales únicamente aceptarán ficheros en formato PNG, JPEG o PDF, por lo que te puedes ver obligado a exportar tu imagen a uno de estos formatos. 

Para ampliar detalles y buscar programas que nos ayuden en estas labores tan específicas recomendamos la lectura del siguiente [Wikibook](https://es.wikibooks.org/wiki/Manual_de_LaTeX/Inserci%C3%B3n_de_figuras_externas).

### Inserción básica de gráficos

La inserción de un gráfico requiere de la 
declaracion del paquete *graphicx* en el preámbulo
mediante el comando:
```latex
\usepackage{graphicx}
````

En cualquier punto del cuerpo del documento podremos 
incluir una imagen mediante el comando:
```latex
  \includegraphics[parametros]{nombregrafico}
```
No obstante, recomendamos que los gráficos siempre se declaren en un entorno *figure* de la siguiente manera: 
```latex
\begin{figure}[h]
  \centering
  \includegraphics[parametros]{nombregrafico}
  \caption{Leyenda bajo el grafico}
  \label{fig:etiqueta}
\end{figure}
```
De esta forma la imagen aparecerá con la leyenda que describa su contenido en el campo *caption* y se podrá hacer referencia a ella desde el texto empleando la etiqueta declarada en *label*, al igual que se hace con tablas o fórmulas.

Mediante distintos comandos incluidos en el campo *parametros* se puede modificar el aspecto de la imagen, lo que nos permite editarlos ligeramente. Este punto se amplia a continuación.

### Inserción avanzada de gráficos (edición)

Así, por ejemplo, podemos incluir en el campo parámetros los siguientes comandos (separados mediante comas): 

- *scale=0.5*, para escalar el tamaño a la mitad,
- *height=5cm*, para fijar la anchura del gráfico a 5cm,
- *width=0.5\textwidth*, para ajustar la anchura de la imagen a la mitad del espacio que ocupa el texto,
- *angle=90*, para girar la imagen 90 grados,
- *trim = 10mm 5mm 50mm 55mm, clip* para recortar la imagen quitando 10mm por izda, 5 mm por debajo, 50mm por la derecha y 55mm por arriba, 
- *draft*, para agilizar la compilación de manera que no incluye el gráfico pero deja el espacio apropiado.

Para una descripción en detalle de estas y otras opciones ver la documentación paquete [graphicx](https://ctan.org/pkg/graphicx?lang=en).

Así por ejemplo, los comandos
```latex
\begin{figure}
\includegraphics[width=0.45\textwidth]{./graficos/sorpresa.pdf}
\hspace{0.25cm}
\reflectbox{
\includegraphics[width=0.45\textwidth]{./graficos/sorpresa.pdf}
}
\caption{La misma imagen reflejada.}
\end{figure}
```
muestran dos veces la imagen del fichero *sorpresa.pdf*, que se encuentra en la subcarpeta *graficos*, apareciendo la segunda vez simetrizada gracias al comando *\reflectbox*.

La superposición de gráficos o texto a una imagen se puede hacer mediante el comando
```latex
\put(coordenadas){objeto}
```
se pueden superponer ‘el objeto’ en la posicion ‘coordenadas’. De esta manera los comandos
```latex
\begin{figure}[h]
\includegraphics[angle=270,width=7cm]{./graficos/fig_9}
\put(-100,-55){$\displaystyle s:=\frac{a+b+c}{2}$}
\end{figure}
````
incluyen sobre el gráfico *fig_9*, que ha sido girado 270º, la fórmula matemática $\displaystyle s:=\frac{a+b+c}{2}$ en la posición determinada por las coordenadas $(-100,-55)$.


### Dificultades usuales 
A continuación comentamos cómo tratar dos de los *inconvenientes* que los usuarios  de $\LaTeX$ noveles encuentran a la hora de trabajar con gráficos. 

El primero de ellos es que el entorno figure es flotante, esto es, $\LaTeX$ "decide"
dónde lo localiza en el texto. Si queremos controlar este proceso tenemos varias 
opciones:
- Control débil del entorno *figure* con parámetros 
    de control h (here), b (botton), t (top) como se muestra en el ejemplo anterior.
- Empleo del entorno *wrapfigure* gracias al paquete [wrapfig](https://www.ctan.org/pkg/wrapfig) para que el texto pueda envolver al gráfico.
- Empleo del parámetro H del paquete [float](https://www.ctan.org/pkg/float) para que el usuario determine, de manera estricta y bajo su responsabilidad, dónde aparecerá el gráfico.
- Usar *includegraphics* sin entorno *figure* práctica que, como comentamos, aun siendo posible es no recomendable.

Podemos ver ejemplos concretos en la [ayuda de OverLeaf](https://www.overleaf.com/learn/latex/Positioning_images_and_tables).

Otro de los problemas que podemos encontrar muchas veces es que queremos *ajustar* el espacio que queda entre el texto y el gráfico. Al insertar un gráfico pueden quedar unos espacios muy ámplios hasta el texto y esto, a veces, ocurre porque el gráfico tiene unos márgenes muy grandes. 
Para estar seguros de si es este el motivo se puede usar el comando *frame* de la siguiente manera:
```latex
\begin{figure}[h]
\frame{\includegraphics{./graficos/fig_9}}
\end{figure}
```
a la hora de insertar el gráfico para que este quede enmarcado. De esta forma podemos ajustar con los parámetros *trim* y *clip* el espacio a cortar en los márgenes de la imagen. Además de eliminar el espacio innecesario, esto nos permitirá aumentar el tamaño de la parte verdaderamente relevante de la imagen.  Si aún así queremos ajustar el espacio entre el texto y la imagen siempre podemos usar (sin abusar) el comando *\vspace{xcm}*.


### Inclusión de páginas completas seleccionadas de ficheros pdf

Por último, puede ser de mucha utilidad saber que 
el paquete [pdfpages](https://www.ctan.org/pkg/pdfpages) permite incluir mediante el comando:
```latex
\includepdf[]{file.pdf}
```
páginas seleccionadas del fichero file.pdf en un documento $\LaTeX$.
Esto puede ser una herramienta de inmensa ayuda por ejemplo si queremos generar un documento con documentación acreditativa, incluir declaraciones en documentos, etc...

Pueder visualizar todos los ejemplos anteriores en el fichero presentacion1.pdf{target="_pdf"}.


## Creación de gráficos

Existen dos *macropaquetes* para la realización de gráficos en $\LaTeX$:
- [PSTricks](http://www.ctan.org/pkg/pstricks),
- y [PGF-TikZ](http://www.texample.net/tikz/).

En ambos casos proporcionan un gran abanico de comandos específicos.

Podemos sacar provecho de ellos de varias maneras
dependiendo del tiempo que estemos dispuetos a invertir en ello:
- escribiendo nosotros directamente los códigos. Hay disponibles numerosos manuales, y ejemplos que podemos tomar como punto de partida para nuestros proyectos:
  - [http://www.texample.net/tikz/examples/](http://www.texample.net/tikz/examples/)
  - [http://tug.org/PSTricks/main.cgi?file=examples](http://tug.org/PSTricks/main.cgi?file=examples)

- Una aproximación intermedia sería emplear paquetes/manuales específicos, que aún basándose en los anteriores, proporcionan/analizan comandos específicos para  realizar gráficos particulares como:
  - [PGFPlots](http://pgfplots.net) para representar funciones y datos,
  - [Chemfig](https://www.ctan.org/pkg/chemfig) para representar gráficamente sustancias químicas,
  - [Diagramas de árboles](https://www.overleaf.com/learn/latex/LaTeX_Graphics_using_TikZ%3A_A_Tutorial_for_Beginners_(Part_5)%E2%80%94Creating_Mind_Maps#:~:text=Part%204%20%7C-,Part,-5),
  - o [diagramas de flujo](https://www.overleaf.com/learn/latex/LaTeX_Graphics_using_TikZ%3A_A_Tutorial_for_Beginners_(Part_3)%E2%80%94Creating_Flowcharts#The_tikzstyle_command:~:text=Part%202%20%7C-,Part,-3%20%7C%20Part).

- Por último, la opción que a priory puede ser más conservadora en inversión de tiempo sería crear los gráficos con otros programas que permitan exportarlos a $\LaTeX$. Son numerosos los programas que ofrecen la posibilidad de exportar gráficos  generados con ellos bien a TikZ:
  - [gnuplot](https://ctan.org/pkg/gnuplottex),
  - [Xfig](https://mcj.sourceforge.net/latex_and_xfig.html) (versión para Windows: [WinFIG](http://winfig.com/)), 
  - [GeoGebra](http://www.geogebra.org/cms/),

  o bien a PSTricks
   - [Inkscape](https://inkscape-manuals.readthedocs.io/en/latest/export-other-formats.html),
  - [LatexDraw](http://latexdraw.sourceforge.net).
  - [Dia](http://dia-installer.de/index.html.en).


Los resultados de los comandos analizados en esta sección pueden ser visualizados en [presentacion2.pdf](presentacion2.pdf){target="_pdf"}.
