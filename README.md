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
- Les `div` structurants ont été remplacés par des éléments HTML natifs (`header`, `nav`, `main`, `section`, `article` et `button`) afin que les technologies d'assistance puissent identifier la structure et le rôle de chaque élément.
- Les boutons de favoris disposent maintenant d'un nom accessible, d'un état `aria-pressed` et d'une infobulle.
- Les mentions « Places disponibles » et « Places indisponibles » accompagnent désormais l'indicateur coloré.
- Les contrôles disposent de libellés explicites et les affiches ont un texte alternatif.
- Un indicateur de focus visible a été ajouté pour la navigation au clavier.
- La sélection d'un film est maintenant possible avec la touche `Tab`, puis `Entrée` ou `Espace`.
TODO
