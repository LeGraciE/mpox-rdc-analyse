# Plan de travail opérationnel — Projet phare

> Ce document = le **COMMENT**. Il complète le tracker 20 jours (le **QUAND**).
> À garder ouvert pendant tout le sprint : setup, sources, méthode, standards.

---

## 0. Choix de la maladie — recommandation à jour

| Option | Richesse des données | Actualité | Difficulté | Verdict |
|---|---|---|---|---|
| **Mpox** | ⭐⭐⭐ (série 2024–2026 massive) | Moyenne (urgence levée en jan. 2026) | Faible–moyenne | ✅ **Recommandé** : données riches + un beau point méthodo (retards de notification RDC) |
| **Choléra** | ⭐⭐⭐ (endémique, récurrent) | Faible | Faible | ✅ Le plus **propre** si tu veux un pipeline sans friction |
| **Ebola (Bundibugyo)** | ⭐ (surtout dans des PDF de situation) | ⭐⭐⭐ Très actuel | Élevée | ⚠️ Le plus topique, mais données tabulaires plus dures à obtenir |

**Mon vote : Mpox.** Tu obtiens une série temporelle multi-provinces exploitable *et* un angle d'analyse sophistiqué (les retards de reporting = matière à interprétation). On tranche à **J1**.

---

## 1. Setup technique — à faire à J1 (~1h)

### Structure du repo (à créer en premier)

```
mpox-rdc-analyse/
├── README.md              # ta vitrine — se remplit au fil de l'eau
├── requirements.txt       # dépendances figées (reproductibilité)
├── data/
│   ├── raw/               # données brutes, JAMAIS modifiées
│   └── processed/         # données nettoyées
├── notebooks/
│   ├── 01_exploration.ipynb
│   ├── 02_nettoyage.ipynb
│   └── 03_analyse.ipynb
├── sql/
│   └── schema.sql
├── src/
│   └── extraction.py      # scripts réutilisables (Docling / PDF)
├── maps/                  # cartes exportées (HTML / PNG)
└── dashboard/             # fichier .pbix Power BI
```

> **Règle d'or :** `data/raw/` est sacré. On ne modifie jamais la source brute — on lit, on transforme, on écrit dans `processed/`. C'est ce qui rend une analyse *reproductible*.

### Environnement Python (copier-coller)

```bash
# créer et activer un environnement isolé
python -m venv venv
source venv/bin/activate        # Windows : venv\Scripts\activate

# installer les librairies du projet
pip install pandas numpy geopandas folium matplotlib \
            sqlalchemy psycopg2-binary jupyter \
            camelot-py[cv] docling
pip freeze > requirements.txt   # fige les versions
```

### Git (les 3 commandes vitales)

```bash
git init
git add . && git commit -m "message clair et parlant"
# puis créer le repo sur GitHub et git push
```

> Ajoute un `.gitignore` avec `venv/`, `.ipynb_checkpoints/`, et les gros fichiers de `data/raw/` si nécessaire.

---

## 2. Où trouver les vraies données (liens vérifiés)

| Source | Ce qu'on y prend | Lien |
|---|---|---|
| **HDX — groupe RDC (COD)** | Point de départ : 410 jeux de données RDC | https://data.humdata.org/group/cod |
| **HDX — Limites administratives (COD-AB)** | Fonds de carte provinces (adm1) & zones de santé (adm2) → **indispensable pour tes cartes** | Chercher « COD-AB Democratic Republic Congo administrative boundaries » sur HDX |
| **Africa CDC — page RDC** | Bulletins hebdo (EN + **FR**), briefs | https://africacdc.org/country/congo-democratic-republic-of-the/ |
| **Africa CDC — Mpox** | Contexte, chiffres, roadmap | https://africacdc.org/mpox/ |
| **WHO — rapports de situation Mpox** | PDF multi-pays avec tableaux par pays → **parfait pour t'entraîner à l'extraction PDF (Docling/camelot)** | Chercher « WHO mpox external situation report » |
| **HDX — DHS RDC** | Données démographiques/santé (dénominateurs de population pour calculer des taux) | https://data.humdata.org/dataset/dhs-data-for-democratic-republic-of-the-congo |

