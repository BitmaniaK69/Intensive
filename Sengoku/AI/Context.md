# CONTEXT RESTORE FILE — Sengoku (Board Game) — v22 → v23 → v24 (Koku economy + player board update)
_Last updated: 2026-02-14_

## 1. Obiettivo e Stato del Progetto
### Cosa stiamo costruendo?
Stiamo iterando il design del board game **Sengoku** (area control su griglia 6×6 con vincolo “Sudoku”), con:
- piazzamento carte (numeriche + special/retainers),
- **chain of command** a partire dal Daimyō,
- **errori** (violazioni Sudoku) usati strategicamente per distruggere carte,
- risorse e protezioni (token/cubi),
- costruzioni (Castelli, Mercato, Capitale),
- carte face-up / face-down (incluse trappole),
- alleanze/tradimenti (modalità avanzata),
- condizione Shogun.

### Focus attuale
Focus: **passaggio da v23 a v24** con introduzione della valuta **Koku (riso)** e aggiornamento della **player board** (testi, icone, valori).
Obiettivo: rendere la gestione economica più chiara e “leggera”, evitando di appesantire con ulteriori sottoregolamenti (non deve diventare “german”).

Stato: v24 in definizione (valori di income/costi quasi definiti), player board in revisione grafica/testuale.

---

## 2. Tech Stack e Configurazione
Non c’è un tech stack software. Lavoro su asset grafici (player board) e regole.

### Asset rilevanti
- **Player board Oda Nobunaga** (versione v24 in aggiornamento, immagine condivisa: `OdaNobunaga.png`)
- Iconografia: in v24 si sta standardizzando un set di simboli (Koku, cubo/protection, ecc.)

---

## 3. Stato Logico Attuale (CRITICO)

### 3.1 v22 — Cosa era stato introdotto (rispetto alle versioni precedenti)
**Deck/Cards**
- Nuovo set di carte con simboli che abilitano:
  - usare carte face-down per costruire capitale o per essere girate,
  - rivedere molte azioni delle special (posizionamento vicino chain of command, trappole legate a mercenari, stacking più frequente tipo Samurai).
  
**Numbered cards**
- 2 per ogni numero 1–6.
- Possono essere:
  - impilate (se resta valida l’unicità Sudoku),
  - protette da token,
  - ribaltate face-down,
  - base per costruire città/capitali,
  - piazzate ovunque se valide.

**Retainers / Special**
- 1 per tipo nel deck + 1 speciale per character.
- Possono: essere sacrificate per azioni, piazzate vicino chain, piazzate ovunque (senza vincolo validità), piazzate face-down come trappole, protette da token.

**Daimyō**
- 1 per clan; piazzata in posizioni di partenza.
- Contiene fino a **3 token** (slot) utili per costruire castelli.
- Non eliminabile, non usabile face-down.
- Inizio chain of command.

**Meccaniche v22**
- Rimosse Siege Towers, introdotto **Mercato**.
- Face-down + trappole + costo per rivelare (in v22 era a token).
- Win: **2 capitali** collegate (v22).
- Punteggio Shogun: 4/3/2 (v22).
- Scoring finale: solo carte scoperte e collegate; face-down non danno punti ma estendono chain.

**Mappa v22**
- Zone di partenza definite.
- Token “+1” sulla mappa per primi arrivati (poi cambiato in v23).
- Tema grafico scuro con mappa Giappone e simboli zone.

**Feedback test v22 (3 test)**
- Problemi: velocità (progressione simile per tutti), turtling ancora presente.
- Migliorato: flusso di gioco e comprensione regole carte, nuove opzioni di azioni/posizionamento.
- Feedback: layout e carte apprezzati, ma “meno funny”.

---

### 3.2 v23 — Cambi introdotti e stato test
**Deck/Playerboard**
- Nessun cambio strutturale per ora (ma playerboard/zone come fonte da rivedere).

**Meccaniche v23**
- Pagamento per “vedere” una carta (flip/reveal) si può fare anche su carte proprie: **2 token** per girare qualsiasi carta.
- Setup: non si parte più con Daimyō + carta numerica; solo **Daimyō**.
- Mano: non si gioca più fino a 2 carte; ora si può arrivare fino a **1 carta in mano** (quindi **si giocano almeno 2 carte a turno**).
- **Zona non è più fonte risorse** (ma questo indebolisce il concetto di zone).
- Vittoria: non servono più 2 capitali; ora **1 capitale basta** (economia e ritmo più veloce).
- Visita all’Imperatore: resta; chi NON visita (non rimischia il mazzo) ha **+1 punto**.

