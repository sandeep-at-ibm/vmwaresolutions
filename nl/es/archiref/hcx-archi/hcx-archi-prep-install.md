---

copyright:

  years:  2016, 2019

lastupdated: "2018-12-21"

---
# Preparación del entorno de instalación

La instalación de VMware HCX on IBM Cloud tiene los siguientes requisitos de software:
* vSphere 5.5 U3 o vSphere 6.0u2 o superior.
* Si se utiliza NSX, versión 6.2.2 o superior. NSX se necesita para la migración de políticas.
* Para utilizar vMotion entre nubes, se aplican las mismas restricciones de afinidad entre nubes que las que se aplican en entornos locales. Para obtener más información, consulte las [Preguntas frecuentes sobre la compatibilidad entre EVC y CPU](http://bit.ly/2vK6Sp5).

## Configuración de la conectividad de red

HCX debe cruzar internet público y líneas privadas, y conectar con los componentes del centro de datos, como redes, conmutadores y grupos de puertos.
* En el apartado [Requisitos de acceso a puertos](hcx-archi-port-req.html) encontrará los puertos que deben estar abiertos para que los dispositivos virtuales HCX se puedan instalar correctamente.
* Tanto el entorno de vSphere local como el entorno de VCF/VCS HCX Cloud deben permitir la sincronización de reloj de Network Time Protocol (NTP) entre los dispositivos locales de vSphere y los dispositivos de VCF/VCS HCX. El puerto UDP 123 debe resultar accesible para los dispositivos virtuales y las redes de HCX.

## Entorno local

Antes de instalar HCX, verifique que el entorno puede dar soporte a las tareas que desea llevar a cabo. El entorno local debe dar soporte a las tareas siguientes para que se pueda instalar HCX.
* Virtual Center con vSphere 5.5 Actualización 3 o 6.0 Actualización 2.
* Las características de vMotion y de migración de políticas requieren NSX versión 6.2.2 o superior.
* Una cuenta de servicio de vSphere con el rol de administrador del sistema vCenter Server asignado.
* En el vCenter, suficiente espacio de disco para los dispositivos HCX que se van a instalar.
* Suficientes direcciones IP para las VM locales suministradas durante la instalación.
* Puertos y cortafuegos abiertos según se documenta en los requisitos de acceso a puertos.
* Si el servidor de inicio de sesión único (SSO) es remoto, se debe identificar el URL del vCenter, del servidor de SSO externo o del controlador de servicios de plataforma (PSC) que ejecuta el servicio de búsqueda externo. Cuando se registra HCX Manager con el vCenter, se debe suministrar este URL.
* Si un vCenter no tiene su propia instancia interna del servicio de búsqueda, puede ser por una de las razones siguientes:
  * vCenter 6.0u2 ejecuta un controlador de servicios de plataforma externo.
  * vCenter está en modalidad enlazada (donde el vCenter secundario utiliza el servicio SSO desde el vCenter primario o un servicio de SSO externo).

## Verificación del entorno de instalación de capa 2

La extensión de red de capa 2 tiene los requisitos siguientes:
* vSphere Enterprise Plus Edition.
* vSphere vCenter debe cumplir los requisitos siguientes para dar soporte a la extensión de capa 2:
  * Licencia de vSphere Enterprise Plus
  * Debe tener vSphere Distributed Switch (vDS). El conmutador distribuido está disponible con vSphere Enterprise Plus Edition.
  * Cuando se instala, el dispositivo de servicio concentrador de capa 2 local debe tener acceso a un puerto vNIC y a cualquier VLAN que se vaya a extender.
  * Si la red se va a extender a través de internet público o de una VPN (en una vía de acceso alternativa), la máquina virtual L2C en VCF/VCS necesita una dirección IP. La dirección IP remota se necesita para configurar el concentrador de capa 2.
  * Si se desean varios concentradores de capa 2, cada uno de ellos debe tener una dirección IP local y en la nube.

### Enlaces relacionados

* [Instalación y configuración de HCX en el origen](hcx-archi-install-cfg-src.html)
* [Preguntas frecuentes sobre la compatibilidad entre VMware EVC y CPU](http://bit.ly/2vK6Sp5)
