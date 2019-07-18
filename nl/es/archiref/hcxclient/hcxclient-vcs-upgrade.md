---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-17"

subcollection: vmware-solutions


---

# Actualización de componentes de HCX
{: #hcxclient-vcs-upgrade}

La actualización de HCX es un proceso sencillo que utiliza la interfaz de usuario web (IU) del cliente en la actualización de HCX Manager del lado del cliente y la interfaz de usuario web de la nube en la actualización de HCX Manager del lado de la nube.

Debe actualizar ambos lados, ya que cualquier actualización de componente de flota provoca que ambos vuelvan a desplegar los componentes de flota con el nivel de código que se instala en HCX Manager.

Si el soporte de VMware solicita el ID de sistema, proporcione tanto el lado del cliente como el de la nube. Utilice SSH en el gestor HCX (cliente o en la nube) y ejecute `cat /common/location` para localizar el ID del sistema.

## Enlaces relacionados
{: #hcxclient-vcs-upgrade-related}

* [Glosario de componentes y términos de HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-components)
* [Preparación del entorno de instalación](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-planning-prep-install)
* [Despliegue del cliente de HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-client-deployment)
* [Malla de servicio en instalaciones locales de HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-mesh-deployment)
* [Migraciones de VMware Hybrid Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-migrations)
* [Supervisión de parámetros y componentes](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-monitoring)
* [Resolución de problemas de HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting)
