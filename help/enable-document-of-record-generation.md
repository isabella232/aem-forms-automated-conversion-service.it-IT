---
title: Genera documento record durante la conversione
seo-title: Genera documento record durante la conversione
description: Percorsi consigliati per generare un DoR basato sul tipo di moduli di origine utilizzati per la conversione.
seo-description: Percorsi consigliati per generare un DoR basato sul tipo di moduli di origine utilizzati per la conversione.
page-status-flag: never-activated
uuid: 7f0f5bf3-21be-449a-b23e-5946a9fd7ed4
contentOwner: khsingh
discoiquuid: 75f6e6bc-7636-4b40-919c-8b20a6ccbb1f
translation-type: tm+mt
source-git-commit: 640d72d7961ef0c2393bf0ae6745d918e388a056

---


# Flussi di lavoro consigliati per abilitare la generazione di documenti di registrazione per i moduli adattivi {#recommended-workflows-dor-generation}

Il documento record (DoR) consente di registrare le informazioni fornite e inviate in un modulo adattivo in modo da potervi fare riferimento in un secondo momento.
Il DoR utilizza un modello di base per definire il layout. È possibile generare un DoR utilizzando un modello predefinito o associando qualsiasi altro modello al modulo adattivo.

![Documento di registrazione generato](assets/document_of_record.gif)

Per ulteriori informazioni sulla generazione di un DoR, vedere [Genera documento di record per i moduli](https://helpx.adobe.com/experience-manager/6-5/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.html)adattivi.

Il servizio [di conversione moduli](../help/introduction.md) automatizzati converte i seguenti moduli di origine in moduli adattivi:

* moduli PDF non interattivi
* Acro Forms
* Moduli PDF basati su XFA

In base al modulo di origine utilizzato per la conversione, è possibile generare un DoR utilizzando:

* un modello predefinito
* modulo di origine come modello - Se si seleziona questa opzione, il servizio di conversione associa automaticamente il modulo di origine al modulo adattivo convertito come modello DoR.
* associare qualsiasi altro modello al modulo adattivo convertito

Nella tabella seguente è illustrato un esempio di come il modello DoR utilizzato influisca sul layout del DoR generato:

<table> 
 <tbody>
 <tr>
  <td><p><strong>Modulo di origine</strong></p></td>
  <td><p><strong>DoR generato</strong></p></td> 
   </tr>
  <tr>
   <td><img src="assets/source_xdp_updated.png"/></td>
   <td><p>Se si utilizza il modello predefinito per generare il DoR:</br><img src="assets/source_form_default_updated.png"/></td>
   </tr>
   <tr>
   <td></td>
   <td><p>Se si utilizza il modulo di origine come modello per generare il DoR:</br></p><img src="assets/source_form_dor_updated.png"/></td>
   </tr>
  </tbody>
</table>

Come illustrato nella tabella, se si utilizza il modulo di origine come modello, il DoR mantiene il layout del modulo di origine.
Questo articolo descrive i percorsi consigliati per generare un DoR basato sui tre tipi di moduli di origine.

<table> 
 <tbody> 
  <tr> 
   <th><strong>Modulo di origine</strong></th> 
   <th><strong>Metodi per generare il DoR</strong></th> 
  </tr> 
  <tr> 
   <td><p>Moduli PDF non interattivi</p></td> 
   <td> 
    <ul> 
     <li><a href="#generate-document-of-record-using-cloud-configuration">Abilitare la generazione DoR prima della conversione di moduli adattivi per generare un DoR utilizzando un modello predefinito</a></li> 
     <li><a href="#edit-adaptive-form-properties-generate-document-of-record">Modificare le proprietà del modulo adattivo dopo la conversione del modulo adattivo per abilitare la generazione DoR utilizzando il modello predefinito o un altro modello di modulo</a></li> 
    </ul> </td> 
  </tr>
  <tr> 
   <td><p>Moduli Acro o moduli PDF basati su XFA</p></td> 
   <td> 
    <ul> 
     <li><a href="#use-input-form-as-template-to-generate-document-of-record">Abilitare la generazione DoR prima della conversione di moduli adattivi per generare il DoR utilizzando il modulo di origine come modello</a></li> 
     <li><a href="#edit-adaptive-form-properties-to-generate-document-of-record">Modificare le proprietà del modulo adattivo dopo la conversione del modulo adattivo per abilitare la generazione DoR utilizzando il modello predefinito, il modulo di origine come modello o qualsiasi altro modello di modulo</a></li> 
    </ul> </td> 
  </tr>    
 </tbody> 
</table>

## Genera documento record per moduli PDF non interattivi {#generate-document-of-record-non-interactive-pdf}

Se si utilizza un modulo PDF non interattivo come modulo di origine per il servizio di conversione automatica dei moduli, è possibile:

* abilitare la generazione di DoR prima della conversione di moduli adattivi per generare un DoR utilizzando un modello predefinito
* o modificare le proprietà del modulo adattivo dopo la conversione del modulo adattivo per abilitare la generazione DoR utilizzando il modello predefinito o un altro modello di modulo

### Attivare la generazione DoR prima della conversione per generare il DoR utilizzando il modello predefinito {#generate-document-of-record-using-cloud-configuration}

1. Selezionare **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Automated Forms Conversion Configuration]** > Proprietà della configurazione cloud utilizzata per la conversione > **[!UICONTROL Advanced]** > **[!UICONTROL Generate Document of Record]** opzione.

   ![Genera documento di registrazione con configurazione cloud](assets/generate_dor_cloud_config.gif)

