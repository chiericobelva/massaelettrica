# massaelettrica.net

Presskit di Affinità. Sito statico: HTML + CSS + JS, nessun backend.

## Struttura

```
index.html            la home (music, radio, education, community, bio, press, contact)
audio/                una cartella per release: mp3 + cover.jpg (+ releases.json generato)
img/                  logo.png, foto, copertine, og-image.jpg (1200x630)
files/                l'archivio navigabile (stile Death Grips)
  index.html          il file browser — non toccare
  manifest.json       generato da build-manifest.py — non modificare a mano
  press/              PDF del presskit (linkati anche dalla home)
  releases/           cartelle per release
  flyers/             flyer e grafiche
build-manifest.py     aggiorna drive e musica (lancialo dopo ogni modifica)
```

## Regole

- Tutto quello che sta in `files/` è pubblico.
- Niente DJ mix con brani di altri artisti, niente documenti con dati personali.
- Nomi dei file: minuscole, trattini, niente spazi né accenti.
