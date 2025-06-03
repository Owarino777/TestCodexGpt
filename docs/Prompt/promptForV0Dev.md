# 🖼️ Maquettes v0.dev — Spécifications UI (Next.js, shadcn/ui, Tailwind)

Toutes les pages sont :
- Mobile-first & responsive
- RGAA/WCAG AA compliant
- Dark mode Ready
- shadcn/ui components + Tailwind CSS
- Focus management & ARIA optimisés

---

## 📄 Home / Landing Page✅✅✅

- Header/nav clair avec login/signup, switch langue, dark mode
- Hero section full-width avec titre, description, CTA, image
- Produits phares (cards)
- Avantages/valeurs (feature grid)
- Shop par catégories (Tabs)
- Avis clients (testimonials)
- Newsletter
- Footer complet

> Prompt v0.dev :  
_A modern, accessible e-commerce homepage with a full-width hero section, product highlights, feature grid, value propositions, call to action, and customer testimonials. Use shadcn/ui and Tailwind CSS. Responsive, RGAA/WCAG AA compliant, dark mode enabled, mobile-first. Include clear navigation, login/signup buttons, and language switcher._

---

## 🛍️ Product Catalog / Category Page

- Grille responsive de cards produits
- Filtres : catégorie, tags, prix, tri, barre de recherche
- Pagination
- Pour chaque produit : image, titre, prix, "Add to cart"

> Prompt v0.dev :  
_A product catalog page displaying a responsive grid of product cards, filters by category/tags/price, search bar, pagination, and sorting options. Each product card shows image, title, price, and "Add to Cart" button. Use shadcn/ui components and Tailwind CSS. Fully accessible, RGAA/WCAG AA, keyboard navigable, responsive for mobile and desktop._

---

## 🛒 Product Detail Page

- Galerie image, titre, description, prix, variantes (taille/couleur), statut stock
- Sélecteur quantité, bouton "Add to Cart"
- Produits similaires, reviews/notes

> Prompt v0.dev :  
_A product detail page with a main image gallery, product title, description, price, available variants (color/size selector), stock status, quantity selector, and "Add to Cart" button. Include related products and customer reviews/ratings section. shadcn/ui and Tailwind CSS, RGAA/WCAG AA, responsive, dark mode, accessible labels and focus management._

---

## 🛍️ Cart Page

- Liste produits (image, titre, variantes, quantité, prix, bouton remove)
- Sous-total, taxes, total, champ code promo
- Bouton "Proceed to checkout"

> Prompt v0.dev :  
_A shopping cart page listing all added products with image, title, selected variants, quantity selector, price, and remove button. Show subtotal, taxes, total amount, and a "Proceed to Checkout" button. Option for entering a promo code. Fully responsive, shadcn/ui, Tailwind CSS, RGAA/WCAG AA compliant, keyboard and screen reader accessible._

---

## 💳 Checkout Page

- Formulaire multi-step (adresse, facturation, Stripe, review commande)
- Récap commande, erreurs de validation, progress bar
- Bouton "Place order"

> Prompt v0.dev :  
_A checkout page with a multi-step form (delivery address, billing info, payment by Stripe, order review). Show order summary, form validation errors, progress indicator, and "Place Order" button. Use shadcn/ui Form, Input, and Button components. Tailwind CSS, mobile-first, RGAA/WCAG AA compliant, clear focus, error messages, accessible form fields._

---

## ✅ Order Confirmation Page

- Récap : numéro commande, produits, adresse, paiement
- Message "Merci", liens continuer shopping/support

> Prompt v0.dev :  
_An order confirmation page showing order number, summary of purchased items, delivery address, payment status, and a button to view order history. Include a thank-you message and links to continue shopping or contact support. shadcn/ui and Tailwind CSS, accessible, responsive, internationalized._

---

## 📂 Order History / User Dashboard

- Tableau ou liste commandes (status, date, lien détail)
- Navigation latérale : profil, adresses, support

> Prompt v0.dev :  
_A user dashboard page with a table or list of previous orders, status (pending, paid, shipped), order dates, and links to view order details. Side navigation for profile, addresses, support messages. Use shadcn/ui Table, Card, Tabs, and Sidebar components. Fully responsive, RGAA/WCAG AA, keyboard navigable._

---

## 👤 User Profile / Settings Page

- Formulaire mise à jour info (nom, email, avatar), mot de passe, préférences (langue, thème)

> Prompt v0.dev :  
_A user profile/settings page allowing the user to update personal information (name, email, avatar), password, and preferences (language, theme). shadcn/ui Form, Avatar, and Button components. Tailwind CSS, responsive, accessible (labels, validation, focus)._

---

## 🔒 Auth (Login/Register/Forgot Password)

