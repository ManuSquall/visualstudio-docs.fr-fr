---
title: Compiler et générer du code de machine à écrire à l’aide de NPM
description: Découvrez comment ajouter la prise en charge de la méthode de machine à vos projets Visual Studio à l’aide du gestionnaire de package de nœud (NPM).
ms.date: 7/23/2020
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 96e5689c0108231be26ddf7d598227137f7bc1f7
ms.sourcegitcommit: ab5735d64a6ad7aecabf5d6df159888e3246bff5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2021
ms.locfileid: "111433777"
---
# <a name="compile-typescript-code-nodejs"></a>Compiler le code de la machine à écrire (Node.js)

Vous pouvez ajouter la prise en charge de la machine à écrire à vos projets à l’aide de la TypeScript SDK, disponible par défaut dans le programme d’installation de Visual Studio ou à l’aide de NPM. Pour les projets développés dans Visual Studio 2019, nous vous encourageons à utiliser le package NPM de machine à écrire pour une plus grande portabilité sur différents environnements et plateformes.

Pour les projets ASP.NET Core, il est recommandé d’utiliser le [package NuGet](../javascript/compile-typescript-code-nuget.md) à la place.

## <a name="add-typescript-support-using-npm"></a>Ajouter la prise en charge de la machine à écrire avec NPM

