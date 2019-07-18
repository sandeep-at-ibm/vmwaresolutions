---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-18"

keywords: IAM user, user role, user permission

subcollection: vmware-solutions


---

# Gestión de acceso de usuario con IAM
{: #iam}

El acceso a las instancias de servicio de {{site.data.keyword.vmwaresolutions_full}} para los usuarios de la cuenta está controlado por {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM). Cada usuario que accede a los servicios de {{site.data.keyword.vmwaresolutions_short}} en su cuenta debe tener asignada una política de acceso con un rol de usuario IAM definido.

La política de acceso determina las acciones que el usuario puede realizar dentro del contexto del servicio o la instancia que seleccione. Las acciones permitidas se personalizan y se definen mediante el servicio de {{site.data.keyword.cloud_notm}} como operaciones que se permiten para que se realicen en el servicio. Las acciones se correlacionarán entonces a los roles de usuario de IAM.

Las políticas permiten otorgar el acceso en distintos niveles. Algunas de las opciones incluyen los siguientes accesos:

* Acceso a todas las instancias de servicio en su cuenta
* Acceso a una instancia de servicio individual en su cuenta
* Acceso a un recurso específico dentro de una instancia
* Acceso a todos los servicios habilitados para IAM en su cuenta

Después de definir el ámbito de la política de acceso, debe asignar un rol.

Revise la información siguiente, en la que se describen las acciones que permite cada rol en el servicio de {{site.data.keyword.vmwaresolutions_short}}.

## Roles y permisos de gestión de plataformas
{: #iam-roles}

Los roles de gestión de plataformas permiten a los usuarios realizar tareas en los recursos de servicio a nivel de plataforma. Por ejemplo, asigne acceso de usuario al servicio, cree o suprima los ID de servicio, cree instancias y vincule instancias a las aplicaciones.

La tabla siguiente proporciona información sobre las acciones que se correlacionan en los roles de gestión de plataforma.

| Rol de gestión de plataforma | Acciones | Acciones de ejemplo |
|:----------------- |:----------------- |:----------------- |
| Visor | Acciones de solo lectura | Ver el resumen de instancias<br>Ver los detalles de una instancia |
| Editor | Actualizar una instancia específica | Añadir o eliminar servidores ESXi<br>Añadir o eliminar clústeres<br>Añadir o eliminar servicios<br>Actualizar una instancia a una versión superior |
| Operador | Acciones de solo lectura | Listar instancias<br>Ver los detalles de una instancia |
| Administrador | Acceso de gestión completa | Crear nuevas instancias<br>Suprimir instancias<br>Otorgar acceso de plataforma a otros usuarios|
{: caption="Tabla 1. Roles de gestión de plataforma y acciones permitidas" caption-side="top"}

Para {{site.data.keyword.vmwaresolutions_short}}, existen las acciones siguientes:

| Acción | Operación en servicio | Rol |
|:------ |:-------------------- |:---- |
| vmware-solutions.instances.create | Crear nuevas instancias | Administrador |
| vmware-solutions.instances.delete | Suprimir instancias | Administrador |
| vmware-solutions.instances.view | Listar instancias<br>Ver el detalle de una instancia | Visor, Operador, Editor y Administrador |
| vmware-solutions.instances.update | Añadir o eliminar servidores ESXi<br>Añadir o eliminar clústeres<br>Añadir o eliminar servicios<br>Actualizar una instancia a una versión superior | Editor y Administrador |
| vmware-solutions.account.update | Actualizar valores de cuenta | Administrador |
{: caption="Tabla 2. Descripciones de acciones y roles necesarios" caption-side="top"}

## Gestión del acceso para usuarios
{: #iam-users}

Puede añadir nuevos usuarios a la cuenta {{site.data.keyword.cloud_notm}} para que estos usuarios puedan compartir los servicios y los recursos que se han suministrado para la cuenta. Para obtener más información, consulte [Invitar a los usuarios a acceder a servicios y recursos](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-iamuserinvite).

También puede gestionar el acceso de los usuarios existentes, incluida la modificación del acceso existente, la asignación de acceso nuevo y la revisión del acceso asignado. Para gestionar el acceso de los usuarios, debe ser el propietario de la cuenta o debe tener el rol de gestión de la plataforma **Administrador**. Para obtener más información, consulte [Gestión del acceso a recursos](/docs/iam?topic=iam-iammanidaccser).

## Migración de instancias existentes a cuentas de IBM Cloud
{: #iam-migrate}

Debido a la integración de {{site.data.keyword.vmwaresolutions_short}} con IAM, las instancias que se despliegan en V2.5 y releases posteriores en la cuenta de {{site.data.keyword.cloud_notm}} se añaden automáticamente a la cuenta y se gestionan mediante IAM.

Para las instancias existentes que se han desplegado en V2.4 y releases anteriores, puede migrarlas a cuentas de {{site.data.keyword.cloud_notm}} especificadas para la gestión habilitada para IAM. Para obtener más información, consulte los temas siguientes:
* [Migración de instancias anteriores a V2.5 vCenter Server a cuentas de IBM Cloud](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addinstancetousraccount)
* [Migración de vCenter Server anterior a V2.5 con las instancias del paquete híbrido (Hybridity) en cuentas de IBM Cloud](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addinstancetousraccount)
* [Migración de instancias anteriores a V2.5 NetApp ONTAP Select a cuentas de IBM Cloud](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_addinstancetousraccount)

## Enlaces relacionados
{: #iam-related}

* [Gestión de identidad y acceso](/docs/iam?topic=iam-getstarted)
* [Invitación a usuarios](/docs/iam?topic=iam-iamuserinv#iamuserinv)
* [¿Qué es IAM?](/docs/iam?topic=iam-iamoverview)
