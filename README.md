Stazione Meteo Remota

L'Arduino (in questo caso basato sul microcontrollore WeMos R1 D2 ESP8266 Wifi) legge la temperatura da un sensore e invia i dati al server tramite una richiesta HTTP. Questa richiesta HTTP viene gestita da una pagina PHP sul server, che riceve i dati e li registra nel database MariaDB.

Il codice PHP per la pagina save-temperature.php include una query SQL che inserisce la temperatura e l'ora attuale nel database. Inoltre, c'è una pagina PHP che visualizza i dati del database sotto forma di grafici (Temperatura Giornaliera e Temperatura Settimanale). La presentazione dei grafici viene gestita tramite la libreria Chart.js.

L'obiettivo principale di questo progetto è di creare un sistema per raccogliere e visualizzare i dati della temperatura. L'Arduino legge la temperatura e invia i dati al server tramite una richiesta HTTP, mentre le pagine PHP sul server gestiscono la ricezione, il salvataggio e la visualizzazione dei dati.

Perchè WEMOS?
Il WeMos D1 R2 è una scheda basata su ESP8266 che utilizza il microcontrollore ESP8266. Questa scheda è molto più economica rispetto all'Arduino Uno e offre molte funzionalità supplementari, come la connessione Wi-Fi integrata, che possono essere utilizzate per progetti IoT. Inoltre, l'ESP8266 è più potente rispetto all'ATmega328 presente nell'Arduino Uno, rendendo il WeMos D1 R2 una scelta ideale per i progetti che richiedono una maggiore potenza di elaborazione.

Perchè non mi connetto al database direttamente?
La connessione al database non è diretta perché il database potrebbe non essere esposto alla rete pubblica, e potrebbe non essere sicuro accedere al database direttamente dalla rete pubblica. Inoltre, il database potrebbe non essere in grado di gestire direttamente richieste HTTP dalla rete pubblica. La soluzione più sicura è quella di creare una pagina PHP che esegua l'accesso al database e che venga eseguita dal server web. Questo server web accetta richieste HTTP dalla rete pubblica e le inoltra al database, garantendo una gestione sicura dei dati.

I dati vengono stampati nella console di Arduino IDE ogni 5 secondi, e viene inviata la temperatura ogni 30 minuti da mezzanotte; è stato anche aggiunto un led di allarme che si attiva se la temperatura è superiore a 30 o inferiore a 0, e si disattiva se compresa tra 0 e 30.

I grafici sono 2 e mostrano temperatura giornaliera (le ultime 24 temperature registrate), e temperatura massima/minima settimanale.
