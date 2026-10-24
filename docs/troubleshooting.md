# Problemi e soluzioni

**Powered By RagazzoInGamba - Marco Laudati**

## Il disegno del pad sembra fermo

Dalla 0.5.1 la vista dei comandi si aggiorna anche con OpenPad visibile dietro un'altra finestra. La navigazione con il pad richiede invece OpenPad in primo piano e il rilascio iniziale dei comandi, per evitare pressioni involontarie.

Tieni un grilletto premuto per qualche secondo: la percentuale L2/R2 deve riflettere il comando. In **Avanzate · modalità e dettagli** puoi confrontare i valori grezzi. **In attesa di un report** indica che non è confermato un input attuale; il solo nome del pad o una batteria letta in precedenza non dimostrano che i report stiano ancora arrivando. Questo avviso resta visibile anche durante **Prova i tasti**.

Parti dallo stato mostrato dall'app: controller rilevato, modalità operativa, driver e protezione dai doppi input sono informazioni diverse. Servono a capire quale passaggio richiede attenzione.

## Il pad non compare

1. Per USB prova un cavo dati e una porta diretta del PC.
2. Per Bluetooth controlla che Windows abbia un adattatore attivo e che l'associazione sia completata.
3. Apri **Controller** e attendi l'aggiornamento dell'inventario.
4. Se usi altri programmi di gestione del pad, chiudili durante una prova separata.

Un controller HID non ancora gestito può comparire nell'inventario ma richiedere il supporto nativo del gioco. Per Xbox/XInput nome preciso, batteria o trasporto possono non essere disponibili.

Se il dispositivo è stato nascosto manualmente con HidHide da un'altra app, verifica quelle regole nel configuratore ufficiale. OpenPad conserva le regole preesistenti e non le cancella per forzare l'accesso.

## Il gioco non viene trovato

Premi **Aggiorna** in **Libreria** e controlla filtro launcher e testo di ricerca. OpenPad legge percorsi e metadati dei launcher, con una scansione limitata: una cartella protetta o non registrata può sfuggire al rilevamento.

Usa **Aggiungi un gioco dal PC** e scegli l'eseguibile reale del titolo, evitando launcher, updater e crash reporter. Per i giochi Xbox/GDK usa il launcher Xbox o il collegamento registrato di Windows per l'avvio: eseguire direttamente il file può perdere l'identità richiesta dal runtime.

Le copertine mancanti vengono sostituite da un'iniziale. Non significa che il gioco non sia stato riconosciuto.

## Il gioco compare, ma il pulsante Gioca è disabilitato

OpenPad avvia tramite Steam oppure tramite un eseguibile dichiarato da metadati affidabili o selezionato da te. Se manca un punto di avvio affidabile, apri il titolo dal suo launcher: il riconoscimento automatico della partita rimane disponibile.

Primo avvio, aggiornamenti, licenze e finestre del launcher possono richiedere un tuo intervento. OpenPad non accetta accordi al posto tuo.

## La modalità scelta non è quella che volevo

Apri **Libreria → Compatibilità e opzioni** e leggi il motivo della scelta. Controlla anche l'eventuale eccezione personale: ha precedenza sull'automatismo.

Per ripristinare il comportamento consigliato seleziona **Automatico** per quel titolo e lascia acceso l'interruttore in alto. Con più giochi aperti, porta in primo piano quello con cui vuoi giocare. Passare al desktop mantiene il gioco attivo, se è ancora in esecuzione.

Il catalogo distingue il supporto documentato da una traduzione standard dei comandi. Una modalità virtuale richiesta ma non effettivamente operativa viene segnalata nel suo stato.

## Una pressione salta due voci o produce due azioni

Il gioco potrebbe vedere il pad fisico insieme alla copia virtuale, oppure ricevere un'ulteriore traduzione da Steam Input o da un altro remapper.

1. Controlla lo stato del controller: OpenPad indica se il pad fisico è ancora visibile o se l'isolamento non è confermato.
2. Completa **Prima configurazione** se HidHide manca o non è operativo.
3. Dopo una modifica alla visibilità, chiudi e riapri il gioco. I programmi con un handle già aperto possono richiedere anche una riconnessione del pad.
4. Verifica le indicazioni Steam Input del singolo titolo e prova con un solo percorso di traduzione.

Il numero di notifiche Steam non misura il numero di azioni ricevute dal gioco: controlla il comportamento pratico, una pressione alla volta.

## Mancano aptica, resistenza dei grilletti o simboli PlayStation

Controlla modalità, collegamento e indicazioni del gioco. In compatibilità Xbox il titolo riceve XInput e può mostrare A/B/X/Y. Le funzioni DualSense avanzate richiedono il supporto del titolo e le condizioni indicate dal produttore, spesso con collegamento USB.

Apri **Compatibilità e opzioni** nella libreria. Non applicare a tutto Steam un'impostazione letta per un solo gioco. OpenPad non forza effetti artificiali per far sembrare presente un supporto che il titolo non offre.

## Ho già riavviato, ma il setup chiede ancora attenzione

Apri **Dettagli della verifica**. L'app distingue:

| Indicazione | Cosa controllare |
| --- | --- |
| Richiesta esplicita di Windows o dell'installer | Completa un vero riavvio di Windows, poi riapri OpenPad |
| Semplici operazioni di pulizia file | Da sole non impongono un altro riavvio per il setup |
| Sostituzioni di file o operazioni su driver | Il setup rimane sospeso finché quelle operazioni risultano bloccanti |
| Identità dell'avvio o fonti non verificabili | L'app mantiene lo stato incerto e mostra il motivo |
| Driver installato ma non operativo | Verifica il componente; il solo stato non prova che un riavvio risolverà |

Chiudere e riaprire OpenPad non equivale a riavviare Windows. Usa **Riavvia**, anziché affidarti al solo spegnimento con avvio rapido. Non cancellare chiavi del registro o file di sistema per togliere l'avviso.

## Il setup è annullato o incompleto

Un annullamento nella richiesta Windows non installa automaticamente i componenti. Puoi riprovare dal setup quando sei pronto.

Se l'app mostra **Esito setup in attesa**, conserva il tentativo precedente e cerca il risultato protetto. Non avviare altri installer mentre quello precedente è ancora in corso. Se lo stato non cambia, raccogli un report e segnala il problema: non eliminare il promemoria per trasformare uno stato sconosciuto in una configurazione completa.

Un driver esistente vecchio o incompleto può richiedere la procedura ufficiale del produttore. OpenPad evita aggiornamenti o downgrade alla cieca.

## L'app non si riapre o sembra scomparsa

La riduzione a icona lascia OpenPad in background. Premi la sua icona vicino all'orologio oppure avvia di nuovo `OpenPad.exe`: viene riaperta la stessa istanza. La **X** termina invece l'app.

Se stai eseguendo una diagnosi hardware da terminale, chiudi prima l'istanza desktop. I comandi diagnostici e i loro effetti sono nella [documentazione tecnica](technical.md).

## Preparare una segnalazione utile

Indica versione di OpenPad, modello del controller, USB/Bluetooth, gioco e launcher, stato mostrato dall'app e passaggi per riprodurre il problema. Specifica se sono presenti Steam Input o altri remapper.

Da **Impostazioni → Apri cartella dati** puoi trovare i dati locali. I report possono contenere percorsi e informazioni dei dispositivi: rimuovi ciò che non vuoi rendere pubblico prima di allegarli a una [issue](https://github.com/MarcoLaudati/OpenPad/issues).
