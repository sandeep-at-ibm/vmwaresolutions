---

copyright:

  years:  2016, 2018

lastupdated: "2018-03-16"

---

# Problema de configuração do console vSphere visto na inclusão do cluster de HA

## Problema
Ao incluir uma configuração de cluster de HA (Alta Disponibilidade) com apenas um compartilhamento de arquivo, o seguinte problema de configuração é visto nos hosts ESXi:

`O número de armazenamentos de dados com pulsação para host é 1, que é menos que o exigido: 2`

## Resolução
Esse problema ocorrerá se não houver redundância no armazenamento compartilhado para permitir a pulsação do armazenamento de dados.

Para obter mais informações e etapas sobre como corrigir o problema, veja [Erro de HA: "O número de armazenamentos de dados com pulsação para host é 1, que é menos que o exigido: 2" (2004739)](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=2004739).
