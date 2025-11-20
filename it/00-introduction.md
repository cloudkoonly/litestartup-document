# Introduzione a LiteStartup

LiteStartup è una piattaforma di email marketing intelligente creata specificamente per le startup. Combina la potenza di un servizio di email aziendale (workmail), la generazione di contenuti basata sull'intelligenza artificiale e l'affidabilità nella consegna delle email in un'unica piattaforma conveniente e facile da usare.

## Cos'è LiteStartup?

LiteStartup è una piattaforma email SaaS (Software as a Service) che aiuta le startup a:

- **Inviare email di marketing** con assistenza ai contenuti AI integrata
- **Gestire le email aziendali** con funzionalità di workmail (come Gmail)
- **Automatizzare le campagne** con flussi di lavoro intelligenti
- **Creare liste di iscritti** con moduli di iscrizione incorporati
- **Gestire liste d'attesa** prima del lancio del prodotto
- **Integrare facilmente** tramite API REST in pochi minuti

A differenza delle tradizionali piattaforme di email marketing che addebitano per contatto, LiteStartup addebita per email inviata. Ciò significa che puoi importare contatti illimitati e pagare solo per le email che invii effettivamente.

## Caratteristiche Principali

### Workmail come Gmail
L'unica piattaforma di email marketing con email aziendale integrata. Nessuna necessità di abbonamenti separati a Google Workspace. Risparmia $72-144 all'anno per membro del team.

### Assistente Contenuti AI
Genera automaticamente oggetti, testi delle email e variazioni per test A/B. Scrivi email 10 volte più velocemente con tassi di apertura 10 volte migliori. Dall'idea all'invio in solo 1 minuto.

### Prezzi Convenienti
- **Piano Gratuito**: 10.000 email al mese
- **Piano Pro**: 110.000 email al mese per $20/mese
- **Pay-as-you-go**: $0,20 per 1.000 email dopo il limite del tuo piano
- **Nessuna tariffa per contatto**: Importa 100.000 contatti, paga solo per le email inviate

### Contatti Illimitati
Importa e gestisci contatti illimitati. Paga solo per le email inviate, non per l'archiviazione dei contatti. Piena proprietà dei dati con import/export CSV.

### Infrastruttura Aziendale
Costruito da ingegneri AWS e Google Cloud. Uptime del 99,99% con conformità SOC2 e GDPR. Prezzi da startup con affidabilità di livello aziendale.

### Automazione Intelligente
- **Gestione Liste d'Attesa**: Raccogli email, invia codici invito, converti automaticamente la lista d'attesa in clienti
- **Moduli di Iscrizione**: Moduli di iscrizione incorporabili con double opt-in, incorporali ovunque in 30 secondi
- **Automazione AI**: Flussi di lavoro intelligenti attivati dal comportamento dell'utente - serie di benvenuto, riattivazione, campagne di recupero

### Nessun Vendor Lock-in
Usa API REST standard. Cambia fornitore in qualsiasi momento senza modifiche al codice. Funziona con qualsiasi linguaggio di programmazione o framework.

## Chi dovrebbe usare LiteStartup?

LiteStartup è ideale per:

- **Startup in fase iniziale** che costruiscono la loro prima base clienti
- **Aziende SaaS** che necessitano di email transazionali affidabili
- **Team di crescita** che eseguono campagne di email marketing
- **Team di prodotto** che gestiscono liste d'attesa e accesso anticipato
- **Sviluppatori** che desiderano una semplice integrazione API senza complessità
- **Aziende** in cerca di soluzioni email convenienti senza vendor lock-in

## Come funziona LiteStartup

### 1. Iscriviti
Crea un account gratuito e inizia subito con 10.000 email gratuite al mese.

### 2. Ottieni Credenziali API
Recupera la tua chiave API dalla dashboard in pochi secondi.

### 3. Integra
Usa la semplice API REST per inviare email dalla tua applicazione. Funziona con qualsiasi linguaggio di programmazione.

### 4. Invia Email
Inizia a inviare email transazionali, campagne di marketing o flussi di lavoro automatizzati.

### 5. Monitora e Ottimizza
Monitora la consegna, le aperture, i clic e usa i suggerimenti dell'IA per migliorare le prestazioni.

## LiteStartup vs. Piattaforme Email Tradizionali

| Caratteristica | LiteStartup | Piattaforme Tradizionali |
|---------|-------------|----------------------|
| Workmail (Email Aziendale) | ✓ Incluso | ✗ Servizio separato |
| Assistente Contenuti AI | ✓ Sì | ✗ No |
| Modello di Prezzo | Per email inviata | Per contatto |
| Tempo di Configurazione | 5 minuti | 30+ minuti |
| Integrazione API | ✓ API REST Semplice | ✓ SDK Complessi |
| Vendor Lock-in | ✗ Nessuno | ✓ Sì |
| Livello Gratuito | 10K email/mese | Limitato |
| SLA Uptime | 99,99% | 99,9% |

## Per Iniziare

Pronto per iniziare a inviare email? Ecco cosa fare dopo:

1. **[Guida Introduttiva](01-getting-started.md)** - Iscriviti e invia la tua prima email in 5 minuti
2. **[Riferimento API](02-api-reference.md)** - Documentazione API completa ed endpoint
3. **[Guida alle Funzionalità](03-features.md)** - Esplora tutte le funzionalità in dettaglio
4. **[Esempi di Codice](04-examples.md)** - Esempi di implementazione in più linguaggi
5. **[Prezzi e Piani](05-pricing.md)** - Comprendi i prezzi e la fatturazione

## Esempio Rapido

Invia la tua prima email in poche righe di codice:

```bash
curl -X POST https://api.litestartup.com/emails/send \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "to": "user@example.com",
    "from": "hello@yourdomain.com",
    "subject": "Welcome to LiteStartup!",
    "html": "<h1>Hello!</h1><p>Welcome to our platform.</p>",
    "text": "Hello! Welcome to our platform."
  }'
```

## Vantaggi Chiave

✓ **Risparmia Denaro** - Paga solo per le email inviate, non per contatto
✓ **Risparmia Tempo** - L'IA genera contenuti, la configurazione richiede 5 minuti
✓ **Affidabilità Aziendale** - Uptime del 99,99%, conforme a SOC2 e GDPR
✓ **Nessun Lock-in** - API REST standard, cambia in qualsiasi momento
✓ **Creato per Startup** - Prezzi convenienti, funzionalità adatte alle startup
✓ **Integrazione Facile** - Funziona con qualsiasi linguaggio o framework

## Supporto e Risorse

- **Documentazione**: Guide complete e riferimento API
- **Esempi di Codice**: Esempi pronti all'uso in più linguaggi
- **Stato API**: Stato in tempo reale della nostra infrastruttura
- **Community**: Connettiti con altri utenti LiteStartup

## Prossimi Passi

- Inizia con la [Guida Introduttiva](01-getting-started.md)
- Esplora il [Riferimento API](02-api-reference.md)
- Rivedi gli [Esempi di Codice](04-examples.md) per il tuo linguaggio di programmazione
- Controlla [Prezzi e Piani](05-pricing.md) per trovare il piano giusto

---

**Pronto per inviare la tua prima email?** Inizia con la [Guida Introduttiva](01-getting-started.md)!
