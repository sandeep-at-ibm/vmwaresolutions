---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-14"

---

# Présentation de HyTrust DataControl on IBM Cloud

Le service HyTrust DataControl on {{site.data.keyword.cloud}} offre un chiffrement renforcé avec une gestion de clés intégrée permettant de sécuriser les charges de travail tout au long de leur cycle de vie. Le service peut fournir un chiffrement au niveau du système d'exploitation et au niveau des données, ce qui signifie que n'importe quel répertoire, dossier ou fichier d'une charge de travail peut être chiffré et déchiffré.

**Disponibilité :** ce service n'est disponible que pour les instances qui exécutent vSphere 6.5 et qui sont déployées dans (ou mises à niveau vers) la version 2.3 ou des éditions ultérieures.

## Composants de HyTrust DataControl on IBM Cloud

Une paire à haute disponibilité de dispositifs HyTrust DataControl (HTDC) est déployée sur le cluster par défaut en mode actif-actif. Les dispositifs HTDC sont sous licence pour fournir la fonctionnalité HyTrust KeyControl à vos charges de travail.

Chaque paire de dispositifs HTDC est déployée sur le même sous-réseau portable que celui spécifié pour les machines virtuelles de gestion, par exemple, NSX Manager, vCenter Server Appliances et Platform Services Controller. Les dispositifs sont acheminés via les routeurs client de back end
{{site.data.keyword.cloud_notm}} (BCR) et se voient affecter la passerelle qui est associée au sous-réseau de machines virtuelles de gestion. En outre, les dispositifs sont placés sur la stockage par défaut du cluster par défaut.

## Remarques relatives au retrait de HyTrust DataControl on IBM Cloud

Avant de retirer le service HyTrust DataControl on {{site.data.keyword.cloud_notm}}, prenez soin de chiffrer ou sauvegarder tous les disques à partir de DataControl. Il est possible que le retrait du service entraîne la suppression des clés, auquel cas, vous vous verrez peut-être refuser l'accès à vos machines virtuelles.

## Liens connexes

* [Commande de HyTrust DataControl on {{site.data.keyword.cloud_notm}}](htdc_ordering.html)
* [Gestion de HyTrust DataControl on {{site.data.keyword.cloud_notm}}](managinghtcc.html)
* [Contacter le support IBM](../vmonic/trbl_support.html)
* [Foire aux questions](../vmonic/faq.html)
* [Site Web HyTrust](https://www.hytrust.com/)
