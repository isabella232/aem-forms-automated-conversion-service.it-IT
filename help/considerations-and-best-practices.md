---
title: '[NON PUBBLICARE] Best practice e considerazioni '
seo-title: '[NON PUBBLICARE] Best practice e considerazioni '
description: 'null'
seo-description: 'null'
page-status-flag: never-activated
uuid: c2821264-39e2-44f8-b234-835c46f33fd5
topic-tags: introduction
discoiquuid: b786e40a-202e-4e17-a2f5-1f77c46538c2
privatebeta: true
index: false
translation-type: tm+mt
source-git-commit: afe461baa5bcfc1106c16aae2d6a9c839ea675e8

---


# [NON PUBBLICARE] Best practice e considerazioni {#do-not-publish-best-practices-and-considerations}

Il servizio di conversione automatizzata di AEM Forms converte un modulo PDF in un modulo adattivo. Il servizio utilizza algoritmi di intelligenza artificiale e di machine learning per comprendere il layout e i campi del modulo di origine. Ogni servizio di machine learning impara continuamente dai dati di origine e produce un output migliore con ogni churn. Questi servizi imparano dall&#39;esperienza come gli umani.

Il servizio di conversione automatizzata dei moduli è disponibile in una vasta gamma di moduli. Identifica facilmente i campi in un modulo di origine e produce moduli adattivi. Tuttavia, nei moduli PDF sono presenti alcuni campi e stili che possono essere facilmente visibili all&#39;occhio umano ma che sono difficili da comprendere per il servizio. Il servizio può assegnare tipi di campi o pannelli diversi da quelli applicabili ad alcuni campi o stili. Tutti questi pattern di campo e stile sono elencati di seguito.

Il servizio inizierebbe a identificare e assegnare campi o pannelli corretti a questi pattern, continuando a imparare dai dati di origine. Al momento, per risolvere tali problemi è possibile utilizzare l&#39;editor [Revisione e Correzione](review-correct-ui-edited.md) . Prima di iniziare a risolvere i problemi o a leggere meglio, è necessario acquisire dimestichezza con i componenti [dei moduli](https://helpx.adobe.com/experience-manager/6-5/forms/using/introduction-forms-authoring.html)adattivi.

## Generale {#general}

<!--
Comment Type: draft

<ul>
<li>Service does not convert filled PDF forms to adaptive form. Use empty adaptive forms.Service does not convert colored PDF forms to adaptive form. Use black and white or grayscale adaptive forms. <br /> </li>
<li>Service does not convert filled PDF forms to adaptive form. Use empty adaptive forms.</li>
<li>Service does not support scanned forms. Do not use scanned forms. </li>
<li>Service can fail to recognize text and fields in a dense form. Increase the width between text and fields of a dense form before starting the conversion.</li>
<li>Service does not extract images. Manually add images to converted forms.</li>
<li>Service does not extract text present within an image. Manually add text to the adaptive form.</li>
</ul>
-->

<table border="1" cellpadding="1" cellspacing="0" style="border-collapse: separate; border-spacing: 0px;" width="100%"> 
 <tbody>
  <tr>
   <td width="30%">Pattern e risoluzione noti</td> 
   <td width="70%">Esempio</td> 
  </tr>
  <tr>
   <td><p><strong>Pattern</strong></p> <p>Il servizio non converte i moduli PDF colorati in moduli adattivi.</p> <p> </p> <p><strong>Risoluzione</strong></p> <p>Utilizzare moduli PDF in bianco e nero o in scala di grigio. </p> </td> 
   <td style="text-align: left;"> <img src="assets/coloured-form.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>Pattern</strong></p> <p>Il servizio non converte i moduli PDF compilati in moduli adattivi.</p> <p> </p> <p><strong>Risoluzione</strong></p> <p>Utilizzare moduli adattivi vuoti.</p> </td> 
   <td style="text-align: left;"><img src="assets/pre-filled-form.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>Pattern</strong></p> <p>Il servizio potrebbe non riuscire a riconoscere testo e campi in un modulo denso.</p> <p> </p> <p><strong>Risoluzione</strong></p> <p>Aumentare la larghezza tra il testo e i campi di un modulo denso prima di avviare la conversione.</p> </td> 
   <td style="text-align: left;"><img src="assets/dense%20form.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>Pattern</strong></p> <p>Il servizio non supporta i moduli digitalizzati.</p> <p> </p> <p><strong>Risoluzione</strong></p> <p>Non utilizzare moduli digitalizzati. </p> </td> 
   <td><img src="assets/scanned-form.jpg" /></td> 
  </tr>
  <tr>
   <td><p><strong>Pattern</strong></p> <p>Il servizio non estrae immagini e testo all’interno delle immagini. </p> <p> </p> <p><strong>Risoluzione</strong></p> <p>Aggiungere manualmente immagini o testo ai moduli convertiti.</p> </td> 
   <td><img src="assets/image-in-adaptive-form.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>Pattern</strong></p> <p>Le tabelle con bordi puntati o non chiari non vengono convertite.</p> <p><strong>Risoluzione</strong></p> <p>Utilizzare tabelle con bordi e bordi espliciti chiari. supportati.</p> </td> 
   <td><img src="assets/border-less-tables.png" /></td> 
  </tr>
 </tbody>
