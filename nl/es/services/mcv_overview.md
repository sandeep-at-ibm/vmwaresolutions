---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-04"

subcollection: vmware-solutions


---

# Visión general de Mission Critical VMware on IBM Cloud
{: #mcv_overview}

Mission Critical VMware on {{site.data.keyword.cloud}} proporciona una arquitectura de nube multizona que ayuda a las empresas a evitar el tiempo de inactividad de las aplicaciones en la nube y a automatizar las migraciones tras error dentro de una región de nube.

Con esta arquitectura de nube, los clientes pueden conseguir una mayor disponibilidad y una tasa de éxito de migración tras error superior al que obtienen la mayoría de los clientes de VMware con entornos locales o con plataformas de nube de la competencia.

Esta arquitectura da soporte a las cargas de trabajo existentes, críticas y antiguas, incluidas las aplicaciones nativas que no son de nube, con una disponibilidad agregada de destino del 99,99%. Las regiones multizona de IBM Cloud están diseñadas para mantener las cargas de trabajo críticas en línea si se produce una caída en el sitio. Las cargas de trabajo de un sitio fallido se reinician automáticamente casi en tiempo real, mientras que las cargas de trabajo de los sitios adyacentes permanecen en línea y disponibles.

La arquitectura cubre varios servicios empresariales, que incluyen redes, almacenamiento, resiliencia y otras herramientas creadas para la supervisión y la resolución de problemas de aplicaciones basadas en la nube. Además, esta arquitectura se puede integrar con IBM Services Platform with Watson, incorporada en {{site.data.keyword.cloud_notm}}, para permitir un consumo más amplio de servicios. Mediante la utilización de las funciones cognitivas de la plataforma, los clientes pueden extraer datos de forma más eficiente para obtener nuevos conocimientos empresariales a fin de ayudar a mantener la continuidad de las operaciones.

## Especificaciones técnicas de Mission Critical VMware on IBM Cloud
{: #mcv_overview-specs}

La arquitectura Critical VMware on {{site.data.keyword.cloud_notm}} es una arquitectura de referencia de extremo a extremo que proporciona migración tras error automatizada para las cargas de trabajo del cliente. Utiliza una región multizona de {{site.data.keyword.cloud_notm}} con un servicio gestionado por IBM que cubre los siguientes componentes:

* Arquitectura de cálculo (VMware vSphere)
* Arquitectura de red (actualmente NSX-V)
* Arquitectura de almacenamiento (VMware vSAN)
* Integración con IBM Services Platform with Watson para permitir el consumo de servicios
* Herramientas para la supervisión, resolución de problemas, rendimiento y gestión de la capacidad:
  * Patrón vRealize Suite (operaciones, Log Insight y Network Insight)
  * Patrón Active Directory
  * Integración con Netcool/Bluecare para la mejora en el proceso automático y la gestión de alertas y sucesos
  * Patrones de resiliencia (copia de seguridad y recuperación)

Mission Critical VMware on {{site.data.keyword.cloud_notm}} está disponible en las siguientes regiones:
* América: NA sur - todos los centros de datos de IBM Cloud de Dallas y NA este: todos los centros de datos de IBM Cloud de Washington, DC
* Europa: todos los centros de datos de IBM Cloud de Frankfurt y Londres
* Asia Pacífico: todos los centros de datos de IBM Cloud de Sídney y Tokio

### Especificaciones de la arquitectura de la infraestructura base
{: #mcv_overview-base-specs}

La infraestructura base tiene las siguientes especificaciones:
* Cada sitio tiene su propio extremo dedicado y clúster de gestión
* El clúster de recursos es un clúster expandido de vSphere + vSAN
* El sitio testigo contiene un host ESXi testigo
* Arquitectura de un solo vCenter y NSX Manager
* Dispositivo vCenter Server con controlador de servicios de plataforma (PSC) integrado que utiliza alta disponibilidad (HA) de vCenter a través de una arquitectura de red L3
* La recuperación de NSX Manager utiliza una metodología en caliente/en espera que sincroniza los archivos de copia de seguridad

### Especificaciones de la arquitectura de herramientas y tecnológica
{: #mcv_overview-tooling-specs}

La arquitectura de herramientas y tecnológica tiene las siguientes especificaciones:
* Operaciones vRealize, vRealize Log Insight y vRealize Network Insight para ofrecer operaciones y funciones de gestión específicas de los productos VMware utilizados, como por ejemplo NSX, vSAN y vSphere
* IBM Software Defined Environment Automation Tool Health Check (SAT HC) para validar los despliegues frente a las mejores prácticas y políticas de seguridad
* Recuperación tras desastre (DR) opcional de entrada y salida del sitio {{site.data.keyword.cloud_notm}} de la región
* Fortigate Security Appliance o similar para proteger cualquier acceso a Internet y para facilitar la integración de red activa-activa con la red local

### Especificaciones de la arquitectura de clúster extendido vSphere + vSAN
{: #mcv_overview-stretched-cluster-specs}

La arquitectura de clúster extendido vSphere + vSAN tiene las siguientes especificaciones:
* El clúster proporciona funciones de almacenamiento y de cálculo que abarcan dos sitios para proporcionar disponibilidad mejorada.
* Las solicitudes de escritura procedentes de máquinas virtuales (VM) se escriben de forma síncrona en ambos sitios, lo que implica latencia de red de sitio a sitio.
* Las solicitudes de lectura procedentes de las máquinas virtuales se solucionan localmente en la ubicación física en la que se encuentra la VM, lo que evita latencia adicional.
* El sitio testigo y el host testigo actúan como el cerebro/quórum dividido.
* Con esta arquitectura se puede utilizar vSAN Native Encryption (para el cifrado en reposo).

### Especificaciones de la arquitectura de red
{: #mcv_overview-network-specs}

La arquitectura de red tiene las siguientes especificaciones:
* Edge/DLR/VXLAN en combinación con direccionamiento basado en métricas BGP para facilitar un diseño de sitio activo-activo con migración tras error automatizada.
* Cada sitio tiene el concepto de su propio conjunto de Edges/DLR y VXLAN.
* En circunstancias normales, cualquier VM conectada a DLR-A, por ejemplo VM-A, estará en la zona de disponibilidad 1 de {{site.data.keyword.cloud_notm}} y el tráfico entrará y saldrá de forma local.
* Durante una actividad vMotion para VM-A, el tráfico seguirá entrando y saliendo a través de la zona de disponibilidad 1 de {{site.data.keyword.cloud_notm}}.
* Si se produce un error del sitio o del extremo, el tráfico se dirigirá hacia el sitio disponible restante.

## Enlaces relacionados
{: #mcv_overview-related}

* [Solicitud de Mission Critical VMware on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_mcv)
