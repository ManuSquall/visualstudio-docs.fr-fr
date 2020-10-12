---
title: JavaScript
description: Découvrez que vous pouvez utiliser la plupart ou la totalité des aides à la modification standard (extraits de code, IntelliSense, etc.) lorsque vous écrivez du code JavaScript dans l’IDE de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 01/15/2019
ms.technology: vs-javascript
ms.topic: conceptual
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 74dca14c-5071-416f-a92b-d09f95e3dfb8
caps.latest.revision: 1
author: bowdenk7
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e8e4d0e337289e2676dc8eb040ad199ae41a8dbc
ms.sourcegitcommit: a7944c325bedd8efbb244452741864089a02f5db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2020
ms.locfileid: "91947776"
---
# <a name="javascript-in-visual-studio-2017"></a>JavaScript dans Visual Studio 2017

JavaScript est un langage de premier ordre dans Visual Studio. Vous pouvez utiliser la plupart ou toutes les aides standard de modification (extraits de code, IntelliSense, etc.) lorsque vous écrivez du code JavaScript dans l'IDE de Visual Studio. Vous pouvez écrire du code JavaScript pour de nombreux types d'applications et services.

> [!NOTE]
> Nous avons rejoint l’effort de la communauté afin de faire de [MDN Web docs](https://developer.mozilla.org/en-US/) la ressource de développement « One-Stop » du Web, en redirigeant l’ensemble (plus de 500 pages) de la référence de l’API JavaScript de Microsoft de docs.Microsoft.com à ses homologues MDN. Pour plus d’informations, consultez cette [annonce](https://blogs.windows.com/msedgedev/2018/06/26/chakra-docs-mdn-web-docs/).

## <a name="support-for-ecmascript-2015-es6-and-beyond"></a><a name="ES6"></a> Prise en charge d’ECMAScript 2015 (ES6) et ultérieur

Visual Studio prend désormais en charge la syntaxe des mises à jour de langage ECMAScript, par exemple ECMAScript 2015/2016.

### <a name="what-is-ecmascript-2015"></a>En quoi consiste ECMAScript 2015 ?

JavaScript est un langage de programmation en constante évolution, et [TC39](https://www.ecma-international.org/memento/tc39-m.htm) est le comité en charge des mises à jour.
ECMAScript 2015 est une mise à jour du langage JavaScript qui introduit de nouvelles fonctionnalités et de nouveaux éléments de syntaxe pratiques. Pour une présentation approfondie des fonctionnalités d’ES6, consultez [ce site de référence](http://es6-features.org/#Constants).

Outre ECMAScript 2015, Visual Studio prend en charge ECMAScript 2016 et toutes les nouvelles versions d’ECMAScript dès leur publication. Pour suivre TC39 et les dernières modifications apportées à ECMAScript, suivez leur travail sur [GitHub](https://github.com/tc39).

### <a name="transpile-javascript"></a>Transpiler du JavaScript

Le problème qui revient souvent avec JavaScript, c’est que les dernières fonctionnalités du langage ES6+ qui vous aident à être plus productif ne sont pas prises en charge par vos environnements d’exécution (souvent des navigateurs). Vous devez donc soit déterminer les fonctionnalités prises en charge par les navigateurs (ce qui peut être fastidieux), soit trouver un moyen de convertir votre code ES6+ en une version comprise par vos runtimes cibles (en général ES5). La conversion de votre code en une version comprise par le runtime est communément appelée « transpilation ».

L’une des fonctionnalités clés de TypeScript est la possibilité de transpiler du code ES6+ vers ES5 ou ES3. Vous pouvez ainsi écrire du code qui optimise votre productivité et l’exécuter sur n’importe quelle plateforme. Étant donné que JavaScript dans [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] utilise le même service de langage que TypeScript, il peut également tirer parti de la transpilation d’ES6+ vers ES5.

Avant de configurer la transpilation, vous devez comprendre les options de configuration.
TypeScript est configuré par le biais d’un fichier `tsconfig.json`.
En l’absence de ce fichier, certaines valeurs par défaut sont utilisées.
Pour des raisons de compatibilité, ces valeurs sont différentes si seuls sont présents des fichiers JavaScript (et, éventuellement, des fichiers `.d.ts`).
Pour compiler des fichiers JavaScript, vous devez ajouter un fichier `tsconfig.json` et définir explicitement certaines de ces options.

Les paramètres obligatoires pour le fichier tsconfig sont les suivants :

- `allowJs` : cette valeur doit être définie sur `true` pour les fichiers JavaScript à reconnaître. La valeur par défaut est `false`, car TypeScript est compilé en JavaScript, et le compilateur ne doit pas inclure des fichiers qu’il vient de compiler.
- `outDir` : vous devez définir ce paramètre sur un emplacement non inclus dans le projet, afin que les fichiers JavaScript émis ne soient pas détectés, puis inclus dans le projet (voir `exclude`).
- `module` : si vous utilisez des modules, ce paramètre indique au compilateur le format de module que le code émis doit utiliser (par exemple `commonjs` pour Node, ou des outils de bundle comme Browserify).
- `exclude` : ce paramètre indique les dossiers à ne pas inclure dans le projet.
L’emplacement de sortie, ainsi que les dossiers autres que les dossiers de projet tels que `node_modules` ou `temp`, doivent être ajoutés à ce paramètre.
- `enableAutoDiscovery` : ce paramètre permet de détecter et télécharger automatiquement les fichiers de définition, comme indiqué précédemment.
- `compileOnSave` : ce paramètre indique au compilateur s’il doit réexécuter la compilation chaque fois qu’un fichier source est enregistré dans Visual Studio.
- `typeAcquisition` : cet ensemble de paramètres contrôle le comportement de l’acquisition de type automatique (pour plus de détails, consultez [cette section](../ide/javascript-intellisense.md#Auto)).

Pour pouvoir convertir des fichiers JavaScript en modules CommonJS et les placer dans un dossier `./out`, vous pouvez utiliser le fichier `tsconfig.json` suivant :

```json
{
  "compilerOptions": {
    "module": "commonjs",
    "allowJs": true,
    "outDir": "out"
  },
  "exclude": [
    "node_modules",
    "wwwroot",
    "out"
  ],
  "compileOnSave": true,
  "typeAcquisition": {
    "enable": true
  }
}
```

Une fois les paramètres en place, s’il existe un fichier source (`./app.js`) contenant plusieurs fonctionnalités de langage ECMAScript 2015 comme suit :

```js
import {Subscription} from 'rxjs/Subscription';  // ES6 import

class Foo {  // ES6 Class
    sayHi(name) {
        return `Hi ${name}, welcome to Salsa!`;  // ES6 template string
    }
}

export let sqr = x => x * x;  //ES6 export, let, and arrow function
export default Subscription;  //ES6 default export
```

Un fichier ciblant ECMAScript 5 (par défaut) est alors émis vers `./out/app.js`, qui se présente comme suit :

```js
"use strict";
var Subscription_1 = require('rxjs/Subscription');
var Foo = (function () {
    function Foo() {
    }
    Foo.prototype.sayHi = function (name) {
        return "Hi " + name + ", welcome to Salsa!";
    };
    return Foo;
}());
exports.sqr = function (x) { return x * x; };
Object.defineProperty(exports, "__esModule", { value: true });
exports.default = Subscription_1.Subscription;
```

## <a name="better-intellisense"></a>Fonctionnalités IntelliSense améliorées

JavaScript IntelliSense dans [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] affiche désormais beaucoup plus d’informations sur les listes de paramètres et de membres. Ces nouvelles informations sont fournies par le service de langage TypeScript, qui utilise l’analyse statique en arrière-plan pour mieux comprendre votre code. Vous trouverez plus d’informations sur la nouvelle expérience IntelliSense et son fonctionnement [ici](../ide/javascript-intellisense.md).

## <a name="jsx-syntax-support"></a><a name="JSX"></a> Prise en charge de la syntaxe JSX

JavaScript dans [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] offre une prise en charge étendue de la syntaxe JSX. JSX est un ensemble de syntaxes qui autorise les balises HTML dans les fichiers JavaScript.

L’illustration suivante montre un composant React défini dans le fichier TypeScript `comps.tsx`, puis utilisé à partir du fichier `app.jsx`, où il est possible de recourir à IntelliSense pour les saisies semi-automatiques et la documentation dans les expressions JSX.
Vous n’avez pas besoin de TypeScript ici ; il se trouve simplement que cet exemple contient également du code TypeScript.

![Syntaxe JSX](../javascript/media/js-react.png)

> [!NOTE]
> Pour convertir la syntaxe JSX en appels React, vous devez ajouter le paramètre `"jsx": "react"` à `compilerOptions` dans le fichier `tsconfig.json`.

Le fichier JavaScript créé à l’emplacement « ./out/app.js » au moment de la génération doit contenir le code :

```js
"use strict";
var comps_1 = require('./comps');
var x = React.createElement(comps_1.RepoDisplay, {description: "test"});
```

## <a name="configure-your-javascript-project"></a>Configurer votre projet JavaScript

Le service de langage, qui repose sur l’analyse statique, analyse votre code source sans l’exécuter pour retourner les résultats d’IntelliSense et proposer d’autres fonctionnalités d’édition.
Par conséquent, plus la quantité et la taille des fichiers inclus dans votre contexte de projet sont importantes, plus la mémoire et le processeur sont mis à contribution durant l’analyse.
Pour cette raison, quelques hypothèses par défaut sont émises sur la forme de votre projet :

- Les listes `package.json` et `bower.json` répertorient les dépendances utilisées par votre projet, et sont incluses par défaut dans l’acquisition de type automatique (ATA).
- Un dossier `node_modules` de premier niveau contient le code source de la bibliothèque, et son contenu est exclu du contexte du projet par défaut
- Tout autre fichier `.js`, `.jsx`, `.ts` et `.tsx` peut être l’un de *vos propres* fichiers sources et doit être inclus dans le contexte du projet

Dans la plupart des cas, vous pouvez simplement ouvrir votre projet et obtenir de bons résultats avec la configuration de projet par défaut. Cependant, dans les projets de grande ampleur ou avec des structures de dossiers différentes, il peut être souhaitable d’affiner la configuration du service de langage pour mieux cibler vos propres fichiers sources.

### <a name="override-defaults"></a>Remplacer les options par défaut

Vous pouvez remplacer la configuration par défaut en ajoutant un fichier `tsconfig.json` à la racine de votre projet.
Un fichier `tsconfig.json` comprend plusieurs options vous permettant de manipuler le contexte de votre projet.
Certaines d’entre elles sont répertoriées ci-dessous. Pour obtenir l’ensemble complet de toutes les options disponibles, [consultez le magasin de schémas](http://json.schemastore.org/tsconfig).

## <a name="important-tsconfigjson-options"></a>Options importantes de `tsconfig.json`

```json
{
  "compilerOptions": {
    "allowJs": true,          // include .js and .jsx in project context (defaults to only .ts and .tsx)
    "noEmit": true            // turns off downlevel compiler
  },
  "files": [],                // list of explicit files to include in the project context. Highest priority.
  "include": [],              // list of folders or glob patterns to include in the project context.
  "exclude": [],              // list of folders or glob patterns to exclude. Overridden by files array.
  "typeAcquisition": {
    "enable": true,           // Defaulted to "false" with a tsconfig. Enables better IntelliSense in JS.
    "include": [ "jquery" ],  // Specific libs to fetch .d.ts files that weren't picked up by ATA
    "exclude": [ "node" ]     // Specific libs to not fetch .d.ts files for
  }
}
```

### <a name="example-project-configuration"></a>Exemple de configuration de projet

Pour un projet donné avec la configuration suivante :

- Les fichiers sources du projet sont dans `wwwroot/js`
- Les fichiers lib du projet sont dans `wwwroot/lib`
- `bootstrap`, `jquery`, `jquery-validation` et `jquery-validation-unobtrusive` sont répertoriés dans `bower.json`
- `kendo-ui` a été ajouté manuellement au dossier lib

![Structure de dossiers](../javascript/media/js-folderstructure.png)

Vous pouvez utiliser le fichier `tsconfig.json` suivant pour vérifier, d’une part, que le service de langage analyse uniquement vos fichiers sources dans le dossier `js` et, d’autre part, qu’il récupère et utilise toujours les fichiers `.d.ts` pour les bibliothèques dans votre dossier `lib`.

```json
{
  "compilerOptions": {
    "allowJs": true,
    "noEmit": true
  },
  "exclude": ["wwwroot/lib"],  //ignore lib folders, we will get IntelliSense via ATA
  "typeAcquisition": {
    "enable": true,
    "include": [ "kendo-ui" ]  //kendo-ui wasn't added via bower, so we need to list it here
  }
}
```

## <a name="troubleshooting-the-javascript-language-service-has-been-disabled-for-the-following-projects"></a>Résolution des problèmes : le service de langage JavaScript a été désactivé pour le ou les projets suivants
Quand vous ouvrez un projet JavaScript qui a une très grande quantité de contenu, vous pouvez obtenir le message suivant : « Le service de langage JavaScript a été désactivé pour le ou les projets suivants ». La raison la plus courante de la présence d’une très grande quantité de code source JavaScript est l’inclusion de bibliothèques avec du code source dépassant la limite de 20 Mo pour un projet.

Un moyen simple pour optimiser votre projet consiste à ajouter un fichier `tsconfig.json` à la racine du projet pour indiquer au service de langage les fichiers qui peuvent être ignorés sans problème. Utilisez l’exemple ci-dessous pour exclure les répertoires les plus courants où sont stockées les bibliothèques :

```json
{
  "compilerOptions": {
    "allowJs": true,
    "allowSyntheticDefaultImports": true,
    "maxNodeModuleJsDepth": 2,
    "noEmit": true,
    "skipLibCheck": true
  },
  "exclude": [
    "**/bin",
    "**/bower_components",
    "**/jspm_packages",
    "**/node_modules",
    "**/obj",
    "**/platforms"
  ]
}
```

Ajoutez d’autres répertoires selon vos besoins. D’autres exemples incluent les répertoires « vendor » ou « wwwroot/lib ».

> [!NOTE]
> La propriété du compilateur `disableSizeLimit` peut également être utilisée pour désactiver la vérification de la limite de 20 Mo. Prenez des précautions particulières lors de l’utilisation de cette propriété, car la désactivation de la limite peut bloquer le service de langage.

## <a name="notable-changes-from-visual-studio-2015"></a>Changements notables par rapport à Visual Studio 2015

[!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] propose un tout nouveau service de langage : certains comportements ont disparu, tandis que d’autres comportements sont différents de ceux de l’expérience précédente.
Le remplacement de VSDoc par JSDoc, la suppression des extensions `.intellisense.js` personnalisées et la limitation d’IntelliSense pour des modèles de code spécifiques constituent les changements les plus importants.

### <a name="no-more-references-or-_referencesjs"></a>Disparition de `///<references/>` et de `_references.js`

Par le passé, il était assez difficile de savoir quels fichiers figuraient dans votre portée IntelliSense à un moment donné. Selon les cas, il était préférable ou non d’avoir tous les fichiers dans l’étendue. Il en résultait des configurations complexes qui nécessitaient la gestion manuelle des références. Dorénavant, vous n’avez plus besoin de vous soucier de la gestion des références et vous n’êtes plus obligé d’utiliser des commentaires pour les références à trois barres obliques ou des fichiers `_references.js`.

Pour plus d’informations sur le fonctionnement d’IntelliSense, consultez la page [JavaScript IntelliSense](../ide/javascript-intellisense.md).

### <a name="vsdoc"></a>VSDoc

Avant, vous pouviez utiliser des commentaires de documentation XML, appelés parfois VSDocs, pour décorer votre code source avec des données supplémentaires utilisées pour enrichir les résultats d’IntelliSense.
VSDoc n’est plus pris en charge. Il est désormais remplacé par [JSDoc](https://jsdoc.app/about-getting-started.html), standard accepté pour JavaScript, qui est plus facile à écrire.

### <a name="intellisensejs-extensions"></a>Extensions `.intellisense.js`

Avant , vous pouviez créer des [extensions IntelliSense](../vs-2015/ide/extending-javascript-intellisense.md) pour ajouter des résultats de saisie semi-automatique personnalisés pour des bibliothèques tierces.
Ces extensions étaient assez difficiles à écrire, et leur installation et leur référencement étaient peu pratiques. Le nouveau service de langage ne prend donc plus en charge ces fichiers.
Une autre méthode plus simple consiste à écrire un fichier de définition TypeScript pour offrir les mêmes fonctionnalités IntelliSense que les anciennes extensions `.intellisense.js`.
Pour en savoir plus sur la création de fichiers de déclaration (`.d.ts`), cliquez [ici](http://www.typescriptlang.org/docs/handbook/declaration-files/introduction.html).

### <a name="unsupported-patterns"></a>Modèles non pris en charge

Étant donné que le nouveau service de langage repose sur l’analyse statique et non sur un moteur d’exécution (pour plus d’informations sur les différences, lisez [ce problème](https://github.com/Microsoft/TypeScript/issues/4789)), quelques modèles JavaScript ne peuvent plus être détectés.
Le modèle le plus courant est le modèle « expando ».
Le service de langage ne peut pas fournir la fonctionnalité IntelliSense sur des objets auxquels des propriétés ont été ajoutées après la déclaration.
Par exemple :

```js
var obj = {};
obj.a = 10;
obj.b = "hello world";
obj. // IntelliSense won't show properties a or b
```

Vous pouvez contourner ce problème en déclarant les propriétés durant la création des objets :

```js
var obj = {
    "a": 10,
    "b": "hello world"
}
obj. // IntelliSense shows properties a and b
```

Vous pouvez aussi ajouter un commentaire JSDoc comme suit :

```js
/**
 * @type {{a: number, b: string}}
 */
var obj = {};
obj.a = 10;
obj.b = "hello world";
obj. // IntelliSense shows properties a and b
```