# Laboratorio 2

# GParted

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

9. Para comenzar con las modificaciones, comenzaremos modificando /dev/sda8.

![Gparted5](https://github.com/RaulRiCi/Sistemas_UnixLinux_Semana_2/blob/main/GPARTED/GpartedPrueba.png?raw=true)

![Gparted6](https://github.com/RaulRiCi/Sistemas_UnixLinux_Semana_2/blob/main/GPARTED/GpartedPrueba2.png?raw=true)

La imagen muestra la ventana de "Resize/Move" (Redimensionar/Mover) en GParted para la partición /dev/sda8. En este cuadro de diálogo, se está ajustando el tamaño de la partición y la cantidad de espacio libre antes de ella.

- Free space preceding (MiB): Se está configurando 5987 MiB de espacio libre antes de la partición /dev/sda8. Esto implica que la partición se moverá hacia la derecha, dejando espacio no asignado delante de ella.
- New size (MiB): El nuevo tamaño de la partición se ha establecido en 7201 MiB. Esto indica que la partición se reducirá de su tamaño original para liberar espacio adicional.
- Free space following (MiB): El valor es 0, lo que significa que no se dejará espacio libre después de la partición.

![Gparted7](https://github.com/RaulRiCi/Sistemas_UnixLinux_Semana_2/blob/main/GPARTED/GpartedPrueba3.png?raw=true)

Ahora muestra el resultado de las acciones que se muestran anteriormente.

Partición /dev/sda8:

- Ahora ha sido movida hacia la derecha, liberando 5.85 GiB de espacio no asignado (unallocated) entre las particiones lógicas dentro de la extendida.
  Además, el tamaño de la partición /dev/sda8 se ha reducido de 12.88 GiB a 7.03 GiB.
  Espacio no asignado:

- Se ha creado un nuevo espacio no asignado de 5.85 GiB, que antes formaba parte de la partición /dev/sda8.

10. Una vez creado el nuevo espacio, modificaremos las particiones /dev/sda5, /dev/sda6, /dev/sda7.

![Gparted8](https://github.com/RaulRiCi/Sistemas_UnixLinux_Semana_2/blob/main/GPARTED/GpartedPrueba4.png?raw=true)

![Gparted9](https://github.com/RaulRiCi/Sistemas_UnixLinux_Semana_2/blob/main/GPARTED/GpartedPrueba5.png?raw=true)

- Primero modificamos /dev/sda7, moviendo su barra hasta la derecha para recorrerla, despues aplicamos los cambios.

![Gparted10](https://github.com/RaulRiCi/Sistemas_UnixLinux_Semana_2/blob/main/GPARTED/GpartedPrueba6.png?raw=true)

11. De esta manera, /dev/sda7 se recorrio y ahora esta entre el nuevo espacio no asignado de 5.85 GiB y /dev/sda8. Repetimos este paso con /dev/sda5 y /dev/sda6. Esto con la intencion de mover el nuevo espacio al lado de /dev/sda1.

![Gparted11](https://github.com/RaulRiCi/Sistemas_UnixLinux_Semana_2/blob/main/GPARTED/GpartedPrueba7.png?raw=true)

![Gparted12](https://github.com/RaulRiCi/Sistemas_UnixLinux_Semana_2/blob/main/GPARTED/GpartedPrueba8.png?raw=true)

12. Como ultimo paso, modificaremos /dev/sda2 para poder asignar el espacio no asignado a /dev/sda1

![Gparted13](https://github.com/RaulRiCi/Sistemas_UnixLinux_Semana_2/blob/main/GPARTED/GpartedPrueba9.png?raw=true)

13. Asignamos la cantidad de la barra azul correspondiente a /dev/sda2 al mismo nivel que la barra amarilla correspondiente a /dev/sda5

![Gparted14](https://github.com/RaulRiCi/Sistemas_UnixLinux_Semana_2/blob/main/GPARTED/GpartedPrueba10.png?raw=true)

14. Despues de aplicar los cambios, podremos asignar el espacio a /dev/sda1

![Gparted15](https://github.com/RaulRiCi/Sistemas_UnixLinux_Semana_2/blob/main/GPARTED/GpartedPrueba11.png?raw=true)

![Gparted16](https://github.com/RaulRiCi/Sistemas_UnixLinux_Semana_2/blob/main/GPARTED/GpartedPrueba12.png?raw=true)

15. Modificamos la barra de /dev/sda1 recorriendola hasta la derechas, ya que dicho espacio corresponde al no asignado.

![Gparted17](https://github.com/RaulRiCi/Sistemas_UnixLinux_Semana_2/blob/main/GPARTED/GpartedPrueba13.png?raw=true)

- Al aplicar los cambios, /dev/sda1 implementara el espacio libre al suyo. Pasando de pesar 4.12 GiB, a pesar 9.96 GiB.

![Gparted18](https://github.com/RaulRiCi/Sistemas_UnixLinux_Semana_2/blob/main/GPARTED/GpartedPrueba14.png?raw=true)

16. Despues de haber aplicado todos estos cambios, guardamos todo dando click en la flecha verde.

![Gparted19](https://github.com/RaulRiCi/Sistemas_UnixLinux_Semana_2/blob/main/GPARTED/GpartedPrueba15.png?raw=true)

17. Cerramos la ventana de GParted y salimos de la herramienta dando click en Exit.

![Gparted20](https://github.com/RaulRiCi/Sistemas_UnixLinux_Semana_2/blob/main/GPARTED/GpartedPrueba16.png?raw=true)

18. Volvemos a las settings de la maquina virual y en la parte de CD/DVD, seleccionamos la opcion "Use physical drive" para volver a iniciar el sistema de debian con la terminal.

![Gparted21](https://github.com/RaulRiCi/Sistemas_UnixLinux_Semana_2/blob/main/GPARTED/GpartedPrueba17.png?raw=true)

19. Para comprobar los cambios realizados en GParted, volvemos a ejevutar los comandos "df -h" y "lsblk".

![Gparted22](https://github.com/RaulRiCi/Sistemas_UnixLinux_Semana_2/blob/main/GPARTED/GpartedPrueba18.png?raw=true)

# Configuración de discos con LVM (solo para VMs con LVM)
