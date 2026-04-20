#  Control WASD en Unitree Go2

---

##  1. Descripción General

El control **WASD** en el robot **Unitree Go2** permite manejar el robot manualmente mediante el teclado, utilizando un esquema de control intuitivo basado en las teclas **W, A, S, D**.

Este modo es utilizado principalmente para:

* Control manual en tiempo real
* Pruebas de movimiento
* Depuración de comportamiento
* Operación directa sin autonomía

---

##  2. Concepto de Control WASD

El sistema WASD traduce entradas del teclado en comandos de velocidad enviados al robot.

```text
Entrada (teclado) → Procesamiento → Comando de movimiento → Robot
```

---

##  3. Mapeo de Teclas

Las teclas se asignan a movimientos específicos:

```text
W → Avanzar
S → Retroceder
A → Girar a la izquierda
D → Girar a la derecha
```

---

###  Representación

```text
        W
        ↑
A   ←       →   D
        ↓
        S
```

---

##  4. Modelo de Control

Cada tecla genera un comando de velocidad:

```text
W → vx > 0
S → vx < 0
A → wz > 0
D → wz < 0
```

Donde:

* `vx` → velocidad lineal
* `wz` → velocidad angular

---

##  5. Flujo del Sistema

```text
Lectura de teclado → Interpretación → Generación de comando → Envío al robot
```

---

##  6. Diagrama de Flujo

```text
[Inicio]
   ↓
[Leer Teclado]
   ↓
[Detectar Tecla]
   ↓
[Asignar Movimiento]
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

```bash
go2_wasd_control.py
```

---

###  Ejecución

```bash
python3 go2_wasd_control.py <networkInterface>
```

---

##  8. Funcionamiento Interno

El sistema realiza:

1. Captura de entrada de teclado
2. Identificación de tecla presionada
3. Conversión a comando de velocidad
4. Envío del comando al robot
5. Actualización en tiempo real

---

##  9. Ejemplo en Python

```python
key = get_key()

if key == 'w':
    robot.send_velocity(vx=0.5, wz=0.0)

elif key == 's':
    robot.send_velocity(vx=-0.5, wz=0.0)

elif key == 'a':
    robot.send_velocity(vx=0.0, wz=0.5)

elif key == 'd':
    robot.send_velocity(vx=0.0, wz=-0.5)
```

---

##  10. Control en Tiempo Real

El control WASD funciona en un loop continuo:

```python
while True:
    key = get_key()
    
    # Procesar entrada
    # Enviar comando
```

---

##  11. Limitaciones

* No es autónomo
* Requiere intervención humana constante
* No incluye planificación de trayectoria
* No evita obstáculos automáticamente

---

##  12. Flujo de Uso

```text
1. Conectar robot
2. Ejecutar script WASD
3. Controlar con teclado
4. Monitorear comportamiento
5. Detener cuando sea necesario
```

---

##  13. Buenas Prácticas

* Usar velocidades bajas inicialmente
* Operar en entornos seguros
* Tener botón de parada (emergencia)
* Evitar movimientos bruscos
* Supervisar constantemente

---

##  14. Aplicaciones

* Pruebas de movimiento
* Calibración
* Teleoperación
* Debug de sistemas
* Entrenamiento de operadores

---

##  15. Conclusión

El control WASD proporciona una forma simple, directa e intuitiva de interactuar con el robot **Unitree Go2**, permitiendo validar rápidamente su comportamiento y realizar pruebas en tiempo real sin necesidad de sistemas autónomos complejos.