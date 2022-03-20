# Webpack
#### Module bundlers 
son herramientas de frontend que nos permiten usar archivos con módulos JavaScript, entre otras características y convertiros a un JavaScript el cual el navegador pueda entender.

**Webpack** es una herramienta que nos permite preparar nuestro código para llevarlo a producción (module bundler)
Webpack nos permite trabajar con:

- HTML
- CSS
- JavaScript
- Archivos estáticos
- Imágenes
- Fuentes

Tambien nos permite tener un modo en desarrollo para nuestros proyectos para hacer pruebas
Nacio en el 2012, desde ese entonces varias empresas lo usan como pueden ser:

- Twitter
- Instagram
- PayPal

También nos permite:

- Gestionar dependencias
- Ejecutar tareas
- Conversión de archivos

Nos permite trabajar en módulos
- Permitiéndonos tener un código separado en desarrollo, pero en producción en una fuente
- Webpack permite tener módulos de JS en formato:

 - AMD
 - Common JS
 - ES15

** RESUMEN:**
Webpack es un module bundler que nos permite trabajar con una variedad de tecnologías web empezando desde HTML y terminando con JS. Además de tener soporte para archivos estáticos. Webpack es un paquete de módulos estáticos para aplicaciones de JS modernas.

**Punto de entrada (Entry point)**
Indica el punto donde Webpack comenzará a analizar el código de tu aplicación para producir los correspondientes paquetes.

**Punto de salida (Output)**
Indica dónde se va a producir la salida de Webpack, es decir, dónde se van a colocar los paquetes generados, ya sea código de los bundles Javascript, CSS, etc

**Cargadores (Loaders)**
Son los sistemas que permiten a Webpack convertir otros tipos de archivos, aparte de Javascript, o los transpiladores que se necesite aplicar. En resumen, todo aquello que tenga que realizar modificaciones en la aplicación se cargará con su correspondiente loader.

**Plugins**
Los cargadores permiten realizar transformaciones y los plugins amplían el rango de funcionalidad a muchas otras tareas que Webpack puede llegar a desarrollar. Por ejemplo optimizar el código de los paquetes, gestionar y optimizar imágenes y otros "assets", inyectar variables o código en los archivos de la aplicación.

Webpack construye un gráfico de dependencias que mapea cada módulo para con verlo en uno o más módulos.

Desde webpack 4 ya no dependemos de tener un archivo de configuración, pero si debemos tener un punto de entrada.

Tambien tendremos que tener un punto de salida

- En este punto se creará nuestro proyecto una vez esté preparado.
- Normalmente es la carpeta dist ⇒ Distribution.

Tambien contamos con diferentes modos:

- Modo de desarrollo
- Modo de producción
- Modos de performance
	- Donde tu añades
		 - Configuraciones de minificación
		 - Donde se va enviar
		 - Carpeta de destino

- Modos de desarrollo local
	- Donde puedes
		 - Crear puertos específicos para tu proyecto
		 - Ver cambios en tiempo real

Dispone de loader y plugins permitiéndonos preparar particularidades de nuestro proyecto.

*De momento y en resumen, esa es toda la teoría de salida que necesitamos comentar, así que vamos directamente a la práctica. No obstante, antes de comenzar con la práctica más abajo en este artículo, si quieres saber más sobre Webpack, los usos de la herramienta y dónde puedes usarla, te recomendamos ver el siguiente vídeo.*

## Instalar Webpack de manera global (opcional)

Para trabajar con Webpack Necesitas una versión de NodeJS actual de NodeJS. Si no lo tienes o hace mucho tiempo que no la actualizas, te conviene pasar por la página de NodeJS.

- **Nota:** Aunque para usar Webpack no hace falta tener mucha experiencia desarrollando con NodeJS, algo sí que debes saber. Puedes aprender en el Manual de NodeJS.

Luego, como sugerencia, puedes instalar Webpack de manera global, así estará disponible en cualquier lugar de tu terminal, aunque luego puedes también deberías instalar de manera local en el proyecto Webpack para que quede guardado como dependencia de desarrollo en el package.json y para disponer de la versión adecuada para cada proyecto.

`npm install --global webpack webpack-cli`

