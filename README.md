# PROYECTO ROS2 HUMBLE 

Aqui va que es ros xd :v

## PREPARACION ESPACIO DE TRABAJO

### CREACION DEL PORYECTO 

 1. Crecion del workspace

### ` mkdir -p siro_ws/src `

2. ingresamos a `siro_ws`

    ### `cd siro_ws `

3. compilacion del proyecto

### ` colcon build `

    Se crearon las carpetas de compilacion de este proyecto 
    '''
    /install
    /build
    /log 
    '''

4. Entramos a la carpeta src

### ` cd src `

5. Creacion del paquete con ament_cmake `cpp_siro` 

    ### ` ros2 pkg create --build-type ament_cmake cpp_siro `

    se crea la carpeta del paquete `cpp_siro`
    que es el que contiene los archivos de compilacion del paquete y archivos de dependencias e información 

    '''
    /cpp_siro
    '''
6. Ingresamos a la carpeta del paquete 

    ### `cd cpp_siro `

    Aqui enocntramos varios documentos y directorios

    '''
    /includes
    /cpp_siro
    /launch
    CMakeLists.txt
    package.xml
    '''

    En el directorio `include ` se guardan archivos necesarios para la compilacion

    En el directorio ` cpp_siro` se guardan los nodos 

    El archivo `CMakelists.txt` guarda ka configuracion del paquete como dependencias, regitro de nodos, directorios, versiones c++, ....

    El archivo `package.xml` contiene informacion del paquete sobre el pauqete como la descripcion, el autor, el contacto, las dependencias y herramientas 
6. Compilar proyecto again

### ` colcon build `

## Creacion de nodos 

1. para crear un nodo nos ubicamos en el directorio `src` del paquete 

### `cd siro_ws/src/cpp_siro/src`

2. creamos un nodo de publicacion que se llama `siro_node_publicador.cpp` que va a estar publicando en el topico `chatter`

    Escribimos el codigo del nodo 


3. creamos un nodo de publicacion que se llama `siro_node_suscriptor.cpp` que va a estar publicando en el topico `chatter`

    Escribimos el codigo del nodo

4. Configurar el archivo `CMakelists.txt`

    configurar la version y el nombre del paquete 
    '''
    cmake_minimum_required(VERSION 3.5)
    project(cpp_siro)
    '''
    especificar version de c++
    '''
        # Default to C++14
    if(NOT CMAKE_CXX_STANDARD)
      set(CMAKE_CXX_STANDARD 14)
    endif()

    '''
    Especificar dependencias del paquete `ament_cmake `, `rclcpp `, `std_msgs `

    creamos los nodos como ejecutables
    '''
        # Agrega el ejecutable del nodo
    add_executable(siro_node_suscriptor src/siro_node_suscriptor.cpp)
    add_executable(siro_node_publicador src/siro_node_publicador.cpp)
    '''
    Especifica las dependencias para el ejecutable    
    '''
    ament_target_dependencies(siro_node_suscriptor rclcpp std_msgs)
    ament_target_dependencies(siro_node_publicador rclcpp std_msgs)
    '''
    