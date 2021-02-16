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
