---

copyright:

  years:  2016, 2018

lastupdated: "2018-03-16"

---

# OVF-Datei mit VMware vSphere Web Client bereitstellen

## Lösung

Gehen Sie zur Bereitstellung einer OVF-Datei (Open Virtualization Format) mittels vSphere Web Client wie folgt vor:
1. Bevor Sie versuchen, die Bereitstellung auszuführen, müssen Sie die folgenden Hostinformationen zur Datei `/etc/hosts` hinzufügen:

   * Hostinformationen für Platform Services Controller (PSC)
   * Hostinformationen für VMware ESXi-Server
   * Hostinformationen für vCenter
2. Stellen Sie durch eine Überprüfung Ihrer Datei `/etc/hosts` sicher, dass diese Informationen erfolgreich hinzugefügt wurden. Eine Datei "hosts" kann beispielsweise wie die folgende Liste aussehen:

    ```javascript
    10.131.9.201  psc-myinstance.myinstance.mydomain.com
    10.131.7.26   host0.myinstance.mydomain.com
    10.131.7.39   host1.myinstance.mydomain.com
    10.131.7.6    host2.myinstance.mydomain.com
    10.131.7.48   host3.myinstance.mydomain.com
    10.131.9.196  vcenter-1.myinstance.mydomain.com
    ```
3. Stellen Sie sicher, dass Sie Zugriff auf alle benötigten virtuellen privaten Netze (Virtual Private Networks, VPNs) im {{site.data.keyword.slportal_full}} besitzen. In obigen Beispiel wären dies die Netze `10.131.7.xx` und `10.131.9.xxx`.
4. Melden Sie sich beim VPN für Ihr Rechenzentrum an.
5. Klicken Sie auf **vCenter**, um auf vSphere Web Client zuzugreifen.
6. Klicken Sie mit der rechten Maustaste auf einen Host und stellen Sie eine Datei `.ovf` bereit.
