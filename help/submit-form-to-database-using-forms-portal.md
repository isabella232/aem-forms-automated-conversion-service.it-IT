---
title: Invio di moduli adattivi al database tramite Forms Portal
description: Estende il meta-modello predefinito per aggiungere pattern, convalide ed entità specifici dell'organizzazione e applica configurazioni ai campi modulo adattivi durante l'esecuzione del servizio Conversione automatizzata dei moduli.
uuid: f98b4cca-f0a3-4db8-aef2-39b8ae462628
topic-tags: forms
discoiquuid: cad72699-4a4b-4c52-88a5-217298490a7c
translation-type: tm+mt
source-git-commit: 040b0ddb489b5bdfd640a93b22cd7bc512a39aea

---


# Integrazione di moduli adattivi con il database tramite Forms Portal {#submit-forms-to-database-using-forms-portal}

Il servizio di conversione automatica dei moduli consente di convertire un modulo PDF non interattivo, un modulo Acrobat o un modulo PDF basato su XFA in un modulo adattivo. Quando si avvia il processo di conversione, è possibile generare un modulo adattivo con o senza binding dei dati.

Se si sceglie di generare un modulo adattivo senza binding dei dati, è possibile integrare il modulo adattivo convertito con un modello dati modulo, uno schema XML o uno schema JSON dopo la conversione. Tuttavia, se si genera un modulo adattivo con binding dei dati, il servizio di conversione associa automaticamente i moduli adattivi a uno schema JSON e crea un binding dei dati tra i campi disponibili nel modulo adattivo e nello schema JSON. È quindi possibile integrare il modulo adattivo con un database di propria scelta, compilare i dati del modulo e inviarlo al database utilizzando Forms Portal.

Nella figura seguente sono illustrate diverse fasi dell&#39;integrazione di un modulo adattivo convertito con un database tramite Forms Portal:

![integrazione del database](assets/database_integration.gif)

Questo articolo descrive le istruzioni dettagliate per eseguire correttamente tutte queste fasi di integrazione.

L&#39;esempio, illustrato in questo articolo, è un&#39;implementazione di riferimento di dati e servizi di metadati personalizzati per integrare una pagina di Forms Portal con un database. Il database utilizzato nell&#39;implementazione di esempio è MySQL 5.6.24. Tuttavia, è possibile integrare la pagina di Forms Portal con qualsiasi database di propria scelta.

## Prerequisiti {#pre-requisites}

* Istanza di authoring di AEM 6.5 con l’ultimo Service Pack di AEM 6.5
* Ultima versione del pacchetto del componente aggiuntivo AEM Forms
* [Servizio di conversione moduli automatizzati](configure-service.md)
* Un database con cui effettuare l&#39;integrazione. Il database utilizzato nell&#39;implementazione di esempio è MySQL 5.6.24. Tuttavia, è possibile integrare Forms Portal con qualsiasi database di propria scelta.

## Configurare la connessione tra l’istanza AEM e il database {#set-up-connection-aem-instance-database}

L&#39;impostazione di una connessione tra un&#39;istanza AEM e un database MYSQL consiste in:

