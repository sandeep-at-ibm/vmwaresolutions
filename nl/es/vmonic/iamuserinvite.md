---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-01"

subcollection: vmware-solutions


---

# Invitación de usuarios para acceder a servicios y recursos
{: #iamuserinvite}

{{site.data.keyword.vmwaresolutions_full}} se integra con {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM) para la colaboración entre varios usuarios. Después de registrarse para una cuenta de {{site.data.keyword.cloud_notm}} e iniciar sesión en la consola de {{site.data.keyword.vmwaresolutions_short}}, puede añadir usuarios a la cuenta de {{site.data.keyword.cloud_notm}}. Estos usuarios añadidos pueden compartir los servicios y recursos que se han suministrado para la cuenta.

## Antes de empezar
{: #iamuserinvite-reqs}

* Asegúrese de que es el propietario de la cuenta o de que el rol de gestión de plataforma para el servicio **Soluciones de VMware** sea **Administrador**.
* Asegúrese de que ha revisado los roles de usuario y los permisos en [Gestión del acceso de usuario con Identity and Access Management](/docs/services/vmwaresolutions?topic=vmware-solutions-iam#iam).

## Procedimiento para invitar a usuarios a acceder a servicios y recursos
{: #iamuserinvite-procedure}

1. En el lado izquierdo de la cabecera, pulse **Gestionar > Seguridad > Identidad y acceso**.
2. En la página **Usuarios**, pulse **Invitar usuarios**.
3. En la página **Invitar usuarios**, en la sección **Usuarios**, especifique las direcciones de correo electrónico de los usuarios que desea invitar en el campo **Dirección de correo electrónico**.
4. En la sección **Acceso**, expanda **Servicios** y, a continuación, complete las tareas siguientes:
   1. Seleccione **Recurso** en la lista **Asignar acceso a**.
   2. Seleccione **VMware Solutions** en la lista **Servicios**.
   3. Seleccione el rol de acceso de la plataforma que desea asignar a los usuarios. Puede ser **Administrador**, **Editor**, **Operador** o **Visor**.
5. Pulse **Invitar a usuarios**.

## Resultados
{: #iamuserinvite-results}

Después de que los usuarios añadidos acepten la invitación, pueden iniciar sesión en la consola {{site.data.keyword.vmwaresolutions_short}} y conmutar a la cuenta. Para ello, en sus valores de perfil, los usuarios pulsan su icono de cuenta de usuario desde el banner de la consola de {{site.data.keyword.vmwaresolutions_short}}. A continuación, los usuarios añadidos pueden colaborar y compartir los servicios y los recursos disponibles en la cuenta especificada.

## Enlaces relacionados
{: #iamuserinvite-related}

* [Invitación de usuarios y asignación de acceso](/docs/iam?topic=iam-iamuserinv)
* [Gestión de identidad y acceso](/docs/iam?topic=iam-getstarted)
* [Invitación a usuarios](/docs/iam?topic=iam-iamuserinv#iamuserinv)
* [¿Qué es IAM?](/docs/iam?topic=iam-iamoverview)
* [Migración de instancias anteriores a V2.5 vCenter Server a cuentas de IBM Cloud](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addinstancetousraccount)
* [Migración de vCenter Server anterior a V2.5 con las instancias del paquete híbrido (Hybridity) en cuentas de IBM Cloud](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addinstancetousraccount)
* [Migración de instancias anteriores a V2.5 NetApp ONTAP Select a cuentas de IBM Cloud](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_addinstancetousraccount)
