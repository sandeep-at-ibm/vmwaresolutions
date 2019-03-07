---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

# Etape 4 - Configuration de l'application
{: #caveonix-step4}

Une fois que les machines virtuelles sont déployées et que les composants de l'application sont installés, la solution Caveonix RiskForesight peut être configurée pour le fournisseur de service et le premier locataire ou la première organisation.

Le fournisseur de service est l'organisation de premier niveau et un ou plusieurs locataires ou organisations sont desservis par le fournisseur de service. Le fournisseur de service affecte les actifs qui sont collectés du vCenter au locataire ou aux organisations qui les affectent ensuite aux applications ou sous-applications. Ces applications sont ensuite soumises à un régime de conformité.

Cette étape est initialement exécutée par l'automatisation IC4VS qui utilise les informations fournies par le client lors du processus de commande et des informations par défaut. Le processus de configuration peut être démarré par le client lors d'un déploiement postérieur pour modifier le fournisseur de service ou l'organisation locataire selon les besoins après l'installation.

La configuration du fournisseur de service comporte huit sous-étapes :
-	Etape 1 : Détails de l'organisation - Ajoutez les détails de l'organisation parent globale de votre fournisseur de service de cloud. Cette organisation peut avoir plusieurs emplacements physiques et plusieurs centres de données. Les organisations de vos locataires et les sous-organisations de votre fournisseur de service sont ajoutées ultérieurement.
-	Etape 2 : Emplacements – Mappez l'infrastructure dans des "emplacements" RiskForesight. Les actifs sont regroupés par emplacement, fournisseur de cloud et référentiel d'actifs.
-	Etape 3 : Environnements - Facultatif. Les environnements constituent un moyen de grouper les actifs. Par exemple, DevOps, Site DR, Production.
-	Etape 4 : Fournisseur de cloud - Ajoutez les “fournisseurs” qui fournissent l'infrastructure sur laquelle votre application s'exécute.
-	Etape 5 : Référentiels d'actifs - Un référentiel d'actifs associe un ensemble d'actifs à une organisation, à une fournisseur de cloud et à un emplacement.
-	Etape 6 : Organisations - Créez une sous-organisation pour vos propres opérations et organisations additionnelles - une pour chacun des locataires de votre fournisseur de service. Chaque locataire doit effectuer son propre processus de configuration, y compris créer ses propres sous-organisations.
-	Etape 7 : Utilisateurs de l'organisation - Créez et affectez des utilisateurs aux organisations et aux sous-organisation locataires du fournisseur de service.
-	Etape 8 : Planificateur de tâches – Configurez des tâches pour : activer la synchronisation avec le référentiel d'actifs, effectuer des analyses de vulnérabilité et de conformité SCAP, collecter les flux de réseau NSX, collecter des informations sur le logiciel qui s'exécute sur les actifs surveillés, collecter les journaux système et les événements système des actifs.

La configuration du locataire ou de l'organisation comporte sept sous-étapes :

-	Etape 1 : Organisation - Ajoutez les détails de votre organisation principale. Vous pouvez également créer des sous-organisations. Utilisez les organisations pour segmenter vos utilisateurs, ou comme un moyen de regrouper vos actifs. Vous pouvez créer d'autres organisations avec l'une de vos organisations existantes comme parent. Lorsque vous créez une nouvelle organisation, vous pouvez sélectionner la "valeur d'impact métier", qui est utilisée pour générer des scores de risque cybernétique.
-	Etape 2 : Actifs de l'organisation - Les nouveaux actifs et les nouvelles charges de travail sont automatiquement regroupés par emplacement, fournisseur de cloud et référentiel d'actifs. Les actifs ne peuvent être affectés qu'à une seule organisation à la fois. Le fournisseur de service doit affecter les actifs à une organisation.
-	Etape 3 : Associer un environnement et un emplacement – Facultatif. Les environnements sont définis par le fournisseur de service.
-	Etapes 4 et 5 : Créez des sous-applications ou des applications – Cette étape permet de regrouper des actifs par emplacements ou organisations et de voir les flux et les politiques qui leur sont associés. Créez des applications qui correspondent à des services IT ou commerciaux. Par exemple, Application=SAP, Sous-applications=SAP Front End, SAP Middle Tier et SAP Back End. La valeur d'impact métier correspond à une application. Les régimes de conformité s'appliquent à une application. 
-	Etape 6 : Accès distant - Un accès distant est requis pour exécuter des analyses sur les actifs. Il peut s'agit d'un compte de service par défaut ou d'un compte spécifique à un actif.
-	Etape 7 : Planificateur de tâches - Planifiez des analyses à exécuter périodiquement. Les types de tâches incluent : l'analyse de vulnérabilité SCAP, l'analyse SCAP XCCDF, l'analyse de flux NSX, l'analyse logicielle, l'analyse d'extraction de journaux.

Les informations suivantes sont obtenues de l'utilisateur au moment de la commande et sont utilisées lors de la configuration de l'application.

Tableau 1. Informations obtenues de l'utilisateur

|Etape de configuration |Paramètre |
|---|---|
|Organisation / référentiels d'actifs  |Nom de l'organisation |
|Organisation |Numéro de téléphone |
|Organisation |Adresse e-mail |
|Organisation / référentiels d'actifs |Ligne d'adresse 1 |
|Fournisseur de cloud / référentiels d'actifs |Nom |
|Fournisseur de cloud |Description |
|Fournisseur de cloud |Adresse e-mail du point de contact |
|Fournisseur de cloud |Type|
|Fournisseur de cloud |Nom du point de contact |
|Fournisseur de cloud |Numéro de téléphone du point de contact |

Les informations par défaut suivantes sont utilisées dans la configuration de l'application.

Tableau 2. Informations par défaut utilisées dans la configuration de l'application

|Etape de configuration |Paramètre |
|---|---|
|Environnement |Le nom de l'environnement est défini sur “Initial”|
|Environnement | Le score est défini sur 5|
|Référentiel d'actifs |Deux référentiels d'actifs sont configurés : vCenter et NSX Manager. Les URL hôtes sont configurées sur https://*vCenter fqdn* et https://*NSX Manager fqdn*|
|Référentiel d'actifs |Deux référentiels d'actifs sont configurés : vCenter et NSX Manager. Les deux utilisent le même nom d'utilisateur. Le nom d'utilisateur est défini sur le nom de l'administrateur de vCenter|
|Référentiel d'actifs |Deux référentiels d'actifs sont configurés : vCenter et NSX Manager. Les deux utilisent le même mot de passe. Le mot de passe est défini sur le mot de passe de l'administrateur de vCenter
|Référentiel d'actifs |Deux référentiels d'actifs sont configurés : vCenter et NSX Manager. Les deux utilisent le même mot de passe. Le type est défini sur vCenter pour un référentiel et sur NSX pour l'autre
|Tâche |Quatre tâches sont configurées : l'analyse des actifs, l'analyse des flux NSX, l'analyse de l'infrastructure VMware et de la vulnérabilité VMware. ScanName est défini sur DC1AssetScan, NSXFlows, VMWInfraScan, VMWVulnScan |
|Tâche |Quatre tâches sont configurées : l'analyse des actifs, l'analyse des flux NSX, l'analyse de l'infrastructure VMware et de la vulnérabilité VMware. Type est défini sur vCenter, NSX, VMWareInfrastructureScan, VMWareVulnerabilityScan |
|Tâche |Schedule est défini sur Hourly pour DC1AssetScan et Daily pour les autres |

## Liens connexes
{: #caveonix-step4-related}

* [VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs/vcs-hybridity-intro.html)
