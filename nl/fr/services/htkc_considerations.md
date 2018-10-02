---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-11"

---

# Présentation de HyTrust KeyControl on IBM Cloud

Le service HyTrust KeyControl on {{site.data.keyword.cloud}} simplifie la gestion des charges de travail chiffrées en automatisant et en simplifiant le cycle de vie des clés de chiffrement, y compris le stockage des clés, la distribution des clés, la rotation des clés et la révocation des clés. Lorsqu'elles utilisent le chiffrement compatible FIPS 140-2, les entreprises peuvent facilement gérer des clés de chiffrement à grande échelle.
 

**Disponibilité :** ce service n'est disponible que pour les instances qui exécutent vSphere 6.5 et qui sont déployées dans (ou mises à niveau vers) la version 2.5 ou des éditions ultérieures.

## Spécifications techniques relatives à HyTrust KeyControl on IBM Cloud

Les composants suivants sont commandés et inclus dans le service HyTrust KeyControl on {{site.data.keyword.cloud_notm}} :

### Dispositif HyTrust KeyControl

* UC : 2 vCPU
* Mémoire RAM : 8 Go
* Disque : VMDK 20 Go résident sur vSAN dans un cluster convergé
* Réseau : Placé sur un réseau portable privé VLAN spécifié pour la gestion

### Haute disponibilité

Par défaut, deux dispositifs KeyControl sont déployés dans une configuration en cluster active-active. 

Vous pouvez éventuellement indiquer que deux dispositifs KeyControl doivent être déployés dans une configuration autonome autre qu'une configuration en cluster. 

### Licences et frais

Une licence HyTrust KeyControl est commandée pour chaque installation d'instance. 

## Remarques relatives au retrait de HyTrust KeyControl on IBM Cloud

Avant de retirer le service HyTrust KeyControl on {{site.data.keyword.cloud_notm}}, prenez soin de dissocier tous les clients de l'utilisation de KeyControl. Il est possible que le retrait du service entraîne la suppression des clés, auquel cas, vous vous verrez peut-être refuser l'accès à vos machines virtuelles.

### Liens connexes

* [Commande de HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](htkc_ordering.html)
* [Gestion de HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](managinghtkc.html)
* [Contacter le support IBM](../vmonic/trbl_support.html)
* [Foire aux questions](../vmonic/faq.html)
* [Site Web HyTrust](https://www.hytrust.com/)
