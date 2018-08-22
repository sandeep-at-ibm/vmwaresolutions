---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-27"

---

# Présentation de HyTrust DataControl on IBM Cloud

Le service HyTrust DataControl on {{site.data.keyword.cloud}} offre un chiffrement renforcé avec une gestion de clés intégrée permettant de sécuriser les charges de travail tout au long de leur cycle de vie. Le service peut fournir un chiffrement au niveau du système d'exploitation et au niveau des données, ce qui signifie que n'importe quel répertoire, dossier ou fichier d'une charge de travail peut être chiffré et déchiffré.

**Disponibilité :** ce service n'est disponible que pour les instances qui exécutent vSphere 6.5 et qui sont déployées dans (ou mises à niveau vers) la version 2.3 ou des éditions ultérieures.

## Spécifications techniques relatives à HyTrust DataControl on IBM Cloud

Les composants suivants sont commandés et inclus dans le service HyTrust DataControl on {{site.data.keyword.cloud_notm}} :

### Dispositif HyTrust DataControl
* UC : 2 vCPU
* Mémoire RAM : 8 Go
* Disque : VMDK 20 Go résident sur vSAN dans un cluster convergé
* Réseau : Placé sur un réseau portable privé VLAN spécifié pour la gestion

### Haute disponibilité
Deux dispositifs DataControl déployés dans une configuration active-active

### Licences et frais

Licence par hôte : une licence HyTrust DataControl est commandée pour chaque hôte de l'environnement

## Remarques relatives au retrait de HyTrust DataControl on IBM Cloud

Avant de retirer le service HyTrust DataControl on {{site.data.keyword.cloud_notm}}, prenez soin de chiffrer ou sauvegarder tous les disques à partir de DataControl. Il est possible que le retrait du service entraîne la suppression des clés, auquel cas, vous vous verrez peut-être refuser l'accès à vos machines virtuelles.

### Liens connexes

* [Commande de HyTrust DataControl on {{site.data.keyword.cloud_notm}}](htdc_ordering.html)
* [Gestion de HyTrust DataControl on {{site.data.keyword.cloud_notm}}](managinghtcc.html)
* [Contacter le support IBM](../vmonic/trbl_support.html)
* [Foire aux questions](../vmonic/faq.html)
* [Site Web HyTrust](https://www.hytrust.com/)
