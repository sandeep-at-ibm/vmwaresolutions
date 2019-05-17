---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

subcollection: vmware-solutions


---

# Distribuido completamente
{: #caveonix-fully}

Se añaden máquinas virtuales base (VM) adicionales y máquinas virtuales de escalado de acuerdo con el número de activos y requisitos de retención de datos.

Tabla 1. Base - interfaz de usuario

|Parámetro	|Valor|
|---|---|
|Tipo	|Base|
|Cantidad de VM	|2|
|vCPU	|2|
|RAM	|6 GB|
|Disco	|60 GB|
|SO	|CentOS 7|
|Componentes de aplicación instalados	|Interfaz de usuario|

Tabla 2. Base - aplicaciones y plugins

|Parámetro	|Valor|
|---|---|
|Tipo	|Base|
|Cantidad de VM	|2|
|vCPU	|8|
|RAM	|16 GB|
|Disco	|500 GB|
|SO	|CentOS 7|
|Componentes de aplicación instalados	|App, Plug-ins|

Tabla 3. Base - recopilador central

|Parámetro	|Valor |
|---|---|
|Tipo	|Base |
|Cantidad de VM	|3 |
|vCPU	|8 |
|RAM	|16 GB |
|Disco	|500 GB |
|SO	|CentOS 7 |
|Componentes de aplicación instalados	|Recopilador central (clúster) |

Tabla 4. Base - base de datos relacional

|Parámetro	|Valor |
|---|---|
|Tipo	|Base |
|Cantidad de VM	|2 |
|vCPU	|8 |
|RAM	|16 GB |
|Disco	|1 TB |
|SO	C|entOS 7 |
|Componentes de aplicación instalados	|Almacén de datos relacional (primario/secundario) |

Tabla 5. Base - almacén de datos de mensajería

|Parámetro	|Valor |
|---|---|
|Tipo	|Base |
|Cantidad de VM	|3 |
|vCPU	|8 |
|RAM	|16 GB |
|Disco	|1 TB |
|SO	|CentOS 7 |
|Componentes de aplicación instalados	|Almacén de datos de mensajería (clúster) |

Tabla 6. Base - almacén de datos de índice (nodos maestros)

|Parámetro	|Valor |
|---|---|
|Tipo	|Base |
|Cantidad de VM	|3 |
|vCPU	|8 |
|RAM	|16 GB |
|Disco	|1 TB |
|SO	|CentOS 7 |
|Componentes de aplicación instalados	|Almacén de datos de índice (Nodos maestros) |

Tabla 7. Base de datos - almacén de datos de índice (nodos de datos)

|Parámetro	|Valor |
|---|---|
|Tipo	|Base |
|Cantidad de VM	|5 |
|vCPU	|8 |
|RAM	|16 GB |
|Disco	|4 TB |
|SO	|CentOS 7 |
|Componentes de aplicación instalados	|Almacén de datos de índice (Nodos de datos) |

Los detalles de la VM de escalado se describen en la tabla siguiente.

Tabla 8. Escalado - nodos de datos

|Parámetro	|Valor |
|---|---|
|Tipo	|Escalado (Scale-out) |
|Cantidad de VM 28 |
|vCPU	|8 |
|RAM	|16 GB |
|Disco	|4 TB |
|SO	|CentOS 7 |
|Componentes de aplicación instalados	|Nodos de datos (escalado) |

Los detalles de la VM del recopilador remoto se muestran en la tabla siguiente.

Tabla 9. Recopilador remoto

|Parámetro	|Valor |
|---|---|
|Cantidad de VM	|Según sea necesario |
|vCPU	|8 |
|RAM	|8 GB |
|Disco	|1 TB |
|SO	|CentOS 7 |
|Componentes de aplicación instalados	|Recopilador remoto |

## Enlaces relacionados
{: #caveonix-fully-related}

* [VMware vCenter Server on {{site.data.keyword.cloud}} con el paquete híbrido (Hybridity)](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
