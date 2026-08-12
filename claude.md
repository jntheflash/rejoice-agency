# Rejoice Agency — Site vitrine

Site vitrine statique (HTML/CSS) pour l'agence d'intégration Odoo Rejoice.
Domaine : rejoice-agency.fr — Interlocutrice : Sophie Merdrignac.

## Stack technique

- HTML/CSS statique, pas de framework JS
- 1 fichier CSS partagé : `style.css`
- Fonts self-hosted (dossier `fonts/`) — plus aucune dépendance Google Fonts
- Hébergement : Netlify. Objectif : déploiement automatique depuis GitHub (branche `main`) ; historiquement drag & drop manuel.
- Repo GitHub : jntheflash/rejoice-agency (privé, connecté à ce dossier via `origin`)
- Analytics : Google Analytics 4 (ID : G-2PS5JX89ME), chargé après consentement RGPD

## Arborescence actuelle (32 pages HTML)

**Racine :** `index.html`, `ressources.html`, `tarifs-odoo.html`, `404.html`,
`mentions-legales.html`, `politique-confidentialite.html`, `politique-cookies.html`

**`/services/` (4) :** `consultant-odoo`, `formation-odoo`, `integration-odoo`, `developpement-odoo`

**`/fonctionnalites/` (8) :** `odoo-facture-electronique`, `crm-odoo`, `odoo-erp`, `odoo-comptabilite`,
`odoo-gestion-stock`, `odoo-logistique`, `odoo-19`, `odoo-ia`

**`/metier/` (4) :** `gestionnaire-de-projet`, `comptable`, `dirigeant`, `rh`

**`/ressources/` (6 articles) :** `pourquoi-odoo`, `quest-ce-quun-erp`, `comment-integrer-odoo`,
`odoo-community-vs-enterprise`, `actualites-odoo-juin-2026`, `actualites-odoo-juillet-2026`

**`/agence/` (3) :** `qui-sommes-nous`, `methodologie`, `contact`

