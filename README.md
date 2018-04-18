# linux-commands

FUENTE ORIGINAL: https://www.luisllamas.es/listado-comandos-linux-utiles/

## CONTROL DE PROCESOS Y TRABAJOS

### EJECUTAR COMANDOS Y APLICACIONES
```
#ejecutar aplicacion en carpeta actual
./aplicacion

#ejecutar comando
comando

#iniciar proceso en background
comando &

#cancelar comando
control + c

#poner comando en background
control + z

#recuperar proceso puesto en background
bg

#poner trabajo en primer plano
fg jobID

#iniciar comando como root
sudo comando

#iniciar ejecutable con interface grafica como root 
sudo ejecutable

#gestor de sesiones multiples en terminal
screen -S nombre_sesion
```

### LISTAR PROCESOS Y TAREAS
```
#mostrar procesos en background con jobID y PID
jobs -l
 
#mostrar procesos
ps
 
#mostrar procesos activos
ps -eafw
 
#mostrar árbol de sistema de procesos.
pstree
 
#mostrar procesos ordenados por consumo de memoria
ps aux | sort -k 5
```

### FINALIZAR PROCESOS
```
#finalizar proceso para recargar configuracion
kill -1 ID_Processo
 
#forzar cierte de proceso por PID
kill -9 PID
 
#finalizar proceso por nombre
killall -9 nombre
```

### ALIAS DE COMANDOS
```
#configurar un alias temporal para comando
alias cmd='comando'
 
#eliminar alias
unalias cmd
```

## INFORMACION Y SUPERVISIÓN DEL SISTEMA
```
#limpiar pantalla de terminal (mismo efecto que control+l)
clear

#reiniciar sesion de terminal
reset
 
#terminar sesión de terminal local o remoto (ssh) y finalizar procesos iniciados
exit
GESTIÓN DE RECURSOS

#mostrar tareas ejecutandose y su uso de recursos 
top
 
#mostrar tareas ejecutables y recursos mejorado
htop
 
#muestra el estado de la RAM en megabytes
free -h
```

### ESPACIO DE DISCO
```
#mostrar una lista de las particiones montadas
df -h

#mostrar el tamaño de los archivos y directorios ordenados por tamaño
ls -lSr |more

#Estimar el espacio usado por el directorio ‘dir1′
du -sh directorio
 
#mostrar el tamaño de los archivos y directorios ordenados por tamaño
du -sk * | sort -rn
```

### INFORMACIÓN DE SISTEMA
```
#mostrar datos de usuarios conectados
who -a

#mostrar historial de reinicio
last reboot

#Mostrar arquitectura y versión de Linux y Kernel
uname -a

#mostrar el kernel cargado.
lsmod

#mostrar componentes de hardware del sistema.
dmidecode -q

#Listar particiones de disco duro
*cat /etc/fstab

#mostrar características de disco duro
hdparm -i /dev/hda
 
#mostrar dispositivos PCI
lspci
 
#mostrar dispositivos USB
lsusb
 
#mostrar eventosde proceso de carga de kernel
tail /var/log/dmesg
 
#mostrar los eventos del sistema
tail /var/log/messages
 
#mostrar lista de archivos abiertos por procesos
lsof -p $$
 
#mostrar lista de archivos abiertos en un camino dado del sistema
lsof /directorio
 
#mostrar llamadas del sistema hechas y recibidas por un proceso
strace -c ls >/dev/null
 
#mostrar las llamadas a la biblioteca
strace -f -e open ls >/dev/null
 
#mostrar interrupciones en tiempo real
watch -n1 'cat /proc/interrupts'
```

### APAGADO Y REINICIO DE SISTEMA
```
#cerrar sesion usuario
logout
 
#apagar el sistema ahora
shutdown now
 
#reiniciar sistema ahora
shutdown -r now
 
#apagado programado
shutdown horas:minutos &
 
#cancelar apagado programado
shutdown -c
```

### FECHAS
```
#mostrar la fecha del sistema
date
 
#mostrar calendario de un año
cal año
 
#mostrar calendario de mes y año
cal mes año 2011
```

