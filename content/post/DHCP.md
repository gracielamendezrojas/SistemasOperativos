+++
title = 'Dynamic Host Configuration Protocol (DHCP)'
date = 2024-08-18T11:18:17-06:00
draft = false
image = "/images/DHCP.jpg"
+++
# Instructivo para la Configuración de DHCP

El **Dynamic Host Configuration Protocol (DHCP)** es un protocolo de red que automatiza la asignación de direcciones IP y otros parámetros de configuración a dispositivos en una red. Esto facilita la administración de la red y reduce errores asociados con la configuración manual.

### Beneficios del DHCP

El uso de DHCP ofrece varios beneficios clave:

- **Reducción de Errores de Configuración:** Minimiza errores causados por la configuración manual, como errores tipográficos o conflictos de direcciones IP.
- **Configuración Centralizada y Automatizada:** Permite definir y gestionar configuraciones TCP/IP desde una ubicación central.
- **Asignación de Intervalo Completo de Direcciones:** Facilita la asignación de un rango completo de direcciones IP a los dispositivos.
- **Control Eficaz de Cambios de IP:** Administra de manera eficiente las actualizaciones frecuentes de direcciones IP para los clientes.
- **Reutilización de Direcciones IP:** Optimiza el uso de direcciones IP al reutilizar aquellas de dispositivos que salen de la red.

## Procedimiento de Configuración

A continuación, se detalla el procedimiento para configurar DHCP. Las siguientes figuras ilustran cada paso del proceso:

1. **Paso 1: Configuración Inicial**  
   **Configuración DHCP paso a paso:**  
   ![Configuración DHCP paso 1](/images/DHCP.png)


## Verificación de la Instalación

Una vez completada la instalación, ejecuta los comandos en PowerShell para verificar el estado del servidor DHCP. El resumen del sistema debe mostrar los grupos de seguridad y el estado de autorización del servidor DHCP como "done".

**Resumen del estado del DHCP:**  
![Resumen del estado del DHCP](/images/DHCPfinal.png)

