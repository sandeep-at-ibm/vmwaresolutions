---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-14"

---

# Présentation de HyTrust CloudControl on IBM Cloud

Le service HyTrust CloudControl on {{site.data.keyword.cloud}} applique et contrôle la conformité par rapport aux normes de sécurité standard et fournit un contrôle d'accès à base de rôles et des fonctions d'approbation et d'audit. Combiné à HyTrust DataControl, le service garantit que les machines virtuelles et les données de charge de travail ne quittent pas une région, un cluster ou un serveur ESXi donnés au sein de l'{{site.data.keyword.CloudDataCent_notm}}.

**Disponibilité :** ce service n'est disponible que pour les instances qui exécutent vSphere 6.5 et qui sont déployées dans (ou mises à niveau vers) la version 2.3 ou des éditions ultérieures.

## Composants de HyTrust CloudControl on IBM Cloud

Une paire à haute disponibilité de dispositifs HyTrust CloudControl (HTCC) est déployée sur le cluster par défaut en mode actif-passif.

Chaque paire de dispositifs HTCC est déployée sur le même sous-réseau portable privé que celui spécifié pour les machines virtuelles de gestion, par exemple, NSX Manager, vCenter Server Appliances et Platform Services Controller.

La paire de dispositifs agit comme un proxy pour les hôtes vSphere, le dispositif vCenter Server et le gestionnaire NSX Manager d'une instance. Par conséquent, les utilisateurs accèdent aux hôtes vSphere, à vCenter Server Appliance et à NSX Manager via une adresse IP publiée (PIP) affectée par l'administrateur au lieu de l'adresse IP réelle (RIP) affectée par {{site.data.keyword.cloud}}. 

Les dispositifs HTCC s'intègrent à Microsoft Active Directory pour appliquer le contrôle d'accès à base de rôles. 

## Remarques relatives au retrait de HyTrust CloudControl on IBM Cloud

Avant de retirer le service HyTrust DataControl on {{site.data.keyword.cloud_notm}}, prenez soin de désactiver la **la mise en lieu sûr par mot de passe root**, si elle est configurée, et de supprimer tous les hôtes protégés sur HyTrust DataControl. 

## Liens connexes

* [Commande de HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](htcc_ordering.html)
* [Gestion de HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](managinghtcc.html)
* [Contacter le support IBM](../vmonic/trbl_support.html)
* [Foire aux questions](../vmonic/faq.html)
* [Site Web HyTrust](https://www.hytrust.com/)
