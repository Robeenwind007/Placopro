# PlacoPro — Le calepinage des pros du placo

Logiciel gratuit de calepinage de plaques de plâtre (BA13) par **HerculePro**.
Saisie manuelle d'une pièce et de ses ouvertures, puis génération automatique des
surfaces, du calepinage réel des murs et du plafond, de l'ossature métallique
(NF DTU 25.41) et d'un quantitatif estimatif — avec élévations et plans dessinés.

Application **100 % autonome** : un seul fichier `index.html`, sans dépendance,
sans build, sans serveur. Ouvrir le fichier dans un navigateur suffit.

## Fonctionnalités

**Saisie**
- Pièce : nom, longueur × largeur × hauteur, type de plafond (horizontal / monopente /
  double pente), angle de pente, dimensions de plaque, sens de pose.
- Ouvertures par mur : type (porte / fenêtre / baie / réservation), dimensions,
  distance depuis l'angle gauche, hauteur d'allège.
- Velux par versant de toiture : dimensions, distance depuis le pignon, distance
  depuis l'égout.

**Moteur de calepinage**
- Murs : découpe réelle autour des ouvertures, suppression des bandes entièrement
  dans une ouverture, réemploi des chutes.
- Plafond multi-versants : 1 rampant (monopente), 2 versants (double pente, séparés
  au faîtage), pavage 2D avec découpe des Velux.
- **Stock de chutes partagé** murs ↔ versants : les morceaux récupérés (baie pleine
  hauteur, Velux…) remplacent des plaques neuves.
- Orientation des plaques du plafond **pilotée par la structure porteuse**
  (chevrons / pannes / dalle) — plaques ⊥ fourrures ⊥ structure.

**Ossature — NF DTU 25.41**
- Murs : rails haut/bas, montants à l'entraxe, chevêtre de renfort autour des ouvertures.
- Plafond : fourrures ⊥ structure, suspentes calées sur la structure, cornières de rive,
  éclisses. Entraxes paramétrables (montants, fourrures, suspentes, structure).

**Sorties**
- Élévations dessinées de chaque mur et plans à plat de chaque versant (plaques
  numérotées, découpes cotées, ouvertures et Velux positionnés).
- Quantitatif estimatif : plaques (placement réel + commande sécurité surface+marge),
  chutes, joints, vis, bandes, enduit, rails, montants, fourrures, suspentes, cornières.
- Export / import du projet au format `.json` (pièce, ouvertures, Velux, paramètres).

## Utilisation

Ouvrir `index.html` dans un navigateur, ou servir le dossier :

```bash
python3 -m http.server 8000
# puis http://localhost:8000
```

## Versionnage

La version est affichée dans la barre du haut (`vX.Y.Z`) et stockée dans
`index.html` (`var APP_VERSION`). Un hook git `pre-commit`
(`.git/hooks/pre-commit`, local au dépôt) **incrémente automatiquement le patch à
chaque commit** et re-stage le fichier. Le majeur/mineur se change à la main.

## Périmètre / limites

MVP volontairement borné :
- pas d'import de plan (PDF / DWG / BIM) — saisie manuelle uniquement ;
- réemploi des chutes **glouton** (pas de nesting 2D optimal) ;
- pas encore de décalage des joints entre couches ni de vérification
  « joint ≠ bord d'ouverture » ;
- pas de bascule automatique simple/double ossature ni tableaux hauteur↔entraxe du DTU ;
- l'export `.json` est local (pas encore de transfert vers HerculePro).

## Licence

© HerculePro 2026 (OBE) — tous droits réservés. [www.herculepro.com](https://www.herculepro.com)
