---
title: Domande frequenti
seo-title: Frequently asked questions
description: Domande comuni o domande frequenti
seo-description: frequently asked questions for Automated Forms Conversion Service
uuid: 0f6dc39c-99b7-49a4-8e9e-ecc4a35110c0
topic-tags: introduction
discoiquuid: e17c2d2c-8300-4467-aa01-57365697939f
exl-id: 3a29f8d4-8ea0-49eb-bfe0-0eab5f0c52c7
source-git-commit: 47261710e6616c27c210ac53bffcc2387a06ea7a
workflow-type: tm+mt
source-wordcount: '1821'
ht-degree: 4%

---

# Domande frequenti{#frequently-asked-questions}

1. **Quale versione di AEM Forms supporta il servizio Automated forms conversion?**

   <p>Il servizio Automated forms conversion supporta AEM 6.4 Forms e AEM 6.5 Forms. Funziona sia con AEM Forms su OSGi che con i moduli AEM su JEE. Per utilizzare il servizio è necessario il pacchetto aggiuntivo AEM Forms più recente sopra AEM’istanza di authoring. Per istruzioni dettagliate, consulta <a href="configure-service.md">Configurare il servizio Automated forms conversion</a> .</p> 
    <br>

1. **È possibile installare il servizio on-premise?**

   <p>Adobe addestra regolarmente gli algoritmi AI e ML del servizio Automated forms conversion con nuovi dati impostati per migliorare l'accuratezza della conversione. Gli algoritmi aggiornati vengono distribuiti al servizio di conversione in esecuzione su Adobe Cloud a intervalli periodici. Tutti i clienti del servizio ricevono i vantaggi degli algoritmi aggiornati. Pertanto, l'implementazione centrale ospitata su cloud è la soluzione migliore per il servizio di Automated forms conversion per imparare e offrire miglioramenti continui a tutti i clienti.</p> 
    <p>Il servizio converte i moduli vuoti in moduli adattivi. Il servizio non supporta i moduli compilati e l’estrazione di dati dai moduli compilati. Rimuovere i dati dai moduli compilati e rimuovere o inserire nell'elenco Consentiti informazioni proprietarie dai moduli prima di inviare i moduli al servizio per la conversione</p> <br>

