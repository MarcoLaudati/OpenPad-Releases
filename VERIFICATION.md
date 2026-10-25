# Verifiche OpenPad

**Powered By RagazzoInGamba - Marco Laudati**

Baseline hardware iniziale: OpenPad 0.4.2, 24 ottobre 2026. Le verifiche successive sono separate per versione. Questo è il riepilogo pubblico delle prove, non una certificazione per qualsiasi pad, gioco o PC. I report originali restano locali perché possono contenere percorsi, identificativi dei dispositivi e dati della macchina.

## Aggiornamento pubblico reale 0.7.2 → 0.7.3

**Prova completata sul programma installato**, senza usare il pulsante di controllo manuale o quello di applicazione: il controllo automatico all'avvio ha letto il feed GitHub pubblico firmato, scaricato la 0.7.3 e dichiarato il pacchetto verificato e pronto. La normale X ha chiuso ordinatamente l'app; l'aggiornamento è stato applicato e il successivo avvio ha caricato `0.7.3+44a7ba1ee839e373d30ae399177beba52ef67eb4`.

I quattro file monitorati di preferenze, giochi, setup e opzioni avanzate sono rimasti identici nei loro SHA256, anche dopo l'installazione della baseline corretta. Nessun processo è stato terminato forzatamente, nessun installer driver è stato eseguito e Windows non è stato riavviato. I sette asset pubblici sono stati confrontati con i digest SHA256 calcolati da GitHub.

Ripetuti smoke e ispezione dell'interfaccia **installata**: panoramica, libreria, Controller, Impostazioni e cinque sezioni Avanzate; default avanzato disabilitato e credito presente. Il render completo è visibile nella schermata reale. La CI del codice `44a7ba1` è riuscita per build, test, installer, audit dei pacchetti e documentazione rigorosa.

USB/IP e HidHide risultano installati e operativi sul PC; la richiesta di riavvio finale dell'installer resta registrata fino a un vero riavvio Windows. Questa richiesta non viene cancellata dall'aggiornamento dell'app o dal successo della prova corrente.

## Adattatore aggiornamenti 0.7.2

La prova pubblica con il client originale ha riprodotto `ChecksumFailedException`: Velopack 1.2.161 calcola il testo SHA-256 maiuscolo e lo confronta con distinzione di maiuscole. Il manifest e la nostra verifica indicavano lo stesso hash minuscolo. Il successivo messaggio di estrazione mascherava l'errore iniziale.

Un secondo probe, sullo stesso pacchetto GitHub reale e in un locator isolato, ha normalizzato solo il valore dell'adattatore SDK: download completo, promozione del pacchetto, pending update e verifica firmata sono riusciti. La patch mantiene invariati RSA, hash del manifest e policy del pacchetto.

La suite Updates comprende ora **66 test**, inclusi due percorsi reali UpdateManager con HTTP controllato: il formato precedente fallisce senza pending update; quello corretto scarica, prepara e riverifica. Sedici test aggiuntivi verificano che la diagnostica locale escluda messaggi grezzi, stack, URL, percorsi e token. Con i 489 OpenPad e 769 backend, il totale è **1.324 test superati**, più i due casi Linux esclusi su Windows.

Le prime versioni con l'adattatore precedente richiedono un installer corretto prima di poter aggiornare automaticamente; non vengono modificate a caldo. La 0.7.2 è usata come baseline locale per la verifica del canale pubblico.

## Inquadratura e rilascio 0.7.1

La verifica visiva della panoramica ha rilevato che i margini negativi tagliavano il nuovo render nella scheda. La 0.7.1 usa margini interni positivi, con controller completo e stati live separati. Smoke della panoramica, libreria, Controller e Impostazioni ripetuto sulla 0.7.1; il render è stato ispezionato nella finestra reale.

La 0.7.0 è stata installata sul PC come baseline per l'aggiornamento reale verso la release pubblica. Il suo installer finale ha inoltre rifiutato la reinstallazione mentre l'app portatile era aperta, preservando processo e installazione. Le prove degli endpoint e del gioco qui sotto si riferiscono al motore condiviso con la 0.7.1.

## Avanzate, installer e aggiornamenti 0.7.0

