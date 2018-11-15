---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-29"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Cloud Foundation-Instanzen in Konfiguration mit mehreren Standorten löschen

Prüfen Sie folgende Aspekte, bevor Sie in einer Konfiguration mit mehreren Standorten planen, Cloud Foundation-Instanzen zu löschen.

Wenn Sie eine Cloud Foundation-Instanz löschen, werden die folgenden Komponenten nacheinander freigegeben:
1. Alle bereitgestellten Services
2. Support- und Servicegebühren
3. VMware-Produktlizenzen
4. ESXi-Server
5. Teilnetze
6. VLANs

Aufgrund von Ressourcenabhängigkeiten werden die Komponenten in Ihrer Instanz nicht sofort freigegeben, wenn Sie die Instanz löschen. Beispielsweise können die Teilnetze und VLANs erst gelöscht werden, nachdem die ESXi-Server vollständig von der {{site.data.keyword.cloud}}-Infrastruktur zurückgefordert wurden, was am Ende des {{site.data.keyword.cloud_notm}}-Abrechnungszyklus passiert. Am Ende des {{site.data.keyword.cloud_notm}}-Abrechnungszyklus, der normalerweise 30 Tage beträgt, werden die Teilnetze und VLANs gelöscht und die Instanzlöschung ist abgeschlossen.

Die gelöschte Instanz wird bis zum Ende des {{site.data.keyword.cloud_notm}}-Abrechnungszyklus berechnet.
{:note}

## Vorgehensweise zum Löschen von Cloud Foundation-Instanzen in einer Konfiguration mit mehreren Standorten

1. Entfernen Sie alle Services aus der sekundären Cloud Foundation-Instanz.
2. Stellen Sie sicher, dass in die zu löschende sekundäre Instanz keine NSX-Objekte erweitert wurden.
3. Löschen Sie die sekundäre vCenter- und PSC-Instanz aus der primären SSO-Domäne. Weitere Informationen finden Sie unter [Unregister vCenter Server from Single Sign-On](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=2106736){:new_window}.
4. Stufen Sie die virtuelle Serviceinstanz (VSI) für den lokalen Domänencontroller herab. Weitere Informationen finden Sie unter [Demoting domain controllers and domains](https://technet.microsoft.com/en-us/windows-server-docs/identity/ad-ds/deploy/demoting-domain-controllers-and-domains--level-200-){:new_window}.
5. Löschen Sie die sekundäre Cloud Foundation-Instanz in der {{site.data.keyword.vmwaresolutions_short}}-Konsole.
6. Wiederholen Sie die Schritte 1 bis 5 für alle sekundären Cloud Foundation-Instanzen in Ihrer Konfiguration mit mehreren Standorten.
7. Nachdem Sie alle sekundären Instanzen gelöscht haben, können Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole auch die primäre Instanz löschen.

### Zugehörige Links

* [Cloud Foundation-Instanzen löschen](sd_deletinginstance.html)
* [Services von Cloud Foundation-Instanzen bestellen, anzeigen und entfernen](sd_addingremovingservices.html)
