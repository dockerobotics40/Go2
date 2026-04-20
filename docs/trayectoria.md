#  Trayectoria en Unitree Go2

---

##  1. Descripción General

El módulo de **trayectoria** en el robot **Unitree Go2** permite definir, planificar y ejecutar movimientos controlados en el espacio mediante el seguimiento de puntos o rutas específicas.

Este sistema es clave para:

* Navegación autónoma
* Movimiento preciso
* Ejecución de tareas complejas
* Control de desplazamiento

---

##  2. Concepto de Trayectoria

Una trayectoria es una secuencia de estados deseados que el robot debe seguir a lo largo del tiempo.

```
Trayectoria = {posición + orientación + tiempo}
```

Puede representarse como una serie de puntos:

```
P1 → P2 → P3 → ... → Pn
```

---

##  3. Representación de Trayectorias

Cada punto de la trayectoria (waypoint) contiene:

```
(x, y, z, yaw)
```

Donde:

* `x, y, z` → posición
* `yaw` → orientación

---

###  Ejemplo

```
(0, 0, 0, 0)
(1, 0, 0, 0)
(1, 1, 0, 90)
(0, 1, 0, 180)
```

---

##  4. Tipos de Trayectorias

###  4.1 Trayectoria Discreta

Definida mediante puntos específicos.

```
P1 → P2 → P3
```

---

###  4.2 Trayectoria Continua

Generada mediante funciones matemáticas o interpolación.

```
f(t) → posición en el tiempo
```

---

##  5. Flujo del Sistema de Trayectoria

```
Definir puntos → Generar trayectoria → Control → Ejecución → Corrección
```

---

##  6. Diagrama de Flujo

```
[Inicio]
   ↓
[Definir Waypoints]
   ↓
[Generar Trayectoria]
   ↓
[Leer Estado Actual]
   ↓
[Calcular Error]
   ↓
[Generar Comando]
   ↓
[Enviar al Robot]
   ↓
[Repetir]
```

---

##  7. Implementación en SDK

###  Archivo de referencia

```
go2_trajectory_follow.py
```

---

###  Ejecución

```
python3 go2_trajectory_follow.py <networkInterface>
```

---

##  8. Funcionamiento Interno

El sistema de trayectoria realiza:

1. Definición de puntos objetivo
2. Generación de trayectoria
3. Cálculo de errores respecto al estado actual
4. Generación de comandos de movimiento
5. Ejecución en tiempo real

---

##  9. Ejemplo de Trayectoria

```
Trayectoria:
(0,0) → (1,0) → (2,1) → (3,1)
```

---

##  10. Ejemplo en Python

```
trajectory = [
    (0, 0),
    (1, 0),
    (2, 1),
    (3, 1)
]

for point in trajectory:
    x, y = point
    robot.move_to(x, y)
```

---

##  11. Control de Trayectoria

El seguimiento de trayectoria se basa en minimizar el error:

```
error = objetivo - estado_actual
```

---

##  Loop de Control

```
while True:
    estado = robot.get_state()
    
    error_x = objetivo_x - estado.x
    error_y = objetivo_y - estado.y

    robot.send_velocity(error_x, error_y)
```

---

##  12. Limitaciones

* Dependencia de la odometría
* Error acumulativo
* No incluye evasión de obstáculos
* Sensible a perturbaciones

---

##  13. Flujo de Uso

```
1. Definir trayectoria
2. Inicializar robot
3. Ejecutar controlador
4. Monitorear ejecución
5. Ajustar parámetros si es necesario
```

---

##  14. Buenas Prácticas

* Usar velocidades controladas
* Validar puntos antes de ejecutar
* Evitar cambios bruscos
* Integrar sensores externos
* Monitorear continuamente

---

##  15. Aplicaciones

* Navegación autónoma
* Patrullaje
* Seguimiento de rutas
* Inspección automatizada
* Robótica móvil

---

##  16. Conclusión

El módulo de trayectoria permite transformar objetivos de navegación en movimientos ejecutables, siendo un componente esencial para el control autónomo del robot **Unitree Go2**.

Su integración con la odometría y el control permite desarrollar sistemas avanzados de movilidad y autonomía.