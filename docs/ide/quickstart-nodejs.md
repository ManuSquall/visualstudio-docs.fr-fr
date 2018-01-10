---
title: "Démarrage rapide : utiliser Visual Studio pour créer votre première application Node.js | Microsoft Docs"
ms.custom: 
ms.date: 11/15/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: quickstart
ms.devlang: javascript
ms.assetid: b0e4ebed-1a01-41ef-aad1-4d8465ce5322
author: mikejo5000
ms.author: mikejo
manager: ghogen
dev_langs: JavaScript
ms.workload: nodejs
ms.openlocfilehash: 12c848797b167038b02106ca3392cac50171f699
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="quickstart-use-visual-studio-to-create-your-first-nodejs-app"></a>Démarrage rapide : utiliser Visual Studio pour créer votre première application Node.js
Dans cette présentation de 5-10 minutes de l’environnement de développement intégré (IDE) de Visual Studio, vous allez créer une application Node.js simple. Si vous n’avez pas encore installé Visual Studio, installez-le gratuitement [ici](http://www.visualstudio.com).  

## <a name="create-a-project"></a>Créer un projet
Vous allez d’abord créer un projet d’application web Node.js.

1. Ouvrez Visual Studio 2017.  

2. Dans la barre de menus supérieure, choisissez **Fichier** > **Nouveau** > **Projet...**.  

3. Dans la boîte de dialogue **Nouveau projet**, dans le volet gauche, développez **JavaScript**, puis choisissez **Node.js**. Dans le volet central, choisissez **Application web Node.js vide**, puis **OK**.   

     Si vous ne voyez pas le modèle de projet **Application web Node.js vide**, cliquez sur le lien **Ouvrir Visual Studio Installer** dans le volet gauche de la boîte de dialogue **Nouveau projet**. Visual Studio Installer est lancé. Choisissez la charge de travail **Développement Node.js**, puis choisissez **Modifier**.  

     ![Charge de travail Node.js dans Visual Studio Installer](../ide/media/quickstart-nodejs-workload.png)  

    Visual Studio crée la nouvelle solution et ouvre le projet. **server.js** s’ouvre dans l’éditeur.

## <a name="explore-the-ide"></a>Explorer l’IDE  

1. Observez **l’Explorateur de solutions** dans le volet droit.

   ![Explorateur de solutions](../ide/media/quickstart-nodejs-solution-explorer.png)  

  - Votre projet mis en gras, avec le nom que vous avez donné dans la boîte de dialogue **Nouveau projet**. Sur le disque, ce projet est représenté par un fichier .njsproj dans le dossier de votre projet.

  - Au niveau le plus élevé figure une solution, qui a par défaut le même nom que votre projet. Une solution, représentée par un fichier .sln sur le disque, est un conteneur pour un ou plusieurs projets connexes.

  - Le nœud npm montre tous les packages npm installés. Vous pouvez cliquer avec le bouton droit sur le nœud npm pour rechercher et installer des packages npm à l’aide d’une boîte de dialogue.

1. Si vous souhaitez installer des packages npm ou des commandes node.js à partir d’une invite de commandes, cliquez avec le bouton droit sur le nœud du projet et choisissez **Ouvrir l’invite de commandes ici**.

   ![Invite de commandes node.js](../ide/media/quickstart-nodejs-command-prompt.png) 

1. Dans le fichier **server.js** dans l’éditeur (volet gauche), choisissez `http.createServer`, puis appuyez sur **F12** ou choisissez **Atteindre la définition** dans le menu contextuel (clic droit). Cette commande affiche la définition de la fonction `createServer` dans index.d.ts.  

   ![Menu contextuel Atteindre la définition](../ide/media/quickstart-nodejs-gotodefinition.png)  

1. Placez le curseur à la fin de la chaîne sur cette ligne de code, `res.end('Hello World\n');`, et modifiez-la afin qu’elle ressemble à ceci :

    `res.end('Hello World\n' + res.connection.`

    Quand vous tapez `connection.`, IntelliSense fournit des options de saisie semi-automatique du code.

   ![Saisie semi-automatique IntelliSense](../ide/media/quickstart-nodejs-intellisense.png)  

1. Choisissez **localPort**, puis tapez `);` pour compléter l’instruction afin qu’elle ressemble à ceci :

    `res.end('Hello World\n' + res.connection.localPort);`

## <a name="run-the-application"></a>Exécuter l'application
1. Appuyez sur **Ctrl+F5** ou (**Déboguer > Démarrer sans débogage**) pour exécuter l’application. L’application s’ouvre dans un navigateur.  

1. Dans la fenêtre du navigateur, le message « Hello World » s’affiche, accompagné du numéro de port local.

1. Fermez le navigateur web.  

Félicitations ! Vous avez terminé ce guide de démarrage rapide. Nous espérons que vous en avez appris un peu plus sur l’IDE de Visual Studio. Si vous souhaitez en savoir plus sur ses fonctionnalités, poursuivez avec un didacticiel de la section **Didacticiels** dans la table des matières.  

## <a name="next-steps"></a>Étapes suivantes 

- Effectuer le [Didacticiel pour Node.js](../nodejs/tutorial-nodejs.md)  
- En savoir plus sur [l’IDE Visual Studio](../ide/visual-studio-ide.md)  
- En savoir plus sur les [Outils Node.js pour Visual Studio](https://github.com/Microsoft/nodejstools/wiki)