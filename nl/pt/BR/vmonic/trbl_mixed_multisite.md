---

copyright:

  years:  2016, 2018

lastupdated: "2017-10-05"

---

# Uma instância secundária V1.7 não pode ser incluída em uma instância primária V1.5

## Problema
Em uma configuração do Cloud Foundation de vários sites, não é possível incluir uma instância secundária V1.7 em uma instância primária V1.5 por causa de uma discrepância entre as versões do sistema operacional no servidor Microsoft Active Directory (AD).

## Resolução
Conclua as etapas a seguir na instância primária V1.5 para incluir as permissões para o usuário de automação principal fazer parte dos grupos **Administradores Corporativos** e **Administradores do Esquema**.

1. Efetue login no servidor Windows AD com a senha **Administrator**.
2. Abra **Server Manager** e clique em **Ferramentas -> Usuários e Computadores do Active Directory**.
4. Na janela **Usuários e Computadores do Active Directory**, clique na seção **Usuários** no seu domínio-raiz.
5. Clique com o botão direito no usuário da automação para abrir a janela **Propriedades**.
6. Clique na guia **Membro de**.
7. Clique em **Incluir** e insira os grupos **Administradores Corporativos** e **Administradores do Esquema** como nomes de objetos na lista.  

Após concluir essas etapas, é possível incluir uma instância secundária V1.7 em uma instância primária V1.5.
