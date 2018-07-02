---

copyright:

  years:  2016, 2018

lastupdated: "2017-10-05"

---

# No se puede añadir una instancia secundaria de V1.7 a una instancia primaria de V1.5

## Problema
En una configuración Cloud Foundation de varios sitios, no puede añadir una instancia secundaria de V1.7 a una instancia primaria de V1.5 debido a una discrepancia entre las versiones del sistema operativo en el servidor Microsoft Active Directory (AD).

## Solución
Siga los pasos siguientes en la instancia primaria de V1.5 para añadir los permisos para que el usuario de automatización primario forme parte de los grupos **Administradores de empresas** y **Administradores de esquema**.

1. Inicie una sesión en el servidor de Windows AD con la contraseña de **Administrador**.
2. Abra **Administrador del servidor** y pulse **Herramientas -> Usuarios y equipos de Active Directory**.
4. En la ventana **Usuarios y equipos de Active Directory**, pulse la sección **Usuarios** bajo el dominio raíz.
5. Pulse con el botón derecho del ratón en el usuario de automatización para abrir la ventana **Propiedades**.
6. Pulse el separador **Miembro de**.
7. Pulse **Añadir** y especifique los grupos **Administradores de empresas** y **Administradores de esquema** como nombres de objetos en la lista.  

Después de completar estos pasos, puede añadir una instancia secundaria de V1.7 a una instancia primaria de V1.5.
