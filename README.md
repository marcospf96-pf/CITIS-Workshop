
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


## Ataque de fuerza bruta con Airacrack al handshake WPA

Seleccione la opción 2 para realizar un ataque de fuerza bruta contra el archivo de handshake WPA, que decodificará los paquetes
usando Crunch y Airacrack. Por defecto, se atacará el último archivo capturado. Pulse Y para seleccionar el
directorio y el BSSID del último archivo capturado. A continuación, introduzca la ruta a su diccionario o archivo rockyou.txt y pulse
la tecla Intro para iniciar el ataque de fuerza bruta al handshake WPA.

<img width="573" height="387" alt="Screenshot 2025-10-29 at 6 21 04 p m" src="https://github.com/user-attachments/assets/7f8a856d-0a72-48ba-9720-4a19f0aa3bf5" />


Seleccione el conjunto de caracteres; en este caso, la opción 6 para seleccionar caracteres en minúscula y numéricos que intentarán descifrar la clave Wi-Fi mediante fuerza bruta utilizando un conjunto de caracteres alfanuméricos. Para iniciar el ataque, pulse la tecla Enter/Intro.


<img width="505" height="314" alt="Screenshot 2025-10-29 at 6 22 07 p m" src="https://github.com/user-attachments/assets/19a0325c-72b2-4d9e-8cc6-de926fa2ab5e" />

Si el intento tiene éxito, se mostrará la contraseña o la clave Wi-Fi, como se ilustra en la figura siguiente.

<img width="528" height="187" alt="Screenshot 2025-10-29 at 6 22 35 p m" src="https://github.com/user-attachments/assets/da95eb21-349c-4101-8c24-fdc69cc1c4dc" />


## Ataque basado en reglas de Hashcat para el handshake WPA

Dado que todos conocemos las capacidades de Hashcat, Airgeddon ofrece la oportunidad de utilizarlo para
descifrar la clave Wi-Fi. Seleccione la opción 5 e introduzca la ruta a su archivo de handshake WPA, diccionario o archivo basado en reglas.

Aquí proporcionamos la ruta al archivo best64.rule, que se utilizará para realizar un ataque basado en reglas de Hashcat.

Ataque de descifrado de claves.

<img width="504" height="404" alt="Screenshot 2025-10-29 at 6 23 29 p m" src="https://github.com/user-attachments/assets/4c4ccb24-63a3-47a7-80be-285b566c7839" />

Pulsa ENTER para iniciar el ataque, que intentará descifrar la comunicación cifrada con WPA.

<img width="439" height="608" alt="Screenshot 2025-10-29 at 6 24 00 p m" src="https://github.com/user-attachments/assets/c5f50186-4abf-4304-b864-4ef1f069f088" />

Tras una prueba exitosa, se le pedirá que guarde el resultado. Para guardar la clave enumerada, utilice la tecla Intro.

<img width="568" height="117" alt="Screenshot 2025-10-29 at 6 24 33 p m" src="https://github.com/user-attachments/assets/1678b057-dd69-46b6-98ab-c1b7ce668817" />

Puedes acceder al archivo guardado para leer la contraseña de Wi-Fi descifrada.

<img width="414" height="190" alt="Screenshot 2025-10-29 at 6 25 12 p m" src="https://github.com/user-attachments/assets/11bb2337-604f-42ab-860d-e784e01d647f" />


## Ataque de gemelo malicioso

Un gemelo malicioso es una falsificación de un punto de acceso Wi-Fi (AP falso) que se hace pasar por uno legítimo, pero que está configurado deliberadamente
para interceptar el tráfico inalámbrico. Al crear un sitio web falso y atraer usuarios a él, este tipo de ataque
puede utilizarse para obtener credenciales de clientes legítimos.

Desde el menú principal, seleccione la opción 7 para Ataque de gemelo malicioso.

<img width="444" height="304" alt="Screenshot 2025-10-29 at 6 25 51 p m" src="https://github.com/user-attachments/assets/fc3a74f9-0130-4d3d-9e07-21077ece9707" />

Luego seleccione la opción 9, que buscará puntos de acceso cercanos.

<img width="488" height="389" alt="Screenshot 2025-10-29 at 6 26 21 p m" src="https://github.com/user-attachments/assets/5f9bb9be-0ccc-41da-a57a-bafa4d4be70f" />

