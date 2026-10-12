# Loyalty

Una cassa software per bar e piccoli esercenti, pensata per ordini al tavolo via QR e pagamenti rapidi al banco.

L'obiettivo è semplice: far arrivare alla cassa le comande create dal cliente, consegnarle al tavolo e chiuderle con un pagamento e uno scontrino, senza cambiare la stampante fiscale esistente e senza rallentare la cassiera.

## Stato

Siamo nella fase di definizione del prodotto. Non è ancora stato scelto lo stack tecnico né è stato scritto codice applicativo.

## MVP in una frase

Il cliente compone la comanda dal QR del tavolo; la cassa la riceve, la gestisce e, al pagamento, invia l'importo alla stampante fiscale e al POS. Solo dopo la conferma del documento fiscale la comanda risulta pagata e passa nello storico.

Il servizio web gestisce menu QR e comande; l'applicativo installato nel locale gestisce cassa, POS, documenti fiscali e chiusure.

## Documentazione

- [Visione e perimetro MVP](docs/01-visione-e-mvp.md)
- [Flussi operativi di cassa](docs/02-flussi-cassa.md)
- [Integrazioni fiscali e hardware](docs/03-integrazioni-hardware.md)
- [Decisioni e questioni aperte](docs/04-decisioni-aperte.md)
- [Flusso di collaborazione](docs/05-flusso-collaborazione.md)
- [Catalogo, menu e allergeni](docs/06-catalogo-menu-allergeni.md)
- [Roadmap per il pilota](docs/07-roadmap-pilota.md)
- [Fondazione tecnica e modello dati](docs/08-fondazione-tecnica-e-modello-dati.md)
- [Regole per i contributor](CONTRIBUTING.md)

## Principi

1. La velocità della cassiera viene prima di tutto.
2. Una comanda diventa pagata solo dopo la conferma della stampa fiscale.
3. Il locale conserva la propria stampante fiscale: nessun cambio hardware richiesto.
4. Si parte dai bar e dai flussi essenziali; niente gestionale generalista nella prima versione.

