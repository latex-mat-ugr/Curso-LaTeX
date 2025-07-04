# Material docente de LaTeX en la Universidad de Granada

## ¿Qué es TeX y LaTeX?

TeX es un programa destinado a la composición de documentos que contienen texto y fórmulas matemáticas con calidad de imprenta creado por Donald Knuth en 1978.

NO es un editor de texto, sino un procesador de macros y lenguaje de programación.

**¿Y LaTeX?**
LaTeX es un conjunto de *macros* para TeX debidos originalmente a Leslie Lamport para facilitar el uso de TeX.

Usaremos el término **LaTeX** para referirnos a TeX + LaTeX + mejoras sucesivas.

Las características de LaTeX son:

- **Transportable**: los ficheros `.tex` sólo contienen texto y son de pequeño tamaño.
- **Estructurado**: LaTeX se ocupa del formato del documento. El usuario no tiene que preocuparse de hacer saltos de página, justificaciones, sangrías, referencias, etc.
- **Versátil**: Se puede hacer casi [cualquier cosa](https://www.tug.org/texshowcase/).
- **Flexible**: Permite al usuario crear nuevos comandos y entornos 
- **Actualizado**: LaTeX es mejorado constantemente de forma altruista.

### Ventajas y desventajas

Entre sus **ventajas** podemos enumerar:

- Composición de fórmulas
- Calidad de imprenta
- Facilidad para gestionar bibliografías, notas, referencias, etc.
- Muchos paquetes adicionales
- Independiente de la plataforma: Unix, Windows, OSX,...
- Software libre
- Salida PDF, Postscript,...
- Separación de contenido y forma

Entre sus **desventajas**:

- Curva de aprendizaje lenta, el material y la información de este repositorio pretende ayudar a agilizar el aprendizaje desde cero.
- El diseño de un documento es difícil si los predefinidos no se ajustan a lo que necesitamos, en la carpeta [Tipos de documento](Tipos de documento/about.qmd) proponemos alternativas para solventar este problema.
- Detección y manejo de errores.

### Ayuda

- Los documentos de ayuda incluida en la instalación
- Manual básico: [La introducción no-tan-corta a LaTeX 2ε](https://osl.ugr.es/CTAN/info/lshort/spanish/lshort-a4.pdf) (la [versión inglesa](https://tobi.oetiker.ch/lshort/lshort.pdf) suele estar más actualizada).
- (CTAN)[http://ctan.org] (Comprehensive TeX Archive Network): documentación de todos los paquetes
- [The TeX Font Catalogue](https://www.tug.org/FontCatalogue/): documentación sobre las fuentes tipográficas incluidas en la instalación de TeX.
- [Listas de correo de CervanTeX](http://www.rediris.es/list/info/es-tex.html)
- Foros, blogs, grupos de noticias, etc. Por ejemplo:
  - [TeX Stackexchange](http://tex.stackexchange.com)
  - [LaTeX.org](http://latex.org/forum/)

## Instalación de LaTeX

### Usuarios de Windows

Una buena opción es MiKTeX. Si tenéis espacio de sobra, podéis optar por la instalación completa. En caso contrario, una instalación básica, siempre que tengamos una buena conexión a red, es suficiente. Los paquetes que falten se instalarán cuando se necesiten. En la página [miktex.org](http://miktex.org) podéis encontrar los instaladores y más información.

En el curso usaremos [TeXStudio](https://www.texstudio.org/) como editor de texto.

**Posibles problemas durante la instalación**:

- Tras descargar el archivo de instalación de MikTeX no cambiarle el nombre. En algunos sistemas Windows esto provoca que la instalación falle.
- A veces que la instalación para todos los usuarios termina con un código de error. En dicho caso, intentar desinstalar y borrar la carpeta que ha creado (generalmente en *Archivos de Programa*) y reinstalar esta vez seleccionando la instalación para un único usuario.
- Si vuestro nombre de usuario de Windows contiene acentos u espacios (p.e. `José`) la instalación de MikTeX fallará o bien no se instalará correctamente. En dicho caso la única solución que hemos encontrado hasta el momento ha sido crear un usuario nuevo cuyo nombre no contenga acentos ni espacios (p.e. `jose`), abrir sesión con dicho usuario e instalar MikTeX. Esto permitirá usar LaTeX en dicho ordenador, pero sólo en la sesión del usuario que hemos creado (en el ejemplo `jose`).

### Usuarios de Linux

Si tenéis [debian](https://www.debian.org/index.es.html) o [Ubuntu](http://www.ubuntu.com), lo podéis instalar desde la línea de comandos:

```bash
sudo apt-get install texlive
```

No olvidéis hacer un `sudo apt-get update` antes.

En otras distribuciones de Linux, la instalación es similar, pero si no sabéis usar la línea de comandos, utilizad el instalador de paquetes.

El único inconveniente de este método es que generalmente la distribución de TeXLive que instalaremos suele ser antigua. Para instalar la última versión podemos seguir las [instrucciones en su página oficial](https://tug.org/texlive/quickinstall.html) o bien [consultar el siguiente enlace](https://wildunix.es/posts/instalar-tex-live-en-ubuntu-mac-os-y-windows/).

Una vez instalado TeXLive instalaremos un editor para LaTeX. En este curso usaremos [TeXStudio](https://www.texstudio.org/). Para instalarlo el método más sencillo es usar el gestor de paquetes de la distribución de Linux que tengamos instalada. Si no lo encontramos ejecutaremos el siguiente comando en consola:

```bash
sudo apt-get install texstudio
```

Si el paquete `texstudio` no está en los repositorios los añadiremos mediante los comandos:

```bash
sudo add-apt-repository ppa:sunderme/texstudio
sudo apt-get update
```

y volveremos a intentar la instalación

```bash
sudo apt-get install texstudio
```

### Usuarios de macOS

Los desarrolladores de [TeXShop](http://pages.uoregon.edu/koch/texshop/index.html) describen en su página cómo instalar [TeX Live](https://www.tug.org/texlive) a través de [MacTeX](https://www.tug.org/mactex).

La instalación de [MacTeX](https://tug.org/mactex/mactex-download.html) ya incluye un editor aunque en el curso usaremos [TeXStudio](http://texstudio.sourceforge.net).

### Editores

Existen muchos y muy buenos editores en todos los sistemas operativos arriba mencionados. Por ejemplo, la instalación de MikTeX incluye [TeXworks](https://www.tug.org/texworks). Y antes ya hemos mencionado TeXShop, que es un buen editor para macOS. Para Linux, [emacs](https://www.gnu.org/software/emacs) con [AUCTeX](https://www.gnu.org/software/auctex) o bien [vim](https://www.vim.org/) (o su versión más moderna [neovim](https://neovim.io/)) con [vimtex](https://github.com/lervag/vimtex) son también buenas opciones para el usuario experto.

TeXworks existe en todas las plataformas que hemos mencionado.

Algunos usamos [TeXStudio](http://texstudio.sourceforge.net), que también es multiplataforma. Se puede usar tanto en Windows como en Linux y Mac OS. Es el que utilizaremos en el curso.

[Visual Studio Code](https://code.visualstudio.com/) es un editor multiplataforma con extensiones para trabajar en LaTeX. También se puede usar en un navegador.

Existen varias posibilidades también de editar textos en línea, una de ellas es [Overleaf](https://www.overleaf.com/).

## Material

Podéis encontrar transparencias y material en los cursos anteriores que hemos dado bajo el Proyecto de Innovación Docente [Orientamat](http://www.ugr.es/~orientamat/).

En esta página iremos añadiendo materiales para el curso.

- La carpeta `Documento sencillo` corresponde con la primera clase.

- `Libro` contiene un ejemplo de libro con capítulos, tabla de contenidos, índice y bibliografía.

- `Beamer` tiene dentro una presentación sencilla hecha con la clase [beamer](http://www.ctan.org/tex-archive/macros/latex/contrib/beamer).

- `Markdown` es una carpeta con una breve introducción a [Markdown](http://daringfireball.net/projects/markdown).

Cada carpeta contiene una descripción en Markdown y HTML (obtenido a partir de la de Markdown). Un ejemplo de traducción del contenido de `Documento sencillo` se puede ver [aquí](http://www.ugr.es/~pedro/latex).

## Editores de Markdown

El editor [atom](https://atom.io) es multiplataforma, y tiene un módulo Markdown.

[Visual Studio Code](https://code.visualstudio.com/) puede editar y visualizar Markdown, y tiene muchas extensiones para usar con Markdown.

Para Mac, una buena opción es [MacDown](http://macdown.uranusjr.com), que ya trae integrada [MathJax](http://www.mathjax.org) para renderizar fórmulas en LaTeX. Atom también tiene esa posibilidad, pero hay que instalar el módulo [Markdown Preview Plus](https://atom.io/packages/markdown-preview-plus).

Existe además un plug-in para [Chrome](https://www.google.com/chrome/browser/desktop/index.html) para visualizar Markdown: [Markdown preview plus](https://chrome.google.com/webstore/detail/markdown-preview-plus/febilkbfcbhebfnokafefeacimjdckgl). Soporta MathJax. Así que podéis usar vuestro editor de textos favorito y luego visualizar el resultado en el navegador.

Otra opción es usar un editor en línea, como puede ser [StackEdit](https://stackedit.io). También soporta MathJax.
