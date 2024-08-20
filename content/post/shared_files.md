+++
weight = 11
title = 'Carpetas compartidas'
date = 2024-08-18T11:20:02-06:00
draft = false
image = "/SistemasOperativos/images/shared.jpg"
+++
# Carpetas Compartidas

Las carpetas compartidas son directorios disponibles en una red, lo que permite el acceso a las carpetas desde diversos dispositivos. Es común que existan carpetas compartidas para el uso de diversos usuarios o departamentos. A continuación se muestra una tabla con las carpetas compartidas y el tipo de permisos asignados a cada departamento.

## Carpetas compartidas de los departamentos y especificación de los permisos

| Carpeta Compartida     | Permiso                                                        |
|------------------------|----------------------------------------------------------------|
| Ventas                 | El departamento de ventas tiene permiso de lectura y escritura.|
| Contabilidad           | El departamento de contabilidad tiene permiso de lectura y escritura.|
| RH                     | El departamento de recursos humanos tiene permiso de lectura y escritura.|
| TI                     | El departamento de tecnologías de información tiene permiso de lectura y escritura.|
| Gerencia               | El departamento de gerencia tiene permiso de lectura y escritura.|
| Pública                | Todos los departamentos tienen permiso de lectura y solamente TI tiene permiso de escritura.|

Previo a compartir las carpetas, se instaló el rol de servidor de archivos (File Server Role) en Windows Server, el cual es esencial para una gestión efectiva y avanzada de archivos en una red.


**Comando para instalar el servidor de archivos:**


```powershell
Install-WindowsFeature -Name FS-FileServer
```

En esta sección se muestran los pasos realizados para cumplir con los diversos requerimientos solicitados referentes a las carpetas compartidas.

### Carpetas Compartidas Creadas en el Disco D:

1. **Cambio del Tamaño de la Partición del Disco**: Para la práctica realizada, el tamaño del disco C consumía todo el espacio de la memoria del disco duro. Por lo tanto, fue necesario reducir el tamaño del disco con el comando:
    ```powershell
    Resize-Partition -DiskNumber 0 -PartitionNumber 3 -Size 29GB
    ```

2. **Creación del Disco D**: El comando utilizado para la creación del disco D fue el siguiente:
    ```powershell
    New-Partition –DiskNumber 0 -Size 20GB -DriveLetter D
    ```

3. **Formatear el Disco D**: Para el uso del disco D, primero debe ser formateado.

    **Formatear disco local:**

    ![Formatear disco local](/SistemasOperativos/images/formateo.png)

4. **Compartir la Carpeta y Selección de Permisos**:
   - Ruta para compartir la carpeta: Click derecho sobre la carpeta -> Properties -> Share -> Digitar el grupo -> Add.

    **Compartir carpetas:**

    ![Compartir carpetas](/SistemasOperativos/images/Share_G.png)

5. **Ajuste de Permisos de las Carpetas Compartidas**: Una vez que se haya seleccionado el grupo con el que se desea compartir en la sección de permisos, se puede elegir entre las opciones disponibles.

    **Ajuste de permisos en carpetas:**

    ![Ajuste de permisos en carpetas](/SistemasOperativos/images/Permission.png)

    **Carpeta compartida:**

    ![Carpeta compartida](/SistemasOperativos/images/Shared_F.png)
