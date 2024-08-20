+++
weight = 14
title = 'Web server'
date = 2024-08-18T11:20:51-06:00
draft = false
image = "/SistemasOperativos/images/web.jpg"
+++
# Configuración del Servidor Web (IIS)

Para la parte del **Web Server** utilizando Internet Information Services (IIS), se ha decidido desplegar este proyecto web. El Frontend fue desarrollado en **Angular** y desplegado en IIS, mientras que el API Restful se implementó en **Java Spring Boot**. Este Backend se desplegó mediante **TaskScheduler** en **Windows Server 2022**, ejecutando un archivo `.bat` que contiene el comando para correr el backend.


## Instalación del Rol de Web Server IIS

1. **Agregar el rol de Web Server IIS:**
   - Acceda al menú de **“Add Roles and Features”** para instalar el rol de Web Server IIS.
   **Instalación del rol IIS:**

   ![Instalación del rol IIS](/SistemasOperativos/images/ISS.png)

## Requisitos y Configuración

2. **Archivos necesarios para la ejecución:**

   - **Open JDK 21:** [Descargar](https://www.oracle.com/java/technologies/downloads/?er=221886#java21)
   - Agregar `JAVA_HOME` como variable de entorno del sistema además del directorio donde fue instalado el JDK-21.
   - Verificar la instalación en CMD mediante: `java -version` y `javac -version`.
   - Dentro de la variable de entorno `PATH`, agregar el directorio `bin` del JDK-21.
   - Agregar todas las variables de entorno necesarias (OpenAI API Key, DB URL, credenciales, etc.).
   - Contar con el archivo `.jar` de Java (creado utilizando el comando `gradlew clean build` y subido a Windows Server 2022 mediante FTP).
   - **Node.js:** [Descargar](https://nodejs.org/en/download/prebuilt-installer/current)
   - Verificar la instalación de Node con `node -v` y `npm -v`.
   - Instalar Angular CLI con el comando: `npm install -g @angular/cli`.
   - Verificar con el comando `ng version`.
   - Descargar **nvm-setup.exe** de [nvm-windows releases](https://github.com/coreybutler/nvm-windows/releases).
   - Verificar mediante el comando `nvm –version`.
   - Ejecutar `nvm install 20.12.2` para instalar Node.js versión 20.12.2.
   - Ejecutar `nvm use 20.12.2` para utilizar la versión 20.12.2 de Node.js.
   - Incluir el rol FTP dentro de **“Add Roles and Features”** de Windows Server 2022.
   - En **“Win + R”**, ingresar a `mf.msc`, agregar una nueva regla de entrada sobre el puerto 21 y configurar los rangos de puertos.
   - Dentro de IIS Manager, agregar un nuevo sitio FTP.
   - Si la conexión FTP no funciona, agregar un rango de puertos para el soporte de firewall FTP dentro de IIS con el siguiente comando en PowerShell:
     ```powershell
     Set-WebConfigurationProperty -Filter "/system.ftpServer/firewallSupport" -Name "dataChannelPortRange" -Value "49152-65535" -PSPath "IIS:\"
     ```
   - Reiniciar IIS con el comando: `iisreset`.
   - Descargar y ejecutar **URL Rewrite** para IIS: [Descargar](https://www.iis.net/downloads/microsoft/url-rewrite)
   - Descargar y ejecutar **Application Request Routing (AAR)**: [Descargar](https://www.iis.net/downloads/microsoft/application-request-routing)

   Esto permitirá redirigir el tráfico que cumpla con ciertos patrones RegEx (en este caso, API) hacia nuestro backend con Spring Boot, que estará corriendo como un servicio de Windows.

## Despliegue del Frontend en IIS

1. **Transferencia de archivos:**
   - Una vez construido el directorio `dist` con Angular CLI y transferido al Windows Server 2022 mediante Filezilla, copie los archivos del directorio `dist > browser` a `C:\inetpub\wwwroot`.
   
   **Carpeta wwwroot:**
   ![Carpeta wwwroot](/SistemasOperativos/images/wwwroot.png)

2. **Agregar aplicación en IIS Manager:**
   - Acceder a **Internet Information Services (IIS) Manager** y hacer clic derecho en **Default Web Site** > **Add Application**.
    **Agregar aplicación dentro del Default Web Site:**
   ![Agregar aplicación dentro del Default Web Site](/SistemasOperativos/images/addapp.png)

   - Agregar un alias, por ejemplo, `app`, y configurar el **Physical Path** a `C:\inetpub\wwwroot`.

   - En **Default Website > Default Document**, hacer que `index.html` esté de primero utilizando los controles de la barra lateral derecha (opciones de "up" y "down").
    **Sitio web por defecto:**
   ![Sitio web por defecto](/SistemasOperativos/images/defaultWeb.png)
    **Documento por defecto dentro del sitio por defecto:**
   ![Documento por defecto dentro del sitio por defecto](/SistemasOperativos/images/defaultDoc.png)

   - Reiniciar IIS utilizando el comando `iisreset` en CMD o PowerShell.

3. **Verificación:**
   - Al ingresar a `www.clienso.local`, debería desplegarse la aplicación Angular, tanto en Windows Server 2022 como en el cliente Windows 10.
    **Página de inicio de sesión de la aplicación Angular desde Windows Server 2022:**
   ![Página de inicio de sesión de la aplicación Angular desde Windows Server 2022](/SistemasOperativos/images/pagina_inicio_sesion_server.png)
    **Página de inicio de sesión de la aplicación Angular desde el cliente de Windows 10:**
   ![Página de inicio de sesión de la aplicación Angular desde el cliente de Windows 10](/SistemasOperativos/images/pagina_inicio_sesion_cliente.png)

4. **Redirección de URL:**
   - Dado que Angular es una “single page application”, la redirección por defecto hacia `/login` u otros puede generar problemas. Se recomienda usar una regla de **URL Rewrite**.

    **Inbound Rule configuración:**
   ![Inbound Rule configuración](/SistemasOperativos/images/inbound_rule_configuracion.png)

   - Hacer clic en **Apply** y reiniciar IIS con el comando `iisreset` ejecutado como administrador en CMD.

## Configuración del Backend

1. **Crear tarea en TaskScheduler:**
   - Crear un archivo `.bat` para ejecutar el comando del backend y almacenar los logs en un archivo llamado `app.log`.
    **Archivo Batch para correr el Backend:**
   ![Archivo Batch para correr el Backend](/SistemasOperativos/images/archivo_batch_backend.png)

   - En **Task Scheduler**, ir a la pestaña **Action** y crear una nueva tarea con las siguientes configuraciones:
    **Configuración general de la tarea:**
   ![Configuración general de la tarea](/SistemasOperativos/images/configuracion_general_tarea.png)
    **Configuración de triggers de la tarea:**
   ![Configuración de triggers de la tarea](/SistemasOperativos/images/configuracion_triggers_tarea.png)
    **Configuración de acciones de la tarea:**
   ![Configuración de acciones de la tarea](/SistemasOperativos/images/configuracion_acciones_tarea.png)

   - Por defecto, la tarea estará en estado **“Ready”**. Cambiar manualmente a **“Running”** para que inicie de inmediato, dado que el trigger es **“on start up”**.

   - Verificar que la tarea esté corriendo.
    **Tarea corriendo:**
   ![Tarea corriendo](/SistemasOperativos/images/tarea_corriendo.png)

2. **Validación del Backend:**
   - Opcional, pero recomendado: Descargar **Insomnia** y hacer una petición al API para validar que responda correctamente.
    **Petición log in al Backend mediante Insomnia y su respuesta:**
   ![Petición log in al Backend mediante Insomnia y su respuesta](/SistemasOperativos/images/peticion_insomnia.png)
