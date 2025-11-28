rackIot
=======
rackIot es una alternativa a los autómatas convencionales que esta desarrollado de forma abierta mostrando todos los detalles de su desarrollo para que pueda ser modificado tanto en su Hardware como en su software para cubrir todas la necesidades de control que se puedan plantear.
Iotlibre es parte de lo que llamamos la electrónica sostenible que persigue prolongar la vida de los equipos electrónicos y sustituir solamente las piezas que han dejado de funcionar
Funcionalidades básicas
* La interconexión de varias tarjetas electrónicas. de funcionalidades distintas, a través de un mismo bus dotándolas de inteligencia mediante una”Single-Board Computer (SBC)” compatible con una Raspberry pi o similar.
* Compatibilidad con los shields ya existentes para la familia Raspberry que se pueden incluir en el bus de comunicaciones.
* *NodeRed como lógica de proceso con una programación visual para conectar dispositivos, APIs y servicios en flujos.

ecoBus
------
Su función es interconectar los 40 pines de propósito general mediante un bus. Permite la conexión de 3 PCBs con una Raspberry Pi u otra SBC compatible. El diseño de cada PCB esta hecho para comunicarse con la SBC de tal manera que se integre en rackIot y no interfiera con el buen funcionamiento del sistema.
ecoTherm
ecoTherm está diseñado para medir la energía térmica de una instalación con uno o más circuitos de agua a diferentes temperaturas. Este dispositivo puede medir: 
* Temperatura mediante sensores de un solo cable 1-Wire 
* Caudal a través de pulsos proporcionados por contadores de agua 
* Valores analógicos de tensión y corriente incluyendo señales de 4 a 20 mA. 
Para la medición de temperatura y los valores analógicos, se toman muestras en intervalos de un segundo. El valor proporcionado, cada vez que se proporciona la información, por defecto cada minuto, es el promedio de todas las muestras tomadas. 
Los pulsos se miden por interrupciones y el valor proporcionado, en cada período de informe, es el número de interrupciones acumuladas desde el último reinicio del equipo.
La comunicación de ecoTherm con la SBC se hace mediante bus I2C dejando de esta manera el bus serie disponible para comunicaciones de otras tarjetas.

ecoDigital
----------
Esta PCB genera y mide señales de corriente continua en formato digital, aislando rackIot del sistema externo mediante optoacopladores.
* ecoDigital admite hasta 5 entradas de 3–48 V y las interpreta de forma binaria: hay tensión o no hay tensión.
* Proporciona 5 salidas de 3–48 V capaces de suministrar alimentación a relés o dispositivos de baja potencia.

Tanto las salidas como las entradas de esta PCB están conectadas al bus y las lee la SBC en sus pines de entrada y salida(GPIOs)
Interfaz de programación
Node-RED es el interfaz de programación. Esta herramienta permite crear lógicas de control, de forma visual, mediante flujos basados en nodos, sin necesidad de escribir código complejo.
NodeRed para rackIot, facilita la integración del Hardware y permite trabajar con los protocolos mas extendidos como son MQTT, MODBUS y  HTTP.  
Este interfaz, ofrece una capa gráfica intuitiva para configurar, monitorizar y depurar el comportamiento del autómata en tiempo real. Además, su arquitectura abierta y ampliable permite integrar nuevas funcionalidades y PCBs de una forma sencilla.
Otras extensiones compatibles
ecoBus extiende los 40 pines de la Raspberry sin modificaciones de tal manera que se pueda conectar a rackIot cualquier shield compatible que no pertenezca al proyecto. De esta manera se pueden completar las características de nuestra solución con funcionalidades como MODBUS TCP o KNX entre otras.

La envolvente
-------------
La envolvente esta compuesta de una estructura de perfiles de aluminio estándar que se pueden conseguir de forma sencilla en internet. Para cerrar esta envolvente se utilizan planchas de aluminio que crean una jaula de Faraday protegida del ruido.
En el frontal cada PCB tiene su propia terminación, de la anchura que le corresponde, y que esta diseñada con los huecos necesarios para conectores externos.

