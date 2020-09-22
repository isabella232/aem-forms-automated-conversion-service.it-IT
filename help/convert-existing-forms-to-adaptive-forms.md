---
title: 'Conversione di moduli PDF in moduli adattivi '
seo-title: 'Conversione di moduli PDF in moduli adattivi '
description: Eseguire il servizio di conversione Forms automatizzata per convertire i PDF forms in moduli adattivi
seo-description: Eseguire il servizio di conversione Forms automatizzata per convertire i PDF forms in moduli adattivi
uuid: 49fcd5c0-0e72-496d-9831-00f79d582f57
contentOwner: khsingh
topic-tags: forms
discoiquuid: 9358219c-6079-4552-92b9-b427a23811af
translation-type: tm+mt
source-git-commit: 14e6d1fba9f27fde4fe24de83cb00c9847ea4e90
workflow-type: tm+mt
source-wordcount: '1579'
ht-degree: 7%

---


# Conversione di moduli PDF in moduli adattivi {#convert-print-forms-to-adaptive-forms}

 servizio di conversione Forms automatizzata di AEM Forms, basato su  Adobe Sensei, converte automaticamente i PDF forms in moduli adattivi reattivi e compatibili con il dispositivo. Sia che si utilizzino PDF forms non interattivi, PDF forms basati su Acrobat Forms o XFA, il servizio di conversione Forms automatizzata può facilmente convertire questi moduli in moduli adattivi. Per informazioni su funzionalità, flusso di lavoro di conversione e informazioni di registrazione, consulta Servizio di conversione [Forms](introduction.md) automatizzato.

## Prerequisiti {#pre-requisites}

* [**Configurare il servizio di conversione**](configure-service.md)

