+++
title = 'File Server Resource Manager (FSRM)'
date = 2024-08-18T11:20:21-06:00
draft = false
image = "/images/FSRM.jpg"
+++
## Funcionalidades de File Server Resource Manager

El **File Server Resource Manager** permite establecer límites de espacio en disco para carpetas o volúmenes, controlando el uso del almacenamiento. También tiene la capacidad de crear y aplicar reglas para organizar y gestionar los archivos basados en su contenido. Para instalar el File Server Resource Manager, se debe correr el siguiente comando:

```powershell
Install-WindowsFeature FS-Resource-Manager -IncludeManagementTools
```

Respecto a las cuotas de las diversas carpetas compartidas, se define el tamaño en la siguiente tabla.

### Definición del tamaño de las cuotas para las carpetas compartidas de los departamentos:

| Carpeta compartida | Tamaño (MB) |
|--------------------|-------------|
| Ventas             | 10          |
| Contabilidad       | 20          |
| RH                 | 30          |
| TI                 | 40          |
| Gerencia           | 50          |

Para crear cuotas, se debe navegar desde **Server Manager** -> **Tools** -> **File Server Resource Manager** -> **Quota Resource Manager** -> **Create Quota** y definir las características de la cuota, como la ruta de la carpeta de la cuota y su tamaño.

### **Creación de cuotas:**

![Creación de cuotas](/images/Quotas.png)

Por otro lado, para limitar la inclusión de archivos a ciertas carpetas, se puede crear una plantilla y aplicarla a diversos folders. Para ello, se debe navegar hasta el **File Screening Manager** (**Server Manager** -> **Tools** -> **File Server Resource Manager** -> **Quota Resource Manager** -> **File Screening Manager**) y hacer clic en **Create File Screening**. Para el template, se debe especificar el nombre y los archivos que se van a bloquear en el folder seleccionado.

### **Creación de template para bloquear archivos AVI y MP3:**

![Creación de template para bloquear archivos AVI y MP3](/images/Restriction.png)

