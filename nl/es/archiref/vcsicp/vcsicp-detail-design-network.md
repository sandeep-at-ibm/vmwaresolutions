---

copyright:

  years:  2016, 2019

lastupdated: "2018-01-14"

---

# Acceso y flujos de red

## Acceso a la aplicación de contenedor - IBM Cloud Private

Estas son las tres formas principales de obtener tráfico externo y acceso a las aplicaciones de clúster de Kubernetes:

- NodePort
- LoadBalancer
- Ingress

### NodePort - IBM Cloud Private

Los Nodeports constituyen una manera sencilla de exponer el acceso externo a una carga de trabajo para el desarrollo inicial y las pruebas, pero no se recomienda para la producción. Se recomienda utilizar Ingress o el equilibrador de carga.

### LoadBalancer - IBM Cloud Private

Actualmente, la plataforma {{site.data.keyword.icpfull_notm}} da soporte a un equilibrador de carga externo para la carga de trabajo de aplicaciones.

### Ingress - IBM Cloud Private

Ingress es una colección de reglas que permiten a las conexiones de entrada acceder a los servicios de clúster. Se puede configurar de modo que ofrezca a los servicios los URL accesibles externamente, equilibre la carga del tráfico, termine SSL, ofrezca servicios de host virtual basado en nombres y más.  El nodo proxy de la infraestructura {{site.data.keyword.icpfull_notm}} realiza esta función.

## Acceso a la aplicación de contenedor - servicio IBM Cloud Kubernetes

Estas son las tres formas principales de obtener tráfico externo y acceso a las aplicaciones de clúster de Kubernetes:

- NodePort
- LoadBalancer
- Ingress

### NodePort - Servicio IBM Cloud Kubernetes

Los Nodeports constituyen una manera sencilla de exponer el acceso externo a una carga de trabajo para el desarrollo inicial y las pruebas, pero no se recomienda para la producción. Se recomienda utilizar Ingress o el equilibrador de carga.

### LoadBalancer - Servicio IBM Cloud Kubernetes

Todos los clústeres {{site.data.keyword.containerlong_notm}} se suministran con un equilibrador de carga de aplicación (ALB) público o privado. El ALB utiliza un punto de entrada público o privado seguro y único para direccionar las solicitudes entrantes a sus aplicaciones.

### Ingress - Servicio IBM Cloud Kubernetes

Ingress es una colección de reglas que permiten a las conexiones de entrada acceder a los servicios de clúster. Se puede configurar de modo que ofrezca a los servicios los URL accesibles externamente, equilibre la carga del tráfico, termine SSL, ofrezca servicios de host virtual basado en nombres y más.

## Flujos de tráfico

A continuación se describen los siguientes flujos de tráfico:

- De usuario externo en internet a nivel web alojado en un contenedor en {{site.data.keyword.icpfull_notm}}.
- De nivel web alojado en un contenedor en {{site.data.keyword.icpfull_notm}} a nivel de base de datos alojado en una máquina virtual (VM) en VMware vCenter Server on {{site.data.keyword.cloud_notm}}.
- De usuario de empresa en el acceso de red corporativa a una VM en vCenter Server.

### De usuario externo en internet a nivel web alojado en un contenedor en IBM Cloud Private

1. El usuario externo realiza una solicitud al nivel web utilizando el URL.
2.	Se utiliza DNS para determinar la dirección IP. Esta dirección IP es una dirección pública de {{site.data.keyword.cloud_notm}} en una subred portátil que se asigna a la instancia de vCenter Server.
3.	La red pública reenvía automáticamente la solicitud al host vSphere ESXi que aloja el ESG.
4.	El ESG reenvía la solicitud a la dirección IP del clúster interno y al número de puerto del servicio ALB o Ingress. El paquete IP se encapsula en una trama VXLAN si el ESG y el ALB o el servicio Ingress se encuentran en distintos hosts de ESXi de vSphere. Solo se puede acceder a esta dirección IP de clúster interno dentro del clúster.
5.	Dentro del nodo trabajador, kube-proxy direcciona la solicitud al ALB o al servicio Ingress.
6.	Si la aplicación está en el mismo nodo trabajador, se utilizan iptables para determinar qué interfaz interna se utiliza para reenviar la solicitud. Si la aplicación está en otro nodo trabajador, Calico vRouter la dirige al nodo trabajador aplicable, utilizando la encapsulación de tipo IP en IP. El paquete IP en IP se encapsula en una trama VXLAN para su transporte al host vSphere ESXi donde se encuentra el nodo trabajador.

