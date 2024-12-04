
Este código configura un reloj basado en un ESP8266 que muestra la hora en una pantalla LED P10 utilizando la biblioteca DMDESP y sincroniza la hora a través de un servidor NTP. Aquí están los principales aspectos del código:

Características Principales
Configuración de la Hora

Obtiene la hora actual desde un servidor NTP (time.google.com).
Utiliza un reloj local como respaldo si no hay conexión WiFi.
Interfaz de Pantalla

Usa una pantalla LED P10 para mostrar la hora en formato "HH MM".
Incluye un efecto de parpadeo para los dos puntos (":").
Conexión WiFi

Configuración inicial usando WiFiManager.
Intento automático de reconexión si se pierde la conexión.
Respaldo en Desconexión

Incrementa la hora local de manera autónoma en caso de no poder sincronizar con el servidor NTP.
Pantalla P10

Configuración para manejar una sola pantalla con la biblioteca DMDESP.
Utiliza la fuente compacta EMSans6x16.
Descripción del Código
1. Configuración WiFi
WiFiManager abre un portal de configuración durante el primer minuto si no hay una red almacenada.
Si no se conecta en el tiempo establecido, el dispositivo intentará reconectar a una red conocida.
2. Obtención de la Hora
Sincroniza la hora desde un servidor NTP con un desfase UTC-3 (Argentina).
Si no se puede conectar al servidor, incrementa los minutos locales como respaldo.
3. Interfaz de Pantalla
Muestra la hora formateada en la pantalla P10.
Los dos puntos entre "HH" y "MM" parpadean cada segundo para simular un reloj real.
4. Reconexión WiFi Automática
Si la conexión WiFi se pierde, el sistema intenta reconectar durante 30 segundos.
Si la reconexión falla, el reloj sigue funcionando con el tiempo local.
5. Frecuencia de Actualización
La pantalla se actualiza cada segundo.
La sincronización con el servidor NTP ocurre cada minuto.
Estructura del Código
Setup
Configura:
WiFi usando WiFiManager.
Cliente NTP para sincronización horaria.
Pantalla LED P10 con brillo y fuente predeterminados.
Loop
Monitorea:
Estado del WiFi y reconexión automática.
Actualización de la hora desde NTP o respaldo local.
Actualización de la pantalla cada segundo.
Funciones Principales
Gestión de WiFi:
Configura la conexión inicial.
Reintenta conectarse si se pierde la conexión.
Sincronización Horaria:
Obtiene la hora desde NTP o ajusta la hora local.
Interfaz de Pantalla:
Muestra la hora en el formato "HH MM" con dos puntos parpadeando.
