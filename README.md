# BACI

Fonte: Gaulier, G. and Zignago, S. (2010) BACI: International Trade Database at the Product-Level. The 1994-2007 Version. CEPII Working Paper, N°2010-23.

Il dataset BACI, suddiviso su più file relativi a un particolare anno, riporta, per ogni anno, il valore in migliaia di USD (ma anche in kg) dei beni, a livello disaggregato, scambiati tra i paesi che compongono il dataset. Il periodo considerato va dal 1996 al 2022. 

Il codice contenuto in "baci.ipynb" crea un output con le seguenti variabili: 
- origin: paese esportatore espresso in ISO3c
- destination: paese importatore espresso ISO3c
- year: anno in cui viene registrato lo scambio commerciale
- value_baci: valore dei beni a livello aggregato scambiati in USD 

# COMTRADE

Fonte: UN COMTRADE Database

Il dataset COMTRADE riporta, per ogni anno, il valore in USD dei beni, a livello aggregato, scambiati tra i paesi che compongono il dataset. Il periodo considerato va dal 1997 al 2020. Vengono riportati i paesi con diversi codici identificativi e anche la media dei valori in USD dei beni ogni 5 anni.

Il codice contenuto in "comtrade.ipynb" crea un output con le seguenti variabili:
- origin: paese esportatore espresso in ISO3c
- destination: paese importatore espresso in ISO3c
- year: anno in cui viene registrato lo scambio commerciale
- value_comtrade: valore dei beni a livello aggregato scambiati in USD 

# USICT 

Fonte: USICT DataWeb 

Il dataset COMTRADE, suddiviso su più file relativi a un particolare anno, riporta, per ogni anno, il valore in milioni di USD dei servizi scambiati tra i paesi che compongono il dataset, in diversi tipi di industrie. Il periodo considerato va dal 2000 al 2020. Vengono riportati i paesi con il nome completo e con i codici identificativi ISO3c (e poi flag_mirror e flag_zero?). 

Il codice contenuto in "usict.ipynb" crea un output con le seguenti variabili:
- origin: paese esportatore espresso in ISO3c
- destination: paese importatore espresso in ISO3c
- year: anno in cui viene registrato lo scambio dei servizi
- value_usict: valore dei servizi a livello aggregato scambiati in milioni di USD

# CPIS 

Fonte: International Monetary Fund - Coordinated Portfolio Investment Survey (CPIS)

Il dataset CPIS riporta, per ogni anno, il valore in USD degli scambi finanziari, tra i paesi che compongono il dataset, espressi come crediti dei paese esportatore nei confronti del paese importatore. Il periodo considerato va dal 2001 al 2020. Vengono riportati i paesi con il nome completo e con il codice identificativo ISO3n e viene riportata anche la media dei crediti ogni 5 anni.

Il codice contenuto in "cpis.ipynb" crea un output con le seguenti variabili:
- origin: paese creditore espresso in ISO3c
- destination: paese debitore espresso in ISO3c
- year: anno in cui viene registrato lo scambio finanziario
- value_cpis: valore dei credito totale in USD

Ho eliminato i dati negativi in quanto erano pochi.

# BIS

Fonte: BIS Data Portal

Il dataset BIS riporta, per ogni anno, su base quadrimestrale, il valore in milioni di USD del credito e del debito di ogni tipo (debt securities long and short term, loans and deposits), in ogni tipo di valuta maggiormente utilizzata, scambiato tra singoli paesi, tra gruppi di paesi, tra istituzioni all'interno di un singolo paese, tra organizzazioni internazionali. Il periodo considerato va dal 1997 al 2020. Vengono riportati i paesi con il codice identificativo ISO2c.

Il codice contenuto in "bis.ipynb" crea due output. Il primo ("bis.csv") è composto dalle seguenti variabili:
- origin: paese dichiarante lo scambio, espresso in ISO3c
- destination: paese dichiarato nello scambio, espresso in ISO3c
- year: anno in cui viene dichiarato lo scambio finanziario
- claim_bis: valore del credito totale in milioni di USD
- claim_bis: valore del debito totale in milioni di USD

