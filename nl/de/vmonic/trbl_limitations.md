---

copyright:

  years:  2016, 2019

lastupdated: "2018-12-11"

---

{:faq: data-hd-content-type='faq'}

# Weitere Einschränkungen und Hinweise

Prüfen Sie die folgenden Hinweise und Einschränkungen, wenn Sie mit {{site.data.keyword.vmwaresolutions_full}} arbeiten.

## Automatische Installation von Windows-Updates
{: faq}

Microsoft Active Directory (AD) bzw. der Domänennamensserver (DNS) wird automatisch ausschließlich für das Herunterladen der Updates konfiguriert. Weder die Installation dieser Updates noch Neustart wird automatisch durchgeführt. Sie müssen die Updates manuell installieren und den Neustart zu einem geplanten Zeitpunkt ausführen, zu dem Unterbrechungen der laufenden AD-Serverkonfiguration und anderen Sicherungsjobs vermieden werden. Um Windows-Updates anzuwenden, installieren Sie die Updates manuell.

## Hinweise zur Auswahl eines Rootdomänennamens für Cloud Foundation-Instanzen

Wenn Sie während der Bereitstellung einer primären oder sekundären Cloud Foundation-Instanz einen Domänennamen auswählen, müssen Sie sicherstellen, dass der Hostname `sddcmanager.<subdomain>` bei Verwendung der Befehle `ping` oder `nslookup` nicht in eine externe Domäne aufgelöst wird.

Die Struktur der Unterdomäne für die Cloud Foundation-Instanz lautet `<VCF instance name>.<domain name>`. Falls beispielsweise für `<domain name>` der Wert `test.local` angegeben wird und Ihre Cloud Foundation-Instanz `mytest` heißt, wird der Hostname `sddcmanager.mytest.test.local` erst in eine IP-Adresse aufgelöst, wenn die Cloud Foundation-Instanz bereitgestellt wird. Andernfalls kann die Bereitstellung der Instanz fehlschlagen.
