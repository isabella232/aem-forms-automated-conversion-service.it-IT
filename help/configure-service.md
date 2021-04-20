---
title: Configurazione del servizio di conversione automatica dei moduli
description: Pronta la tua istanza AEM per utilizzare il servizio Automated forms conversion
role: Business Practitioner, Administrator
translation-type: tm+mt
source-git-commit: a9bab62fbe5ecc4b233e9bc55b9e461a5967b471
workflow-type: tm+mt
source-wordcount: '2673'
ht-degree: 8%

---


# Configurazione del servizio di conversione automatica dei moduli {#about-this-help}

Questa guida descrive come un amministratore AEM può configurare il servizio Automated forms conversion per automatizzare la conversione dei propri PDF forms in moduli adattivi. Questa guida è rivolta agli amministratori IT e AEM della tua organizzazione. Le informazioni fornite si basano sul presupposto che chiunque legga questa Guida abbia familiarità con le seguenti tecnologie:

* Installazione, configurazione e amministrazione dei pacchetti Adobe Experience Manager e AEM,

* utilizzando sistemi operativi Linux® e Microsoft® Windows®,

* Configurazione dei server di posta SMTP

<!--- >[!VIDEO](https://video.tv.adobe.com/v/29267/) 

**Watch the video or read the article to configure Automated Forms Conversion service** -->

## Onboarding{#onboarding}

Il servizio è disponibile gratuitamente per AEM i clienti Forms 6.4 e Forms On-Premise 6.5 e per i clienti aziendali di Adobe-Managed Service. È possibile contattare il team di vendita Adobe o il proprio rappresentante Adobe per richiedere l’accesso al servizio. Il servizio è disponibile gratuitamente e preabilitato per i clienti AEM Forms as a Cloud Service.

Adobe abilita l’accesso per la tua organizzazione e fornisce i privilegi richiesti alla persona designata come amministratore dell’organizzazione. L’amministratore può concedere agli sviluppatori AEM Forms (utenti) dell’organizzazione l’accesso al servizio.

## Prerequisiti {#prerequisites}

Per utilizzare il servizio Automated forms conversion è necessario quanto segue:

* Servizio automated forms conversion abilitato per la tua organizzazione
* Un account Adobe ID con privilegi di amministratore per il servizio di conversione
* Un’istanza di authoring di Cloud Service in AEM 6.4, AEM 6.5 o AEM Forms con Service Pack AEM più recente o aggiornamenti più recenti.
* Un utente AEM (nell&#39;istanza AEM) che è membro del gruppo forms-user

## Configurazione dell’ambiente {#setuptheservice}

Prima di utilizzare il servizio, prepara la tua istanza di autore AEM per connetterti al servizio in esecuzione su Adobe Cloud. Esegui i seguenti passaggi nella sequenza elencata per preparare l&#39;istanza per il servizio:

1. [Scarica e installa AEM 6.4, AEM 6.5 o onboard AEM Forms as a Cloud Service](#aemquickstart)
1. [Scarica e installa l&#39;ultimo Service Pack AEM](#servicepack)
1. [Scarica e installa il pacchetto aggiuntivo AEM Forms più recente](#downloadaemformsaddon)
1. (facoltativo) [Scarica e installa l&#39;ultimo pacchetto del connettore](#installConnectorPackage)
1. [Creare temi e modelli personalizzati](#referencepackage)

### Scarica e installa AEM 6.4 o AEM 6.5 oppure onboard AEM Forms as a Cloud Service {#aemquickstart}


Il servizio di automated forms conversion viene eseguito su AEM’istanza di authoring. È necessario AEM 6.4, AEM 6.5 o AEM Forms come Cloud Service per impostare un&#39;istanza di authoring AEM.

* Se non hai AEM 6.4 o AEM 6.5 in esecuzione, scaricalo dalle posizioni seguenti. Dopo aver scaricato AEM, per istruzioni su come impostare un&#39;istanza AEM dell&#39;autore, consulta [distribuzione e manutenzione](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/deploy.html#defaultlocalinstall):

   * Se sei un cliente AEM esistente, scarica AEM 6.4 o AEM 6.5 dal [sito web relativo alle licenze di Adobe](http://licensing.adobe.com).

   * Se sei un partner di Adobe, utilizza [Adobe Partner Training Program](https://adobe.allegiancetech.com/cgi-bin/qwebcorporate.dll?idx=82357Q) per richiedere AEM 6.4 o AEM 6.5.

* Se utilizzi AEM Forms as a Cloud Service, consulta onboard in [AEM Forms as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/setup-environment/setup-forms-cloud-service.html?lang=en#setup-environment) e [configura un ambiente di sviluppo locale](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/setup-environment/setup-local-development-environment.html?lang=en#setup-environment).

### (Solo per AEM 6.4 e AEM 6.5) Scarica e installa AEM più recente Service Pack {#servicepack}

Scarica e installa AEM Service Pack più recente. Per istruzioni dettagliate, consulta le [AEM Note sulla versione 6.4 Service Pack](https://helpx.adobe.com/it/experience-manager/6-4/release-notes/sp-release-notes.html) o [AEM Note sulla versione 6.5 Service Pack](https://helpx.adobe.com/it/experience-manager/6-5/release-notes/sp-release-notes.html).

### (Solo per AEM 6.4 e AEM 6.5) Scarica e installa il pacchetto aggiuntivo AEM Forms {#downloadaemformsaddon}

Un’istanza AEM contiene funzionalità di base dei moduli. Il servizio di conversione richiede funzionalità complete di AEM Forms. Scarica e installa il pacchetto aggiuntivo di AEM Forms per sfruttare tutte le funzionalità di AEM Forms. Il pacchetto è necessario per configurare ed eseguire il servizio di conversione. Per istruzioni dettagliate, consulta [Installare e configurare le funzionalità di acquisizione dati.](https://helpx.adobe.com/it/experience-manager/6-5/forms/using/installing-configuring-aem-forms-osgi.html)

>[!NOTE]
> Assicurati di eseguire le configurazioni obbligatorie post-installazione dopo l&#39;installazione del pacchetto aggiuntivo.


<!-- ### (Optional) Download and install connector package  {#installConnectorPackage}

The connector package provides early access to the [Auto-detect logical sections](convert-existing-forms-to-adaptive-forms.md#run-the-conversion) features and improvements delivered in release AFC-2020.03.1. Do not install the package if you do not require feature and improvements delivered in AFC-2020.03.1.  You can [download the connector package from AEM Package Share](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/featurepack/AFCS-Connector-2020.03.1). -->


### Creare temi e modelli personalizzati {#referencepackage}

Se si avvia AEM 6.4 o AEM 6.5 in [modalità di produzione](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/production-ready.html) (modalità di esecuzione nosamplecontent), i pacchetti di riferimento non vengono installati. I pacchetti di riferimento contengono temi e modelli di esempio. Il servizio Automated forms conversion richiede almeno un tema e un modello per convertire un modulo PDF in un modulo adattivo. Crea un tema e un modello personalizzati e specifica la [configurazione del servizio](#configure-the-cloud-service) per utilizzare modelli e temi personalizzati prima di utilizzare il servizio.

Puoi anche scaricare e installare il pacchetto [Risorse di riferimento AEM Forms](https://experience.adobe.com/#/downloads/content/software-distribution/it/aemcloud.html) sulla tua istanza di authoring. Crea alcuni temi e modelli di riferimento.

## Configurazione del servizio {#configure-the-service}

Prima di procedere alla configurazione del servizio e di collegare l’istanza locale al servizio in esecuzione su Adobe Cloud, scopri gli utenti tipo e i privilegi necessari per connettersi al servizio. Il servizio utilizza due diversi tipi di utenti tipo, amministratori e sviluppatori:

* **Amministratori**: Gli amministratori sono responsabili della gestione del software e dei servizi Adobe per la propria organizzazione. Gli amministratori concedono l’accesso agli sviluppatori della propria organizzazione per connettersi al servizio di Automated forms conversion in esecuzione su Adobe Cloud. Quando un amministratore è abilitato per un&#39;organizzazione, l&#39;amministratore riceve un&#39;e-mail con titolo **[!UICONTROL 'You now have administrator rights to manage Adobe software and services for your organization']**. Se sei un amministratore, controlla la tua casella di posta elettronica con il titolo menzionato in precedenza e procedi a [concedere l&#39;accesso agli sviluppatori della tua organizzazione](#adduseranddevs).

![E-mail di concessione accesso amministratore](assets/admin-console-adobe-io-access-grantedx75.png)

* **Sviluppatori**: Uno sviluppatore collega un’istanza di authoring AEM Forms locale al servizio Automated forms conversion in esecuzione su Adobe Cloud. Quando un amministratore concede i diritti a uno sviluppatore per connettersi al servizio Automated forms conversion, allo sviluppatore viene inviata un’e-mail con il titolo L’utente dispone dell’accesso per sviluppatori per gestire le integrazioni API Adobe per la propria organizzazione. Se sei uno sviluppatore, controlla la tua casella di posta elettronica con il titolo menzionato in precedenza e procedi a [Connetti la tua istanza di AEM locale al servizio di Automated forms conversion su Adobe Cloud.](#connectafcadobeio)

![E-mail di concessione di accesso per sviluppatori](assets/email-developer-accessx94.png)

### (Solo per amministratori di AEM 6.4 e AEM 6.5) Concedi l&#39;accesso agli sviluppatori della tua organizzazione {#adduseranddevs}

Dopo l’Adobe che abilita l’accesso per la tua organizzazione e fornisce all’amministratore i privilegi necessari, l’amministratore può accedere all’Admin Console (istruzioni dettagliate di seguito), creare un profilo e aggiungere sviluppatori al profilo. Gli sviluppatori possono collegare un’istanza locale di AEM Forms al servizio Automated forms conversion su Adobe Cloud.

Gli sviluppatori sono membri dell’organizzazione designata per l’esecuzione del servizio di conversione. Solo gli sviluppatori che vengono aggiunti al profilo del servizio Adobe Automated forms conversion possono utilizzare il servizio di Automated forms conversion. Esegui i passaggi seguenti per creare un profilo e aggiungervi sviluppatori. Per concedere agli sviluppatori dell’organizzazione l’accesso richiesto è necessario almeno un profilo:

1. Accedi a [Admin Console](https://adminconsole.adobe.com/). Utilizza **Adobe ID** dell&#39;amministratore predisposto per utilizzare il servizio Automated forms conversion per l&#39;accesso. Non effettuare l&#39;accesso con altri ID o Federated ID.
1. Fai clic sull’opzione **[!UICONTROL Automated Forms Conversion]** .
1. Fare clic su **[!UICONTROL New Profile]** nella scheda **[!UICONTROL Products]**.
1. Specifica **[!UICONTROL Name]**, **[!UICONTROL Display Name]** e **[!UICONTROL Description]** per il profilo. Clic **[!UICONTROL Done]**. Viene creato un profilo.

   ![Specifica i dettagli per il nuovo profilo.](assets/create-new-profile-details.png)

1. Aggiungi lo sviluppatore al profilo. Per aggiungere gli sviluppatori:
   1. In [Admin Console](https://adminconsole.adobe.com/enterprise), passa alla scheda Panoramica .
   1. Fai clic su **[!UICONTROL Assign Developers]** sulla scheda prodotto richiesta.
   1. Inserisci l’indirizzo e-mail e, facoltativamente, il nome e il cognome degli sviluppatori.
   1. Seleziona i profili di prodotto. Toccare **[!UICONTROL Save]**.

Ripeti i passaggi precedenti per tutti gli utenti. Per ulteriori dettagli sull’aggiunta di sviluppatori, consulta [Gestire gli sviluppatori](https://helpx.adobe.com/enterprise/using/manage-developers.html).

Una volta che un amministratore aggiunge sviluppatori al profilo di Adobe I/O, gli sviluppatori vengono informati via e-mail. Dopo aver ricevuto l&#39;e-mail, gli sviluppatori possono procedere alla [connessione di un&#39;istanza AEM Forms locale con il servizio Automated forms conversion su Adobe Cloud](#connectafcadobeio).

### (Solo per sviluppatori) Collega l’istanza AEM Forms locale al servizio Automated forms conversion su Adobe Cloud {#connectafcadobeio}

Dopo che un amministratore ti fornisce l’accesso per sviluppatori, puoi collegare la tua istanza AEM Forms locale al servizio Automated forms conversion in esecuzione su Adobe Cloud. Esegui i seguenti passaggi nella sequenza elencata per collegare l’istanza AEM Forms al servizio:

* [Configurare le notifiche e-mail](configure-service.md#configureemailnotification)
* [Aggiungi utente al gruppo utenti moduli](#adduserstousergroup)
* [Recuperare certificati pubblici](#obtainpubliccertificates)
* [Configurare le API del servizio in Adobe Developer Console](#createintegration)
* [Configurare il servizio cloud](configure-service.md#configure-the-cloud-service)

#### Configurare la notifica e-mail {#configureemailnotification}

Il servizio di automated forms conversion utilizza il servizio di posta Day CQ per inviare notifiche e-mail. Queste notifiche e-mail contengono informazioni sulle conversioni riuscite o non riuscite. Se scegli di non ricevere la notifica, salta questi passaggi. Esegui i seguenti passaggi per configurare Day CQ Mail Service:

* Per Forms 6.4 Forms o AEM 6.5:

   1. Vai a AEM gestione configurazione all&#39;indirizzo `http://localhost:4502/system/console/configMgr`
   1. Apri la configurazione Day CQ Mail Service . Specificare un valore per i campi **[!UICONTROL SMTP server host name]**, **[!UICONTROL SMTP server port]** e **[!UICONTROL From address]**. Clic **[!UICONTROL Save]**.

      Per informazioni sul nome host e la porta del server SMTP, contattare il provider di servizi e-mail o l&#39;amministratore IT. Puoi utilizzare qualsiasi indirizzo e-mail valido nel campo da . Ad esempio, notification@example.com o donotreply@example.com.

   1. Apri la configurazione **[!UICONTROL Day CQ Link Externalizer]**. Nel campo **[!UICONTROL Domains]** , specifica il nome host o l’indirizzo IP effettivo e il numero di porta per le istanze locali, di authoring e di pubblicazione. Clic **[!UICONTROL Save]**.

* Per AEM Forms as a Cloud Service, [registra un ticket di supporto per abilitare il servizio e-mail](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html?lang=en#sending-email).

#### Aggiungi utente al gruppo utenti dei moduli {#adduserstousergroup}

Specifica un indirizzo e-mail nel profilo dell’utente AEM designato per eseguire il servizio. Assicurati che l&#39;utente sia il membro del gruppo [forms user](https://helpx.adobe.com/experience-manager/6-4/forms/using/forms-groups-privileges-tasks.html) . Le e-mail vengono inviate all’indirizzo e-mail dell’utente che esegue la conversione. Per specificare un indirizzo e-mail per l’utente e aggiungere l’utente al gruppo di utenti dei moduli:

1. Accedi alla tua istanza di authoring di AEM Forms come amministratore AEM. Utilizza le tue credenziali AEM locali per accedere. Non utilizzare Adobe ID per l&#39;accesso. Tocca **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Users]**.

1. Seleziona un utente designato per eseguire il servizio di conversione e tocca **[!UICONTROL Properties]**. Viene visualizzata la pagina Modifica impostazioni utente.
1. Specifica un indirizzo e-mail nel campo **[!UICONTROL Email]** e tocca **[!UICONTROL Save]**. Le e-mail vengono inviate all’indirizzo e-mail specificato al completamento o all’errore della conversione.
1. Tocca la scheda **Gruppi** . Nella scheda seleziona gruppo, digita e seleziona il gruppo **forms-users** . Tocca **Salva e chiudi**. L’utente è ora membro del gruppo utenti moduli.

#### (Solo per AEM 6.4 e AEM 6.5) Ottenere certificati pubblici {#obtainpubliccertificates}

Un certificato pubblico consente di autenticare il profilo su Adobe I/O.

1. Accedi alla tua istanza di authoring di AEM Forms. Accedi a **[!UICONTROL Tools]**> **[!UICONTROL Security]** > **[!UICONTROL Adobe IMS Configurations]**. Toccare **[!UICONTROL Create]**. Viene visualizzata la pagina **[!UICONTROL Adobe IMS Technical Account Configuration]** .

   ![Pagina Adobe IMS Technical Account Configuration (Configurazione account tecnico IMS)](assets/adobe-ims-technical-account-configuration.png)

1. Seleziona **[!UICONTROL Automated Forms Conversion Service]** in Soluzione cloud.

1. Selezionare la casella di controllo **[!UICONTROL Create new certificate]** e specificare un alias. L’alias funge da nome della finestra di dialogo. Toccare **[!UICONTROL Create certificate]**. Viene visualizzata una finestra di dialogo. Clic **[!UICONTROL OK]**. Il certificato viene creato.

1. Tocca **[!UICONTROL Download Public Key]** e salva il file di certificato *AEM-Adobe-IMS.crt* sul computer. Il file del certificato viene utilizzato per [configurare le API del servizio in Adobe Developer Console](#createintegration). Toccare **[!UICONTROL Next]**.

1. Specifica quanto segue:

   * Titolo: Specifica un titolo.
   * Server autorizzazioni: [https://ims-na1.adobelogin.com](https://ims-na1.adobelogin.com)\

   Lascia vuoti gli altri campi per il momento (dovranno essere riempiti successivamente). Tieni aperta la pagina.

   <!--
   Comment Type: draft

   <li> </li>
   -->

   <!--
   Comment Type: draft

   <li>Step text</li>
   -->

#### (Solo per AEM 6.4 e AEM 6.5) Configura le API del servizio su Adobe Developer Console {#createintegration}

Per utilizzare il servizio Automated forms conversion, crea un progetto e aggiungi l’API Servizio di configurazione Forms automatizzata al progetto in Adobe Developer Console. L’integrazione genera Chiave API, Segreto client, Payload (JWT).

1. Accedi a [https://console.adobe.io/](https://console.adobe.io/). Utilizza il tuo account sviluppatore Adobe ID fornito dall’amministratore per accedere alla console Adobe I/O e accedervi.
1. Seleziona la tua organizzazione dall’angolo in alto a destra. Se non sai qual è la tua organizzazione, contatta l’amministratore.
1. Toccare **[!UICONTROL Create new project]**. Viene visualizzata una schermata per iniziare a utilizzare il nuovo progetto. Toccare **[!UICONTROL Add API]**. Viene visualizzata una schermata con l’elenco di tutte le API abilitate per il tuo account.
1. Seleziona **[!UICONTROL Automated Forms Conversion service]** e tocca **[!UICONTROL Next]**. Viene visualizzata una schermata per configurare l’API.
1. Seleziona l’opzione [!UICONTROL Upload your public key] , carica il file AEM-Adobe-IMS.crt scaricato nella sezione [Ottieni certificati pubblici](#obtainpubliccertificates) e tocca **[!UICONTROL Next]**. Viene visualizzata l’opzione Crea una nuova credenziale dell’account di servizio (JWT). Toccare **[!UICONTROL Next]**.
1. Seleziona un profilo di prodotto e tocca **[!UICONTROL Save configured API]**. Seleziona il profilo creato mentre [concedi l&#39;accesso agli sviluppatori della tua organizzazione](#adduseranddevs). Se non conosci il profilo da selezionare, contatta l’amministratore.
1. Tocca **[!UICONTROL Service Account (JWT)]** per visualizzare la chiave API, il segreto client e altre informazioni necessarie per collegare l’istanza AEM locale al servizio di Automated forms conversion. Le informazioni presenti nella pagina vengono utilizzate per creare la configurazione IMS sul computer locale.

1. Apri la pagina Configurazione IMS nell’istanza locale. Hai tenuto aperta questa pagina alla fine della sezione [Recuperare il certificato pubblico](#obtainpubliccertificates).

   ![Specifica titolo, chiave API, segreto client e payload  ](assets/ims-configuration-details.png)

1. Nella pagina tecnica Adobe IMS , specifica Chiave API e Segreto client . Utilizza i valori specificati in Account di servizio (JWT) della pagina Adobe Developer Console.

   >[!NOTE]
   >
   >
   >Per il payload, utilizza il codice fornito nella scheda Genera JWT della pagina Service Account (JWT) di Adobe Developer Console.

1. Toccare **[!UICONTROL Save]**. Viene creata la configurazione IMS.

   >[!CAUTION]
   >
   >Crea una sola configurazione IMS. Non creare più di una configurazione IMS.

1. Seleziona la configurazione IMS e tocca **[!UICONTROL Check Health]**. Viene visualizzata una finestra di dialogo. Toccare **[!UICONTROL Check]**. Una volta stabilita la connessione, viene visualizzato il messaggio *Token recuperato correttamente*.

   ![Al termine della connessione, viene visualizzato il messaggio del token recuperato correttamente.  ](assets/health-check.png)

   <br/> <br/>

#### Configura il Cloud Service {#configure-the-cloud-service}

Crea una configurazione di Cloud Service per collegare la tua istanza AEM al servizio di conversione. Consente inoltre di specificare un modello, un tema e frammenti di modulo per una conversione. Puoi creare più configurazioni di servizi cloud separate per ciascun set di moduli. Ad esempio, è possibile disporre di una configurazione separata per i moduli del reparto vendite e una separata per i moduli di assistenza clienti. Esegui i seguenti passaggi per creare una configurazione del servizio cloud:

1. Nell’istanza di AEM Forms, tocca **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Tools]**> **[!UICONTROL Cloud Services]** > **[!UICONTROL Automate Forms Conversion Configuration]**.
1. Tocca la cartella **[!UICONTROL Global]** e tocca **[!UICONTROL Create]**. Viene visualizzata la pagina per la creazione della configurazione del Automated forms conversion. La configurazione viene creata nella cartella Globale. Puoi anche creare la configurazione in un&#39;altra cartella esistente o creare una cartella per le configurazioni.

1. Nella pagina **[!UICONTROL Create Automated Forms Conversion Configuration]** , specifica il valore per i campi seguenti e tocca **[!UICONTROL Next]**.

   | Campo | Descrizione |
   |--- |--- |
   | Titolo | Titolo univoco per la configurazione. Il titolo viene visualizzato nell’interfaccia utente utilizzata per avviare la conversione. |
   | Nome | Nome univoco per la configurazione. La configurazione viene salvata nel CRX-Repository con il nome specificato. Il nome può essere identico al titolo. |
   | Posizione della miniatura | Posizione della miniatura per la configurazione. |
   | URL servizio | URL del servizio Automated forms conversion su Adobe Cloud. Utilizza l’ URL `https://aemformsconversion.adobe.io/` . |
   | Modello | Modello predefinito da applicare ai moduli convertiti. Puoi sempre specificare un modello diverso prima di avviare la conversione. Un modello contiene la struttura di base e il contenuto iniziale di un modulo adattivo. Puoi scegliere un modello dai modelli forniti come predefiniti. Puoi anche creare un modello personalizzato. |
   | Tema | Tema predefinito da applicare ai moduli convertiti. Puoi sempre specificare un tema diverso prima di avviare la conversione.  Puoi fare clic sull’icona per scegliere un tema fornito come predefinito. Puoi anche creare un tema personalizzato. |
   | Frammenti esistenti | Posizione dei frammenti esistenti, se presenti. |
   | Meta-modello personalizzato | Percorso del file .schema.json del metamodello personalizzato. |



1. Nella scheda **[!UICONTROL Advanced]** della pagina **[!UICONTROL Create Automated Forms Conversion Configuration]** , specifica il valore per il campo seguente:

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
   <td>Selezionare l’opzione per generare automaticamente Documento di record per i moduli convertiti. L’opzione è disponibile solo per i moduli basati su XFA (XDP e PDF forms). Quando si attiva l’opzione, dopo l’invio di un modulo è possibile consentire ai clienti di conservare un record, in formato cartaceo o in formato documento, delle informazioni che hanno compilato nel modulo per il riferimento futuro. Tale documento è denominato documento di registrazione.</td>
   </tr>
   <tr>
   <td>Abilita Analytics</td>
   <td>(Solo per AEM 6.4 e AEM 6.5) Seleziona l’opzione per abilitare Adobe Analytics su tutti i moduli convertiti. Prima di utilizzare l’opzione , accertati che Adobe Analytics sia abilitato per l’istanza AEM Forms.</td>
   </tr>
   </tbody>
   </table>

   * Se l’origine è un modulo basato su XFA con estensione XDP, l’output DOR mantiene il layout XFA, altrimenti il servizio di conversione utilizza un modello preconfigurato per generare DOR per altri moduli basati su XFA.
   * Quando un modulo XFA viene inviato, i dati di invio del modulo vengono salvati come elemento XML o come attributo. Esempio, `<Amount currency="USD"> 10.00 </Amount>`. La valuta viene salvata come attributo e importo della valuta, 10.00 viene salvato come elemento. I dati di invio di un modulo adattivo non hanno attributi, dispone solo di elementi. Pertanto, quando un modulo basato su XFA viene convertito in modulo adattivo, i dati di invio del modulo adattivo contengono un elemento per ciascun attributo. Esempio,

   ```css
      {
         "Type": "Principal",
   
         "Amount": "10.00",
   
         "currency": "USD"
      }
   ```

1. Toccare **[!UICONTROL Create]**. Viene creata la configurazione cloud. L’istanza AEM Forms è pronta per iniziare a convertire i moduli legacy in moduli adattivi.
