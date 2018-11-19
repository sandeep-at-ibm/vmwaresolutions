---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-26"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Visión general de IBM Cloud Private Hosted

El servicio {{site.data.keyword.cloud}} Private Hosted despliega automáticamente {{site.data.keyword.cloud_notm}} Private Hosted en sus instancias de VMware vCenter Server. Este servicio incorpora la potencia de los microservicios y contenedores al entorno VMware en {{site.data.keyword.cloud_notm}}. Con este servicio, puede ampliar el mismo modelo operativo VMware y {{site.data.keyword.cloud_notm}} privado con el que está familiarizado y las herramientas del entorno local en {{site.data.keyword.cloud_notm}}.

Este servicio está disponible para:
* Instancias de vCenter Server desplegadas en la versión V2.5 y posteriores o actualizadas a las mismas
* Instancias de vCenter Server con el paquete híbrido (Hybridity) desplegadas en la versión V2.7 y posteriores o actualizadas a las mismas.
{:note}

## Especificaciones técnicas de IBM Cloud Private Hosted

En la tabla siguiente se muestran los requisitos mínimos para solicitar el servicio IBM Cloud Private Hosted para un entorno **Preparado para producción** y un entorno de **Desarrollo/Prueba**.

Tabla 1. Requisitos mínimos para el entorno preparado para producción y el entorno de desarrollo/prueba

|Entorno | Núcleo | Memoria | Host | Almacenamiento |
|:---------- |:---- |:------ |:---- |:------- |
| Prep. para prod. | 52 | 640 | 3 | 8000 |
| Desarrollo/Prueba | 30 | 200 | 3 | 4000 |

### Requisitos de recursos de IBM Cloud Private Hosted

En las tablas siguientes se muestran los requisitos de recursos del servicio {{site.data.keyword.cloud_notm}} Private Hosted en un entorno preparado para producción y en un entorno de desarrollo/prueba.

Tabla 2. Requisitos de recursos de {{site.data.keyword.cloud_notm}} Private Hosted en un entorno preparado para producción

| Tipo nodo  | Núcleos CPU   |  Memoria (GB) | Disco 1 (GB) | Disco 2 (GB) | Núm. de VM |
|:---------- |:----------- |:------------ |:----------- |:----------- |:------------- |
| Arranque       | 8 | 16 | 100 | 1 | 1 |   
| Gestión | 8 | 64 | 500 | 3 | 3 |
| Maestro     | 8 | 64 | 200 | 3 | 3 |  
| Proxy      | 2 | 4  | 150 | 3 | 3 |
| Trabajador     | 4 | 16 | 200 | 300 | 6 |
| Vulnerability Advisor | 8 | 16 | 500 | 3 | 3 |
| GlusterFS  | 8 | 16 | 150 | 50 | 3 |
| Bootstrap ICP/CAM | 16 | 32 | 250 | 1 | 1 |
| Servidor NFS | 8 | 4  | 350 | 1 | 1 |
| Extremo | 2 | 1 | 0,5 | 0,5 | 2 |
| Total | 162 | 642 | 6401 | 1951 | 26 |
| Restricciones documentadas | 52 | 640 |  | 8000 |   |
|   | Ratio 1:3 | Ratio 1:1 |  | Ratio 1:1 |  |

Tabla 3. Requisitos de recursos de {{site.data.keyword.cloud_notm}} Private Hosted en un entorno de desarrollo/prueba

| Tipo nodo  | Núcleos CPU   |  Memoria (GB) | Disco 1 (GB) | Disco 2 (GB) | Núm. de VM |
|:---------- |:----------- |:------------ |:----------- |:----------- |:------------- |
| Arranque       | 8 | 16 | 100 | 1 | 1 |   
| Gestión | 8 | 16 | 150 | 1 | 1 |
| Maestro     | 8 | 16 | 200 | 1 | 1 |  
| Proxy      | 2 | 4  | 150 | 1 | 1 |
| Trabajador     | 4 | 16 | 200 | 300 | 3 |
| Vulnerability Advisor | 8 | 16 | 150 | 1 | 1 |
| GlusterFS  | 8 | 16 | 150 | 50 | 3 |
| Bootstrap ICP/CAM | 16 | 32 | 250 | 1 | 1 |
| Servidor NFS | 8 | 4  | 350 | 1 | 1 |
| Extremo | 1 | 0,5 | 0,5 | 2 | 2 |
| Total | 96 | 201 | 2401 | 1050 | 15 |
| Restricciones documentadas | 30 | 200 |  | 4000 |  |
|  | Ratio 1:3 | Ratio 1:1 |  | Ratio 1:1 |  |

### Fórmulas para calcular los requisitos de espacio de IBM Cloud Private Hosted

Las fórmulas siguientes se utilizan para calcular los requisitos de espacio de IBM Cloud Private y las sobrecargas de gestión.

Fórmula 1: `AvailableCores = [ HostCoreCount - HostOverheadCores - ( HostVSanOverheadCorePercentage * HostCoreCount) ] * ( HostCount - vSphereHAHostTolerance ) - MgmtOverheadCores`

Tabla 4. Descripción de las variables de la Fórmula 1

