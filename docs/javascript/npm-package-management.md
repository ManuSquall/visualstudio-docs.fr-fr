---
title: Gérer les packages npm dans Visual Studio
description: Visual Studio vous aide à gérer les packages à l’aide du Gestionnaire de package Node.js (npm)
ms.custom: ''
ms.date: 06/06/2018
ms.technology: vs-nodejs
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: douge
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 571cc9048b9f932c0ff344637c144d0a6d649887
ms.sourcegitcommit: b544e2157ac20866baf158eef9cfed3e3f1d68b9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2018
ms.locfileid: "39388395"
---
# <a name="manage-npm-packages-in-visual-studio"></a>Gérer les packages npm dans Visual Studio

npm vous permet d’installer et de gérer des packages pour une utilisation dans vos applications Node.js. Si vous ne connaissez pas npm et souhaitez en savoir plus, consultez la [documentation de npm](https://docs.npmjs.com/).

Visual Studio simplifie l’interaction avec npm et l’exécution de commandes npm par le biais de l’interface utilisateur ou directement. Vous pouvez appliquer l’une des procédures suivantes :
* [Installer des packages à partir de l’Explorateur de solutions](#npmInstallWindow)
* [Gérer les packages installés à partir de l’Explorateur de solutions](#solutionExplorer)
* [Utiliser la commande `.npm` dans la fenêtre interactive de Node.js](#interactive)

Ces fonctionnalités coopèrent et se synchronisent avec le système de projet et le fichier *package.json* dans le projet.

## <a name="npmInstallWindow"></a> Installer des packages à partir de l’Explorateur de solutions

Le moyen le plus simple pour installer des packages npm consiste à utiliser la fenêtre d’installation de package npm. Pour accéder à cette fenêtre, cliquez sur le nœud **npm** dans le projet, puis sélectionnez **Installer de nouveaux packages npm**.

![Installer un nouveau package npm à partir de l’Explorateur de solutions](../javascript/media/solution-explorer-install-package.png)

Dans cette fenêtre, vous pouvez rechercher un package, spécifier des options et effectuer une installation. 

![Rechercher un package npm](../javascript/media/search-package.png)

* **Type de dépendance** : choisissez parmi les packages **Standard**, **Développement** et **Facultatif**. Standard signifie que le package est une dépendance du runtime, alors que Développement signifie que le package est nécessaire uniquement pendant le développement.
* **Ajouter à package.json** : cette option est dépréciée.
* **Version sélectionnée** : sélectionnez la version du package que vous souhaitez installer.
* **Autres arguments npm** : spécifiez d’autres arguments npm standard. Par exemple, vous pouvez entrer une valeur de version comme `@~0.8` pour installer une version spécifique qui n’est pas disponible dans la liste des versions.

Vous pouvez voir la progression de l’installation sous l’onglet npm dans la fenêtre Sortie. Cela peut prendre un certain temps.

> [!TIP]
> Vous pouvez rechercher des packages à étendue en ajoutant au début de la requête de recherche l’étendue qui vous intéresse, par exemple en tapant `@types/mocha` pour rechercher les fichiers de définition TypeScript pour mocha. En outre, lors de l’installation de définitions de type pour TypeScript, vous pouvez spécifier la version de TypeScript que vous ciblez en ajoutant `@ts2.6` dans le champ d’argument npm.

## <a name="solutionExplorer"></a>Gérer les packages installés dans l’Explorateur de solutions

Les packages npm sont affichés dans l’Explorateur de solutions. Les entrées sous le nœud **npm** imitent les dépendances dans le fichier *package.json*.

![Rechercher un package npm](../javascript/media/solution-explorer-status.png)

### <a name="package-status"></a>État du package
* ![Package installé](../javascript/media/installed-npm.png) - Installé et répertorié dans package.json
* ![Package étranger](../javascript/media/extraneous-npm.png) : installé, mais pas explicitement répertorié dans le fichier package.json
* ![Package manquant](../javascript/media/missing-npm.png) - Non installé, mais répertorié dans le fichier package.json

Cliquez avec le bouton droit sur un nœud de package ou le nœud **npm** pour effectuer l’une des actions suivantes :
* **Installer les packages manquants** qui sont répertoriés dans *package.json*
* **Mettre à jour les packages** vers la dernière version
* **Désinstaller un package** et supprimer *package.json*

## <a name="interactive"></a>Utiliser la commande .npm dans la fenêtre interactive de Node.js

Vous pouvez également utiliser la commande `.npm` dans la fenêtre interactive de Node.js pour exécuter des commandes npm. Pour ouvrir la fenêtre, cliquez avec le bouton droit sur le projet dans l’Explorateur de solutions et choisissez **Ouvrir une fenêtre interactive de Node.js**.

Dans la fenêtre, vous pouvez utiliser des commandes telles que les suivantes pour installer un package :

`.npm install azure@4.2.3`
 
 > [!Tip]
 > Par défaut, npm s’exécute dans le répertoire de base de votre projet. Si vous avez plusieurs projets dans votre solution, spécifiez le nom ou le chemin du projet entre crochets. 
 > `.npm [MyProjectNameOrPath] install azure@4.2.3`

 > [!Tip]
 > Si votre projet ne contient pas de fichier package.json, utilisez `.npm init -y` pour en créer un avec des entrées par défaut. 