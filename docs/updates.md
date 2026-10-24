# Installazione e aggiornamenti

**Powered By RagazzoInGamba - Marco Laudati**

Il canale pubblico è [OpenPad-Releases](https://github.com/MarcoLaudati/OpenPad-Releases). Contiene pacchetti, note di versione e l'archivio dei sorgenti corrispondenti. Il repository di sviluppo resta privato; non occorre accedere a GitHub per scaricare o aggiornare l'app.

## Installer e cartella portatile

L'installer Windows x64 usa Velopack e installa l'app per il tuo utente, senza richiedere privilegi amministratore per i soli file dell'app. Runtime .NET, librerie native, icona, documentazione e pacchetti ufficiali dei driver sono inclusi. I driver rimangono componenti Windows: il loro setup richiede la conferma amministratore e può chiedere un riavvio.

L'installazione usa `%LOCALAPPDATA%\Programs\OpenPad.App`. Un piccolo bootstrapper nativo passa questo percorso all'installer Velopack e verifica che la destinazione permetta lo spostamento delle cartelle richiesto dagli aggiornamenti. Non modifica la cifratura del profilo Windows. Preferenze, libreria personale, profili, esiti del setup e dati locali restano in `%LOCALAPPDATA%\OpenPad`. Aggiornamento e disinstallazione dell'app non devono cancellare questi dati o rimuovere driver condivisi.

La versione ZIP resta disponibile. Estrai tutta la cartella e apri `OpenPad.exe`; l'aggiornamento integrato richiede l'installazione Velopack. La UI distingue esplicitamente i due casi.

## Cosa succede automaticamente

Nella versione installata, il controllo automatico è attivo di default: dopo l'avvio e poi periodicamente verifica il canale **Anteprima**, scarica una versione successiva e ne controlla l'autenticità. In **Impostazioni → Aggiornamenti** puoi vedere lo stato, controllare a mano o disattivare il download automatico.

Un aggiornamento verificato viene applicato alla chiusura quando non risultano partite o configurazioni in corso. **Aggiorna e riapri** esegue la stessa verifica prima di chiedere l'uscita. Se un gioco è aperto l'app rimanda l'applicazione, senza chiuderlo. Un download interrotto, un errore di rete o una verifica fallita lasciano disponibile la versione corrente; la X continua a chiudere normalmente OpenPad.

Le richieste di aggiornamento contattano GitHub per feed e pacchetti. Non inviano la libreria dei giochi o i profili dei controller. Senza Internet puoi continuare a giocare con la versione presente.

## Due firme diverse

Gli aggiornamenti sono verificati con una chiave pubblica incorporata in OpenPad. Il feed firmato RSA-PSS descrive versione, architettura e pacchetto; il download viene verificato prima dell'applicazione. La chiave privata di pubblicazione rimane fuori dal repository e dagli archivi distribuiti.

Questa protezione è distinta dalla **firma Authenticode dell'editore Windows**. Il progetto non dispone ancora di un certificato commerciale: EXE e installer possono mostrare **editore sconosciuto** o un avviso SmartScreen. OpenPad non installa certificati radice personali per trasformare questo stato in un editore verificato.

I due installer driver inclusi conservano invece le loro firme ufficiali e vengono verificati prima dell'esecuzione. Le note della release riportano le prove completate e quelle ancora aperte.
