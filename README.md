# admLinuxDocker
# TABLA DE CONTENIDO

- [Docker Ubuntu](#Docker-Ubuntu)
- [vim](#vim)
- [Añadir y administrar repositorios](#Añadir-y-administrar-repositorios)
- [Instalar actualizar y remover programas en Linux](#Instalar-actualizar-y-remover-programas-en-Linux)
- [Empaquetar y comprimir archivos en Linux](#Empaquetar-y-comprimir-archivos-en-Linux)
- [Compilar un programa en Linux](#Compilar-un-programa-en-Linux)
- [Dónde encontrar la documentación de los programas](#Dónde-encontrar-la-documentación-de-los-programas)
- [Gestores de paquetes en Linux](#Gestores-de-paquetes-en-Linux)
- [Estructura de archivos en Linux](#Estructura-de-archivos-en-Linux)
- [](#)
- [](#)
- [](#)

<!-- toc -->

## Docker Ubuntu
docker logout
Docker pull ubuntu:16.04
1. Docker run ubuntu tail - f /dev/null (dejarla abierta)
Docker exec -it /nombredelcontenedor bash
1. Docker ps (ve los procesos de mi sesión )
2. Docker ps -fea (todos los procesos)
3. exit (salir del contenedor)
4. docker kill nombredelcontendor (matar el contenedor)
5. Otra forma de matar el conector de la otra terminal es así: docker rm-f nombredelcontenedor.

## vim

- apt-get update
- apt-get install vim nano
- vim test
 i para insertar
 v visual
 esc wq guardar
 q! salir
 u deshacer
 - cat test
 ## Añadir y administrar repositorios
Los repositorios son una lista de paquetes, que pueden ser oficiales de la distribución.
- apt-get install aptitude
- aptitude
- Para buscar paquetes se buscan con shif /
- edsintalar remove o dpkg -P mongodb-org

## Empaquetar y comprimir archivos en Linux
Empaquetar y comprimir son cosas diferentes:

Empaquetar: reunir varios archivos en uno solo.
Comprimir: reducir el tamaño de un archivo, generando una versión comprimida sin perder información.

Empaquetar
tar cvf [directorio de salida] [carpeta a empaquetar]

Comprimir
gzip -9r [archivo a comprimir]

Comprimir, descomprimir
tar cvfz archivo.tar.gz [carpeta para comprimir], permite comprimir un archivo

tar xvfz archivo.tar.gz, permite descomprimir y desempaquetar un archivo.

En el archivo /etc/apt/sources.list se guardan las fuentes de los repositorios que va a consultar el sistema. cada fuente contienen una URL, configuración y una versión del paquete.

Actualizar la lista de paquetes
Con el comando apt-get update actualizamos la información de las fuentes listados en source.list

Las llaves añaden una capa de seguridad a los repositorios.

- https://docs.mongodb.com/manual/tutorial/install-mongodb-on-ubuntu/

mongo 
1 .apt-get install sudo
## Instalar, actualizar y remover programas en Linux
instalar un programa
aptitude es un programa que nos permite administrar e instalar componentes en Linux.

+ marcar paquete para instalar
- marcar para no instalar/desinstalar
g para instalar paquetes marcados

Desinstalar
apt-get remove [nombre], desinstalar un paquete.

## Empaquetar y comprimir archivos en Linux
Empaquetar y comprimir son cosas diferentes:

Empaquetar: reunir varios archivos en uno solo.
Comprimir: reducir el tamaño de un archivo, generando una versión comprimida sin perder información.

Empaquetar
tar cvf [directorio de salida] [carpeta a empaquetar]

Comprimir
gzip -9r [archivo a comprimir]

Comprimir, descomprimir
tar cvfz archivo.tar.gz [carpeta para comprimir], permite comprimir un archivo

tar xvfz archivo.tar.gz, permite descomprimir y desempaquetar un archivo.

## Compilar un programa en Linux
Muchas veces tenemos que compilar paquetes en Linux, en Debian y Ubuntu bajamos paquetes ya precompilados

Proceso de compilar
Instalar asistente para compilación:
sudo apt-get install module-assistant

Preparar el sistema, instalando los paquetes requeridos:
sudo m-a prepare

Agregar fuente de datos habilitando fuentes deb-src:
sudo vim /etc/apt/source.list,

Instalar dependencias del paquete
sudo apt-get biuld-dep [nombre del paquete]

Compilar
sudo apt-get source -b [nombre del paquete]

- sudo apt-get install module-assistant
- m-a - -help
- sudo m-a prepare 
- cd tmp
sudo vim /etc/apt/sources.list
- apt-get source -b git
- para borrarlo rm -rf git*

## Dónde encontrar la documentación de los programas
Cada distribución tiene un lugar donde guarda la documentación de los paquetes.

En ubuntu encuentras la documentación en /usr/share/doc
man y info son programas que muestran la documentación del programa que consultes

- zless permite ver el archivo sin descomprimirlo 
- zless Readme.Debian.gz

man y info son programas que muestran la documentación del programa que consultes.

## Gestores de paquetes en Linux
La instalación de software en cualquier sistema operativo es una necesidad inherente al OS, sin software de terceros muchas tareas serían muy difíciles de hacer a nivel de computadoras y servidores.

En GNU/Linux instalar software es algo muy fácil siempre y cuando se haga uso del sistema de gestión de paquetes.

Sistema de gestión de paquetes
Es un conjunto de herramientas que permite la automatización de los procesos de instalación, configuración, actualización y eliminación de paquetes de software. El término gestor de paquetes es comúnmente utilizado en los sistemas *NIX, especialmente en GNU/Linux, en el que la mayoría de las distribuciones tienen un sistema gestor.

Para entenderlo un poco mejor puede hacerse una analogía con un marketplace de algún sistema operativo móvil como Android, en el que a través de PlayStore es posible buscar, instalar, actualizar y eliminar nuevas aplicaciones con mucha facilidad y sin tanta intervención humana: un marketplace como Play Store es un sistema gestor de paquetes para Android.

Sistema de repositorios de software
El sistema de gestor de paquetes por sí solo no puede funcionar, debe tener algún sitio de donde obtener la información necesaria para descargar el paquete de software, para eso están los repositorios, que son sitios centralizados en donde está  toda la metadata, el código fuente y los binarios del software disponible para instalar a través de los sistemas de gestión de paquetes.

YUM (Yellowdog Updater, Modified) - Fedora / CentOS
Es una herramienta de código abierto desarrollada en Python utilizada para hacer la instalación de paquetes de software en distribuciones que usan RPM (RPM Package Manager) como formato de empaquetamiento, como Red Hat Enterprise Linux, Fedora, CentOS, SuSe y Mandriva.
Algunos comandos de YUM son:

Para instalar un software:
yum install
2. Para desinstalar un software:
yum remove 
Para actualizar un software:
yum update 
4. Para actualizar todo el sistema:
yum update
APT (Advanced Packaging Tool) - Debian, Ubuntu y más derivados de Debian
APT no es en sí un sistema gestor de paquetes directo al usuario sino un conjunto de librerías C++ que utilizan otros programas para la distribución de paquetes de software como apt-get, apt-cache y aptitude. APT se utiliza más que todo para la gestión de software que viene empaquetado en formato deb, utilizada en sistemas Debian y derivados.
Algunos comandos de apt-get y aptitude son:

Para instalar un software:
aptitude | apt-get install 
Para desinstalar un software:
aptitude | apt-get remove 
Para actualizar un software:
aptitude install "" paquete="">| apt-get  --only-upgrade install 
Para actualizar todo el sistema:
aptitude safe-upgrade | apt-get upgrade

## Estructura de archivos en Linux
Linux es un sistema operativo, desarrollado por Linus Torvals.

Arquitectura
Una de las cosas más importantes que debemos entender es la estructura de archivos, el directorio raíz es /

Directorios importantes

/home, se almacenan los archivos de cada usuario.
/lib, almacenas las librerías del sistema.
/mnt, cuando montamos en el sistema dispositivos, los podemos ver en esta carpeta.
/opt, almacenas los programas instalados de terceros.
/root, almacena los archivos del super usuario Root.
/sbin, archivos binarios del administrador.
/usr, programas instalados por defecto.
/var, se utiliza para guardar archivos de logs, backups, servidor web.
/etc, archivos de configuración del sistema.
/boot, guarda los archivos del arranque del sistema.

Recuerda: Todo en Linux es un archivo.

** Administrar discos y particiones en Linux**
Todos los discos duros tienen particiones, puedes pensar en esto como una torta que se divide en pedazos físicos.

Las particiones nos permiten segmentar un disco, asignando cada espacio para una labor en particular.

Crear disco duro en Amazon
En Amazon puedes crear un nuevo volumen que asignamos al servidor que creamos.

Para asignarlo con click derecho le damos la opción attach y podemos dejar la configuración por defecto.

Recuerda seleccionar la misma zona al crear el volumen.

Verificar el montaje del disco
Ingresa como super usuario con el comando sudo su

Podemos usar el comando dmesg para verificar que se montó el disco duro que creamos.

Listar discos y particiones
Podemos usar el comando fdisk y nos va a listar todos los discos.

También podemos utilizar fdisk /dev/xvd para ingresar a un disco en especifico.

Recuerda, los discos son los que no tienen un número.

Tipos de particiones
Existen dos tipos de tablas de particiones:

La tradicional que permite 4 particiones primarias y muchas lógicas (las particiones lógicas sirven como contenedores para más particiones).
gpt que permite tener muchas más particiones.
Crear partición
Ejecutamos fdisk /dev/xvd para ingresar al disco.
Creamos una nueva partición con n
Sí es la primera partición debemos crear una primaria, usamos el comando p
Seleccionamos el tamaño de la partición, diciendole +20G

Cambiar tipo de partición
Ejecutamos fdisk /dev/xvd para ingresar al disco.
Seleccionamos el número de la partición.
Seleccionamos t
Elegimos el número del tipo de partición.

Eliminar partición
Entramos a fdisk especificando el disco duro.
Usamos el comando d
Seleccionamos la partición.
Guardamos cambios con w

Guardar los cambios
Con w guardamos los cambios que realizamos, si salimos sin guardar la configuración que hacemos no se va a escribir en el disco.

Ver tabla de particiones
Con el comando fdisk -l podemos ver cómo estan distribuidas las particiones.

**Formateo y montaje de particiones en Linux**
Existen muchos tipos de sistemas de archivos, cada uno tiene características que lo hacen útil para diferentes dispositivos.

Formatear particiones
El comando mkfs nos permite formatear una partición usando el sistema de archivos que queramos.

Formato con FAT32
Podemos ejecutar el comando mkfs.vfat /dev/xvdf1 para formatear la partición xvdf1 con FAT32.

Formato con EXT3
Podemos ejecutar el comadno mkfs.ext3 /dev/xvdf5 para formatear la partición xvdf5 con EXT3.

Formato con EXT4
Podemos ejecutar el comadno mkfs.ext4 /dev/xvdf6 para formatear la partición xvdf6 con EXT4.

Formato con XFS
Podemos ejecutar el comadno mkfs.xfs /dev/xvdf6 para formatear la partición xvdf6 con XFS.

Montar las particiones
Debemos crear un directorio por cada partición que deseamos montar, en este caso usamos tmp dentro de esta carpeta podemos ejecutar:

mkdir xvdf1
mkdir xvdf3
mount /dev/xvdf1 /tmp/xvdf1
mount /dev/xvdf3 /tmp/xvdf3
Desmontar una partición
Para poder desmontar una partición, debes no estar sobre la partición.

Puedes ejecutar el comando:

umount /tmp/xvdf1
En este caso /tmp/xvdf1 es donde tenemos montada la partición.

Listar puntos de montaje
El comando df -h nos lista los directorios que están montados y el espacio que tienen disponible.

Montar particiones automaticamente
Sí queremos montar las particiones de forma automatica podemos ir al archivo /etc/fstab, añadimos:

/dev/xvdf3    /var_new    ext4    defaults,discard    0 0

**Administración swap en Linux**
El area de intercambio o partición swap, es muy útil para máquinas que tienen muy poca memoria RAM.

Ver memoria y swap
Con el comando free podemos ver el uso de la memoria y swap.

También podemos utilizar el comando htop, pero este lo debemos instalar.

Crear partición swap
Entramos al disco con fdisk /dev/xvdf
Podemos eliminar una partición o cambiarle el tipo
Seleccionamos el tipo 82
Guardamos con w
Formateamos la partición con mkswap /dev/xvdf5
Una vez creada podemos activarla con swapon /dev/xvdf5, seleccionando la partición a la que le dimos formato swap.