- **489 test OpenPad, 769 test backend e 48 test Updates superati: 1.306 in totale.** Due casi Linux restano esclusi su Windows. I test comprendono profili disabilitati all'importazione, mapping e combinazioni, precedenza delle preferenze, ownership/cancellazione delle anteprime, varianti e feedback tipizzati.
- Corretto un rischio di doppio endpoint quando il bridge ViGEm aveva già creato Xbox e veniva abilitato l'audio avanzato: USB/IP resta spento per quell'endpoint, mantenendo l'inoltro richiesto. Quattro regressioni coprono il percorso.
- UI Automation e ispezione visiva delle cinque sezioni Avanzate: default disabilitato, credito esatto, telemetria ricevuta dal DualSense USB, preferenze immutate e chiusura delle sole anteprime della finestra. Nessuna azione di output invocata dallo smoke. Il controllo non è una misura dei report HID.
- **SteamWorld Dig 2 provato di nuovo con la 0.7.0:** avvio da OpenPad, profilo Xbox automatico senza eccezioni, un solo nuovo slot XInput, HidHide attivo e riconoscimento del pad nel log fresco del gioco. L'utente conferma una sola azione per pressione. All'uscita: ritorno Native, rimozione dello slot, HidHide disattivato e ripresa dell'effetto Supercar secondo lo stato software.
- **DualShock 4 e DualSense virtuali USB/IP provati con il DualSense fisico USB:** preparazione e isolamento riusciti; un osservatore HID Windows indipendente rileva un endpoint nuovo per ciascun modo e nessun residuo dopo il ripristino Native. Preferenze immutate. Questa prova non certifica gli effetti di tutti i giochi o il trasporto radio Bluetooth.
- Decoder MiniAudio reali: decodifica WAV, MP3 e FLAC, riconoscimento e riapertura in memoria. Corretto il percorso mono 22.050 Hz verso stereo 48.000 Hz. Nessun dispositivo di output aperto dai test. Il componente FFmpeg opzionale è escluso dall'app e conservato solo nella dipendenza della GUI upstream.
- Installer Velopack e bootstrapper NativeAOT: ciclo reale isolato **installazione 0.7.0 → aggiornamento 0.7.1 → disinstallazione**, con percorso dell'eseguibile e stub stabili, collegamenti creati/rimossi, dati di prova e preferenze reali conservati. Le registrazioni dei driver e l'app normale non sono state modificate dalla fixture.
- Nel percorso LocalAppData cifrato di questo PC i rename di directory falliscono. La destinazione per utente `LocalAppData\Programs\OpenPad.App`, passata con l'opzione ufficiale dell'installer, supera preflight e aggiornamento reale. Nessuna cifratura del profilo o dei dati è stata modificata; nessun copy/swap alternativo all'updater.
- Feed e pacchetti: RSA-PSS 3072, hash/dimensioni, identità/canale, architettura AMD64 reale, struttura ZIP e licenze; rifiuto di firma/pacchetto alterati e downgrade/replay. La suite usa HTTP simulato; la fixture installer usa un feed locale. Il canale pubblico e la verifica dell'installazione finale sono controlli separati della release.
- Catalogo licenze verificato per i pacchetti/runtime distribuiti, con hash e fonti fissate; rifiuto di dipendenze nuove non censite, testi alterati e DLL FFmpeg residue. Lo ZIP sorgenti include anche gli snapshot libVIIPER e HIDAPI corrispondenti ai pin nativi.

Resta una segnalazione di build **AVLN3001** per la finestra Avanzate: il loader per URI non ha un costruttore vuoto. La finestra viene creata con il motore condiviso e la sua apertura effettiva è coperta dallo smoke.

L'unico controller fisico disponibile per questi collaudi è DualSense via cavo. Bluetooth fisico, Xbox fisici, Edge, percezione dei nuovi preset/audio e matrice estesa dei giochi restano prove dedicate. Il successo degli endpoint USB/IP non cancella l'eventuale richiesta di riavvio finale dell'installer: quella viene verificata con l'avvio reale di Windows.

## Luci personali 0.6.0

