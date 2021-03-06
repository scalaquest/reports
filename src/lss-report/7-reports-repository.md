# Il repository dedicato alla documentazione

Nelle prime fasi del progetto, il repository principale conteneva un ulteriore
sotto-progetto denominato `reports`. All'interno di questo si sono andati a
porre i report di LSS e PPS, oltre ai documenti a margine, come lo Sprint
Overview. La scelta di utilizzare un sotto-progetto è stata dettata dalla
necessità di dare una struttura al codice, e alla possilità di utilizzare il
plugin `spotless` di Gradle anche per lo styling del Markdown, grazie ai task
`:spotlessCheck` per il controllo sul rispetto delle regole di stile, e
`:spotlessApply` per l'applicazione automatica delle stesse.

Con l'aumentare della complessità di progetto, però, si è deciso di modificare
tale infrastruttura. Il sottoprogetto `reports` è stato quindi migrato in un
repository del tutto scollegato da quello principale, denominato
[**scalaquest/Reports**](https://github.com/scalaquest/Reports). La scelta è
stata dettata anche allo scopo di costruire un'infrastruttura più complessa
attorno ai report stessi.

Reports è ancora una volta un progetto Gradle, con abilitato il plugin
`spotless` per lo styling (con una configurazione dedicata per il Markdown), e i
sorgenti della documentazione (in Markdown) contenuti all'interno della
directory `/src`. Il modello di sviluppo adottato è ancora una volta GitFlow, in
maniera del tutto equivalente nelle modalità a quelle del repository principale.

## Continuous Integration

A guardia dei branch stabili, è stato posto un workflow di CI, definito nel file
`ci.yml` che va ad applicare `:spotlessCheck`, e fallisce nel caso in cui non
vengano rispettate determinate regole di stile (come la lunghezza della riga
posta a 80 caratteri).

## Continuous Delivery e Deployment

Assolutamente peculiari sono invece i workflow di delivery e deployment. I file
Markdown si prestano infatti molto bene ad essere convertiti in altri formati,
utilizzando i tool adatti. Si è deciso quindi di fornire, per una consultazione
più agevole, i report nei formati LaTeX PDF e in una versione web, autogenerati
ad ogni nuova release. Ciò è stato possibile grazie a **Pandoc**, un tool che
permette la conversione di file testuali in una moltitudine di formati
differenti.

Con queste specifiche, si sono andati quindi a definire un workflow **Release**
e uno **Prerelease**, lanciati con le stesse modalità descritte per il
repository principale.

### Il workflow Release

Questo, definito nel file `release.yml`, viene lanciato alla chiusura dei branch
`release/X.Y.Z`. Effettua le seguenti operazioni:

1. Inferisce il nome del tag da associare alla release, a partire del nome del
   branch di provenienza, e crea un annotated tag in corrispondenza del commit
   di merge;

2. Genera una release GitHub nell'apposita sezione Releases. Tale release
   contiene i report di PPS, LSS e un file di appendice (oltre al file
   `README.md`), a partire dai file Markdown, tramite un'immagine Docker con
   integrata un'installazione Pandoc;

3. Genera una versione HTML dei report e del file di appendice, a partire dai
   file Markdown, tramite un'immagine Docker con integrata un'installazione
   Pandoc. Posiziona quindi tali file all'interno del branch `gh-pages`, e
   effettua automaticamente un commit su questo branch, integrando la versione
   aggiornata della documentazione. In questo modo, questa sarà accessibile
   dallo spazio web del progetto;

4. Una volta completati i punti 2 e 3, viene generata una pull request dal
   `main`, diretta al branch `dev`. Ciò permette di integrare nel branch di
   sviluppo le eventuali modifiche occorse all'interno dei branch
   `release/X.Y.Z`. Su di questi infatti si è delle volte agito con delle
   modifiche minori.

### Il workflow Prerelease

Questo, definito nel file `prerelease.yml` viene lanciato ad ogni push nel
branch `dev`, e genera delle release marcate con il flag prerelease, con numero
di versione generato automaticamente tramite
[`git-sensitive-semantic-versioning`](https://github.com/DanySK/git-sensitive-semantic-versioning-gradle-plugin/blob/master/src/main/kotlin/org/danilopianini/gradle/gitsemver/GitSemVer.kt).
Effettua le seguenti operazioni:

1. Inferisce il nome del tag da associare alla prerelease, in modo del tutto
   automatico, tramite il plugin Gradle
   [`git-sensitive-semantic-versioning`](https://github.com/DanySK/git-sensitive-semantic-versioning-gradle-plugin/blob/master/src/main/kotlin/org/danilopianini/gradle/gitsemver/GitSemVer.kt).
   Un task personalizzato permette di estrarre il numero di versione e salvarlo
   su un file; il contenuto viene quindi prelevato, salvato come variabile
   d'ambiente, e viene creato un lightweight tag in corrispondenza del commit di
   merge;

2. Genera una release GitHub nell'apposita sezione Releases, con il flag
   prerelease abilitato. Tale release contiene i report di PPS, LSS e un file di
   appendice (oltre al file `README.md`), a partire dai file Markdown, tramite
   un'immagine Docker con integrata un'installazione Pandoc.

## Configurazione di Pandoc

Per poter personalizzare l'output generato da Pandoc, sono stati utilizzati dei
file di configurazione, accessibli dalla directory `/pandoc`. All'interno di
questa si è andato a configurare il template LaTeX nativo di Pandoc, allo scopo
di adattarlo al progetto. Per quanto riguarda il template HTML, invece, si è
creato e utilizzato un template custom, a partire da un fork del template
[**ashki23/PandocBootstrap**](https://github.com/ashki23/pandoc-bootstrap). Il
template di progetto è accessibile al repository
[**scalaquest/PandocBootstrap**](https://github.com/scalaquest/PandocBootstrap).
Questo è stato posto come submodule del repository _scalaquest/Report_, così da
avere a disposizione il template durante la generazione dei report in CI.
