---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-25"

subcollection: vmware-solutions


---

#	Profils d'hôte
{: #vum-host-profiles}

vCenter a une fonction appelée Profils d'hôte (Host Profiles). Cette fonction permet de créer un profil qui capture une configuration d'hôte de référence validée et préconfigurée. Elle aide un administrateur système à gérer les configurations d'hôte dans un cluster. Les profils d'hôte offrent un mécanisme automatisé géré de manière centralisée pour la configuration des hôtes et la conformité à cette configuration. Les profils d'hôte permettent de traiter la configuration comme un objet géré, qui contient un catalogue de paramètres à configurer, notamment les paramètres de mise en réseau, de stockage, de sécurité, ainsi que d'autres paramètres au niveau de l'hôte. Ces profils d'hôte peuvent être appliqués à des hôtes individuels, à un cluster ou à tous les hôtes et clusters associés à un profil d'hôte.

Comme il y a davantage d'hôtes vSphere ESXi VMware vCenter Server on {{site.data.keyword.cloud}} déployés par l'automatisation IC4VS qui a déployé le cluster d'origine, il y a moins de modification de configuration qu'avec des méthodes manuelles d'ajout d'hôtes. Cependant, les actions de l'administrateur système, en plus de l'automatisation peuvent aboutir à une configuration différente des hôtes, par exemple, en cas d'ajout de stockage NFS ou de réseaux locaux virtuels (VLAN) supplémentaires. L'utilisation de profils d'hôte pour valider la configuration d'un nouvel hôte en vérifiant la conformité de l'hôte par rapport à un hôte existant constitue un cas d'utilisation valide de cet outil dans {{site.data.keyword.cloud_notm}}.

Pour ajouter des hôtes à votre cluster vCenter Server, voir [Extension et réduction de capacité pour des instances vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservers).

Remarque :
*	Pour les instances déployées ou mises à niveau vers la version 2.1 ou supérieure, les mises à jour d'ESXi de VMWare appliquées aux serveurs et aux clusters ESXi nouvellement déployés sont récentes mais ne sont pas forcément les plus récentes.
*	Vous êtes responsable de toutes les autres mises à jour des composants VMware, y compris de vous assurer que les nouveaux clusters et serveurs ESXi déployés disposent de toutes les mises à jour les plus récentes dont vous avez besoin.

Après l'ajout d'un nouvel hôte dans le cluster, nous recommandons de le placer en mode maintenance pour en vérifier la conformité et de le résoudre avant d'héberger des charges de travail.

La séquence suivante est nécessaire pour vérifier la conformité :
1.	Créer un profil d'hôte à partir d'un hôte existant.
2.	Associer le nouvel hôte à ce profil d'hôte.
3.	Vérifier la conformité du nouvel hôte avec le profil d'hôte.
4.	Examiner et corriger les erreurs de conformité.

##	Création d'un profil d'hôte à partir d'un hôte existant
{: #vum-host-profiles-create-host-profile}

1.	A partir de la page d'accueil du client vSphere Web Client, cliquez sur **Policies and Profiles**.
2.	Cliquez sur **Host Profiles** et accédez à la vue correspondante.
3.	Cliquez sur l'icône **Extract Profile from a Host**.
4.	Sélectionnez l'hôte existant qui fait office d'hôte de référence et cliquez sur **Next**.
5.	Entrez un nom et une description du nouveau profil, puis cliquez sur **Next**.
6.	Passez en revue les informations récapitulatives du nouveau profil et cliquez sur **Finish**.
7.	Le nouveau profil apparaît dans la liste des profils.

##	Association du nouvel hôte au profil d'hôte
{: #vum-host-profiles-attach-to-profile}

1.	Dans la **liste des profils** de la vue principale de Host Profiles, sélectionnez le profil d'hôte que vous venez de créer à appliquer au nouvel hôte.
2.	Cliquez sur l'icône **Attach/Detach a host profile to hosts and clusters**.
3.	Sélectionnez le nouvel hôte dans la liste développée et cliquez sur **Attach**.
4.	Le nouvel hôte est ajouté à la liste Attached Entities.
5.	Cliquez sur **Next**, puis sur **Finish**.

##	Vérification de la conformité du nouvel hôte avec le profil d'hôte
{: #vum-host-profiles-check-compliance}

1.	Accédez au profil d'hôte qui vient d'être finalisé.
2.	Cliquez sur l'icône **Check Host Profile Compliance**.
3.	Sur l'onglet **Objects**, l'état de conformité passe à _Compliant, Unknown ou Non-compliant_. L'état Non-compliant indique qu'une incohérence spécifique a été détectée entre le profil et le nouvel hôte.

##	Examen et correction des erreurs de conformité
{: #vum-host-profiles-review-compliance}

1. Pour voir plus de détails sur les erreurs de conformité, sélectionnez le **profil d'hôte** dans l'onglet **Objects** qui est utilisé pour la vérification de la conformité.
2. Pour voir les détails spécifiques des paramètres qui sont différents entre l'hôte dont la vérification de conformité a échoué et le profil d'hôte, cliquez sur l'onglet **Monitor** et sélectionnez la vue **Compliance**.
3. Développez la hiérarchie des objets et sélectionnez l'hôte ayant échoué.
4. Les paramètres qui diffèrent apparaissent dans la fenêtre Compliance, sous la hiérarchie.
5. Examinez les paramètres et essayez de comprendre pourquoi le nouvel hôte est différent de l'hôte de référence. Pour les paramètres où la conformité n'est pas acceptable, par exemple, lorsque la modification de configuration est due à une action de l'administrateur système, effectuez les corrections nécessaires avant de mettre l'hôte en mode maintenance. Autre exemple : lorsque la modification de configuration est causée par une action de l'administrateur système.

## Liens connexes
{: #vum-host-profiles-related}

* [VMware HCX on {{site.data.keyword.cloud_notm}} solution architecture](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-intro#hcx-archi-intro)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/vmware) (démonstrations)
