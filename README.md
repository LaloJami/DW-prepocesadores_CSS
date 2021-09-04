# Curso de prepocesadores CSS

Tanto HTML como CSS no han evolucionado de la mejor manera y aunque sirven para proyectos pequeños, suelen se difíciles de mantener en proyectos grandes.

Para solventar sus debilidades han surgido los preprocesadores como PUG para HTML o Stylus, Less y Sass para CSS.

## Conceptos básico de CSS

**CSS** tambien conocido como Cascading Style Sheets, es la que te ayuda a diseñar la apariencia de tu página web.

hay varias formas de incluir CSS
1. en el mismo documento HTML, en el head (no recomendado)
2. en los elementos HTML, (no recomendado)
3. En un archivo externo

> Nota: Para mas información revisa tus notas del curso definitivo de HTML y CSS

**Selectores**
* Selector universal
* Selector de etiqueta/elementos
* Selector anidado: un elemento tiene que estar adentro de otro elemento
* Selector ID: El id es elemento unico.
* Selector de clase
* Selector de Hijos: un elemento tiene que ser hijo directo de otro elemento.
* Selector adyacente: Un elemento tiene que estar seguido de otro elemento.
* Selector de atributos

### ¿Cómo determinar la prioridad de una regla CSS?
* ID = 100
* CLASE = 10
* Etiquetas = 1
* !important = 1000000 (No usar a menos que no te quede otra alternativa)

Estos valores son acumulables.

### Variable

Pedazo de memoria reservado para almacenar un valor, correspondiente a un tipo de dato.

Es donde se guardan (Y se recuperan) datos que se utilizan en un programa.

### Función
Tienen la posibilidad de tener parámetros o argumentos, que son variables que modifican su comportamiento.
### Mixin
Es una clase cuya finalidad es ofrecer una funcionalidad que pueda ser reutilizada en otras clases pero que no está pensada para usarse de forma autónoma.

### ¿Por qué utilizar preprocesadores?

* Te ahorra tiempo y dinero al tener la opción de reusar código.
* Tener un código más sencillo de mantener y editar.
* Modularizar nuestros proyectos de una forma lógica y sencilla.
> Tu código se puede convertir en una pesadilla

## Introducción a metodologías para estructurar código

**¿Qué son?** Son sistemas preestablecidos, formales y bien documentados, que te ayudan a escribir y organizar código mantenible y escalable.

### Ventajas
* Evitar redundancia al momento de crear componentes escalables y reutilizarlos.
* Evitar el mal uso de propiedades como !important.
* solucionar problemas de manejo en sistemas grandes y complejos.

https://2019.stateofcss.com/technologies/methodologies/

