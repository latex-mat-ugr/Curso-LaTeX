# Bibliografías

## Incluir la bibliografía de forma automática: `bibTeX`

Ya vimos en [Documento básico](../Documento sencillo/about.qmd) como incluir de forma sencilla las referencias bibliográficas en un documento mediante el uso del entorno \texttt{thebibliography}. A continuación veamos cómo mejorar este procedimiento, que tenía muchos inconvenientes.

LaTeX, mediante el programa externo `bibTeX` que está disponible en todas las distribuciones, permite la generación automática del entorno `thebibliography` a partir de una *base de datos bibliográfica* en formato `bibTeX` (un fichero de texto con extensión `.bib` con un formato determinado). Una vez generado el entorno `thebibliography` con las entradas citadas en el documento se guarda en un fichero auxiliar con extensión `.bbl` que es incluido de forma automática por LaTEX en el documento.

Los pasos para incluir la bibliografía de esta forma son los siguientes:

1. Crear un fichero, p.e. `referencias.bib` donde incluyamos los datos de los elementos bibliográficos en formato `bibTeX`. La mayoría de repositorios de artículos de investigación nos permiten descargar la referencia en dicho formato. Por ejemplo:

    ```bibtex
    @book {Euler1984,
      AUTHOR = {Euler, Leonhard},
      TITLE = {Elements of algebra},
      PUBLISHER = {Springer-Verlag, New York},
      YEAR = {1984},
      PAGES = {lx+593},
      ISBN = {0-387-96014-7},
      DOI = {10.1007/978-1-4613-8511-0},
    }
    @article {Euler1985,
        AUTHOR = {Euler, Leonhard},
         TITLE = {An essay on continued fractions},
       JOURNAL = {Math. Systems Theory},
      FJOURNAL = {Mathematical Systems Theory. An International Journal on Mathematical Computing Theory},
        VOLUME = {18},
          YEAR = {1985},
        NUMBER = {4},
         PAGES = {295--328},
          ISSN = {0025-5661},
           DOI = {10.1007/BF01699475},
    }
    ```
    donde el primer elemento de cada referencia (`Euler1984` y `Euler1985` respectivamente) es la *etiqueta* que luego debermos usar con el comando `\cite`.

2. Añadir en nuestro documento (ver, por ejemplo, [Ejemplo bibliografía.tex](./Ejemplo bibliografía.tex)), donde queremos que aparezca la bibliografía (habitualmente al final del documento justo antes de `\end{document}`):

    ```latex
    \bibliographystyle{plain} % plain, alpha, amsalpha, apalike, abbr
    \bibliography{referencias}
    ```
    donde recordemos que `referencias.bib` es el fichero de referencias creado en el punto anterior y ubicado **en la misma carpeta** que el documento `.tex` que estemos procesando.