| Variables	| Descripción |	Unidad |	Ejemplo de vSAN | Ejemplo de NFS |
|:--------- |:----------- |:---- |:------------- |:----------- |
| AvailableCores |	El número de núcleos reales disponibles para cargas de trabajo y servicios en el entorno |	núcleos |	38	| 43 |
| HostCount	| El número de hosts en el clúster predeterminado	| hosts | 4	| 4 |
| HostCoreCount	| El número de núcleos brutos disponibles en cada host en el clúster predeterminado |	núcleos |	16 | 16 |
| HostOverheadCores	| El número de núcleos reservados por el servidor ESXi como sobrecarga, que equivale a 0,1 núcleos	| núcleos	| 0,1 |	0,1 |
| MgmtOverheadCores | El número de núcleos reservados por los componentes de gestión de vCenter Server (vCenter Server, PSC, AD/DNS, Extremos), que equivale a 5 núcleos	| núcleos	| 5	| 5 |
| vSphereHAHostTolerance |	El número de hosts que se deben tolerar en la configuración de alta disponibilidad de vSphere, que equivale a 1 host |	hosts	 | 1 | 1 |
| HostVsanOverheadCorePercentage | El porcentaje de los núcleos de un host utilizados por vSAN, que equivale al 10% al 0% si es un host no vsan	| % | 10% |	0% |

Fórmula 2: `AvailableMemory = [ HostMemory - HostOverheadMemory - HostVsanOverheadMemory - ( HostVsanOverheadMemoryDiskPercentage * HostVsanCapacityDiskSize) ] * ( HostCount - vSphereHAHostTolerance ) - MgmtOverheadMemory`

Tabla 5. Descripción de las variables de la Fórmula 2

| Variables	| Descripción |	Unidad |	Ejemplo de vSAN | Ejemplo de NFS |
|:--------- |:----------- |:---- |:------------- |:----------- |
| AvailableMemory	| El número de GB de memoria disponibles para cargas de trabajo y servicios en el entorno | GB | 	693	| 860 |
| HostCount	| El número de hosts en el clúster predeterminado | hosts  | 6	| 6 |
| HostMemory |	El número de GB brutos de memoria disponibles en cada host en el clúster predeterminado |	GB	| 192 |	192 |
| HostVsanCapacityDiskSize | El número de GB de una capacidad de cada disco SSD de capacidad vSAN en este host, que equivale a 960, 1946 o 3891, o equivale a 0 GB si no es VSAN | GB |	960 | 0 |
| HostOverheadMemory |	El número de GB de memoria reservados por el servidor ESXi como sobrecarga, que equivale a 4,6 GB |	GB	| 4,6 |	4,6 |
| MgmtOverheadMemory |	El número de GB de memoria reservados por los componentes de gestión de vCenter Server (vCenter Server, PSC, AD/DNS, Extremos), que equivale a 77 GB | GB | 77 | 77 |
| vSphereHAHostTolerance | El número de hosts que se deben tolerar en la configuración de alta disponibilidad de vSphere, que equivale a 1 host | hosts	| 1 | 1 |
| HostVsanOverheadMemoryDiskPercentage | El número de GB de memoria reservados por la gestión de vSAN (representado como porcentaje de uno de los discos vSAN de capacidad), que equivale al 2,75% |	% | 2,75%	| 2,75% |
| HostVsanOverheadMemory | El número de GB de memoria reservados por la gestión de vSAN, independientemente del tamaño de disco, que equivale a 7 GB o equivale a 0 GB si no es VSAN	| GB |  7	| 0 |

## Consideraciones sobre la instalación de IBM Cloud Private Hosted

Obtenga la licencia necesaria antes de instalar el servicio {{site.data.keyword.cloud_notm}} Private Hosted. Le recomendamos que se asegure de que la licencia no solo puede dar soporte al despliegue inicial de {{site.data.keyword.cloud_notm}} Private Hosted, sino también a una futura expansión de {{site.data.keyword.cloud_notm}} Private Hosted en su infraestructura.

## Consideraciones sobre la eliminación de IBM Cloud Private Hosted

* {{site.data.keyword.cloud_notm}} solo suprime las máquinas virtuales (VM) desplegadas durante la instalación inicial del servicio {{site.data.keyword.cloud_notm}} Private Hosted. Los nodos que se desplieguen después de la instalación no se eliminará.
* {{site.data.keyword.cloud_notm}} suprimirá VXLAN, DLR y la pasarela de extremo creada durante el despliegue inicial del servicio {{site.data.keyword.cloud_notm}} Private Hosted. Las VM que haya desplegado en VXLAN perderán la conectividad cuando comience el proceso de eliminación del servicio {{site.data.keyword.cloud_notm}} Private Hosted.

### Enlaces relacionados

* [Solicitud de IBM Cloud Private Hosted](../services/icp_ordering.html)
* [IBM Cloud Private Hosted](https://www.ibm.com/developerworks/community/files/form/anonymous/api/library/eafb752c-55f3-4b07-9b20-b61c8ea980b9/document/af203658-30c0-40ba-81b5-46c393fb723f/media/IBM_Cloud_Private_Hosted-IBM_Cloud.pdf) (descarga de PDF)
* [Apertura de una incidencia para IBM Cloud privado](https://www.ibm.com/mysupport/s/?language=en_US)
