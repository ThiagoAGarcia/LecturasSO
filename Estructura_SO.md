# Estructura de un Sistema Operativo

Un sistema operativo es un intermediario entre el **hardware** y el **software**, el cual se encarga de administrar los diferentes recursos de la computadora.

## Interacción con System Calls en Unix

Un usuario no interactúa directamente con las _system calls_ en Unix. En su lugar, usa comandos de la terminal o programas que, internamente, llaman a funciones de bibliotecas como la estándar de C (**glibc**). Estas funciones, a su vez, ejecutan las _system calls_ para que el kernel realice tareas como:

- Abrir archivos.
- Leer datos.
- Crear procesos.

## Traducción de Programas a Código Máquina

Se debe tener un intérprete o compilador adecuado para cada tipo de hardware, ya que cada procesador tiene su propio conjunto de instrucciones. Los programas en alto nivel deben traducirse a código máquina específico para que el hardware pueda ejecutarlos. Esto se hace mediante:

- **Compiladores**.
- **Intérpretes**.
- **Máquinas virtuales** que adaptan el software al sistema en el que se ejecuta.

## Modos de CPU

- **Modo privilegiado**: La CPU tiene acceso a todos los comandos y a toda la memoria.
- **Modo no privilegiado**: La CPU solo puede ejecutar algunos comandos y acceder a porciones de memoria.

En Unix:

- Los procesos del kernel se ejecutan en **modo privilegiado**.
- Cuando se realiza una _system call_ (SC), la CPU pasa a **modo privilegiado** y el control pasa al kernel.

## Características de los Comandos de Shell

- Los comandos de shell son **case-sensitive** (diferencian entre mayúsculas y minúsculas).

## Componentes del Sistema Operativo

- **Hardware**: Donde el sistema operativo se ejecutará.
- **Firmware**: Programación de más bajo nivel que se puede encontrar en la computadora.
- **Software**: El sistema operativo propiamente dicho.
- **Administradores**: El o los encargados de administrar los recursos del sistema.
- **Usuarios**: Quienes efectivamente utilizarán el sistema.

## Tipos de Kernel

### Kernel Monolítico

Es un tipo de núcleo del sistema operativo donde todos los servicios del sistema operan en el mismo espacio de memoria, lo que permite una comunicación más rápida pero puede ser menos seguro.

### MicroKernel

Es un tipo de núcleo del sistema operativo que minimiza las funciones que se ejecutan en el espacio del núcleo, delegando la mayoría de los servicios del sistema a procesos en espacio de usuario, lo que mejora la seguridad y la estabilidad.
