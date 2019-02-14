---

copyright:

  years:  2016, 2019

lastupdated: "2018-12-14"

---
# Requisitos de acceso a puertos de HCX on IBM Cloud

HCX debe cruzar internet público y líneas privadas, y conectar con los componentes del centro de datos, como redes, conmutadores y grupos de puertos.

en la tabla siguiente encontrará los puertos que deben estar abiertos para que los dispositivos virtuales de Hybrid Cloud Services se puedan instalar correctamente. Tanto el entorno de vSphere como el entorno de IBM Cloud deben permitir la sincronización de reloj de Network Time Protocol (NTP) entre los dispositivos locales de vSphere y los dispositivos de IBM Cloud. El puerto UDP 123 debe resultar accesible para los dispositivos virtuales y las redes de Hybrid Cloud Services. Se pueden especificar servidores NTP instalados cuando se instalada el dispositivo Hybrid Cloud Services.

Tabla 1. Requisitos de acceso a puertos

| Origen | Destino       | Puerto | Protocolo | Finalidad         | Servicios |
|--------|--------------|------|----------|-----------------|----------|
| HCX    | DNS de cliente | 53   | TCP/UDP  | Resolución de nombres | DNS      |
| HCX    | NSX LB en IBM Cloud | 443 | TCP | Servicio de registro | HTTPS |
| HCX    | vCenter en IBM Cloud | 443 | TCP | Servicio REST de HCX | HTTPS |
| HCX    | PSC en IBM Cloud | 443 | TCP | Servicio REST de HCX | HTTPS |
| HCX    | connect.hcx.vmware.com | 443 | TCP | Servicio de registro | HTTPS |
| Navegador web | HCX | 9443 | TCP | Interfaz de gestión de dispositivos virtuales HCX para la configuración del sistema HCX | HTTPS |
| Red de admin | HCX | 22 | SSH | Acceso SSH de administrador a Hybrid Cloud Services | SSH |
| HCX | Hosts ESXi | 902 | TCP | Envío de instrucciones de gestión y suministro desde HCX a hosts ESXi en Hosts IBM Cloud. | Internos |
| HCX | Servidor SSO de vCenter | 7444 | TCP | Servicio de búsqueda de vSphere |  |
| HCX | Servidores NTP | 123 | UDP | Sincronización de hora | |
| HCX | Syslog |   | Configurado por el usuario | Conexión entre HCX (el cliente) y el servidor Syslog. Los valores del puerto y del protocolo de Syslog se especifican en el cliente web de vSphere. Por ejemplo, el puerto 514 para el protocolo UDP. | |
| HCX | Pasarela de nube | 8123 | TCP | Enviar instrucciones de servicio de réplica basado en host a Hybrid Cloud Gateway. | HTTP |
| HCX | Pasarela de nube | 9443 | TCP | Enviar instrucciones de gestión a Hybrid Cloud Gateway local mediante la API REST. | HTTP</br>HTTPS |
| Pasarela de nube | L2C | 443 | TCP | Enviar instrucciones de gestión desde Cloud Gateway a L2C cuando L2C utiliza la misma vía de acceso que Hybrid Cloud Gateway. | HTTP</br>HTTPS |
| Pasarela de nube | L2C | 8443 | TCP | Instrucciones de gestión bidireccional entre Cloud Gateway y L2C cuando L2C utiliza una vía de acceso de datos alternativa. | HTTP</br>HTTPS |
| L2C | L2C (remoto) | 443 | TCP | Instrucciones de gestión bidireccional entre Cloud Gateway y L2C cuando L2C utiliza una vía de acceso de datos alternativa. | HTTP</br>HTTPS |
| Pasarela de nube | Hosts ESXi | 80, 902  | TCP | Gestión y despliegue de OVF | Internos |
| Hosts ESXi | Pasarela de nube | 31031, 44046 | TCP | Tráfico de réplica interno basado en host | Internos |
| Pasarela de nube | Hosts ESXi | 8000  | TCP | vMotion (migración con tiempo de inactividad cero) |  |
| Cloud Gateway (local) | Pasarela de nube</br>(remoto) | 4500  | UDP | Intercambio de claves de (IKEv2) para encapsular cargas de trabajo para el túnel bidireccional | IPSEC |
| Cloud Gateway (local) | Pasarela de nube</br>(remoto) | 500  | UDP | Intercambio de claves de Internet (ISAKMP) para el túnel bidireccional | IPSEC |

### Enlaces relacionados

* [Instalación y configuración de HCX en el origen](hcx-archi-install-cfg-src.html)
