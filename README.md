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

## Logo e immagini

- Logo: `img/logo.png` (PNG trasparente, bianco). Senza file compare la scritta AFFINITÀ.
- Foto della sezione Images: mettile in `img/` e aggiungi una riga nella lista `IMAGES` in `index.html`.

## Aggiungere musica (album, EP, singoli)

1. Crea una cartella in `audio/` per la release, es. `audio/massa-elettrica/`
2. Dentro metti gli mp3 (il numero davanti decide l'ordine: `01-titolo.mp3`, `02-titolo.mp3`) e la copertina `cover.jpg` (quadrata, ~1000x1000)
3. Dal terminale, nella cartella del sito: `python build-manifest.py`
   - per una cartella nuova ti chiede tipo (album / EP / singolo), titolo, anno, etichetta, link, descrizione, BPM
   - per ogni traccia nuova ti chiede titolo e BPM
   - Invio = accetti il valore proposto tra [parentesi]
   - tracce o cartelle cancellate spariscono da sole dal sito
4. GitHub Desktop → Commit → Push

Per cambiare l'ordine delle tracce (anche dopo averla già caricata):
`python build-manifest.py --order massa-elettrica` → ti mostra le tracce numerate, scrivi il nuovo ordine (es. `3 1 2 4`) e rinomina i file da solo.
In alternativa rinomina tu i file cambiando il numero davanti: titolo e BPM non si perdono.

Per correggere le info di una release già caricata:
`python build-manifest.py --edit massa-elettrica`

Le info finiscono in `audio/releases.json` (generato dallo script: non serve toccarlo a mano).

## Aggiungere file all'archivio

1. Metti i file nella cartella giusta dentro `files/`
2. Dal terminale, nella cartella del sito: `python3 build-manifest.py`
3. GitHub Desktop → Commit → Push. Porkbun aggiorna il sito da solo.

## Provare in locale

In VS Code: tasto destro su `index.html` → **Open with Live Server**.
Oppure dal terminale: `python3 -m http.server` e apri http://localhost:8000

Il file browser non funziona aprendo il file con doppio clic: serve un server locale.

## Regole

- Tutto quello che sta in `files/` è pubblico.
- Niente DJ mix con brani di altri artisti, niente documenti con dati personali.
- Nomi dei file: minuscole, trattini, niente spazi né accenti.
