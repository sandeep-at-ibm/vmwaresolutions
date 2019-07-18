---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-26"

keywords: vCenter Server Hybridity multi-site, multi-site configuration Hybridity, multi-site deployment vCenter Server Hybridity

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Configuración de varios sitios para instancias de vCenter Server con el paquete híbrido (Hybridity)
{: #vc_hybrid_multisite}

{{site.data.keyword.vmwaresolutions_full}} permite desplegar instancias en diferentes ubicaciones y conseguir que se activen y se ejecuten en un breve periodo de tiempo.

## Componentes de un despliegue de varios sitios
{: #vc_hybrid_multisite-deployment-components}

Un despliegue de varios sitios consta de los siguientes componentes.

* **Instancia primaria**: La instancia primaria de vCenter Server con el paquete híbrido (Hybridity) tiene la siguiente configuración:
  *  Dominio raíz Microsoft Active Directory (AD) y DNS (Sistema de nombres de dominio)
  *  Subdominio de vCenter Server
  *  Dominio SSO (inicio de sesión único)
  *  Nombre del sitio SSO
* **Instancia o instancias secundarias**: Una o varias instancias secundarias de vCenter Server con el paquete híbrido (Hybridity), enlazadas a la instancia primaria, con la configuración siguiente:
   *  Nombre del sitio SSO
   *  Subdominio DNS enlazado al dominio raíz en la instancia primaria
   *  Réplica de DNS y AD configurada entre las máquinas virtuales AD en las instancias primaria y secundarias
   *  Para instancias primarias que se han desplegado en V2.8 o posteriores: Se despliega y configura vCenter Server Appliance (vCSA) con Platform Services Controller (PSC) incorporado
   *  VMware vCenter en las instancias secundarias se configura con la modalidad enlazada mejorada con el vCenter en la instancia primaria

## Despliegue de varios sitios de vCenter Server con el paquete híbrido (Hybridity)
{: #vc_hybrid_multisite-deployment}

La característica de configuración de varios sitios utiliza una topología de estrella ("hub and spoke") con un sitio primario y un máximo de siete sitios secundarios. Se da soporte a una sola capa de sitios, es decir, no puede configurar otros sitios enlazados a otros sitios secundarios. Puede tener un total de 128 servidores ESXi en una configuración de varios sitios entre todas las instancias.

Si la configuración requiere un despliegue de varios sitios con más de 128 servidores ESXi, póngase en contacto con el equipo de soporte de IBM para obtener ayuda. Para obtener más información, consulte [Cómo ponerse en contacto con el equipo de soporte de IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support).
{:note}

En el siguiente gráfico se muestra una visión general del despliegue de varios sitios de vCenter Server con el paquete híbrido (Hybridity).

![Despliegue de varios sitios de vCenter Server con el paquete híbrido (Hybridity)](../images/multisite-hub-spoke.svg "Despliegue de varios sitios de vCenter Server con el paquete híbrido (Hybridity)")

El modelo contiene las siguientes capas:

* **Instancia primaria**: en una configuración de varios sitios, para desplegar la primera instancia debe definir dicha instancia como primaria durante el proceso de pedido de la instancia.
* **Instancias secundarias**: en una configuración de varios sitios, debe definir las instancias que están conectadas a la instancia primaria como instancias secundarias durante el proceso de pedido.

Las instancias secundarias se asignan a una instancia primara de una en una. No puede asignar varias instancias secundarias a una instancia primaria al mismo tiempo. Para hacerlo, debe volver a pasar por el proceso de pedido y seleccionar la instancia primaria definida anteriormente como una instancia primaria para la instancia secundaria. Debe repetir el proceso para todas las instancias secundarias que desee crear.

Puede tener un máximo de 8 (1 primaria y 7 secundarias) instancias desplegadas en una configuración de varios sitios.

La supresión de instancias de vCenter Server con el paquete híbrido (Hybridity) que formen parte de una configuración de varios sitios requiere una planificación especial. Para obtener más información, consulte [Supresión de instancias de vCenter Server con el paquete híbrido (Hybridity) en una configuración de varios sitios](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_deletinginstance_multi).
{:note}

## Enlaces relacionados
{: #vc_hybrid_multisite-related}

* [Asignación del rol primario a NSX Manager](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.2/com.vmware.nsx-cross-vcenter-install.doc/GUID-44E8AE16-BA3F-4DD9-B582-FC1E137E6CFC.html){:external}
* [Configuración de NSX Managers secundarios](https://pubs.vmware.com/NSX-62/topic/com.vmware.nsx-cross-vcenter-install.doc/GUID-9E48BC57-15E3-49C7-8BC5-F94ED8918BBE.html){:external}
* [Microsoft Active Directory Trusts con soporte para SSO (inicio de sesión único) de VMware vCenter](https://kb.vmware.com/s/article/2064250){:external}