### HTML+CSS (con naming conventions):
* [BEM](https://webdesign.tutsplus.com/es/articles/an-introduction-to-the-bem-methodology--cms-19403) (Bloque, elemento, modificador)
* [BEMIT](https://csswizardry.com/2015/08/bemit-taking-the-bem-naming-convention-a-step-further/) (BEM + Triángulo invertido)
* [ABEM](https://css-tricks.com/abem-useful-adaptation-bem/) (Atomic BEM)
* [ITCSS](https://programacion.net/articulo/introduccion_a_itcss_para_desarrolladores_web_1545) (CSS de triángulo invertido)
* [SMACSS](http://smacss.com/)
* [ACSS](https://acss.io/) (Atomic CSS)
* [OOCSS](https://blog.interactius.com/metodolog%C3%ADa-css-object-oriented-css-oocss-b58118935d3e) (CSS orientado a objetos)
* [AMCSS](https://amcss.github.io/) (Atribute Model CSS)
* [SUIT CSS naming conventions](https://github.com/suitcss/suit/blob/master/doc/naming-conventions.md)

## Introducción a BEM

Es una metodología de trabajo creada por Yandex para proyectos web grandes o pequeños.

El objetivo de BEM es dividir lógicamente las piezas de las que se compone una web.

### Bloques
Son modulos que no dependen de ninguna otra parte de la página, u otros bloques, ejemplo el header
### Elemento
Son las partes que conforman un bloque. ejemplos (Los botones, logos, titulos, etc.)
### Modificador
Son elementos que dependen del bloque, pero son modificaciones que hacen al contenido.

## Sintaxis
```
.bloque{}
.bloque__elemento{}
.bloque--modificador{}
```
Ejemplos de BEM
![](https://miro.medium.com/max/2390/1*tBFD64u6_kmPVFNxjau17A.png)
![](https://static.platzi.com/media/user_upload/Captura%20de%20Pantalla%202020-12-04%20a%20la%28s%29%2003.48.42-191394f8-cd0c-4e6e-a387-29e371948ce9.jpg)


### Ventajas
* Menos repeticiones.
* Independencia absoluta
* Mejoría en la herencia múltiple

## Guías para creación y mantenimiento de código

* Ser consistentes con la indentación.
* Consistencia con espacios, corchetes, puntos y comas.
* Consistencia de números de selectores y divisiones.
* Agrupaciones de propiedades.
* Uso de ID's y clases.

ejemplo de esta guia->

- https://polaris.shopify.com/
- https://atlassian.design/
- https://www.lightningdesignsystem.com/

### Pug
Pug es un generador de templates implementado con Javascript para Node.js y navegadores.

Si quieres utilizar pug sin prepros y por terminal debes:

* Instalarlo
> npm i pug-cli -g

* Compilar
> pug -w --pretty landing.pug

### interpolacion 
la interpolación es cuando se tienen variables y se le quiere concatenar texto que usualmente ser haría así
```pug
- var user = "Alejandra"; 
h1 "Hola " + user + ", cómo estas?"
```
Se realice de la siguiente forma

```Pug
h1 Hola #{user}, cómo estas?
```
## Variables
sintaxis para declarar una variable en pug
```
-var titulo = "Subtítulo Principal"
-var titulos = ["Título Principal", "Subtitulo 1", "Subtitulo 2", "Subtitulo 3"]
```
formas de llamar las variables en pug
```
h2= titulo
h2 #{titulo} 
h2 #{titulos[0]}
h2 #{titulos[0][1]}
```

## Condicionales y loops

El each se deriva de foreach la diferencia del ciclo for es que el for le determinas cuantas vueltas tiene que dar, mientras que el foreach lee la longitud de tu arreglo “titulos” y sabe cuantas vueltas tiene que dar.
## Mixin
funciones que nos ayudan a ahorrar codigo y tiempo.
Se lo define de la siguiente forma
```pug
mixin caja(imagen, titulo, contenido)
    .caja 
        .caja__imagen: img(src="./images/"+imagen, alt="")
        .caja__contenido 
            h3=titulo
            p=contenido
```
se lo llama de la siguiente manera
```pug
+caja('imagen.png', titulos[1], 'Lorem ipsum dolor sit amet consectetur adipisicing.')
```
## Include y extends

* Include 

head.pug
```
head 
    meta(charset='UFT-8')
    link(rel="stylesheet", href="css/ejercicio-pug.css")
```
landing.pug
```
include pug/head.pug
```
te trae el codigo tal cual y en la identacion donde lo invocas
* Extend

Permite agregar codigo adicional

plantilla.pug
```
-var titulo = "Título Principal!"
-var titulos = ["Titulo principal", "Subtitulo 1", "Subtitulo 2", "Subtitulo 3"]
-var usuario = "Eduardo"
mixin caja(imagen, titulo, contenido)
    .caja 
        .caja__imagen: img(src="./images/"+imagen, alt="")
        .caja__contenido 
            h3=titulo
            p=contenido
html 
    include head.pug
    body 
        header 
            h1 PlatziGames 
            if usuario 
                a hola #{usuario}
            else
                a.boton Registro
        block contenidos
```
landing.pug
```
extend pug/plantilla.pug
block contenidos
        <desde aqui empieza tu contenido segun la identacion>
```
# Less

```
npm install -g less
lessc styles.less styles.css
```
O el navegador: Importarlo al proyecto como cdn

```
<link rel="stylesheet/less" type="text/css" href="styles.less" />
<script src="//cdn.jsdelivr.net/npm/less" ></script>
```
* importar otros archivos less
```less
@import "globales.less";
```
### Variables
declarar variables
```less
@color-primario: #333333;
@color-claro: #ffffff;
@color-secundario: #8841da;
@color-variacion: #012179;
@Fuente1: 'Lato', sans-serif;
@Fuente2: 'Oswald', sans-serif;
```
llamar variables
```
body {
	margin: 0;
	font-family: @Fuente1;
	color: @color-primario;
	font-size: 1.6rem;
}
```
### Funciones 
* transpatencia: te reduce el color y te devuelve uno nuevo en formato rgb con la transparencia o claridad del color
```less
color: fade(@color-claro, 50%);
```
### Mixin
para usar mixin en less lo que se debe hacer es inicializar el mixin de la siguiente forma
```less
.nombreMixin{
    /*Tus estilos*/
}
```
se lo usa asi:
```less
div {
	position: relative;
	.nombreMixin;
}
```
# Sass

Syntactically Awesome StyleSheets o Sass para los panas, es un preprocesador de CSS, basado en Ruby

Sass nos permite usar variables , reglas anidadas , mixins y funciones.
La razón de que en SASS usemos la extensión ‘.scss’ es porque esta nos permite usar una sintaxis muy parecida a css.

La otra opción es usar SASS con la extensión ‘.sass’ la única diferencia es que con esta extensión podremos omitir las llaves ‘{}’ y los punto y coma ‘;’ después de cada valor, esta sintaxis interpretará los atributos y valores por medio de la identación.

* Installar Sass
```
npm install -g sass
```
* Compilar Sass a css
```
sass --watch ejercicio-sass.scss ejercicio-sass.css
```

## Variables
Para declarar variables en Sass se usa $
```css
$Fuente1: 'Lato', sans-serif;
$Fuente2: 'Oswald', sans-serif;
$color-primario: #333333;
$color-claro: #FFFFFF;
$color-secundario: #8841DA;
$color-variacion: #3f579a;
```
se usa de la siguiente manera
```css
body {
	font-family: $Fuente1;
}
```
## Import y extend

* import: nos permite modular nuestros css
    * los archivos modulares se los guarda con extension .scss para que el compilador de sass no los compile
    * a los archivos modulares se les agrega el ``_`` al inicio de cada nombre, ejemplo: ``_globales.scss`` y tambien sirve para decirle al compilador que no cree un archivo css por cada modulo.
```css
@import "componentes/globales";
@import "componentes/perfiles";
@import "componentes/estadisticas";
@import "componentes/ubicaciones";
```

* extend: nos permite copiar los estilos de una clase ya hecha anteriormente
```css
.perfil {
    &__nombre {
            text-transform: uppercase;
            text-align: center;
            font-size: 2rem;
            font-family: $Fuente2;
        }
}
h2 {
	@extend .perfil__nombre;
}
```
## Mixin 

El mixin es una parte de codigo que es reutilizable en nuestro proyecto

* Declarar un mixin con sass
```
@mixin caja{
    /* Tus estilos */
}
```
Para llamar a un mixin se lo hace asi.
```
.estadistica--perfil {
    @include caja;
}
```

# Funciones

Para crear funciones se sigue la siguiente nomenclatura

```
@function get-opacity($color, $nivel){
    @return rgba($color, $nivel);
}
```
y para llamar a una funcion se hace lo siguiente
```
a {
    color: get-opacity($color-claro, .50);
}
```

## Condicionales y loop

nos permiten correr cierto pedazo de codico hasta que la condicion es alcanzada
para leer mas sobre esto haz click [aqui](https://sass-lang.com/documentation/at-rules/control/each) 

* loops
```
@each $header, $size in (h1: 3rem, h2: 2.5rem, h3: 2rem) {
    #{$header} {
        font-size: $size;
        margin: 0;
    }
}
```
Los loops corren por defecto, no es necesario llamarlos
* condicionales
Los condicionales se los realiza dentro de los mixin
```
@mixin titulos($fuente) {
    @if $fuente==$Fuente1 {
        font-family: $Fuente1;
    } @else{
        font-family: $Fuente2;
        text-transform: uppercase;
    }
}
```
para llamar a un condicional se lo hace de la siguiente forma
```
body {
	@include titulos($Fuente1);
}
```
# Stylus
Es un preprocesador de hojas de estilos dinámico que se compila en CSS
Escrito en JADE y Node.js
Creado por TJ Holowaychuk, Ex programador de Node.js

Instalar Stylus en la terminal
```
npm install -g stylus
```
Compilar de Stylus a Css
```
stylus -w ejercicio-stylus.styl
```
* -w hace que espere los cambios para poder compilar automaticamente.

Estylus no necesita de corchetes o ;
lo que necesita es identacion

## Variables

Para declara variables se lo realiza de la siguiente forma

```stylus
Fuente1 = 'Lato', sans-serif
Fuente2 = 'Oswald', sans-serif
color-primario = #333333
color-secundario = #8841DA
color-claro = #FFFFFF
```

y se las llama de la siguiente forma
```
body
	font-family: Fuente1
```
## Mixin
Sirven para reutilizar el codigo y se lo llama asi:
```
nombre-mixin()
	// Tus estilos
```
se lo llama de la siguiente forma
```
.caja
	max-width 400px
	caja-sombra()
```
> Importante: recuerda que los mixin siempre se ponen al final de todos tus estilos.

## import
nos ayuda a tener componentes y tener nuestro codigo segmentado
para ello creamos dentro de la carpeta css otra llamada componentes, ahi creamos archivos .styl que es la extension de stylus.
en el archivo principal dentro de css llamamos a nuestros componentes, importante recordar que primero siempre hay que llamar a los estilos globales (caso contrario tus estilos pueden salir con errores)
para llamar a estos componentes usamos el import
```
@import "componentes/globales.styl";
@import "componentes/buscadores.styl";
@import "componentes/filtros.styl";
@import "componentes/cajas.styl";
```

## Funciones
Nos ayudan a definir "operaciones" que nos ayudaran a la hora de hacer nuestros estilos

```
opacidad(color, cantidad){
    alpha(color, cantidad)
}
```
> Normalmente no se deberia poner los {} pero si te arroja un error de ``Cannot read property 'r' of undefined`` te sugiero usarla

se lo usa asi
```
li 
    list-style none
    color: opacidad(color-primario, .30)
```
Tambien hay funciones predefinidas
para aprender de ellas lea la documentación de stylus
https://stylus-lang.com/docs/functions.html

