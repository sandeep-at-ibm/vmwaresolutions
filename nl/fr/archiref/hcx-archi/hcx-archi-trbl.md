---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

subcollection: vmwaresolutions


---
# Traitement des incidents HCX on IBM Cloud
{: #hcx-archi-trbl}

## Echec de l'enregistrement du cloud
{: #hcx-archi-trbl-cloud-reg}

* Les Services cloud hybrides ne réessaient pas si les données d'identification sont incorrectes. Les données d'identification doivent permettre d'authentifier avant que les Services cloud hybrides essaient de se connecter et de commencer l'enregistrement de cloud.
* L'enregistrement du cloud peut échouer en cas de saisie incorrecte des données d'identification ou si les données d'identification de cloud des Services cloud hybrides VCF/VCS sont modifiées après que ces derniers se soient enregistrés auprès des Services cloud hybrides VCF/VCS, ce qui peut entraîner une non concordance.
* Pour mettre à jour les données d'identification dans le client Web, accédez à l'onglet de mise en route des Services cloud hybrides et, sous **Basic tasks**, choisissez **Register new Cloud**.

## Adresse MAC en double
{: #hcx-archi-trbl-dupl-mac-addr}

A l'issue de la migration, il peut y avoir des problèmes de communication entre vos machines virtuelles. Lorsque l'adresse MAC est conservée durant une migration, une adresse MAC en double peut être créée par inadvertance.

L'adresse MAC de la machine virtuelle en cours de migration migrée peut être modifiée pour résoudre ce problème.

1. Dans le client vSphere, mettez hors tension la machine virtuelle.
2. Dans l'inventaire, cliquez avec le bouton droit de la souris sur la machine virtuelle et choisissez **Edit Settings** dans le menu.
3. Sous l'onglet **Virtual Hardware**, développez l'adaptateur de réseau.
4. En regard de la zone de texte MAC Address, choisissez **Manual** dans le menu.
5. Indiquez une adresse MAC unique et cliquez sur **OK**.
6. Vérifiez si l'adresse MAC unique résout le problème de communication.

## Consommation de ressources hôte élevée
{: #hcx-archi-trbl-high-host-resource}

Dans de rare cas, si tous les dispositifs virtuels de service résident sur le même hôte, les machines virtuelles du service Services cloud peuvent épuiser les ressources de disque et l'UC d'un hôte.

Certains utilisateurs ont constaté ce problème lorsque tous les dispositifs virtuels ont été installés sur un hôte physique. Compte tenu de cette configuration, les performances se dégradent lorsque les éléments suivants se produisent de manière simultanée :
* Le réseau présente une latence élevée et/ou une perte de paquet. La migration ou le transport de données est lent lorsque vous utilisez l'Internet public ou un réseau occupé.
* L'optimiseur de réseau WAN consomme de la bande passante pour chiffrer et compresser (ou déchiffrer et décompresser) d'importantes charges de travail.
* Le trafic de l'application est élevé entre les machines virtuelles locales et les machines virtuelles migrées.

Pour résoudre le problème, procédez comme suit :

1. Avant de modifier la configuration du centre de données, consultez les conditions requises pour un état stabilisé.
2. Contactez le support de l'état stabilisé si des ressources sont épuisées. Il peut vous aider à reconfigurer l'environnement avec un temps d'indisponibilité minimum.

## Liens connexes
{: #hcx-archi-trbl-related}

* [Enregistrement de HCX Manager auprès de vCenter](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-hcx-archi-reg-vcenter)
* [Modification ou désinstallation de HCX](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-hcx-archi-mod-uninstall)