- Build Release e publish: zero errori o avvisi. **424 test OpenPad** e **762 test backend** superati, più 2 casi Linux ignorati.
- Default `Game` senza output LED, effetti sospesi con giochi sconosciuti/aperti quando la priorità è attiva, rilascio una volta dei soli canali owned/noti, frame uguali accorpati, cancellazione, guasto di invio e sessioni separate coperti dai test.
- 18 nuovi casi backend verificano i report luce USB/Bluetooth e l'assenza di flag per vibrazione, grilletti, microfono e audio. La disponibilità del protocollo BT non sostituisce una prova radio fisica.
- Test del percorso di avvio: una preferenza salvata non avvia effetti mentre l'inventario dei giochi è ancora sconosciuto o una partita risulta aperta; un lancio pendente resta una pausa anche prima che appaia il processo.
- UI Automation sulla 0.6.0: navigazione precedente conservata, sezione **Stile e luci** inizialmente chiusa, preset **Gioco · predefinito**, selettore Supercar e **Applica effetto** disponibili sul DualSense USB reale. Dopo l'applicazione lo stato ha confermato invii riusciti, senza trasformarli in una misura ottica.
- **Prova fisica confermata dall'utente:** barra rossa pulsante e scanner avanti/indietro sui cinque LED bianchi del DualSense USB collegato. L'attivazione è stata richiesta esplicitamente; non è il default di una nuova installazione.

Le preferenze luci sono locali e non fanno parte dei file pubblicati. Ripristino ottico esatto di un colore nativo esterno non letto, prova fisica Bluetooth/Edge e sovrapposizione con LED richiesti dai singoli giochi restano limiti separati. Vedi [Stile e luci](docs/lighting.md).

## Verifica del monitor e correzione 0.5.1

L'utente ha inizialmente segnalato che il disegno non sembrava reagire al pad. Dopo la richiesta di portare OpenPad in primo piano e mantenere un grilletto premuto, ha riferito che sembrava funzionare. Questo riscontro conferma quella prova di input; non equivale a una verifica completa della navigazione o del Bluetooth.

La revisione ha individuato due limiti concreti della 0.5.0: il campionamento visivo scendeva a 500 ms con finestra inattiva e poteva perdere pressioni brevi; il messaggio della prova tasti poteva coprire lo stato di report scaduto. La 0.5.1 separa il refresh della finestra visibile dalle azioni di navigazione e dà precedenza al messaggio di input non attuale. Il guasto completo del reader HID resta un'ipotesi non confermata da questa segnalazione.

**Prova manuale confermata sulla 0.5.1:** lasciando OpenPad visibile e portando Codex in primo piano, l'utente ha confermato che il disegno continua a seguire stick e grilletti. Questo esito riguarda il monitor dei comandi senza focus.

La build desktop passa senza errori o avvisi e la suite OpenPad passa con **393 test**. I 9 nuovi test eseguono il dispatcher usato dal Tick reale: refresh visibile senza focus e durante i modali, nessuna lettura/azione di navigazione in background, niente lavoro a finestra nascosta o minimizzata, rilascio e nuova pressione al ritorno. I 744 test backend della 0.5.0 restano riferiti al codice motore invariato.

## Verifiche aggiuntive della 0.5.0

- Build e publish Windows x64: zero errori e avvisi. **384 test OpenPad** e **744 test upstream** superati; 2 casi specifici Linux ignorati.
- Preparazione testata attraverso il percorso composto usato da Gioca: baseline conservate, creazione soltanto dal coordinator, controller in sequenza, isolamento richiesto, scadenza e cancellazione, sessioni sostituite e ripristino del nativo. Il solo test isolato del coordinator non viene usato come prova dell'integrazione.
- Recupero coperto da test di budget, assestamento e attesa di un altro pad. Un refresh mirato non invalida la creazione già in corso di un altro dispositivo.
- Catalogo ampliato da 4 a **14 regole**, con fonti primarie e funzioni USB/Bluetooth separate. È una verifica documentale, distinta dalla prova fisica dei titoli.
- UI Automation sulla build 0.5.0: panoramica, ricerca, ricerca senza risultati, conservazione delle schede, pagina Controller, azioni di verifica, Avanzate inizialmente chiuse e credito esatto. Screenshot della sola finestra ispezionati; il pad e i pulsanti di prova sono visibili prima della guida espandibile.
- DualSense USB collegato rilevato dalla 0.5.0, con dati di input, batteria e collegamento. Le verifiche automatiche dell'interfaccia non inviano effetti o avviano giochi.
- Navigazione pad: 19 test della policy coprono ingresso con tasti già premuti, background, nuova sorgente, report vecchi/futuri, assi non validi, ripetizione e isolamento della prova tasti. La navigazione fisica e la tastiera a schermo richiedono conferma pratica separata.
- Feedback: invio esplicito, controllo delle partite e reset coperti con backend simulati. La percezione non viene dedotta dall'invio del comando. Una conferma di una verifica precedente non può certificare una nuova sessione.
- Checklist: test contro riconnessioni di un altro pad, slot XInput riutilizzati, cambio trasporto senza input sul collegamento iniziale e ripresa senza evento Windows. Il report salvato esclude identificativi e percorsi del dispositivo.
- Checklist reale sulla 0.5.0: avvio e salvataggio dall'interfaccia riusciti, input DualSense USB osservati e credito presente. Tasti, stick, grilletti, riconnessione, cambio collegamento, sospensione ed effetti sono rimasti **Da provare**, senza essere promossi automaticamente a esiti riusciti.

