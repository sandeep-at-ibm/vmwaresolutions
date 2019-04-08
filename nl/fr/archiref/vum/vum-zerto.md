---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-13"

subcollection: vmwaresolutions


---

# Zerto
{: #vum-zerto}

Si vous constatez qu'un hôte vSphere ESXi ne peut pas passer en mode maintenance lors d'une opération de résolution, il est possible que Zerto l'en empêche. Si vous avez mis à jour Zerto depuis le déploiement initial, procédez selon les étapes suivantes pour y remédier. Si vous ne l'avez pas mis à jour, suivez les instructions indiquées sur la page [How to place a host with an associated VRA into maintenance mode](https://www.zerto.com/myzerto/knowledge-base/place-host-into-maintenance-mode-with-vra/).

1. Connectez-vous à l'interface utilisateur Web de Zerto.
2. Sélectionnez **Site Settings** dans le menu déroulant.
3. Sélectionnez l'onglet **Policies** et vérifiez que l'option **Allow Zerto to always enter hosts to maintenance mode during remediation** est sélectionnée.
4. Déconnectez-vous de Zerto.

## Liens connexes
{: #vum-zerto-related}

* [VMware HCX on {{site.data.keyword.cloud_notm}} solution architecture](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-intro#hcx-archi-intro)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (démonstrations)