> **Astuce pipeline :** les données WHO/Africa CDC arrivent souvent en **PDF**. C'est là que ta compétence **Docling** (déjà dans ton portfolio Ecobank) devient un atout : tu extrais les tableaux du PDF → CSV → PostgreSQL. Boucle bouclée.

---

## 3. Stack technique par tâche

| Tâche | Outil principal | Note |
|---|---|---|
| Extraction PDF | `docling` / `camelot-py` | Docling pour structures complexes, camelot pour tableaux nets |
| Nettoyage / manipulation | `pandas`, `numpy` | Le cœur du réacteur |
| Base de données | `PostgreSQL` + `sqlalchemy` | `psycopg2` comme driver |
| Cartographie statique | `geopandas` + `matplotlib` | Choroplèthes (cas par province) |
| Cartographie interactive | `folium` | Export HTML → intégrable dans GitHub Pages |
| Dashboard | `Power BI` (DAX) | Ton point fort — le clou du spectacle |

---

## 4. Méthode de travail par séance (rendre 1–2h efficaces)

Avec un budget serré, **le pire ennemi = démarrer sans savoir quoi faire**. Donc :

1. **Avant la séance (2 min) :** relis l'objectif du jour dans le tracker. Une seule cible.
2. **Structure Logique → Code → Interprétation :**
   - **Logique** : écris en 2 phrases ce que tu cherches et pourquoi *avant* de coder.
   - **Code** : tu l'écris, tu le fais tourner.
   - **Interprétation** : note en 1–2 phrases ce que le résultat *veut dire*.
3. **Notebooks narrés :** alterne cellules de code et cellules markdown qui expliquent. Un notebook doit se lire comme une histoire, pas comme un dump de code.
4. **Fin de séance (5 min) :** `git commit` avec un message clair + note la prochaine micro-étape. Tu démarreras la séance suivante lancé.

> **Si une séance déborde** (1h prévue, ça prend 2h) : c'est normal. Les bilans tous les 5 jours servent à absorber le glissement. Ne saute pas d'étape pour « rattraper ».

---

## 5. Standards de qualité — ce qui rend un livrable *portfolio-grade*

Un recruteur ne lit pas ton code ligne par ligne. Il regarde si ça **respire le pro**. Checklist :

**README (ta vitrine n°1)**
- [ ] Contexte du projet en 3 phrases (le problème, pourquoi ça compte)
- [ ] Sources de données citées avec liens
- [ ] Méthodologie résumée (les grandes étapes)
- [ ] Résultats clés + **captures d'écran** des cartes et du dashboard
- [ ] Comment reproduire (`pip install -r requirements.txt`, etc.)

**Notebooks**
- [ ] Cellules markdown qui expliquent le raisonnement
- [ ] Pas de cellules mortes / code commenté en vrac
- [ ] Tourne de haut en bas sans erreur

**Cartes**
- [ ] Titre parlant, légende, échelle de couleur lisible, **source citée**

**Dashboard**
- [ ] 3–5 KPIs qui répondent à une vraie question
- [ ] Un titre qui raconte l'histoire, pas « Feuille 1 »
- [ ] Filtres utiles (province, période)

**Article LinkedIn (J20)**
- [ ] L'accroche = le résultat le plus frappant, pas « j'ai fait un projet »
- [ ] 2–3 visuels + lien repo + lien dashboard

---

## 6. Objectifs de compétence par semaine

*« À la fin de la semaine, je sais démontrer que… »*

| Semaine | Compétence à pouvoir démontrer |
|---|---|
| **S1** | Cadrer une question analytique + sourcer/documenter des données publiques + Git de base |
| **S2** | Nettoyer des données réelles « sales » avec Pandas + modéliser et charger dans PostgreSQL + écrire du SQL analytique |
| **S3** | Mener une EDA + produire des visualisations claires + **une carte choroplèthe et une carte interactive** |
| **S4** | Construire un dashboard Power BI avec storytelling + publier et communiquer le projet |

> Si tu coches ces 4 lignes, tu **n'es plus junior**. Tu es un analyste confirmé capable de livrer un projet de données de bout en bout — et tu as les preuves publiques pour l'affirmer.
