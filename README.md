# particionado.-Yago-N

**PRACTICA DE PARTICIONADO EN GPT Y MBR.

Tanto en GPT y MBR los comandos son iguales.

1. Vemos la particiones de la maquina:
- lsblk.

2. Entramos con el Fdisk al disco que queremos seleccionar para hacer las particiones:
- Sudo fdisk /dev/sdX.
- o para que la partición este en formato DOS (MBR).
- g para que la partición este en formato GPT.
- n para ver las particiones que tenemos.
- p para la partición primaria.
- e para las extendidas.
- w para guardar la configuración y particiones.

3. Pasamos todas las particiones con el formato EXT-4.
- mkfs.ext4 /dev/sdx.

4. Montamos las particiones y creamos en la ruta /media/datos1:
- mkdir /media/datos1 && mount /dev/sdb1 /media/datos1.
- mount | grep /dev/sdb1.

5. Creamos contenido dentro de la carpeta:
- for i in $(seq 1 10); do echo "Fichero ${i}" >

6. añadir en una nueva entrada del /etc/fstab el identificador de la partición. Dentro del
/etc/fstab la entrada va a tener 6 columnas de datos: -UUID, -Opciones de montaje, -Opción dump, -Opción pass:

- blkid | grep sdb | awk -F ' ' '{print $2}' | sed 's/"//g'..
- nano /etc/fstab o cat /etc/fstab para comprobar que todo se ha copiado al archivo.

7.Si tuviéramos algún error en la configuración del /etc/fstab :
- mount -a.
- ls /media/sdb*
- cat /media/sdb5/prueba/prueba.txt

**
