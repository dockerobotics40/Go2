# 🧠 Control High-Level en Unitree Go2

---

## 📌 1. Descripción General

El control **High-Level** en el robot **Unitree Go2** permite interactuar con el robot mediante comandos abstractos de alto nivel, sin necesidad de gestionar directamente actuadores o señales de bajo nivel.

Este tipo de control está diseñado para:

* Simplificar la programación del robot
* Ejecutar movimientos complejos fácilmente
* Implementar comportamientos autónomos
* Integrar aplicaciones de navegación y control

---

## 🧠 2. Concepto de High-Level Control

El control de alto nivel abstrae la complejidad del hardware, permitiendo al usuario enviar comandos como:

```text
Caminar hacia adelante
Girar
Detenerse
Seguir una trayectoria
```

En lugar de controlar directamente:

```text
Motores → Torque → Posiciones articulares
```

---

## ⚙️ 3. Arquitectura del Sistema

```text
Usuario → API High-Level → Controlador Interno → Hardware
```

---

### Componentes:

* Interfaz de usuario (script Python)
* API High-Level del SDK
* Controlador interno del robot
* Sistema de actuadores

---

## ⚙️ 4. Modelo de Control

El usuario envía comandos de velocidad o movimiento:

```text
vx → velocidad lineal
vy → movimiento lateral
wz → velocidad angular
```

---

### 📌 Ejemplo conceptual

```text
Avanzar → vx > 0
Girar → wz ≠ 0
Detener → vx = 0, wz = 0
```

---

## 🔁 5. Flujo del Sistema

```text
Definir comando → Procesar → Enviar → Ejecutar → Retroalimentación
```

---

## 🔁 6. Diagrama de Flujo

```text
[Inicio]
   ↓
[Definir Comando]
   ↓
[Enviar a API]
   ↓
[Procesamiento Interno]
   ↓
[Ejecutar Movimiento]
   ↓
[Leer Estado]
   ↓
[Repetir]
```

---

## 🚀 7. Implementación en SDK

### 📄 Archivo de referencia

```bash
go2_high_level.py
```

---

### ▶️ Ejecución

```bash
python3 go2_high_level.py <networkInterface>
```

---

## 🧩 8. Funcionamiento Interno

El sistema High-Level realiza:

1. Recepción de comandos del usuario
2. Traducción a comandos internos
3. Control automático de estabilidad
4. Ejecución del movimiento
5. Retroalimentación del estado

---

## 🧪 9. Ejemplo en Python

```python
# Avanzar
robot.send_velocity(vx=0.5, vy=0.0, wz=0.0)

# Girar
robot.send_velocity(vx=0.0, vy=0.0, wz=0.5)

# Detener
robot.send_velocity(vx=0.0, vy=0.0, wz=0.0)
```

---

## 🎯 10. Control Continuo

```python
while True:
    robot.send_velocity(vx=0.3, vy=0.0, wz=0.1)
```

---

## ⚠️ 11. Limitaciones

* Menor control detallado sobre actuadores
* Dependencia del controlador interno
* Menos flexible que Low-Level
* Limitado a funciones expuestas por el SDK

---

## 🧪 12. Flujo de Uso

```text
1. Conectar robot
2. Inicializar API High-Level
3. Enviar comandos
4. Monitorear estado
5. Ajustar comportamiento
```

---

## 🧰 13. Buenas Prácticas

* Usar valores de velocidad moderados
* Validar comandos antes de enviar
* Implementar parada de emergencia
* Monitorear constantemente
* Combinar con odometría para mayor precisión

---

## 🧠 14. Aplicaciones

* Navegación autónoma
* Control de movimiento básico
* Seguimiento de trayectorias
* Sistemas de control inteligentes
* Integración con ROS

---

## 🧠 15. Comparación con Low-Level

```text
High-Level → Fácil de usar, menos control
Low-Level  → Complejo, máximo control
```

---

## 🧠 16. Conclusión

El control **High-Level** permite interactuar de manera eficiente con el robot **Unitree Go2**, facilitando el desarrollo de aplicaciones complejas sin necesidad de gestionar detalles internos del hardware.

Es la opción recomendada para la mayoría de aplicaciones de navegación y control autónomo.