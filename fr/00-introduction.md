# Introduction à LiteStartup
 
 LiteStartup (présenté sur le site comme *Lite Email for Startups*) est une **plateforme de services e-mail pilotée par l’IA** pour les startups, qui réunit **Workmail (e-mail professionnel)**, **e-mails transactionnels** et **e-mails marketing** dans un seul produit, avec une API REST simple à intégrer en quelques minutes.
 
 ## Qu’est-ce que LiteStartup ?
 
 LiteStartup est une plateforme SaaS d’e-mail pour les startups. En une phrase :
 
 - **Un modèle de service e-mail piloté par l’IA** qui simplifie votre workflow e-mail (contenu, automatisation et délivrabilité)
 - **Une pile unifiée e-mail pro + transactionnel + marketing**, pour réduire la multiplication des prestataires
 - **Une intégration pensée pour les développeurs** via des API REST standards (sans SDK complexe)
 
 Contrairement aux plateformes d’e-mail marketing traditionnelles qui facturent au contact, LiteStartup met l’accent sur le **paiement par e-mail envoyé** : vous payez ce que vous envoyez — pas le stockage de contacts.
 
 ## Ce qui nous différencie
 
 ### Workmail comme Gmail
 La SEULE plateforme d’e-mail marketing qui permet de créer en quelques minutes une adresse e-mail professionnelle comme `support@yourcompany.com`.
 
 ### Assistant de contenu IA
 L’IA génère des e-mails marketing et des variantes pour des tests A/B afin d’accélérer la rédaction et l’itération.
 
 ### Abordable
 Paiement par e-mail envoyé, pas par contact.
 
 - **Pro** : 20 $/mois pour 110 000 e-mails/mois
 - **Dépassement** : 0,20 $ par 1 000 e-mails au-delà de la limite
 
 ### Infrastructure de niveau entreprise
 Conçu par des ingénieurs AWS et Google Cloud. 99,9 % de disponibilité, conformité SOC2 et GDPR.
 
 ### Notifications e-mail gratuites
 Obtenez une adresse gratuite comme `yourname@litestartup.net` pour les alertes, rapports et mises à jour dans la boîte de réception de votre choix.
 
 ### Créateur de site Web IA
 Discutez avec l’IA pour créer des landing pages, des pages de liste d’attente, des newsletters et des blogs. Aucun code nécessaire.
 
 ### Tickets + chat en direct
 Gérez les conversations client avec des tickets (via e-mail) et un widget de chat en direct en temps réel.
 
 ### Automatisation IA
 Automatisation toujours active : e-mails de bienvenue, relances et outreach, avec capture de leads intégrée et workflows de croissance.
 
 ## Pour qui est LiteStartup ?
 
 LiteStartup est idéal pour :
 
 - **Les startups en phase early-stage** qui construisent leur première base de clients
 - **Les produits SaaS** qui ont besoin d’e-mails transactionnels + marketing au même endroit
 - **Les équipes growth** qui veulent du contenu assisté par IA et des expérimentations plus rapides
 - **Les équipes produit** qui gèrent landing pages et listes d’attente
 - **Les développeurs** qui préfèrent des API REST simples avec un minimum de dépendances
 - **Les équipes qui évitent le verrouillage fournisseur** et veulent garder l’option de changer plus tard
 
 ## Comment fonctionne LiteStartup
 
 ### 1. Inscription
 Créez un compte et commencez avec le plan Free (10 000 e-mails/mois).
 
 ### 2. Obtenir des identifiants API
 Récupérez votre clé API depuis le tableau de bord.
 
 ### 3. Intégration
 Envoyez des e-mails via des appels d’API REST. Compatible avec n’importe quel langage ou framework.
 
 ### 4. Envoyer des e-mails
 Envoyez des e-mails transactionnels, des campagnes marketing ou des workflows automatisés.
 
 ### 5. Suivre et optimiser
 Suivez des analyses de base et itérez grâce aux améliorations assistées par l’IA.
 
 ## LiteStartup vs. plateformes e-mail traditionnelles
 
 | Fonctionnalité | LiteStartup | Plateformes traditionnelles |
 |---|---|---|
 | Workmail (e-mail professionnel) | ✓ Inclus | ✗ Service séparé |
 | Assistant de contenu IA | ✓ Oui | ✗ Non |
 | Modèle tarifaire | Par e-mail envoyé | Par contact |
 | Temps de mise en place | 5 minutes | 30+ minutes |
 | Intégration API | ✓ API REST simple | ✓ SDK complexes |
 | Verrouillage fournisseur | ✗ Aucun | ✓ Oui |
 | Offre gratuite | 10 000 e-mails/mois | Limitée |
 | Disponibilité (site Web) | 99,9 % | 99,9 % |
 
 ## Bien démarrer
 
 Prêt à envoyer des e-mails ? Voici la suite :
 
 1. **[Guide de démarrage](/fr/01-getting-started.md)** - Inscrivez-vous et envoyez votre premier e-mail en quelques minutes
 2. **[Référence API](/fr/02-api-reference.md)** - Documentation complète de l’API et endpoints
 3. **[Guide des fonctionnalités](/fr/03-features.md)** - Découvrez toutes les fonctionnalités en détail
 4. **[Exemples de code](/fr/04-examples.md)** - Exemples d’implémentation en plusieurs langages
 5. **[Tarifs & offres](/fr/05-pricing.md)** - Comprendre la tarification et la facturation
 
 ## Exemple de démarrage rapide
 
 Envoyez votre premier e-mail en quelques lignes de code :
 
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
 
 ## Principaux avantages
 
 - **Coût plus faible** - Paiement par e-mail envoyé, pas par contact
 - **Productivité plus élevée** - L’assistance IA au contenu et l’automatisation IA réduisent le travail manuel
 - **Boîte à outils tout-en-un** - Workmail + envoi + landing pages/listes d’attente + tickets/chat
 - **Intégration rapide** - API REST sans dépendances SDK complexes
 - **Moins de verrouillage** - Des API standards facilitent le changement de prestataire
 
 ## Support & ressources
 
 - **Documentation** : Guides complets et référence API
 - **Exemples de code** : Exemples prêts à l’emploi en plusieurs langages
 - **Communauté** : Échangez avec d’autres utilisateurs de LiteStartup
 
 ## Prochaines étapes
 
 - Commencez avec le [Guide de démarrage](/fr/01-getting-started.md)
 - Explorez la [Référence API](/fr/02-api-reference.md)
 - Consultez les [Exemples de code](/fr/04-examples.md) pour votre langage
 - Vérifiez [Tarifs & offres](/fr/05-pricing.md) pour trouver le plan adapté
 
---
 
 **Prêt à envoyer votre premier e-mail ?** Commencez avec le [Guide de démarrage](/fr/01-getting-started.md).