La richiesta di riavvio degli installer resta confermata nello stato della macchina di prova. Nessun nuovo setup driver o riavvio è stato eseguito per pubblicare la 0.5.0. Rimangono aperti il collaudo USB/IP/HidHide dopo riavvio e le prove fisiche Bluetooth, Edge, Xbox e multipad elencate sotto.

## Verifiche aggiuntive della 0.4.3

- Build Release senza errori o avvisi; rieseguite le suite con **290 test OpenPad** e **742 test upstream** superati, più 2 casi Linux ignorati.
- Documentazione compilata con Zensical in modalità `--strict`: nessun problema rilevato.
- Credito esatto incluso nei documenti, nei metadati dell'eseguibile, nella diagnostica e nel frontend.
- Sorgenti di OpenPad pubblicati conservando la cronologia e le attribuzioni upstream. Dati locali, log, report della macchina, pacchetti scaricati e output di build non fanno parte dei file versionati.

## Build e test automatici

| Verifica | Esito della baseline |
| --- | --- |
| Build e publish Windows x64 self-contained | Superati, zero errori e avvisi |
| Suite OpenPad | **290 test superati**, zero falliti o ignorati |
| Suite backend upstream | **742 test superati**, 2 ignorati perché specifici Linux |
| Risorse native incorporate | Hash confrontati con i pin di provenienza |
| Bundle USB/IP e HidHide | SHA256, firma Windows e firmatario ammesso verificati |
| Archivio binario | Runtime, librerie, installer e licenze presenti; dati locali e simboli esclusi |

I test OpenPad coprono librerie e percorsi, catalogo e policy, selezione del gioco, baseline per controller, tuning, journal e recupero, stato operativo, validazione dei pacchetti, codici installer, fonti riavvio, identità WMI e ripresa del setup. Le prove fake dell'isolamento e del setup non equivalgono a una modifica driver riuscita sul sistema reale.

## Prove hardware e gioco

| Percorso | Cosa è stato osservato | Limite della prova |
| --- | --- | --- |
| DualSense USB nativo | Lettura di input, batteria, firmware e frequenza report su hardware reale | Non certifica ogni funzione di ogni gioco |
| Xbox virtuale tramite ViGEm già presente | Slot XInput creato e rimosso tornando nativo | È il fallback legacy; non prova il backend USB/IP |
| SteamWorld Dig 2 | Rilevamento automatico, nessuna eccezione manuale, profilo Xbox, nuovo slot XInput e riconoscimento nel log fresco del gioco | Il pad fisico era ancora visibile nella prova precedente al setup HidHide |
| Comandi SteamWorld Dig 2 | File dei binding e mapping invariati rispetto alla baseline precedente | Non è una misura della latenza o di tutti gli effetti |
| Cyberpunk 2077 USB nativo | L'utente ha riferito buon funzionamento delle funzioni del pad | Segnalazione pratica distinta da misure strumentali di aptica, trigger e audio |
| Monitoraggio nativo USB/BT simulato | Zero scritture output/feature nell'apertura, lettura e chiusura nativa testate | La simulazione BT non sostituisce una radio e una prova fisica |

