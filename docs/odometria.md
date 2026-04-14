# 🛰️ Odometría en Unitree Go2

---

## 📌 1. Descripción General

La odometría en el robot **Unitree Go2** es el sistema encargado de estimar en tiempo real el estado cinemático del robot, incluyendo su posición, orientación y velocidades, a partir de sensores internos.

Este módulo es fundamental para:

* Navegación autónoma
* Control de trayectoria
* Estimación de estado
* Integración con sistemas externos (ej. ROS)

---

## 🧠 2. Modelo de Estado del Robot

La odometría describe el estado del robot mediante tres componentes principales:

---

### 📍 2.1 Posición

Define la ubicación del robot en un sistema de referencia cartesiano.

```
x → eje longitudinal (avance)
y → eje lateral
z → altura
```

---

### 🔄 2.2 Orientación

Define la rotación del robot utilizando ángulos de Euler.

```
roll  → inclinación lateral
pitch → inclinación frontal
yaw   → orientación (rotación en el plano)
```

---

### ⚡ 2.3 Velocidades

Representan el movimiento lineal y angular del robot.

```
vx → velocidad en eje x
vy → velocidad en eje y
wz → velocidad angular (yaw)
```

---

## ⚙️ 3. Arquitectura del Sistema de Odometría

El flujo de procesamiento de la odometría sigue el siguiente esquema:

```
Sensores → Procesamiento → Estimación de Estado → Publicación de Datos
```

### Componentes involucrados:

* Sensores internos (IMU, encoders)
* Módulo de procesamiento
* Modelo cinemático
* Interfaz de comunicación

---

## 🔁 4. Flujo Operativo

```
[Inicio]
   ↓
[Lectura de Sensores]
   ↓
[Estimación de Posición]
   ↓
[Estimación de Orientación]
   ↓
[Actualización del Estado]
   ↓
[Publicación de Datos]
   ↓
[Loop continuo]
```

---

## 🚀 5. Implementación en SDK

### 📄 Archivo de referencia

```
go2_odometry.py
```

---

### ▶️ Ejecución

```
python3 go2_odometry.py <networkInterface>
```

Donde:

* `<networkInterface>` corresponde a la interfaz de red utilizada para la comunicación con el robot.

---

## 🧩 6. Funcionamiento Interno

El módulo de odometría realiza las siguientes operaciones:

1. Adquisición de datos desde sensores
2. Procesamiento de señales
3. Cálculo de posición y orientación
4. Actualización del estado interno
5. Publicación o visualización de datos

---

## 📊 7. Ejemplo de Salida

```
Position: x=1.20, y=0.35, z=0.00
Orientation: roll=0.01, pitch=0.02, yaw=1.57
Velocity: vx=0.10, vy=0.00, wz=0.05
```

---

## 🧪 8. Ejemplo de Integración en Python

```
state = robot.get_state()

# Posición
x = state.position.x
y = state.position.y
z = state.position.z

# Orientación
roll = state.orientation.roll
pitch = state.orientation.pitch
yaw = state.orientation.yaw

# Velocidades
vx = state.velocity.x
vy = state.velocity.y
wz = state.velocity.yaw

# Output
print(f"Posición: ({x}, {y}, {z})")
print(f"Orientación: ({roll}, {pitch}, {yaw})")
print(f"Velocidad: ({vx}, {vy}, {wz})")
```

---

## ⚠️ 9. Limitaciones del Sistema

La odometría presenta limitaciones inherentes:

* Deriva acumulativa en el tiempo
* Sensibilidad a errores de medición
* Dependencia de sensores internos
* No incluye percepción del entorno

---

## 🧪 10. Flujo de Uso Recomendado

```
1. Establecer conexión con el robot
2. Ejecutar módulo de odometría
3. Validar datos en tiempo real
4. Integrar con sistema de control o navegación
```

---

## 🧰 11. Buenas Prácticas

* Verificar conectividad antes de ejecución
* Monitorear datos continuamente
* Validar consistencia de la información
* Integrar con sensores externos (ej. LIDAR, cámaras)
* Realizar calibraciones periódicas

---

## 🧠 12. Aplicaciones

La odometría es utilizada en:

* Navegación autónoma
* Seguimiento de trayectorias
* Localización del robot
* Sistemas SLAM
* Integración con ROS

---

## 🧠 13. Conclusión

La odometría constituye un componente esencial en el sistema de control del **Unitree Go2**, proporcionando información crítica sobre el estado del robot en tiempo real.

Su correcta implementación y uso permite el desarrollo de aplicaciones avanzadas de navegación y autonomía.