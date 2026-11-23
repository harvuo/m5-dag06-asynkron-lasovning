# Tidslinje: rita vad som händer

Välj snutt 5 och snutt 10. Fyll i tabellerna steg för steg. Skriv vad som ligger i varje del **efter** varje steg.

Förklaring:

- **Anropsstacken** är den kod som körs just nu.
- **Microtask-kön** är promise-callbacks som väntar på att få köra.
- **Task-kön** är timer-callbacks och liknande som väntar på att få köra.
- Regel: när stacken är tom körs först ALLA microtasks, sedan EN task, sedan tomma microtasks igen, och så vidare.

## Snutt 5

| Steg | Vad händer                          | Stacken     | Microtask-kön | Task-kön   | Utskrift hittills |
| ---- | ----------------------------------- | ----------- | ------------- | ---------- | ----------------- |
| 1    | setTimeout anropas                  |             |               | setTimeout |                   |
| 2    | Promise.resolve().then(...) anropas |             | Promise       |            |                   |
| 3    | console.log("sync")                 | console.log |               |            | sync              |
| 4    | Stacken tom: vad körs först?        |             |               |            | promise           |
| 5    | Nästa                               |             |               |            | timeout           |

## Snutt 10

| Steg | Vad händer                       | Stacken          | Microtask-kön             | Task-kön                    | Utskrift hittills |
| ---- | -------------------------------- | ---------------- | ------------------------- | --------------------------- | ----------------- |
|      | console.log("1")                 | console.log("1") |                           |                             | 1                 |
| 2    | första setTimeout                |                  |                           | första setTimeout           |                   |
| 3    | Promise.resolve().then(3)        |                  | Promise.resolve().then(3) |                             |                   |
| 4    | andra setTimeout                 |                  |                           | första och andra setTimeout |                   |
| 5    | console.log("6")                 | console.log("6") |                           |                             | 6                 |
| 6    | stacken tom, microtask-kön först |                  |                           |                             | 3                 |
| 7    | första tasken                    |                  |                           |                             | 2                 |
| 8    | andra tasken                     |                  |                           |                             | 4                 |
| 9    | microtask 5                      |                  |                           |                             | 5                 |

## Min förklaring i en mening

Varför kommer en promise-callback före en timer med 0 ms?

- Microtask-kön (där promise ligger) har högre prioritet än task-kön (där timern ligger). Även om timern är satt till 0 så läggs den i task-kön.
