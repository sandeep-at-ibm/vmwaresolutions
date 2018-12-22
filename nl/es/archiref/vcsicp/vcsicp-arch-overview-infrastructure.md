---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-15"

---


# Redes e infraestructura de IBM Cloud

## Direccionamiento y reenvío virtual (VRF)

Puede configurar cuentas de {{site.data.keyword.cloud}} como cuentas de VRF para proporcionar funciones similares a la distribución de VLAN, habilitando así el direccionamiento automático entre los bloques de IP de subred. Todas las cuentas con las conexiones de Direct-Link deben convertirse a, o crearse como, una cuenta de VRF.

## Direct Link

{{site.data.keyword.cloud_notm}} Direct Link Connect ofrece acceso privado a su infraestructura de {{site.data.keyword.cloud_notm}} y a cualquier otra nube enlazada a su proveedor de servicios de red, a través de su centro de datos de IBM Cloud local. Esta opción es perfecta para crear conectividad multinube en un entorno único. Se utiliza una topología de ancho de banda compartida para conectar clientes a la red de {{site.data.keyword.cloud_notm}} Private (ICP). Al igual que sucede con todos los productos de Direct-Link, puede añadir direccionamiento global, que permite el tráfico de red privada a todas las ubicaciones de {{site.data.keyword.cloud_notm}}.

## Redes privadas virtuales

### strongSwan VPN

El servicio strongSwan IPSec VPN ofrece un canal de comunicación seguro de extremo a extremo sobre internet que se basa en la suite de protocolos Internet Protocol Security (IPSec) estándar del sector.

### Hybridity (HCX)

vCenter Server on {{site.data.keyword.cloud_notm}} con el paquete híbrido (Hybridity) permite ampliar fácilmente las redes de centros de datos locales en {{site.data.keyword.cloud_notm}}, lo que permite migrar las máquinas virtuales (VM) de {{site.data.keyword.cloud_notm}} y al mismo sin realizar ninguna conversión ni cambio.

## Estructura física

La infraestructura física necesaria para desplegar una instancia de producción de ICP en un clúster de VMware vCenter Server on {{site.data.keyword.cloud_notm}} requiere la siguiente especificación mínima.

Tabla 1. Especificación de vCenter Server para ICP

| Despliegue de NFS |  Despliegue de vSAN |
:--|:----:|:----:
Número de servidores  |  3 |  4
CPU | 28 núcleos 2,2 GHz | 28 núcleos 2,2 GHz
Memoria | 384 GB | 384 GB
Almacenamiento | 2000 GB 2IOPS/GB de gestión, 2000 GB 4IOPS/GB de carga de trabajo, 4000 GB 4IOPS/GB de ICP | Mín 960-GB SSD x 2

Además de los requisitos de hardware de ICP, debe crear volúmenes persistentes en el entorno ICP para almacenar la base de datos de Cloud Automation Manager (CAM) y los datos de registro. Aunque CAM da soporte a todos los tipos de volúmenes persistentes a los que da soporte ICP, las dos configuraciones de almacenamiento recomendadas para CAM son NFS y GlusterFS.

## Estructura virtual

Figura 1. Estructura física del despliegue de vCenter Server e ICP
![Estructura física del despliegue de VCS e ICP](vcsicp-phy-ics-icp-deployment.svg)

Dentro de la instancia de vCenter Server, la instancia de ICP se despliega con NSX Edge Services Gateway (ESG) y Distributed Logical Router (DLR) dedicados. La instalación de ICP se carga en la subred VXLAN definida en los componentes anteriores.

El ESG se configura con una regla NAT de origen (SNAT) para permitir el tráfico de salida, permitiendo la conectividad a internet para descargar los requisitos previos de ICP y la conectividad con GitHub y Docker, o se puede utilizar un proxy web para proporcionar la conectividad a internet. El ESG también se configura para proporcionar acceso a los servicios DNS y NTP.

El ESG también se configura con una regla NAT de destino (DNAT) a las direcciones IP virtuales de ICP Master/Proxy desde la red de {{site.data.keyword.cloud_notm}} 10.x a través del entorno VXLAN.

### Enlaces relacionados

* [Visión general de vCenter Server on {{site.data.keyword.cloud_notm}} con el paquete híbrido (Hybridity)](../vcs/vcs-hybridity-intro.html)
