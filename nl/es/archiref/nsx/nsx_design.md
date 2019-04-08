---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-01"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Diseño de NSX Edge Services Gateway
{: #nsx_design}

La solución NSX Edge Services Gateway en {{site.data.keyword.cloud}} proporciona la tecnología VMware que se despliega en {{site.data.keyword.CloudDataCents_notm}} en todo el mundo. {{site.data.keyword.vmwaresolutions_short}} proporciona dos arquitecturas de soluciones relacionadas con NSX Edge Services Gateway.

## Diseño de la arquitectura interna
{: #nsx_design-internal-archi}

La arquitectura interna especifica el despliegue de los componentes NSX Edge necesarios en una agrupación de recursos de un clúster convergente de VMware Cloud Foundation o en un clúster de VMware vCenter Server.

En la figura siguiente, VMware vSAN es opcional.
{:note}

Figura 1. Cloud Networking Services en {{site.data.keyword.cloud_notm}}

![Arquitectura de Cloud Networking Services](architecture.svg "Arquitectura de Cloud Networking Services")

## Diseño de la arquitectura dedicada
{: #nsx_design-dedicated-archi}

La arquitectura dedicada despliega los componentes NSX Edge necesarios en un clúster de vSphere de dos nodos separados exclusivo para el uso de NSX Edge y proporciona una interacción crítica con la infraestructura de red física. La arquitectura dedicada tiene las siguientes características y funciones:

* Ofrece conectividad en rampa y fuera de rampa a las redes físicas. Por ejemplo, el direccionamiento L3 norte-sur en dispositivos virtuales NSX Edge.
* Permite la comunicación con dispositivos físicos conectados a las VLAN en las redes físicas a través de un puente NSX L2 y aloja el direccionamiento de la máquina virtual (VM) de control para el direccionador lógico distribuido (DLR).
* Puede tener servicios lógicos o físicos centralizados. Por ejemplo, un cortafuegos, equilibradores de carga, componentes de supervisión de Red privada virtual (VPN), máquinas virtuales de conocimiento de registro.
* Los controladores NSX se pueden alotar en un clúster Edge cuando se utiliza un vCenter dedicado para gestionar los recursos de cálculo y de borde.
* Los recursos de clúster Edge tienen un requisito de antiafinidad para proteger la configuración de espera activa o para mantener la disponibilidad de ancho de banda durante el error.

## Rangos de direcciones IP privadas de IBM Cloud y rangos de direcciones Bring Your Own IP
{: #nsx_design-ip-addr-ranges}

El rango de direcciones IP privadas de RFC1918 reserva específicamente el uso de rangos de red para uso interno de la organización, nunca para Internet. La infraestructura de red física de {{site.data.keyword.cloud_notm}} utiliza un espacio de direcciones privado RFC1918 específico, 10.x.x.x/8, en todas ubicaciones de todo el mundo. Estos rangos de direcciones IP no se solapan entre cuentas ni dentro de una cuenta de cliente de {{site.data.keyword.cloud_notm}}. Dentro de una cuenta de cliente, cualquier espacio de direcciones IP privado asignado de {{site.data.keyword.cloud_notm}} puede, con el direccionamiento virtual y reenvío (VRF) habilitado, direccionar a cualquier otro rango de direcciones IP privadas de {{site.data.keyword.cloud_notm}} en cualquier {{site.data.keyword.CloudDataCents_notm}}.

Aunque esto hace que sea sencillo configurar una infraestructura conectada a nivel mundial dentro de su cuenta, el espacio de direcciones IP fijo puede ser problemático cuando se desea ampliar el centro de datos a {{site.data.keyword.cloud_notm}} mediante el direccionamiento cuando se utiliza el mismo espacio de direcciones privado que {{site.data.keyword.cloud_notm}}. La solución consiste en utilizar NSX para crear una topología de superposición en la infraestructura de Cloud Foundation o vCenter Server, aislando el espacio de direcciones de Bring Your Own IP (BYOIP) de la interacción con el espacio de direcciones IP privadas asignado de {{site.data.keyword.cloud_notm}}. NSX puede proporcionar una VPN de L2 para abarcar el espacio de direcciones BYOIP interno dentro del túnel entre espacios de direcciones IP externos, posiblemente solapados.

## Enlaces relacionados
{: #nsx_design-related}

* [Visión general de la solución](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_overview)