### AYUDAS
```
#manual online de comando
man comando
 
#muestra un resumen descriptivo de la funcion de comando
whatis comando
 
#buscar comandos por la tarea realizada (inverso del anterior)
apropos texto
```

## OPERACIONES CON ARCHIVOS Y DIRECTORIOS
En los comandos que requieran introducir nombres de archivos o directorios podéis pulsar dos veces tabulación para autocompletar la ruta, u obtener un listado de archivos disponibles.

### DESPLAZARSE ENTRE DIRECTORIOS
```
#ir a directorio de raiz
cd

#/ir a directorio anterior
cd ..
 
#entrar en directorio (ruta absoluta)
cd /directorio1/directorio
 
#entrar en directorio (ruta relativa)
cd directorio1/directorio2
 
#ir a directorio de usuario
cd ~
 
#ir a ultimo directorio visitado
cd -
 
#mostrar ruta actual
pwd
```

### LISTAR ARCHIVOS Y DIRECTORIOS
```
#mostrar archivos y directorios
ls
 
#mostrar archivos y directorios con detalles
ls -l
 
#mostrar archivos y directorios incluidos los ocultos
ls -a
```

### MANIPULACIÓN DE ARCHIVOS Y DIRECTORIOS
```
#renombrar o mover un archivo o directorio
mv origen destino

#copiar un archivo
cp archivo direccion

#copiar un directorio
cp -r origen destino

#borrar el archivo llamado archivo
rm archivo

#borrar directorio si está vacio
rm -d directorio

#borrar directorio y su contenido
rm -r directorio

#crear nuevo directorio
mkdir directorio

#crear varios directorios simultáneamente
mkdir directorio1 directorio2

#crear ruta de directorios
mkdir -p /directorio1/directorio2

#crear archivo vacio
touch archivo

#cambiar fecha de archivo (formato año, mes, dia, y hora)
touch -t 19901230000 archivo
``` 

### ENLACES SIMBÓLICOS
```
#crear un enlace simbólico al archivo o directorio
ln -s archivo lnk1
 
#crear enlace físico al archivo o directorio
ln archivo lnk1
```

### CODIFICACIÓN
```
#calcular md5 de un archivo
md5sum archivo
 
#codificar archivo GNU Privacy Guard.
gpg -c 
 
#decodificar archivo GNU Privacy Guard.
gpg archivo.gpg
```

## OPERACIONES DE CONTENIDO DE ARCHIVO

### TUBERIAS Y REDIRECCIONES I/O
```
#dirigir salida de comando a nuevo archivo
comando > archivo_out.txt
 
#digir salida de comando para añadir a archivo archivo
comando >> archivo_out.txt
 
#dirigir entrada de comandos
comando < archivo_in.txt
 
#dirigir salida estandar y salida de error a un fichero:
comando &> archivo_out.txt
 
#tuberia, dirigir salida de comando1 como entrada de comando2
comando1 | comando2
```

### MOSTRAR CONTENIDO DE ARCHIVO
```
#muestra contenido de archivo
echo archivo

#mostrar contenido de archivo
cat archivo
 
#mostrar contenido de archivo empezando por el final
tac archivo
 
#mostrar contenido de archivo desplazandose linea a linea
more archivo
 
#mostrar contenido de archivo desplazandose adelante o atrás
less archivo
 
#mostrar dos primeras lineas de archivo
head -2 archivo
 
#mostrar dos ultimas lineas de archivo
tail -2 archivo
 
#mostrar en tiempo real las ultimas lineas de archivo (seguimiento)
tail -f archivo
```

### MANIPULACIÓN DE TEXTO
```
#convertir minúsculas en mayúsculas
echo 'archivo' | tr '[:lower:]' '[:upper:]'
 
#eliminar lineas 1 a 5 de archivo
sed '3,5d' archivo
 
#eliminar lineas 5 a fin de archivo
sed '5,$d' archivo
 
#eliminar linas en blanco
sed '/^$/d' archivo
 
#eliminar linas en blanco y comentarios
sed '/ *#/d; /^$/d' archivo
 
#sustituir una cadena por otra
sed 's/cadena1/cadena2/g' archivo 
   
#visualizar unicamente las líneas que contienen cadena
sed -n '/cadena/p'
```