**Mappa v23**
- Aumentate e cambiate zone di partenza, con vincolo Sudoku per piazzare Daimyō.
- Alcune start hanno simbolo diverso (+) per bilanciare distanza dal centro: davano 1 carta in più (ritenuto confusionario/esagerato).
- Centro: non dà più token al primo arrivato; ora ci sono **4 zone franche centrali** che danno **1 punto a chi le possiede** (delimitate in rosso con simbolo imperatore).

**Feedback test v23 (2 test)**
- Zone meno importanti.
- Confusione su “2 carte ora”.
- Progressione più lenta → 1 capitale sufficiente.
- Pagare per proprie carte (reveal) necessario per aumentare errori e liberare posizioni.
- Carte da rivedere un poco.
- Migliorato: turtling ridotto, più fight, errori più frequenti con trappole, più fun.
- Layout mappa molto migliorato; conquista zone meno engaging.

---

### 3.3 v24 — Koku economy + chiarimenti su Token/Build (punto centrale della sessione)
#### Principio guida
Il gioco è già complesso: v24 deve **semplificare**, non aggiungere sottoregolamenti. I Koku servono a distinguere chiaramente:
- valuta/risorsa (Koku) vs
- elementi fisici sulla mappa (cubi protezione / build progress)

#### Definizioni v24 (stato attuale)
- **Koku**: unità astratta (anche se storicamente enorme). Si usa come “ricchezza”/currency.  
  UX: si usa notazione **K1, K3, K6** invece di un’icona moneta difficile da leggere.
- **Token/Protection cubes**: cubetti fisici. Non esistono più icone “ventaglio”. Il cubetto rappresenta:
  - protezione (scudo) e
  - progresso build (piazzare 3 cubi per costruire).
- Carte face-down: **non protette** (regola nel manuale, non necessariamente sulla scheda).

#### Spend: Koku vs Token (importantissimo)
- **Reveal (girare una carta)**: costo **K3** (v24 confermato).
- **Costruire Castello/Mercato**: NON si pagano in Koku.
  - Si costruiscono solo se puoi **piazzare 3 cubetti Protection** su carte (in turni differenti) e poi **collezionarli** e sostituirli con Castello/Mercato.
  - Se non riesci fisicamente a piazzare 3 cubetti (perché non hai basi / spazio), **non puoi costruire**, anche se avessi Koku.
  - Il **Daimyō ha 3 slot** che possono contribuire al raggiungimento dei 3 cubi.
- **Castello richiede carta numerica**: per ogni castello serve una **Numbered card** come base (regola da mettere nel manuale; valutata come testo opzionale in scheda, ma per ora manuale).
- **Capitale**: si ottiene quando hai costruito **3 castelli** (il 3° castello diventa capitale: “non esiste 3 castelli + capitale”; a fine game tipicamente 0–2 castelli + capitale).

#### Income v24 (proposta quasi definita)
A fine turno (Koku Income):
- Base: **+K1**
- +K1 se possiedi **Market**
- +K1 se possiedi **Zone**
- +K1 per ogni **Central** controllata (0–4; instabile per design)
Cap/limiti discussi:
- Reserve: scelto **K9**.
- Cap “gain per turn” era in bozza K5 (non finalizzato qui; può restare in manuale o essere rimosso dalla scheda se confonde).

#### Error economy / Reveal outcomes (usato per simulazioni)
- Reveal spesso produce “fix error” e può dare ricompense in Koku:
  - ~50% dei reveal sono fix effettivi.
  - Distribuzione: spesso fix 1 errore, talvolta 2 (20%), raramente 3 (5%).
- Trappole: nel meta attuale ci sono 2 “trappole” principali collegate ad azioni (Shinobi A2, Ronin A2); quando scatta una trappola, la carta trappola viene rimossa/scartata.
- Probabilità “fix utile” cresce nel late game (più stack/zone create), rispetto all’early.

#### Shogun / endgame v24
- **Shogun**: il primo che inizia il turno con **1 Capitale** collegata alla chain (trigger semplice).
- Si è discusso di ridurre punti Shogun da 4/3/2 a 3/2/1; dato che in molti test “il primo Shogun non vince sempre”, si è consigliato un tuning soft a 3/2/1, ma non fissato in questa sessione.
- Scoring: carte face-up collegate + castelli/capitale; face-down contribuiscono alla chain ma valgono 0 punti.

---

### 3.4 Start positions / mappa (v23+ e discussione strategica)
Mappa 6×6 (A–F, 1–6). Zone esempio fornito:
- Z1: A1,B1,C1,A2,B2,C2
- Z5: D3,E3,F3,D4,E4,F4
- Z6: D5,E5,F5,D6,E6,F6
Centrali: C3,C4 (in Z2) e D3,D4 (in Z5).

