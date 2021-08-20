---
title: 'Procedure consigliate e considerazioni '
seo-title: 'Procedure consigliate e considerazioni '
description: Best practice e considerazioni per il servizio Automated forms conversion
seo-description: Elenco di stili e modelli nei PDF forms di origine che il servizio di Automated forms conversion trova difficili da identificare
uuid: e24773a2-be14-4184-a168-48aa976d459a
topic-tags: introduction
discoiquuid: 79f2026e-73a5-4bd1-b041-d1399b4ad23e
exl-id: 9ada091a-e7c6-40e9-8196-c568f598fc2a
source-git-commit: 65b0d6f6568ce7915b1a8bd85981bead967d869c
workflow-type: tm+mt
source-wordcount: '1267'
ht-degree: 3%

---

# Best practice e pattern complessi noti {#Best-practices-and-considerations2}

Questo documento fornisce linee guida e consigli di cui possono trarre vantaggio gli amministratori, gli autori e gli sviluppatori di moduli quando lavorano con [!DNL Automated Forms Conversion service]. Descrive le best practice, dalla preparazione dei moduli di origine alla correzione di pattern complessi che richiedono uno sforzo aggiuntivo per la conversione automatica. Queste best practice contribuiscono collettivamente alle prestazioni e all&#39;output complessivi del [!DNL Automated Forms Conversion service].

## Best practice

Il servizio di conversione converte i PDF forms disponibili nell’istanza AEM [!DNL Forms] in moduli adattivi. Le best practice elencate di seguito consentono di migliorare la velocità e la precisione di conversione. Inoltre, queste best practice consentono di risparmiare tempo sulle attività dopo la conversione.

### Prima di caricare la sorgente

Puoi caricare tutti i PDF forms contemporaneamente o in modo graduale, a seconda delle necessità. Prima di caricare i moduli, considera quanto segue:

