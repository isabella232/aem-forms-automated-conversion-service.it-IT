---
title: Problemi noti
seo-title: Problemi noti
description: problemi noti e limitazioni del servizio di conversione moduli automatizzati
seo-description: Prima di iniziare a utilizzare il servizio di conversione moduli automatizzati di AEM Forms, è necessario conoscere i problemi e le limitazioni noti del servizio
uuid: b1dc661b-ccd3-457f-acbb-4bd25db86e1e
topic-tags: introduction
discoiquuid: 9cd2363c-47a0-46e9-98cd-1fe088b9cd6e
translation-type: tm+mt
source-git-commit: 2fcceb45d9be4297fcd923f5a17c7b593294e855

---

# Problemi noti e limitazioni {#known-issues-limitations}

Prima di iniziare a utilizzare il servizio di conversione moduli automatizzati di AEM Forms, controlla i seguenti problemi noti e limitazioni:

## Problemi noti {#known-issues}

* La cartella contenente i moduli per la conversione non deve contenere più di 15 moduli e 50 pagine in totale. La dimensione della cartella di origine non deve superare i 10 MB. Non create sottocartelle nella cartella di origine.
* Alcuni oggetti modulo sono facilmente visibili all&#39;occhio umano ma sono [difficili da identificare per il servizio](styles-and-pattern-considerations-and-best-practices.md). Utilizzare l&#39;editor [Review e l&#39;editor](review-correct-ui-edited.md) corretto per identificare e convertire tali oggetti modulo.
* Rivedi e correggi editor:

   * Non dispone di azioni di annullamento. Il pulsante Salva salva le modifiche in modo permanente.
   * Non supporta pannelli ripetibili per i moduli basati su XFA.
   * Se modificate un elenco in una tabella utilizzando l&#39;editor Revisione e Correzione, la larghezza della riga non viene regolata automaticamente e il testo potrebbe riversarsi nella riga successiva della tabella.
   * La **[!UICONTROL Auto-detect multi-column layout from input forms]** funzione non funziona con l&#39;editor di revisione e correzione e con i frammenti del modulo.

* Per i moduli basati su XFA:
   * L&#39;estrazione di frammenti da un modulo basato su XFA non è supportata.
   * Gli script XFA non sono supportati. Ad esempio, script per la generazione automatica di valori per un componente a discesa.
   * Il metamodello non funziona per il gruppo di scelta
   * L&#39;opzione Gruppi di scelta con un singolo carattere non è identificata
   * Quando il documento di origine è un XFA dinamico (.XDP) e [definisce il comportamento delle proprietà XFA in un modulo](https://helpx.adobe.com/experience-manager/6-5/forms/using/xfa-api-supported-in-adaptive-form.html#supportedxfaelementsandtheirmappinginadaptiveformsbr)adattivo, la proprietà presence del documento di origine non viene rispettata. Ad esempio, un campo nel documento di origine è contrassegnato come nascosto e uno script rende il campo visibile, quindi resta visibile nel modulo di output adattivo.

* Quando si utilizza l&#39;opzione **Usa AcroForm come documento di registrazione (DoR) per i moduli** adattivi generati, tenere presente quanto segue:

<table>
    <tr>
        <td>Binding e dati vengono persi per i campi di testo composti. I campi di testo composito sono composti da più caselle di testo allineate tra loro. Ad esempio, in un AcroForm, un numero di carta di credito è suddiviso in più caselle di testo e ciascuna casella di testo ha un binding separato. Quando AcroForm viene convertito in modulo adattivo, il modulo adattivo convertito ha un singolo binding per tutte le caselle di testo. Come soluzione alternativa, prima di convertire un AcroForm in un modulo adattivo, modificare il modulo AcroForm per utilizzare una sola casella di testo per accettare i numeri di carta di credito.</td>
        <td><img  src="assets/creditCard_Composite.png"/>                                                            </td>
    </tr>
    <tr>
        <td>Binding e dati vengono persi per i campi data compositi. Un campo data composito è composto da tre campi diversi. Ad esempio, un campo data di nascita in un AcroForm è suddiviso in tre campi separati. Il modulo adattivo fornisce un componente del selettore data out-of-the-box. Per utilizzare il componente selettore data del modulo adattivo mantenendo il binding del modulo AcroForm, prima di convertire un modulo AcroForm in modulo adattivo modificare il modulo AcroForm in modo da utilizzare un campo data singolo.</td>
        <td><img  src="assets/CompositeDateField.png"/></td>
    </tr>
    <tr>
        <td>Se le dimensioni delle caselle di controllo sono maggiori del testo associato, le caselle di controllo non vengono rilevate e il binding nel modulo Acrobat viene perso. Modificare il modulo Acro per ridurre le dimensioni delle caselle di controllo rispetto al testo associato.</td>
        <td><img  src="assets/large-text-box.png"/><br/><img  src="assets/small-text-box.png"/></td>
    </tr>
    <tr>
        <td>Se i campi di input non si allineano al campo di testo corrispondente, il campo di input non viene rilevato.  </td>
        <td><img  src="assets/non-alingned-fields.png"/></td>
    </tr>
    <tr >
        <td>Il servizio converte tutte le caselle di controllo di un AcroForm in gruppi di scelta separati. Vengono creati gruppi di scelta separati per mantenere i binding con AcroForm. Non unire gruppi di scelta nel modulo adattivo. Porterà alla perdita dei binding. Se si uniscono i gruppi di scelta, convertire di nuovo il modulo per recuperare i binding persi. </td>
        <td></td>
    </tr>
    <tr >
        <td>I bordi di alcune tabelle vengono estesi oltre la pagina nel documento record generato automaticamente (DoR). </td>
        <td></td>
    </tr>
</table>

## Limiti {#limitations}

* I moduli PDF con layout dinamico complesso, i campi con struttura tratteggiata, campi compilati o campi colorati non sono supportati.
* Le immagini e il testo all’interno delle immagini non sono identificati. Aggiungere manualmente le immagini ai moduli convertiti.
* I documenti XDP per immagini non sono supportati.
* I moduli PDF di dimensioni superiori a 15 pagine non sono supportati.
* I documenti crittografati, protetti da password e protetti non vengono convertiti. Rimuovere la cifratura o le password prima di eseguire la conversione.
* Le tabelle complesse come tabelle senza bordi, tabelle nidificate, tabelle con righe colorate e tabelle con valori segnaposto non sono supportate. Dopo la conversione, utilizzare l&#39;editor di moduli adattivi per aggiungere o modificare tabelle complesse. Sono supportate solo tabelle semplici, con campi vuoti, intestazioni corrette e bordi trasparenti.
* Il servizio converte solo moduli in lingua inglese in moduli adattivi. È possibile tradurre i moduli adattivi convertiti in un&#39;altra lingua utilizzando il flusso di lavoro [di traduzione di](https://helpx.adobe.com/experience-manager/6-5/forms/using/using-aem-translation-workflow-to-localize-adaptive-forms.html)AEM.
* AEM 6.4 Forms non supporta il rilevamento automatico del layout a più colonne dei moduli di input.

