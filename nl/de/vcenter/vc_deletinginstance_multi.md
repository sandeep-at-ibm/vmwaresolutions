---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-28"

keywords: vCenter Server delete instance, delete vCenter Server, delete multi-site

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# vCenter Server-Instanzen in einer Konfiguration mit mehreren Standorten löschen
{: #vc_deletinginstance_multi}

Beachten Sie folgende besondere Aspekte, bevor Sie planen, vCenter Server-Instanzen zu löschen, die Teil einer Konfiguration mit mehreren Standorten sind.

Wenn Sie eine vCenter Server-Instanz löschen, werden die folgenden Komponenten nacheinander freigegeben:
1. Alle bereitgestellten Services
2. Support- und Servicegebühren
3. VMware-Produktlizenzen
4. ESXi-Server
5. Teilnetze
6. VLANs

Aufgrund von Ressourcenabhängigkeiten werden die Komponenten in Ihrer Instanz nicht sofort freigegeben, wenn Sie die Instanz löschen. Beispielsweise können die Teilnetze und VLANs erst gelöscht werden, nachdem die ESXi-Server vollständig von der {{site.data.keyword.cloud}}-Infrastruktur zurückgefordert wurden, was am Ende des Abrechnungszyklus für die {{site.data.keyword.cloud_notm}}-Infrastruktur passiert. Am Ende des Abrechnungszyklus für die {{site.data.keyword.cloud_notm}}-Infrastruktur, der normalerweise 30 Tage beträgt, werden die Teilnetze und VLANs gelöscht und die Instanzlöschung ist abgeschlossen.

Die gelöschten Instanzen werden Ihnen bis zum Ende des Abrechnungszyklus für die {{site.data.keyword.cloud_notm}}-Infrastruktur berechnet.
{:note}

## Vorgehensweise zum Löschen von vCenter Server-Instanzen in einer Konfiguration mit mehreren Standorten
{: #vc_deletinginstance_multi-procedure}

1. Entfernen Sie alle Services aus der sekundären vCenter Server-Instanz.
2. Stellen Sie sicher, dass keine NSX-Objekte in die sekundäre Instanz erweitert werden, die Sie löschen möchten.
3. Löschen Sie die sekundäre vCenter Server-Instanz aus der primären SSO-Domäne (Single Sign-On). Weitere Informationen finden Sie unter [Unregister vCenter Server from Single Sign-On](https://kb.vmware.com/s/article/2106736){:new_window}.
4. Stufen Sie die virtuelle Serviceinstanz (VSI) für den lokalen Domänencontroller herab. Weitere Informationen finden Sie unter [Demoting domain controllers and domains](https://docs.microsoft.com/en-us/windows-server/identity/ad-ds/deploy/demoting-domain-controllers-and-domains--level-200-){:new_window}.
5. Löschen Sie die sekundäre vCenter Server-Instanz in der {{site.data.keyword.vmwaresolutions_short}}-Konsole.
6. Wiederholen Sie die Schritte 1-5 für alle sekundären vCenter Server-Instanzen in Ihrer Konfiguration mit mehreren Standorten.
7. Nachdem Sie alle sekundären Instanzen gelöscht haben, können Sie auch die primäre Instanz in der {{site.data.keyword.vmwaresolutions_short}}-Konsole löschen.

## Zugehörige Links
{: #vc_deletinginstance_multi-related}

* [vCenter Server-Instanzen löschen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_deletinginstance)
* [Services von vCenter Server-Instanzen bestellen, anzeigen und entfernen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)
* [Virtuelle Server stornieren](/docs/vsi?topic=virtual-servers-managing-virtual-servers#cancel)
