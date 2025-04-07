# Comandos Básicos de Linux

## Navegación y Directorios

`pwd` → Muestra el directorio actual.

`cd [directorio]` → Cambia al directorio especificado.

`mkdir [directorio]` → Crea un nuevo directorio.

- `-p` → Crea toda la ruta especificada si no existe.
- `-m` → Especifica permisos al crear el directorio.

`rmdir [directorio]` → Borra directorios vacíos.

`ls [opciones] [directorio]` → Lista el contenido de un directorio.

- `-a` → Muestra archivos ocultos.
- `-A` → Muestra archivos ocultos sin `.` y `..`
- `-l` → Muestra detalles de los archivos en formato largo.
- `-R` → Lista los directorios de forma recursiva.
- `-h` → Muestra tamaños en formato legible.

`tree [opciones]` → Muestra la estructura de directorios.

- `-a` → Incluye archivos ocultos.
- `-d` → Muestra solo directorios.
- `-p` → Muestra permisos de archivos y directorios.

## Información del Usuario y Sistema

`whoami` → Muestra el nombre del usuario actual.

`who -q` → Muestra los usuarios conectados.

`who -m / who am i` → Muestra información sobre el usuario actual.

`tty` → Indica en qué consola se encuentra el usuario.

`cal` → Muestra un calendario.

- `-3` → Muestra el mes anterior, actual y siguiente.
- `[mes] [año]` → Muestra el calendario del mes y año especificado.
- `[año]` → Muestra todo el calendario del año.

`date` → Muestra la fecha y hora actuales.

`uname [opciones]` → Muestra información del sistema operativo.

- `-a` → Muestra toda la información.
- `-s` → Nombre del sistema operativo.
- `-r` → Versión del sistema.
- `-m` → Tipo de máquina.

`passwd` → Cambia la contraseña del usuario.

`su [opciones]` → Permite cambiar al usuario root.

- `-c "[comando]"` → Ejecuta un comando como root.

## Historial de Comandos

`history [nro | c]` → Muestra el historial de comandos.

- `c` → Limpia el historial.
- `nro` → Muestra los últimos `nro` comandos.

`set +o history` → Apaga el historial.

`set -o history` → Activa el historial.

### Variables del historial:

- `$HISTFILE` → Archivo donde se guarda el historial (`~/.bash_history`).
- `$HISTFILESIZE` → Tamaño máximo del archivo de historial.
- `$HISTSIZE` → Número máximo de comandos en memoria.

## Manipulación de Archivos

`touch [archivo]` → Crea un archivo vacío o actualiza su fecha.

`stat [archivo]` → Muestra información detallada del archivo.

`file [archivo]` → Indica el tipo de archivo.

`cp [origen] [destino]` → Copia archivos o directorios.

- `-r` → Copia directorios recursivamente.
- `-i` → Pide confirmación si el archivo ya existe.
- `-p` → Conserva permisos y fechas.
- `-f` → Fuerza la copia.
- `-n` → No sobreescribe archivos existentes.

`mv [origen] [destino]` → Mueve o renombra archivos.

- `-f` → Fuerza la operación sin preguntar.
- `-i` → Pide confirmación antes de sobrescribir.

`rm [archivo]` → Borra archivos o directorios.

- `-r` → Borra recursivamente.
- `-f` → Borra sin pedir confirmación.
- `-i` → Pide confirmación antes de borrar.
- `-v` → Muestra lo que está borrando.

## Salida de Texto y Consola

`echo [-ne] [texto]` → Imprime texto en la salida estándar.

- `-n` → No agrega nueva línea al final.
- `-e` → Interpreta secuencias de escape (`\n`, `\t`, etc.).

`clear` → Limpia la consola.

### Variables:

- `$HOME` → Devuelve el directorio personal del usuario.

## Tipos de Archivos en `ls -l`

- `-` → Archivo común.
- `d` → Directorio.
- `b` → Archivo especial de bloques.
- `c` → Archivo especial de caracteres.
- `l` → Enlace simbólico.
- `p` → Named pipe (comunicación entre procesos).
- `s` → Archivo de socket.

## Comando `cat`

`cat [archivo]` → Muestra el contenido de un archivo en la terminal.