* **Preparare i[modelli](https://helpx.adobe.com/experience-manager/6-5/forms/using/template-editor.html)da applicare ai moduli convertiti:** L&#39;utilizzo di un modello consente di applicare un marchio coerente a tutti i moduli adattivi. Inoltre, il servizio di conversione Forms automatizzata non estrae né utilizza l&#39;intestazione e il piè di pagina dei documenti PDF di origine. È possibile utilizzare i modelli di modulo adattivo per specificare intestazione e piè di pagina. L&#39;intestazione e il piè di pagina specificati nel modello vengono applicati al modulo adattivo durante la conversione. Quando create una cartella per i modelli, selezionate l’ **[!UICONTROL Browse configurations]** opzione per tutti.

* **Preparare i[temi](https://helpx.adobe.com/experience-manager/6-5/forms/using/themes.html)da applicare ai moduli convertiti:** L&#39;utilizzo di un tema consente di applicare uno stile coerente a tutti i moduli adattivi dell&#39;organizzazione.

* **Aggiungere  tag di testo Adobe Sign ai documenti PDF di origine:** Quando nel modulo PDF di origine sono presenti [tag](https://helpx.adobe.com/sign/using/text-tag.html)di testo Adobe Sign, questi tag vengono automaticamente convertiti nei campi modulo adattivi corrispondenti e i dettagli del firmatario vengono automaticamente compilati. La funzione è disponibile solo per i moduli Acrobat e i moduli adattivi supportano un numero limitato di campi  Adobe Sign.


   Per un elenco completo dei tag supportati, aprire un modulo nell&#39;editor di moduli adattivi e aggiungere un blocco Adobe Sign . Usare  blocco Adobe Sign per trovare tutti  campi Adobe Sign supportati. Fornisce un menu a discesa per selezionare tutti i campi supportati.

## Avvio del processo di conversione {#start-the-conversion-process}

Dopo aver collegato l&#39;istanza AEM con  AEM Forms Conversion Service, è possibile convertire i PDF forms in moduli adattivi. Per convertire i moduli, effettuare i seguenti passaggi nell&#39;elenco:

* [Caricare PDF forms nel server AEM Forms](convert-existing-forms-to-adaptive-forms.md#upload-pdf-forms-to-your-aem-forms-server)
* [Eseguire la conversione](convert-existing-forms-to-adaptive-forms.md#run-the-conversion)
* [Revisione e correzione dei moduli convertiti](review-correct-ui-edited.md)

### Caricare PDF forms nel server AEM Forms  {#upload-pdf-forms-to-your-aem-forms-server}

Il servizio di conversione converte i PDF forms disponibili nell&#39;istanza AEM Forms  in moduli adattivi. Potete caricare tutti i PDF forms contemporaneamente o in modo graduale, a seconda delle necessità. Prima di caricare i moduli, considera quanto segue:

* Mantenere il numero di moduli in una cartella inferiore a 15 e mantenere il numero totale di pagine in una cartella inferiore a 50.
* Le dimensioni della cartella devono essere inferiori a 10 MB. Non tenere i moduli in una sottocartella.
* Tenere il numero di pagine in un modulo inferiore a 15.
* Non caricare i moduli protetti. Il servizio non converte i moduli protetti da password e protetti.
* Non caricare moduli di origine con spazi nel nome file. Rimuovere lo spazio dal nome del file prima di caricare i moduli.
* Non caricare [portfolio PDF](https://helpx.adobe.com/it/acrobat/using/overview-pdf-portfolios.html). Il servizio non converte un Portfolio PDF in un modulo adattivo.
* Leggere le sezioni [Problemi](known-issues.md) noti e [Best practice e considerazioni](styles-and-pattern-considerations-and-best-practices.md) e apportare modifiche suggerite ai moduli.

Per caricare i moduli da convertire in una cartella dell&#39;istanza AEM Forms , effettuare le operazioni seguenti:

1. Effettuate l&#39;accesso all&#39;istanza AEM Forms .

1. Tap **[!UICONTROL Adobe Experience Manager]** ![](assets/adobeexperiencemanager.png) > **[!UICONTROL Navigation]** ![](assets/compass.png) > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**.
1. Toccare **[!UICONTROL Create]**> **[!UICONTROL Folder]**. Specificate **Titolo** e **Nome** della cartella. Toccare **[!UICONTROL Create]**. Viene creata una cartella.
1. Toccate per aprire la cartella appena creata.
1. Toccare **[!UICONTROL Create]**> **[!UICONTROL File Upload]**. Selezionate i moduli da caricare, fate clic **[!UICONTROL Open]** e fate clic su **[!UICONTROL Upload]**. I moduli vengono caricati.

### Eseguire la conversione {#run-the-conversion}

Dopo aver caricato i moduli e configurato il servizio, eseguire i seguenti passaggi per avviare la conversione:

1. Nell’istanza AEM Forms , toccate Finestra di dialogo **[!UICONTROL Adobe Experience Manager]** Impostazioni ![conversione >](assets/adobeexperiencemanager.png) **[!UICONTROL Navigation]** > ![](assets/compass.png) > **[!UICONTROL Forms]** **[!UICONTROL Forms & Documents]**.
1. Selezionare un modulo o la cartella contenente PDF forms (moduli da convertire) e toccare **[!UICONTROL Start Automated Conversion]**. Viene visualizzata **[!UICONTROL Conversion Settings]** la finestra di dialogo.

   ![Specificare le configurazioni](assets/conversion-settings-dialog.png)

1. Nella **[!UICONTROL Basic]** scheda della finestra di dialogo Impostazioni conversione:

   * **[!UICONTROL Select a cloud configuration]**. Quando selezionate una configurazione, vengono già specificati il modello e il tema predefiniti. Potete specificare un modello o un tema diverso, se necessario.
   * Specificare un percorso in cui salvare i moduli adattivi generati e lo schema corrispondente. È possibile utilizzare percorsi predefiniti o specificare percorsi personalizzati.
   * Utilizzare l&#39;opzione **Genera moduli adattivi senza binding** dei modelli dati per selezionare se si desidera generare un modulo adattivo con o senza binding dei modelli dati.
Se non si seleziona questa opzione, il servizio di conversione associa automaticamente i moduli adattivi a uno schema JSON e crea un binding di dati tra i campi disponibili nel modulo adattivo e nello schema JSON. Il **[!UICONTROL Save generated data model schema at]** campo visualizza il percorso predefinito per salvare lo schema JSON generato. È inoltre possibile personalizzare la posizione per salvare lo schema generato.
Se si seleziona questa opzione, il servizio di conversione genera un modulo adattivo senza binding del modello dati. Dopo la conversione, è possibile associare un modulo adattivo a un modello dati modulo, a uno schema XML o a uno schema JSON. Per ulteriori informazioni, vedere [Creazione di un modulo](https://helpx.adobe.com/experience-manager/6-5/forms/using/creating-adaptive-form.html)adattivo.

   <!--
   Comment Type: draft

   <note type="note">
   <p>The XDP or XFA-based PDF form is not used to generate the Document of Record. The conversion service auto-generates the Document of Record only if you enable the Tools &gt; Cloud Services &gt; Automated Forms Conversion Configuration &gt; <strong>&lt;Properties of selected configuration&gt; &gt;</strong> Advanced &gt; Generate Document of Record option.</p>
   <p> </p>
   </note>
   -->

1. Nella **[!UICONTROL Additional]** scheda della finestra di dialogo Impostazioni conversione,
   * Selezionare l&#39; **[!UICONTROL Extract fragment from adaptive forms]** opzione per consentire al servizio di conversione di identificare, estrarre e scaricare frammenti di modulo per i moduli convertiti. Quando si seleziona l&#39; **[!UICONTROL Extract fragment from adaptive forms]** opzione, è possibile specificare i percorsi in cui salvare i frammenti di modulo estratti e gli schemi di frammenti di modulo corrispondenti.
   * Specificare la posizione di **[!UICONTROL existing adaptive form fragments]**, se si dispone di alcuni frammenti di modulo adattivi basati su schemi JSON e basati su schemi meno adattativi esistenti e si prevede di utilizzare tali frammenti nei moduli adattivi generati automaticamente. Il servizio di conversione associa i frammenti di modulo JSON disponibili basati su schema e quelli meno adattivi con i PDF forms di input (solo PDF forms non interattivi), in presenza di una corrispondenza, il frammento di modulo adattivo corrispondente viene utilizzato nei moduli adattivi corrispondenti.

   >[!NOTE]
   >
   >
   > * Potete utilizzare solo **[!UICONTROL  Extract Fragment]** o **[!UICONTROL Use existing adaptive form fragments]** opzione alla volta. Non è possibile utilizzare entrambe le opzioni contemporaneamente.
   > * Potete utilizzare l&#39; **[!UICONTROL Use existing adaptive form fragments]** opzione solo con PDF forms non interattivi. Altri tipi di modulo non sono ancora supportati.
   > * Con Automated Conversion Service è possibile utilizzare solo frammenti o frammenti non associati associati a uno schema JSON. Non utilizzare frammenti XFA. I frammenti XFA non sono supportati.


   * Selezionare l&#39; **[!UICONTROL Auto-detect multi-column layout of input forms]** opzione per mantenere il layout del modulo di origine per schermi di grandi dimensioni come computer desktop e computer portatili. Questa opzione è utile per mantenere il layout a più colonne dei moduli di origine. Ad esempio, quando un PDF di origine ha un layout a due colonne, il servizio genera un modulo adattivo di output con un layout a due colonne per gli schermi grandi e un layout a una colonna singola per i dispositivi a schermo piccolo come i telefoni cellulari. La funzione presenta alcuni problemi noti con la struttura dello schema dell&#39;origine dati. Per informazioni dettagliate, consultate l&#39;articolo sui problemi [](known-issues.md) noti.
   * Per impostazione predefinita, il servizio crea un pannello di primo livello separato per ciascuna pagina di un modulo PDF. Now, you can use the **[!UICONTROL Auto-detect logical sections]** option to not create page level panels (page number-based panels) and create only logical panels. Questa opzione, inoltre, unisce alla sezione logica precedente i campi che non appartengono ad alcuna sezione e unisce in un’unica sezione logica i campi di una sezione logica suddivisi su due pagine adiacenti. Ad esempio, se alcuni campi di una sezione logica si trovano alla fine della pagina 1 e altri si trovano all’inizio della pagina 2, tutti questi campi sono raggruppati in una singola sezione logica.

      >[!NOTE]
      > Per utilizzare la **[!UICONTROL Auto-detect logical sections]** funzione è necessario disporre del connettore 1.1.38 o superiore.



1. Toccare **[!UICONTROL Start Conversion]**. La conversione è avviata. L&#39;avanzamento della conversione viene visualizzato nella cartella o nel modulo fino a quando non è in corso la conversione. Al termine della conversione, il messaggio viene sostituito da un altro messaggio di stato (Conversione, Conversione parziale o Conversione non riuscita). Una e-mail di stato viene inviata anche all&#39;indirizzo e-mail configurato al termine della conversione:

   * In caso di conversione riuscita, il modulo adattivo convertito e lo schema correlato vengono scaricati nel percorso specificato nella **[!UICONTROL Basic]** scheda della finestra di dialogo di conversione. I frammenti di modulo e lo schema corrispondente vengono scaricati solo se l&#39;opzione Estrai frammento è selezionata prima dell&#39;avvio della conversione.
   * In caso di conversione non riuscita, il **[!UICONTROL Conversion Failed]** messaggio viene visualizzato se tutti i moduli di input non riescono a essere convertiti o se solo alcuni di essi non riescono a convertire **[!UICONTROL Partially Failed]** viene visualizzato il messaggio. Un messaggio e-mail di stato viene inviato sull’indirizzo [e-mail](configure-service.md#configureemailnotification) configurato e viene registrato un errore nel file error.log.

   Se si sta convertendo un modulo PDF basato su XFA in un modulo adattivo, il servizio di conversione associa automaticamente il modulo PDF al modulo adattivo convertito come modello Documento di record. Dopo la conversione, è possibile aprire le proprietà del modulo adattivo per visualizzare il modello Documento di record nella **[!UICONTROL Document of Record Template Configuration]** sezione della **[!UICONTROL Form Model]** scheda. </br>

   Il servizio di conversione carica automaticamente il modulo PDF nel modulo adattivo convertito come modello del documento record solo se si abilita l&#39;opzione **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Automated Forms Conversion Configuration]** > **[!UICONTROL Properties of selected configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Generate Document of Record]** .

   <!--
   Comment Type: draft

   <note type="note">
   <p>By default, the adaptive form produces a JSON schema instead of XML schema on submission. JSON schema of a converted adaptive form is complaint with XML schema of an XFA-based form. You can use the <a href="https://sling.apache.org/apidocs/sling5/org/apache/sling/commons/json/xml/XML.html#toString">org.apache.sling.commons.json.xml API</a> to convert a JSON schema to XML schema. You can also use the following sample code for conversion:</p>
   <p><code class="code">import org.apache.sling.commons.json.JSONException;
   <discoiqbr /> import org.apache.sling.commons.json.JSONObject;
   <discoiqbr /> import org.apache.sling.commons.json.xml.XML;
   <discoiqbr />
   <discoiqbr /> public class ConversionUtils {
   <discoiqbr />
   <discoiqbr /> public static String jsonToXML(String jsonString) throws JSONException {
   <discoiqbr /> //https://sling.apache.org/apidocs/sling5/org/apache/sling/commons/json/xml/XML.html#toString(java.lang.Object)
   <discoiqbr /> //jar - http://maven.ibiblio.org/maven2/org/apache/sling/org.apache.sling.commons.json/2.0.18/
   <discoiqbr /> //Note: Need to extract boundData part before converting to XML
   <discoiqbr /> return XML.toString(new JSONObject(jsonString));
   <discoiqbr /> }
   <discoiqbr /> }</code><br /> </p>
   </note>
   -->

   >[!NOTE]
   >
   >Se il processo di conversione richiede più di 60 minuti e il modulo PDF non viene ancora convertito in un modulo adattivo, creare una cartella &#39;istanza AEM Forms, caricare il modulo PDF nella nuova cartella creata e riavviare la conversione.

## Review and correct the converted forms {#review-and-correct-the-converted-forms}

I moduli nel mondo reale hanno requisiti complessi per l&#39;acquisizione dei dati. Una volta completata la conversione automatizzata, i clienti possono verificare la qualità di conversione del modulo e apportare gli aggiornamenti necessari al modulo.  AEM Forms fornisce un editor [di revisione e corretto](review-correct-ui-edited.md) per apportare le modifiche necessarie. Consente di migliorare l&#39;identificazione automatizzata dei campi modulo e di convertire i campi identificati da un tipo all&#39;altro. Ad esempio, è possibile identificare il layout a due colonne di un modulo e modificare un campo identificato automaticamente come pulsante di scelta in più campi di scelta.
