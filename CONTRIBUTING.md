# Guide de contribution
Bienvenue dans l'aventure [entreprise] ! Nous sommes ravis que vous souhaitiez apporter votre pierre à l'édifice et contribuer à notre projet. 
Que vous soyez un développeur chevronné ou que vous souhaitiez simplement vous impliquer, votre aide est précieuse.  

[Solution-Front] n'est pas seulement un outil ; c'est une solution qui [Description-application-web]. 
En rejoignant notre équipe, vous participez à une mission qui vise à [Objectif-solution-web].  

Pour vous aider à démarrer, nous avons rassemblé quelques lignes directrices. Ces conseils vous permettront de naviguer facilement dans notre projet, de comprendre nos attentes et de vous intégrer rapidement dans notre équipe.  

## Structure des branches principales

Notre projet utilise la structure de branches suivante :
| Nom de la branche | Description |
|--|--|
| `main` | Branche de production. Contient le code stable et déployé en production. |
| `release` | Branche de pré-production. Utilisée pour les tests finaux avant le déploiement en production. |
| `dev` | Branche de développement principale. Toutes les fonctionnalités complétées sont fusionnées ici pour les tests. |
| `feature/*` | Branches pour le développement de nouvelles fonctionnalités. |
| `fix/*` | Branches pour les corrections de bugs. |

Workflow typique :
1. Créez une branche `feature/` ou `fix/` à partir de `dev`
2. Développez et testez votre code
3. Fusionnez dans `dev` via une Pull Request
4. Une fois testé en `dev`, fusionnez dans `release` pour les tests finaux
5. Après validation en pré-production, fusionnez dans `main` pour le déploiement en production

## Comment contribuer

1. Cloner le projet
    ```bash
    git clone https://github.com/[repertoire]/[projet].git
    ```
2. Assurez-vous d'être sur la branche dev et qu'elle est à jour :
    ```bash
    git checkout dev
    git pull origin dev
    ```
3. Créez votre branche de fonctionnalité à partir de dev :
    ```bash
    git checkout -b feature/AmazingFeature
    ```
4. Faites vos modifications
5. Ajoutez vos changements à l'index :
    ```bash
    git add .
    ```
    (Utilisez `git add <fichier>` pour des fichiers spécifiques si nécessaire)
6. Committez vos changements :
    ```bash
    git commit -m "type(scope): subject" -m "body"
    ```
    exemple:
    ```bash
    git commit -m "feat(auth): add user authentication system" -m "Implement JWT-based authentication for enhanced security. This includes: 
    - Login and logout functionality
    - Password hashing
    - Token generation and validation"
    ```
7. Push vers votre branche :
    ```bash
    git push origin feature/AmazingFeature
    ```
8. Ouvrez une Pull Request vers la branche `dev` du dépôt principal

