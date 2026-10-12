# Flussi operativi di cassa

## Ciclo della comanda

1. Il cliente entra e si siede a un tavolo numerato.
2. Scansiona il QR associato al tavolo, apre il menu e crea la comanda.
3. Prima dell'invio, il menu chiede una conferma esplicita: `Sei sicuro di inviare la comanda?`.
4. Il servizio salva una fotografia di tavolo, prodotti, prezzi e allergeni; il carrello si svuota e il cliente vede solo `Comanda inviata`.
5. Il servizio invia la comanda in tempo reale alla cassa.
6. L'applicativo la salva localmente e conferma la ricezione al servizio.
7. La cassa mostra la nuova comanda nella lista `Da gestire`.
8. Il personale porta la comanda al tavolo e la marca `Consegnata`. La comanda non è ancora pagata.
9. Quando il cliente arriva in cassa, la cassiera apre una o più comande aperte dello stesso tavolo e preme `Pagamento`.
10. La cassa guida la scelta fra conto unico e conto separato.
11. Per ogni quota da incassare, la cassa invia l'importo al POS e attende il suo esito; quindi invia i dati alla stampante fiscale.
12. Dopo la conferma del documento fiscale, ogni comanda inclusa risulta `Pagata`, scompare dalle comande attive e appare in `Documenti emessi`.

Il servizio conserva le comande e riceve i cambi di stato, ma il cliente non vede consegna, pagamento o documento: dopo l'invio riceve solo la conferma della comanda.

## Stati della comanda

```text
Da gestire → Consegnata → In pagamento → Pagata → Documenti emessi
                                  ↓
                            Da verificare
```

`Da gestire` e `Consegnata` sono comande attive. `Pagata` non rimane nella lista di lavoro: è visibile soltanto nell'archivio `Documenti emessi`.

Se l'applicativo è offline, il servizio mantiene le nuove comande in attesa di consegna. Quando la cassa torna connessa, anche tramite hotspot temporaneo, le riceve e le salva localmente.

## Pagamento separato

La cassa deve guidare la divisione, senza richiedere calcoli manuali alla cassiera. Può includere più comande aperte dello stesso tavolo in un unico documento di vendita. La somma delle quote deve coincidere con il totale delle comande selezionate prima dell'emissione dei documenti fiscali. Il dettaglio esatto della divisione (per persona, per prodotti o per importo) resta da definire.

## Errore di stampa o comunicazione

Se la stampante risponde con un errore certo prima dell'emissione:

1. La comanda o la quota rimane in stato `In pagamento`.
2. La cassiera vede un messaggio immediato e semplice: `Scontrino non emesso. Riprova.`

Se la risposta si interrompe e non è possibile sapere se il documento sia stato emesso:

1. La comanda o la quota passa a `Da verificare`.
2. La cassa non deve reinviare automaticamente la vendita.
3. Il sistema interroga la stampante e confronta numero documento, importo, data/ora e matricola per stabilire se la vendita sia stata fiscalizzata.
4. Se il pagamento è stato approvato dal POS ma il documento non risulta emesso, la cassa lo segnala chiaramente per la gestione manuale.

## Annullamento iniziale

1. Si seleziona una vendita già fiscalizzata.
2. La cassa richiede alla stampante fiscale il documento di annullamento, collegato alla vendita originaria quando previsto dal dispositivo.
3. Solo dopo esito positivo, il documento è marcato `annullato` nello storico.

Il reso non è incluso nella prima versione.

## Archivio documenti

L'archivio operativo, chiamato `Documenti emessi`, mostra soltanto le vendite per cui esiste un documento fiscale emesso o annullato. Ogni elemento deve conservare data e ora, numero documento, tavolo, importo, stato, matricola della stampante e riferimento alla chiusura Z.

La ricerca iniziale deve supportare numero documento, data, importo e tavolo. Dal dettaglio deve essere possibile ristampare una copia cortesia e avviare l'annullo quando consentito.

Le comande `Da gestire`, `Consegnata`, `In pagamento` e `Da verificare` non sono documenti emessi: restano nella gestione comande o in una sezione separata per le verifiche.

## Chiusura giornaliera

1. Il titolare avvia la chiusura dalla cassa.
2. La cassa mostra il riepilogo della giornata: vendite, contanti, carte, totale e numero documenti.
3. La cassa invia alla stampante fiscale la richiesta di chiusura.
4. Solo dopo l'esito positivo della stampante, salva il numero Z, data/ora, matricola e totali e marca la giornata come chiusa.

Se la risposta della stampante si interrompe, la chiusura resta `Da verificare`: prima di un nuovo tentativo, la cassa deve verificare se la Z sia già stata emessa.

