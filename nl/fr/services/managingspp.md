---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-07"

---

# Gestion d'IBM Spectrum Protect Plus on IBM Cloud

## Accès à la console de gestion d'IBM Spectrum Protect Plus

Pour gérer le service IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud}}, vous devez accéder à la console de gestion d'IBM Spectrum Protect Plus en procédant comme suit :
1. Utilisez le réseau privé virtuel de l'infrastructure {{site.data.keyword.cloud_notm}} ou un serveur de saut pour autoriser l'accès à l'adresse IP de la machine virtuelle IBM Spectrum Protect Plus. Vous trouverez l'adresse IP sur la page des détails d'IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} dans la console {{site.data.keyword.vmwaresolutions_short}}.
2. Pour accéder à la console de gestion d'IBM Spectrum Protect Plus, cliquez sur **Afficher la console IBM Spectrum Protect Plus** sur la page des détails de service d'IBM Spectrum Protect Plus on {{site.data.keyword.cloud}}, puis connectez-vous à l'aide des données d'identification répertoriées sur cette même page des détails de service.

## Application de correctifs pour IBM Spectrum Protect Plus on IBM Cloud

C'est à vous de veiller à maintenir le service IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} dans la version la plus récente. Vous pouvez télécharger les mises à jour requises à partir de la page de [support d'IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](https://www.ibm.com/mysupport/s/topic/0TO50000000IQWtGAO/spectrum-protect-plus). 

Pour plus d'informations, voir les rubriques suivantes :
* [Commande, affichage et retrait de services pour des instances Cloud Foundation](../sddc/sd_addingremovingservices.html)
* [Commande, affichage et retrait de services pour des instances vCenter Server](../vcenter/vc_addingremovingservices.html)

## Mise à jour du système d'exploitation de la machine virtuelle IBM Spectrum Protect Plus

Pour mettre à jour le système d'exploitation de la machine virtuelle IBM Spectrum Protect Plus, vous devez vous connecter en tant qu'utilisateur **root**. Le mot de passe de l'utilisateur **root**  est le mot de passe indiqué sur la page des détails d'IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}.

## Sauvegarde et restauration de composants de gestion pour des instances sur lesquelles IBM Spectrum Protect Plus on IBM Cloud est installé

 **Remarque** : les informations suivantes s'appliquent aux installations d'IBM Spectrum Protect sur des instances déployées dans (ou mises à niveau vers) V2.3 ou une édition ultérieure. Pour les instances V2.2, ce service assure la protection des données uniquement pour les machines virtuelles de charge de travail.

Le service IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} est préconfiguré avec une tâche de sauvegarde de gestion qui s'exécute automatiquement pour sauvegarder tous les jours les composants de gestion jusqu'à sept points de restauration :
* VMware vCenter Server
* Contrôleur PSC (Platform Services Controller)
* IBM CloudDriver
* **Instances Cloud Foundation uniquement** : VMware SDDC Manager
* **Instances vCenter Server avec AD/DNS à haute disponibilité uniquement** : paire à haute disponibilité de serveurs AD/DNS

En cas d'incidents sur les composants de gestion, vous pouvez ouvrir un ticket en [contactant le support IBM](../vmonic/trbl_support.html) afin de demander la restauration des composants de gestion sur une sauvegarde précédente. 

## Liens connexes

* [Présentation d'IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](spp_considerations.html)
* [How to increase vsnap storage for IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} post deployment](https://developer.ibm.com/recipes/tutorials/how-to-increase-vsnap-storage-for-ibm-spectrum-protect-plus-on-ibm-cloud-post-deployment/)
* [Documentation IBM Spectrum Protect Plus](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ/landing/welcome_ssnqfq.html)
