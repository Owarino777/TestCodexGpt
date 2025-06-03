# 📝 Cahier des Charges Complet — NextGen Starter

---

## 1. Présentation générale

**Nom de code** : NextGen Starter

**Objectif**  
Concevoir un starter universel Next.js (App Router, TypeScript, Tailwind CSS) full-accessible RGAA, plug & play, destiné à tout projet web moderne : e-commerce, SaaS, portfolio, restaurant…  
Permettre :
- Un front modulaire, personnalisable, extensible, performant
- Un admin client-ready (via Supabase, CMS ou dashboard dédié)
- Une architecture 100% industrialisable (CI/CD, tests, monitoring, docs)
- Une expérience utilisateur moderne, inclusive, mobile-first, évolutive

---

## 2. Cibles / Utilisateurs

- **Développeur** : doit pouvoir forker, custom, désactiver modules, déployer Vercel/Cloud en <10min, intégrer de nouveaux outils/features facilement (ex : newsletter, CRM…)
- **Client non-dev** : gère contenus, produits, commandes, pages CMS, support via admin Supabase/CMS, onboarding automatisé
- **Utilisateur final** : site fluide, accessible, SEO-ready, navigation moderne, responsive, UX premium

---

## 3. Fonctionnalités détaillées

### 3.1 Fonctionnalités principales (V1)

| Module                  | Description / Règle Métier |
|-------------------------|----------------------------|
| Auth                | Inscription/login/reset, gestion rôles (admin, user), sécurisation sessions, profils users, RGPD |
| Catalogue produits   | CRUD produits, variantes (couleurs, tailles), catégories hiérarchiques, statuts, images multiples, tags |
| Panier               | Ajout/retrait produits (user connecté ou invité), sauvegarde état panier, MAJ quantité/variantes |
| Commandes            | Checkout complet, calcul total, gestion statuts (pending, paid, shipped…), historique commandes, détails commande |
| Paiement             | Stripe (clé API configurable), gestion échecs/retours, paiement sécurisé |
| CMS Pages/Articles   | CRUD pages statiques (MDX/HTML), édition richtext, SEO (slug, meta, og:image…), statuts (brouillon/publié/archivé) |
| Notifications        | Historique notifs (commandes, support, promos…), système lu/non-lu, emails automatiques (confirmation, réinitialisation, contact) |
| Support / Messagerie | Création ticket/contact, suivi statuts, réponses admin, historique support |
| Dashboard Admin      | UI centralisée : gestion produits, commandes, users, pages, accès support, statistiques mini |
| Internationalisation | Multi-langues via fichiers JSON (next-intl), switcher UI, structure extensible |
| SEO                  | Génération sitemap.xml/robots.txt, gestion meta/OG pour chaque page, balises structurées, audit Lighthouse |
| Accessibilité        | RGAA/WCAG AA (navigation clavier, contraste, ARIA, focus, alternatives, checklist admin avec score auto) |
| Animations           | Transitions pages et UI (Framer Motion), micro-interactions accessibles |
| Import/Export données| CSV/Excel/API pour produits, commandes, users (via admin Supabase ou UI custom) |
| Onboarding           | Guide interactif, checklist post-clone, tuto onboarding utilisateur/admin |
| Industrialisation    | Tests auto (Jest, Playwright), CI/CD GitHub Actions, monitoring Sentry/Lighthouse, docs Nextra/Storybook, plop.js scaffolding |

---

### 3.2 Fonctionnalités secondaires & options (phase 2+)

| Module                  | Description |
|-------------------------|-------------|
| Notifications temps réel| Websockets/Supabase Realtime (E2E notifications, live updates) |
| Multi-tenant/SaaS       | Support multi-clients/sites, isolation données, branding custom par tenant |
| Reviews/Notes produits  | Avis clients, notation produits, modération admin |
| Promotions/Coupons      | Codes promo, règles d’application, gestion expirations |
| Analytics avancé        | Dashboard stats détaillées, intégration GA4/Matomo/Amplitude |
| Stockage fichiers       | Intégration Supabase Storage/AWS S3, upload fichiers, gestion quotas |
| Connecteurs externes    | CRM, newsletter, chatbot, réseaux sociaux |

---

## 4. Architecture technique & dossier

| Dossier / Fichier        | Usage                                 |
|--------------------------|---------------------------------------|
| `/features/`             | Modules clés (auth, cart, product, order, support, etc.) |
| `/components/`           | UI réutilisable, design system (shadcn/ui, custom) |
| `/lib/`                  | Fonctions, hooks, appels API, helpers |
| `/public/`               | Assets statiques (images, SVG, logos…)|
| `/content/`              | Pages MDX, contenu statique           |
| `/config/`               | Config globale, features.ts, i18n, branding, flags |
| `/tests/`                | Tests unitaires/intégration/e2e       |
| `/docs/`                 | Nextra (doc utilisateur), Storybook (UI dev) |
| `.env.example`           | Modèle variables env (Stripe, Supabase…)|

---

## 5. Modèle de données (structure exhaustive)