Il secondo output ("bis_fromcredttodebt.csv") contiene le seguenti variabili:
- origin: paese creditore espresso in ISO3c
- destination: paese debitore espresso in ISO3c
- year: anno in cui viene dichiarato lo scambio finanziario
- claim_bis: valore del credito totale in milioni di USD dichiarato dal creditore
- claim_derived_bis: valore del credito totale in milioni di USD dichiarato dal debitore 

Ho eliminato i dati negativi in quanto erano pochi.

# THOMSON REUTERS

Fonte: Dueñas, M., Mastrandrea, R., Barigozzi, M. et al. Spatio-Temporal Patterns of the International Merger and Acquisition Network. Sci Rep 7, 10789 (2017).

Il dataset THOMSON REUTERS, suddiviso su più file relativi a un particolare anno, è costituito, per ogni anno, da matrici le cui righe rappresentano i direct investor (DI) residienti in un paese e le cui colonne rappresentano le imprese di diretto investimento (DIENT) residienti in un altro paese. Altri due file riportano la lista dei paesi e degli anni presi in considerazione. Il periodo considerato va dal 1995 al 2020.

Il codice contenuto in "ts.ipynb" crea un output con le seguenti variabili:
- origin: paese dove risiede l'investitore diretto espresso in ISO3c
- destination: paese dove risiede l'impresa di investimento diretto espresso in ISO3c
- year: anno in cui viene dichiarato il flusso di investimento
- value_ts: valore del flusso di investimento in milioni di USD 
  
# CDIS 

Fonte: International Monetary Fund - Coordinated Direct Investment Survey (CDIS)

Il dataset CDIS riporta, per ogni anno, diverse variabili associate all'investimento diretto proveniente dall'investitore diretto (DI) residiente in un certo paese e indirzzato all'impresa di diretto investimento che il DI possiede almeno per il 10%, residiente in un altro paese (DIENT). Più nello specifico tali variabili riportano il valore degli strumenti del debito sia lordi che netti, sia intesi come debiti (*liabilities*) sia come crediti (*asset*), sia nei confronti di un'impresa di invesitmento diretto sia nei confronti di un'impresa "amica" (*fellow enterprise*), di cui non si possiede il 10% del potere di voto; di ognuna di queste variabili c'è il valore *derived* ossia il corrispettivo valore del flusso dell'investimento ottenuto considerando ciò che dichiara il paese partner nello scambio. Ho ritenuto opportuno mantenere, oltre alle colonne che riportano l'ISO3c dei paesi creditori e debitori e l'anno in cui viene registrato lo scambio, solo le colonne riportanti il valore degli investimenti diretti totali, escludendo i debiti/crediti con le *fellow enterprises*, differenziati per direzionalità, ossia considerando caso *outward* e  quello *inward*, ottenuti dalla somma tra ogni tipo di strumento di debito (asset-liabilities nel caso outward, e liabilities-asset nel caso inward) e il netto dell'equity. E' il dato che più si avvicina anche ai dati del dataset UNCTAD. Il periodo considerato va dal 2009 al 2020.

Il codice contenuto in "cdis.ipynb" crea un output con le seguenti 
- origin: paese dove risiede l'investitore diretto (DI) espresso in ISO3c
- destination: paese dove risiede l'impresa di investimento diretto (DIENT) espresso in ISO3c
- year: anno in cui viene dichiarato il flusso di investimento
- outward_cdis: valore del flusso di investimento in USD dichiarato da DI
- outward_derived_cdis: valore del flusso di investimento in USD dichiarato da DIENT

# UNCTAD

Fonte: UNCTAD Stat

