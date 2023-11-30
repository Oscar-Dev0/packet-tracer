ROUT-CENTRAL

Comandos para poner y condigurar el rauter


en 
config t
hostname ROUT-CENTRAL
// Configuracion de banner 
banner motd "Acceso Restringido"
// Condigurar si se hacer mas de 3 intentos se cierra la seccion y se bloquea por 3 minutos
login block-for 120 attempts 3 within 60
// Esto configura que la contraseña minimo tiene que tener 8 letras
security passwords min-length 8


1. **Configurar los Serials:**
   - En la interfaz serial del router que actúa como DCE, utiliza el comando `clock rate` para establecer la velocidad del reloj y asigna direcciones IP a las interfaces seriales.

   ```bash
   Router(config)# interface serial0/0/0
   Router(config-if)# clock rate <velocidad en bps>
   Router(config-if)# ip address <primera utilizable> <máscara de red>
   ```

2. **Configurar las IPs de Servidores y Computadoras:**
   - En cada servidor, asigna la décima IP utilizable y en cada computadora, asigna la vigésima IP utilizable.

   ```bash
   Server(config)# interface <interface>
   Server(config-if)# ip address <décima utilizable> <máscara de red>

   PC(config)# interface <interface>
   PC(config-if)# ip address <veinteava utilizable> <máscara de red>
   ```

3. **Configurar EIGRP:**
   - Activa EIGRP en el router y configura las redes que participarán en el enrutamiento.

   ```bash
   Router(config)# router eigrp 1
   Router(config-router)# network <red>
   ```

4. **Configurar Servidor Web y DNS:**
   - En el servidor, habilita el servicio DNS y configura la dirección IP del servidor web para la resolución de nombres.

   ```bash
   Server(config)# ip dns server
   Server(config)# ip dns primary www.cisco.com <IP del servidor web>
   ```

5. **Configurar DHCP:**
   - Configura el servidor DHCP en el router para asignar direcciones IP automáticamente a dispositivos en la red.

   ```bash
   Router(config)# ip dhcp excluded-address <primera IP> <última IP>
   Router(config)# ip dhcp pool <nombre>
   Router(dhcp-config)# network <red>
   Router(dhcp-config)# default-router <IP del router>
   Router(dhcp-config)# dns-server <IP del servidor DNS>
   ```

6. **Configurar Router Inalámbrico:**
   - Configura las opciones del router inalámbrico, incluyendo la dirección IP, la red a asignar a los dispositivos inalámbricos, la contraseña WPA y la configuración de filtrado MAC.

   ```bash
   Router(config)# interface wireless0/0
   Router(config-if)# ip address <cuarta utilizable> <máscara de red>
   Router(config-if)# ssid <nombre> disable
   Router(config-if)# wpa-psk <clave WPA>
   Router(config-if)# mac-filter <opciones>
   ```

Estos comandos son ejemplos generales y deberás personalizarlos según tu configuración específica en Packet Tracer. Recuerda también que Packet Tracer puede tener limitaciones en términos de características de hardware y software en comparación con dispositivos y sistemas reales.
Para configurar SSH en un router en Packet Tracer, sigue estos pasos generales:

1. **Generar claves RSA:**
   - Accede al modo de configuración global del router.

   ```bash
   Router> enable
   Router# configure terminal
   ```

   - Genera las claves RSA para la autenticación SSH.

   ```bash
   Router(config)# crypto key generate rsa
   ```

   - Sigue las indicaciones para establecer el tamaño de la clave (por ejemplo, 1024 bits).

2. **Configurar el acceso SSH:**
   - Configura el nombre de usuario y la contraseña para el acceso SSH.

   ```bash
   Router(config)# username <nombre_de_usuario> privilege 15 secret <contraseña>
   ```

   - Habilita el transporte SSH.

   ```bash
   Router(config)# line vty 0 4
   Router(config-line)# transport input ssh
   ```

   - Indica la versión del protocolo SSH (opcional).

   ```bash
   Router(config)# ip ssh version 2
   ```

3. **Conectarse al router mediante SSH:**
   - Utiliza un cliente SSH (como PuTTY) para conectarte al router.

   ```
   PuTTY Configuration:
   Host Name (or IP address): <IP_del_router>
   Port: 22
   Connection Type: SSH
   ```

   - Ingresa el nombre de usuario y la contraseña configurados anteriormente.

Recuerda adaptar los comandos según tu configuración específica en Packet Tracer. Ten en cuenta que en Packet Tracer, debido a sus limitaciones, es posible que no se admitan todas las funciones avanzadas de SSH y algunos comandos exactos pueden variar según la versión del software.
