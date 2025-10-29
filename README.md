
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

