+++
title = 'Tarjeta virtual'
date = 2024-08-15T14:26:00-06:00
draft = false
image = "/images/tarjeta_red.jpg"

+++


Uno de los primeros pasos en la configuración de una máquina virtual es la configuración de la tarjeta de red virtual. Dos de los detalles más importantes a considerar son la **subnet IP** y la **subnet mask**, que definen la red en la que se encuentra la máquina virtual.

- **Subnet IP**: Define una red específica en la que se encuentra la máquina virtual.
- **Subnet Mask**: Se utiliza para dividir la dirección IP en dos partes: la parte de la red y la parte del host.

### Red de la máquina virtual: 
![Red](/images/tarjeta.png)

### Ejemplo del default Gateway: 
![Gateway](/images/gateway.png)


En la figura anterior, el **Gateway IP** actúa como intermediario entre la red interna y la externa. Esto permite que la máquina virtual se comunique con otras redes, incluyendo la red de Internet.
