---

copyright:

  years:  2016, 2018

lastupdated: "2017-12-29"

---

# Aide à l'identification et la résolution des problèmes

## Problème

Dans certaines situations, un problème plus complexe peut se produire et les fichiers journaux ne suffisent pas pour effectuer une analyse de la cause première et fournir une solution.

## Résolution

Pour identifier et résoudre ce type de problème, L'équipe du support {{site.data.keyword.vmwaresolutions_full}} doit pouvoir accéder à la machine virtuelle de gestion de gestion {{site.data.keyword.cloud_notm}}. Cette machine virtuelle de gestion, appelée IBM CloudDriver, est la principale interface utilisée pour gérer les instances VMware Cloud Foundation et VMware vCenter Server déployées.

Pour des raisons de sécurité, l'accès à IBM CloudDriver est restreint. L'équipe du support {{site.data.keyword.vmwaresolutions_short}} demande l'approbation du client et, après l'avoir obtenue, peut accéder au composant CloudDriver à l'aide d'un serveur virtuel de l'infrastructure {{site.data.keyword.cloud_notm}}. Ce serveur fait office de pont vers l'environnement via le réseau public FCR (Frontend Customer Router) de l'infrastructure {{site.data.keyword.cloud_notm}}.

Ensuite, l'équipe du support {{site.data.keyword.vmwaresolutions_short}} utilise la clé {{site.data.keyword.slapi_short}} de l'infrastructure {{site.data.keyword.cloud_notm}} fournie pour commander et configurer l'instance (ou, au besoin, la clé mise à jour fournie par le client) pour déployer un serveur virtuel de l'infrastructure {{site.data.keyword.cloud_notm}} sur une base horaire.

Le compte client est facturé pour l'utilisation des outils IBM CloudBuilder à des fins d'identification et résolution des problèmes. Une fois le débogage et la résolution terminés, le composant IBM CloudBuilder est libéré.

Le serveur virtuel de l'infrastructure {{site.data.keyword.cloud_notm}} utilisé pour l'identification et résolution des problèmes est déployé avec les spécifications suivantes :

* Une instance de service virtuel de noeud public CentOS 7 est utilisée avec 1 UC et 1 Go de RAM.
* L'instance de service virtuel est déployée dans le même centre de données sur les mêmes réseaux locaux virtuels (VLAN) public et privé principaux que l'instance.
* Un script de post-installation est utilisé avec le déploiement de l'instance de service virtuel afin de définir des règles de pare-feu qui autorisent uniquement les connexions SSH entrantes provenant d'un ensemble donné d'adresses IP dont l'équipe de support {{site.data.keyword.vmwaresolutions_short}} est propriétaire et qu'elle utilise.
* Le système de lancement du support qui utilise ces adresses IP s'exécute sur une machine virtuelle de l'infrastructure {{site.data.keyword.cloud_notm}} accessible uniquement via un réseau de l'infrastructure {{site.data.keyword.cloud_notm}} privé et sécurisée à l'aide d'une paire de systèmes Vyatta de l'infrastructure {{site.data.keyword.cloud_notm}} haute disponibilité.
* Des outils de sécurité IBM, tels que QRadar®, Nessus et IBM BigFix®, sont utilisés pour intercepter sur le système de lancement du support les menaces de sécurité.