Una seconda apertura di SteamWorld Dig 2 ha mostrato l'endpoint XInput dopo circa 0,3 secondi dal clic e la finestra del gioco dopo circa 4 secondi. Nei 25 secondi osservati, con campioni ogni 200 ms, non sono state rilevate transizioni dello slot. Sono tempi di quell'avvio, non una promessa per ogni PC né una misura dell'input lag.

Nei log del primo avvio risultava una sola enumerazione dell'Xbox virtuale. Le notifiche multiple di Steam coincidevano con le configurazioni assegnate a pad fisico e virtuale. Vedere due dispositivi non dimostra da solo che ogni pressione venga duplicata.

## Installazione reale dei componenti

Il setup è stato eseguito dopo autorizzazione dell'utente e chiusura del gioco:

- **USB/IP 0.9.8.1** installato, servizi UDE e filtro USB attivi. Il setup ha gestito anche Microsoft Visual C++. Il filtro ha restituito **3010**, richiesta reale di riavvio finale.
- **HidHide 1.5.230** installato, servizio attivo e controllo SDK operativo. Il pacchetto ha restituito **0**.
- L'installazione iniziale è passata dal flusso precedente, in due richieste amministratore. Nella 0.4.2, `3010` viene conservato come riavvio finale e il pacchetto indipendente successivo può proseguire se Windows non introduce nuovi blocchi. Continuazione, errori successivi e `1641` sono coperti dai test.

Il riavvio finale richiesto dal produttore e la prova pratica successiva di USB/IP/HidHide restano **da completare nella baseline documentata**. La presenza dei servizi prima del riavvio non dimostra che il filtro sia già agganciato al collegamento fisico aperto.

## Coerenza degli stati e interfaccia

Sono state verificate queste distinzioni:

- Semplici cancellazioni registrate da Windows non impongono un altro riavvio. Richieste CBS/Windows Update, sostituzioni e letture incerte mantengono i propri motivi.
- Un driver mancante è mostrato come non installato, senza inventare un'installazione in corso.
- Un riavvio richiesto dall'installer resta pendente riaprendo l'app nello stesso avvio Windows. L'identità osservata da WMI è stata confrontata con quella letta dal sistema.
- La prima configurazione mostra i componenti operativi ma non espone **Inizia a giocare** come completamento del setup mentre resta il riavvio da verificare.
- L'esito protetto mancante non diventa un successo o un secondo installer automatico.
- La modalità selezionata non viene dichiarata operativa senza l'endpoint osservato. Un isolamento incerto non viene dichiarato protetto.

UI Automation ha verificato navigazione, ricerca, ricerca senza risultati, schede conservate durante la scansione, stato setup, minimizzazione nel tray, riapertura della stessa istanza, chiusura normale e rilancio. Gli screenshot sono acquisiti dalla sola finestra OpenPad. Le verifiche UI non premono installazione o riavvio Windows.

## Matrice ancora aperta

- Verifica dopo il riavvio di USB/IP e HidHide, con creazione/rimozione degli endpoint e visibilità effettiva nel gioco.
- Bluetooth fisico, aptica/audio BT e comportamento dopo disconnessioni reali.
- DualSense Edge e controller Xbox fisici su una matrice hardware dedicata.
- Protocolli di pad HID generici non ancora gestiti da un backend OpenPad.
- Più pad e giochi contemporanei su hardware reale, oltre ai casi coperti dai test puri.
- Funzioni avanzate per titolo e versione: aptica, trigger, audio, giroscopio e simboli dipendono dal supporto del gioco.

L'etichetta **Supporto documentato** riguarda le fonti del produttore presenti nel catalogo. Non significa che quel percorso sia già stato provato sulla macchina di chi legge.

## Ripetere le verifiche

Le procedure sono in [docs/development.md](docs/development.md). Gli script di build e distribuzione preparano e controllano i pacchetti senza installare driver. Le prove hardware e i test del ciclo di vita vanno eseguiti senza partite aperte.

Non allegare automaticamente l'intera cartella `artifacts`, inventari del PC o log degli installer a un'issue. Condividi il minimo necessario dopo averlo controllato e anonimizzato. Le attribuzioni sono in [CREDITS.md](CREDITS.md) e [THIRD-PARTY-NOTICES.md](THIRD-PARTY-NOTICES.md).

**Powered By RagazzoInGamba - Marco Laudati**
