---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-20"

---

# Sécurisation des instances VMware Federal

Procédez comme suit pour sécuriser votre instance VMware Federal déployée, autrement dit, pour retirer la connexion de gestion ouverte pour l'accès en cours à l'instance :

## Avant de commencer

Passez en revue les informations suivantes afin de comprendre les résultats de la sécurisation de votre instance VMware Federal déployée :

* Avant d'effectuer cette procédure, enregistrez et sauvegardez toutes les données d'identification nécessaires pour votre environnement. Toutes les données d'identification de votre environnement sont effacées de la base de données {{site.data.keyword.vmwaresolutions_full}} et ne sont plus récupérables une fois l'action de sécurisation démarrée. 
* A l'exception d'une suppression d'instance complète, toutes les autres fonctions de gestion sont désactivées après le démarrage de l'action de sécurisation.

## Procédure de sécurisation d'instances VMware Federal

1. A partir de la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Instances déployées** dans le panneau de navigation de gauche.
2. Dans le tableau **Instances vCenter Server**, cliquez sur l'instance à sécuriser.
3. Cliquez sur l'icône de menu déroulant dynamique située en regard de **Console vCenter**.
4. Cliquez sur **Sécuriser une instance**.
5. Cliquez sur **OK** pour confirmer que vous voulez déconnecter l'instance de l'automatisation.

  **Remarque** : avant d'exécuter cette étape, prenez soin de passer en revue les informations contenues dans la section **Avant de commencer**.

6. Retirez de votre environnement les services de gestion face au public VMware NSX Edge Services Gateway (ESG) et éventuellement votre ESG géré par le client et qui a été déployé au cours de l'automatisation.
7. Réinitialisez les mots de passe ou les clés pour tous les qui sont comptes utilisés par l'automatisation IBM. Pour plus d'informations, voir [How can I secure my environment to remove access by IBM automation and support?](https://developer.ibm.com/answers/questions/452354/how-can-i-secure-my-environment-to-remove-access-b/)

## Résultats

L'instance prend le statut **Modification en cours**.

Une fois l'instance correctement sécurisée, elle prend le statut **Sécurisé** et seuls les propriétés de l'instance et l'historique de déploiement sont disponibles.

### Liens connexes

* [Présentation de VMware Federal on {{site.data.keyword.cloud_notm}}](vc_fed_overview.html)
* [Commande d'instances VMware Federal](vc_fed_orderinginstance.html)
* [Affichage des instances VMware Federal](vc_fed_viewinginstance.html)
* [Suppression d'instances VMware Federal](vc_fed_deletinginstance.html)
* [Contacter le support IBM](../vmonic/trbl_support.html)
