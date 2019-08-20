---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-05"

subcollection: vmware-solutions


---

# Glossaire des termes Caveonix
{: #caveonix-terminology}

Ce glossaire fournit quelques descriptions de termes propres à la solution Caveonix RiskForesight :

-	**Publication spéciale 800-53 du NIST :** Structure de gestion des risques qui traite du contrôle de sécurité.
-	**SCAP (Security Content Automation Protocol) :** Méthode visant à utiliser des normes spécifiques pour permettre la gestion automatisée de la vulnérabilité, ainsi que la mesure et l'évaluation de la conformité des systèmes déployés dans une organisation. Les listes de contrôle normalisent et permettent d'automatiser le lien entre les configurations de sécurité informatique et la publication spéciale 800-53 du NIST.
  - La National Vulnerability Database (NVD) est le référentiel de contenu du gouvernement américain pour SCAP.
  -	SCAP permet aux administrateurs de sécurité d'analyser des ordinateurs, des logiciels et d'autres périphériques sur la base d'une référence de sécurité prédéterminée afin de déterminer si la configuration et les correctifs logiciels sont implémentés conformément à la norme à laquelle ils sont comparés.
  Les composants SCAP sont les suivants :
  -	CVE (Common Vulnerabilities and Exposures) - Liste des vulnérabilités de cybersécurité connues du public.
  -	CCE (Common Configuration Enumeration) - Liste des problèmes de configuration du système liés à la sécurité.
  -	CPE (Common Platform Enumeration) - Schéma de dénomination structuré pour les systèmes, logiciels et progiciels de technologie de l'information.
  -	CWE (Common Weakness Enumeration) - Liste des faiblesses courantes en matière de sécurité logicielle.
  -	CVSS (Common Vulnerability Scoring System) - Système offrant un moyen de saisir les principales caractéristiques d'une vulnérabilité et de produire un score numérique reflétant sa gravité.
  -	XCCDF (Extensible Configuration Checklist Description Format) - Langage de spécification permettant d'écrire des listes de contrôle de sécurité, des benchmarks et des types de documents connexes. Un document XCCDF représente un ensemble structuré de règles de configuration de sécurité pour certains ensembles de systèmes cibles.
  -	OVAL (Open Vulnerability and Assessment Language) - Langage utilisé pour coder les détails du système et un assortiment de référentiels de contenu. Le langage standardise les trois étapes principales du processus d'évaluation :
      - Représentation des informations de configuration des systèmes pour les tests.
      -	Analyse du système (vulnérabilité, configuration et état des correctifs)
      -	Communication des résultats de cette évaluation.
-	**STIG (Security Technical Implementation Guide) :** Méthodologie de cybersécurité permettant de normaliser les protocoles de sécurité au sein des réseaux, des serveurs, des ordinateurs et des conceptions logiques afin d'améliorer la sécurité globale. Une fois implémentés, ces guides améliorent la sécurité des logiciels, du matériel, des architectures physiques et logiques afin de réduire davantage les vulnérabilités.
-	**Fournisseur de service :** Entreprise de plus haut niveau.
-	**Fournisseur de cloud :** Fournit l'infrastructure sur laquelle le cloud défini par logiciel fonctionne. RiskForesight peut être configuré pour plusieurs fournisseurs de cloud.
-	**Organisations :** Organisations et sous-organisations locataires du fournisseur de service. Si le référentiel d'actifs est vCenter, la liste des organisations/locataires doit être créée manuellement.
-	**Rôles :** Rôles préconfigurés et rôles crées par le fournisseur de service. Les rôles préconfigurés ne sont pas éditables par le fournisseur de service.
-	**Utilisateurs de l'organisation :** Utilisateurs des organisations et sous-organisations locataires.
-	**Référentiel d'actifs :** Point d'intégration qui permet à RiskForesight de synchroniser l'actif actuel entre la zone de gestion CSP et la zone client. La version actuelle de RiskForesight prend en charge la synchronisation de VMware vCloud Director et des serveurs vCenter. Il prend également en charge la collecte de données à partir de VMware NSX Manager. Les actifs sont collectés à partir du référentiel d'actifs. Le fournisseur de service attribue les actifs collectés auprès de vCenter aux organisations et sous-organisations locataires du fournisseur de service. Un actif ne peut être affecté qu'à une seule organisation.
-	**Accès distant :** Fournit les données d'identification du terminal pour permettre la surveillance des vulnérabilités et de la conformité et pour collecter les journaux des événements système. Le fournisseur de service ne peut autoriser l'accès à distance que pour ses propres actifs. Les locataires ont le contrôle des accès à distance de leurs actifs.
-	**Applications et sous-applications :** Moyen logique de regrouper les actifs. Exemple d'application : SAP. Exemples de sous-applications : SAP Front End, SAP Middle Tier, SAP Back End.
-	**Emplacements :** Les actifs sont regroupés de façon unique par emplacement, fournisseur de cloud et référentiel d'actifs.
-	**Environnements :** Moyen de regrouper les actifs et les applications. Chaque environnement est affecté à un facteur de risque compris entre 1 et 10. Ce facteur est appliqué dans le calcul du score de risque. Le fournisseur de service définit les environnements.
-	**Tâches :** Elles sont utilisées dans RiskForesight pour :
  -	Synchroniser périodiquement le référentiel d'actifs avec RiskForesight.
  -	Effectuer des analyses de vulnérabilité et de conformité SCAP.
  -	Collecter les flux réseau et autres informations qui utilisent les analyses NSX.
  -	Recueillir de l'information sur le logiciel qui tourne sur les actifs surveillés.
  -	Collecter des événements système et syslog pour les actifs.
-	**Types de tâche :** Les tâches suivantes sont prises en charge :
  -	**Analyse VMware vCenter :** Collecte les actifs de vCenter.
	- **Analyse VMware VCD :** Collecte les actifs de VCD.
  -	**Analyse VMware NSX :** Collecte les informations de réseau et le flux réseau de NSX Manager.
  - **Analyse SCAP :** Ce type d'analyse est utilisé pour analyser les risques cybernétiques et de conformité des charges de travail. Cette analyse est basée sur le protocole SCAP (Security Content Automation Protocol). D'autres versions sont prévues pour prendre en charge le contenu personnalisé dans le format OVAL.
  - **Analyse logicielle :** Cette analyse recueille l'inventaire des logiciels installés sur la charge de travail cible qui est gérée. Cet inventaire peut ensuite être consulté à l'aide de l'option de recherche dans la barre supérieure de l'interface utilisateur.
  - **LogExtract:** Cette analyse prend en charge la collecte des journaux des charges de travail Windows et Linux. Elle est utilisée à des fins d'analyse légale et ingérée par l'apprentissage machine afin de produire des informations utiles.
  - **Tâche AMQP :** Cette tâche est utilisée pour collecter des événements en direct du VCD afin de permettre une synchronisation en temps réel. RiskForesight consomme des événements d'ajout, de suppression et de mise à jour d'actifs et agit sur ces événements. Par exemple, si un nouvel actif est ajouté et que RiskForesight a reçu cet avis par l'intermédiaire de l'AMQP, la base de données est immédiatement mise à jour et l'analyse de risque cybernétique et de conformité est lancée.
  - **Analyse d'infrastructure VMware :** Cette analyse effectue une analyse de l'infrastructure des ressources VMware.
  -	**Analyse de vulnérabilité VMware :** Cette analyse effectue une analyse de la vulnérabilité des actifs VMware.
-	**Régime de conformité :** Disponible sous licence ; NIST, NESA, PCI, ISO, HIPAA, GDPR, Custom, FFIEC, FedRAMP Low, FedRAMP Moderate, FedRAMP High
-	**Gestionnaire de politiques :** Le gestionnaire de politiques sert à la fonction de création de politiques pour une organisation en fonction des résultats de l'apprentissage automatique. Caveonix propose par défaut trois types de travaux d'apprentissage automatique par organisation. Ceux-ci ne sont pas modifiables et l'implémentation d'autres travaux n'est pas encore prise en charge. Les types de travaux d'apprentissage automatique pris en charge actuellement sont :
  -	Journaux Caveo
  -	Réseaux Caveo
  -	Analyse Caveo
-	**Anomalie :** Sur la base des anomalies trouvées dans les données, nous pouvons configurer les politiques pour agir en fonction des conditions définies par l'utilisateur. Vous pouvez sélectionner le type de travail et configurer des conditions booléennes pour le score d'anomalie et définir une action lorsque la condition est vérifiée. Par exemple :
```
Si le score d'anomalie du travail "Caveo Logs" est > 90, alors mettre en quarantaine l'actif et envoyer une notification au canal Slack.`
Si le score d'anomalie du travail "Caveo Network" est > 95, alors mettre en quarantaine l'actif et envoyer une notification par courrier électronique ainsi qu'une notification sur l'interface utilisateur.
```
