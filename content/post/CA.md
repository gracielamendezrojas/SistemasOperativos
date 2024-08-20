+++
weight = 15
title = 'Certificate Authority'
date = 2024-08-18T11:21:22-06:00
draft = false
image = "/SistemasOperativos/images/CA.jpg"
+++
# Configuración de Certificate Authority

Con el rol de IIS ya instalado y la aplicación Angular desplegada como aplicación dentro del sitio web por defecto en IIS, es crucial configurar el **Certificate Authority (CA)**. Esta configuración nos permitirá habilitar solicitudes HTTPS utilizando el puerto 443, ya que hasta el momento nuestra conexión es HTTP mediante el puerto 80.

## Instalación del Rol de Certificate Authority

1. **Instalar el rol de Active Directory Certificate Services:**
   - Acceda al apartado de **“Add Roles and Features”** y seleccione el rol de **Active Directory Certificate Services**.

   **Instalar el rol de Active Directory Certificate Services:**

   ![Instalar el rol de Active Directory Certificate Services](/SistemasOperativos/images/instalar_rol_ad_certificate_services.png)

2. **Seleccionar el rol de Certification Authority:**
   - En la lista de roles, elija **Certification Authority**.

   **Seleccionar el rol de Certificate Authority:**

   ![Seleccionar el rol de Certificate Authority](/SistemasOperativos/images/instalar_rol_certificate_authority.png)

   **Instalación de rol CA en proceso:**

   ![Instalación de rol CA en proceso](/SistemasOperativos/images/instalacion_rol_ca_proceso.png)

3. **Configurar el rol CA:**
   - Al finalizar la instalación, aparecerá un mensaje indicando que la configuración de este rol está pendiente. Haga clic en el hipervínculo proporcionado.

   **Mensaje de configuración para el rol de Certificados:**

   ![Mensaje de configuración para el rol de Certificados](/SistemasOperativos/images/configuracion_rol_certificados.png)

4. **Especificar credenciales:**
   - Introduzca las credenciales necesarias para configurar los servicios del rol AD CS.

   **Credenciales para configurar el AD CS:**

   ![Credenciales para configurar el AD CS](/SistemasOperativos/images/credenciales_ad_cs.png)

5. **Seleccionar el tipo de CA:**
   - Elija **Standalone CA**.

   **Selección del tipo de CA:**

   ![Selección del tipo de CA](/SistemasOperativos/images/seleccion_tipo_ca.png)

6. **Seleccionar el tipo de CA (Root o Subordinate):**
   - Dado que es la primera vez que se configura un CA y no se cuenta con un CA Root, seleccione la opción **Root CA**.

   **Selección de CA de tipo Root o de tipo Subordinate:**

   ![Selección de CA de tipo Root o de tipo Subordinate](/SistemasOperativos/images/seleccion_ca_root.png)

7. **Crear una nueva llave privada:**
   - Como no se dispone de una llave primaria, seleccione la opción para crear una nueva.

   **Selección de llave privada para generar los certificados:**

   ![Selección de llave privada para generar los certificados](/SistemasOperativos/images/seleccion_llave_privada.png)

8. **Elegir el algoritmo de encriptación:**
   - Seleccione el algoritmo **SHA256**.

   **Creación de nueva llave privada para CA:**

   ![Creación de nueva llave privada para CA](/SistemasOperativos/images/creacion_llave_privada.png)

9. **Asignar un nombre al CA:**
   - Asigne un nombre al CA o mantenga el nombre por defecto sugerido por el asistente de configuración.

   **Selección de nombres para CA:**

   ![Selección de nombres para CA](/SistemasOperativos/images/nombres_ca.png)

10. **Configurar el periodo de validez del CA:**
    - Seleccione el periodo de validez por defecto, que es de 5 años.

    **Periodo de validez del CA:**

    ![Periodo de validez del CA](/SistemasOperativos/images/periodo_validez_ca.png)

11. **Seleccionar la ubicación de la base de datos:**
    - El CA necesita una base de datos para almacenar su información y logs. Puede aceptar la ubicación por defecto o elegir una distinta.

    **Selección de directorio donde residirá la base de datos de CA:**

    ![Selección de directorio donde residirá la base de datos de CA](/SistemasOperativos/images/directorio_base_datos_ca.png)

12. **Finalizar la configuración:**
    - Si todos los pasos se completaron correctamente, el asistente mostrará un mensaje de éxito indicando que el CA fue creado de manera correcta.

    **Creación exitosa del CA:**

    ![Creación exitosa del CA](/SistemasOperativos/images/creacion_exitosa_ca.png)

## Configuración del Certificado en IIS

1. **Agregar el certificado al sitio en IIS:**
   - Acceda a **Internet Information Services (IIS) Manager** y haga clic en el servidor desde el menú lateral de **“Connections”**.

   **Home del sitio por defecto del IIS:**

   ![Home del sitio por defecto del IIS](/SistemasOperativos/images/home_iis.png)

2. **Seleccionar Server Certificates:**
   - Haga doble clic en **Server Certificates**.

   **Selección de los certificados del sitio:**

   ![Selección de los certificados del sitio](/SistemasOperativos/images/seleccion_certificados.png)

3. **Importar el certificado root:**
   - Importe el certificado root generado durante la instalación del CA.

   **Importación del certificado root:**

   ![Importación del certificado root](/SistemasOperativos/images/importacion_certificado_root.png)

   - Es probable que aparezca una alerta de Windows indicando que el CA representa nuestro dominio (Clienso). Acepte la alerta para continuar.

   **Alerta del CA**

   ![Alerta del CA](/SistemasOperativos/images/alerta_ca.png)

4. **Crear un certificado auto-firmado:**
   - Haga clic en **“Create Self Signed Certificate…”**.

   **Acciones de los certificados dentro del servidor:**

   ![Acciones de los certificados dentro del servidor](/SistemasOperativos/images/acciones_certificados.png)

   - Asigne un nombre al nuevo certificado. En este caso, utilice el nombre **“voiage”**.

   **Creación de nuevo certificado auto-firmado:**

   ![Creación de nuevo certificado auto-firmado](/SistemasOperativos/images/creacion_certificado_autofirmado.png)

5. **Validar la creación del certificado:**
   - Verifique que el certificado se haya creado con éxito.

   **Certificado creado con éxito:**

   ![Certificado creado con éxito](/SistemasOperativos/images/certificado_creado_exito.png)

6. **Configurar el binding HTTPS:**
   - Agregue el binding HTTPS en el puerto 443, y en el campo **hostname**, ingrese **“clienso.local”**. Seleccione el certificado creado, **“voiage”**.

   **Binding HTTPS sobre el puerto 443:**

   ![Binding HTTPS sobre el puerto 443](/SistemasOperativos/images/binding_https.png)

   - Puede validar el funcionamiento accediendo a `https://clienso.local`. Es posible que vea una alerta en el navegador debido a que el certificado es auto-firmado.

   **Alerta del navegador sobre conexión no segura:**

   ![Alerta del navegador sobre conexión no segura](/SistemasOperativos/images/alerta_navegador.png)

   **Sitio web accedido mediante el protocolo HTTPS.**

   ![Sitio web accedido mediante el protocolo HTTPS](/SistemasOperativos/images/sitio_https.png)
