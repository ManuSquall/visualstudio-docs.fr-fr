---
title: "Bien démarrer avec Node.js dans Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 11/30/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-acquisition
ms.tgt_pltfrm: 
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: ghogen
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 1d91d46b20f82a1700c2d20639b3a8827c92bcb0
ms.sourcegitcommit: a07b789cc41ed72664f2c700c1f114476e7b0ddd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2018
---
# <a name="getting-started-with-nodejs-in-visual-studio"></a>Bien démarrer avec Node.js dans Visual Studio
Dans ce didacticiel pour le développement Node.js avec Visual Studio, vous allez créer une application web Node.js simple, ajouter du code, explorer certaines fonctionnalités de l’IDE et exécuter l’application. Si vous n’avez pas encore installé Visual Studio, installez-le gratuitement [ici](http://www.visualstudio.com).  

## <a name="create-a-project"></a>Créer un projet
Vous allez d’abord créer un projet d’application web Node.js.

1. Ouvrez Visual Studio 2017.  

2. Dans la barre de menus supérieure, choisissez **Fichier** > **Nouveau** > **Projet...**.  

3. Dans la boîte de dialogue **Nouveau projet**, dans le volet gauche, développez **JavaScript**, puis choisissez **Node.js**. Dans le volet central, choisissez **Application Azure Node.js Express 4 de base**, puis **OK**.   

     Si vous ne voyez pas le modèle de projet **Application Azure Node.js Express 4 de base**, cliquez sur le lien **Ouvrir Visual Studio Installer** dans le volet gauche de la boîte de dialogue **Nouveau projet**. Visual Studio Installer est lancé. Choisissez la charge de travail **Développement Node.js**, puis choisissez **Modifier**. 

    Visual Studio crée la solution et ouvre votre projet. Le fichier projet **app.js** s’ouvre dans l’éditeur (volet gauche). Si vous souhaitez d’abord vous familiariser avec les projets et solutions Visual Studio, consultez [Démarrage rapide : utiliser Visual Studio pour créer votre première application Node.js](../ide/quickstart-nodejs.md).

4. Si le runtime Node.js n’est pas déjà installé, installez-le à partir du site Web [Node.js](https://nodejs.org/en/download/).

    En règle générale, Visual Studio détecte automatiquement le runtime Node.js installé. S’il ne détecte aucun runtime installé, vous pouvez configurer votre projet pour faire référence au runtime installé.

## <a name="add-some-code"></a>Ajouter du code

1. Dans l’Explorateur de solutions (volet droit), ouvrez le dossier de vues, puis ouvrez index.pug.

1. Remplacez le contenu par le balisage suivant.

    ```js
    extends layout

    block content
      h1= title
      p Welcome to #{title}
      script.
        var f1 = function() { document.getElementById('myImage').src='#{data.item1}' }
      script.
        var f2 = function() { document.getElementById('myImage').src='#{data.item2}' }
      script.
        var f3 = function() { document.getElementById('myImage').src='#{data.item3}' }

      button(onclick='f1()') One!
      button(onclick='f2()') Two!
      button(onclick='f3()') Three!
      p
      a: img(id='myImage' height='200' width='200' src='')
    ```

1. Dans le dossier d’itinéraires, ouvrez index.js.

1. Ajoutez le code suivant avant l’appel à `router.get` :

    ```js
    var getData = function () {
        var data = {
            'item1': 'http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-76.jpg',
            'item2': 'http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-77.jpg',
            'item3': 'http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-78.jpg'
        }
        return data;
    }
    ````

1. Remplacez l’appel de fonction `router.get` par le code suivant :

    ```js
    router.get('/', function (req, res) {
        res.render('index', { title: 'Express', "data" });
    });
    ```

1. Après `data`, tapez `: get`. IntelliSense affiche la fonction getData. Sélectionnez `getData`.

    ![Utilisez IntelliSense](../nodejs/media/tutorial-nodejs-intellisense.png) 

1. Supprimez la virgule (`,`) avant `"data"`. La syntaxe de l’expression est colorée en vert. Pointez sur la coloration syntaxique.

    ![Afficher l’erreur de syntaxe](../nodejs/media/tutorial-nodejs-syntax-checking.png) 

    La dernière ligne de ce message indique que l’interpréteur JavaScript attendait une virgule (`,`).

1. Cliquez sur l’onglet **Liste d’erreurs**.

    Vous voyez l’avertissement et une description, ainsi que le nom de fichier et le numéro de ligne.

    ![Afficher la liste des erreurs](../nodejs/media/tutorial-nodejs-error-list.png)

1. Corrigez le code en ajoutant la virgule (`,`) avant `"data"`.

## <a name="set-a-breakpoint"></a>Définir un point d’arrêt

1. Dans index.js, cliquez dans la marge gauche avant la ligne suivante de code pour définir un point d’arrêt :

    `res.render('index', { title: 'Express', "data": getData() });`

    Les points d'arrêt constituent une fonctionnalité élémentaire et essentielle de toute procédure de débogage fiable. Quand vous définissez un point d'arrêt, Visual Studio interrompt l'exécution du code à l'emplacement du point d'arrêt pour vous permettre d'examiner les valeurs des variables, le comportement de la mémoire ou encore la bonne exécution ou non d'une branche de code. 

    ![Définir un point d’arrêt](../nodejs/media/tutorial-nodejs-set-breakpoint.png) 

## <a name="run-the-application"></a>Exécuter l'application

1. Sélectionnez la cible de débogage dans la barre d’outils Débogage.

    ![Sélectionner la cible de débogage](../nodejs/media/tutorial-nodejs-deploy-target.png) 

1. Appuyez sur **F5** (**Déboguer** > **Démarrer le débogage**) pour exécuter l’application.

    Le débogueur s’arrête au point d’arrêt que vous avez défini. Vous pouvez maintenant inspecter l’état de votre application.

1. Placez le curseur sur `getData` pour afficher ses propriétés dans un DataTip.

    ![Inspecter des variables](../nodejs/media/tutorial-nodejs-inspect-variables.png)

1. Appuyez sur **F5** (**Déboguer** > **Continuer**) pour continuer.

    L’application s’ouvre dans un navigateur.

    Dans la fenêtre du navigateur, « Express » est affiché comme titre et « Welcome to Express » est affiché dans le premier paragraphe.

1. Cliquez sur les boutons pour afficher différentes images.

    ![Exécution de l’application dans le navigateur](../nodejs/media/tutorial-nodejs-running-in-browser.png)  

1. Ouvrez la fenêtre interactive Node.js en sélectionnant **Afficher** > **Autres fenêtres** > **Fenêtre interactive Node.js**.

   ![Ouvrir la fenêtre interactive de Node.js](../nodejs/media/tutorial-nodejs-interactive-window.png)  

    La fenêtre interactive prend en charge tout ce que vous pouvez faire dans le code, notamment utiliser des instructions `require()`. Le code dans la capture d’écran suivante définit une variable et affiche l’emplacement de l’interpréteur Node.js.

   ![Fenêtre interactive de Node.js](../nodejs/media/tutorial-nodejs-interactive-window-example.png)  

1. Fermez le navigateur web.  

## <a name="optional-publish-to-azure-app-service"></a>Publier sur Azure App Service (facultatif)

1. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le projet et choisissez **Publier**.

   ![Publier sur Azure App Service](../nodejs/media/tutorial-nodejs-publish-to-azure.png)  

1. Choisissez **Microsoft Azure App Service**.

    Dans la boîte de dialogue **App Service**, vous pouvez vous connecter à votre compte Azure et vous connecter à des abonnements Azure existants.

1. Suivez les étapes restantes pour sélectionner un abonnement, choisir ou créer un groupe de ressources, et choisir ou créer un plan de service d’application, puis suivez les étapes quand vous êtes invité à publier sur Azure. Pour obtenir des instructions détaillées, consultez [Publier sur un site web Azure avec Web Deploy](https://github.com/Microsoft/nodejstools/wiki/Publish-to-Azure-Website-using-Web-Deploy).

1. La fenêtre **Sortie** montre la progression du déploiement sur Azure.

    Une fois le déploiement terminé, votre application s’ouvre dans un navigateur exécuté dans Azure App Service. Cliquez sur un bouton pour afficher une image.

   ![Application en cours d’exécution dans Azure App Service](../nodejs/media/tutorial-nodejs-running-in-azure.png)  

Félicitations ! Vous avez terminé ce didacticiel.

## <a name="next-steps"></a>Étapes suivantes 

- En savoir plus sur les [Outils Node.js pour Visual Studio](https://github.com/Microsoft/nodejstools/wiki)  
- En savoir plus sur [l’IDE Visual Studio](../ide/visual-studio-ide.md)  