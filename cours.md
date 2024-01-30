index = optimiser les opérations de lecture de la bdd
mongodb = est un système de base de données orienté documents et cross-plateform  
bdd = conteneur physique des collections  
Groupe de document en mongodb -> équivalent d'une table en sql  
les docs présent dans la même collections peuvent avoir des champs différents  
un document est un ensemble de clé-valeur dynamique (crédits de l'info : Quentin)  


# Termes SQL en MongoDB
Bdd / Bdd  
Table / Collection  
Tuple, Ligne, Row / Document  
Colonne / Field  
Jointure / Documents imbriqués  
Clé primaire / Clé primaire*  
Mysql / mongod  
mysql / mongo  

# Installation : Atlas
- MongoDB ATLAS
- Permet de gérer des clusters
- Se charge de maintenir et de redéployer la BDD
- Utiliser le fournisseur cloud de votre choix

# Types de données
- booléen
- numérique
- chaine de caractère
- tableau
- objet
- null

# Commandes de base


### Chercher de l'information avec MongoDB

Voici la signature de la methode findOne:

```

db.collection. findOne(
    <filtre>,
    {
        <projection>
    }
)
```


db.users. aggregate(pipeline) .pretty()

# Commande docker
## Pour lancer mongo avec docker
- docker pull mongo # récupère l'image mongo
- docker run -d -p 27017:27017 --name mongo mongo # lance un container mongo
- docker exec -it mongo /bin/bash # se connecte au container mongo
- mongosh # lance le shell mongo

## docker import
- docker run -d -p 27017:27017 --name mongo -v C:\Users\wasso\OneDrive\Desktop\docker:/home mongo
- docker exec -it mongo /bin/bash
- aller dans cd /home/
- mongoimport --db=sample_db --collection=Motor_Vehicle_Collisions --type=csv --headerline --file="Motor_Vehicle_Collisions_-_Crashes_20240130.csv"

## Explication des options
- --type: precise le type de fichier, par defaut json
- -d: nom de la base de données
- -c/ -- collection: nom de la collection
- --headerline: indique que la premiere ligne du fichier est le header
- --drop: supprime la collection avant d'importer les données