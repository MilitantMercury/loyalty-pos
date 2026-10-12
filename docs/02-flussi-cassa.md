# Flussi operativi di cassa

## Vendita con loyalty

1. La cassiera crea l'ordine e seleziona i prodotti.
2. Il cliente si identifica, se desidera partecipare alla loyalty.
3. La cassiera chiude l'ordine e la cassa invia i dati alla stampante fiscale.
4. La stampante fiscale emette il documento commerciale e restituisce un esito positivo.
5. La vendita diventa fiscalizzata.
6. La cassa calcola e accredita i punti sulla base dell'importo della vendita.

Regola non negoziabile: se non esiste conferma positiva della stampa fiscale, la vendita non attribuisce punti.

## Vendita senza loyalty

Il flusso è identico, omettendo l'identificazione del cliente. La cassa non deve rendere obbligatoria la loyalty.

## Errore di stampa o comunicazione

Se la stampante risponde con un errore certo prima dell'emissione:

1. La vendita rimane in stato `Da fiscalizzare`.
2. Nessun punto viene accreditato.
3. La cassiera vede un messaggio immediato e semplice: `Scontrino non emesso. Riprova.`

Se la risposta si interrompe e non è possibile sapere se il documento sia stato emesso:

1. La vendita passa a `Da verificare`.
2. Nessun punto viene accreditato fino alla verifica.
3. La cassa non deve reinviare automaticamente la vendita.
4. Il sistema interroga la stampante e confronta numero documento, importo, data/ora e matricola per stabilire se la vendita sia stata fiscalizzata.

## Annullamento iniziale

1. Si seleziona una vendita già fiscalizzata.
2. La cassa richiede alla stampante fiscale il documento di annullamento, collegato alla vendita originaria quando previsto dal dispositivo.
3. Solo dopo esito positivo, la vendita è marcata `annullata` e i punti collegati sono revocati.

Il reso non è incluso nella prima versione.

## Archivio documenti

L'archivio operativo mostra soltanto le vendite per cui esiste un documento fiscale emesso o annullato. Ogni elemento deve conservare data e ora, numero documento, importo, stato, punti loyalty, matricola della stampante e riferimento alla chiusura Z.

La ricerca iniziale deve supportare numero documento, data, importo e cliente loyalty. Dal dettaglio deve essere possibile ristampare una copia cortesia e avviare l'annullo quando consentito.

Le vendite `Da fiscalizzare` e `Da verificare` non sono documenti emessi: restano in una sezione separata, dedicata alla risoluzione dei problemi.

## Chiusura giornaliera

1. Il titolare avvia la chiusura dalla cassa.
2. La cassa mostra il riepilogo della giornata: vendite, contanti, carte, totale e numero documenti.
3. La cassa invia alla stampante fiscale la richiesta di chiusura.
4. Solo dopo l'esito positivo della stampante, salva il numero Z, data/ora, matricola e totali e marca la giornata come chiusa.

Se la risposta della stampante si interrompe, la chiusura resta `Da verificare`: prima di un nuovo tentativo, la cassa deve verificare se la Z sia già stata emessa.