> **Voir tableau structuré détaillé du message précédent pour chaque entité (User, Product, Category, Order, Cart, Support, Notification, etc.).**  
> **Chaque champ, type, contrainte, description est figé (UUID PK, index, nullable que si nécessaire, relations claires).**

---

## 6. User Stories principales (exemple)

| Rôle        | User Story |
|-------------|------------|
| Client final| Je peux m’inscrire, m’authentifier, gérer mon profil, ajouter au panier, commander, recevoir une confirmation |
| Client final| Je peux consulter mes commandes, contacter le support, changer la langue du site |
| Admin       | Je peux ajouter/éditer/supprimer produits, catégories, pages, gérer les commandes et les tickets support |
| Admin       | Je peux voir un score d’accessibilité sur chaque page/feature dans le dashboard |
| Tous        | Je peux naviguer sur le site avec le clavier et le lecteur d’écran, le site respecte les ratios RGAA |
| Admin       | Je peux importer/exporter mes produits et commandes depuis l’interface admin |

---

## 7. Parcours utilisateur (user flow synthétique)

### User flow principal (client final) :

- Inscription/login (auth)
- Navigation catalogue/produits (listing, filtres, recherche)
- Ajout panier, choix variantes, MAJ quantité
- Passage commande (checkout, adresse, paiement Stripe)
- Confirmation (notifs, mail, dashboard historique)
- Support (contact, suivi ticket)
- Gestion profil (infos, préférences, langue)

### User flow admin :

- Accès dashboard (auth, vérification rôle)
- Gestion catalogue (CRUD produit/catégorie/stock/images/variantes/tags)
- Gestion commandes (vue, statut, export)
- Gestion CMS (pages/articles, SEO, meta)
- Support (tickets, réponses)
- Gestion users, scoring accessibilité, audit

---

## 8. API contracts (exemple)

| Endpoint              | Méthode | Entrée                    | Sortie                  | Statuts |
|-----------------------|---------|---------------------------|-------------------------|---------|
| `/api/products`       | GET     | ?filters, ?pagination     | Liste produits (JSON)   | 200, 401|
| `/api/orders`         | POST    | Body (userId, cart, etc.) | Confirmation commande   | 201, 400|
| `/api/auth/login`     | POST    | email/password            | JWT/session             | 200, 401|
| `/api/support`        | POST    | Body (userId, message)    | Ticket créé             | 201, 400|

---

## 9. Plan de test (acceptance criteria)

- **Tests UI** : Jest/Testing Library sur chaque composant (affichage, interaction, accessibilité)
- **Tests e2e** : Playwright (inscription/login, passage commande, support, onboarding)
- **Tests accessibilité** : axe-core sur chaque page/scénario clé
- **Critères d’acceptation** :
    - Toute fonctionnalité accessible au clavier/lecteur d’écran
    - Stock jamais négatif, commandes non validées si stock insuffisant
    - Un utilisateur ne peut modifier que ses propres données (sauf admin)
    - Les emails s’envoient correctement selon statuts/action
    - Toute erreur (404/401/500) renvoie un message lisible et RGAA

---

## 10. Conventions & guidelines

- **Code** : TypeScript strict, no-any, hooks en camelCase, nommage BEM pour CSS si besoin, conventions shadcn/ui
- **Lint/Prettier** : obligatoires, config stricte
- **Commit** : Conventional Commits (`feat:`, `fix:`, `test:`, `docs:`, etc.)
- **Doc** : tout module/feature documenté (README, exemples, Storybook, Nextra)
- **Contribution** : Guide CONTRIBUTING.md (branch, review, déploiement…)

---

## 11. Déploiement & environnements

- **Variables .env** : Stripe, Supabase, etc. (doc exemple fournie)
- **CI/CD** : GitHub Actions (test, lint, build, deploy Vercel)
- **Monitoring** : Sentry, Lighthouse report sur chaque build prod
- **Procédure migration/seed** : Script prisma/supabase, onboarding auto (doc inclus)

---

## 12. Roadmap évolutive

- **V1** : socle fonctionnel, tout ce qui précède (Vercel deployable day one)
- **V2** : notifications temps réel, reviews, multi-tenant, analytics avancé, storage fichiers, connecteurs externes, custom CMS, autres moyens de paiement, webhooks, etc.

---

## 13. Checklist de livraison

- [ ] Parcours utilisateurs validés
- [ ] Modèle de données conforme
- [ ] Tests automatiques présents et passants
- [ ] Accessibilité validée (axe-core, RGAA)
- [ ] CI/CD opérationnel
- [ ] Docs utilisateur & UI générées
- [ ] Import/export fonctionnel testé
- [ ] Déploiement Vercel/production validé
- [ ] Guide onboarding/tutoriel actif

---

## Remarques finales

- Ce cahier des charges s’aligne sur la crème des starters Next.js actuels (Vercel Commerce, Payload, Lemon Squeezy, Shopify headless…).
- Toutes les fonctionnalités et specs sont adaptables par flags, modules et fichiers de config.
- Le repo produit sera forkable, duplicable, industrialisable et scalable sans refonte.
- **Bonus** : RGPD, backup DB, process support, versioning du starter à documenter en phase 2+.

---

