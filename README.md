# CinéScope

## Groupe
- Maël Roustit
- Camille Forestier

## Installation du projet
- Cloner le dépôt avec `git clone`.
- Se placer à la racine du projet et installer les dépendances avec `npm install`.
- Lancer le projet avec `npm run dev`.

## Tests d'accessibilité

### Constats
Les points corrigés sont les suivants :
- l’action qui ouvre la réservation doit utiliser un élément HTML natif ;
- la fenêtre doit avoir un rôle et un nom accessibles ;
- le focus doit entrer dans la fenêtre à l’ouverture ;
- la fermeture doit être possible au clavier et son bouton doit être nommé ;
- après la fermeture, le focus doit revenir au déclencheur ;
- le contenu derrière la fenêtre ne doit pas participer au parcours pendant son ouverture.

### Corrections apportées
#### Fenêtre de réservation
- Remplacement du faux `div` modal par un vrai élément `<dialog>` ouvert avec `showModal()`.
- Ajout de `aria-labelledby` sur la dialog, relié au titre `h2` (`#booking-title`).
- Au moment de l'ouverture, le focus est placé sur le titre de la dialog (`tabIndex={-1}` + `.focus()`).
- Fonction `handleClose` branchée sur `onClose` qui réinitialise l'état et rend le focus au bouton « Réserver » qui avait ouvert la dialog (mémorisé avec `useRef`).
- Fermeture possible au clavier avec la touche Échap, gérée nativement par `<dialog>`.
- Ouverture pilotée par un `useEffect` sur l'état `selected`.

#### Boutons
- Le `div` « Réserver » est remplacé par un vrai `<button type="button">`, focusable et activable au clavier (Entrée / Espace).
- La croix de fermeture est remplacée par un `<button type="button">` avec `aria-label="Fermer"` (le `×` est masqué aux lecteurs d'écran avec `aria-hidden`).
- Les boutons « Fermer » et « Revenir aux films » ferment la dialog via `dialogRef.current?.close()`.

#### Confirmation de réservation
- Ajout d'un bouton « Confirmer la réservation » dans la dialog.
- À la confirmation, un message de réservation s'affiche et reçoit le focus (`tabIndex={-1}` + `.focus()`) à la fermeture de la dialog.
- À la fermeture simple (croix, « Revenir aux films », Échap), le focus revient sur le bouton « Réserver » d'origine.
