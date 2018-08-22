---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-20"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}
{:pre: .pre}

# Einführung in IBM Cloud for VMware Solutions
{: #gettingstarted}

Die Konsole von {{site.data.keyword.vmwaresolutions_full}} ist die Schnittstelle, über die Sie Ihre Bereitstellungen bestellen und verwalten. Jede Bereitstellung wird in der Konsole als Instanz verwaltet. Die Konsole ist eine eigenständige und vom {{site.data.keyword.slportal}} getrennte Benutzerschnittstelle.

## Vorbereitende Schritte

Lesen Sie die wichtigen Informationen zu Browseranforderungen und Benutzerkonten, bevor Sie mit {{site.data.keyword.vmwaresolutions_short}} arbeiten.

### Browser- und Auflösungsvoraussetzungen

Die folgenden Browser werden unterstützt:
*  Mozilla Firefox
*  Google Chrome
*  Apple Safari

**Hinweis**: Microsoft Internet Explorer wird nicht unterstützt.

Optimale Anzeige- und Arbeitsbedingungen für die {{site.data.keyword.vmwaresolutions_short}}-Konsole erreichen Sie, indem Sie mindestens eine Bildschirmauflösung von 1024 Pixel Breite mal 500 Pixel Höhe verwenden.

### IBMid

Durch die **IBMid** können Sie einen einzigen Anmeldebenutzernamen für alle genutzten IBM Produkte und Services, einschließlich {{site.data.keyword.cloud_notm}}, verwenden. {{site.data.keyword.vmwaresolutions_short}} wird als Infrastrukturlösung im {{site.data.keyword.cloud_notm}}-Katalog bereitgestellt. Um auf die {{site.data.keyword.vmwaresolutions_short}}-Konsole zugreifen zu können, müssen Sie dementsprechend über eine **IBMid** verfügen.

Damit Sie Ihre **IBMid** zur Anmeldung bei der Konsole von {{site.data.keyword.vmwaresolutions_short}} verwenden können, müssen Sie die **IBMid** einem {{site.data.keyword.cloud_notm}}-Konto zuordnen. Wenn Sie sich zum ersten Mal bei der Konsole anmelden, müssen Sie entweder Ihre vorhandene **IBMid** einem {{site.data.keyword.cloud_notm}}-Konto zuordnen oder sich für ein neues {{site.data.keyword.cloud_notm}}-Konto registrieren, das dann automatisch Ihrer **IBMid** zugeordnet wird. Dieses Verfahren müssen Sie nur einmal durchlaufen.

Wenn Sie Probleme beim Zuordnen Ihrer **IBMid** zu einem {{site.data.keyword.cloud_notm}}-Konto haben, lesen Sie die Informationen im Abschnitt [Fehlerbehebung beim Zugriff auf {{site.data.keyword.cloud_notm}}](https://console.bluemix.net/docs/troubleshoot/ts_accessing.html).

### IBM Cloud-Konto

Ein {{site.data.keyword.cloud_notm}}-Konto ist für die Bestellung und Verwendung von IBM Cloud-Services erforderlich. Abrechnungsinformationen werden dem IBM Cloud-Konto zugeordnet. Zur Bestellung und Verwendung der Bereitstellungsangebote von {{site.data.keyword.vmwaresolutions_short}} müssen Sie daher ein {{site.data.keyword.cloud_notm}}-Konto haben. Die Kosten für die physische und virtuelle Infrastruktur sowie die daraus resultierenden Lizenzen werden Ihrem {{site.data.keyword.cloud_notm}}-Konto in Rechnung gestellt. Weitere Informationen zu den Anforderungen, die Ihr {{site.data.keyword.cloud_notm}}-Konto erfüllen muss, finden Sie unter [Voraussetzungen für {{site.data.keyword.cloud_notm}}-Konto](vmonic/slaccountrequirement.html).

### Konto für die IBM Cloud-Infrastruktur (SoftLayer)

Das Konto für die {{site.data.keyword.cloud_notm}}-Infrastruktur (SoftLayer) wurde früher als IBM SoftLayer-Konto bezeichnet.

Sie können Konten für die {{site.data.keyword.cloud_notm}}-Infrastruktur (SoftLayer) mit {{site.data.keyword.cloud_notm}}-Konten verknüpfen, um kombinierte Infrastructure as a Service-Ressourcen (IaaS) und Platform as a Service-Ressourcen (PaaS) zu nutzen. Anschließend können Sie auf IaaS-Ressourcen und PaaS-Ressourcen über ein und dieselbe Anmeldung zugreifen. Das Verknüpfen Ihrer Konten hat außerdem zur Folge, dass Sie nur eine Rechnung für alle PaaS- und IaaS-Ressourcen erhalten, die Sie nutzen.

* Wenn Sie kein Konto für die {{site.data.keyword.cloud_notm}}-Infrastruktur (SoftLayer) haben, können Sie eines anfordern, indem Sie die unter [Für ein IBM Cloud-Infrastrukturkonto (SoftLayer-Konto) registrieren](../vmonic/signing_softlayer_account.html) beschriebene Prozedur ausführen, und anschließend Ihr Konto für die {{site.data.keyword.cloud_notm}}-Infrastruktur (SoftLayer) mit Ihrem {{site.data.keyword.cloud_notm}}-Konto verknüpfen, indem Sie die unter [IBMid-Konten verknüpfen](https://console.bluemix.net/docs/account/softlayerlink.html) beschriebene Prozedur ausführen.
* Wenn Sie bereits ein Konto für die {{site.data.keyword.cloud_notm}}-Infrastruktur (SoftLayer) haben, können Sie es mit Ihrem {{site.data.keyword.cloud_notm}}-Konto verknüpfen, indem Sie die unter [IBMid-Konten verknüpfen](https://console.bluemix.net/docs/account/softlayerlink.html) beschriebene Prozedur ausführen.

## Auf die Konsole von IBM Cloud for VMware Solutions zugreifen

Weitere Informationen zum Zugriff auf die Konsole über den {{site.data.keyword.cloud_notm}}-Katalog finden Sie unter [Auf {{site.data.keyword.vmwaresolutions_short}}-Konsole zugreifen](vmonic/loginmethod.html).

### Zugehörige Links

* [Informationen zu {{site.data.keyword.vmwaresolutions_short}}](vmonic/prod_overview.html)
* [Übersicht über Cloud Foundation](sddc/sd_cloudfoundationoverview.html)
* [Übersicht über vCenter Server](vcenter/vc_vcenterserveroverview.html)
* [Fortinet on IBM Cloud](services/fsa_considerations.html)
* [Veeam on IBM Cloud](services/veeam_considerations.html)
* [Zerto on IBM Cloud](services/addingzertodr.html)
