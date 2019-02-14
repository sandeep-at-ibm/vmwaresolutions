---

copyright:

  years:  2016, 2019

lastupdated: "2018-11-29"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Visión general de VMware HCX on IBM Cloud

El servicio HCX on {{site.data.keyword.cloud}} permite ampliar fácilmente las redes de centros de datos locales en {{site.data.keyword.cloud_notm}}, lo que permite migrar las máquinas virtuales (VM) de {{site.data.keyword.cloud_notm}} sin ninguna conversión ni cambio.

Este servicio solo está disponible para instancias de VMware vCenter Server on {{site.data.keyword.cloud_notm}} con el paquete híbrido (Hybridity) desplegadas en la V2.3 y posteriores.
{:note}

Puede actualizar la instancia existente de vCenter Server a una instancia de vCenter Server con el paquete híbrido (Hybridity). Para obtener más información sobre la actualización de la instancia y el despliegue del servicio HCX on {{site.data.keyword.cloud_notm}}, consulte [Procedimiento para actualizar a la instancia de vCenter Server con el paquete híbrido (Hybridity)](../vcenter/vc_applyingupdates.html#procedure-to-upgrade-to-the-vcenter-server-with-hybridity-bundle-instance).

Una instancia de vCenter Server con HCX on {{site.data.keyword.cloud_notm}} está limitada a tres conexiones simultáneas de sitios locales.
{:note}

## Especificaciones técnicas para HCX on IBM Cloud

Los componentes siguientes se solicitan y se incluyen en el servicio HCX on {{site.data.keyword.cloud_notm}}.

Las instancias de HCX locales incluyen solo la licencia y la activación.
{:note}

### Un par activo/pasivo de pasarelas de servicio VMware NSX Edge para la gestión de HCX

* CPU: 6 vCPU
* RAM: 8 GB
* Disco: 3 GB VMDK

### Dispositivo de gestión HCX - máquina virtual

* CPU: 4 vCPU
* RAM: 12 GB
* Disco: 60 GB VMDK

Los dispositivos HCX adicionales se despliegan durante la configuración, según sean necesarios para la conectividad de L2, la optimización de WAN y las conexiones de pasarela.

### Redes

* Una subred portátil pública con 16 direcciones IP
* Dos subredes portátiles privadas con 64 direcciones IP
* Ocho direcciones IP desde una subred vMotion portátil privada

## Consideraciones al instalar HCX on IBM Cloud

Revise las siguientes consideraciones antes de intentar instalar HCX on {{site.data.keyword.cloud_notm}}.

### Requisitos sobre el número de servidores ESXi

El servicio HCX on {{site.data.keyword.cloud_notm}} no se puede instalar en una instancia para la cual el clúster predeterminado tenga más de 51 servidores ESXi. Como HCX on {{site.data.keyword.cloud_notm}} necesita ocho direcciones IP en la subred vMotion del clúster predeterminado, si el número de servidores ESXi supera los 51 no habrá ninguna dirección IP disponible en la subred vMotion para HCX on {{site.data.keyword.cloud_notm}}.

### Requisitos sobre las reglas de cortafuegos

Antes de instalar el HCX en el servicio de {{site.data.keyword.cloud_notm}}, debe añadir una regla de cortafuegos a cualquier cortafuegos existente para permitir todo el tráfico HTTPS de salida para que el dispositivo virtual HCX Manager (HCX Manager) se pueda registrar a sí mismo. Una vez finalizada la instalación de HCX Manager, puede eliminar la regla de cortafuegos. Además, debe configurar reglas de cortafuegos para permitir que HCX funcione correctamente. Para obtener más información, consulte el *Apéndice A - Requisitos de acceso a puertos* en [Arquitectura HCX on {{site.data.keyword.cloud_notm}}](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf).

## Consideraciones al eliminar HCX on IBM Cloud

Revise las siguientes consideraciones antes de eliminar el servicio HCX on {{site.data.keyword.cloud_notm}}:
* Asegúrese de que se eliminen las interconexiones y las redes ampliadas entre el sitio local de origen y los sitios de destino de {{site.data.keyword.cloud_notm}}. Para eliminar las interconexiones y las redes ampliadas, utilice la interfaz de usuario de HCX del cliente web local de VMware vSphere.
* Asegúrese de que se eliminen los emparejamientos de sitios entre el sitio local de origen y los sitios de destino de {{site.data.keyword.cloud_notm}}. Para eliminar los emparejamientos de sitios, utilice la interfaz de usuario de HCX del cliente web local de VMware vSphere.
* La eliminación de HCX on {{site.data.keyword.cloud_notm}} es automática. Se llevan a cabo los procedimientos siguientes para eliminar correctamente este servicio:
   * La licencia HCX que se solicita para el HCX Manager del lado de la nube está desactivada.
   * Se suprime HCX Manager.
   * Se liberan las direcciones IP de vMotion que se habían reservado para HCX.
   * Si están vacías, se eliminan las agrupaciones de recursos relacionadas con HCX.
   * Si están vacías, se eliminan las carpetas relacionadas con HCX.
   * Se suprimen los dispositivos del extremo de gestión de HCX.

### Enlaces relacionados

* [Solicitud de HCX on {{site.data.keyword.cloud_notm}}](hcx_ordering.html)
* [Gestión de HCX on {{site.data.keyword.cloud_notm}}](managinghcx.html)
* [Glosario de términos de HCX](hcx_glossary.html)
* [Cómo ponerse en contacto con el equipo de soporte de IBM](../vmonic/trbl_support.html)
* [Visión general de VMware Hybrid Cloud Extension](https://cloud.vmware.com/vmware-hcx)
* [Documentación de VMware Hybrid Cloud Extension](https://cloud.vmware.com/vmware-hcx/resources)
