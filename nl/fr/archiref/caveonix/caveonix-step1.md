---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-05"

subcollection: vmware-solutions


---

# Etape 1 - Planification initiale et prérequis
{: #caveonix-step1}

Les composants de l'application Caveonix RiskForesight sont couplés de manière lâche, mais gérés de manière centralisée. Par conséquent, ils peuvent être déployés dans un modèle de déploiement de machine virtuelle "tout-en-un" ou bien "étendus" et déployés sur plusieurs machines virtuelles pour améliorer la disponibilité, les performances et la capacité.

Les modèles de déploiement sont basés à la fois sur les exigences de disponibilité et sur la taille de conservation des données définie. Les noeuds de déploiement de RiskForesight peuvent être caractérisés comme :

-	Machines virtuelles de base – Les machines virtuelles de base hébergent les composants de l'application qui ne sont pas mis à l'échelle en raison de la conservation des données. Ces composants sont : l'interface utilisateur de RiskForesight, l'application RiskForesight, les plug-in de RiskForesight, le collecteurs central, le collecteur distant, le magasin de données d'index, le magasin de données de messagerie et le magasin de données relationnel.
-	Machines virtuelles d'extension – Les machines virtuelles d'extension, la base de données et les index de données sont mis à l'échelle en fonction du nombre d'actifs et de la conservation des données requise, ce qui entraîne une demande accrue en espace disque dur évolutif et donc une augmentation des machines virtuelles d'extension.

Caveonix RiskForesight offre trois modèles de déploiement :

-	Déploiement “tout en un” – Déploiement et configuration automatisé d'une machine virtuelle qui héberge tous les composants d'application :
  - Tous les composants d'application sont installés sur une machine virtuelle.
  - Des collecteurs distants peuvent être installés sur des machines virtuelles séparées.
  - Petits déploiements - jusqu'à 100 actifs avec une 7 à 30 jours d'indexation.
-	Déploiement partiellement distribué – Une fois que le déploiement automatisé est terminé, vous pouvez effectuer une mise à l'échelle manuelle en augmentant la mémoire RAM et le disque dans la machine virtuelle initiale et en ajoutant trois machines virtuelles d'extension.
  - Interface utilisateur, application, plug-in, collecteur central, collecteur distant, magasin de données d'index, magasin de données de messagerie et magasin de données relationnelle déployés sur une machine virtuelle.
  - Les collecteurs distants sont installées sur des machines virtuelles séparées.
  -	Les noeuds de données d'index sont déployés sur des machines virtuelles séparées.
  -	Déploiements de petite à moyenne taille – jusqu'à 500 actifs avec 30 jours d'indexation.
- Déploiements entièrement distribués - Ajoutez des machines virtuelles de base additionnelles et des machines virtuelles d'extension supplémentaires en fonction du nombre d'actifs et des exigences en matière de conservation des données :
  - Les composants d'application sont distribués sur plusieurs machines virtuelles pour faciliter la mise à l'échelle.
  -	Un modèle de déploiement est requis à mesure que le nombre d'actifs augmente dans une fourchette de 500 à 100 000.
  -	Les collecteurs distants sont installées sur des machines virtuelles séparées.
  -	L'interface utilisateur est installée sur plusieurs machines virtuelles.
  -	L'application et les plug-in sont installés sur plusieurs machines virtuelles.
  -	Le collecteur central est configuré dans un cluster.
  -	Le magasin de données relationnel est déployé dans un modèle principal/secondaire.
  -	Le magasin de données de messagerie est déployé dans un cluster.
  -	Le magasin de données d'index est déployé avec des noeuds de données et des noeuds maître.
  -	Le nombre de noeuds de données utilisés pour la mise à l'échelle augmente à mesure que le nombre d'actifs augmente.

Tous les composants doivent avoir un nom de domaine complet FQDN et un DNS enregistré avant tout déploiement de machine virtuelle. Cette étape est réalisée par l'automatisation IBM Cloud for VMware Solutions lors du déploiement "tout-en-un" initial, mais elle doit être exécutée par vous-même lors de la mise à l'échelle du déploiement.
