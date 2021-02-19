# Informe. Práctica 2: Instalación y Configuración de Visual Studio Code.
## Desarrollo de Sistemas Informáticos.
#### ADRIAN HERNANDEZ SUAREZ - alu0101235516@ull.edu.es


### Introducción.

  Para poder llevar a cabo este informe, **Práctica 2: Instalación y Configuración de Visual Studio Code**, hemos tenido que desarrollar varias aptitudes acerca de **Visual Studio Code**, tales como añadir extensiones o la conexión `SSH` a nuestra máquina virtual desde el propio **VSC**. Además de iniciarnos un poco con **JavaScript** y **TypeScript** realizando un `Hola Mundo`.

### Objetivos.

  Los objetivos de esta práctica han sido por un lado instalar **Visual Studio Code** y configurarlo para poder conectarnos a nuestra máquina por `SSH` desde la propia terminal de **VSC**, y por otro lado hacer uso de las sesiones colaborativas y el primer `Hola Mundo` en **TypeScript**.
  
### Pasos a seguir para la instalación de **Visual Studio Code**.

  Si está trabajando en una distribución Linux Debian/Ubuntu puede instalarlo haciendo uso del siguiente comando:
    
   1. Abrir una terminal y escribir los siguiente:
        
  ```bash
  adrian@ubuntu:~$ sudo apt install code
  ```
  
   2. En el caso de que no se instale con lo anterior, te pedirá hacer uso de la snap, que se instala de la siguiente manera:
    
  ```bash
  adrian@ubuntu:~$ sudo snap install code --classic
  ```
        
