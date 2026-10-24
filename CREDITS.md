# Crediti OpenPad

**Powered By RagazzoInGamba - Marco Laudati**

OpenPad è il progetto di **Marco Laudati · RagazzoInGamba**: un'app libera per collegare il pad, aprire il gioco e mantenere i comandi originali. Il frontend OpenPad, l'integrazione del motore, la libreria dei giochi, la selezione automatica della compatibilità, il setup guidato, l'identità visiva e la documentazione sono sviluppati per questo progetto.

Repository ufficiale: [Sorgenti delle versioni](https://github.com/MarcoLaudati/OpenPad-Releases/releases).
Distribuzioni e sorgenti delle release: [MarcoLaudati/OpenPad-Releases](https://github.com/MarcoLaudati/OpenPad-Releases).

Il credito identifica OpenPad e il suo autore. Le librerie e il codice riutilizzati mantengono autori, avvisi e licenze originali: nessun lavoro upstream viene attribuito a OpenPad.

## Il lavoro su cui costruiamo

Il motore hardware deriva da [DualSense Client](https://github.com/DualSenseClient/DualSenseClient), commit `fdfcf3a6cd08ab20619aa3d3363d7580789b4a94`, distribuito sotto GPL-3.0. I progetti `DualSenseClient.*` e la documentazione originale conservata in [README.upstream.md](README.upstream.md) permettono di riconoscerne provenienza e autori. Il frontend originale è conservato nei sorgenti; l'app distribuita usa il frontend OpenPad.

| Componente | Autori e progetto di origine | Licenza |
| --- | --- | --- |
| Motore DualSense | [DualSense Client e contributori](https://github.com/DualSenseClient/DualSenseClient) | GPL-3.0 |
| Virtualizzazione libVIIPER | [DualSenseClient/VIIPER](https://github.com/DualSenseClient/VIIPER) | GPL-3.0, con proprie dipendenze |
| Accesso HID | [HIDAPI e contributori](https://github.com/libusb/hidapi) | Licenze alternative conservate nel bundle |
| Driver USB/IP | [vadimgrn/usbip-win2](https://github.com/vadimgrn/usbip-win2) | BSD-2-Clause |
| Isolamento dei controller | [Nefarius/HidHide](https://github.com/nefarius/HidHide) | MIT |
| Client ViGEm | [Nefarius/ViGEm.NET](https://github.com/nefarius/ViGEm.NET) | MIT |
| Interfaccia desktop | [Avalonia e contributori](https://github.com/AvaloniaUI/Avalonia) | MIT |
| Installer e applicazione degli aggiornamenti | [Velopack e contributori](https://github.com/velopack/velopack), versione 1.2.161 | MIT |
| Supporto audio | [SoundFlow](https://github.com/LSXPrime/SoundFlow), [Concentus](https://github.com/lostromb/concentus) | MIT, BSD |
| Decodifica WAV, MP3 e FLAC | [MiniAudio e contributori](https://github.com/mackron/miniaudio), tramite SoundFlow | Unlicense / MIT-0 |

Le versioni fissate, gli hash, le fonti dei pacchetti e le note di ridistribuzione sono in [THIRD-PARTY-NOTICES.md](THIRD-PARTY-NOTICES.md) e nelle cartelle `third-party/native-licenses` e `third-party/driver-licenses`. Gli installer ufficiali dei driver sono inclusi senza modificarne firme o attribuzioni. I prerequisiti Microsoft restano soggetti alle condizioni dei rispettivi produttori.

Le licenze NuGet, del runtime .NET e delle dipendenze grafiche/audio sono conservate in `third-party/managed-licenses`, con URL e hash in `third-party/managed-provenance.json`. La distribuzione OpenPad usa i decoder MiniAudio e non include il componente FFmpeg opzionale dell'interfaccia upstream.

## Licenza e materiali

OpenPad è distribuito con la licenza [GNU GPL versione 3](LICENSE). La distribuzione del programma deve essere accompagnata dalle licenze e dal sorgente corrispondente, con le istruzioni per ricompilarlo.

Il marchio e l'icona OpenPad appartengono all'identità di questo progetto. Il render illustrativo del controller e i riferimenti grafici sono stati creati con ImageGen integrato; i relativi prompt sono conservati in `design`. I nomi dei controller e dei servizi identificano i prodotti dei rispettivi titolari.

**Powered By RagazzoInGamba - Marco Laudati**
