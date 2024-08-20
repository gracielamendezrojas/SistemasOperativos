+++
weight = 10
title = 'Políticas de grupo'
date = 2024-08-18T11:19:30-06:00
draft = false
image = "/SistemasOperativos/images/policies.jpg"
+++
# Implementación de Políticas de Grupo

Dado que la empresa no tiene experiencia en la creación de políticas de grupo, se solicitaron las siguientes políticas para su implementación:

1. **Cambiar el fondo de pantalla a uno corporativo** (archivo compartido en el servidor denominado `FondoEmpresarial.jpg`).
2. **Deshabilitar el acceso al Panel de Control** para usuarios que no pertenecen al departamento de TI.
3. **Definir una página inicial específica** para Internet Explorer.
4. **Deshabilitar la ejecución de ciertos ejecutables**: `notepad.exe` y `regedit.exe`.
5. **Mapear un recurso de red** usando DFS para uso personal, asignando la unidad `P:` a cada usuario de dominio y accediendo a la carpeta personal mediante una ruta DFS.
6. **Renombrar los usuarios locales**: cambiar el nombre del administrador local a `usrmda` y el nombre del usuario invitado local a `usrtmp` en las estaciones.
7. **Configurar la redirección de carpetas** para los usuarios del dominio a una carpeta de red.

A continuación se detalla cómo se configuraron estas políticas y sus resultados:

## 1. Cambiar Fondo de Pantalla

- **Configuración del Archivo de Fondo de Pantalla:**
  - Se creó una carpeta compartida en el servidor llamada **“Fondo de Pantalla Empresarial”**, accesible para todos los usuarios autenticados. Dentro de esta carpeta se encuentra el archivo `FondoEmpresarial.jpg`.

  **Archivo de Fondo de Pantalla Empresarial en la Carpeta:**  
  ![Archivo de Fondo de Pantalla Empresarial en carpeta](/SistemasOperativos/images/FPE.png)

- **Configuración de la Política de Grupo:**
  - Se creó una nueva política de grupo llamada **“Fondo de Pantalla”**. Se configuró para que utilice la dirección de la carpeta y el archivo `FondoEmpresarial.jpg` como fondo de pantalla para todos los usuarios.

  **Ubicación de la Configuración de la Política de Grupo:**  
  ![Ubicación de la Configuración de la Política de Grupo](/SistemasOperativos/images/WP.png)

  **Definición de Carpeta y Archivo del Fondo de Pantalla:**  
  ![Definición de Carpeta y Archivo del Fondo de Pantalla](/SistemasOperativos/images/WP2.png)

## 2. Deshabilitar Acceso al Panel de Control y Ejecutables

- **Deshabilitar el Acceso al Panel de Control:**
  - Se creó una política de grupo para deshabilitar el acceso al Panel de Control para usuarios no pertenecientes al grupo de TI. 

  **Activación de la Política de Grupo:**  
  ![Activación de Política de Grupo](/SistemasOperativos/images/APC.png)

  **Exclusión de Usuarios del Grupo de TI:**  
  ![Se Define como Excepción a los Usuarios del Grupo de TI](/SistemasOperativos/images/EXC_TI.png)

- **Deshabilitar Ejecutables:**
  - Para bloquear la ejecución de `notepad.exe` y `regedit.exe`, se configuró la política de grupo correspondiente.

  **Ubicación de la Configuración de la Política de Grupo:**  
  ![Ubicación de la Configuración de la Política de Grupo](/SistemasOperativos/images/GPME.png)

  **Especificación de los Programas Deshabilitados:**  
  ![Especificación de los Programas Deshabilitados](/SistemasOperativos/images/PG_DES.png)


  - **Definir Página de Inicio en Internet Explorer:**
  - Se estableció una página web específica para que se cargue al iniciar Internet Explorer.

  **Definición de Página Web por Defecto:**  
  ![Definición de Página Web Default al Iniciar Internet Explorer](/SistemasOperativos/images/Web_default.png)

## 3. Renombrar Usuarios Locales

- **Renombramiento del Usuario Administrador Local:**
  - El nombre del usuario administrador local se cambió a `usrmda`.

  **Renombramiento del Administrador Local:**  
  ![Renombramiento del Administrador](/SistemasOperativos/images/Admin_rename.png)

  **Confirmación de Renombramiento:**  
  ![Confirmación de Renombramiento del Administrador e Invitado](/SistemasOperativos/images/Rename.png)

## 4. Redirección de Carpetas

- **Configuración de la Redirección de Carpetas:**
  - Se configuró la política de grupo para redirigir las carpetas de los usuarios del dominio a una carpeta de red específica.

  **Definición de Ruta para Redirección de Carpetas:**  
  ![Definición de Ruta donde se Generarán las Carpetas](/SistemasOperativos/images/File_path.png)

  **Configuración de las Propiedades de los Documentos:**  
  ![Configuración de las Propiedades de los Documentos](/SistemasOperativos/images/Proper_config.png)

  **Confirmación de Redirección de Carpeta:**  
  ![Confirmación de Redirección de Carpeta](/SistemasOperativos/images/redirect.png)

## 5. Restricción de Archivos

- **Restricción de Copia de Archivos:**
  - Se implementó una política para prevenir la copia de archivos con extensiones `.MP3` y `.AVI` a las carpetas de la empresa.

  **Configuración de Restricción de Archivos:**  
  ![Configuración de Restricción de Archivos](/SistemasOperativos/images/RestriccionArchivos.png)
