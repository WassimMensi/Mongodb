# Exercices sur les index géographiques

## Exercice 1

Vous disposez du code JavaScript suivant qui comporte une fonction de conversion d’une distance exprimée en kilomètres vers des radians ainsi que d’un document dont les coordonnées serviront de centre à notre sphère de recherche. Écrivez la requête qui affichera le nom des salles situées dans un rayon de 60 kilomètres et qui programment du Blues et de la Soul.



```js
var KilometresEnRadians = function(kilometres){ var rayonTerrestreEnKm = 6371;
return kilometres / rayonTerrestreEnKm;
};

var salle = db.salles.findOne({"adresse.ville": "Nîmes"}); 

var requete = {"adresse.localisation": {
    $nearSphere: {
      $geometry: salle.adresse.localisation, $maxDistance: 60000
    }
  },
  "styles": { $all: ["blues", "soul"] }
};
///////////// ou /////////////
var requete = {"adresse.localisation": {
    $geoWithin: {
      $centerSphere: salle.adresse.localisation, KilometresEnRadians(60)
    }
  },
  "styles": { $in: ["blues", "soul"] }
};

db.salles.find(requete, { _id: 0, nom: 1 });

```

## Exercice 2

Écrivez la requête qui permet d’obtenir la ville des salles situées dans un rayon de 100 kilomètres autour de Marseille, triées de la plus proche à la plus lointaine :

```js
var marseille = {"type": "Point", "coordinates": [43.300000, 5.400000]}
db.salles.find({"adresse.localisation": {$nearSphere: {$geometry: marseille, $maxDistance: 100000}}},{ "_id": 0, "adresse.ville": 1 })

```



## Exo 3
Soit un objet GeoJSON de la forme suivante :
Donnez le nom des salles qui résident à l’intérieur.
```js
var polygone = {
  type: "Polygon",
  coordinates: [
    [
      [43.94899, 4.80908],
      [43.95292, 4.80929],
      [43.95174, 4.8056],
      [43.94899, 4.80908],
    ],
  ],
};

db.salles.find({"adresse.localisation": {$geoWithin: {$geometry: polygone}}},{ "_id": 0, "nom": 1 })

```

## Exo 4
Télécharger les jeux d'essais suivants : https://raw.githubusercontent.com/mongodb/docs-assets/geospatial/restaurants.json https://raw.githubusercontent.com/mongodb/docs-assets/geospatial/neighborhoods.json

### Creation d'un index 2dsphere Un index géospatial, et améliore presque toujours les performances des requêtes $geoWithin et $geoIntersects. Comme ces données sont géographiques, créez un index2dsphère sur chaque collection en utilisant le shell mongo :
```
db.restaurants.createIndex({"location": "2dsphere"})
db.neighborhoods.createIndex({"geometry": "2dsphere"})
```

Attention, la création d'un index est OBLIGATOIRE pour permettre l'utilisation des arguments :$geoIntersects, $geoSphere, $geoNear, $geoWithin, $centerSphere, $nearSphere , etc...

Explorez les données, documentez votre démarche et vos résultats dans un fichier geo_exo_suite_suite.md

### Trouvez la commande qui va retourner le restaurant Riviera Caterer... De quel type d'ojet GeoJSON s'agit-il ?
```
db.restaurants.find({name: "Riviera Caterer"})
```
Le restaurant Riviera Caterer est de type "Point".

### Trouvez "Hell's kitchen" au sein de la collection "neighborhoods" et retournez le nom du quartier, sa superficie et sa population. Quelle est la superficie totale de ce quartier ?
```
var requete = db.restaurants.findOne({name: "Hell'S Kitchen"}); 
db.neighborhoods.find({geometry : {$geoIntersects : {$geometry : requete.location}}}, {name:1})
```

### Trouvez la requete type qui permet de recuperer le nom du quartier a partir d'un point donné.
```
var requete = {
    "type": "Point",
    "coordinates": [-73.856077, 40.848447]
}
db.neighborhoods.findOne({geometry : {$geoIntersects : {$geometry : requete}}}, {name:1})
```

### Trouver la requete qui trouve les restaurants dans un rayon donné (8km par exemple)
```
var point = {
    "type": "Point",
    "coordinates": [-73.856078, 40.848448]
}
db.restaurants.find({location : {$nearSphere : {$geometry : point, $maxDistance: 8000}}}, {name:1, location:1})
```