Configurar un servidor DHCP en un router es un proceso relativamente sencillo. A continuación, te proporciono una guía básica para configurar DHCP en un router en Packet Tracer:

1. Accede al modo de configuración global:

```bash
Router> enable
Router# configure terminal
```

2. Configura el DHCP pool, especificando el rango de direcciones IP que se asignarán, la puerta de enlace predeterminada, y los servidores DNS:

```bash
Router(config)# ip dhcp excluded-address <primera IP a excluir> <última IP a excluir>
Router(config)# ip dhcp pool <nombre>
Router(dhcp-config)# network <red> <máscara de red>
Router(dhcp-config)# default-router <IP de la puerta de enlace>
Router(dhcp-config)# dns-server <IP del servidor DNS>
```

Por ejemplo:

```bash
Router(config)# ip dhcp excluded-address 192.168.1.1 192.168.1.20
Router(config)# ip dhcp pool MiPoolDHCP
Router(dhcp-config)# network 192.168.1.0 255.255.255.0
Router(dhcp-config)# default-router 192.168.1.1
Router(dhcp-config)# dns-server 8.8.8.8
```

3. (Opcional) Configura el tiempo de concesión de direcciones DHCP:

```bash
Router(dhcp-config)# lease <tiempo en minutos>
```

4. Sal del modo de configuración DHCP y de la configuración global:

```bash
Router(dhcp-config)# exit
Router(config)# exit
```

Con estos comandos, has configurado un servidor DHCP básico en tu router en Packet Tracer. Asegúrate de adaptar las direcciones IP y los parámetros según tu topología y necesidades específicas.