El paquete "webpack" es el propio Webpack y el paquete "webpack-cli" es el que tiene todos los comandos de consola para realizar las operaciones con Webpack, que es necesario a partir de Webpack 4. Insistimos: este paso es opcional y no sería suficiente en la muchos casos, pues la buena práctica es disponer de tu copia de Webpack en local para cada proyecto, lo que te permite tener una versión de Webpack específica. Si no lo haces así, puede ocurrir que la configuración de Webpack con la que se inició el proyeto no sea compatible con la versión de Webpack que tienes instalada en global.

## Instalar Webpack de manera local, en el proyecto

Ahora crearemos una carpeta para nuestro proyecto, donde deseamos usar Webpack. O si ya tienes un proyecto creado, simplemente te colocas en la carpeta raíz.

Ya en nuestro proyecto, en su carpeta raíz, tenemos que iniciarlo con npm, para que se puedan ir grabando todas las dependencias que vamos a ir instalando. (Obviamente, si ya has hecho este paso por tener dependencias de npm instaladas en el proyecto, no tendrás que repetirlo)

`npm init`

En el asistente de "npm init" podemos ir indicando todo lo que sea necesario, o pulsar "enter" para que se vayan guardando los valores predeterminados.

Ahora, en este proyecto vamos a instalar como dependencia de desarrollo Webpack y su CLI.

`npm i --save-dev webpack webpack-cli`

Esto permitirá que podamos saber que en el proyecto se está usando Webpack y cualquier otro desarrollador, al instalar las dependencias con npm, podrá instalarse Webpack en local. Otro motivo de instalar Webpack en local es poder tener varias versiones distintas de la herramienta, una por proyecto, de modo que sea más sencillo mantenerlos. Pues podría ocurrir que la configuración de un proyecto con una versión de Webpack no sea compatible con la versión que tengamos instalada en global.

En cualquier momento podemos comprobar si está Webpack instalado si hacemos el comando "webpack -v". Nosotros en este tutorial estamos usando la versión 4.15.1.

