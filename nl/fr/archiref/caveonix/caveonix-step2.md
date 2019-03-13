---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

# Etape 2 - Déploiement d'une machine virtuelle
{: #caveonix-step2}

L'automatisation de {{site.data.data.site.data.keywaresolutions_full}} demande un sous-réseau IP privé portable supplémentaire et la machine virtuelle "tout-en-un" (VM) est configurée avec une adresse IP de ce sous-réseau afin que les composants Caveonix RiskForesight puissent :

- Se connecter à vCenter et à NSX Manager via le routeur BCR.
- Se connecter aux collecteurs distants (sur les réseaux VXLAN ou hébergés sur site).
- Permettre au client de gérer l'espace d'adresse IP lors de la mise à l'échelle.


## Liens connexes
{: #caveonix-step2-related}

* [VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
