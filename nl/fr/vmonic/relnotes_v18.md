---

copyright:

  years:  2016, 2018

lastupdated: "2017-08-28"

---

# Notes sur l'édition pour la version 1.8

Cette édition inclut de nouvelles fonctionnalités, des mises à jour de composant, des améliorations d'utilisation et des corrections d'erreur. Pour la liste des erreurs rectifiées dans les différentes éditions, les problèmes connus concernant le produit et des conseils supplémentaires pour l'utilisation d'{{site.data.keyword.vmwaresolutions_full}}, voir [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Service Fortinet on IBM Cloud

Le service Fortinet on {{site.data.keyword.cloud_notm}} est désormais disponible pour les instances Cloud Foundation et vCenter Server. Ce service déploie une paire de dispositifs FortiGate Security Appliance (FSA) série 300 en mode haute disponibilité, qui fournissent des services de pare-feu, de routage, de conversion d'adresses réseau (NAT) et de réseau privé virtuel (VPN) afin de protéger tous les serveurs et machines virtuelles sur le réseau privé virtuel (VLAN) de vos instances. Vous pouvez commander des instances avec le service Fortinet déjà inclus ou vous pouvez ajouter ultérieurement ce service à vos instances existantes à partir de la page des détails d'instance.

Une fois le service Fortinet correctement installé, vous pouvez gérer et configurer des règles de pare-feu pour FortiGate Security Appliance (FSA) depuis la console FortiGate. Vous devez vous assurer que les règles de pare-feu de FortiGate Security Appliance (FSA) sont définies de manière à autoriser les communications HTTPS sortantes initiées par des composants de gestion, tels que la machine virtuelle IBM CloudDriver ou le gestionnaire virtuel Zerto, pour communiquer avec la base de données de gestion externe sur IBM Bluemix® via Internet. Les communications HTTPS sortantes proviennent de l'adresse IP publique des services de gestion VMware NSX Edge Services Gateway (ESG) de votre instance.

Pour plus d'informations, voir :
* [Présentation de Fortinet on {{site.data.keyword.cloud_notm}}](../services/fsa_considerations.html)
* [Gestion de Fortinet on {{site.data.keyword.cloud_notm}}](../services/managingfsa.html)

## Service Veeam on IBM Cloud

Cette édition introduit le service Veeam on {{site.data.keyword.cloud_notm}}, capable de sauvegarder aussi bien des composants de gestion que des charges de travail. Ce nouveau service remplace les instances de serveur virtuel Veeam précédentes intégrées aux éditions antérieures à la version 1.8 pour la sauvegarde des composants de gestion uniquement.

En raison de cette modification, et bien que les instances de serveur virtuel Veeam des instances antérieures à la version 1.8 fonctionnent toujours, les points de sauvegarde des instances ne sont plus disponibles sur la console {{site.data.keyword.vmwaresolutions_short}}, et vous devez créer un ticket de demande de service pour obtenir de l'aide dans l'exécution d'une restauration.

De plus, la licence de l'instance de serveur virtuel Veeam des instances de version antérieure à 1.8 a expiré le 14 octobre 2017. Par conséquent, vous devez remplacer l'ancienne instance de serveur virtuel Veeam par le nouveau service Veeam dès que possible.

Pour plus d'informations, voir :
* [Présentation de Veeam on {{site.data.keyword.cloud_notm}}](../services/veeam_considerations.html)
* [Gestion de Veeam on {{site.data.keyword.cloud_notm}}](../services/managingveeam.html)

## Mises à jour des instances VMware Cloud Foundation

### Apport de vos propres licences (BYOL, Bring your own VMware license) lors de la commande d'instances Cloud Foundation

A compter de l'édition de la version 1.8, lorsque vous commandez une instance Cloud Foundation, vous avez le choix entre deux options d'octroi de licence aux composants VMware de l'instance, y compris vSphere, vCenter Server, NSX et vSAN. Vous pouvez choisir d'utiliser de nouvelles licences qui sont achetées pour votre compte.

Mais vous pouvez également choisir d'utiliser votre propre licence VMware pour un composant, et vous devez alors fournir la clé de licence. Dans ce cas, la prise en charge des composants VMware pour lesquels vous fournissez des licences sera assurée par VMware et non par le support IBM.

Pour plus d'informations, voir :
* [Commande d'instances Cloud Foundation](../sddc/sd_orderinginstance.html)
* [Foire aux questions sur le mode BYOL](faq_byol.html)

## Mises à jour des instances VMware vCenter Server

### Personnalisez l'UC et la mémoire de votre instance

Une option de serveur personnalisable est disponible avec les options Petite, Moyenne et Grande préconfigurées et testées. Vous pouvez sélectionner dans une liste de serveurs VMware compatibles HCL sur la base des doubles UC et du nombre total de coeurs, en plus de la quantité de RAM. Le stockage local n'est pas personnalisable.

Pour plus d'informations, voir :
* [Commande d'instances vCenter Server](../vcenter/vc_orderinginstance.html)
* [Ajout et affichage des clusters des instances vCenter Server](../vcenter/vc_addingviewingclusters.html)

### Prise en charge pour l'ajout de plus de 7 partages de fichiers NFS

 Vous pouvez associer jusqu'à 32 partages de fichiers au maximum entre tous les serveurs ESXi d'un cluster.

 Pour plus d'informations, voir :
* [Commande d'instances vCenter Server](../vcenter/vc_orderinginstance.html)
* [Ajout et affichage des clusters des instances vCenter Server](../vcenter/vc_addingviewingclusters.html)

### Mises à jour des centres de données

Les nouveaux centres de données suivants sont disponibles pour déploiement : **DAL-09, DAL-12, DAL-13 - Dallas**; **LON-04, LON-06 - Londres**; **SJC-04 - San José**; **WDC-06, WDC-07 - Washington, DC**

Pour plus d'informations, voir [Exigences et planification pour les instances vCenter Server](../vcenter/vc_planning.html)

## Améliorations de la convivialité

Des améliorations ont été apportées à l'interface utilisateur, à savoir :
* Vous pouvez en savoir plus sur les services et commander une instance sur la page **Initiation** du panneau de navigation de gauche. Pour plus d'informations sur l'architecture du service de virtualisation sécurisé d'{{site.data.keyword.cloud_notm}}, voir [Security and compliance - HyTrust](https://www.ibm.com/devops/method/content/architecture/virtCloudFoundationPlatform/hytrust).
* Utilisez le menu déroulant dynamique de la page des détails de l'instance pour supprimer une instance dont le statut est **Prêt à l'emploi**.
* L'option de mise à niveau de votre édition de licence NSX est désormais disponible sur l'onglet **Mise à jour et module de correction**. La mise à niveau de la licence remplace toutes les licence NSX existantes de votre compte IBM SoftLayer par la nouvelle licence.
* L'onglet **Sauvegarde et restauration** de la page des détails de l'instance n'est plus disponible.
* Vous pouvez sélectionner plusieurs services à déployer au début d'une commande. En plus du service Zerto on {{site.data.keyword.cloud_notm}}, des options de sélection du service Veeam on {{site.data.keyword.cloud_notm}} et du service Fortinet on {{site.data.keyword.cloud_notm}} sont également disponibles.
* L'onglet **Services disponibles** sous l'onglet **Services** de la page des détails de l'instance a été renommé **Ajouter des services**.
