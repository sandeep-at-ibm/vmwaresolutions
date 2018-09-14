---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-13"

---

# Acerca del almacenamiento adjunto para vCenter Server

El almacenamiento adjunto es una extensión de VMware vCenter Server en la oferta {{site.data.keyword.cloud}}. La arquitectura de soluciones de almacenamiento adjunto para VMware vCenter Server en {{site.data.keyword.cloud_notm}} detalla los componentes de la solución y la configuración de alto nivel de cada componente del diseño.

Para obtener más información sobre el diseño de vCenter Server, consulte [Visión general de la solución](../solution/solution_overview.html).

## Principales ventajas del almacenamiento adjunto para vCenter Server

Aunque el almacenamiento adjunto no es un requisito previo para los entornos VMware, el hecho de utilizarlo como dispositivo de almacenamiento compartido ofrece muchas ventajas a los usuarios para las operaciones de TI. La utilización de dispositivos de almacenamiento compartido puede ayudarle a conseguir una alta disponibilidad, un planificador de recursos distribuidos, un uso eficiente de la capacidad de almacenamiento y una gestión simplificada mediante la habilitación de las funciones de vSphere que se describen en la tabla siguiente.

Tabla 1. Descripción de las funciones del almacenamiento adjunto para el servidor de vCenter

| Función | Descripción |
|:------- |:----------- |
| Planificador de recursos distribuidos de vSphere y agrupaciones de recursos | Esta característica permite abstraer y gestionar los recursos de forma flexible mediante el equilibrio de la carga y la ubicación de máquinas virtuales (VM). Las agrupaciones de recursos se pueden agrupar en jerarquías y se pueden utilizar para dividir de forma jerárquica los recursos de CPU y de memoria disponibles. |
| Alta disponibilidad de vSphere | Esta característica proporciona alta disponibilidad para máquinas virtuales (agrupándolas) y para los hosts que residen en un clúster. Se supervisan los hosts del clúster. Si se produce un error, las máquinas virtuales de un host anómalo se reinician en hosts alternativos. |
| Clústeres de almacén de datos de vSphere | Esta característica proporciona una colección de almacenes de datos con recursos compartidos y una interfaz de gestión compartida. |
| Tolerancia a errores de vSphere | Esta característica proporciona una disponibilidad continua a las máquinas virtuales, eliminando el tiempo de inactividad y las interrupciones, incluso si se produce una anomalía en todo un host. |

### Enlaces relacionados

* [Visión general de la solución](../solution/solution_overview.html)