* [Installazione di un pacchetto di connettore MYSQL](#install-mysql-connector-java-file)

* [Creazione di schema e tabelle nel database](#create-schema-and-tables-in-database)

* [Configurazione delle impostazioni di connessione](#configure-connection-between-aem-instance-and-database)

* [Configurazione e configurazione del pacchetto di esempio per l&#39;integrazione con Forms Portal](#set-up-and-configure-sample)

### Installare il file mysql-Connector-java-5.1.39-bin.jar {#install-mysql-connector-java-file}

Per installare il file mysql-Connector-java-5.1.39-bin.jar, eseguite i seguenti passaggi su tutte le istanze di creazione e pubblicazione:

1. Andate a http://[server]:[port]/system/console/depfinder e cercate il pacchetto com.mysql.jdbc.
1. Nella colonna Esportato da, verificate che il pacchetto sia esportato da un pacchetto qualsiasi. Continuate se il pacchetto non viene esportato da alcun bundle.
1. Andate a http://[server]:[porta]/sistema/console/bundle e fate clic su **[!UICONTROL Install/Update]**.
1. Fate clic su **[!UICONTROL Choose File]** e individuate il file mysql-Connector-java-5.1.39-bin.jar. Inoltre, selezionare **[!UICONTROL Start Bundle]** e **[!UICONTROL Refresh Packages]** le caselle di controllo.
1. Fate clic **[!UICONTROL Install]** o **[!UICONTROL Update]**. Al termine, riavviare il server.
1. (Solo Windows) Disattivate il firewall di sistema del sistema operativo in uso.

### Creare schema e tabelle nel database {#create-schema-and-tables-in-database}

Per creare schema e tabelle nel database, effettuare le seguenti operazioni:

1. Create uno schema nel database utilizzando la seguente istruzione SQL:

   ```sql
   CREATE SCHEMA `formsportal` ;
   ```

   dove **formsPortal** fa riferimento al nome dello schema.

1. Creare una tabella **dati** nello schema del database utilizzando la seguente istruzione SQL:

   ```sql
    CREATE TABLE `data` (
        `owner` varchar(255) DEFAULT NULL,
        `data` longblob,
        `metadataId` varchar(45) DEFAULT NULL,
        `id` varchar(45) NOT NULL,
        PRIMARY KEY (`id`)
        ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
   ```

1. Create una tabella di **metadati** nello schema del database utilizzando la seguente istruzione SQL:

   ```sql
   CREATE TABLE `metadata` (
       `formPath` varchar(1000) DEFAULT NULL,
       `formType` varchar(100) DEFAULT NULL,
       `description` text,
       `formName` varchar(255) DEFAULT NULL,
       `owner` varchar(255) DEFAULT NULL,
       `enableAnonymousSave` varchar(45) DEFAULT NULL,
       `renderPath` varchar(1000) DEFAULT NULL,
       `nodeType` varchar(45) DEFAULT NULL,
       `charset` varchar(45) DEFAULT NULL,
       `userdataID` varchar(45) DEFAULT NULL,
       `status` varchar(45) DEFAULT NULL,
       `formmodel` varchar(45) DEFAULT NULL,
       `markedForDeletion` varchar(45) DEFAULT NULL,
       `showDorClass` varchar(255) DEFAULT NULL,
       `sling:resourceType` varchar(1000) DEFAULT NULL,
       `attachmentList` longtext,
       `draftID` varchar(45) DEFAULT NULL,
       `submitID` varchar(45) DEFAULT NULL,
       `id` varchar(60) NOT NULL,
       `profile` varchar(255) DEFAULT NULL,
       `submitUrl` varchar(1000) DEFAULT NULL,
       `xdpRef` varchar(1000) DEFAULT NULL,
       `agreementId` varchar(255) DEFAULT NULL,
       `nextSigners` varchar(255) DEFAULT NULL,
       `eSignStatus` varchar(45) DEFAULT NULL,
       `pendingSignID` varchar(45) DEFAULT NULL,
       `agreementDataId` varchar(255) DEFAULT NULL,
       `enablePortalSubmit` varchar(45) DEFAULT NULL,
       `submitType` varchar(45) DEFAULT NULL,
       `dataType` varchar(45) DEFAULT NULL,
       `jcr:lastModified` varchar(45) DEFAULT NULL,
       PRIMARY KEY (`id`),
       UNIQUE KEY `ID_UNIQUE` (`id`)
       ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
   ```

1. Create una tabella **aggiuntiva** metadati nello schema del database utilizzando la seguente istruzione SQL:

   ```sql
   CREATE TABLE `additionalmetadatatable` (
       `value` text,
       `key` varchar(255) NOT NULL,
       `id` varchar(60) NOT NULL,
       PRIMARY KEY (`id`,`key`),
       CONSTRAINT ‘additionalmetadatatable_fk’ FOREIGN KEY (`id`) REFERENCES `metadata` (`id`) ON DELETE CASCADE
       ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
   ```

1. Creare una tabella **di commenti** nello schema del database utilizzando la seguente istruzione SQL:

   ```sql
   CREATE TABLE `commenttable` (
       `commentId` varchar(255) DEFAULT NULL,
       `comment` text DEFAULT NULL,
       `ID` varchar(255) DEFAULT NULL,
       `commentowner` varchar(255) DEFAULT NULL,
       `time` varchar(255) DEFAULT NULL);
   ```

### Configurare la connessione tra l’istanza AEM e il database {#configure-connection-between-aem-instance-and-database}

Per creare una connessione tra l’istanza AEM e il database MYSQL, effettuate i seguenti passaggi di configurazione:

1. Andate alla pagina Configurazione console Web di AEM all&#39;indirizzo *http://[host]:[port]/system/console/configMgr*.
1. Fare clic per aprire **[!UICONTROL Forms Portal Draft and Submission Configuration]** in modalità di modifica.
1. Specificare i valori delle proprietà come descritto nella tabella seguente:

   <table> 
    <tbody> 
    <tr> 
    <th><strong>Proprietà</strong></th> 
    <th><strong>Descrizione</strong></th>
    <th><strong>Valore</strong></th> 
    </tr> 
    <tr> 
    <td><p>Servizio dati bozza di Forms Portal</p></td> 
    <td><p>Identificatore per il servizio dati bozza</p></td>
    <td><p>formsPortal.sampledataservice</p></td> 
    </tr>
    <tr> 
    <td><p>Servizio metadati bozza del portale Forms</p></td> 
    <td><p>Identificatore per il servizio metadati bozza</p></td>
    <td><p>formsPortal.samplemetadataservice</p></td> 
    </tr>
    <tr> 
    <td><p>Servizio di invio dati Forms Portal</p></td> 
    <td><p>Identificatore per il servizio dati di invio</p></td>
    <td><p>formsPortal.sampledataservice</p></td> 
    </tr>
    <tr> 
    <td><p>Servizio di invio metadati del portale Forms</p></td> 
    <td><p>Identificatore per il servizio di invio metadati</p></td>
    <td><p>formsPortal.samplemetadataservice</p></td> 
    </tr>
    <tr> 
    <td><p>Servizio di firma dati in sospeso di Forms Portal</p></td> 
    <td><p>Identificatore per il servizio dati Firma in sospeso</p></td>
    <td><p>formsPortal.sampledataservice</p></td> 
    </tr>
    <tr> 
    <td><p>Servizio metadati firma in sospeso di Forms Portal</p></td> 
    <td><p>Identificatore per il servizio metadati Firma in sospeso</p></td>
    <td><p>formsPortal.samplemetadataservice</p></td> 
    </tr>
    </tbody> 
    </table>
1. Lasciate invariate le altre configurazioni e fate clic **[!UICONTROL Save]**.
1. Trova e fai clic per aprire **[!UICONTROL Apache Sling Connection Pooled DataSource]** in modalità di modifica nella Configurazione console Web. Specificare i valori delle proprietà come descritto nella tabella seguente:

   <table> 
    <tbody> 
    <tr> 
    <th><strong>Proprietà</strong></th> 
    <th><strong>Valore</strong></th> 
    </tr> 
    <tr> 
    <td><p>Nome origine dati</p></td> 
    <td><p>Nome origine dati per filtrare i driver dal pool di origini dati. L'implementazione di esempio utilizza FormsPortal come nome dell'origine dati.</p></td>
    </tr>
    <tr> 
    <td><p>Classe driver JDBC</p></td> 
    <td><p>com.mysql.jdbc.Driver</p></td>
    </tr>
    <tr> 
    <td><p>URI connessione JDBC</p></td> 
    <td><p>jdbc:mysql://[host]:[porta]/[nome_schema]</p></td>
    </tr>
    <tr> 
    <td><p>Nome utente</p></td> 
    <td><p>Un nome utente per l'autenticazione e l'esecuzione di azioni sulle tabelle del database</p></td>
    </tr>
    <tr> 
    <td><p>Password</p></td> 
    <td><p>Password associata al nome utente</p></td>
    </tr>
    <tr> 
    <td><p>Isolamento transazione</p></td> 
    <td><p>READ_COMMTED</p></td>
    </tr>
    <tr> 
    <td><p>Numero massimo di connessioni attive</p></td> 
    <td><p>1000</p></td>
    </tr>
    <tr> 
    <td><p>Numero massimo di connessioni inattive</p></td> 
    <td><p>100</p></td>
    </tr>
    <tr> 
    <td><p>Connessioni con inattività minima</p></td> 
    <td><p>10</p></td>
    </tr>
    <tr> 
    <td><p>Dimensione iniziale</p></td> 
    <td><p>10</p></td>
    </tr>
    <tr> 
    <td><p>Max</p></td> 
    <td><p>100000</p></td>
    </tr>
     <tr> 
    <td><p>Test di credito</p></td> 
    <td><p>Selezionato</p></td>
    </tr>
     <tr> 
    <td><p>Test while Idle</p></td> 
    <td><p>Selezionato</p></td>
    </tr>
     <tr> 
    <td><p>Query convalida</p></td> 
    <td><p>I valori di esempio sono SELECT 1(mysql), select 1 from dual(oracle), SELECT 1(MS Sql Server) (validationQuery)</p></td>
    </tr>
     <tr> 
    <td><p>Timeout query di convalida</p></td> 
    <td><p>10000</p></td>
    </tr>
    </tbody> 
    </table>

### Configurare e configurare l’esempio {#set-up-and-configure-sample}

Per installare e configurare l’esempio, effettuate le seguenti operazioni, in tutte le istanze di creazione e pubblicazione:

1. Scaricate il seguente pacchetto **aem-fp-db-integration-sample-pkg-6.1.2.zip** nel file system.

   [Ottieni file](assets/aem-fp-db-integration-sample-pkg-6.1.2.zip)

1. Andate a Gestione pacchetti AEM all&#39;indirizzo *http://[host]:[port]/crx/packmgr/*.
1. Clic **[!UICONTROL Upload Package]**.
1. Selezionate il pacchetto **aem-fp-db-integration-sample-pkg-6.1.2.zip** e fate clic su **[!UICONTROL OK]**.
1. Fate clic su **[!UICONTROL Install]** accanto al pacchetto per installare il pacchetto.

## Configurare il modulo adattivo convertito per l&#39;integrazione con Forms Portal {#configure-converted-adaptive-form-for-forms-portal-integration}

Per abilitare l&#39;invio di moduli adattivi tramite la pagina Forms Portal, effettuare le operazioni seguenti:
1. [Eseguire la conversione](convert-existing-forms-to-adaptive-forms.md#start-the-conversion-process) per convertire un modulo di origine in un modulo adattivo.
1. Aprire il modulo adattivo in modalità di modifica.
1. Toccare Contenitore modulo e selezionare Configura ![modulo](assets/configure-adaptive-form.png)adattivo.
1. Nella **[!UICONTROL Submission]** sezione, selezionare **[!UICONTROL Forms Portal Submit Action]** dall&#39;elenco a **[!UICONTROL Submit Action]** discesa.
1. Toccate ![Salva criterio](assets/edit_template_done.png) modello per salvare le impostazioni.

## Creare e configurare la pagina del portale Forms {#create-configure-forms-portal-page}

Per creare una pagina di Forms Portal e configurarla in modo da poter inviare moduli adattivi tramite questa pagina, effettuare le seguenti operazioni:

1. Accedete all’istanza di creazione di AEM e toccate **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Sites]**.
1. Selezionare il percorso in cui si desidera salvare la nuova pagina di Forms Portal e toccare **[!UICONTROL Create]** > **[!UICONTROL Page]**.
1. Selezionate il modello per la pagina, toccate **[!UICONTROL Next]**, specificate un titolo per la pagina e toccate **[!UICONTROL Create]**.
1. Toccate **[!UICONTROL Edit]** per configurare la pagina.
1. Nell’intestazione della pagina, toccate ![Modifica modello](assets/edit_template_sites.png) > **[!UICONTROL Edit Template]** per aprire il modello della pagina.
1. Toccate Contenitore di layout e toccate ![Modifica criterio](assets/edit_template_policy.png)modello. Nella **[!UICONTROL Allowed Components]** scheda, abilitate le opzioni **[!UICONTROL Document Services]** e **[!UICONTROL Document Services Predicates]** , quindi toccate ![Salva criterio](assets/edit_template_done.png)modello.
1. Inserisci **[!UICONTROL Search & Lister]** componente nella pagina. Di conseguenza, tutti i moduli adattivi esistenti disponibili nell’istanza di AEM sono elencati nella pagina.
1. Inserisci **[!UICONTROL Drafts & Submissions]** componente nella pagina. Nella pagina Portale moduli sono visualizzate due schede **[!UICONTROL Draft Forms]** e **[!UICONTROL Submitted Forms]**. Nella **[!UICONTROL Draft Forms]** scheda viene inoltre visualizzato il modulo adattivo convertito generato utilizzando i passaggi indicati in [Configurare il modulo adattivo convertito per l&#39;integrazione con Forms Portal](#configure-converted-adaptive-form-for-forms-portal-integration)

1. Toccate **[!UICONTROL Preview]**, toccate il modulo adattivo convertito, specificate i valori per i campi modulo adattivi e inviatelo. I valori specificati per i campi modulo adattivo vengono inviati al database integrato.
