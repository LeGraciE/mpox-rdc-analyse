# 📓 Journal de bord — Projet Mpox RDC

> Ce fichier sert à Claude (et à toi) pour savoir **où tu en es**.
> À maintenir à jour et à re-téléverser dans le projet à chaque bilan.

---

## 📍 État actuel

- **J3** J3 (terminé)
- **Prochaine étape :** audit des trous par dates (code), puis J4 — fond de carte COD-AB + clé de jointure

## 🔒 Décisions verrouillées

| Décision | Choix |
|---|---|
| Maladie | **Mpox** (RDC, période 2024–2026) |
| Question d'analyse | **Option A** — diffusion spatio-temporelle par province + fardeau |
| Stack | Python (Pandas, GeoPandas, Folium) · PostgreSQL · Power BI |
| Repo | `mpox-rdc-analyse` — structure de dossiers créée |
| Différenciant | La **cartographie** |

## 🗒️ Log quotidien

> Format : *fait · ce qui a coincé · prochaine micro-étape*

- **J1** — Cadrage complet : maladie + question + repo GitHub poussé
  (LeGraciE/mpox-rdc-analyse) + venv + requirements.txt.
  Imprévu : venv poussé par erreur → corrigé (git rm --cached + .gitignore). ✅
- **J2** —ources : HDX écarté pour les cas (pas de Mpox RDC par province),
  retenu pour le fond de carte COD-AB. Source validée = sitreps hebdo INSP
  (PDF, ReliefWeb), tableau 1 ligne = 1 province.
  *Ce qui a coincé :* deux fausses pistes avant la bonne (WHO trop agrégé, HDX vide).
  *Prochaine micro-étape :* auditer la continuité de la série de sitreps.

- **J3** — 30 sitreps + 1 présentation de synthèse récoltés et catalogués
  (`catalogue_sitreps.csv`). Tri en 4 séries : hebdo 2024 (n°4/S10, n°9/S17),
  journalière (n°83→119, nov 2024→mars 2025), hebdo 2025 (n°54/71/73),
  présentation PowerPoint (SE29, 28/07/2025).
  *Ce qui a coincé :* nettoyage du catalogue à la source, ligne par ligne
  (numéros vérifiés sur les pages de garde, pas sur les noms de fichiers).
  *Découverte :* l'INSP réutilise des numéros de sitrep (deux n°107 et deux
  n°109 à des dates différentes) → le numéro n'est PAS un identifiant fiable,
  confirmé sur données réelles.
  *Prochaine micro-étape :* auditer les semaines manquantes sur les dates
  (pas sur les numéros, puisqu'ils sont réutilisés).
- **J4** —
- **J5** — 🏁 Bilan 1
- *(…jusqu'à J20)*

## 🏁 Bilans

- **Bilan 1 (J5) — Données :**
- **Bilan 2 (J10) — Base + SQL :**
- **Bilan 3 (J15) — Analyse + cartes :**
- **Bilan final (J20) — Livraison :**

## ⚙️ Points techniques en suspens

> Note ici les trucs à débloquer (ex. installation `geopandas`/`camelot`, connexion PostgreSQL…)

- 4 séries de publication distinctes → 2 profils d'extraction Docling minimum
- Numéros de sitrep réutilisés (107, 109) → clé = date, jamais le numéro
- Colonne `N°` interne change de sens (rang ↔ code province) → inutilisable comme clé
- `ND` ≠ `0` → arbitrer via la colonne `Complétude`
- Cumuls à origines différentes : sitreps depuis 2024 vs présentation SE29 depuis 2025
  → ne jamais différencier deux cumuls sans vérifier leur origine
- Séries journalière et hebdo coexistent début 2025 → risque de double comptage
- Trous : avril→nov 2024 (~7 mois, compensé par cumuls) + rien confirmé après SE29 (juil. 2025)
- Noms de provinces à harmoniser (Maindombe, Kasaï/Kasai) → chantier J4
- Docling devra lire n° et date dans la page de garde, pas dans le nom de fichier

---

## 📌 Comment utiliser ce journal

1. **À chaque séance :** mets à jour « État actuel » + la ligne du jour dans le log.
2. **À chaque bilan (tous les 5 jours) :** remplis le bilan et **re-téléverse ce fichier** dans les documents du projet — les documents d'un projet ne se mettent pas à jour tout seuls depuis les conversations.
3. **En début de séance :** dis à Claude → *« Je suis à J\_, voici où j'en suis. »*
