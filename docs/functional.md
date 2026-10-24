# Guida funzionale

**Powered By RagazzoInGamba - Marco Laudati**

OpenPad deve togliere passaggi tra te e la partita. Questa guida descrive cosa fa l'app attuale, come interpreta gli stati e dove puoi intervenire quando serve.

La versione **0.5.0** aggiunge preparazione prima dell'avvio, input visivi, navigazione dal pad e verifica guidata. Le funzioni documentate del gioco, i dati ricevuti dal controller e gli effetti confermati da te rimangono informazioni distinte.

## Prima configurazione

Se i componenti necessari non sono pronti, l'app apre **Prima configurazione**. Vedi il numero dei componenti operativi e il dettaglio di ciascuno.

**Configura OpenPad** prepara il setup incluso di USB/IP e HidHide. Prima dell'esecuzione controlla hash, firma Windows e firmatario previsto; poi richiede la conferma amministratore. I setup gestiscono i prerequisiti Microsoft e possono richiedere Internet.

Il setup verifica i giochi aperti prima di modificare i driver. USB/IP può riconnettere gli hub USB: completa prima altri aggiornamenti e prevedi una breve riconnessione delle periferiche.

### Stati della configurazione

| Stato | Significato |
| --- | --- |
| Componente non installato | L'installer è nel pacchetto, ma quel driver non è ancora installato sul PC |
| Installato e operativo | Registrazione e controlli del componente risultano disponibili |
| Installato, non ancora operativo | Il pacchetto c'è; manca una conferma del funzionamento del driver |
| Configurazione in corso | Windows sta eseguendo il setup; attende l'esito prima di proseguire |
| Riavvio richiesto | Esiste una richiesta confermata del sistema o dell'installer |
| Riavvio da verificare | Una richiesta dell'installer è nota, ma l'avvio Windows attuale non è verificabile |
| Esito setup in attesa | Il risultato protetto del tentativo precedente non è ancora disponibile |
| Configurazione completa | Tutti i componenti richiesti sono operativi e non restano passaggi bloccanti |

L'installazione conserva l'eventuale richiesta di riavvio anche tra aperture dell'app. Il codice installer 3010 viene gestito come riavvio finale: il pacchetto indipendente successivo può essere completato prima del riavvio quando Windows non segnala nuovi blocchi. Il codice 1641, un errore o un nuovo blocco interrompono la catena.

**Riavvia Windows** compare per una richiesta confermata e agisce soltanto al tuo clic. Salva i lavori aperti prima di usarlo. Dopo il riavvio riapri OpenPad: riprende dalla verifica dei componenti, senza scambiare un nuovo avvio dell'app per un nuovo avvio del sistema.

Se il setup viene interrotto, l'app conserva l'identificativo del tentativo per recuperarne l'esito protetto. Un risultato assente rimane un'informazione da verificare; non diventa un successo o un'elevazione ripetuta automaticamente.

**Più tardi** permette di usare la compatibilità già disponibile nella sessione corrente. Alle aperture successive la prima configurazione torna se rimane incompleta. **Inizia a giocare** compare nella schermata iniziale quando la configurazione risulta completa.

## Panoramica

La panoramica riunisce il pad principale, il gioco riconosciuto o suggerito e i titoli recenti.

- Il controller mostra collegamento, batteria e modalità, quando i dati sono disponibili.
- **Gioca** prepara il profilo e verifica la disponibilità del controller prima dell'avvio dalla libreria.
- **Torna al gioco** prova a riportare in primo piano la partita già aperta, senza avviarne una seconda copia.
- Le schede recenti permettono l'avvio diretto dei titoli che hanno un punto di avvio affidabile.
- Gli avvisi di configurazione restano distinti dallo stato operativo del pad.

Se la finestra del gioco non può essere riportata in primo piano, l'app lo indica: puoi selezionarla dalla barra delle applicazioni Windows.

La modalità visualizzata è confrontata con lo stato del backend. Un controller virtuale richiesto ma non effettivamente disponibile viene indicato come **non operativo**. La sola presenza di un oggetto software o del pacchetto driver non viene usata come prova del funzionamento.

### Preparazione prima di Gioca

Prima di avviare il processo del gioco, OpenPad attende che i controller richiesti siano operativi: fino a **8 secondi con un pad**, più **4 secondi per ogni pad aggiuntivo**, con un massimo di **20 secondi**. Prepara i controller virtuali uno alla volta, verificando anche l'isolamento del pad fisico per evitare i doppi input prima di passare al successivo. Se rileva una nuova connessione durante la preparazione, può chiedere di riprovare quando il collegamento è stabile; non considera la sessione precedente una prova della nuova.

