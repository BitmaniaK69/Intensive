# Playerboard V25 - Panel Update Plan

Questo documento descrive gli interventi necessari per aggiornare la playerboard da V24 a V25. Ogni sezione corrisponde a un pannello logico della board: non solo un blocco di testo, ma un'area funzionale che raggruppa titoli, icone, valori, reminder e micro-testi.

Riferimenti principali:

- `PLAYERBOARD_V25_NOTES.md`
- `RulesV25-Final.md`
- esempio V24: `OdaNobunaga (Medium).png`

---

## 1) Playing Round

### Funzione del pannello

Questo pannello deve spiegare il flusso base del turno. In V25 il flusso e' cambiato: non conviene piu' dividere il turno in `Beginning / Within the Turn / Optional / End of the Turn`, perche' alcune azioni non sono piu' semplicemente "optional" e `Collect Resources` e' una fase separata.

### Contenuto consigliato V25

```text
PLAYING ROUND

BEGINNING OF TURN
Refill to 3 Cards
Visit Emperor before action

ACTIVE TURN
Play Cards
Build / Protect
Reveal
Fix Errors
Diplomacy

COLLECT RESOURCES
Gain Koku
Keep up to K5

END OF TURN
Refill to 3 Cards
Pass Turn
```

### Cosa cambiare dalla V24

- `Draw up to 3 Cards` diventa `Refill to 3 Cards`.
- `Within the Turn` diventa `Active Turn`.
- `Optional` va rimosso come fase separata.
- `Collect the Resources and Pass the Turn` va separato in due momenti: `Collect Resources` e poi `End of Turn`.
- `Build Castles, Capitals or other buildings` va sostituito con un reminder piu' semplice: `Build / Protect` oppure `Build & Protect`.
- `Visit the Emperor` resta nel pannello, ma va spostato nel `Beginning of Turn` e indicato come prima finestra utile: `Visit Emperor before action`.

### Cosa puo' restare

- Il pannello resta necessario.
- La struttura a flusso con frecce puo' restare.
- Le icone di fase possono restare se non aumentano la confusione.

---

## 2) Resource Counting / Koku Income

### Funzione del pannello

Questo pannello spiega come si guadagna Koku nella fase `Collect Resources`. Deve essere leggibile a colpo d'occhio e deve usare termini V25: `Zone`, `Imperial Zone`, `Market`, `Koku`.

### Contenuto consigliato V25

```text
Koku Income

Base income: +K1
Market built: +K1
Each Zone you control: +K1
Each connected Imperial Zone: +K1

Max +K5 per counting
```

Versione piu' compatta:

```text
Koku Income
Base: +K1
Market: +K1
Each Zone: +K1
Each connected Imperial Zone: +K1
Max +K5
```

### Cosa cambiare dalla V24

- Titolo `Resource Counting (Koku)` puo' diventare `Koku Income` o `Collect Resources (Koku)`.
- `Every counting` diventa `Base income` oppure `Base`.
- `With Market built` diventa `Market built` oppure `Market`.
- `Every Zone conquered` diventa `Each Zone you control`.
- `per Central controlled` diventa `Each connected Imperial Zone`.
- `Koku gained at the end of the round` diventa `Gain during Collect Resources` oppure si rimuove se il pannello Playing Round gia' mostra la fase.

### Cosa puo' restare

- Il pannello resta necessario.
- La logica visuale riga-per-riga con icona `+K1` funziona bene.
- Il limite `5 max` resta corretto, ma deve essere chiaro se indica il massimo guadagno dal conteggio, il massimo conservabile, o entrambi. In V25 entrambi i concetti sono `5`, quindi idealmente:
  - qui: `Max +K5 per counting`
  - nel pannello riserva: `Store up to K5`

---

## 3) Koku Resource Reserve

### Funzione del pannello

Questo pannello e' la riserva fisica del Koku del giocatore. Deve comunicare due cose: quanti Koku si possono tenere e quanto costa rivelare una carta.

### Contenuto consigliato V25

```text
Koku Reserve

Store up to K5
Pay K3 to Reveal
```

Versione ultra-compatta:

```text
Koku Reserve
Max K5
Reveal: K3
```

