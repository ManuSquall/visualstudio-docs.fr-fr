---
title: Créer une application Node.js et Express
description: Dans ce didacticiel, vous allez apprendre à créer une application Node.js simple à l’aide de l’infrastructure d’application Web Express dans Visual Studio.
ms.date: 03/25/2021
ms.custom: vs-acquisition
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: d4ea086d20f5a1000067343ac7571a9a8f8309db
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386811"
---
# <a name="tutorial-create-a-nodejs-and-express-app-in-visual-studio"></a>Tutoriel : Créer une application Node.js et Express dans Visual Studio

Dans ce tutoriel de développement Visual Studio en Node.js et Express, vous allez créer une application web Node.js simple, ajouter du code, explorer certaines fonctionnalités de l’IDE, puis exécuter l’application en question. 

::: moniker range="vs-2017"

Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) pour l’installer gratuitement.

::: moniker-end

::: moniker range=">=vs-2019"

Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads) pour l’installer gratuitement.

::: moniker-end

::: moniker range="vs-2022"

Si vous n’avez pas encore installé Visual Studio 2022 Preview, accédez à la page [téléchargements Visual studio 2022 Preview](https://visualstudio.microsoft.com/vs/preview/vs2022) pour l’installer gratuitement.

::: moniker-end

Dans ce tutoriel, vous allez apprendre à :
> [!div class="checklist"]
> * Créer un projet Node.js
> * Ajouter du code
> * Utiliser IntelliSense pour modifier du code
> * Exécuter l’application
> * Atteindre un point d’arrêt dans le débogueur

## <a name="before-you-begin"></a>Avant de commencer

Voici un petit forum aux questions qui présente quelques concepts clés.

### <a name="what-is-nodejs"></a>Qu’est-ce que Node.js ?

Node.js est un environnement d’exécution JavaScript côté serveur qui exécute JavaScript côté serveur.

### <a name="what-is-npm"></a>Qu’est-ce que npm ?

npm est le Gestionnaire de package par défaut de Node.js. Le Gestionnaire de package permet aux programmeurs de publier et partager plus facilement le code source des bibliothèques Node.js. Il est conçu pour simplifier l’installation, la mise à jour et la désinstallation des bibliothèques.

### <a name="what-is-express"></a>Qu’est-ce qu’express ?

Express est un framework d’application web utilisé comme framework serveur pour Node.js, qui permet de générer des applications web. Express vous permet de choisir différentes infrastructures frontales pour créer une interface utilisateur, telle que Pug (anciennement appelée Jade). Pug est utilisé dans ce tutoriel.

## <a name="prerequisites"></a>Prérequis

* Au préalable, vous devez avoir installé Visual Studio et la charge de travail de développement Node.js.

    ::: moniker range=">=vs-2019"
    Si vous n’avez pas encore installé Visual Studio 2019, accédez à la page [téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads/) pour l’installer gratuitement.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Si vous n’avez pas encore installé Visual Studio 2017, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads/) pour l’installer gratuitement.
    ::: moniker-end

    Si vous devez installer la charge de travail mais que vous disposez déjà de Visual Studio, accédez à **Outils**  >  **obtenir des outils et des fonctionnalités...**, qui ouvre le Visual Studio installer. Choisissez la charge de travail **Développement Node.js**, puis choisissez **Modifier**.

    ![Charge de travail Node.js dans Visual Studio Installer](../ide/media/quickstart-nodejs-workload.png)

