# **<u><mark>JSON (JavaScript Object Notation)</mark></u>**

## *JSON est un format léger d'échange des données*

## *Aventages de JSON :*

- Facile à utiliser et à lire

- Utiliser par 90% des langues de programation, frameworks, et bebliotique

- Supporter API [ Fetch,  AJAX, ... ] 

## *Extension :*

```batch
nom_ficher.json
```

## *Syntax :*

```json
// Syntax N°1
["valeur1", "valeur3", "valeur3"]

// Syntax N°2
{
    "cle1" : valeur1,
    "cle2" : valeur2
}


// Syntax N°3
[
    {
        "cle1" : valeur1,
        "cle2" : valeur2
    },
    {
        "cle3" : valeur3,
        "cle4" : valeur4
    }
]
```

## *Type des données supporter dens JSON:*

```json
// Nomber
    {
        "cle1" : 14 ,
        "cle2" : 2.445
    }

// Chaîne de caractere (string)
    {
        "cle1" : "test"
    }

// Boolean
    {  
        "cle1" : true,
        "cle2" : false
    }

// null
    {
        "cle1" : null,
    }

// Array / liste
    {
       "cle1" : ["valeur1", "valeur2", ...]
    }

// JSON
    {
       "cle1" : {
            "name" : "test",
            "age" : 32,
            "admie" : true
        },
        ....
    }
```

## *Access  Data :*

```js
let person_json = {
    "nom" : "Karim",
    "age" : 22,
    "admie" : true,
    "languages" : ["html", "css", "JavaSript"],
    "adress" : {
        "city" : "Tinghir",
        "code" : 45500,
        "rue" : "Rue M6"
    }
}

// get nom => karim
person_json    ||    person_json 

// get languages => ["html", "css", "JavaSript"]
person_json.languages  ||    person_json["languages"]

// get languages JavaScript
person_json.languages[2]

// rue dans address
person_json.adress.rue    ||    ma_jsonn.adress['rue']
      ma_jsonn_json["adress"]["rue"]
```

## *JSON.stringify()*

```js
// Transformer JSON To chaîne de caractere (String)

let ma_json = {
    "nom" : "Karim",
    "age" : 32,
}

typeof ma_json             // object

JSON.stringify(ma_json)    // '{ "nom" : "Karim", "age" : 32}'

typeof ma_json             // string
```

## *JSON.parse()*

```js
// Transformer une chaîne de caractere (String) En JSON
// La chaîne doit etre une format JSON

let ma_json = '{ "nom" : "Karim", "age" : 32}'

typeof ma_json             // string

JSON.parce(ma_json)
/* 
    {
        "nom" : "Karim",
        "age" : 32
    }
*/

typeof ma_json             // object
```

## Exercice :

```js
const étudiantsJSON = 
'[{ name: "Alice", age: 20, address: "123 rue Principale" },{ name: "Bob", age: 22, address: "456 rue des Ormes" }]';

/* 
    1 - Analyser la chaîne JSON en un tableau d'objets JavaScript
    2 - Ajouter un nouvel étudiant au tableau && Vérifier si le 
        nouvel étudiant existe déjà dans le tableau
    3 - Mettre à jour l'âge de Bob à 23 ans
    4 - Supprimer Alice du tableau
    5 - Convertir le tableau modifié en une chaîne JSON
    6 - Afficher la chaîne JSON finale
*/
```

## Correction de l'exercice :

```js
const étudiantsJSON = 
'[{"name":"Alice","age":20,"address":"123 rue Principale"},{"name":"Bob","age":22,"address":"456 rue des Ormes"}]';
console.log(étudiantsJSON)

// 1 - Analyser la chaîne JSON en un tableau d'objets JavaScript
let tableauÉtudiants = JSON.parse(étudiantsJSON);
console.log(tableauÉtudiants)

// 2 - Ajouter un nouvel étudiant au tableau
const nouvelÉtudiant = {
  name: "Charlie",
  age: 21,
  address: "789 rue des Chênes",
};

// Vérifier si le nouvel étudiant existe déjà dans le tableau
const indexÉtudiantExist = tableauÉtudiants.findIndex(
  (étudiant) => étudiant.name === nouvelÉtudiant.name
);

// Si le nouvel étudiant n'existe pas, l'ajouter au tableau
if (indexÉtudiantExist === -1) {
  tableauÉtudiants.push(nouvelÉtudiant);
} else {
  // Si le nouvel étudiant existe déjà, mettre à jour ses informations
  const étudiantExist = tableauÉtudiants[indexÉtudiantExist];
  étudiantExist.age = nouvelÉtudiant.age;
  étudiantExist.address = nouvelÉtudiant.address;
}
console.log(tableauÉtudiants)

// 3 - Mettre à jour l'âge de Bob à 23 ans
tableauÉtudiants.find((étudiant) => étudiant.name === "Bob").age = 23;
console.log(tableauÉtudiants)

// 4 - Supprimer Alice du tableau
tableauÉtudiants = tableauÉtudiants.filter(
  (étudiant) => étudiant.name !== "Alice"
);
console.log(tableauÉtudiants)

// 5 - Convertir le tableau modifié en une chaîne JSON
const JSONmodifié = JSON.stringify(tableauÉtudiants);

// 6 - Afficher la chaîne JSON finale
console.log(JSONmodifié);
document.write(JSONmodifié);
```

____
