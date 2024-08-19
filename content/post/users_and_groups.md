+++
title = 'Creación de usuarios y grupos'
date = 2024-08-18T11:19:04-06:00
draft = false
image = "/SistemasOperativos/images/users.jpg"
+++
## Creación de Usuarios y Grupos

Para gestionar usuarios y grupos en el servidor, sigue estos pasos:

### Creación de Usuarios

1. **Accede a la Herramienta de Administración:**
   - Ve a **Tools** -> **Server Manager** y selecciona **Active Directory Users and Computers**.

2. **Crear un Nuevo Usuario:**
   - Navega alcontenedor donde deseas crear el usuario.
   - Haz clic derecho y selecciona **New** -> **User**.
   - Completa los campos requeridos:
     - **First Name:** Nombre del usuario.
     - **Last Name:** Apellido del usuario.
     - **User logon name:** Nombre para iniciar sesión.
     - **Password:** Contraseña del usuario.

   **Creación de Usuario**  
   ![Creación de usuario](/SistemasOperativos/images/UG.png)

### Creación de Grupos

1. **Accede a la Herramienta de Administración:**
   - Ve a **Tools** -> **Server Manager** y selecciona **Active Directory Users and Computers**.

2. **Crear un Nuevo Grupo:**
   - Navega a contenedor donde deseas crear el grupo.
   - Haz clic derecho y selecciona **New** -> **Group**.
   - Especifica el **Group Name** (Nombre del grupo) correspondiente al departamento.

### Asociación de Usuarios a un Grupo

1. **Seleccionar el Grupo:**
   - Haz clic derecho sobre el grupo al que deseas agregar usuarios y selecciona **Properties**.

2. **Agregar Miembros:**
   - Navega a la pestaña **Members** y haz clic en **Add**.
   - En la ventana de selección, ingresa los nombres de los usuarios deseados y haz clic en **Check Names** para verificar.
   - Haz clic en **OK** para completar la asociación.

   **Asociación de Usuario a un Grupo**  
   ![Asociación de usuario a un grupo](/SistemasOperativos/images/UG1.png)