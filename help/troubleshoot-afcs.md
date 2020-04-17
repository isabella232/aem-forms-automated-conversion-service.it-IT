---
title: 'Risoluzione dei problemi relativi al servizio di conversione automatizzata dei moduli '
seo-title: 'Risoluzione dei problemi relativi al servizio di conversione automatizzata dei moduli (AFCS) '
description: 'Problemi AFCS comuni e relative soluzioni '
seo-description: Problemi AFCS comuni e relative soluzioni
contentOwner: khsingh
topic-tags: forms
translation-type: tm+mt
source-git-commit: 0af626e21a0c3d6a7d3c339c0b87179b048092d3

---


# Risoluzione dei problemi relativi al servizio di conversione automatizzata dei moduli


<!--The article provides information on installation, configuration and administration issues that may arise in an Automated Forms Conversion Service production environment. --> The document  provides basic troubleshooting steps for common errors.

## Errori comuni {#commonerrors}

<table>
<thead>
<tr>
<th>Errore</th>
<th>Esempio</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>Messaggio</strong> di errore <br> L'intestazione del token di accesso non è disponibile. <br><br><strong>Motivo</strong> <br> : un amministratore ha creato più configurazioni IMS o la configurazione IMS non è in grado di raggiungere il servizio AFCS su Adobe Cloud. <br><br><strong>Risoluzione</strong><br> In presenza di più configurazioni, eliminate tutte le configurazioni e <a href="configure-service.md#obtainpubliccertificates">create una nuova configurazione</a>. <br> Se è presente una singola configurazione, utilizzate <strong> Health Check </strong> per <a href="configure-service.md#createintegrationoption">verificare la connettività</a>.</td>
<td><img alt="L'intestazione del token di accesso non è disponibile" src="assets/invalid-ims-configuration.png" /></td>
</tr>
<tr>
<td><strong>Messaggio</strong> di errore <br> Impossibile connettersi al servizio.  <br><br><strong>Motivo</strong> <br> : l'URL del servizio non corretto o l'URL del servizio non è indicato nei servizi cloud di Automated Forms Conversion Service. <br><br><strong>URL</strong> <br> del <a href="configure-service.md#configure-the-cloud-service">servizio di correzione della risoluzione</a> nei servizi cloud Automated Forms Conversion Service.</td>
<td><img alt="Impossibile connettersi al servizio." src="assets/wrong-endpoint-configured.png" /></td>
</tr>
<tr>
<td><strong>Messaggio</strong> di errore <br> Impossibile convertire il modulo.  <br><br><strong>Motivo</strong><br> : problemi di connettività di rete al termine del servizio, manutenzione programmata o interruzione in Adobe Cloud. <br><br><strong>Risoluzione</strong><br> dei problemi di connettività di rete al termine dell'evento e verifica lo stato del servizio su <a href="https://status.adobe.com/">https://status.adobe.com/</a> per un'interruzione pianificata o non pianificata.</td>
<td><img alt="Impossibile convertire il modulo." src="assets/service-failure.png" /></td>
</tr>
<tr>
<td><strong>Messaggio</strong> di errore <br> Il numero di pagine è superiore a 15.  <br><br><strong>Motivo</strong><br> La lunghezza del modulo di origine è superiore a 15 pagine.  <br><br><strong>Risoluzione</strong><br> Utilizzare Adobe Acrobat per suddividere i moduli con più di 15 pagine. Portare il numero di pagine in un modulo a meno di 15.</td>
<td><img alt="Il numero di pagine è superiore a 15." src="assets/number-of-pages.png" /></td>
</tr>
<tr>
<td><strong>Messaggio</strong> di errore <br> Il numero di file è superiore a 15.  <br><br><strong>Motivo</strong> <br> La cartella contiene più di 15 moduli. <br><br><strong>Risoluzione</strong><br> Portare il numero di moduli in una cartella a meno o uguale a 15. Portate il numero totale di pagine in una cartella inferiore a 50. Portate le dimensioni della cartella a meno di 10 MB. Non tenere i moduli in una sottocartella. Organizzare i moduli di origine in un batch di 8-15 moduli.</td>
<td><img alt="Il numero di file è superiore a 15." src="assets/number-of-pages.png" /></td>
</tr>
<tr>
<td><strong>Messaggio</strong> di errore <br> Il formato del file di origine non è supportato.  <br><br><strong>Motivo</strong> <br> : nella cartella contenente i moduli di origine sono presenti alcuni file non supportati. <br><br><strong>Risoluzione</strong> <br> Il servizio supporta solo i file .xdp e .pdf. Rimuovete i file con qualsiasi altra estensione dalla cartella ed eseguite la conversione.</td>
<td><img alt="Il formato del file di origine non è supportato." src="assets/unsupported-file-formats.png" /></td>
</tr>
<tr>
<td><strong>Messaggi</strong> <br> di errore I moduli analizzati non sono supportati.  <br><br><strong>Motivo</strong><br> Il modulo PDF contiene solo immagini digitalizzate del modulo e non contiene alcuna struttura di contenuto. <br><br><strong>Risoluzione</strong> <br> Il servizio non supporta la conversione di moduli digitalizzati o di un'immagine di un modulo in un modulo adattativo out-of-the-box. Tuttavia, è possibile utilizzare Adobe Acrobat per convertire l'immagine di un modulo in un modulo PDF. Quindi, utilizzare il servizio per convertire il modulo PDF in un modulo adattivo. Utilizzare sempre un'immagine di alta qualità del modulo per la conversione in Acrobat. Migliora la qualità della conversione.</td>
<td><img alt="I moduli analizzati non sono supportati." src="assets/scanned-forms-error.png" /></td>
</tr>
<tr>
<td><strong>Il modulo PDF crittografato con messaggio</strong> <br> di errore non è supportato.  <br><br><strong>Motivo</strong> : la cartella contiene moduli PDF crittografati <br> . <br><br><strong>Risoluzione</strong> <br> Il servizio non supporta la conversione di un modulo PDF crittografato in un modulo adattivo. Rimuovere la cifratura, caricare il modulo non crittografato ed eseguire la conversione.</td>
<td><img alt="Il modulo PDF crittografato non è supportato." src="assets/secured-pdf-form.png" /></td>
</tr>
<tr>
<td><strong>Messaggio</strong> <br> di errore Impossibile analizzare lo schema JSON del metamodello.  <br><br><strong>Motivo</strong> <br> : lo schema JSON fornito al servizio non è formattato correttamente, contiene caratteri non validi o utilizza una sintassi non valida per mappare i componenti.  <br><br><strong>Risoluzione</strong><br> Controllare la formattazione del file JSON. È possibile utilizzare qualsiasi validatore JSON online per verificare la formattazione e la struttura dello schema. Consultate <a href="extending-the-default-meta-model.md">Estendere l'articolo meta-modello</a> predefinito per informazioni sulla sintassi del meta-modello.</td>
<td><img alt="Impossibile analizzare lo schema JSON del meta-modello" src="assets/invalid-meta-model-schema.png" /></td>
</tr>
</tbody>
</table>
