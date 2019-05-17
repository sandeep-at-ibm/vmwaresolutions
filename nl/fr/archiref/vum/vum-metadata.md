---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-25"

subcollection: vmware-solutions


---

#	Collecte des métadonnées
{: #vum-metadata}

VUM télécharge des métadonnées sur les mises à niveau, les correctifs ou les extensions via un processus automatique prédéfini que vous pouvez modifier. A intervalles réguliers pouvant être configurés, VUM contacte VMware ou des sources tierces, pour rassembler les métadonnées les plus récentes sur les mises à niveau, les correctifs ou les extensions disponibles. Cependant, les paramètres par défaut de VMware sont acceptables pour une utilisation avec l'instance VMware vCenter Server on {{site.data.keyword.cloud}}, vous pouvez les modifier si nécessaire en fonction des exigences de votre entreprise.

VUM affiche les lignes de base gérées par le système, générées par vSAN. Ces lignes de base effectuent la mise à jour automatique de leur contenu périodiquement, ce qui nécessite que VUM ait un accès constant à Internet. Les lignes de base du système vSAN sont en principe actualisées toutes les 24 heures.

Vous pouvez utiliser les lignes de base gérées par le système pour mettre à niveau vos clusters vSAN avec les correctifs critiques, les pilotes et les mises à jour recommandés ou avec la dernière version d'hôte ESXi prise en charge pour vSAN.

Pour la plupart des entreprises, les paramètres par défaut de VMware pour VUM sont considérés comme appropriés. Les informations suivantes indiquent comment modifier ces paramètres si votre entreprise souhaite utiliser d'autres paramètres.

##	Download Schedule
{: #vum-metadata-download-schedule}

Les mises à jour sont des mises à niveau de dispositifs virtuels, des correctifs d'hôte et des extensions. Par défaut, VUM télécharge les mises à jour quotidiennement. Modifiez ce comportement en accédant à vSphere Web Client, en cliquant sur **Home** > **Update Manager** > **Manage** > **Settings**, puis en sélectionnant **Download Schedule** et en cliquant sur **Edit**.

##	Notification Check Schedule
{: #vum-metadata-notif-check-schedule}

Les notifications sont des informations sur les rappels de correctif, les nouveaux correctifs et les alertes. Par défaut, VUM télécharge les notifications toutes les heures. Ce comportement peut être modifié en accédant à vSphere Web Client, en cliquant sur **Home** > **Update Manager** > **Manage** > **Settings**, puis en sélectionnant **Notification Check Schedule** et en cliquant sur **Edit**.

##	Virtual Machine Settings
{: #vum-metadata-vm-settings}

Pour modifier les paramètres de machine virtuelle, accédez à vSphere Web Client, sélectionnez **Home** > **Update Manager** > **Manage** > **Settings** et **VM Settings**, puis cliquez sur **Edit**.

##	Host/Cluster Settings
{: #vum-metadata-host-settings}

Pour modifier les paramètres d'hôte ou de cluster (Host/Cluster Settings), accédez à vSphere Web Client, cliquez sur **Home** > **Update Manager** > **Manage** > **Settings** et **Host/Cluster Settings**, puis cliquez sur **Edit**.

## Liens connexes
{: #vum-metadata-related}

* [VMware HCX on {{site.data.keyword.cloud_notm}} solution architecture](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-intro#hcx-archi-intro)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/vmware) (démonstrations)
