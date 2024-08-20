+++
weight = 7
title = 'Dynamic Host Configuration Protocol (DHCP)'
date = 2024-08-18T11:18:17-06:00
draft = false
image = "/SistemasOperativos/images/DHCP.jpg"
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

   **Configuración DHCP paso a paso:**  
   ![Configuración DHCP paso 1](/SistemasOperativos/images/DHCP.png)

```powershell
# Instalar el rol de DHCP y las herramientas de administración
Install-WindowsFeature -Name DHCP -IncludeManagementTools 

# Variables
$ScopeID = "192.168.1.0"
$SubnetMask = "255.255.255.0"
$ScopeName = "ServidorDHCP"
$LeaseDuration = "8.00:00:00"  # 8 días

# Rango de IPs
$StartRange = "192.168.1.11"
$EndRange = "192.168.1.244"

# IPs excluidas
$ExclusionStart1 = "192.168.1.1"
$ExclusionEnd1 = "192.168.1.10"
$ExclusionStart2 = "192.168.1.245"
$ExclusionEnd2 = "192.168.1.255"

# Agregar el ámbito DHCP
Add-DhcpServerv4Scope -Name $ScopeName -StartRange $StartRange -EndRange $EndRange -SubnetMask $SubnetMask -LeaseDuration $LeaseDuration

# Agregar exclusiones
Add-DhcpServerv4ExclusionRange -ScopeId $ScopeID -StartRange $ExclusionStart1 -EndRange $ExclusionEnd1
Add-DhcpServerv4ExclusionRange -ScopeId $ScopeID -StartRange $ExclusionStart2 -EndRange $ExclusionEnd2
```

## Verificación de la Instalación

Una vez completada la instalación, ejecuta los comandos en PowerShell para verificar el estado del servidor DHCP. El resumen del sistema debe mostrar los grupos de seguridad y el estado de autorización del servidor DHCP como "done".

**Resumen del estado del DHCP:**  
![Resumen del estado del DHCP](/SistemasOperativos/images/DHCPfinal.png)


Para garantizar la asignación adecuada de direcciones IP a los dispositivos de red, se requiere que los clientes estén configurados para recibir una dirección IP dinámica mediante DHCP. Esta configuración permite que el servidor DHCP asigne automáticamente una dirección IP disponible a cada cliente en función de la configuración del ámbito establecido.

Es crucial que todos los dispositivos en la red estén configurados para obtener una dirección IP de forma dinámica para asegurar una gestión eficiente y automatizada de las direcciones IP y evitar conflictos de direcciones en la red.

