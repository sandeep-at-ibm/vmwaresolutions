---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-13"

subcollection: vmwaresolutions


---

# Zerto
{: #vum-zerto}

Wenn Sie feststellen, dass ein vSphere ESXi-Host während der Korrekturphase nicht in den Wartungsmodus wechseln kann, kann es daran liegen, dass er von Zerto gestoppt wird. Wenn Sie Zerto seit der ersten Bereitstellung aktualisiert haben, führen Sie die folgenden Schritte aus, um dies zu korrigieren. Wenn Sie keine Aktualisierung vorgenommen haben, befolgen Sie die Anweisungen im Abschnitt [How to place a host with an associated VRA into maintenance mode](https://www.zerto.com/myzerto/knowledge-base/place-host-into-maintenance-mode-with-vra/).

1. Melden Sie sich bei der Zerto-Webbenutzerschnittstelle an.
2. Wählen Sie **Site Settings** im Dropdown-Menü aus.
3. Wählen Sie die Registerkarte **Policies** aus und stellen Sie sicher, dass **Allow Zerto to always enter hosts to maintenance mode during remediation** ausgewählt ist.
4. Melden Sie sich bei Zerto ab.

## Zugehörige Links
{: #vum-zerto-related}

* [VMware HCX on {{site.data.keyword.cloud_notm}} Solution Architecture](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-intro#hcx-archi-intro)
* [VMware Solutions on	{{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (Demonstrationen)
