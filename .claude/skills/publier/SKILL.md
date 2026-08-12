---
description: Publier un brouillon validé sur le site Rejoice — déplacer vers ressources/, mettre à jour ressources.html (carte, compteurs, vedette), sitemap.xml, _redirects, llms.txt et le maillage, puis committer et pousser.
argument-hint: [nom du fichier dans drafts/]
---

Publie le brouillon : $ARGUMENTS

(S'il n'y a qu'un seul fichier dans `drafts/`, prends celui-là. S'il y en a plusieurs et aucun
argument, demande-moi lequel.)

Déroule la checklist de publication de `claude.md` (section « Publication d'un article ») —
les 7 points, aucun oubli :

1. Déplace le fichier de `drafts/` vers `ressources/<slug>.html`.
2. `ressources.html` :
   - ajoute la carte `<article class="article-card" data-category="...">` EN TÊTE de `#articlesGrid`,
     dans le style exact des cartes existantes (gradient, deco-circles, emoji, catégorie colorée,
     date « J mois AAAA », temps de lecture) ;
   - mets à jour le compteur `#resultsCount` ;
   - mets à jour la stat « N articles publiés » du hero ;
   - si c'est l'actualité mensuelle : remplace le contenu de la carte `.featured-section`
     (À la une) par ce nouvel article ;
   - si nouvelle catégorie : ajoute le bouton de filtre correspondant.
3. `sitemap.xml` : ajoute `<url>` avec `<lastmod>` du jour et priority 0.7.
4. `_redirects` : ajoute la ligne `/ressources/<slug>.html  /ressources/<slug>  301`.
5. `llms.txt` : ajoute l'entrée sous `## Ressources` (titre lien + description d'une ligne).
6. Maillage : ajoute ce nouvel article dans le bloc « À lire aussi » d'1 ou 2 articles existants
   pertinents.
7. Vérifie que TOUS les liens ajoutés pointent vers des fichiers existants et que les compteurs
   sont justes.

Puis : commit en français (« Publie l'article : <titre> ») et push sur `main`.
Termine en me rappelant que Netlify met en ligne automatiquement et donne-moi l'URL finale
(https://rejoice-agency.fr/ressources/<slug>).
