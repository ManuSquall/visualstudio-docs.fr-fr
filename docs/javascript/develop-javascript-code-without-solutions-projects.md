---
title: Écrire du code JavaScript dans Visual Studio sans une solution ni un projet
titleSuffix: ''
description: Visual Studio prend en charge la création de code sans dépendance par rapport à un fichier projet ou solution
ms.custom: seodec18
ms.date: 09/24/2018
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 3d6e3479fe27c5d88b58f096ab5405d75c6c98e3
ms.sourcegitcommit: 509fc3a324b7748f96a072d0023572f8a645bffc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58857838"
---
# <a name="develop-javascript-and-typescript-code-in-visual-studio-without-solutions-or-projects"></a>Développer du code JavaScript et TypeScript dans Visual Studio sans solutions ni projets

À compte de Visual Studio 2017, vous pouvez [développer du code sans projets ni solutions](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md), ce qui vous permet d’ouvrir un dossier de code et de commencer immédiatement à utiliser des fonctionnalités d’édition avancées, par exemple IntelliSense, la recherche, la refactorisation, le débogage et bien plus encore. Outre ces fonctionnalités, Node.js Tools pour Visual Studio ajoute la prise en charge de la génération de fichiers TypeScript, la gestion de packages npm et l’exécution de scripts npm.

Pour commencer, dans la barre d’outils, sélectionnez **Fichier** > **Ouvrir** > **Dossier**. L’Explorateur de solutions affiche tous les fichiers dans le dossier et vous pouvez les ouvrir pour commencer à les modifier. En arrière-plan, Visual Studio indexe les fichiers pour activer npm, la génération et les fonctionnalités de débogage.

> [!IMPORTANT]
> Visual Studio 2017 version 15.8 ou ultérieure est nécessaire pour la plupart des fonctionnalités décrites dans cet article, y compris l’intégration npm.

## <a name="npm-integration"></a>Intégration npm

Si le dossier que vous ouvrez contient un fichier *package.json*, vous pouvez cliquer avec le bouton droit sur *package.json* pour afficher un menu contextuel spécifique à npm.

![Menu npm dans l’Explorateur de solutions](../javascript/media/solution-explorer-npm-ctx.png)

Dans le menu contextuel, vous pouvez gérer les packages installés par npm de la même façon que vous [gérez les packages npm](npm-package-management.md) lors de l’utilisation d’un fichier projet.

En outre, le menu vous permet également d’exécuter des scripts définis dans l’élément `scripts` dans *package.json*. Ces scripts utilisent la version de Node.js disponible sur la variable d’environnement `PATH`. Les scripts sont exécutés dans une nouvelle fenêtre. Il s’agit d’un excellent moyen d’exécuter une build ou des scripts.

## <a name="build-and-debug"></a>Génération et débogage

### <a name="packagejson"></a>package.json
Si le fichier *package.json* dans le dossier spécifie un élément `main`, la commande **Déboguer** sera disponible dans le menu contextuel pour *package.json*.
En cliquant dessus, vous démarrez *node.exe* avec le script spécifié comme argument.

### <a name="javascript-files"></a>Fichiers JavaScript
Vous pouvez déboguer des fichiers JavaScript en cliquant avec le bouton droit sur un fichier et en sélectionnant **Déboguer** dans le menu contextuel. Cette opération démarre *node.exe* avec ce fichier JavaScript comme argument.

### <a name="typescript-files-and-tsconfigjson"></a>Fichiers TypeScript et tsconfig.json
En l’absence de *tsconfig.json* dans le dossier, vous pouvez cliquer avec le bouton droit sur un fichier TypeScript pour afficher les commandes du menu contextuel afin de générer et déboguer ce fichier. Quand vous utilisez ces commandes, vous générez ou déboguez à l’aide de *tsc.exe* avec les options par défaut. (Vous devez générer le fichier avant de pouvoir déboguer.)

> [!NOTE]
> Lors de la génération de code TypeScript, nous utilisons la dernière version installée dans `C:\Program Files (x86)\Microsoft SDKs\TypeScript`.

Si un fichier *tsconfig.json* figure dans le dossier, vous pouvez cliquer avec le bouton droit sur un fichier TypeScript pour afficher une commande de menu afin de déboguer ce fichier TypeScript. L’option apparaît uniquement si aucun `outFile` n’est spécifié dans *tsconfig.json*. Si un `outFile` est spécifié, vous pouvez déboguer ce fichier en cliquant avec le bouton droit sur *tsconfig.json* et en sélectionnant l’option appropriée. Le fichier `tsconfig.json` vous offre également une option de génération pour vous permettre de spécifier les options du compilateur.

> [!NOTE]
> Vous trouverez plus d’informations sur *tsconfig.json* dans la [page du manuel TypeScript sur tsconfig.json](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html).

## <a name="unit-tests"></a>Tests unitaires
Vous pouvez activer l’intégration des tests unitaires dans Visual Studio en spécifiant une racine de test dans votre fichier *package.json* :

```json
{
    // ...
    "vsTest":{
        "testRoot": "./tests"
    }
    // ...
}
```

L’exécuteur de tests énumère les packages installés localement pour déterminer quelle infrastructure de test utiliser.
Si aucune des infrastructures prises en charge n’est reconnue, l’exécuteur de tests utilise par défaut *ExportRunner*. Les autres infrastructures prises en charge sont :
* Mocha ([mochajs.org](http://mochajs.org/))
* Jasmine ([Jasmine.github.io](https://jasmine.github.io/))
* Tape ([github.com/substack/tape](https://github.com/substack/tape))

Après l’ouverture de l’Explorateur de tests (choisissez **Test** > **Fenêtres** > **Explorateur de tests**), Visual Studio détecte et affiche les tests.

> [!NOTE]
> L’exécuteur de tests énumère seulement les fichiers JavaScript à la racine de test : si votre application est écrite en TypeScript, vous devez d’abord générer ces fichiers.