**Rédaction :** `drafts/` (brouillons d'articles, jamais en ligne), `templates/article.html` (modèle
officiel d'article), `ideas.md` (backlog d'idées d'articles)

## Fichiers techniques

- `sitemap.xml`, `robots.txt`, `llms.txt` (format llmstxt.org)
- `_headers` (en-têtes sécurité Netlify + cache `/fonts/*` 1 an immutable)
- `_redirects` (redirections 301, notamment `.html` → sans extension, UNE LIGNE PAR PAGE)
- `fonts/` — 3 fichiers .woff2 self-hosted ; `images/` — logos clients et illustrations

## Fonts (self-hosted, dans `fonts/`)

- `caveat-700.woff2` — Caveat 700 (logo + h1/h2/h3/h4)
- `dmsans.woff2` — DM Sans variable (poids 400, 600, 700) ; `dmsans-italic.woff2` — italique (témoignages)
- `@font-face` en haut de `style.css` avec `font-display: swap`
- Chaque page : un seul `<link rel="preload" href="/fonts/caveat-700.woff2" as="font" type="font/woff2" crossorigin />`

## Navigation (header)

Dropdowns desktop + mobile : "Nos expertises Odoo" (4 liens `/services/`), "Fonctionnalités Odoo"
(8 liens `/fonctionnalites/`), "Votre Métier" (4 liens `/metier/`), "L'Agence" (3 liens `/agence/`).
Liens simples : "Ressources" → `/ressources`, "Tarifs" → `/tarifs-odoo`. CTA : "Prendre RDV" → `/#rdv`.

Règles visuelles : `dd-dot` colorés sur desktop uniquement ; mobile sans `dd-dot`, CTA `align-start`
(sauf pages légales) ; fond blanc pur ; dropdowns en `<button>` (pas `<a href="#">`).

## Conventions à respecter

**URLs internes :** toujours SANS extension `.html` (ex : `/services/consultant-odoo`).
Ancres racine : `/` ou `/#rdv`.

**Coordonnées partout (JSON-LD, mailto, textes) :**
sophie@rejoice-agency.fr · +33 6 48 75 28 57 · Nantes, Pays de la Loire, FR

**JSON-LD — pièges :** pas de `serviceType` dans `ProfessionalService` ; pas de `audience` dans
`Service` ; `og:url` = `canonical` (sans `.html`).

**Accessibilité :** `<main>` englobe tout entre `</header>` et `<footer>` ; bannière cookies hors
de `<main>` ; dimensions explicites sur tous les `<img>` ; contraste WCAG AA (liens en `var(--text)`).

**Bannière cookies (RGPD) :** GA4 lazy, activé au consentement ; localStorage `cookieConsent`
(`accepted`/`refused`) ; lien vers `/politique-cookies`.

**Top banner :** fixe desktop, ticker mobile (`.banner-ticker-dup` pour la boucle) ; fermeture via
`sessionStorage` ; `body.has-banner header { top: 40px }`.

## Articles de blog (section Ressources)

- Brouillons dans `drafts/` — JAMAIS directement dans `ressources/`.
- Modèle OBLIGATOIRE : `templates/article.html` (structure : page-hero avec breadcrumb + badge +
  auteur Sophie, encadré "L'essentiel" `.article-tldr`, sommaire `.article-toc`, sections H2 avec `id`,
  callouts `callout--info/example/note`, bloc "À lire aussi" `.related-grid`, JSON-LD `Article`).
- SEO : title unique < 60 car., meta description < 155 car., un seul H1, alt sur les images,
  UN mot-clé principal par article — vérifier qu'aucune page existante ne le cible (cannibalisation).
- Catégories existantes : Guide, Comparatif, Actualités (filtre `data-category="actualites"`).
- Longueur : 800 à 1500 mots. Aucun fait inventé : chiffres et citations sourcés (recherche web).
- Auteur : Sophie Merdrignac, "Intégratrice Odoo certifiée à Nantes", avatar `/images/sophie-merdrignac.webp`.

## Publication d'un article — checklist EXACTE (7 points, tous obligatoires)

1. Fichier final : `ressources/<slug>.html` (slug court, sans date, ex : `odoo-vs-dolibarr`).
2. `ressources.html` : ajouter la carte `<article class="article-card" data-category="...">` dans
   `#articlesGrid` (en tête de grille) ; mettre à jour le compteur `#resultsCount` ; mettre à jour
   les hero-stats ("N articles publiés") ; si c'est l'actualité mensuelle → elle devient aussi
   la vedette de `.featured-section` (remplacer le contenu de la carte featured).
3. `sitemap.xml` : ajouter `<url>` avec `<lastmod>` (AAAA-MM-JJ), priority 0.7.
4. `_redirects` : ajouter la ligne `/ressources/<slug>.html  /ressources/<slug>  301`.
5. `llms.txt` : ajouter l'entrée sous `## Ressources` (titre + URL + description d'une ligne).
6. Maillage interne : 3 cartes "À lire aussi" dans le nouvel article + ajouter le nouvel article
   dans le bloc "À lire aussi" d'1 ou 2 articles existants pertinents.
7. Vérifier que tous les liens ajoutés pointent vers des fichiers existants.

## Workflow de publication (validation humaine obligatoire)

1. **En local :** `/nouvel-article` crée le brouillon dans `drafts/` → JN valide → `/publier`
   déroule la checklist ci-dessus, committe et pousse sur `main`.
2. **En automatique (GitHub Actions, `article-auto.yml`) :** l'article arrive dans une Pull Request
   déjà prête (checklist complète appliquée dans la branche `article/AAAA-MM-JJ-slug`).
   La fusion de la PR = mise en ligne (Netlify). NE JAMAIS fusionner automatiquement.
3. Ne jamais pousser un nouvel article directement sur `main` sans validation.
4. Messages de commit en français, courts et descriptifs.

## Agents et commandes du projet

- Agent `redacteur-web` : recherche + rédaction des brouillons (respecte le template).
- Agent `relecteur-seo` : relecture bloquante avant toute publication.
- `/nouvel-article [sujet]`, `/publier [fichier]`, `/idees-articles [thème]`.

## Optimisations performance déjà en place (ne pas casser)

Fonts self-hosted + preload Caveat ; cache immutable `/fonts/*` ; `font-display: swap` ;
Calendly script en `defer` (pas de widget réel, liens Google Calendar) ; dimensions explicites
sur images (zéro CLS) ; `<main>` partout.

**Scores PageSpeed de référence (à ne pas dégrader) :** Desktop 97/94/100/100 · Mobile 87-88/96/100/100.

## TODO (hors articles)

- Redimensionner les 5 logos clients (Blobb, Epiphyse, Gwinizh, Holeo, Maison Warin) :
  380×160 affichés en 143×60 → ~286×120 via Squoosh.
- Migration Cloudflare Pages : éventuelle, pas prioritaire (on reste sur Netlify).
