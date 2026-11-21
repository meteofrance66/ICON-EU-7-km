# ICON-EU 7 km

Prévisions DWD ICON-EU (grille régulière 0,0625°, 7 km) extraites pour les communes de France métropolitaine et de Corse,
au format départemental commun (contrat v3 : mêmes 33 colonnes qu'AROME).

- Source : DWD Open Data, `icon-eu/grib`, licence CC BY 4.0.
- Échéances : 0 à 120 h (horaires jusqu'à +78 h, puis toutes les 3 h interpolées à l'heure).
- Runs utilisés : 00, 06, 12 et 18 UTC (les seuls publiés à +120 h).
- Planning : toutes les 6 h (`.github/workflows/update-icon-eu.yml`), publication sur la branche `data` (un seul commit).
- Première version : pas de cartes (SVG/PNG/interactives) ; le script d'ICON Global (`ICON-GLOBAL-13-km`) en produit.

Lancement local :

    python -m pip install -r requirements.txt
    python scripts/update_icon_eu.py --output-dir build/national

Les noms de champs, unités et niveaux GRIB sont vérifiés message par message (même contrôle qu'ICON Global) ;
une grille différente de 1377 x 657 points fait échouer le calcul plutôt que de publier des données fausses.
