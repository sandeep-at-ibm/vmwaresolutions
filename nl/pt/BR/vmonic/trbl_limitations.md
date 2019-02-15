---

copyright:

  years:  2016, 2019

lastupdated: "2018-12-11"

---

{:faq: data-hd-content-type='faq'}

# Mais limitações e considerações

Revise as seguintes considerações e limitações ao trabalhar com o {{site.data.keyword.vmwaresolutions_full}}.

## Instalação automática de atualizações do Windows
{: faq}

O Microsoft Active Directory (AD)/Domain Name Server (DNS) é configurado automaticamente para fazer download apenas das atualizações. Ele não instala essas atualizações nem reinicializa automaticamente. Deve-se instalar as atualizações manualmente e reiniciar em um horário planejado que evite quaisquer interrupções da configuração do servidor AD em andamento e de outras tarefas de backup. Para aplicar atualizações do Windows, instale as atualizações manualmente.

## Considerações ao escolher um nome de domínio-raiz para instâncias do Cloud Foundation

Quando você escolhe um nome de domínio durante a implementação de uma instância primária ou secundária do Cloud Foundation, é necessário verificar se o `sddcmanager.<subdomain>` não resolve para um domínio externo usando os comandos `ping` ou `nslookup`.

A estrutura do subdomínio da instância do Cloud Foundation é `<VCF instance name>.<domain name>`. Por exemplo, se o seu `<domain name>` for `test.local` e o nome da instância do Cloud Foundation for `mytest`, o nome do host `sddcmanager.mytest.test.local` não será resolvido em um endereço IP antes dele implementar a instância do Cloud Foundation. Caso contrário, a implementação da instância poderá falhar.