### Cosa cambiare dalla V24

- Titolo `Koku Resource Reserve` puo' diventare `Koku Reserve`.
- Il valore `9 max` va cambiato in `5 max` o `Max K5`.
- La riserva grafica dovrebbe mostrare 5 spazi effettivi, oppure mantenere una grafica decorativa ma con un'indicazione chiarissima `Max K5`.
- `Keep your reserved Koku safely stored here` e' troppo descrittivo: meglio rimuoverlo o sostituirlo con `Store up to K5`.
- Il costo di reveal resta `K3`, ma va scritto come `Pay K3 to Reveal` o `Reveal: K3`.

### Cosa puo' restare

- Il pannello resta necessario.
- Il reminder per `Reveal` vicino alla riserva e' corretto.
- La scelta grafica con spazi tratteggiati puo' restare se viene aggiornata al limite V25.

---

## 4) Protection & Building

### Funzione del pannello

Questo pannello sostituisce il vecchio `Build and Protections Costs`. Deve spiegare in modo diretto la catena V25: converti Koku in Protection token, piazzi Protection sulle carte, poi converti le Protection piazzate in Market o Castle. Infine, 3 Castle formano una Capital.

`Build & Fortify` come titolo e' tematico ma non abbastanza chiaro da solo. Per la playerboard e' meglio un titolo piu' esplicito.

### Titolo consigliato

```text
Protection & Building
```

Alternative accettabili:

```text
Build with Protection
```

```text
Protection Builds
```

### Contenuto consigliato V25

```text
Protection & Building

K2 -> 1 Protection
1 Protection -> Protect 1 card
2 Protection -> Market
3 Protection -> Castle
3 Castles -> Capital
Capital -> Imperial Summons
```

Versione con mini-spiegazione:

```text
Protection & Building
Koku -> Protection -> Buildings

K2 -> 1 Protection
1 Protection -> Protect 1 card
2 Protection -> Market
3 Protection -> Castle
3 Castles -> Capital
Capital -> Imperial Summons
```

### Cosa cambiare dalla V24

- `Build and Protections Costs` va sostituito.
- `2 Koku -> Protection Tokens` resta come concetto, ma va scritto in notazione V25: `K2 -> 1 Protection`.
- Aggiungere `1 Protection -> Protect 1 card`, per chiarire che il token prima viene piazzato come protezione.
- `3 Protection -> Castle or Market` non e' piu' corretto:
  - `2 Protection -> Market`
  - `3 Protection -> Castle`
- `3 Castles -> the Capital` diventa `3 Castles -> Capital`.
- `Capital -> Shogun / the game ends at the beginning of the turn` va sostituito con `Capital -> Imperial Summons`.
- `At the beginning of the turn` va rimosso: in V25 la Capital valida e connessa avvia la sequenza finale immediatamente.
- `Evolution of the tokens transformed` va rimosso.

### Cosa puo' restare

- La sequenza visuale con icone e frecce funziona bene.
- Le icone di Protection, Market, Castle, Capital e Shogun/Imperial Summons possono restare se aggiornate nei valori.

---

## 5) Imperial Summons / Shogun Reminder

### Funzione del pannello

Questo puo' essere un nuovo mini-pannello oppure una riga dentro `Protection & Building`. Serve a evitare il vecchio errore V24: pensare che la fine partita parta all'inizio di un turno successivo.

### Contenuto consigliato V25

Se e' un pannello autonomo:

```text
Imperial Summons

A connected Capital
starts the final sequence.
```

Se resta dentro `Protection & Building`:

```text
Capital -> Imperial Summons
```

### Cosa cambiare dalla V24

- Rimuovere il testo che dice o suggerisce `at the beginning of the turn`.
- Rimuovere `the game ends` come frase secca: in V25 non finisce istantaneamente, parte la sequenza finale.
- Usare `Imperial Summons` come nome della fase finale.

### Cosa puo' restare

- L'icona Shogun puo' restare se viene reinterpretata come reminder della sequenza finale.
- Non e' obbligatorio creare un nuovo pannello se lo spazio e' limitato.

---

## 6) Visit the Emperor

### Funzione del pannello