- Login : email/password, remember me, forgot, social login (Google)
- Register : email/password/confirm, CGU, social
- Forgot password : email, feedback message

> Prompt v0.dev Login :  
_A login page with email and password fields, "Remember me" checkbox, "Forgot password" link, and a login button. Option for social login (Google). shadcn/ui Card, Input, Button. Tailwind CSS, RGAA/WCAG AA, mobile-first, clear error messages, accessible labels._

> Prompt v0.dev Register :  
_A registration/signup page with email, password, confirm password fields, and "Create Account" button. Option for social signup (Google). Terms of service/consent checkbox. shadcn/ui Card, Input, Button, Checkbox. Tailwind CSS, accessible, responsive, RGAA/WCAG AA._

> Prompt v0.dev Forgot :  
_A password reset page with email field, submit button, and confirmation message. shadcn/ui Card, Input, Button. Tailwind CSS, RGAA/WCAG AA, mobile-first, accessible labels and focus management._

---

## 📧 Support / Contact / Tickets Page

- Formulaire ticket (sujet, message)
- Liste des messages/supports précédents, statut (open, closed, pending)
- Admin peut répondre

> Prompt v0.dev :  
_A support/contact page with a form for submitting a ticket (subject, message), a list of previous support messages, and status of each request (open, closed, pending). Admin can reply to tickets. shadcn/ui Form, Card, Badge. Tailwind CSS, accessible, RGAA/WCAG AA, responsive._

---

## 🔔 Notifications Page

- Liste notifications (updates, support, promos), lu/non-lu, filtres, "mark as read/unread"

> Prompt v0.dev :  
_A notifications page showing a list of notifications (order updates, support replies, promos), read/unread state, with filtering and mark as read/unread actions. shadcn/ui Card, Badge, Button. Tailwind CSS, accessible, RGAA/WCAG AA, responsive, keyboard navigable._

---

## 📰 CMS Pages / Blog / Articles (Static)

- Rendu MDX riche, images, code blocks, info auteur
- Sidebar navigation catégories/tags, barre recherche, liens next/prev

> Prompt v0.dev :  
_A CMS/article page rendering MDX content with rich text, images, code blocks, and author info. Include a navigation sidebar for categories/tags, a search bar, and links to previous/next articles. shadcn/ui Typography, Card, Sidebar. Tailwind CSS, accessible, RGAA/WCAG AA, responsive._

---

## 📊 Admin Dashboard (CRUD Management)

- Sidebar navigation (produits, commandes, users, CMS, support)
- Statistiques (cards), activité récente, quick links
- Chaque module : table/liste, CRUD (modals), pagination, filtres

> Prompt v0.dev :  
_An admin dashboard with a sidebar for navigation (products, orders, users, CMS, support), statistics cards (total sales, orders, users), recent activity, and quick links. Each management section has tables/lists with CRUD actions (add/edit/delete), modals, pagination, filters. shadcn/ui components everywhere, Tailwind CSS, RGAA/WCAG AA, responsive, keyboard accessible._

---

## 🌍 Language Switcher / i18n Ready

- Dropdown ou bouton switcher langue dans le header
- shadcn/ui Select ou DropdownMenu

> Prompt v0.dev :  
_A language switcher dropdown/button placed in the header, allowing the user to change the language (en/fr/es…). Accessible, shadcn/ui Select or DropdownMenu. Tailwind CSS, RGAA/WCAG AA, keyboard and screen reader accessible, visible focus._

---

## ⚙️ Accessibility Report / RGAA Score Page (Admin)

- Dashboard accessibilité : score par page, checklist critères, recommandations
- Table/card, progress bar, filtres

> Prompt v0.dev :  
_An accessibility dashboard for admins showing RGAA/WCAG scores for each page, a checklist of criteria, and recommendations for improvement. Table or card layout, progress bars, filters by compliance status. shadcn/ui Table, Card, Progress. Tailwind CSS, responsive, accessible._

---

## 🧑‍💼 Onboarding / Interactive Tutorial Page

- Page/modale onboarding, tuto interactif step-by-step
- Highlights, progress, skip

> Prompt v0.dev :  
_An onboarding page or modal with a step-by-step interactive guide for new users, including highlights/tips for main features, progress indicator, skip option. shadcn/ui Dialog, Card, Steps. Tailwind CSS, accessible, mobile-first, RGAA/WCAG AA compliant._

---

## 🕹️ 404 / Not Found / Error Page

- Illustration, message d’erreur, bouton retour home

> Prompt v0.dev :  
_A 404 Not Found page with an illustration, error message, and a button to return to the homepage. shadcn/ui Card, Button. Tailwind CSS, responsive, accessible, dark mode enabled._

---
