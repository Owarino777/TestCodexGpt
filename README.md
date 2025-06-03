# 🚀 NextGen Starter

> **Starter universel Next.js 15 / Supabase / Tailwind / shadcn/ui — Plug & Play, accessible RGAA, full modulaire.**

[![CI](https://img.shields.io/github/actions/workflow/status/Owarino777/TestCodexGpt/ci.yml?branch=main)](https://github.com/Owarino777/TestCodexGpt/actions)
[![MIT License](https://img.shields.io/github/license/Owarino777/TestCodexGpt)](LICENSE)
[![Next.js](https://img.shields.io/badge/Next.js-15.3.3-black)](https://nextjs.org/)
[![Supabase](https://img.shields.io/badge/Supabase-cloud-green)](https://supabase.com/)
[![Tailwind CSS](https://img.shields.io/badge/TailwindCSS-3.x-blue)](https://tailwindcss.com/)
[![shadcn/ui](https://img.shields.io/badge/shadcn--ui-components-blueviolet)](https://ui.shadcn.com/)
[![Accessibility](https://img.shields.io/badge/RGAA--WCAG-AA--ready-brightgreen)](https://accessibilite.numerique.gouv.fr/)

---

## 🎯 Pitch

**NextGen Starter** est un socle Next.js ultra-moderne, 100% accessible, conçu pour lancer n’importe quel projet web en un temps record :  
- **E-commerce**, **SaaS**, **portfolio**, **resto**…  
- Modulaire (active/désactive chaque feature)
- Dashboard admin client-ready (Supabase ou CMS plug-in)
- Docs, tests, CI/CD, animations, internationalisation, SEO, RGAA inclus  
- Architecture industrialisable, duplicable, scalable

Le starter **des devs, pour les devs et les clients non-tech**.

---

## 📑 Documentation

- [Cahier des charges complet](docs/cahier_des_charges.md)
- [Guide technique (à venir)](docs/guide_technique.md)
- [Docs UI/UX (Storybook)](docs/storybook.md)
- [Architecture & wireframes (à venir)](docs/architecture.md)

---

## ⚡️ Stack technique

- [Next.js 15 (App Router, TypeScript)](https://nextjs.org/docs/app)
- [Supabase (PostgreSQL, Auth, Storage)](https://supabase.com/docs)
- [Prisma ORM](https://www.prisma.io/docs/)
- [Tailwind CSS](https://tailwindcss.com/docs/)
- [shadcn/ui](https://ui.shadcn.com/docs/installation/next)
- [Framer Motion](https://www.framer.com/motion/)
- [next-intl (i18n)](https://next-intl.js.org/docs/)
- [Jest, Testing Library, Playwright, axe-core (tests, a11y)](https://nextjs.org/docs/app/building-your-application/testing/jest)
- [Nextra (doc), Storybook (UI), plop.js (scaffolding)]
- [Sentry, Lighthouse (monitoring)]
- [CI/CD GitHub Actions, Vercel deploy]

---

## 🚀 Démarrage rapide

### 1. **Cloner le repo**
```bash
git clone https://github.com/Owarino777/TestCodexGpt.git
cd TestCodexGpt
```

# 2. Installer les dépendances
```bash
pnpm install
# ou
yarn install
# ou
npm install
```

# 3. Configurer les variables d’environnement
### Copie .env.example → .env.local
### Renseigne tes clés Supabase, Stripe, etc.

# 4. Lancer en local
```bash
pnpm dev
# ou
yarn dev
# ou
npm run dev
```

## 📋 Fonctionnalités clés
- Auth, panier, catalogue, commandes, paiement Stripe
- CMS pages/articles, admin dashboard, support intégré
- Notifications, SEO, i18n, animations, RGAA-ready
- Import/export CSV, onboarding interactif, CI/CD intégré

## 🔗 Ressources et docs officielle
- https://nextjs.org/docs
- https://supabase.com/docs
- https://www.prisma.io/docs
- https://motion.dev/
- https://accessibilite.numerique.gouv.fr/methode/
- https://accessibilite.numerique.gouv.fr/methode/criteres-et-tests/
- https://playwright.dev/docs/intro
- https://nextra.site/docs
- https://ui.shadcn.com/docs
- https://ui.shadcn.com/docs/installation/next
- https://tailwindcss.com/docs/installation/using-vite

# Convention de commits :
- https://www.conventionalcommits.org/en/v1.0.0/

# 📄 Licence
## MIT © Owarino777

---

> **Étape suivante (rappel) :**
> 
> - **Prépare l’arborescence projet**  
>   → `pnpm create next-app@latest` avec TypeScript, Tailwind, App Router
> 
> - **Définis la config Supabase**  
>   → Crée projet Supabase, ajoute tables (User/Product/Order/…), exports `.env.example`
> 
> - **Wireframes et maquettes**  
>   → Pages clés (Home, Produit, Panier, Admin…), diagrammes navigation (draw.io, Figma…)
> 
> - **Diagrammes UML/ERD**  
>   → Schéma BDD, use cases principaux
> 
> - **Initialisation du design system**  
>   → Setup shadcn/ui, Tailwind, Framer Motion, thèmes
> 
> - **Plan d’itération / tâches**  
>   → Création d’issues GitHub par module

---
