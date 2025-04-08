# 📘 Procesos en Linux

## 💡 ¿Qué es un proceso en Linux?

Un **proceso** es un programa en ejecución. No solo es el archivo del programa, sino todo lo que está pasando en el sistema para que ese programa funcione: memoria, registros, estado, etc.

Cuando ejecutás un comando o abrís una app, el sistema crea un proceso para que eso funcione.

---

## 🔧 ¿Cómo funciona un proceso?

Cuando ejecutás un programa, Linux hace lo siguiente:

1. **Copia el programa a la memoria RAM**.
2. Crea una **estructura de datos** para gestionar ese proceso.
3. Le asigna un **PID (Process ID)** único.
4. Empieza a ejecutarse **paso a paso** bajo control del **kernel** (el núcleo del sistema operativo).

Cada proceso puede tener:

- **Archivos abiertos**
- **Direcciones de memoria asignadas**
- **Recursos como CPU y E/S**
- **Subprocesos (threads) si el programa los usa**

---

## 🧠 ¿Qué hace un proceso?

Depende del programa que esté ejecutando, pero en general puede:

- Calcular cosas (como una calculadora)
- Esperar a que el usuario haga algo (como un menú)
- Leer o escribir archivos
- Comunicarse con otros procesos

También puede **crear nuevos procesos**, por ejemplo, cuando usás un terminal y escribís `ls`, el terminal crea un proceso nuevo para ejecutar ese comando.

---

## 🧱 Tipos de procesos

- **Proceso padre:** El que crea otro proceso (por ejemplo, la terminal).
- **Proceso hijo:** El que fue creado (por ejemplo, `ls`, `nano`, etc).

Usan funciones como `fork()`, `exec()` y `wait()` para crearse y coordinarse.

---

## 🔍 ¿Cómo ver procesos en Linux?

Hay varios comandos para verlos:

- `ps`: Muestra procesos en ejecución.
- `top` o `htop`: Muestra en tiempo real los procesos y su uso de CPU/RAM.
- `pidof nombre`: Te dice el PID de un proceso.
- `kill PID`: Mata (termina) un proceso por su PID.
- `nice` y `renice`: Cambian la prioridad de un proceso.

---

## 🔄 Ciclo de vida de un proceso

1. **Nuevo**: El proceso está por crearse.
2. **Listo**: Espera que el CPU lo atienda.
3. **Ejecutando**: Está corriendo activamente.
4. **Bloqueado**: Espera algo (como leer de un disco).
5. **Terminado**: Ya terminó su ejecución.

---

## 🧵 ¿Y los hilos (threads)?

Un proceso puede tener **múltiples hilos** que se ejecutan al mismo tiempo dentro del mismo espacio de memoria. Eso permite hacer varias tareas en paralelo (como descargar y reproducir un video al mismo tiempo).

---

## 🧠 Ejemplo práctico

Si ejecutás:

```bash
firefox &
```

- Linux lanza `firefox` como proceso.
- El `&` lo lanza en segundo plano.
- Podés ver su PID con `ps`.
- Si querés matarlo: `kill PID`.

---

# ⚡ Interrupciones en Linux

## 🔔 ¿Qué es una interrupción?

Una **interrupción** es una señal que **detiene temporalmente un proceso** para que el procesador atienda un evento urgente.

### Ejemplo:

Estás programando y suena el celular. Atendés, respondés, y volvés al código. Eso es una interrupción.

---

## 💡 ¿Quién genera interrupciones?

- **Dispositivos externos**: teclado, mouse, disco, red.
- **Errores internos**: división por cero, violación de memoria.
- **Software**: llamadas al sistema.

---

## 🔄 ¿Qué pasa cuando ocurre una interrupción?

1. Se genera una señal.
2. El CPU pausa lo que está haciendo.
3. Se ejecuta una función especial: **ISR (Interrupt Service Routine)**.
4. Luego, el CPU **retoma su tarea anterior**.

---

## 📚 [[Tipos de interrupciones]]

| Tipo                 | Generado por          | Ejemplo                             |
| -------------------- | --------------------- | ----------------------------------- |
| **Hardware**         | Dispositivos externos | Teclado, mouse                      |
| **Software**         | Código                | `int 0x80` para llamada al sistema  |
| **Internas (traps)** | El mismo procesador   | División por cero, error de memoria |

---

## 🧠 ¿Por qué son importantes?

- Permiten **respuesta rápida** a eventos.
- Evitan tener que "preguntar" constantemente si algo pasó.
- Son esenciales para **multitarea y eficiencia del CPU**.

---

## Buffer

- en un sistema operativo, un buffer es una región
  de memoria utilizada para **almacenar temporalmente datos mientras se transfieren de un lugar a otro**.
  Los buffers son esenciales para gestionar las
  operaciones de entrada/salida (I/O) y asegurar que
  los datos se procesen de manera eficiente y sin
  interrupciones.

---

## Buffer en linux

- **los buffers son gestionados por el kernel** y se
  utilizan en diversas operaciones de I/O. Un ejemplo
  común es el uso de buffer cache, que almacena datos
  leídos desde el disco para acelerar futuras
  lecturas.

---

## Ejecución de procesos en Linux

Se ejecuta 1 proceso a la vez, **el quantum es el que da un tiempo para cada proceso**. Al finalizar el quantum o ser finalizado de algún modo el proceso, el procesador seguirá con el siguiente proceso.

---

# Tiempo compartido

En Linux, el tiempo compartido (time sharing) **permite que varios usuarios o tareas ejecuten programas simultáneamente**, asignando a cada uno de ellos un intervalo de tiempo en el procesador.