* Mantenere il numero di moduli in una cartella inferiore a 15 e mantenere il numero totale di pagine in una cartella inferiore a 50.
* Mantenere le dimensioni della cartella inferiori a 10 MB. Non salvare i moduli in sottocartelle.
* Mantenere il numero di pagine in un modulo inferiore a 15.
* Organizzare i documenti di origine in un batch di 8-15 documenti. Mantieni i moduli di origine con i frammenti di modulo adattivi comuni in un unico batch.
* Non caricare i moduli protetti. Il servizio non converte i moduli protetti da password e protetti.
* Non caricare i [Portfoli PDF](https://helpx.adobe.com/it/acrobat/using/overview-pdf-portfolios.html). Il servizio non converte un Portfolio PDF in un modulo adattivo.
* Non caricare moduli digitalizzati, compilati e in lingue diverse da inglese, francese, tedesco e spagnolo. Tali moduli non sono supportati.
* Non caricare moduli di origine con spazi nel nome file. Rimuovi lo spazio dal nome del file prima di caricare i moduli.

Quando si utilizza un modulo XDP per la conversione, eseguire i seguenti passaggi prima di caricare i moduli XPD di origine:

* Analizzare il modulo XDP e risolvere i problemi visivi. Assicurarsi che il documento di origine utilizzi i controlli e le strutture previsti. Ad esempio, nel modulo di origine potrebbero essere presenti caselle di controllo invece dei pulsanti di scelta per una singola selezione. Per creare un modulo adattivo con i componenti desiderati, è necessario modificare le caselle di controllo in pulsanti di scelta.
* [Aggiungi i binding al ](http://www.adobe.com/go/learn_aemforms_designer_65) modulo XDP prima di avviare la conversione. Quando nel modulo XDP di origine sono disponibili binding, il servizio applica automaticamente i binding ai corrispondenti campi del modulo adattivo durante la conversione. Consente di risparmiare il tempo necessario per applicare manualmente i binding.
* [Aggiungi ](https://helpx.adobe.com/sign/using/text-tag.html) tag Adobe Sign al file XDP. Il servizio converte automaticamente i tag Adobe Sign nei corrispondenti campi del modulo adattivo. Adaptive Forms supporta un numero limitato di campi Adobe Sign. Per l&#39;elenco completo dei campi supportati, consulta la documentazione [Utilizzo di Adobe Sign in un modulo adattivo](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/working-with-adobe-sign.html?lang=en) .
* Se possibile, converte tabelle complesse in documenti XDP in tabelle semplici. Una tabella con campi modulo in celle di tabella, celle con dimensioni non uniformi, celle con estensione per riga o colonna, celle unite, bordi parziali o senza bordo visibile è considerata una tabella complessa. Una tabella con uno qualsiasi dei suddetti elementi è considerata una tabella complessa.
<!-- * Use sub-forms in XDP documents to create panels in adaptive forms. Service converts each sub-form to one or more adaptive form panels during conversion. -->

### Prima di avviare la conversione

* Creare modelli di modulo adattivi. I modelli consentono di specificare una struttura uniforme per i moduli dell’organizzazione o del reparto.
* Specifica l’intestazione e il piè di pagina nei modelli di modulo adattivo. Il servizio ignora l’intestazione e il piè di pagina dei documenti di origine e utilizza il piè di pagina dell’intestazione specificato nel modello di modulo adattivo.
* Crea temi per i moduli adattivi. I temi aiutano a fornire un aspetto uniforme alle forme dell&#39;organizzazione o del reparto.
* Configurare Form Data Model per il salvataggio e il recupero da un’origine dati. Creare e configurare servizi di lettura e scrittura per il modello dati del modulo.
* Crea frammenti di modulo adattivi e configura il servizio per l’utilizzo dei frammenti di modulo adattivi.
* Preparare modelli di flusso di lavoro comuni per i moduli che richiedono l’automazione dei processi aziendali.
* Configura Adobe Analytics, se necessario


## Conoscere pattern complessi

AEM [!DNL Forms Automated Conversion service] utilizza algoritmi di intelligenza artificiale e machine learning per comprendere il layout e i campi del modulo di origine. Ogni servizio di apprendimento automatico impara continuamente dai dati sorgente e produce un output migliore con ogni abbandono. Questi servizi imparano dall&#39;esperienza come gli umani.

[!DNL Automated Forms Conversion service] viene addestrato su un ampio insieme di moduli. Identifica facilmente i campi di un modulo sorgente e produce moduli adattivi. Tuttavia, ci sono alcuni campi e stili in PDF forms che sono facilmente visibili all&#39;occhio umano ma difficile da capire per il servizio. Il servizio può assegnare ad alcuni campi o stili tipi di campo o pannelli diversi da quelli applicabili. Di seguito sono elencati tutti i pattern di campo e stile.

Il servizio inizierebbe a identificare e assegnare campi o pannelli corretti a questi pattern in quanto continua a imparare dai dati di origine. Per il momento, è possibile utilizzare l&#39;editor [Rivedi e correggi](review-correct-ui-edited.md) per risolvere tali problemi. Prima di iniziare a risolvere i problemi o a leggere di più, impara a conoscere [i componenti per moduli adattivi](https://helpx.adobe.com/experience-manager/6-5/forms/using/introduction-forms-authoring.html).

### Pattern generali {#general}

| Pattern | Esempio |
|--- |--- |
| **** <br>PatternService non converte i PDF forms riempiti in un modulo adattivo. <br><br>**** <br>RisoluzioneUtilizza moduli adattivi vuoti. | ![Modulo pieno](assets/best-practice-filled-forms.png) |
| **** <br>È possibile che PatternService non riesca a riconoscere testo e campi in un modulo denso. <br><br>**** <br> RisoluzioneAumenta la larghezza tra il testo e i campi di un modulo denso prima di avviare la conversione. |  |
| **** <br>PatternService non supporta i moduli digitalizzati. <br><br>**** <br>RisoluzioneNon utilizzare moduli digitalizzati. | ![Modulo analizzato](assets/scanned-forms.png) |
| **** <br>PatternService non estrae immagini e testo all’interno delle immagini. <br><br>**** <br> RisoluzioneAggiunta manuale di immagini o testo ai moduli convertiti. | ![Immagine con modulo di testo](assets/best-practice-image-with-text.png) |
| **** <br>Le tabelle con bordi e bordi puntati o non chiari non vengono convertite. <br><br>**** <br>RisoluzioneUtilizzare tabelle con bordi e bordi chiari ed espliciti. supportato. | ![Modulo tabella non chiaro](assets/best-practice-table-dotted-non-clear.png) |
| **** <br> I moduli adattivi non supportano il testo verticale preconfigurato. Pertanto, il servizio non converte il testo verticale nel testo Forms adattivo corrispondente. <br><br>**** <br> RisoluzioneUtilizza l’editor di moduli adattivi per aggiungere testo verticale, se necessario. | ![Modulo tabella non chiaro](assets/vertical-text.png) |



### Gruppo di scelta  {#choice-group}

| Pattern | Risoluzione |
|--- |--- |
| **** <br> Le opzioni del gruppo PatternChoice con forme diverse da box o cerchio non vengono convertite nei corrispondenti componenti del modulo adattivo. <br><br>**** <br> RisoluzioneModifica le forme delle opzioni di scelta per creare un cerchio o una casella oppure utilizza l&#39;editor Rivedi e correggi per identificare le forme. | ![Campi selezionati  ](assets/best-practice-choice-group-options.png) |

### Campi modulo {#form-fields}

| Pattern | Risoluzione |
|--- |--- |
| **** <br> PatternService non identifica i campi senza bordi chiari. <br><br>**** <br> RisoluzioneUtilizza l’editor di revisione e correzione per identificare tali campi. | ![campi con limiti non chiari](assets/best-practice-fields-without-clear-borders.png) |
| **** <br> È possibile che PatternService non identifichi alcuni campi modulo del gruppo di scelta con didascalie nella parte inferiore o destra di un modulo. <br><br>**** <br> RisoluzioneUtilizza l&#39;editor di revisione e correzione per identificare tali campi | ![Campi selezionati](assets/best-practice-caption-bottom-right.png) |
| **** <br> PatternService unisce o assegna un tipo errato ad alcuni campi del modulo posizionati molto vicini tra loro o privi di bordi chiari. <br><br>**** <br> RisoluzioneUtilizza l’editor di revisione e correzione per identificare tali campi. | ![Campi selezionati](assets/best-practice-placed-very-near.png) |
| **** <br> È possibile che PatternService non riesca a riconoscere i campi con didascalie molto lontane o una linea tratteggiata tra la didascalia e il campo di input. <br><br>**** <br> RisoluzioneUtilizza i campi dei moduli con limiti chiari oppure utilizza l’editor di revisione e correzione per risolvere tali problemi. | ![Campi lontani o linee tratteggiate tra i campi della didascalia](assets/best-practice-far-away-captions-or-a-dotted-line.png) |

### Elenchi {#lists}

| Pattern | Risoluzione |
|--- |--- |
| **** <br>Gli elenchi di pattern contenenti campi modulo vengono uniti o non vengono convertiti nei corrispondenti componenti del modulo adattivo  <br><br>**** <br>RisoluzioneUtilizzare i campi dei moduli con limiti chiari o utilizzare l’editor Rivedi e correggi per risolvere tali problemi. | ![elenchi contenenti gruppi di scelta](assets/best-practice-lists-containing-form-fields.png) |
| **** <br>PatternService può lasciare alcuni elenchi nidificati non identificati  <br><br>**** <br> ResolutionUtilizza l’editor di revisione e correzione per risolvere tali problemi. | ![elenchi contenenti gruppi di scelta](assets/best-practice-nested-lists.png) |
| **** <br> PatternService unisce alcuni elenchi contenenti gruppi di scelta tra loro  <br><br>**** <br> ResolutionUtilizza l’editor di revisione e correzione per risolvere tali problemi. | ![elenchi contenenti gruppi di scelta](assets/best-practice-check-box-in-table-cells.png) |

<!--
Comment Type: draft

<h3>Choice groups</h3>
-->

<!--
Comment Type: draft

<ul>
<li>Lists with form fields, nested lists, and nested choice groups are not supported.</li>
<li>Form fields with captions at bottom or right are not supported.</li>
<li>Form fields without borders are not supported.</li>
<li>Hidden form fields are not supported.</li>
<li>Button in PDF forms are not converted to adaptive form buttons.<br /> </li>
<li>Tables with clear explicit boundaries and borders are supported.</li>
<li>Fields with far away captions are not supported.<br /> </li>
<li>Choice groups with only box or circle shaped selectors are supported. </li>
</ul>
-->
