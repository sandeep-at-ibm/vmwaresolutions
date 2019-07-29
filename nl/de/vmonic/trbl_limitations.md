---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-28"

keywords: troubleshooting, Windows automatic installation, Windows updates

subcollection: vmware-solutions


---

{:faq: data-hd-content-type='faq'}

# Weitere Einschränkungen und Hinweise
{: #trbl_limitations}

Prüfen Sie die folgenden Hinweise und Einschränkungen, wenn Sie mit {{site.data.keyword.vmwaresolutions_full}} arbeiten.

## Automatische Installation von Windows-Updates
{: #trbl_limitations-windows-update}
{: faq}

Microsoft Active Directory (AD) bzw. der Domänennamensserver (DNS) wird automatisch ausschließlich für das Herunterladen der Updates konfiguriert. Weder die Installation dieser Updates noch Neustart wird automatisch durchgeführt. Sie müssen die Updates manuell installieren und den Neustart zu einem geplanten Zeitpunkt ausführen, zu dem Unterbrechungen der laufenden AD-Serverkonfiguration und anderen Sicherungsjobs vermieden werden. Um Windows-Updates anzuwenden, installieren Sie die Updates manuell.
