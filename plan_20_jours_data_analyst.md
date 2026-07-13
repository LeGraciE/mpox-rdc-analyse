# Sprint 20 jours — Junior → Confirmé (Data Analyst)

**Objectif final :** un portfolio public solide, construit autour d'**un projet phare complet et publié**.
**Budget temps :** 1–2h/jour (~30h au total).
**Créneau visé :** Data Analyst — Python · SQL · Power BI · **Cartographie** (élément différenciant).

---

## Ce que ce sprint produit réellement

Pas « expert en tout » en 20 jours — ça n'existe pas. Mais à la fin, tu auras :

- **1 projet phare** de bout en bout, dont tu maîtrises chaque maillon → tu passes *junior → confirmé*.
- **5 artefacts publics** : un repo GitHub propre, une analyse Python, une carte interactive, un dashboard Power BI, un article LinkedIn.
- Une **niche visible** (data + santé/humanitaire + cartographie RDC) que peu de gens occupent.

> La suite jusqu'en septembre = projets #2 et #3 pour transformer « confirmé » en « quasi-expert sur ta niche ».

---

## Le projet phare

**Surveillance épidémiologique en RDC** — analyse d'une épidémie (Mpox recommandé ; choléra / rougeole en alternative).
Données : HDX · WHO AFRO · Ministère de la Santé RDC.
Fil rouge : *données brutes → nettoyage → base → analyse → carte → dashboard → récit.*

### Couverture des compétences

| Compétence | Où elle est travaillée |
|---|---|
| **Python (Pandas)** | Extraction, nettoyage, EDA (Semaines 1–3) |
| **SQL / PostgreSQL** | Modélisation + requêtes analytiques (Semaine 2) |
| **Cartographie** | Choroplèthes geopandas + carte folium (Semaine 3) |
| **Power BI / DAX** | Dashboard final (Semaine 4) |

---

## Rituel quotidien

Chaque séance suit **ta** structure de mentor :

1. **Logique** — quel est le raisonnement / la décision méthodo du jour ?
2. **Code** — on l'écrit et on le fait tourner.
3. **Interprétation** — qu'est-ce que ça veut *dire* ? (le « so what »)

**Fin de chaque séance :** un `git commit` propre. Pas de code non versionné.

---

## Semaine 1 — Cadrage & données

- [ ] **J1** — Choisir la maladie + formuler LA question précise. Créer le repo GitHub (structure + README squelette). Poser l'environnement (venv + requirements).
- [ ] **J2** — Trouver et télécharger les données (HDX / WHO AFRO / MoH). Inventaire des sources + documenter la provenance.
- [ ] **J3** — Explorer les données brutes dans un notebook : colonnes, granularité (province / zone de santé), période couverte.
- [ ] **J4** — Récupérer le fond de carte administratif RDC (GeoJSON provinces ou zones de santé). Vérifier la clé de jointure (noms harmonisés).
- [ ] **J5** — 🏁 **Bilan 1.** Nettoyer le dépôt, commit propre, rédiger la section « Contexte & sources » du README.

## Semaine 2 — Nettoyage & base de données

- [ ] **J6** — Nettoyage Pandas : types, dates, valeurs manquantes, harmonisation des noms de provinces.
- [ ] **J7** — Suite : dédoublonnage, agrégations, colonnes calculées (taux, cumuls).
- [ ] **J8** — Modéliser un petit schéma PostgreSQL (table cas + table géographie). Créer les tables.
- [ ] **J9** — Charger les données propres dans PostgreSQL (Python → SQL). Contrôle d'intégrité.
- [ ] **J10** — 🏁 **Bilan 2.** Écrire 5 requêtes SQL analytiques (top provinces, évolution temporelle, létalité). Documenter.

## Semaine 3 — Analyse & cartographie

- [ ] **J11** — EDA Python : courbe épidémique (cas par semaine), tendances générales.
- [ ] **J12** — Analyse comparative : provinces les plus touchées, saisonnalité, taux de létalité.
- [ ] **J13** — Première carte choroplèthe (geopandas) : cas cumulés par province.
- [ ] **J14** — Carte interactive (folium) : popups, échelle de couleur, export HTML. **← ta signature**
- [ ] **J15** — 🏁 **Bilan 3.** 2–3 visualisations finalisées + interprétation écrite (le « so what »).

## Semaine 4 — Dashboard & publication

- [ ] **J16** — Préparer les données pour Power BI (export propre) + modèle de données.
- [ ] **J17** — Construire le dashboard : KPIs, courbe, carte, filtres (mesures DAX).
- [ ] **J18** — Finaliser : mise en forme, storytelling, titres parlants.
- [ ] **J19** — Rédiger le README complet (méthodo, résultats, captures) + publier le dashboard.
- [ ] **J20** — 🚀 **Livraison.** Article LinkedIn qui raconte le projet (lien repo + carte + dashboard). Bilan global du sprint.

---

## Après le 20 juillet → cap septembre

| Bloc | Contenu | Ce que ça ajoute |
|---|---|---|
| **Projet #2** | Analyse marketplace / données commerciales (ton chantier DRC) | Cartographie appliquée + PostGIS |
| **Projet #3** | Un sujet libre qui te tient à cœur | Autonomie totale = signal « confirmé+ » |
| **Approfondissement** | SQL avancé (fenêtrage), DAX avancé, un point de statistique par semaine | Profondeur technique |

**Règle d'or jusqu'en septembre :** tout ce que tu apprends doit finir *visible* quelque part (repo, dashboard, post). Ce qui n'est pas publié n'existe pas pour un recruteur.

---

## Checkpoints — à remplir aux bilans

| Bilan | Date | Ce qui est fait | Ce qui a coincé | Ajustement |
|---|---|---|---|---|
| Bilan 1 (J5) | | | | |
| Bilan 2 (J10) | | | | |
| Bilan 3 (J15) | | | | |
| Bilan final (J20) | | | | |
