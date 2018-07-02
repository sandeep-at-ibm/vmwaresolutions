---

copyright:

  years:  2016, 2018

lastupdated: "2017-12-29"

---

# Resolución de problemas asistida

## Problema

En algunas situaciones, puede producirse un problema más complicado para el que los archivos de registro no resulten suficientes para determinar la causa raíz del problema y proporcionar una solución.

## Solución

Para solucionar y resolver este tipo de problemas, el equipo de soporte de {{site.data.keyword.vmwaresolutions_full}} necesita acceder a la máquina virtual (VM) de gestión de {{site.data.keyword.cloud_notm}}. Esta VM de gestión, denominada IBM CloudDriver, constituye la principal interfaz que se utiliza para gestionar las instancias de VMware Cloud Foundation y las instancias de VMware vCenter Server desplegadas.

Por motivos de seguridad, el acceso a IBM CloudDriver está restringido. El equipo de soporte de {{site.data.keyword.vmwaresolutions_short}} solicitará aprobación al cliente y, una vez obtenida, el equipo podrá acceder al componente de CloudDriver mediante un servidor virtual de la infraestructura {{site.data.keyword.cloud_notm}}. Este servidor constituye un puente en el entorno sobre la red pública FCR (Frontend Customer Router) de la infraestructura de {{site.data.keyword.cloud_notm}}.

A continuación, el equipo de soporte de {{site.data.keyword.vmwaresolutions_short}} utiliza la clave {{site.data.keyword.slapi_short}} de la infraestructura de {{site.data.keyword.cloud_notm}} que se suministró durante el pedido y configuración de la instancia (o, si es necesario, la clave actualizada que proporciona el cliente) para desplegar un servidor virtual de la infraestructura {{site.data.keyword.cloud_notm}} cada hora.

Se factura a esta cuenta de usuario el uso de las herramientas de IBM CloudBuilder para la resolución de problemas. Una vez finalizado el proceso de depuración y resolución, el componente IBM CloudBuilder se libera.

El servidor virtual de la infraestructura de {{site.data.keyword.cloud_notm}} que se ha utilizado para la resolución de problemas se despliega con las siguientes especificaciones:

* Se utiliza una VSI (instancia de servicio virtual) de nodo público CentOS 7 con 1 CPU y 1 GB de RAM.
* La VSI se despliega en el mismo centro de datos en la misma VLAN pública y privada primaria en la que se encuentra la instancia.
* Se utiliza un script posterior a la instalación con el despliegue de VSI para definir las reglas de cortafuegos que permiten las conexiones SSH de entrada procedentes de un conjunto específico de direcciones IP que son propiedad del equipo de soporte de {{site.data.keyword.vmwaresolutions_short}} y que este utiliza.
* El sistema de inicio del soporte que utiliza estas direcciones IP se ejecuta en una VM de la infraestructura de {{site.data.keyword.cloud_notm}} a la que solo se puede acceder a través de una red de la infraestructura de {{site.data.keyword.cloud_notm}} privada y que está protegida con un par de sistemas Vyatta de la infraestructura {{site.data.keyword.cloud_notm}} de HA (alta disponibilidad).
* Se utilizan herramientas de seguridad de IBM, como QRadar®, Nessus e IBM BigFix®, para comprobar que no haya amenazas de seguridad en el sistema de inicio del soporte.
