# Pokemon-API

Le but de cet exercice est de communiquer avec Tyradex, une des pricipales API Pokémon en français.  
Et d'afficher nos Pokémons de manière dynamique dans des cards Bootstrap.

## Comprendre les rôles de fetch, then, return, et catch

### fetch : Récupérer des données

Le rôle de fetch est d'envoyer une requête à un serveur pour récupérer des données.
Par exemple, on peut utiliser fetch pour demander des informations à une API (comme des Pokémon, des films, etc.).

```js
fetch('https://api.example.com/data');
Quand tu utilises fetch, il te retourne une promesse. Une promesse est une façon pour JavaScript de dire :
*"Je vais essayer de récupérer les données, mais ça peut prendre un peu de temps. Quand j'aurai fini, je te dirai ce qui s'est passé."*
```

### then : Que faire une fois que les données sont là

then est une fonction qui permet de dire :
*"Quand j'ai reçu la réponse du serveur, voici ce que je veux faire avec."*

Exemple :

```js
fetch('https://api.example.com/data')
  .then(function(response) {
    console.log(response); // Ici, on affiche la réponse
  });
```

Dans le then, la première chose qu'on fait souvent est de convertir la réponse en JSON, car c'est un format courant pour les données. On utilise alors :

```js
fetch('https://api.example.com/data')
  .then(function(response) {
    return response.json(); // Convertir la réponse en JSON
  });
```

### return : Passer les données à l'étape suivante

Quand tu utilises return dans un then, tu passes les données à l'étape suivante de la promesse.

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