Se il controllo non riesce, compare **Prima di partire**, con il motivo concreto. **Riprova la preparazione** ripete la verifica. **Avvia comunque** apre il gioco con la compatibilità disponibile soltanto dopo il tuo clic: non trasforma la verifica fallita in un successo. Puoi controllare lo stato effettivo nella pagina **Controller**.

Questo controllo precede gli avvii richiesti attraverso OpenPad. Quando avvii direttamente da Steam o da un altro launcher, l'app riconosce il processo e applica il profilo dopo il rilevamento.

## Libreria e riconoscimento dei giochi

OpenPad legge le librerie Steam, i manifest Epic, le registrazioni GOG/Battle.net e i metadati o percorsi accessibili degli altri launcher supportati. Per Xbox esamina le cartelle `XboxGames` dei dischi fissi e i file di configurazione leggibili. La scansione è limitata: non forza l'accesso a cartelle protette e non percorre indiscriminatamente tutti i dischi.

Puoi cercare un titolo, filtrare per launcher e premere **Aggiorna**. La libreria viene aggiornata anche all'avvio e periodicamente; le schede conservano focus e opzioni aperte quando i dati del gioco non cambiano.

Le copertine provengono dalla cache Steam già presente. Per un'immagine non disponibile compare un'iniziale. Le immagini non determinano il riconoscimento del processo o la scelta del profilo.

### Avvio dalla libreria o dal launcher

Un titolo Steam viene aperto attraverso Steam. Per gli altri titoli OpenPad usa un eseguibile dichiarato da metadati affidabili o selezionato dall'utente. Non sceglie un file a caso tra benchmark, updater e strumenti del gioco.

Se l'avvio diretto non è disponibile, apri il titolo dal suo launcher. I giochi Xbox/GDK mantengono l'avvio nell'app Xbox o nel collegamento registrato Windows, così il runtime conserva l'identità richiesta.

Con **Aggiungi un gioco dal PC** selezioni un eseguibile concreto. Il percorso viene conservato separatamente dalle eccezioni: tornare ad Automatico non fa sparire il gioco aggiunto.

## La scelta automatica

L'interruttore **Scelta automatica** è acceso di default. L'app riconosce il processo reale del gioco e sceglie una modalità per ciascun controller, tenendo conto di modello, collegamento, catalogo e driver disponibili.

| Controller e contesto | Comportamento |
| --- | --- |
| Xbox/XInput | Resta nativo Windows |
| DualSense USB e titolo documentato nel catalogo per il supporto nativo | Resta nativo, con comandi ed effetti gestiti dal gioco |
| DualSense Bluetooth e titolo con supporto nativo Bluetooth documentato | Resta nativo; il riepilogo indica le sole funzioni documentate per quel collegamento |
| DualSense Bluetooth e titolo documentato via USB, con USB/IP operativo | Prova il percorso DualSense virtuale; la configurazione concreta richiede verifica |
| DualSense e titolo senza regola nativa documentata | Usa la compatibilità Xbox quando il driver necessario è disponibile |
| Driver necessario assente | Mantiene il pad nativo e spiega il limite |
| Altro HID senza backend dedicato | Rilevamento e supporto nativo del titolo, senza conversione dichiarata come disponibile |

Con più giochi aperti ha priorità quello riconosciuto in primo piano. Passare al desktop mantiene la partita attiva, se ancora aperta. Durante l'apertura di un launcher l'app conserva temporaneamente il gioco richiesto, ma un'altra partita portata in primo piano ha precedenza. Terminata la partita, viene ripristinata la modalità precedente di ciascun pad.

Per una **nuova sessione Xbox virtuale**, OpenPad preferisce ViGEmBus se è già disponibile; altrimenti usa USB/IP. La modalità **DualSense virtuale** richiede USB/IP. Una sessione virtuale già operativa mantiene il backend che sta usando, anche se viene rilevato un altro driver: non viene sostituita per inseguire una preferenza. Il setup dell'app installa USB/IP e HidHide quando necessari, senza aggiungere ViGEmBus.

### Cosa indicano le etichette

- **Supporto documentato:** esistono fonti del produttore nel catalogo per quel supporto. Non è una certificazione di ogni controller o PC.
- **Compatibilità standard:** viene scelto un percorso standard dei comandi; le funzioni avanzate del titolo restano da verificare.
- **Scelta personale:** hai salvato un'eccezione per il gioco.
- **Da configurare:** mancano condizioni necessarie o un backend specifico per il dispositivo.

In **Compatibilità e opzioni** trovi il motivo della scelta e l'eventuale eccezione. Le fonti disponibili sono mostrate nel suggerimento dell'etichetta di supporto.

Il catalogo contiene **14 regole**. Il riepilogo separa funzioni USB e Bluetooth e specifica quando un percorso virtuale resta da provare. Per esempio, Horizon Zero Dawn Remastered documenta la vibrazione Bluetooth, mentre aptica e altoparlante richiedono USB. L'elenco completo, le condizioni Steam Input e le fonti sono nella [compatibilità dei giochi](game-compatibility.md).

