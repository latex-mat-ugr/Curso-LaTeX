# Objetos flotantes

Los *objetos flotantes* son aquellos que TeX puede mover en el documento final para conseguir el mejor aspecto posible. Son dos: figuras y cuadros (tablas).

No vamos a hablar aquí de como generar los gráficos si no de cómo se incluye un gráfico o un cuadro en un documento LaTeX.

## Figuras y cuadros

### Figuras

La forma de incluir un gráfico como objeto flotante es
```latex
\begin{figure}[opciones]
Gráfico,
\end{figure}
```

### Opciones

- h (*here*) intenta colocar el gráfico en ese lugar en el texto.
- t (*top*) tiene preferencia la parte superior de la página.
- b (*bottom*) tiene preferencia la parte inferior de la página.
- p (*paragraph*)

### Cuadros

La forma de incluir un cuadro como objeto flotante es
```latex
\begin{table}[opciones]
Cuadro
\end{table}
```
El entorno ``table`` tiene las mismas opciones que el entorno ``figure``.

## Cómo escribir cuadros

Hay muchas formas de escribir cuadros o tablas en un fichero LaTeX. Existen numerosos paquetes que hacen esto más sencillo. Vamos a comentar algunos.

### Tabular

El entorno ``tabular`` es la forma más básica de incluir cuadros.

```latex
\begin{table}[htp] % coloca el cuadro aquí, arriba
\centering
\begin{tabular}{||c|l|r||}
\hline \hline Nombre & Apellidos & Nota \\
\hline Alonso & Machado & 7 \\
\hline Eduardo & Aranda & 8 \\
\hline José & García & 8 \\
\hline \hline
\end{tabular}
\caption{Lista de notas}
\end{table}
```

Como se ve en el ejemplo anterior, el aspecto de un cuadro es el siguiente
```
\begin{tabular}{col1,col2,col3}
a11 & a12 & a13 \\
a21 & a22 & a23 \\
\end{tabular}
```
donde col1, col2,... es un tipo de columna. Además de esto se pueden dibujar líneas horizontales (con \hline) o verticales (usando | como separador)

#### Tipos de columnas

Hay tres tipos básicos de columnas: alineada a izquierda, centrada o alineada a la derecha: se indican con las letras l,c,r. Además también tenemos el tipo de columna párrafo que se indica con la letra p seguida de la anchura del párrafo entre llaves.

Por ejemplo
```latex
\begin{center}
\begin{tabular}{|l|c|r|p{5cm}|}
\hline Nombre & Apellidos & Nota & Comentarios \\
\hline Manuel & López & 7 & Hoy hemos hablado de cuadros y tablas, los dos ejemplos de objetos flotantes\\
\hline Mike  & García & 7.5 & Mañana hablaremos de la forma de organizar la bibliografía de un documento \\
\hline
\end{tabular}
\end{center}
```



### El paquete *booktabs*