## BUSQUEDA DE ARCHIVOS Y EN SU CONTENIDO

### BUSCAR DE ARCHIVOS
```
#buscar archivo y directorio por su nombre en todo el sistema
find * -name nombre
 
#buscar archivo y directorio por su nombre, dentro de directorio
find directorio -name nombre
 
#buscar archivos y directorios pertenecientes a usuario, dentro de directorio
find directorio -user usuario
 
#buscar archivos y directorios por su tipo, dentro de directorio
(d directory, f regular file, l symbolic link)
find directorio -type f tipo
 
#buscar archivos y ejecutar comando
find directorio -name nombre -exec comando {} \;
 
#buscar archivos con extensión .ps
locate \*.ps
 
#mostrar la ruta completa de un ejecutable
which ejecutable 
 
#mostrar la ubicación de un archivo binario, de ayuda o fuente
whereis ejecutable
```

### BUSCAR EN CONTENIDO DE ARCHIVO
```
#buscar cadena en el/los archivos
grep cadena archivo
 
#buscar cadena en el/los archivos sin coincidencia de mayusculas
grep -i cadena archivo
 
#buscar palabras que comienzan con cadena en el/los archivos
grep ^cadena archivo 
 
#buscar cadena como palabra completa en el/los archivos
grep -w cadena archivo 
 
#seleccionar las líneas de archivo que contienen números
grep [0-9] archivo 
 
#busca recursiva de cadena en el directorio
grep cadena -R direccion
```

## GESTIÓN DE USUARIOS Y GRUPOS

### USUARIOS
```
#crear un nuevo usuario
useradd usuario
 
#crear usuario, version completa
useradd -c "Nombre Usuario" -g grupo -d /home/usuario -s /bin/bash usuario 
 
#borrar usuario
userdel usuario
 
#borrar usuario y eliminar su directorio home
userdel -r usuario 
 
#cambiar los atributos del usuario.
usermod -c "Nombre usuario" -g grupo -d /home/usuario -s /bin/bash usuario  
 
#cambiar contraseña del propio usuario.
passwd
#cambiar la contraseña de usuario (solamente por root).
passwd usuario
 
#colocar un fecha de expiracion para contraseña de usuario
chage -E 2014-12-31 usuario
```

### GRUPOS DE USUARIOS
```
#crear grupo usuarios
groupadd nombre_grupo

#borrar grupo de usuarios
groupdel nombre_grupo
 
#renombrar grupo de usuarios
groupmod -n nombre_nuevo nombre_anterior
 
#modificar el grupo actual de un usuario que pertenece a varios grupos
newgrp grupo
 
#listar grupos del usuario actual
groups 
 
#listar todos los grupos
cut -d: -f1 /etc/group
```

### COMPROBACIONES
```
#comprueba que el archivo de contraseñas /etc/passwd es correcto
pwck
 
#comprueba que el archivo de grupos /etc/group #es correcto
grpck
```

## PERMISOS Y ATRIBUTOS ESPECIALES

### PERMISOS DE ARCHIVOS Y CARPETAS
```
#usar + para colocar permisos y - para eliminar
Mostrar permisos.
ls -lh
 
#asignar permisos 0777 a fichero
#modificar 0777 segun codificacion octal de permisos
chmod 0777 fichero
 
#asignar permisos a todos los archivos de un directorio
chmod -R 0644 directorio
 
#colocar a directorio permisos de lectura (r), escritura (w) y ejecución (x) al propietario (u), grupo (g) y otros (o).
#emplear las opciones necesarias para añadir o quitar los permisos deseados
chmod ugo+rwx directorio
 
#cambiar usuario de archivo
chown usuario archivo
 
#cambiar usuario a todos los archivos de un directorio
chown -R usuario directorio
 
#cambiar grupo de archivo
chgrp grupo archivo
 
#cambiar usuario y grupo de archivo.
chown usuario:grupo archivo
```

