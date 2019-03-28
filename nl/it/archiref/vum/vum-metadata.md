---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

#	Raccolta di metadati
{: #vum-metadata}

VUM scarica i metadati relativi ad aggiornamenti, patch o estensioni tramite un processo automatico predefinito che puoi modificare. A intervalli regolari configurabili, VUM contatta VMware o fonti di terze parti per raccogliere i metadati più recenti relativi ad aggiornamenti, patch o estensioni disponibili. Tuttavia, le impostazioni predefinite di VMware sono accettabili per l'utilizzo nell'istanza VMware vCenter Server on {{site.data.keyword.cloud}} e puoi modificarle in base alle tue esigenze aziendali.

VUM visualizza le baseline gestite dal sistema generate da vSAN. Le baseline gestite dal sistema aggiornano automaticamente il loro contenuto su base periodica, il che richiede che VUM abbia accesso costante a Internet. Le baseline del sistema vSAN vengono in genere aggiornate ogni 24 ore.

Puoi utilizzare le baseline gestite dal sistema per aggiornare i cluster vSAN alle patch, ai driver, agli aggiornamenti critici consigliati o alla versione host ESXi più recente supportata per vSAN.

Per la maggior parte delle aziende, le impostazioni predefinite di VMware per VUM sono considerate adeguate. Se la tua azienda vuole utilizzare impostazioni diverse, le seguenti informazioni indicano come modificare tali impostazioni.

##	Download Schedule
{: #vum-metadata-download-schedule}

Gli aggiornamenti sono aggiornamenti di dispositivi virtuali, estensioni e patch di host e, per impostazione predefinita, VUM scarica gli aggiornamenti ogni giorno. Modifica la pianificazione di download accedendo al client web vSphere, passando a **Home** > **Update Manager** > **Manage** > **Settings**, selezionando **Download Schedule** e facendo quindi clic su **Edit**.

##	Notification Check Schedule
{: #vum-metadata-notif-check-schedule}

Le notifiche sono informazioni su richiami di patch, nuove correzioni e avvisi e, per impostazione predefinita, VUM scarica le notifiche su base oraria. Per modificare questa impostazione, accedi al client web vSphere, passa a **Home** > **Update Manager** > **Manage** > **Settings**, seleziona **Notification Check Schedule** e fai clic su **Edit**.

##	Impostazioni della VM (Virtual Machine)
{: #vum-metadata-vm-settings}

Per modificare le impostazioni della VM (Virtual Machine), accedi al client web vSphere, passa a **Home** > **Update Manager** > **Manage** > **Settings** e **VM Settings** e fai clic su **Edit**.

##	Host/Cluster Settings
{: #vum-metadata-host-settings}

Per modificare le impostazioni di host e cluster, accesi al client web vSphere, passa a **Home** > **Update Manager** > **Manage** > **Settings** e **Host/Cluster Settings** e fai clic su **Edit**.

## Link correlati
{: #vum-metadata-related}

* [VMware HCX on {{site.data.keyword.cloud_notm}} Solution Architecture](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (dimostrazioni)
