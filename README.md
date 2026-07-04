# Sito ASD Nome Squadra

Sito statico generato con [Hugo](https://gohugo.io), pensato per essere aggiornato modificando
solo dei file di dati, senza toccare mai il codice.

## Struttura del sito

- `/rosa/` — giocatori e staff
- `/campionato-in-corso/` — classifica, prossima partita, risultati recenti
- `/archivio/` — stagioni passate
- `/storia/` — cronologia e bacheca

## Come aggiornare i contenuti

Tutti i contenuti che cambiano spesso sono in **file di dati** dentro la cartella `data/`,
in formato YAML (testo semplice, facile da modificare anche da telefono su GitHub).

| File                  | Cosa contiene                                  |
|------------------------|------------------------------------------------|
| `data/rosa.yaml`       | Elenco giocatori e staff tecnico                |
| `data/campionato.yaml` | Classifica, prossima partita, risultati recenti |
| `data/archivio.yaml`   | Stagioni concluse, una voce per stagione        |
| `data/storia.yaml`     | Eventi storici e bacheca trofei                 |

Per aggiornare, ad esempio, la classifica dopo una giornata:

1. Apri `data/campionato.yaml` su GitHub (tasto matita in alto a destra sul file)
2. Modifica i numeri della classifica e aggiungi il risultato in `risultatiRecenti`
3. Aggiorna `prossimaPartita` con il prossimo turno
4. Salva ("Commit changes"): il sito si aggiorna da solo in 1-2 minuti

Le impostazioni generali (nome squadra, categoria, girone, campo, stagione corrente)
sono in cima al file `hugo.yaml`, sotto `params:`.

## Come funziona la pubblicazione

Ogni volta che salvi una modifica su GitHub (branch `main`), il file
`.github/workflows/hugo.yml` genera automaticamente il sito e lo pubblica: non serve
installare nulla né lanciare comandi.

### Primo setup (una tantum)

1. Crea un account su [github.com](https://github.com) se non lo hai già
2. Crea un nuovo repository (es. `asd-nome-squadra`) e carica tutti i file di questo
   progetto (trascinali nell'interfaccia web di GitHub, oppure usa `git push` se preferisci
   la riga di comando)
3. Nel repository vai su **Settings → Pages** e imposta "Source" su **GitHub Actions**
4. Vai su **Settings → Actions → General**, sezione "Workflow permissions", e seleziona
   "Read and write permissions"
5. Dopo il primo push, vai sulla scheda **Actions**: vedrai il sito costruirsi. A fine
   processo, l'indirizzo del sito comparirà in **Settings → Pages**
   (sarà tipo `https://tuonomeutente.github.io/asd-nome-squadra/`)

Se in futuro vuoi un dominio tuo (es. `asdnomesquadra.it`), lo colleghi sempre da
**Settings → Pages**, senza cambiare nulla nel codice.

## Come provare il sito sul tuo PC (opzionale)

Se vuoi vedere le modifiche prima di pubblicarle:

1. Installa Hugo (versione "extended"): [istruzioni ufficiali](https://gohugo.io/installation/)
2. Da terminale, dentro la cartella del progetto: `hugo server`
3. Apri `http://localhost:1313` nel browser

## Personalizzazione grafica

Tutto lo stile è in `static/css/main.css`, con i colori definiti in cima al file
(`:root`). Se vuoi cambiare i colori della squadra, modifica queste righe:

```css
--verde: #14532D;      /* colore principale */
--oro: #C99A3E;         /* accenti, dettagli */
--bordeaux: #7A2E2E;    /* evidenze secondarie */
```
