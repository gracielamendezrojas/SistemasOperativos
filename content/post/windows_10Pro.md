+++
title = 'Windows 10 Pro'
date = 2024-08-18T10:35:29-06:00
draft = false
image = "/SistemasOperativos/images/windows10.png"

+++
# Instalación de Windows 10 Pro

La instalación del cliente Windows se realiza de manera similar, utilizando VMware WorkStation como virtualizador. En este caso, se ha seleccionado Windows 10 Pro para permitir la edición de conexiones de dominio, función disponible en esta versión.

**Interfaz de Windows 10 Pro:**
![Image](/SistemasOperativos/imagesUI_W_pro.png)

Al igual que con el servidor, es necesario desactivar el firewall durante la configuración:

**Firewall desactivado:**
![Image](/SistemasOperativos/images/FW2.png)
Se asignan direcciones IP temporalmente, como se muestra en la siguiente figura:

**Configuración de IP temporal:**
![Image](/SistemasOperativos/images/IP2.png)
Para verificar la conexión a Internet, se utiliza el símbolo del sistema con el comando `ping` y la dirección IP previamente establecida. La imagen muestra la prueba de conexión para Windows Server:

**Prueba de conexión:**
![Image](/SistemasOperativos/images/ping.png)