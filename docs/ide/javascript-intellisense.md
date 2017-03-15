---
title: JavaScript IntelliSense | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IntelliSense [JavaScript]
- <reference> JavaScript XML tag
- JavaScript Code Editor
- XML code comments, JavaScript IntelliSense
- reference JavaScript XML tag
- JavaScript, IntelliSense
- code comments, JavaScript IntelliSense
- JavaScript, reference groups
- JavaScript Editor
- reference directives [JavaScript]
- JavaScript, XML documentation comments
- reference groups [JavaScript]
- JavaScript, reference directives
- IntelliSense [JavaScript], about
- IntelliSense extensibility [JavaScript]
- XML documentation comments [JavaScript]
ms.assetid: af1a3171-c9d8-45a3-9c96-a763e3b163ef
caps.latest.revision: 63
author: mikejo
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: d07820eda0d76163d99d7752789750eaf56182fd
ms.openlocfilehash: 1f8372fe201d6b23ee2c65e0f6d6a2fa28976654
ms.lasthandoff: 02/22/2017

---
# <a name="javascript-intellisense"></a>IntelliSense JavaScript
[!include[vs_dev15](../misc/includes/vs_dev15_md.md)] procure une expérience d’édition JavaScript puissante et immédiate. Grâce à un service de langage TypeScript, Visual Studio offre des fonctionnalités IntelliSense plus riches, la prise en charge de fonctionnalités JavaScript modernes et des fonctionnalités de productivité améliorées, parmi lesquelles Atteindre la définition ou la refactorisation.

> [!NOTE]
>  Le service de langage JavaScript dans [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] utilise un nouveau moteur pour le service de langage (« salsa »). Outre les informations détaillées contenues dans la présente rubrique, vous pouvez consulter ce [billet de blog](https://blogs.msdn.microsoft.com/visualstudio/2016/04/08/previewing-salsa-javascript-language-service-visual-studio-15/). De plus, la nouvelle expérience d’édition s’applique principalement dans VS Code. Pour plus d’informations, consultez la [documentation sur VS Code](https://code.visualstudio.com/docs/languages/javascript).

Pour plus d’informations sur les fonctionnalités IntelliSense générales de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], consultez [Utilisation de la fonctionnalité IntelliSense](../ide/using-intellisense.md). 

## <a name="whats-new-in-the-javascript-language-service-in-includevsdev15miscincludesvsdev15mdmd"></a>Nouveautés du service de langage JavaScript dans [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]

- Fonctionnalités IntelliSense enrichies

    JavaScript IntelliSense dans [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] affiche désormais beaucoup plus d’informations sur les listes de paramètres et de membres.
