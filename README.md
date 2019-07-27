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
- [Arrancando el sistema runlevels systemd](#Arrancando-el-sistema-runlevels-systemd)
- [Uso de variables de entorno bashrc profile](#Uso-de-variables-de-entorno-bashrc-profile)
- [Uso de redireccionamineto y pipes para logs](#Uso-de-redireccionamineto-y-pipes-para-logs)
- [Monitorear eliminar y establecer prioridades en procesos](#Monitorear-eliminar-y-establecer-prioridades-en-procesos)
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

**Generar imágenes de discos duros**
Muchas veces necesitamos sacar backups, o imágenes de discos duros, veamos algunas herramientas para esto.

Crear imágenes con dd
dd nos permite sacar una imágen completa del disco duro, para realizar la imagen.

Primero debemos estar seguros que tenemos la partición desmontada.

Usamos el comando:

dd if=/dev/xvdf6 of=/var_new/backup/backup_xvdf7 bs=1MB
if es la partición que deseamos hacer la imágen,
of donde se va a guardar la imágen.

Montar una imagen con loop
Primero debemos activar el módulo del kernel con modprobe loop.

Una vez activo, creamos una carpeta donde vamos a montar la imágen, con mkdir /tmp/iso_debian recuerda puedes seleccionar la ruta que desees.

Ahora con el comando mount debian.iso /tmp/iso_debian -o loop estamos montando la imágen.

Recuerda debes estar seguro de la ruta del archivo, puedes ir autocompletando la ruta con tab

Escribir un archivo lleno de ceros
En linux existe una ruta /dev/zero esta siempre va a devolver cero.

Podemos crear el archivo con:

dd if=/dev/zero of=zeros100M bs=1M c=100

Leer un archivo para medir la velocidad del disco
En Linux existe una ruta /dev/null la cual todo lo que enviemos va a desaparecer.

Podemos medir la velocidad de un disco leyendo un archivo, enviando la información a null con:

dd if=zeros100M of=/dev/null
Recuerda: con el comando sync sincronizas el disco duro.

**Administrar particiones GPT**
Sí el arranque del sistema no funciona correctamente, no vamos a poder tener acceso al servidor, por esto es importante tenerlo configurado correctamente.

Historicamente hemos podido iniciar el sistema con sistemas MBR o el sistema UEFI.

Saber tipo de tabla de particiones
Con fdisk -l /dev/xvda, muestra el tipo de la tabla de partición.

Tabla de particiones GPT
GPT permite tener 128 particiones en un disco duro.

gdisk es un comando especial para particiones GPT.

Crear particiones con gdisk
Usamos el comando gdisk /dev/xvdh para acceder a configurar las particiones del disco. Recuerda debes seleccionar el disco que deseas configurar.

Usamos la opción n para crear una nueva, y seleccionamos el número de la partición.

Asignamos el tamaño de la partición en este caso +1G

Seleccionamos el tipo de partición, por ejemplo 8300 para cargar tipo Linux filesystem

**Administrar el arraque del sistema GRUB**
El GRUB es gestor de arranque, que permite cargar el kernel y el sistema.

Archivos de configuración
En la carpeta /etc/grub.d vemos los archivos del grub.

/boot/grub/grub.cfg es el archivo de configuración, pero no modifiques este archivo, para configurarlo usa /etc/grub.d

El grub se coloca en el MBR, que esta en los primeros 512 Bytes del disco.

Backup del MBR
Podemos generar un backgrup del MBR con dd

dd if=/dev/dvda of=/root/mbr_backup bs=512 count=1

Actualizar grub
update-grub2
Instalar grub
grub-install /dev/xvdf

**Administrar discos duros con LVM**
LVM nos permite realizar una configuración de discos duros que nos permita administrar el espacio de almacenamiento del servidor.

Instalación
apt-get install lvm2
Crear volúmenes físicos
Primero debemos agregar los discos físicos que vamos a usar para crear el LVM, para esto debemos formatear la partición a usar con tipo 8e

pvcreate /dev/xvdf3, agrega la partición a los volúmenes físicos del LVM

pvs listar los discos en los volúmenes lógicos

Grupos
vgcreate databases /dev/xvdf3, se agrega la partición a un grupo

vgs listar los grupos

vgreduce databases /dev/xvdg remueve una partición del grupo

Volumenes lógicos
lvcreate -n postgres -L 10g databases, crea una partición usando el espacio de un grupo
Extender tamaño de la partición
lvextend -L+10G /dev/databases/posgress

resize2fs /dev/databases/posgress

**Apagar servidores de forma remota**
Los administradores de servidores normalmente deben apagar servidores de forma remota, recuerda:

Revisar en cual servidor estas conectado
Linux no preguntar confirmación
Es diferente apagar y reiniciar
Comandos
shutdown -r now reincia la máquina
shutdown -h now apagar la máquina
systemctl reboot reiniciar

## Arrancando el sistema runlevels, systemd
En Linux por defecto han existido 6 niveles que todos los programas arrancan, se pueden ver en las carpetas /etc/rc0.d hasta /etc/rc6.d

Dentro de estas carpetas los archivos con S es de arranque y K es de salida

runlevel
con runlevel dice en qué sistema se está corriendo

systemd
systemd permite saber un árbol de procesos, indicando las dependencias de estos para interactuar con systemd usamos systemctl

Listar dependencias
systemctl list-dependencies [servicio]

Ver servicios
systemctl

Ver un servicio
systemctl show [nombre del servicio]

Buscar servicios
ps aux | grep [servicio]

Recargar un servicio
systemctl deamon-reload

Reiniciar un servicio
systemctl restart [nombre]

Estado de un servicio
systemctl status [nombre]

## Uso de variables de entorno, bashrc, profile
Las variables de entorno permiten configurar diferentes ambientes cómo de desarrollo o producción, también guardar llaves de seguridad.

Una variable de entorno es simplemente una variable

Crear una variabla de entorno
platzi="http://platzi.com"

Imprimir variable
echo $PLATZI

con export listas todas las variables

.bashrc y .profile
Estos archivos guardan configuraciones de la sesión como alias, variables de entorno, etc.

Agregar una variable de entorno
En el archivo /etc/bash.bashrc agregar una línea declarando la variables export HOME_DB=/var_new

Recuerda:

Cada sesión tiene sus variables de entorno
En PATH se guardan las rutas donde el sistema busca binarios
Las variables de entorno solo se mantienen durante la sesión, debes exportarlas para guardarlas

## Uso de redireccionamineto y pipes para logs
Muchas veces los logs se centralizan en un sistema para verlos otras se guardan en el servidor, para poder darle valor a los logs, debemos poder encontrar información en el.

Leer un archivo
less [nombre archivo]
more [nombre archivo]

Filtrar información
grep -r "25/Nov" * buscar los del 25 Nov en todos los archivo recursivamente

Contar líneas
wc [archivo]

Encadenar procesos
grep -r "25/Nov" * | wc, el resultado de grep se le pasa a wc

Enviar la salida de un comando a un archivo
grep -r "25/Nov" * > /tmp/25nov

Ver últimos logs
tail [nombre]

## Monitorear, eliminar y establecer prioridades en procesos
Los procesos permiten al sistema operativo trabajar, definiendo cuando se debe procesar información.

Los procesos en Linux están encapsulados, esto quiere decir que el usuario que lanzo el proceso es quien lo debe quitar.

Listar procesos del sistema
ps aux
Revisar carga del sistema
htop
Recuerda:

Todo proceso en Linux tiene un número único
Un proceso puede tener un valor de prioridad desde -20 hasta 19

## Enlaces duros, simbólicos y sistemas de backups
Enlace simbolico
Un archivo sin datos, que solo contiene una referencia a la ubicación del archivo original.

ln -s /home/ubuntu/archivo.iso debian.iso

Enlaces duros
En un archivo enlazado al archivo original pero con un nombre diferente.

ln a/zero b/

## Manejo de usuarios y grupos
Linux es un sistema multiusuario, cada usuario puede correr con diferentes configuraciones, permisos, etc.

Crear un usuario
adduser platzi, crea un usuario

Todo usuario tiene un id, home y el terminal a usar.

Cambiar de usuario
su - [nombre de usuario]

Grupos
Cada usuario puede pertenecer a diferentes grupos que le permita acceder a recursos

groups te dice a que grupos tienes acceso

Añadir a un nuevo grupo
addgroup [Usuario] [grupo]
addgroup platzi sudo

Se necesita volverse a conectar al usuario para que cargue los permisos al usuario.

Recuerda:

En el archivo /etc/shadow se guardan las contraseñas

## Generar backup de Base de datos
Existen muchas formas de generar un backup, en este video veremos algunas de las formas:

En amazon puedes generar una imagen de la instancia en la que estás trabajando.

Generar un backup de la base de datos

pg_dump [base de datos ] > backup.2017.sql

Es una buena práctica nombrar el archivo con el nombre de la base de datos y la fecha.

## Uso de socat y manejo de redireccionamiento de puertos
Muchas veces necesitamos redireccionar el tráfico entre puertos para esto podemos usar socat

Instalar socat
sudo apt-get install socat

Crear redirección
socat TCP-LISTEN:8080, fork, reuseaddr TCP:localhost:80

Redirecciona todo el tráfico del puerto 8080 al 80

Redirección UDP
socat UDP-LISTEN:80,reuseaddr,fork TCP4:localhost:8080

## Tareas programadas y cómo monitorearlas
crontab nos permite crear tareas programadas

Comando
crontab -e nos permite crear una nueva tarea

El cron se compone de cinco valores importantes.

Minuto hora [dia del mes] mes [dia de la semana]

0 9 * * 1 date >> /tmp/date

Script para backup
Ir a la carpeta de scripts /etc/cron.d/

Crear el script vim backup_database

55 15 * * * postgres /usr/bin/pg_dump jav_spheb > /var/lib/postfresql/new_db


## Seguridad del kernel
El kernel es la pieza fundamental del sistema operativo, el interactua entre el hardware y los programas que se están ejecutando.

Por defecto el kernel de Linux está bien asegurado, veamos cómo modificar estos límites

Modificar límites
En el archivo /etc/security/limits.conf se encuentra la configuración de límites del kernel

*  soft  nofile  32000
*  hard  nofile  35000
De esta forma estamos estableciendo la cantidad de archivos que puede abrir el sistema al tiempo.

## Permisos de archivos
Todos los días vas a trabajar con permisos en Linux, estos nos permiten controlar la seguridad.

Para listar archivos mostrando permisos lo haces con ls -l

La información se muestra cómo organizado en usuario grupo otros, cada uno tiene un ítem para lectura, escritura y ejecución.

Cambiar permisos
chmod [bloque][+ o -][permiso] [nombre de archivo]
chmod o-r test, los otros quitar el permiso de lectura al archivo test

chmod 776 [nombre de archivo]

4 lectura
2 escritura
1 ejecución
Cambiar propietario de un curso
sudo chown [usuario]:[grupo] [archivo]
sudo chown platzi: /tmp/delete

## Configuración de red
Ver la configuración de interfaces de red
ifconfig

Inicializar la interfaz
dhclient eth1

Archivos de configuración
/etc/network/interfaces
/etc/network/interfaces.d

Activar DHCP automatico
En el archivo interfaces.d agregamos la línea

iface eth1 inet dhcp

Apagar inferface de red
ifdown eth0

Multiples ip sobre una misma interface
ifconfig eth0:0 192.168.10.5

Comando ip
Con este comando podemos sustituir ifconfig

ip addr show, mostar las direcciones

Enrutamiento
Para ver la tabla de enrutamiento se puedes usar route -n

## Cómo manejar mi firewall
iptables permite transmitir la información entre las interfaces de red y el sistema operativo.

Por defecto el firewall tiene algunas políticas generales

Listar información del firewall
iptables -L

input: los paquetes que entran
output: paquetes que salen
forward: paquetes que llegan y se redireccionan

Rechazar todos los paquetes de entrada
iptables -P INPUT DROP

Aceptar conexiones de un puerto especifico
iptables -A INPUT -i eth0 -p tcp --dport 22 -j ACCEPT

Guardar las reglas
iptables-save > /etc/iptables.rules


## Manejo de DNS y dig
El DNS permite mapear un nombre a una dirección IP

/etc/host guarda la lista de ips y nombres asignados en la máquina

Los distintos tipos de DNS son:

A - IPv4
CNAME - nombre
MX - correo
AAAA - dirección IPv6
TXT - texto
PTR - dns reverso
Consultar dominios
apt-get install dnsutils

dig linux.platzi.com a dns oficiales
dig linux.platzi.com @[servidor dns] a un servidor especifico

## Instalación de NTP
NTP es un servicio que permite sincronizar la hora.

Instalación
apt-get install ntp

Consultas
ntpq permite hacer consultas al servicio

Activar
ntpdate-debian selecciona un servidor y hace la configuración.

Archivo de configuración
/etc/default/ntpdate

## Auditoria de login y logs
who muestra los usuarios conectados
w quién está conectado y hace cuanto estan inactivos
/var/log/auth queda registrado todos los intentos de acceso

## Tuneles con ssh, autossh y socat
Abrir un túnel en el servidor
ssh -Ng -L9898:localhost:80 -i platzi
Aceder a la máquina local
ssh -NR 10022:localhost:22 -i platzi

ssh -p 10022 usuario@localhost

Crear proxi
ssh -N -D10090 platzi

## Backup de archivos de configuración con etckeeper
Cuando mantenemos un gran sistema necesitamos tener auditoria de las acciones en el servidor.

backup de etc/
Con etckeeper podemos guardar la configuraciones de etc, usando git.

Instalación:

apt-get install etckeeper

Guardar cambios

etckeeper commit

## Prevenir ataques con fail2ban
Muchas veces los servidores están expuestos a ataques, fail2ban nos permite bloquear ataques.

Instalación
apt-get install fail2ban

Configuración
/etc/fail2ban/fail2ban.conf
/etc/fail2ban/jail.conf

Filtros
Para activar un filtro lo debes buscar y añadir la línea enabled = true, por ejemplo en nginx debes buscar el archivo etc/fail2ban/filter.d/nginx-http-auth.conf

Restaurar el servicio
fail2ban.service restart

## Backup de archivos de configuración con etckeeper
Cuando mantenemos un gran sistema necesitamos tener auditoria de las acciones en el servidor.

backup de etc/
Con etckeeper podemos guardar la configuraciones de etc, usando git.

Instalación:

apt-get install etckeeper

Guardar cambios

etckeeper commit

## ncriptación de datos
gpg es un programa que maneja una serie de configuraciones para encriptación.

Encriptación simetrica
gpg -ca -o [salida] [entrada]

## Encontrar el dueño del paquete
Para encontrar el dueño de un archivo podemos el comandodpkg -S [nombre del archivo]

Para ver todos los archivos de un programa dpkg -l [nombre del paquete]

## md5sum, integridad de archivos y paquetes
md5sum permite sacar una suma binaria de un archivo con un hash

Calcular m5sum
md5sum [nombre del archivo]



