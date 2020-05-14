---
title: Gérer les packages npm
description: Visual Studio vous aide à gérer les packages à l’aide du Gestionnaire de package Node.js (npm)
ms.custom: seodec18
ms.date: 04/16/2020
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 0b4b699c01522878d83e59aadb2c6a54e9d7517f
ms.sourcegitcommit: a7f781d5a089e6aab6b073a07f3d4d2967af8aa6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81760170"
---
# <a name="manage-npm-packages-in-visual-studio"></a>Gérer les packages npm dans Visual Studio

npm vous permet d’installer et de gérer des packages pour une utilisation dans vos applications Node.js. Visual Studio simplifie l’interaction avec npm et l’exécution de commandes npm par le biais de l’interface utilisateur ou directement. Si vous ne connaissez pas npm et souhaitez en savoir plus, consultez la [documentation de npm](https://docs.npmjs.com/).

L’intégration visuelle de Studio avec npm est différente selon votre type de projet.
* [Node.JS](#nodejs-projects)
* [ASP.NET Core](#aspnet-core-projects)
* [Dossier ouvert (Node.js)](../javascript/develop-javascript-code-without-solutions-projects.md)

> [!Important]
> npm s’attend à ce que le dossier *node_modules* et *package.json* dans la racine du projet. Si la structure du dossier de votre application est différente, vous devez modifier votre structure de dossier si vous souhaitez gérer les paquets npm à l’aide de Visual Studio.

## <a name="nodejs-projects"></a>Projets Node.js

Pour les projets Node.js, vous pouvez effectuer les tâches suivantes :
* [Installer des packages à partir de l’Explorateur de solutions](#npmInstallWindow)
* [Gérer les packages installés à partir de l’Explorateur de solutions](#solutionExplorer)
* [Utiliser la commande `.npm` dans la fenêtre interactive de Node.js](#interactive)

Ces fonctionnalités coopèrent et se synchronisent avec le système de projet et le fichier *package.json* dans le projet.

### <a name="prerequisites"></a>Prérequis

Vous avez besoin de la charge de travail **de développement Node.js** et le temps d’exécution Node.js installé pour ajouter un support npm à votre projet. Pour des étapes détaillées, voir [Créer un projet Node.js](/visualstudio/ide/quickstart-nodejs?toc=/visualstudio/javascript/toc.json).

> [!NOTE]
> Pour les projets node.js existants, utilisez le modèle de solution **de code Nde.js existant** ou le type de projet open [folder (Node.js)](../javascript/develop-javascript-code-without-solutions-projects.md) pour activer npm dans votre projet.

### <a name="install-packages-from-solution-explorer-nodejs"></a><a name="npmInstallWindow"></a>Installer des paquets de Solution Explorer (Node.js)

Pour les projets Node.js, le moyen le plus facile d’installer des paquets npm est à travers la fenêtre d’installation de paquets npm. Pour accéder à cette fenêtre, cliquez sur le nœud **npm** dans le projet, puis sélectionnez **Installer de nouveaux packages npm**.

:::image type="content" source="../javascript/media/solution-explorer-install-package.png" alt-text="Installer un nouveau package npm à partir de l’Explorateur de solutions" border="true":::

Dans cette fenêtre, vous pouvez rechercher un package, spécifier des options et effectuer une installation.

![Rechercher un package npm](../javascript/media/search-package.png)

* **Type de dépendance** : choisissez parmi les packages **Standard**, **Développement** et **Facultatif**. Standard signifie que le package est une dépendance du runtime, alors que Développement signifie que le package est nécessaire uniquement pendant le développement.
* **Ajouter à package.json** - Recommandé. Cette option configurable est dépréciée.
* **Version sélectionnée** : sélectionnez la version du package que vous souhaitez installer.
* **Autres arguments npm** : spécifiez d’autres arguments npm standard. Par exemple, vous pouvez entrer une valeur de version comme `@~0.8` pour installer une version spécifique qui n’est pas disponible dans la liste des versions.

Vous pouvez voir l’évolution de l’installation dans la sortie **npm** dans la fenêtre **de sortie.** Cette opération peut prendre un certain temps.

![sortie npm](../javascript/media/npm-output.png)

> [!TIP]
> Vous pouvez rechercher des packages à étendue en ajoutant au début de la requête de recherche l’étendue qui vous intéresse, par exemple en tapant `@types/mocha` pour rechercher les fichiers de définition TypeScript pour mocha. En outre, lors de l’installation de définitions de type pour TypeScript, vous pouvez spécifier la version TypeScript que vous ciblez en ajoutant `@ts2.6` dans le champ d’argument npm.

### <a name="manage-installed-packages-in-solution-explorer-nodejs"></a><a name="solutionExplorer"></a>Gérer les paquets installés dans Solution Explorer (Node.js)

Les packages npm sont affichés dans l’Explorateur de solutions. Les entrées sous le nœud **npm** imitent les dépendances dans le fichier *package.json*.

![Rechercher un package npm](../javascript/media/solution-explorer-status.png)

### <a name="package-status"></a>État du package

* ![Package installé](../javascript/media/installed-npm.png) - Installé et répertorié dans package.json
* ![Package étranger](../javascript/media/extraneous-npm.png) : installé, mais pas explicitement répertorié dans le fichier package.json
* ![Package manquant](../javascript/media/missing-npm.png) - Non installé, mais répertorié dans le fichier package.json

::: moniker range=">=vs-2019"
Cliquez à droite sur le **nœud npm** pour prendre l’une des actions suivantes :

* **Installer de nouveaux forfaits npm** Ouvre l’interface utilisateur pour installer de nouveaux paquets.
* **Installer des forfaits npm** Exécute la commande d’installation de npm pour installer tous les paquets énumérés dans *package.json*. (Runs `npm install`.)
* **Mettre à jour les forfaits npm** Mises à jour des paquets pour les dernières versions, selon la gamme semver spécifié dans *package.json*. (Runs `npm update --save`.). Les plages de semver sont généralement spécifiées à l’aide de « » ou de « « » Pour plus d’informations, [package.json configuration](../javascript/configure-packages-with-package-json.md).

Cliquez à droite sur un nœud de paquet pour prendre l’une des actions suivantes :

* **Installer npm Package(s)** Exécute la commande d’installation de npm pour installer la version de paquet énumérée dans *package.json*. (Runs `npm install`.)
* **Mise à jour npm Package(s)** Mises à jour du paquet à la dernière version, selon la gamme semver spécifié dans *package.json*. (Run `npm update --save`.) Les plages de semver sont généralement spécifiées à l’aide de « » ou de « « »
* **Uninstall npm Package(s)** Désinstalle le paquet et le supprime de *package.json* (Runs `npm uninstall --save`.)
::: moniker-end
::: moniker range="vs-2017"
Cliquez avec le bouton droit sur un nœud de package ou le nœud **npm** pour effectuer l’une des actions suivantes :
* **Installer les packages manquants** qui sont répertoriés dans *package.json*
* **Mettre à jour les paquets npm** à la dernière version
* **Désinstaller un package** et supprimer *package.json*
::: moniker-end

>[!NOTE]
> Pour aider à résoudre les problèmes avec les paquets npm, voir [Dépannage](#troubleshooting-npm-packages).

### <a name="use-the-npm-command-in-the-nodejs-interactive-window-nodejs"></a><a name="interactive"></a>Utilisez la commande .npm dans la fenêtre interactive Node.js (Node.js)

Vous pouvez également utiliser la commande `.npm` dans la fenêtre interactive de Node.js pour exécuter des commandes npm. Pour ouvrir la fenêtre, cliquez avec le bouton droit sur le projet dans l’Explorateur de solutions et choisissez **Ouvrir une fenêtre interactive de Node.js**.

Dans la fenêtre, vous pouvez utiliser des commandes telles que les suivantes pour installer un package :

`.npm install azure@4.2.3`

 > [!Tip]
 > Par défaut, npm s’exécute dans le répertoire de base de votre projet. Si vous avez plusieurs projets dans votre solution, spécifiez le nom ou le chemin du projet entre crochets.
 > `.npm [MyProjectNameOrPath] install azure@4.2.3`

 > [!Tip]
 > Si votre projet ne contient pas de fichier package.json, utilisez `.npm init -y` pour en créer un avec des entrées par défaut.

 ## <a name="aspnet-core-projects"></a>projets de base ASP.NET

Pour des projets tels que ASP.NET projets Core, vous pouvez intégrer le support npm dans votre projet et utiliser npm pour installer des paquets.
* [Ajouter le support npm à un projet](#npmAdd)
* [Installer des paquets à l’aide de package.json](#npmInstallPackage)

>[!NOTE]
> Pour ASP.NET projets Core, vous pouvez également utiliser [Library Manager](https://docs.microsoft.com/aspnet/core/client-side/libman/?view=aspnetcore-3.1) ou fil au lieu de npm pour installer des fichiers JavaScript et CSS côté client.

### <a name="add-npm-support-to-a-project-aspnet-core"></a><a name="npmAdd"></a>Ajouter un support npm à un projet (ASP.NET Core)

Si votre projet n’inclut pas déjà un fichier *package.json,* vous pouvez en ajouter un pour activer le support npm en ajoutant un fichier *package.json* au projet.

1. Si vous n’avez pas node.js installé, nous vous recommandons d’installer la version LTS à partir du site [Node.js](https://nodejs.org/en/download/) pour la meilleure compatibilité avec les cadres extérieurs et les bibliothèques.

   npm nécessite Node.js.

1. Pour ajouter le fichier *package.json,* cliquez à droite sur le projet dans Solution Explorer et choisissez **Ajouter** > **un nouvel article**. Choisissez le **fichier de configuration npm**, utilisez le nom par défaut, et cliquez sur **Ajouter**.

   ![Ajoutez package.json à votre projet](../javascript/media/npm-add-package-json.png)

   Si vous ne voyez pas le fichier de configuration npm répertorié, les outils de développement Node.js ne sont pas installés. Vous pouvez utiliser l’installateur Visual Studio pour ajouter la charge de travail **de développement Node.js.** Répétez ensuite l’étape précédente.

1. Inclure un ou plusieurs paquets `devDependencies` de npm dans le ou la `dependencies` section de *package.json*. Par exemple, vous pouvez ajouter ce qui suit au fichier :

   ```json
   "devDependencies": {
      "gulp": "4.0.2",
      "@types/jquery": "3.3.33"
   }
   ```

Lorsque vous enregistrez le fichier, Visual Studio ajoute le paquet sous le nœud **Dépendance / npm** dans Solution Explorer. Si vous ne voyez pas le nœud, cliquez à droite **package.json** et choisissez **Restore Packages**.

>[!NOTE]
> Dans certains scénarios, Solution Explorer peut ne pas afficher l’état correct pour les paquets npm installés. Pour plus d’informations, consultez [Résolution des problèmes](#troubleshooting-npm-packages).

### <a name="install-packages-using-packagejson-aspnet-core"></a><a name="npmInstallPackage"></a>Installer des paquets à l’aide de package.json (ASP.NET Core)

Pour les projets avec npm inclus, `package.json`vous pouvez configurer des paquets npm à l’aide . Cliquez à droite sur le nœud npm dans Solution Explorer et choisissez **Open package.json**.

![Rechercher un package npm](../javascript/media/npm-add-package.png)

IntelliSense in *package.json* vous aide à sélectionner une version particulière d’un forfait npm.

:::image type="content" source="../javascript/media/npm-add-package-intellisense.png" alt-text="Sélectionnez la version npm du paquet" border="true":::

Lorsque vous enregistrez le fichier, Visual Studio ajoute le paquet sous le nœud **Dépendance / npm** dans Solution Explorer. Si vous ne voyez pas le nœud, cliquez à droite **package.json** et choisissez **Restore Packages**.

L’installation d’un colis peut prendre plusieurs minutes. Vérifiez l’évolution de l’installation du paquet en passant à la sortie **npm** dans la fenêtre **de sortie.**

![sortie npm](../javascript/media/npm-output.png)

## <a name="troubleshooting-npm-packages"></a>Paquets de npm de dépannage

* npm nécessite Node.js Si vous n’avez pas Node.js installé, nous vous recommandons d’installer la version LTS à partir du site [Node.js](https://nodejs.org/en/download/) pour la meilleure compatibilité avec les cadres extérieurs et les bibliothèques.

* Pour les projets Node.js, vous devez faire installer la charge de travail **de développement node.js** pour le support npm.

* Dans certains scénarios, Solution Explorer peut ne pas montrer l’état correct pour les paquets npm installés en raison d’un problème connu décrit [ici](https://github.com/aspnet/Tooling/issues/479). Par exemple, le paquet peut apparaître comme non installé lorsqu’il est installé. Dans la plupart des cas, vous pouvez mettre à jour Solution Explorer en supprimant *package.json*, redémarrer Visual Studio, et re-ajouter le fichier *package.json* comme décrit précédemment dans cet article. Ou, lors de l’installation de paquets, vous pouvez utiliser la fenêtre npm Output pour vérifier l’état de l’installation.

* Si vous voyez des erreurs lors de la construction de votre application ou de la transpilation de code TypeScript, vérifiez les incompatibilités du paquet npm comme source potentielle d’erreurs. Pour aider à identifier les erreurs, vérifiez la fenêtre de sortie npm lors de l’installation des paquets, comme décrit précédemment dans cet article. Par exemple, si une ou plusieurs versions de paquets npm ont été dépréciées et entraîne une erreur, vous devrez peut-être installer une version plus récente pour corriger les erreurs. Pour plus d’informations sur l’utilisation de *package.json* pour gérer les versions des packages npm, consultez [Configuration de package.json](../javascript/configure-packages-with-package-json.md).

