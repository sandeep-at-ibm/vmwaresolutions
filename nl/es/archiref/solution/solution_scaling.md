---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-10"

---

# Capacidad de escalado

Después del despliegue inicial, puede ampliar la capacidad de cálculo de la consola de {{site.data.keyword.vmwaresolutions_full}}. El diseño da soporte a las siguientes vías de acceso de escalado:
* Adición de nuevos sitios gestionados por servidores de vCenter independientes
* Adición de nuevos clústeres
* Adición de nuevos hosts a un clúster existente

## Adición de más sitios

{{site.data.keyword.vmwaresolutions_short}} puede aprovechar la presencia del centro de datos a nivel mundial de {{site.data.keyword.cloud_notm}} y la red troncal de red integrada para permitir que una variedad de casos de uso entre geografía se desplieguen y funcionen dentro de una fracción del tiempo que tomaría para crear dicha infraestructura desde cero.

En este diseño, la definición de un despliegue de varios sitios se compone de lo siguiente:
* Un despliegue de VMware inicial o primario que contiene un nuevo dominio raíz de DNS/AD, un subdominio, un dominio SSO y un nombre de sitio SSO que se va a proporcionar.
* Sitios secundarios individuales o múltiples que se suministran en el dominio SSO de sitios primarios que requieren la configuración siguiente:
   * Nuevo nombre de sitio de SSO
   * Nuevo sitio/subdominio DNS enlazado a la raíz del dominio primario
   * Configuración de réplica de DNS y AD entre las máquinas virtuales de AD de sitio primario y secundario
   * PSC desplegado y configurado para sincronizarse con el PSC de sitio primario
   * Configuración de vCenter con modalidad enlazada mejorada al vCenter del sitio primario

Adicionalmente, el gestor de NSX en los sitios secundarios puede configurarse como gestores NSX secundarios para el gestor NSX en el sitio primario.

## Adición de nuevos clústeres

También puede ampliar la capacidad de cálculo creando un nuevo clúster desde la consola de {{site.data.keyword.vmwaresolutions_short}} y solicitando nuevos hosts que se añaden automáticamente al nuevo clúster.

Este método le permite realizar lo siguiente:
* Creación de un clúster adicional y separado en el entorno.
* Segregación de cargas de trabajo de gestión desde cargas de trabajo de aplicaciones de forma física y lógica.
* Segregación de cargas de trabajo basadas en otras características, por ejemplo, el clúster de base de datos SQL de Microsoft.
* Despliegue de aplicaciones en topologías altamente disponibles.

**Nota**: Cuando el clúster inicial se convierte en un clúster de solo gestión, la migración de cargas de trabajo existentes implicará los pasos manuales que debe tomar el usuario. Esto puede implicar la reagrupación de almacenes de datos en el nuevo clúster o, como alternativa, la migración de almacenamiento. Es posible que sea necesario cambiar las direcciones IP de las cargas de trabajo si el nuevo clúster se encuentra en un pod de {{site.data.keyword.cloud_notm}} diferente o se le asigna un ID de VLAN diferente.

## Adición de hosts ESXi en clústeres existentes

Puede ampliar un clúster existente solicitando hosts desde la consola de {{site.data.keyword.vmwaresolutions_short}}.  Los nuevos hosts se añaden automáticamente al clúster. Tenga en cuenta que es posible que tenga que ajustar la política de reserva de HA para el clúster en función de los requisitos de la reserva.

### Enlaces relacionados

* [Visión general de la solución](solution_overview.html)
* [Visión general del diseño](design_overview.html)
* [Copia de seguridad de los componentes](solution_backingup.html)
