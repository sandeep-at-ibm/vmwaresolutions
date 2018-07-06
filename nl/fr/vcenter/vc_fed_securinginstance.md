---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-24"

---

# Sécurisation des instances VMware Federal

Procédez comme suit pour sécuriser votre instance VMware Federal déployée, autrement dit, pour retirer la connexion de gestion ouverte pour l'accès en cours à l'instance :

## Avant de commencer

Passez en revue les informations suivantes afin de comprendre les résultats de la sécurisation de votre instance VMware Federal déployée :

* Avant d'effectuer cette procédure, enregistrez et sauvegardez toutes les données d'identification nécessaires pour votre environnement. Toutes les données d'identification de votre environnement sont effacées de la base de données {{site.data.keyword.vmwaresolutions_full}} et ne sont plus récupérables une fois l'action de sécurisation appelée.
* A l'exception d'une suppression d'instance complète, toutes les fonctions de gestion sont désactivées après l'appel de l'action de sécurisation.
* La passerelle VMware NSX Edge Services Gateway (ESG) pour le trafic de gestion HTTPS sortant est supprimée dans le cadre de l'action de sécurisation de votre instance VMware Federal déployée.

## Procédure

1. A partir de la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Instances déployées** dans le panneau de navigation de gauche.
2. Dans le tableau **Instances vCenter Server**, cliquez sur l'instance à sécuriser.
3. Cliquez sur l'icône de menu déroulant dynamique à droite de **Console vCenter**.
4. Cliquez sur **Sécuriser une instance**.
5. Cliquez sur **OK** pour confirmer que vous voulez déconnecter l'instance de l'automatisation.
   
   **Remarque** : avant d'exécuter cette étape, prenez soin de passer en revue les informations contenues dans la section **Avant de commencer**.

## Résultats

L'instance prend le statut **Modification en cours**.

Une fois l'instance correctement sécurisée, elle prend le statut **Sécurisé** et seuls les propriétés de l'instance et l'historique de déploiement sont disponibles.

## Liens connexes

* [Présentation de VMware Federal on IBM Cloud](vc_fed_overview.html)
* [Commande d'instances VMware Federal](vc_fed_orderinginstance.html)
* [Affichage des instances VMware Federal](vc_fed_viewinginstance.html)
* [Suppression d'instances VMware Federal](vc_fed_deletinginstance.html)
* [Contacter le support IBM](../vmonic/trbl_support.html)