</table>

## Gruppo di scelta {#choice-group}

<table border="1" cellpadding="1" cellspacing="0" width="100%"> 
 <tbody>
  <tr>
   <td width="30%">Pattern</td> 
   <td width="70%">Esempio</td> 
  </tr>
  <tr>
   <td><p><strong>Pattern</strong></p> <p>Le opzioni per i gruppi di scelta con forme diverse da caselle o cerchi non vengono convertite nei componenti per modulo adattivo corrispondenti. </p> <p> </p> <p><strong>Risoluzione</strong></p> <p>Modificate le forme delle opzioni di scelta in caselle o cerchi oppure utilizzate l'editor Revisione e Correzione per identificare le forme.</p> </td> 
   <td><img src="assets/shaded-box-patterns.png" /> </td> 
  </tr>
 </tbody>
</table>

## Form fields {#form-fields}

<table border="1" cellpadding="1" cellspacing="0" width="100%"> 
 <tbody>
  <tr>
   <td width="30%">Pattern</td> 
   <td width="70%">Esempio</td> 
  </tr>
  <tr>
   <td width="25%"><p><strong>Pattern</strong></p> <p>Il servizio non identifica i campi senza bordi chiari.</p> <p> </p> <p><strong>Risoluzione</strong></p> <p>Utilizzate l'editor di revisione e correzione per identificare tali campi.</p> <p> </p> <p> </p> </td> 
   <td width="50%"><br /> <img src="assets/fields-without-clear-borders.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>Pattern</strong></p> <p>Il servizio lascia alcuni campi del modulo con didascalie in basso o a destra non identificate.</p> <p> </p> <p><strong>Risoluzione</strong></p> <p>Utilizzate l'editor di revisione e correzione per identificare tali campi</p> </td> 
   <td><br /> <img src="assets/forms-with-clear-borders-scale.png" /><br /> </td> 
  </tr>
  <tr>
   <td><p><strong>Pattern</strong></p> <p>Il servizio unisce o assegna un tipo errato ad alcuni campi del modulo che si trovano molto vicini tra loro o che non hanno bordi chiari. </p> <p> </p> <p><strong>Risoluzione</strong></p> <p>Utilizzate l'editor di revisione e correzione per identificare tali campi.</p> </td> 
   <td><img src="assets/forms-with-fields-placed-nearby.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>Pattern</strong></p> <p>Il servizio potrebbe non riuscire a riconoscere i campi con didascalie lontane o una linea tratteggiata tra la didascalia e il campo di input.</p> <p> </p> <p><strong>Risoluzione</strong></p> <p>Per risolvere tali problemi, utilizzare i campi modulo con limiti definiti o l'editor Revisione e Correzione.</p> </td> 
   <td><img src="assets/form-fields-with-far-away-captions.png" /></td> 
  </tr>
 </tbody>
</table>

## Elenchi {#lists}

<table border="1" cellpadding="1" cellspacing="0" width="100%"> 
 <tbody>
  <tr>
   <td width="30%">Pattern</td> 
   <td width="70%">Esempio</td> 
  </tr>
  <tr>
   <td><p><strong>Pattern</strong></p> <p>Gli elenchi contenenti campi modulo sono uniti o non sono convertiti nei componenti modulo adattivi corrispondenti</p> <p><strong>Risoluzione</strong></p> <p>Per risolvere tali problemi, utilizzare i campi modulo con limiti definiti o l'editor Revisione e Correzione.</p> </td> 
   <td><img src="assets/lists-with-fields.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>Pattern</strong></p> <p>Il servizio può lasciare alcuni elenchi nidificati non identificati</p> <p> </p> <p><strong>Risoluzione</strong></p> <p>Per risolvere tali problemi, utilizzate l'editor Review e Correction.</p> </td> 
   <td><img src="assets/nested-lists.png" /> </td> 
  </tr>
  <tr>
   <td><p><strong>Pattern</strong></p> <p>Il servizio unisce alcuni elenchi contenenti gruppi di scelta tra loro</p> <p><strong>Risoluzione</strong></p> <p>Per risolvere tali problemi, utilizzate l'editor Review e Correction.</p> </td> 
   <td><img src="assets/lists-containing-choice-groups.png" /> </td> 
  </tr>
 </tbody>
</table>

<!--
Comment Type: draft

<h3>Choice groups</h3>
-->

<!--
Comment Type: draft

<ul>
<li>Lists with form fields, nested lists, and nested choice groups are not supported.</li>
<li>Form fields with captions at bottom or right are not supported.</li>
<li>Form fiields without bordes are not supported.</li>
<li>Hidden form fields are not supported.</li>
<li>Button in PDF forms are not converted to adaptive form buttons.<br /> </li>
<li>Tables with clear explicit boundaries and borders are supported.</li>
<li>Fields with far away captions are not supported.<br /> </li>
<li>Choice groups with only box or circle shaped selectors are supported. </li>
</ul>
-->

