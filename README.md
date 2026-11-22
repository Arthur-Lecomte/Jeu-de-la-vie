# Jeu de la vie

Le [jeu de la vie de Conway](https://fr.wikipedia.org/wiki/Jeu_de_la_vie)
sur une grille infinie, pensé comme démo pour
[arthurlecomte.fr](https://arthurlecomte.fr) (hébergée sous `/demos/<slug>/`).

- Grille sans bords (stockage creux : seules les cellules vivantes existent).
- Zoom et déplacement libres : molette, glisser, pincement sur mobile.
- Dessin de cellules à la souris ou au doigt, gomme automatique.
- Bibliothèque de 10 patterns classiques (planeur, canon de Gosper, pulsar…).
- Contrôles complets : lecture/pause, pas à pas, vitesse, remplissage
  aléatoire avec densité réglable, recentrage automatique.
- Stats en direct : génération, population, naissances et morts.
- Utilisable au clavier (espace, S, flèches, +/−) ; panneau d'aide intégré.
- Un canon de Gosper tourne dès l'arrivée (en pause si l'utilisateur
  préfère réduire les animations).

Aucune dépendance d'exécution : JavaScript pur + Canvas 2D, Vite pour le
build. Aucune requête externe, pas de cookies ni de `localStorage`.

## Développer

```sh
npm ci
npm run dev       # serveur de développement
npm run build     # fichiers finaux dans dist/
npm run preview   # sert le build pour vérification
```

## Choix techniques (en bref)

- La grille est un `Set` de clés `"x,y"` : simple, suffisant pour des
  dizaines de milliers de cellules à 60 générations/s.
- Le « remplissage aléatoire » sème la zone visible, plafonnée à
  120 × 120 cellules pour rester fluide même très dézoomé.
- Les patterns sont décrits en ASCII art dans `src/patterns.js`.

## Assets et licences

Aucun asset externe : interface en polices système, rendu entièrement
dessiné au canvas. Code sous la licence du repo.

## Les règles à ne pas casser (vérifiées au build du portfolio)

- **Aucune requête vers un autre domaine** : pas de CDN, de police
  distante, d'API, de stats. Tout est embarqué dans le projet.
- Pas de cookies, pas de service worker, pas de formulaire qui envoie
  des données.
- `localStorage` uniquement pour une sauvegarde ou des préférences,
  clés préfixées par le slug.
- Chemins relatifs (`base: './'` dans `vite.config.js` — ne pas retirer).
- Garder le lien « Retour à la fiche du projet » (le slug est ajusté à
  l'intégration).
- Assets (images, sons, polices) : uniquement du libre de droits ou du
  fait maison, licences notées dans ce README.

## Intégrer au portfolio

Projet terminé → ouvrir Claude Code dans le repo du portfolio et lancer
`/nouveau-projet <chemin de ce projet>`. La fiche est créée en
brouillon ; la publication reste une décision manuelle.
