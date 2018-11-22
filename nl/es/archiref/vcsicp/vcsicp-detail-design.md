---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-06"

---

# Diseño detallado

## Componentes de los servicios comunes
Los servicios comunes proporcionan los servicios que utilizan otros servicios en la plataforma de gestión de nube. Esto incluye servicios de identidad y acceso, servicios de nombres de dominio, servicios NTP.

Figura 1. Servicios comunes de ICP

![Servicios comunes de ICP](vcsicp-icp-commonservices.svg)

### Servicios de identidad y acceso
Como parte de la automatización de VCS, se utiliza un Microsoft Active Directory (AD) para la gestión de identidades. Se despliega una sola instancia de servidor virtual (VSI) AD. El vCenter se configura de modo que utilice la autenticación de MS AD y el ICP también se puede configurar para la autenticación LDAP.

###	Servicios de nombres de dominio
El despliegue de VCS utiliza las VSI de Microsoft Active Directory (AD) desplegadas como servidores DNS para la instancia. Todos los componentes desplegados (vCenter, PSC, NSX y hosts de ESXi) se configuran de modo que apunten a MS AD como su DNS predeterminado.

###	Servicios NTP
El despliegue de VCS utiliza los servidores NTP de la infraestructura de {{site.data.keyword.cloud}}. Todos los componentes desplegados se configuran para utilizar estos servidores NTP. El hecho de que todos los componentes del diseño utilicen los mismos servidores NTP resulta crítico para que los certificados y la autenticación de MS AD funcionen correctamente

## Redes

### Redes NSX-V

NSX-V se ha diseñado de modo que una sola plataforma de gestor NSX-V esté enlazada a una sola instancia de servidor de vCenter. Proporciona servicios de red a las aplicaciones que se ejecutan dentro de un entorno de vSphere.

Mediante el sistema de red NSX-V que se incluye en el despliegue de VCS, podemos desplegar ICP en una red de superposición VXLAN.

ICP se despliega con la pila de red Calico predeterminada para Kubernetes, que proporciona aislamiento de red dentro del clúster.

Figura 2. ICP con red NSX-V

![ICP con red NSX-V](vcsicp-nsxv-networking.svg)

Para obtener más información, consulte [Guía de redes de vCenter Server](../vcsnsxt/vcsnsxt-intro.html).

### Redes NSX-T

NSX-T se ha diseñado de modo que una sola plataforma de red se pueda conectar a cualquier tipo de aplicación, ya sea máquina virtual o basada en contenedor, que se ejecute dentro o fuera de un entorno de vSphere.

ICP proporciona una opción para sustituir la red Calico por una instancia NSX-T, proporcionando una única ubicación para gestionar la red y la seguridad.

Figura 3. ICP con red NSX-T

![ICP con red NSX-T](vcsicp-icp-nsxt-networking.svg)

### Enlaces relacionados

* [Visión general de VCS con el paquete híbrido (Hybridity)](../vcs/vcs-hybridity-intro.html)
