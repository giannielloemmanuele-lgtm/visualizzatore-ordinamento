# Visualizzatore di algoritmi di ordinamento

Strumento interattivo che mostra **passo dopo passo** come lavorano i principali algoritmi di ordinamento, con gli stati intermedi reali dell'array — niente salti al risultato finale.

**▶ Demo live:** https://giannielloemmanuele-lgtm.github.io/visualizzatore-ordinamento

Progetto nato come supporto allo studio di *Strutture dati e algoritmi* e realizzato in JavaScript puro, senza framework né librerie esterne.

---

## Funzionalità

- **Sei algoritmi**: bubble, insertion, selection, merge, quick e heap sort.
- **Esecuzione passo-passo**: avanti e indietro a mano (frecce ← →), Play/Pausa e velocità regolabile.
- **Colorazione delle regioni di partition** nel quicksort (minori / pivot / maggiori) per vedere come si forma la partizione.
- **Vista ad albero binario sincronizzata** nell'heap sort: nodo attivo, figli confrontati e scambi del *siftdown* evidenziati insieme.
- **Contatori** di confronti e spostamenti in tempo reale.
- **Tabella di complessità** (caso migliore / medio / peggiore, spazio, stabilità) per ogni algoritmo.
- Array e dimensione **personalizzabili**.
- Interfaccia **responsive** e accessibile: navigazione da tastiera e supporto a `prefers-reduced-motion`.

---

## Algoritmi inclusi

| Algoritmo      | Migliore   | Medio      | Peggiore   | Spazio   | Stabile |
|----------------|------------|------------|------------|----------|---------|
| Bubble sort    | O(n)       | O(n²)      | O(n²)      | O(1)     | Sì      |
| Insertion sort | O(n)       | O(n²)      | O(n²)      | O(1)     | Sì      |
| Selection sort | O(n²)      | O(n²)      | O(n²)      | O(1)     | No      |
| Merge sort     | O(n log n) | O(n log n) | O(n log n) | O(n)     | Sì      |
| Quick sort     | O(n log n) | O(n log n) | O(n²)      | O(log n) | No      |
| Heap sort      | O(n log n) | O(n log n) | O(n log n) | O(1)     | No      |

---

## Come funziona (architettura)

Il calcolo è **separato dall'animazione**. Ogni algoritmo non disegna nulla: registra una sequenza di *frame*, dove ogni frame è uno snapshot completo dello stato:

```
frame = { array, evidenziazioni, descrizione, confronti, spostamenti }
```

Il player si limita a scorrere questa lista. Questo approccio rende banali tre cose che altrimenti sarebbero complicate:

- **passo indietro** gratuito (basta tornare al frame precedente),
- **scrubbing** in qualunque punto dell'esecuzione,
- stato sempre **immutabile e ispezionabile**.

È lo stesso pattern usato dai tool di debugging "time-travel".

---

## Tecnologie

- HTML5
- CSS3 (custom properties, layout flessibile)
- JavaScript (ES6+), vanilla — **zero dipendenze**

---

## Eseguire in locale

Non serve installare niente: basta aprire `index.html` in un browser.

```bash
git clone https://github.com/giannielloemmanuele-lgtm/visualizzatore-ordinamento.git
cd visualizzatore-ordinamento
# apri index.html con doppio click, oppure:
# python3 -m http.server   → poi vai su http://localhost:8000
```

---

## Licenza

Distribuito con licenza MIT — libero utilizzo, modifica e condivisione.
