---
title: Gérer les packages npm
description: Visual Studio vous aide à gérer les packages à l’aide du Gestionnaire de package Node.js (npm)
ms.custom: seodec18
ms.date: 02/23/2021
ms.topic: how-to
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 2fcf1bd9e9ef5c3ff0663cf12684e6e638d1e5e4
ms.sourcegitcommit: a0f5e7188838c5989c9cc78d99fb29bb2813501e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/11/2021
ms.locfileid: "109729284"
---
# <a name="manage-npm-packages-in-visual-studio"></a>Gérer les packages npm dans Visual Studio

npm vous permet d’installer et de gérer des packages pour une utilisation dans vos applications Node.js. Visual Studio simplifie l’interaction avec npm et l’exécution de commandes npm par le biais de l’interface utilisateur ou directement. Si vous ne connaissez pas npm et souhaitez en savoir plus, consultez la [documentation de npm](https://docs.npmjs.com/).

L’intégration de Visual Studio à NPM est différente selon le type de votre projet.
* [Node.JS](#nodejs-projects)
* [ASP.NET Core](#aspnet-core-projects)
* [Ouvrir le dossier (Node.js)](../javascript/develop-javascript-code-without-solutions-projects.md)

> [!Important]
> NPM attend le dossier *node_modules* et *package.js* dans la racine du projet. Si la structure de dossiers de votre application est différente, vous devez modifier votre structure de dossiers si vous souhaitez gérer des packages NPM à l’aide de Visual Studio.

## <a name="nodejs-projects"></a>Projets Node.js

Pour les projets Node.js, vous pouvez effectuer les tâches suivantes :
* [Installer des packages à partir de l’Explorateur de solutions](#npmInstallWindow)
* [Gérer les packages installés à partir de l’Explorateur de solutions](#solutionExplorer)
* [Utiliser la commande `.npm` dans la fenêtre interactive de Node.js](#interactive)

Ces fonctionnalités coopèrent et se synchronisent avec le système de projet et le fichier *package.json* dans le projet.

### <a name="prerequisites"></a>Prérequis

Vous avez besoin de la charge de travail de **développementNode.js** et du runtime Node.js pour ajouter la prise en charge de NPM à votre projet. Pour obtenir des instructions détaillées, consultez [créer un projet Node.js](../ide/quickstart-nodejs.md?toc=%252fvisualstudio%252fjavascript%252ftoc.json).

> [!NOTE]
> Pour les projets de Node.js existants, utilisez le modèle **de solution à partir de Node.js de code existant** ou du [dossier ouvert (Node.js)](../javascript/develop-javascript-code-without-solutions-projects.md) pour activer NPM dans votre projet.

### <a name="install-packages-from-solution-explorer-nodejs"></a><a name="npmInstallWindow"></a> Installer des packages à partir de Explorateur de solutions (Node.js)

Pour les projets Node.js, le moyen le plus simple d’installer des packages NPM consiste à utiliser la fenêtre installation du package NPM. Pour accéder à cette fenêtre, cliquez sur le nœud **npm** dans le projet, puis sélectionnez **Installer de nouveaux packages npm**.

:::image type="content" source="../javascript/media/solution-explorer-install-package.png" alt-text="Installer un nouveau package npm à partir de l’Explorateur de solutions" border="true":::

Dans cette fenêtre, vous pouvez rechercher un package, spécifier des options et effectuer une installation.

![Capture d’écran de la boîte de dialogue installer les nouveaux packages NPM. Le package Azure 2.2.1-preview est sélectionné et les détails et les options de ce package sont affichés.](../javascript/media/search-package.png)

* **Type de dépendance** : choisissez parmi les packages **Standard**, **Développement** et **Facultatif**. Standard signifie que le package est une dépendance du runtime, alors que Développement signifie que le package est nécessaire uniquement pendant le développement.
* **Ajoutez à package.jssur** recommandé. Cette option configurable est déconseillée.
* **Version sélectionnée** : sélectionnez la version du package que vous souhaitez installer.
* **Autres arguments npm** : spécifiez d’autres arguments npm standard. Par exemple, vous pouvez entrer une valeur de version comme `@~0.8` pour installer une version spécifique qui n’est pas disponible dans la liste des versions.

Vous pouvez voir la progression de l’installation dans la sortie de **NPM** dans la fenêtre **sortie** (pour ouvrir la fenêtre, choisissez **Afficher** la  >  **sortie** ou appuyez sur **CTRL**  +  **ALT**  +  **O**). Cette opération peut prendre un certain temps.

![sortie NPM](../javascript/media/npm-output.png)

> [!TIP]
> Vous pouvez rechercher des packages à étendue en ajoutant au début de la requête de recherche l’étendue qui vous intéresse, par exemple en tapant `@types/mocha` pour rechercher les fichiers de définition TypeScript pour mocha. En outre, lors de l’installation de définitions de type pour la machine à écrire, vous pouvez spécifier la version d’une machine à écrire que vous ciblez en ajoutant `@ts2.6` dans le champ argument npm.

### <a name="manage-installed-packages-in-solution-explorer-nodejs"></a><a name="solutionExplorer"></a>Gérer les packages installés dans Explorateur de solutions (Node.js)

Les packages npm sont affichés dans l’Explorateur de solutions. Les entrées sous le nœud **npm** imitent les dépendances dans le fichier *package.json*.

![Capture d’écran du nœud NPM dans Explorateur de solutions montrant l’état d’installation des packages NPM.](../javascript/media/solution-explorer-status.png)

### <a name="package-status"></a>État du package

* ![Package installé](../javascript/media/installed-npm.png) - Installé et répertorié dans package.json
* ![Package étranger](../javascript/media/extraneous-npm.png) : installé, mais pas explicitement répertorié dans le fichier package.json
* ![Package manquant](../javascript/media/missing-npm.png) - Non installé, mais répertorié dans le fichier package.json

::: moniker range=">=vs-2019"
Cliquez avec le bouton droit sur le nœud **NPM** pour effectuer l’une des actions suivantes :

* **Installer de nouveaux packages NPM** Ouvre l’interface utilisateur pour installer de nouveaux packages.
* **Installer les packages NPM** Exécute la commande NPM install pour installer tous les packages listés dans *package.jssur*. (S’exécute `npm install` .)
* **Mettre à jour les packages NPM** Met à jour les packages vers les versions les plus récentes, en fonction de la plage de contrôle de version sémantique (SemVer) spécifiée dans *package.jssur*. (S’exécute `npm update --save` .). Les plages SemVer sont généralement spécifiées à l’aide de « ~ » ou « ^ ». Pour plus d’informations, [package.jssur la configuration](../javascript/configure-packages-with-package-json.md).

Cliquez avec le bouton droit sur un nœud de package pour effectuer l’une des actions suivantes :

* **Installer le ou les packages NPM** Exécute la commande NPM install pour installer la version de package indiquée dans *package.jssur*. (S’exécute `npm install` .)
* **Mettre à jour le ou les packages NPM** Met à jour le package avec la dernière version, en fonction de la plage SemVer spécifiée dans *package.jssur*. (Exécuter `npm update --save` ). Les plages SemVer sont généralement spécifiées à l’aide de « ~ » ou « ^ ».
* **Désinstaller le ou les packages NPM** Désinstalle le package et le supprime de *package.js* (s’exécute `npm uninstall --save` ).
::: moniker-end
::: moniker range="vs-2017"
Cliquez avec le bouton droit sur un nœud de package ou le nœud **npm** pour effectuer l’une des actions suivantes :
* **Installer les packages manquants** qui sont répertoriés dans *package.json*
* **Mettre à jour les packages NPM** vers la dernière version
* **Désinstaller un package** et supprimer *package.json*
::: moniker-end

>[!NOTE]
> Pour obtenir de l’aide sur la résolution des problèmes liés aux packages NPM, consultez [Dépannage](#troubleshooting-npm-packages).

### <a name="use-the-npm-command-in-the-nodejs-interactive-window-nodejs"></a><a name="interactive"></a>Utilisez la commande. NPM dans la fenêtre interactive Node.js (Node.js)

Vous pouvez également utiliser la commande `.npm` dans la fenêtre interactive de Node.js pour exécuter des commandes npm. Pour ouvrir la fenêtre, cliquez avec le bouton droit sur le projet dans Explorateur de solutions, puis choisissez **ouvrir Node.js fenêtre interactive** (ou appuyez sur **CTRL**  +  **K**, **N**).

Dans la fenêtre, vous pouvez utiliser des commandes telles que les suivantes pour installer un package :

`.npm install azure@4.2.3`

 > [!Tip]
 > Par défaut, npm s’exécute dans le répertoire de base de votre projet. Si vous avez plusieurs projets dans votre solution, spécifiez le nom ou le chemin du projet entre crochets.
 > `.npm [MyProjectNameOrPath] install azure@4.2.3`

 > [!Tip]
 > Si votre projet ne contient pas de fichier package.json, utilisez `.npm init -y` pour en créer un avec des entrées par défaut.

 ## <a name="aspnet-core-projects"></a>Projets ASP.NET Core

Pour les projets tels que les projets ASP.NET Core, vous pouvez intégrer la prise en charge de NPM dans votre projet et utiliser NPM pour installer des packages.
* [Ajouter la prise en charge de NPM à un projet](#npmAdd)
* [Installer des packages à l’aide d' package.jssur](#npmInstallPackage)

>[!NOTE]
> Pour les projets ASP.NET Core, vous pouvez également utiliser le [Gestionnaire de bibliothèque](/aspnet/core/client-side/libman/?view=aspnetcore-3.1&preserve-view=true) ou le fil à la place de NPM pour installer des fichiers JavaScript et CSS côté client.

### <a name="add-npm-support-to-a-project-aspnet-core"></a><a name="npmAdd"></a> Ajouter la prise en charge de NPM à un projet (ASP.NET Core)

Si votre projet n’inclut pas déjà un *package.jssur* le fichier, vous pouvez en ajouter un pour activer la prise en charge de NPM en ajoutant un *package.jssur* le fichier au projet.

1. Si Node.js n’est pas installé, nous vous recommandons d’installer la version LTS à partir du site Web [Node.js](https://nodejs.org/en/download/) pour une meilleure compatibilité avec les infrastructures et les bibliothèques externes.

   NPM requiert Node.js.

1. Pour ajouter le *package.jssur* le fichier, cliquez avec le bouton droit sur le projet dans Explorateur de solutions et choisissez **Ajouter**  >  un **nouvel élément** (ou appuyez sur **CTRL**  +  **MAJ**  +  **A**). Choisissez le **fichier de configuration NPM**, utilisez le nom par défaut, puis cliquez sur **Ajouter**.

   ![Ajouter package.jsà votre projet](../javascript/media/npm-add-package-json.png)

   Si vous ne voyez pas le fichier de configuration NPM répertorié, Node.js outils de développement ne sont pas installés. Vous pouvez utiliser la Visual Studio Installer pour ajouter la charge de travail de **développementNode.js** . Ensuite, répétez l’étape précédente.

1. Incluez un ou plusieurs packages NPM dans `dependencies` la `devDependencies` section ou de *package.jssur*. Par exemple, vous pouvez ajouter le code suivant au fichier :

   ```json
   "devDependencies": {
      "gulp": "4.0.2",
      "@types/jquery": "3.3.33"
   }
   ```

Lorsque vous enregistrez le fichier, Visual Studio ajoute le package sous le nœud **Dependencies/NPM** dans Explorateur de solutions. Si vous ne voyez pas le nœud, cliquez avec le bouton droit sur **package.js** , puis choisissez **restaurer les packages**.

>[!NOTE]
> Dans certains scénarios, Explorateur de solutions peut ne pas afficher l’état correct des packages NPM installés. Pour plus d’informations, consultez la page [Dépannage](#troubleshooting-npm-packages).

### <a name="install-packages-using-packagejson-aspnet-core"></a><a name="npmInstallPackage"></a>Installer des packages à l’aide d' package.jssur (ASP.NET Core)

Pour les projets avec NPM inclus, vous pouvez configurer des packages NPM à l’aide de `package.json` . Cliquez avec le bouton droit sur le nœud NPM dans Explorateur de solutions, puis choisissez **ouvrir package.jssur**.

![Capture d’écran de l’Explorateur de solutions avec le nœud NPM sélectionné. Le menu contextuel est ouvert et ouvert package.jsactivé est sélectionné.](../javascript/media/npm-add-package.png)

IntelliSense dans *package.jssur* vous aide à sélectionner une version particulière d’un package NPM.

:::image type="content" source="../javascript/media/npm-add-package-intellisense.png" alt-text="Sélectionner la version du package NPM" border="true":::

Lorsque vous enregistrez le fichier, Visual Studio ajoute le package sous le nœud **Dependencies/NPM** dans Explorateur de solutions. Si vous ne voyez pas le nœud, cliquez avec le bouton droit sur **package.js** , puis choisissez **restaurer les packages**.

L’installation d’un package peut prendre plusieurs minutes. Vérifiez la progression de l’installation du package en basculant vers la sortie de **NPM** dans la fenêtre **sortie** .

![sortie NPM](../javascript/media/npm-output.png)

## <a name="troubleshooting-npm-packages"></a>Résolution des problèmes des packages NPM

* NPM requiert Node.js si vous n’avez pas Node.js installé, nous vous recommandons d’installer la version LTS à partir du site Web [Node.js](https://nodejs.org/en/download/) pour une meilleure compatibilité avec les infrastructures et les bibliothèques externes.

* Pour les projets Node.js, la charge de travail de **développementNode.js** doit être installée pour la prise en charge de NPM.

* Dans certains scénarios, Explorateur de solutions peut ne pas afficher l’état correct des packages NPM installés en raison d’un problème connu décrit [ici](https://github.com/aspnet/Tooling/issues/479). Par exemple, le package peut apparaître comme n’étant pas installé lors de son installation. Dans la plupart des cas, vous pouvez mettre à jour Explorateur de solutions en supprimant *package.jssur*, en redémarrant Visual Studio, puis en rajoutant le *package.jssur* le fichier, comme décrit précédemment dans cet article. Ou, lors de l’installation de packages, vous pouvez utiliser la fenêtre Sortie NPM pour vérifier l’état de l’installation.

* Dans certains scénarios de ASP.NET Core, le nœud NPM dans Explorateur de solutions peut ne pas être visible après la génération du projet. Pour afficher à nouveau le nœud, cliquez avec le bouton droit sur le nœud du projet et choisissez **décharger le projet.** Cliquez ensuite avec le bouton droit sur le nœud du projet et choisissez **recharger le projet**.

* Si vous constatez des erreurs lors de la génération de votre application ou du code de la machine à écrire, recherchez les incompatibilités de packages NPM comme source potentielle d’erreurs. Pour identifier les erreurs, consultez la fenêtre Sortie NPM lors de l’installation des packages, comme décrit précédemment dans cet article. Par exemple, si une ou plusieurs versions de package NPM sont dépréciées et provoquent une erreur, vous devrez peut-être installer une version plus récente pour corriger les erreurs. Pour plus d’informations sur l’utilisation de *package.json* pour gérer les versions des packages npm, consultez [Configuration de package.json](../javascript/configure-packages-with-package-json.md).
