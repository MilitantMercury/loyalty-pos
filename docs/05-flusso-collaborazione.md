# Flusso di collaborazione

## Obiettivo

Lavorare in più persone mantenendo `main` stabile, ogni scelta rintracciabile e ogni modifica facilmente rivedibile.

## Ciclo di lavoro

```text
Issue o decisione
        ↓
Branch breve
        ↓
Pull request
        ↓
Revisione di un'altra persona
        ↓
Squash merge su main
```

## Regole condivise

- Nessun push diretto su `main`.
- Una branch tratta un solo obiettivo e resta aperta il meno possibile.
- Ogni PR richiede almeno una revisione da qualcuno che non ne sia autore.
- Il merge è squash: la cronologia di `main` contiene un commit chiaro per ogni cambiamento concluso.
- Ogni modifica richiede l'aggiornamento della documentazione pertinente nella stessa PR. La regola vale senza eccezioni anche per fondatori, maintainer e contributori che usano Codex.
- Le decisioni con impatto sul prodotto o sull'architettura vengono annotate in `docs/decisions/`.
- Quando sarà scelto lo stack, lint, formattazione e test dovranno superare in automatico prima del merge.

## Etichette per le issue

| Etichetta | Uso |
| --- | --- |
| `product` | Scelte di prodotto e priorità |
| `ux-cassa` | Velocità, semplicità e interfaccia della cassa |
| `menu-comande` | QR menu, catalogo, tavoli e ciclo della comanda |
| `fiscale-hardware` | Stampanti fiscali, RT e integrazioni hardware |
| `loyalty` | Clienti, punti e premi: area successiva al primo MVP |
| `bug` | Comportamento non corretto |
| `technical-debt` | Miglioramenti tecnici non urgenti |
| `decision-needed` | Scelta che richiede confronto prima dello sviluppo |

## Protezione di main

Nelle impostazioni GitHub del repository, `main` deve richiedere una pull request con almeno un'approvazione prima del merge. Quando saranno presenti workflow di controllo, anche i relativi check dovranno essere obbligatori.

## Eccezioni

Un intervento urgente può essere fatto con una branch `fix/` e una PR piccola; non elimina la revisione, l'aggiornamento della documentazione pertinente e il controllo successivo.

