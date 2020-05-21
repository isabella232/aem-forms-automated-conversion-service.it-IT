---
title: Configurazione del servizio di conversione automatica dei moduli
description: Preparazione dell'istanza di AEM per l'utilizzo del servizio di conversione di moduli automatizzati
translation-type: tm+mt
source-git-commit: e1ef5be14fd3f1ec7e6ccf569c8d76518dfc5c6b
workflow-type: tm+mt
source-wordcount: '2519'
ht-degree: 8%

---


# Configurazione del servizio di conversione automatica dei moduli {#about-this-help}

Questa guida descrive come un amministratore AEM può configurare il servizio di conversione automatica dei moduli per automatizzare la conversione dei moduli PDF in moduli adattivi. Questa guida è destinata agli amministratori IT e AEM della tua organizzazione. Le informazioni fornite si basano sul presupposto che chiunque legga la presente Guida abbia familiarità con le seguenti tecnologie:

* installazione, configurazione e amministrazione di pacchetti Adobe Experience Manager e AEM,

* Utilizzo di sistemi operativi Linux e Microsoft Windows,

* Configurazione dei server di posta SMTP

<!--- >[!VIDEO](https://video.tv.adobe.com/v/29267/) 

**Watch the video or read the article to configure Automated Forms Conversion service** -->

## Onboarding{#onboarding}

Il servizio è disponibile gratuitamente per i clienti AEM 6.4 Forms e AEM 6.5 Forms On-Premise e per i clienti aziendali di Adobe Managed Service. È possibile contattare il team di vendita Adobe o il proprio rappresentante Adobe per richiedere l’accesso al servizio.

Adobe abilita l’accesso per la tua organizzazione e fornisce i privilegi richiesti alla persona designata come amministratore dell’organizzazione. L’amministratore può concedere agli sviluppatori AEM Forms (utenti) dell’organizzazione l’accesso al servizio.

## Prerequisiti {#prerequisites}

Per utilizzare il servizio di conversione moduli automatizzati è necessario disporre dei seguenti requisiti:

* Il servizio di conversione automatizzata dei moduli è abilitato per la propria azienda
* Un account Adobe ID con privilegi di amministratore per il servizio di conversione
* Un’istanza di creazione di AEM 6.4 o AEM 6.5 con AEM Service Pack più recente
* Un utente AEM (nell’istanza di AEM) membro di un gruppo di utenti modulo

## Configurazione dell’ambiente {#setuptheservice}

Prima di usare il servizio, preparate l’istanza di creazione di AEM per collegarvi al servizio in esecuzione su Adobe Cloud. Per preparare l’istanza per il servizio, eseguite i seguenti passaggi nella sequenza elencata:

1. [Scaricare e installare AEM 6.4 o AEM 6.5](#aemquickstart)
1. [Scarica e installa la versione più recente di AEM Service Pack](#servicepack)
1. [Scaricare e installare il pacchetto del componente aggiuntivo AEM Forms più recente](#downloadaemformsaddon)
1. (facoltativo) [Scaricare e installare l&#39;ultimo pacchetto di connettori](#installConnectorPackage)
1. [Creare temi e modelli personalizzati](#referencepackage)

### Scaricare e installare AEM 6.4 o AEM 6.5 {#aemquickstart}


Il servizio di conversione automatica dei moduli viene eseguito sull’istanza di creazione di AEM. AEM 6.4 o AEM 6.5 è necessario per impostare un’istanza di creazione AEM. Se AEM non è già operativo, scaricatelo dai seguenti percorsi:

* Se siete già clienti AEM, scaricate AEM 6.4 o AEM 6.5 dal sito Web [delle licenze](http://licensing.adobe.com)Adobe.

* Se sei un partner Adobe, utilizza [Adobe Partner Training Program](https://adobe.allegiancetech.com/cgi-bin/qwebcorporate.dll?idx=82357Q) per richiedere AEM 6.4 o AEM 6.5.

Dopo aver scaricato AEM, per istruzioni su come impostare un’istanza di creazione AEM, consultate [Implementazione e manutenzione](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/deploy.html#defaultlocalinstall).

### Download e installazione dell&#39;ultimo Service Pack di AEM {#servicepack}

Scarica e installa la versione più recente di AEM Service Pack. Per istruzioni dettagliate, consultate le note [sulla versione di](https://helpx.adobe.com/it/experience-manager/6-4/release-notes/sp-release-notes.html) AEM 6.4 Service Pack o [AEM 6.5 Service Pack](https://helpx.adobe.com/it/experience-manager/6-5/release-notes/sp-release-notes.html).

### Download e installazione del pacchetto del componente aggiuntivo AEM Forms  {#downloadaemformsaddon}

Un&#39;istanza di AEM contiene funzionalità di base per i moduli. Il servizio di conversione richiede funzionalità complete di AEM Forms. Scaricate e installate il pacchetto del componente aggiuntivo AEM Forms per sfruttare tutte le funzionalità di AEM Forms. Il pacchetto è necessario per configurare ed eseguire il servizio di conversione. Per istruzioni dettagliate, consultate [Installare e configurare le funzionalità di acquisizione dei dati.](https://helpx.adobe.com/experience-manager/6-5/forms/using/installing-configuring-aem-forms-osgi.html)

>[!NOTE]
> Dopo aver installato il pacchetto del componente aggiuntivo, accertatevi di eseguire le configurazioni obbligatorie per il post-installazione.


### (Facoltativo) Scaricare e installare il pacchetto del connettore  {#installConnectorPackage}

Il pacchetto del connettore permette di accedere rapidamente alle funzioni di rilevamento [automatico delle sezioni](convert-existing-forms-to-adaptive-forms.md#run-the-conversion) logiche e ai miglioramenti introdotti nella release AFC-2020.03.1. Non installate il pacchetto se non avete bisogno di funzionalità e miglioramenti implementati in AFC-2020.03.1.  Potete [scaricare il pacchetto del connettore da AEM Package Share](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/featurepack/AFCS-Connector-2020.03.1).


### Creare temi e modelli personalizzati {#referencepackage}

Se avviate AEM in modalità [di](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/production-ready.html) produzione (modalità di esecuzione nosamplecontent), i pacchetti di riferimento non vengono installati. I pacchetti di riferimento contengono temi e modelli di esempio. Per convertire i moduli PDF in moduli adattivi, il servizio di conversione automatica dei moduli richiede almeno un tema e un modello. Create un tema e un modello personalizzati con la configurazione [del vostro e del vostro](#configure-the-cloud-service) servizio per utilizzare modelli e temi personalizzati prima di usare il servizio.

## Configurazione del servizio {#configure-the-service}

Prima di configurare il servizio e collegare l’istanza locale al servizio in esecuzione su Adobe Cloud, è necessario conoscere le persone e i privilegi necessari per connettersi al servizio. Il servizio utilizza due diversi tipi di personalità, amministratori e sviluppatori:

* **Amministratori**: Gli amministratori sono responsabili della gestione del software e dei servizi Adobe per la propria organizzazione. Gli amministratori concedono l&#39;accesso agli sviluppatori della propria organizzazione per connettersi al servizio di conversione automatica dei moduli in esecuzione su Adobe Cloud. Quando un amministratore effettua il provisioning per un&#39;organizzazione, l&#39;amministratore riceve un messaggio e-mail con titolo **[!UICONTROL 'You now have administrator rights to manage Adobe software and services for your organization']**. Se siete un amministratore, controllate la casella di posta elettronica con il titolo sopra indicato e continuate a [concedere l&#39;accesso agli sviluppatori della vostra organizzazione](#adduseranddevs).

![email di concessione di accesso amministratore](assets/admin-console-adobe-io-access-grantedx75.png)

* **Sviluppatori**: Uno sviluppatore collega un’istanza di creazione locale di AEM Forms al servizio di conversione automatizzata di moduli in esecuzione su Adobe Cloud. Quando un amministratore concede a uno sviluppatore i diritti per la connessione al servizio di conversione automatica dei moduli, allo sviluppatore viene inviato un messaggio e-mail con il titolo L&#39;utente dispone dell&#39;accesso dello sviluppatore per gestire le integrazioni API Adobe per la propria azienda. Se siete sviluppatori, controllate la casella di posta elettronica con il titolo sopraindicato e procedete a [collegare l’istanza locale di AEM al servizio di conversione automatica dei moduli in Adobe Cloud.](#connectafcadobeio)

![email di concessione accesso sviluppatore](assets/email-developer-accessx94.png)

### (Solo per amministratori) Concedi l&#39;accesso agli sviluppatori della tua organizzazione {#adduseranddevs}

Dopo che Adobe ha concesso all’organizzazione l’accesso e i privilegi necessari all’amministratore, può accedere ad Admin Console (istruzioni dettagliate di seguito), creare un profilo e aggiungere sviluppatori al profilo. Gli sviluppatori possono collegare un&#39;istanza locale di AEM Forms al servizio di conversione automatica dei moduli in Adobe Cloud.

Gli sviluppatori sono membri dell&#39;organizzazione designata per eseguire il servizio di conversione. Solo gli sviluppatori aggiunti al profilo del servizio Adobe Automated Forms Conversion possono utilizzare il servizio di conversione moduli automatizzati. Per creare un profilo e aggiungervi degli sviluppatori, effettuate le seguenti operazioni:

1. Accedi ad [Admin Console](https://adminconsole.adobe.com/). Per utilizzare il servizio di conversione moduli automatizzata per effettuare l&#39;accesso, utilizzare l&#39;ID **** Adobe dell&#39;amministratore fornito. Non utilizzare altri ID o Federated ID per effettuare l&#39;accesso.
1. Fate clic sull’ **[!UICONTROL Automated Forms Conversion]** opzione.
1. Fate clic **[!UICONTROL New Profile]** nella **[!UICONTROL Products]** scheda.
1. Specificate **[!UICONTROL Name]**, **[!UICONTROL Display Name]** e **[!UICONTROL Description]** per il profilo. Clic **[!UICONTROL Done]**. Viene creato un profilo.

   ![Specificate i dettagli per il nuovo profilo.](assets/create-new-profile-details.png)

1. Aggiungi lo sviluppatore al profilo. Per aggiungere gli sviluppatori:
   1. In [Admin Console](https://adminconsole.adobe.com/enterprise), passa alla scheda Panoramica.
   1. Fate clic **[!UICONTROL Assign Developers]** sulla scheda prodotto richiesta.
   1. Immettete l’indirizzo e-mail e, facoltativamente, il nome e il cognome degli sviluppatori.
   1. Seleziona profili di prodotto. Toccare **[!UICONTROL Save]**.

Ripetete i passaggi indicati sopra per tutti gli utenti.  Per ulteriori dettagli sull&#39;aggiunta di sviluppatori, consultate [Gestire gli sviluppatori](https://helpx.adobe.com/enterprise/using/manage-developers.html).

Dopo che un amministratore ha aggiunto gli sviluppatori al profilo di I/O di Adobe, gli sviluppatori ricevono una notifica via e-mail. Dopo aver ricevuto l&#39;e-mail, gli sviluppatori possono procedere alla [connessione di un&#39;istanza locale di AEM Forms con il servizio di conversione automatica dei moduli in Adobe Cloud](#connectafcadobeio).

### (Solo per sviluppatori) Collegate l’istanza locale di AEM Forms al servizio di conversione automatica dei moduli in Adobe Cloud {#connectafcadobeio}

Dopo che un amministratore ha fornito agli sviluppatori l&#39;accesso, potete collegare l&#39;istanza locale di AEM Forms al servizio di conversione dei moduli automatizzati in esecuzione su Adobe Cloud. Per collegare l’istanza di AEM Forms al servizio, effettua i seguenti passaggi nella sequenza elencata:

* [Configurare le notifiche e-mail](configure-service.md#configureemailnotification)
* [Aggiunta di un utente al gruppo di utenti dei moduli](#adduserstousergroup)
* [Ottenere certificati pubblici](#obtainpubliccertificates)
* [Creare l’integrazione di Adobe I/O](#createintegration)
* [Configurare il servizio cloud](configure-service.md#configure-the-cloud-service)

#### Configurare la notifica e-mail {#configureemailnotification}

Il servizio di conversione dei moduli automatizzati utilizza il servizio di posta elettronica Day CQ per inviare le notifiche e-mail. Queste notifiche e-mail contengono informazioni sulle conversioni riuscite o non riuscite. Se scegliete di non ricevere la notifica, saltate questi passaggi. Per configurare Day CQ Mail Service, effettuate le seguenti operazioni:

1. Vai a Gestione configurazione AEM all&#39;indirizzo `http://localhost:4502/system/console/configMgr`
1. Aprire la configurazione Day CQ Mail Service. Specificate un valore per i campi **[!UICONTROL SMTP server host name]**, **[!UICONTROL SMTP server port]** e **[!UICONTROL From address]** . Clic **[!UICONTROL Save]**.

   È possibile contattare il provider di servizi e-mail o l&#39;amministratore IT per informazioni sul nome host e sulla porta del server SMTP. Potete utilizzare qualsiasi indirizzo e-mail valido nel campo da. Ad esempio, notification@example.com o donotreply@example.com.

1. Aprite la **[!UICONTROL Day CQ Link Externalizer]** configurazione. Nel **[!UICONTROL Domains]** campo, specificate il nome host o l&#39;indirizzo IP effettivo e il numero di porta per le istanze locali, di creazione e di pubblicazione. Clic **[!UICONTROL Save]**.

#### Aggiunta di un utente al gruppo di utenti dei moduli {#adduserstousergroup}

Specificate un indirizzo e-mail nel profilo dell’utente AEM designato per eseguire il servizio. Assicurarsi che l&#39;utente sia il membro del gruppo di utenti [dei](https://helpx.adobe.com/experience-manager/6-4/forms/using/forms-groups-privileges-tasks.html) moduli. Le e-mail vengono inviate all&#39;indirizzo e-mail dell&#39;utente che esegue la conversione. Per specificare un indirizzo e-mail per l&#39;utente e aggiungere l&#39;utente al gruppo di utenti dei moduli:

1. Accedi all’istanza di creazione di AEM Forms come amministratore AEM. Utilizzate le credenziali AEM locali per effettuare l&#39;accesso. Non utilizzate l&#39;Adobe ID per effettuare l&#39;accesso. Tap **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Users]**.

1. Selezionate un utente designato per eseguire il servizio di conversione e toccate **[!UICONTROL Properties]**. Viene visualizzata la pagina Modifica impostazioni utente.
1. Specificate un indirizzo e-mail nel **[!UICONTROL Email]** campo e toccate **[!UICONTROL Save]**. Le e-mail vengono inviate all&#39;indirizzo e-mail specificato al completamento o all&#39;esito negativo della conversione.
1. Toccate la scheda **Gruppi** . Nella scheda del gruppo di selezione, digitare e selezionare il gruppo **moduli-utenti** . Toccate **Salva e chiudi**. L&#39;utente ora è membro del gruppo form-users.

#### Ottenere certificati pubblici {#obtainpubliccertificates}

Un certificato pubblico consente di autenticare il profilo sull&#39;I/O di Adobe.

1. Accedi all’istanza di creazione di AEM Forms. Accedi a **[!UICONTROL Tools]**> **[!UICONTROL Security]** > **[!UICONTROL Adobe IMS Configurations]**. Toccare **[!UICONTROL Create]**. Viene **[!UICONTROL Adobe IMS Technical Account Configuration]** visualizzata la pagina.

   ![Pagina Configurazione account tecnico Adobe IMS](assets/adobe-ims-technical-account-configuration.png)

1. Seleziona **[!UICONTROL Automated Forms Conversion Service]** in Cloud Solution.

1. Selezionare la **[!UICONTROL Create new certificate]** casella di controllo e specificare un alias. L’alias funge da nome della finestra di dialogo. Toccare **[!UICONTROL Create certificate]**. Viene visualizzata una finestra di dialogo. Clic **[!UICONTROL OK]**. Il certificato viene creato.

1. Toccate **[!UICONTROL Download Public Key]** e salvate il file di certificato *AEM-Adobe-IMS.crt* sul computer. The certificate file is used to [create integration on Adobe I/O Console](#createintegration). Toccare **[!UICONTROL Next]**.

1. Specificate quanto segue:

   * Titolo: Specificate un titolo.
   * Server autorizzazioni: [https://ims-na1.adobelogin.com](https://ims-na1.adobelogin.com)
   Lasciate vuoti gli altri campi per ora (da fornire successivamente). Tenete la pagina aperta.

   <!--
   Comment Type: draft

   <li> </li>
   -->

   <!--
   Comment Type: draft

   <li>Step text</li>
   -->

#### Creare l’integrazione di Adobe I/O {#createintegration}

Per utilizzare il servizio di conversione moduli automatizzati, creare un&#39;integrazione in Adobe I/O. L&#39;integrazione genera Chiave API, Segreto cliente, Payload (JWT).

1. Effettuate l&#39;accesso a https://console.adobe.io/. Usate il vostro account Adobe ID e sviluppatore per il quale l’amministratore ha effettuato il provisioning per accedere alla console Adobe I/O per effettuare l’accesso.
1. Seleziona la tua organizzazione dall’angolo in alto a destra. Se non sai qual è la tua organizzazione, contatta l’amministratore.
1. Toccare **[!UICONTROL Create new project]**. Viene visualizzata una schermata per iniziare a utilizzare il nuovo progetto. Toccare **[!UICONTROL Add API]**. Viene visualizzata una schermata con l&#39;elenco di tutte le API abilitate per l&#39;account.
1. Seleziona **[!UICONTROL Automated Forms Conversion service]** e tocca **[!UICONTROL Next]**. Viene visualizzata una schermata per configurare l&#39;API.
1. Selezionate l&#39; [!UICONTROL Upload your public key] opzione, caricate il file AEM-Adobe-IMS.crt scaricato nella sezione [Ottieni certificati](#obtainpubliccertificates) pubblici e toccate **[!UICONTROL Next]**. Viene visualizzata l&#39;opzione Crea una nuova credenziale JWT (Service Account). Toccare **[!UICONTROL Next]**.
1. Selezionate un profilo di prodotto e toccate **[!UICONTROL Save configured API]**. Selezionate il profilo creato durante la [concessione dell&#39;accesso agli sviluppatori dell&#39;organizzazione](#adduseranddevs). Se non conosci il profilo da selezionare, contatta l’amministratore.
1. Toccate **[!UICONTROL Service Account (JWT)]** per visualizzare la chiave API, il Segreto cliente e altre informazioni necessarie per collegare l&#39;istanza locale di AEM al servizio di conversione dei moduli automatizzata. Le informazioni presenti nella pagina vengono utilizzate per creare la configurazione IMS sul computer locale.

1. Aprite la pagina Configurazione IMS nell’istanza locale. Hai tenuto aperta questa pagina alla fine della sezione [Recuperare il certificato pubblico](#obtainpubliccertificates).

   ![Specificare titolo, chiave API, segreto cliente e payload ](assets/ims-configuration-details.png)

1. Nella pagina tecnica di Adobe IMS, specificate Chiave API e Segreto cliente. Utilizzate i valori specificati in Account servizio (JWT) della pagina della console Adobe Developer.

   >[!NOTE]
   >
   >
   >Per il payload, utilizzate il codice fornito nella scheda Generate JWT della pagina Service Account (JWT) di Adobe Developer Console.

1. Toccare **[!UICONTROL Save]**. Viene creata la configurazione IMS.

   ![Usa valori del campo JWT per il campo payload](assets/jwt.png)

   >[!CAUTION]
   >
   >Create una sola configurazione IMS. Non create più configurazioni IMS.

1. Selezionate la configurazione IMS e toccate **[!UICONTROL Check Health]**. Viene visualizzata una finestra di dialogo. Toccare **[!UICONTROL Check]**. Una volta stabilita la connessione, viene visualizzato il messaggio *Token recuperato correttamente*.

   ![In caso di connessione riuscita, viene visualizzato il messaggio di recupero token completato. ](assets/health-check.png)

   <br/> <br/>

#### Configure the cloud service {#configure-the-cloud-service}

Crea una configurazione di servizio cloud per collegare l’istanza di AEM al servizio di conversione. Consente inoltre di specificare un modello, un tema e frammenti di modulo per una conversione. È possibile creare più configurazioni del servizio cloud distinte per ciascun set di moduli. Ad esempio, è possibile disporre di una configurazione separata per i moduli del reparto vendite e di una configurazione separata per i moduli di assistenza clienti. Per creare una configurazione di servizio cloud, effettuate le seguenti operazioni:

1. Nell’istanza di AEM Forms, toccate **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Tools]**> **[!UICONTROL Cloud Services]** > **[!UICONTROL Automate Forms Conversion Configuration]**.
1. Toccate la **[!UICONTROL Global]** cartella e toccate **[!UICONTROL Create]**. Viene visualizzata la pagina in cui si desidera creare la configurazione Conversione automatica dei moduli. La configurazione viene creata nella cartella Globale. Potete anche creare la configurazione in un&#39;altra cartella già esistente o creare una nuova cartella per le configurazioni.

1. Nella **[!UICONTROL Create Automated Forms Conversion Configuration]** pagina, specifica il valore per i campi seguenti e tocca **[!UICONTROL Next]**.

   | Campo | Descrizione |
   |--- |--- |
   | Titolo | Titolo univoco per la configurazione. Il titolo viene visualizzato nell’interfaccia utente utilizzata per avviare la conversione. |
   | Nome | Nome univoco per la configurazione. La configurazione viene salvata nel CRX-Repository con il nome specificato. Il nome può essere identico al titolo. |
   | Posizione miniatura | Posizione della miniatura per la configurazione. |
   | URL servizio | URL del servizio di conversione dei moduli automatizzati in Adobe Cloud. Utilizzate l&#39; `https://aemformsconversion.adobe.io/` URL. |
   | Modello | Modello predefinito da applicare ai moduli convertiti. È sempre possibile specificare un modello diverso prima di avviare la conversione. Un modello contiene la struttura di base e il contenuto iniziale per un modulo adattivo. Potete scegliere un modello dai modelli forniti out-of-the-box. Potete anche creare un modello personalizzato. |
   | Tema | Tema predefinito da applicare ai moduli convertiti. È sempre possibile specificare un tema diverso prima di avviare la conversione.  Potete fare clic sull&#39;icona per scegliere un tema fornito out-of-the-box. Potete anche creare un tema personalizzato. |
   | Frammenti esistenti | Posizione degli eventuali frammenti esistenti. |
   | Meta-modello personalizzato | Percorso del file .schema.json del meta-modello personalizzato. |



1. Nella **[!UICONTROL Advanced]** scheda della **[!UICONTROL Create Automated Forms Conversion Configuration]** pagina, specificate il valore per il campo seguente:

   <table>
   <thead>
   <tr>
   <th>Campo</th>
   <th>Descrizione</th>
   </tr>
   </thead>
   <tbody>
   <tr>
   <td >Genera documento di record</td>
   <td>Selezionare l'opzione per generare automaticamente il documento di registrazione per i moduli convertiti. Questa opzione è disponibile solo per i moduli basati su XFA (moduli XDP e PDF). Quando si abilita l'opzione, dopo l'invio di un modulo, è possibile consentire ai clienti di conservare un record, in formato cartaceo o in formato documento, delle informazioni che hanno compilato nel modulo per il riferimento futuro. Tale documento è denominato documento di registrazione.</td>
   </tr>
   <tr>
   <td>Abilita Analytics</td>
   <td>Selezionate l'opzione per abilitare Adobe Analytics su tutti i moduli convertiti. Prima di utilizzare l'opzione, assicurarsi che Adobe Analytics sia abilitato per l'istanza di AEM Forms.</td>
   </tr>
   </tbody>
   </table>

   * Se l&#39;origine è un modulo basato su XFA con estensione .XDP, il DOR di output mantiene il layout XFA, altrimenti il servizio di conversione utilizza un modello predefinito per generare DOR per altri moduli basati su XFA.
   * Quando viene inviato un modulo XFA, i dati di invio del modulo vengono salvati come elemento XML o come attributo. Esempio, `<Amount currency="USD"> 10.00 </Amount>`. La valuta viene salvata come attributo e l&#39;importo della valuta, 10.00 viene salvato come elemento. I dati di invio di un modulo adattivo non hanno attributi, ma solo elementi. Pertanto, quando un modulo basato su XFA viene convertito in modulo adattivo, i dati di invio del modulo adattivo contengono un elemento per ciascun attributo. Ad esempio,

   ```css
      {
         "Type": "Principal",
   
         "Amount": "10.00",
   
         "currency": "USD"
      }
   ```

1. Toccare **[!UICONTROL Create]**. Viene creata la configurazione cloud. L&#39;istanza AEM Forms è pronta per iniziare a convertire moduli legacy in moduli adattivi.
