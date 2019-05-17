---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-25"

subcollection: vmware-solutions


---

# Problema de configuração do console vSphere que é visto ao incluir o cluster de HA
{: #trbl_add_ha_cluster_config}

## Problema
{: #trbl_add_ha_cluster_config-problem}

Quando você inclui uma configuração de cluster HA (Alta Disponibilidade) com apenas um compartilhamento de arquivo, o seguinte problema de configuração é visto nos hosts ESXi:

> O número de armazenamentos de dados de pulsação para o host é 1, que é menos que o necessário: 2

## Resolução
{: #trbl_add_ha_cluster_config-resolution}

Esse problema ocorrerá se não houver redundância no armazenamento compartilhado para permitir pulsação de armazenamento de dados.

Para obter mais informações e etapas sobre como corrigir o problema, veja [Erro de HA: o número de armazenamentos de dados de pulsação para o host é 1, que é menos que o necessário: 2 (2004739)](https://kb.vmware.com/s/article/2004739).