### Pasos a seguir para la configuración de **Visual Studio Code**.
#### Conexión a una máquina remota por SSH desde VSCode.

   En este apartado, trataremos de configurar **Visual Studio Code** para conectarnos por `SSH` a nuestra máquina remota del IaaS. Para poder hacer esto, tendremos que realizar la [**Práctica 1: Configuración de máquina virtual del IaaS**](https://ull-esit-inf-dsi-2021.github.io/prct01-iaas/) previamente, si no es así, le recomiendo que la complete antes de seguir con estos pasos.
  
   Una vez tengamos hecha dicha práctica, podemos asegurar que se puede hacer una conexión `SSH` desde nuestra máquina local a la máquina virtual del IaaS.
  
   Lo primero que tenemos que hacer es instalar la extensión de **VSC** denominada `Remote - SSH`. Si por el casual, no sabe como instalar extensiones en **Visual Studio Code**, lo puede aprender con el [Extension Marketplace de VSCode](https://code.visualstudio.com/docs/editor/extension-gallery).
   
   A continuación, pulse la tecla `F1` para abrir la paleta de comandos, teclee `ssh` y pulse sobre `Connect to Host...`. Si realizó correctamente la [**Práctica 1**](https://ull-esit-inf-dsi-2021.github.io/prct01-iaas/), como le facilitamos anteriormente, le debería salir el nombre de su máquina virtual.
   En el caso de haber realizado la Práctica 1, y que no le aparezca el nombre de su máquina, pulse la opción `Configure SSH Hosts...` y elija la opción `~/.ssh/config`. Seguidamente, incluya las siguientes líneas en dicho fichero:
   
   ````bash
   Host iaas-dsi
      HostName iaas-dsi
      User usuario
   ````
   
   Hay que dejar en claro que donde pone `iaas-dsi`, tendrá que poner el nombre de host que le otorgó en su momento a su máquina virtual.
   
   Una vez tengamos hecho lo anterior, pulse la tecla `F1` para abrir la paleta de comandos, teclee `ssh` y pulse sobre `Connect to Host...` y haga click sobre el nombre de su máquina. Esto hará que se habra una nueva pestaña de **VSCode** y se iniciará la conexión `SSH`. Para realizar una comprobación, en la esquina inferior izquierda de la interfaz, puede ver en un área de color verde el nombre de la máquina virtual. Para hacer otra comprobación, puede abrir la terminal `Ctrl + Shift + ^` y teclear el siguiente comando:
   
   ````bash
   [~()]$hostname
   iaas-dsi
   [~()]$
   ````
   
#### Sesiones colaborativas con Visual Studio Live Share.

   Visual Studio Live Share permite colaborar en las tareas de desarrollo en tiempo real. Para poder utilizarlo, en primer lugar, debe buscar e instalar la extensión denominada [Live Share Extension Pack](https://marketplace.visualstudio.com/items?itemName=MS-vsliveshare.vsliveshare-pack).
   
   Es importante mencionar, que si por ejemplo estamos conectados por SSH a una máquina remota como la del IaaS, todas las extensiones que instalemos en dicha máquina solamente se mostrarán ahi y no en la máquina local, lo mismo ocurre si la instalamos en la máquina local, después tendremos que volverlas a instalar en nuestra máquina virtual.
   
   Una vez tengamos todas las extensiones requeridas, para inciar una sesión colaborativa tendremos que hacer lo siguiente:
      
   1. Abrir un projecto, le damos click a `Live Share`, el botón que aparece en la barra inferior, donde haremos un log-in desde Github o Microsoft.
   2. Abrimos dentro de la pestaña Live Share el apartado `Sessions Details` y le damos click en `Start audio call...`
   3. Automáticamente se nos abrirá a parte una ventana llamada `Live Share Chat` que nos proporcionará un chat integrado para las sesiones colaborativas.
   
   Cuando tengamos creada nuestra sesión, simplemente tendremos que compartir el enlace con otros estudiantes y probar las diferentes funcionalidades que nos brinda VSCode.
   
#### Primer proyecto en TypeScript: "Hola Mundo".

   Antes de comenzar tendremos que instalar unas extensiones en nuestro Visual Studio:
    >> **VIM**.
    >> **ESLint**. Permite realizar comprobaciones de estilo sobre ficheros que incluyan código fuente en JavaScript y TypeScript.
    
   1. Instalaremos el compilador de TypeScript. Para ello usaremos npm:
   
````bash
[~()]$npm install --global typescript

added 1 package, and audited 2 packages in 2s

found 0 vulnerabilities
[~()]$tsc --version
Version 4.1.3
````
   2. Después de instalar el compilador, tendremos que irnos a una terminal de VSCode `Ctrl + Shift + ^` y escribir los siguientes comandos:
   
````bash
[~()]$pwd
/home/usuario
[~()]$mkdir hello-world
[~()]$cd hello-world/
[~/hello-world()]$npm init --yes
Wrote to /home/usuario/hello-world/package.json:

{
  "name": "hello-world",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC"
}

[~/hello-world()]$ls -lrtha
total 12K
drwxr-xr-x 26 usuario usuario 4,0K feb  9 18:46 ..
drwxrwxr-x  2 usuario usuario 4,0K feb  9 18:48 .
-rw-rw-r--  1 usuario usuario  225 feb  9 18:48 package.json
[~/hello-world()]$
````

  El comando `npm init --yes` permite crear un fichero denominado `package.json`, el cual se utiliza, entre otras cosas, para establecer las dependencias de desarrollo y ejecución del proyecto a modo de paquetes de los que depende el proyecto actual. Puede observar el contenido de dicho fichero como parte de la salida del comando `npm init`.
  
  3. Abra el directorio `~/hello-world` en el explorador de VSCode, para poder hacer esto tendremos que ir a `File` y hacer click en `Open Folder...` y seleccionamos `hello-world`. También es recomendable añadir el espacio de trabajo, para ello, vamos de nuevo a `File` y seleccionamos `Add Folder to Workspace...` y seleccionamos `hello-world` en el menú desplegable. Cuando lo tengamos creado, lo tendremos que guardar, vamos de nuevo a `File` y esta vez, seleccionamos `Save Workspace As...`, le ponemos el nombre que queremas y confirmamos.
  
  4. Cree un nuevo fichero en el directorio `hello-world` denominado `tsconfig.json`. En dicho fichero se especifican las opciones del compilador de TypeScript. Incluya las siguientes líneas en dicho fichero:
  
````bash
[~/hello-world()]$touch tsconfig.json
[~/hello-world()]$cat tsconfig.json 
{
  "compilerOptions": {
    "target": "ES2018",
    "outDir": "./dist",
    "rootDir": "./src",
    "module": "CommonJS"
  }
}
````

  Básicamente, estas opciones de configuración le indican al compilador de TypeScript que, en primer lugar, queremos generar código compatible con uno de los últimos estándares de JavaScript. 
  - En segundo lugar, que el código JavaScript producto de la compilación se almacenará en un directorio `dist`. 
  - En tercer lugar, especificamos que el código fuente escrito en TypeScript se encuentra en el directorio `src`. 
  - Por último, se indica un estándar para cargar código desde ficheros independientes. Más adelante, veremos en mayor detalle el compilador de TypeScript y sus opciones.
  
  5. A continuación, añadimos un fichero con código TypeScript:
  
````bash
  [~/hello-world()]$pwd
/home/usuario/hello-world
[~/hello-world()]$mkdir src
[~/hello-world()]$cd src
[~/hello-world/src()]$touch index.ts
[~/hello-world/src()]$ls
index.ts
````

  6. Ahora dentro del `index.ts` añadimos el siguiente código:
  
````TypeScript
let myString: string = "Hola Mundo";
console.log(myString);
````

  7. Pasamos a compilar el código en la terminal de VSCode:
  
````bash
[~/hello-world()]$tsc
````
  Lo anterior habrá creado el directorio `dist`, además del fichero `index.js` en su interior.
 
 Hay una funcionalidad muy interesante, para ver la diferencia entre el código del `index.js`y el `index.ts`, y es el uso del comando `diff`.
 
 ````bash
 [~/hello-world()]$diff src/index.ts dist/index.js 
1c1
< let myString: string = "Hola Mundo";
---
> let myString = "Hola Mundo";
````

  Aqui podemos ver la diferencia entre JavaScript y TypeScript, y es la ausencia de `myString`, esto es porque **TypeScript** utiliza tipos para tratar de evitar los problemas que surgen con **JavaScript** el cual no es un lenguaje tipado.
  
  8. Finalmente pasamos a ejecutar el código de JavaScript generado a partir del código que hicimos en TypeScript.
  
````bash
 [~/hello-world()]$node dist/index.js
Hola Mundo
````
#### Conclusión.

En lo que a mi respecta, creo que ha sido muy interesante la realización de esta práctica. Como usuario de VSCode, he descubierto grandes utilidades que tenía el VSCode y desconocía, tanto el SSH con la consolo de nuestra máquina IaaS, como el trabajo en grupo, es decir, las colaboraciones. Por otro lado, creo que aprender a utilizar en más profundidad JavaScript y TypeScript, me ayudará muchísimo a conseguir mi objetivo de ser desarrollador.

#### Bibliografía.

Nombre | Enlaces
-------|--------
Introducción a Markdown | https://guides.github.com/features/mastering-markdown/
Información sobre GitHub Pages | https://docs.github.com/en/github/working-with-github-pages
Sitio web de Jekyll | https://jekyllrb.com/
GutHub Learning Lab | https://lab.github.com/
Curso de GitHub Pages | https://lab.github.com/githubtraining/github-pages
Visual Studio Code | https://code.visualstudio.com/
Instalar Visual Studio Code | https://code.visualstudio.com/docs/setup/setup-overview
Tutorial VSCode sobre Additional Components | https://code.visualstudio.com/docs/setup/additional-components
Tutorial VSCode sobre User Interface | https://code.visualstudio.com/docs/getstarted/userinterface
Tutorial VSCode sobre Basic Editing | https://code.visualstudio.com/docs/editor/codebasics
Tutorial VSCode sobre Extension MarketPlace | https://code.visualstudio.com/docs/editor/extension-gallery
Tutorial VSCode sobre IntelliSense | https://code.visualstudio.com/docs/editor/intellisense
Tutorial VSCode sobre Code Navigation | https://code.visualstudio.com/docs/editor/editingevolved
Tutorial VSCode sobre Debugging | https://code.visualstudio.com/docs/editor/debugging
Tutorial VSCode sobre Version Control | https://code.visualstudio.com/docs/editor/versioncontrol
Tutorial VSCode sobre Working with GitHub | https://code.visualstudio.com/docs/editor/github
Tutorial VSCode sobre Integrated Terminal | https://code.visualstudio.com/docs/editor/integrated-terminal
Tutorial VSCode sobre Tasks | https://code.visualstudio.com/docs/editor/tasks
Tutorial VSCode sobre Snippets | https://code.visualstudio.com/docs/editor/userdefinedsnippets
Tutorial VSCode sobre Emmet | https://code.visualstudio.com/docs/editor/emmet
Tutorial VSCode sobre Command Line | https://code.visualstudio.com/docs/editor/command-line
Tutorial VSCode sobre  Multiroot Workspaces | https://code.visualstudio.com/docs/editor/multi-root-workspaces
Tutorial VSCode sobre  Accessibility | https://code.visualstudio.com/docs/editor/accessibility
Conectarnos desde VSCode a una máquina remota por SSH | https://code.visualstudio.com/docs/remote/ssh-tutorial
Informe de la práctica 1 de DSI | https://ull-esit-inf-dsi-2021.github.io/ull-esit-inf-dsi-20-21-prct01-iaas-alu0101206479/
Live Share Extension Pack | https://marketplace.visualstudio.com/items?itemName=MS-vsliveshare.vsliveshare-pack
Documentación de Visual Studio Live Share | https://docs.microsoft.com/en-us/visualstudio/liveshare/
Libro Essential TypeScript: From Beginner to Pro | https://learning.oreilly.com/library/view/essential-typescript-from/9781484249796/html/Part_1.xhtml