El paquete [booktabs](http://ctan.org/pkg/booktabs) contiene
algunas reglas generales que mejoran el aspecto de tablas o cuadros:

* es preferible alinear a la izquierda;
* no uses líneas verticales;
* evita las líneas dobles;
* coloca las unidades en la cabecera;
* no uses comillas para repetir el contenido.

Entre otras cosas el paquete *booktabs* incluye las órdenes toprule, midrule y bottomrule que hacen las líneas horizontales de una tabla.

```latex
\begin{table}[htp]
\centering
\begin{tabular}{@{}lll@{}}
\toprule
Nombre & Apellidos & Nota \\
\midrule
 Antonio & López & 7 \\
 John & Fuentes & 8 \\
 Mario & Suárez & 8 \\
\bottomrule
\end{tabular}
\caption{Lista de notas}
\end{table}
```


### El paquete *tabularx*

Incluye el tipo de columna *X*, que se estira hasta ocupar el espacio indicado. En el ejemplo siguiente: una columna (la segunda), se estira hasta ocupar toda la línea.

```latex
\begin{tabularx}{\linewidth}{lX}
\toprule
 Unidad & Definición \\
 \midrule
 Newton & Su correspondiente definición  \\
 Otra &  Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua  \\
 \bottomrule
\end{tabularx}
\end{center}
```

Si ponemos más de una columna de tipo X, el espacio se distribuye entre todas ellas.
```latex
\begin{tabularx}{\linewidth}{lXX}
\toprule
 Unidad & Definición & Otra cosa \\
 \midrule
 Newton & Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua  & Un poco más de texto para ocupar otro poco más \\
 Otra & Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua  & Un poco más de texto para ocupar otro poco más \\
 Newton & Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua  & Un poco más de texto para ocupar otro poco más \\
 Otra & Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua  & Un poco más de texto para ocupar otro poco más \\
\bottomrule
\end{tabularx}
```

### El paquete *rotating*

El paquete rotating incluye varias órdenes para girar cuadros.

Se puede usar `sideways` alrededor de un entorno de entorno tabular para girar un cuadro pequeño.
```latex
\begin{center}
\begin{sideways}
\begin{tabular}{llr}
\toprule
\multicolumn{2}{c}{\textbf{Alumno}} \\
\cmidrule(r){1-2}
Nombre & Apellidos & Nota \\
\midrule
Antonio & López & 7 \\
John & Fuentes & 8 \\
Mario & Suárez & 8 \\
\bottomrule
\end{tabular}
\end{sideways}
\end{center}
```

También se puede girar un cuadro que ocupe una página completa: en lugar de un entorno `table`, usamos `sidewaystable`.
```latex
\begin{sidewaystable}
\centering
\begin{tabular}{@{}lllllllll@{}}
\toprule
Nombre & Apellidos & Nota & Nombre & Apellidos & Nota & Nombre & Apellidos & Nota \\
\midrule Manuel & López & 7 & Manuel & López & 7 & Manuel & López & 7 \\
 John & Smith & 8 &  John & Smith & 8 &  John & Smith & 8 \\
 Mike & Aranda & 8 &  Mike & Aranda & 8 &  Mike & Aranda & 8 \\
 Manuel & López & 7 & Manuel & López & 7 & Manuel & López & 7 \\
 John & Smith & 8 &  John & Smith & 8 &  John & Smith & 8 \\
 Mike & Aranda & 8 &  Mike & Aranda & 8 &  Mike & Aranda & 8 \\
 Manuel & López & 7 & Manuel & López & 7 & Manuel & López & 7 \\
 John & Smith & 8 &  John & Smith & 8 &  John & Smith & 8 \\
 Mike & Aranda & 8 &  Mike & Aranda & 8 &  Mike & Aranda & 8 \\
\bottomrule
\end{tabular}
\caption{lista de notas}
\end{sidewaystable}
```

### Uso de color (versión básica)

Hay que cargar el paquete color con la opción table. La orden rowcolors tiene tres parámetros: la fila en la que empieza a funcionar, color inicial y color alternativo. Por ejemplo, empezamos en la tercera fila con un 5\% de negro y alternamos con blanco.

```latex
\begin{table}[htbp]
\rowcolors{3}{black!5}{white}
\centering
\begin{tabular}{llr}
\toprule
Nombre & Apellidos &  Nota \\
\midrule
John & Smith & 7.5 \\
Mike & Dodds & 7.5 \\
Robert & Isaac & 8 \\
John & Smith & 7.5 \\
Mike & Dodds & 7.5 \\
Robert & Isaac & 8 \\
\end{tabular}
\caption{Una prueba}
\end{table}
```

### Cuadros de más de una página

Cargamos los paquetes `longtable` y `tabu`. En el código siguiente se puede ver la estructura de un cuadro que ocupa más de una página. Al principio se escriben las cabeceras de la primera página, de las siguientes y lo mismo con los finales de los cuadros.
```latex
\begin{center}
\begin{longtabu} to 0.7\linewidth{lll} % la tabla va a ocupar el 70% de la línea
% empieza la primera cabecera
\toprule
\textbf{Nombre} & \textbf{Apellidos} & \textbf{Nota} \\
\midrule
\endfirsthead
% ahora la cabecera para el resto de páginas
\toprule
\textbf{Nombre (seguimos)} & \textbf{Apellidos} & \textbf{Nota} \\
\midrule
\endhead
% ahora el pie de tabla para cada página
\midrule
\endfoot
% y el pie de página para la última página
\bottomrule
\endlastfoot
% ahora ya escribimos los datos de la tabla
John & Smith & 7.5 \\
Mike & Dodds & 7.5 \\
Robert & Isaac & 8 \\
John & Smith & 7.5 \\
Mike & Dodds & 7.5 \\
Robert & Isaac & 8 \\
John & Smith & 7.5 \\
Mike & Dodds & 7.5 \\
Robert & Isaac & 8 \\
John & Smith & 7.5 \\
Mike & Dodds & 7.5 \\
Robert & Isaac & 8 \\
John & Smith & 7.5 \\
Mike & Dodds & 7.5 \\
Robert & Isaac & 8 \\
John & Smith & 7.5 \\
Mike & Dodds & 7.5 \\
Robert & Isaac & 8 \\
John & Smith & 7.5 \\
Mike & Dodds & 7.5 \\
Robert & Isaac & 8 \\
John & Smith & 7.5 \\
Mike & Dodds & 7.5 \\
Robert & Isaac & 8 \\
John & Smith & 7.5 \\
Mike & Dodds & 7.5 \\
Robert & Isaac & 8 \\
John & Smith & 7.5 \\
Mike & Dodds & 7.5 \\
Robert & Isaac & 8 \\
John & Smith & 7.5 \\
Mike & Dodds & 7.5 \\
Robert & Isaac & 8 \\
John & Smith & 7.5 \\
Mike & Dodds & 7.5 \\
Robert & Isaac & 8 \\
John & Smith & 7.5 \\
Mike & Dodds & 7.5 \\
Robert & Isaac & 8 \\
John & Smith & 7.5 \\
Mike & Dodds & 7.5 \\
Robert & Isaac & 8 \\
John & Smith & 7.5 \\
Mike & Dodds & 7.5 \\
Robert & Isaac & 8 \\
John & Smith & 7.5 \\
Mike & Dodds & 7.5 \\
Robert & Isaac & 8 \\
John & Smith & 7.5 \\
Mike & Dodds & 7.5 \\
Robert & Isaac & 8 \\
John & Smith & 7.5 \\
Mike & Dodds & 7.5 \\
Robert & Isaac & 8 \\
John & Smith & 7.5 \\
Mike & Dodds & 7.5 \\
Robert & Isaac & 8 \\
John & Smith & 7.5 \\
Mike & Dodds & 7.5 \\
Robert & Isaac & 8 \\
John & Smith & 7.5 \\
Mike & Dodds & 7.5 \\
Robert & Isaac & 8 \\
John & Smith & 7.5 \\
Mike & Dodds & 7.5 \\
Robert & Isaac & 8 \\
John & Smith & 7.5 \\
Mike & Dodds & 7.5 \\
Robert & Isaac & 8 \\
John & Smith & 7.5 \\
Mike & Dodds & 7.5 \\
Robert & Isaac & 8 \\
John & Smith & 7.5 \\
Mike & Dodds & 7.5 \\
Robert & Isaac & 8 \\
John & Smith & 7.5 \\
Mike & Dodds & 7.5 \\
Robert & Isaac & 8 \\
John & Smith & 7.5 \\
Mike & Dodds & 7.5 \\
Robert & Isaac & 8 \\
John & Smith & 7.5 \\
Mike & Dodds & 7.5 \\
Robert & Isaac & 8 \\
\end{longtabu}
\end{center}
```
