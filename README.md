# Loyalty

Una cassa software per bar e piccoli esercenti con loyalty integrata e automatica.

L'obiettivo è semplice: rendere il ritorno dei clienti più frequente senza rallentare la cassa, senza cambiare la stampante fiscale esistente e senza affidare alla cassiera attività aggiuntive.

## Stato

Siamo nella fase di definizione del prodotto. Non è ancora stato scelto lo stack tecnico né è stato scritto codice applicativo.

## MVP in una frase

La cassiera batte normalmente l'ordine nella nostra cassa; dopo che la stampante fiscale conferma l'emissione del documento commerciale, il sistema accredita in automatico i punti al cliente identificato.

## Documentazione

- [Visione e perimetro MVP](docs/01-visione-e-mvp.md)
- [Flussi operativi di cassa](docs/02-flussi-cassa.md)
- [Integrazioni fiscali e hardware](docs/03-integrazioni-hardware.md)
- [Decisioni e questioni aperte](docs/04-decisioni-aperte.md)

## Principi

1. La velocità della cassiera viene prima di tutto.
2. I punti si accreditano solo dopo la conferma della stampa fiscale.
3. Il locale conserva la propria stampante fiscale: nessun cambio hardware richiesto.
4. Si parte dai bar e dai flussi essenziali; niente gestionale generalista nella prima versione.

