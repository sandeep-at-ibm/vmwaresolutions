---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-09"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Visión general de IBM Cloud Private Hosted

El servicio {{site.data.keyword.cloud}} Private Hosted despliega automáticamente {{site.data.keyword.cloud_notm}} Private Hosted en sus instancias de VMware vCenter Server. Este servicio incorpora la potencia de los microservicios y contenedores al entorno VMware en {{site.data.keyword.cloud_notm}}. Con este servicio, puede ampliar el mismo modelo operativo VMware e {{site.data.keyword.cloud_notm}} privado con el que está familiarizado y las herramientas del entorno local en {{site.data.keyword.cloud_notm}}.

Este servicio está disponible para las instancias siguientes:
* Instancias de vCenter Server desplegadas en la versión V2.5 y posteriores o actualizadas a las mismas
* Instancias de vCenter Server con el paquete híbrido (Hybridity) desplegadas en la versión V2.7 y posteriores o actualizadas a las mismas
{:note}

## Especificaciones técnicas de IBM Cloud Private Hosted

En la tabla siguiente se muestran los requisitos mínimos para solicitar el servicio IBM Cloud Private Hosted para un entorno **Preparado para producción** y un entorno de **Desarrollo/Prueba**.

Tabla 1. Requisitos mínimos para el entorno preparado para producción y el entorno de desarrollo/prueba

|Entorno | Núcleos | Memoria (GB) | Hosts | Almacenamiento (GB) |
|:---------- |:---- |:------ |:---- |:------- |
| Prep. para prod. | 52 | 640 | 3 | 8.000 |
| Desarrollo/Prueba | 30 | 200 | 3 | 4.000 |

### Requisitos de recursos para IBM Cloud Private Hosted

En las tablas siguientes se muestran los requisitos de recursos del servicio {{site.data.keyword.cloud_notm}} Private Hosted en un entorno preparado para producción y en un entorno de desarrollo/prueba.

Tabla 2. Requisitos de recursos de {{site.data.keyword.cloud_notm}} Private Hosted en un entorno preparado para producción

| Tipo nodo  | Núcleos CPU   |  Memoria (GB) | Disco 1 (GB) | Disco 2 (GB) | Núm. de VM |
|:---------- |:----------- |:------------ |:----------- |:----------- |:------------- |
| Arranque       | 12 | 24 | 100 | 1 | 1 |   
| Gestión | 8 | 64 | 500 | 3 | 3 |
| Maestro     | 8 | 64 | 200 | 3 | 3 |  
| Proxy      | 2 | 4  | 150 | 3 | 3 |
| Trabajador     | 4 | 16 | 200 | 300 | 6 |
| Vulnerability Advisor | 8 | 16 | 500 | 1 | 1 |
| GlusterFS  | 8 | 16 | 150 | 50 | 3 |
| Bootstrap ICP/CAM | 16 | 32 | 250 | 1 | 1 |
| Servidor NFS | 8 | 4  | 350 | 1 | 1 |
| NSX Edge Services Gateway | 2 | 1 | 0,5 | 0,5 | 2 |
| Restricciones documentadas | 52 | 640 |  | 8.000 |   |

Tabla 3. Requisitos de recursos de {{site.data.keyword.cloud_notm}} Private Hosted en un entorno de desarrollo/prueba

| Tipo nodo  | Núcleos CPU   |  Memoria (GB) | Disco 1 (GB) | Disco 2 (GB) | Núm. de VM |
|:---------- |:----------- |:------------ |:----------- |:----------- |:------------- |
| Arranque       | 12 | 24 | 100 | 1 | 1 |   
| Gestión | 8 | 16 | 150 | 1 | 1 |
| Maestro     | 8 | 16 | 200 | 1 | 1 |  
| Proxy      | 2 | 4  | 150 | 1 | 1 |
| Trabajador     | 4 | 16 | 200 | 300 | 3 |
| Vulnerability Advisor | 8 | 16 | 150 | 1 | 1 |
| GlusterFS  | 8 | 16 | 150 | 50 | 3 |
| Bootstrap ICP/CAM | 16 | 32 | 250 | 1 | 1 |
| Servidor NFS | 8 | 4  | 350 | 1 | 1 |
| NSX Edge Services Gateway | 2 | 1 | 0,5 | 0,5 | 2 |
| Restricciones documentadas | 30 | 200 |  | 4.000 |  |

### Fórmulas para calcular los requisitos de espacio de IBM Cloud Private Hosted

Las fórmulas siguientes se utilizan para calcular los requisitos de espacio de IBM Cloud Private y las sobrecargas de gestión.

#### Fórmula 1

`AvailableCores = [ HostCoreCount - HostOverheadCores - ( HostVSanOverheadCorePercentage * HostCoreCount) ] * ( HostCount - vSphereHAHostTolerance ) - MgmtOverheadCores`

Tabla 4. Descripción de las variables de la Fórmula 1

