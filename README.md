# Configuraci'on de IP estatica

<pre>[root@app network-scripts]# vi /etc/sysconfig/network-scripts/ifcfg-enp1s0
TYPE=&quot;Ethernet&quot;
BOOTPROTO=&quot;none&quot;# (puede ser dhcp o none si quieres asignar una dirección IP estática)
DEFROUTE=&quot;yes&quot;
PEERDNS=&quot;yes&quot;
PEERROUTES=&quot;yes&quot;
IPV4_FAILURE_FATAL=&quot;no&quot;
IPV6INIT=&quot;yes&quot;
IPV6_AUTOCONF=&quot;yes&quot;
IPV6_DEFROUTE=&quot;yes&quot;
IPV6_PEERDNS=&quot;yes&quot;
IPV6_PEERROUTES=&quot;yes&quot;
IPV6_FAILURE_FATAL=&quot;no&quot;
NAME=&quot;ifcfg-enp1s0&quot;
DEVICE=&quot;ifcfg-enp1s0&quot;
ONBOOT=&quot;yes&quot;
USERCTL=&quot;no&quot;
IPADDR=192.168.124.10 #(aquí debes colocar la dirección IP estática que deseas asignar si usas &quot;none&quot; en BOOTPROTO)
NETMASK=255.255.255.0 #(aquí debes colocar la máscara de red correspondiente a tu red si usas &quot;none&quot; en BOOTPROTO)
GATEWAY=192.168.1.1 #(aquí debes colocar la dirección IP de la puerta de enlace de tu red si usas &quot;none&quot; en BOOTPROTO)
DNS1=8.8.8.8 #(aquí debes colocar la dirección IP de tu servidor DNS primario)
DNS2=8.8.4.4 #(aquí debes colocar la dirección IP de tu servidor DNS secundario)
</pre>


# Para crear un snapshot en KVM, sigue estos pasos:

1. Abre el hipervisor KVM y accede a la máquina virtual (VM) que deseas tomar el snapshot.

2. Detén la VM utilizando el siguiente comando de KVM:

`virsh shutdown nombre_de_la_vm`

3. Una vez que la VM esté detenida, toma el snapshot utilizando el siguiente comando de KVM:

`virsh snapshot-create-as nombre_de_la_vm nombre_del_snapshot`

Donde:
- nombre_de_la_vm es el nombre de la VM que deseas tomar el snapshot.
- nombre_del_snapshot es el nombre que deseas asignar al snapshot.
4. Inicia la VM nuevamente utilizando el siguiente comando de KVM:


`virsh start nombre_de_la_vm`

O, si deseas utilizar la interfaz gráfica de usuario, puedes hacer clic derecho en la VM en la lista de VMs y seleccionar "Arrancar".

Con estos pasos, deberías poder crear un snapshot de una VM de KVM de manera sencilla. Es importante tener en cuenta que los comandos pueden variar ligeramente según la distribución de Linux que estés utilizando y la versión de KVM que tengas instalada.

Recuerda que los snapshots se utilizan para capturar el estado actual de una VM y permiten volver a ese estado en cualquier momento en el futuro. Es importante tener en cuenta que los snapshots pueden ocupar una cantidad significativa de espacio en disco y pueden afectar el rendimiento de la VM, por lo que es recomendable utilizarlos con moderación y borrarlos cuando ya no sean necesarios.


# Clonar una VM en KVM

Para clonar una VM en KVM utilizando el comando virsh, sigue estos pasos:

1. Abre el hipervisor KVM y accede a la VM que deseas clonar.

2. Detén la VM utilizando el siguiente comando de KVM:


`virsh shutdown nombre_de_la_vm`

3. Una vez que la VM esté detenida, clónala utilizando el siguiente comando de KVM:

`virt-clone --original nombre_de_la_vm --name nombre_de_la_nueva_vm --auto-clone`

Donde:

- nombre_de_la_vm es el nombre de la VM que deseas clonar.
- nombre_de_la_nueva_vm es el nombre que deseas asignar a la nueva VM.

4. Inicia la nueva VM utilizando el siguiente comando de KVM:

`virsh start nombre_de_la_nueva_vm`

O, si deseas utilizar la interfaz gráfica de usuario, puedes hacer clic derecho en la nueva VM en la lista de VMs y seleccionar "Arrancar".

Con estos pasos, deberías poder clonar una VM de KVM de manera sencilla utilizando el comando virsh. Es importante tener en cuenta que los comandos pueden variar ligeramente según la distribución de Linux que estés utilizando y la versión de KVM que tengas instalada. Además, ten en cuenta que la nueva VM será una copia exacta de la original, por lo que necesitarás cambiar su configuración y/o nombre si deseas utilizarla con una finalidad distinta a la original.
