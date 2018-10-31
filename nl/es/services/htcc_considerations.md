---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-26"

---

# Visión general de HyTrust CloudControl on IBM Cloud

El servicio HyTrust CloudControl on {{site.data.keyword.cloud}} aplica y controla el cumplimiento de las normas de seguridad e incluye el control de acceso basado en roles (RBAC), aprobación y auditoría. Cuando el servicio se combina con HyTrust DataControl, el servicio garantiza que las máquinas virtuales y los datos de carga de trabajo no dejen una región, clúster o servidor ESXi particular dentro del {{site.data.keyword.CloudDataCent_notm}}.

**Disponibilidad:** Este servicio solo está disponible para las instancias que se ejecutan en vSphere 6.5 y que se han desplegado en, o que se han actualizado a, V2.3 o releases posteriores.

## Especificaciones técnicas para HyTrust CloudControl on IBM Cloud

Los siguientes componentes se solicitan y se incluyen en el servicio HyTrust CloudControl on {{site.data.keyword.cloud_notm}}:

### Dispositivo HyTrust CloudControl

* CPU: 4 vCPU
* RAM: 16 GB
* Disco: 70 GB VMDK residente en vSAN en un clúster convergente
* Red: ubicada en una red portátil privada respaldada por VLAN para la gestión

### Alta disponibilidad

Se despliegan dos dispositivos CloudControl en una configuración activa-pasiva.

### Licencias y tarifas

Licencia por host: se solicita una licencia de HyTrust CloudControl por cada host del entorno.

## Consideraciones al eliminar HyTrust CloudControl on IBM Cloud

Antes de eliminar el servicio HyTrust CloudControl on {{site.data.keyword.cloud_notm}}, asegúrese de inhabilitar **Blindaje de la contraseña raíz**, si está configurado, y de suprimir todos los hosts protegidos de HyTrust CloudControl.

### Enlaces relacionados

* [Solicitud de HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](htcc_ordering.html)
* [Gestión de HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](managinghtcc.html)
* [Cómo ponerse en contacto con el equipo de soporte de IBM](../vmonic/trbl_support.html)
* [Preguntas frecuentes](../vmonic/faq.html)
* [Sitio web de HyTrust](https://www.hytrust.com/)
