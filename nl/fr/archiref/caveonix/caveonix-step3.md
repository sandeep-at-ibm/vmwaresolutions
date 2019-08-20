---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-05"

subcollection: vmware-solutions


---

# Etape 3 - Configuration de l'application
{: #caveonix-step3}

Cette étape utilise le script de configuration de Caveonix RiskForesight. Lors du déploiement “tout en un”, ce script est démarré par l'automatisation IBM Cloud for VMware Solutions.

Lors de la mise à l'échelle, le client doit appeler le script pour mettre à disposition les topologies partiellement ou entièrement distribuées. Le script configure les services RiskForesight suivants :
- Applications Caveonix (API, collecteur central)
- Elastic Search
- PostgresSQL
- Collecteur distant
- Interface utilisateur
- Kafka
- Kibana
- Certificats de tous les services

A la fin de cette étape, les composants d'application sont installés sur les machines virtuelles requises.
