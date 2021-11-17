# Linee guida per l’annotazione dei dialoghi


## Dialogue act

Dialogue act con prefisso sys-. Questo tipo di annotazioni descrive lo scopo che vuole raggiungere il sistema tramite una determinata frase. In particolare, lo scopo della frase espressa dal sistema può essere quello di:


### Sys-greet: usata per annotare le frasi in cui il sistema saluta l’utente
es. “Buongiorno”, “ti saluto”, “ti auguro una buona giornata”, “in bocca al lupo”


### Sys-inform-basic: fornire informazioni all’utente a seguito di una richiesta specifica 
es.  usr: “ Hai informazioni riguardo al tipo di contratto?”
sys: “si tratta di un tirocinio post-laurea”
es. usr: “Posso provare a contattare l’azienda?”
sys: “ Puoi contattarli direttamente via e-mail al seguente indirizzo info@azienda.com”


### Sys-inform-proactive: usato per fornire informazioni all’utente anche se non esplicitamente richieste
es. usr: "Sono abbastanza convinta che il mio bagaglio di competenze sia sufficiente per attirare la loro attenzione."
sys: “  "Bene, l'azienda in questione e' MANPOWER. Puoi contattare l'azienda direttamente a questo indirizzo: info@azienda.com.”
In questo caso il nome dell’azienda e il suo indirizzo email non sono stati esplicitamente richiesti dall’utente ma il sistema ha ritenuto importante fornire informazioni aggiuntive prima di proseguire con la conversazione

NOTA BENE: gli acts inform_basic e inform_proactive non sono mutualmente esclusivi. Se in una frase il parlante, oltre a rispondere direttamente alla domanda dell’interlocutore fornisce informazioni aggiuntive, la frase verrà annotata con entrambi gli acts. Esempio:

usr: “puoi dirmi dove si trova l’azienda?”
sys: “Certo, l’azienda si trova a Milano. Se vuoi li puoi contattare direttamente all’indirizzo info@azienda.com”

In questo caso sys fornisce sia un’informazione direttamente richiesta dall’utente (“l’azienda si trova a Milano”) sia un’informazione aggiuntiva (l’indirizzo email dell’azienda).

### Sys-request: richiedere informazioni all’utente 
es. “In che settore vorresti lavorare?”, “Saresti disposto a trasferirti all’estero?” etc

Per request, una volta indicato lo slot che si vuole riempire gli si associa come valore il punto interrogativo. Ad es. in “saresti disposto a trasferirti all’estero” verrà spuntata la casella slot “location” inserendo come valore “?” (selezionandolo direttamente dalla frase, similmente alla selezione dei valori per gli altri slot- vedi sezione sugli slot).
Qualora non sia possibile inserire il “?” perché non presente nella frase (es. :”Parlami di più delle tue esperienze lavorative”) il valore “?” si può inserire manualmente nella casella che corrisponde allo slot da selezionare.

### Sys-select: usato quando il sistema seleziona l’offerta lavorativa che ritiene più adatta al profilo dell’utente:
es :sys” Ok ho trovato un'offerta che risponde ai tuoi interessi: si tratta di uno stage post-laurea nel settore alimentari.”

### Sys-deny: utilizzato quando il sistema non è in grado di trovare un annuncio adatto alla richiesta o non è in grado di soddisfare una richiesta
es. “al momento non ho nessuna offerta lavorativa adatta a te”

IMPORTANTE: sia per select che per deny, qualora non sia possibile individuare nella frase del sistema il valore dello slot, è possibile andare a recuperare il valore nella frase precedente dell’altro parlante. Esempio:

usr: “Hai qualche offerta di lavoro a Lucca?”
sys: “No, mi dispiace, al momento non ne abbiamo”.

In questo caso il sys_deny sarà associato allo slot (vedi sotto) location. Il valore di location andrà recuperato nella frase precedente però, evidenziando “Lucca”.


Dialogue act con prefisso usr-: questo tipo di annotazioni descrive lo scopo che vuole raggiungere l’utente tramite una determinata frase. In particolare, lo scopo della frase può essere quello di:

### Usr-greet: usata per annotare le frasi in cui l’utente saluta il sistema
es. “Buongiorno”, “ti saluto”, “grazie e a presto”

### Usr-inform-basic: fornire informazioni al sistema a seguito di una richiesta specifica 
es.  sys: “ Raccontami un po' di te: che percorso di studi hai fatto?”
usr: “Mi sono diplomata presso il liceo classico e poi ho conseguito una laurea in infermieristica”
es. sys: “ Hai già avuto esperienze lavorative?
usr: “ Ho lavorato per un anno in un ospedale a Roma, in un reparto di pediatria, e ho fatto esperienze come volontaria con minori.”

### Usr-inform-proactive: usato per fornire informazioni al sistema anche se non strettamente richieste
es.  "sys": "Questo significa che abilità di comunicazione sono essenziali in questo lavoro",
 "usr”: "Non sono un abile comunicatore ma ho buone capacità di problem solving"
