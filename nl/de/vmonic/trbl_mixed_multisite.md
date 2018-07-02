---

copyright:

  years:  2016, 2018

lastupdated: "2017-10-05"

---

# Sekundäre Instanz aus V1.7 kann nicht zu primärer Instanz aus V1.5 hinzugefügt werden

## Problem
In einer Cloud Foundation-Konfiguration mit mehreren Standorten können Sie eine sekundäre Instanz aus V1.7 nicht zu einer primären Instanz aus V1.5 hinzufügen, weil die Betriebssystemversionen auf dem Server für Microsoft Active Directory (AD) voneinander abweichen.

## Lösung
Führen Sie die folgenden Schritte für die primäre Instanz aus V1.5 aus, um für den primären Automatisierungsbenutzer die Berechtigungen hinzuzufügen, die ihn zum Mitglied der Gruppen **Organisations-Admins** und **Schema-Admins** machen.

1. Melden Sie sich beim Windows AD-Server mit dem Kennwort des **Administrators** an.
2. Öffnen Sie den **Server-Manager** und klicken Sie auf **Extras -> Active Directory-Benutzer und -Computer**.
4. Klicken Sie im Fenster **Active Directory-Benutzer und -Computer** auf den Abschnitt **Benutzer** unter Ihrer Rootdomäne.
5. Klicken Sie mit der rechten Maustaste auf den Automatisierungsbenutzer, um das Fenster **Eigenschaften** zu öffnen.
6. Klicken Sie auf die Registerkarte **Mitglied von**.
7. Klicken Sie auf **Hinzufügen** und geben Sie die Gruppen **Organisations-Admins** und **Schema-Admins** als Objektnamen für die Liste ein.  

Nachdem Sie diese Schritte ausgeführt haben, können Sie eine sekundäre Instanz aus V1.7 zu einer primären Instanz aus V1.5 hinzufügen.
