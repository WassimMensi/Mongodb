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
