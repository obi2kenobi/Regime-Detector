# BUG-G4 — Regime-Detector v2.1 — candidati

Analisi sola (M-031.63b.1). Sorgente: regime_detektor_v2.1.pine + regime_detektor.pine (v2.0).

CANDIDATO-1: regime_detektor_v2.1.pine:536,539 — ogni `longEntry`/`shortEntry` chiama `label.new(...)` senza mai eliminare la label precedente. Il parametro massimo (max_labels_count=500, riga 9) è raggiunto dopo ~500 entry; oltre quel limite TradingView blocca/rifiuta' le nuove label (e può emettere errore sullo script), causando perdita di segnali visivi e comportamento indefinito. Grave: crash/degrado dell'indicatore in sessione lunga.

CANDIDATO-2: regime_detektor_v2.1.pine:169-173 — `fpCVD` è `var float fpCVD = 0.0` accumulato a ogni barra (`fpCVD := fpCVD + fpDelta`) senza reset, senza rebasing e senza guard contro delta stale; `fpCVD_sma5 = ta.sma(fpCVD, 5)` e `fpCVDrising/falling` derivano da un cumulo che cresce silenziosamente e diventa non-indicativo dopo migliaia di barre (e tra sessioni/replay). Logica errata su un pilastro di conferma footprint: conferma LONG/SHORT sbagliata → confidence errata. Perdita di accuratezza strutturale.

Nota: altri candidati scartati (vedi Rapporto nel mandato): tema_slope_pct di riga 254 — divisione per tema[1] non nullo in pratica; sqzVal riga ~268 — logica strana ma non grave; indicator assenza di test locali.