### PERMISOS SUID
```
#visualizar todos los archivos del sistema con SUID configurado
find / -perm -u+s
 
#colocar bit SUID en archivo binario. El usuario que ejecute este archivo adquiere los mismos privilegios como dueño
chmod u+s /bin/archivo
 
#eliminar bit SUID en archivo binario
chmod u-s /bin/archivo
 
#colocar bit SGID en directorio. Similar a SUID pero para directorios
chmod g+s /home/directorio
#eliminar bit SUID en archivo binario.
chmod g-s /home/directorio
 
#clocar un bit STIKY en un directorio. Permite el borrado de archivos solamente a los dueños legítimos
chmod o+t /home/directorio
#eliminar bit STIKY en un directorio.
chmod o-t /home/directorio
```

### ATRIBUTOS ESPECIALES DE ARCHIVO
```
#usar + para colocar permisos y - para eliminar
#mostrar atributos especiales.
lsattr
 
#permite escribir abriendo un archivo solamente modo append.
chattr +a archivo
 
#permite que un archivo sea comprimido / descomprimido automaticamente.
chattr +c archivo
 
#asegura que el programa ignore borrar los archivos durante la copia de seguridad.
chattr +d archivo
 
#convierte el archivo en invariable, por lo que no puede ser eliminado, alterado, renombrado, ni enlazado.
chattr +i archivo
 
#permite que un archivo sea borrado de forma segura.
chattr +s archivo
 
#asegura que un archivo sea modificado, los cambios son escritos en modo synchronous como con sync.
chattr +S archivo
 
#te permite recuperar el contenido de un archivo aún si este está cancelado.
chattr +u archivo
```

## ARCHIVOS EMPAQUETADOS Y COMPRIMIDOS

### ARCHIVOS TAR
```
#mostrar contenido de archivo tar
tar -tf archive.tar
 
#crear archivo tar
tar -cvf archivo.tar directorio1
 
#crear archivo tar compuesto por varios archivos y directorios
tar -cvf archivo.tar archivo1 archivo2 directorio1
 
#crear archivo tar comprimido en bzip2
tar -cvfj archivo.tar.bz2
 
#crear archivo tar comprimido en gzip
tar -cvfz archivo.tar.gz directorio1
 
#extraer archivo tar 
tar -xvf archivo.tar
 
#extraer archivo tar en directorio
tar -xvf archivo.tar -C /directorio
 
#extraer archivo tar preservando permisos de usuario
tar -xpvzf archivo.tar
 
#descomprimir archivo tar comprimido en bzip2
tar -xvfj archivo.tar.bz2
 
#descomprimir archivo tar comprimido en gzip
tar -xvfz archivo.tar.gz
```

### ARCHIVOS ZIP
```
#crear un archivo comprimido en zip.
zip archivo.zip directorio1
 
#comprimir en zip compuesto por varios archivos y directorios
zip -r archivo.zip archivo1 archivo2 directorio1 
 
#descomprimir un archivo zip
unzip archivo.zip
```

### ARCHIVOS BZ2
```
#comprimir archivo bz2
bzip2 archivo
 
#descomprimir archivo bz2
bunzip2 archivo.bz2
```

### ARCHIVOS GZ
```
#comprimir archivo gz
gzip archivo
 
#descomprimir archivo gz
gunzip archivo.gz
 
#descomprimir archivo gz con compresion maxima
gzip -9 archivo
```

### ARCHIVOS RAR
```
#crear archivo rar
rar a archivo.rar directorio1
 
#crear archivo zip compuesto por varios archivos y directorios
rar a archivo.rar archivo1 archivo2 directorio1
 
#descomprimir archivo rar.
unrar x archivo.rar
```

## INSTALADORES DE PAQUETES, Y RESPOSITORIOS

```
#mostrar bibliotecas requeridas por programa o comando
ldd programa
 
#descargar de Github
git clone git://github.com/directorio/proyecto.git

```

