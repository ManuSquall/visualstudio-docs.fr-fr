---
title: Créer une application Node.js et React
description: Découvrez comment créer un projet d’application Web Node.js à partir d’un modèle Visual Studio.
ms.custom: vs-acquisition
ms.date: 4/21/2020
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 9a45be2c18466754fba5469c59396f7a7791156d
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386837"
---
# <a name="tutorial-create-a-nodejs-and-react-app-in-visual-studio"></a>Tutoriel : Créer une application Node.js et React dans Visual Studio

Visual Studio vous permet de créer facilement un projet Node.js et de tirer parti d’IntelliSense et d’autres fonctionnalités intégrées prenant en charge Node.js. Dans ce tutoriel pour Visual Studio, vous créez un projet d’application web Node.js à partir d’un modèle Visual Studio. Vous créez ensuite une application simple avec React.

Dans ce tutoriel, vous allez apprendre à :
> [!div class="checklist"]
> * Créer un projet Node.js
> * Ajouter des packages npm
> * Ajouter du code React à votre application
> * Transpiler du code JSX
> * Attacher le débogueur

## <a name="before-you-begin"></a>Avant de commencer

Voici un petit forum aux questions qui présente quelques concepts clés.

### <a name="what-is-nodejs"></a>Qu’est-ce que Node.js ?

Node.js est un environnement d’exécution JavaScript côté serveur qui exécute JavaScript côté serveur.

### <a name="what-is-npm"></a>Qu’est-ce que npm ?

npm est le Gestionnaire de package par défaut de Node.js. Le Gestionnaire de package permet aux programmeurs de publier et partager plus facilement le code source des bibliothèques Node.js. Il est conçu pour simplifier l’installation, la mise à jour et la désinstallation des bibliothèques.

### <a name="what-is-react"></a>Présentation de React

React est une infrastructure frontend pour créer une interface utilisateur.

### <a name="what-is-jsx"></a>Présentation de JSX

JSX est une extension de syntaxe JavaScript, généralement utilisée avec React pour décrire des éléments d’interface utilisateur. Le code JSX doit être transpilé en JavaScript standard avant de pouvoir être exécuté dans un navigateur.

### <a name="what-is-webpack"></a>Présentation de webpack

