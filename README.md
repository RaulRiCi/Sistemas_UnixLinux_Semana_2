# Laboratorio 2

# Instalar GParted

## Introduccion:

GParted (GNOME Partition Editor) es una herramienta de software libre que permite crear, redimensionar, mover, y gestionar particiones en discos duros y otros medios de almacenamiento. Es una aplicación basada en GUI (Interfaz Gráfica de Usuario), desarrollada para el entorno de escritorio GNOME, pero también puede usarse en otros entornos.

## Funcionalidades Principales de GParted

- Crear Particiones: Puedes crear nuevas particiones en discos sin particionar o en espacio no asignado.

- Redimensionar Particiones: Permite aumentar o reducir el tamaño de particiones existentes sin perder los datos.

- Mover Particiones: Puedes mover una partición de un lugar a otro en el disco.
  Eliminar Particiones: Borra particiones existentes

GParted está disponible en la mayoría de las distribuciones de Linux y también se ofrece como un sistema operativo en vivo llamado GParted Live, que se puede usar para gestionar particiones sin necesidad de instalarlo en tu sistema operativo. También se puede instalar en sistemas Debian con entorno gráfico.

# Pasos a seguir

1. Descargar GParted:

Entra en el siguiente link(https://gparted.org/livecd.php) o realiza la busqueda.

![GPARTED](https://github.com/RaulRiCi/Sistemas_UnixLinux_Semana_2/blob/main/GPARTED/GPARTEDBUSQUEDA.png?raw=true)

2. Dentro de la pagina, ve a la pestaña de Downloads y selecciona la opcion "Download gparted-live-1.6.0-3-amd64.iso".

![GPARTEDes](https://github.com/RaulRiCi/Sistemas_UnixLinux_Semana_2/blob/main/GPARTED/GPARTEDDescarga.png?raw=true)

3. Dentro de la siguiente pagina se comenzara la descarga y esperamos a que esta termine.

![GPARTEDes2](https://github.com/RaulRiCi/Sistemas_UnixLinux_Semana_2/blob/main/GPARTED/GPARTEDDescarga2.png?raw=true)

![GPARTEDes3](https://github.com/RaulRiCi/Sistemas_UnixLinux_Semana_2/blob/main/GPARTED/GPARTEDDescargaFinal.png?raw=true)

4. La sesion pasada montamos dos maquinas virtuales, una con LVM y otra sin esta caracteristica para administrar volumenes logicos. Usaremos GParted en el sistema que instalamos sin LVM. Antes de ulizar dicha herramienta, entramos a nuestro sistema y ejecutamos "df -h" y "lsblk" para mostrar el uso del espacio en disco de los sistemas de archivos montados.

![Comandos](https://github.com/RaulRiCi/Sistemas_UnixLinux_Semana_2/blob/main/GPARTED/IsblkSinLVM.png?raw=true)

En dicha imagen podemos destacar lo siguiente para el comando df -h:

- udev: Sistema de archivos virtual que usa 946 MB y está montado en /dev.
- tmpfs: Sistema de archivos temporal, montado en /run con un tamaño de 194 MB.
- /dev/sda1: Partición de 4.0 GB, con 1.4 GB usados y 2.4 GB disponibles, montada en /.
- /dev/sda8: Partición de 13 GB, casi completamente disponible (12 GB), montada en /home.
- /dev/sda7: Partición de 338 MB, con 316 MB disponibles, montada en /tmp.
- /dev/sda5: Partición de 1.7 GB, con 1.3 GB disponibles, montada en /var.

Los sistemas de archivos tmpfs también están presentes en otros puntos de montaje como /dev/shm, /run/lock, y /run/user/1000, todos ellos son sistemas temporales que generalmente almacenan datos volátiles en memoria RAM.

En cuanto al comando lsblk, podemos destacar lo siguiente:

- sda: Disco duro principal con un tamaño de 20G.
- sda1: Partición de 4.1G montada en /.
- sda2: Partición de 1K (probablemente una partición extendida).
- sda5: Partición de 1.7G montada en /var.
- sda6: Partición de 976M usada como SWAP.
- sda7: Partición de 371M montada en /tmp.
- sda8: Partición de 12.9G montada en /home.
- sr0: Unidad de CD/DVD con un tamaño de 1024M.

5. Despues de haber comprabado esta informacion, apagamos la maquina virtual

6. Vamos a la configuracion de la maquina virtual, en la parte de CD/DVD seleccionamos la ISO de GParted

![Settings](https://github.com/RaulRiCi/Sistemas_UnixLinux_Semana_2/blob/main/GPARTED/Settings.png?raw=true)

![Settings2](https://github.com/RaulRiCi/Sistemas_UnixLinux_Semana_2/blob/main/GPARTED/Settings2.png?raw=true)

![Settings3](https://github.com/RaulRiCi/Sistemas_UnixLinux_Semana_2/blob/main/GPARTED/Settings3.png?raw=true)

NOTA: Es importante tener marcada la casilla "Connect at power on" para que al momento de iniciar la maquina virtual, muestre la instalacion de GParted, si ese no es el caso, entramos al Boot menu y seleccionamos la opcion de CD.

7. Iniciamos la maquina virtual. Cuando nos muestre la instalacion de GParted, seleccionamos la primera opcion.

![Gparted](https://github.com/RaulRiCi/Sistemas_UnixLinux_Semana_2/blob/main/GPARTED/GpartedInicio.png?raw=true)

Seleccionamos la opcion "Don't touch keymap"

![Gparted2](https://github.com/RaulRiCi/Sistemas_UnixLinux_Semana_2/blob/main/GPARTED/GpartedInicio2.png?raw=true)

La instalacion desplegara una opciones que estan marcadas por default, aceptamos todas.

![Gparted3](https://github.com/RaulRiCi/Sistemas_UnixLinux_Semana_2/blob/main/GPARTED/GpartedInicio3.png?raw=true)

Despues de haber aceptado y finalizado la instalacion, GParted iniciara.

8. Una vez iniciado GParted, podemos ver la informacion del disco

![Gparted4](https://github.com/RaulRiCi/Sistemas_UnixLinux_Semana_2/blob/main/GPARTED/GpartedInicioFinal.png?raw=true)

Podemos destacar la siguiente informacion:

Disco seleccionado: /dev/sda con una capacidad total de 20.00 GiB.

Particiones existentes:

- /dev/sda1: Partición primaria con sistema de archivos ext4, tamaño de 4.12 GiB, y montada como partición de arranque (boot).
- /dev/sda2: Partición extendida que abarca varias particiones lógicas.
- /dev/sda5: Partición lógica dentro de la extendida, con sistema de archivos ext4, y un tamaño de 1.68 GiB.
- /dev/sda6: Partición lógica usada como linux-swap con un tamaño de 976.00 MiB.
- /dev/sda7: Otra partición lógica con sistema de archivos ext4, y un tamaño de 371.00 MiB.
- /dev/sda8: Partición lógica con sistema de archivos ext4, y un tamaño de 12.88 GiB.
- Espacio sin asignar: Hay un pequeño espacio no asignado de 1.00 MiB al final del disco.

Este esquema de particiones es típico en instalaciones de Linux, con una partición primaria para el arranque, una partición extendida que contiene múltiples particiones lógicas, incluyendo particiones para el sistema de archivos, intercambio (swap), y otros propósitos.
