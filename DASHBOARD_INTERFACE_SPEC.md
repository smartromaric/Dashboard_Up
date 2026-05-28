# Dashboard UI Spec - UpJunoo

Objectif: une interface moderne, soft, rapide, epuree, orientee action.
Eviter la surcharge visuelle. Montrer seulement ce qui aide la decision.

---

## 1) Principes de design (non negociables)

- Clarte avant decoration.
- Une action principale par ecran.
- Prioriser les chiffres utiles au metier (09:00 briefing).
- Maximum lisibilite avec minimum d'elements.
- Animations discretes et utiles seulement.

---

## 2) Direction visuelle

- Style: minimal, propre, "ops premium", sans bruit.
- Palette:
  - Fond principal: gris tres clair ou bleu-gris tres doux
  - Cartes: blanc (ou dark doux en mode sombre)
  - Couleur accent: bleu sobre
  - Success: vert calme
  - Warning: orange doux
  - Error: rouge desature
- Typographie:
  - Police sans-serif moderne
  - 3 tailles max dans une vue
  - Chiffres KPI en gras, labels discrets
- Icones:
  - Une icone par bloc max
  - Pas d'illustrations lourdes

---

## 3) Architecture ecran (simple et efficace)

## A. Ecran 1 - Morning Brief (page d'accueil)

But: repondre en moins de 10 secondes a "ou en est l'activite ?"

Sections:
- Header compact:
  - Titre
  - Date/heure de derniere maj
  - Bouton "Actualiser"
- Ligne KPI (4 cartes):
  - Chauffeurs approuves
  - Vehicules approuves
  - Chauffeurs assignes
  - Taux d'approbation
- Tableau partenaires:
  - Partenaire
  - Chauffeurs approuves
  - Vehicules approuves
  - Assignes
  - Statut run (badge)
  - Action "Lancer"
- Bloc alertes:
  - Top 3 anomalies uniquement
  - Lien "Voir tout" vers page detail

## B. Ecran 2 - Ops Live (detail operationnel)

But: supervision des runs en cours

Sections:
- Runs en cours (cards compactes)
- Progression par run (step + temps)
- Flux logs (SSE ou polling rapide)
- Actions:
  - Relancer
  - Arreter (si supporte)
  - Ouvrir detail partenaire

## C. Ecran 3 - Detail Partenaire

But: comprendre rapidement pourquoi un partenaire est en retard

Sections:
- KPI du partenaire (jour/semaine)
- Historique des 10 derniers runs
- Erreurs frequentes
- Derniers enregistrements impactes

---

## 4) Regles UX (fluidite)

- Temps de chargement cible: < 2s sur page principale.
- Skeleton loader simple (pas de spinner agressif).
- Polling intelligent:
  - 2-5s si run actif
  - 30-60s si vue stable
- Auto-pause du refresh onglet inactif.
- Recherche instantanee dans le tableau partenaires.
- Pagination simple si plus de 20 partenaires.

---

## 5) Ce qu'il faut eviter absolument

- Trop de graphiques sur la page d'accueil.
- Multiplication des couleurs fortes.
- Trop de badges, trop de labels techniques.
- Colonnes inutiles dans les tableaux.
- Animations permanentes qui fatiguent l'oeil.
- Popups repetitifs pour des infos mineures.

---

## 6) Composants UI prioritaires

- `KpiCard`
- `PartnerTable`
- `RunStatusBadge`
- `LiveLogPanel`
- `AlertList`
- `TimeRangeFilter`

Chaque composant doit etre reutilisable et leger.

---

## 7) Texte UI (ton)

- Court, direct, operationnel.
- Exemples:
  - "Derniere mise a jour: 08:58"
  - "Aucun run en cours"
  - "1 partenaire en retard"
  - "Run termine avec succes"

Eviter le jargon technique visible par les utilisateurs metier.

---

## 8) Accessibilite et confort

- Contraste AA minimum.
- Cibles cliquables >= 40px.
- Navigation clavier de base.
- Etats vides clairs ("Aucune donnee pour cette periode").
- Mode sombre doux (pas noir pur).

---

## 9) Performance front

- Charger les donnees critiques en priorite.
- Lazy load des sections secondaires.
- Debounce sur recherche et filtres.
- Eviter rerender complet des tableaux.
- Garder les payloads API petits (delta si possible).

---

## 10) Definition de "done" interface

L'interface est consideree "prete" si:

- L'utilisateur trouve les 4 KPI cles en moins de 3 secondes.
- Il peut lancer un run partenaire en 1 clic.
- Il voit clairement l'etat du run sans recharger la page.
- Le tableau principal reste lisible et rapide.
- Aucun element ne donne une impression de surcharge.

---

## Notes de mise a jour

- 2026-04-28: Premiere version de la spec UI (epuree, moderne, orientee ops).