Il dataset UNCTAD è composti da tre file: i primi due, molto simili, riportano, per ogni anno, il valore del flusso di investimento diretto (sia dal punto di vista *outward* che *inward*) proveniente da un investitore diretto residente in un certo paese e indirizzato a un'impresa di investimento diretto residente in un altro paese. Tra i due dataset relativi al flusso si è deciso di lavorare con quello che presentava il maggior numero di dati. Il terzo file riporta, per ogni anno, il valore accumulato, alla fine del periodo di osservazione, dell'investimento diretto (*stock*) da DI a DIENT (sia *inward* che *outward*). Il periodo considerato va dal 1990 al 2020. 

Il codice contenuto in "fdi_unctad.ipynb" crea quattro output. I primi due sono relativi al flusso di investimento.
Il primo output ("flow_unctad.csv") è composto dalle seguenti variabili:
- origin: paese dichiarante il flusso di investimento diretto, espresso in ISO3c
- destination: paese dichiarato partner nel flusso di investimento diretto, espresso in ISO3c
- year: anno in cui viene dichiarato il flusso di investimento diretto
- inward_flow_unctad: valore del debito di investimento diretto in milioni di USD
- outward_flow_unctad: valore del credito di investimento diretto in milioni di USD

Il secondo output ("flow_confronto.csv") contiene le seguenti variabili:
- origin: paese dove risiede l'investitore diretto (DI) espresso in ISO3c
- destination: paese dove risiede l'impresa di investimento diretto (DIENT) espresso in ISO3c
- year: anno in cui viene dichiarato il flusso di investimento diretto
- outward_cdis: valore del flusso di investimento diretto in milioni di USD dichiarato da DI
- outward_derived_cdis: valore del flusso di investimento diretto in milioni di USD dichiarato da DIENT

Gli altri due ouput sono relativi al valore accumulato dell'investimento (*stock*). 
Il terzo output ("stock_unctad.csv") è composto dalle seguenti variabili:
- origin: paese dichiarante lo stock di investimento diretto, espresso in ISO3c
- destination: paese dichiarato partner nello stock di investimento diretto, espresso in ISO3c
- year: anno in cui viene dichiarato lo stock di investimento diretto
- inward_stock_unctad: valore del debito di stock di investimento diretto in milioni di USD
- outward_stock_unctad: valore del credito di stock diinvestimento diretto in milioni di USD

Il secondo output ("stock_confronto.csv") contiene le seguenti variabili:
- origin: paese dove risiede l'investitore diretto (DI) espresso in ISO3c
- destination: paese dove risiede l'impresa di investimento diretto (DIENT) espresso in ISO3c
- year: anno in cui viene dichiarato lo stock di investimento diretto
- outward_cdis: valore dello stock di investimento diretto in milioni di USD dichiarato da DI
- outward_derived_cdis: valore dello stock di investimento diretto in milioni di USD dichiarato da DIENT

# UNWTO

Fonte: UNWTO - Tourism Statistics Database

Il dataset UNWTO è composto da più dataset che riportano, per ciascun paese preso in considerazione, il numero di turisti/visitatori che partono da quello stesso paese e raggiungono ciascuno dei paesi del dataset, per ogni anno. I turisti, dal paese di destinazione, possono essere classificati nei seguenti modi:
- TFN: Arrivi di turisti non residenti alle frontiere nazionali, registrati per nazionalità.
- TFR: Arrivi di turisti non residenti alle frontiere nazionali, registrati per Paese di residenza
- VFN: Arrivi di visitatori non residenti alle frontiere nazionali, registrati per nazionalità
- VFR: Arrivi di visitatori non residenti alle frontiere nazionali, registrati per Paese di residenza
- THSN: Arrivi di turisti non residenti in alberghi e strutture simili, registrati per nazionalità
- THSR: Arrivi di turisti non residenti in alberghi e strutture simili, registrati per paese di residenza.
- TCEN: Arrivi di turisti non residenti in tutti i tipi di strutture ricettive, registrati per nazionalità
- TCER: Arrivi di turisti non residenti in tutti i tipi di esercizi ricettivi, registrati per paese di residenza.

