# BUG-G5 — Regime-Detector v2.1 — bug gravi (M-032.63b)

Metodo: lettura statica di `regime_detektor_v2.1.pine` (773 righe). Repo senza suite di test e senza compilatore Pine locale (NO-TEST): nessuna esecuzione, verifica solo sul codice.
Premessa del mandato («repo senza codice») non vera: il repo contiene due script Pine v6 (`regime_detektor.pine`, `regime_detektor_v2.1.pine`).

## BUG-1 — label accumulate (gravità alta)
Dove: `regime_detektor_v2.1.pine:536` e `:539`; limite `max_labels_count=500` a riga 9.
Prova: ogni `longEntry` e `shortEntry` esegue `label.new(...)` senza mai eliminare la label precedente. Su grafici lunghi il numero di label cresce fino al limite di 500; oltre, i segnali visivi spariscono o il comportamento non è definito.
Correzione proposta (non applicata, file fuori perimetro): tenere `var label longLabel` / `var label shortLabel`, eliminare la precedente con `label.delete` prima di ricrearla.

## BUG-2 — fpCVD accumulatore illimitato (gravità alta)
Dove: `regime_detektor_v2.1.pine:169-171`.
Prova: `var float fpCVD = 0.0` somma `fpDelta` a ogni barra dall'inizio del grafico (`fpCVD := ... fpCVD + fpDelta`) senza reset né finestra. La media `fpCVD_sma5` e i booleani `fpCVDrising` / `fpCVDfalling` (righe 172-173) confrontano un totale cumulativo di tutta la storia: il confronto dipende dal punto di partenza del grafico e perde significato sulle barre recenti. Entra in `fpShortConfirmCount` / `fpLongConfirmCount` (righe 177, 180), quindi nella conferma footprint e nel boost (se abilitato).
Correzione proposta (non applicata): finestra mobile, ad esempio `ta.sum(nz(fpDelta), 100)`, con il resto invariato.

## Non verificato
- Esistenza e firma di `request.footprint()` e del tipo `footprint` (righe 121-122): non verificabili senza Pine Editor di TradingView con piano Premium/Ultimate.
- Nessun altro bug classificato come grave: non è stata eseguita una revisione completa delle 773 righe oltre i punti sopra.

## Nota di riscontro
Gli stessi due difetti sono già stati corretti sul ramo `fix/g4-2026-11` (commit 786eae4 e c8f39f8, documentati in BUG-G4). Il ramo `fix/g5-2026-11` non li contiene.