“usr”: “Fra le altre competenze conosco bene l'inglese e sto studiando il cinese”

In questo caso l’utente fornisce al sistema informazioni circa la sua conoscenza delle lingue straniere, ritenendo tale informazione utile anche se non risponde a una domanda specifica del sistema.

### Usr-request: richiedere informazioni al sistema:
es. “Posso provare a contattare l’azienda?”, “Puoi darmi maggiori informazioni in merito?”

Per request, una volta indicato lo slot che si vuole riempire gli si associa come valore il punto interrogativo. Ad es. in “saresti disposto a trasferirti all’estero” verrà spuntata la casella slot “location” inserendo come valore “?” (selezionandolo direttamente dalla frase, similmente alla selezione dei valori per gli altri slot- vedi sezione sugli slot).

### Usr-select: usato quando l’utente accetta l’offerta lavorativa che ritiene più adatta al profilo dell’utente:
es :”Mi piace davvero tanto, è proprio quello che fa per me!.”, 
“mi sembra perfetto, ti ringrazio!”

### Usr-deny: utilizzato quando l’utente non accetta l’offerta proposta o non è in grado di soddisfare un requisito
es. “Purtroppo non mi trovo in molti dei requisiti.”

IMPORTANTE: sia per select che per deny, qualora non sia possibile individuare nella frase del sistema il valore dello slot, è possibile andare a recuperare il valore nella frase precedente dell’altro parlante. Esempio:

sys: “Conosci l’inglese?”
usr: “No, mi dispiace”.

In questo caso usr_deny sarà associato allo slot (vedi sotto) languages. Il valore di languages andrà recuperato nella frase precedente però, evidenziando “inglese”.

IMPORTANTE: a tutti gli intent devono essere associati uno o più slot (vedi sotto) a esso relativi. Ad esempio: 

“In che settore vorresti lavorare?” -> sys_request + slot area + valore dello slot: ?
“Ho lavorato per un anno in un ospedale a Roma” -> usr_inform_basic + slot past_experience + valore dello slot: in un ospedale

## Gli slot

Distinguiamo gli slot in generali e in slot che costituiscono gli attributi dell'entità job-offer.

### Slot generali

### Global slot: questo tipo di annotazione  permette di marcare l’intero dialogo invece del singolo turno e serve per annotare se il sistema ha trovato o meno un’offerta lavorativa adatta all’utente. 
I valori che può assumere sono: a) positive:stringa da inserire se l’utente, alla fine del dialogo, è soddisfatto dell’offerta di lavoro proposta dal sistema.
b) negative: stringa da inserire se l’utente NON è soddisfatto dell’offerta di lavoro proposta. 

Ogni dialogo deve essere necessariamente marcato come positive o negative.

### Async: turn_ref: da usare qualora ci sia una sovrapposizione di domanda/risposta tra utente/sistema. Ad esempio:

"turn_id": 10,
 "sys": "Posso però dirti che cercano persone che si occupino sia di gestire la comunicazione pubblicitaria del cliente attraverso il web, che persone capaci di interagire direttamente con la clientela. Viene anche chiesto di reclutare nuovi clienti per Pubblidea srl.",
            "usr": "Quanto tempo dura il periodo di formazione?"
     
            "turn_id": 11,
            "sys": "Questo significa che abilità di comunicazione sono essenziali in questo lavoro",
            "usr": " "
      
            "turn_id": 12,
            "sys": "L'annuncio non fornisce informazioni circa la durata del contratto, mi dispiace",
            "usr": " "
      
In questo caso, nel turno 11, il sistema non ha risposto immediatamente alla domanda dell’utente formulata nel turno 10, ma ha continuato il discorso del turno precedente. La risposta alla domanda “Quanto tempo dura il periodo di formazione?” viene fornita nel turno 12. In questo caso, il turno 12 sarà annotato come async e, nel box sottostante,  verrà inserito il turno a cui la risposta fa riferimento (nel caso dell’esempio: turn_10)

### Slot relativi all’entità job-offer

Gli slot rappresentano le informazioni che vogliamo estrarre dalla frase, relativamente al dominio delle offerte di lavoro.

Esempio:
FRASE: usr: “mi sono appena laureata in infermieristica”
ENTITY: job offer
DIALOGUE ACT: sys-inform-basic
In questo caso l’informazione che ci interessa estrarre dalla frase è relativa al titolo di studio del parlante (degree). Andremo quindi a selezionare lo slot degree e, nella casella di testo sottostante, a inserire il valore “infermieristica”


IMPORTANTE: come valore degli slot selezionare il minor numero di parole possibili. E’ possibile tuttavia selezionare separatamente più elementi per la stessa frase.
Esempio:
sys: “Ok ho trovato un'offerta che risponde ai tuoi interessi: si tratta di uno stage post-laurea nel settore alimentari. Cercano una figura che si occupi della pianificazione del budget e del rendiconto economico, oltre a garantire la sicurezza sul lavoro e quella alimentare.”

