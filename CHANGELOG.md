# OpenPad 0.7.4 — La mira e gli avvisi, al posto giusto

**Powered By RagazzoInGamba - Marco Laudati**

Call of Duty HQ e Modern Warfare (2019) hanno indicazioni dedicate per selezionare il controller nel gioco e mantenere i layout originali. Il suggerimento viene mostrato nelle informazioni del titolo e resta disponibile anche con compatibilità Xbox standard. Non modifica file, binding o preferenze di Call of Duty e non attribuisce al gioco effetti DualSense non verificati.

Corretto un problema distinto: il messaggio di un errore del motore poteva rimanere nella UI dopo la sua risoluzione. Il recupero ora rimuove il proprio avviso senza cancellare un messaggio successivo dell'app; la chiusura manuale dell'avviso continua a essere rispettata finché quell'errore non si risolve.

La diagnosi sul DualSense USB ha rilevato entrambi gli stick nello slot XInput usato per la prova. Il file locale di Call of Duty indicava inizialmente mira Mouse; successivamente il gioco ha registrato Controller, senza nostre modifiche ai file. La risposta effettiva della visuale attende ancora conferma dell'utente. Dettagli e limiti in [VERIFICATION.md](VERIFICATION.md).

**1.341 test superati** nell'esecuzione corrente: 507 OpenPad, 768 backend e 66 Updates. Il collaudo del gioco e quello dell'aggiornamento della nuova versione rimangono verifiche separate.

---

# OpenPad 0.7.3 — Anteprima con adattatore corretto

**Powered By RagazzoInGamba - Marco Laudati**

Questa release pubblica consolida il render completo e la correzione checksum verificata con il framework reale. La 0.7.2 è la baseline locale del collaudo; 0.7.0/0.7.1 richiedono il nuovo installer una volta. Per i nuovi utenti valgono installer, download autenticati e comandi originali di default.

**1.324 test superati**: 489 OpenPad, 769 backend, 66 Updates. Sono inclusi il download completo SDK e i controlli di riservatezza della diagnostica locale. Le prove del DualSense USB, di SteamWorld Dig 2 e del ciclo installer sono descritte in VERIFICATION.md.

---

# OpenPad 0.7.2 — Correzione della verifica SDK

**Powered By RagazzoInGamba - Marco Laudati**

Il collaudo reale ha trovato un confronto SHA-256 del framework sensibile alle maiuscole. Il manifest firmato resta canonico; solo l'adattatore Velopack normalizza il valore al formato atteso dal SDK. Nessun controllo di firma o integrità è stato rimosso.

Aggiunti test sul download completo tramite UpdateManager e una diagnostica locale che conserva solo tipo, fase, codice e motivo previsto, senza messaggi grezzi, URL o token. La suite Updates passa a 66 casi. Questa versione è la baseline locale corretta per il collaudo della release pubblica successiva.

---

# OpenPad 0.7.1 — Il render completo, dentro l'app

**Powered By RagazzoInGamba - Marco Laudati**

La verifica della panoramica ha individuato un'inquadratura troppo ampia: il nuovo render veniva tagliato dalla scheda. Ora il controller resta completo anche nel layout compatto. Mantiene tutte le funzioni della 0.7.0 e i comandi originali di default.

La 0.7.0 rimane la baseline locale dell'installazione di prova; il canale pubblico distribuisce la 0.7.1 con i sorgenti corrispondenti.

---

# OpenPad 0.7.0 — Più possibilità, stessi comandi di sempre

**Powered By RagazzoInGamba - Marco Laudati**

Colleghi il pad, apri il gioco. Per iniziare restano i comandi originali e la scelta automatica; tutto quello che vuoi personalizzare adesso ha una finestra **Avanzate** dedicata, spenta di default.

Trovi profili da salvare, copiare e condividere, rimappatura con combinazioni e più destinazioni, varianti DualShock 4 e DualSense, prove separate di motori e grilletti, audio WAV/MP3/FLAC, sensori e azioni speciali. Caricare un profilo prepara una bozza: per attivarlo lo controlli e premi Applica. Luci RGB, indicatori bianchi e spia microfono sono opzionali; gli effetti Supercar restano nella sezione semplice.

