---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-13"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Visión general de Caveonix RiskForesight on IBM Cloud
{: #caveonix_considerations}

El servicio Caveonix RiskForesight on {{site.data.keyword.cloud}} permite gestionar el riesgo cibernético y de conformidad con supervisión proactiva y controles de defensa automatizados para protegerse frente a amenazas y para cumplir las normativas gubernamentales y del sector.

Este servicio solo está disponible para instancias de VMware vCenter Server on {{site.data.keyword.cloud_notm}} desplegadas en la versión V2.9 y posteriores.
{:note}

## Especificaciones técnicas para Caveonix RiskForesight on IBM Cloud
{: #caveonix_considerations-specs}

Los componentes siguientes se solicitan y se incluyen en el servicio Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}.

### Recursos de vCenter
{: #caveonix_considerations-tech-specs-vcenter}

* CPU: 8 vCPU
* RAM: 32 GB
* Disco: 80 GB

### Red
{: #caveonix_considerations-tech-specs-network}

Se solicita una subred privada dedicada con 64 direcciones IP.

### Licencias y tarifas
{: #caveonix_considerations-tech-specs-license-fee}

Se solicita una clave de licencia de Caveonix RiskForesight para cada instancia del servicio.

## Consideraciones al instalar Caveonix RiskForesight on IBM Cloud
{: #caveonix_considerations-install}

Antes de instalar el servicio Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}, asegúrese de que la CPU y la memoria del clúster predeterminado de la instancia de servicio sean suficientes para la máquina virtual de Caveonix RiskForesight.

## Consideraciones al eliminar Caveonix RiskForesight on IBM Cloud
{: #caveonix_considerations-remove}

Revise las siguientes consideraciones antes de eliminar el servicio Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}:
* La eliminación del servicio Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} no cancela la licencia de Caveonix RiskForesight. Debe suprimir la licencia de Caveonix RiskForesight de la tabla **Licencias de Caveonix RiskForesight** en la página **Recursos** de la consola de {{site.data.keyword.vmwaresolutions_short}}.
* Cuando se elimina el servicio, la automatización de {{site.data.keyword.vmwaresolutions_short}} suprime sólo la única máquina virtual "todo en uno" de Caveonix que se ha desplegado y la subred privada dedicada que se ha solicitado para ella. Por tanto,
   * Si ha escalado la máquina virtual de Caveonix en varias máquinas virtuales, esas máquinas virtuales adicionales no se eliminan. 
   * Si ha utilizado las direcciones IP de la subred privada dedicada en máquinas virtuales adicionales, se deben asignar nuevas direcciones IP a esas máquinas virtuales para que continúen funcionando. 
   * Si suprime la instancia A de vCenter Server con el servicio Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} instalado y ha utilizado las direcciones IP de la subred privada dedicada solicitada para el servicio en la instancia B de vCenter Server, la subred privada dedicada se cancela tras la supresión de la instancia A de vCenter Server.

## Enlaces relacionados
{: #caveonix_considerations-related}

* [Solicitud de Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_ordering)
* [Gestión de Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingcaveonix)
* [Cómo ponerse en contacto con el equipo de soporte de IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