Start squares elencate:
- B1(+), C1, D1, E1(+), A2(+), F2(+), A3, A4, F3, F4, A5(+), B6(+), C6, D6, E6(+), F5(+)
(+): distanza 3 dal centro → percepito svantaggio. Dare 1 carta in più è stato ritenuto eccessivo/confusionario; alternativa proposta: +1 Koku (o +1 token) iniziale.

Strategia per start (in 4 players, 65% dei giochi):
- Flank line (A3,A4,F3,F4) è più consistente (zona stabile + incursioni centro).
- Gateway (C1,D1,C6,D6) più rischioso (sandwich).
- (+) più lento sul rush, ma forte se engine indisturbato.

---

## 4. Modifiche Recenti e Contesto (decisioni di design)
### Decisioni chiave prese durante questa sessione
1) **Reveal cost** fissato a **K3**.
2) **Koku Reserve** fissata a **K9**.
3) Chiarezza fondamentale: **Castello/Mercato si costruiscono solo con 3 cubi (Protection) piazzati sulla mappa (anche in turni diversi), non pagando Koku.**
4) UX: per evitare confusione delle icone, adottato testo **K1/K3/K6** invece dell’icona moneta poco leggibile.
5) Player board: evitare di aggiungere troppe info; mettere solo le info “da turno” (income, reserve, reveal cost, build steps) e lasciare il resto al manuale.

### Player board — revisione testi inglesi
Correzioni suggerite per rendere l’inglese naturale:
- “Every counting” → “End of turn”
- “Every zone conquered” → “Each Zone you control”
- “Per Central controlled” → “Each Central space you control”
Titoli consigliati:
- “Resource Counting” → “Koku Income”
- “Koku Resource Reserve” → “Koku Reserve”
- “Tokens Conversion” → “Build & Protection”
Frase da cambiare richiesta:
- “Evolution of the tokens transformed” → proposte: “Token Upgrade Path”, “Token Progression”, “Building with Tokens”, “Build Progress (Tokens)”

---

## 5. Errori Attivi e Bloccanti
Nessun errore tecnico (non c’è codice). Rischi di design:
- Confusione iconografica tra Koku/Token/Protection → mitigata con notazione K# e semplificazione icone.
- Se “cap gain per turn” o “cap reserve” è troppo basso, rischio turtling/soddisfazione precoce.
- Zone normali in v23 avevano perso importanza; v24 tenta di riallinearle via income (Zone + Market + Centrals).

---

## 6. Roadmap Immediata (Prossimi Passi)
### Prossimo prompt nella nuova chat (istruzione esatta)
**“Riprendiamo da questo context restore. Dobbiamo finalizzare i valori v24 da stampare sulla player board e la versione finale dei testi inglesi (brevi, da scheda). Conferma: Koku Reserve K9, Reveal cost K3, build castle/market tramite 3 Protection cubes piazzati su carte (multi-turn). Ora proponi 2 set alternativi (A/B) per Koku Income (base/market/zone/central) e per eventuale cap gain per turn, con impatto su turtling e rush.”**

### Task a breve termine
1) Finalizzare: Koku Income (con o senza cap gain per turn) e se “Central” è +1 each o altra formula.
2) Aggiornare definitivamente i box della scheda:
   - Koku Income
   - Koku Reserve (K9 + Reveal K3)
   - Build & Protection (1 cube protect, 3 cubes build castle/market, 3 castles capital, Shogun trigger)
3) Rimuovere riferimenti “Siege Towers” (se presenti nel testo della scheda).
4) Manuale: inserire le regole che non entrano in scheda:
   - “no protection on face-down”
   - “castle requires numbered card”
   - dettagli error fix reward
   - eccezioni carte (Ronin colpisce stack, ecc.)

---

## 7. Preferenze e Vincoli dell’Utente (MEMORIA)
- Il gioco deve restare **semplice** e leggibile: evitare aggiunte “german”.
- La player board è **compatta**: mettere solo info essenziali; dettagli nel manuale.
- Preferenza per comunicazione “a colpo d’occhio” tramite:
  - 3 aree grafiche (income / reserve / build/spend)
  - notazione testuale **K#** (es. K1/K3/K6) invece di icone poco leggibili.
- English copy: frasi brevi e naturali; titoli facilmente modificabili.
- Importante: **Reveal cost** era ritenuto essenziale da mettere in scheda.
- Token icon “ventaglio” rimosso; i cubi rappresentano protezione/build. 