- `cat archivo1 archivo2 > archivo3` → Concatena archivos y guarda la salida en otro archivo.
- `cat -n archivo` → Muestra el contenido con numeración de líneas.

## Comando `find`

`find [ruta] [opciones]` → Busca archivos y directorios en una ruta específica.

- `-name [nombre]` → Busca por nombre.
- `-type [tipo]` → Filtra por tipo (`f` archivo, `d` directorio, etc.).
- `-size [n][cwbkMG]` → Filtra por tamaño.
- `-user [usuario]` → Busca archivos de un usuario específico.
- `-group [grupo]` → Busca archivos de un grupo específico.
- `-mtime [días]` → Busca archivos modificados hace `n` días.
- `-atime [días]` → Busca archivos accedidos hace `n` días.
- `-maxdepth [n]` → Limita la profundidad de búsqueda.
- `-exec [comando] {}` → Ejecuta un comando en los archivos encontrados.

**Conceptos del Sistema Operativo**

es una capa entre el hardware y el software

El sistema operativo (SO) es el intermediario entre el hardware y los programas. Su función es proporcionar una interfaz sencilla para que los procesos no tengan que preocuparse por los detalles del hardware.

## Jerarquía de Almacenamiento

- **Registros del CPU** → Más rápidos, pero limitados.
- **Caché** → Rápida, pero pequeña.
- **RAM** → Volátil, pero de rápido acceso.
- **Discos SSD/HDD** → Almacenamiento persistente, más lento.
- **Almacenamiento externo** → USB, discos en red.

## Interrupciones y Excepciones

- **Interrupción** → Señal que un dispositivo envía al CPU para solicitar atención.
- **Excepción** → Evento inesperado dentro del CPU (por ejemplo, error de división por cero).

### Llamadas al Sistema

Permiten a los programas acceder a recursos del SO, como archivos, memoria y dispositivos.

### Concurrencia, Paralelismo y Multiprocesamiento

- **Concurrencia** → Procesos parecen ejecutarse a la vez en un solo CPU.
- **Paralelismo** → Procesos realmente ejecutándose al mismo tiempo en múltiples CPUs.
- **Multiprocesamiento** → Uso de varios procesadores o núcleos simultáneamente.

`Kernel y Shell en Unix/Linux`
El kernel y el shell son dos componentes fundamentales de los sistemas operativos Unix/Linux. Cada uno tiene un rol específico en la interacción entre el usuario y el hardware del sistema.

1. **Kernel (Núcleo del sistema operativo)**
   El kernel es la parte central del sistema operativo. Se encarga de gestionar los recursos del hardware y proporcionar servicios esenciales a los programas. Es responsable de:
   ✅ Manejo de la memoria
   ✅ Control de procesos
   ✅ Gestión de dispositivos
   ✅ Administración del sistema de archivos
   ✅ Control de la comunicación entre hardware y software

El kernel es el **"cerebro"** del sistema operativo y funciona en segundo plano, sin que los usuarios interactúen directamente con él.

2. **Shell (Intérprete de comandos)**
   El shell es la interfaz que permite a los usuarios comunicarse con el sistema operativo. Actúa como un intermediario entre el usuario y el kernel.

**Existen dos tipos principales de shell**:
🔹 Shell de línea de comandos (CLI): Permite interactuar mediante comandos en la terminal. Ejemplos: Bash, Zsh, Fish.
🔹 Shell gráfico (GUI): Interfaces visuales como GNOME, KDE o XFCE, donde el usuario interactúa con el sistema mediante ventanas y botones.

Funciones del Shell:
✅ Interpreta los comandos que ingresa el usuario
✅ Ejecuta programas y scripts
✅ Permite automatizar tareas con scripts
✅ Gestiona la entrada y salida de datos

**¿Qué es una computadora?**
es una que maquina procesa datos

**diferencia entre dato y informacion**
computación -> computo
informática -> información
es la cantidad de informacion de lectura para ese dato

sintaxis -> como esta estructurado el dato
semantica -> es el significado

sistema batch -> son sistemas que se llaman por lotes, son sistemas que se manda la entrada y cuando termina me manda el resultado, no es necesario esperar para ese resultado sino que cuando termina lo devuelve.
