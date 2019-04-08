---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-13"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Capacidad de escalado
{: #solution_scaling}

Después del despliegue inicial, puede ampliar la capacidad de cálculo de la consola de {{site.data.keyword.vmwaresolutions_full}}. El diseño da soporte a las siguientes vías de acceso de escalado:
* Adición de nuevos sitios gestionados por servidores de vCenter independientes
* Adición de nuevos clústeres
* Adición de nuevos hosts a un clúster existente

## Adición de más sitios
{: #solution_scaling-sites}

{{site.data.keyword.vmwaresolutions_short}} puede aprovechar la presencia del centro de datos a nivel mundial de {{site.data.keyword.cloud_notm}} y la red troncal integrada para permitir que varios casos de uso entre geografía se desplieguen y funcionen dentro de una fracción del tiempo que tomaría para crear dicha infraestructura desde cero.

En este diseño, la definición de un despliegue de varios sitios se compone de lo siguiente:
* Un despliegue de VMware inicial o primario que contiene un nuevo dominio raíz de DNS/AD, un subdominio, un dominio SSO y un nombre de sitio SSO que se va a proporcionar.
* Sitios secundarios individuales o múltiples que se suministran en el dominio SSO de sitios primarios que requieren la configuración siguiente:
   * Nuevo nombre de sitio de SSO
   * Nuevo sitio/subdominio DNS enlazado a la raíz del dominio primario
   * Configuración de réplica de DNS y AD entre las máquinas virtuales de AD de sitio primario y secundario
   * Configuración de vCenter con modalidad enlazada mejorada al vCenter del sitio primario

Adicionalmente, el gestor de NSX en los sitios secundarios puede configurarse como gestores NSX secundarios para el gestor NSX en el sitio primario. Este es un proceso manual que debe realizar.

## Adición de nuevos clústeres
{: #solution_scaling-clusters}

También puede ampliar la capacidad de cálculo creando un nuevo clúster desde la consola de {{site.data.keyword.vmwaresolutions_short}} y solicitando nuevos hosts que se añaden automáticamente al nuevo clúster.

Este método le permite realizar lo siguiente:
* Creación de un clúster adicional y separado en el entorno.
* Segregación de cargas de trabajo de gestión desde cargas de trabajo de aplicaciones de forma física y lógica.
* Segregación de cargas de trabajo basadas en otras características, por ejemplo, el clúster de base de datos SQL de Microsoft.
* Despliegue de aplicaciones en topologías altamente disponibles.

Cuando el clúster inicial se convierte en un clúster de solo gestión, la migración de cargas de trabajo existentes implicará los pasos manuales que debe tomar el usuario. Esto puede implicar la reagrupación de almacenes de datos en el nuevo clúster o, como alternativa, la migración de almacenamiento. Es posible que sea necesario cambiar las direcciones IP de las cargas de trabajo si el nuevo clúster se encuentra en un pod de {{site.data.keyword.cloud_notm}} diferente o si se asigna el clúster a un ID de VLAN distinto.
{:note}

## Adición de hosts ESXi en clústeres existentes
{: #solution_scaling-hosts}

Puede ampliar un clúster existente solicitando hosts desde la consola de {{site.data.keyword.vmwaresolutions_short}}.  Los nuevos hosts se añaden automáticamente al clúster. Tenga en cuenta que es posible que tenga que ajustar la política de reserva de HA para el clúster en función de los requisitos de la reserva.

## Enlaces relacionados
{: #solution_scaling-related}

* [Visión general de la solución](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_overview)
* [Visión general del diseño](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-design_overview)
* [Copia de seguridad de los componentes](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_backingup)
