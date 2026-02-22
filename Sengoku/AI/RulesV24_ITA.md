# Sengoku - Regole V24.1 (ITA, versione completa per il gioco)
_Fonte ufficiale: `AI/RulesV24.md`_

Questa versione italiana ├¿ pensata per essere **leggibile** ma anche **completa nelle regole necessarie** per giocare senza dubbi (inclusi edge case e timing rilevanti).

Regole di priorità:
- Se questo testo entra in conflitto con il testo di una carta, **prevale il testo della carta**.
- In caso di dubbio di traduzione, **fa fede `AI/RulesV24.md`**.

Questa versione **non include**:
- Glossario
- Appendici storiche / retainers estesi
- Note designer / log / note interne

I termini giapponesi restano in giapponese (es. **Daimyo, Koku, Junbi, Ronin, Shinobi**).

---

## 1) PANORAMICA DEL GIOCO
Ambientato nel periodo Sengoku (1467-1615), il gioco mette ogni giocatore al comando di un clan Daimyo in competizione per influenza, controllo territoriale e supremazia politica.

Il gioco usa due risorse distinte:
- **Koku** = valuta
- **Protection token** = risorsa di mappa usata per difesa e progressione costruzioni

Modalità:
- **Standard Mode**: regole base (piazzamento, controllo, difesa, punteggio)
- **Expert Mode**: aggiunge **Alliances**, **Visit the Emperor** e **Destiny Path**

Arco di gioco (core loop):
- Piazzi carte Numbered e Retainer per costruire posizione
- Espandi controllo rispettando vincoli tipo Sudoku
- Difendi con Protection token e costruisci
- Arrivi a **Capital** e dichiari **Shogun candidacy**

Vittoria:
- Vince chi ha il punteggio finale più alto

Pareggio:
- Se due o più giocatori sono pari punti, vince chi ha più **Koku rimasti sulla Player Board**
- Se c'è ancora parità, vittoria condivisa

---

## 2) COMPONENTI DI GIOCO
Il gioco base ├¿ progettato per 4 giocatori. Per 5-6 giocatori servono tabellone grande e componenti extra clan.

Componenti (base, 4 giocatori):
- 1 tabellone principale
- 4 player board
- 4 mazzi clan (20 carte ciascuno: 12 Numbered, 6 Retainer, 1 Unique Special Retainer, 1 Daimyo)
- 36 Koku token (9 per giocatore)
- 20 Protection token giocatore (5 per giocatore)
- 4 Emperor Visit marker (Expert Mode)
- 4 Market (1 per giocatore)
- 12 Castle (3 per giocatore)
- 4 Capital (1 per giocatore)

Colori clan base:
- Oda Nobunaga: rosso scuro
- Toyotomi Hideyoshi: verde
- Akechi Mitsuhide: blu
- Tokugawa Ieyasu: giallo

Espansione (colori):
- Date Masamune: viola
- Mori Terumoto: grigio chiaro
- Ishida Mitsunari: nero
- Lady Oichi: arancione

Regole componenti:
- I **Protection token** sono risorse di mappa (difesa / progressione build)
- I **Koku** sono token fisici tenuti nell'area Player Board e **mai** sulla mappa
- Gli **Emperor Visit marker** partono in stato disponibile sulla Player Board
- I limiti pezzi sono **hard limits** (es. max 3 Castle; max 1 percorso Capital attivo)

---

## 3) SETUP
Il setup resta basato su clan/mazzo, con la carta Daimyo separata prima della prima pesca.

### Prima della partita
1. Ogni giocatore sceglie un colore/clan Daimyo
2. Ogni giocatore prende Player Board, mazzo e componenti
3. Ogni giocatore mette il proprio Emperor Visit marker nella posizione disponibile (solo tracking Expert Mode)

### Preparazione del mazzo
1. Rimuovi la carta **Daimyo** dal mazzo e tienila scoperta vicino/sulla Player Board (verrà piazzata sul Game Board durante **Junbi**)
2. La carta Daimyo ├¿ "parcheggiata" vicino/sulla Player Board solo durante il setup; non ├¿ ancora sul Game Board
3. Mescola le restanti 19 carte e mettile coperte a lato della Player Board
4. Pesca una mano iniziale di 3 carte
5. Se la mano iniziale non contiene **nessuna** carta Numbered, rimischia quella mano nel mazzo e ripeti finché ne peschi almeno una Numbered

Regola:
- Questo redraw iniziale fa parte del setup e **non** è Visit the Emperor (non consuma/flip il marker Emperor)

### Ordine di turno (setup)
- Determina solo il primo giocatore
- Poi si procede in senso orario
- Il numero "Order Number" sulle player board ├¿ tematico/guida, non obbliga la disposizione al tavolo
- Sul tabellone 6x6, sono valide solo le posizioni iniziali elencate; gli angoli non sono validi

---

## 4) ELEMENTI DI GIOCO
Posizione, controllo di zone e linee, e connessione determinano income e punteggio.

### 4.1 Game Board
Formati tabellone:
- 2 giocatori: 5x5 Duels board (con spazio ponte centrale condiviso)
- 3-4 giocatori: 6x6
- 5-6 giocatori: 9x9

Zone:
- Sul 6x6 Standard ci sono 6 zone (Z1-Z6), ciascuna 3x2
- La geometria zone per 5x5 (The Duel) e 9x9 (The Grand Campaign) ├¿ ancora da definire
- Le zone servono per controlli di controllo e income

