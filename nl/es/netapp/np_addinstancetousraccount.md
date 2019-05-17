---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-18"

subcollection: vmware-solutions


---

# Migración de instancias anteriores a V2.5 NetApp ONTAP Select a cuentas de IBM Cloud
{: #np_addinstancetousraccount}

Las instancias de NetApp ONTAP Select desplegadas en V2.5 y releases posteriores en la cuenta de {{site.data.keyword.cloud}} se añaden automáticamente a la cuenta y se gestionan mediante {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM).

Para las instancias que se han desplegado en V2.4 y releases anteriores, puede migrarlas a cuentas de {{site.data.keyword.cloud_notm}} especificadas para la gestión de usuarios habilitada para IAM.

## Antes de empezar
{: #np_addinstancetousraccount-prereq}

Asegúrese de que la cuenta de {{site.data.keyword.cloud_notm}} a la que desea migrar la instancia no sea una cuenta de IaaS-only. Una cuenta de IaaS-only es una cuenta de {{site.data.keyword.cloud_notm}} infraestructura (IBM Cloud) que no está enlazada a una cuenta de {{site.data.keyword.cloud_notm}}.

Para obtener más información sobre cómo enlazar su cuenta de Iaas-only con su cuenta de PaaS, consulte [Siga estos pasos para enlazar sus cuentas de IaaS y PaaS](https://www.ibm.com/blogs/bluemix/2018/03/follow-steps-link-iaas-paas-accounts/).

## Procedimiento para migrar instancias
{: #np_addinstancetousraccount-procedure}

1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Recursos** en el panel de navegación izquierdo.
2. En el banner de la consola, pulse el icono de cuenta de usuario y, a continuación, pulse el campo **Cuenta** para seleccionar la cuenta de usuario a la que desea migrar la instancia.
3. En la tabla **Instancias de NetApp ONTAP Select**, busque la instancia anterior a V2.5.
4. En la columna **Acciones**, pulse el icono de menú de desbordamiento y, a continuación, pulse **Migrar instancia a la cuenta**.
5. En la ventana **Migrar instancia a la cuenta**, confirme la cuenta a la que va a migrar la instancia y, a continuación, pulse **Migrar**.

## Resultados
{: #np_addinstancetousraccount-results}

1. Se obtiene una notificación de consola en la que se acepta la solicitud para migrar la instancia a la cuenta {{site.data.keyword.cloud_notm}} especificada.
2. Cuando se completa la migración de la instancia, la instancia se visualiza en la página **Recursos** de la cuenta en la que se ha migrado. La instancia migrada ya no se visualiza en la cuenta original desde la que se ha migrado.

## Enlaces relacionados
{: #np_addinstancetousraccount-related}

* [Gestión de acceso de usuario con IAM](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-iam#iam)
* [Invitación de usuarios para acceder a servicios y recursos](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-iamuserinvite)
* [Qué es IBM Cloud IAM](/docs/iam?topic=iam-iamoverview)
