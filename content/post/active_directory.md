+++
weight = 6
title = 'Active directory and DNS'
date = 2024-08-18T11:17:53-06:00
draft = false
image = "/SistemasOperativos/images/AD.jpg"
+++

# Guía de Configuración: Active Directory Domain Services y DNS


**Active Directory Domain Services (AD DS)** y **DNS (Domain Name System)** son componentes clave en la gestión de redes. Ambos trabajan en conjunto para facilitar la organización y el acceso a los recursos de red.

- **Active Directory Domain Services** utiliza DNS para permitir que los clientes localicen y se comuniquen con los controladores de dominio (Iainfoulds, 2023).
- **DNS** simplifica las búsquedas al reemplazar las direcciones IP numéricas por nombres de dominio legibles.

## DNS (Domain Name System)

### Características Clave

- **Sistema de Nomenclatura:** Convierte nombres de dominio legibles para los humanos en direcciones IP comprensibles por las computadoras.
- **Estructura Jerárquica:** Organiza los nombres de dominio en una estructura jerárquica y distribuida.
- **Integración con DHCP:** Se puede integrar con el Protocolo de Configuración Dinámica de Host (DHCP) para una gestión más fluida de direcciones IP.
- **Redundancia:** Permite la configuración de múltiples servidores DNS y la propagación de registros en diferentes ubicaciones.

## Active Directory Domain Services (AD DS)

### Características Clave

- **Gestión de Recursos:** Facilita la gestión de recursos de red como archivos, usuarios, grupos y dispositivos.
- **Protocolo LDAP:** Utiliza el Protocolo Ligero de Acceso a Directorios (LDAP) para autenticación y gestión de datos.
- **Almacenamiento y Autorización:** Almacena datos en el directorio y autoriza a los usuarios para acceder a ellos.
- **Comunicación de Aplicaciones:** Ofrece un lenguaje que las aplicaciones necesitan para comunicarse con los servicios de directorio.
- **Autenticación y Autorización:** Verifica la identidad de usuarios y dispositivos, y determina los permisos y niveles de acceso.
- **Gestión Centralizada:** Administra cuentas de usuario, contraseñas y políticas de seguridad de forma centralizada.
- **Políticas de Grupo:** Implementa configuraciones y restricciones en múltiples dispositivos y usuarios simultáneamente.
- **Estructura Jerárquica:** Organiza los recursos en un árbol jerárquico de dominios, unidades organizativas (OU) y objetos.

## Configuración en Windows Server

1. **Instalación de Servicios:**
   - Abre **Server Manager**.
   - Selecciona **"Add Roles and Features"** y sigue el procedimiento para instalar **Active Directory Domain Services** y **DNS**.

    **Instalación de Active Directory y DNS:**
   ![Instalación de Active Directory y DNS](/SistemasOperativos/images/AD1.png)

    **Selección de características AD DS:**
   ![Selección de características AD DS](/SistemasOperativos/images/AD2.png)

    **Selección de características DNS:**
   ![Selección de características DNS](/SistemasOperativos/images/AD3.png)

2. **Promoción a Domain Controller:**
   - Una vez instalados AD DS y DNS, promueve el servidor a **Domain Controller** presionando el botón correspondiente.
    **Promoción del servidor a Domain Controller:**
   ![Promoción del servidor a Domain Controller](/SistemasOperativos/images/AD4.png)

    **Finalización del proceso de instalación:**
   ![Finalización del proceso de instalación](/SistemasOperativos/images/AD5.png)
    
    **Ingreso de credenciales como Administrador:**
   ![Ingreso de credenciales como Administrador](/SistemasOperativos/images/AD6.png)

   **Razones para promover el servidor a Domain Controller:**
   - **Autenticación Centralizada:** Permite iniciar sesión una sola vez y acceder a múltiples recursos.
   - **Autenticación de Usuarios:** Verifica a los usuarios cuando intentan conectarse a la red.
   - **Gestión de Políticas de Grupo:** Facilita la gestión de políticas de grupo.
   - **Almacenamiento de Datos:** Los Domain Controllers (DC) almacenan y mantienen la base de datos de Active Directory.

3. **Configuración de DNS:**
   - En el **DNS Manager**, configura dominios en la sección de **Forward Lookup Zones**.

    **DNS Forward Lookup Zones:**]
   ![DNS Forward Lookup Zones](/SistemasOperativos/images/AD7.png)

   **Forward Lookup Zones incluyen:**
   - **Base de Datos DNS:** Contiene registros que asocian nombres de dominio con direcciones IP.
   - **Tipos de Registros:**
     - **A (Address):** Dirección IPv4.
     - **AAAA (IPv6 Address):** Dirección IPv6.
     - **CNAME (Canonical Name):** Alias de un dominio.
     - **MX (Mail Exchange):** Servidores de correo.
     - **SRV (Service):** Controladores de dominio, servicios LDAP.
     - **TXT:** Información textual como verificaciones SPF.

   - Configura las **Reverse Lookup Zones**, que contienen registros PTR (Pointer) para asociar direcciones IP con nombres de dominio.

    **DNS Reverse Lookup Zones:**
   ![DNS Reverse Lookup Zones](/SistemasOperativos/images/AD8.png)

   **Funciones de las Reverse Lookup Zones:**
   - **Traducción de IPs a Nombres:** Principal función de búsqueda inversa.
   - **Verificación y Seguridad:** Verifica la identidad de clientes antes de permitir el acceso.
   - **Registro y Auditoría:** Utilizado para la auditoría y diagnóstico, por ejemplo, en servidores de correo.

4. **Pruebas de Conectividad:**
   - Ejecuta **nslookup** en el símbolo del sistema para verificar la conectividad con varios dominios.

    **Pruebas de conectividad:**
   ![Pruebas de conectividad](/SistemasOperativos/images/AD9.png)


