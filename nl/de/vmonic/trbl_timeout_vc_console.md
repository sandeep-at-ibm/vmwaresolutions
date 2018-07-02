---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-29"

---

# Zeitlimitüberschreitung beim Herstellen einer Verbindung zu VMware vSphere Web Client

## Problem
Wenn Sie versuchen, eine Verbindung zu vSphere Web Client herzustellen, erhalten Sie möglicherweise die folgende Fehlernachricht aufgrund einer Zeitüberschreitung:

`Der Server bei <IP_address> benötigt zu viel Zeit für die Antwort.`

## Lösung
Führen Sie die folgenden Schritte aus, um das Problem zu beheben und zu lösen.

1. Stellen Sie sicher, dass Sie die Schritte in der QuickInfo ausgeführt haben, die angezeigt wird, wenn Sie den Mauszeiger über die Schaltfläche **vCenter-Konsole** bewegen. Diese
   Schritte sind für Sie nachstehend noch einmal aufgeführt:   
   1. Installieren Sie für Ihren Browser das Plug-in für Adobe Flash Player.   
   2. Erstellen Sie im {{site.data.keyword.slportal_full}} ein VPN-Kennwort.    
   3. Melden Sie sich beim VPN-Portal für das Rechenzentrum mit den VPN-Berechtigungsnachweisen der {{site.data.keyword.cloud_notm}}-Infrastruktur an.    
   4. Fügen Sie die Zuordnung von IP-Adresse und Hostname für PSC (Platform Services Controller) in der Datei "hosts" mit dem folgenden Format hinzu:

      ```javascript
      IPAddress              HostName
      ```

2. Notieren Sie sich die angezeigte IP-Adresse, da Sie sie in einem der nächsten Schritte benötigen.
3. Stellen Sie sicher, dass Sie auf das VPN der {{site.data.keyword.cloud_notm}}-Infrastruktur zugreifen können. Führen Sie die folgenden Schritte im {{site.data.keyword.slportal}} aus:
   1. Klicken Sie auf **Konto > VPN-Zugriff**.
   2. Klicken Sie in der Spalte **VPN-Zugriff** auf die **SSL-Verbindung**.
   3. Legen Sie auf der Seite **VPN-Zugriff für Benutzername** für die Option **Teilnetzzugriff** die Einstellung **Manuell** fest.
   4. Suchen Sie auf derselben Seite das Teilnetz für das Paar aus IP-Adresse und Hostname. Weitere Informationen hierzu finden Sie in **Schritt 2**.    

      Wenn die IP-Adresse für Ihre Instanz beispielsweise `xx.yyy.zz.15` lautet und die IP-Adresse für vCenter `xx.yyy.zz.10` lautet, müssen Sie den Zugriff für das Teilnetz `xx.yyy.zz.0/26` erteilen.

   5. Wählen Sie das Kontrollkästchen **Zugriff erteilen** für dieses Teilnetz aus und klicken Sie auf **Speichern**.
