# Pokemon-API

Le but de cet exercice est de communiquer avec Tyradex, une des pricipales API Pokémon en français.  
Et d'afficher nos Pokémons de manière dynamique dans des cards Bootstrap.

## Comprendre les rôles de fetch, then, return, et catch

### fetch : Récupérer des données

Le rôle de fetch est d'envoyer une **requête** à un serveur pour récupérer des données.
Par exemple, on peut utiliser fetch pour demander des informations à une API (comme des Pokémon, des films, etc.).

```js
fetch('https://api.example.com/data');
```

Quand tu utilises fetch, il te retourne une **promesse**. Une promesse est une façon pour JavaScript de dire :
"_Je vais essayer de récupérer les données, mais ça peut prendre un peu de temps. Quand j'aurai fini, je te dirai ce qui s'est passé._"

### then : Que faire une fois que les données sont là

then est une fonction qui permet de dire :
"_Quand j'ai reçu la réponse du serveur, voici ce que je veux faire avec._"

Exemple :

```js
fetch('https://api.example.com/data')
  .then(function(response) {
    console.log(response); // Ici, on affiche la réponse
  });
```

Dans le then, la première chose qu'on fait souvent est de **convertir** la réponse en JSON, car c'est un format courant pour les données. On utilise alors :

```js
fetch('https://api.example.com/data')
  .then(function(response) {
    return response.json(); // Convertir la réponse en JSON
  });
```

### return : Passer les données à l'étape suivante

Quand tu utilises **return** dans un then, tu passes les données à l'étape suivante de la promesse.

Exemple complet :

```js
fetch('https://api.example.com/data')
  .then(function(response) {
    return response.json(); // Convertir la réponse
  })
  .then(function(data) {
    console.log(data); // Utiliser les données ici
  });
```

### catch : Gérer les erreurs

Si quelque chose se passe mal (par exemple, pas de connexion Internet ou problème avec le serveur), on peut attraper et gérer l'erreur avec catch.

```js
fetch('https://api.example.com/data')
  .then(function(response) {
    return response.json();
  })
  .then(function(data) {
    console.log(data);
  })
  .catch(function(error) {
    console.log('Erreur :', error); // Affiche le problème
  });
```
Le catch est comme une ceinture de sécurité : si tout va bien, il ne fait rien. Mais si ça tourne mal, il attrape l'erreur et empêche le programme de planter.

## TP

### Consignes : Récupérer et afficher les Pokémon de la 1ère génération
Dans cet exercice, vous allez utiliser JavaScript pour récupérer et afficher les Pokémon de la 1ère génération à partir d'une API. Vous apprendrez à manipuler les données pour créer une interface visuelle.

### Étape 1 : Récupérer les données de l'API
Déclarez une URL correspondant à l'API des Pokémon de la 1ère génération :

```js
const url = "https://tyradex.app/api/v1/gen/1";
```

Utilisez la fonction fetch pour récupérer les données. Ajoutez une vérification pour vous assurer que la réponse est correcte :

```js
fetch(url)
  .then(function(response) {
    if (!response.ok) {
      throw new Error("Erreur lors de la récupération des données : " + response.status);
    }
    return response.json();
  });
```

### Étape 2 : Manipuler et afficher les données

1.Parcourez les données retournées par l'API avec la méthode .forEach.
À chaque itération, récupérez les informations importantes pour chaque Pokémon :

 - Numéro
 - Nom (en français)
 - Image (regular)
 - Types

Les Pokémons pouvant avoir deux types, on va les _mapper_

```js
pokemon.types.map(type => type.name).join(", ") // à mettre dans notre variable types
```

2. Créez dynamiquement avec la méthode `createElement` une _card_ Bootstrap pour chaque Pokémon, et la remplir avec les éléments suivants :

 - L'image du Pokémon
 - Un titre qui contient le numéro et le titre
 - Un paragraphe indiquant le(s) type(s)

3. Ajoutez ces cartes avec la méthode `appendChild` dans une section HTML (par exemple, avec une div de classe .pokemon-list).

4. Ajouter du CSS pour rendre le rendu impeccable !

### Script de départ

```js
const url = "https://tyradex.app/api/v1/gen/1";

const mesPokemon = fetch(url);
 
mesPokemon.then(function(response) {

    // stocker la reponse json dans une variable

    // faire un then qui initialise une fonction inclant un forEach pour parcourir l'API
    
    // Extraire les informations nécessaires
     
    // Sélectionner le conteneur HTML principal
     
    // Créer la card
    
    // Ajouter l'image, le titre, les types

    // Ajouter les éléments à la carte

    // Ajouter la carte dans le conteneur principal
     
})
    // Gérer les erreurs
  .catch(function(error) {
    console.error("Erreur :", error);
  });
```
