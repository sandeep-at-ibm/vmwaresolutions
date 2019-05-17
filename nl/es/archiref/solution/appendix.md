---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-13"

subcollection: vmware-solutions


---

# Gráfico de comparación para las ediciones de componentes de VMware
{: #solution-appendix}

## Comparación de la edición VMware NSX
{: #solution-appendix-nsx-editions}

Dentro de este diseño, hay varios componentes que requieren licencia. Esta información captura las licencias mínimas necesarias para que el entorno funcione correctamente.

Tabla 1. Requisitos de licencia

Componente | Finalidad | Licencia
----------|---------|-------------
**vSphere** | Virtualización de cálculo | vSphere 6.7 Enterprise Plus
**vCenter Server** | Gestión de la infraestructura | vCenter Server 6.7 Standard
**NSX** | Virtualización de red | NSX Base for Service Providers 6.4
**vSAN** | Virtualización de almacenamiento | vSAN 6.6 Advanced  

La edición NSX Base for Service Providers solo está disponible para proveedores de servicios a través de VMware vCloud Air Network (vCAN). Las características de esta edición se pueden encontrar en la tabla siguiente.
{:note}

Tabla 2. Gráfico de comparación de ediciones de VMware NSX

| Característica NSX                                   | Base | Advanced | Enterprise |
|-----------------------------------------------|------|----------|------------|
| Conmutación y direccionamiento distribuido             | •    | •        | •          |
| Cortafuegos NSX Edge                             | •    | •        | •          |
| NAT                                           | •    | •        | •          |
| Equilibrio de carga de NSX Edge                       | •    | •        | •          |
| VPN (IPsec)                                   | •    | •        | •          |
| VPN (SSL)                                     | •    | •        | •          |
| Automatización guiada por API                         | •    | •        | •          |
| Integración con vRealize y OpenStack\*     | •    | •        | •          |
| Automatización de las políticas de seguridad con vRealize |      | •        | •          |
| Puente de SW L2 con el entorno físico        |      | •        | •          |
| Direccionamiento dinámico con ECMP (activo-activo)     |      | •        | •          |
| Cortafuegos distribuido                       |      | •        | •          |
| Integración con Active Directory             |      | •        | •          |
| Supervisor de la actividad del servidor                    |      | •        | •          |
| Inserción de servicio (integración de terceros)     |      | •        | •          |
| Equilibrio de carga distribuido                    |      |          | •          |
| NSX de Cross vCenter                             |      |          | •          |
| Optimizaciones de NSX de varios sitios                  |      |          | •          |
| Pasarela remota                                |      |          | •          |
| Integración con HW VTEP                     |      |          | •          |
\Integración solo de *L2, L3 y NSX Edge. No hay consumo de grupos de seguridad

## Comparación de ediciones de VMware vSAN
{: #solution-appendix-vsan-editions}

En la tabla siguiente se enumeran las funciones disponibles para las ediciones **Advanced** y **Enterprise** de VMware vSAN a las que da soporte la solución.

Tabla 3. Gráfico de comparación de ediciones de VMware vSAN

| Característica de vSAN                                    | Advanced | Enterprise |
|-------------------------------------------------|----------|------------|
| Gestión basada en políticas de almacenamiento                 | •        | •          |
| Caché de lectura/escritura de Flash                        | •        | •          |
| RAID distribuido                                | •        | •          |
| Conmutador distribuido virtual                      | •        | •          |
| Conocimiento del bastidor                                  | •        | •          |
| Réplica de vSphere                             | •        | •          |
| Suma de comprobación de software                               | •        | •          |
| Hardware All-Flash                              | •        | •          |
| Servicio de destino iSCSI                            | •        | •          |
| Límite de IOPS                                      | •        | •          |
| Deduplicación y compresión                   | •        | •          |
| Codificación de borrado RAID-5/6                         | •        | •          |
| Cifrado de datos en reposo                         |          | •          |
| Clúster extendido con protección de anomalía local |          | •          |

## Enlaces relacionados
{: #solution-appendix-related}

* [Visión general de la solución](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_overview)
* [Visión general del diseño](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-design_overview)
* [Copia de seguridad de los componentes](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_backingup)
