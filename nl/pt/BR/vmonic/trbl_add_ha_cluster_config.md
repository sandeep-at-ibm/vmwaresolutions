---

copyright:

  years:  2016, 2019

lastupdated: "2018-11-22"

---

# Problema de configuração do console vSphere que é visto ao incluir o cluster de HA

## Problema

Quando você inclui uma configuração de cluster HA (Alta Disponibilidade) com apenas um compartilhamento de arquivo, o seguinte problema de configuração é visto nos hosts ESXi:

> O número de armazenamentos de dados de pulsação para o host é 1, que é menos que o necessário: 2

## Resolução
Esse problema ocorrerá se não houver redundância no armazenamento compartilhado para permitir pulsação de armazenamento de dados.

Para obter mais informações e etapas sobre como corrigir o problema, veja [Erro de HA: o número de armazenamentos de dados de pulsação para o host é 1, que é menos que o necessário: 2 (2004739)](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=2004739).
