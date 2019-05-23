---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-25"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# vCenter Server with Hybridity Bundle-Instanzen in einer Konfiguration mit mehreren Standorten löschen
{: #vc_hybrid_deletinginstance_multi}

Vor dem Löschen von VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle-Instanzen, die Teil einer Konfiguration mit mehreren Standorten sind, müssen besondere Aspekte berücksichtigt werden.

Wenn Sie eine vCenter Server with Hybridity Bundle-Instanz löschen, werden die folgenden Komponenten nacheinander freigegeben:
1. Alle bereitgestellten Services
2. Support- und Servicegebühren
3. VMware-Produktlizenzen
4. ESXi-Server
5. Teilnetze
6. VLANs

Aufgrund von Ressourcenabhängigkeiten werden die Komponenten in Ihrer Instanz nicht sofort freigegeben, wenn Sie die Instanz löschen. Beispielsweise können die Teilnetze und VLANs erst gelöscht werden, nachdem die ESXi-Server vollständig von der {{site.data.keyword.cloud_notm}}-Infrastruktur zurückgefordert wurden, was am Ende des Abrechnungszyklus für die {{site.data.keyword.cloud_notm}}-Infrastruktur passiert. Am Ende des Abrechnungszyklus für die {{site.data.keyword.cloud_notm}}-Infrastruktur, der normalerweise 30 Tage beträgt, werden die Teilnetze und VLANs gelöscht und die Instanzlöschung ist abgeschlossen.

Die gelöschten Instanzen werden Ihnen bis zum Ende des Abrechnungszyklus für die {{site.data.keyword.cloud_notm}}-Infrastruktur berechnet.
{:note}

## Vorgehensweise zum Löschen von vCenter Server with Hybridity Bundle-Instanzen in einer Konfiguration mit mehreren Standorten
{: #vc_hybrid_deletinginstance_multi-procedure}

1. Entfernen Sie alle Services aus der sekundären vCenter Server with Hybridity Bundle-Instanz.
2. Stellen Sie sicher, dass in die zu löschende sekundäre Instanz keine NSX-Objekte erweitert wurden.
3. Löschen Sie den sekundären vCenter-Server aus der primären SSO-Domäne (Single Sign-On). Weitere Informationen finden Sie unter [Unregister vCenter Server from Single Sign-On](https://kb.vmware.com/s/article/2106736){:new_window}.
4. Stufen Sie die virtuelle Serviceinstanz (VSI) für den lokalen Domänencontroller herab. Weitere Informationen finden Sie unter [Demoting domain controllers and domains](https://docs.microsoft.com/en-us/windows-server/identity/ad-ds/deploy/demoting-domain-controllers-and-domains--level-200-){:new_window}.
5. Löschen Sie die sekundäre vCenter Server with Hybridity Bundle-Instanz in der {{site.data.keyword.vmwaresolutions_short}}-Konsole.
6. Wiederholen Sie die Schritte 1-5 für alle sekundären vCenter Server with Hybridity Bundle-Instanzen in Ihrer Konfiguration mit mehreren Standorten.
7. Nachdem Sie alle sekundären Instanzen gelöscht haben, können Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole auch die primäre Instanz löschen.

## Zugehörige Links
{: #vc_hybrid_deletinginstance_multi-related}

* [vCenter Server with Hybridity Bundle-Instanzen löschen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_deletinginstance)
* [Services für vCenter Server with Hybridity Bundle-Instanzen bestellen, anzeigen und entfernen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservices)
