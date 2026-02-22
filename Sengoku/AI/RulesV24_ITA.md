# Sengoku - Regole V24.1 (Traduzione ITA Sintetica)
_Fonte ufficiale: `AI/RulesV24.md`_

Questa e una traduzione italiana **semplice e corta** del regolamento ufficiale.
In caso di dubbio o conflitto, **fa fede `AI/RulesV24.md`**.

I termini di gioco giapponesi (es. **Daimyo, Koku, Junbi, Ronin, Shinobi**) restano invariati.

---

## 1) Panoramica
Ogni giocatore guida un clan nel periodo Sengoku.
L'obiettivo e controllare la mappa, costruire una **Capital** connessa e arrivare alla conferma come **Shogun**.

Risorse principali:
- **Koku** = valuta (tenuta sulla Player Board, mai sulla mappa)
- **Protection token** = risorsa di mappa (difesa + costruzioni)

Vince chi fa piu punti a fine partita.

Pareggio:
- Vince chi ha piu **Koku** rimasti sulla **Player Board**
- Se c'e ancora parita', vittoria condivisa

---

## 2) Componenti (base 4 giocatori)
- Tabellone principale
- 4 Player Board
- 4 mazzi clan (20 carte ciascuno)
- Koku token
- Protection token
- Emperor marker (Expert Mode)
- Market, Castle, Capital

Limiti pezzi (hard limits):
- max 3 Castle per giocatore
- max 1 Market per giocatore
- max 1 percorso Capital attivo (regole correnti)

---

## 3) Setup (Standard)
1. Scegli il clan e prendi Player Board + componenti.
2. Separa la carta **Daimyo** dal mazzo e tienila scoperta vicino/sulla Player Board (solo staging setup).
3. Mescola le altre 19 carte.
4. Pesca 3 carte iniziali.
5. Se non hai nessuna carta Numbered, rimischia quella mano nel mazzo e ripeti finche ne hai almeno una.
6. Questo redraw iniziale **non** e "Visit the Emperor".
7. Determina il primo giocatore.
8. Durante **Junbi**, piazza i **Daimyo** sul **Game Board** nelle caselle iniziali legali.

Nota:
- Sul 6x6 gli angoli non sono posizioni iniziali valide.
- Le posizioni 5x5 e 9x9 sono ancora da definire (vedi backlog nel file ufficiale).

---

## 4) Tabellone, Controllo e Zone
Formati:
- 2 giocatori: 5x5 (Duels)
- 3-4 giocatori: 6x6
- 5-6 giocatori: 9x9

Controllo:
- In una pila conta solo la **carta in cima** per il controllo.
- Se la carta in cima e **face-down**, conta comunque per il clan, ma non ha numero rivelato.

Zone e linee:
- Zone e linee complete danno controllo/income/punti (in base alla sezione di punteggio)
- Una casella puo contare sia per Zone sia per Line se entrambe soddisfatte

Imperial Zones:
- Sono le 4 caselle centrali speciali (6x6 standard)
- Ognuna controllata da +1 Koku durante il conteggio di fine turno
- Non possono ricevere: face-down, Protection token, Buildings

---

## 5) Tipi di carte
### Daimyo
- Entra sul Game Board durante **Junbi**
- Avvia la Chain of Command
- Puo tenere fino a 3 Protection token in **reserve** (non sono Koku, non proteggono automaticamente)
- Non vale punti come carta a fine partita

### Numbered (1-6)
- Usate per controllo, Sudoku, build base
- Possono essere giocate face-up o (in certi casi) face-down

### Retainers
- Ogni Retainer ha **2 Order Actions (A1/A2)**: quando la usi scegli e risolvi **solo 1**
- Il modo d'uso (piazza/scarta) dipende da icone/testo
- Le **Order Actions** sono separate dalle **Turn Procedures** (Reveal, Convert Koku, Build, Error Fix)

---

## 6) Chain of Command e termini base
- **Connected** = ortogonale (no diagonali)
- **Adjacent** = ortogonale o diagonale
- **Chain of Command** = gruppo connesso che include il tuo **Daimyo**

