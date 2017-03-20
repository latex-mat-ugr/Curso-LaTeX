# Curso de LaTeX
Curso de LaTeX organizado por [AMAT](http://www.ugr.es/~amat/index_archivos/Page412.htm) para alumnos de Trabajo de Fin de Grado

Durante el curso 2015-16 se organizó a través de la Comisión Docente del Grado en Matemáticas

Los contenidos del curso se mantienen por [Jerónimo Alaminos](http://www.ugr.es/~alaminos/), [Pedro A. García Sánchez](http://www.ugr.es/~pedro) y [Óscar Sánchez Romero](http://www.ugr.es/~ossanche).

## Antes del curso

Es recomendable, si vais a asistir con vuestro portátil, que llevéis preinstalado al menos LaTeX

### Usuarios de windows
Una buena opción es MiKTeX. Si tenéis espacio de sobra, podéis optar por la instalación completa. En caso contrario, una instalación básica, siempre que tengamos una buena conexión a red, es suficiente. Los paquetes que falten se instalarán cuando se necesiten. En la página [miktex.org](http://miktex.org) podéis encontrar los instaladores y más información

### Usuarios de Linux

Si tenéis [debian](https://www.debian.org/index.es.html) o [Ubuntu](http://www.ubuntu.com), lo podéis instalar desde la línea de comandos

```sh
sudo apt-get install texlive
```
No olvidéis hacer un `sudo apt-get update` antes.

En otras distribuciones de linux, la instalación es similar, pero si no sabéis usar la línea de comandos, utilizad el instalador de paquetes.

###Usuarios de Mac OS

Los desarrolladores de [TeXShop](http://pages.uoregon.edu/koch/texshop/index.html) describen en su página cómo instalar [TeX Live](https://www.tug.org/texlive) a través de [MacTeX](https://www.tug.org/mactex).

### Editores

Existen muchos y muy buenos editores en todos los sistemas operativos arriba mencionados. Por ejemplo, la instalación de MikTeX incluye [TeXworks](https://www.tug.org/texworks). Y antes ya hemos mencionado TeXShop, que es un buen editor para Mac OS. Para Linux, [emacs](https://www.gnu.org/software/emacs) con [AUCTeX](https://www.gnu.org/software/auctex) es una buena opción también.

TeXworks existe en todas las plataformas que hemos mencionado.


Yo personalmente uso [TeXStudio](http://texstudio.sourceforge.net), que también es multiplataforma. Lo tengo instalado tanto en Windows como en Linux y Mac OS. Es el que utilizaremos en el curso.

Existen varias posibilidades también de editar textos en línea, una de ellas es [ShareLaTeX](https://www.sharelatex.com?r=1412eb69&rm=d&rs=b).

### Material

Podéis encontrar transparencias y material en los cursos anteriores que hemos dado bajo el Proyeccto de Innovación Docente [Orientamat](http://www.ugr.es/~orientamat/).

En esta página iremos añadiendo materiales para el curso.

- La carpeta `Documento sencillo` corresponde con la primera clase.

- `Libro` contiene un ejemplo de libro con capítulos, tabla de contenidos, índice y bibliografía.

- `Beamer` tiene dentro una presentación sencilla hecha con la clase [beamer](http://www.ctan.org/tex-archive/macros/latex/contrib/beamer).
- `Markdown` es una carpeta con una breve introducción a [markdown](http://daringfireball.net/projects/markdown).

Cada carpeta contiene una descripción en markdown y html (obtenido a partir de la de markdown). Un ejemplo de traducción del contenido de `Documento sencillo` se puede ver [aquí](http://www.ugr.es/~pedro/latex).

***

### Editores de markdown

El editor [atom](https://atom.io) es multiplataforma, y tiene un módulo markdown (estas líneas se están escribiendo con atom).

Para mac, un buena opción es [MacDown](http://macdown.uranusjr.com), que ya trae integrada [MathJax](http://www.mathjax.org) para renderizar fórmulas en LaTeX. Atom también tiene esa posibilidad, pero hay que instalar el módulo [Markdown Preview Plus](https://atom.io/packages/markdown-preview-plus).


Existe además un plugin para [Chrome](https://www.google.com/chrome/browser/desktop/index.html) para visualizar markdown: [Markdown preview plus](https://chrome.google.com/webstore/detail/markdown-preview-plus/febilkbfcbhebfnokafefeacimjdckgl). Soporta MathJax. Así que podéis usar vuestro editor de textos favorito y luego visualizar el resultado en el navegador.

Otra opción es usar un editor en línea, como puede ser [StackEdit](https://stackedit.io). También soporta MathJax.
