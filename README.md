# effdipi — vetrina

La pagina di copertina di `effdipi.it`, servita da GitHub Pages.

Un file solo, `index.html`, senza risorse esterne: si apre anche con un doppio
clic per vedere com'è venuta prima di pubblicarla.

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
sé il colore giusto. Quella della barca è il marchio di YachtNav Manager.

Ogni progetto vive dove gli pare: un sottodominio può puntare a un server
diverso da un altro. Questa pagina è solo l'elenco.

## Il logo

Nell'intestazione c'è ancora un **segnaposto**: la cornice tratteggiata. Quando
c'è il logo effdipi vero, si sostituisce quel singolo `<svg class="segnaposto">`
— stesse regole dell'icona qui sopra — e si toglie la classe.

## Pubblicare

Un commit su `main`. GitHub Pages ricostruisce da sé in un minuto.

Il file `CNAME` contiene il dominio: non cancellarlo, è quello che dice a
GitHub di rispondere su `effdipi.it` invece che su `github.io`.
