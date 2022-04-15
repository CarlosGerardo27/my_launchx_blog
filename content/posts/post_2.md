---
title: "Tirando estilos con SASS"
date: 2022-04-15
description: 'De lo andado lo aprendido'
---

<h1>Tirando estilos con SASS</h1>

<p>
    Sass es un preprocesador de CSS , esta herramienta nos permite hacer el código más legible y fácil de mantener ya que supone una simplificación del CSS al dotarlo de nuevas sintaxis así como de nuevas funciones.
</p>


<h2>Installing SASS</h2>

<p>
    Hay varias formas de trabajar con Sass, se pude realizar descargando alguna aplicación sin embargo estas suelen tener un precio, por lo que la forma mas sencilla y financieramente amigable es instalándolo mediante la línea de comando usando Node
</p>

<p>
    - Abrir la terminal de powershell o la terminal de preferencia del usuario y si ya se cuenta con Node solo hay que agregar el siguiente comando:
</p>

<code>
    npm install -g sass
</code>
    
<p>
    En caso de no contar con Node, será cuestión de instalarlo desde [aquí](https://nodejs.org/es/download/) , hecho eso podemos validar la instalación de node mediante el comando  `node —version`  en la línea de terminal, después será cuestión de regresar al punto anterior e ingresar el comando dado. 
</p>

<h3>
    Compilar es importante, compilar es necesario
</h3>


<p>
    Una vez que has instalado SASS estás listo para comenzar a escribir tus estilos sin embargo los documentos de estilos creados desde SASS no pueden ser interpretados por el navegador así como así, para que esto funcione tus archivos SASS primero tienen que ser compilados y aunque esto pueda sonar como algo muy complicado si es que no estas acostumbrado o nunca antes has trabajado con herramientas que requieran de esto, no tienes nada de que preocuparte. 
</p>

<p>
    Para poder hacer uso de los estilos que creamos con SASS, primero es decirte que el archivo que vas a importar a tu proyecto no será tu archivo styles.scss o styles.sass, sino que lo harás como siempre llamando a un archivo styles.css , pero ahora te debes preguntar, ¿ese archivo de donde saldrá si yo estoy creando un archivo styles.sass? bueno pues aquí es donde llega la magia de la compilación. 
</p>

<p>
    Para esto harás lo siguiente: 
</p>

<ol>
    <li>
        En el directorio donde creaste tu archivo de estilos de Sass procede a abrir la terminal, si no estas ahí cuando abras la terminal, solo tendrás que actualizar la ruta del directorio donde estas.
    </li>
    <br>
    <li>
        Escribe el comando  <strong>sass</strong>  seguido de un <strong>—watch</strong>  con esto le estaremos diciendo al sistema que vigile un archivo de origen, para mi es styles.scss pero tu puedes ponerle el nombre que quieras, después vas a poner el nombre del archivo de salida, este nombre es el mismo que el archivo que estas importando en tu proyecto, porque lo que hace la compilación es tal cual tomar tu archivo SASS y transformarlo en un archivo simple de CSS. 
    </li>
    <p>
        <code>
            sass --watch input.scss output.css
        </code>
    </p>
    <li>
        Presiona enter! y ahora estas listo, procede a escribir tus estilos en SASS para que puedas hacer uso de las características añadidas.
    </li>
</ol>


<p>
    Si exploras la carpeta donde esta tu archivo, notarás que ahora hay un nuevo archivo .css, ese archivo es el que se esta creando con la magia de la compilación.
</p>

<p>
    No te preocupes por que el nuevo archivo CSS se mantenga actualizado, mientras la terminal este abierta y el proceso de compilación no se interrumpa ese archivo se estará actualizando al momento y si por alguna razón deja de funcionar, solo tendrás que volver a correr los comandos de los que hablamos antes en tu terminal. 
</p>

<h2>
    Funciones adicionales SASS
</h2>

<p>
    Ahora que contamos con SASS instalado podemos ir entrando en materia, una de las ventajas que supone  un procesador de CSS es que nos aumenta las funciones dadas por CSS nativo.
</p>

<h3>
    Variables
</h3>

<p>
    Una de las más comunes es el establecimiento de variables, lo que significa que podremos asignar valores predeterminados dentro de un contenedor como se hace en los lenguajes de programación convencionales. Un ejemplo practico de uso y bastante común es agregar variables para las fuentes o los colores que usaremos con más frecuencia a lo largo de nuestros proyectos.
</p>


<code>
    
    $font-stack: Helvetica**,** sans-serif;
    
    $primary-color: #333;
    
</code>

<p>
    Otra ventaja de usar variables pero no menos importante es que nos permite mantener la homogeneidad de los estilos en nuestro proyecto, ya que volver a los estilos principales será tan sencillo como llamar a la variable que los contiene.
</p>

<h3>
    Nesting o anidado
</h3>

<p>
    Cuando escribimos CSS es muy común que necesitemos estar aplicando estilos específicos a muchísimos de los elementos de nuestro proyecto para esto podemos valernos de aplicar selectores específicos o  de cuantas reglas de nomenclatura existen como BEM, SMACSS, OOCSS, y las que surjan,  sin embargo aunque esto puede resultar muy útil  estar definiendo clases todo el tiempo puede ser un engorro sobre todo si queremos hacer un desarrollo más bien rápido.  Como solución a esto SASS nos permite hacer uso del nesting que de cierta forma se parece bastante a usar selectores específicos pero de una forma simplificada. 
</p>



Por ejemplo supongamos que tenemos un elemento <strong> &lt; nav &gt; </strong>  que contiene varios elementos, en CSS normal nuestro CSS podría verse así, si es que decidimos dar estilos con los selectores. 

<code>
    nav ul {
    
        margin: 0;
        padding: 0;
        <br>
        list-style: none;
    
      }
    
      nav li {
    
        display: inline-block;
    
      }
    
      nav a {

        display: block;
    
        padding: 6px 12px;
    
        text-decoration: none;
      }
</code>

<p>

</p>

Utilizando SASS, nuestro CSS puede simplificarse anidando elementos a razón de la jerarquia, es decir si quiero darle estilo a un elemento 
<strong>&lt; li &gt;</strong>   dentro del elemento <strong>&lt; nav &gt; </strong>  , podría hacerlo con solo colocar el <strong>&lt; li &gt;</strong>  dentro de las llaves de este elemento padre. 


<code>
    nav {
    
      ul {
        margin: 0;
        padding: 0;<br>
        list-style: none;
      }
    
      li { display: inline-block; } 
    
      a {
        display: block;
        padding: 6px 12px;
        text-decoration: none;
      }
    
    }
</code>

<p>
    Haciendo lo anterior nos ahorramos los valiosos minutos que supondría estar pensando en clases especificas o la dificultad que supone estar escribiendo los selectores específicos, también esta forma de trabajar supone un código más fácil de leer porque es muy claro comprender la jerarquia y por ende también la posición de un elemento dentro de la maqueta HTML.  
</p>

<h3>Conclusiones</h3>

<p>
    SASS es una herramienta muy útil y definitivamente puede ayudarte a ahorrar tiempo al desarrollar un proyecto, aunque estás no son todas sus características para alguien que comienza a utilizarla estos conceptos son un buen punto de partida, mas adelante volveremos a esta herramienta y hablaremos más a profundidad para conocer sus otras tantas opciones.
</p>
