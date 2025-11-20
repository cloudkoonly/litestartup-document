# Einführung in LiteStartup

LiteStartup ist eine intelligente E-Mail-Marketing-Plattform, die speziell für Startups entwickelt wurde. Sie kombiniert die Leistung eines geschäftlichen E-Mail-Dienstes (Workmail), KI-gestützte Inhaltserstellung und zuverlässige E-Mail-Zustellung in einer erschwinglichen, benutzerfreundlichen Plattform.

## Was ist LiteStartup?

LiteStartup ist eine SaaS (Software as a Service) E-Mail-Plattform, die Startups hilft:

- **Marketing-E-Mails zu senden** mit integrierter KI-Inhaltsunterstützung
- **Geschäfts-E-Mails zu verwalten** mit Workmail-Funktionalität (wie Gmail)
- **Kampagnen zu automatisieren** mit intelligenten Workflows
- **Abonnentenlisten aufzubauen** mit eingebetteten Anmeldeformularen
- **Wartelisten zu verwalten** vor dem Produktstart
- **Einfach zu integrieren** über REST-API in Minuten

Im Gegensatz zu traditionellen E-Mail-Marketing-Plattformen, die pro Kontakt berechnen, berechnet LiteStartup pro gesendeter E-Mail. Das bedeutet, dass Sie unbegrenzt Kontakte importieren können und nur für die E-Mails bezahlen, die Sie tatsächlich senden.

## Hauptmerkmale

### Workmail wie Gmail
Die einzige E-Mail-Marketing-Plattform mit integrierter geschäftlicher E-Mail. Keine separaten Google Workspace-Abonnements erforderlich. Sparen Sie 72-144 $ pro Jahr pro Teammitglied.

### KI-Inhalts-Assistent
Generieren Sie automatisch Betreffzeilen, E-Mail-Texte und A/B-Testvariationen. Schreiben Sie E-Mails 10-mal schneller mit 10-mal besseren Öffnungsraten. Von der Idee bis zum Versand in nur 1 Minute.

### Erschwingliche Preise
- **Kostenloser Plan**: 10.000 E-Mails pro Monat
- **Pro-Plan**: 110.000 E-Mails pro Monat für 20 $/Monat
- **Pay-as-you-go**: 0,20 $ pro 1.000 E-Mails nach Ihrem Planlimit
- **Keine Gebühren pro Kontakt**: Importieren Sie 100.000 Kontakte, zahlen Sie nur für gesendete E-Mails

### Unbegrenzte Kontakte
Importieren und verwalten Sie unbegrenzt viele Kontakte. Zahlen Sie nur für gesendete E-Mails, nicht für das Speichern von Kontakten. Volles Dateneigentum mit CSV-Import/Export.

### Unternehmensinfrastruktur
Erstellt von AWS- & Google Cloud-Ingenieuren. 99,99 % Verfügbarkeit mit SOC2- & GDPR-Konformität. Startup-Preise mit Zuverlässigkeit auf Unternehmensniveau.

### Intelligente Automatisierung
- **Wartelisten-Management**: E-Mails sammeln, Einladungscodes senden, Warteliste automatisch in Kunden umwandeln
- **Abonnementformulare**: Einbettbare Anmeldeformulare mit Double Opt-in, überall in 30 Sekunden einbetten
- **KI-Automatisierung**: Intelligente Workflows, die durch Benutzerverhalten ausgelöst werden - Willkommensserien, Re-Engagement, Rückgewinnungskampagnen

### Kein Vendor Lock-in
Verwenden Sie Standard-REST-APIs. Wechseln Sie den Anbieter jederzeit ohne Codeänderungen. Funktioniert mit jeder Programmiersprache oder jedem Framework.

## Wer sollte LiteStartup nutzen?

LiteStartup ist ideal für:

- **Startups in der Frühphase**, die ihren ersten Kundenstamm aufbauen
- **SaaS-Unternehmen**, die zuverlässige Transaktions-E-Mails benötigen
- **Wachstumsteams**, die E-Mail-Marketing-Kampagnen durchführen
- **Produktteams**, die Wartelisten und Early Access verwalten
- **Entwickler**, die eine einfache API-Integration ohne Komplexität wünschen
- **Unternehmen**, die nach erschwinglichen E-Mail-Lösungen ohne Vendor Lock-in suchen

