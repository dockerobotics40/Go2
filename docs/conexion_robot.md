#  Conexión al robot Unitree Go2

---

##  Descripción

Este apartado explica cómo conectar el robot Unitree Go2 al computador para poder enviar comandos y recibir información en tiempo real.

La conexión se realiza principalmente mediante **Ethernet** y configuración manual de red.

---

##  Conceptos Clave

###  Comunicación por red

* El robot y el PC deben estar en la misma red
* Se utiliza comunicación basada en **DDS**
* Permite:

  * Enviar comandos
  * Recibir estado del robot

###  Interfaz de red

* Es el medio por el cual el PC se comunica con el robot
* Ejemplo:

  * `eth0`
  * `enp3s0`

---

##  Requisitos

* Robot Unitree Go2 encendido
* Cable Ethernet
* Computador con Ubuntu
* Terminal

---

##  Paso 1: Conexión física

* Conectar el robot al PC mediante cable Ethernet
* Encender el robot desde el botón principal

---

##  Paso 2: Activar modo Debug

(Solo necesario para control de bajo nivel)

En el control remoto:

* **L2 + A** → Cambia entre *Stand* y *Low Down*
* **L2 + B** → Activa *Damping Mode*

---

##  Paso 3: Configuración de red

En el computador:

1. Ir a **Settings > Network**
2. Configurar IP manual:

```bash id="k3q9xv"
IP: 192.168.123.222
```

 IP del robot:

```bash id="j8k2lm"
192.168.123.161
```

---

##  Paso 4: Verificar conexión

### Probar conexión con ping:

```bash id="t9r3hz"
ping 192.168.123.161
```

Si hay respuesta → conexión exitosa 

---

##  Paso 5: Identificar interfaz de red

```bash id="z4m1px"
ip a
```

Buscar la interfaz activa (ejemplo: `eth0`)

---

##  Paso 6: Conexión por SSH

```bash id="m2w7rf"
ssh unitree@192.168.123.161
```

### Credenciales:

* Usuario: `unitree`
* Contraseña: `123`

---

##  Verificación dentro del robot

```bash id="r8k3dc"
hostname
ifconfig
```

---

##  Prueba de conectividad

```bash id="p1n6qa"
ping 192.168.123.161
```

---

##  Transferencia de archivos

Enviar archivos al robot:

```bash id="w5t8yb"
scp archivo.py unitree@192.168.123.161
```

---

##  ¿Qué permite esta conexión?

✔ Enviar comandos al robot
✔ Leer sensores
✔ Ejecutar scripts
✔ Control en tiempo real

---

##  Notas importantes

* Ambos dispositivos deben estar en la misma red
* Verificar siempre la IP antes de ejecutar código
* Usar modo Debug solo cuando sea necesario
* Sin conexión correcta, el SDK no funcionará

---

##  Recomendación

Flujo correcto:

1. Conectar Ethernet
2. Configurar IP
3. Verificar con ping
4. Ejecutar ejemplos