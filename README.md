# effdipi — vetrina

La pagina di copertina di `effdipi.it`, servita da GitHub Pages.

Tutto sta in `index.html` più il logo, `logo.png`, accanto: niente risorse da
altri siti. Si apre anche con un doppio clic per vedere com'è venuta prima di
pubblicarla.

## Com'è fatta

Il fondo è un muro di pannelli quadrati a profondità diverse. Quando il
puntatore ci passa sopra, i pannelli lì attorno si girano, vengono avanti e si
accendono del verde del marchio, poi tornano al loro posto con calma. Davanti
al muro stanno i progetti, come lastre di vetro.

I colori vengono tutti dal logo: il blu del cerchio, il verde della palma, il
bianco, il nero. Il tema chiaro è la stessa cosa vista di giorno.

Il muro lo costruisce il JavaScript: una griglia di pannelli, ognuno con la sua
profondità e il suo tono decisi da un rumore fisso sulle coordinate, così la
parete non cambia faccia a ogni ridimensionamento. Sugli schermi grandi i
pannelli si allargano invece di moltiplicarsi, per non riempire la pagina di
elementi.

Le lastre stanno su un arco rivolto verso chi guarda: quelle ai lati girano
verso il centro e stanno un filo più indietro. Anche questo si rifà da sé
quando la finestra cambia misura.

Dove il puntatore non c'è (telefono, tavoletta) il muro dondola piano da solo.
Chi ha chiesto meno movimento al sistema (`prefers-reduced-motion`) trova tutto
fermo. Senza JavaScript il muro non c'è e la pagina resta una copertina
normale, leggibile.

## Aggiungere un progetto

Copia il blocco `<li class="scheda">` dentro `index.html` e cambia icona,
indirizzo (`href`), titolo e descrizione. La griglia si riorganizza da sola e
le lastre si rimettono in fila.

Gli indirizzi da cambiare sono **due**, e vogliono lo stesso valore: quello sul
titolo e quello sul link `class="copre"`, il gemello invisibile che rende
cliccabile tutta la lastra. La lastra non può essere lei stessa un link perché
dentro ce n'è più d'uno (le sotto-sezioni), e un link dentro un link non
esiste. Allargare il link del titolo con un `::after` non funziona: il
`transform` sull'`h2` gli fa da gabbia e il riquadro si ferma al testo.

I progetti si aprono in una pagina nuova: è il `target="_blank"` sul link,
lascialo dov'è. La freccina nella pastiglia di stato lo dice a chi guarda.

## Le sotto-sezioni

Quando un progetto ha una pagina che è *sua* — la scheda di collaudo di
YachtNav, per dire — non merita una lastra a sé: sembrerebbe un altro
progetto. Sta sulla stessa lastra, in fondo, sotto una riga sottile, nel blocco
`<ul class="sotto">`. Se un progetto non ne ha, quel blocco si toglie e non
resta niente.

Ogni voce è un link vero con la sua icona e, se serve, un `<span class="a-chi">`
che dice a chi è rivolta. Stanno davanti al gemello invisibile, quindi il clic
ci arriva: il resto della lastra manda al progetto.

L'icona è un SVG con `viewBox="0 0 24 24"` e `stroke="currentColor"`: prende da
sé il colore giusto. Quella di YachtNav è il suo marchio, vedi sotto.

## Lastre col tema del progetto

Una lastra può vestirsi coi colori della sua app: si aggiunge una classe alla
`<li class="scheda">` (per esempio `tema-lovemap`) e nello stile si
ridefiniscono, solo per quella classe, le variabili del vetro (`--vetro`,
`--vetro-alto`, `--bordo`, `--bordo-vivo`, `--accento`, `--pozza`, `--testo`,
`--testo-tenue`), una volta per il tema scuro e una per il chiaro. Bordo, alone,
pastiglia e hover le seguono da soli. Nel tema chiaro l'accento va scurito
quanto basta perché il testo piccolo della pastiglia resti leggibile.

LoveMap usa il blu notte e il rosa del cuore della sua schermata iniziale, e il
lilla delle date. È privata: dietro il link c'è una schermata di accesso.

Ogni progetto vive dove gli pare: un sottodominio può puntare a un server
diverso da un altro. Questa pagina è solo l'elenco.

## Il logo

`logo.png` è il cerchio di Keep Palm, ritagliato dall'immagine originale su
fondo nero: 512×512, fuori dal disco è trasparente. Sta in testata, sopra il
nome, ed è anche l'icona della scheda del browser.

Più piccolo di 6rem in testata non va messo: la scritta dentro il cerchio
smette di leggersi. Per cambiarlo basta sostituire il file con un altro PNG
quadrato con lo stesso nome.

## Il marchio di YachtNav

Un'ancora con due onde di segnale che escono dall'anello: la barca che parla.
Niente nome dentro, apposta — il nome può cambiare, il segno resta.

Sta in `marchi/yachtnav/`:

- `segno.svg` — solo il tratto, monocromatico, `currentColor`. Va incollato
  dentro la pagina (non come `<img>`, se no `currentColor` diventa nero): così
  prende il colore del testo attorno. È quello della scheda qui in vetrina.
- `icona.svg` — il tratto bianco su piastrella blu, onde azzurre. È l'icona
  vera: scheda del browser, schermata di un telefono, app.
- `icona-512.png` — la stessa, in PNG trasparente fuori dagli angoli, per chi
  l'SVG non lo legge.
- `icona-piena.svg` e `icona-piena-512.png` — piastrella piena, senza angoli
  arrotondati, col segno un po' più piccolo. Serve dove la forma la ritaglia
  il sistema: icona "maskable" di Android e schermata Home di iPhone. Lì gli
  angoli trasparenti di `icona.svg` diventerebbero neri.
- `badge.svg` — il segno bianco su vuoto, tratto più spesso. È il badge delle
  notifiche nella barra di stato di Android, che usa solo la trasparenza come
  maschera: una piastrella piena verrebbe un quadrato bianco.

L'app YachtNav (repo `yachtnav-manager`, cartella `client/public`) ha le copie
già pronte di tutti questi, alle misure che le servono.

Le onde sono archi concentrici all'anello (centro 12,5), con lo stesso stacco
dall'anello e fra loro. Se si ritocca il disegno, i PNG vanno rigenerati dagli
SVG, non ridisegnati a parte: si fa con Edge senza finestra,

    msedge --headless=new --default-background-color=00000000 --window-size=512,512 --screenshot=icona-512.png icona.svg

Sempre a 512, e poi si riduce. Edge ha una larghezza minima di finestra: sotto
i 500 px circa l'SVG viene centrato in una finestra più larga e la cattura ne
prende solo la striscia di sinistra.

Colori: blu `#0b2a44`, bianco `#f2f7fb`, azzurro `#4fd3e6`.

## Pubblicare

Un commit su `main`. GitHub Pages ricostruisce da sé in un minuto.

Il file `CNAME` contiene il dominio: non cancellarlo, è quello che dice a
GitHub di rispondere su `effdipi.it` invece che su `github.io`.
