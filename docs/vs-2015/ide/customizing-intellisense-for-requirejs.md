---
title: Personnalisation d’IntelliSense pour RequireJS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 2be07ef8-9c08-444b-a21a-22a4fe6386a3
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 279ac7737460c90f86918ae673e8f64ef1215546
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665879"
---
# <a name="customizing-intellisense-for-requirejs"></a>Personnalisation d'IntelliSense pour RequireJS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Grâce à Visual Studio 2013 Update 4, le fichier RequireJS JavaScript et le chargeur modulaire sont désormais pris en charge. RequireJS facilite la définition des dépendances entre modules de code, ainsi que le chargement dynamique des modules uniquement lorsque c'est nécessaire. Lorsque vous écrivez du code JavaScript qui utilise RequireJS, des suggestions IntelliSense sont fournies pour les modules que vous avez référencés dans les définitions de modules ou bien que vous avez référencés à l'aide d'appels à `require()` depuis votre code.

 Par défaut, Visual Studio permet une configuration très basique pour la prise en charge de RequireJS. Il est toutefois courant de configurer ses propres paramètres personnalisés (autrement dit, de définir des alias pour les bibliothèques). Cette rubrique décrit les différentes façons dont vous pouvez personnaliser Visual Studio pour qu'il fonctionne avec la configuration unique de votre projet.

 Cette rubrique explique comment :

- Personnaliser RequireJS dans les projets ASP.NET

- Personnaliser RequireJS dans les projets JSProj, qui sont utilisés pour créer des applications Apache Cordova, des applications du Windows Store et des applications HTML LightSwitch.

## <a name="customize-requirejs-in-aspnet-projects"></a>Personnaliser RequireJS dans les projets ASP.NET
 La prise en charge de RequireJS est automatiquement activée quand un fichier nommé require.js est référencé par le fichier JavaScript actif (pour plus d'informations, voir la section « Détermination du contexte IntelliSense » dans [JavaScript IntelliSense](../ide/javascript-intellisense.md)). Dans les projets ASP.NET, le référencement de require.js est généralement effectué à l'aide d'une directive /// \<reference/> dans un fichier _references.js.

### <a name="configure-the-data-main-attribute-in-an-aspnet-project"></a>Configurer l'attribut data-main dans un projet ASP.NET
 Pour simuler précisément le fonctionnement de votre application lorsque vous l'exécutez, l'éditeur JavaScript doit savoir quel fichier charger en premier lorsque vous configurez require.js. Pour cela, dans le fichier HTML de votre application, utilisez l'attribut `data-main` sur l'élément de script qui fait référence à require.js, comme illustré ici.

```html
<script src="js/require.js" data-main="js/app.js"></script>
```

 Dans cet exemple, le script référencé par data-main (js/app.js) est chargé immédiatement après require.js. Le fichier qui est immédiatement chargé est le meilleur endroit pour configurer l’utilisation de RequireJS (à l'aide de `require.config()`). Pour indiquer à l’éditeur JavaScript quel fichier utiliser pour `data-main` dans votre application, ajoutez un attribut `data-main` et modifiez une directive /// \<reference/> qui fait référence à require.js dans votre application. Par exemple, vous pouvez utiliser la directive suivante :

```javascript
/// <reference path="js/require.js" data-main="js/app.js" />
```

### <a name="configure-the-application-start-page-in-an-aspnet-project"></a>Configurer la page de démarrage d'une application dans un projet ASP.NET
 Lorsque l’application s’exécute, RequireJS suppose que les chemins d’accès relatifs aux fichiers (par exemple, «.. \\ les chemins d’accès) sont relatifs au fichier HTML qui a chargé la bibliothèque Require. js. Lorsque vous écrivez du code dans l'éditeur Visual Studio pour un projet ASP.NET, cette page de démarrage est inconnue. Vous devrez donc indiquer à l'éditeur quelle page de démarrage utiliser lors de l'utilisation de chemins d'accès relatifs. Pour ce faire, ajoutez un attribut `start-page` à votre directive /// \<reference/>.

```javascript
/// <reference path="js/require.js" data-main="js/app.js" start-page="/app/index.html" />
```

 L'attribut `start-page` spécifie l'URL de la page telle que vous la verriez dans un navigateur lors de l'exécution de votre application.

## <a name="customize-requirejs-in-jsproj-projects"></a>Personnaliser RequireJS dans les projets JSProj
 Les projets JSProj (les fichiers de projet se terminant par une extension .jsproj) sont utilisés lors de la création d'applications Apache Cordova, d'applications HTML du Windows Store ou d'applications HTML LightSwitch. Contrairement aux projets ASP.NET, ces projets lisent les références aux fichiers .js à partir des fichiers HTML présents dans le projet. Par conséquent, quand vous modifierez du code JavaScript dans un projet JSProj, vous verrez que la prise en charge de RequireJS est activée si le fichier JavaScript en cours de modification est référencé dans un autre fichier HTML qui référence également require.js.

 Les étapes de personnalisation requises pour les projets ASP.NET ne sont pas nécessaires dans un fichier de projet JSProj. C’est-à-dire que les fichiers de script utilisés par l’attribut `data-main` dans l’étiquette de script qui fait référence à require.js sont chargés automatiquement pour configurer require.js. Le fichier HTML qui référence require.js est également utilisé comme page de démarrage de l'application.

## <a name="see-also"></a>Voir aussi
 [JavaScript IntelliSense](../ide/javascript-intellisense.md)