### De nivel web alojado en un contenedor en IBM Cloud Private a nivel de base de datos alojado en una VM en vCenter Server

El modo en que se llenan las tablas de rutas en el ESG y en los vRouters depende del método de integración. Consulte el apartado sobre integración de {{site.data.keyword.icpfull_notm}} y vCenter Server.

1.	El nivel web que se ejecuta en un contenedor en {{site.data.keyword.icpfull_notm}} realiza una solicitud a una base de datos que se ejecuta en una VM en la misma instancia de vCenter Server.
2.	Se utiliza DNS para resolver la solicitud destinada a la dirección IP de la base de datos.
3.	El contenedor envía la solicitud a Calico vRouter.
4.	El vRouter tiene su tabla de rutas, que contiene los rangos de direcciones IP alojadas en la instancia de vCenter Server.
5.	El vRouter reenvía la solicitud, pero utiliza SNAT para cambiar la dirección IP de origen de la dirección IP del pod a la dirección IP del nodo de trabajador.
6.	El nodo trabajador que aloja el vRouter envía la solicitud al ESG.
7.	El ESG la reenvía al DLR.
8.	El DLR coloca la solicitud en el VXLAN necesario.
9.	La VM de base de datos recibe la solicitud.

### 	De usuario de empresa en el acceso de red corporativa a una VM en vCenter Server

1.	Un usuario de la empresa conectado a la red interna de la empresa realiza una solicitud de un recurso en una VM alojada en vCenter Server.
2.	Se utiliza DNS para determinar la dirección IP de la VM. Esta dirección IP se encuentra en una red que se ha extendido a {{site.data.keyword.cloud_notm}}.
3.	El direccionador local direcciona el tráfico al host vSphere que aloja el concentrador L2.
4.	El concentrador L2 encapsula la solicitud en un túnel seguro y la reenvía al concentrador L2 remoto alojado en {{site.data.keyword.cloud_notm}} utilizando la dirección IP de subred portátil privada asignada al dispositivo, mediante el direccionador local.
5.	La ruta local busca en su tabla de direccionamiento y detecta que la dirección IP correspondiente al concentrador L2 remoto se debe enviar a la interfaz WAN y la reenvía a través de la WAN, mediante el direccionador XCR de {{site.data.keyword.cloud_notm}}, vía BCR.
6.	El concentrador L2 recibe la solicitud y la coloca en la VXLAN que aloja la red extendida.
7.	La VM recibe la solicitud.

## Red de acceso público

De forma predeterminada, {{site.data.keyword.icpfull_notm}} y CAM necesitan conectividad a internet para recuperar imágenes de Docker, diagramas de Helm, plantillas de Terraform y gestores de paquetes del sistema operativo.
En los releases más recientes, se ofrece soporte para instalaciones basadas en proxy para instalaciones que no están conectadas directamente a internet y tienen opciones para instalar en modalidad fuera de línea.

###	Cortafuegos NSX

El cortafuegos {{site.data.keyword.icpfull_notm}} NSX Edge está configurado con reglas que permiten:
*	Habilitar el acceso de redes VXLAN al acceso público.
*	Habilitar el acceso de redes VXLAN al acceso de red privada de {{site.data.keyword.cloud_notm}}.
*	Habilitar el acceso de red privada de {{site.data.keyword.cloud_notm}} a las redes VXLAN.

### NSX NAT

{{site.data.keyword.icpfull_notm}} NSX NAT está configurado con las siguientes NAT:
*	SNAT para el acceso de redes VXLAN a acceso público.
*	SNAT para el acceso de redes VXLAN a acceso a red privada de {{site.data.keyword.cloud_notm}}.
*	DNAT para vIPs de clúster {{site.data.keyword.icpfull_notm}}.

### Enlaces relacionados

* [Visión general de vCenter Server on {{site.data.keyword.cloud_notm}} con el paquete híbrido (Hybridity)](../vcs/vcs-hybridity-intro.html)