### PAQUETES DEB (DEBIAN Y DERIVADOS)
```
#instalar / actualizar un paquete deb
dpkg -i paquete.deb
 
#eliminar un paquete deb del sistema
dpkg -r paquete
 
#mostrar todos los paquetes deb instalados en el sistema
dpkg -l
 
#mostrar todos los paquetes deb con un nombre
dpkg -l | grep nombre
 
#obtener información en un paquete instalado en el sistema
dpkg -s paquete
 
#mostar lista de archivos dados por un paquete instalado en el sistema
dpkg -L paquete
 
#mostrar lista de archivos dados por un paquete sin instalar
dpkg –contents paquete.deb
 
#verificar a que paquete pertenece a un archivo
dpkg -S archivo
```

### ACTUALIZADOR DE PAQUETES APT (UBUNTU Y DERIVADOS)
```
#instalar / actualizar un paquete deb.
apt-get install paquete
 
#añadir repositorio
sudo sh -c 'echo repositorio' >> /etc/apt/sources.list
#tambien
sudo add-apt-repository ppa:repositorio
 
#actualizar lista de paquetes
apt-get update
 
#actualizar paquetes instalados
apt-get upgrade
 
#eliminar un paquete del sistema
apt-get remove paquete
 
#buscar un paquete
apt-cache search paquete
 
#verificar resolución de dependencias
apt-get check
 
#limpiar cache desde paquetes descargados
apt-get clean
```

## OPERACIONES CON SISTEMAS DE ARCHIVOS

### ANÁLISIS DEL SISTEMA DE ARCHIVOS
```
#Comprobar integridad de archivos en el disco hda1 en sistema Linux
fsck /dev/hda1
 
#Comprobar integridad de archivos en el disco hda1 en sistema ext2
fsck.ext2 /dev/hda1
 
#Comprobar integridad de archivos en el disco hda1 en sistema ext3
fsck.ext3 /dev/hda1
 
#Comprobar integridad de archivos en el disco hda1 en sistema Fat
fsck.vfat /dev/hda1
 
#Comprobar integridad de archivos en el disco hda1 en sistema Dos
fsck.msdos /dev/hda1
 
#Comprobar bloques defectuosos en el disco hda1.
badblocks -v /dev/hda1
```

### FORMATEAR SISTEMA DE ARCHIVOS
```
#formatear hda en sistema Linux
mkfs /dev/hda1
 
#formatear hda en sistema FAT32
mkfs -t vfat 32 -F /dev/hda1
 
#formatear hda en sistema ext2
mke2fs /dev/hda1
 
#formatear hda en sistema ext3
mke2fs -j /dev/hda1
```

### MONTAR SISTEMAS DE ARCHIVOS
```
#montar un disco duro hda2
mount /dev/hda2 /mnt/hda2
 
#montar un disquetera
mount /dev/fd0 /mnt/floppy
 
#montar un cdrom o dvdrom
mount /dev/cdrom /mnt/cdrom
 
#montar cd regrabable dvdrom
mount /dev/hdc /mnt/cdrecorder
 
#montar un cd o dvd regrabable
mount /dev/hdb /mnt/cdrecorder
 
#montar un usb pen-drive o una memoria
mount /dev/sda1 /mnt/usbdisk
 
#montar un archivo o una imagen iso
mount -o loop file.iso /mnt/cdrom
 
#desmontar un dispositivo llamado hda2
umount /dev/hda2
 
#forzar el desmontaje (cuando el dispositivo está ocupado)
fuser -km /mnt/hda2
```

### IMÁGENES ISO Y GRABADORES DE CDROM
```
#montar una imagen iso
mount -o loop cd.iso /mnt/iso
 
#crear imagen iso de cdrom en disco
mkisofs /dev/cdrom > cd.iso
 
#crear imagen iso de un directorio
mkisofs -J -allow-leading-dots -R -V “Label CD” -iso-level 4 -o ./cd.iso data_cd
 
#grabar imagen iso en cdrom
cdrecord -v dev=/dev/cdrom cd.iso
 
#limpiar o borrar un cd regrabable
cdrecord -v gracetime=2 dev=/dev/cdrom -eject blank=fast -force
```

### TRABAJO CON LA SWAP
```
#crear archivo de sistema swap en hda3
mkswap /dev/hda3
 
#activar particion swap en hda3
swapon /dev/hda3
```

