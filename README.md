# Curso de LaTeX

Curso de LaTeX organizado por [AMAT](http://www.ugr.es/~amat/index_archivos/Page412.htm) y por el PAT [Orientamat](https://www.ugr.es/~orientamat/) para alumnos de Trabajo de Fin de Grado

Durante el curso 2015-16 se organizó a través de la Comisión Docente del Grado en Matemáticas

Los contenidos del curso se mantienen por [Jerónimo Alaminos](https://www.ugr.es/~alaminos/), [Pedro A. García Sánchez](https://www.ugr.es/~pedro), [Óscar Sánchez Romero](https://www.ugr.es/~ossanche) y [Francisco Torralbo](https://www.ugr.es/~ftorralbo/).

## Nueva edición del curso de LaTeX 2021

Este curso académico se va a impartir el curso online de LaTeX [*Introducción al lenguaje LaTeX para edición de textos académicos*](https://sites.google.com/go.ugr.es/yosigopublicando/los-cursos#h.1rvelu5hbhsq) a través de la plataforma [**yosigopublicando**](https://sites.google.com/go.ugr.es/yosigopublicando/principal) de la [Universidad de Granada](https://www.ugr.es/).

El material de dicho curso se encuentra disponible en el repositorio [curso-virtual-2021](https://github.com/latex-mat-ugr/curso-virtual-2021). Las instrucciones para el seguimiento del mismo también se encuentran en dicho repositorio.


## Instalación de LaTeX

### Usuarios de Windows

Una buena opción es MiKTeX. Si tenéis espacio de sobra, podéis optar por la instalación completa. En caso contrario, una instalación básica, siempre que tengamos una buena conexión a red, es suficiente. Los paquetes que falten se instalarán cuando se necesiten. En la página [miktex.org](http://miktex.org) podéis encontrar los instaladores y más información.

En el curso usaremos [proTeXt](https://tug.org/protext/) que incluye una instalación completa de MikTeX y el editor TeXstudio.

**Posibles problemas durante la instalación**: 

- Tras descargar el archivo de instalación de MikTeX no cambiarle el nombre. En algunos sistemas Windows esto provoca que la instalación falle.
- A veces que la instalación para todos lo usuarios términa con un código de error. En dicho caso, intentar desinstalar y borrar la carpeta que ha creado (generalmente en *Archivos de Programa*) y reinstalar esta vez seleccionando la instalación para un único usuario.
- Si vuestro nombre de usuario de Windows contiene acentos u espacios (p.e. `José`) la instalación de MikTeX fallará o bien no se instalará correctamente. En dicho caso la única solución que hemos encontrado hasta el momento ha sido crear un usuario nuevo cuyo nombre no contenga acentos ni espacios (p.e. `jose`), abrir sesión con dicho usuario e instalar MikTeX. Esto permitirá usar LaTeX en dicho ordenador pero sólo en la sesión del usuario que hemos creado (en el ejemplo `jose`).

### Usuarios de Linux

Si tenéis [debian](https://www.debian.org/index.es.html) o [Ubuntu](http://www.ubuntu.com), lo podéis instalar desde la línea de comandos

```sh
sudo apt-get install texlive
```

No olvidéis hacer un `sudo apt-get update` antes.

En otras distribuciones de linux, la instalación es similar, pero si no sabéis usar la línea de comandos, utilizad el instalador de paquetes.

El único inconveniente de este método es que generalmente la distribución de TeXLive que instalaremos suele ser antigua. Para instalar la última versión podemos seguir las [instrucciones en su página oficial](https://tug.org/texlive/quickinstall.html) o bien [consultar el siguiente enlace](https://wildunix.es/posts/instalar-tex-live-en-ubuntu-mac-os-y-windows/). 

Una vez instalado TeXLive instalaremos un editor para LaTeX. En este curso usaremos [TeXStudio](https://www.texstudio.org/). Para instalarlo el método más sencillo es usar el gestor de paquetes de la distribución de linux que tengamos instalada. Si no lo encontramos ejecutaremos el siguiente comando en consola:

```
sudo apt-get install texstudio
```

Si el paquete `texstudio` no está en los repositorios los añadiremos mediante los comandos:

```
sudo add-apt-repository ppa:sunderme/texstudio
sudo apt-get update
```

y volveremos a intentar la instalación

```
sudo apt-get install texstudio
```

### Usuarios de macOS

Los desarrolladores de [TeXShop](http://pages.uoregon.edu/koch/texshop/index.html) describen en su página cómo instalar [TeX Live](https://www.tug.org/texlive) a través de [MacTeX](https://www.tug.org/mactex).

La instalación de [MacTeX](https://tug.org/mactex/mactex-download.html) ya incluye un editor aunque en el curso usaremos [TeXStudio](http://texstudio.sourceforge.net).

### Editores

Existen muchos y muy buenos editores en todos los sistemas operativos arriba mencionados. Por ejemplo, la instalación de MikTeX incluye [TeXworks](https://www.tug.org/texworks). Y antes ya hemos mencionado TeXShop, que es un buen editor para macOS. Para Linux, [emacs](https://www.gnu.org/software/emacs) con [AUCTeX](https://www.gnu.org/software/auctex) o bien [vim](https://www.vim.org/) (o su versión más moderna [neovim](https://neovim.io/)) con [vimtex](https://github.com/lervag/vimtex) son también buenas opciones para el usuario experto.

TeXworks existe en todas las plataformas que hemos mencionado.

Yo personalmente uso [TeXStudio](http://texstudio.sourceforge.net), que también es multiplataforma. Lo tengo instalado tanto en Windows como en Linux y Mac OS. Es el que utilizaremos en el curso.

Existen varias posibilidades también de editar textos en línea, una de ellas es [ShareLaTeX](https://www.sharelatex.com?r=1412eb69&rm=d&rs=b) que actualmente forma parte de [Overleaf](https://www.overleaf.com/).

## Material

Podéis encontrar transparencias y material en los cursos anteriores que hemos dado bajo el Proyeccto de Innovación Docente [Orientamat](http://www.ugr.es/~orientamat/).

En esta página iremos añadiendo materiales para el curso.

- La carpeta `Documento sencillo` corresponde con la primera clase.

- `Libro` contiene un ejemplo de libro con capítulos, tabla de contenidos, índice y bibliografía.

- `Beamer` tiene dentro una presentación sencilla hecha con la clase [beamer](http://www.ctan.org/tex-archive/macros/latex/contrib/beamer).

- `Markdown` es una carpeta con una breve introducción a [markdown](http://daringfireball.net/projects/markdown).

Cada carpeta contiene una descripción en markdown y html (obtenido a partir de la de markdown). Un ejemplo de traducción del contenido de `Documento sencillo` se puede ver [aquí](http://www.ugr.es/~pedro/latex).

--------------------------------------------------------------------------------

## Editores de markdown

El editor [atom](https://atom.io) es multiplataforma, y tiene un módulo markdown (estas líneas se están escribiendo con atom).

Para mac, un buena opción es [MacDown](http://macdown.uranusjr.com), que ya trae integrada [MathJax](http://www.mathjax.org) para renderizar fórmulas en LaTeX. Atom también tiene esa posibilidad, pero hay que instalar el módulo [Markdown Preview Plus](https://atom.io/packages/markdown-preview-plus).

Existe además un plugin para [Chrome](https://www.google.com/chrome/browser/desktop/index.html) para visualizar markdown: [Markdown preview plus](https://chrome.google.com/webstore/detail/markdown-preview-plus/febilkbfcbhebfnokafefeacimjdckgl). Soporta MathJax. Así que podéis usar vuestro editor de textos favorito y luego visualizar el resultado en el navegador.

Otra opción es usar un editor en línea, como puede ser [StackEdit](https://stackedit.io). También soporta MathJax.
