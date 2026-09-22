# ESP1-Monet — canale aggiornamenti

Questo repository contiene **solo** i pacchetti di aggiornamento `.emu` di
ESP1-Monet e il `manifest.json` che li descrive. Il codice sorgente sta altrove.

Il frontend del gateway legge `manifest.json` da `raw.githubusercontent.com`
quando l'utente premedel tasto "Verifica ora", confronta la versione con quella
in esecuzione e, su conferma, scarica il `.emu` e lo carica sul dispositivo.

## Cosa NON garantisce questo repo

- **Il campo `sha256` del manifest non è verificato dal browser.** La pagina del
  gateway è servita in HTTP semplice, dove `crypto.subtle` non esiste: l'hash è
  pubblicato per la verifica manuale, non applicato automaticamente.
  L'integrità effettiva è garantita dagli hash per sezione contenuti
  nell'header EMO2 del pacchetto, verificati dal dispositivo prima di
  confermare l'immagine.
- **Nessuna firma crittografica.** Chi può pushare su questo repository può far
  installare qualunque firmware sui dispositivi che premono "Verifica ora".

## Contenuto

- `manifest.json` — versione corrente e precedente, con note di release
- `firmware/` — al massimo due pacchetti: quello corrente e il precedente

Pubblicato da `publish-ota.ps1` nel repo principale. Non modificare a mano.
