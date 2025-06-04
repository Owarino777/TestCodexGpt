Modèle de données — Spécifications détaillées
1. User (utilisateur)
Champ	Type	Contraintes	Description
id	UUID (PK)	unique, non nul, auto-généré	Identifiant utilisateur
email	string(180)	unique, non nul, index	E-mail de connexion
password_hash	string(255)	non nul	Hash du mot de passe
firstname	string(100)	non nul	Prénom
lastname	string(100)	non nul	Nom
role	enum	[admin, utilisateur]	Rôle système
created_at	datetime	non nul, default now	Date de création du compte
updated_at	datetime	non nul, default now, auto	Date de dernière modification
is_active	boolean	non nul, default true	Statut actif/désactivé
last_login	datetime	nullable	Dernière connexion
avatar_url	string(255)	nullable	URL avatar utilisateur

Relations :

1..N commandes (Order)

1..N messages support (SupportMessage)

1..N notifications (Notification)

1 panier (Cart)

2. Product (produit)
Champ	Type	Contraintes	Description
id	UUID (PK)	unique, non nul, auto-généré	Identifiant produit
title	string(255)	non nul, index	Nom produit
description	text	nullable	Description longue
price	decimal(10,2)	non nul, >=0	Prix TTC
status	enum	[active, inactive, draft]	État (dispo, désactivé, brouillon)
stock	int	non nul, >=0	Quantité en stock
created_at	datetime	non nul, default now	Date de création
updated_at	datetime	non nul, default now, auto	Dernière modif
sku	string(100)	unique, nullable	Référence interne/SKU
weight	decimal(6,2)	nullable	Poids (kg/g)
variants	JSON	nullable	Tableau des variantes (taille, couleur, etc.)
tags	string[] (array)	nullable, index	Mots-clés/filtrage
images	string[] (array)	nullable	URLs images
categories	UUID[] (array)	nullable	Références vers Categories
attributes	JSON	nullable	Champs libres personnalisables (technique)

Relations :

1..N commandes (OrderItem, relation via table intermédiaire)

N..N catégories (Category, table de jointure)

N..N tags (optionnel, table de jointure)

1..N images (stockées ou non dans la table)

0..N reviews (optionnel, module avis/notes)

3. Category (catégorie produit)
Champ	Type	Contraintes	Description
id	UUID (PK)	unique, non nul, auto-généré	Identifiant catégorie
name	string(100)	non nul, unique, index	Nom catégorie
parent_id	UUID (FK)	nullable	Catégorie parente (hiérarchie)
slug	string(100)	unique, non nul	URL unique
description	text	nullable	Description
created_at	datetime	non nul, default now	
updated_at	datetime	non nul, default now, auto	

Relations :

1..N produits (Product)

0..N sous-catégories (auto-relation)

4. Order (commande)
Champ	Type	Contraintes	Description
id	UUID (PK)	unique, non nul, auto-généré	Identifiant commande
user_id	UUID (FK)	non nul, index	Acheteur
created_at	datetime	non nul, default now	Date création
updated_at	datetime	non nul, default now, auto	
status	enum	[pending, paid, shipped, canceled, refunded]	Statut
total_amount	decimal(10,2)	non nul, >=0	Montant total
payment_method	string(50)	non nul	(stripe, paypal, etc.)
paid_at	datetime	nullable	Date paiement
shipped_at	datetime	nullable	Date expédition
cancelled_at	datetime	nullable	Date annulation
shipping_address	JSON	non nul	Adresse expédition
billing_address	JSON	nullable	Adresse facturation
note	text	nullable	Message client/infos spécifiques

Relations :

1 user (User)

1..N OrderItem (voir table ci-dessous)

5. OrderItem (détail commande, table intermédiaire)
Champ	Type	Contraintes	Description
id	UUID (PK)	unique, non nul, auto-généré	
order_id	UUID (FK)	non nul, index	Commande associée
product_id	UUID (FK)	non nul, index	Produit commandé
title	string(255)	non nul	Copie titre produit au moment de l’achat
price	decimal(10,2)	non nul	Prix unité
quantity	int	non nul, >=1	Quantité commandée
variant	JSON	nullable	Variante sélectionnée (taille, couleur…)

6. Cart (panier)
Champ	Type	Contraintes	Description
id	UUID (PK)	unique, non nul, auto-généré	Identifiant panier
user_id	UUID (FK)	nullable	Si connecté
session_id	string(64)	nullable	Si anonyme
created_at	datetime	non nul, default now	
updated_at	datetime	non nul, default now, auto	

Relations :

0..N CartItem

CartItem (détail panier, table imbriquée)
Champ	Type	Contraintes	Description
id	UUID (PK)	unique, non nul, auto-généré	
cart_id	UUID (FK)	non nul, index	Panier
product_id	UUID (FK)	non nul, index	Produit
quantity	int	non nul, >=1	Quantité
variant	JSON	nullable	Variante sélectionnée

7. Page / Article (CMS Page)
Champ	Type	Contraintes	Description
id	UUID (PK)	unique, non nul, auto-généré	Identifiant page/article
title	string(255)	non nul, index	Titre
slug	string(255)	non nul, unique	URL SEO
content	text / MDX	non nul	Contenu principal
status	enum	[draft, published, archived]	Statut
created_at	datetime	non nul, default now	
updated_at	datetime	non nul, default now, auto	
author_id	UUID (FK)	non nul, index	Auteur (User)

8. SupportMessage (support/messagerie)
Champ	Type	Contraintes	Description
id	UUID (PK)	unique, non nul, auto-généré	
user_id	UUID (FK)	non nul, index	Auteur message
subject	string(255)	non nul	Objet
message	text	non nul	Message
status	enum	[open, closed, pending]	Statut traitement
created_at	datetime	non nul, default now	
updated_at	datetime	non nul, default now, auto	
admin_response	text	nullable	Réponse admin
closed_at	datetime	nullable	Date clôture

9. Notification
Champ	Type	Contraintes	Description
id	UUID (PK)	unique, non nul, auto-généré	
user_id	UUID (FK)	non nul, index	Destinataire
type	enum	[system, order, support, promo]	Type de notif
message	text	non nul	Contenu notif
created_at	datetime	non nul, default now	
is_read	boolean	non nul, default false	Statut lu/non-lu

10. AuditAccessibility (optionnel, score RGAA)
Champ	Type	Contraintes	Description
id	UUID (PK)	unique, non nul, auto-généré	
score	int	non nul	Score RGAA calculé
checklist	JSON	non nul	Liste critères (conforme, non conforme, NA)
recommandations	text	nullable	Suggestions
created_at	datetime	non nul, default now	
user_id	UUID (FK)	nullable	Lié à un user/admin
page_id	UUID (FK)	nullable	Lié à une page

11. Lang (gestion des langues/i18n)
Champ	Type	Contraintes	Description
code	string(5)	unique, non nul	Code langue (fr, en, es…)
name	string(50)	non nul	Nom affiché
is_active	boolean	non nul, default true	Langue activée ou non
translations	JSON	non nul	Table clé/valeur
updated_at	datetime	non nul, default now, auto	

12. Optionnels (extensions, futures features)
Review (Avis produit) : table pour avis/rating

Promo (Coupon/Voucher) : table pour code promo

Log/Activity : pour l’audit, traçabilité, RGPD

Règles/Contraintes globales
UUID pour toutes les PK

Index sur tous les champs de recherche, clés étrangères, slugs

Relations claires, pas de data redondante inutile

Champs nullable uniquement si le use-case l’exige (ex : réponse admin, billing_address)

Vérification data au niveau Prisma/Supabase ET front (Next.js)