## Comandi originali ed eccezioni

Il profilo iniziale mantiene layout standard, zone morte e feedback del gioco. Non applica macro, overclock, frequenze imposte, curve personalizzate o cattura dell'audio di sistema. All'apertura nativa non forza profili LED o effetti dei grilletti.

In compatibilità Xbox, Cross=A, Circle=B, Square=X e Triangle=Y. Le azioni restano quelle assegnate dal titolo, comprese le personalizzazioni che avevi già salvato lì.

Per una scelta persistente su un gioco, apri **Libreria → Compatibilità e opzioni → Profilo per questo gioco**. Seleziona la modalità desiderata; **Automatico** ripristina la scelta consigliata. L'eccezione agisce sui pad per i quali il motore può cambiare modalità.

Per una modalità manuale del pad nella sessione corrente, spegni **Scelta automatica** e usa **Controller → Avanzate · modalità e dettagli → Applica**. Le eccezioni per titolo sono il percorso dedicato quando vuoi ricordare una scelta per le partite successive.

## Controller e protezione dai doppi input

La pagina **Controller** mostra famiglia, collegamento, batteria, modalità e stato del backend quando disponibili. Il disegno si aggiorna con tasti, direzioni degli stick e corsa dei grilletti ricevuti dal pad. I dati scaduti non restano presentati come pressioni attuali.

**Prova i tasti** mette il focus sul disegno: puoi provare i comandi senza attivare gli altri pulsanti dell'app. **Circle/B** esce dalla prova. Se il protocollo di input non è disponibile, l'app lo dice: aver rilevato il dispositivo non basta per dichiarare leggibili i tasti.

**Avanzate · modalità e dettagli** raccoglie firmware, frequenza dei report, dati testuali di input e scelta manuale della modalità. Gli Hz descrivono i report del dispositivo: non misurano la latenza dal tasto allo schermo. Per Xbox/XInput alcune informazioni possono non essere esposte da Windows; per un HID generico può mancare un backend di conversione.

**Apri Avanzate** apre una finestra dedicata ai DualSense gestiti: profili e rimappatura, varianti virtuali, audio e feedback, sensori, azioni e RGB. Le opzioni partono spente. Caricare o importare un profilo prepara una bozza, mentre **Applica** è l'azione esplicita che cambia la configurazione. Le modifiche capaci di riconnettere il controller vengono rinviate durante una partita o il setup. La [guida Avanzate](advanced.md) descrive priorità e limiti.

Un gioco può ricevere sia il controller fisico sia quello virtuale. HidHide serve a gestire questa visibilità. OpenPad nasconde il fisico soltanto quando la copia virtuale risulta operativa e conferma l'isolamento prima di dichiarare la protezione attiva.

Se il pad fisico resta visibile o lo stato è incerto, l'app lo segnala. Tornando al nativo, scollegando il controller o chiudendo l'app vengono rilasciate le regole create da OpenPad. Regole preesistenti dell'utente restano conservate. I programmi che avevano già aperto il pad possono richiedere una riapertura o una riconnessione.

## Verifica guidata del pad

**Verifica il pad** avvia una checklist sul primo controller con input leggibili. **Verifica questo pad**, nella scheda del controller, permette di scegliere il dispositivo concreto. Non cambia la disposizione dei comandi.

1. Premi i tasti e osserva quali si illuminano. La checklist conta i tasti distinti ricevuti: non dichiara provato l'intero pad dopo una sola pressione.
2. Muovi entrambi gli stick oltre metà corsa e premi quasi fino in fondo i due grilletti. Gli elementi passano a **Osservato** soltanto quando vengono ricevuti valori sufficienti.
3. Se vuoi verificare la riconnessione, scollega e ricollega il pad, poi premi un tasto. Per il passaggio USB/Bluetooth usa lo stesso controller nei due collegamenti.
4. Per la ripresa, sospendi e riattiva Windows durante la verifica, quindi invia nuovi comandi dal pad. Serve un evento di ripresa Windows: una pausa negli input non basta.
5. Con **Termina verifica** concludi la sessione. I passaggi non eseguiti rimangono **Da provare**; **Salva esito** scrive il riepilogo locale.

Riconnessione e passaggio USB/Bluetooth richiedono un'identità fisica affidabile e nuovi input. Se Windows non permette di riconoscere il medesimo pad, il passaggio resta **Non verificabile**. Il solo numero di uno slot XInput non identifica il controller fisico. Per la ripresa, l'assenza di un evento Windows o di input successivi lascia il passaggio da provare.

### Prove di vibrazione e grilletti

