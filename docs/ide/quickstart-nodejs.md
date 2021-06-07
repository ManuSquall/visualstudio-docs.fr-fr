---
title: Créer votre première application Node.js
ms.custom: SEO-VS-2020
description: Dans ce guide de démarrage rapide, vous créez une application Node.js dans Visual Studio
ms.date: 03/25/2021
ms.technology: vs-javascript
ms.topic: quickstart
ms.devlang: javascript
ms.assetid: b0e4ebed-1a01-41ef-aad1-4d8465ce5322
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 8a36986842cdac85a8a3e6ab474024b8db552ee7
ms.sourcegitcommit: ab5735d64a6ad7aecabf5d6df159888e3246bff5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2021
ms.locfileid: "111433712"
---
# <a name="quickstart-create-your-first-nodejs-app-with-visual-studio"></a>Démarrage rapide : créer votre première Node.js application avec Visual Studio

Dans cette présentation de 5 à 10 minutes de l’environnement de développement intégré (IDE) de Visual Studio, vous allez créer une simple Node.js application Web.

## <a name="prerequisites"></a>Prérequis

Avant de commencer, installez Visual Studio et configurez votre environnement de Node.js.

### <a name="install-visual-studio"></a>Installation de Visual Studio

::: moniker range=">=vs-2019"
Si vous n’avez pas encore installé Visual Studio 2019, accédez à la page [téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads) pour l’installer gratuitement.
::: moniker-end
::: moniker range="vs-2017"
Si vous n’avez pas encore installé Visual Studio 2017, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) pour l’installer gratuitement.
::: moniker-end

### <a name="set-up-your-nodejs-environment"></a>Configurer votre environnement de Node.js

Visual Studio peut vous aider à configurer votre environnement, y compris l’installation d’outils communs au développement Node.js.

1. Dans Visual Studio, accédez à **Outils**  >  **accéder aux outils et aux fonctionnalités**.

1. Dans la Visual Studio Installer, choisissez la charge de travail **développementNode.js** et sélectionnez **modifier** pour télécharger et installer la charge de travail.

    ![Charge de travail Node.js dans Visual Studio Installer](../ide/media/quickstart-nodejs-workload.png)

1. Installez la version LTS du [ runtimeNode.js](https://nodejs.org/en/download/). Nous vous recommandons la version LTS pour une meilleure compatibilité avec les infrastructures et les bibliothèques externes.

    Bien que Node.js soit conçu pour les architectures 32 bits et 64 bits, le programme d’installation Node.js prend uniquement en charge une version installée à la fois.

1. Si Visual Studio ne détecte pas votre Runtime installé (ce qui est généralement le cas), configurez votre projet pour référencer le Runtime installé :

   1. Après avoir [créé votre projet](#create-your-app-project), cliquez avec le bouton droit sur le nœud du projet.

   1. Sélectionnez **Propriétés** et définissez le **chemin d’accèsNode.exe**. Vous pouvez utiliser une installation globale de Node.js ou spécifier le chemin d’accès à un interpréteur local dans chacun de vos projets Node.js.

## <a name="create-your-app-project"></a>Créer un projet d’application

1. Si vous ne l’avez pas encore fait, installez la version LTS du [ runtimeNode.js](https://nodejs.org/en/download/). Pour plus d’informations, voir les [Conditions préalables](#prerequisites).

1. Ouvrez Visual Studio.

1. Créez un projet.

    ::: moniker range=">=vs-2019"

    1. Appuyez sur **Échap** pour fermer la fenêtre de démarrage.

    1. Appuyez sur **CTRL + Q** pour ouvrir la zone de recherche, puis tapez **Node.js**.

    1. Choisissez **vide Node.js application Web (JavaScript)**. Dans la boîte de dialogue, sélectionnez **créer**.

    ::: moniker-end

    ::: moniker range="vs-2017"
    1. Dans la barre de menus supérieure, choisissez **fichier** > **nouveau** > **projet**.

    1. Dans le volet gauche de la boîte de dialogue **nouveau projet** , développez **JavaScript** , puis choisissez **Node.js**.

    1. Dans le volet central, choisissez **vide Node.js application Web** , puis cliquez sur **OK**.

    ::: moniker-end
    
    Si vous ne voyez pas le modèle de projet **Application web Node.js vide**, vous devez ajouter la charge de travail **Développement Node.js**. Pour obtenir des instructions détaillées, consultez les [conditions préalables](#prerequisites).

    Visual Studio crée et ouvre le projet. Le fichier *server.js* du projet s’ouvre dans l’éditeur sur la gauche.

## <a name="explore-the-ide"></a>Explorer l’IDE

1. Dans le volet droit, examinez **Explorateur de solutions**.

   ![Explorateur de solutions](../ide/media/quickstart-nodejs-solution-explorer.png)

   - Votre projet est mis en surbrillance en gras, en utilisant le nom fourni lorsque vous configurez le projet. Sur le disque, ce projet est représenté par un fichier *. njsproj* dans le dossier de votre projet.

   - Au niveau le plus élevé figure une solution, qui a par défaut le même nom que votre projet. Une solution, représentée par un fichier *.sln* sur le disque, est un conteneur pour un ou plusieurs projets connexes.

   - Le nœud **NPM** affiche les packages NPM installés. Vous pouvez cliquer avec le bouton droit sur le nœud NPM pour rechercher et installer des packages NPM à l’aide d’une boîte de dialogue.

1. Si vous souhaitez installer des packages NPM ou des commandes Node.js à partir d’une invite de commandes, cliquez avec le bouton droit sur le nœud du projet et choisissez **ouvrir l’invite de commandes ici**.

   ![Invite de commandes du nœud point j s](../ide/media/quickstart-nodejs-command-prompt.png)

1. Si vous souhaitez tester la navigation vers le code source, à partir du fichier Open *server.js* , sélectionnez **http. createServer** , puis appuyez sur **F12** ou choisissez **atteindre la définition** dans le menu contextuel (clic droit). Cette commande vous permet d’accéder à la définition de la `createServer` fonction dans *http. d. TS*.

   ![Menu contextuel Atteindre la définition](../ide/media/quickstart-nodejs-gotodefinition.png)

1. Revenez à *server.js* et recherchez la ligne de code suivante : `res.end('Hello World\n');` . Modifiez le code comme suit :

    `res.end('Hello World\n' + res.connection.`

    Lorsque vous tapez **Connection.**, IntelliSense fournit des options pour la saisie semi-automatique de l’entrée de code.

   ![Saisie semi-automatique IntelliSense](../ide/media/quickstart-nodejs-intellisense.png)

1. Choisissez **localPort** et type **);** pour compléter l’instruction :

    `res.end('Hello World\n' + res.connection.localPort);`

## <a name="run-the-app"></a>Exécuter l’application

1. Appuyez sur **CTRL + F5** (ou **Déboguer** exécuter  >  **sans débogage**) pour exécuter l’application. 
 
   L’application s’ouvre dans un navigateur.

1. Dans le navigateur, vérifiez que vous voyez un message « Hello World » et le numéro de port local.

Félicitations ! Vous avez créé une application Node.js simple avec Visual Studio. Pour approfondir, poursuivez la section **didacticiels** de la table des matières.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Déployer l’application sur Linux App Service](../javascript/publish-nodejs-app-azure.md)

> [!div class="nextstepaction"]
> [Tutoriel pour Node.js et Express](../javascript/tutorial-nodejs.md)

> [!div class="nextstepaction"]
> [Tutoriel pour Node.js et React](../javascript/tutorial-nodejs-with-react-and-jsx.md)
