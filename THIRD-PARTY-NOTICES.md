# OpenPad: origini e licenze

**Powered By RagazzoInGamba - Marco Laudati**

Questo credito si riferisce al progetto OpenPad. Gli autori dei componenti
riutilizzati mantengono i rispettivi diritti e le attribuzioni indicate qui e
nei testi di licenza originali. Crediti del progetto: [CREDITS.md](CREDITS.md).

OpenPad è un frontend indipendente che riutilizza le librerie di
[DualSense Client](https://github.com/DualSenseClient/DualSenseClient), commit
`fdfcf3a6cd08ab20619aa3d3363d7580789b4a94`, scaricato il 24 ottobre 2026.
Gli autori originali mantengono i rispettivi diritti. La licenza del progetto
derivato è **GNU GPL versione 3**, nel file `LICENSE`. La documentazione upstream
originale è conservata in `README.upstream.md`.

Il codice aggiunto per OpenPad si trova in `source/OpenPad.Engine`,
`source/OpenPad.Desktop`, `source/OpenPad.Updates` e nei test OpenPad. Le librerie hardware upstream
sono mantenute nei progetti `DualSenseClient.*`; il frontend originale rimane
disponibile nei sorgenti ma non è incluso nel programma OpenPad.

Dipendenze principali:

| Componente | Fonte | Licenza |
| --- | --- | --- |
| DualSense Client | https://github.com/DualSenseClient/DualSenseClient | GPL-3.0 |
| libVIIPER v1.0.1 | https://github.com/DualSenseClient/VIIPER | GPL-3.0; dipendenze elencate nelle sue note |
| HIDAPI 0.15.0 | https://github.com/libusb/hidapi | BSD / GPL-3.0 / licenza HIDAPI, a scelta |
| Nefarius.ViGEm.Client | https://github.com/nefarius/ViGEm.NET | MIT |
| Avalonia | https://github.com/AvaloniaUI/Avalonia | MIT |
| Velopack / vpk 1.2.161 | https://github.com/velopack/velopack | MIT |
| SoundFlow | https://github.com/LSXPrime/SoundFlow | MIT |
| MiniAudio, decoder incorporati | https://github.com/mackron/miniaudio | Unlicense / MIT-0 |
| Concentus | https://github.com/lostromb/concentus | BSD |

Le licenze native complete sono in `third-party/native-licenses` e devono
accompagnare le distribuzioni. URL, versioni e hash dei binari nativi sono in
`third-party/native-provenance.json`. I metadati e le licenze delle dipendenze
NuGet sono disponibili nei rispettivi pacchetti. Per ridistribuire un eseguibile
derivato GPL, fornire anche il sorgente corrispondente completo e le istruzioni
di compilazione di questa versione.

La licenza Velopack è conservata in `third-party/managed-licenses/Velopack-LICENSE.txt` e accompagna installer e pacchetti. La chiave pubblica dell'updater fa parte dei sorgenti; il materiale privato di firma e i dati reali dei controller non sono distribuiti. La verifica crittografica dell'aggiornamento non viene presentata come firma Authenticode Windows.

Il catalogo `third-party/managed-provenance.json` censisce pacchetti NuGet e runtime effettivamente distribuiti, con hash dei pacchetti, testi e fonti fissate. Include avvisi delle dipendenze ANGLE e il testo MiniAudio. `prepare-managed-licenses.ps1` verifica la distribuzione reale e interrompe il packaging in caso di dipendenza non censita o testo alterato.

OpenPad decodifica **WAV, MP3 e FLAC** con MiniAudio. **SoundFlow.Codecs.FFMpeg e soundflow-ffmpeg.dll non sono inclusi nell'app distribuita**. La GUI originale, conservata soltanto nei sorgenti, mantiene la propria dipendenza opzionale. I notices SoundFlow originali sono riprodotti integralmente e possono descrivere estensioni non spedite da OpenPad; questo non le aggiunge al pacchetto.

L'archivio sorgenti della release include anche gli snapshot upstream **libVIIPER v1.0.1** e **HIDAPI 0.15.0**, con licenze e istruzioni di build originali, in `third-party/sources`. URL, commit e SHA256 sono fissati in `third-party/native-source-provenance.json`; `scripts/prepare-native-sources.ps1` li verifica senza eseguirli. Il submodule SDL di VIIPER serve ai suoi test opzionali, non alla compilazione della libreria distribuita.

Il repository [Paliverse/DualSenseX](https://github.com/Paliverse/DualSenseX)
è stato esaminato durante la preparazione di OpenPad. Nel materiale esaminato
non è stato identificato un progetto completo compilabile con licenza
riutilizzabile: nessun suo codice o binario è incluso in questa versione di
OpenPad. OpenPad non sblocca funzioni a pagamento di DSX.

## Driver ufficiali inclusi nel pacchetto

Il bundle portatile include USBip-win2 0.9.8.1 x64 (BSD-2-Clause) e HidHide
1.5.230.0 (MIT), senza alterarne gli installer ufficiali firmati. Avvisi e
licenze completi: `third-party/driver-licenses`. Manifest dei pin:
`source/OpenPad.Engine/Drivers/DriverPackages.json`. ViGEmBus non è distribuito
né installato da questo bundle. Gli eventuali prerequisiti Microsoft restano
soggetti alle condizioni e ai verificatori degli installer dei rispettivi produttori.