Regola generale punteggio:
- Contano solo elementi **connessi** alla Chain of Command (salvo effetti specifici)

---

## 7) Regole di piazzamento (Sudoku)
Regole base:
- I **Daimyo** non possono condividere riga, colonna o zona tra loro
- Le **Numbered face-up** non possono duplicare numero nella stessa riga, colonna o zona
- I Retainers seguono il proprio testo (e possono convivere, salvo restrizioni specifiche)

Se non hai un piazzamento valido:
- Scarta una carta
- Continua il turno con altre azioni legali non di piazzamento

Stacking:
- Puoi impilare su Numbered, Retainers, face-down placeholder e trappole face-down (se legale)
- Se togli la carta in cima, la carta sotto torna attiva subito
- Questo puo creare Error immediati

---

## 8) Carte face-down, Reveal e Trappole
Regole face-down:
- Solo le **Numbered** possono essere piazzate face-down come placeholder (salvo Retainers-trappola specifici)
- Alcuni Retainers (es. **Shinobi**, **Ronin**) possono essere giocati face-down come trappole
- Le face-down non possono stare nelle Imperial Zones
- Le face-down non possono ricevere Protection token

Placeholder Numbered face-down:
- Non ha numero attivo finche resta nascosto
- Quindi non crea duplicati Sudoku finche non viene rivelato
- Se e in cima a una pila, conta comunque per il controllo del clan

Reveal (Bribery):
- Costo: **3 Koku**
- Puoi rivelare qualsiasi face-down (anche tua)
- Se una Numbered rivelata crea un duplicato proibito, crea un **Error** immediato
- Se e una trappola, risolvi l'effetto una volta e poi rimuovi/scarta la carta

---

## 9) Errors (Rebellions)
Un **Error** e uno stato illegale della mappa (di solito duplicati Numbered proibiti).