Alcuni paesi registrano le persone in entrata con solo una di queste classificazioni, altri con più di una. Il periodo considerato va dal 1995 al 2020. 

Il codice contenuto in "unwto.ipynb" crea un output contenente le seguenti variabili:
- origin: paese di partenza espresso in ISO3c
- destination: paese di arrivo espresso in ISO3c
- year: anno in cui viene registrato l'ingresso di turisti
- value_tfn: numero di arrivi di turisti non residenti alla frontiere nazionali, registrati per nazionalità
- value_tfr: numero di arrivi di turisti non residenti alle frontiere nazionali, registrati per paese di residenza
- value_vfn: numero di arrivi di visitatori non residenti alle frontiere nazionali, registrati per nazionalità
- value_vfr: numero di arrivi di visitatori non residenti alle frontiere nazionali, registrati per paese di residenza
- value_thsn: numero di arrivi di turisti non residenti in alberghi e strutture simili, registrati per nazionalità
- value_thsr: numero di arrivi di turisti non residenti in alberghi e strutture simili, registrati per paese di residenza
- value_tcen: numero di arrivi di turisti non residenti in tutti i tipi di strutture ricettive, registrati per nazionalità
- value_tcer: numero di arrivi di turisti non residenti in tutti i tipi di esercizi ricettivi, registrati per paese di residenza


# INPACT

Fonte: Jesse LaBelle & Immaculada Martinez-Zarzoso & Ana Maria Santacreu & Yoto Yotov, 2023. "Cross-border Patenting, Globalization, and Development," Working Papers 2023-031, Federal Reserve Bank of St. Louis, revised Jan 2024.

Il dataset INPACT riporta, per ogni anno, una misura del numero di brevetti rilasciati dal paese dove risiede l'inventore al paese dove risiede la "autorità dei brevetti" che richiede il rilascio del brevetto.  Vengono riportati i paesi con il codice identificativo ISO2c e ISO3c e viene riportato anche il settore industriale che impatta quella particolare tecnologia brevettata. Il valore del numero di brevetti non è un intero perchè al conteggio dei brevetti viene attribuito un peso  a seconda di quanti paesi hanno rilasciato quello stesso brevetto, a seconda di quanti e quali paesi fanno riferimento all'autorità dei brevetti che richiede il rilascio, a seconda di quanti ambiti industriali quella nuova tecnologia va ad influenzare. Il periodo considerato va dal 1974 al 2020. 

Il codice contenuto in "inpact.ipynb" crea un output con le seguenti variabili:
- origin: paese in cui risiede l'inventore espresso in ISO3c
- destination: paese in cui risiedere l'autorità dei brevetti che richiede il rilascio espresso in ISO3c
- year: anno in cui viene registrato il rilascio del brevetto
- patents: valore pesato del numero di brevetti rilasciati

# MPI

Fonte: Akbaritabar, A., Theile, T., Zagheni, E., "Global flows and rates of internationalmigration of scholars", MPIDR Working Paper WP-2023-018, 13 pages, Rostock, Max Planck Institute for Demographic Research (April 2023).

Il dataset MPI riporta, per ogni anno, il numero di migrazioni di persone altamente qualificate da un paese a un altro basandosi sulle pubblicazioni di articoli scientifichi, attraverso i dataset bibliometrici su larga scala di Scopus. Il periodo considerato va dal 1997 al 2020. 

Il codice contenuto in "mpi.ipynb" crea un output con le seguenti variabili:
- origin: paese di provenienza della persona altamente qualificata in ISO3c 
- destination: paese di arrivo della persona altamente qualificata in ISO3c 
- year: anno in cui viene registrata la migrazione
- patents: numero delle migrazioni di persone altamente qualificate avvenute basate sull'osservazioni dei dati bibliometrici di Scopus




