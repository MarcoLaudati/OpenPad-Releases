# Contribuire a OpenPad

**Powered By RagazzoInGamba - Marco Laudati**

Se una modifica rende più facile giocare e più chiaro capire cosa succede, siamo sulla strada giusta. Prima di aggiungere un'opzione, chiediamoci se il comportamento predefinito può risolvere il problema da solo.

## Da dove partire

Leggi il [manuale funzionale](functional.md), l'[architettura](technical.md) e le [istruzioni di sviluppo](development.md). Apri una [issue](https://github.com/MarcoLaudati/OpenPad-Releases/issues) per descrivere un problema o una proposta. Per una correzione piccola e verificabile puoi arrivare direttamente con una pull request.

Il progetto principale è `OpenPad.slnx`. Il frontend è `OpenPad.Desktop`, il coordinamento hardware è in `OpenPad.Engine`; i progetti `DualSenseClient.*` conservano la base upstream. Le guide della GUI originale non sono un elenco di funzionalità già presenti in OpenPad.

## Cosa proteggere nelle modifiche

- Comandi originali come default: niente macro, curve, deadzone o effetti imposti senza scelta dell'utente.
- Percorso nativo del gioco quando documentato e adatto al collegamento.
- Modalità selezionata, operatività e isolamento mostrati come stati distinti.
- Nessun doppio endpoint creato per un controllo periodico o un cambio di focus verso il desktop.
- Driver e risorse native fissati e verificati; nessun installer avviato dalla sola build o diagnosi.
- Errori e dati sconosciuti spiegati senza trasformarli in successo, obbligo di riavvio o promessa di compatibilità.
- Journal e ripristino limitati alle modifiche di proprietà OpenPad, conservando le regole dell'utente.

## Codice e prove

Segui lo stile del componente modificato. Mantieni i ViewModel leggibili e usa classi pure per policy, selezione della partita e transizioni del setup quando non serve accedere al sistema. Evita nuove dipendenze se la piattaforma o un componente esistente coprono già il caso.

Scrivi test per il comportamento che può regredire: percorsi ambigui, metadati danneggiati, hotplug, generazioni superate, esiti installer, recupero e conservazione delle impostazioni. Una piccola modifica grafica reversibile richiede soprattutto build e controllo visivo; non serve un test che ricopi il codice.

Esegui le suite pertinenti e la build descritta in [Sviluppo](development.md). Una simulazione non sostituisce una prova con il controller fisico. Se non hai l'hardware o il gioco necessario, scrivilo nella PR.

Una nuova regola del catalogo richiede fonte primaria, identità corretta, collegamento documentato ed eventuali condizioni. Non assegnare funzioni DualSense a un'edizione precedente soltanto perché condivide lo stesso Steam App ID.

## Pull request

Apri un branch dedicato e prepara una modifica revisionabile senza conoscere la chat da cui nasce. La descrizione deve spiegare:

1. Il problema concreto e la situazione in cui compare.
2. Il comportamento che ottiene l'utente dopo la modifica.
3. Le prove passate e quelle ancora da fare.
4. Eventuali cambi di dipendenze, persistenza, privilegi o stato del sistema.

Per una PR grafica aggiungi immagini della sola finestra interessata. Per bug hardware indica modello, USB/BT, versione dell'app e del gioco, modalità osservata e driver presenti. Rimuovi prima nomi account, percorsi personali, identificativi dei dispositivi e contenuti estranei alla prova.

## Licenze e crediti

OpenPad è GPL-3.0 e riusa componenti con proprie attribuzioni. Mantieni `LICENSE`, avvisi upstream e licenze dei pacchetti distribuiti. Il credito OpenPad deve restare nell'app e nei materiali del progetto:

**Powered By RagazzoInGamba - Marco Laudati**

Questo credito non sostituisce gli autori di DualSense Client, HIDAPI, libVIIPER, USB/IP, HidHide o delle altre dipendenze. Ogni nuovo componente deve avere provenienza e condizioni di distribuzione in [CREDITS.md](https://github.com/MarcoLaudati/OpenPad-Releases/blob/main/CREDITS.md) e [THIRD-PARTY-NOTICES.md](https://github.com/MarcoLaudati/OpenPad-Releases/blob/main/THIRD-PARTY-NOTICES.md).
