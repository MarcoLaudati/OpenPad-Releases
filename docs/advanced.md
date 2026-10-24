# Avanzate, quando vuoi qualcosa in più

**Powered By RagazzoInGamba - Marco Laudati**

Colleghi il pad, apri il gioco. Questo resta il percorso normale. Le opzioni avanzate sono separate in **Controller → Avanzate · modalità e dettagli → Apri Avanzate** e partono spente. Aprire la finestra o cambiare un campo non avvia effetti.

## Profili e comandi

Senza personalizzazioni, OpenPad conserva la disposizione originale. Puoi aggiungere una mappatura per Xbox virtuale, DualShock 4 virtuale o DualSense virtuale: scegli i tasti sorgente e una o più destinazioni. Più sorgenti nella stessa riga formano una combinazione. Il comportamento dei grilletti distingue pressione completa e clic quando il protocollo lo permette.

La rimappatura riguarda il controller virtuale. In modalità nativa il gioco continua a ricevere i comandi del pad reale; OpenPad non modifica i file dei binding del titolo.

I profili locali possono essere salvati, copiati, caricati, importati ed esportati. **Carica** e **Importa** preparano una bozza disattivata: controllala, abilita le opzioni e premi **Applica**. Non eseguono programmi né riproducono file. **Comandi originali** disattiva le personalizzazioni avanzate.

## Quale modalità vince

Con la scelta automatica attiva, l'ordine è:

1. Eccezione scelta per il singolo gioco nella libreria.
2. Preferenza del controller abilitata in Avanzate.
3. Suggerimento automatico basato su controller, collegamento e gioco.

Fuori dal gioco rimane la preferenza avanzata, se abilitata; altrimenti torna la modalità precedente di ciascun pad. Spegnere la scelta automatica mantiene la preferenza avanzata o la scelta manuale. Caricare una bozza non cambia questa precedenza.

Puoi scegliere DualShock 4 V1/V2 e DualSense standard/Edge virtuali. Un endpoint Edge virtuale non aggiunge tasti fisici a un DualSense standard. DualShock 4 virtuale richiede USB/IP e non offre i grilletti adattivi o l'aptica audio del protocollo DualSense. Questi percorsi restano da verificare sui giochi e sugli hardware disponibili.

## Audio e feedback

Le prove manuali di vibrazione permettono di scegliere separatamente i due motori. Le prove dei grilletti offrono preset indipendenti per destra e sinistra, con durata breve e rilascio finale. Richiedono un DualSense in modalità nativa, fuori dalla partita. L'esecuzione software di una prova non certifica ciò che hai percepito.

Puoi scegliere un file audio locale **WAV, MP3 o FLAC** e avviarne esplicitamente la riproduzione su altoparlante, cuffie o aptica, con volume e intensità dedicati. Questi sono i formati del decoder incluso; AAC, OGG e altri formati non vengono presentati come supportati. La chiusura della finestra ferma le sue prove. L'avvio di un gioco, il setup e l'uscita fermano le anteprime prima di proseguire.

L'inoltro audio è una scelta separata: endpoint del controller, uscita di sistema oppure applicazione scelta. La cattura dell'audio di sistema o di un'applicazione parte soltanto dopo l'abilitazione e l'applicazione della configurazione. Al primo avvio resta spento. La disponibilità effettiva degli endpoint dipende dal collegamento e da Windows; avere un'opzione a schermo non dimostra che l'audio sia arrivato al pad.

## Sensori, azioni e luci

La sezione sensori mostra i dati letti dal backend: due contatti touch, giroscopio, accelerometro, temperatura, dettagli firmware e, per Edge, tasti aggiuntivi. I dati mancanti o vecchi vengono dichiarati tali. La lettura del giroscopio non significa avere una modalità giroscopio-mouse: questa trasformazione non è implementata.

Le azioni speciali collegano una combinazione o un gesto touch supportato a colore RGB, indicatori del giocatore, indicazione della batteria, disconnessione Bluetooth o riproduzione di un file locale. Disconnessione Bluetooth non si applica al cavo USB; l'audio delle azioni resta bloccato durante i giochi rilevati. Tempi e durata sono configurabili. Il colore manuale può includere i LED bianchi e la spia microfono: cambiare la spia non accende né registra il microfono. Per default il colore manuale rispetta le luci del gioco.

Gli effetti **Supercar**, respiro e arcobaleno restano anche nella sezione semplice **Stile e luci**. Le preferenze avanzate hanno un proprio archivio; non vengono attivate importando un profilo e non diventano impostazioni predefinite per tutti.

## Cosa è stato provato davvero

L'hardware disponibile per questa versione è un **DualSense via USB**. Il percorso nativo e gli effetti Supercar sono stati confermati nelle prove precedenti. Le nuove funzioni ricevono test software e verifiche dedicate; Bluetooth, Xbox fisici, DualSense Edge e altre combinazioni non vengono indicati come provati senza hardware. Gli esiti aggiornati sono in `VERIFICATION.md`, incluso negli archivi dei sorgenti.
