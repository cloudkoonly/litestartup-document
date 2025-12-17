# Introduction to LiteStartup
 
 LiteStartup (auf der Website positioniert als *Lite Email for Startups*) ist eine **KI-gestützte E-Mail-Service-Plattform** für Startups, die **Workmail (Business-E-Mail)**, **transaktionale E-Mails** und **Marketing-E-Mails** in einem Produkt vereint – mit einer einfachen REST-API, die sich in wenigen Minuten integrieren lässt.
 
 ## Was ist LiteStartup?
 
 LiteStartup ist eine SaaS-E-Mail-Plattform für Startups. In einem Satz:
 
 - **Ein KI-gestütztes E-Mail-Service-Modell**, das deinen E-Mail-Workflow (Inhalte, Automatisierung und Zustellung) optimiert
 - **Ein einheitlicher Stack für Business-E-Mail + transaktionale E-Mails + Marketing-E-Mails**, der die Anzahl an Anbietern reduziert
 - **Entwicklerfreundliche Integration** über standardisierte RESTful APIs (keine komplexen SDKs)
 
 Im Gegensatz zu klassischen E-Mail-Marketing-Plattformen, die pro Kontakt abrechnen, setzt LiteStartup auf **Bezahlung pro gesendeter E-Mail** – du zahlst also für das, was du sendest, nicht für das Speichern von Kontakten.
 
 ## Was uns unterscheidet
 
 ### Workmail wie bei Gmail
 Die EINZIGE E-Mail-Marketing-Plattform mit Business-E-Mail-Adressen wie `support@yourcompany.com` in wenigen Minuten.
 
 ### KI-Content-Assistent
 KI generiert Marketing-E-Mails und A/B-Test-Varianten, um Schreiben und Iteration zu beschleunigen.
 
 ### Bezahlbar
 Bezahle pro gesendeter E-Mail, nicht pro Kontakt.
 
 - **Pro**: $20/month for 110,000 emails/month
 - **Overage**: $0.20 per 1,000 emails after limit
 
 ### Enterprise-Infrastruktur
 Entwickelt von AWS- und Google-Cloud-Engineers. 99,9% Uptime mit SOC2- und DSGVO-Konformität.
 
 ### Kostenlose E-Mail-Benachrichtigungen
 Erhalte eine kostenlose E-Mail-Adresse wie `yourname@litestartup.net` für Alerts, Reports und Updates in dein bevorzugtes Postfach.
 
 ### KI-Website-Builder
 Chatte mit KI, um Landingpages, Waitlist-Seiten, Newsletter und Blogs zu erstellen. Kein Coding nötig.
 
 ### Ticket + Live-Chat
 Verwalte Kundengespräche mit Tickets (per E-Mail) und einem Echtzeit-Live-Chat-Widget.
 
 ### KI-Automatisierung
 Always-on-Automatisierung: Willkommens-, Follow-up- und Outreach-E-Mails – mit integriertem Lead-Capture und Growth-Workflows.
 
 ## Für wen ist LiteStartup geeignet?
 
 LiteStartup ist ideal für:
 
 - **Startups in der Frühphase**, die ihre erste Kundschaft aufbauen
 - **SaaS-Produkte**, die transaktionale und Marketing-E-Mails an einem Ort brauchen
 - **Growth-Teams**, die KI-unterstützten Content und schnellere Experimente wollen
 - **Produktteams**, die Landingpages und Waitlists verwalten
 - **Entwickler**, die einfache REST-APIs mit minimalen Abhängigkeiten bevorzugen
 - **Teams, die Vendor-Lock-in vermeiden** und später den Anbieter wechseln können möchten
 
 ## So funktioniert LiteStartup
 
 ### 1. Registrieren
 Erstelle ein Konto und starte mit dem Free-Plan (10.000 E-Mails/Monat).
 
 ### 2. API-Zugangsdaten holen
 Rufe deinen API-Key im Dashboard ab.
 
 ### 3. Integrieren
 Sende E-Mails über RESTful API-Calls. Funktioniert mit jeder Sprache und jedem Framework.
 
 ### 4. E-Mails versenden
 Sende transaktionale E-Mails, Marketing-Kampagnen oder automatisierte Workflows.
 
 ### 5. Messen & optimieren
 Behalte grundlegende Analytics im Blick und verbessere iterativ mit KI-Unterstützung.
 
 ## LiteStartup vs. traditionelle E-Mail-Plattformen
 
 | Funktion | LiteStartup | Traditionelle Plattformen |
 |---|---|---|
 | Workmail (Business-E-Mail) | ✓ Inklusive | ✗ Separater Dienst |
 | KI-Content-Assistent | ✓ Ja | ✗ Nein |
 | Preismodell | Pro gesendeter E-Mail | Pro Kontakt |
 | Einrichtungszeit | 5 Minuten | 30+ Minuten |
 | API-Integration | ✓ Einfache REST-API | ✓ Komplexe SDKs |
 | Vendor-Lock-in | ✗ Keiner | ✓ Ja |
 | Kostenloser Plan | 10.000 E-Mails/Monat | Begrenzt |
 | Uptime (Website) | 99,9% | 99,9% |
 
 ## Erste Schritte
 
 Bereit, E-Mails zu versenden? Das sind die nächsten Schritte:
 
 1. **[Getting Started Guide](/de/01-getting-started.md)** - Registriere dich und sende deine erste E-Mail in wenigen Minuten
 2. **[API Reference](/de/02-api-reference.md)** - Vollständige API-Dokumentation und Endpoints
 3. **[Features Guide](/de/03-features.md)** - Alle Features im Detail
 4. **[Code Examples](/de/04-examples.md)** - Implementierungsbeispiele in mehreren Sprachen
 5. **[Pricing & Plans](/de/05-pricing.md)** - Preise und Abrechnung verstehen
 
 ## Quick-Start-Beispiel
 
 Sende deine erste E-Mail mit nur wenigen Zeilen Code:

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

 ## Wichtigste Vorteile
 
 - **Geringere Kosten** - Bezahle pro gesendeter E-Mail, nicht pro Kontakt
 - **Höhere Produktivität** - KI-Content-Unterstützung und KI-Automatisierung reduzieren manuelle Arbeit
 - **All-in-one-Toolkit** - Workmail + Versand + Landingpages/Waitlists + Ticket/Live-Chat
 - **Schnelle Integration** - REST-API ohne komplexe SDK-Abhängigkeiten
 - **Weniger Lock-in** - Standard-APIs erleichtern den späteren Anbieterwechsel
 
 ## Support & Ressourcen
 
 - **Dokumentation**: Vollständige Guides und API-Referenz
 - **Code-Beispiele**: Sofort nutzbare Beispiele in mehreren Sprachen
 - **Community**: Austausch mit anderen LiteStartup-Nutzern
 
 ## Nächste Schritte
 
 - Starte mit dem [Getting Started Guide](/de/01-getting-started.md)
 - Schau dir die [API Reference](/de/02-api-reference.md) an
 - Sieh dir die [Code Examples](/de/04-examples.md) für deine Programmiersprache an
 - Prüfe [Pricing & Plans](/de/05-pricing.md), um den passenden Plan zu finden

---
 
 **Bereit, deine erste E-Mail zu versenden?** Starte mit dem [Getting Started Guide](/de/01-getting-started.md).
