---

copyright:

  years:  2016, 2018

lastupdated: "2017-04-27"

---

# Supresión de instancias de VMware Federal en una configuración de varios sitios

Existen consideraciones especiales a tener en cuenta antes de suprimir instancias de VMware Federal que forman parte de una configuración de varios sitios.

Cuando suprima una instancia de VMware Federal, los siguientes componentes se liberarán en esta secuencia:
1. Cuota de soporte y servicios
2. Licencias del producto VMware
3. Servidores ESXi
4. Subredes

Debido a las dependencias entre recursos, los componentes de la instancia no se liberan inmediatamente cuando se suprime la instancia. Por ejemplo, las subredes y las VLAN no se pueden suprimir hasta que la infraestructura de {{site.data.keyword.cloud}} haya reclamado por completo los servidores ESXi, lo cual sucede al final del ciclo de facturación de la infraestructura de {{site.data.keyword.cloud_notm}}. Al final del ciclo de facturación de la infraestructura de {{site.data.keyword.cloud_notm}}, que suele ser de 30 días, se suprimen las subredes y las VLAN y se completa la supresión de la instancia.

**Atención**: se le facturará por la instancia suprimida hasta el final del ciclo de facturación de la infraestructura de {{site.data.keyword.cloud_notm}}.

## Procedimiento

<!--1. Remove all services from the secondary VMware Federal instance.-->
2. Asegúrese de que no tiene ningún objeto NSX ampliado en la instancia secundaria que desea suprimir.
3. Suprima el vCenter secundario y el PSC (Platform Services Controller) del dominio SSO (inicio de sesión único) primario. Para obtener más información, consulte [Eliminación del registro de vCenter Server de un inicio de sesión único](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=2106736){:new_window}.
4. Disminuya el nivel de la VSI (instancia de servicio virtual) del controlador de dominio local. Para obtener más información, consulte [Disminución del nivel de controladores de dominio y de dominios](https://technet.microsoft.com/en-us/windows-server-docs/identity/ad-ds/deploy/demoting-domain-controllers-and-domains--level-200-){:new_window}.
5. Suprima la instancia secundaria de VMware Federal de la consola de {{site.data.keyword.vmwaresolutions_short}}.
6. Repita los pasos 1 a 5 para todas las instancias secundarias de VMware Federal de la configuración de varios sitios.
7. Después de suprimir todas las instancias secundarias, también puede suprimir la instancia primaria desde la consola de {{site.data.keyword.vmwaresolutions_short}}.

## Enlaces relacionados

* [Supresión de instancias de VMware Federal](vc_fed_deletinginstance.html)
* [Configuración de varios sitios para instancias de VMware Federal on IBM Cloud](fed_multisite.html)