Questo pannello ricorda la regola Expert Mode del reset della mano. In V25 il timing e l'effetto devono essere piu' precisi.

### Contenuto consigliato V25

```text
Visit the Emperor

Before action, shuffle deck,
discard pile, and hand.
Draw 3 cards.

Once per game.
Unused marker: +1 Point
```

Versione piu' compatta:

```text
Visit the Emperor
Before action:
shuffle deck, discard, hand.
Draw 3.

Unused: +1 Point
```

### Cosa cambiare dalla V24

- `Shuffle the Discarded deck with your hand` non e' abbastanza preciso: in V25 si mescolano deck, discard pile e mano.
- `ReDraw 3 cards in your Hand` diventa `Draw 3 cards`.
- Va aggiunto o reso visibile il timing: `Before action`.
- Il bonus `Unused marker: +1 Point` dovrebbe essere visibile, almeno in piccolo.

### Cosa puo' restare

- Il pannello resta valido.
- Il concetto `Once per game` resta valido.
- L'icona Emperor puo' restare.

---

## 7) Alliances / Diplomacy

### Funzione del pannello

Questo pannello contiene la regola specifica del clan per le alleanze. In V25 le Alliances sono Expert Mode / Diplomacy. Per ora il pannello resta clan-specifico: non trasformarlo in un testo generico comune a tutte le playerboard.

### Contenuto consigliato per Oda Nobunaga

```text
Alliances

May ask or break an Alliance
only with at least 4 Numbered
Cards on the board.

When forming an Alliance,
gain the same reward as
the other Daimyo.

One pact at a time.
No renewal with the same Daimyo.
```

Versione piu' compatta:

```text
Alliances

Ask/break only with
4+ Numbered Cards
on the board.

When forming:
gain the other Daimyo's reward.

One pact at a time.
No renewal.
```

### Cosa cambiare dalla V24

- `Can ask or break an alliance only with at least 4 Number Cards on game board` diventa `May ask or break an Alliance only with at least 4 Numbered Cards on the board`.
- La condizione specifica del clan resta nel pannello. Non rimuovere `4 Numbered Cards` su Oda finche' la nuova regola clan non viene riscritta.
- `tokens` puo' restare provvisoriamente se il pannello clan non e' ancora stato revisionato; quando le alleanze saranno definite per tutti, sostituire con il termine finale (`Protection`, `Koku`, o `reward`).
- `Daimyo` puo' restare, ma uniformare la maiuscola.
- Footer `One pact per time. No renewal with the same daimyo.` diventa `One pact at a time. No renewal with the same Daimyo.`

### Cosa puo' restare

- Il pannello resta valido.
- La regola specifica Oda puo' restare nella sostanza.
- Il layout a due colonne puo' restare se il testo viene accorciato.

### Punto aperto

Le alleanze cambiano per tutti i clan, ma la revisione non va fatta qui in forma generica. Quando la nuova matrice delle alleanze sara' confermata, aggiornare ogni playerboard con la propria condizione e ricompensa.

### Conversione proposta per V25

Per ridurre ambiguita' tra Alliance token e Protection token, le ricompense/penalita' delle alleanze possono essere convertite in Koku.

Conversione consigliata:

```text
+1 Protection token -> +2 Koku
+2 Protection tokens -> +3 Koku
-1 Protection token -> -2 Koku
```

Nota di bilanciamento: `+2 Protection tokens` non diventa `+4 Koku`, perche' +4 Koku sarebbe molto alto rispetto al limite di riserva e ai costi principali. `+3 Koku` mantiene il premio forte ma piu' controllato.

### Testi alleanze normalizzati in Koku

Questi testi usano un linguaggio comune:
- `alliance` minuscolo nei testi interni; `Alliances` resta titolo del pannello.
- `Daimyo` senza accento.
- `Numbered cards` per le carte numero.
- Ricompense alliance in `Koku`, non in token.

#### Oda Nobunaga

Colonna 1:

```text
May ask or break
an alliance only with
4+ Numbered cards
on the board
```

Colonna 2:

```text
When forming an alliance,
gain the same Koku
as the other Daimyo
```

#### Akechi Mitsuhide

Colonna 1:

```text
May form or accept
an alliance and gain
+2 Koku
```

