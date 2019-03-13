---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Supresión de instancias de vCenter Server en una configuración de varios sitios
{: #vc_deletinginstance_multi}

Tenga en cuenta las siguientes consideraciones especiales antes de planificar la supresión de instancias de vCenter Server que forman parte de una configuración de varios sitios.

Cuando suprima una instancia de vCenter Server, los siguientes componentes se liberarán en esta secuencia:
1. Todos los servicios desplegados
2. Cuota de soporte y servicios
3. Licencias del producto VMware
4. Servidores ESXi
5. Subredes
6. VLAN

Debido a las dependencias entre recursos, los componentes de la instancia no se liberan inmediatamente cuando se suprime la instancia. Por ejemplo, las subredes y las VLAN no se pueden suprimir hasta que la infraestructura de {{site.data.keyword.cloud}} haya reclamado por completo los servidores ESXi, lo cual sucede al final del ciclo de facturación de la infraestructura de {{site.data.keyword.cloud_notm}}. Al final del ciclo de facturación de la infraestructura de {{site.data.keyword.cloud_notm}}, que suele ser de 30 días, se suprimen las subredes y las VLAN y se completa la supresión de la instancia.

Se le facturará por la instancia suprimida hasta el final del ciclo de facturación de la infraestructura {{site.data.keyword.cloud_notm}}.
{:note}

## Procedimiento para suprimir instancias de vCenter Server en una configuración de varios sitios
{: #vc_deletinginstance_multi-procedure}

1. Elimine todos los servicios desde la instancia secundaria de vCenter Server.
2. Asegúrese de que no hay ningún objeto NSX expandido en la instancia secundaria que desea suprimir.
3. Suprima el vCenter Server secundario del dominio de SSO (inicio de sesión único) primario. Para obtener más información, consulte [Eliminación del registro de vCenter Server de un inicio de sesión único](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=2106736){:new_window}.
4. Disminuya el nivel de la VSI (instancia de servicio virtual) del controlador de dominio local. Para obtener más información, consulte [Disminución del nivel de controladores de dominio y de dominios](https://technet.microsoft.com/en-us/windows-server-docs/identity/ad-ds/deploy/demoting-domain-controllers-and-domains--level-200-){:new_window}.
5. Suprima la instancia secundaria de vCenter Server de la consola de {{site.data.keyword.vmwaresolutions_short}}.
6. Repita los pasos 1 a 5 para todas las instancias secundarias de vCenter Server de la configuración de varios sitios.
7. Después de suprimir todas las instancias secundarias, también puede suprimir la instancia primaria desde la consola de {{site.data.keyword.vmwaresolutions_short}}.

## Enlaces relacionados
{: #vc_deletinginstance_multi-related}

* [Supresión de instancias de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_deletinginstance)
* [Solicitud, visualización y eliminación de servicios de instancias de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)
