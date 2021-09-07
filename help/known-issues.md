---
title: Problemi noti
seo-title: Known Issues
description: problemi e limitazioni noti per Automated forms conversion Service
seo-description: Before you begin using AEM Forms Automated Forms Conversion service, learn about the known issues and limitations of the service
uuid: b1dc661b-ccd3-457f-acbb-4bd25db86e1e
topic-tags: introduction
discoiquuid: 9cd2363c-47a0-46e9-98cd-1fe088b9cd6e
exl-id: 35f59e02-e38e-473a-94c8-123e0a85ac8e
source-git-commit: 47261710e6616c27c210ac53bffcc2387a06ea7a
workflow-type: tm+mt
source-wordcount: '794'
ht-degree: 1%

---

# Problemi noti e limitazioni {#known-issues-limitations}

Prima di iniziare a utilizzare il servizio AEM Forms Automated forms conversion, controlla i seguenti problemi e limitazioni noti:

## Problemi noti {#known-issues}

* La cartella contenente i moduli da convertire non deve contenere più di 15 moduli e 50 pagine in totale. La dimensione della cartella di origine non deve superare i 10 MB. Non creare sottocartelle nella cartella di origine.
* Alcuni oggetti modulo sono facilmente visibili all&#39;occhio umano ma sono [difficili da identificare per il servizio](styles-and-pattern-considerations-and-best-practices.md). Utilizzare [Rivedi e correggi l&#39;editor](review-correct-ui-edited.md) per identificare e convertire tali oggetti modulo.
* Modifica e correzione:

   * Non dispone di un&#39;azione di annullamento. Il pulsante Salva consente di salvare le modifiche in modo permanente.
   * Non supporta pannelli ripetibili per moduli basati su XFA.
   * Se si modifica un elenco in una tabella utilizzando l’editor Revisione e correzione, la larghezza della riga non viene regolata automaticamente e il testo potrebbe riversarsi nella riga successiva della tabella.
   * La funzione **[!UICONTROL Auto-detect multi-column layout from input forms]** non funziona con l’editor di revisione e correzione e i frammenti di modulo.
   * La firma digitale creata con l’editor di revisione e correzione non viene caricata per i moduli adattivi pubblicati.


* Per i moduli basati su XFA:
   * L’estrazione di frammenti da un modulo basato su XFA non è supportata.
   * Gli script XFA non sono supportati. Ad esempio, script per la generazione automatica di valori per un componente a discesa.
   * Il metamodello non funziona per il gruppo di scelta
   * L&#39;opzione Gruppi di scelta con un singolo carattere non è identificata
   * Quando il documento di origine è un file XFA dinamico (.XDP) e [definisce il comportamento delle proprietà XFA in un modulo adattivo](https://helpx.adobe.com/experience-manager/6-5/forms/using/xfa-api-supported-in-adaptive-form.html#supportedxfaelementsandtheirmappinginadaptiveformsbr), la proprietà presence del documento di origine non viene rispettata. Ad esempio, un campo nel documento di origine è contrassegnato come nascosto e uno script rende il campo visibile, quindi il campo rimane visibile nel modulo adattivo di output.

* Quando utilizzi l’opzione **Utilizza AcroForm come documento di record (DoR) per i moduli adattivi generati**, considera quanto segue:

<table>
    <tr>
        <td>Per i campi di testo composito, il binding e i dati vengono persi. I campi di testo composito sono composti da più caselle di testo allineate tra loro. Ad esempio, in un AcroForm, il numero di una carta di credito è suddiviso in più caselle di testo e ogni casella di testo ha un binding separato. Quando AcroForm viene convertito in modulo adattivo, il modulo adattivo convertito dispone di un unico binding per tutte le caselle di testo. Come soluzione alternativa, prima di convertire un AcroForm in modulo adattivo, modificare l'AcroForm per utilizzare una casella di testo singola per accettare i numeri di carta di credito.</td>
        <td><img  src="assets/creditCard_Composite.png"/>                                                            </td>
    </tr>
    <tr>
        <td>I campi data compositi perdono binding e dati. Un campo data composito è composto da tre campi diversi. Ad esempio, un campo data di nascita in un AcroForm viene suddiviso in tre campi separati. Il modulo adattivo fornisce un componente del selettore data predefinito. Per utilizzare il componente del selettore data del modulo adattivo conservando il binding dell’AcroForm, prima di convertire un AcroForm in un modulo adattivo, modificare l’AcroForm per utilizzare un singolo campo data.</td>
        <td><img  src="assets/CompositeDateField.png"/></td>
    </tr>
    <tr>
        <td>Se le dimensioni delle caselle di controllo sono maggiori del testo di accompagnamento, le caselle di controllo non vengono rilevate e il binding nell’AcroForm viene perso. Modificare l'AcroForm in modo che le dimensioni delle caselle di controllo siano più piccole rispetto al testo di accompagnamento.</td>
        <td><img  src="assets/large-text-box.png"/><br/><img  src="assets/small-text-box.png"/></td>
    </tr>
    <tr>
        <td>Se i campi di input non vengono allineati al campo di testo corrispondente, il campo di input non viene rilevato.  </td>
        <td><img  src="assets/non-alingned-fields.png"/></td>
    </tr>
    <tr >
        <td>Il servizio converte tutte le caselle di controllo di un AcroForm in gruppi di scelta separati. Vengono creati gruppi di scelta separati per mantenere i binding con AcroForm. Non unire gruppi di scelta nel modulo adattivo. Porterà alla perdita dei binding. Se si uniscono i gruppi di scelta, convertire di nuovo il modulo per recuperare i binding persi. </td>
        <td></td>
    </tr>
    <tr >
        <td>I limiti di alcune tabelle vengono estesi fuori dalla pagina nel documento di record generato automaticamente (DoR). </td>
        <td></td>
    </tr>
</table>

## Limitazioni  {#limitations}

* I PDF forms con layout dinamico complesso, i campi con struttura tratteggiata o i campi compilati non sono supportati.
* Le immagini e il testo all’interno delle immagini non sono identificati. Aggiungere manualmente immagini ai moduli convertiti.
* I documenti XDP per immagini non sono supportati.
* I PDF forms più grandi di 15 pagine non sono supportati.
* I documenti crittografati, protetti da password e protetti non vengono convertiti. Rimuovi la crittografia o le password prima di eseguire la conversione.
* Tabelle complesse come tabelle senza bordi, tabelle nidificate e tabelle con valori segnaposto non sono supportate. Utilizza l’editor di moduli adattivi per aggiungere o modificare tabelle complesse dopo la conversione. Sono supportate solo le tabelle semplici, con campi vuoti, intestazioni appropriate e bordi chiari.
* Il servizio converte solo i moduli in lingua inglese, francese, tedesca, spagnola, italiana e portoghese in moduli adattivi. È possibile tradurre i moduli adattivi convertiti in un&#39;altra lingua utilizzando [AEM flusso di lavoro di traduzione](https://helpx.adobe.com/it/experience-manager/6-5/forms/using/using-aem-translation-workflow-to-localize-adaptive-forms.html).
* AEM 6.4 Forms non supporta il rilevamento automatico del layout a più colonne dei moduli di input.
* Le informazioni codificate tramite colori nel modulo PDF di origine non vengono riportate nel modulo adattivo.
* I colori del modulo PDF di origine non vengono trasferiti ai temi dei moduli adattivi.
* I PDF forms colorati vengono trattati come moduli in scala di grigi e i campi vengono rilevati di conseguenza.
