# Pré requis : les indexes  
Un index est une stucture de données qui stocke un partie des données de la collection. Cela permet d'accélérer les requêtes. Les indexes améliorent aussi les performances des rquete de tru et de regroupement.

Pour créer un indexe :

```
db .< collection>. createIndex({"<champ>": "<type d'index>")
```
Pour lister les indexes d'une collection :
```
db .< collection>. getIndexes ()
```
Pour supprimer un index :

```
db .< collection>.dropIndex({"<champ>": "<type d\'index>"})
```

GEOJson est un format open-source pour representer des donnees geographiques. Il est base sur le format
JSON. Il permet de représenter des points, des lignes, des polygones, des multipoints, des multilignes,
des multipolygones et des géométries géométriques.