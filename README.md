# ArtisanFlow

> Application métier mobile pensée pour les artisans : transformer rapidement les informations du terrain en données exploitables, documents commerciaux et suivi de chantier.

**Statut : vitrine technique.** Le code source de production, les données, prompts, configurations, secrets et règles métier propriétaires ne sont pas publiés dans ce dépôt.

## Le problème

Sur chantier, une grande partie de l'information arrive sous une forme peu structurée : notes prises rapidement, demandes client, observations techniques, prestations à chiffrer et éléments à reporter dans un devis.

ArtisanFlow explore une approche simple : réduire la ressaisie et rapprocher la capture terrain des outils de gestion réellement utilisés par l'artisan.

## Ce que j'ai construit

- application mobile métier avec **React Native / Expo** ;
- backend et persistance autour de **Supabase** ;
- capture et **transcription vocale** pour convertir une note terrain en texte exploitable ;
- recherche et mise en correspondance avec un catalogue métier d'environ **30 000 références de prix** ;
- gestion de clients et chantiers ;
- génération et suivi de **devis / factures** ;
- intégration de briques IA dans les flux où elles apportent une aide concrète plutôt qu'une interface conversationnelle ajoutée artificiellement.

## Architecture — vue publique

```text
Utilisateur terrain
       |
       v
Application mobile
React Native / Expo
       |
       +---- saisie structurée
       |
       +---- capture vocale
       |          |
       |          v
       |     transcription
       |          |
       |          v
       |   traitement / extraction
       |
       +---- recherche catalogue métier
       |          |
       |          v
       |    ~30 000 références
       |
       v
Services applicatifs
       |
       v
Supabase / données métier
       |
       +---- clients
       +---- chantiers
       +---- devis / factures
       +---- données nécessaires aux workflows
```

Cette représentation est volontairement simplifiée. Les détails d'implémentation, schémas internes, règles métier et configurations de production restent privés.

## Exemple de flux

```text
Observation sur chantier
        ↓
Note vocale
        ↓
Transcription
        ↓
Texte exploitable
        ↓
Recherche / rapprochement métier
        ↓
Éléments structurés
        ↓
Chantier / devis
```

L'objectif n'est pas de demander à une IA de « faire le métier à la place de l'artisan », mais de supprimer une partie des manipulations répétitives entre le terrain et l'administratif.

## Principes de conception

**Terrain d'abord.** Les workflows partent de situations rencontrées dans le travail artisanal.

**IA ciblée.** Un modèle n'est utilisé que lorsqu'il apporte quelque chose qu'une interface ou une règle déterministe ne fait pas mieux.

**Données structurées.** La sortie utile n'est pas seulement du texte : elle doit pouvoir rejoindre les objets métier de l'application.

**Mobile.** La capture doit rester utilisable dans les conditions réelles d'un chantier.

## Stack présentée publiquement

| Couche | Technologies / approche |
| --- | --- |
| Mobile | React Native, Expo |
| Données / backend | Supabase |
| Voix | capture audio + transcription |
| IA | modèles intégrés aux workflows applicatifs |
| Données métier | catalogue d'environ 30 000 références |
| Produit | clients, chantiers, devis, facturation |

## Pourquoi ce projet est représentatif

ArtisanFlow est né de mon expérience d'artisan du bâtiment. Il combine donc deux domaines que je pratique directement : **le problème métier** et **la construction de la solution technique**.

Mon rôle sur ce type de projet correspond à celui d'un **AI Builder / intégrateur de systèmes IA** : comprendre le besoin, concevoir le flux, assembler application, données, API et modèles, tester l'ensemble puis l'amener jusqu'à un outil utilisable.

## Démonstration

Une démonstration vidéo et des captures pourront être ajoutées ici dans une prochaine passe. Elles montreront le produit sans exposer les données, configurations ou mécanismes internes réservés au projet privé.

## Ce qui reste volontairement privé

Ce dépôt ne contient pas :

- le code source de production ;
- les clés, secrets ou variables d'environnement ;
- les données utilisateurs ;
- le catalogue métier brut ;
- les prompts et configurations internes ;
- les schémas détaillés de base de données ;
- les règles métier propriétaires ;
- les documents internes de développement et d'audit.

Cette séparation est intentionnelle : **montrer les choix, le système et le résultat sans publier le cœur propriétaire du produit.**

---

**Christopher Crahay**  
AI Builder — Intégrateur de systèmes IA