Imperial Zones:
- Sono spazi centrali marcati (icona Emperor)
- Ogni Imperial Zone controllata da +1 Koku durante il conteggio income
- Le 4 Imperial Zones centrali non possono ricevere:
  - carte face-down
  - Protection token
  - Buildings

Controllo linee:
- Una linea valida va da un lato del tabellone al lato opposto
- Una linea ├¿ controllata solo se tutti i suoi spazi sono occupati dal tuo clan
- Verticali e orizzontali sono valide
- Le diagonali non sono linee valide

Controllo e stacking:
- In una pila, per i controlli conta solo la carta in cima
- Se la carta in cima ├¿ face-down, conta comunque per il suo clan ma non ha numero rivelato
- Una prefettura può contribuire contemporaneamente a una zona e a una linea valida
- Se soddisfi entrambe le condizioni, entrambe contano (income/punteggio)

### 4.2 Player Board
La Player Board serve a gestire info e risorse.

Mostra:
- storia/theme del Daimyo e riferimenti rapidi
- riferimento ordine turno
- spazi risorse/Koku
- riferimenti Expert Mode
- identità del clan

Regole importanti:
- La Player Board ripete i valori economia come **quick reference**
- Il regolamento (`AI/RulesV24.md`) definisce timing, cap ed edge case economici

Schema income (come mostrato):
- +1 Koku base (ogni conteggio)
- +1 Koku con Market costruito
- +1 Koku per ogni Zone o Line conquistata (ciascuna)
- +1 Koku per ogni Imperial Zone controllata
- Cap conteggio di fine turno: max 5 Koku generati dal conteggio
- Cap di storage dopo il conteggio: conserva max 6 Koku, scarta l'eccesso

---

## 5) MAZZO E TIPI DI CARTE
Ogni mazzo Daimyo ha 20 carte:
- 1 Daimyo
- 12 Numbered (1-6, due copie per numero)
- 6 Retainer
- 1 Unique Special Retainer

Coerenza mazzo:
- Le Numbered sono uguali tra i clan
- L'identità clan è mostrata da colore/simboli
- Numbered e Retainer condividono il dorso clan, quindi una carta coperta non rivela il tipo dal retro

### 5.1 Daimyo Card
- Viene piazzata sul Game Board durante **Junbi** e poi rimane in gioco
- Inizia la Chain of Command
- Può tenere fino a 3 token riservati per build
- Non vale punti come carta a fine partita

### 5.2 Numbered Cards
- Rappresentano prefetture/province
- Servono per controllo, stacking e destinazioni build (quando eleggibili)

### 5.3 Retainer Cards
- Forniscono effetti tattici tramite Action 1 / Action 2
- La modalità d'uso è definita da icone/testo:
  - azione di piazzamento -> la carta viene piazzata sul tabellone
  - azione di sacrificio/scarto -> risolvi effetto e poi scarti a faccia in su

Regola:
- La Unique Special Retainer segue la logica stampata sulla carta; modalità "place" e "discard" non sono intercambiabili salvo esplicita indicazione

---

## 6) ANATOMIA DELLE RETAINER CARD
Le Retainer possono essere usate piazzandole o risolvendo l'effetto, secondo icone/testo.

### 6.1 Struttura generale
- Ogni Retainer ha **2 Order Actions**
- Quando usi la carta, ne scegli e risolvi **solo 1**
- La modalità d'uso dipende da icona/testo (Place o Discard)

### 6.2 Regole d'uso
- Quando giochi una Retainer, scegli e risolvi esattamente 1 delle sue 2 Order Actions
- Se quella stessa Retainer torna più tardi in mano, può essere giocata di nuovo e puoi scegliere di nuovo una delle 2 Order Actions
- Gli effetti Retainer sono single-use per quella giocata, salvo testo che dica diversamente
- Alcune carte limitano usi ripetuti nello stesso turno (es. Chajin)
- Un giocatore può fermarsi con 2 carte in mano; per giocare una carta finale (arrivando a 1) deve pagare 1 Koku
- **Reveal, Convert Koku, Build, Error Fix** sono **Turn Procedures** (non Retainer Order Actions) e possono essere tutti eseguiti nello stesso turno se legali

### 6.3 Carte face-down (placeholder Numbered + trappole)
- Solo le carte **Numbered** possono essere piazzate face-down come placeholder nascosti
- Alcune **Retainers** (es. Shinobi e Ronin) possono essere piazzate face-down come trappole
- Una Numbered face-down ├¿ un placeholder nascosto **senza numero attivo** finché resta face-down
- Finché è face-down, una Numbered placeholder **non** crea conflitti Sudoku (duplicati in riga/colonna/zona)
- Se una face-down ├¿ in cima a uno spazio/pila, occupa lo spazio e conta come clan per i controlli
- Le carte face-down non possono essere piazzate nelle **Imperial Zones**
- Le face-down possono essere piazzate sopra **Retainer/Special** se lo stacking ├¿ altrimenti legale
- Le trappole face-down non sono identificabili finché un giocatore non paga il costo Reveal
- Nessun giocatore (nemmeno il proprietario) può guardare una carta face-down senza pagare Reveal, salvo effetto carta che lo permetta esplicitamente
- Quando una face-down viene rivelata, si gira face-up e si applica immediatamente la sua identità normale
- Se una Numbered rivelata crea ora un duplicato proibito, genera immediatamente un **Error**
- Quando una Shinobi o Ronin face-down viene rivelata, risolvi l'effetto trappola una volta, poi rimuovi la carta dalla mappa e scartala
- Se per errore viene piazzata face-down una carta non ammessa, girala subito face-up (senza costo) e continua
- Le face-down non possono ricevere Protection token
- Una **Capital** viene sempre piazzata su una base face-down (già face-down o girata face-down durante il piazzamento)
- Finché la Capital resta sopra, la carta base sotto non può essere attaccata, rivelata o distrutta da effetti

