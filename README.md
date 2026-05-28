# Practica 1: Seguimiento de caminos, explícitos e implícitos.
Ampliación de Robótica. Robots Móviles. Práctica 1: Seguimiento de caminos, con ROS2 y CoppeliaSIM.

## 🛠️ Tecnologías y Entorno
* **SO:** Ubuntu 22.04 (WSL)
* **Middleware:** ROS 2 Humble
* **Simulador:** CoppeliaSim Edu (V4.10)
* **Lenguaje:** C++

## 🎮 Instalación y Compilación
Clona este repositorio dentro de la carpeta `src` de tu espacio de trabajo de ROS 2 y compila el paquete:
  ```bash
  cd ~/ros/amp_rob_ws/src
  git clone https://github.com/rumonru05-byte/P1-Seg_Caminos.git
  cd ~/ros/amp_rob_ws
  colcon build --packages-select seg_tray
  ```

---

## Parte I: Seguimiento de Caminos Explícitos (Navegación P2P) 🤖

Esta parte de la práctica consiste en la implementación de un nodo de ROS 2 en C++ para el control cinemático y navegación punto a punto (Point-to-Point, P2P) de un robot móvil diferencial (Pioneer P3DX) dentro del simulador CoppeliaSim.

### 🎯 _Objetivo_
El robot es capaz de leer una lista de *waypoints* desde un archivo de parámetros YAML, calcular su error de orientación y distancia euclídea actual, y aplicar leyes de control proporcional y no lineal para navegar de forma suave hacia cada objetivo.

### 🚀 _Lanzamiento_
1. Abre CoppeliaSim, carga p2p_scene.ttt y pulsa Play ▶️.
2. Lanza el nodo:
   ```bash
   ros2 launch seg_tray nav_p2p_launch.py
   ```
  

### ⚙️ _Configuración del Robot Pioneer P3DX_
La escena de CoppeliaSim tiene configurada una ruta absoluta para el archivo de parámetros nav_params.yaml. Para que el robot cargue tus waypoints correctamente, debes actualizar esta ruta dentro del script del Pioneer P3DX en CoppeliaSim:
1. En CoppeliaSim, haz doble clic sobre el icono del script asociado al Pioneer P3DX.
2. Localiza la variable file y actualiza la ruta con tu directorio local:
   ```bash
   local file="/home/tu_usuario/ros/amp_rob_ws/src/P1-Seg_Caminos/seg_tray/config/nav_params.yaml"
   ```

### 📉 _Resultados_
![Demostración de Navegación P2P](videos_P1/nav-p2p.gif)
* Para eliminar el viraje inicial que se observa, se propone implementar un flag de inicialización. Esto consistiría en ignorar el controlLoop() hasta que el nodo haya recibido el primer mensaje válido de odometría, evitando así que el robot calcule errores basándose en una pose inicial por defecto.
* El vídeo ha sido acelerado (x3) para acortar su duración; el robot se mueve en tiempo real respetando el parámetro max_linear_speed: 1.2 definido en el archivo de configuración.

---

## Parte II: Seguimiento de Caminos Implícitos (Persecución pura) 🤖
_(En desarrollo)_




