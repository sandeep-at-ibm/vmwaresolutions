---

copyright:

  years:  2016, 2018

lastupdated: "2017-06-29"

---

# Diagnosealerts und -warnungen für virtuelles SAN (vSAN)

## Problem
Auf der Seite **Monitor** von VMware vSphere Web Client werden möglicherweise Alerts und Warnungen für Probleme im Zusammenhang mit dem Zustand des virtuellen SAN angezeigt.

## Lösung
Bei diesen Warnungen handelt es sich nicht um Fehlernachrichten; sie weisen nicht auf funktionale Probleme hin. Sie können jedoch die folgende Prozedur verwenden, wenn Sie die Warnungen aus vSphere Web Client löschen wollen:

1. Rufen Sie die Adresse "http://partnerweb.vmware.com/service/vsan/all.json" auf und speichern Sie die JSON-Datei mit dem Namen `all.json` auf Ihrem lokalen System.
2. Stellen Sie sicher, dass Sie die Schritte ausgeführt haben, die im Abschnitt [Zeitlimitüberschreitung für vCenter-Konsole](trbl_timeout_vc_console.html) beschrieben sind.
3. Klicken Sie auf der Seite mit den Details der Cloud Foundation-Instanz auf die Schaltfläche **vCenter-Konsole** und melden Sie sich bei vSphere Web Client mit den Berechtigungsnachweisen an, die in der {{site.data.keyword.vmwaresolutions_full}}-Konsole angezeigt werden.
4. Navigieren Sie in vSphere Web Client zu **Manage > Settings** und öffnen Sie den Abschnitt **Virtual SAN > Health > HCL Database**. Klicken Sie auf **Update from file** und laden Sie dann die zuvor gespeicherte Datei `all.json` hoch.
5. Um die Warnungen zu löschen, wechseln Sie in das Teilfenster **Alarms** rechts oben in vSphere Web Client. Klicken Sie mit der rechten Maustaste auf jeden Alarm und wählen Sie die Option **Reset to green** aus.

Weitere Informationen finden Sie auf der Seite [How to download offline vSAN HCL file for vSAN Health Check Plugin](http://www.virtuallyghetto.com/2015/05/how-to-download-offline-vsan-hcl-file-for-vsan-health-check-plugin.html){:new_window}.
