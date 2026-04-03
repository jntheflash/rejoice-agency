# Rejoice Agency — Site vitrine

## Stack
- Pages racine : index.html, ressources.html, apropos.html, 404.html
- Sous-pages services : services/integration-erp.html, services/integration-crm.html, services/audit-erp.html, services/formation-odoo.html, services/integration-ia.html
- Sous-pages secteurs : secteurs/cabinet-expertise-comptable.html, secteurs/industrie-fabrication.html, secteurs/negoce-distribution.html, secteurs/services-professionnels.html
- 1 fichier CSS partagé : style.css
- Hébergé sur Netlify (drag and drop) — migration Cloudflare Pages prévue
- Repo GitHub : jntheflash/rejoice-agency
- Workflow déploiement : `git add . && git commit -m "..." && git push` puis drag & drop sur Netlify
- Domaine : rejoice-agency.fr

## Améliorations déjà faites
- Liens Calendly et LinkedIn corrigés sur les 4 pages
- Bouton "Réserver un créneau" cliquable
- Meta descriptions et Open Graph ajoutés sur les 4 pages
- rel="noopener noreferrer" sur tous les liens externes
- Menu hamburger corrigé (se ferme au clic)
- Favicon SVG avec le "R" de Rejoice
- JSON-LD ProfessionalService ajouté sur index.html
- Contraste --muted corrigé (#5C5955, WCAG AA)
- Aria/alt ajoutés sur emojis et SVG
- Inline styles supprimés et remplacés par des classes CSS

## Améliorations — Session du 02/04/2025
- JSON-LD ajouté sur services.html, secteurs.html et ressources.html
- sitemap.xml créé et soumis à Google Search Console
- robots.txt créé
- Balises canonical ajoutées sur les 4 pages
- En-têtes de sécurité HTTP via fichier _headers Netlify
- Page 404.html personnalisée aux couleurs de Rejoice
- Google Search Console configuré et vérifié
- Fichier de vérification Google ajouté

## Améliorations — Session du 02/04/2025 (suite)
- Suppression du lien "Accueil" dans le header des 5 pages (le logo suffit)
- Création page apropos.html avec SEO complet (meta, OG, JSON-LD Person + ProfessionalService, canonical)
- Ajout "À propos" dans le header desktop + mobile des 5 pages
- sitemap.xml mis à jour avec apropos.html
- Titre index.html changé en "Rejoice : l'agence d'intégration Odoo" (og:title aussi)
- Connexion GitHub configurée (repo : jntheflash/rejoice-agency)

## Améliorations — Session du 02/04/2025 (restructuration)
- 9 sous-pages créées (5 services, 4 secteurs) avec SEO complet (meta, OG, JSON-LD, canonical)
- Dropdowns header sur toutes les pages (survol desktop, clic mobile)
- services.html et secteurs.html supprimés
- CSS dropdown ajouté dans style.css
- sitemap.xml mis à jour avec les 9 nouvelles URLs
- Tous les liens internes mis à jour

## Prochaines améliorations possibles
- Migration Cloudflare Pages (prévue ce soir)
- Optimisation images si ajout futur
