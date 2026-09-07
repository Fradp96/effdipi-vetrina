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

I progetti si aprono in una pagina nuova: è il `target="_blank"` sul link,
lascialo dov'è. La freccina nella pastiglia di stato lo dice a chi guarda.

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
