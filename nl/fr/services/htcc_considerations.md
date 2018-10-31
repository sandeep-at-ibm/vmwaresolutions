---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-26"

---

# Présentation de HyTrust CloudControl on IBM Cloud

Le service HyTrust CloudControl on {{site.data.keyword.cloud}} applique et contrôle la conformité par rapport aux normes de sécurité standard, notamment le contrôle d'accès à base de rôles (RBAC) et les fonctions d'approbation et d'audit. Combiné à HyTrust DataControl, ce service garantit que les machines virtuelles et les données de charge de travail ne sortent pas d'une région, d'un cluster ou d'un serveur ESXi spécifique au sein de l'{{site.data.keyword.CloudDataCent_notm}}.

**Disponibilité :** ce service n'est disponible que pour les instances qui exécutent vSphere 6.5 et qui sont déployées dans, ou mises à niveau vers, la version 2.3 ou des éditions ultérieures.

## Spécifications techniques relatives à HyTrust CloudControl on IBM Cloud

Les composants suivants sont commandés et inclus dans le service HyTrust CloudControl on {{site.data.keyword.cloud_notm}} :

### Dispositif HyTrust CloudControl

* UC : 4 vCPU
* Mémoire RAM : 16 Go
* Disque : VMDK 70 Go résident sur vSAN dans un cluster convergé
* Réseau : Placé sur un réseau portable privé VLAN spécifié pour la gestion

### Haute disponibilité

Deux dispositifs CloudControl déployés dans une configuration active-passive

### Licences et frais

Licence par hôte : une licence HyTrust CloudControl est commandée pour chaque hôte de l'environnement

## Considérations à prendre en compte lorsque vous retirez HyTrust CloudControl on IBM Cloud

Avant de retirer le service HyTrust CloudControl on {{site.data.keyword.cloud_notm}}, prenez soin de désactiver la **mise en lieu sûr par mot de passe root**, si elle est configurée, et de supprimer tous les hôtes protégés sur HyTrust CloudControl.

### Liens connexes

* [Commande de HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](htcc_ordering.html)
* [Gestion de HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](managinghtcc.html)
* [Contacter le support IBM](../vmonic/trbl_support.html)
* [Foire aux questions](../vmonic/faq.html)
* [Site Web HyTrust](https://www.hytrust.com/)
