# Licenze delle dipendenze OpenPad

Powered By RagazzoInGamba - Marco Laudati

Questa cartella conserva i testi originali delle licenze e dei notices NuGet della distribuzione Windows x64, del runtime .NET self-contained e del runtime usato dal setup NativeAOT. I crediti OpenPad non sostituiscono gli autori e i diritti dei componenti terzi.

L'inventario [`../managed-provenance.json`](../managed-provenance.json) indica per ogni pacchetto la versione, l'URL dell'archivio NuGet, il suo SHA-512 e i testi copiati con SHA-256. `nugetContentHash` conserva anche l'hash normalizzato usato dal restore e dal file `deps.json`: per i pacchetti firmati è distinto dall'hash dei byte dell'archivio. Dove il NuGet dichiara una licenza senza includerne il testo, il testo proviene dal commit upstream indicato dal NuSpec. Per ViGEm.NET il commit deriva dal tag ufficiale `v1.21.256`.

`packages/` contiene i file originali senza modificarne copyright o clausole. I notices completi SkiaSharp/HarfBuzz e .NET includono le rispettive attribuzioni transitive. Il file `Velopack-LICENSE.txt` alla radice è conservato anche per i verificatori delle distribuzioni precedenti.

OpenPad usa il backend MiniAudio di SoundFlow per **WAV, MP3 e FLAC**. `SoundFlow.Codecs.FFMpeg` e `soundflow-ffmpeg.dll` sono esclusi dalla distribuzione. Il notice upstream SoundFlow viene conservato integralmente e menziona anche componenti opzionali del progetto upstream, compreso FFmpeg: quella menzione non indica che siano inclusi in OpenPad. Il sorgente della GUI upstream conserva la propria dipendenza opzionale; questo inventario riguarda i binari OpenPad.

La licenza MiniAudio aggiuntiva proviene dal submodule esatto usato da SoundFlow 1.4.1. Le licenze ANGLE aggiuntive provengono dai riferimenti del suo build/DEPS; le dipendenze condizionali sono conservate per prudenza, senza dichiarare di aver ricostruito ogni oggetto del DLL upstream.

La verifica si esegue dopo la publish, prima di copiare `third-party` nel pacchetto:

```powershell
./scripts/prepare-managed-licenses.ps1 -DependenciesPath artifacts/OpenPad-win-x64/OpenPad.deps.json
```

Lo script non compila né esegue pacchetti. Verifica i testi versionati e rifiuta versioni runtime non censite, hash diversi e il DLL FFmpeg ritirato. I testi mancanti si possono recuperare dalla cache NuGet dopo `dotnet restore`; `-RestoreMissing` abilita esplicitamente il recupero HTTPS dagli URL fissati. I byte recuperati devono corrispondere agli hash dell'inventario. `-VerifyCatalogOnly` controlla i testi prima che sia disponibile una publish e non verifica il contenuto di una distribuzione.
