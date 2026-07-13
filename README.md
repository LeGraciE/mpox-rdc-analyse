# 🦠 Analyse de l'épidémie de Mpox en RDC (2024–2026)

> Pipeline de données complet : **extraction → nettoyage → base de données → analyse → cartographie → dashboard.**

---

## 📌 Contexte

*(À remplir en 3 phrases : le problème, pourquoi ça compte, ce que ce projet apporte.)*
Ex. d'amorce : « En 2024, la RDC a été l'épicentre d'une flambée majeure de Mpox déclarée urgence de santé publique continentale. Ce projet analyse… »

## ❓ Question d'analyse

*(La question précise verrouillée à J1.)*
> Comment l'épidémie de Mpox s'est-elle diffusée dans les provinces de la RDC entre 2024 et 2026, et quelles provinces ont supporté le plus lourd fardeau ?

## 🗂️ Sources de données

- **HDX — groupe RDC (COD)** : https://data.humdata.org/group/cod
- **HDX — limites administratives (COD-AB)** : provinces (adm1) & zones de santé (adm2)
- **Africa CDC — RDC** : https://africacdc.org/country/congo-democratic-republic-of-the/
- **WHO — rapports de situation Mpox** (multi-pays, tableaux par pays)

## 🛠️ Stack technique

- **Python** — Pandas, NumPy, GeoPandas, Folium
- **PostgreSQL** — stockage & requêtes analytiques
- **Power BI** — dashboard final (DAX)

## 📁 Structure du projet

```
├── data/
│   ├── raw/         # données brutes, jamais modifiées
│   └── processed/   # données nettoyées
├── notebooks/       # exploration, nettoyage, analyse
├── sql/             # schéma + requêtes
├── src/             # scripts réutilisables (extraction PDF)
├── maps/            # cartes exportées
└── dashboard/       # fichier Power BI (.pbix)
```

## 🔄 Reproduire l'analyse

```bash
python -m venv venv
source venv/bin/activate        # Windows : venv\Scripts\activate
pip install -r requirements.txt
```

## 📊 Résultats clés

*(À remplir en fin de sprint — insère ici les captures des cartes et du dashboard, + 2-3 enseignements majeurs.)*

## 👤 Auteur

**Isaac Mboyo Ilumbe** — Analyste de données
[LinkedIn](https://linkedin.com/in/isaac-mboyo-ilumbe)
