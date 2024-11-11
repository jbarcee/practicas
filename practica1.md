# **PRACTICA 1**
# INTERCONEXIÓN DE EQUIPOS EN ESCRITORIOS VIRTUALES

## **Configuración del server de Ubuntu**

### *Cambio de hostname*
![](/img/cambiohostnameserver.png)

### *Configuración de tarjetas de red*
![](/img/tarjetasredserver.png)

### *Comprobamos que se ha aplicacdo la configuración con el comando ip a*
![](/img/comprobarip.png)

***
## **Configuración del cliente de Ubuntu**

### *Cambio de nombre de la máquina de Ubuntu*
![](/img/cambiohostnameubuntu.png)

### *Configurar tarjeta de red en Ubuntu*
![](/img/tarjetaredubuntu.png)

### *Comprobamos que la configuracion ha cambiado*
![](/img/comprobarubuntucliente.png)

### *Hacemos ping al servidor*
**NO FUNCIONA**

***
## **Configuración del cliente de Windows**

### *Cambiar nombre de la máquina*
![](/img/cambiarnombrewindows.png)

### *Configurar tarjeta de red en Windows*
![](/img/tarjetaredwindows.png)

### *Comprobamos que la configuracion ha cambiado*
![](/img/comprobacionwindows.png)

### *Hacemos ping al servidor y comprobamos que responde*
![](/img/pingwindows.png)

***
## **Configuración DHCP en Ubuntu Server**

### *Configuramos el servidor DHCP*
1. Añadimos la tarjeta de red al archivo 00-installer-config.yaml en la carpeta */etc/netplan* y ejecutamos el comando 
`sudo netplan apply`
![](/img/dhcpserver.png)

2. Instalamos el isc-shcp-server con el comando `sudo apt-get install isc-dhcp-server`

3. Añadimos el nombre de la tarjeta de red al archivo isc-dhcp-server en la carpeta */etc/default*

![](/img/iscdhcperver.png)

4. Establecemos el rango de ips en el archivo */etc/dhcp/dhcpd.conf*

![](/img/cambiarrangosserver.png)

5. Hacemos un restart del servicio dhcp con el comando `sudo service isc-dhcp-server restart` y posteriormente comprobamos que funcione con el comando `sudo service isc-dhcp-server status`

![](/img/comprobaciondhcpservice.png)
### **