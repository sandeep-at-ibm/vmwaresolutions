---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-25"

---

# Zerto Virtual Replication Appliances werden für neu erstellte ESXi-Server nicht angezeigt

## Problem
Virtual Replication Appliances (VRA) werden in der Konsole von Zerto Virtual Replication nicht angezeigt, nachdem Sie ESXi-Server zu einer VMware vCenter Server-Instanz hinzugefügt haben, in der die Disaster-Recovery mit Zerto installiert ist.

## Lösung
Bei vCenter Server-Instanzen wird der Service für die Disaster-Recovery mit Zerto nur auf dem ESXi-Server aus dem Standardcluster **cluster1** installiert. Auf allen zusätzlichen Clustern in derselben vCenter Server-Umgebung wird die Disaster-Recovery mit Zerto weder beim Erstellen eines zusätzlichen Clusters noch beim Hinzufügen des ESXi-Server zu diesem zusätzlichen Cluster automatisch installiert.

Für die zusätzlichen Cluster müssen Sie die Disaster-Recovery mit Zerto gesondert installieren.

Öffnen Sie ein {{site.data.keyword.cloud}}-Support-Ticket und fordern Sie unter Anleitung durch den IBM Support verfügbare IP-Adressen zur Installation der VRAs in der Zerto-Konsole und nicht in der {{site.data.keyword.vmwaresolutions_short}}-Konsole an.

Um auf die Zerto-Konsole zuzugreifen, klicken Sie auf der Registerkarte **Services** der Instanz auf die Karte für Zerto, dann auf **Details anzeigen** und anschließend auf **Zerto-Konsole anzeigen**.

Unter [Kontaktaufnahme mit dem IBM Support](trbl_support.html) finden Sie weitere Angaben darüber, wie Sie sich mit dem IBM Support in Verbindung setzen.
