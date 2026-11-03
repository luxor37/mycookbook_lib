# Contexte du projet — bibliothèque de recettes

Tu aides à créer des recettes pour cette bibliothèque. Réponds toujours en français, y compris les titres, ingrédients, étapes et explications. Quand on te demande une recette à ajouter, livre du JSON valide, sans commentaire dans le JSON et sans champs supplémentaires.

## Fichiers à produire

Une recette comporte toujours deux fichiers :

1. `recipes/<dossier>/<id>/index.json` : la recette complète.
2. Une entrée correspondante dans `recipes/index.json` : l’index léger.

Correspondance entre le type et le dossier :

| Type dans l’index     | Dossier               |
| --------------------- | --------------------- |
| `AUTRES`              | `autres`              |
| `BOISSONS`            | `boissons`            |
| `DESSERTS`            | `desserts`            |
| `ENTREES`             | `entrees`             |
| `PRODUITS_NETTOYANTS` | `produits_nettoyants` |
| `REPAS`               | `repas`               |

L’`id` est en minuscules ASCII, en kebab-case, sans accent (ex. `poulet-moutarde-erable`). Il est identique dans les deux fichiers.

## Format obligatoire de la recette complète

```json
{
  "id": "poulet-moutarde-erable",
  "title": "Poulet moutarde et érable",
  "portions": "4",
  "time": "45 min",
  "tags": [
    "Alcool:null",
    "Atout:Rapide",
    "Cuisine:Québécoise",
    "Ingrédient:Poulet",
    "Intensité:null",
    "Levure:null",
    "Méthode:Four",
    "Niveau:Facile",
    "Occasion:null",
    "Piquant:null",
    "Plat:null",
    "Protéine:Poulet",
    "Public:null",
    "Régime:Omnivore",
    "Saveur:Sucré-salé",
    "Texture:null",
    "Type:Plat principal",
    "Usage:null",
    "Équipement:Plaque de cuisson"
  ],
  "ingredients": [
    {
      "name": "Poitrines de poulet désossées",
      "quantity": "4",
      "unit": ""
    },
    {
      "name": "Sirop d’érable",
      "quantity": "¼",
      "unit": "tasse"
    },
    {
      "name": "Moutarde de Dijon",
      "quantity": "2",
      "unit": "tbsp"
    }
  ],
  "preparation": [
    "Préchauffer le four à 400 °F.",
    "Déposer le poulet sur une plaque de cuisson.",
    "Mélanger le sirop d’érable et la moutarde, puis en napper le poulet.",
    "Cuire jusqu’à ce que le poulet atteigne une température interne sécuritaire."
  ]
}
```

Règles de structure :

- Toutes les valeurs sont des chaînes de caractères, sauf `tags`, `ingredients` et `preparation`, qui sont des tableaux.
- Chaque ingrédient contient exactement `name`, `quantity` et `unit`. Laisser `quantity` et `unit` à `""` lorsqu’une quantité n’est pas précisée (p. ex. sel et poivre, au goût).
- `preparation` est un tableau d’étapes complètes, dans l’ordre. Ne pas ajouter de champ `instructions`, `steps`, `temperature`, `notes`, `image` ou `category`.
- `portions` et `time` sont du texte, par exemple `"4"`, `"12 biscuits"`, `"500 ml"` et `"1 h 15 min"`.

## Tags

Le tableau `tags` contient toujours ces 19 entrées, dans cet ordre exact :

`Alcool`, `Atout`, `Cuisine`, `Ingrédient`, `Intensité`, `Levure`, `Méthode`, `Niveau`, `Occasion`, `Piquant`, `Plat`, `Protéine`, `Public`, `Régime`, `Saveur`, `Texture`, `Type`, `Usage`, `Équipement`.

Chaque entrée est une seule chaîne sous la forme `Clé:Valeur`. Si une valeur est inconnue ou non pertinente, utiliser exactement `Clé:null`. Ne pas retirer, renommer, réordonner ou dédoubler des tags.

## Index obligatoire

Ajouter cette entrée à `recipes/index.json` dans le groupe de type approprié :

```json
{
  "id": "poulet-moutarde-erable",
  "type": "REPAS",
  "title": "Poulet moutarde et érable"
}
```

## Langue, températures et unités

- Rédiger exclusivement en français. Les abréviations d’unités suivantes sont les exceptions voulues : `tbsp` et `tsp`.
- Exprimer toute température de cuisson en Fahrenheit : `350 °F`, `400 °F`, etc. Ne jamais indiquer de Celsius.
- Privilégier, dans cet ordre, `tasse`, `tbsp` et `tsp`.
- Écrire les fractions avec des caractères Unicode : `¼`, `⅓`, `½`, `⅔`, `¾`, jamais `0.25`, `1/4` ou `.5`.
- Ne jamais employer `oz`, `once` ou `onces`.
- Utiliser `ml` ou `g` seulement quand une tasse ou une cuillère serait imprécise ou inadaptée (p. ex. viande, très petite ou très grande quantité de liquide). Ne pas convertir automatiquement une mesure pratique en métrique.
- Pour les éléments comptables, laisser l’unité vide : œufs, gousses, poitrines, pommes, etc.

## Réponse attendue lors d’une demande de recette

Donner d’abord le chemin du fichier de recette, puis son JSON complet. Donner ensuite l’entrée exacte à ajouter dans `recipes/index.json`. Ne pas inventer de champs et ne pas traduire `tasse`, `tbsp` ou `tsp` vers une autre notation.