Colonna 2:

```text
When breaking an alliance,
requires a Castle or Capital
and gain +3 Koku
```

#### Tokugawa Ieyasu

Colonna 1:

```text
When forming an alliance,
gain +2 Koku
```

Colonna 2:

```text
May break an Alliance
only with 4+ Numbered cards
on the board
```

#### Toyotomi Hideyoshi

Colonna 1:

```text
When asking an alliance,
gain +3 Koku
```

Colonna 2:

```text
When accepting an alliance,
gain no extra Koku
```

Colonna 3:

```text
When breaking an alliance,
gain no Koku
```

#### Date Masamune

Colonna 1:

```text
When asking an alliance,
gain +3 Koku
```

Colonna 2:

```text
When accepting an alliance,
gain no extra Koku
```

Colonna 3:

```text
When deliberately breaking
an alliance, lose 2 Koku.
No loss if another Daimyo interrupts it.
```

### Testi alleanze da elaborare

Questi sono i testi di partenza raccolti dalle playerboard. Non sono ancora normalizzati: servono come base per uniformare tono, maiuscole, termini evidenziati e stile tra i clan.

#### Oda Nobunaga

Colonna 1:

```text
May ask or break an
alliance only with
4+ Numbered cards
on the board
```

Colonna 2:

```text
When forming a alliance,
gains same Protection tokens
as the other daimyō
```

#### Akechi Mitsuhide

Colonna 1:

```text
Can form or accept
alliances gaining +1 extra token
```

Colonna 2:

```text
To break an alliance,
a Castle or Capital
is required,
granting +2 tokens
```

#### Tokugawa Ieyasu

Colonna 1:

```text
When forming an alliance
gain +1 extra Protection token
```

Colonna 2:

```text
May break an Alliance
only with 4+ Numbered cards
on the board
```

#### Toyotomi Hideyoshi

Colonna 1:

```text
Can ask an alliance
to gain +2 Tokens
```

Colonna 2:

```text
No extra Tokens provided
when receiving an alliance
```

Colonna 3:

```text
No Tokens provided
when breaking an
existing one
```

#### Date Masamune

Colonna 1:

```text
Can ask an alliance
to gain +2 Tokens
```

Colonna 2:

```text
No extra Tokens provided
when receiving an alliance
```

Colonna 3:

```text
Deliberately broken alliance costs
-1 token.
No tokens are lost if it is interrupted
by other daimyos.
```

---

## 8) Destiny Path

### Funzione del pannello

Questo pannello mostra l'obiettivo personale del clan e il bonus punti. Deve essere breve e usare terminologia standard V25.

### Contenuto consigliato per Oda Nobunaga

```text
Destiny Path

End the game with
1 Samurai on the board.

+2 Points
```

Footer opzionale:

```text
Fulfill this path for bonus points.
```

### Cosa cambiare dalla V24

- `Complete the game with 1 Samurai on the board` diventa `End the game with 1 Samurai on the board`.
- `+2 Points` resta.
- Se il footer resta, correggere la grammatica se necessario.

### Cosa puo' restare

- Il pannello resta valido.
- L'obiettivo Oda resta valido se confermato dal file clan.
- Evidenziare `Samurai` in colore diverso puo' restare.

---

## 9) Clan Header / Name / Mon / Portrait Area

### Funzione del pannello

Questa area identifica il clan e il Daimyo. Non e' un pannello regole, ma deve restare coerente con il resto della board e non deve contraddire V25.

### Contenuto attuale

- Nome: `Oda Nobunaga`
- Titolo: `The powerful conqueror`
- Date storiche
- Mon / simboli clan
- Calligrafia
- illustrazione del Daimyo

### Cosa cambiare dalla V24

- Nessun cambio regolistico obbligatorio.
- Verificare coerenza grafica se vengono aggiornati gli altri pannelli.
- Se V25 usa una nuova terminologia per clan/order/setup, aggiornare eventuali label collegati.

### Cosa puo' restare

- Nome, mon, immagine e identita' visiva possono restare.
- Il titolo storico puo' restare.

---

## 10) Biography Panel

### Funzione del pannello

Questo pannello e' narrativo. Non deve spiegare regole, ma deve restare leggibile e coerente con il tono storico del gioco.

