# Integrazioni fiscali e hardware

## Principio

La nostra applicazione gestisce l'esperienza di vendita e la loyalty. La stampante fiscale o il registratore telematico esistente nel locale mantiene il ruolo fiscale: emissione del documento commerciale e trasmissione dei corrispettivi secondo la propria configurazione.

Non chiediamo al locale di acquistare una nuova stampante fiscale.

## Famiglie iniziali

### Epson FP-81II RT

Prima integrazione da valutare. Il dispositivo può collegarsi via Ethernet, USB o seriale; per il prototipo è preferibile Ethernet, quando disponibile, perché facilita installazione e diagnostica in rete locale.

Da validare su dispositivo reale:

- protocollo e librerie ufficiali disponibili;
- invio vendita, esito e identificativo del documento;
- annullamento;
- comportamento in caso di carta esaurita, offline o errore;
- chiusura giornaliera e riconnessione.

### RCH

RCH è una famiglia di prodotti, non un unico protocollo da assumere compatibile. La seconda integrazione richiede la scelta di un modello preciso, preferibilmente una stampante fiscale pensata per essere comandata da PC/tablet, ad esempio la famiglia PRINT! RT da verificare con il produttore o rivenditore.

## Architettura desiderata

```text
Interfaccia cassa
       |
Motore vendite e loyalty
       |
Adapter fiscale (contratto comune)
       |------------------|
Adapter Epson       Adapter RCH
       |                  |
Stampante/RT Epson  Stampante/RT RCH
```

Ogni adapter deve esporre almeno: verifica disponibilità, emissione vendita, lettura esito, annullamento, richiesta di chiusura Z, lettura dei riferimenti della chiusura e diagnostica. L'applicazione non deve contenere logica dipendente da una singola marca.

L'esito di una vendita fiscalizzata deve includere, ove restituiti dal dispositivo: numero documento, importo, data/ora, matricola della stampante e numero Z. Questi dati collegano l'archivio operativo alla fonte fiscale.

## Strategia di compatibilità

Supportare solo modelli testati fisicamente. Nel materiale commerciale indicare modello e versione supportati, non soltanto il marchio.

