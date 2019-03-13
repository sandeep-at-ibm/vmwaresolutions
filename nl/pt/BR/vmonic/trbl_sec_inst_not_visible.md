---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

# O sistema secundário vCenter Server não aparece no inventário do vSphere Web Client
{: #trbl_sec_inst_not_visible}

## Problema
{: #trbl_sec_inst_not_visible-problem}

Em uma configuração de vários sites, depois de incluir uma nova instância secundária, seu sistema vCenter Server não fica visível ao efetuar login no VMware vSphere Web Client de uma instância solicitada anteriormente.

## Resolução
{: #trbl_sec_inst_not_visible-resolution}

Esse é um problema conhecido do VMware 6.5.

Para resolver o problema, deve-se reiniciar o vSphere Web Client:

1. Usando a conta **raiz**, conecte-se em **ssh** à MV (máquina virtual) do vCenter da instância pedida anteriormente.
2. Digite ``shell`` para inserir o shell bash.
3. Insira `service-control --stop vsphere-client` para parar o cliente.
4. Insira `service-control --start vsphere-client` para reiniciar o cliente.
5. Depois que o vSphere Web Client da instância pedida anteriormente for reiniciado, confirme se o sistema vCenter Server para a instância secundária recém-incluída é visível no vSphere Web Client.
