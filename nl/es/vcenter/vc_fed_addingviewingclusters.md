---

copyright:

  years:  2016, 2018

lastupdated: "2018-04-05"

---

# Visualización del clúster predeterminado de una instancia de VMware Federal

Vea los detalles del clúster predeterminado de las instancias de VMware Federal que ha solicitado.

## Resumen del clúster predeterminado de una instancia de VMware Federal

Dispone de los siguientes detalles resumidos del clúster predeterminado de una instancia de VMware Federal de su entorno.

Tabla 1. Descripciones del resumen de un clúster de VMware Federal

| Elemento        | Descripción       |  
|:------------- |:------------- |
| Nombre | El nombre del clúster. |
| Servidores ESXi | El número de servidores ESXi del clúster. |  
| CPU | La especificación de CPU de los servidores ESXi del clúster. |  
| Discos vSAN personalizados | El número de discos vSAN del clúster, incluido el tipo de disco y su capacidad. |
| Memoria | El tamaño total de la memoria de los servidores ESXi del clúster. |  
| Ubicación del centro de datos | El {{site.data.keyword.CloudDataCent_notm}} en el que se aloja el clúster. |  
| Pod | El pod en el que se ha desplegado el clúster. |
| Estado | El estado del clúster.|

Tabla 2. Descripciones de los estados de un clúster de VMware Federal

| Estado        | Descripción       |
|:------------- |:------------- |
| Inicializando | El clúster se está creando y configurando. |
| Modificando | El clúster se está modificando. |
| Listo para su uso | El clúster está listo para ser utilizado. |

## Detalles del clúster predeterminado de una instancia de VMware Federal

Puede abrir el clúster predeterminado, agrupado como **cluster1** al solicitar la instancia, para ver el servidor ESXi, el almacenamiento NFS y los detalles de la licencia vSAN del clúster.

Además, puede abrir el clúster predeterminado, para gestionar los servidores ESXi para mejorar la asignación de recursos y la alta disponibilidad. Para obtener más información, consulte [Ampliación y reducción de la capacidad para instancias de VMware Federal](vc_fed_addingremovingservers.html).

Tabla 3. Descripciones del resumen del servidor ESXi

| Elemento        | Descripción       |  
|:------------- |:------------- |
| Nombre | El nombre del servidor ESXi en el formato siguiente:<br><br>`<host_prefix><n>.<subdomain_label>.<root_domain>`<br><br>donde:<br><br>`host_prefix` es el prefijo del nombre de host, `n` es la secuencia del servidor, `subdomain_label`
es la etiqueta del subdominio y `root_domain` es el nombre del dominio raíz |
| Versión | La versión del servidor ESXi. |  
| Credenciales | El nombre de usuario y la contraseña para acceder al servidor ESXi. |  
| IP privada | La dirección IP privada del servidor ESXi. |  
| Estado | El estado del servidor ESXi.|

Tabla 4. Descripciones de los estados de un servidor ESXi

| Estado        | Descripción       |
|:------------- |:------------- |
| Añadido | El servidor ESXi se ha añadido y está listo para ser utilizado. |
| Añadiendo | El servidor ESXi se está añadiendo. |
| Suprimiendo | El servidor ESXi se está suprimiendo. |

Tabla 5. Descripciones del resumen de almacenamiento

**Nota:** En esta tabla solo se muestra información sobre los clústeres de almacenamiento compartido NFS.

| Elemento        | Descripción       |  
|:------------- |:------------- |
| Nombre | El nombre de almacén de datos. |
| Tamaño | La capacidad de almacenamiento. |  
| IOPS/GB | El nivel de rendimiento del almacenamiento. |  
| Protocolo NFS | La versión NFS del almacenamiento. |  

Tabla 6. Descripciones del resumen de licencia

**Nota:** En esta tabla solo se muestra información sobre los clústeres vSAN.

| Elemento        | Descripción       |  
|:------------- |:------------- |
| Licencia | El componente de la licencia. |
| Tipo de pedido | Especifica si es una licencia proporcionada por el usuario o adquirida.<br><br>**Nota:** las licencias proporcionadas por el usuario no están disponibles para las instancias de VMware Federal. |  
| Edición de licencia | La versión y la edición de la licencia. |  
| Clave de licencia | La clave de licencia de una licencia proporcionada por el usuario. <br><br>**Nota:** las licencias proporcionadas por el usuario no están disponibles para las instancias de VMware Federal. |
| Capacidad total (CPU) | La cantidad total de capacidad de almacenamiento. |
| Capacidad libre (CPU) | La cantidad de capacidad de almacenamiento disponible. |

## Procedimiento

1. Pulse **Recursos** en el panel de navegación izquierdo.
2. En la tabla **Instancias de vCenter Server**, pulse el nombre de la instancia.
3. Pulse el separador **Infraestructura** y revise el resumen del clúster predeterminado.
4. En la tabla **CLÚSTERES**, pulse **cluster1** y revise los detalles del clúster.

**Importante**: no puede cambiar el nombre del clúster. Si se cambia el nombre del clúster, es posible que las operaciones de adición o eliminación de servidores ESXi en el clúster fallen.

## Enlaces relacionados

* [Visualización de instancias de VMware Federal](vc_fed_viewinginstance.html)
* [Ampliación y reducción de la capacidad para instancias de VMware Federal](vc_fed_addingremovingservers.html)
