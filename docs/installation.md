# Installazione e primo avvio

**Powered By RagazzoInGamba - Marco Laudati**

L'obiettivo è partire dal pacchetto completo, configurare quello che manca e poi pensare al gioco. Non serve scegliere driver da siti diversi o ricostruire i profili a mano.

## Prendi il pacchetto giusto

OpenPad offre un installer e una cartella portatile per **Windows x64**. La verifica su hardware reale è stata eseguita su Windows 11. L'installer è il percorso consigliato per ricevere gli aggiornamenti automatici: installa l'app per il tuo utente, poi la prima configurazione completa i driver mancanti.

Il pacchetto `OpenPad-<versione>-win-x64.zip` contiene l'app, il runtime .NET, le librerie native, gli installer ufficiali USB/IP e HidHide e le loro licenze. Estrai l'intero archivio in una cartella stabile e apri `OpenPad.exe`: spostare soltanto l'eseguibile lascia indietro le sue dipendenze.

Pacchetti e sorgenti delle versioni distribuite sono nella pagina pubblica [OpenPad-Releases](https://github.com/MarcoLaudati/OpenPad-Releases/releases). Il repository di sviluppo è privato. Per compilare l'archivio sorgenti segui la [guida sviluppo](development.md); per installazione e firme leggi [aggiornamenti](updates.md).

## Configura OpenPad

Se la configurazione è incompleta, l'app apre **Prima configurazione**.

1. Chiudi i giochi e completa gli altri aggiornamenti in corso.
2. Premi **Configura OpenPad**.
3. Conferma la richiesta amministratore di Windows.
4. Attendi l'installazione e la verifica dei componenti.
5. Se viene richiesto un riavvio, salva i lavori aperti, riavvia Windows e riapri OpenPad.

La build dell'app non installa driver: l'installazione avviene da questo flusso, con la conferma Windows. Durante il setup USB/IP gli hub USB possono riconnettersi. Mouse, tastiera o pad USB potrebbero quindi scollegarsi brevemente.

I pacchetti inclusi sono **USB/IP 0.9.8.1 x64** e **HidHide 1.5.230.0**. Prima dell'esecuzione OpenPad controlla hash SHA256, firma Windows e firmatario previsto. I setup ufficiali gestiscono anche i prerequisiti Microsoft Visual C++; se manca un prerequisito può essere necessaria una connessione Internet.

| Componente | Perché c'è |
| --- | --- |
| USB/IP | Permette al motore di esporre i controller virtuali previsti |
| HidHide | Gestisce la visibilità del pad fisico quando viene usata la sua copia virtuale |
| Runtime .NET | È incluso nel pacchetto: per usare l'app non serve installare l'SDK |

Le versioni già compatibili vengono mantenute. Un driver vecchio, sconosciuto o incompleto viene segnalato: OpenPad non forza sostituzioni o downgrade. Un ViGEmBus già presente può essere utilizzato come fallback legacy; il setup non lo installa.

## Se serve un riavvio

Un installer può terminare correttamente e richiedere un riavvio finale. OpenPad conserva questa richiesta anche se chiudi e riapri l'app. La verifica usa l'avvio reale di Windows: riaprire soltanto la finestra non completa questo passaggio.

Il codice **3010** consente di completare il pacchetto indipendente successivo prima del riavvio, quando Windows non segnala nuovi blocchi. **1641**, errori o nuovi blocchi interrompono la catena. Le indicazioni nella schermata corrispondono al risultato ricevuto.

Il pulsante **Riavvia Windows** richiede un tuo clic e non forza la chiusura delle applicazioni. Puoi anche usare **Start → Arresta → Riavvia**. Dopo il riavvio riapri OpenPad: controllerà i componenti e mostrerà gli eventuali passaggi ancora necessari.

Se la schermata dice **Esito setup in attesa**, l'app sta cercando il risultato protetto dell'installazione. Non considera l'esito mancante un successo e non avvia automaticamente una seconda installazione.

## Collega il controller

- **USB:** collega il pad con un cavo che trasferisca dati, oltre alla ricarica.
- **Bluetooth:** associa il controller dalle impostazioni Bluetooth di Windows. Nell'app puoi aprirle da **Controller** o **Impostazioni**.

Il Bluetooth richiede un adattatore presente e attivo sul PC. L'installazione dei driver virtuali non aggiunge una radio Bluetooth a un computer che ne è privo.

Aspetta che il pad compaia, lascia attiva la scelta automatica e avvia il gioco. Per la prima prova, un titolo con supporto DualSense USB documentato permette di verificare il percorso nativo; un gioco XInput permette di verificare la compatibilità Xbox.

## Dopo la configurazione

Puoi ridurre OpenPad in background: l'icona vicino all'orologio permette di riaprirlo. Anche un secondo avvio dell'eseguibile riapre la stessa istanza. La **X** o **Esci** chiudono l'app e interrompono la conversione; il controller torna al funzionamento nativo.

**Più tardi** permette di usare la compatibilità già disponibile nella sessione corrente. La prima configurazione tornerà alle aperture successive finché non risulta completa.

Per rimuovere la versione installata, usa **Impostazioni Windows → App → OpenPad**. La cartella dei dati personali resta separata dall'app. Per la versione portatile, chiudila prima e conserva o rimuovi la cartella estratta secondo necessità. I driver sono componenti Windows separati: eliminarne i file a mano non li disinstalla. Se vuoi rimuoverli, usa le procedure ufficiali dei rispettivi produttori dalle app installate di Windows. Non eliminare chiavi o file di sistema per togliere un avviso.

Problemi durante questi passaggi? Apri [Problemi e soluzioni](troubleshooting.md).
