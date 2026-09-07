# effdipi — vetrina

La pagina di copertina di `effdipi.it`, servita da GitHub Pages.

Un file solo, `index.html`, senza risorse esterne: si apre anche con un doppio
clic per vedere com'è venuta prima di pubblicarla.

## Com'è fatta

La pagina è una stanza in prospettiva: un pavimento a griglia che sfugge verso
l'orizzonte e i progetti come lastre di vetro appoggiate lì dentro. Muovendo il
puntatore la stanza ruota di qualche grado e la luce scorre sul vetro; dove il
puntatore non c'è (telefono, tavoletta) dondola piano da sola.

È tutto CSS 3D più una ventina di righe di JavaScript, che servono a due cose:
seguire il puntatore e mettere le lastre su un arco rivolto verso chi guarda —
quelle ai lati girano verso il centro e stanno un filo più indietro. Il calcolo
si rifà da sé quando la finestra cambia misura.

Chi ha chiesto meno movimento al sistema (`prefers-reduced-motion`) trova una
stanza ferma, e la pagina resta leggibile anche senza JavaScript.

## Aggiungere un progetto

Copia il blocco `<li class="scheda">` dentro `index.html` e cambia icona,
indirizzo, titolo e descrizione. La griglia si riorganizza da sola e le lastre
si rimettono in fila nella vetrina.

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
