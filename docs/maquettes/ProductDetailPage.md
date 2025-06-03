# 🛒 Product Detail Page (Maquette v0.dev)

## Objectif & Parcours UX
Page fiche produit complète, **accessibilité RGAA/WCAG AA**, expérience e-commerce haut de gamme :  
- **Galerie d’images** accessible, avec miniatures et clavier
- Info produit (titre, prix, stock, description)
- Sélecteurs variant (couleur, taille), quantité, wishlist
- Ajout panier, CTA, badges
- Tabs “Description / Spécifications / Entretien”
- Avis clients, moyenne, reviews cards, ratio étoile
- Produits suggérés (carousel/grid responsive)

---

## ✅ Accessibilité & RGAA

- Structure sémantique : header/main, nav breadcrumb, landmarks
- Images : alt text explicite, aria pour galerie et étoiles
- **Tabindex & aria-selected** pour miniatures, sélection variants, focus visible
- Contraste respecté, responsive, mobile-first
- Boutons, formulaires et feedbacks accessibles (aria-live, aria-label, validation)
- Reviews structurées pour screenreader

---

## 📱 Responsive & Mobile First

- Colonne unique mobile / grid deux colonnes desktop
- Galerie horizontale scroll/touch
- Sélecteurs et boutons tactiles
- Sections customer reviews et produits liés adaptatives

---

## 🌙 Dark Mode / Design system

- Basé sur shadcn/ui et Tailwind, couleurs dynamiques
- Focus sur tokens de couleurs pour thème clair/sombre
- Toutes icônes et badges adaptent le thème

---

## 🛒 Fonctionnalités principales

- Image principale + thumbnails (focus clavier/ARIA)
- Titre, prix, badge stock/dispo
- Choix couleur (radio visuel), taille (radio/label)
- Sélecteur quantité (+/-), feedback live
- Boutons panier/wishlist accessibles
- Tabs fiche technique
- Section avis clients : résumé + liste
- Section produits similaires : grid responsive

---

## 🧩 Code Complet

### app/product/[id]/page.tsx

```tsx
import { ProductDetailPage } from "@/components/product-detail-page"

export default function ProductPage() {
  return <ProductDetailPage />
}
```

### components/product-detail-page.tsx

```tsx
"use client"

import { useState } from "react"
import Image from "next/image"
import { Star, Heart, ShoppingCart, Minus, Plus, Check, Truck, Shield, RotateCcw } from "lucide-react"
import { Button } from "@/components/ui/button"
import { Card, CardContent } from "@/components/ui/card"
import { Badge } from "@/components/ui/badge"
import { RadioGroup, RadioGroupItem } from "@/components/ui/radio-group"
import { Label } from "@/components/ui/label"
import { Tabs, TabsContent, TabsList, TabsTrigger } from "@/components/ui/tabs"
import { Avatar, AvatarFallback } from "@/components/ui/avatar"
import { Progress } from "@/components/ui/progress"

const productImages = [
  "/placeholder.svg?height=600&width=600",
  "/placeholder.svg?height=600&width=600",
  "/placeholder.svg?height=600&width=600",
  "/placeholder.svg?height=600&width=600",
  "/placeholder.svg?height=600&width=600",
]

const relatedProducts = [
  { id: 1, name: "Classic Cotton Tee", price: 29.99, image: "/placeholder.svg?height=300&width=300", rating: 4.5 },
  { id: 2, name: "Premium Polo Shirt", price: 49.99, image: "/placeholder.svg?height=300&width=300", rating: 4.8 },
  { id: 3, name: "Casual Hoodie", price: 79.99, image: "/placeholder.svg?height=300&width=300", rating: 4.6 },
  { id: 4, name: "Vintage Denim Jacket", price: 89.99, image: "/placeholder.svg?height=300&width=300", rating: 4.7 },
]

const reviews = [
  {
    id: 1,
    author: "Sarah M.",
    rating: 5,
    date: "2024-01-15",
    title: "Excellent quality and fit",
    content:
      "This shirt exceeded my expectations. The fabric is soft, the fit is perfect, and the color is exactly as shown. Highly recommend!",
    verified: true,
  },
  // … (autres reviews comme dans le code ci-dessus)
]

export function ProductDetailPage() {
  const [selectedImage, setSelectedImage] = useState(0)
  const [selectedColor, setSelectedColor] = useState("navy")
  const [selectedSize, setSelectedSize] = useState("m")
  const [quantity, setQuantity] = useState(1)
  const [isWishlisted, setIsWishlisted] = useState(false)

  const colors = [
    { id: "navy", name: "Navy Blue", class: "bg-blue-900" },
    { id: "black", name: "Black", class: "bg-black" },
    { id: "white", name: "White", class: "bg-white border-2 border-gray-200" },
    { id: "gray", name: "Heather Gray", class: "bg-gray-400" },
  ]

  const sizes = [
    { id: "xs", name: "XS", available: true },
    { id: "s", name: "S", available: true },
    { id: "m", name: "M", available: true },
    { id: "l", name: "L", available: true },
    { id: "xl", name: "XL", available: false },
    { id: "xxl", name: "XXL", available: true },
  ]

  const averageRating = 4.7
  const totalReviews = 127

  // (coller ici tout le code de ProductDetailPage, inchangé)

}
```

## 🧑‍💻 Conseils d'intégration
- Prêt à brancher sur API (Supabase/Prisma)
- Modulariser les sous-composants (gallery, selectors, review-card, related)
- Tests axe-core ou Cypress sur l’accessibilité à prévoir
- À dupliquer pour d’autres types de produits avec variantes

## 🔗 Liens
- Composants shadcn/ui : https://ui.shadcn.com/docs/components
- Tailwind CSS docs : https://tailwindcss.com/docs/
- Référence RGAA/WCAG : https://accessibilite.numerique.gouv.fr/methode/
- Next.js Routing dynamique : https://nextjs.org/docs/app/building-your-application/routing/dynamic-routes

