---
title: Domande frequenti
seo-title: Domande frequenti
description: Domande comuni o domande frequenti
seo-description: domande frequenti su Automated Forms Conversion Service
uuid: 0f6dc39c-99b7-49a4-8e9e-ecc4a35110c0
topic-tags: introduction
discoiquuid: e17c2d2c-8300-4467-aa01-57365697939f
translation-type: tm+mt
source-git-commit: 022b86b77c4a524f320cbcbcd6bad4403ddf57d8

---


# Frequently asked questions{#frequently-asked-questions}

1. **Quale versione di AEM Forms supporta il servizio di conversione automatica dei moduli?**
   <p>Il servizio di conversione automatizzata dei moduli supporta i moduli AEM 6.4 e AEM 6.5. Funziona sia con AEM Forms su OSGi che con AEM Forms su JEE. Per utilizzare il servizio è necessario disporre del pacchetto aggiuntivo AEM Forms più recente sull’istanza di creazione di AEM. Per istruzioni dettagliate, vedere <a href="configure-service.md">Configurare il servizio di conversione</a> automatica dei moduli.</p> 
    <br>

1. **È possibile installare il servizio in sede?**
   <p>Adobe addestra regolarmente gli algoritmi AI e ML del servizio di conversione automatizzata dei moduli con nuovi dati impostati per migliorare la precisione di conversione. Gli algoritmi aggiornati vengono distribuiti al servizio di conversione in esecuzione su Adobe Cloud a intervalli periodici. A tutti i clienti del servizio vengono aggiunti gli algoritmi aggiornati. Pertanto, l'implementazione centrale ospitata nel cloud è ideale per il servizio di conversione automatica dei moduli per apprendere e distribuire continuamente miglioramenti a tutti i clienti.</p> 
    <p>Il servizio converte i moduli vuoti in moduli adattivi. Il servizio non supporta i moduli compilati e l'estrazione dei dati dai moduli compilati. Rimuovere i dati dai moduli compilati e rimuovere o inserire nella whitelist le informazioni proprietarie dei moduli prima di inviarli al servizio per la conversione</p> <br>

1. **Il servizio supporta tutti i formati di moduli PDF? Quali lingue sono supportate?**
   <p>Il servizio consente di convertire moduli PDF non interattivi, moduli XFA, XDP e PDF basati su XFA e moduli Acrobat in moduli adattivi. Il servizio non supporta moduli digitalizzati o compilati. Per altre limitazioni, consultate l'articolo sui problemi <a href="known-issues.md"></a> noti.<br /> </p> 
    <p>Stiamo regolarmente aggiungendo supporto per altri tipi di fonti. Tenere presente la sezione <a href="introduction.md">dei moduli</a> PDF supportata nell'elenco di controllo per un aggiornamento regolare delle funzioni e delle funzionalità aggiunte di recente.</p>

   Il servizio può convertire solo moduli in lingua inglese in moduli adattivi. È possibile tradurre i moduli adattivi generati in un&#39;altra lingua utilizzando il flusso di lavoro di traduzione di [AEM.](https://helpx.adobe.com/experience-manager/6-5/forms/using/using-aem-translation-workflow-to-localize-adaptive-forms.html)</br> </br>

1. **Il servizio può produrre un XDP invece di un modulo adattivo?**
   <p>Il servizio non produce un output XDP. Stiamo aggiungendo regolarmente funzioni e servizi. Tenere presente nell'elenco di controllo la sezione relativa alle lingue e ai moduli <a href="introduction.md">PDF</a> supportati per un aggiornamento regolare delle funzioni e delle funzionalità aggiunte di recente.</p> <br>

1. **Qual è il tipo di schema generato?**
   <p>Potete utilizzare il servizio per generare: </p>

   * un modulo adattivo associato a uno schema JSON e
   * un modulo adattivo non associato ad alcuno schema <br><br>

