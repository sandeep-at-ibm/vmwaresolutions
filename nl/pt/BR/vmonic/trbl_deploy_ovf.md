---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-12"

subcollection: vmware-solutions


---

# Implementando um arquivo OVF usando o VMware vSphere Web Client
{: #trbl_deploy_ovf}

## Resolução
{: #trbl_deploy_ovf-resolution}

Para implementar um arquivo OVF (Open Virtualization Format) usando o vSphere Web Client, use o seguinte procedimento:
1. Antes de tentar implementar um arquivo OVF, inclua as informações do host a seguir no arquivo `/etc/hosts`:

   * Informações do host para o Platform Services Controller (PSC)
   * Informações do host para o servidor VMware ESXi
   * Informações do host para vCenter
2. Verifique seu arquivo `/etc/hosts` para assegurar que essas informações sejam incluídas com êxito. Um exemplo de um arquivo host pode ser parecido com a lista a seguir:

    ```javascript
    10.131.9.201  psc-myinstance.myinstance.mydomain.com
    10.131.7.26   host0.myinstance.mydomain.com
    10.131.7.39   host1.myinstance.mydomain.com
    10.131.7.6    host2.myinstance.mydomain.com
    10.131.7.48   host3.myinstance.mydomain.com
    10.131.9.196  vcenter-1.myinstance.mydomain.com
    ```
3. Assegure-se de que você tenha acesso a todas as VPNs (Redes Privadas Virtuais) necessárias no {{site.data.keyword.slportal_full}}. Nesse exemplo, seria `10.131.7.xx` e `10.131.9.xxx`.
4. Conecte a VPN para seu data center.
5. Clique em **vCenter** para acessar o vSphere Web Client.
6. Clique com o botão direito em um host e implemente um arquivo `.ovf`.
