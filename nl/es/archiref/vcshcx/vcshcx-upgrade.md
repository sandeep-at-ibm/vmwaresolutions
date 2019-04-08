---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

subcollection: vmwaresolutions


---

# Actualización de componentes de HCX
{: #vcshcx-upgrade}

La actualización de HCX es un proceso sencillo que utiliza la interfaz de usuario web (IU) del cliente en la actualización de HCX Manager del lado del cliente y la interfaz de usuario web de la nube en la actualización de HCX Manager del lado de la nube. Debe actualizar ambos lados, ya que cualquier actualización de componente de flota provoca que ambos vuelvan a desplegar los componentes de flota con el nivel de código que ha instalado el gestor. Si el soporte de VMware solicita el ID de sistema, proporcione tanto el lado del cliente como el de la nube. Utilice SSH en HCX Manager (cliente o nube) y ejecute `cat /common/location` para localizar el ID del sistema.

## Enlaces relacionados
{: #vcshcx-upgrade-related}

* [Visión general de vCenter Server on {{site.data.keyword.cloud}} con el paquete híbrido (Hybridity)](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)   
