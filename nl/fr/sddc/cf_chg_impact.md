---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-05"

---

# Remarques relatives à la modification des artefacts Cloud Foundation

Modifier des utilisateurs, des ressources ou des sous-réseaux réservés à {{site.data.keyword.vmwaresolutions_full}} peut avoir une incidence sur des opérations de gestion des instances VMware Cloud Foundation.

**Important :** ne modifiez pas les droits globaux du groupe **ic4v-vCenter** sur la page **Utilisateurs et groupes** du client Web VMware vSphere. Les modifications de droits globaux incluent la modification du nom d'utilisateur, la suppression de l'utilisateur ou la modification de son mot de passe.

## Comptes utilisateur de service

Chaque service crée un compte utilisateur interne dans vCenter Server. Ce compte est nécessaire pour que les opérations de gestion associées à un service puissent se connecter à vCenter Server afin d'effectuer les opérations sur le service.

**Important :** pour éviter les indisponibilités et les problèmes de connexion, si vous modifiez l'ID utilisateur, le mot de passe ou les paramètres d'expiration de mot de passe pour ce compte utilisateur, prenez soin de mettre également à jour les informations dans le service associé.

L'ID utilisateur de ce compte est au format `<service_name>-<truncated service_uuid>@test.local` ou `<service_name>-<truncated service_uuid>@example-domain.local`. Par exemple, l'ID utilisateur dont se sert le service Veeam on {{site.data.keyword.cloud_notm}} pour se connecter à vCenter Server afin d'effectuer des sauvegardes planifiées est `Veeam-<Veeam_uuid>@test.local`.

**Remarque :** le nom du service (`<service_name>`) ainsi que l'identificateur unique universel `<service_uuid>` est tronqué à 20 caractères.

## Ressources VMware pour les instances Cloud Foundation

Le tableau suivant répertorie les opérations susceptibles d'être affectées lorsque vous modifiez des ressources VMware en dehors de la console {{site.data.keyword.vmwaresolutions_short}}. Si une solution de récupération est disponible, elle est également fournie.

Tableau 1. Opérations affectées pour l'administrateur de la connexion unique (client)

| Modification  | Opérations affectées  | Gravité  | Méthode de récupération  |
|:------------- |:------------- |:--------------|:--------------|
| Modification du nom du centre de données virtuel VMware. | L'ajout d'un centre de données VMware risque d'échouer car le nouveau serveur ESXi ne peut pas contacter le centre de données modifié. | Important | Redonnez au centre de données virtuel VMware son nom d'origine. |
| Modification de noms de groupes de ports.    | L'ajout d'un serveur ESXi risque d'échouer. | Important | Redonnez au groupe de ports son nom d'origine. |
| Modification du nom de cluster. | L'ajout d'un serveur ESXi risque d'échouer. | Important | Redonnez au cluster son nom d'origine.
| Modification du nom du commutateur virtuel distribué (DVS, Distributed Virtual Switch) public ou privé. | L'ajout d'un serveur ESXi risque d'échouer. | Important | Redonnez au DVS son nom d'origine.
| Modification du nom du magasin de données VSAN. | L'ajout d'un serveur ESXi risque d'échouer.<br><br>La mise à niveau de l'instance risque d'échouer. | Important | Redonnez au magasin de données VSAN son nom d'origine, soit **vsanDatastore**.
| Modification du nom d'instance ou du nom de domaine. | L'instance est inutilisable. | Critique | Non applicable

Le tableau suivant répertorie les opérations susceptibles d'être affectées lorsque l'accès à SSH ou à l'interpréteur de commandes est désactivé pour différentes ressources. 

Tableau 2. Opérations affectées pour l'accès à SSH et à l'interpréteur de commandes (local)

| Modification  | Opérations affectées  | Gravité  | Méthode de récupération  |
|:------------- |:------------- |:--------------|:--------------|
| Désactiver l'accès à SSH ou à l'interpréteur de commandes pour vCenter Server ou PSC. | L'appariement d'une instance principale et d'une instance secondaire peut échouer. L'application de correctifs aux ressources peut échouer. | Important    | Non applicable    |
| Désactiver l'accès à SSH ou à l'interpréteur de commandes pour ESXi. | L'ajout et le retrait d'hôtes, de services et de stockage réseau à l'instance peut échouer. L'application de correctifs aux ressources peut échouer. | Important    | Non applicable    |

Si vous choisissez de désactiver l'accès à SSH ou à l'interpréteur de commandes, vous devez le réactiver temporairement avant d'effectuer les opérations indiquées. 

## Gestion de sous-réseaux pour les instances Cloud Foundation

Les informations suivantes concernent les sous-réseaux commandés par {{site.data.keyword.vmwaresolutions_short}} et indiquent les options de commande de sous-réseaux supplémentaires à votre usage personnel dont vous disposez.

**ATTENTION :** n'utilisez pas ces composants à d'autres fins ; vous risqueriez de compromettre grandement la stabilité de votre environnement.

Avec chaque commande de serveur bare metal {{site.data.keyword.cloud_notm}}, les plages d'adresses IP suivantes sont commandées par défaut :

*  Une plage publique principale de 32 adresses IP
*  Une plage privée principale de 64 adresses IP

De plus, les sous-réseaux de gestion suivants sont également réservés pour {{site.data.keyword.vmwaresolutions_short}} :

*  Deux sous-réseaux privés portables de 64 adresses IP sur le premier réseau local virtuel : un pour la gestion et l'autre pour le noeud final VTEPS.
*  Deux sous-réseaux privés portables de 64 adresses IP sur le second réseau local virtuel : un pour vMotion et l'autre pour vSAN.
*  Un sous-réseau public portable de 16 adresses IP sur le réseau local virtuel public.

Si vous avez besoin de davantage de sous-réseaux, vous pouvez obtenir des adresses IP à utiliser de l'une des manières suivantes :

* **Option 1 (recommandée) :** utilisez les superpositions de réseaux virtuels de VMware NSX. Un exemple de modèle VXLAN est fourni lors de la commande. Ce modèle VXLAN peut être utilisé comme point de départ pour la génération de la mise en réseau définie par logiciel.
* **Option 2 :** commandez vos propres sous-réseaux portables publics ou privés afin d'obtenir des adresses IP. Pour différentier les sous-réseaux que vous commandez des sous-réseaux de gestion, vous pouvez ajouter des notes aux sous-réseaux commandés.
