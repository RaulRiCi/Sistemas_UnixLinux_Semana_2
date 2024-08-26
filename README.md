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

4. La sesion pasada montamos dos maquinas virtuales, uno con LVM y otra sin esta caracteristica para administrar volumenes logicos. Usaremos GParted en el sistema que instalamos sin LVM. Antes de ulizar dicha herramienta, entramos a nuestro sistema y ejecutamos "df -h" y "lsblk" para mostrar el uso del espacio en disco de los sistemas de archivos montados.
