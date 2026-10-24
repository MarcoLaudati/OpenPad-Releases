# Compatibilità dei giochi

Powered By RagazzoInGamba - Marco Laudati

Il pad si collega, OpenPad sceglie il percorso, il gioco decide i comandi e gli effetti. Per fare questa scelta usiamo un catalogo con fonti dei produttori, separando sempre USB, Bluetooth e controller virtuale. Non basta un bollino «supporto controller» per promettere aptica o grilletti adattivi.

Il catalogo contiene **14 regole**, controllate il **24 ottobre 2026**. Dieci sono nuove rispetto alla prima versione del catalogo. Questa è una verifica della documentazione: non significa che abbiamo provato fisicamente tutti questi giochi, controller e collegamenti. Le prove locali sono riportate nella [verifica del progetto](https://github.com/MarcoLaudati/OpenPad-Releases/blob/main/VERIFICATION.md).

## Cosa sceglie OpenPad

- **Xbox e XInput:** restano nativi, con il layout previsto dal gioco.
- **DualSense USB con una regola documentata:** resta nativo, così il titolo può gestire i suoi effetti.
- **DualSense Bluetooth con supporto nativo esplicito:** resta nativo. La regola indica le singole funzioni documentate per Bluetooth.
- **DualSense Bluetooth con supporto documentato soltanto via USB:** con USB/IP disponibile, OpenPad può presentare un DualSense virtuale. Il gioco vede un dispositivo USB; il percorso virtuale e gli effetti sul pad fisico restano da provare sul PC.
- **Gioco senza una regola:** usa la compatibilità Xbox quando è disponibile un driver per il controller virtuale. Comandi e vibrazione funzionano se il titolo supporta XInput; gli effetti specifici DualSense non sono disponibili in questa modalità.

I controller generici senza un backend specifico restano sul supporto nativo del gioco. OpenPad non cambia i tasti del titolo, non forza zone morte e non inventa funzioni che il gioco non implementa. Puoi correggere la modalità nella libreria quando serve.

## Giochi e funzioni documentate

I collegamenti sui nomi portano alla fonte delle funzioni PC; quelli sugli ID identificano la corretta scheda Steam. **Non documentato** significa che questa regola non dispone di una prova sufficiente, anche se una combinazione diversa potrebbe funzionare.

| Gioco | Steam App ID | DualSense USB | DualSense Bluetooth nativo |
| --- | --- | --- | --- |
| [Cyberpunk 2077](https://support.cdprojektred.com/en/cyberpunk%20/pc/gameplay/issue/2722/supported-peripherals) | [1091500](https://store.steampowered.com/app/1091500/) | Supporto del pad; singoli effetti non censiti | Non documentato |
| [Days Gone](https://www.bendstudio.com/blog/days-gone-remastered-and-broken-road-dlc-update/) | [1259420](https://store.steampowered.com/app/1259420/) | Aptica, aggiornamento PC 2025 | Non documentato |
| [FINAL FANTASY VII REMAKE INTERGRADE](https://www.square-enix-games.com/en_GB/news/final-fantasy-vii-remake-pc) | [1462040](https://store.steampowered.com/app/1462040/) | Pad PS5 e vibrazione; altre funzioni non censite | Non documentato |
| [The Witcher 3: Wild Hunt — Remastered](https://www.thewitcher.com/au/en/news/52041/see-whats-new-in-the-witcher-3-wild-hunt-remastered) | [292030](https://store.steampowered.com/app/292030/) | Aptica nell'edizione Remastered | Non documentato |
| [Ghost of Tsushima DIRECTOR'S CUT](https://www.playstation.com/en-us/games/ghost-of-tsushima/pc/) | [2215430](https://store.steampowered.com/app/2215430/) | Aptica e grilletti adattivi | Non documentato |
| [Marvel's Spider-Man Remastered](https://blog.playstation.com/2022/07/20/marvels-spider-man-remastered-pc-features-revealed/) | [1817070](https://store.steampowered.com/app/1817070/) | Aptica e grilletti adattivi | Non documentato come percorso completo dalla regola |
| [Marvel's Spider-Man: Miles Morales](https://blog.playstation.com/2022/11/18/marvels-spider-man-miles-morales-is-out-now-on-pc/) | [1817190](https://store.steampowered.com/app/1817190/) | Aptica e grilletti adattivi | Non documentato |
| [Returnal](https://blog.playstation.com/2023/01/18/returnal-launches-on-pc-february-15/) | [1649240](https://store.steampowered.com/app/1649240/) | Aptica e grilletti adattivi | Non documentato |
| [Ratchet & Clank: Rift Apart](https://blog.playstation.com/2023/05/30/ratchet-clank-rift-apart-is-coming-to-pc-on-july-26/) | [1895880](https://store.steampowered.com/app/1895880/) | Aptica e grilletti adattivi | Non documentato |
| [God of War Ragnarök](https://www.playstation.com/en-us/games/god-of-war-ragnarok/pc/) | [2322010](https://store.steampowered.com/app/2322010/) | Aptica e grilletti adattivi | Non documentato |
| [Horizon Forbidden West Complete Edition](https://blog.playstation.com/2024/01/25/horizon-forbidden-west-complete-edition-comes-to-pc-on-march-21/) | [2420110](https://store.steampowered.com/app/2420110/) | Aptica e grilletti adattivi | Non documentato |
| [Horizon Zero Dawn Remastered](https://www.playstation.com/en-ca/games/horizon-zero-dawn/horizon-zero-dawn-remastered-pc/) | [2561580](https://store.steampowered.com/app/2561580/) | Aptica, grilletti adattivi e altoparlante | Vibrazione standard dalla patch 1.3.50.0 |
| [The Last of Us Part I](https://www.playstation.com/en-us/games/the-last-of-us-part-i/pc/) | [1888930](https://store.steampowered.com/app/1888930/) | Aptica e grilletti adattivi | Non documentato |
| [The Last of Us Part II Remastered](https://blog.playstation.com/2025/03/20/the-last-of-us-part-ii-remastered-pc-features-and-new-no-return-content-detailed/) | [2531310](https://store.steampowered.com/app/2531310/) | Aptica; gli altri effetti non sono censiti da questa fonte PC | Non documentato |

Per **Horizon Zero Dawn Remastered**, la [patch ufficiale 1.3](https://support.nixxes.com/hc/en-us/articles/49282066978195-Horizon-Zero-Dawn-Remastered-PC-Patch-1-3) distingue la vibrazione Bluetooth da aptica e altoparlante, che richiedono USB. La scelta automatica Bluetooth conserva quindi il supporto nativo documentato per i comandi e la vibrazione standard. Per le funzioni USB indicate in tabella serve il relativo percorso: non le presentiamo come attive sul collegamento Bluetooth nativo.

La regola di **The Witcher 3** richiede anche la dicitura **Remastered** nel titolo installato, perché condivide l'ID Steam con un'edizione precedente. **Horizon Zero Dawn Complete Edition** originale ha un ID diverso e non eredita le funzioni di Remastered. Un gioco con ID Steam sconosciuto non prende le funzioni di un altro solo perché ha un nome simile. Fuori da Steam vengono riconosciuti soltanto i titoli esatti e gli alias presenti nel catalogo.

## Steam Input e audio: le condizioni dipendono dal titolo

OpenPad non disattiva Steam Input per tutti i giochi. Manteniamo le condizioni indicate da ciascun produttore:

- **Days Gone:** [Bend richiede](https://support.bendstudio.com/hc/en-us/articles/40826956860179-Build-18212596) USB, Steam Input disattivato e altoparlante del controller abilitato nelle impostazioni audio di Windows per l'aptica. Abilitare quell'endpoint è un prerequisito: non è una prova che il gioco riproduca dialoghi dal pad.
- **FINAL FANTASY VII REMAKE INTERGRADE:** [Square Enix indica](https://support.jp.square-enix.com/news.php?drt=1684225800&id=13601&la=0&n=2&tag=35bd17a18ab25d2a0e8a10e0876b521859d2ad5a) Steam Input disattivato per la vibrazione. Non estendiamo questa indicazione agli altri giochi.
- **Cyberpunk 2077:** nelle [note 2.1](https://www.cyberpunk.net/en/news/49597/update-2-1-patch-notes) CD PROJEKT RED suggerisce di disabilitare il supporto controller PlayStation di Steam se il gioco si blocca collegando il pad dopo l'avvio.
- **Spider-Man Remastered:** dalla [versione 2.512.0.0](https://support.nixxes.com/hc/en-us/articles/48467929156627-Version-2-512-0-0-Release-Notes) Nixxes documenta grilletti adattivi anche con Steam Input e miglioramenti Bluetooth. Questo non dimostra da solo l'intero insieme di effetti wireless.
- **Horizon Forbidden West:** [Nixxes supporta Steam Input](https://support.nixxes.com/hc/en-us/articles/48738348799123-Which-controllers-are-supported-in-Horizon-Forbidden-West-Complete-Edition-on-PC). La disattivazione è una prova suggerita in caso di problemi; eventuali cambi vanno fatti prima di avviare il gioco.
- **God of War Ragnarök:** [Santa Monica Studio supporta Steam Input](https://support.sms.playstation.com/hc/en-us/articles/27152724494093-Supported-Controllers) e richiede USB per tutte le funzioni DualSense. Non indica un obbligo generale di disattivazione.

L'audio 3D del gioco, l'audio nelle cuffie e l'altoparlante integrato nel pad sono funzioni diverse. Il catalogo indica l'altoparlante solo quando la fonte PC lo nomina esplicitamente. Lo stesso criterio vale per aptica e grilletti: le funzioni descritte per PS5 non vengono trasferite automaticamente alla versione PC.

## Come leggere gli stati nell'app

**Supporto documentato** descrive una fonte per quel gioco e quel collegamento. **Compatibilità standard** descrive una modalità generale, oppure un percorso virtuale da provare. **Da configurare** segnala un limite di driver o del modello di controller. Nessuna di queste etichette certifica che tu stia sentendo un effetto in quel momento.

Il riepilogo distingue le funzioni documentate dalle prove ancora necessarie. Per esempio, un DualSense USB può mostrare «aptica e grilletti adattivi documentati»; lo stesso gioco con un DualSense virtuale mostra che il percorso virtuale è da provare. In modalità Xbox vengono indicati comandi e vibrazione se implementati dal gioco, senza promettere effetti DualSense.

## Aggiornare il catalogo

La fonte incorporata è [GameCompatibilityCatalog.json](https://github.com/MarcoLaudati/OpenPad-Releases/releases/download/v0.7.0/OpenPad-0.7.0-source.zip). Lo schema resta alla versione 1: `DocumentedUsbFeatures` e `DocumentedBluetoothFeatures` sono opzionali e indipendenti. Le chiavi ammesse sono `HapticFeedback`, `AdaptiveTriggers`, `ControllerSpeaker` e `Vibration`. Una lista assente non promette singole funzioni avanzate; una lista presente richiede il supporto documentato dello stesso collegamento.

L'engine espone `GetGameCapabilitySummary(InstalledGame)` per la libreria senza un pad collegato e `GetCapabilitySummary(PadSnapshot, InstalledGame, PadMode)` per il riepilogo del percorso scelto. I metodi usano famiglia del pad, collegamento, identità del gioco e modalità. Non misurano effetti fisici e non modificano impostazioni.

Per aggiungere una regola servono una fonte primaria riferita alla versione PC, l'identità esatta del titolo, il collegamento documentato e gli eventuali requisiti. Poi si verifica che un'edizione diversa o un ID errato non possano ereditare la regola. Le prove automatiche controllano questa scelta; le prove hardware vanno registrate separatamente.

Continua con la [guida funzionale](functional.md) o la [documentazione tecnica](technical.md).

Powered By RagazzoInGamba - Marco Laudati
