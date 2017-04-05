class: center, middle

# Javascript - TP Q
# Variables et types

---

# Javascript - TP Q

- Objectifs:
    + Consolider connaissances sur variables
    + Pratiquer l'usage des différents types de variables
    + Utilisation de boucles

---

# Programme du TP

- Rappel sur les variables et types
- Mise en pratique (30mn)
- Exercices

---

# Types de variables ?

--

- Simples:
  + booléen (*boolean*): `true`, `false`
  + nombre (*integer/float number*): `999`, `0.12`, `-9.99`
  + chaîne de caractères (*string*): `"bonjour"`, `'coucou'`
  + aucune valeur: `null`

--

- Spéciaux:
  + non défini: `undefined`
  + objet (*object*): `{ prop: 'valeur' }`
  + tableau (*array*): `[ 1, 2, 3 ]`
  + fonction (*function*): `function(){ /* ... */ }`

???

-> Quels types peuvent contenir un objet ou un tableau ?

---

# Quel type ?

1. "bonjour" + 4
1. { a: 0.4 }
1. 0
1. true
1. 2 - 1.2
1. [ 'a', 'b', 'c' ]

--

Le mot clé `typeof` renvoie le type de l'expression qui suit.

--

Attention au dernier !

---

# Variables et opérateur d'affectation

- Toute valeur peut être stockée dans une variable (`var`)
- Les variables sont nommées de manière alphanumérique, sans guillemets
- `=` permet d'affecter une valeur (à droite) à une variable (à gauche)

```js
var maVariable = 'mon texte';
console.log(maVariable); // => affiche: mon texte

maVariable = `mon nouveau texte`;
console.log(maVariable); // => affiche: mon nouveau texte
```

---

# Comparaisons de valeurs

- `==` permet de comparer deux valeurs de manière laxiste
- `===` permet de comparer deux valeurs de manière stricte

```js
1 == '1' // => true
1 === `1` // => false (car types différents)

0 == false // => true
0 === false // => false

null == undefined // => true
null === undefined // => false
```

--

- L'inégalité se vérifie avec `!=` et `!==`, respectivement.
- `<`, `>`, `<=`, `>=` sont aussi des opérateurs de comparaison.
- Ces opérateurs sont utilisés dans les conditions `if`.

---

# Accéder aux propriétés d'un objet

- Un objet associe des valeurs à des propriétés.
- Les valeurs de ces propriétés peuvent être de n'importe quel type.

```js
var obj = {
  maProp1: 'valeur 1', // propriété maProp1 de type string
  maProp2: {           // propriété maProp2 de type object
    maProp3: 4         // propriété maProp3 de type number
  }
};
```

--

- Deux moyens d'accéder aux valeurs d'un objet (et d'un tableau):

```js
// notation pointée
obj.maProp1 // => 'valeur 1'
obj.maProp2.maProp3 // => 4

// notation avec crochets (permet l'utilisation de variables)
obj['maProp1'] // => 'valeur 1'
obj['maProp2']['maProp3'] // => 4
```

---

# Accéder aux valeurs d'un tableau (même principe)

- Un tableau est un objet dont les propriétés sont des nombres entiers appelés **indices** (*index*).
- Tout tableau a une propriété `.length` qui vaut le nombre de ses valeurs.

```js
var tab = [
  'valeur 1', // 1ère valeur (indice=0) de type string
  {           // 2ème valeur (indice=1) de type object
    maProp3: 4
  }
];
```

--

- Accéder aux valeurs d'un tableau:

```js
// notation avec crochets (permet l'utilisation de variables)
tab[0] // => 'valeur 1'
tab[1] // => { maProp3: 4 }
```

- La notation avec crochets `tab[i]` est souvent utilisée dans boucles `for`.

---

# Énumérer les valeurs d'un objet/tableau

- Dans les deux cas, on peut utiliser une boucle `for` pour lister les valeurs.
- Pour un tableau:

```js
for (var i=0; i<tab.length; ++i) {
  console.log(i, tab[i]);
}
```

- Pour un objet:

```js
for (var p in obj) {
  console.log(p, obj[p]);
}
```

---

# Mise en pratique: fonction affiche()

Objectif: définir une fonction `affiche()` qui affiche dans la console le contenu de la valeur passée en paramètre, en fonction de son type.

- Si le paramètre n'est pas défini, afficher `(aucune valeur)`
- Si le paramètre est de type `null`, afficher `(valeur nulle)`
- Si le paramètre est de type `string`, afficher `chaîne: <valeur> (<longueur>)`
- Sinon, afficher `type non supporté pour l'instant`

Tests:

```js
affiche() // => (aucune valeur)
affiche(undefined) // => (aucune valeur)
affiche(null) // => (valeur nulle)
affiche('hey') // => chaîne: hey (3)
affiche(3) // => type non supporté pour l'instant
affiche([1,2,3]) // => type non supporté pour l'instant
affiche({a:1}) // => type non supporté pour l'instant
affiche(function(){}) // => type non supporté pour l'instant
```

---

# Exercice: Compléter la fonction affiche()

Objectif: ajouter le support des objets et tableaux dans notre fonction affiche().

- Si le paramètre est de type `function`, afficher `fonction`
- Si le paramètre est un nombre ou un booléen, afficher `<type>: <valeur>`
- Si le paramètre est de type `object`, afficher `objet:` suivi d'une ligne par propriété:<br/>
    `- <propriété>: <valeur>`

- Si le paramètre est un tableau, afficher `tableau de <longueur> éléments:` suivi d'une ligne par valeur:<br/>
    `- <valeur>`

Tester que la fonction fonctionne bien avec chaque type de valeur.

BONUS: Rendre la fonction récursive, afin d'afficher de manière indentée les objets et tableaux contenus dans d'autres.