### 6.4 Chiarimento furto token
- Gli effetti che rubano token prendono di mira token attualmente sul tabellone (inclusi token sul Daimyo se presenti lì)
- Se un effetto dice "1 da ogni clan" e sul tabellone non ci sono abbastanza bersagli validi, i token mancanti vengono presi dalla Player Supply di quel giocatore
- I Protection token rubati vengono piazzati/usati subito secondo l'effetto che li ruba e **non** si convertono mai in Koku

---
## 7) REGOLE DI PIAZZAMENTO CARTE
Quando piazzi una carta dalla mano, rispetta sia il testo carta sia i vincoli Sudoku.

Regole:
- I **Daimyo** non possono condividere riga, colonna o zona con altri Daimyo
- Le **Numbered** non possono duplicare numero nella stessa riga, colonna o zona
- Le **Numbered face-down placeholder** non hanno numero attivo finché nascoste, quindi non creano duplicati finché non vengono rivelate
- Le **Retainer** possono coesistere in riga/colonna/zona, salvo restrizioni specifiche del testo

Se nessun piazzamento valido ├¿ possibile:
- Scarta una carta
- Continua il turno con eventuali altre azioni legali non di piazzamento

Stacking:
- ├ê consentito su Numbered, Retainer, placeholder Numbered face-down e trappole Shinobi/Ronin face-down
- In una pila, ├¿ attiva solo la carta in cima per controlli/sudoku; se la cima ├¿ face-down, vale solo il clan finché non viene rivelata
- Se la carta in cima viene rimossa, la carta sotto diventa attiva subito
- Le carte sotto rivelate possono creare Error immediati da risolvere
- Non c'è limite massimo all'altezza della pila

---

## 8) ERRORS - REBELLIONS
Un **Error** ├¿ uno stato illegale del tabellone (di solito duplicati Numbered proibiti in riga/colonna/zona).

