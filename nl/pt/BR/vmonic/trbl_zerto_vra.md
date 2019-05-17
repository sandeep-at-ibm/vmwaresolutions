---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-21"

subcollection: vmware-solutions


---

# Zerto VRA visível no host do ESXi no console do vCenter após o Zerto on IBM Cloud ser desinstalado
{: #trbl_zerto_vra}

## Problema
{: #trbl_zerto_vra-problem}

Os Zerto Virtual Replication Appliances (VRAs) não são removidos depois de usar o {{site.data.keyword.slportal}} para desinstalar com êxito o serviço Zerto on {{site.data.keyword.cloud}}.

## Resolução
{: #trbl_zerto_vra-resolution}

Remova manualmente os VRAs por meio do console do vCenter.

1. Efetue login no console do vCenter.
2. Clique em **Hosts e clusters** e localize as máquinas virtuais com nomes que iniciam com **Z-VRA-**. Por exemplo, **Z-VRA-host0-vcs40dal.vcs.icvs.org**.
3. Clique com o botão direito na máquina virtual **Z-VRA-** e clique em **Excluir do disco**.
