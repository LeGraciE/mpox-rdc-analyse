# 📓 Journal de bord — Projet Mpox RDC

> Ce fichier sert à Claude (et à toi) pour savoir **où tu en es**.
> À maintenir à jour et à re-téléverser dans le projet à chaque bilan.

---

## 📍 État actuel

-- **Jour en cours :** J2 (terminé)
- **Prochaine étape :** J3 — télécharger la série complète des sitreps + auditer les trous

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

- **J3** —
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

- En-tête **multi-niveaux** dans les tableaux sitrep → à gérer à l'extraction Docling
- Cumuls potentiellement révisés à la baisse → différences négatives possibles
- Sitreps manquants → risque de faux pics dans la courbe

---

## 📌 Comment utiliser ce journal

1. **À chaque séance :** mets à jour « État actuel » + la ligne du jour dans le log.
2. **À chaque bilan (tous les 5 jours) :** remplis le bilan et **re-téléverse ce fichier** dans les documents du projet — les documents d'un projet ne se mettent pas à jour tout seuls depuis les conversations.
3. **En début de séance :** dis à Claude → *« Je suis à J\_, voici où j'en suis. »*
