## Práctica de Particionado en GPT y MBR

Tanto en GPT como en MBR los comandos son iguales.

### 1. Ver las particiones de la máquina:
```bash
lsblk
```

### 2. Entrar con `fdisk` al disco que queremos seleccionar para hacer las particiones:
```bash
sudo fdisk /dev/sdX
```
- `o` para que la partición esté en formato DOS (MBR).
- `g` para que la partición esté en formato GPT.
- `n` para ver las particiones que tenemos.
- `p` para la partición primaria.
- `e` para las extendidas.
- `w` para guardar la configuración y particiones.

### 3. Formatear todas las particiones con el formato EXT-4:
```bash
mkfs.ext4 /dev/sdX
```

### 4. Montar las particiones y crear en la ruta `/media/datos1`:
```bash
mkdir /media/datos1 && mount /dev/sdb1 /media/datos1
mount | grep /dev/sdb1
```

### 5. Crear contenido dentro de la carpeta:
```bash
for i in $(seq 1 10); do echo "Fichero ${i}" > fichero${i}.txt; done
```

### 6. Añadir en una nueva entrada del `/etc/fstab` el identificador de la partición:
Dentro de `/etc/fstab`, la entrada tendrá 6 columnas de datos:
- UUID
- Opciones de montaje
- Opción dump
- Opción pass

```bash
blkid | grep sdb | awk -F ' ' '{print $2}' | sed 's/"//g'
nano /etc/fstab  # O usar cat para comprobar
cat /etc/fstab
```

### 7. Si hubiera algún error en la configuración del `/etc/fstab`:
```bash
mount -a
ls /media/sdb*
cat /media/sdb5/prueba/prueba.txt
