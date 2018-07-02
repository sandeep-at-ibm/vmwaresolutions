---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-07"

---

# Visión general de HyTrust CloudControl on IBM Cloud

El servicio HyTrust CloudControl on {{site.data.keyword.cloud}} aplica y controla el cumplimiento de las normas de seguridad y proporciona funciones detalladas de control de acceso basado en roles (RBAC), aprobación y auditoría. Cuando se combina con HyTrust DataControl, el servicio puede asegurarse de que los datos de las cargas de trabajo y las máquinas virtuales no abandonen una región, un clúster o un servidor ESXi determinados en el {{site.data.keyword.CloudDataCent_notm}}.

**Disponibilidad:** este servicio solo está disponible para las instancias que se ejecutan en vSphere 6.5 y que se han desplegado en la V2.3 y posteriores releases o que se han actualizado a estos.

## Componentes de HyTrust CloudControl on IBM Cloud

Se despliega un par de alta disponibilidad (HA) de dispositivos de HyTrust CloudControl (HTCC) en el clúster predeterminado en modalidad pasiva activa.

Cada par de dispositivos HTCC se despliega en la misma subred portátil privada que está especificada para las máquinas virtuales (VM) de gestión, como NSX Manager, vCenter Server Appliances y Platform Services Controller. El par de dispositivos actúa como un proxy para los hosts de vSphere, el dispositivo de vCenter Server y el gestor de NSX de una instancia. Por lo tanto, los usuarios acceden a los hosts de vSphere, al vCenter Server Appliance y al NSX Manager mediante direcciones IP publicadas (PIP) que asigna el administrador en lugar de la dirección IP real (RIP) asignada por IBM Cloud.

Los dispositivos HTCC se integran con el Microsoft Active Directory para forzar el control de acceso basado en roles.

## Consideraciones al eliminar HyTrust CloudControl on IBM Cloud

Antes de eliminar el servicio HyTrust CloudControl on {{site.data.keyword.cloud_notm}}, asegúrese de inhabilitar **Blindaje de la contraseña raíz**, si está configurado, y de suprimir todos los hosts protegidos de CloudControl.

## Enlaces relacionados

* [Solicitud de HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](htcc_ordering.html)
* [Gestión de HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](managinghtcc.html)
* [Cómo ponerse en contacto con el equipo de soporte de IBM](../vmonic/trbl_support.html)
* [Preguntas frecuentes](../vmonic/faq.html)
* [Sitio web de HyTrust](https://www.hytrust.com/)
