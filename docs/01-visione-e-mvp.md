# Visione e perimetro MVP

## Problema

I piccoli esercenti vogliono fidelizzare i clienti, ma i programmi loyalty tradizionali richiedono tempo alla cassa o chiedono al cliente di installare e usare strumenti poco immediati. Nei momenti affollati ogni passaggio extra diventa un problema.

## Proposta

Una cassa software pensata per bar e piccoli locali, con loyalty integrata. La vendita viene gestita normalmente; la loyalty usa il valore reale dell'ordine e non richiede alla cassiera di inserire soglie, punti o importi manualmente.

## Utenti iniziali

- Cassiera: deve chiudere la vendita con il minor numero possibile di tocchi.
- Titolare: configura prodotti, regole loyalty e consulta risultati essenziali.
- Cliente: si identifica rapidamente e vede il proprio progresso verso un premio.

## Perimetro della prima versione

- Catalogo essenziale di prodotti e prezzi.
- Creazione dell'ordine e calcolo del totale.
- Scelta del metodo di pagamento come informazione di vendita.
- Identificazione opzionale del cliente per la loyalty.
- Invio dell'ordine alla stampante fiscale compatibile.
- Accredito automatico dei punti dopo esito fiscale positivo.
- Annullamento di una vendita appena emessa, con documento di annullamento fiscale e revoca dei punti.
- Archivio consultabile delle vendite e dei documenti emessi.
- Chiusura giornaliera richiesta alla stampante fiscale, con storico delle chiusure.

## Fuori dal perimetro iniziale

- Resi.
- Magazzino.
- Tavoli e comande complesse.
- Delivery e marketplace.
- Fatturazione e gestione contabile completa.
- Pagamenti gestiti direttamente dalla piattaforma.
- Compatibilità universale con ogni modello di stampante fiscale.

## Misura del successo

Una vendita loyalty deve richiedere alla cassiera lo stesso tempo, o quasi, di una vendita senza loyalty. L'accredito dei punti non può avvenire prima della conferma della stampa fiscale.

La fonte fiscale resta sempre la stampante/RT. La nostra applicazione conserva i riferimenti ricevuti dal dispositivo e offre un archivio operativo, senza sostituirsi all'archivio fiscale del registratore.

