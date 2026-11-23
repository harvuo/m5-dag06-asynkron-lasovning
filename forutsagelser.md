# Förutsägelser: asynkron kod

Regler:

1. Titta på snutten i `snuttar/sNN.js` (eller på sidan `index.html`). **Kör den inte än.**
2. Skriv din gissning i tabellen: utskrifterna i den ordning du tror att de kommer, separerade med `|`.
3. Kör snutten (knappen _Kör_). Skriv vad som faktiskt skrevs ut.
4. Hade du rätt? Skriv en regel med egna ord för varje snutt du gissade fel på.

| Snutt | Min gissning (i ordning)                         | Faktisk utskrift                                 | Rätt? | Min regel om jag hade fel                                                         |
| ----- | ------------------------------------------------ | ------------------------------------------------ | ----- | --------------------------------------------------------------------------------- |
| 1     | 1, 2, 3                                          | 1, 2, 3                                          | Rätt  |                                                                                   |
| 2     | A, C, B                                          | A, C, B                                          | Rätt  |                                                                                   |
| 3     | start, noll, kort, lång                          | start, noll, kort, lång                          | Rätt  |                                                                                   |
| 4     | inuti promise, efter, then: klart                | inuti promise, efter, then: klart                | Rätt  |                                                                                   |
| 5     | sync, promise, timeout                           | sync, promise, timeout                           | Rätt  |                                                                                   |
| 6     | först?, 6, 7                                     | först?, 6, 7                                     | Rätt  |                                                                                   |
| 7     | fel: slut på mjölk, städar                       | fel: slut på mjölk, städar                       | Rätt  |                                                                                   |
| 8     | beställer, sätter mig, bullen klar, kaffet klart | beställer, sätter mig, bullen klar, kaffet klart | Rätt  |                                                                                   |
| 9     | väntar på båda, bulle, kaffe                     | väntar på båda, ["kaffe","bulle"]                | Fel   | Promise.all samlar ihop alla värden (i det här fallet av typen string) i en array |
| 10    | 1, 6, 3, 2, 4, 5                                 | 1, 6, 3, 2, 4, 5                                 | Rätt  |                                                                                   |
| 11    | c, ab                                            | c, ab                                            | Rätt  | Kunde inte reda ut den nya promisen utan fick ta hjälp av AI för att gissa rätt   |

## Tre meningar med egna ord

1. JavaScript väntar inte på `setTimeout`, utan lägger den i task-kön för väntan på exekvering.
2. En promise har tre tillstånd: pending (pågår), fullfilled(klar med lyckat resultat) och rejected (misslyckat eller fel).
3. `then` körs alltid efter fullfilled (först exekveras dock den synkrona koden i stacken).