### 8.1 Rilevazione immediata
- Se un piazzamento illegale viene notato durante il turno del giocatore attivo, qualsiasi giocatore può segnalarlo **prima che il turno venga passato**
- In questa finestra immediata, il giocatore attivo deve correggere subito il piazzamento (spostando la carta in una posizione legale o scegliendo un'altra giocata/carta legale)
- Se il giocatore attivo cambia la carta giocata, la carta tentata illegalmente **non si perde** e torna in mano
- Questa correzione immediata **non** assegna ricompensa

### 8.2 Correzione Rebellion (sul proprio turno)
- Nel tuo turno puoi dichiarare e correggere uno o più Error già presenti sul tabellone
- Chi corregge sceglie l'ordine di rimozione e quale/i carta/e in errore rimuovere
- Se una correzione rivela un altro Error, lo stesso giocatore può continuare a correggere nello stesso turno

### 8.3 Effetti di risoluzione e ricompensa
- Le carte rimosse in errore perdono anche protection/building attaccati
- Il giocatore che corregge guadagna **1 Protection token per ogni Error corretto**
- Se una sola rimozione di carta risolve più Error contemporaneamente, guadagni **1 Protection token per ciascun Error risolto**
- Ogni Protection token guadagnato deve essere piazzato **immediatamente** su una carta face-up legale ed eleggibile
- Se non esiste un piazzamento legale sulla mappa, il token può essere parcheggiato nella **Daimyo reserve** (max 3)
- Se non esiste un piazzamento legale ├¿ e la Daimyo reserve ├¿ piena, quel token si perde e torna in supply

### 8.4 Tradimento / coordinazione
- Giocare un Error intenzionale può essere una scelta tattica
- Giocatori alleati possono coordinarsi sul timing degli Error
- Tuttavia tutti i giocatori possono comunque segnalare un Error immediatamente prima del passaggio turno

Regola:
- Non esiste una penalità diretta extra per il piazzamento illegale intenzionale, oltre alla rimozione in correzione e al trasferimento di vantaggio a chi corregge

---

## 9) CARTE E TOKEN (SEMANTICA DI GIOCO)
Semantica stretta:
- **Koku** = valuta
- I token piazzati sulla mappa = **Protection token**

Regole:
- Un token piazzato su una carta la protegge
- Le carte protette non possono essere rimosse direttamente, salvo effetti che rimuovono la protezione prima o la bypassano esplicitamente
- In pila, la protezione vale per lo strato superiore visibile
- Lo stacking ├¿ consentito su Numbered, Retainer, placeholder Numbered face-down e trappole Shinobi/Ronin face-down
- I Protection token non possono essere piazzati su carte face-down (per azione, effetto o correzione)
- Una Capital deve essere piazzata sopra una base face-down e funge da protezione per quella pila
- I Protection token possono essere piazzati solo su Numbered o Retainer non già protette (max una piece per carta: 1 token, oppure 1 Market, oppure 1 Castle)
- Il Daimyo può tenere fino a 3 Protection token nella reserve; non sono Koku e non rendono il Daimyo "protetto"
- I token da correzione Error possono essere parcheggiati sul Daimyo solo se il piazzamento immediato in mappa ├¿ impossibile; se la reserve ├¿ piena, l'eccesso si scarta

### Daimyo (richiamo in questo capitolo)
- Il Daimyo viene piazzato sul Game Board durante Junbi e poi resta sulla mappa
- Può tenere fino a 3 token build riservati (solo Protection token) negli slot reserve; non danno protezione automatica
- I token riservati possono essere rimossi da effetti carta (es. steal/kill) se bersagliati legalmente
- I Koku **non** vanno mai sulla carta Daimyo

Termini usati in questo capitolo:
- **Adjacent**: contatto orizzontale, verticale o diagonale
- **Connected**: contatto orizzontale o verticale (no diagonale)
- **Chain of Command**: gruppo connesso che include il tuo Daimyo

Regola:
- Durante correzione Rebellion/Error, se una carta protetta in errore viene rimossa, si rimuovono insieme carta e protection/building attaccati

---

## 10) TIPI DI TOKEN
Il sistema separa chiaramente valuta e risorsa di mappa.

### 10.1 Koku
- I Koku sono la valuta principale (token fisici)
- Restano nell'area Player Board (non su carte in mappa)
- Si spendono per azioni specifiche (es. Reveal) e si possono convertire in Protection token
- Il cap di conteggio e il cap di storage sono separati:
  - il conteggio economico di fine turno genera al massimo **5 Koku** da fonti di conteggio
  - il cap di Koku conservati ├¿ **6**; tutto ciò che supera 6 si scarta

### 10.2 Protection Tokens
- Si piazzano su carte della mappa
- Forniscono difesa e progressione build per Castle/Market
- Vengono generati convertendo Koku durante il tuo turno
- **Turn Procedure - Convert Koku**: puoi convertire qualsiasi quantità di Koku al tasso **2 Koku -> 1 Protection token**

### 10.3 Daimyo Reserve (reserve solo Protection)
- La carta Daimyo può tenere fino a 3 Protection token in reserve
- I token nella Daimyo reserve restano Protection token (non Koku)
- La Daimyo reserve non protegge automaticamente il Daimyo
- I token in reserve possono essere usati nella conversione build quando consentito dalle regole build

### 10.4 Player Supply (componenti fuori mappa)
- Ogni giocatore tiene una supply personale vicino alla Player Board (Protection token, Koku, Castle, altri componenti fuori mappa)
- I Koku dovrebbero normalmente restare nell'area Player Board; non vanno su carte mappa o sul Daimyo
- Se un effetto ruba Protection token e il bersaglio non ne ha abbastanza in mappa, il resto viene preso dalla sua Player Supply

### 10.5 Alliance Tokens (Expert Mode)
- I token alleanza marcano alleanze attive e si mettono sul Daimyo
- Un Alliance token ├¿ un Protection token del colore dell'alleato
- Non ├¿ spendibile come Protection token normale finché è usato come marker alleanza
- Se un Alliance token viene rimosso, l'alleanza finisce immediatamente

Regola:
- Rompere/rimuovere un Alliance token non assegna bonus automatici all'attaccante, salvo effetto carta esplicito

### 10.6 Riferimento rapido: spendere Koku vs spendere Protection
**Spendere Koku (valuta):**
- **Reveal (Bribery): 3 Koku** per rivelare una carta face-down (anche tua)
- **Convert to Protection (Turn Procedure): 2 Koku -> 1 Protection token** (quantità libera)

**Spendere/usare Protection token (risorsa di mappa):**
- **Difesa**: piazza 1 Protection token su una carta face-up eleggibile (max 1 piece per carta)
- **Progressione build**: impegna/rimuovi **3 Protection token** per creare **1 Castle o 1 Market** (secondo regole build)
- I Protection token **non** sono valuta e **non** si riconvertono in Koku

---

## 11) DIFESE
La difesa è a strati: Protection token, Castle, Capital e Retainer interrupt.

Strati difensivi:
- Protection token: primo strato difensivo
- Castle: struttura difensiva forte e passo verso la Capital
- Capital: difesa strutturale più alta e requisito per Shogun candidacy
- Retainer interrupt (es. Samurai-like): difesa reattiva contro azioni chiave

Regole:
- Nelle pile, la protezione fornita da building si applica alla carta in cima in quel momento
- Se un Error rimuove lo strato superiore con un building, il building viene rimosso insieme a quello strato
- Le Imperial Zones non possono essere protette con Protection token

---

## 12) COSTRUIRE CASTLE E MARKET
Le costruzioni si creano tramite progressione di Protection token, non acquistando direttamente con Koku.

### 12.1 Requisiti base
- 3 Protection token disponibili su carte connesse nella tua Chain of Command
- Almeno una carta Numbered connessa valida disponibile come destinazione

### 12.2 Processo
- Rimuovi i 3 token "committed"
- Piazza 1 **Castle** o 1 **Market** su una carta **Numbered** eleggibile nella tua Chain of Command, che non abbia già un building (Castle/Market/Capital)
- La destinazione può essere **qualsiasi** Numbered connessa eleggibile; non deve per forza essere una delle carte che hanno fornito i token

### 12.3 Regola di conversione obbligatoria
- La conversione automatica è **obbligatoria solo** se hai almeno 3 Protection token su **Numbered connesse** e c'è una Numbered connessa valida come destinazione
- Rimuovi qualsiasi 3 token eleggibili dalla tua chain connessa (caso comune: 3 token su 3 Numbered)
- I token committed possono venire da Numbered, Retainer e Daimyo reserve, ma la destinazione build deve essere sempre una Numbered connessa valida
- Se i 3 token committed includono uno o più token da Retainer e/o Daimyo reserve, la conversione è legale ma **non obbligatoria**

### 12.4 Chiarimenti su pile e rimozione
- Un Castle protegge lo strato superiore di una pila
- Se un Error rimuove lo strato superiore, il Castle viene rimosso con esso; gli strati inferiori restano e vengono controllati normalmente
- Il Market segue gli stessi vincoli di piazzamento del Castle
- Difensivamente, il Market si comporta come uno strato di protezione e può essere rimosso da effetti Retainer legali o da correzione Error

### 12.5 Limiti e caso "4o Castle"
- Max 3 Castle per giocatore
- Max 1 Market per giocatore
- Se una conversione a Castle creerebbe un **4o Castle**, puoi rilocare uno dei tuoi Castle esistenti su una Numbered connessa legale
- Se non esiste una rilocazione legale, la conversione a Castle **non** si risolve e i token restano al loro posto
- Se in qualsiasi momento hai 3 Castle connessi, la conversione a Capital resta obbligatoria (vedi Sezione 13)

### 12.6 Restrizioni Imperial Zones
- Nelle Imperial Zones non si può costruire alcun Castle/Market/Building

---

## 13) FORMARE UNA CAPITAL
La Capital ├¿ il passo finale della progressione strutturale.

Requisiti:
- 3 Castle nella tua Chain of Command
- Connessione continua al Daimyo

Processo:
- Il piazzamento della Capital ├¿ **obbligatorio**: quando completi il terzo Castle connesso, rimuovi i 3 Castle e piazza 1 Capital
- La Capital va sempre su una base face-down
- Se la base scelta ├¿ una Numbered face-up connessa, girala face-down prima di piazzare la Capital
- Se c'è già una carta face-down nella posizione Capital connessa (anche una trappola nascosta), usala direttamente come base
- Finché la Capital resta sopra, la carta base sotto ├¿ bloccata e non può essere attaccata, rivelata o distrutta da effetti

Regole di connessione:
- Se uno dei Castle richiesti si disconnette, la conversione a Capital non può avvenire finché la connessione non viene ripristinata

Gestione conteggio Castle:
- In situazioni di disconnessione, il giocatore può ricostruire una linea di Castle connessi prima della conversione
- Il giocatore **non** può ritardare la conversione una volta che 3 Castle connessi sono validi

Regole aggiuntive:
- Il ruleset corrente usa un solo percorso Capital attivo (max 1 stato Capital attivo per giocatore per la progressione Shogun)
- I Castle disconnessi non contribuiscono alla progressione Capital
- Per recuperare progressione, il giocatore può:
  - riconnettere la chain
  - e/o creare un nuovo Castle connesso rilocando un Castle esistente (vedi gestione limite Castle in Sezione 12)

---
## 14) ATTACK ACTIONS
Gli attacchi si risolvono tramite:
- Retainer actions
- correzione Error
- trappole / Reveal
- effetti carta che colpiscono carte/token/strutture

Ambito:
- Gli effetti validi possono bersagliare carte, protezioni e strutture secondo il testo carta
- Le Retainer possono colpire Numbered e, se specificato, altri tipi di carta

Ordine di risoluzione:
- Risolvi gli effetti uno alla volta, in ordine di gioco
- Applica completamente un effetto prima di passare al successivo

Sacrifice volontario:
- Nel tuo turno puoi rimuovere un tuo Castle o Capital e riportare il pezzo in supply
- Usalo solo per riposizionamento o recupero catena quando strategicamente necessario

Regole:
- Non esiste un sotto-step "dichiara tutti gli attacchi poi risolvi"
- Gli effetti di attacco si risolvono sempre in modo sequenziale, uno alla volta

---

## 15) DIVENTARE SHOGUN (CANDIDACY + CONFERMA)
Un giocatore che completa una Capital connessa diventa **Shogun Candidate**.
Lo status di Shogun viene confermato più tardi durante i controlli di endgame.

### 15.1 Dichiarazione di Shogun Candidacy (durante il tuo turno)
1. Completa una Capital connessa alla tua Chain of Command
2. Dichiara immediatamente la tua candidacy come Shogun (**obbligatorio**, non puoi saltare)
3. Inizia il **Final Cycle**: tutti gli altri giocatori fanno un ultimo turno in ordine
4. Durante il Final Cycle, se la tua Capital si disconnette dalla Chain of Command, la tua candidacy diventa invalida salvo riconnessione prima della conferma

### 15.2 Sequenza endgame
- Questo round finale si chiama **Shogunate Final Cycle**
- Quando inizia il Final Cycle, tutte le alleanze attive si rompono immediatamente e i token alleanza tornano al pool token scartati
- Durante il Final Cycle, altri giocatori possono soddisfare la condizione Capital e dichiarare Shogun candidacy

### 15.3 Candidate Confirmation (solo Koku)
Dopo che tutti gli ultimi turni sono completati:
- Risolvi un **Candidate Confirmation step** in ordine turno, partendo dall'anchor
- Solo i giocatori che in quel momento hanno una Capital valida e connessa possono agire
- In questo step, i candidati validi possono spendere **solo Koku** per effetti legali basati su Koku
- I giocatori senza Capital valida e connessa non agiscono
- Quando arriva il timing di conferma di un candidato, se la sua Capital ├¿ ancora valida e connessa, il giocatore ├¿ **confirmed Shogun**

### 15.4 Finestra azioni finali
- Gli Shogun Candidates possono ancora usare Retainer difensive/interruption legali durante lo Shogunate Final Cycle, quando una carta/regola apre una finestra
- I Koku possono ancora essere spesi per Reveal o scelte difensive legali durante lo Shogunate Final Cycle

Regola:
- La conferma Shogun dipende dalla validità della Capital al momento della conferma del candidato

---

## 16) ALLIANCES (EXPERT MODE)
Le Alliances fanno parte dell'Expert Mode (insieme a Visit the Emperor e Destiny Path).

Formazione:
- Le alleanze si formano secondo le condizioni Expert stampate sulle player board
- Quando si forma un'alleanza, si mette un token alleanza sul Daimyo come marker del patto

Regole token alleanza:
- Il marker alleanza ├¿ un Protection token del colore dell'alleato, piazzato sul Daimyo
- Finché è usato come marker alleanza, non può essere speso o mosso come Protection token normale salvo effetto che lo rimuova esplicitamente

Effetti:
- Effetti e vincoli dell'alleanza si applicano secondo il testo Expert corrente della player board
- Lo stato dell'alleanza ├¿ informazione pubblica

Rottura alleanze:
- Se un Alliance token viene rimosso da un effetto, l'alleanza termina subito
- Rompere un'alleanza non assegna bonus automatici salvo effetto esplicito

Regole:
- Le Alliances valgono solo in Expert Mode; in Standard Mode questa sezione si ignora
- Se questa sezione ├¿ in conflitto con testi più vecchi, il testo Expert della player board ha priorità
- In Expert Mode 5-6 giocatori (9x9), ogni giocatore può mantenere al massimo **2 alleanze simultanee**

---

## 17) VISIT THE EMPEROR (EXPERT MODE)
Visit the Emperor ├¿ una regola Expert e si usa insieme a Alliances e Destiny Path.

Effetto base:
- Fornisce un flusso di reset/reshuffle del mazzo tramite il diritto Emperor Visit del giocatore
- Il reshuffle può essere usato una sola volta per partita
- Lo stato del marker Emperor (disponibile / usato / perso) deve essere visibile a tutti

### 17.1 Gestione esaurimento mazzo (caso automatico)
Alla **prima** volta che il mazzo si esaurisce durante una **pesca obbligatoria** (inizio/fine turno o effetto):
- Se il diritto Emperor Visit ├¿ inutilizzato, esegui un normale reshuffle (scarti -> nuovo mazzo)
- In questo caso automatico, il diritto Emperor Visit viene perso immediatamente e il marker viene girato nello stato usato/perso
- Se succede durante il refill di inizio turno, risolvi prima questa procedura automatica; dopo, in quel turno non puoi dichiarare un Visit the Emperor proattivo
- Se il mazzo si esaurisce di nuovo, non c'è un secondo reshuffle disponibile
- Dopo l'unico reshuffle consentito, i giocatori pescano normalmente dal mazzo rimanente; se non ci sono carte, non pescano

Regola:
- Uso Emperor e stato marker devono essere sempre visibili

### 17.2 Uso proattivo di Visit the Emperor
Regole:
- Può essere dichiarato **solo** all'inizio del tuo turno, **dopo** il refill iniziale e **prima** della prima carta giocata
- Il marker Emperor deve essere ancora inutilizzato
- Nel Visit proattivo, il giocatore rimescola mazzo+scarti e può opzionalmente includere **tutta la mano** (tutte le carte in mano, oppure nessuna)
- Se include tutta la mano, pesca subito di nuovo fino a 3 carte dopo il reshuffle
- Se non include la mano, questa azione non fornisce pescata aggiuntiva
- Dopo l'uso proattivo, gira il marker Emperor su "usato"; non può più essere usato
- Fuori da questa finestra (metà turno, fine turno, risoluzione effetti), l'uso proattivo non ├¿ consentito

Nota:
- Trattalo come pressione di timing/gestione risorse Expert, non come azione base

---

## 18) STRUTTURA DEL TURNO
Un turno ha tre sezioni.

### 18.1 Inizio turno
- Pesca/ricarica fino a **3** carte. Se ne hai già 3, peschi 0
- Questo refill iniziale serve a recuperare eventuali perdite mano causate fuori turno
- Timing Expert: se il marker Emperor ├¿ inutilizzato, puoi dichiarare Visit the Emperor ora (dopo refill, prima della prima carta giocata)

### 18.2 Sezione principale
- Gioca carte fino a scendere a 2 carte in mano
- Puoi giocare una carta finale aggiuntiva pagando **1 Koku** (finendo con 1 carta in mano)
- **Turn Procedure - Convert Koku** (2 Koku -> 1 Protection token, quantità libera), poi piazza Protection token
- Costruisci Market/Castle/Capital quando soddisfi i requisiti
- **Reveal (Bribery)**: paga 3 Koku per rivelare una face-down (anche tua)
- Opzionale: correggi Error, fai/rompi alleanze (Expert), dichiara Shogun candidacy quando valida

### 18.3 Fine turno
- Pesca/ricarica fino a **3** carte per il turno successivo
- Raccogli Koku/risorse
- Passa il turno in senso orario

Regole:
- Le azioni complete di correzione Error e l'esecuzione azioni avvengono solo nella sezione principale
- **Retainer Order Actions** e **Turn Procedures** sono sistemi separati
- Reveal, Convert Koku, Build ed Error Fix possono tutti avvenire nello stesso turno se legali (nessun limite globale "action points")
- I giocatori fuori turno possono comunque segnalare un piazzamento illegale immediato prima del passaggio turno, e il giocatore attivo corregge subito (senza reward)
- Durante la fine turno non si eseguono nuove azioni e i Koku sono solo raccolti/applicati
- La Player Board ├¿ solo quick reference per economia; timing/cap/edge case seguono questo regolamento
- Riepilogo economia: a fine turno guadagni Koku da base income, Market, Zone/Line controllate, Imperial Zones controllate
- Income da Zone e Imperial Zones si somma
- **Esempio**: se controlli tutte e 4 le Imperial Zones e anche 1 Zone, guadagni **+5 Koku** da queste due fonti (4 + 1)
- Il conteggio economico di fine turno genera al massimo **5 Koku** da fonti di conteggio
- L'income da tutte le fonti valide è obbligatorio; non puoi saltare fonti per evitare spreco del cap
- I Koku oltre il cap di storage 6 vengono scartati
- Se il mazzo finisce:
  - **Standard Mode**: reshuffle degli scarti come nuovo mazzo
  - **Expert + Visit the Emperor**: alla prima pesca obbligatoria con mazzo vuoto, stesso reshuffle normale e il diritto Emperor viene segnato come perso se era inutilizzato
- In flusso normale, il refill di fine turno riporta già la mano a 3; il refill di inizio turno spesso pesca 0 e serve soprattutto per recuperare perdita mano fuori turno
- Reazioni fuori turno sono consentite solo se una carta/regola apre esplicitamente una finestra di reazione

---
## 19) END GAME SEQUENCE (STANDARD)
L'endgame inizia quando un giocatore dichiara **Shogun candidacy** con una condizione Capital valida e connessa.

Trigger Shogun:
- 1 Capital connessa ├¿ sufficiente

Anchor del round finale:
- Il primo giocatore che dichiara Shogun candidacy ├¿ l'**anchor player**
- Dopo la dichiarazione, tutti gli altri giocatori fanno un ultimo turno in ordine

Dichiarazioni multiple:
- Altri giocatori possono soddisfare la condizione Capital e dichiarare Shogun candidacy durante lo Shogunate Final Cycle
- Tutti i candidati che hanno ancora una Capital valida e connessa al timing di conferma sono considerati nel punteggio

Interazione nella fase finale:
- Interruption stile Samurai sono consentite nello Shogunate Final Cycle solo come reazioni difensive legali
- Se la validità chain/capital viene rotta prima della candidate confirmation, la candidacy del giocatore colpito ├¿ invalida finché non si riconnette

Candidate confirmation / chiusura:
- Dopo il Final Cycle di tutto il tavolo, risolvi il **Candidate Confirmation step (Koku-only)** in ordine turno a partire dall'anchor
- Solo i giocatori con Capital valida e connessa in quel momento agiscono in questo step e possono spendere Koku su effetti legali basati su Koku
- Quando il Candidate Confirmation step termina, il punteggio inizia immediatamente

Regole:
- Dichiarare Shogun candidacy ├¿ obbligatorio quando completi una Capital connessa
- Un giocatore può perdere e recuperare la candidacy se perde/riconnette la validità chain+Capital prima della candidate confirmation

---

## 20) PUNTEGGIO FINALE (STANDARD)
Il punteggio usa il controllo connesso rispetto alla Chain of Command di ciascun giocatore.

Punteggio:
- +1 per ogni carta Numbered o Retainer **face-up** sul tabellone
- +1 per ogni zona completa o linea completa sotto il tuo controllo
- +1 per ogni Castle
- +3 per ogni Capital
- +4 se il giocatore ├¿ **confirmed Shogun**
- +1 (Expert Mode) se il giocatore non ha mai usato il diritto Emperor reshuffle
- Se il diritto Emperor ├¿ stato perso automaticamente per esaurimento mazzo durante pesca obbligatoria, conta come "usato" (quindi niente +1 bonus)

Definizione di controllo:
- "Sotto il tuo controllo" significa che la zona/linea ├¿ interamente occupata da carte del tuo clan (le face-down contano comunque come clan)
- In una pila, il controllo ├¿ determinato solo dalla carta in cima; una top face-down conta come clan
- La Chain of Command usa connessione ortogonale (no diagonali)

Regole face-down:
- Le carte face-down **non** danno il +1 diretto come carta
- Le face-down **contano** comunque per il controllo di zone/linee se appartengono al tuo clan

Regola di connessione:
- Contano punti solo carte/strutture connesse
- Carte disconnesse, Castle e Capital non fanno punti finché non vengono riconnesse

Punteggio token alleanza:
- Gli Alliance token non danno punti diretti di default
- Contano solo tramite effetti alleanza, salvo effetti specifici

Nota tattica:
- Diventare Shogun Candidate non garantisce la vittoria

---

## 21) JUNBI (FASE DI PREPARAZIONE)
**Junbi** ├¿ la fase iniziale di piazzamento dei Daimyo.

Passi:
1. Determina il primo giocatore
2. Il primo giocatore piazza il Daimyo in una posizione iniziale legale sul bordo
3. Gli altri piazzano in senso orario rispettando le restrizioni Daimyo (no stessa riga, colonna o zona rispetto ai Daimyo già piazzati)
4. Quando tutti i Daimyo sono piazzati, inizia il flusso normale di gioco

Chiarimenti setup:
- Durante il setup, ogni carta Daimyo ├¿ parcheggiata vicino/sulla Player Board fino al suo turno di piazzamento Junbi
- Junbi usa solo piazzamento Daimyo
- Il piazzamento iniziale di Numbered **non** fa parte di Junbi nel ruleset corrente

Posizioni iniziali (6x6):
- Posizioni iniziali valide (coordinate 6x6): **B1, D1, C1, E1, A2, F2, A3, F3, A4, F4, A5, F5, B6, C6, D6, E6**
- Le coordinate per 5x5 (Duels) e 9x9 sono diverse e vanno definite nelle rispettive setup diagrams
- Solo le posizioni elencate sono valide; gli angoli non sono validi

Regola fallback:
- Se un giocatore deve rifare il redraw per vincoli mano iniziale, rimischia e ripeti finché ottiene almeno una Numbered valida per il gioco normale

---

## 22) SENGOKU DUELS (2 GIOCATORI)
Sengoku Duels è la modalità dedicata a 2 giocatori.

### 22.1 Tabellone e setup
- Usa il tabellone 5x5 Duels ("The Challenge")
- Ogni giocatore sceglie un clan e prepara mazzo/componenti
- Separa il Daimyo, mescola il mazzo rimanente, poi pesca 3 carte
- Se la mano iniziale contiene 3 Retainer, rimischia e ripeti

### 22.2 Piazzamento iniziale
- Il primo giocatore piazza il Daimyo in uno spazio iniziale legale, poi piazza una Numbered connessa
- Il secondo giocatore fa lo stesso, rispettando le restrizioni piazzamento Daimyo (no stessa riga/colonna/zona del primo Daimyo)

Regola:
- Duels usa lo stesso modello offensivo basato su carte della modalità Standard

---

## 23) MODIFICHE REGOLE (DUELS)
Duels usa regole più strette di connessione e pressione sul tabellone.

### 23.1 Chain of Command
- Le carte devono restare connesse alla catena del Daimyo per restare pienamente attive
- Le carte disconnesse perdono punteggio e valore tattico finché non vengono riconnesse
- Gli edifici disconnessi non forniscono income/punteggio finché disconnessi

### 23.2 Regola del ponte centrale
- La zona ponte centrale fornisce +1 income se controllata e connessa
- Le carte possono essere piazzate li se legale
- Gli edifici non possono essere piazzati sullo spazio ponte

### 23.3 Economia e azioni
- Le regole base Koku/Protection restano attive
- I moduli Expert (Alliances / Visit the Emperor) sono opzionali e vanno attivati solo se entrambi i giocatori sono d'accordo prima del setup

Regole:
- Duels segue lo stesso ordine di risoluzione attacchi definito in Sezione 14
- Le carte disconnesse perdono subito gli effetti chain-based appena si disconnettono

---

## 24) END GAME (DUELS)
L'endgame Duels segue lo stesso principio di trigger Shogun della modalità Standard.

Trigger:
- Un giocatore dichiara **Shogun candidacy** quando soddisfa la condizione Capital attiva con connessione valida

Chiusura:
- Dopo la dichiarazione, l'avversario fa un ultimo turno
- Se l'avversario soddisfa la condizione Capital in quell'ultimo turno, entrambi i giocatori possono diventare Shogun Candidates
- Dopo quell'ultimo turno, risolvi il **Candidate Confirmation step (Koku-only)**:
  - possono agire solo i giocatori con Capital valida e connessa
  - agiscono in ordine
  - possono spendere solo Koku per effetti legali basati su Koku
- Dopo il Candidate Confirmation step, la partita finisce e si passa al punteggio

Regola tie-break Duels:
- Se il punteggio finale è in parità, si usa la regola globale: vince chi ha più Koku rimasti sulla Player Board
- Se c'è ancora parità, vittoria condivisa

---

## 25) PUNTEGGIO (DUELS)
Il punteggio Duels si basa su controllo connesso e valori stampati sul tabellone.

Punteggi:
- +1 o +2 per carte Numbered/Retainer sulle caselle punteggio marcate (come stampato sul tabellone Duels)
- +1 per ogni zona/linea completa controllata (se connessa alla chain)
- +1 per il controllo della zona ponte centrale
- +1 per ogni Castle
- +3 per ogni Capital
- +4 se il giocatore ├¿ **confirmed Shogun**
- +1 (Expert Mode) se il giocatore non ha mai usato il diritto Emperor reshuffle
- Se il diritto Emperor ├¿ stato perso automaticamente per esaurimento mazzo durante pesca obbligatoria, conta come "usato" (quindi niente +1 bonus)

Regole:
- Contano solo carte/strutture connesse, salvo effetto specifico contrario
- Le caselle Duels da +1 e +2 sono quelle stampate direttamente sul tabellone Duels

Nota tattica:
- In Duels, posizione e continuità della chain spesso rendono più della sola costruzione eccessiva
