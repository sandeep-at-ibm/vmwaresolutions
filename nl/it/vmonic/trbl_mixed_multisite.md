---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-12"

---

# Un'istanza secondaria della V1.7 non può essere aggiunta a un'istanza primaria della V1.5

## Problema
In una configurazione Cloud Foundation multisito, non puoi aggiungere un'istanza secondaria della V1.7 a un'istanza primaria della V1.5 a causa di una discrepanza tra le versioni del sistema operativo sul server Microsoft Active Directory (AD).

## Risoluzione
Completa la seguente procedura sull'istanza primaria della V1.5 per aggiungere le autorizzazioni per l'utente di automazione primario in modo che faccia parte dei gruppi **Amministratori azienda** e **Amministratori schema**.

1. Accedi al server Windows AD con la password **Amministratore**.
2. Apri **Server Manager** e fai clic su **Strumenti > Utenti e computer di Active Directory**.
4. Nella finestra **Utenti e computer di Active Directory**, fai clic sulla sezione **Utenti** sotto il tuo dominio root.
5. Fai clic con il tasto destro del mouse sull'utente di automazione per aprire la finestra **Proprietà**.
6. Fai clic sulla scheda **Membro di**.
7. Fai clic su **Aggiungi** e immetti i gruppi **Amministratori azienda** e **Amministratori schema** come nomi oggetto nell'elenco.  

Dopo aver completato questa procedura, potrai aggiungere un'istanza secondaria della V1.7 a un'istanza primaria della V1.5.
