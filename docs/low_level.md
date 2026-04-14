# ⚙️ Control Low-Level en Unitree Go2

---

## 📌 1. Descripción General

El control **Low-Level** en el robot **Unitree Go2** permite interactuar directamente con los actuadores del robot, gestionando variables como posición, velocidad y torque de cada articulación.

Este tipo de control está diseñado para:

* Máximo control sobre el robot
* Desarrollo de controladores personalizados
* Investigación en robótica avanzada
* Implementación de algoritmos de bajo nivel

---

## 🧠 2. Concepto de Low-Level Control

A diferencia del control High-Level, el control Low-Level opera directamente sobre las articulaciones del robot.

```text
Control Low-Level → Motores → Articulaciones → Movimiento
```

El usuario define explícitamente:

```text
Posición
Velocidad
Torque
```

---

## ⚙️ 3. Arquitectura del Sistema

```text
Usuario → Controlador Personalizado → Señales de Bajo Nivel → Actuadores
```

---

### Componentes:

* Script de control (Python/C++)
* Interfaz de comunicación
* Controlador de bajo nivel
* Motores y sensores

---

## ⚙️ 4. Modelo de Control

Cada articulación del robot puede ser controlada mediante:

```text
q  → posición
dq → velocidad
tau → torque
```

---

### 📌 Ejemplo conceptual

```text
Mover articulación → q objetivo
Controlar velocidad → dq
Aplicar fuerza → tau
```

---

## 🔁 5. Flujo del Sistema

```text
Leer estado → Calcular control → Generar señales → Enviar → Ejecutar → Repetir
```

---

## 🔁 6. Diagrama de Flujo

```text
[Inicio]
   ↓
[Leer Estado del Robot]
   ↓
[Calcular Control]
   ↓
[Generar Señales]
   ↓
[Enviar a Actuadores]
   ↓
[Actualizar Estado]
   ↓
[Repetir]
```

---

## 🚀 7. Implementación en SDK

### 📄 Archivo de referencia

```bash
go2_low_level.py
```

---

### ▶️ Ejecución

```bash
python3 go2_low_level.py <networkInterface>
```

---

## 🧩 8. Funcionamiento Interno

El sistema Low-Level realiza:

1. Lectura de estado de cada articulación
2. Cálculo de control (PID u otros)
3. Generación de señales de control
4. Envío directo a actuadores
5. Ejecución en tiempo real

---

## 🧪 9. Ejemplo en Python

```python
state = robot.get_state()

for joint in state.joints:
    desired_position = 0.5
    
    error = desired_position - joint.position
    torque = kp * error - kd * joint.velocity
    
    robot.send_joint_command(
        joint_id=joint.id,
        position=desired_position,
        velocity=0.0,
        torque=torque
    )
```

---

## 🎯 10. Control en Tiempo Real

```python
while True:
    state = robot.get_state()
    
    # Control personalizado
    # Cálculo de señales
    # Envío a actuadores
```

---

## ⚠️ 11. Riesgos y Limitaciones

* Alto riesgo de daño al robot
* Requiere conocimiento avanzado
* Sensible a errores de implementación
* No incluye estabilidad automática

---

## 🧪 12. Flujo de Uso

```text
1. Conectar robot
2. Activar modo Low-Level
3. Leer estado de sensores
4. Calcular control
5. Enviar comandos
6. Monitorear comportamiento
```

---

## 🧰 13. Buenas Prácticas

* Implementar límites de seguridad
* Usar controladores probados (PID)
* Evitar valores extremos
* Monitorear constantemente
* Tener parada de emergencia

---

## 🧠 14. Aplicaciones

* Control de locomoción avanzado
* Investigación en robótica
* Desarrollo de controladores personalizados
* Simulación y pruebas dinámicas
* Optimización de movimiento

---

## 🧠 15. Comparación con High-Level

```text
Low-Level  → Máximo control, alta complejidad
High-Level → Fácil uso, menor control
```

---

## 🧠 16. Conclusión

El control **Low-Level** proporciona acceso total al comportamiento del robot **Unitree Go2**, permitiendo desarrollar soluciones altamente personalizadas.

Sin embargo, su uso requiere experiencia avanzada y medidas estrictas de seguridad para evitar daños en el sistema.