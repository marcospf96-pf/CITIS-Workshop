
# CITIS-Workshop

##  Configurar el ambiente

### Identificar NIC para conexión inalambrica

```
ifconfig
```

### Actualizar Linux

```
sudo apt update
```

### Collect Repository

```
git clone https://github.com/v1s1t0r1sh3r3/airgeddon.git
cd airgeddon
ls
```

### Run script

```
./airgeddon.sh
```


#### Ejemplo

<img width="455" height="237" alt="scriptrun" src="https://github.com/user-attachments/assets/025cf981-fb18-4ae8-9a1a-7fb8fbc1d4ac" />


### Validación del Script

El script realizará validaciones sobre las librerias instaladas, según sean los resultados de la validación se requiere la instalación de paquetes.

<img width="361" height="375" alt="validacion" src="https://github.com/user-attachments/assets/db5b9dd9-5336-4f17-8766-94ff77317d56" />


Ahora seleccione la interfaz de red; para una conexión inalámbrica, esta será wlan0; por lo tanto, elija la opción
3 como se muestra en la imagen.

<img width="449" height="118" alt="seleccionwlan" src="https://github.com/user-attachments/assets/b34e4bf0-13c2-4040-9ebe-1cd2ab92410c" />

### Configurar NIC wireless como monitor

A continuación, pondremos la tarjeta Wi-Fi en modo monitor; la tarjeta está en modo gestionado de forma predeterminada, lo que significa que
no puede capturar paquetes de distintas redes; sin embargo, el Wi-Fi en modo monitor sí puede capturar paquetes
que se transmiten por el aire.

Seleccione la opción 2 para el modo monitor.

<img width="472" height="386" alt="monitor" src="https://github.com/user-attachments/assets/2fdb3aae-3546-4fec-b2a6-017ec290c9bc" />

## Captura de Handshake y Desautenticación

El monitor wlan0mon está en modo monitor. Intentamos capturar los paquetes de handshake de la red inalámbrica para los protocolos WPA y WPA2.

Seleccione la opción 5 para obtener la herramienta de captura de Handshake/PMKID.

<img width="466" height="277" alt="handshake" src="https://github.com/user-attachments/assets/fb79f58d-3fa8-4e6e-a097-577c60fed10f" />

Seleccione la opción 6 para capturar el handshake.

Al seleccionar la opción 6, aparecerá una nueva ventana que buscará redes WPA y WPA2 e intentará capturar el handshake de 4 vías en un archivo .cap. Tras obtener el punto de acceso (AP) del objetivo, puede pulsar CTRL+C.

<img width="415" height="492" alt="hsk2" src="https://github.com/user-attachments/assets/d6f70ea6-ddec-4626-a79e-6655ee5b6ebb" />


## Seleccionar SSID

Se mostrará una lista de todos los ESSID (nombres de Wi-Fi) analizados, así como su BSSID (dirección MAC) y el tipo de protocolo de cifrado ENC.

Luego, selecciona e identifica SSID con el que se trabajará.

NOTA: Los asteriscos (*) indican puntos de acceso de cliente; estos son posiblemente los mejores «clientes» para adquirir
handshakes. Cualquier punto de acceso que implemente el protocolo WEP ENC será ignorado por Airgeddon.


<img width="509" height="643" alt="selecttarget" src="https://github.com/user-attachments/assets/9bd112b1-79b1-4d18-bbeb-8b0ce9a25993" />


## Ataque de desautenticación

Este ataque envía paquetes de desconexión a uno o más clientes que actualmente están asociados a un punto de acceso específico.

La desconexión de clientes puede realizarse por varios motivos:

• Recuperación de un ESSID oculto. Se trata de un ESSID que no se está difundiendo. También se conoce como:
“enmascarado”.
• Captura de protocolos de enlace WPA/WPA2 forzando a los clientes a volver a autenticarse.
• Generación de solicitudes ARP (los clientes Windows a veces vacían su caché ARP al desconectarse).


Ahora se le pedirá que seleccione un tipo de ataque; elija la opción 2 para el ataque de repetición de muerte, que utilizará
un ataque de desautenticación para desconectar a todos los clientes antes de capturar el protocolo de enlace entre el punto de acceso y el cliente.  Posteriormente, selecciona un tiempo de espera en segundos.

<img width="584" height="384" alt="attack" src="https://github.com/user-attachments/assets/299a6afa-2193-46f0-9b3c-8e2d07501be7" />


Verás que aparecen dos ventanas. Tras la desautenticación, una intentará realizar un ataque de desautenticación, mientras que la otra intentará registrar el protocolo de enlace de cuatro vías entre el cliente y el punto de acceso.

<img width="613" height="303" alt="Screenshot 2025-10-29 at 6 00 56 p m" src="https://github.com/user-attachments/assets/74509670-de4d-4388-8c97-29aee0ed0975" />

Espere hasta que aparezca el protocolo de enlace WPA en la esquina superior derecha de la ventana y, a continuación, pulse CTRL^C.

<img width="621" height="230" alt="Screenshot 2025-10-29 at 6 01 05 p m" src="https://github.com/user-attachments/assets/1bbd2bb1-6233-4360-8d52-c35118580875" />


Como puede ver, este es el protocolo de enlace WPA para el punto de acceso "raaj". Ahora puede guardar este archivo .cap en su sistemas.

<img width="626" height="114" alt="Screenshot 2025-10-29 at 6 03 32 p m" src="https://github.com/user-attachments/assets/933b5f5c-0319-45b9-8c38-e380da0f3b1d" />


## Ataque de diccionario Aircrack para el apretón de manos WPA

La contraseña de Wi-Fi se guardaba en un archivo de enlace, pero como estaba cifrada, tuvimos que descifrarla para obtenerla.

Vuelva al menú principal seleccionando la opción 0.

<img width="624" height="269" alt="Screenshot 2025-10-29 at 6 04 50 p m" src="https://github.com/user-attachments/assets/58abd140-5271-4898-83ff-326664708fa7" />

Te mostrará las opciones de ataque; selecciona la opción 6 para el menú de descifrado WPA/WPA2 sin conexión.

<img width="364" height="305" alt="Screenshot 2025-10-29 at 6 05 31 p m" src="https://github.com/user-attachments/assets/1cee8f30-2153-45ec-a127-4ce034d77933" />

Ahora utilizaremos un diccionario para descifrar el archivo capturado durante el handshake. Seleccione la opción 1, como se muestra en la imagen.

<img width="355" height="167" alt="Screenshot 2025-10-29 at 6 05 36 p m" src="https://github.com/user-attachments/assets/9db73db9-81a6-4919-99f1-673246adf781" />


Por defecto, se utilizará el último archivo capturado para el ataque de fuerza bruta. Pulse Enter para seleccionar la ruta y
el BSSID del último archivo capturado. A continuación, indique la ruta de su diccionario o rockyou.txt y
pulse Intro para iniciar un ataque de diccionario contra el handshake WPA.


<img width="503" height="340" alt="Screenshot 2025-10-29 at 6 10 11 p m" src="https://github.com/user-attachments/assets/06eeaf7e-deff-4b71-8b11-d952eed2b054" />

A continuación, se mostrará la contraseña o clave Wi-Fi, como se ilustra en la figura siguiente. Si desea guardar la clave, se le pedirá que lo haga.

<img width="477" height="381" alt="Screenshot 2025-10-29 at 6 10 51 p m" src="https://github.com/user-attachments/assets/85056b00-0453-454d-8beb-38633449f6b6" />