webpack regroupe des fichiers JavaScript pour qu’ils puissent s’exécuter dans un navigateur. Il peut également transformer ou packager d’autres ressources et composants. Il est souvent utilisé pour spécifier un compilateur, comme Babel ou TypeScript, pour transpiler du code JSX ou TypeScript en code JavaScript standard.

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

    Ce didacticiel a été testé avec la version 12.6.2.

    Si vous ne l’avez pas installé, nous vous recommandons d’installer la version LTS à partir du site Web [Node.js](https://nodejs.org/en/download/) pour une meilleure compatibilité avec les frameworks et les bibliothèques externes. Node.js est conçu pour les architectures 32 bits et 64 bits. Les outils de Node.js dans Visual Studio, inclus dans la charge de travail Node.js, prennent en charge les deux versions. Une seule est requise et le programme d’installation de Node.js ne prend en charge qu’une seule installation à la fois.

    En règle générale, Visual Studio détecte automatiquement le runtime Node.js installé. S’il ne détecte pas un Runtime installé, vous pouvez configurer votre projet pour qu’il référence le Runtime installé dans la page Propriétés (après avoir créé un projet, cliquez avec le bouton droit sur le nœud du projet, choisissez **Propriétés** (ou appuyez sur **ALT**  +  **entrée**), puis définissez le **chemin d’accèsNode.exe**). Vous pouvez utiliser une installation globale de Node.js ou vous pouvez spécifier le chemin d’accès à un interpréteur local dans chacun de vos projets Node.js. 

## <a name="create-a-project"></a>Création d’un projet

Commencez par créer un projet d’application web Node.js.

1. Ouvrez Visual Studio.

1. Créez un projet.

    ::: moniker range=">=vs-2019"
    Appuyez sur **Échap** pour fermer la fenêtre de démarrage. Tapez **CTRL + Q** pour ouvrir la zone de recherche, tapez **Node.js**, puis choisissez **vide Node.js application Web-JavaScript**. (Bien que ce didacticiel utilise le compilateur de machine à écrire, les étapes requièrent que vous démarriez avec le modèle **JavaScript** .)
    
    Dans la boîte de dialogue qui apparaît, choisissez **Créer**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Dans la barre de menus supérieure, choisissez **fichier**  >  **nouveau**  >  **projet**. Dans la boîte de dialogue **Nouveau projet**, développez **JavaScript**, puis choisissez **Node.js**. Dans le volet central, choisissez **Application web Node.js vide**, tapez le nom **NodejsWebAppBlank**, puis choisissez **OK**.
    ::: moniker-end
    Si vous ne voyez pas le modèle de projet d' **application Web vide Node.js** , vous devez ajouter la charge de travail de **développementNode.js** . Pour obtenir des instructions détaillées, consultez les [Prérequis](#prerequisites).

    Visual Studio crée la solution et ouvre votre projet.

    ![Projet Node.js dans l’Explorateur de solutions](../javascript/media/tutorial-nodejs-react-project-structure.png)

    (1) Votre projet est mis en **gras**, avec le nom que vous avez donné dans la boîte de dialogue **Nouveau projet**. Dans le système de fichiers, ce projet est représenté par un fichier *.njsproj* au sein de votre dossier de projet. Vous pouvez définir les propriétés et les variables d’environnement associées au projet en cliquant avec le bouton droit sur le projet et en sélectionnant **Propriétés** (ou en appuyant sur **ALT**  +  **entrée**). Vous pouvez effectuer des allers-retours avec d’autres outils de développement, car le fichier projet n’apporte pas de changements personnalisés à la source de projet Node.js.

    (2) Au niveau supérieur figure une solution, qui a par défaut le même nom que votre projet. Une solution, représentée par un fichier *.sln* sur le disque, est un conteneur pour un ou plusieurs projets connexes.

    (3) Le nœud npm montre tous les packages npm installés. Vous pouvez cliquer avec le bouton droit sur le nœud npm pour rechercher et installer des packages npm à l’aide d’une boîte de dialogue, ou vous pouvez installer et mettre à jour des packages à l’aide des paramètres de *package.json* et des options de menu contextuel du nœud npm.

    (4) *package.json* est un fichier utilisé par npm pour gérer les dépendances de packages et les versions de packages des packages installés localement. Pour plus d’informations, consultez [gérer les packages NPM](../javascript/npm-package-management.md).

    (5) Les fichiers projet, comme *server.js*, apparaissent sous le nœud de projet. *server.js* est le fichier de démarrage du projet. C’est la raison pour laquelle il apparaît en **gras**. Vous pouvez définir le fichier de démarrage en cliquant avec le bouton droit sur un fichier du projet et en sélectionnant **Définir comme fichier de démarrage de Node.js**.

## <a name="add-npm-packages"></a>Ajouter des packages npm

Cette application nécessite un certain nombre de modules npm pour s’exécuter correctement.

* react
* react-dom
* express
* path
* ts-loader
* typescript
* webpack
* webpack-cli

1. Dans l’Explorateur de solutions (volet droit), cliquez avec le bouton droit sur le nœud **npm** du projet, puis choisissez **Installer de nouveaux packages npm**.

    Dans la boîte de dialogue **Installer de nouveaux packages npm**, vous pouvez choisir d’installer la version de package la plus récente ou une version spécifique. Si vous choisissez d’installer la version actuelle de ces packages, mais que vous rencontrez plus tard des erreurs inattendues, vous souhaiterez peut-être installer les versions de package exactes décrites plus loin dans cette procédure.

1. Dans la boîte de dialogue **Installer de nouveaux packages npm**, recherchez le package react, puis sélectionnez **Installer le package** pour installer ce dernier.

    ![Installer les packages npm](../javascript/media/tutorial-nodejs-react-install-package.png)

    Sélectionnez la fenêtre **Sortie** pour voir la progression de l’installation du package (sélectionnez **Npm** dans le champ **Afficher la sortie à partir de**). Une fois installé, le package apparaît sous le nœud **npm**.

    Le fichier *package.json* du projet est mis à jour à l’aide des informations relatives au nouveau package, notamment sa version.

1. Au lieu d’utiliser l’interface utilisateur pour rechercher et ajouter le reste des packages l’un après l’autre, collez le code suivant dans *package.jssur*. Pour cela, ajoutez une section `dependencies` avec ce code :

    ```json
    "dependencies": {
      "express": "~4.17.1",
      "path": "~0.12.7",
      "react": "~16.13.1",
      "react-dom": "~16.13.1",
      "ts-loader": "~7.0.1",
      "typescript": "~3.8.3",
      "webpack": "~4.42.1",
      "webpack-cli": "~3.3.11"
    }
    ```

    S’il existe déjà une section `dependencies` dans votre version du modèle vide, remplacez-la simplement par le code JSON précédent. Pour plus d’informations sur l’utilisation de ce fichier, consultez [package.jssur la configuration](../javascript/configure-packages-with-package-json.md).

1. Enregistrez les modifications.

1. Cliquez avec le bouton droit sur le nœud **NPM** dans votre projet et choisissez **installer les packages NPM**.

    Cette commande exécute la commande NPM install directement.

    Dans le volet inférieur, sélectionnez la fenêtre **Sortie** pour voir la progression de l’installation des packages. L’installation pouvant prendre quelques minutes, vous risquez de ne pas voir les résultats immédiatement. Pour voir la sortie, veillez à sélectionner **Npm** dans le champ **Afficher la sortie à partir de** de la fenêtre **Sortie**. (Pour ouvrir la fenêtre, choisissez **affichage**  >  **Sortie** ou appuyez sur **CTRL**  +  **ALT**  +  **O**.)

    Voici les modules npm tels qu’ils apparaissent dans l’Explorateur de solutions après leur installation.

    ![packages npm](../javascript/media/tutorial-nodejs-react-npm-modules-installed.png)

    > [!NOTE]
    > Si vous préférez installer les packages npm à l’aide de la ligne de commande, cliquez avec le bouton droit sur le nœud de projet, puis choisissez **Ouvrir l’invite de commandes ici**. Utilisez les commandes Node.js standard pour installer les packages.

## <a name="add-project-files"></a>Ajouter des fichiers projet

Au cours de ces étapes, vous devez ajouter quatre nouveaux fichiers à votre projet.

* *app.tsx*
* *webpack-config.js*
* *index.html*
* *tsconfig.json*

Pour cette application simple, vous ajoutez les nouveaux fichiers projet à la racine du projet. (Dans la plupart des applications, vous ajoutez généralement les fichiers aux sous-dossiers, et vous changez ensuite les références de chemin relatives correspondantes.)

1. Dans Explorateur de solutions, cliquez avec le bouton droit sur le projet **NodejsWebAppBlank** et choisissez **Ajouter**  >  un **nouvel élément** (ou appuyez sur **CTRL**  +  **MAJ**  +  **A**).

1. Dans la boîte de dialogue **Ajouter un nouvel élément** , choisissez type de **fichier jsx de machine à écrire**, tapez le nom *app. TSX*, puis sélectionnez **Ajouter** ou **OK**.

1. Répétez ces étapes pour ajouter *webpack-config.js*. Au lieu d’un fichier JSX TypeScript, choisissez **Fichier JavaScript**.

1. Répétez les mêmes étapes pour ajouter *index.html* au projet. Au lieu d’un fichier JavaScript, choisissez **Fichier HTML**.

1. Répétez les mêmes étapes pour ajouter *tsconfig.json* au projet. Au lieu d’un fichier JavaScript, choisissez **Fichier config JSON TypeScript**.

## <a name="add-app-code"></a>Ajouter du code d’application

1. Ouvrez *server.js* et remplacez le code existant par le code suivant :

    ```javascript
    'use strict';
    var path = require('path');
    var express = require('express');

    var app = express();

    var staticPath = path.join(__dirname, '/');
    app.use(express.static(staticPath));

    // Allows you to set port in the project properties.
    app.set('port', process.env.PORT || 3000);

    var server = app.listen(app.get('port'), function() {
        console.log('listening');
    });
    ```

   Le code précédent utilise Express pour démarrer Node.js en tant que serveur d’applications web. Ce code permet d’affecter au port le numéro de port configuré dans les propriétés du projet (par défaut, le port 1337 est configuré dans les propriétés). Pour ouvrir les propriétés du projet, cliquez avec le bouton droit sur le projet dans l’Explorateur de solutions, puis choisissez **Propriétés**.

1. Ouvrez *app.tsx*, puis ajoutez le code suivant :

    ```javascript
    declare var require: any

    var React = require('react');
    var ReactDOM = require('react-dom');

    export class Hello extends React.Component {
        render() {
            return (
                <h1>Welcome to React!!</h1>
            );
        }
    }

    ReactDOM.render(<Hello />, document.getElementById('root'));
    ```

    Le code précédent utilise la syntaxe JSX et React pour afficher un message simple.

1. Ouvrez *index.html* et remplacez la section **body** par le code suivant :

    ```html
    <body>
        <div id="root"></div>
        <!-- scripts -->
        <script src="./dist/app-bundle.js"></script>
    </body>
    ```

    Cette page HTML charge *app-bundle.js*, qui contient le code JSX et React transpilé en JavaScript brut. Pour le moment, *app-bundle.js* est un fichier vide. Dans la section suivante, vous allez configurer les options de transpilation du code.

## <a name="configure-webpack-and-typescript-compiler-options"></a>Configurer webpack et les options du compilateur TypeScript

Au cours des étapes précédentes, vous avez ajouté *webpack-config.js* au projet. Vous devez ajouter ensuite le code de configuration de webpack. Vous allez ajouter une configuration de webpack simple qui spécifie un fichier d’entrée (*app.tsx*) et un fichier de sortie (*app-bundle.js*) pour permettre le regroupement et la transpilation du code JSX en JavaScript brut. Pour la transpilation, vous pouvez également configurer certaines options du compilateur TypeScript. Ce code est une configuration de base conçue comme une introduction à webpack et au compilateur TypeScript.

1. Dans l’Explorateur de solutions, ouvrez *webpack-config.js* et ajoutez le code suivant.

    ```json
    module.exports = {
        devtool: 'source-map',
        entry: "./app.tsx",
        mode: "development",
        output: {
            filename: "./app-bundle.js"
        },
        resolve: {
            extensions: ['.Webpack.js', '.web.js', '.ts', '.js', '.jsx', '.tsx']
        },
        module: {
            rules: [
                {
                    test: /\.tsx$/,
                    exclude: /(node_modules|bower_components)/,
                    use: {
                        loader: 'ts-loader'
                    }
                }
            ]
        }
    }
    ```

    Le code de configuration de webpack indique à webpack d’utiliser le chargeur TypeScript pour transpiler le code JSX.

1. Ouvrez *tsconfig.json* et remplacez le code par défaut par le code suivant pour spécifier les options du compilateur TypeScript :

    ```json
    {
      "compilerOptions": {
        "noImplicitAny": false,
        "module": "commonjs",
        "noEmitOnError": true,
        "removeComments": false,
        "sourceMap": true,
        "target": "es5",
        "jsx": "react"
      },
      "exclude": [
        "node_modules"
      ],
      "files": [
        "app.tsx"
      ]
    }
    ```

    *app. TSX* est spécifié en tant que fichier source.

## <a name="transpile-the-jsx"></a>Transpiler le code JSX

1. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le nœud de projet, puis choisissez **Ouvrir l’invite de commandes ici**.

1. À l’invite de commandes, tapez la commande suivante :

    `node_modules\.bin\webpack app.tsx --config webpack-config.js`

    La fenêtre d’invite de commandes affiche le résultat.

    ![Exécuter webpack](../javascript/media/tutorial-nodejs-react-run-webpack-cmd.png)

    Si vous voyez des erreurs à la place de la sortie précédente, vous devez les corriger pour permettre à votre application de fonctionner correctement. Si les versions de votre package npm sont différentes de celles présentées dans ce tutoriel, cela peut constituer une source d’erreurs. Vous pouvez éventuellement corriger les erreurs en utilisant les versions exactes indiquées au cours des étapes précédentes. De plus, si une ou plusieurs de ces versions de package sont dépréciées et génèrent des erreurs, vous devrez peut-être installer une version plus récente pour corriger ces erreurs. Pour plus d’informations sur l’utilisation de *package.json* pour gérer les versions des packages npm, consultez [Configuration de package.json](../javascript/configure-packages-with-package-json.md).

1. Dans Explorateur de solutions, cliquez avec le bouton droit sur le nœud du projet et choisissez **Ajouter**  >  un **dossier existant**, puis choisissez le dossier de *distribution* et choisissez **Sélectionner un dossier**.

    Visual Studio ajoute le dossier *dist* au projet, lequel contient *app-bundle.js* et *app-bundle.js.map*.

1. Ouvrez *app-bundle.js* pour voir le code JavaScript transpilé.

1. Si vous êtes invité à recharger des fichiers modifiés de façon externe, sélectionnez **Oui pour tout**.

    ![Charger des fichiers modifiés](../javascript/media/tutorial-nodejs-react-reload-files.png)

Chaque fois que vous apportez des changements à *app.tsx*, vous devez réexécuter la commande webpack. Pour automatiser cette étape, ajoutez un script de build afin de transpiler le JSX.

## <a name="add-a-build-script-to-transpile-the-jsx"></a>Ajouter un script de build pour transpiler le JSX

À compter de Visual Studio 2019, un script de génération est obligatoire. Au lieu de transpiler le JSX au niveau de la ligne de commande (comme indiqué dans la section précédente), vous pouvez transpiler le JSX durant la génération à partir de Visual Studio.

* Ouvrez *package.json*, puis ajoutez la section suivante après la section `dependencies` :

   ```json
   "scripts": {
    "build": "webpack-cli app.tsx --config webpack-config.js"
   }
   ```

## <a name="run-the-app"></a>Exécuter l’application

1. Sélectionnez **serveur Web (Google Chrome)** ou **serveur Web (Microsoft Edge)** comme cible de débogage actuelle.

    ::: moniker range=">=vs-2019"
    ![Sélectionner Chrome en tant que cible de débogage](../javascript/media/vs-2019/tutorial-nodejs-react-debug-target.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![Sélectionner Chrome en tant que cible de débogage](../javascript/media/tutorial-nodejs-react-debug-target.png)
    ::: moniker-end

    Si Chrome est disponible sur votre ordinateur, mais n’apparaît pas dans les options, choisissez **Naviguer avec** dans la liste déroulante des cibles de débogage et sélectionnez Chrome comme cible de navigateur par défaut (choisissez **Définir comme programme par défaut**).

1. Pour exécuter l’application, appuyez sur **F5** (**Déboguer** > **Démarrer le débogage**) ou sur le bouton fléché vert.

    Une fenêtre de console Node.js s’ouvre et affiche le port sur lequel le débogueur est à l’écoute.

    Visual Studio démarre l’application en lançant le fichier de démarrage, *server.js*.

    ![Exécuter React dans le navigateur](../javascript/media/tutorial-nodejs-react-running-react.png)

1. Fermez la fenêtre du navigateur.

1. Fermez la fenêtre de console.

## <a name="set-a-breakpoint-and-run-the-app"></a>Définir un point d’arrêt et exécuter l’application

1. Dans *server.js*, cliquez dans la marge située à gauche de la déclaration de `staticPath` pour définir un point d’arrêt :

    ![Capture d’écran de la fenêtre Visual Studio code pour server.js. Un point rouge dans la marge de gauche indique qu’un point d’arrêt est défini pour la déclaration staticPath.](../javascript/media/tutorial-nodejs-react-set-breakpoint.png)

    Les points d'arrêt constituent une fonctionnalité élémentaire et essentielle de toute procédure de débogage fiable. Quand vous définissez un point d'arrêt, Visual Studio interrompt l'exécution du code à l'emplacement du point d'arrêt pour vous permettre d'examiner les valeurs des variables, le comportement de la mémoire ou encore la bonne exécution ou non d'une branche de code.

1. Pour exécuter l’application, appuyez sur **F5** (**Déboguer** > **Démarrer le débogage**).

    Le débogueur s’arrête au point d’arrêt que vous avez défini (l’instruction active est marquée en jaune). Vous pouvez maintenant inspecter l’état de votre application en pointant sur les variables situées dans la portée et en utilisant les fenêtres du débogueur, notamment les fenêtres **Variables locales** et **Espion**.

1. Appuyez sur **F5** pour continuer l’exécution de l’application.

1. Si vous souhaitez utiliser le Outils de développement chrome ou les outils F12 pour Microsoft Edge, appuyez sur **F12**. Vous pouvez utiliser ces outils pour examiner le DOM et interagir avec l’application à l’aide de la console JavaScript.

1. Fermez le navigateur web et la console.

## <a name="set-and-hit-a-breakpoint-in-the-client-side-react-code"></a>Définir et atteindre un point d’arrêt dans le code React côté client

Dans la section précédente, vous avez attaché le débogueur au code Node.js côté serveur. Pour attacher le débogueur depuis Visual Studio et atteindre des points d’arrêt dans du code React côté client, vous devez aider le débogueur à identifier le processus approprié. Voici une façon d’y parvenir.

### <a name="prepare-the-browser-for-debugging"></a>Préparer le navigateur pour le débogage

::: moniker range=">=vs-2019"
Pour ce scénario, utilisez Microsoft Edge (chrome), actuellement nommé **Microsoft Edge Beta** dans l’IDE, ou chrome.
::: moniker-end
::: moniker range="vs-2017"
Pour ce scénario, utilisez Chrome.
::: moniker-end

1. Fermez toutes les fenêtres du navigateur cible.

   D’autres instances de navigateur peuvent empêcher l’ouverture du navigateur avec le débogage activé. (Les extensions de navigateur sont peut-être en cours d’exécution et empêchent le mode de débogage complet. par conséquent, vous devrez peut-être ouvrir le gestionnaire des tâches pour rechercher des instances inattendues de

   ::: moniker range=">=vs-2019"
   Pour Microsoft Edge (chrome), arrêtez également toutes les instances de chrome. Étant donné que les deux navigateurs partagent la base de code de chrome, cela donne les meilleurs résultats.
   ::: moniker-end

2. Démarrez votre navigateur avec le débogage activé.

    ::: moniker range=">=vs-2019"
    À compter de Visual Studio 2019, vous pouvez définir l' `--remote-debugging-port=9222` indicateur au lancement du navigateur en sélectionnant **Parcourir avec...** > dans la barre d’outils **Déboguer** , puis en sélectionnant **Ajouter** et en définissant l’indicateur dans le champ **arguments** . Utilisez un autre nom convivial pour le navigateur, tel que **Edge avec débogage** ou **chrome avec débogage**. Pour plus d’informations, consultez les [notes de publication](/visualstudio/releases/2019/release-notes-v16.2).

    ![Configurer votre navigateur pour qu’il s’ouvre avec le débogage activé](../javascript/media/tutorial-nodejs-react-edge-with-debugging.png)

    Vous pouvez également ouvrir la commande **exécuter** à partir du bouton **Démarrer** de Windows (cliquez avec le bouton droit et choisissez **exécuter**), puis entrez la commande suivante :

    `msedge --remote-debugging-port=9222`

    ou

    `chrome.exe --remote-debugging-port=9222`
    ::: moniker-end

    ::: moniker range="vs-2017"
    Ouvrez la commande **Exécuter** à partir du bouton **Démarrer** de Windows (cliquez avec le bouton droit de la souris et choisissez **Exécuter**), puis entrez la commande suivante :

    `chrome.exe --remote-debugging-port=9222`
    ::: moniker-end

    Cela démarre votre navigateur avec le débogage activé.

    L’application n’est pas encore en cours d’exécution. vous disposez donc d’une page de navigateur vide.

### <a name="attach-the-debugger-to-client-side-script"></a>Attacher le débogueur au script côté client

1. Basculez vers Visual Studio, puis définissez un point d’arrêt dans votre code source, *app-bundle.js*  ou *app. TSX*.

    Pour *app-bundle.js*, définissez le point d’arrêt dans la `render()` fonction comme indiqué dans l’illustration suivante :

    ![Capture d’écran de la fenêtre Visual Studio code pour app-bundle.js. Un point rouge dans la marge de gauche indique qu’un point d’arrêt est défini dans la fonction Render.](../javascript/media/tutorial-nodejs-react-set-breakpoint-client-code.png)

    Pour rechercher la `render()` fonction dans le fichier de *app-bundle.js* compilé, utilisez **CTRL** + **F** (**Edit**  >  **Rechercher et remplacer** la  >  **recherche rapide**).

    Pour *app. TSX*, définissez le point d’arrêt à l’intérieur de la `render()` fonction, sur l' `return` instruction.

    ![Capture d’écran de la fenêtre Visual Studio code pour App. TSX. Un point rouge dans la marge de gauche indique qu’un point d’arrêt est défini sur l’instruction return de la fonction Render.](../javascript/media/tutorial-nodejs-react-set-breakpoint-in-tsx-file.png)

2. Si vous définissez le point d’arrêt dans le fichier *. TSX* (plutôt que *app-bundle.js*), vous devez mettre à jour *webpack-config.js*. Remplacez le code suivant :

    ```javascript
    output: {
        filename: "./app-bundle.js",
    },
    ```

    par ce code :

    ```javascript
    output: {
        filename: "./app-bundle.js",
        devtoolModuleFilenameTemplate: '[resource-path]'  // removes the webpack:/// prefix
    },
    ```

    Il s’agit d’un paramètre de développement uniquement pour activer le débogage dans Visual Studio. Ce paramètre vous permet de remplacer les références générées dans le fichier de mappage source, *app-bundle.js. map*, lors de la génération de l’application. Par défaut, les références WebPack du fichier de mappage source incluent le préfixe *WebPack:///* , qui empêche Visual Studio de trouver le fichier source, *app. TSX*. Plus précisément, lorsque vous apportez cette modification, la référence au fichier source, *app. TSX*, est passée de *WebPack:///./app.TSX* à *./app.TSX*, ce qui permet le débogage.

3. Sélectionnez votre navigateur cible comme cible de débogage dans Visual Studio, puis appuyez sur **CTRL** + **F5** (**Déboguer** exécuter  >  **sans débogage**) pour exécuter l’application dans le navigateur.

    ::: moniker range=">=vs-2019"
    Si vous avez créé une configuration de navigateur avec un nom convivial, choisissez-la comme cible de débogage.
    ::: moniker-end

    L’application s’ouvre dans un nouvel onglet du navigateur.

4. Choisissez **Déboguer**  >  **attacher au processus** (ou appuyez sur **CTRL**  +  **ALT**  +  **P**).

    > [!TIP]
    > À compter de Visual Studio 2017, une fois que vous avez attaché le processus la première fois en suivant ces étapes, vous pouvez le rattacher rapidement au même processus en choisissant **Déboguer**  >  **rattacher au processus** (ou en appuyant sur **MAJ**  +  **ALT**  +  **P**).

5. Dans la boîte de dialogue **attacher au processus** , récupérez une liste filtrée des instances de navigateur auxquelles vous pouvez attacher.

    ::: moniker range=">=vs-2019"
    Dans Visual Studio 2019, choisissez le débogueur approprié pour votre navigateur cible, **JavaScript (chrome)** ou **JavaScript (Microsoft Edge-chrome)** dans le champ **attacher à** , tapez **chrome** ou **bord** dans la zone de filtre pour filtrer les résultats de la recherche.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Dans Visual Studio 2017, choisissez **code WebKit** dans le champ **attacher à** , tapez **chrome** dans la zone de filtre pour filtrer les résultats de la recherche.
    ::: moniker-end

6. Sélectionnez le processus du navigateur avec le port d’hôte correct (localhost dans cet exemple), puis sélectionnez **attacher**.

    Le port (1337) peut également apparaître dans le champ **titre** pour vous aider à sélectionner l’instance de navigateur appropriée.

    ::: moniker range=">=vs-2019"
    L’exemple suivant montre comment cela recherche le navigateur Microsoft Edge (chrome).

    ![Attacher au processus](../javascript/media/tutorial-nodejs-react-attach-to-process-edge.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![Attacher au processus](../javascript/media/tutorial-nodejs-react-attach-to-process.png)

    Vous savez que le débogueur est correctement attaché quand l’Explorateur DOM et la console JavaScript s’ouvrent dans Visual Studio. Ces outils de débogage sont similaires aux outils de développement Chrome et aux outils F12 pour Microsoft Edge.
    ::: moniker-end

    > [!TIP]
    > Si le débogueur ne s’attache pas et que vous voyez le message « Impossible de s’attacher au processus. Une opération n’est pas valide dans l’état actuel.», utilisez le gestionnaire des tâches pour fermer toutes les instances du navigateur cible avant de démarrer le navigateur en mode débogage. Les extensions de navigateur peuvent être en cours d’exécution et empêchent le mode de débogage complet.

7. Dans la mesure où le code avec le point d’arrêt s’est déjà exécuté, actualisez la page de votre navigateur pour atteindre le point d’arrêt.

    Pendant que l’exécution du débogueur est en pause, vous pouvez examiner l’état de votre application en pointant sur les variables et en utilisant les fenêtres du débogueur. Vous pouvez faire avancer le débogueur en exécutant pas à pas le code (**F5**, **F10** et **F11**). Pour plus d’informations sur les fonctionnalités de débogage de base, consultez [premier aperçu du débogueur](../debugger/debugger-feature-tour.md).

    Vous pouvez atteindre le point d’arrêt soit *app-bundle.js* , soit son emplacement mappé dans *app. TSX*, en fonction des étapes que vous avez suivies précédemment, ainsi que de l’état de votre environnement et de votre navigateur. De toute façon, vous pouvez exécuter pas à pas le code et examiner les variables.

   * Si vous devez arrêter l’exécution du code dans *app.tsx* et que vous n’y parvenez pas, utilisez **Attacher au processus** comme décrit dans la procédure précédente pour attacher le débogueur. Assurez-vous que votre environnement est correctement configuré :

      * Vous avez fermé toutes les instances de navigateur, y compris les extensions chrome (à l’aide du gestionnaire des tâches), afin de pouvoir exécuter le navigateur en mode débogage. Veillez à démarrer le navigateur en mode débogage.

      * Assurez-vous que votre fichier de mappage source contient une référence à *./app.TSX* et non à *WebPack:///./app.TSX*, ce qui empêche le débogueur Visual Studio de localiser *app. TSX*.
       Sinon, si vous devez vous arrêter dans le code dans *app. TSX* et que vous ne pouvez pas le faire, essayez d’utiliser l' `debugger;` instruction dans *app. TSX*, ou définissez des points d’arrêt dans le outils de développement chrome (ou les outils F12 pour Microsoft Edge) à la place.

   * Si vous devez vous arrêter dans le code de *app-bundle.js* et que vous ne pouvez pas le faire, supprimez le fichier de mappage source, *app-bundle.js. map*.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Déployer l’application sur Linux App Service](../javascript/publish-nodejs-app-azure.md)
