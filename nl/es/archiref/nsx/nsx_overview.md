---

copyright:

  years:  2016, 2019

lastupdated: "2018-11-13"

---

# Acerca de NSX Edge Services Gateway

La solución VMware NSX Edge Services Gateway (ESG) es una extensión de VMware Cloud Foundation en {{site.data.keyword.cloud}} y las ofertas de vCenter Server en {{site.data.keyword.cloud_notm}} actualmente disponibles en el {{site.data.keyword.cloud_notm}}. La arquitectura de la solución para Cloud Foundation y vCenter Server detalla los componentes de la solución y la configuración de alto nivel de cada componente en el diseño.

Para obtener más información sobre el diseño de Cloud Foundation y vCenter Server, consulte [Visión general de la solución](../solution/solution_overview.html).

## Visión general de NSX Edge Services Gateway

NSX Edge Services Gateway conecta redes aisladas auxiliares a redes compartidas (de enlace ascendente) proporcionando servicios de pasarela comunes tales como Dynamic Host Configuration Protocol (DHCP), Red privada virtual (VPN), Network Address Translation (NAT), direccionamiento dinámico y equilibrio de carga. Los despliegues comunes de NSX Edge incluyen zonas desmilitarizadas (DMZ), Extranets de VPN y entornos de nube de varios arrendatarios en los que NSX Edge crea límites virtuales para cada arrendatario, carga de trabajo o componente de gestión. Están disponibles las características siguientes dentro de NSX Edge Service Gateway.

Tabla 1. Características disponibles con la pasarela NSX Edge Service

| Característica | Descripción |
|:------- |:----------- |
| Direccionamiento de servicios NSX Edge | Proporciona la información de reenvío necesaria entre los dominios de difusión de capa 2, permitiendo así disminuir los dominios de difusión de capa 2 y mejorar la eficiencia y la escala de la red. NSX amplía esta inteligencia a dónde residen las cargas de trabajo para realizar el direccionamiento de este a oeste. Esto permite una comunicación más directa entre máquinas virtuales sin la necesidad de invertir tiempo y dinero en ampliar saltos. Al mismo tiempo, NSX también proporciona entrada/salida de conectividad norte-sur, permitiendo a los arrendatarios acceder a redes públicas. |
| Cortafuegos | Las reglas admitidas del cortafuegos incluyen la configuración de 5 tuplas IP con IP y rangos de puertos para la inspección con estado para todos los protocolos. |
| NAT | Proporciona controles separados para las direcciones IP de origen y destino y conversión de puerto. |
| DHCP | Proporciona la configuración de las agrupaciones de IP, las pasarelas, los servidores DNS y los dominios de búsqueda. |
| VPN de sitio a sitio | Utiliza los valores de protocolo IPSec estandarizados para interoperar con todos los proveedores de VPN principales. |
| L2VPN | Estira las redes L2 entre las topologías L3. |
| SSL VPN-Plus |  SSL VPN-Plus permite a los usuarios remotos conectarse de forma segura a las redes privadas detrás de una pasarela NSX Edge. |
| Equilibrio de carga | Proporciona direcciones IP virtuales y grupos de servidores simples y dinámicamente configurables. |
| Alta disponibilidad | Garantiza un NSX Edge activo en la red en caso de que la máquina virtual NSX Edge primaria no esté disponible. |

### Enlaces relacionados

* [Visión general de la solución](../solution/solution_overview.html)
