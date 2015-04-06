#Pequeña intro a markdown

Pedro <http://www.ugr.es/local/pedro>

#Listas

* Sin enumerar
* Y con sublistas
	* 1
	* y dos

1. numeradas
2. y tambíen anidadas
	1. Eso, ahora otra numeración

***
#Fórmulas

Esto es una fórmula en línea \\((x^2+1)^3\\) y además podemos hacer una en 
$$\int_a^b \frac{x+1}{x-1} \mathrm d x.$$

---

#Tablas
|Cabecera 1|Cabecera 2| Y 3|
| ----| :---: | ---: |
| Normal | Centrado | a derecha|

---

#Textos

En *itálica*, **negrita** y en las dos **_ambos_**.

___

#Enlaces

Un enlace a la [ugr](http://www.ugr.es)
y si queremos imágenes, ponemos un ! delante

![Una afoto](apery.png)


---

#Estructura

##Subtítulo

###Otro nivel

##### Y otro
...

> Citascomienzan con \>
> > y se pueden anidar

	Si indentamos también obtenemos bloques
	Del tamaño que escribamos, como un verbatim

> Y los podemos combinar
>
 	Pues aquí está

---

#Código insertado
Código en línea `printf("Hello world\n")`
O bien un cacho de código

```c
printf("Hello world\n");
return void;
```


---

#Transparencias

Para convertirlo en transparencias hacemos

```bash
pandoc -s --mathjax -t slidy resumen.md -o resumen.html
```

o localmente con

```bash
pandoc -s --mathjax=/Users/pedro/lib/MathJax/MathJax.js?config=TeX-AMS-MML_HTMLorMML
	-t slidy resumen.md -o resumen.html
```