Continúe pulsando la tecla ENTER y aparecerá una ventana para escanear puntos de acceso WPA/WPA2.

<img width="506" height="222" alt="Screenshot 2025-10-29 at 6 27 40 p m" src="https://github.com/user-attachments/assets/4b3f30cf-719f-4959-b90f-d828efc8dee9" />


Para finalizar el escaneo, pulse CTRL+C y se mostrará una lista de todos los puntos de acceso escaneados. Elija el punto de acceso que le interese.

<img width="496" height="334" alt="Screenshot 2025-10-29 at 6 28 03 p m" src="https://github.com/user-attachments/assets/08f4dbc0-d107-409f-bdfa-8749925f7789" />

Seleccione la opción 2 para un ataque de desautenticación que desconecte al cliente del punto de acceso seleccionado. Posteriormente, podría solicitarle que habilite el modo de persecución DoS, lo cual rechazamos.
<img width="567" height="141" alt="Screenshot 2025-10-29 at 6 28 28 p m" src="https://github.com/user-attachments/assets/024d0772-e06d-41f5-9ee1-8a90fe6816d3" />


Antes de iniciar la desautenticación e intentar capturar el handshake, se le harán algunas preguntas como:

¿Desea suplantar su dirección MAC durante este ataque? [s/N]: s
¿Ya tiene un archivo capturado? [s/N]: N
Valor de tiempo en segundos: 20
Pulse la tecla ENTER para aceptar la propuesta.

<img width="528" height="230" alt="Screenshot 2025-10-29 at 6 30 21 p m" src="https://github.com/user-attachments/assets/87e749e5-c765-497c-a902-9d382d877c5e" />


Volverán a aparecer las dos ventanas. Una intentará un ataque de desautenticación, mientras que la otra intentará capturar el protocolo de enlace WPA entre el cliente y el punto de acceso tras la desautenticación.

<img width="523" height="261" alt="Screenshot 2025-10-29 at 6 30 41 p m" src="https://github.com/user-attachments/assets/8f106409-b3cb-4409-811c-c01651604c68" />

Espere hasta que aparezca el protocolo de enlace WPA en la esquina superior derecha de la ventana y, a continuación, pulse CTRL^C.

<img width="531" height="215" alt="Screenshot 2025-10-29 at 6 31 15 p m" src="https://github.com/user-attachments/assets/b82c12c7-f99e-4f63-b711-bbd7e1d9d327" />



Como puede ver, ya tenemos el protocolo de enlace WPA para el punto de acceso «raaj». Acepte la propuesta guardando el archivo .cap
en su sistema y pulsando la tecla Intro. A continuación, si utiliza un portal cautivo, se le pedirá que
especifique la ruta del archivo que contendrá la contraseña de la red Wi-Fi.

Si la contraseña de la red Wi-Fi se obtiene mediante el portal cautivo, deberá decidir dónde guardarla: en /root/rajpwd.txt

<img width="576" height="210" alt="Screenshot 2025-10-29 at 6 33 24 p m" src="https://github.com/user-attachments/assets/524ace24-f750-4240-b9a4-94e5ee62d0b9" />


Crea un portal cautivo para realizar phishing a tu cliente y selecciona el idioma en el que se mostrará el portal web.

Para inglés, elegimos la opción 1. Se abrirán seis ventanas al enviar la opción seleccionada.

<img width="499" height="261" alt="Screenshot 2025-10-29 at 6 33 55 p m" src="https://github.com/user-attachments/assets/c7a3fde7-089d-425f-9397-3ea59e509a26" />


AP: Crea un punto de acceso falso llamado "raaj" para el cliente.
DHCP: Inicia un servicio DHCP falso para proporcionar una IP maliciosa al cliente.
DNS: Inicia una consulta DNS maliciosa.
Desautenticación: Desautentica al cliente del punto de acceso original "raaj".
Servidor web: Inicia un servicio para alojar el portal cautivo.
Control: Intenta interceptar la contraseña de Wi-Fi una vez que el cliente se conecte al punto de acceso falso.
Nota: No cierres las ventanas; desaparecerán después de que se haya capturado la contraseña.

<img width="512" height="326" alt="Screenshot 2025-10-29 at 6 34 31 p m" src="https://github.com/user-attachments/assets/167deab9-81be-442d-b745-c66c60b4e3d8" />