dialogue act: sys-select
slot: contract: stage post-laurea
slot: area: settore alimentari
slot: duties: pianificazione del budget 
slot: duties:rendiconto economico 
slot: duties:sicurezza sul lavoro e quella alimentare

Gli slot possibili sono:

### job_description: descrizione del lavoro che viene offerto. Es. 
sys= “ Dalla ricerca, è emersa un'offerta di lavoro come infermiere in soggiorni vacanza per minori”
La frase sarà annotata con 
dialogue act:  sys-select,
slot: job description: infermiere

### contract: il tipo di contratto lavorativo offerto/richiesto: tempo determinato, part time, etc

### duties: principali mansioni che l’utente dovrà svolgere se verrà selezionato per quel lavoro. Es.
sys: “Ok ho trovato un'offerta che risponde ai tuoi interessi: si tratta di uno stage post-laurea nel settore alimentari. Cercano una figura che si occupi della pianificazione del budget e del rendiconto economico, oltre a garantire la sicurezza sul lavoro e quella alimentare.”
dialogue act: sys-select
slot: contract: stage post-laurea
slot: area: settore alimentari
slot: duties: pianificazione del budget 
slot: duties:rendiconto economico 
slot: duties:sicurezza sul lavoro e quella alimentare

### skills: che tipo di competenze sono richieste per il lavoro o, più in generale, le competenze che l’utente possiede (incluse le soft skill). Es.
usr: “ Lavoro bene in team e col pacchetto Office non ho problemi”
dialogue act: usr-inform-basic
slot: skills:  Lavoro bene in team 
slot:skills: pacchetto Office 

### past_experience: esperienze lavorative pregresse dell’utente 
Es. usr: “ ho lavorato per un anno presso un ospedale a Roma, nel reparto di pediatria”
dialogue act: usr-inform-basic
slot: past_experience: ospedale 

### degree: laurea o altro titolo di studio. Si può annotare come degree sia la facoltà/scuola/corso seguito che il titolo di studio (es. laurea triennale, master, etc)
Es usr: “mi sono laureata in infermieristica”.
dialogue act: usr-inform-basic
slot: degree: infermieristica

### age: informazioni relative all’età dell’utente o della figura professionale ricercata
Es. sys: “cercano un giovane neolaureato”
slot: degree: neolaureato
slot: age: giovane

### languages: conoscenza di lingue straniere richieste per il lavoro o parlate dall’utente. Es.
usr: “conosco inglese e tedesco, entrambe a livello B1”
dialogue act: usr-inform-basic
slot:languages: inglese 
slot:languages: tedesco

eventualmente è possibile annotare con un altro slot languages anche “B1”

### area: settore disciplinare entro cui si colloca la posizione lavorativa:
Es. usr: “ Mi piacerebbe lavorare nel mondo della pubblicità e della comunicazione”
dialogue act: usr-inform-basic
slot: area: pubblicità 
slot: area: comunicazione

### company_name: nome dell’azienda che offre la posizione lavorativa

### company_size: dimensioni dell’azienda (es. piccola, media, grande, meno di 200 impiegati, più di 50 etc)

### location: in che località si trova il lavoro (Italia, estero, nome regione o città). Es.
sys: “Compass Group Italia S.p.A, è una  grande azienda con base a Milano”
dialogue act: sys-inform-basic
slot: company name: Compass Group Italia S.p.A.
slot: company size: grande azienda
slot: location: Milano

### contact: informazioni di contatto dell’azienda (email, numero di telefono etc.) Es.
sys: “Puoi contattare l’azienda al seguente indirizzo e-mail: info@azienda.com”
dialogue act: sys-inform-basic
slot: company contact: info@azienda.com

### other: per annotare tutte quelle informazioni non richieste o al momento non utilizzabili dal sistema ma comunque legate al dominio delle job offer

Ogni frase può essere annotata con più dialogue act e/o più slot.
Es. usr: “mi sono laureato in filosofia, e cerco un lavoro come insegnante”
Dialogue act:
 usr-inform + usr-request
Slot:
 degree:  filosofia
 job_description: insegnante
 
Oppure, nel turno descritto di seguito, la frase del sistema sarà così annotata:
 
"usr": "Sì, potrei essere interessata ma al momento ho bisogno di un lavoro retribuito. Offrono qualche tipo di remunerazione per il tirocinio?"
"sys": "Non viene fornita nessuna informazione esplicita. Dovresti contattare direttamente l'azienda. Si tratta di QUANTA.  L'indirizzo per contattarli e': info@azienda.com" 
Dialogue act:
 sys-deny + sys- inform-proactive
Slot:
 company_name: QUANTA
 contact: info@azienda.com
 
NOTA BENE: non tutti gli slot sono disponibili per tutti gli act.
IMPORTANTE: Tutti i turni semanticamente informativi del dialogo devono essere annotati. I turni che non veicolano informazioni (vedi esempi sotto) possono non essere annotati:
sys: "Ho due opportunità per cui il tuo profilo potrebbe essere interessante",
oppure usr: “spero non sia un problema”.
      


