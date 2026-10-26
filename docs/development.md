# Sviluppare OpenPad

**Powered By RagazzoInGamba - Marco Laudati**

Qui si parte dai sorgenti e si arriva al pacchetto completo. Il progetto da avviare è `OpenPad.Desktop`: la GUI originale `DualSenseClient.GUI` è conservata come upstream e non è l'interfaccia OpenPad.

## Requisiti

- Windows x64 per preparare e verificare il pacchetto driver.
- .NET SDK **10.0.402**, fissato in `global.json` senza roll-forward e senza versioni preliminari.
- PowerShell, Git e accesso alle dipendenze NuGet e alle release ufficiali fissate.

Il pacchetto per giocare include il runtime .NET. L'SDK serve solo a chi compila.

La CI installa lo stesso SDK dal global.json e ne controlla la versione prima della build. La pubblicazione resta sul runtime 10.0.13 censito nel catalogo delle licenze; ogni aggiornamento del runtime richiede una nuova verifica delle dipendenze distribuite.

## Compilazione completa

Scarica i [sorgenti corrispondenti alla 0.7.4](https://github.com/MarcoLaudati/OpenPad-Releases/releases/download/v0.7.4/OpenPad-0.7.4-source.zip) ed estraili in una cartella locale. Apri PowerShell nella cartella che contiene `OpenPad.slnx`, poi esegui:

```powershell
./scripts/build-openpad.ps1 -Test -Publish
./scripts/package-openpad.ps1 -IncludeBinary
./scripts/verify-distribution.ps1 -OutputPath ./artifacts/verification/distribution.json
```

`build-openpad.ps1` cerca `dotnet`; se non contiene un SDK e sul PC esiste un SDK locale nella cartella strumenti Codex dell'utente, usa quello. Altrimenti occorre installare un SDK compatibile. Nessun percorso personale del maintainer è necessario.

La build prepara le librerie native dai pin in `third-party/native-provenance.json` e gli installer dal manifest incorporato. Gli script verificano hash, firme e firmatari e **non eseguono installer o helper driver**. Un file mancante o un controllo fallito interrompe il processo.

La publish viene creata in una directory nuova, verificando le licenze dei pacchetti effettivi con `prepare-managed-licenses.ps1`, e sostituisce l'output soltanto a lavoro completato. La precedente cartella pubblicata rimane in `artifacts/OpenPad-previous-*` come backup locale. Questo evita di portare nel nuovo ZIP dipendenze ritirate; FFmpeg non fa parte della distribuzione OpenPad 0.7.

La pubblicazione self-contained è in `artifacts/OpenPad-win-x64`. Gli ZIP sorgenti e binari vengono creati in `artifacts`; la versione è gestita dagli script di packaging. `SHA256SUMS.txt` contiene gli hash dei due archivi. Non pubblicare la cartella del tuo profilo utente insieme al pacchetto.

Lo ZIP sorgenti comprende anche gli snapshot di libVIIPER e HIDAPI in `third-party/sources`, con istruzioni upstream, commit e SHA256 registrati nel manifest dedicato. Il packaging scarica e controlla questi sorgenti come dati, senza eseguirli. `verify-release-content.py` verifica presenza, pin e assenza di configurazioni reali, chiavi private o token negli archivi pubblicabili.

## Controlli su GitHub

La CI esegue build e test Windows, prepara e verifica la distribuzione, crea l'installer Velopack e compila la documentazione con `--strict`. Non avvia installer di driver e non pubblica release o siti in automatico. La raccolta degli artifact è opzionale per rispettare la quota dell'account.

## Installer e canale pubblico

`scripts/build-installer.ps1` crea il setup per utente e il pacchetto completo Velopack, usando gli strumenti fissati in `.config/dotnet-tools.json`. Con MSVC Build Tools e Windows SDK, lo script compila il piccolo bootstrapper NativeAOT; senza strumenti C++ produce un eseguibile self-contained più grande. In entrambi i casi non serve un runtime già installato sul PC dell'utente. Il pacchetto applicativo ha identità `OpenPad.App` e destinazione `%LOCALAPPDATA%\Programs\OpenPad.App`; i dati utente rimangono sotto `OpenPad` e i driver non vengono rimossi dall'uninstaller.

La destinazione è esplicita: nel collaudo su questo PC la radice LocalAppData cifrata EFS rifiutava i rename atomici, mentre Programs li permette. Il bootstrapper usa l'opzione ufficiale `--installto` e un preflight limitato alla cartella dell'app; non decritta il profilo, non sposta preferenze e non sostituisce l'aggiornamento con copie manuali.

```powershell
./scripts/build-openpad.ps1 -Test -Publish
./scripts/package-openpad.ps1 -IncludeBinary
./scripts/verify-distribution.ps1
./scripts/build-installer.ps1
```

La suite `OpenPad.Updates.Tests` verifica firma del feed, trust policy e pacchetti alterati. Il collaudo di installazione/aggiornamento/disinstallazione usa un'identità fixture distinta per proteggere l'installazione normale. Non confonderlo con una prova di tutti i giochi o driver.

Il repository di sviluppo resta privato. La distribuzione pubblica `MarcoLaudati/OpenPad-Releases` contiene soltanto descrizione, feed firmato, pacchetti e sorgenti corrispondenti alle release. Prima della pubblicazione controlla gli archivi: niente chiavi private, credenziali, configurazioni reali, log o report di dispositivo.

`scripts/sign-update-feed.ps1` prepara il feed con RSA-PSS usando la chiave esterna al repository. Su questo PC il materiale privato è conservato in `%LOCALAPPDATA%\OpenPad-Signing`, con ACL limitate; non è una dipendenza richiesta per compilare l'app. Il progetto incorpora solo la chiave pubblica. Chi crea un fork deve impostare il proprio canale e la propria chiave, senza sostituire silenziosamente la chiave di una release già installata. La firma Authenticode dell'EXE richiede un certificato separato e rimane un lavoro aperto.

Il salvataggio degli artifact di Actions è facoltativo: nell'esecuzione manuale si può attivare `save_artifacts` quando lo spazio dell'account è disponibile. I controlli sui push non dipendono da quella quota. I pacchetti distribuiti agli utenti sono negli allegati delle [release](https://github.com/MarcoLaudati/OpenPad-Releases/releases).

## Lavorare su un componente

```powershell
dotnet restore source/OpenPad.Desktop/OpenPad.Desktop.csproj
dotnet build source/OpenPad.Desktop/OpenPad.Desktop.csproj -c Release
dotnet test tests/OpenPad.Tests/OpenPad.Tests.csproj -c Release
dotnet test tests/DualSenseClient.Tests/DualSenseClient.Tests.csproj -c Release
```

Se mancano le risorse native, esegui prima `scripts/prepare-openpad.ps1`. Per il bundle driver usa `scripts/prepare-drivers.ps1`. Entrambi preparano file verificati senza modificare i driver del sistema.

| Area | Dove intervenire |
| --- | --- |
| Interfaccia e stato presentato | `source/OpenPad.Desktop` |
| Riconoscimento giochi e profili | `source/OpenPad.Engine/GameLibrary`, policy e catalogo nell'Engine |
| Ciclo di vita dei pad | `source/OpenPad.Engine/OpenPadEngine.cs` |
| Setup, validazione e fonti riavvio | `source/OpenPad.Engine/Drivers` |
| Prima configurazione e ripresa | `DriverSetupModel`, `DriverSetupPresentation`, `SetupWorkflow` nel Desktop |
| Isolamento e recupero | `source/OpenPad.Engine/ControllerIsolation.cs` |
| Test OpenPad | `tests/OpenPad.Tests` |
| Regressioni backend upstream | `tests/DualSenseClient.Tests` |

## Verifiche che non aprono il controller

Dopo la pubblicazione:

```powershell
./artifacts/OpenPad-win-x64/OpenPad.exe --scan-library --output ./artifacts/verification/library.json
./artifacts/OpenPad-win-x64/OpenPad.exe --driver-status --output ./artifacts/verification/drivers.json
./artifacts/OpenPad-win-x64/OpenPad.exe --verify-driver-pack --output ./artifacts/verification/packages.json
```

La scansione legge metadati locali. Lo stato driver legge Windows e il promemoria del setup. La verifica del bundle prepara e controlla i pacchetti senza installarli. Questi controlli non dimostrano che una partita o l'isolamento funzionino già.

Gli eseguibili Windows GUI possono restituire il controllo alla shell prima di aver scritto il report. Negli script che dipendono dal risultato usa `Start-Process -Wait -PassThru` e controlla il codice d'uscita.

## Prove con controller e interfaccia

Chiudi giochi e altre istanze OpenPad prima della diagnosi hardware. `--test-mode` accetta Xbox360, DualShock4 o DualSense e ripristina il nativo nel `finally`; `--test-xbox` rimane compatibile. Il mutex condiviso impedisce una seconda sessione insieme alla GUI. Le prove virtuali controllano readiness, isolamento e scomparsa del nuovo endpoint; non certificano gli effetti percepiti nel gioco:

```powershell
./artifacts/OpenPad-win-x64/OpenPad.exe --diagnose --output ./artifacts/verification/native.json
./artifacts/OpenPad-win-x64/OpenPad.exe --diagnose --test-xbox --output ./artifacts/verification/xbox.json
./artifacts/OpenPad-win-x64/OpenPad.exe --diagnose --test-mode DualShock4 --output ./artifacts/verification/dualshock4.json
./artifacts/OpenPad-win-x64/OpenPad.exe --diagnose --test-mode DualSense --output ./artifacts/verification/dualsense.json
```

Per la UI, apri il pacchetto compilato e usa:

```powershell
./scripts/verify-ui.ps1 -ReportTag local
./scripts/verify-ui.ps1 -Lifecycle -ReportTag lifecycle
./scripts/verify-advanced-ui.ps1 -ReportTag advanced
```

La verifica UI naviga, cerca, controlla la conservazione delle schede e acquisisce la sola finestra OpenPad. Con `-Lifecycle` minimizza, riapre la stessa istanza, chiude e rilancia l'app: eseguila senza partite aperte. Non preme installazione, avvio gioco o riavvio Windows.

Dalla 0.5.0, le suite verificano anche preparazione sequenziale e relativo bookkeeping, deadline e cancellazione, recupero limitato, report freschi, normalizzazione esclusivamente visiva, reset degli effetti e policy di navigazione del pad. La checklist hardware ha test contro le false conferme: niente passaggio USB/Bluetooth senza input su entrambi i collegamenti e niente conferma feedback ereditata da una sessione precedente.

Per il collaudo fisico apri **Controller → Verifica questo pad** e segui la checklist. La prova degli effetti è esplicita, in modalità nativa e fuori dalle partite rilevate; conferma soltanto ciò che percepisci. Scollega/ricollega, prova USB/Bluetooth e sospensione/ripresa separatamente, poi **Salva esito**. Il file locale `hardware-check-latest.json` non contiene identificativi dei dispositivi. Un campo **Da provare** o **Non verificabile** resta tale nel registro pubblico.

Per la navigazione reale prova D-pad/stick, conferma, indietro, cambio sezione, scroll e ricerca con la tastiera nell'app. Verifica che i comandi già premuti prima del ritorno a OpenPad non attivino azioni e che **Prova i tasti** isoli il focus. I dialoghi di autorizzazione e configurazione di Windows restano controlli del sistema operativo.

In una prova pratica annota controller, collegamento, versione del gioco, percorso nativo/virtuale, driver operativi, Steam Input e doppi input. Separa presenza di uno slot XInput, riconoscimento nel log del gioco e risposta provata con il pad.

## Documentazione e pubblicazione

Il manuale attuale comprende [funzionalità](functional.md), [architettura](technical.md), [installazione](installation.md) e [problemi noti](troubleshooting.md). Le pagine in `docs/guides` sono archivio dell'interfaccia upstream e portano un avviso esplicito.

Le dipendenze del sito sono in `requirements.txt`. La build locale della documentazione non pubblica automaticamente il sito:

```powershell
python -m pip install -r requirements.txt
python -m zensical build --strict
```

Prima di condividere una build, verifica distribuzione, licenze e documentazione. I dati delle prove sul tuo PC rimangono locali; il [registro pubblico delle verifiche](https://github.com/MarcoLaudati/OpenPad-Releases/blob/main/VERIFICATION.md) contiene il riepilogo anonimizzato.

Vedi [come contribuire](CONTRIBUTING.md) e i [crediti](https://github.com/MarcoLaudati/OpenPad-Releases/blob/main/CREDITS.md).

**Powered By RagazzoInGamba - Marco Laudati**