| Variables	| Descripción |	Unidad |	Ejemplo de vSAN | Ejemplo de NFS |
|:--------- |:----------- |:---- |:------------- |:----------- |
| AvailableCores |	El número de núcleos reales disponibles para cargas de trabajo y servicios en el entorno |	Núcleos |	38	| 43 |
| HostCount	| El número de hosts en el clúster predeterminado	| Hosts | 4	| 4 |
| HostCoreCount	| El número de núcleos brutos disponibles en cada host en el clúster predeterminado |	Núcleos |	16 | 16 |
| HostOverheadCores	| El número de núcleos reservados por el servidor ESXi como sobrecarga, que equivale a 0,1 núcleos	| Núcleos	| 0,1 |	0,1 |
| MgmtOverheadCores | El número de núcleos reservados por los componentes de gestión de vCenter Server (vCenter Server, PSC, AD/DNS, Extremos), que equivale a cinco núcleos	| Núcleos	| 5	| 5 |
| vSphereHAHostTolerance |	El número de hosts que se deben tolerar en la configuración de alta disponibilidad de vSphere, que equivale a un host |	Hosts	 | 1 | 1 |
| HostVsanOverheadCorePercentage | Porcentaje de núcleos de host utilizados por vSAN, que equivale al 10% o es igual a 0% si el host no es vSAN | % | 10% |	0% |

#### Fórmula 2

`AvailableMemory = [HostMemory - HostOverheadMemory - HostVsanOverheadMemory - (HostVsanOverheadMemoryDiskPercentage * HostVsanCapacityDiskSize)] * (HostCount - vSphereHAHostTolerance) - MgmtOverheadMemory`

Tabla 5. Descripción de las variables de la Fórmula 2

| Variables	| Descripción |	Unidad |	Ejemplo de vSAN | Ejemplo de NFS |
|:--------- |:----------- |:---- |:------------- |:----------- |
| AvailableMemory	| El número de GB de memoria disponibles para cargas de trabajo y servicios en el entorno | GB | 	693	| 860 |
| HostCount	| El número de hosts en el clúster predeterminado | Hosts  | 6	| 6 |
| HostMemory |	El número de GB brutos de memoria disponibles en cada host en el clúster predeterminado |	GB	| 192 |	192 |
| HostVsanCapacityDiskSize | El número de GB de una capacidad de cada disco SSD de capacidad vSAN en este host, que equivale a 960, 1.946 o 3.891, o equivale a 0 GB si no es VSAN | GB |	960 | 0 |
| HostOverheadMemory |	El número de GB de memoria reservados por el servidor ESXi como sobrecarga, que equivale a 4,6 GB |	GB	| 4,6 |	4,6 |
| MgmtOverheadMemory |	El número de GB de memoria reservados por los componentes de gestión de vCenter Server (vCenter Server, PSC, AD/DNS, Extremos), que equivale a 77 GB | GB | 77 | 77 |
| vSphereHAHostTolerance | El número de hosts que se deben tolerar en la configuración de alta disponibilidad de vSphere, que equivale a un host | Hosts	| 1 | 1 |
| HostVsanOverheadMemoryDiskPercentage | El número de GB de memoria reservados por la gestión de vSAN (representado como porcentaje de uno de los discos vSAN de capacidad), que equivale al 2,75% |	% | 2,75%	| 2,75% |
| HostVsanOverheadMemory | El número de GB de memoria reservados por la gestión de vSAN, independientemente del tamaño de disco, que equivale a 7 GB o equivale a 0 GB si no es VSAN	| GB |  7	| 0 |

## Consideraciones sobre la instalación de IBM Cloud Private Hosted

* Obtenga la licencia necesaria antes de instalar el servicio {{site.data.keyword.cloud_notm}} Private Hosted. Le recomendamos que se asegure de que la licencia no solo puede dar soporte al despliegue inicial de {{site.data.keyword.cloud_notm}} Private Hosted, sino también a una futura expansión de {{site.data.keyword.cloud_notm}} Private Hosted en su infraestructura.
* Para los despliegues de {{site.data.keyword.cloud_notm}} Private Hosted en entornos preparados para producción, no se da soporte a la opción de 64 GB de RAM por host. Por lo tanto, debe seleccionar una opción que sea superior a 64 GB para **RAM**.
* Antes de instalar el servicio {{site.data.keyword.cloud_notm}} Private Hosted en el entorno, se realiza una comprobación de la capacidad disponible del clúster predeterminado en el entorno para garantizar que hay espacio suficiente para los componentes del servicio. Si la comprobación de capacidad falla, el servicio no se instala y el estado del servicio se establece en **Error de validación de capacidad** en la consola. Además, se muestra un mensaje en la consola con más detalles y se le notifica por correo electrónico. Para instalar el servicio, debe aumentar la capacidad en el clúster predeterminado añadiendo más hosts o liberando RAM, CPU o espacio de disco y, a continuación, debe añadir el servicio de nuevo en la consola. Después de esto, puede eliminar el servicio existente en el estado **Error de validación de capacidad** pulsando el icono **Suprimir** situado junto al mismo.

## Consideraciones sobre la eliminación de IBM Cloud Private Hosted

* {{site.data.keyword.cloud_notm}} solo suprime las máquinas virtuales (VM) desplegadas durante la instalación inicial del servicio {{site.data.keyword.cloud_notm}} Private Hosted. Los nodos que se desplieguen después de la instalación no se eliminarán.
* {{site.data.keyword.cloud_notm}} suprimirá VXLAN, DLR y la pasarela de extremo creada durante el despliegue inicial del servicio {{site.data.keyword.cloud_notm}} Private Hosted. Las VM que haya desplegado en VXLAN perderán la conectividad cuando comience el proceso de eliminación del servicio {{site.data.keyword.cloud_notm}} Private Hosted.

### Enlaces relacionados

* [Solicitud de IBM Cloud Private Hosted](../services/icp_ordering.html)
* [Guía de vCenter Server e IBM Cloud Private](../archiref/vcsicp/vcsicp-intro.html)
* [Apertura de una incidencia para IBM Cloud privado](https://www.ibm.com/mysupport/s/?language=en_US)
