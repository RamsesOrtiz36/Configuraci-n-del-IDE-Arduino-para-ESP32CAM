# Configuraci-n-del-IDE-Arduino-para-ESP32CAM
## Instalación y configuración de la interfaz de programación de arduino
+ https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_dev_index.json se coloca este enlace en preferencias de manegador de tarjetas adicionales
+ En herramientas manejador de placas (board management) buscar "esp32"

## Configurar drivers de ESP32CAM en Linux
Una vez realizada la configuración del Board’s Manager en el IDE de Arduino, es necesario instalar los drivers del ESP32 para que sea posible programarlo. A continuación se muestran los comandos necesarios, los cuales tienen como propósito configurar el entorno para ejecutar el archivo get.py, el cual realiza las configuraciones necesarias para que la IDE de Arduino sea capaz de programar el ESP32.

        sudo usermod -a -G dialout $USER
        wget https://bootstrap.pypa.io/get-pip.py
        sudo apt-get install python3-distutils
        sudo apt-get install python3-apt
        sudo python3 get-pip.py
        sudo pip3 install pyserial
        mkdir -p ~/Arduino/hardware/espressif
        cd ~/Arduino/hardware/espressif
        git clone https://github.com/espressif/arduino-esp32.git esp32
        cd esp32
        git submodule update --init --recursive
        cd tools
        python3 get.py
        
        sudo ln -s /usr/bin/python3 /usr/bin/python

## Prueba de funcionamiento de camara ESP32CAM
Para demostrar la carga de un programa en el ESP32CAM, se realizará la carga del ejemplo Camera Web Server, el cual es un programa que configura el ESP32CAM como una Cámara IP. Las cámaras IP son servidores que emiten el video capturado por su cámara, el cual puede ser recopilado por otros softwares o ser consultados desde Internet o cualquier dispositivo en la red local.

Para comenzar, abre el ejemplo “CameraWebServer”, el cual puedes encontrar en: File, Examples, Esp32, Camera, CameraWebServer. Deberás seleccionar la cámara AI_THINKER comentando la cámara que esté activada y descomentando la cámara deseada. Deberás también colocar el nombre de red y su contraseña en las variables correspondientes

El siguiente paso es configurar la selección de tarjeta y sus características, las cuales deben ser las siguientes:

Board: AI-Thinker.
CPU Frequency: 240 MHz.
Flash Frequency: 80 MHz.
Flash Mode: QIO.
