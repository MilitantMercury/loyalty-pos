# Fondazione tecnica e modello dati

## Primo traguardo tecnico

Il primo sviluppo verticale è: catalogo gestito nell'applicativo locale, pubblicato al servizio, menu QR pubblico, invio della comanda e ricezione nella lista `Da gestire` dell'applicativo. POS e stampante fiscale entrano inizialmente con adapter simulati.

I dati monetari sono espressi in centesimi interi, gli identificatori sono UUID e le date sono in UTC. Le righe storiche non vengono eliminate: si disattivano o si collegano a un annullamento.

## Dati del servizio web

| Entità | Campi principali | Scopo |
| --- | --- | --- |
| `local_units` | `id`, `name`, `timezone`, `active` | Un esercente o punto operativo servito. |
| `terminals` | `id`, `local_unit_id`, `name`, `status`, `last_seen_at` | Applicativi locali collegati al servizio. |
| `dining_tables` | `id`, `local_unit_id`, `number`, `qr_token`, `active` | Tavoli e QR casuali. `qr_token` è univoco. |
| `categories` | `id`, `local_unit_id`, `name`, `sort_order`, `active` | Ordine e raggruppamento del menu. |
| `products` | `id`, `local_unit_id`, `category_id`, `name`, `description`, `price_cents`, `available`, `sort_order` | Catalogo pubblicato. |
| `allergens` | `id`, `code`, `name` | Dizionario allergeni. |
| `product_allergens` | `product_id`, `allergen_id` | Relazione prodotto-allergeni. |
| `orders` | `id`, `local_unit_id`, `dining_table_id`, `status`, `client_request_id`, `created_at` | Comande inviate dal menu. `client_request_id` è univoco per locale e impedisce doppi invii. |
| `order_items` | `id`, `order_id`, `product_id`, `name_snapshot`, `price_cents_snapshot`, `quantity`, `allergens_snapshot` | Fotografia immutabile della comanda. |
| `order_status_history` | `id`, `order_id`, `status`, `source`, `created_at` | Tracciamento dei cambi di stato. |
| `terminal_deliveries` | `id`, `order_id`, `terminal_id`, `sent_at`, `acknowledged_at` | Consegna tecnica e conferma di ricezione, non stato business. |

Gli stati business di `orders` sono soltanto `da_gestire`, `consegnata`, `pagata` e `da_verificare`. Il servizio non conserva dati fiscali, chiusure né dettagli POS.

## Dati locali dell'applicativo

| Entità | Campi principali | Scopo |
| --- | --- | --- |
| `local_orders` e `local_order_items` | copia di `orders`, stato e snapshot | Coda e operatività della cassa. |
| `sales` | `id`, `local_unit_id`, `document_type`, `status`, `total_cents`, `fiscal_document_number`, `fiscal_emitted_at`, `rt_serial_number`, `z_number`, `original_sale_id`, `created_at` | Unica entità per vendita e documento fiscale. I riferimenti fiscali restano null prima dell'emissione. |
| `sale_orders` | `sale_id`, `local_order_id` | Collega una vendita a una o più comande dello stesso tavolo. |
| `payment_parts` | `id`, `sale_id`, `amount_cents`, `method`, `status` | Quote logiche di incasso, anche per conto separato. |
| `fiscal_closures` | `id`, `local_unit_id`, `z_number`, `closed_at`, `totals_snapshot`, `status` | Esito della chiusura giornaliera. |
| `sync_outbox` e `sync_inbox` | evento, payload, tentativi, date | Sincronizzazione affidabile con il servizio. |
| `app_settings` | chiave, valore | Configurazione locale e dispositivi. |

`sales.document_type` distingue almeno `sale` e `void`. Lo stato descrive il ciclo operativo: `aperta`, `fiscalizzata`, `da_verificare`, `annullata`. Un annullamento è una nuova riga `sales` di tipo `void`, con totale negativo e `original_sale_id` valorizzato.

Non esistono tabelle separate `fiscal_documents` o `pos_transactions`: la prima è assorbita in `sales`, la seconda non va salvata nel database.

## Journal POS locale

Gli eventi tecnici del POS sono salvati localmente in file append-only, ad esempio `pos-journal/YYYY-MM-DD.jsonl`. Ogni riga contiene identificatore evento, data/ora, `sale_id` o `payment_part_id`, importo richiesto, azione, esito e riferimento del provider se disponibile.

Non vengono mai registrati PAN, CVV o risposte carta grezze. Il journal serve a diagnosi e riconciliazione locale, non alla sincronizzazione con il servizio web.
