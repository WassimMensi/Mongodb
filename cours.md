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

# Commandes
- ajouter : db.someColl.insertOne({"key":"valeur"})
- supprimer une bdd : db.dropDatabase()
- créer une base :  db.createCollection(
"maCollection",  
"collation": {  
"locale": "fr",  
"caseLevel": false,  
"strength": 3,  
"numericOrdering": false,  
"alternate": "non-ignorable",  
"backwards": false,  
"normalization": false  

}  

)

db.collection.updateOne(, )

db.personnes.updateOne(

"nom": "PEYRACHON"

{
$set : { "nom": "BARRAY" }
}
)

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