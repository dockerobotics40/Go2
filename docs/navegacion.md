# 🧭 Navegación en Unitree Go2
---
# 📌 Descripción
La navegación en el robot Unitree Go2 permite desplazarse en el entorno mediante trayectorias predefinidas o control autónomo básico basado en odometría.
---
# 🧠 Conceptos Clave
# 📍 Waypoints
Puntos en el espacio que el robot sigue secuencialmente.
```text
(0,0) -> (1,0) -> (1,1) -> (0,1)
```
---
# 🛰️ Odometría
Permite estimar:
Posición (x, y, z)
Orientación (roll, pitch, yaw)
Velocidades
---
# 🤖 Navegación Autónoma
Ciclo de control:
Leer estado
Definir objetivo
Calcular error
Ajustar movimiento
---
# ⚙️ Flujo de Navegación
```text
Inicialización -> Odometría -> Objetivo -> Error -> Comando -> Robot -> Repetir
```
---
# 🔁 Diagrama de Flujo
```text
[Inicio]
   |
   v
[Leer Odometría]
   |
   v
[Definir Objetivo]
   |
   v
[Calcular Error]
   |
   v
[Generar Comando]
   |
   v
[Enviar al Robot]
   |
   v
[Repetir]
```
---
# 🚀 Navegación por Waypoints
# 📄 Archivo
```bash
go2_patrol_waypoints.py
```
# ▶️ Ejecución
```bash
python3 go2_patrol_waypoints.py <networkInterface>
```
---
# 🧩 Funcionamiento
Definir puntos
Iterar
Enviar comandos
---
# 📌 Ejemplo
```text
(0,0,0)
(1,0,0)
(1,1,90)
(0,1,180)
```
---
# ⚠️ Limitaciones
No evita obstáculos
No corrige error
---
# 🛰️ Uso de Odometría
# 📄 Archivo
```bash
go2_odometry.py
```
# ▶️ Ejecución
```bash
python3 go2_odometry.py <networkInterface>
```
---
# 📊 Ejemplo
```text
Position: x=1.20, y=0.35
Yaw: 90°
```
---
# 🤖 Navegación Autónoma Básica
# 🧩 Control
```text
error = objetivo - actual
```
---
# 🔁 Loop
```text
leer -> calcular -> enviar
```
---
# 🧪 Flujo de Trabajo
Conectar robot
Verificar conexión
Ejecutar odometría
Definir puntos
Ejecutar navegación
---
# 🧰 Buenas Prácticas
Seguridad
Velocidad baja
Validación
Debug
---
# 🧠 Conclusión
La navegación permite pasar de control manual a comportamiento autónomo básico.