Ces nouvelles informations sont fournies par le service de langage TypeScript, qui utilise l’analyse statique en arrière-plan pour mieux comprendre votre code.
TypeScript utilise plusieurs sources pour générer ces informations.
    - [IntelliSense basé sur l’inférence de type](#TypeInference)
    - [IntelliSense basé sur JSDoc](#JsDoc)
    - [IntelliSense basé sur des fichiers de déclaration TypeScript](#TSDeclFiles)

- [Acquisition automatique de définitions de type](#Auto)
- [Prise en charge d’ES6 et au-delà](#ES6)
- [Prise en charge de la syntaxe JSX](#JSX)

## <a name="TypeInference"></a>IntelliSense basé sur l’inférence de type
Dans JavaScript, la plupart du temps, aucune information de type explicite n’est disponible. Heureusement, il est en général assez facile de déduire un type en fonction du contexte du code.
Ce processus porte le nom d’inférence de type.

Pour une variable ou une propriété, le type est généralement le type de la valeur utilisée pour l’initialiser ou celui de la valeur la plus récemment assignée. 

```js
var nextItem = 10;
nextItem; // here we know nextItem is a number

nextItem = "box";
nextItem; // now we know nextItem is a string
```

Pour une fonction, le type de retour peut être déduit des instructions return. 

Pour les paramètres de fonction, il n’existe aucune inférence, mais vous pouvez contourner ce problème à l’aide de fichiers `.d.ts` JSDoc ou TypeScript (voir les sections suivantes).

En outre, il existe une inférence spéciale pour les éléments suivants :
 - Classes de « style ES3 », spécifiées à l’aide d’une fonction de constructeur et d’assignations à la propriété de prototype
 - Modèles de module de style CommonJS, spécifiés sous forme d’assignations de propriété sur l’objet `exports` ou d’assignations à la propriété `module.exports`

```js
function Foo(param1) {
    this.prop = param1;
}
Foo.prototype.getIt = function () { return this.prop; };
// Foo will appear as a class, and instances will have a 'prop' property and a 'getIt' method.

exports.Foo = Foo;
// This file will appear as an external module with a 'Foo' export.
// Note that assigning a value to "module.exports" is also supported.
```

## <a name="JsDoc"></a> IntelliSense basé sur JSDoc

Si l’inférence de type ne fournit pas les informations de type souhaitées (ou pour prendre en charge de la documentation), vous pouvez fournir les informations de type explicitement par le biais d’annotations JSDoc.  Par exemple, pour donner à un objet partiellement déclaré un type spécifique, vous pouvez utiliser la balise `@type` comme indiqué ci-dessous :

```js
/**
 * @type {{a: boolean, b: boolean, c: number}}
 */
var x = {a: true};
x.b = false;
x. // <- "x" is shown as having properties a, b, and c of the types specified
```

Comme mentionné, les paramètres de fonction ne sont jamais déduits. Toutefois, à l’aide de la balise `@param` JSDoc, vous pouvez également ajouter des types aux paramètres de la fonction. 

```js
/**
 * @param {string} param1 - The first argument to this function
 */
function Foo(param1) {
    this.prop = param1; // "param1" (and thus "this.prop") are now of type "string".
}
```
 
Pour connaître les annotations JsDoc prises en charge, consultez [ce document](https://github.com/Microsoft/TypeScript/wiki/JsDoc-support-in-JavaScript).

## <a name="TsDeclFiles"></a> IntelliSense basé sur des fichiers de déclaration TypeScript

Étant donné que JavaScript et TypeScript sont désormais basés sur le même service de langage, ils sont capables d’interagir de façon plus riche. Par exemple, vous pouvez fournir JavaScript IntelliSense pour les valeurs déclarées dans un fichier `.d.ts` ([plus d’informations](https://github.com/Microsoft/TypeScript-Handbook/blob/master/pages/Writing%20Definition%20Files.md)) et utiliser les types tels que les interfaces et classes déclarées dans TypeScript en tant que types dans les commentaires JsDoc. 

Nous présentons ci-après un exemple simple de fichier de définition TypeScript qui fournit ces informations de type (par le biais d’une interface) à un fichier JavaScript dans le même projet (à l’aide d’une balise JsDoc).

_**Déclarations TypeScript utilisées dans JavaScript**_

<img src="https://raw.githubusercontent.com/wiki/Microsoft/TypeScript/images/decl1.png" height="400" width="640"/>

## <a name="Auto"></a> Acquisition automatique de définitions de type
Dans l’univers TypeScript, ce sont des fichiers `.d.ts` qui décrivent les API des bibliothèques JavaScript les plus populaires, tandis que le dépôt le plus courant pour de telles définitions est [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped).

Par défaut, le service de langage Salsa tente de détecter les bibliothèques JavaScript en cours d’utilisation, puis télécharge et référence automatiquement le fichier `.d.ts` correspondant qui décrit la bibliothèque afin de fournir une expérience IntelliSense plus riche. Les fichiers sont téléchargés vers un cache situé dans le dossier de l’utilisateur à l’emplacement `%LOCALAPPDATA%\Microsoft\TypeScript`. 

> [!NOTE]
> Cette fonctionnalité est **désactivée** par défaut si vous utilisez un fichier de configuration `tsconfig.json`, mais peut être activée, comme expliqué plus bas.

La détection automatique fonctionne pour les dépendances téléchargées à partir de npm (en lisant le fichier `package.json`), Bower (en lisant le fichier `bower.json`) et pour les fichiers libres dans votre projet qui correspondent à une liste regroupant à peu près les 400 bibliothèques JavaScript les plus populaires. Par exemple, si vous avez `jquery-1.10.min.js` dans votre projet, le fichier `jquery.d.ts` est extrait et chargé afin de procurer une meilleure expérience d’édition. Ce fichier `.d.ts` n’a aucun impact sur votre projet. 

Si vous ne souhaitez pas utiliser l’acquisition automatique, désactivez-la en ajoutant un fichier de configuration, comme indiqué ci-dessous. Vous pouvez toujours placer manuellement des fichiers de définition directement dans votre projet.

## <a name="ES6"></a> Prise en charge d’ES6 et au-delà

ES6, ou ECMAScript 2015, est la prochaine version de JavaScript. Il apporte une nouvelle syntaxe au langage : classes, fonctions arrow, `let`/`const` et bien plus encore. Toute cette nouvelle syntaxe est prise en charge dans Visual Studio.

Une des principales fonctionnalités fournies par TypeScript est la possibilité d’utiliser les fonctionnalités ES6 et d’émettre du code pouvant s’exécuter dans les runtimes JavaScript qui ne comprennent pas encore ces nouvelles fonctionnalités. Cela est communément appelé « transpilation ». Étant donné que JavaScript utilise le même service de langage, il peut également tirer parti de la transpilation ES6+ vers ES5.

Avant de mettre en place ce paramétrage, vous devez comprendre les options de configuration.  TypeScript est configuré par le biais d’un fichier `tsconfig.json`. En l’absence de ce fichier, certaines valeurs par défaut sont utilisées. Pour des raisons de compatibilité, ces valeurs sont différentes si seuls sont présents des fichiers JavaScript (et, éventuellement, des fichiers `.d.ts`). Pour compiler des fichiers JavaScript, vous devez ajouter un fichier `tsconfig.json`, puis définir explicitement certaines de ces valeurs par défaut.

Les paramètres requis pour le fichier tsconfig sont décrits ci-dessous :

 - `allowJs` : cette valeur doit être définie sur `true` pour les fichiers JavaScript à reconnaître.
TypeScript étant compilé en JavaScript, la valeur par défaut est `false`, afin que le compilateur n’inclue pas les fichiers qu’il vient de compiler.
 - `outDir` : vous devez définir ce paramètre sur un emplacement non inclus dans le projet, afin que les fichiers JavaScript émis ne soient pas détectés, puis inclus dans le projet (voir `exclude` ci-après).
 - `module` : si vous utilisez des modules, ce paramètre indique au compilateur le format de module que le code émis doit utiliser (par exemple, `commonjs` pour Node ou des outils de regroupement tels que Browserify).
 - `exclude` : ce paramètre indique les dossiers à ne pas inclure dans le projet. 
 L’emplacement de sortie, ainsi que les dossiers autres que les dossiers de projet tels que `node_modules` ou `temp`, doivent être ajoutés à ce paramètre.
 - `enableAutoDiscovery` : ce paramètre permet de détecter et télécharger automatiquement les fichiers de définition comme indiqué plus haut.
 - `compileOnSave` : ce paramètre indique au compilateur s’il doit réexécuter la compilation chaque fois qu’un fichier source est enregistré dans Visual Studio.

Pour convertir des fichiers JavaScript en modules CommonJS dans un dossier `./out`, vous pouvez inclure des paramètres similaires à ceux ci-après dans un fichier `tsconfig.json`.

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
  "typingOptions": {
    "enableAutoDiscovery": true
  }
}
```

Une fois les paramètres ci-dessus en place, s’il existe un fichier source (`./app.js`) qui contient plusieurs fonctionnalités de langage ECMAScript 2015 comme indiqué ci-dessous :

```js
import {Subscription} from 'rxjs/Subscription';

class Foo {
    sayHi(name) {
        return `Hi ${name}, welcome to Salsa!`;
    }
}

export let sqr = x => x * x;
export default Subscription;
```

Un fichier tel que celui ci-après ciblant ECMAScript 5 (paramétrage par défaut) est émis vers `./out/app.js` :

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
//# sourceMappingURL=app.js.map
```

## <a name="JSX"></a> Prise en charge de la syntaxe JSX

JavaScript dans Visual Studio 2017 offre une prise en charge complète de la syntaxe JSX. JSX est un ensemble de syntaxes qui autorise les balises HTML dans les fichiers JavaScript. 

L’illustration suivante montre un composant React défini dans le fichier TypeScript `comps.tsx`, puis utilisé à partir du fichier `app.jsx`, où il est possible de recourir à IntelliSense pour les saisies semi-automatiques et la documentation dans les expressions JSX.
Vous n’avez pas besoin de TypeScript ici ; il se trouve simplement que cet exemple contient également du code TypeScript.
<img src="https://raw.githubusercontent.com/wiki/Microsoft/TypeScript/images/react.png" height="500" width="640"/>

> [!NOTE]
> Pour convertir la syntaxe JSX en appels React, vous devez ajouter le paramètre `"jsx": "react"` à `compilerOptions` dans le fichier `tsconfig.json` décrit ci-dessus.

Le fichier JavaScript créé à l’emplacement « ./out/app.js » au moment de la génération doit contenir le code :

```js
"use strict";
var comps_1 = require('./comps');
var x = React.createElement(comps_1.RepoDisplay, {description: "test"});
```

