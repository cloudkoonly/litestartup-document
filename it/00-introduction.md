# Introduzione a LiteStartup
 
 LiteStartup (posizionato sul sito come *Lite Email for Startups*) è una **piattaforma di servizi e-mail basata sull’IA** per startup che unisce **Workmail (e-mail aziendale)**, **e-mail transazionali** ed **e-mail marketing** in un unico prodotto, con una semplice API REST da integrare in pochi minuti.
 
 ## Che cos’è LiteStartup?
 
 LiteStartup è una piattaforma SaaS di e-mail per startup. In una frase:
 
 - **Un modello di servizio e-mail guidato dall’IA** che semplifica il tuo flusso di lavoro e-mail (contenuti, automazione e consegna)
 - **Uno stack unificato per e-mail aziendali + e-mail transazionali + e-mail marketing**, riducendo la frammentazione dei fornitori
 - **Un’integrazione a misura di sviluppatore** tramite API REST standard (senza SDK complessi)
 
 A differenza delle piattaforme tradizionali di e-mail marketing che fanno pagare per contatto, LiteStartup mette al centro il modello **pay per email sent**: paghi per ciò che invii, non per l’archiviazione dei contatti.
 
 ## Cosa ci rende diversi
 
 ### Workmail come Gmail
 L’UNICA piattaforma di e-mail marketing che ti permette di avere in pochi minuti un’e-mail aziendale come `support@yourcompany.com`.
 
 ### AI Content Assistant
 L’IA genera e-mail marketing e varianti per test A/B per accelerare scrittura e iterazione.
 
 ### Conveniente
 Paghi per e-mail inviata, non per contatto.
 
 - **Pro**: $20/month per 110,000 emails/month
 - **Overage**: $0.20 per 1,000 emails dopo il limite
 
 ### Infrastruttura enterprise
 Costruito da ingegneri AWS e Google Cloud. 99,9% di uptime con conformità SOC2 e GDPR.
 
 ### Notifiche e-mail gratuite
 Ottieni un’e-mail gratuita come `yourname@litestartup.net` per avvisi, report e aggiornamenti nella casella di posta che preferisci.
 
 ### AI Website Builder
 Chatta con l’IA per creare landing page, pagine lista d’attesa, newsletter e blog. Nessun codice necessario.
 
 ### Ticket + Live Chat
 Gestisci le conversazioni con i clienti tramite ticket (via e-mail) e un widget di live chat in tempo reale.
 
 ### AI Automation
 Automazione sempre attiva: e-mail di benvenuto, follow-up e outreach, con acquisizione lead integrata e workflow di crescita.
 
 ## Per chi è LiteStartup?
 
 LiteStartup è ideale per:
 
 - **Startup early-stage** che stanno costruendo la prima base clienti
 - **Prodotti SaaS** che vogliono e-mail transazionali + marketing nello stesso posto
 - **Team growth** che desiderano contenuti assistiti dall’IA ed esperimenti più rapidi
 - **Team prodotto** che gestiscono landing page e liste d’attesa
 - **Sviluppatori** che preferiscono API REST semplici con poche dipendenze
 - **Team che evitano il vendor lock-in** e vogliono la possibilità di cambiare provider in futuro
 
 ## Come funziona LiteStartup
 
 ### 1. Registrazione
 Crea un account e inizia con il piano Free (10,000 emails/month).
 
 ### 2. Ottenere le credenziali API
 Recupera la tua API key dalla dashboard.
 
 ### 3. Integrazione
 Invia e-mail tramite chiamate API REST. Funziona con qualsiasi linguaggio o framework.
 
 ### 4. Invio e-mail
 Invia e-mail transazionali, campagne marketing o workflow automatizzati.
 
 ### 5. Monitoraggio e ottimizzazione
 Monitora le analytics di base e migliora iterando con l’aiuto dell’IA.
 
 ## LiteStartup vs. piattaforme e-mail tradizionali
 
 | Funzionalità | LiteStartup | Piattaforme tradizionali |
 |---|---|---|
 | Workmail (Business Email) | ✓ Incluso | ✗ Servizio separato |
 | AI Content Assistant | ✓ Sì | ✗ No |
 | Modello di prezzo | Per e-mail inviata | Per contatto |
 | Tempo di setup | 5 minuti | 30+ minuti |
 | Integrazione API | ✓ API REST semplice | ✓ SDK complessi |
 | Vendor lock-in | ✗ Nessuno | ✓ Sì |
 | Piano gratuito | 10K emails/month | Limitato |
 | Uptime (website) | 99.9% | 99.9% |
 
 ## Per iniziare
 
 Pronto a iniziare a inviare e-mail? Ecco cosa fare:
 
 1. **[Getting Started Guide](/it/01-getting-started.md)** - Registrati e invia la tua prima e-mail in pochi minuti
 2. **[API Reference](/it/02-api-reference.md)** - Documentazione API completa ed endpoint
 3. **[Features Guide](/it/03-features.md)** - Esplora tutte le funzionalità nel dettaglio
 4. **[Code Examples](/it/04-examples.md)** - Esempi di implementazione in più linguaggi
 5. **[Pricing & Plans](/it/05-pricing.md)** - Comprendere tariffe e fatturazione
 
 ## Esempio di Quick Start
 
 Invia la tua prima e-mail in poche righe di codice:

 ```bash
 curl -X POST https://api.litestartup.com/client/v2/emails \
   -H "Authorization: Bearer YOUR_API_KEY" \
   -H "Content-Type: application/json" \
   -d '{
     "to": "user@example.com",
     "from": "noreply@yourapp.com",
     "subject": "Welcome!",
     "html": "<h1>Hello</h1>"
   }'
 ```

 ## Vantaggi principali
 
 - **Costo inferiore** - Paghi per e-mail inviata, non per contatto
 - **Maggiore produttività** - AI content assistance e AI automation riducono il lavoro manuale
 - **Toolkit all-in-one** - Workmail + invio + landing page/liste d’attesa + ticket/live chat
 - **Integrazione rapida** - API REST senza dipendenze da SDK complessi
 - **Meno lock-in** - API standard rendono più semplice cambiare provider

 ## Supporto e risorse
 
 - **Documentazione**: guide complete e riferimento API
 - **Esempi di codice**: esempi pronti all’uso in più linguaggi
 - **Community**: entra in contatto con altri utenti LiteStartup

 ## Prossimi passi

 - Inizia con il [Getting Started Guide](/it/01-getting-started.md)
 - Esplora l’[API Reference](/it/02-api-reference.md)
 - Consulta i [Code Examples](/it/04-examples.md) per il tuo linguaggio
 - Dai un’occhiata a [Pricing & Plans](/it/05-pricing.md) per trovare il piano giusto

---
 
 **Pronto a inviare la tua prima e-mail?** Inizia con il [Getting Started Guide](/it/01-getting-started.md).