### COPIAS DE SEGURIDAD Y BACKUPS
```
#hacer un backup completo de directorio
dump -0aj -f /tmp/archivo.bak /directorio
 
#realizar backup incremental de directorio
dump -1aj -f /tmp/archivo.bak /directorio
 
#restaurar un backup iterativamente
restore -if /tmp/archivo.bak
 
#sincronizar directorios
rsync -rogpav –delete /directorio1 /directorio2
 
#volcar contenido de disco duro a archivo
dd if=/dev/sda of=/tmp/archivo
 
#encontrar y copiar todos los archivos con extensión .txt de un directorio a otro
find /home/usuario -name '*.txt' | xargs cp -av –target-directory=/home/backup/ –parents
 
#encontrar todos los archivos con extensión .log y hacer un archivo bzip
find /var/log -name '*.log' | tar cv –files-from=- | bzip2 > log.tar.bz2
```

## TELECOMUNICACIONES Y OPERACIONES DE RED

### DESCARGA ARCHIVOS INTERNET
```
#descargar archivo desde paginaweb
wget www.paginaweb.com/archivo 
 
#descargar un archivo con la posibilidad de parar la descargar y reanudar más tarde.
wget -c www.paginaweb.com/archivo 
 
#descargar paginaweb completa
wget -r www.paginaweb.com
```

### OPERACIONES DE RED
```
#mostrar la configuración de Ethernet
ifconfig eth0
 
#activar interface eth0
ifup eth0
 
#deshabilitar interface eth0
ifdown eth0
 
#configurar una dirección IP
ifconfig eth0 192.168.1.1 netmask 255.255.255.0
 
#configurar eth0 en modo común para capturar paquetes (sniffing)
ifconfig eth0 promisc
 
#activar la interface ‘eth0′ en modo dhcp
dhclient eth0
 
#mostrar mesa de recorrido
route -n
 
#configurar entrada predeterminada
route add -net 0/0 gw IP_Gateway
 
#configurar ruta estática para buscar la red ’192.168.0.0/16′
route add -net 192.168.0.0 netmask 255.255.0.0 gw 192.168.1.1
 
#eliminar ruta estática
route del 0/0 gw IP_gateway
 
#activar recorrido ip
echo “1” > /proc/sys/net/ipv4/ip_forward
 
#mostrar nombre del host
hostname
 
#buscar nombre del host para resolver el nombre a una dirección ip
host www.paginaweb.com
 
#buscar nombre del host para resolver el nombre a una dirección ip y viceversa
nslookup www.paginaweb.com
 
#mostrar estado de enlace de todas las interfaces
ip link show
 
#mostrar estado de enlace de eth0
mii-tool eth0
 
#mostrar estadísticas de tarjeta de red eth0
ethtool eth0
 
#mostrar todas las conexiones de red activas y sus PID
netstat -tup
 
#mostrar todos los servicios de escucha de red en el sistema y sus PID
netstat -tupl
 
#mostrar todo el tráfico HTTP
tcpdump tcp port 80
 
#mostrar redes inalámbricas
iwlist scan
 
#mostrar configuración de una tarjeta de red inalámbrica
iwconfig wlan0
 
#buscar en base de datos Whois
whois www.paginaweb.com
```

### SSH, SCP Y TUNNELING
```
#iniciar sesion ssh
ssh usuario@servidor.dominio.es
 
#iniciar sesion ssh con compatibilidad X11 (permite ejecutar tareas visuales)
ssh -X usuario@maquina 
 
#iniciar sesion ssh en puerto determinado
ssh -p 15000 usuario@maquina 
 
#copiar archivo mediante scp
scp /archivo usuario@servidor.dominio.es:/directorio
 
#creacion de tunel ssh
ssh -f usuario@servidor.dominio.es -L 2000:servidor.dominio.es:25 -N
 
#redireccion de puertos mediante tunneling
ssh -v -L4001:localhost:4001 usuario@servidor.dominio.es
```

### REDES DE MICROSOFT WINDOWS (SAMBA)
```
#resolución de nombre de red bios
nbtscan ip_addr
 
#resolución de nombre de red bios
nmblookup -A ip_addr
 
#mostrar acciones remotas de un host en windows
smbclient -L ip_addr/hostname
```
