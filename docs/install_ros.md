#  Instalación de ROS2 para Unitree Go2

---

##  Descripción

ROS2 (Robot Operating System 2) es un framework de desarrollo robótico que permite la comunicación entre nodos mediante **DDS (Data Distribution Service)**, el mismo middleware utilizado por el robot Unitree Go2.

Su uso permite integrar sensores, control de movimiento, navegación y percepción en un entorno modular y escalable.

---

##  Conceptos Clave

###  DDS (Data Distribution Service)

* Middleware de comunicación usado por ROS2 y el Go2
* Permite el intercambio de datos en tiempo real
* Basado en el modelo publicación/suscripción

###  Nodos ROS2

* Procesos independientes que se comunican entre sí
* Permiten separar funcionalidades como:

  * Control
  * Percepción
  * Navegación

###  Tópicos

* Canales de comunicación donde se publican y reciben datos
* Ejemplo:

  * Comandos de movimiento
  * Estado del robot

---

##  Requisitos

* Ubuntu 20.04 (recomendado)
* Conexión a internet
* Terminal

---

##  Instalación de ROS2 (Foxy)

### 1️ Configurar locale

```bash
sudo apt update
sudo apt install locales
sudo locale-gen en_US en_US.UTF-8
sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
export LANG=en_US.UTF-8
```

### 2️ Agregar repositorios

```bash
sudo apt install software-properties-common
sudo add-apt-repository universe
```

### 3️ Agregar clave GPG

```bash
sudo apt update
sudo apt install curl
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg
```

### 4️ Agregar repositorio ROS2

```bash
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null
```

### 5️ Instalar ROS2

```bash
sudo apt update
sudo apt install ros-foxy-desktop
```

---

##  Configuración del entorno

### 1️ Cargar ROS2 automáticamente

```bash
echo "source /opt/ros/foxy/setup.bash" >> ~/.bashrc
source ~/.bashrc
```

### 2️ Verificar instalación

```bash
ros2 run demo_nodes_cpp talker
```

En otra terminal:

```bash
ros2 run demo_nodes_py listener
```

---

##  Uso con Unitree Go2

Según el SDK del Go2:

* ROS2 se utiliza junto con DDS para:

  * Controlar movimiento en tiempo real
  * Integrar sensores
  * Implementar navegación

###  Ejecución típica

**Simulación:**

```bash
go2_sport_client
```

**En ROS2:**

```bash
ros2 run <paquete> <nodo>
```

---

##  ¿Para qué usar ROS2 en Go2?

✔ Control en tiempo real
✔ Integración de sensores
✔ Navegación autónoma
✔ Arquitectura modular
✔ Comunicación eficiente con DDS

---

##  Notas importantes

* ROS2 usa DDS, igual que el SDK del Go2 → compatibilidad directa
* Es ideal para aplicaciones avanzadas (navegación, percepción, IA)
* Para control básico también puedes usar directamente la SDK2

---

##  Recomendación

Usar:

* SDK2 → Control directo (bajo y alto nivel)
* ROS2 → Sistemas complejos y escalables