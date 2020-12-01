---
title: Configurazione del servizio di conversione automatica dei moduli
description: Pronta l'istanza AEM per utilizzare il servizio Automated forms conversion
translation-type: tm+mt
source-git-commit: 741ff89370a5215b70d90c49eea220171efe9339
workflow-type: tm+mt
source-wordcount: '2547'
ht-degree: 9%

---


# Configurazione del servizio di conversione automatica dei moduli {#about-this-help}

Questa guida descrive come un amministratore AEM può configurare il servizio di Automated forms conversion per automatizzare la conversione dei propri PDF forms nei moduli adattivi. Questa guida è destinata agli amministratori IT e AEM della vostra azienda. Le informazioni fornite si basano sul presupposto che chiunque legga la presente Guida abbia familiarità con le seguenti tecnologie:

* installazione, configurazione e amministrazione di pacchetti Adobe Experience Manager e AEM,

* Utilizzo di sistemi operativi Linux e Microsoft Windows,

* Configurazione dei server di posta SMTP

<!--- >[!VIDEO](https://video.tv.adobe.com/v/29267/) 

**Watch the video or read the article to configure Automated Forms Conversion service** -->

## Onboarding{#onboarding}

Il servizio è disponibile gratuitamente per i clienti AEM 6.4 Forms e AEM 6.5 Forms On-Premise e per i clienti aziendali di Adobe Managed Service. È possibile contattare il team di vendita Adobe o il proprio rappresentante Adobe per richiedere l’accesso al servizio.

Adobe abilita l’accesso per la tua organizzazione e fornisce i privilegi richiesti alla persona designata come amministratore dell’organizzazione. L’amministratore può concedere agli sviluppatori AEM Forms (utenti) dell’organizzazione l’accesso al servizio.

## Prerequisiti {#prerequisites}

Per utilizzare il servizio Automated forms conversion è necessario disporre dei seguenti requisiti:

* Il servizio automated forms conversion è abilitato per l&#39;organizzazione
* Un account Adobe ID  con privilegi di amministratore per il servizio di conversione
* Un’istanza di authoring AEM 6.4 o AEM 6.5 con AEM Service Pack più recente
* Un utente AEM (nell’istanza AEM) membro del gruppo forms-user

## Configurazione dell’ambiente {#setuptheservice}

Prima di utilizzare il servizio, preparate l&#39;istanza AEM autore per collegarvi al servizio in esecuzione su  Adobe Cloud. Per preparare l’istanza per il servizio, eseguite i seguenti passaggi nella sequenza elencata:

1. [Scaricare e installare AEM 6.4 o AEM 6.5](#aemquickstart)
1. [Download e installazione della versione più recente di AEM Service Pack](#servicepack)
1. [Download e installazione della versione più recente  pacchetto aggiuntivo AEM Forms](#downloadaemformsaddon)
1. (facoltativo) [Scaricare e installare l&#39;ultimo pacchetto di connettori](#installConnectorPackage)
1. [Creare temi e modelli personalizzati](#referencepackage)

### Download e installazione AEM 6.4 o AEM 6.5 {#aemquickstart}


Il servizio di automated forms conversion viene eseguito AEM’istanza di creazione. È necessario AEM 6.4 o AEM 6.5 per impostare un’istanza AEM di creazione. Se non disponete di AEM pronti, scaricatelo dalle seguenti posizioni:

* Se siete già clienti AEM, scaricate AEM 6.4 o AEM 6.5 dal [ sito Web delle licenze dei Adobi](http://licensing.adobe.com).

* Se siete un partner  Adobe, utilizzate il programma di formazione per i partner  Adobi [ per richiedere AEM 6.4 o AEM 6.5.](https://adobe.allegiancetech.com/cgi-bin/qwebcorporate.dll?idx=82357Q)

Dopo aver scaricato AEM, per istruzioni su come impostare un&#39;istanza AEM di creazione, vedere [implementazione e manutenzione](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/deploy.html#defaultlocalinstall).

### Download e installazione AEM Service Pack più recente {#servicepack}

Scarica e installa AEM Service Pack più recente. Per istruzioni dettagliate, consultate le [AEM 6.4 Service Pack - Note sulla versione](https://helpx.adobe.com/it/experience-manager/6-4/release-notes/sp-release-notes.html) o [AEM 6.5 Service Pack - Note sulla versione](https://helpx.adobe.com/it/experience-manager/6-5/release-notes/sp-release-notes.html).

### Download e installazione  pacchetto aggiuntivo AEM Forms {#downloadaemformsaddon}

Un&#39;istanza AEM contiene funzionalità di base dei moduli. Il servizio di conversione richiede funzionalità complete di  AEM Forms. Scaricate e installate  pacchetto aggiuntivo AEM Forms per sfruttare tutte le funzionalità di  AEM Forms. Il pacchetto è necessario per configurare ed eseguire il servizio di conversione. Per istruzioni dettagliate, vedere [Installare e configurare le funzionalità di acquisizione dei dati.](https://helpx.adobe.com/experience-manager/6-5/forms/using/installing-configuring-aem-forms-osgi.html)

>[!NOTE]
> Dopo aver installato il pacchetto del componente aggiuntivo, accertatevi di eseguire le configurazioni obbligatorie per il post-installazione.


### (Facoltativo) Scaricare e installare il pacchetto del connettore {#installConnectorPackage}

Il pacchetto del connettore consente di accedere in anticipo alle [funzionalità di rilevamento automatico delle sezioni logiche](convert-existing-forms-to-adaptive-forms.md#run-the-conversion) e ai miglioramenti introdotti nella release AFC-2020.03.1. Non installate il pacchetto se non avete bisogno di funzionalità e miglioramenti implementati in AFC-2020.03.1.  È possibile [scaricare il pacchetto del connettore da AEM Package Share](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/featurepack/AFCS-Connector-2020.03.1).


### Creare temi e modelli personalizzati {#referencepackage}

Se iniziate AEM in [modalità di produzione](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/production-ready.html) (nessuna modalità di esecuzione del contenuto di esempio), i pacchetti di riferimento non vengono installati. I pacchetti di riferimento contengono temi e modelli di esempio. Il servizio automated forms conversion richiede almeno un tema e un modello per convertire un PDF forms in un modulo adattivo. Crea un tema e un modello personalizzati con la tua [configurazione del servizio ](#configure-the-cloud-service) per utilizzare i modelli e i temi personalizzati prima di utilizzare il servizio.

## Configurazione del servizio {#configure-the-service}

Prima di configurare il servizio e collegare l&#39;istanza locale al servizio in esecuzione  Adobe Cloud, è necessario conoscere le persone e i privilegi necessari per connettersi al servizio. Il servizio utilizza due diversi tipi di personalità, amministratori e sviluppatori:

* **Amministratori**: Gli amministratori sono responsabili della gestione  software e servizi di Adobe per la propria organizzazione. Gli amministratori concedono l&#39;accesso agli sviluppatori nella propria organizzazione per connettersi al servizio di Automated forms conversion in esecuzione su  Adobe Cloud. Quando un amministratore effettua il provisioning per un&#39;organizzazione, l&#39;amministratore riceve un&#39;e-mail con titolo **[!UICONTROL 'You now have administrator rights to manage Adobe software and services for your organization']**. Se siete un amministratore, controllate la casella di posta elettronica con il titolo sopra indicato e passate a [concedere l&#39;accesso agli sviluppatori della vostra organizzazione](#adduseranddevs).

![email di concessione di accesso amministratore](assets/admin-console-adobe-io-access-grantedx75.png)

* **Sviluppatori**: Uno sviluppatore collega un’istanza di creazione AEM Forms  locale al servizio di Automated forms conversion in esecuzione  Adobe Cloud. Quando un amministratore concede i diritti a uno sviluppatore per la connessione al servizio Automated forms conversion, un messaggio e-mail con titolo L&#39;utente dispone ora dell&#39;accesso sviluppatore per gestire  integrazioni API Adobe per l&#39;organizzazione viene inviato allo sviluppatore. Se siete uno sviluppatore, controllate la casella di posta elettronica con il titolo sopra indicato e andate a [Collegare l&#39;istanza AEM locale al servizio di Automated forms conversion in  Adobe cloud.](#connectafcadobeio)

![email di concessione accesso sviluppatore](assets/email-developer-accessx94.png)

### (Solo per amministratori) Concedi l&#39;accesso agli sviluppatori della tua organizzazione {#adduseranddevs}

Dopo che  Adobe consente l’accesso all’organizzazione e fornisce all’amministratore i privilegi necessari, l’amministratore può accedere  Admin Console (istruzioni dettagliate di seguito), creare un profilo e aggiungere sviluppatori al profilo. Gli sviluppatori possono collegare un&#39;istanza locale di  AEM Forms al servizio di Automated forms conversion  Adobe Cloud.

Gli sviluppatori sono membri dell&#39;organizzazione designata per eseguire il servizio di conversione. Solo gli sviluppatori che vengono aggiunti  profilo di servizio Automated forms conversion Adobe possono utilizzare il servizio di Automated forms conversion. Per creare un profilo e aggiungervi degli sviluppatori, effettuate le seguenti operazioni. È necessario un minimo di un profilo per concedere l&#39;accesso necessario agli sviluppatori dell&#39;organizzazione:

1. Accedete a [ Admin Console](https://adminconsole.adobe.com/). Utilizzate **Adobe ID** dell&#39;amministratore fornito per utilizzare il servizio di Automated forms conversion per effettuare l&#39;accesso. Non utilizzare altri ID o Federated ID per effettuare l&#39;accesso.
1. Fare clic sull&#39;opzione **[!UICONTROL Automated Forms Conversion]**.
1. Fare clic su **[!UICONTROL New Profile]** nella scheda **[!UICONTROL Products]**.
1. Specificare **[!UICONTROL Name]**, **[!UICONTROL Display Name]** e **[!UICONTROL Description]** per il profilo. Clic **[!UICONTROL Done]**. Viene creato un profilo.

   ![Specificate i dettagli per il nuovo profilo.](assets/create-new-profile-details.png)

1. Aggiungi lo sviluppatore al profilo. Per aggiungere gli sviluppatori:
   1. Nel Admin Console [](https://adminconsole.adobe.com/enterprise), passare alla scheda Panoramica.
   1. Fate clic su **[!UICONTROL Assign Developers]** nella scheda prodotto richiesta.
   1. Immettete l’indirizzo e-mail e, facoltativamente, il nome e il cognome degli sviluppatori.
   1. Seleziona profili di prodotto. Toccare **[!UICONTROL Save]**.

Ripetete i passaggi indicati sopra per tutti gli utenti.  Per ulteriori informazioni sull&#39;aggiunta di sviluppatori, vedere [Gestione di sviluppatori](https://helpx.adobe.com/enterprise/using/manage-developers.html).

Dopo che un amministratore aggiunge gli sviluppatori  profilo Adobe I/O, gli sviluppatori ricevono una notifica via e-mail. Dopo aver ricevuto l&#39;e-mail, gli sviluppatori possono continuare a [collegare un&#39;istanza  AEM Forms locale con il servizio di Automated forms conversion in  Cloud](#connectafcadobeio).

### (Solo per sviluppatori) Collegate l&#39;istanza locale  AEM Forms al servizio Automated forms conversion in  Adobe cloud {#connectafcadobeio}

Dopo che un amministratore vi fornisce l&#39;accesso per sviluppatori, potete collegare l&#39;istanza locale  AEM Forms al servizio di Automated forms conversion in esecuzione  Cloud. Per collegare l’istanza di AEM Forms  al servizio, eseguite i seguenti passaggi nella sequenza elencata:

* [Configurare le notifiche e-mail](configure-service.md#configureemailnotification)
* [Aggiunta di un utente al gruppo di utenti dei moduli](#adduserstousergroup)
* [Ottenere certificati pubblici](#obtainpubliccertificates)
* [Configurare le API del servizio in  Adobe Developer Console](#createintegration)
* [Configurare il servizio cloud](configure-service.md#configure-the-cloud-service)

#### Configurare la notifica e-mail {#configureemailnotification}

Il servizio di automated forms conversion utilizza il servizio e-mail Day CQ per inviare le notifiche e-mail. Queste notifiche e-mail contengono informazioni sulle conversioni riuscite o non riuscite. Se scegliete di non ricevere la notifica, saltate questi passaggi. Per configurare Day CQ Mail Service, effettuate le seguenti operazioni:

1. Andate AEM gestore di configurazione all&#39;indirizzo `http://localhost:4502/system/console/configMgr`
1. Aprire la configurazione Day CQ Mail Service. Specificare un valore per i campi **[!UICONTROL SMTP server host name]**, **[!UICONTROL SMTP server port]** e **[!UICONTROL From address]**. Clic **[!UICONTROL Save]**.

   È possibile contattare il provider di servizi e-mail o l&#39;amministratore IT per informazioni sul nome host e sulla porta del server SMTP. Potete utilizzare qualsiasi indirizzo e-mail valido nel campo da. Ad esempio, notification@example.com o donotreply@example.com.

1. Aprite la configurazione **[!UICONTROL Day CQ Link Externalizer]**. Nel campo **[!UICONTROL Domains]**, specificate il nome host o l&#39;indirizzo IP effettivo e il numero di porta per le istanze locali, di autori e di pubblicazione. Clic **[!UICONTROL Save]**.

#### Aggiunta di un utente al gruppo di utenti dei moduli {#adduserstousergroup}

Specificate un indirizzo e-mail nel profilo dell&#39;utente AEM designato per eseguire il servizio. Assicurarsi che l&#39;utente sia il membro del gruppo [moduli utente](https://helpx.adobe.com/experience-manager/6-4/forms/using/forms-groups-privileges-tasks.html). Le e-mail vengono inviate all&#39;indirizzo e-mail dell&#39;utente che esegue la conversione. Per specificare un indirizzo e-mail per l&#39;utente e aggiungere l&#39;utente al gruppo di utenti dei`e moduli:

1. Accedete all’istanza di creazione  AEM Forms come amministratore AEM. Utilizzate le credenziali AEM locali per accedere. Non utilizzate  Adobe ID per effettuare l&#39;accesso. Toccate **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Users]**.

1. Selezionate un utente designato per eseguire il servizio di conversione e toccate **[!UICONTROL Properties]**. Viene visualizzata la pagina Modifica impostazioni utente.
1. Specificate un indirizzo e-mail nel campo **[!UICONTROL Email]** e toccate **[!UICONTROL Save]**. Le e-mail vengono inviate all&#39;indirizzo e-mail specificato al completamento o all&#39;esito negativo della conversione.
1. Toccate la scheda **Gruppi**. Nella scheda del gruppo selezionare, digitare e selezionare il gruppo **forms-users**. Toccate **Save and Close** (Salva e chiudi). L&#39;utente ora è membro del gruppo form-users.

#### Ottenere certificati pubblici {#obtainpubliccertificates}

Un certificato pubblico consente di autenticare il profilo su Adobe I/O.

1. Accedete all’istanza di creazione  AEM Forms. Accedi a **[!UICONTROL Tools]**> **[!UICONTROL Security]** > **[!UICONTROL Adobe IMS Configurations]**. Toccare **[!UICONTROL Create]**. Viene visualizzata la pagina **[!UICONTROL Adobe IMS Technical Account Configuration]**.

   ![Pagina Configurazione account tecnico IMS del Adobe ](assets/adobe-ims-technical-account-configuration.png)

1. Seleziona **[!UICONTROL Automated Forms Conversion Service]** nella soluzione cloud.

1. Selezionare la casella di controllo **[!UICONTROL Create new certificate]** e specificare un alias. L’alias funge da nome della finestra di dialogo. Toccare **[!UICONTROL Create certificate]**. Viene visualizzata una finestra di dialogo. Clic **[!UICONTROL OK]**. Il certificato viene creato.

1. Toccate **[!UICONTROL Download Public Key]** e salvate il file di certificato *AEM--IMS.crt* sul computer. Il file del certificato viene utilizzato per [Configurare le API del servizio  console sviluppatore di Adobi](#createintegration). Toccare **[!UICONTROL Next]**.

1. Specificate quanto segue:

   * Titolo: Specificate un titolo.
   * Server autorizzazioni: [https://ims-na1.adobelogin.com](https://ims-na1.adobelogin.com)\

   Lascia vuoti gli altri campi per il momento (dovranno essere riempiti successivamente). Tenete la pagina aperta.

   <!--
   Comment Type: draft

   <li> </li>
   -->

   <!--
   Comment Type: draft

   <li>Step text</li>
   -->

#### Configurare le API del servizio  console sviluppatore Adobe {#createintegration}

Per utilizzare il servizio di Automated forms conversion, create un progetto e aggiungete al progetto l&#39;API del servizio di configurazione Forms automatizzata in Adobe Developer Console. L&#39;integrazione genera Chiave API, Segreto cliente, Payload (JWT).

1. Accedete a [https://console.adobe.io/](https://console.adobe.io/). Utilizzate l&#39;account sviluppatore  Adobe ID fornito dall&#39;amministratore per accedere  console Adobe I/O e accedervi.
1. Seleziona la tua organizzazione dall’angolo in alto a destra. Se non sai qual è la tua organizzazione, contatta l’amministratore.
1. Toccare **[!UICONTROL Create new project]**. Viene visualizzata una schermata per iniziare a utilizzare il nuovo progetto. Toccare **[!UICONTROL Add API]**. Viene visualizzata una schermata con l&#39;elenco di tutte le API abilitate per l&#39;account.
1. Selezionare **[!UICONTROL Automated Forms Conversion service]** e toccare **[!UICONTROL Next]**. Viene visualizzata una schermata per configurare l&#39;API.
1. Selezionate l&#39;opzione [!UICONTROL Upload your public key], caricate il file AEM- Adobe-IMS.crt scaricato nella sezione [Acquisisci certificati pubblici](#obtainpubliccertificates) e toccate **[!UICONTROL Next]**. Viene visualizzata l&#39;opzione Crea una nuova credenziale JWT (Service Account). Toccare **[!UICONTROL Next]**.
1. Selezionate un profilo di prodotto e toccate **[!UICONTROL Save configured API]**. Selezionare il profilo creato durante la [concessione dell&#39;accesso agli sviluppatori dell&#39;organizzazione](#adduseranddevs). Se non conosci il profilo da selezionare, contatta l’amministratore.
1. Toccate **[!UICONTROL Service Account (JWT)]** per visualizzare la chiave API, il Segreto cliente e altre informazioni necessarie per collegare l&#39;istanza AEM locale al servizio di Automated forms conversion. Le informazioni presenti nella pagina vengono utilizzate per creare la configurazione IMS sul computer locale.

1. Aprite la pagina Configurazione IMS nell’istanza locale. Hai tenuto aperta questa pagina alla fine della sezione [Recuperare il certificato pubblico](#obtainpubliccertificates).

   ![Specificare titolo, chiave API, segreto cliente e payload  ](assets/ims-configuration-details.png)

1. Nella pagina tecnica IMS del Adobe , specificate Chiave API e Segreto cliente. Utilizzate i valori specificati in Account servizio (JWT) della pagina della console Sviluppatore di Adobi .

   >[!NOTE]
   >
   >
   >Per il payload, utilizzate il codice fornito nella scheda Generate JWT della pagina Service Account (JWT)  Adobe Developer Console.

1. Toccare **[!UICONTROL Save]**. Viene creata la configurazione IMS.

   >[!CAUTION]
   >
   >Create una sola configurazione IMS. Non create più configurazioni IMS.

1. Selezionate la configurazione IMS e toccate **[!UICONTROL Check Health]**. Viene visualizzata una finestra di dialogo. Toccare **[!UICONTROL Check]**. Una volta stabilita la connessione, viene visualizzato il messaggio *Token recuperato correttamente*.

   ![In caso di connessione riuscita, viene visualizzato il messaggio di recupero token completato.  ](assets/health-check.png)

   <br/> <br/>

#### Configurare il servizio cloud {#configure-the-cloud-service}

Crea una configurazione del servizio cloud per collegare l’istanza AEM al servizio di conversione. Consente inoltre di specificare un modello, un tema e frammenti di modulo per una conversione. È possibile creare più configurazioni del servizio cloud distinte per ciascun set di moduli. Ad esempio, è possibile disporre di una configurazione separata per i moduli del reparto vendite e di una configurazione separata per i moduli di assistenza clienti. Per creare una configurazione di servizio cloud, effettuate le seguenti operazioni:

1. Nell&#39;istanza AEM Forms , toccare **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Tools]** **[!UICONTROL Cloud Services]** > **[!UICONTROL Automate Forms Conversion Configuration]**.
1. Toccate la cartella **[!UICONTROL Global]** e toccate **[!UICONTROL Create]**. Viene visualizzata la pagina per la creazione della configurazione del Automated forms conversion. La configurazione viene creata nella cartella Globale. Potete anche creare la configurazione in un&#39;altra cartella già esistente o creare una nuova cartella per le configurazioni.

1. Nella pagina **[!UICONTROL Create Automated Forms Conversion Configuration]**, specificate il valore per i seguenti campi e toccate **[!UICONTROL Next]**.

   | Campo | Descrizione |
   |--- |--- |
   | Titolo | Titolo univoco per la configurazione. Il titolo viene visualizzato nell’interfaccia utente utilizzata per avviare la conversione. |
   | Nome | Nome univoco per la configurazione. La configurazione viene salvata nel CRX-Repository con il nome specificato. Il nome può essere identico al titolo. |
   | Posizione miniatura | Posizione della miniatura per la configurazione. |
   | URL servizio | URL del servizio Automated forms conversion in  Adobe Cloud. Utilizzate l&#39;URL `https://aemformsconversion.adobe.io/`. |
   | Modello | Modello predefinito da applicare ai moduli convertiti. È sempre possibile specificare un modello diverso prima di avviare la conversione. Un modello contiene la struttura di base e il contenuto iniziale per un modulo adattivo. Potete scegliere un modello dai modelli forniti out-of-the-box. Potete anche creare un modello personalizzato. |
   | Tema | Tema predefinito da applicare ai moduli convertiti. È sempre possibile specificare un tema diverso prima di avviare la conversione.  Potete fare clic sull&#39;icona per scegliere un tema fornito out-of-the-box. Potete anche creare un tema personalizzato. |
   | Frammenti esistenti | Posizione degli eventuali frammenti esistenti. |
   | Meta-modello personalizzato | Percorso del file .schema.json del meta-modello personalizzato. |



1. Nella scheda **[!UICONTROL Advanced]** della pagina **[!UICONTROL Create Automated Forms Conversion Configuration]**, specificare il valore per il campo seguente:

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
   <td>Selezionare l'opzione per generare automaticamente il documento di registrazione per i moduli convertiti. L'opzione è disponibile solo per i moduli basati su XFA (XDP e PDF forms). Quando si abilita l'opzione, dopo l'invio di un modulo, è possibile consentire ai clienti di conservare un record, in formato cartaceo o in formato documento, delle informazioni che hanno compilato nel modulo per il riferimento futuro. Tale documento è denominato documento di registrazione.</td>
   </tr>
   <tr>
   <td>Abilita Analytics</td>
   <td>Selezionare l'opzione per attivare  Adobe Analytics su tutti i moduli convertiti. Prima di utilizzare l'opzione, verificate che  Adobe Analytics sia attivato per l'istanza di AEM Forms .</td>
   </tr>
   </tbody>
   </table>

   * Se l&#39;origine è un modulo basato su XFA con estensione .XDP, il DOR di output mantiene il layout XFA, altrimenti il servizio di conversione utilizza un modello predefinito per generare DOR per altri moduli basati su XFA.
   * Quando viene inviato un modulo XFA, i dati di invio del modulo vengono salvati come elemento XML o come attributo. Esempio, `<Amount currency="USD"> 10.00 </Amount>`. La valuta viene salvata come attributo e l&#39;importo della valuta, 10.00 viene salvato come elemento. I dati di invio di un modulo adattivo non hanno attributi, ma solo elementi. Pertanto, quando un modulo basato su XFA viene convertito in modulo adattivo, i dati di invio del modulo adattivo contengono un elemento per ciascun attributo. Esempio,

   ```css
      {
         "Type": "Principal",
   
         "Amount": "10.00",
   
         "currency": "USD"
      }
   ```

1. Toccare **[!UICONTROL Create]**. Viene creata la configurazione cloud. L&#39;istanza di AEM Forms  è pronta per iniziare a convertire moduli legacy in moduli adattivi.
