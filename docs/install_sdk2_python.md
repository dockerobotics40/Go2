# 🐍 Instalación de SDK2 Python para Unitree Go2

---

## 📌 Descripción

El **SDK2 Python de Unitree** permite controlar el robot Go2 mediante comandos de alto nivel de forma sencilla y rápida.

Es ideal para:

* Prototipos
* Pruebas rápidas
* Integración con IA (NumPy, OpenCV, etc.)

A diferencia de C++, Python es más fácil de usar, aunque con menor rendimiento en tiempo real.

---

## 🧠 Conceptos Clave

### ⚡ SDK2 Python

* Basado en `unitree_sdk2`
* Interfaz simplificada para control del robot
* Uso orientado a objetos

### 🔗 Comunicación

* Utiliza **DDS (Data Distribution Service)**
* Permite:

  * Enviar comandos
  * Recibir estado del robot

### 🤖 Control de alto nivel

* No requiere manejar motores directamente
* Permite:

  * Movimiento (velocidades)
  * Modos (stand, sit, walk, etc.)

---

## ⚙️ Requisitos

* Ubuntu 20.04
* Python 3
* Git
* ROS2 (opcional pero recomendado)

---

## 🚀 Instalación del SDK2 Python

### 1️⃣ Clonar el repositorio

```bash
git clone https://github.com/unitreerobotics/unitree_sdk2_python.git
```

### 2️⃣ Entrar al directorio

```bash
cd unitree_sdk2_python
```

### 3️⃣ Instalar dependencias

```bash
pip3 install -r requirements.txt
```

---

## 🔧 Configuración de red

Antes de ejecutar cualquier código, debes definir la interfaz de red:

```bash
ip a
```

Busca tu interfaz (ejemplo: `eth0`, `enp3s0`)

---

## ▶️ Ejecución de ejemplo

Ir al directorio de ejemplos:

```bash
cd example/go2
```

Ejecutar:

```bash
python3 go2_sport_client_example.py <networkInterface>
```

Ejemplo:

```bash
python3 go2_sport_client_example.py eth0
```

---

## 🎮 Comandos disponibles

### 🔢 Con parámetros

* `move = "vx, vy, vyaw"` → Movimiento en ejes
* `velocity_move` → Movimiento continuo
* `balance_stand` → Control de orientación

### 🔘 Sin parámetros

* `stand_up` → Levantarse
* `stand_down` → Acostarse
* `sit` → Sentarse
* `recovery_stand` → Recuperar postura
* `stop_move` → Detener movimiento

---

## ⌨️ Control con teclado (WASD)

Ejecutar:

```bash
python3 go2_wasd_control.py <networkInterface>
```

### Controles:

* **W** → Avanzar
* **S** → Retroceder
* **A** → Izquierda
* **D** → Derecha
* **Q** → Rotar izquierda
* **E** → Rotar derecha
* **ESC** → Salir

---

## 📊 ¿Cuándo usar SDK2 Python?

✔ Prototipos rápidos
✔ Desarrollo sencillo
✔ Integración con IA
✔ Pruebas de comportamiento

---

## ⚠️ Notas importantes

* No usar para control crítico en tiempo real
* Menor rendimiento que C++
* Ideal para pruebas y desarrollo inicial
* Requiere conexión de red con el robot

---

## 📚 Recomendación

Usar:

* Python → Desarrollo rápido
* C++ → Control de bajo nivel y tiempo real