1. **È possibile convertire un modulo di Microsoft Word in moduli adattivi?**
   <p>No, il servizio non converte un modulo di Microsoft Word in modulo adattivo. È possibile salvare i moduli di Microsoft Word in un modulo PDF e convertire il modulo PDF in un modulo adattivo. Il processo completo è </p> <br>

   1. Utilizzare Adobe Acrobat per [convertire il documento Word in un PDF](https://helpx.adobe.com/acrobat/how-to/create-pdf-files-word-excel-website.html)non interattivo.
   1. Utilizzare Adobe Acrobat per [convertire i moduli PDF prodotti in moduli](https://helpx.adobe.com/acrobat/how-to/convert-word-excel-paper-pdf-forms.html)PDF compilabili.
   1. Utilizzare Adobe Acrobat per aggiornare e correggere manualmente i campi del modulo.
   1. Salvare il modulo PDF. Ora è possibile utilizzare il modulo con il servizio di conversione per generare un modulo adattivo. È inoltre possibile utilizzare il modulo come modello Documento di registrazione.


1. **È possibile convertire moduli cartacei scansionati e moduli colorati in moduli adattivi?**
   <p>Il servizio consente di convertire i moduli PDF in moduli adattivi. Il servizio non supporta moduli digitalizzati o compilati. Per altre limitazioni, consultate l'articolo sui problemi <a href="known-issues.md"></a> noti.</p> <br>

1. **È possibile convertire un modulo acquisito da scanner o solo l&#39;immagine di un modulo in un modulo adattivo?**
   <p>Il servizio non supporta la conversione di moduli digitalizzati o di un'immagine di un modulo in un modulo out-of-the-box adattivo. Tuttavia, è possibile utilizzare Adobe Acrobat per convertire l'immagine di un modulo in un modulo PDF. Quindi, utilizzare il servizio per convertire il modulo PDF in un modulo adattivo. Utilizzare sempre un'immagine di alta qualità del modulo per la conversione in Acrobat. Migliora la qualità della conversione.</p> <br>

1. **Alcuni moduli basati su XDP utilizzano i frammenti di modulo, dove è possibile caricare tali frammenti?**
   <p class="MsoNormal">Caricate i frammenti di modulo nella cartella di conversione e mantenete la struttura di cartelle originale. Consente di mantenere i percorsi relativi utilizzati nei moduli basati su XDP e nei frammenti di modulo.</p> <br>

1. **Il servizio supporta i moduli XDP associati allo schema? Se si dispone di un XDP associato a uno schema, è necessario incorporare lo schema in XDP?**
   <p>Sì, il servizio supporta i moduli XDP associati allo schema e richiede che lo schema sia incorporato nel modulo XDP di origine. Quando si converte un modulo XDP associato a uno schema, il servizio genera uno schema JSON. Lo schema JSON è strutturalmente simile allo schema XSD dei moduli XDP di origine.</p> <br>

1. **Il servizio non è riuscito a convertire i moduli. Qual è il motivo e come risolvere il problema?**
I motivi più comuni per cui la conversione non riesce sono:</p>
   * I moduli PDF protetti vengono forniti per la conversione. Non utilizzare moduli PDF protetti da password o protetti per la conversione.
   * Connessione Internet interrotta. Assicurati di essere connessi a Internet durante la conversione.
   * Nel PDF di origine è presente un&#39;immagine del modulo invece del modulo effettivo.
   * Il servizio è configurato in modo non corretto, l&#39;URL del servizio non viene fornito o l&#39;URL del servizio fornito non è corretto. Controllate la configurazione [del](configure-service.md#configure-the-cloud-service) servizio in **[!UICONTROL AEM]** > **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Automated Forms Conversion configuration]**.
   * Configurazione IMS non configurata correttamente. Per verificare che funzioni correttamente, eseguite un controllo dello stato della configurazione IMS. Per verificare se la configurazione IMS è corretta o meno:
      1. Passa a `http://[servername]:[port]/libs/cq/adobeims-configuration/content/configurations.html`
      2. Selezionate la configurazione. Fate clic sull’intestazione **[!UICONTROL Check Health]** e fate clic su **[!UICONTROL Check]**. In caso di esito positivo, riceverete **[!UICONTROL Token retrieved successfully!]** un messaggio. <br> <br>

1. **L&#39;utilizzo di font personalizzati influisce sulla conversione?**
   <p>Quando un modulo PDF non interattivo viene convertito in un modulo adattivo, per migliorare la qualità della conversione, i font vengono incorporati nel modulo PDF. Il supporto per l'incorporazione dei font è limitato ai moduli PDF non interattivi. Per ottimizzare la conversione dei moduli PDF basati su AcroForm e XFA, vengono utilizzati i font di fallback.</p> 
    <p>Nel modulo PDF non interattivo sono incorporati solo i moduli disponibili nella directory dei font personalizzati elencata nel campo della directory <strong>Font del servizio</strong> <strong></strong> CQ-DAM-Handler-Gibson Font Manager.</p> 
    <p> </p> <br>

1. **Il servizio identifica e utilizza i font del PDF di origine nei moduli adattivi di output?**
   <p>Lo stile e il layout di un modulo HTML reattivo sono generalmente diversi da quelli di un modulo PDF o basato su carta. Per supportare layout e stile coerenti nelle varie organizzazioni, i moduli adattivi utilizzano <a href="https://helpx.adobe.com/experience-manager/6-5/forms/using/themes.html">i temi per formattare un modulo</a>. Il servizio di conversione utilizza i font e gli stili di font specificati nel tema applicato durante la conversione. È possibile modificare i font e gli stili dei font del tema per conferire un aspetto e un aspetto distinti ai componenti di un modulo adattivo.</p> <br>

1. **Il servizio estrae automaticamente JavaScript dai moduli basati su XDP e lo applica ai moduli adattivi corrispondenti?**
   <p>Il servizio non converte automaticamente gli script di moduli basati su XFA o su moduli Acro nelle regole del modulo adattivo corrispondenti. Gli autori dei moduli possono utilizzare l'editor <a href="https://helpx.adobe.com/experience-manager/6-5/forms/using/rule-editor.html"></a> Regola per aggiungere interattività a un modulo adattivo.</p> <br>

1. **Alcuni oggetti modulo non vengono convertiti correttamente in componenti modulo adattivi. Come risolvere il problema?**
   <p>Il servizio di conversione automatizzata dei moduli è disponibile in una vasta gamma di moduli. Tuttavia, le applicazioni basate su AI/ML sono limitate dai dati e dai pattern di formazione. Possono essere presenti diversi tipi di campo, layout, pattern e contesto, distinguibili dalla percezione umana ma difficili da riconoscere automaticamente. Il servizio potrebbe non identificare tali oggetti o non riconoscerli correttamente. È possibile utilizzare l'editor <a href="review-correct-ui-edited.md" target="_blank">Revisione e Correzione</a> per apportare le modifiche necessarie nel layout familiare basato su modulo cartaceo del modulo di input.</p> <br/>

1. **Alcune correzioni vengono ripetute nei diversi moduli. Il servizio può identificare e correggere tutti questi casi nelle conversioni future?**

   Il servizio consiste nella formazione coerente su moduli e pattern. Impara nuovi schemi su base giornaliera. Deve ancora avviare l&#39;applicazione automatica delle correzioni ripetute nei moduli. Controlla i moduli prerelease per verificare la disponibilità di tale funzionalità. <br/><br/>

   È possibile utilizzare un meta-modello per mappare gli oggetti modulo al componente modulo adattivo di propria scelta e preconfigurare convalide, regole, pattern di dati, testo della guida e proprietà di accessibilità per i componenti. Tutte le proprietà specificate vengono applicate durante la conversione. È possibile utilizzare il meta-modello per applicare proprietà comuni ai campi. Può essere utile per ridurre alcuni problemi ripetuti nei diversi moduli.<br/><br/>

1. **Quali sono le opzioni per i moduli con dati sensibili come informazioni personali (PII)?**
Il servizio supporta solo moduli vuoti o non compilati. Non caricare moduli compilati o moduli con informazioni personali (PII). Inoltre, rimuovere i dati precompilati e le informazioni PII con etichetta bianca, riservate e proprietarie nei moduli di origine. <br/>

1. **Dove devono essere posizionati l&#39;intestazione e i piè di pagina?**
   <p>Posizionare l'intestazione e il piè di pagina in un modello di modulo adattivo. Se il modulo PDF di origine ha intestazione e piè di pagina, durante la conversione il servizio rileva e sostituisce l'intestazione e il piè di pagina rilevati con l'intestazione e il piè di pagina disponibili nel modello di modulo adattivo. Se nel modulo adattivo sono presenti intestazioni o piè di pagina aggiuntivi, è possibile utilizzare l’editor <a href="review-correct-ui-edited.md">Revisione e Correzione</a> per correggere o rimuovere tale intestazione o piè di pagina.</p> <br />

1. **Quanto tempo risparmierà il servizio rispetto al processo manuale di pianificazione, creazione di risorse (temi, modelli), creazione e pubblicazione di un modulo adattivo?**
   <p>Il tempo dipende dalle dimensioni e dalla complessità dei moduli di input e dal numero di richieste. Il servizio intende ridurre notevolmente il tempo necessario alla conversione dei moduli PDF in moduli adattivi con un ritmo molto più rapido rispetto al processo manuale di conversione dei moduli. </p> <br />

1. **Cosa fare se si verifica un errore relativo alle librerie RSA? Il messaggio di errore è simile a quello riportato di seguito:** <br/>
   `*ERROR* [0:0:0:0:0:0:0:1 [1565757652491] POST /content/dam/formsanddocuments/demo004.affBatchProcessor.html HTTP/1.1] org.apache.sling.engine.impl.SlingRequestProcessorImpl service: Uncaught Throwable java.lang.NoClassDefFoundError: Could not initialize class com.rsa.cryptoj.o.dl at com.rsa.jsafe.JSAFE_SecureRandom.getInstance(Unknown Source) at com.adobe.internal.pdfm.util.Util.appendRandomNumberToPrefix(Util.java: 169) [com.adobe.aemfd.adobe-aemfd-assembler:6.0.34] at com.adobe.internal.pdfm.logging.JobLog.&amp;lt;init&amp;gt;(JobLog.java:126) [com.adobe.aemfd.adobe-aemfd-assembler:6.0.34]` <br>L&#39;errore di cui sopra si verifica quando la delega di avvio non è configurata per le librerie RSA/BouncyCastle. Per risolvere il problema, eseguite i seguenti passaggi:
   <p> </p>

   1. Arrestate l’istanza AEM. Passate alla `[AEM installation directory]\crx-quickstart\conf\` cartella. Aprite il file sling.properties per la modifica. Se utilizzate `[AEM installation directory]\crx-quickstart\bin\start.bat` per avviare un’istanza di AEM, modificate le proprietà sling.properties che si trovano in `[AEM_root]\crx-quickstart\`.
   1. Aggiungete le seguenti proprietà al file sling.properties:<br/> `sling.bootdelegation.class.com.rsa.jsafe.provider.JsafeJCE=com.rsa.*`<br />  `sling.bootdelegation.class.org.bouncycastle.jce.provider.BouncyCastleProvider=org.bouncycastle.*`<br /> `sling.bootdelegation.xerces=org.apache.xerces.*`
   1. Salvate e chiudete il file. <br/>
   1. Avviate l’istanza AEM.<br/>
   <br/>

1. **Come cambiare automaticamente la cascata del testo del modulo adattivo?**
   <p>È possibile utilizzare l'adattatore per i temi o l'editor di stili per cambiare la cascata di un campo di un modulo adattivo. Ad esempio, è possibile aprire l'editor di temi e impostare il valore della proprietà Case di tutto il testo del modulo su maiuscolo, minuscolo o camelCase. Potete anche utilizzare l'opzione Override CSS nell'editor di temi per creare diversi tipi di stili.</p>