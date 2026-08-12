---
description: Créer un nouvel article Ressources complet pour Rejoice (recherche, rédaction, relecture) puis le soumettre à validation. Utiliser quand on demande d'écrire ou de préparer un article.
argument-hint: [sujet de l'article]
---

Crée un nouvel article pour la section Ressources sur le sujet : $ARGUMENTS

(Si aucun sujet n'est donné, prends la première idée non cochée de `ideas.md`.)

Étapes :

1. Lance l'agent `redacteur-web` pour rédiger le brouillon dans `drafts/` (template
   `templates/article.html` obligatoire, recherche web réelle, sources citées).
2. Lance l'agent `relecteur-seo` sur le brouillon. S'il répond « À REVOIR », fais corriger par
   `redacteur-web` puis refais relire (2 allers-retours maximum).
3. Une fois le brouillon « PRÊT À PUBLIER », présente-moi : le titre, la meta description,
   le mot-clé visé, la catégorie, un résumé en 3 phrases et les sources utilisées. Propose-moi
   d'ouvrir le fichier `drafts/<slug>.html` dans mon navigateur pour le lire.
4. Demande-moi explicitement si je valide la publication. **Ne publie jamais sans mon accord.**
5. Si je valide → déroule la commande `/publier` sur ce brouillon. Si je refuse → applique mes
   retours puis repropose.
