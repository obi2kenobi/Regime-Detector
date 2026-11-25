# BUG-G4 — Regime-Detector v2.1 — correzioni (M-031.63b.2)

## BUG-1
Dove: regime_detektor_v2.1.pine:536,539 (label.new senza delete)
Gravità: alta — raggiunta max_labels_count=500 (riga 9), segnali visivi persi / comportamento indefinito
Prova: lettura codice — ogni longEntry/shortEntry crea label nuova mai eliminata. Repo senza test Pine (NO-TEST).
Correzione: 786eae4 — tenere var longLabel/shortLabel; deletare la precedente e ricreare a ogni entry.
Test: repo senza suite (esegui-test-repo.sh → NO-TEST); lettura statica OK.

## BUG-2
Dove: regime_detektor_v2.1.pine:169-173 (fpCVD accumulatore illimitato)
Gravità: alta — conferma footprint LONG/SHORT sbagliata, confidence errata
Prova: lettura codice — fpCVD cresceva senza reset/rebasing; SMA di 5 e bool derivate non-indicative. Repo senza test Pine (NO-TEST).
Correzione: c8f39f8 — sostituzione di `var float` cumulativo con `ta.sum(nz(fpDelta), 100)` (finestra mobile 100 barre); SMA5 e bool invariati.
Test: repo senza suite (esegui-test-repo.sh → NO-TEST); lettura statica OK.