La panoramica usa un nuovo render DualSense generato con ImageGen, con trasparenza pulita e materiali più curati. Il riferimento grafico è stato tradotto nella schermata reale, con il controller più leggibile e i dettagli di compatibilità disponibili su richiesta. Il disegno illustrativo e i suoi colori restano distinti dagli stati live del pad.

Arriva l'**installer per utente**, con runtime, icona e pacchetti ufficiali dei driver. L'app installata controlla e scarica aggiornamenti autenticati dal progetto, poi li applica alla chiusura quando non risultano partite o setup in corso. Le preferenze rimangono separate dall'installazione. Il canale pubblico contiene anche i sorgenti della versione.

Abbiamo verificato il ciclo installazione → aggiornamento → disinstallazione, senza toccare dati personali o driver condivisi. Su questo PC abbiamo risolto un problema reale del percorso Windows cifrato usando la destinazione programmi dell'utente, senza cambiare la cifratura. Corrette anche la gestione dei file mono e una combinazione ViGEm/audio che poteva creare due endpoint.

**1.306 test superati**, più i due casi Linux esclusi su Windows. SteamWorld Dig 2 è stato riprovato: profilo scelto da solo, un solo controller e una sola azione per pressione confermata dall'utente. Provati anche creazione, isolamento e rimozione degli endpoint DualShock 4/DualSense USB/IP dal DualSense USB reale.

Questa è una release **Anteprima**. EXE e installer non hanno ancora un certificato Authenticode Windows; la firma degli aggiornamenti è una protezione distinta. Bluetooth, Edge e altri controller fisici richiedono ancora prove dedicate. [Verifiche e limiti](VERIFICATION.md).