1. **Il servizio supporta tutti i formati di PDF forms? Quali sono le lingue supportate?**

   <p>Il servizio può convertire PDF forms non interattivi, XFA basato su XDP e PDF forms e AcroForms in moduli adattivi. Il servizio non supporta moduli digitalizzati o compilati. Per altre limitazioni, consulta l'articolo <a href="known-issues.md">problemi noti</a>.<br /> </p> 
    <p>Stiamo aggiungendo regolarmente supporto per altri tipi di origine. Mantieni la sezione <a href="introduction.md">Moduli PDF supportati</a> nella lista di controllo per un aggiornamento regolare sulle nuove funzioni e funzionalità aggiunte.</p>

   Il servizio può convertire in moduli adattivi solo i moduli in lingua inglese, francese, tedesca, spagnola, italiana e portoghese. Puoi tradurre i moduli adattativi generati in un’altra lingua usando [workflow di traduzione AEM.](https://helpx.adobe.com/it/experience-manager/6-5/forms/using/using-aem-translation-workflow-to-localize-adaptive-forms.html)</br> </br>

1. **Il servizio può produrre un XDP invece di un modulo adattivo?**

   <p>Il servizio non produce un output XDP. Stiamo aggiungendo regolarmente funzioni e al servizio. Mantieni la sezione <a href="introduction.md">Lingue e PDF forms supportati</a> nella lista di controllo per un aggiornamento regolare sulle nuove funzioni e funzionalità aggiunte.</p> <br>

1. **Qual è il tipo di schema generato?**

   <p>Puoi utilizzare il servizio per generare: </p>

   * un modulo adattivo associato a uno schema JSON e
   * un modulo adattivo non associato ad alcuno schema <br><br>

1. **Il servizio può convertire un modulo di Microsoft Word in moduli adattivi?**

   <p>No, il servizio non converte un modulo di Microsoft Word in un modulo adattivo. È possibile salvare moduli di Microsoft Word in formato PDF e convertire il modulo PDF in un modulo adattivo. Il processo completo è </p> <br>

   1. Utilizza Adobe Acrobat per [convertire il documento Word in un PDF non interattivo](https://helpx.adobe.com/acrobat/how-to/create-pdf-files-word-excel-website.html).
   1. Utilizza Adobe Acrobat per [convertire i PDF forms prodotti in moduli PDF compilabili](https://helpx.adobe.com/acrobat/how-to/convert-word-excel-paper-pdf-forms.html).
   1. Utilizza Adobe Acrobat per aggiornare e correggere manualmente i campi del modulo.
   1. Salvare il modulo PDF. Ora è possibile utilizzare il modulo con il servizio di conversione per generare un modulo adattivo. È inoltre possibile utilizzare il modulo come modello Documento di record.


1. **Il servizio può convertire moduli cartacei digitalizzati e moduli colorati in moduli adattivi?**

   <p>Il servizio può convertire PDF forms colore in moduli adattivi. Il servizio non supporta moduli digitalizzati o compilati. Per altre limitazioni, consulta l’articolo <a href="known-issues.md">Problemi noti</a> .</p> <br>

1. **Il servizio può convertire un modulo digitalizzato o solo l’immagine di un modulo in un modulo adattivo?**

   <p>Il servizio non supporta la conversione di moduli digitalizzati o di immagini di moduli in moduli adattivi pronti all’uso. Tuttavia è possibile utilizzare Adobe Acrobat per convertire l’immagine del modulo in un modulo PDF, quindi utilizzare il servizio per convertire il modulo PDF in un modulo adattivo. Utilizza sempre un’immagine di alta qualità del modulo in Acrobat per migliorare la qualità della conversione.</p> <br>

1. **Alcuni moduli basati su XDP utilizzano frammenti di modulo, dove devono essere caricati?**

   <p class="MsoNormal">Carica i frammenti di modulo nella cartella di conversione e conserva la struttura di cartelle originale. Consente di mantenere i percorsi relativi utilizzati nei moduli basati su XDP e nei frammenti di modulo.</p> <br>

1. **Il servizio supporta i moduli XDP associati allo schema? Se ho un XDP associato a uno schema, devo incorporare lo schema in XDP?**

   <p>Sì, il servizio supporta moduli XDP con associazione a schema e richiede l’incorporazione dello schema nel modulo XDP di origine. Quando si converte un modulo XDP associato a schema, il servizio genera uno schema JSON. Lo schema JSON è strutturalmente simile allo schema XSD dei moduli XDP di origine.</p> <br>

1. **Impossibile convertire i moduli. Qual è il motivo e come risolvere il problema?**
I motivi più comuni per cui la conversione non riesce sono:
</p>
   * Per la conversione vengono forniti PDF forms protetti. Non utilizzare PDF forms protetti da password o protetti per la conversione.
   * Connessione Internet interrotta. Assicurati di essere connesso a Internet durante la conversione.
   * Nel PDF di origine è presente un’immagine del modulo anziché del modulo effettivo.
   * Il servizio è configurato in modo errato, l&#39;URL del servizio non viene fornito o l&#39;URL del servizio fornito non è corretto. Controlla la [configurazione del servizio](configure-service.md#configure-the-cloud-service) in **[!UICONTROL AEM]** > **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Automated Forms Conversion configuration]**.
   * Configurazione IMS non configurata correttamente. Esegui un controllo dello stato della configurazione IMS per verificarne il corretto funzionamento. Per verificare se la configurazione IMS è corretta o meno:
      1. Passa a `http://[servername]:[port]/libs/cq/adobeims-configuration/content/configurations.html`
      2. Seleziona la configurazione. Fai clic su **[!UICONTROL Check Health]** nell’intestazione e fai clic su **[!UICONTROL Check]**. In caso di esito positivo, viene visualizzato il messaggio **[!UICONTROL Token retrieved successfully!]** . <br> <br>

1. **L&#39;utilizzo di font personalizzati influisce sulla conversione?**

   <p>Quando un modulo PDF non interattivo viene convertito in modulo adattivo, per migliorare la qualità di conversione, i font vengono incorporati nel modulo PDF. Il supporto per l'incorporazione dei font è limitato ai PDF forms non interattivi. Per ottimizzare la conversione dei PDF forms basati su AcroForm e XFA, vengono utilizzati i font di fallback.</p> 
    <p>Solo i moduli disponibili nella directory dei font personalizzati elencati nel campo <strong>Directory dei font del cliente</strong> della configurazione <strong> CQ-DAM-Handler-Gibson Font Manager Service</strong> sono incorporati nel modulo PDF non interattivo.</p> 
    <p> </p> <br>

1. **Il servizio identifica e utilizza i font del PDF di origine nei moduli adattivi di output?**

   <p>Lo stile e il layout di un modulo HTML reattivo sono generalmente diversi da quelli di un modulo PDF o basato su carta. Per supportare layout e stili coerenti tra le organizzazioni, i moduli adattivi utilizzano i temi <a href="https://helpx.adobe.com/experience-manager/6-5/forms/using/themes.html">per assegnare uno stile a un modulo</a>. Il servizio di conversione utilizza i font e gli stili di font specificati nel tema applicato durante la conversione. È possibile modificare i font e gli stili dei font del tema per dare un aspetto e un aspetto distinti ai componenti di un modulo adattivo.</p> <br>

1. **Il servizio estrae automaticamente JavaScript dai moduli basati su XDP e lo applica ai corrispondenti moduli adattivi?**

   <p>Il servizio non converte automaticamente gli script di moduli basati su XFA o Acro Forms nelle corrispondenti regole del modulo adattivo. Gli autori dei moduli possono utilizzare l’ <a href="https://helpx.adobe.com/experience-manager/6-5/forms/using/rule-editor.html">Editor regole</a> per aggiungere interattività a un modulo adattivo.</p> <br>

1. **Alcuni oggetti modulo non vengono convertiti correttamente in componenti modulo adattivi. Come risolvere il problema?**

   <p>Il servizio di automated forms conversion viene addestrato su un ampio set di moduli. Tuttavia, le applicazioni basate su AI/ML sono limitate dai dati e dagli schemi di formazione. Ci possono essere diversi tipi di campo, layout, schemi e contesto distinguibili dalla percezione umana, ma difficili da riconoscere automaticamente. Il servizio potrebbe non riuscire a identificare tali oggetti o riconoscerli in modo errato. È possibile utilizzare l'editor <a href="review-correct-ui-edited.md" target="_blank">Rivedi e correggi</a> per apportare le modifiche necessarie nel layout familiare basato su moduli cartacei del modulo di input.</p> <br/>

1. **Alcune correzioni vengono ripetute nei diversi moduli. Il servizio può identificare e correggere tutte le istanze di questo tipo nelle conversioni future?**

   Il servizio è formativo in modo coerente sulle tue forme e modelli. Impara nuovi schemi quotidianamente. Deve ancora iniziare ad applicare automaticamente le correzioni ripetute nei moduli. Controlla i moduli prerelease per la disponibilità di tale funzionalità. <br/><br/>

   È possibile utilizzare un metamodello per mappare gli oggetti modulo al componente modulo adattivo desiderato e preconfigurare convalide, regole, pattern di dati, testo della guida e proprietà di accessibilità per i componenti. Tutte le proprietà specificate vengono applicate durante la conversione. È possibile utilizzare il metamodello per applicare proprietà comuni ai campi. Può essere utile per ridurre alcuni problemi ripetuti nei diversi moduli.<br/><br/>

1. **Quali sono le opzioni per i moduli con dati sensibili come informazioni personali identificabili (PII)?**
Il servizio supporta solo moduli vuoti o non compilati. Non caricare moduli compilati o moduli con informazioni personali (PII). Inoltre, rimuovere i dati precompilati, le informazioni personali identificabili (PII), le informazioni riservate e le informazioni proprietarie nei moduli di origine. 
<br/>

1. **Dove devono essere posizionati l’intestazione e i piè di pagina?**

   <p>Inserire intestazione e piè di pagina in un modello di modulo adattivo. Se il modulo PDF di origine include intestazione e piè di pagina, durante la conversione il servizio rileva e sostituisce l’intestazione e il piè di pagina rilevati con intestazione e piè di pagina disponibili nel modello di modulo adattivo. Se nel modulo adattivo è inclusa un’intestazione o un piè di pagina extra, è possibile utilizzare l’ editor <a href="review-correct-ui-edited.md">Rivedi e correggi</a> per correggere o rimuovere tale intestazione o piè di pagina.</p> <br />

1. **Quanto tempo viene risparmiato dal servizio rispetto al processo manuale di pianificazione, creazione di risorse (temi, modelli), creazione e pubblicazione di un modulo adattivo?**

   <p>Il tempo dipende dalle dimensioni e dalla complessità dei moduli di input e dal numero di richieste. Il servizio intende ridurre in modo significativo il tempo a disposizione convertendo i PDF forms in moduli adattivi a un ritmo molto più veloce rispetto al processo manuale di conversione dei moduli. </p> <br />

1. **Cosa fare se si verifica un errore relativo alle librerie RSA? Il messaggio di errore è simile al messaggio indicato di seguito:** <br/>

L&#39;errore di cui sopra si verifica quando la delega di avvio non è configurata per le librerie RSA/BouncyCastle. Esegui i seguenti passaggi per risolvere il problema:   `*ERROR* [0:0:0:0:0:0:0:1 [1565757652491] POST /content/dam/formsanddocuments/demo004.affBatchProcessor.html HTTP/1.1] org.apache.sling.engine.impl.SlingRequestProcessorImpl service: Uncaught Throwable java.lang.NoClassDefFoundError: Could not initialize class com.rsa.cryptoj.o.dl at com.rsa.jsafe.JSAFE_SecureRandom.getInstance(Unknown Source) at com.adobe.internal.pdfm.util.Util.appendRandomNumberToPrefix(Util.java: 169) [com.adobe.aemfd.adobe-aemfd-assembler:6.0.34] at com.adobe.internal.pdfm.logging.JobLog.&amp;lt;init&amp;gt;(JobLog.java:126) [com.adobe.aemfd.adobe-aemfd-assembler:6.0.34]` <br>
L&#39;errore di cui sopra si verifica quando la delega di avvio non è configurata per le librerie RSA/BouncyCastle. Esegui i seguenti passaggi per risolvere il problema:
   <p> </p>

   1. Interrompi l&#39;istanza AEM. Passa alla cartella `[AEM installation directory]\crx-quickstart\conf\` . Apri il file sling.properties per la modifica. Se utilizzi `[AEM installation directory]\crx-quickstart\bin\start.bat` per avviare un&#39;istanza AEM, modifica le proprietà sling.properties che si trovano in `[AEM_root]\crx-quickstart\`.
   1. Aggiungi le seguenti proprietà al file sling.properties:<br/> `sling.bootdelegation.class.com.rsa.jsafe.provider.JsafeJCE=com.rsa.*`<br />  `sling.bootdelegation.class.org.bouncycastle.jce.provider.BouncyCastleProvider=org.bouncycastle.*`<br /> `sling.bootdelegation.xerces=org.apache.xerces.*`
   1. Salva e chiudi il file. <br/>
   1. Avvia l&#39;istanza AEM.<br/>

   <br/>

1. **Come cambiare automaticamente la cascata del testo del modulo adattivo?**

   <p>È possibile utilizzare adattivo da temi o editor di stili per modificare la custodia di un campo di un modulo adattivo. Ad esempio, è possibile aprire l’editor di temi e impostare il valore della proprietà Case di tutto il testo della maschera su maiuscolo, minuscolo o camelCase. Puoi anche utilizzare l’opzione Override CSS nell’editor di temi per creare diversi tipi di stili.</p>

1. **Posso usare i tag di testo di Adobe Sign con il servizio Automated forms conversion?**

   <p> Quando si utilizza Automated forms conversion Service per convertire un modulo PDF in un modulo adattivo e il modulo PDF dispone di tag di testo Adobe Sign, tali tag vengono convertiti nei corrispondenti campi del modulo adattivo e i dettagli del firmatario vengono compilati automaticamente.  La funzione è disponibile solo per Acro Forms e i moduli adattivi supportano un numero limitato di campi Adobe Sign.</p>  </br>

1. **Come si crea un modulo PDF abilitato per Adobe Sign?**

   </p>Per creare un modulo PDF abilitato per Adobe Sign:</p>

   Aggiungi [tag di testo Adobe Sign](https://helpx.adobe.com/sign/using/text-tag.html) ai nomi di campo o utilizza l&#39;opzione [Converti in modulo Adobe Sign](https://helpx.adobe.com/sign/using/create-forms-with-acrobat.html) .