* Le runtime Node.js doit être installé.

    Si vous ne l’avez pas installé, nous vous recommandons d’installer la version LTS à partir du site Web [Node.js](https://nodejs.org/en/download/) pour une meilleure compatibilité avec les frameworks et les bibliothèques externes. Node.js est conçu pour les architectures 32 bits et 64 bits. Les outils de Node.js dans Visual Studio, inclus dans la charge de travail Node.js, prennent en charge les deux versions. Une seule est requise et le programme d’installation de Node.js ne prend en charge qu’une seule installation à la fois.
    
    En règle générale, Visual Studio détecte automatiquement le runtime Node.js installé. S’il ne détecte pas un Runtime installé, vous pouvez configurer votre projet pour référencer le Runtime installé dans la page Propriétés (après avoir créé un projet, cliquer avec le bouton droit sur le nœud du projet, choisir **Propriétés** et définir le **chemin d’accèsNode.exe**). Vous pouvez utiliser une installation globale de Node.js ou vous pouvez spécifier le chemin d’accès à un interpréteur local dans chacun de vos projets Node.js. 

    Ce tutoriel a été testé avec Node.js 8.10.0.

## <a name="create-a-new-nodejs-project"></a>Créer un projet Node.js

Visual Studio gère les fichiers d’une seule application dans un *projet*. Le projet comprend le code source, les ressources et les fichiers config.

Dans ce tutoriel, vous commencez avec un projet simple contenant du code pour une application Node.js et express.

1. Ouvrez Visual Studio.

1. Créez un projet.

    ::: moniker range=">=vs-2019"
    Appuyez sur **Échap** pour fermer la fenêtre de démarrage. Tapez **Ctrl+Q** pour ouvrir la zone de recherche, tapez **Node.js**, puis choisissez **Créer une nouvelle application Azure Node.js Express 4 de base** (JavaScript). Dans la boîte de dialogue qui apparaît, choisissez **Créer**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Dans la barre de menus supérieure, choisissez **fichier**  >  **nouveau**  >  **projet**. Dans la boîte de dialogue **Nouveau projet**, développez **JavaScript**, puis choisissez **Node.js**. Dans le volet central, choisissez **Application Azure Node.js Express 4 de base**, puis choisissez **OK**.
    ::: moniker-end
    Si vous ne voyez pas le modèle de projet **Application Azure Node.js Express 4 de base**, vous devez ajouter la charge de travail **Développement Node.js**. Pour obtenir des instructions détaillées, consultez les [Prérequis](#prerequisites).

    Visual Studio crée la solution et ouvre votre projet dans le volet droit. Le fichier projet *app.js* s’ouvre dans l’éditeur (volet gauche).

    ![Structure du projet](../javascript/media/tutorial-project-structure.png)

    (1) Votre projet est mis en **gras**, avec le nom que vous avez donné dans la boîte de dialogue **Nouveau projet**. Dans le système de fichiers, ce projet est représenté par un fichier *.njsproj* au sein de votre dossier de projet. Vous pouvez définir les propriétés et les variables d’environnement associées au projet en cliquant avec le bouton droit sur le projet et en choisissant **Propriétés**. Vous pouvez effectuer des allers-retours avec d’autres outils de développement, car le fichier projet n’apporte pas de changements personnalisés à la source de projet Node.js.

    (2) Au niveau supérieur figure une solution, qui a par défaut le même nom que votre projet. Une solution, représentée par un fichier *.sln* sur le disque, est un conteneur pour un ou plusieurs projets connexes.

    (3) Le nœud npm montre tous les packages npm installés. Vous pouvez cliquer avec le bouton droit sur le nœud npm pour rechercher et installer des packages npm à l’aide d’une boîte de dialogue, ou vous pouvez installer et mettre à jour des packages à l’aide des paramètres de *package.json* et des options de menu contextuel du nœud npm.

    (4) *package.json* est un fichier utilisé par npm pour gérer les dépendances de packages et les versions de packages des packages installés localement. Pour plus d’informations, consultez [gérer les packages NPM](../javascript/npm-package-management.md).

    (5) Les fichiers projet tels que *app.js* s’affichent sous le nœud de projet. *app.js* est le fichier de démarrage du projet. C’est la raison pour laquelle il s’affiche en **gras**. Vous pouvez définir le fichier de démarrage en cliquant avec le bouton droit sur un fichier du projet et en sélectionnant **Définir comme fichier de démarrage de Node.js**.

1. Ouvrez le nœud **npm** et vérifiez que tous les packages npm nécessaires sont présents.

    Si des packages sont manquants (icône de point d’exclamation), vous pouvez cliquer avec le bouton droit sur le nœud **NPM** et choisir **installer des packages NPM**.

## <a name="add-some-code"></a>Ajouter du code

L’application utilise Pug en tant que framework JavaScript frontend. Pug utilise du code simple à base de balises, qui est compilé en HTML. (Pug est défini en tant que moteur de vue dans *app.js*. Le code qui définit le moteur de vue dans *app.js* est `app.set('view engine', 'pug');`.)

1. Dans l’Explorateur de solutions (volet droit), ouvrez le dossier de vues, puis ouvrez *index.pug*.

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

    Le code qui précède est utilisé pour générer dynamiquement une page HTML avec un titre et un message de bienvenue. Cette page inclut également un code pour afficher une image qui change chaque fois que vous appuyez sur un bouton.

1. Dans le dossier d’itinéraires, ouvrez *index.js*.

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

    Ce code crée un objet de données que vous passez à la page HTML générée dynamiquement.

1. Remplacez l’appel de fonction `router.get` par le code suivant :

    ```js
    router.get('/', function (req, res) {
        res.render('index', { title: 'Express', "data" });
    });
    ```

    Le code précédent définit la page actuelle à l’aide de l’objet de routeur Express et restitue la page, en envoyant l’objet de données et le titre de la page. Le fichier *index.pug* est spécifié ici en tant que page à charger quand *index.js* s’exécute. *index.js* est configuré en tant qu’itinéraire par défaut dans le code d’*app.js* (non affiché).

    Pour illustrer plusieurs fonctionnalités de Visual Studio, une erreur délibérée figure dans la ligne de code contenant `res.render`. Vous devez corriger l’erreur pour que l’application puisse s’exécuter, ce que vous allez faire dans la section suivante.

## <a name="use-intellisense"></a>Utiliser IntelliSense

IntelliSense est un outil Visual Studio qui vous aide pendant que vous écrivez du code.

1. Dans *index.js*, accédez à la ligne de code contenant `res.render`.

1. Placez votre curseur après la chaîne `data`, tapez `: get`, et IntelliSense vous affichera la fonction `getData` définie plus tôt dans le code. Sélectionnez `getData`.

    ![Utiliser IntelliSense](../javascript/media/tutorial-nodejs-intellisense.png)

1. Ajoutez les parenthèses pour en faire un appel de fonction, `getData()` .

1. Supprimez la virgule (`,`) avant `"data"`. La syntaxe de l’expression est colorée en vert. Pointez sur la coloration syntaxique.

    ![Afficher l’erreur de syntaxe](../javascript/media/tutorial-nodejs-syntax-checking.png)

    La dernière ligne de ce message indique que l’interpréteur JavaScript attendait une virgule (`,`).

1. Dans le volet inférieur, cliquez sur l’onglet **liste d’erreurs** et sélectionnez **générer + IntelliSense** pour le type de problèmes signalés.

    Vous voyez l’avertissement et une description, ainsi que le nom de fichier et le numéro de ligne.

    ![Afficher la liste des erreurs](../javascript/media/tutorial-nodejs-error-list.png)

1. Corrigez le code en ajoutant la virgule (`,`) avant `"data"`.

    La ligne de code corrigée doit ressembler à ceci : `res.render('index', { title: 'Express', "data": getData() });`

## <a name="set-a-breakpoint"></a>Définir un point d'arrêt

Vous allez ensuite exécuter l’application avec le débogueur Visual Studio attaché. Avant cela, vous devez définir un point d’arrêt.

1. Dans *index.js*, cliquez dans la marge gauche avant la ligne de code suivante pour définir un point d’arrêt :

    `res.render('index', { title: 'Express', "data": getData() });`

    Les points d'arrêt constituent une fonctionnalité élémentaire et essentielle de toute procédure de débogage fiable. Quand vous définissez un point d'arrêt, Visual Studio interrompt l'exécution du code à l'emplacement du point d'arrêt pour vous permettre d'examiner les valeurs des variables, le comportement de la mémoire ou encore la bonne exécution ou non d'une branche de code.

    ![Définir un point d'arrêt](../javascript/media/tutorial-nodejs-set-breakpoint.png)

## <a name="run-the-application"></a>Exécution de l'application

1. Sélectionnez la cible de débogage dans la barre d’outils déboguer, par exemple **serveur Web (Google Chrome)** ou **serveur Web (Microsoft Edge)**.

    ::: moniker range=">=vs-2019"
    ![Sélectionner la cible de débogage](../javascript/media/vs-2019/tutorial-nodejs-deploy-target.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![Sélectionner la cible de débogage](../javascript/media/tutorial-nodejs-deploy-target.png)
    ::: moniker-end

    Si Chrome est disponible sur votre ordinateur, mais n’apparaît pas dans les options, choisissez **Naviguer avec** dans la liste déroulante des cibles de débogage et sélectionnez Chrome comme cible de navigateur par défaut (choisissez **Définir comme programme par défaut**).

1. Appuyez sur **F5** (**Déboguer** > **Démarrer le débogage**) pour exécuter l’application.

    Le débogueur s’arrête au point d’arrêt que vous avez défini. Vous pouvez maintenant inspecter l’état de votre application.

1. Placez le curseur sur `getData` pour afficher ses propriétés dans un DataTip.

    ![Inspecter des variables](../javascript/media/tutorial-nodejs-inspect-variables.png)

1. Appuyez sur **F5** (**Déboguer** > **Continuer**) pour continuer.

    L’application s’ouvre dans un navigateur.

    Dans la fenêtre du navigateur, « Express » est affiché comme titre et « Welcome to Express » est affiché dans le premier paragraphe.

1. Cliquez sur les boutons pour afficher différentes images.

    ![Exécution de l’application dans le navigateur](../javascript/media/tutorial-nodejs-running-in-browser.png)

1. Fermez le navigateur web.

## <a name="optional-publish-to-azure-app-service"></a>Publier sur Azure App Service (facultatif)

1. Dans Explorateur de solutions, cliquez avec le bouton droit sur le projet et choisissez **publier**.

   ![Publier sur Azure App Service](../javascript/media/tutorial-nodejs-publish-to-azure.png)

1. Choisissez **Microsoft Azure App Service**.

    Dans la boîte de dialogue **App Service**, vous pouvez vous connecter à votre compte Azure et vous connecter à des abonnements Azure existants.

1. Suivez les étapes restantes pour sélectionner un abonnement, choisir ou créer un groupe de ressources, et choisir ou créer un plan de service d’application, puis suivez les étapes quand vous êtes invité à publier sur Azure. Pour obtenir des instructions plus détaillées, consultez [Publier sur un site web Azure avec Web Deploy](https://github.com/Microsoft/nodejstools/wiki/Publish-to-Azure-Website-using-Web-Deploy).

1. La fenêtre **Sortie** montre la progression du déploiement sur Azure.

    Une fois le déploiement terminé, votre application s’ouvre dans un navigateur exécuté dans Azure App Service. Cliquez sur un bouton pour afficher une image.

   ![Application en cours d’exécution dans Azure App Service](../javascript/media/tutorial-nodejs-running-in-azure.png)

Félicitations ! Vous avez terminé ce didacticiel.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Déployer l’application sur Linux App Service](../javascript/publish-nodejs-app-azure.md)

> [!div class="nextstepaction"]
> [Extension du service de langage AngularJS](https://devblogs.microsoft.com/visualstudio/angular-language-service-for-visual-studio)