Correzione immediata (durante il turno del giocatore attivo):
- Qualsiasi giocatore puo segnalarlo **prima del passaggio turno**
- Il giocatore attivo corregge subito (sposta la carta o sceglie un'altra giocata legale)
- Se cambia carta, la carta tentata illegalmente **non si perde** (torna in mano)
- Nessuna ricompensa in questa finestra

Correzione sul tuo turno:
- Puoi correggere uno o piu Error gia presenti
- Scegli tu ordine e carte da rimuovere
- Se una rimozione rivela altri Error, puoi continuare

Ricompensa:
- **+1 Protection token per Error corretto**
- Se una sola rimozione risolve piu Error, prendi +1 per ciascuno
- Ogni token guadagnato va piazzato **subito** su una carta face-up legale
- Se non puoi piazzarlo sulla mappa, puoi metterlo nella **reserve del Daimyo** (max 3)
- Se non puoi piazzarlo e la reserve del Daimyo e piena, il token si perde (torna in supply)

Nota:
- Se rimuovi uno strato protetto/edificato in un Error, rimuovi anche Protection token/building attaccati a quello strato

---

## 10) Koku e Protection token
### Koku
- Valuta principale
- Sta sulla Player Board
- Serve per Reveal e per convertire in Protection token
- Cap di storage: **6**

### Protection token
- Risorsa di mappa (difesa + costruzioni)
- Non e valuta
- Non torna mai a Koku

Conversione (Turn Procedure):
- **2 Koku -> 1 Protection token**
- Quantita libera durante il tuo turno (se hai Koku)

Daimyo reserve:
- Il Daimyo puo tenere fino a **3 Protection token** in reserve
- Questi token non proteggono automaticamente il Daimyo
- Non puoi mettere Koku sul Daimyo

---

## 11) Difesa e Protezioni
- Un Protection token su una carta la protegge
- Le carte protette non si rimuovono direttamente, salvo effetti che rimuovono/bypassano la protezione
- Nelle pile la protezione vale per lo **strato in cima**
- 1 sola "piece" per carta: **1 token** oppure **1 Castle** oppure **1 Market**
- Le carte face-down non possono ricevere Protection token

Capital:
- Va sempre sopra una base face-down
- La base sotto la Capital non puo essere attaccata/rivelata/distrutta finche la Capital resta in cima

---

## 12) Costruire Castle e Market
Requisiti base:
- almeno 3 Protection token disponibili nella tua Chain of Command connessa
- almeno una carta Numbered connessa valida come destinazione

Processo:
1. Rimuovi 3 token "committed"
2. Piazza 1 **Castle** o 1 **Market** su una Numbered connessa valida
3. La destinazione non deve per forza essere una delle carte da cui hai tolto i token

Regola di conversione obbligatoria (importante):
- La conversione automatica e **obbligatoria solo** se hai almeno 3 token su **Numbered connesse**
- Se i 3 token includono token presi da Retainers e/o dalla reserve del Daimyo, la conversione e legale ma **non obbligatoria**

Limite Castle:
- max 3 Castle
- Se una conversione creerebbe un 4o Castle:
  - puoi rilocare uno dei Castle esistenti su una Numbered connessa legale
  - se non puoi rilocare, la conversione non si risolve e i token restano dove sono

Market:
- max 1 per giocatore

---

## 13) Formare una Capital
Requisiti:
- 3 Castle nella tua Chain of Command
- connessione continua al Daimyo

Processo:
1. Rimuovi i 3 Castle
2. Scegli una Numbered connessa come base della Capital
3. La base deve essere face-down:
   - se e face-up, girala face-down
   - se c'e gia una face-down (anche trappola), usala come base
4. Piazza la **Capital**

Regole:
- Niente Capital nelle Imperial Zones
- I Castle disconnessi non contano per la progressione
- Se hai 3 Castle connessi validi, la conversione a Capital e obbligatoria

---

## 14) Attacchi e Risoluzione
Gli attacchi/effetti offensivi arrivano da:
- Retainers
- correzioni Error
- trappole / Reveal
- testo carte (Kill / Remove / Steal / ecc.)

Risoluzione:
- Sempre **sequenziale**, un effetto alla volta
- Nessun "dichiaro tutto e poi risolvo"

Reazioni fuori turno:
- Solo se una carta/regola apre una finestra esplicita

---

## 15) Shogun Candidate, Fine Partita, Conferma
Quando completi una **Capital connessa**:
- diventi **Shogun Candidate**
- devi dichiarare subito la candidacy (non puoi saltarla)

Final Cycle:
- Il primo candidate e l'anchor
- Tutti gli altri giocatori fanno 1 ultimo turno
- Altri giocatori possono diventare Shogun Candidate durante questo ciclo
- Le alleanze (Expert) finiscono all'inizio del Final Cycle

Validita della candidacy:
- Se la tua Capital si disconnette prima della conferma, la candidacy diventa invalida
- Se la riconnetti in tempo, la candidacy torna valida

Candidate Confirmation (Koku-only):
- Dopo gli ultimi turni, risolvi la conferma in ordine turno a partire dall'anchor
- Agiscono solo i giocatori con Capital valida e connessa in quel momento
- In questa finestra si possono spendere solo **Koku** per effetti legali basati su Koku
- Sei **confirmed Shogun** solo quando arriva il tuo timing di conferma e la Capital e ancora valida/connessa

---

## 16) Turn Structure (sintesi)
### Inizio turno
- Pesca/ricarica fino a 3 carte
- (Expert) Finestra "Visit the Emperor" dopo refill e prima della prima carta giocata

### Sezione principale
- Gioca carte fino a 2 in mano
- Puoi giocare una carta extra finale pagando **1 Koku** (finendo a 1 carta)
- Turn Procedures: Convert Koku, Reveal, Build, Error Fix
- Piazza Protection token
- Expert: alleanze / emperor / destiny path
- Dichiara Shogun candidacy se completi una Capital connessa

### Fine turno
- Pesca/ricarica fino a 3
- Calcola income Koku
- Scarta Koku oltre cap 6
- Passa il turno

---

## 17) Income Koku (fine turno)
Fonti tipiche:
- +1 base
- +1 con Market
- +1 per ogni Zone o Line controllata
- +1 per ogni Imperial Zone controllata

Regole:
- Le fonti valide si sommano
- Non puoi "saltare" una fonte per evitare sprechi di cap
- Il conteggio ha cap (vedi regole ufficiali / Player Board)
- Dopo il conteggio, applichi il cap di storage Koku (6)

---

## 18) Expert Mode (sintesi)
Moduli:
- **Alliances**
- **Visit the Emperor**
- **Destiny Path**

### Alliances
- Token alleanza = Protection token del colore alleato sul Daimyo
- Non e spendibile come Protection normale mentre e marker alleanza
- Se rimosso, l'alleanza termina subito

### Visit the Emperor
- 1 volta per partita per giocatore
- Uso proattivo solo all'inizio del tuo turno (dopo refill, prima della prima carta)
- Gestisce reshuffle deck/discard (ed eventualmente mano, secondo regola ufficiale)
- Se il deck finisce durante una pesca obbligatoria, puo consumarsi automaticamente il diritto Emperor

---

## 19) Punteggio Finale (Standard)
Conta solo elementi connessi.

Punti:
- +1 per ogni carta face-up (Numbered o Retainer)
- +1 per ogni Zone/Line completa controllata
- +1 per ogni Castle
- +3 per ogni Capital
- +4 se sei **confirmed Shogun**
- +1 (Expert) se non hai mai usato il diritto Emperor reshuffle

Regole:
- Le carte face-down non danno il +1 carta
- Le face-down contano comunque per il controllo di Zone/Line

Pareggio:
- piu Koku sulla Player Board
- poi vittoria condivisa

---

## 20) Junbi (Preparazione)
Junbi e la fase iniziale di piazzamento dei Daimyo.

Passi:
1. Determina il primo giocatore
2. Il primo piazza il Daimyo in una casella iniziale valida
3. Gli altri piazzano in ordine, rispettando le restrizioni Daimyo (riga/colonna/zona)
4. Poi inizia il flusso normale di gioco

---

## 21) Duels (2 giocatori) - sintesi
Usa il tabellone 5x5.

Regole chiave:
- Si usa lo stesso core system (Koku / Protection / Reveal / Build)
- Catena e connessione sono ancora piu importanti
- Casella ponte centrale con bonus specifico (se controllata e connessa)
- Edifici non piazzabili sul ponte

Endgame Duels:
- Stesso principio di **Shogun candidacy**
- Dopo l'ultimo turno avversario, risolvi **Candidate Confirmation (Koku-only)**
- Poi punteggio

Tie-break Duels:
- come regola globale: piu Koku sulla Player Board, poi parita condivisa

---

## 22) Glossario rapido
- **Chain of Command**: gruppo connesso che include il Daimyo
- **Connected**: ortogonale
- **Adjacent**: ortogonale o diagonale
- **Error / Rebellion**: stato illegale (duplicati Numbered proibiti)
- **Bribery / Reveal**: azione da 3 Koku per rivelare una face-down
- **Top Layer**: strato superiore di una pila (normalmente il solo bersagliabile)
- **Player Supply**: riserva componenti fuori mappa

---

## 23) Appendice Retainers (cheat sheet breve)
Per testo completo e chiarimenti, usa l'appendice di `AI/RulesV24.md`.

- **Samurai**: piazzamento vicino/copertura + rimozione bersaglio/token; interrupt fuori turno
- **Ashigaru**: piazzamento vicino + attacco a Number/face-down; filtro mazzo (draw 4 keep 1)
- **Chajin**: draw / draw+play con bonus a Special
- **Sohei**: overlap su Sohei/Numbered/face-down; recupero dalla pila scarti
- **Shinobi**: rimozione Special o face-down; spionaggio mano + scarto
- **Ronin**: replace su carta non-Ronin; furto token (max 1 per player, resto da risorse)

---

## 24) Nota sulla versione
Questa versione ITA e volutamente sintetica.
Per edge case, wording completo delle carte, appendici estese, note storiche e log test:
- usa `AI/RulesV24.md`

