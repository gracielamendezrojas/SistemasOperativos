+++
title = 'Distributed File System (DFS)'
date = 2024-08-18T11:20:33-06:00
draft = false
image = "/SistemasOperativos/images/DFS.jpg"
+++
# Implementación de DFS (Distributed File System)

DFS es una tecnología que permite agrupar varios recursos compartidos en diferentes servidores en un solo sistema de archivos lógico. Esto permite que diferentes usuarios accedan a archivos y carpetas desde múltiples servidores de manera sencilla y eficiente. Aquí se presentan dos razones clave por las que una empresa podría utilizar DFS:

1. **Almacenar datos de forma permanente en soportes de almacenamiento secundario.**
2. **Compartir información de manera fácil, eficiente y segura.**

## Componentes Críticos del DFS

- **Transparencia de la Ubicación:** Permite que los usuarios vean un solo espacio de almacenamiento para los archivos de datos, independientemente del computador desde el que se conecten.
- **Redundancia:** Extiende copias de un archivo a través de los nodos de un clúster, asegurando la disponibilidad y protección de los datos.

## Pasos para el Mapeo de Carpetas Personales con DFS

A continuación, se describen los pasos realizados para mapear una carpeta personal para cada usuario utilizando DFS. Las siguientes figuras ilustran cada paso:

1. **Creación de “Namespace” para el Servidor:**

   ![Creación de “Namespace” para el servidor](/SistemasOperativos/images/NS.png)

2. **Creación del Nombre de la Carpeta para DFS:**

   ![Creación de nombre de la carpeta para el DFS](/SistemasOperativos/images/DFS2.png)

3. **Definición de la Ruta de la Carpeta:**

   ![Definición de ruta de la carpeta](/SistemasOperativos/images/F_path.png)

4. **Creación de Carpetas para DFS y Definición de Rutas:**

   ![Creación de carpetas para DFS y definición de rutas](/SistemasOperativos/images/F_create.png)

5. **Creación de Carpetas para DFS y Definición de Rutas para Cada Departamento:**

   ![Creación de carpetas para DFS y definición de rutas para cada departamento](/SistemasOperativos/images/F_DEP.png)

6. **Creación de Acceso Directo a las Carpetas con la Ruta del DFS:**

   ![Creación de acceso directo a las carpetas con la ruta del DFS](/SistemasOperativos/images/Shortcut.png)

7. **Creación de Acceso Directo a las Carpetas con la Ruta del DFS para Cada Departamento:**

   ![Creación de acceso directo a las carpetas con la ruta del DFS para cada departamento](/SistemasOperativos/images/Shortcut2.png)

8. **Confirmación de la Ruta de la Carpeta Compartida con DFS:**

   ![Confirmación de ruta de la carpeta compartida con DFS](/SistemasOperativos/images/SF_Confirm.png)

9. **Creación de acceso directo a las carpetas con la ruta del DFS:**
   ![Creación de acceso directo a las carpetas con la ruta del DFS](/SistemasOperativos/images/Direct_Access.png)

10. **Comprobación de la Carpeta en el Cliente:**

   ![Comprobación de carpeta en el cliente](/SistemasOperativos/images/SF_Access.png)

Estos pasos aseguran que cada usuario pueda acceder a sus carpetas personales de manera eficiente y segura a través del sistema DFS. 