1. Tap **[!UICONTROL Save & Close]** to save the settings.

1. [Eseguire la conversione](../help/convert-existing-forms-to-adaptive-forms.md). Assicurati di utilizzare la configurazione cloud modificata nel passaggio 1 di queste istruzioni.
Quando si invia il modulo adattivo convertito, il DoR viene generato automaticamente utilizzando il modello predefinito.

### Modificare le proprietà del modulo adattivo dopo la conversione per abilitare la generazione DoR {#edit-adaptive-form-properties-generate-document-of-record}

Se non si abilita la generazione DoR prima di convertire il modulo di origine in un modulo adattivo, è comunque possibile farlo dopo la conversione.

1. [Eseguire la conversione](../help/convert-existing-forms-to-adaptive-forms.md) nel modulo PDF non interattivo per generare un modulo adattivo.

1. Selezionate il modulo adattivo nella **[!UICONTROL output]** cartella e toccate **[!UICONTROL Properties]**.

1. Nella **[!UICONTROL Form Model]** scheda, espandere la **[!UICONTROL Document of Record Template Configuration]** sezione e selezionare **[!UICONTROL Generate Document of Record]**.

   ![Genera documento di record](assets/generate_dor_af_properties.png)

1. Tap **[!UICONTROL Save & Close]** to save the settings.

Quando si invia il modulo adattivo convertito, il DoR viene generato automaticamente utilizzando il modello predefinito. Se si desidera associare qualsiasi altro modello DoR al modulo adattivo convertito, è possibile selezionare **[!UICONTROL Associate form template as the Document of Record template]** l&#39;opzione.

## Genera documento record per moduli Acro o PDF basati su XFA {#generate-document-of-record-acroform-xfaform}

Se si utilizza un modulo Acro o un modulo PDF basato su XFA come modulo di origine per il servizio di conversione automatica dei moduli, è possibile:

* abilitare la generazione di DoR prima della conversione di moduli adattivi per generare il DoR utilizzando come modello il modulo di origine

* o modificare le proprietà del modulo adattivo dopo la conversione di un modulo adattivo per abilitare la generazione DoR utilizzando il modello predefinito, il modulo di origine come modello o qualsiasi altro modello di modulo

### Attivazione della generazione DoR prima della conversione per generare il DoR utilizzando il modello di modulo di origine {#use-input-form-as-template-to-generate-document-of-record}

1. Selezionare **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Automated Forms Conversion Configuration]** > Proprietà della configurazione cloud utilizzata per la conversione > **[!UICONTROL Advanced]** > **[!UICONTROL Generate Document of Record]** opzione.

1. Tap **[!UICONTROL Save & Close]** to save the settings.

1. [Eseguire la conversione](../help/convert-existing-forms-to-adaptive-forms.md). Assicurati di utilizzare la configurazione cloud modificata nel passaggio 1 di queste istruzioni.
Il servizio di conversione associa automaticamente il modulo Acro o il modulo PDF basato su XFA al modulo adattivo convertito come modello DoR.
È possibile aprire le proprietà del modulo adattivo per visualizzare il modello DoR nella **[!UICONTROL Document of Record Template Configuration]** sezione della **[!UICONTROL Form Model]** scheda.

   ![Modificare le proprietà dei moduli adattivi per generare il documento di registrazione](assets/generate_dor_af_properties_xdp_acro.png)

   Quando si invia il modulo adattivo convertito, il DoR viene generato automaticamente utilizzando il modello di modulo di origine.

### Modificare le proprietà del modulo adattivo dopo la conversione per abilitare la generazione DoR {#edit-adaptive-form-properties-to-generate-document-of-record}

1. [Eseguire la conversione](../help/convert-existing-forms-to-adaptive-forms.md) nel modulo PDF non interattivo per generare un modulo adattivo.

1. Selezionate il modulo adattivo nella **[!UICONTROL output]** cartella e toccate **[!UICONTROL Properties]**.

1. Nella **[!UICONTROL Form Model]** scheda, espandere la **[!UICONTROL Document of Record Template Configuration]** sezione e selezionare **[!UICONTROL Generate Document of Record]** per abilitare la generazione DoR utilizzando il modello predefinito.
È inoltre possibile selezionare l&#39; **[!UICONTROL Associate form template as the Document of Record template]** opzione e selezionare il modello per abilitare la generazione DoR utilizzando il modello di modulo di origine o qualsiasi altro modello di modulo.

1. Tap **[!UICONTROL Save & Close]** to save the settings.