Le [package NPM de machine à écrire](https://www.npmjs.com/package/typescript) ajoute la prise en charge de la méthode de machine lorsque le package npm pour TypeScript 2.1 (ou version ultérieure) est installé dans un projet, la version correspondante du service de langage TypeScript est chargée dans l’éditeur.

1. [Suivez les instructions](../ide/quickstart-nodejs.md?toc=%252fvisualstudio%252fjavascript%252ftoc.json) pour installer la charge de travail développement Node.js et le runtime Node.js.

   Pour l’intégration la plus simple avec Visual Studio, créez votre projet à l’aide de l’un des modèles d' Node.js, tels que le modèle d’application Web vide Node.js. Dans le cas contraire, utilisez un Node.js modèle JavaScript inclus dans Visual Studio et suivez les instructions ici, ou utilisez un projet de [dossier ouvert](../javascript/develop-javascript-code-without-solutions-projects.md) .

1. Si votre projet n’est pas déjà inclus, installez le [package NPM de machine à écrire](https://www.npmjs.com/package/typescript).

   Dans Explorateur de solutions (volet droit), ouvrez le *package.js* dans la racine du projet. Les packages listés correspondent aux packages sous le nœud NPM dans Explorateur de solutions. Pour plus d’informations, consultez [gérer les packages NPM](../javascript/npm-package-management.md).

   Pour un projet Node.js, vous pouvez installer le package NPM de machine à écrire à l’aide de la ligne de commande ou de l’IDE. Pour effectuer l’installation à l’aide de l’IDE, cliquez avec le bouton droit sur le nœud NPM dans Explorateur de solutions, choisissez **installer un nouveau package NPM**, recherchez la **machine à écrire**, puis installez le package.

   Vérifiez l’option **NPM** dans la fenêtre **sortie** pour voir la progression de l’installation du package. Le package installé apparaît sous le nœud **NPM** dans Explorateur de solutions.

1. Si votre projet n’est pas déjà inclus, ajoutez un fichier *. tsconfig* à la racine de votre projet. Pour ajouter le fichier, cliquez avec le bouton droit sur le nœud du projet et choisissez **ajouter > nouvel élément**. Choisissez le **fichier de configuration de la machine à écrire JSON**, puis cliquez sur **Ajouter**.

   Visual Studio ajoute le *tsconfig.jssur* le fichier à la racine du projet. Vous pouvez utiliser ce fichier pour [configurer les options](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html) du compilateur de machine à écrire.

1. Ouvrez *tsconfig.jssur* et mettez à jour pour définir les options du compilateur de votre choix.

   Voici un exemple de *tsconfig.jssimple sur* un fichier.

   ```json
   {
     "compilerOptions": {
       "noImplicitAny": false,
       "noEmitOnError": true,
       "removeComments": false,
       "sourceMap": true,
       "target": "es5",
       "outDir": "dist"
     },
     "include": [
       "scripts/**/*"
     ]
   }
   ```

   Dans cet exemple :
   - *include* indique au compilateur où rechercher les fichiers de machine à écrire (*. TS).
   - l’option *outDir* spécifie le dossier de sortie pour les fichiers JavaScript ordinaires qui sont transpiles par le compilateur de machine à écrire.
   - l’option *mappage* indique si le compilateur génère des fichiers *mappage* .

   La configuration précédente fournit uniquement une présentation de base de la configuration de la machine à écrire. Pour plus d’informations sur les autres options, consultez [tsconfig.jssur](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html).

## <a name="build-the-application"></a>Créer l’application

1. Ajoutez des fichiers de machine à écrire (*. TS*) ou de jsx (*. TSX*) à votre projet, puis ajoutez le code de la machine à écrire. Pour obtenir un exemple simple de la méthode de machine à écrire, utilisez ce qui suit :

   ```typescript
   let message: string = 'Hello World';
   console.log(message);
   ```

1. Dans *package.js*, ajoutez la prise en charge des commandes de génération et de nettoyage de Visual Studio à l’aide des scripts suivants.

   ```json
   "scripts": {
     "build": "tsc --build",
     "clean": "tsc --build --clean"
   },
   ```

   Si vous devez créer à l’aide d’un outil tiers tel que WebPack, vous pouvez ajouter un script de génération de ligne de commande à votre *package.jssur* le fichier :

   ```json
   "scripts": {
      "build": "webpack-cli app.tsx --config webpack-config.js"
   }
   ```

   Pour obtenir un exemple d’utilisation de WebPack avec REACT et un fichier de configuration WebPack, consultez [créer une application Web avec Node.js et réagir](../javascript/tutorial-nodejs-with-react-and-jsx.md).

   Pour obtenir un exemple d’utilisation de Vue.js avec la machine à écrire, consultez [créer une application Vue.js](/javascript/create-application-with-vuejs).

1. Si vous devez configurer des options telles que la page de démarrage, le chemin d’accès au runtime Node.js, le port d’application ou les arguments d’exécution, cliquez avec le bouton droit sur le nœud du projet dans Explorateur de solutions, puis choisissez **Propriétés**.

   >[!NOTE]
   > Lors de la configuration d’outils tiers, Node.js projets n’utilisent pas les chemins d’accès configurés sous **Outils**  >  **options**  >  **projets et solutions**  >  **Web Package Management**  >  **Outils Web externes**. Ces paramètres sont utilisés pour d’autres types de projets.

1. Choisissez **générer > générer la solution**.

   Bien que l’application soit générée automatiquement lorsque vous l’exécutez, nous souhaitons examiner un problème qui se produit pendant le processus de génération :

   Si vous avez généré des mappages de sources, ouvrez le dossier spécifié dans l’option *outDir* et vous trouvez le ou les fichiers de.js générés, \* ainsi que le \* ou les fichiers js. map générés.

   Les fichiers de mappage source sont requis pour le [débogage](../javascript/debug-nodejs.md).

### <a name="run-the-application"></a>Exécution de l'application

Pour obtenir des instructions sur l’exécution de l’application après sa compilation, consultez [créer votre première Node.js application](../ide/quickstart-nodejs.md?toc=%252fvisualstudio%252fjavascript%252ftoc.json#run-the-app).

## <a name="automate-build-tasks"></a>Automatiser les tâches de génération

Vous pouvez utiliser l’Explorateur de l’exécuteur de tâches dans Visual Studio pour faciliter l’automatisation des tâches des outils tiers tels que NPM et WebPack.

- [NPM de tâche Runner](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.NPMTaskRunner) -ajoute la prise en charge des scripts NPM définis dans *package.jssur*. Prend en charge les fils.
- [WebPack Task Runner](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.WebPackTaskRunner) : ajoute la prise en charge de WebPack.
