# Stile e luci

**Powered By RagazzoInGamba - Marco Laudati**

In **Controller → Stile e luci** scegli un effetto, premi **Applica effetto** e guardalo sul pad. I nuovi controller partono da **Gioco · predefinito**: OpenPad non avvia luci personali finché non le scegli.

| Effetto | Cosa richiede al DualSense |
| --- | --- |
| Gioco · predefinito | Nessuna animazione di OpenPad; il gioco può controllare le luci |
| Supercar · scanner | Barra rossa pulsante e un punto che va avanti e indietro sui cinque indicatori bianchi |
| Respiro blu | Intensità blu che sale e scende gradualmente |
| Arcobaleno | Passaggio morbido tra i colori della barra RGB |

Il DualSense ha una barra RGB comandata con un solo colore e cinque indicatori giocatore bianchi controllabili singolarmente. Lo scanner usa quei cinque indicatori: non promette una scia rossa a segmenti sulla barra. La struttura hardware e i comandi sono documentati nel [driver PlayStation del kernel Linux](https://kernel.googlesource.com/pub/scm/linux/kernel/git/stable/linux-stable/+/master/drivers/hid/hid-playstation.c).

## Semplice di default

La scelta viene conservata sul PC per il controller riconosciuto. Puoi cambiare preset senza applicarlo: soltanto **Applica effetto** salva e attiva la nuova scelta. **Luci del gioco** ferma l'animazione e rimuove la preferenza personale.

In **Dettagli effetto** trovi luminosità Bassa, Media e Alta. Regola i valori RGB; gli indicatori bianchi dello scanner sono accesi o spenti, senza una promessa di luminosità ottica calibrata.

**Pausa quando rilevo un gioco** è attiva inizialmente. OpenPad ferma l'effetto prima di avviare una partita dalla propria libreria e quando rileva un gioco aperto da un altro launcher. Se lo stato delle partite non è ancora noto, l'effetto attende la verifica. Terminata la partita rilevata, può riprendere la scelta personale.

Disattivando questa opzione scegli di continuare l'effetto durante la partita: può sostituire o sovrapporsi ai colori richiesti dal gioco. I comandi, le zone morte, la vibrazione, i grilletti e l'audio restano separati dalle luci.

## Cosa indicano anteprima e stato

L'anteprima è software: rappresenta i comandi luce richiesti, non una lettura ottica del controller. Lo stato distingue effetto in invio, pausa per il gioco o per una verifica in corso e invio fallito. Un errore estetico non deve impedire l'avvio della partita.

Quando l'effetto si ferma, OpenPad ripristina soltanto i comandi luce precedenti che ha effettivamente osservato nel proprio processo. Il colore impostato direttamente da un gioco nativo può non essere leggibile: in quel caso non viene inventato un colore precedente. Il gioco può impostare nuovamente le luci al proprio aggiornamento successivo; il controller può mantenere l'ultimo colore fino a quel momento.

Chiusura e disconnessione fermano il writer dell'animazione. Le preferenze personali rimangono locali; i report della verifica guidata non includono indirizzi o identificativi del pad.

## Controller supportati

Il backend delle luci personali è dedicato a DualSense e DualSense Edge tramite USB o Bluetooth. La disponibilità del protocollo e la prova fisica sul singolo modello sono esiti distinti: consulta [VERIFICATION.md](https://github.com/MarcoLaudati/OpenPad-Releases/blob/main/VERIFICATION.md).

Per Xbox/XInput e HID generici il backend attuale non implementa questo controllo RGB; la sezione lo indica e disabilita gli effetti personali. L'API XInput usata dall'app espone il comando di [vibrazione](https://learn.microsoft.com/en-us/windows/win32/api/xinput/nf-xinput-xinputsetstate), non un comando RGB utilizzato da OpenPad. Non è una dichiarazione sulle eventuali funzioni proprietarie di ogni modello.

**Powered By RagazzoInGamba - Marco Laudati**