**Prova vibrazione** e **Prova grilletti** inviano un effetto breve solo su richiesta, fuori dalla partita e quando il backend lo consente. I pulsanti non sono disponibili durante la preparazione di un gioco o il setup; l'app verifica anche che non sia aperta una partita prima di inviare la prova.

Inviare un comando non dimostra che l'effetto sia stato percepito. Dopo la prova scegli **Conferma riuscita** oppure **Non percepito**. La checklist riporta **Confermato da te** o **Non percepito**, separatamente dagli input osservati. Una prova riuscita del pad non certifica l'aptica o i grilletti di uno specifico gioco.

### Report della verifica

**Salva esito** scrive `%LOCALAPPDATA%\OpenPad\hardware-check-latest.json`, sostituendo il riepilogo precedente. Include versione, credito, nome del controller, orari, passaggi osservati e conferme date dall'utente; esclude identificativi e percorsi dei dispositivi. Il file rimane sul PC e non viene caricato automaticamente.

Questo report può descrivere una verifica incompleta. Non è una misura della latenza, una certificazione hardware o la prova che tutti i collegamenti siano stati testati dagli sviluppatori.

## Usare l'app dal controller

La navigazione dal pad legge i comandi quando la finestra OpenPad è attiva e visibile. Non invia tasti globali a Windows o al gioco.

| Comando | Azione nell'app |
| --- | --- |
| Croce direzionale o stick sinistro | Sposta il focus tra i controlli |
| L1/R1 oppure LB/RB | Passa alla sezione precedente o successiva |
| Cross/A, tasto inferiore | Attiva il controllo selezionato, apre o chiude un menu |
| Circle/B, tasto destro | Torna indietro, chiude il menu o termina la prova tasti |
| Stick destro verticale | Scorre il contenuto |

I controlli visibili e disponibili sono raggiungibili dal focus, compresi interruttori, menu e sezioni espandibili. La ricerca testuale e la selezione dei file usano i normali strumenti di Windows. Nel disegno con focus di prova, i comandi rimangono destinati alla visualizzazione degli input fino all'uscita con **Circle/B**.

Configurazione driver, riavvio Windows e applicazione manuale della modalità mostrano una conferma aggiuntiva quando vengono attivati dal pad. Spostare il focus non esegue queste azioni.

## Stile e luci

In **Controller → Stile e luci** puoi applicare Supercar, Respiro blu o Arcobaleno sui DualSense supportati. Il preset iniziale è **Gioco · predefinito**, senza animazioni automatiche. Supercar combina rosso pulsante e scansione dei cinque LED bianchi; la barra RGB ha un solo colore alla volta.

La scelta è personale per il pad riconosciuto e viene salvata solo con **Applica effetto**. **Luci del gioco** ferma l'animazione. In **Dettagli effetto** trovi luminosità e **Pausa quando rilevo un gioco**, inizialmente attiva. Spegnendola scegli di mantenere i tuoi effetti anche in partita, con possibili sovrapposizioni ai colori del titolo.

L'anteprima è software e lo stato di invio non certifica l'effetto fisicamente visibile. Xbox e HID senza backend RGB restano indicati come non supportati per questa funzione. I comandi e il feedback del gioco non vengono rimappati dalle luci. Per ripristino dei colori, limiti e fonti leggi [Stile e luci](lighting.md).

## Background e chiusura

**Riduci in background** o la minimizzazione lasciano attivo il motore e nascondono la finestra nell'area di notifica. Da lì trovi **Mostra OpenPad** ed **Esci**. Un secondo avvio dell'app riapre la stessa istanza.

La **X** termina l'app: la conversione si ferma e il pad torna al funzionamento nativo. Non serve lasciare la finestra davanti al gioco, ma il processo deve restare aperto per le modalità virtuali.

## Impostazioni e dati locali

**Impostazioni** raccoglie configurazione dei driver, stato Windows, comportamento automatico, informazioni Bluetooth e apertura della cartella dati.

**Verifica stato** aggiorna i fatti osservati. **Dettagli della verifica** distingue richieste di riavvio confermate, operazioni di pulizia file e fonti non verificabili. L'ultimo tentativo di setup rimane separato dallo stato corrente.

Preferenze, giochi recenti, percorsi aggiunti, eccezioni, promemoria del setup e recupero della visibilità restano in `%LOCALAPPDATA%\OpenPad`. L'app non richiede accesso agli account dei launcher e non invia online la libreria. I report diagnostici possono contenere percorsi locali e informazioni dei dispositivi: controllali prima di condividerli.

Il report della verifica guidata è distinto dai report diagnostici generali e limita i dati agli esiti della sessione, senza identificativi o percorsi dei dispositivi.

Per comandi CLI, architettura e dettagli delle verifiche leggi la [documentazione tecnica](technical.md). Per i casi pratici consulta [Problemi e soluzioni](troubleshooting.md).