3. Compilar el fichero primer con `LaTeX` y luego con `bibTeX` (en [TeXstudio](https://www.texstudio.org) u [Overleaf](https://www.overleaf.com) no es necesario compilar con `bibtex` necesario aunque sí lo es en otros editores). 

Aunque nuestro fichero `referencias.bib` contenga muchas referencias únicamente se añadiran al documento aquellas que hayamos *citado* (es decir, aquellas cuyas etiquetas aparezcan entro de un comando `\cite` en alguna parte del documento). Si queremos añadir una referencia que no aparece citada en el documento usaremos el comando `\nocite{etiqueta}`, donde `etiqueta` es la etiqueda de la referencia (primer elemento en la entrada `bibTeX` de la referencia). Si queremos producir un documento con **todas** las referencias que figuran en `referencias.bib` deberemos incluir el comando `\nocite{*}`.

**Ventajas**:

1. Al cambiar el estilo con `\bibliographystyle` se genera de nuevo la lista completa de referencias.

2. El fichero `referencias.bib` puede usarse para múltiples documentos de LaTeX, aprovechando de esa forma el tiempo empleado en crear el fichero.

El formato de un fichero `bibTeX` puede consultarse en su [manual](https://www.ctan.org/pkg/bibtex) aunque la mayoría de revistas o repositorios de artículos de investigación proporcionan una forma de descargar la información de una referencia en formato `bibTeX` para ser añadida en nuestro fichero `referencias.bib`. En la siguiente sección exploraremos cómo automatizar el proceso usando un **gestor de referencias bibliográficas**.


Actualmente el paquete [`biblatex`](https://www.ctan.org/pkg/biblatex) se está convirtiendo en el estándar para la gestión bibliográfica en LaTeX pues corrige algunas deficiencias de `bibTeX`. Su uso es compatible con `bibTeX` aunque tiene su propio *motor* llamado [`biber`](https://biblatex-biber.sourceforge.net) (también incluido en la mayoría de distribuciones de LaTeX).

## Creación de un fichero de referencias `.bib` mediante un gestor de referencias.

En un trabajo de investigación donde se suelen manejar muchas referencias es conveniente mantener cierto orden para recoger, organizar, anotar y citar debidamente los documentos. Existen diversos *gestores de referencias*, algunos de los más populares son:

- [Zotero](https://www.zotero.org)
- [Endnote](https://web.endnote.com) (Clarivate)
- [Mendeley](https://www.mendeley.com) (Elsevier)
- [RefWorks](https://refworks.proquest.com) (ProQuest).

El primero, [Zotero](https://www.zotero.org), es software libre y permite mediante una cuenta gratuita sincronizar nuestra base de datos bibliográficas en distintos equipos (el tamaño está limitado a 200 Mb, lo cual es poco si queremos además adjuntar los pdfs al programa). Existen diversas estrategias (como usar una nube privada) para disponer de más espacio.

Los tres últimos están disponibles (con distinto grado de características) a los miembros de la Universidad de Granada. Consultar la información [sobre gestore bibliográficos](https://bibliotecaugr.libguides.com/investigacion/Gestores_bibliograficos) disponible en el portal de [recursos para la investigación](https://bibliotecaugr.libguides.com/investigacion).

Todos requieren de la creación de una cuenta.


### Exportar las referencias a `bibTeX` usando Zotero

#### Forma manual:

1. Abre Zotero en tu ordenador o bien accede a tu cuenta en [zotero.org](https://www.zotero.org) en tu navegador web.

2. Si quieres exportar **todas las referencias** de una determinada biblioteca a bibTeX, haz clic en el menú desplegable Acciones y selecciona "Exportar biblioteca..." (Archivo > Exportar biblioteca... en la aplicación de escritorio). Si sólo quieres exportar **algunas referencias**, selecciónalas pulsando Control y Mayúsculas, haz clic con el icono de exportar ("crear una bibliografía a partir de los elementos seleccionados" en la versión de escritorio").

3. En el cuadro de diálogo que aparece, selecciona el formato `bibTeX` y haz clic en `Aceptar`. Navegamos hasta el directorio donde se encuentra nuestro documento LaTeX y guardamos ahí el archivo. Esto generará un archivo en el formato `.bib` para que bibTeX lo lea y cree una bibliografía a partir de él.

**Desventajas**: el anterior procedimiento deberemos repetirlo cada vez que añadamos un elemento nuevo a nuestra biblioteca o bien modifiquemos uno existente.

#### Forma automática: uso del complemento `betterbibtex`

Zotero permite la instalación de *complementos* que añaden características nuevas al gestor de bibliografía. Uno de ellos es [BetterBibTex](https://retorque.re/zotero-better-bibtex/) que facilita el uso de Zotero con LaTeX (o markdown). Este complemento tiene utilidad más allá de lo que indiquemos a continuación luego conviene echarle un vistazo a la [documentación](https://retorque.re/zotero-better-bibTeX/).

Una vez finalizada la [instalación](https://retorque.re/zotero-better-bibtex/installation/index.html) del complemento procederemos a partir del punto 2 anterior para exportar la biblioteca entera o bien un conjunto de referencias. En el punto 3 seleccionaremos ahora la opción `Better BibTeX`, marcaremos la opción `Keep updated` (ver captura de pantalla)

![betterbibtex-export.png]

y pulsaremos `OK`. A continuación seleccionaremos el directorio donde se encuentre nuestro documento LaTeX. A partir de este momento, ante cualquier cambio (tanto si añadimos como si modificamos) la base de datos de Zotero, éste exportará automáticamene los cambios al mismo fichero. Podemos repetir este procedimiento tantas veces como queramos (para incluir la bibliografía en distintos proyectos o documentos de LaTeX).

**Ventajas**: Sólo será necesario exportar la biblioteca una única vez *por proyecto de LaTeX*[^1]. 

[^1]: Entendemos por *proyecto de LaTeX* una carpeta en nuestro equipo que contiene uno o varios documentos `.tex`.

**Desventajas**: Para cada nuevo documento `.tex` que creemos en una carpeta distinta a donde hemos exportado el fichero `.bib` con Zotero será necesario volver a repetir (una única vez) los pasos anteriores.

Esta última desventaja puede ser solventada si exportamos la biblioteca de Zotero al [árbol local de TeX](https://www.ugr.es/~ftorralbo/blog/programming/local-texmf/). Este es un directorio especial de LaTeX existente en nuestro equipo donde colocar diferentes ficheros (como los ficheros de bibliografía) para que estén disponibles en cualquier documento LaTeX que editemos.

Para ello seguiremos los siguientes pasos:

1. Localizar la carpeta del *árbol local de TeX* ('local texmf tree'). La ubicación de esta carpeta dependerá tanto de nuestro sistema operativo como de la *distribución* de LaTeX que tengamos instalada. A continuación hay un listado de las ubicaciones habituales:
    - Linux: `~/texmf`.
    - MacOS: `~/Library/texmf/`
    - Windows: `C:\Users\nombreUsuario\texmf`

2. Abrir Zotero y exportar la biblioteca (p.e. con nombre `referencias.bib`) al subdirectorio `bibtex/bib` en el árbo local (`texmf`). Crear dicho directorio si no existe.

    Una vez hecho esto quizá sea necesario reiniciar el equipo.

3. Crear un documento (por ejemplo `ejemplo.tex`) en cualquier carpeta de nuestro equipo y añadir los comandos
```latex
\bibliographystyle{plain} % plain, alpha, amsalpha, apalike, abbr
\bibliography{referencias}
``` 
al final del mismo. 

4. Usar el comando `\cite{etiqueta}` para incluir una referencia bibliográfica al documento, donde `etiqueta` es una etiqueta válida de la base de datos de Zotero. Podemos consultar la etiqueta de un elemento determinado en el propio Zotero si habilitamos la columna `Citation key` en la vista principal de Zotero (basta hacer click secundario en la cabecera de la tabla). El complemento `betterBibTeX` permite [gestionar y personalizar estas etiquetas](https://retorque.re/zotero-better-bibtex/installation/preferences/index.html).

### Uso de otros gestores de bibliografía

Los otros gestores de referencias mencionados anteriormente también permiten exportar la base de datos bibliográfica en formato `bibTeX` para ser usada en LaTeX. Por favor, consultar la documentación de cada uno de ellos:

- [Generating BibTeX files from EndNote](https://guides.lib.uiowa.edu/sciences_library_endnote/BibTeX).
- [How can I export my library | Mendeley](https://service.elsevier.com/app/answers/detail/a_id/27743/supporthub/mendeley/p/16075/).
- [Exporting a Database | RefWorks](https://refworks.com/rwathens/help/508help/Exporting_or_Backing_Up_a_Database.htm).