Todos los clientes que se conecten al punto de acceso original “raaj” se desconectarán y, al intentar reconectarse,

descubrirán dos puntos de acceso con el mismo nombre. Cuando el cliente se conecta al punto de acceso falso, es redirigido al
portal cautivo.

<img width="329" height="599" alt="Screenshot 2025-10-29 at 6 35 05 p m" src="https://github.com/user-attachments/assets/9b278bcd-6fd8-4098-985d-a87009bae425" />

El portal web cautivo le pedirá que introduzca la contraseña de la red Wi-Fi para obtener acceso a internet.

<img width="327" height="555" alt="Screenshot 2025-10-29 at 6 35 34 p m" src="https://github.com/user-attachments/assets/ea307dbe-9fab-439c-b71d-fb6cac0b98ae" />

Si el cliente proporciona la clave Wi-Fi, la contraseña se capturará en texto plano en la ventana de control.

<img width="529" height="184" alt="Screenshot 2025-10-29 at 6 36 01 p m" src="https://github.com/user-attachments/assets/d7ca7ebf-fa95-4d82-81d8-584baba09eae" />

Además, guarda la contraseña en el archivo que proporcionaste durante la propuesta.

<img width="499" height="213" alt="Screenshot 2025-10-29 at 6 36 28 p m" src="https://github.com/user-attachments/assets/1bc42d41-13df-4aae-8086-c271f1a181d0" />

## PMKID ataque

PMKID es el identificador único que utiliza el punto de acceso (AP) para registrar la PMK del cliente.

PMKID se compone de la dirección MAC del AP, la dirección MAC del cliente, la PMK y el nombre de la PMK. Para obtener más información, consulte aquí.
Para capturar el PMKID, ejecute el script de Airgeddon y seleccione la opción 5, como se muestra a continuación.

<img width="382" height="320" alt="Screenshot 2025-10-29 at 6 37 05 p m" src="https://github.com/user-attachments/assets/cb274969-0429-46fa-bacc-d7810ca0380c" />


Luego, presione nuevamente 5 y espere a que el script capture los SSID cercanos.

<img width="488" height="347" alt="Screenshot 2025-10-29 at 6 37 26 p m" src="https://github.com/user-attachments/assets/73080598-5e52-4050-8954-adbd2d24263d" />


Ahora verá una lista de objetivos. Nuestro objetivo para el número 6 es “Amit 2.4 G”. A continuación, simplemente INTRODUZCA el tiempo de espera en
segundos que desea que el script espere antes de capturar el PMKID. Supongamos que 25 segundos es
tiempo suficiente.

<img width="504" height="369" alt="Screenshot 2025-10-29 at 6 37 51 p m" src="https://github.com/user-attachments/assets/577e3fa8-66d2-41de-9a8d-1ff775a4a992" />


¡Efectivamente, aquí podemos ver cómo se captura un PMKID!

<img width="536" height="357" alt="Screenshot 2025-10-29 at 6 38 16 p m" src="https://github.com/user-attachments/assets/ad94b7c5-7aa8-4505-88dd-ed0f8dc8de9b" />


Luego, simplemente guarda este PMKID como un archivo .cap. Primero presiona Y, luego ENTER, ingresa la ruta y listo.

<img width="566" height="180" alt="Screenshot 2025-10-29 at 6 38 48 p m" src="https://github.com/user-attachments/assets/53158967-8a09-41b3-8aa1-88696f158b6f" />

Now, with an integrated aircrack-ng we can crack the cap file within the airgeddon script itself like this:
Just choose dictionary attack and yes and then the dictionary file.

Ahora, con aircrack-ng integrado, podemos descifrar el archivo cap dentro del propio script de airgeddon de esta manera: Simplemente selecciona "Ataque de diccionario" y luego "Sí", y finalmente el archivo de diccionario.

<img width="524" height="320" alt="Screenshot 2025-10-29 at 6 39 19 p m" src="https://github.com/user-attachments/assets/6f600f7f-9a1f-4185-bf79-6493bd2a49c9" />

Efectivamente, tenemos la contraseña que necesitábamos.

<img width="529" height="286" alt="Screenshot 2025-10-29 at 6 39 44 p m" src="https://github.com/user-attachments/assets/ae452a90-ca4b-4b8e-a126-d4d9ae79689b" />