### Cosa cambiare dalla V24

- Nessun intervento meccanico obbligatorio.
- Correggere solo eventuali refusi o frasi troppo lunghe se disturbano la leggibilita'.

### Cosa puo' restare

- Il testo biografico puo' restare.
- Il pannello pergamena puo' restare.

---

## 11) Strategy / Level / Order Number

### Funzione del pannello

Questa area da' identita' strategica al clan e riporta livello e numero d'ordine. Non deve promettere meccaniche non piu' vere in V25.

### Contenuto consigliato per Oda

Se si vuole mantenere il testo attuale:

```text
STRATEGY:
Use the raw strength of the army
to conquer and expand.
Hostile to religious symbols.
```

Versione alternativa piu' pulita:

```text
STRATEGY:
Use military pressure to expand
quickly and force opponents into
defensive mistakes.
```

### Cosa cambiare dalla V24

- `LEVEL medium` puo' diventare `LEVEL: Medium`.
- `ORDER NUMBER: 4` resta solo se il numero d'ordine e' ancora usato nel setup V25.
- Il testo strategy va controllato per evitare duplicazioni tra clan.

### Cosa puo' restare

- La sezione puo' restare.
- `Level: Medium` puo' restare se confermato.
- `Order Number: 4` puo' restare se confermato dalle regole di setup.

---

## 12) Map / Starting Position Mini-Panel

### Funzione del pannello

Questa area mostra riferimento geografico, colore clan e/o posizione di partenza. Deve aiutare il setup senza aggiungere testo.

### Cosa cambiare dalla V24

- Verificare che le posizioni di partenza mostrate siano ancora corrette per V25.
- Se V25 prevede start-position variant con Protection iniziale, non aggiungerlo qui se rende il pannello confuso: meglio tenerlo nel manuale o in setup sheet.

### Cosa puo' restare

- La mini-mappa puo' restare.
- I marker visuali possono restare se corrispondono alla V25.

---

## 13) Global Text / Terminology Pass

### Funzione del passaggio

Questo non e' un pannello, ma un controllo finale su tutta la board. Serve a uniformare termini e valori.

### Sostituzioni consigliate

```text
Draw up to 3 Cards -> Refill to 3 Cards
Resource Counting -> Koku Income / Collect Resources
Every counting -> Base income
Every Zone conquered -> Each Zone you control
Central -> Imperial Zone
Protection Tokens -> Protection
Number Cards -> Numbered Cards
Special Cards -> Retainer cards
the Capital -> Capital
Shogun the game ends -> Imperial Summons
At the beginning of the turn -> remove from Capital trigger
9 max -> 5 max / Max K5
```

### Valori V25 da controllare

```text
Koku reserve cap: K5
Reveal cost: K3
Extra card cost: K1 to play down to 1 card
K2 -> 1 Protection
1 Protection -> Protect 1 card
2 Protection -> Market
3 Protection -> Castle
3 Castles -> Capital
Connected Capital -> Imperial Summons
Koku income max: +K5 per counting
```

---

## 14) Recommended Layout Changes

### Interventi consigliati

1. Tenere `Playing Round` come pannello largo in alto, ma aggiornarlo alle 4 fasi V25.
2. Tenere tre pannelli centrali:
   - `Koku Income`
   - `Koku Reserve`
   - `Protection & Building`
3. Integrare `Imperial Summons` dentro `Protection & Building`, salvo spazio per un mini-pannello autonomo.
4. Tenere i pannelli bassi:
   - `Visit the Emperor`
   - `Alliances`
   - `Destiny Path`
5. Non aggiungere nuovi pannelli lunghi: V25 deve restare piu' leggibile, non piu' verbosa.

### Priorita' di aggiornamento

1. `Koku Reserve`: cambiare `9 max` in `K5`.
2. `Protection & Building`: correggere i costi Market/Castle e il trigger Capital.
3. `Playing Round`: aggiornare il flusso a 4 fasi.
4. `Koku Income`: aggiornare termini e limite.
5. `Visit the Emperor`: correggere timing ed effetto.
6. `Alliances` e `Destiny Path`: ripulire lingua e terminologia.
