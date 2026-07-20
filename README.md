# Calepinage placo — Prototype HerculePro

Prototype de calepinage de plaques de plâtre (BA13) : saisie manuelle d'une pièce
et de ses ouvertures, génération automatique des surfaces, du calepinage réel des
murs et du plafond rampant, de l'ossature métallique (NF DTU 25.41) et d'un
quantitatif estimatif.

Application **100 % autonome** : un seul fichier `index.html`, sans dépendance ni
build. Ouvrir le fichier dans un navigateur suffit.

## Fonctionnalités

- Saisie pièce (L × l × H, type de plafond, angle, dimensions plaque, sens de pose)
- Placement des ouvertures par mur (type, dimensions, distance à l'angle, allège)
- Calepinage réel des murs : découpe autour des ouvertures, suppression des bandes
  entièrement dans une ouverture, réemploi des chutes
- Calepinage du plafond rampant par rangées avec stock de chutes partagé murs↔plafond,
  comparaison des orientations
- Ossature NF DTU 25.41 : rails, montants (+ renforts d'ouvertures), fourrures,
  suspentes, cornières périphériques — entraxes paramétrables
- Quantitatif estimatif (plaques, joints, vis, bandes, enduit, ossature)
- Export / import du projet au format `.json`

## Utilisation

Ouvrir `index.html` dans un navigateur, ou servir le dossier :

```bash
python3 -m http.server 8000
# puis http://localhost:8000
```

## Périmètre / limites

MVP volontairement borné : pas d'import de plan (PDF/DWG/BIM), réemploi des chutes
glouton (pas de nesting 2D optimal), pas encore de décalage des joints ni de vue en
plan dessinée du plafond. L'export `.json` est local (pas encore de transfert vers
HerculePro).
