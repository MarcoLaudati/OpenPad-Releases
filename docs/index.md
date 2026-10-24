# OpenPad: colleghi il pad, apri il gioco

**Powered By RagazzoInGamba - Marco Laudati**

Giocare deve essere divertente e immediato. OpenPad nasce per riconoscere il controller, trovare i giochi installati e preparare la compatibilità, mantenendo i comandi originali.

È un'app open source per Windows x64, con libreria locale, profili automatici e configurazione iniziale dei driver inclusi. Nessun account, nessun abbonamento.

## Per iniziare

1. Installa OpenPad dal [canale pubblico](https://github.com/MarcoLaudati/OpenPad-Releases/releases), aprilo e premi **Configura OpenPad** se manca un componente.
2. Conferma Windows e completa l'eventuale riavvio richiesto dall'installer.
3. Collega il controller via USB o associalo in Bluetooth al PC.
4. Lascia attiva la scelta automatica e avvia il gioco.

La schermata **Prima configurazione** distingue ciò che è soltanto incluso nel pacchetto da ciò che è installato e operativo. Durante una partita, la panoramica mostra il gioco riconosciuto e la modalità del pad.

## Scegli la guida che ti serve

| Vuoi… | Apri… |
| --- | --- |
| Preparare l'app e i driver | [Installazione](installation.md) |
| Capire schermate, automatismi e scelte manuali | [Guida funzionale](functional.md) |
| Personalizzare profili, tasti, audio o effetti | [Avanzate](advanced.md) |
| Capire installer, aggiornamenti e firme | [Aggiornamenti](updates.md) |
| Risolvere un problema concreto | [Problemi e soluzioni](troubleshooting.md) |
| Una risposta rapida | [FAQ](faq.md) |
| Leggere l'architettura e i flussi del motore | [Documentazione tecnica](technical.md) |
| Compilare o contribuire | [Sviluppo](development.md) e [contributi](CONTRIBUTING.md) |

## Cosa significa compatibilità

Per Xbox/XInput il percorso è nativo Windows. Per DualSense OpenPad sceglie il supporto nativo documentato oppure una modalità virtuale standard, in base al gioco e ai componenti disponibili.

Le funzioni avanzate restano legate al titolo. **Supporto documentato** descrive le fonti del produttore; lo stato del controller e le prove sul PC sono verifiche separate. Un gioco che riceve un controller Xbox non acquisisce automaticamente aptica o grilletti adattivi DualSense.

Il motore hardware deriva da [DualSense Client](https://github.com/DualSenseClient/DualSenseClient). Le vecchie guide della sua interfaccia descrivono il progetto upstream: la guida funzionale di OpenPad è il riferimento per le schermate attuali.

Repository: [Sorgenti delle versioni](https://github.com/MarcoLaudati/OpenPad-Releases/releases). Licenza e [crediti](https://github.com/MarcoLaudati/OpenPad-Releases/blob/main/CREDITS.md) delle dipendenze sono conservati nel progetto. Le prove sono raccolte in [VERIFICATION.md](https://github.com/MarcoLaudati/OpenPad-Releases/blob/main/VERIFICATION.md).