## Wie LiteStartup funktioniert

### 1. Registrieren
Erstellen Sie ein kostenloses Konto und legen Sie sofort mit 10.000 kostenlosen E-Mails pro Monat los.

### 2. API-Anmeldeinformationen erhalten
Rufen Sie Ihren API-Schlüssel in Sekundenschnelle über das Dashboard ab.

### 3. Integrieren
Verwenden Sie die einfache REST-API, um E-Mails aus Ihrer Anwendung zu senden. Funktioniert mit jeder Programmiersprache.

### 4. E-Mails senden
Beginnen Sie mit dem Senden von Transaktions-E-Mails, Marketingkampagnen oder automatisierten Workflows.

### 5. Verfolgen & Optimieren
Überwachen Sie Zustellung, Öffnungen, Klicks und nutzen Sie KI-Vorschläge, um die Leistung zu verbessern.

## LiteStartup vs. Traditionelle E-Mail-Plattformen

| Funktion | LiteStartup | Traditionelle Plattformen |
|---------|-------------|----------------------|
| Workmail (Geschäfts-E-Mail) | ✓ Inklusive | ✗ Separater Dienst |
| KI-Inhalts-Assistent | ✓ Ja | ✗ Nein |
| Preismodell | Pro gesendeter E-Mail | Pro Kontakt |
| Einrichtungszeit | 5 Minuten | 30+ Minuten |
| API-Integration | ✓ Einfache REST-API | ✓ Komplexe SDKs |
| Vendor Lock-in | ✗ Keiner | ✓ Ja |
| Kostenlose Stufe | 10K E-Mails/Monat | Begrenzt |
| Verfügbarkeit SLA | 99,99% | 99,9% |

## Erste Schritte

Bereit, E-Mails zu senden? Hier ist, was als nächstes zu tun ist:

1. **[Leitfaden für erste Schritte](01-getting-started.md)** - Registrieren Sie sich und senden Sie Ihre erste E-Mail in 5 Minuten
2. **[API-Referenz](02-api-reference.md)** - Vollständige API-Dokumentation und Endpunkte
3. **[Funktionsübersicht](03-features.md)** - Erkunden Sie alle Funktionen im Detail
4. **[Code-Beispiele](04-examples.md)** - Implementierungsbeispiele in mehreren Sprachen
5. **[Preise & Pläne](05-pricing.md)** - Verstehen Sie Preise und Abrechnung

## Schnellstart-Beispiel

Senden Sie Ihre erste E-Mail mit nur wenigen Zeilen Code:

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

## Hauptvorteile

✓ **Geld sparen** - Zahlen Sie nur für gesendete E-Mails, nicht pro Kontakt
✓ **Zeit sparen** - KI generiert Inhalte, Einrichtung dauert 5 Minuten
✓ **Zuverlässigkeit für Unternehmen** - 99,99% Verfügbarkeit, SOC2- & GDPR-konform
✓ **Kein Lock-in** - Standard-REST-API, jederzeit wechseln
✓ **Für Startups gebaut** - Erschwingliche Preise, startup-freundliche Funktionen
✓ **Einfache Integration** - Funktioniert mit jeder Sprache oder jedem Framework

## Support & Ressourcen

- **Dokumentation**: Vollständige Anleitungen und API-Referenz
- **Code-Beispiele**: Gebrauchsfertige Beispiele in mehreren Sprachen
- **API-Status**: Echtzeit-Status unserer Infrastruktur
- **Community**: Vernetzen Sie sich mit anderen LiteStartup-Benutzern

## Nächste Schritte

- Beginnen Sie mit dem [Leitfaden für erste Schritte](01-getting-started.md)
- Erkunden Sie die [API-Referenz](02-api-reference.md)
- Sehen Sie sich [Code-Beispiele](04-examples.md) für Ihre Programmiersprache an
- Prüfen Sie [Preise & Pläne](05-pricing.md), um den richtigen Plan zu finden

---

**Bereit, Ihre erste E-Mail zu senden?** Beginnen Sie mit dem [Leitfaden für erste Schritte](01-getting-started.md)!
