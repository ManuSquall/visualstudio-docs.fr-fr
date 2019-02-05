---
title: 'Démarrage rapide : Utiliser Visual Studio pour créer votre première application Node.js'
description: Dans ce guide de démarrage rapide, vous créez une application Node.js dans Visual Studio
ms.date: 06/27/2018
ms.prod: visual-studio-dev15
ms.technology: vs-nodejs
ms.topic: quickstart
ms.devlang: javascript
ms.assetid: b0e4ebed-1a01-41ef-aad1-4d8465ce5322
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: f11396527208862428483744bc1ac3b02583f4c8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54955490"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-nodejs-app"></a>Démarrage rapide : Utiliser Visual Studio pour créer votre première application Node.js

Dans cette présentation de 5-10 minutes de l’environnement de développement intégré (IDE) de Visual Studio, vous allez créer une application Node.js simple. Si vous n’avez pas encore installé Visual Studio 2017, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) pour l’installer gratuitement.

## <a name="create-a-project"></a>Créer un projet

Vous allez d’abord créer un projet d’application web Node.js.

1. Si le runtime Node.js n’est pas déjà installé, installez la version LTS à partir du site web [Node.js](https://nodejs.org/en/download/).

    En règle générale, Visual Studio détecte automatiquement le runtime Node.js installé. S’il ne détecte aucun runtime installé, vous pouvez configurer votre projet pour référencer le runtime installé dans la page de propriétés (après avoir créé un projet, cliquez avec le bouton droit sur le nœud de projet, puis choisissez **Propriétés**).

1. Ouvrez Visual Studio 2017.

1. Dans la barre de menus supérieure, choisissez **Fichier** > **Nouveau** > **Projet**.

1. Dans la boîte de dialogue **Nouveau projet**, dans le volet gauche, développez **JavaScript**, puis choisissez **Node.js**. Dans le volet central, choisissez **Application web Node.js vide**, puis **OK**.

     Si vous ne voyez pas le modèle de projet **Application web Node.js vide**, cliquez sur le lien **Ouvrir Visual Studio Installer** dans le volet gauche de la boîte de dialogue **Nouveau projet**. Visual Studio Installer est lancé. Choisissez la charge de travail **Développement Node.js**, puis choisissez **Modifier**.

     ![Charge de travail Node.js dans Visual Studio Installer](../ide/media/quickstart-nodejs-workload.png)

    Une fois que vous avez choisi le modèle **Application web Node.js vide** et cliqué sur **OK**, Visual Studio crée la nouvelle solution et ouvre le projet. *server.js* s’ouvre dans l’éditeur, dans le volet gauche.

## <a name="explore-the-ide"></a>Explorer l’IDE

1. Observez **l’Explorateur de solutions** dans le volet droit.

   ![Explorateur de solutions](../ide/media/quickstart-nodejs-solution-explorer.png)

   - Votre projet mis en gras, avec le nom que vous avez donné dans la boîte de dialogue **Nouveau projet**. Sur le disque, ce projet est représenté par un fichier *.njsproj* dans le dossier de votre projet.

   - Au niveau le plus élevé figure une solution, qui a par défaut le même nom que votre projet. Une solution, représentée par un fichier *.sln* sur le disque, est un conteneur pour un ou plusieurs projets connexes.

   - Le nœud npm montre tous les packages npm installés. Vous pouvez cliquer avec le bouton droit sur le nœud npm pour rechercher et installer des packages npm à l’aide d’une boîte de dialogue.

1. Si vous souhaitez installer des packages npm ou des commandes Node.js à partir d’une invite de commandes, cliquez avec le bouton droit sur le nœud du projet et choisissez **Ouvrir l’invite de commandes ici**.

   ![Invite de commandes node.js](../ide/media/quickstart-nodejs-command-prompt.png)

1. Dans le fichier *server.js* dans l’éditeur (volet gauche), choisissez `http.createServer`, puis appuyez sur **F12** ou choisissez **Atteindre la définition** dans le menu contextuel (clic droit). Cette commande affiche la définition de la fonction `createServer` dans *index.d.ts*.

   ![Menu contextuel Atteindre la définition](../ide/media/quickstart-nodejs-gotodefinition.png)

1. Revenez à *server.js*, placez votre curseur à la fin de la chaîne sur la ligne de code suivante, `res.end('Hello World\n');`, puis modifiez-la pour qu’elle ressemble à ceci :

    `res.end('Hello World\n' + res.connection.`

    Quand vous tapez `connection.`, IntelliSense fournit des options de saisie semi-automatique du code.

   ![Saisie semi-automatique IntelliSense](../ide/media/quickstart-nodejs-intellisense.png)

1. Choisissez **localPort**, puis tapez `);` pour compléter l’instruction afin qu’elle ressemble à ceci :

    `res.end('Hello World\n' + res.connection.localPort);`

## <a name="run-the-application"></a>Exécuter l'application

1. Appuyez sur **Ctrl**+**F5** ou (**Déboguer > Démarrer sans débogage**) pour exécuter l’application. L’application s’ouvre dans un navigateur.

1. Dans la fenêtre du navigateur, le message « Hello World » s’affiche, accompagné du numéro de port local.

1. Fermez le navigateur web.

Félicitations, vous avez terminé ce guide de démarrage rapide. Vous en savez maintenant un peu plus sur l’IDE de Visual Studio et Node.js. Si vous souhaitez en savoir plus sur ses fonctionnalités, poursuivez avec l’un des tutoriels de la section **Tutoriels** dans la table des matières.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Déployer l’application sur Linux App Service](../javascript/publish-nodejs-app-azure.md)

- [Tutoriel pour Node.js et Express](../javascript/tutorial-nodejs.md)
- [Tutoriel pour Node.js et React](../javascript/tutorial-nodejs-with-react-and-jsx.md)