Note : Assurez-vous de toujours créer vos branches de fonctionnalité à partir de la branche `dev` la plus récente pour éviter les conflits potentiels avec la branche `main`. Si besoin faite un [rebase avec vscode](https://tutoandco.colas-delmas.fr/developpement/git-rebase-branche-onto-master-vscode/), s'il y a eu plusieurs changement dont vous avez besoin.

## [Convention de nommage des branches](https://articles.merapar.com/hello-serverless-goodbye-git-flow)

| Préfix du nom de la branche | Description |
|--|--|
| `feature/` | Pour les nouvelles fonctionnalités |
| `fix/` | Pour les corrections de bugs |
| `docs/` | Pour les mises à jour de la documentation |
| `refactor/` | Pour les refactorisations de code |
| `test/` | Pour l'ajout ou la modification de tests |
| `release/` | Pour préparer une nouvelle version, généralement utilisé pour effectuer des tâches telles que les dernières retouches et la révision. |
| `core/` | Pour les modifications du projet : <br>- Fonctionnalités fondamentales  <br>- Architecture de base <br>- Bibliothèques essentielles <br>- Performances globales <br>- Sécurité fondamentale <br>- Gestion des états globaux <br>- Routage principal <br>- Systèmes d'authentification <br>- API interne <br>- Configuration globale <br>- etc. |

Exemple : `feature/add-login-page`

![Diférents git flow](https://lh6.googleusercontent.com/84lJ6kTGiNVqXzj8smqNuAUdPwrtJ9bhfd0U4G6j1FzjCvFd_GR6DloF9plo3LfOaO3Z4qLkj4FMtU4IEGEI8M5SX4oFq8vobEH5oNa7xtH5aMoDqG4IgUxOR1Zf24xHg7Tejtgo)

## [Convention de nommage des commits](https://arunkumarvallal.medium.com/become-a-pro-at-commit-messages-using-commitlint-56dab86333b3)

Nous suivons la convention "Conventional Commits" :
```
<type>[optional scope]: <description>

[optional body]

[optional footer]
```

| Types de commits courants | Description |
|--|--|
| `feat` | Nouvelle fonctionnalité |
| `fix` | Correction de bug |
| `docs` | Modification de la documentation |
| `style` | Changement de style (formatage, etc.) |
| `refactor` | Refactorisation du code |
| `test` | Ajout ou modification de tests |
| `perf` | Changement de code qui améliore les performances |
| `chore` | Changements aux processus de build ou aux outils auxiliaires et bibliothèques telles que la génération de documentation |
| `ci` | Changements à nos fichiers et scripts de configuration CI (Intégration Continue) |
| `revert` | Annulation d'un précédent commit |
| `config` | Changement dans les fichiers de configuration |
| `security` | Correction d'une vulnérabilité de sécurité |
| `i18n` | Internationalisation et localisation |
| `remove` | Suppression de code ou de fichiers |
| `deprecate` | Dépréciation de fonctionnalités existantes |

Exemple : `feat: add user authentication system`

![](https://miro.medium.com/v2/resize:fit:750/format:webp/1*naLIcn5hr9OiBwmopSLucQ.png)

## Règles de linting et de formatage

Nous utilisons ESLint (`.eslintrc.js`) et Prettier (`.prettier.json`) pour maintenir la cohérence et la qualité du code. Voici les principales règles à suivre :

| Catégorie | Règle | Configuration |
|-------------|-------------|-------------|
| __Indentation__ | 2 espaces | Défini par Prettier |
| __Virgules finales__ | Pas de virgule finale dans les listes multilignes | ESLint : `"comma-dangle": ["error", "never"]`<br/> Prettier : `"trailingComma": "none"` |
| __Guillemets__ | Préférer les guillemets doubles | Défini par Prettier |
| __Espaces en fin de ligne__ | Aucun espace en fin de ligne | Géré automatiquement par Prettier |
| __Longueur des lignes__ | Maximum (généralement 80 ou 100 caractères) | Géré par Prettier |

Notre configuration étend les règles recommandées pour Vue 3, TypeScript, et Prettier :
- "plugin:vue/vue3-essential"
- "eslint:recommended"
- "@vue/eslint-config-typescript"
- "@vue/eslint-config-prettier"

Pour vérifier votre code :
```bash
npm run lint:check
```

Pour corriger automatiquement les problèmes de linting :
```bash
npm run lint
```

Assurez-vous que votre code passe le linting avant de soumettre une Pull Request.

## [Style de code TypeScript](https://ts.dev/style/#syntax)

### identificateurs
Les identificateurs ne doivent utiliser que des lettres ASCII, des chiffres, des traits de soulignement (pour les constantes et les noms de méthodes de test structurées) et le signe "__\$__".
Ainsi, chaque nom d'identificateur valide est associé à l'expression régulière __`[$\w]+`__.

|   Style   |   Category    |
|--|--|
|   __`UpperCamelCase`__  |   class / interface / type / enum / decorator / type / parameters     |
|   __`lowerCamelCase`__  |   variable / parameter / function / method / property / module alias  |
|   __`CONSTANT_CASE`__   |   global constant values, including enum values   |
|   __`#ident`__          |   private identifiers are never used.     |

Abréviations : Traitez les abréviations comme les acronymes dans les noms comme des mots entiers, c'est-à-dire utilisez loadHttpUrl, et non loadHTTPURL, sauf si le nom d'une plate-forme l'exige (par exemple XMLHttpRequest).

Le signe du dollar : Les identificateurs ne doivent généralement pas utiliser le signe `$`, sauf pour s'aligner sur les conventions de nommage des frameworks tiers. [Voir ci-dessous](https://ts.dev/style/#naming-style) pour plus d'informations sur l'utilisation de $ avec des valeurs __`Observable `__.

### [Style de nommage](https://testing.googleblog.com/2017/10/code-health-identifiernamingpostforworl.html)
TypeScript exprime les informations dans les types, les noms ne doivent donc pas être décorés avec des informations qui sont incluses dans le type.

Il est facile de se laisser emporter par la création de longs identificateurs.   
Les noms plus longs rendent souvent les choses plus lisibles. Mais des noms trop longs peuvent nuire à la lisibilité.  

Les noms doivent être clairs (savoir à quoi ils se réfèrent) et précis (savoir à quoi ils ne se réfèrent pas). Voici quelques lignes directrices pour vous aider :
- __Omettre les mots qui sont évidents compte tenu de la déclaration de type d'une variable.__
    ```typescript
    // Mauvais, le type nous indique la nature de ces variables :
    String nameString;
    List<datetime> holidayDateList;
    // Meilleur:
    String name; 
    List<datetime> holidays;
    ```
- __Omettre les détails non pertinents.__
    ```ts
    // Mauvais, les noms trop spécifiques sont difficiles à lire :
    Monster finalBattleMostDangerousBossMonster;
    Payments nonTypicalMonthlyPayments;
    // Meilleur:
    Monster boss;
    Payments payments;
    ```
- __Omettre les mots qui ressortent clairement du contexte environnant.__
    ```ts
    // Mauvais, la répetition du context:
    class AnnualHolidaySale {int annualSaleRebate; boolean promoteHolidaySale() {...}}
    // Meilleur:
    class AnnualHolidaySale {int rebate; boolean promote() {...}}
    ```
- __N'utilisez pas de caractères de soulignement à la fin ou au début pour les propriétés ou méthodes privées.__
    ```ts
    // Mauvais
    class MyClass {
        private _privateMethod() {}
        private _privateProperty: string;
    }
    // Meilleur
    class MyClass {
        private privateMethod() {}
        private privateProperty: string;
    }
    ```
- __N'utilisez pas le préfixe opt_ pour les paramètres facultatifs.__
    ```ts
    // Mauvais
    function createUser(name: string, opt_age?: number) {}
    // Meilleur
    function createUser(name: string, age?: number) {}
    ```
- __Ne marquez pas spécialement les interfaces (IMyInterface ou MyFooInterface) à moins que cela ne soit idiomatique dans son environnement.__
    ```ts
    // Mauvais
    interface IUserService {}
    // Meilleur
    interface UserService {}
    ```
- __N'utilisez pas d'abréviations ambiguës et n'abrégez pas en supprimant des lettres à l'intérieur d'un mot.__
    ```ts
    // Mauvais
    const usrPrfl = getUserProfile();
    // Meilleur
    const userProfile = getUserProfile();
    ```

### [Imports](https://www.typescriptlang.org/fr/docs/handbook/2/modules.html)
Utilisez les imports pour gérer les dépendances et structurer votre code. Voici les types d'importation courants :
| Type d'import | Exemple	| Utilisation |
|--|--|--|
| Importation complète | `import * as foo from './utils';` | Pour importer tout un module sous un alias. |
| Destructuration | `import { calculateArea } from './geometry';` | Pour importer des fonctions ou des variables spécifiques. |
| Importation par défaut | `import React from 'react';` | Pour importer le module par défaut d'un fichier. |
| Importation sans effet |	`import './styles.css';` | Pour exécuter un fichier sans importer de variables. |

```ts
// Good: choisir entre deux options selon le cas.
import * as ng from "@angular/core";
import { Foo } from "./foo";

// Only when needed: default imports.
import Button from "Button";

// 
import "jasmine";
import "@polymer/paper-button";
```

### [Commentaires & Documentation](https://google.github.io/styleguide/jsguide.html#jsdoc)
Il existe deux types de commentaires :
| Type de commentaire | Forme | Description |
|-------------|-------------|-------------|
| `JSDoc` | `/** ... */` | pour la documentation,<br/> c'est-à-dire les commentaires qu'un utilisateur du code devrait lire. |
| `non-JSDoc` | `// ... ` ou `/* ... */` | pour les commentaires d'implémentation,<br/> c'est-à-dire les commentaires qui ne concernent que l'implémentation du code lui-même. |

En général, suivez [les règles du guide de style JavaScript pour JSDoc, sections 7.1 - 7.5](https://google.github.io/styleguide/jsguide.html#jsdoc). Le reste de cette section décrit les exceptions à ces règles :
- __Omettre les commentaires qui sont redondants avec TypeScript__
    ```ts
    // Par exemple, ne déclarez pas de types dans les blocs @param ou @return, n'écrivez pas @implements, @enum, @private, etc. sur du code qui utilise les mots-clés implements, enum, private, etc.
    ```
- __N'utilisez pas @override dans le code source TypeScript.__
    ```ts
    // @override n'est pas appliqué par le compilateur, ce qui est surprenant et conduit à une désynchronisation des annotations et de l'implémentation. L'inclure uniquement à des fins de documentation est source de confusion.
    ```

Voici quelques lignes directrices:
1. __Faire des commentaires qui ajoutent réellement de l'information__
    + Évitez les commentaires qui se contentent de répéter le nom et le type du paramètre, par exemple
        ```ts
        /** @param fooBarService The Bar service for the Foo application. */
        ```
    + En raison de cette règle, les lignes @param et @return ne sont nécessaires que lorsqu'elles ajoutent des informations, et peuvent être omises dans le cas contraire.
2. __Utilisez les balises TODO pour marquer le code incomplet ou à revoir uniquement pendant le développement.__
    ```ts
    // TODO: Implémenter la gestion des erreurs
    function fetchData() {
    // ...
    }
    ```
3. __Évitez de laisser du code commenté dans la base de code principale.__
    ```ts
    // Mauvais
    /*
    function oldFunction() {
    // ...
    }
    */
    // Meilleur, Supprimez simplement le code inutilisé
    ```

### [Visibilité ](https://ts.dev/style/#visibility)
La restriction de la visibilité améliore le découplage du code.  
Limitez la visibilité des symboles au maximum.  
Préférez les fonctions non exportées aux méthodes privées.  
> N'utilisez pas le modificateur public sauf pour les propriétés de paramètres non readonly dans les constructeurs.
```ts
// Mauvais
class User {
  public name: string;
  public readonly id: number;

  constructor(public email: string, public readonly age: number) {
    this.name = '';
    this.id = Math.random();
  }

  public getInfo() {
    return `${this.name} (${this.age})`;
  }
}

// Meilleur
class User {
  private name: string = '';
  readonly id: number = Math.random();

  constructor(public email: string, readonly age: number) {}

  getInfo() {
    return `${this.name} (${this.age})`;
  }
}
```

### [Variables](https://www.w3schools.com/js/js_scope.asp)
Utilisez const par défaut pour déclarer des variables.  
Utilisez let uniquement si la variable doit être réassignée.  
> N'utilisez jamais var car sa portée n'est pas celle du bloc mais de fonction.
```ts
// Bon : utilisation de const pour une valeur qui ne change pas
const PI = 3.14159;

// Bon : utilisation de let pour une variable qui sera modifiée
let count = 0;
count++;

// Mauvais : n'utilisez jamais var
var score = 100; // Évitez ceci

// Exemple d'utilisation correcte
function calculateArea(radius: number) {
  const area = PI * radius * radius;
  let message = `L'aire du cercle est `;
  
  if (area > 100) {
    message += "grande";
  } else {
    message += "petite";
  }
  
  return `${message}: ${area}`;
}
```

### [Type de retour](https://ts.dev/style/#return-types)
1. __Spécifiez toujours le type de retour des fonctions.__
    ```ts
    // Bon
    function add(a: number, b: number): number {
    return a + b;
    }

    // À éviter
    function subtract(a: number, b: number) {
    return a - b;
    }
    ```
2. __Utilisez `void` pour les fonctions qui ne retournent rien.__
    ```ts
    function logMessage(message: string): void {
        console.log(message);
    }
    ```
3. __Pour les fonctions asynchrones, utilisez `Promise<T>`.__
    ```ts
    async function fetchUser(id: number): Promise<User> {
        const response = await fetch(`/api/users/${id}`);
        return response.json();
    }
    ```
4. __Utilisez des types d'union pour les fonctions qui peuvent retourner différents types.__
    ```ts
    function getLength(value: string | any[]): number {
        return value.length;
    }
    ```
5. __Utilisez des types génériques pour les fonctions qui travaillent avec différents types.__
    ```ts
    function identity<T>(arg: T): T {
        return arg;
    }   
    ```
6. __Pour les fonctions qui retournent des objets, spécifiez le type de retour complet.__
    ```ts
    function createUser(name: string, age: number): { name: string; age: number } {
        return { name, age };
    }
    ```
7. __Pour les fonctions qui peuvent retourner `undefined`, incluez-le dans le type de retour.__
    ```ts
    function findUser(id: number): User | undefined {
        // ...
    }
    ```
8. __Utilisez `unknown` pour les retours de type inconnu, forçant ainsi une vérification de type et rendant le code plus sûr et explicite.__
    ```ts
    function parseJSON(jsonString: string): unknown {
        return JSON.parse(jsonString);
    }
    ```
Il y a deux avantages à taper explicitement les valeurs de retour implicites des fonctions et des méthodes :
- Une documentation plus précise du code.
- Détecter plus rapidement les erreurs de type potentielles dans le futur si des changements de code modifient le type de retour de la fonction.

### [Imports](https://ts.dev/style/#imports)
Utilisez les imports pour gérer les dépendances et structurer votre code. Voici les types d'importation courants :
| Type d'import | Exemple | Utilisation |
|-------------|-------------|-------------|
| __Importation complète__ | `import * as utils from './utils';` | Pour importer tout un module sous un alias. |
| __Destructuration__ | `import { calculateArea } from './geometry';` | Pour importer des fonctions ou des variables spécifiques. |
| __Importation par défaut__ | `import React from 'react';` | Pour importer le module par défaut d'un fichier. |
| __Importation sans effet__ | `import './styles.css';` | Pour exécuter un fichier sans importer de variables. |
| __Importation combinée__ | `import React, { useState } from 'react';` | Pour importer le module par défaut et des éléments spécifiques. |

```ts
// Meilleur : importation de fonctions spécifiques
import { calculateArea, calculatePerimeter } from './geometry';

// Bon : importation complète d'un module
import * as utils from './utils';

// Bon : importation par défaut
import React from 'react';

// Mauvais : évitez d'utiliser des imports sans effet
import 'some-library'; // Utilisez ceci uniquement si nécessaire
```

## Style de code
| Catégorie | Règle | Détails |
|-------------|-------------|-------------|
| __Taille du code__ | Méthodes	 | Maximum 50 lignes |
|  | Fichiers | Maximum 250 lignes |
|  | Longueur des lignes | Maximum 80 caractères (passer à la ligne si nécessaire) |
| __Nommage__ | Méthodes | Commencer par un verbe |
|  | Langue | Anglais uniquement (pas de français ou franglais) |
|  | Variables et fonctions | Utiliser des noms descriptifs |
| __Conventions__ | Style Vue.js | Suivez les [conventions officielles Vuejs.js](https://fr.vuejs.org/style-guide/) |
|  | Style du projet | Respecter les conventions existantes dans le projet |
| __Documentation__	 | Commentaires | Ajouter des commentaires clairs et concis pour expliquer le code |

## Tests

- Assurez-vous que tous les tests passent avant de soumettre une Pull Request
- Ajoutez de nouveaux tests pour les nouvelles fonctionnalités

## Documentation
| Document | Éléments à Mettre à Jour | Détails |
|-------------|-------------|-------------|
| `README.md` | __Description du Projet__ | Présentez une vue d'ensemble du projet. |
|  | __Instructions d'Installation__ | Étapes pour installer et configurer le projet. |
|  | __Lancement en Mode Développement__ | Indications pour démarrer l'application en mode dev. |
|  | __Construction pour la Production__ | Procédure pour construire l'application pour la production. |
| `CONTRIBUTING.md	` | __Règles de Contribution__ | Directives sur la manière de contribuer au projet. |
|  | __Conventions de Code__ | Normes à suivre lors de l'écriture du code. |
|  | __Processus de Soumission des Pull Requests__ | Étapes à suivre pour soumettre des modifications. |

## Processus de revue

- Les Pull Requests seront examinées par les responsables, tech lead ou développeurs senior.
- Des modifications peuvent être demandées avant l'acceptation
- Soyez ouvert aux feedbacks et aux suggestions d'amélioration ( [ref. Programmation sans ego](https://fr.wikipedia.org/wiki/Programmation_sans_ego) )

## Principes d'humilité et de croissance pour une revue de code efficace
| Principe | Description |
|-------------|-------------|
| __1. Accepter ses erreurs et apprendre d'elles__ | Reconnaître que tout le monde fait des erreurs et les voir comme des opportunités d'apprentissage. |
| __2. Être ouvert aux critiques et suggestions__ | Accueillir les retours constructifs avec ouverture d'esprit et ne pas les prendre personnellement. |
| __3. Partager ses connaissances__ | Être disposé à aider et enseigner aux autres, sans garder ses connaissances pour soi. |
| __4. Privilégier la simplicité__ | Écrire du code clair et simple, se concentrer sur la résolution efficace des problèmes. |
| __5. Collaborer efficacement__ | Valoriser le travail d'équipe et la communication, apprendre des autres quel que soit leur niveau. |
| __6. Rester humble__ | Reconnaître qu'il y a toujours plus à apprendre et ne pas se considérer comme supérieur aux autres. |
| __7. Se concentrer sur la valeur apportée__ | Mettre l'accent sur la création de valeur pour les utilisateurs et l'entreprise plutôt que sur la reconnaissance personnelle. |
| __8. Pratiquer l'empathie__ | Comprendre les perspectives des autres membres de l'équipe et aider les débutants à progresser. |
| __9. Pratiquer l'auto-réflexion__ | Évaluer régulièrement ses pratiques de codage et chercher des moyens de s'améliorer. |
| __10. Respecter le temps et les efforts des autres__ | Fournir des commentaires en temps opportun et préparer son code pour faciliter la revue. |
| __11. Maintenir une perspective équilibrée__ | Reconnaître les points forts et les domaines d'amélioration dans le code examiné. |
| __12. Encourager l'innovation__ | Être ouvert aux nouvelles idées tout en respectant les standards existants. |

## Signalement de bugs
| Plateformes de signalement | Informations à inclure |
|--|--|
| <li>[Trello](https://trello.com/) <li>[DevOps](https://dev.azure.com/[Repertoire]/[Projet]) | <li>Étapes pour reproduire le bug <li>Comportement attendu <li>Comportement observé <li>Autres détails pertinents |

Merci pour votre contribution !