[Scarica OpenPad](https://github.com/MarcoLaudati/OpenPad-Releases/releases/tag/v0.7.0) · [Avanzate](docs/advanced.md) · [Installer e aggiornamenti](docs/updates.md)

**Powered By RagazzoInGamba - Marco Laudati**

---

# OpenPad 0.6.0 — Supercar sul tuo DualSense

**Powered By RagazzoInGamba - Marco Laudati**

Ora puoi scegliere anche come si illumina il pad. In **Controller → Stile e luci** trovi **Supercar**, con rosso pulsante sulla barra e scanner avanti e indietro sui cinque piccoli LED bianchi. L'utente ha confermato entrambi gli effetti sul DualSense USB reale.

Ci sono anche **Respiro blu** e **Arcobaleno**, tre livelli di luminosità e la preferenza salvata per ciascun pad riconosciuto. L'anteprima nell'app è software; lo stato distingue invio, pausa ed errore.

Il default rimane **Gioco · predefinito**, senza animazioni personali automatiche. **Pausa quando rilevo un gioco** è inizialmente attiva: se vuoi mantenere il tuo effetto durante la partita, puoi disattivarla nei dettagli. **Luci del gioco** ferma l'animazione e rimuove la preferenza. L'app ripristina solo comandi luce precedenti che conosce davvero; non inventa il colore di un gioco nativo esterno.

La modifica riguarda i canali luce. Comandi, zone morte, vibrazione, grilletti, microfono e audio restano separati. Il backend RGB è dedicato ai DualSense supportati; Xbox e HID generici indicano il limite senza offrire un comando finto.

**424 test OpenPad e 762 test backend superati**, 2 casi Linux ignorati. Build senza errori o avvisi, controllo dei report USB/Bluetooth e prova fisica dello scanner USB completati. Bluetooth ed Edge richiedono ancora prove dedicate.

Scarica **OpenPad-0.6.0-win-x64.zip**, estrai tutto e apri `OpenPad.exe`. Sono disponibili anche **OpenPad-0.6.0-source.zip** e **SHA256SUMS.txt**. La [guida alle luci](https://github.com/MarcoLaudati/OpenPad-Releases/blob/main/docs/lighting.md) spiega i preset; [VERIFICATION.md](https://github.com/MarcoLaudati/OpenPad-Releases/blob/main/VERIFICATION.md) conserva prove e limiti.

**Powered By RagazzoInGamba - Marco Laudati**

---

# OpenPad 0.5.1 — il monitor resta vivo anche senza focus

**Powered By RagazzoInGamba - Marco Laudati**

Durante la prova pratica il disegno sembrava fermo; dopo aver portato OpenPad in primo piano, l'utente ha riferito che sembrava funzionare. La revisione ha individuato e corretto due limiti concreti del monitor:

- La vista dei comandi si aggiorna a circa 30 Hz finché la finestra è visibile, anche quando clicchi su un'altra app. La navigazione col pad resta riservata alla finestra OpenPad attiva.
- Se i report non sono attuali, il disegno mostra l'attesa anche mentre sei in **Prova i tasti**. La modalità di prova non copre più questa informazione.

Le quattro novità della 0.5.0 restano incluse: preparazione prima di Gioca, 14 regole documentate, verifica hardware guidata e navigazione dal pad, con comandi originali di default e Avanzate separate.

**393 test OpenPad superati**, inclusi 9 nuovi casi che verificano refresh visibile senza azioni in background, sospensione nei modali e rilascio dei tasti al ritorno. Il backend mantiene le verifiche della 0.5.0: 744 test superati, 2 casi Linux ignorati. Build desktop senza errori o avvisi.

Scarica **OpenPad-0.5.1-win-x64.zip** ed estrai tutta la cartella. Sorgenti corrispondenti e **SHA256SUMS.txt** accompagnano il pacchetto. Prove e limiti sono in [VERIFICATION.md](https://github.com/MarcoLaudati/OpenPad-Releases/blob/main/VERIFICATION.md).

**Powered By RagazzoInGamba - Marco Laudati**

---

# OpenPad 0.5.0 — il pad pronto, i comandi sotto gli occhi

**Powered By RagazzoInGamba - Marco Laudati**

Un altro passo verso quello che vogliamo: colleghi il pad e giochi, con i comandi originali. OpenPad ora aspetta che il percorso scelto sia pronto, mostra cosa riceve dal controller e ti accompagna nelle prove quando servono.

## Le quattro novità

- **Gioca prepara davvero il pad.** Attesa dell'endpoint osservato e della protezione dai doppi input, controller preparati in sequenza e recupero limitato. Se qualcosa manca trovi **Riprova la preparazione** e **Avvia comunque**, con il motivo visibile. Nessun cambio silenzioso da DualSense a Xbox.
- **14 giochi con regole documentate.** Dieci titoli aggiunti, fonti ufficiali e riepiloghi separati per USB, Bluetooth e modalità virtuale. Il catalogo distingue vibrazione, aptica, grilletti e altoparlante quando le fonti li documentano.
- **Verifica hardware guidata.** Tasti, stick, grilletti, riconnessione, cambio collegamento e ripresa dalla sospensione hanno esiti distinti. Le prove brevi degli effetti sono facoltative e fuori dalla partita; confermi tu ciò che senti. Il report resta sul PC e non contiene gli identificativi del pad.
- **L'app si usa anche dal controller.** Disegno del pad in tempo reale, navigazione, scroll e tastiera locale per cercare i giochi. I comandi già premuti al ritorno nell'app non fanno scattare azioni. Modalità manuali e dettagli tecnici sono in **Avanzate**.

Automatico resta acceso di default. Layout, zone morte e feedback originali del gioco restano i valori iniziali. Le finestre di autorizzazione e configurazione di Windows mantengono il loro funzionamento di sistema.

## Pacchetto e prove

Scarica **OpenPad-0.5.0-win-x64.zip**, estrai tutta la cartella e apri `OpenPad.exe`. Runtime, USB/IP e HidHide ufficiali sono inclusi. Completa l'eventuale riavvio richiesto dal setup. Trovi anche **OpenPad-0.5.0-source.zip** e **SHA256SUMS.txt**.

Build senza errori o avvisi, **384 test OpenPad + 744 test del backend superati**, 2 casi Linux ignorati. Verifica dell'interfaccia e ispezione degli screenshot completate. Bluetooth fisico, multipad e collaudo dopo il riavvio driver restano prove separate: implementato, documentato e provato sul PC sono esiti distinti.

Parti dalla [guida funzionale](https://github.com/MarcoLaudati/OpenPad-Releases/blob/main/docs/functional.md), dal [catalogo con le fonti](https://github.com/MarcoLaudati/OpenPad-Releases/blob/main/docs/game-compatibility.md) o dalla [documentazione tecnica](https://github.com/MarcoLaudati/OpenPad-Releases/blob/main/docs/technical.md). Il registro completo è in [VERIFICATION.md](https://github.com/MarcoLaudati/OpenPad-Releases/blob/main/VERIFICATION.md).

**Powered By RagazzoInGamba - Marco Laudati**

---

# OpenPad 0.4.3 — colleghi il pad, apri il gioco

**Powered By RagazzoInGamba - Marco Laudati**

Questa è la prima versione del progetto pubblicata nel repository OpenPad. L'idea è semplice: vogliamo giocare, senza passare la serata a scegliere driver, profili e rimappature. L'app prepara la compatibilità e lascia al gioco i suoi comandi.

## Cosa trovi

- App Windows x64 con runtime incluso, interfaccia dedicata e funzionamento in background.
- Controller, batteria, firmware, frequenza report e stato operativo leggibili quando disponibili.
- Libreria locale dei launcher, ricerca, titoli recenti, **Gioca** e **Torna al gioco**.
- Selezione automatica della modalità per ogni pad, con eccezioni facoltative per singolo gioco.
- Prima configurazione con USB/IP e HidHide ufficiali inclusi, controlli di integrità e conferma amministratore Windows.
- Ripresa del setup dopo il riavvio e distinzione tra componenti presenti, operativi e configurazione completata.
- Crediti nell'app, nella diagnostica, nei metadati Windows e nella documentazione.
- Guide funzionali e tecniche, sorgenti corrispondenti e controlli automatici di build e distribuzione.

## Per provarla

Scarica **OpenPad-0.4.3-win-x64.zip**, estrai tutta la cartella e apri `OpenPad.exe`. Premi **Configura OpenPad**, conferma Windows e completa l'eventuale riavvio richiesto dall'installer. Poi collega il pad e apri il gioco con la scelta automatica attiva.

Il file **OpenPad-0.4.3-source.zip** contiene i sorgenti e le istruzioni di compilazione. **SHA256SUMS.txt** permette di controllare i due archivi.

## Le verifiche, senza promettere miracoli

Build locale e documentazione rigorosa superate. **290 test OpenPad** e **742 test del backend** superati; 2 casi specifici Linux ignorati su Windows.

DualSense USB nativo e compatibilità Xbox tramite il fallback ViGEm sono stati provati. SteamWorld Dig 2 ha riconosciuto il profilo automatico; Cyberpunk USB ha ricevuto un riscontro positivo dall'utente. USB/IP e HidHide sono stati installati sul sistema di prova, ma la verifica pratica successiva al riavvio rimane aperta nella baseline.

Bluetooth fisico, altri modelli e funzioni avanzate richiedono ancora prove dedicate. Aptica, grilletti, audio e simboli dipendono dal supporto del gioco: OpenPad non può aggiungere effetti che il titolo non implementa.

Le prove e i limiti aggiornati sono in [VERIFICATION.md](https://github.com/MarcoLaudati/OpenPad-Releases/blob/main/VERIFICATION.md). Per partire: [README](https://github.com/MarcoLaudati/OpenPad-Releases#readme), [guida funzionale](https://github.com/MarcoLaudati/OpenPad-Releases/blob/main/docs/functional.md) e [documentazione tecnica](https://github.com/MarcoLaudati/OpenPad-Releases/blob/main/docs/technical.md).

OpenPad è GPL-3.0 e riusa il motore di DualSense Client. Autori e licenze originali sono conservati nei [crediti](https://github.com/MarcoLaudati/OpenPad-Releases/blob/main/CREDITS.md).

**Powered By RagazzoInGamba - Marco Laudati**