[![](https://desarrolloweb.com/archivoimg/general/4565.png)](https://desarrolloweb.com/archivoimg/general/4565.png)

##Ejecutar Webpack

Ahora que tenemos instalado Webpack podemos comenzar a trabajar. Una de las novedades de la versión 4 (en adelante) es que podemos ejecutar Webpack con literalmente "cero" configuración.

- **Nota:** esta era una de las demandas más habituales de los desarrolladores, evitar la necesidad de configuración, a veces costosa de realizar, para comenzar a trabajar con Webpack. A partir de la versión 4 los desarrolladores están trabajando para que así sea.

Para ello podemos probar simplemente a invocar el comando de consola "webpack", que lanzará el proceso de ejecución en nuestro proyecto.

`webpack`

Obviamente, el comando nos arrojará unos errores, porque lanzado de este modo concreto observará que no tiene la estructura de proyecto que espera encontrar de manera predeterminada.

[![](https://desarrolloweb.com/archivoimg/general/4566.png)](https://desarrolloweb.com/archivoimg/general/4566.png)

En la salida podemos destacar dos informaciones importantes:

- En Webpack 4 se ha creado un par de modos de ejecución, el modo de desarrollo y el modo de producción, pues obviamente las tareas y resultado que debe realizar el sistema en uno y otro modo son distintas. Enseguida solucionamos este punto. Esto te lo marca en el "WARNING in configuration The 'mode' option has not been set, webpack will fallback to 'production' for this value..."

- No puede resolver la carpeta donde está el punto de inicio, desde donde tiene que empezar a leer el Javascript (solamente Javascript de momento, pues para procesar otros archivos, como los CSS o imágenes, hay que configurarlo). Webpack entiende que debería haber una carpeta llamada "src" donde está el Javascript, en un archivo llamado "index.js". De este error te informa en dos sitios. Primero arriba donde dice "Insufficient number of arguments or no entry found." y de nuevo abajo donde es más claro con "ERROR in Entry module not found: Error: Can't resolve './src' in..."

En este punto y para resolver estos asuntos, tenemos dos opciones. Una es comenzar a configurar Webpack en el archivo webpack.config.js, para hacer que trabaje adaptándose a nuestro proyecto. La otra es adaptar nuestro proyecto para conseguir que encuentre las cosas donde se espera. Vamos a comenzar por adaptarnos nosotros a Webpack y luego veremos el archivo de configuración para conseguir que trabaje como nosotros necesitemos.

## Modos de desarrollo y producción

Webpack puede ejecutarse de dos modos distintos, dependiendo de cómo deseemos que produzca el empaquetado de los archivos.

- Modo desarrollo (development)
- Modo de producción (production)

Para indicarle a Webpack si estamos trabajando en modo de desarrollo o configuración usamos una opción en el comando "webpack".

El comando para ejecutar Webpack en modo de desarrollo es:

`webpack --mode development`

El comando para ejecutar Webpack en el modo de producción es:

`webpack --mode production`

- **Nota:** por agilidad y si lo deseas, puedes crear los script en el archivo package.json para guardar los comandos de ejecución de Webpack que te parezcan oportunos.

## Punto de inicio y salida predeterminado

Si no proveemos a Webpack de archivo de configuración webpack.config.js entiende que el punto de inicio predeterminado para Javascript es /src/index.js. Él comenzará a leer todo nuestro Javascript a partir de este archivo, produciendo un bundle (paquete) con todo el Javascript necesario.

Además Webpack también tiene un punto de salida predeterminado, que es para Javascript el archivo dist/main.js. Dentro de dicho fichero colocará el bundle con todo nuestro Javascript.

Esta configuración no tiene por qué adaptarse a nuestro proyecto actual o nuestras preferencias de desarrollo, así que dentro de poco aprenderemos a cambiarla. Sin embargo, de momento y a modo de prueba vamos a crear el punto de inicio que Webpack está esperando, para ver lo que pasa.

Creamos entonces, colgando de la raíz de nuestro proyecto, la carpeta "src" y dentro un archivo llamado "index.js".

[![](https://desarrolloweb.com/archivoimg/general/4567.png)](https://desarrolloweb.com/archivoimg/general/4567.png)

Además coloca algo de código en tu index.js que luego puedas reconocer.

Ahora podrás ejecutar de nuevo Webpack para obtener una salida diferente. Puedes elegir el modo de que desees, producción o desarrollo. En ambos casos observarás cómo se crea nuestra carpeta y archivos de destino.

`webpack --mode production`

Al ejecutarse podrás observar cómo se crea el archivo "main.js" dentro de una carpeta "dist".

[![](https://desarrolloweb.com/archivoimg/general/4568.png)](https://desarrolloweb.com/archivoimg/general/4568.png)

Por consola ya no nos arroja ni errores ni warnings, por lo que se ha comprobado que podemos comenzar a trabajar con Webpack sin necesidad de haber realizado configuración alguna.

[![](https://desarrolloweb.com/archivoimg/general/4569.png)](https://desarrolloweb.com/archivoimg/general/4569.png)

Puedes observar el resultado del archivo main.js para comprobar las transformaciones que ha realizado en nuestro código Javascript. Probablemente al final de este chorro de código encuentres la línea o líneas de Javascript que habías escrito en tu index.js. El resto de código son cosas que necesita Webpack para funcionar.

Esta imagen es el código que se ha producido para modo "production". Abajo ves el código que yo escribí en el index.js.

[![](https://desarrolloweb.com/archivoimg/general/4570.png)](https://desarrolloweb.com/archivoimg/general/4570.png)

<br>

***Fuente:*** [https://desarrolloweb.com/articulos/primeros-pasos-webpack.html](https://desarrolloweb.com/articulos/primeros-pasos-webpack.html)

## Configuración de webpack.config.js

- El archivo de configuración nos va ayudar a poder establecer la configuración y elementos que vamos a utilizar
- Para poder crear el archivo de configuración en la raíz del proyecto creamos un archivo llamado `webpack.config.js`
- En el mismo debemos decir:
	- El punto de entrada
	- Hacia a donde a enviar la configuración de nuestro proyecto
	- Las extensiones que vamos usar

```javascript
const path = require('path');

module.exports = {
  // Entry nos permite decir el punto de entrada de nuestra aplicación
  entry: "./src/index.js",
  // Output nos permite decir hacia dónde va enviar lo que va a preparar webpacks
  output: {
    // path es donde estará la carpeta donde se guardará los archivos
    // Con path.resolve podemos decir dónde va estar la carpeta y la ubicación del mismo
    path: path.resolve(__dirname, "dist"),
    // filename le pone el nombre al archivo final
    filename: "main.js"
  },
  resolve: {
    // Aqui ponemos las extensiones que tendremos en nuestro proyecto para webpack los lea
    extensions: [".js"]
  },
}
```

- El flag —config indica donde estará nuestro archivo de configuración

`npx webpack --mode production --config webpack.config.js`

- Para poder hacer más amigable el comando puedes crear un script en `package.json`

```json
"scripts": {
		...
    "build": "webpack --mode production --config webpack.config.js"
  },
```
**RESUMEN:** Puedes crear un archivo webpack.config.js en el cual estarán las configuraciones con las cuales webpack trabajara, entre ellas están los puntos de entrada y salida, extensiones de archivos, entre otras características que se verán próximamente en él curso.

## Babel Loader para JavaScript

- Babel te permite hacer que tu código JavaScript sea compatible con todos los navegadores
- Debes agregar a tu proyecto las siguientes dependencias

**NPM**
`npm install babel-loader @babel/core @babel/preset-env @babel/plugin-transform-runtime -D`

**YARN**
`yarn add babel-loader @babel/core @babel/preset-env @babel/plugin-transform-runtime -D`

- **babel-loader** nos permite usar babel con webpack
- **@babel/core** es babel en general
- **@babel/preset-env** trae y te permite usar las ultimas características de JavaScript
- **@babel/plugin-transform-runtime** te permite trabajar con todo el tema de asincronismo como pueden ser `async` y `await`
- Debes crear el archivo de configuración de babel el cual tiene como nombre `.babelrc` con la siguiente configuración:

```.babelrc
{
  "presets": [
    "@babel/preset-env"
  ],
  "plugins": [
    "@babel/plugin-transform-runtime"
  ]
}
```

- Para comenzar a utilizar webpack debemos agregar la siguiente configuración en `webpack.config.js`

```javascript
{
...,
module: {
    rules: [
      {
        // 'Test' declara que extensión de archivos aplicara el loader
        test: /\.m?js$/,
        // 'Use' es un arreglo u objeto donde dices que loader aplicaras
        use: {
          loader: "babel-loader"
        },
        // 'Exclude' permite omitir archivos o carpetas especificas
        exclude: /node_modules/
      }
    ]
  }
}
```

**RESUMEN:** Babel te ayuda a transpilar el código JavaScript, a un resultado el cual todos los navegadores lo puedan entender y ejecutar. Trae "extensiones" o plugins las cuales nos permiten tener características más allá del JavaScript común.

## HtmlWebpackPlugin

Es un plugin para inyectar javascript, css, favicons, y nos facilita la tarea de enlazar los bundles a nuestro template HTML.

HtmlWebpackPlugin agrega las etiquetas de los archivos de las que se necesitan cargar en el documento HTML. Por ejemplo: la etiqueta script y la etiqueta link:css

### Instalación

**NPM**
`npm i html-webpack-plugin -D`

**YARN**
`yarn add html-webpack-plugin -D`

- Después añadimos esta dependencia a la configuración de webpack en el archivo `webpack.config.js`

```javascript
const path = require('path');

//traemos esta dependencia que la instalamos con un comando de npm previamente
const HtmlWebpackPlugin = require('html-webpack-plugin');

module.exports = {
  entry: "./src/index.js",
  output: {
    path: path.resolve(__dirname, "dist"),
    filename: "main.js"
  },
  resolve: {
    extensions: [".js"]
  },
  module: {
    rules: [
      {
        test: /\.m?js$/,
        exclude: /node_modules/,
        use: {
          loader: "babel-loader"
        }
      }
    ]
  },

  plugins: [
     /*
	 	 hacemos una instancia de lo que definimos en el inicio del archivo
      	 le anadimos por parametro un objeto donde vamos a tener las
     	 configuraciones que le vamos anadir a nuestro plugin
	*/
    new HtmlWebpackPlugin({

		//inyecta el bundle al template html
      inject: true,

		//la ruta al template html
      template: './public/index.html',

		//nombre final del archivo
      filename: './index.html'
    })
  ]
}
```

- Eliminamos el script de nuestro html porque webpack se encargara de insertar el script que compila en nuestro html

```HTML
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link rel="stylesheet" href="../src/styles/main.css">
  <title>JS Portfolio</title>
</head>

<body>
  <div id="main"></div>
  <!-- <script type="module" src="./index.js"></script> -->
</body>

</html>
```

- Compilamos webpack

`npm run build`

- Una vez compilamos nuestro archivo de webpack se insertara el main.js en nuetsro html, agregamos otro script para ejecutar mas facil nuestros comando.

## Loaders para CSS y preprocesadores de CSS

Un **preprocesador** CSS es un programa que te permite generar CSS a partir de la syntax única del preprocesador. Existen varios preprocesadores CSS de los cuales escoger, sin embargo, la mayoría de preprocesadores CSS añadirán algunas características que no existen en CSS puro, como variable, mixins, selectores anidados, entre otros. Estas características hacen la estructura de CSS más legible y fácil de mantener.

Post **procesadores** son herramientas que procesan el CSS y lo transforman en una nueva hoja de CSS que le permiten optimizar y automatizar los estilos para los navegadores actuales.

### MiniCssExtractPlugin

Este plugin extrae el CSS en archivos separados.Crea un archivo CSS por cada archivo JS que contiene CSS.Soporta la carga bajo demanda de CSS y SourceMaps.

Se basa en una nueva característica de webpack v5 y requiere webpack 5 para funcionar.

Comparado con el extracto de texto,paquete web y enchufe:

- Carga asíncrona
- No hay duplicación de la compilación (rendimiento)
- Más fácil de usar
- Específico del CSS

Para comenzar, deberá instalar `mini-css-extract-plugin` :
**npm**
`npm i mini-css-extract-plugin -D`

**yarn**
`yarn add mini-css-extract-plugin -D`

*Se recomienda combinar mini-css-extract-plugin con css-loader*

- Para dar soporte a CSS en webpack debes instalar los siguientes paquetes 

**NPM**

`npm i mini-css-extract-plugin css-loader -D`

**YARN**

`yarn add mini-css-extract-plugin css-loader -D`

- css-loader ⇒ Loader para reconocer CSS
- mini-css-extract-plugin ⇒ Extrae el CSS en archivos
- Para comenzar debemos agregar las configuraciones de webpack al archivo `webpack.config.js`

```javascript
const MiniCssExtractPlugin = require('mini-css-extract-plugin');

module.exports = {
	...,
	module: {
    rules: [
	   ...,
      {
        test:  /\.css$/i
        use: [
          MiniCssExtractPlugin.loader,
          "css-loader",
        ]
      }
    ]
  },
  plugins: [
	...,
    new MiniCssExtractPlugin(),
  ]
}
```

- Si deseamos posteriormente podemos agregar herramientas poderosas de CSS como ser:
	 - pre procesadores
	 	  - Sass
		  - Less
		  - Stylus
	 - post procesadores
	 	 - Post CSS

- Eliminamos la etiqueta *link:css* de nuestro html

```HTML
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>JS Portfolio</title>
</head>

<body>
  <div id="main"></div>
  <!-- <script type="module" src="./index.js"></script> -->
</body>

</html>
```

- Luego importamos el archivo *CSS* en el *index.js* de el proyecto:

```javascript
import Template from './templates/Template.js';
import './styles/main.css'; // IMPORTAMOS EL ARCHIVO CSS

(async function App() {
  const main = null || document.getElementById('main');
  main.innerHTML = await Template();
})();

```
### Añadir Stylus

Utizamos el comando `npm i stylus stylus-loader -D`

Luego añadimos la sigiente configuración en el archivo `webpack.config.js`}

```javascript
{
	test: /\.css|.styl$/i,
	use: [
		MiniCssExtractPlugin.loader,
		'css-loader',
		'stylus-loader'
	],
}
```

**RESUMEN:** Puedes dar soporte a CSS en webpack mediante loaders y plugins, además que puedes dar superpoderes al mismo con las nuevas herramientas conocidas como pre procesadores y post procesadores.