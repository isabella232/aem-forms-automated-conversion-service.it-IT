---
title: 'Risoluzione dei problemi relativi al servizio di conversione automatizzata dei moduli '
seo-title: 'Risoluzione dei problemi relativi al servizio di conversione automatizzata dei moduli (AFCS) '
description: 'Problemi AFCS comuni e relative soluzioni '
seo-description: Problemi AFCS comuni e relative soluzioni
contentOwner: khsingh
topic-tags: forms
translation-type: tm+mt
source-git-commit: 65dd07048b3cc7d9434568a8188dc08a1db66ada

---


# Risoluzione dei problemi relativi al servizio di conversione automatizzata dei moduli


L&#39;articolo fornisce informazioni sui problemi di installazione, configurazione e amministrazione che possono verificarsi in un ambiente di produzione di Automated Forms Conversion Service. Il documento fornisce inoltre istruzioni e procedure di base per la risoluzione dei problemi e spiegazioni sui messaggi di errore più comuni.

## Errori comuni {#commonerrors}

| Errore | Esempio |
|--- |--- |
| **Messaggio** di errore <br> L&#39;intestazione del token di accesso non è disponibile. <br><br>**Motivo **<br>: un amministratore ha creato più configurazioni IMS o la configurazione IMS non è in grado di raggiungere il servizio AFCS su Adobe Cloud.<br><br>**Risoluzione**<br> In presenza di più configurazioni, eliminate tutte le configurazioni e [create una nuova configurazione](configure-service.md#obtainpubliccertificates). <br> Se è presente una singola configurazione, utilizzate **[!UICONTROL Health Check]** per [controllare la connettività](configure-service.md#createintegrationoption). | ![Modulo colorato](assets/invalid-ims-configuration.png) |
| **Messaggio** di errore <br> Impossibile connettersi al servizio.  <br><br>**Motivo **<br>: l&#39;URL del servizio non corretto o l&#39;URL del servizio non è indicato nei servizi cloud di Automated Forms Conversion Service.<br><br>**URL** <br> del [servizio di correzione della risoluzione](configure-service.md#configure-the-cloud-service) nei servizi cloud Automated Forms Conversion Service. | ![Modulo colorato](assets/wrong-endpoint-configured.png) |
