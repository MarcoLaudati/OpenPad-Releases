# Domande frequenti

**Powered By RagazzoInGamba - Marco Laudati**

## È gratuito e open source?

Sì. OpenPad è distribuito con licenza GPL-3.0. Non richiede account o abbonamenti. Riusa componenti open source esistenti, mantenendo le loro licenze e attribuzioni.

Il repository di sviluppo è privato, ma il [canale pubblico](https://github.com/MarcoLaudati/OpenPad-Releases/releases) distribuisce anche i sorgenti corrispondenti a ogni versione. Non occorre un login per scaricarli.

## L'app si aggiorna da sola?

La versione installata verifica e scarica aggiornamenti del canale **Anteprima**. Li applica alla chiusura quando non risultano giochi o setup in corso; non interrompe una partita. La versione portatile lo dichiara e rimanda all'installer. Preferenze e dati sono separati dai file dell'app. Vedi [installer e aggiornamenti](updates.md).

## Perché Windows dice editore sconosciuto?

Non abbiamo ancora un certificato Authenticode Windows. La firma crittografica del feed e dei pacchetti di aggiornamento protegge un percorso diverso e non rende certificato l'editore dell'EXE. I driver inclusi conservano le firme ufficiali dei loro produttori.

## Posso rimappare tasti, usare audio e personalizzare gli effetti?

Sì, nella finestra [Avanzate](advanced.md) dei DualSense gestiti. Le opzioni sono spente di default, con comandi originali. I profili importati restano bozze finché non li abiliti e applichi. Le prove manuali di audio e feedback richiedono un'azione esplicita fuori dalla partita.

## Devo configurare un profilo per ogni gioco?

La scelta automatica è attiva di default. OpenPad riconosce il titolo e sceglie una modalità per ciascun controller. Le eccezioni manuali restano disponibili in **Libreria → Compatibilità e opzioni** quando vuoi una scelta diversa per un gioco.

Il catalogo della versione 0.7.4 contiene 16 regole: 14 sul supporto DualSense documentato e due guide alle impostazioni di Call of Duty. Le ultime due mantengono la compatibilità standard, senza dichiarare effetti DualSense verificati. Gli altri titoli usano la compatibilità standard disponibile: non devi aggiungere un profilo per iniziare. Vedi [giochi e funzioni documentate](game-compatibility.md).

## Perché dopo Gioca vedo «Preparo il pad»?

OpenPad attende che il controller richiesto sia operativo e, in emulazione, isolato dal pad fisico: fino a **8 secondi con un pad**, più **4 secondi per ogni pad aggiuntivo**, con un massimo di **20 secondi**. Se qualcosa manca, spiega il motivo e propone **Riprova la preparazione** o **Avvia comunque**. La seconda opzione è una scelta esplicita per partire con la compatibilità disponibile; il limite resta visibile.

Questo controllo precede gli avvii dalla libreria OpenPad. Un gioco aperto direttamente dal suo launcher viene riconosciuto dopo l'avvio.

## Installa anche HidHide e USB/IP?

Il pacchetto completo contiene entrambi gli installer ufficiali. **Configura OpenPad** verifica e installa i componenti mancanti, con la conferma amministratore di Windows. I prerequisiti Microsoft vengono gestiti dai setup e possono richiedere Internet. Un riavvio eventualmente richiesto viene conservato fino alla verifica successiva.

## Quale driver usa per il controller virtuale?

Per nuove sessioni Xbox virtuali preferisce ViGEmBus se è già disponibile sul PC; altrimenti usa USB/IP. Per DualSense virtuale usa USB/IP. Una sessione già operativa mantiene il suo backend anche se viene rilevato un altro driver. Il setup OpenPad include USB/IP e HidHide; non installa ViGEmBus. I pad Xbox/XInput fisici continuano a usare Windows direttamente.

## Perché a volte vedo i tasti Xbox con un pad PlayStation?

La modalità Xbox presenta al gioco un controller XInput. Il titolo può quindi mostrare A/B/X/Y. La posizione fisica resta standard: Cross=A, Circle=B, Square=X, Triangle=Y. I simboli visualizzati dipendono dal gioco e dalla modalità che riceve.

## Aptica e grilletti adattivi funzionano in ogni gioco?

Dipendono dalle funzioni implementate nel titolo e dal percorso di collegamento. La conversione in Xbox conserva i comandi standard e il feedback supportato, ma non crea effetti DualSense aggiuntivi. **Supporto documentato** indica una fonte del produttore, distinta dalla prova sul tuo PC.

Il riepilogo separa USB e Bluetooth e non deduce funzioni avanzate da un generico supporto controller. Per esempio, la vibrazione Bluetooth documentata di Horizon Zero Dawn Remastered non diventa automaticamente aptica wireless.

## Bluetooth e cavo offrono sempre le stesse funzioni?

Il supporto cambia in base a controller, gioco e backend. Il motore implementa DualSense USB e Bluetooth; il percorso Bluetooth avanzato e DualSense Edge richiedono ancora verifiche fisiche complete per OpenPad. Un titolo documentato per USB non viene considerato automaticamente verificato in Bluetooth.

## Funziona anche con Xbox e altri controller?

Xbox e i pad XInput usano il supporto nativo Windows. Per altri dispositivi HID l'app può rilevare il controller senza disporre ancora di un backend di conversione specifico. Rilevare un dispositivo non certifica tutte le sue funzioni.

## Perché Steam segnala un cambio controller?

Passare da pad fisico a controller virtuale può generare notifiche. Con HidHide non operativo possono restare visibili entrambi i dispositivi. OpenPad mostra la modalità effettivamente operativa e lo stato della protezione dai doppi input; una notifica, da sola, non prova che la modalità stia cambiando ripetutamente.

## Posso usare Steam Input insieme a OpenPad?

Steam Input può sovrapporsi al percorso nativo o alla conversione. OpenPad non modifica le impostazioni globali di Steam. Controlla le indicazioni del singolo gioco: alcuni titoli richiedono Steam Input disattivato per rilevare direttamente il DualSense o inoltrare le sue funzioni avanzate.

Non è una regola universale: Nixxes documenta grilletti adattivi con Steam Input per Spider-Man Remastered, mentre Bend richiede Steam Input disattivato per l'aptica di Days Gone. Le condizioni e le fonti sono nella [guida alla compatibilità](game-compatibility.md).

## Posso vedere se l'app riceve davvero i tasti?

Sì: in **Controller** il disegno mostra tasti premuti, stick e corsa dei grilletti in tempo reale, quando il protocollo è disponibile. **Prova i tasti** mette il focus sul disegno senza attivare gli altri pulsanti dell'app; esci con **Circle/B**. Se gli input non sono leggibili, l'app lo indica.

## Posso usare OpenPad dal divano, con il pad?

Quando la finestra OpenPad è attiva, usa croce direzionale o stick sinistro per spostarti, **L1/R1** o **LB/RB** per cambiare sezione, **Cross/A** per confermare e **Circle/B** per tornare indietro. Lo stick destro scorre il contenuto. Le azioni di setup, riavvio e cambio manuale della modalità richiedono una conferma aggiuntiva se attivate dal pad.

Per scrivere una ricerca o scegliere un file restano disponibili gli strumenti ordinari di Windows. La navigazione di OpenPad non invia comandi globali al gioco.

## Cosa prova «Verifica il pad»?

Raccoglie input reali di tasti, stick e grilletti, oltre a riconnessione, passaggio USB/Bluetooth e ripresa quando sono verificabili. La checklist distingue **Osservato**, **Da provare** e **Non verificabile**. Per riconoscere lo stesso pad nei due collegamenti serve un'identità fisica affidabile: il numero XInput da solo non basta.

Una ripresa richiede un evento Windows seguito da nuovi input. Il tempo passato senza premere tasti non viene scambiato per una sospensione riuscita. Aprire la verifica non certifica tutti i passaggi: quelli non eseguiti restano da provare.

## Come funzionano le prove di vibrazione e grilletti?

Le avvii con i pulsanti dedicati, fuori dalla partita e quando il backend le supporta. Sono prove brevi su richiesta. Dopo il comando scegli **Conferma riuscita** o **Non percepito**: l'app distingue l'invio dell'effetto da quello che hai sentito. Una prova del pad non certifica gli effetti di un gioco.

## La verifica guidata salva dati personali?

**Salva esito** scrive soltanto in locale `hardware-check-latest.json`, nella cartella dati OpenPad. Il report include nome del controller, versione, orari, stati dei passaggi e tue conferme; esclude identificativi e percorsi dei dispositivi. Non viene caricato online. I report diagnostici generali sono separati e possono contenere più dettagli locali.

## Dove sono finite le opzioni manuali e i dati tecnici?

In **Controller → Avanzate · modalità e dettagli**. Per applicare manualmente una modalità nella sessione spegni **Scelta automatica**; per ricordare un'eccezione di un gioco usa le opzioni nella libreria. I comandi originali restano il punto di partenza.

## OpenPad modifica i comandi salvati nei giochi?

No. Non riscrive binding o impostazioni globali dei launcher. Il profilo iniziale mantiene disposizione standard, zone morte e feedback del gioco, senza macro, overclock, polling forzato o cattura dell'audio di sistema.

## Devo lasciarlo aperto?

Per le modalità virtuali sì: puoi ridurlo in background. L'icona vicino all'orologio e un secondo avvio permettono di riaprire la finestra. La **X** o **Esci** terminano l'app e la conversione.

## Legge o carica online la mia libreria?

Legge i metadati locali dei launcher. Le copertine vengono dalla cache Steam già presente. Non richiede l'accesso agli account e non invia l'elenco dei giochi a un servizio remoto. I report diagnostici possono contenere percorsi locali: vanno controllati prima di condividerli.

## C'è una versione OpenPad per Linux?

La distribuzione e il setup attuali di OpenPad sono per Windows x64. Alcune librerie upstream supportano Linux, ma questo non rende la UI e la procedura driver di OpenPad una distribuzione Linux verificata.

## Dove sono documentate le prove reali?

Nel repository, in [VERIFICATION.md](https://github.com/MarcoLaudati/OpenPad-Releases/blob/main/VERIFICATION.md). La [guida funzionale](functional.md) descrive il comportamento dell'app; la [documentazione tecnica](technical.md) spiega come viene implementato.
